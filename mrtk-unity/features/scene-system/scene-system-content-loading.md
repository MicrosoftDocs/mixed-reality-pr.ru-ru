---
title: Сцена загрузки содержимого системы сцены
description: Документация по загрузке сцен с помощью МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177584"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="3f672-104">Сцена загрузки содержимого системы сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-104">Scene system content loading</span></span>

<span data-ttu-id="3f672-105">Все операции загрузки содержимого являются асинхронными, и по умолчанию вся загрузка содержимого является аддитивной.</span><span class="sxs-lookup"><span data-stu-id="3f672-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="3f672-106">Операции загрузки содержимого никогда не влияют на сцены диспетчера и освещения.</span><span class="sxs-lookup"><span data-stu-id="3f672-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="3f672-107">Сведения о мониторинге хода загрузки и активации сцены см. в разделе [мониторинг загрузки содержимого](scene-system-load-progress.md).</span><span class="sxs-lookup"><span data-stu-id="3f672-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="3f672-108">Загрузка содержимого</span><span class="sxs-lookup"><span data-stu-id="3f672-108">Loading content</span></span>

<span data-ttu-id="3f672-109">Чтобы загрузить сцены содержимого, используйте `LoadContent` метод:</span><span class="sxs-lookup"><span data-stu-id="3f672-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="3f672-110">Загрузка одного сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-110">Single scene loading</span></span>

<span data-ttu-id="3f672-111">Эквивалент одной загрузки сцены можно достичь с помощью необязательного `mode` аргумента.</span><span class="sxs-lookup"><span data-stu-id="3f672-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="3f672-112">`LoadSceneMode.Single` Сначала выгрузите все загруженные сцены содержимого, прежде чем продолжить загрузку.</span><span class="sxs-lookup"><span data-stu-id="3f672-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="3f672-113">Загрузка следующего или предыдущего сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-113">Next / previous scene loading</span></span>

<span data-ttu-id="3f672-114">Содержимое может быть загружено в порядке построения индекса.</span><span class="sxs-lookup"><span data-stu-id="3f672-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="3f672-115">Это полезно для демонстрации приложений, которые принимают пользователей через набор демонстрационных сцен по одному.</span><span class="sxs-lookup"><span data-stu-id="3f672-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Текущие сцены в сборке в параметрах проигрывателя](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="3f672-117">Обратите внимание, что следующая или Предыдущая загрузка содержимого использует Лоадсценемоде. Single по умолчанию, чтобы обеспечить выгрузку предыдущего содержимого.</span><span class="sxs-lookup"><span data-stu-id="3f672-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="3f672-118">`PrevContentExists` Возвращает значение true, если существует хотя бы одна сцена содержимого с меньшим индексом сборки, чем самый низкий загруженный в данный момент индекс сборки.</span><span class="sxs-lookup"><span data-stu-id="3f672-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="3f672-119">`NextContentExists` Возвращает значение true, если имеется хотя бы одна сцена содержимого с более высоким индексом сборки, чем у самого высокого индекса сборки, загруженного в данный момент.</span><span class="sxs-lookup"><span data-stu-id="3f672-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="3f672-120">Если `wrap` аргумент имеет значение true, содержимое будет циклически возвращаться к первому или последнему индексу сборки.</span><span class="sxs-lookup"><span data-stu-id="3f672-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="3f672-121">Это избавляет от необходимости проверять следующее/предыдущее содержимое:</span><span class="sxs-lookup"><span data-stu-id="3f672-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="3f672-122">Загрузка по тегу</span><span class="sxs-lookup"><span data-stu-id="3f672-122">Loading by tag</span></span>

![Загрузка сцен содержимого по тегу](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="3f672-124">Иногда желательно загружать сцены содержимого в группы.</span><span class="sxs-lookup"><span data-stu-id="3f672-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="3f672-125">Например, этап работы может состоять из нескольких сцен, каждый из которых должен загружаться одновременно для функционирования.</span><span class="sxs-lookup"><span data-stu-id="3f672-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="3f672-126">Чтобы упростить это, можно пометить сцены, а затем загрузить их или выгрузить с помощью этого тега.</span><span class="sxs-lookup"><span data-stu-id="3f672-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="3f672-127">Загрузка по тегу также может быть полезной, если исполнители хотят внедрять или удалять элементы из интерфейса без необходимости изменения скриптов.</span><span class="sxs-lookup"><span data-stu-id="3f672-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="3f672-128">Например, выполнение этого скрипта со следующими двумя наборами тегов дает разные результаты:</span><span class="sxs-lookup"><span data-stu-id="3f672-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="3f672-129">Тестирование содержимого</span><span class="sxs-lookup"><span data-stu-id="3f672-129">Testing content</span></span>

<span data-ttu-id="3f672-130">Имя сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-130">Scene Name</span></span> | <span data-ttu-id="3f672-131">Тег сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-131">Scene Tag</span></span> | <span data-ttu-id="3f672-132">Загружено скриптом</span><span class="sxs-lookup"><span data-stu-id="3f672-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="3f672-133">дебугтерраинфисикс</span><span class="sxs-lookup"><span data-stu-id="3f672-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="3f672-134">Ландшафта</span><span class="sxs-lookup"><span data-stu-id="3f672-134">Terrain</span></span> | <span data-ttu-id="3f672-135">•</span><span class="sxs-lookup"><span data-stu-id="3f672-135">•</span></span>
<span data-ttu-id="3f672-136">структуретестинг</span><span class="sxs-lookup"><span data-stu-id="3f672-136">StructureTesting</span></span> | <span data-ttu-id="3f672-137">Структуры</span><span class="sxs-lookup"><span data-stu-id="3f672-137">Structures</span></span> | <span data-ttu-id="3f672-138">•</span><span class="sxs-lookup"><span data-stu-id="3f672-138">•</span></span>
<span data-ttu-id="3f672-139">вежетатионтулс</span><span class="sxs-lookup"><span data-stu-id="3f672-139">VegetationTools</span></span> | <span data-ttu-id="3f672-140">Растительности</span><span class="sxs-lookup"><span data-stu-id="3f672-140">Vegetation</span></span> | <span data-ttu-id="3f672-141">•</span><span class="sxs-lookup"><span data-stu-id="3f672-141">•</span></span>
<span data-ttu-id="3f672-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="3f672-142">Mountain</span></span> | <span data-ttu-id="3f672-143">Ландшафта</span><span class="sxs-lookup"><span data-stu-id="3f672-143">Terrain</span></span> | <span data-ttu-id="3f672-144">•</span><span class="sxs-lookup"><span data-stu-id="3f672-144">•</span></span>
<span data-ttu-id="3f672-145">Кабина</span><span class="sxs-lookup"><span data-stu-id="3f672-145">Cabin</span></span> | <span data-ttu-id="3f672-146">Структуры</span><span class="sxs-lookup"><span data-stu-id="3f672-146">Structures</span></span> | <span data-ttu-id="3f672-147">•</span><span class="sxs-lookup"><span data-stu-id="3f672-147">•</span></span>
<span data-ttu-id="3f672-148">Деревья</span><span class="sxs-lookup"><span data-stu-id="3f672-148">Trees</span></span> | <span data-ttu-id="3f672-149">Растительности</span><span class="sxs-lookup"><span data-stu-id="3f672-149">Vegetation</span></span> | <span data-ttu-id="3f672-150">•</span><span class="sxs-lookup"><span data-stu-id="3f672-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="3f672-151">Окончательное содержимое</span><span class="sxs-lookup"><span data-stu-id="3f672-151">Final content</span></span>

<span data-ttu-id="3f672-152">Имя сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-152">Scene Name</span></span> | <span data-ttu-id="3f672-153">Тег сцены</span><span class="sxs-lookup"><span data-stu-id="3f672-153">Scene Tag</span></span> | <span data-ttu-id="3f672-154">Загружено скриптом</span><span class="sxs-lookup"><span data-stu-id="3f672-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="3f672-155">дебугтерраинфисикс</span><span class="sxs-lookup"><span data-stu-id="3f672-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="3f672-156">донотинклуде</span><span class="sxs-lookup"><span data-stu-id="3f672-156">DoNotInclude</span></span> |
<span data-ttu-id="3f672-157">структуретестинг</span><span class="sxs-lookup"><span data-stu-id="3f672-157">StructureTesting</span></span> | <span data-ttu-id="3f672-158">донотинклуде</span><span class="sxs-lookup"><span data-stu-id="3f672-158">DoNotInclude</span></span> |
<span data-ttu-id="3f672-159">вежетатионтулс</span><span class="sxs-lookup"><span data-stu-id="3f672-159">VegetationTools</span></span> | <span data-ttu-id="3f672-160">донотинклуде</span><span class="sxs-lookup"><span data-stu-id="3f672-160">DoNotInclude</span></span> |
<span data-ttu-id="3f672-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="3f672-161">Mountain</span></span> | <span data-ttu-id="3f672-162">Ландшафта</span><span class="sxs-lookup"><span data-stu-id="3f672-162">Terrain</span></span> | <span data-ttu-id="3f672-163">•</span><span class="sxs-lookup"><span data-stu-id="3f672-163">•</span></span>
<span data-ttu-id="3f672-164">Кабина</span><span class="sxs-lookup"><span data-stu-id="3f672-164">Cabin</span></span> | <span data-ttu-id="3f672-165">Структуры</span><span class="sxs-lookup"><span data-stu-id="3f672-165">Structures</span></span> | <span data-ttu-id="3f672-166">•</span><span class="sxs-lookup"><span data-stu-id="3f672-166">•</span></span>
<span data-ttu-id="3f672-167">Деревья</span><span class="sxs-lookup"><span data-stu-id="3f672-167">Trees</span></span> | <span data-ttu-id="3f672-168">Растительности</span><span class="sxs-lookup"><span data-stu-id="3f672-168">Vegetation</span></span> | <span data-ttu-id="3f672-169">•</span><span class="sxs-lookup"><span data-stu-id="3f672-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="3f672-170">Реакция на событие редактора</span><span class="sxs-lookup"><span data-stu-id="3f672-170">Editor behavior</span></span>

<span data-ttu-id="3f672-171">Все эти операции можно выполнять в редакторе и в режиме воспроизведения с помощью [инспектора служб](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) в системе сцены.</span><span class="sxs-lookup"><span data-stu-id="3f672-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="3f672-172">В режиме редактирования сцены загружаются мгновенно, а в режиме воспроизведения можно наблюдать за ходом загрузки и использовать [маркеры активации.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="3f672-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Система сцен в инспекторе с выделенной загрузкой содержимого](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
