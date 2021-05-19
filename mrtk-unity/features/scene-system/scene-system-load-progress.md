---
title: Система сцен — ход выполнения загрузки
description: Документация по загрузке содержимого сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144405"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="43152-104">Мониторинг загрузки содержимого</span><span class="sxs-lookup"><span data-stu-id="43152-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="43152-105">Ход выполнения операции сцены</span><span class="sxs-lookup"><span data-stu-id="43152-105">Scene operation progress</span></span>

<span data-ttu-id="43152-106">При загрузке или выгрузке содержимого `SceneOperationInProgress` свойство будет возвращать значение true.</span><span class="sxs-lookup"><span data-stu-id="43152-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="43152-107">Ход выполнения этой операции можно отслеживать с помощью `SceneOperationProgress` Свойства.</span><span class="sxs-lookup"><span data-stu-id="43152-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="43152-108">`SceneOperationProgress`Значение является средним значением всех текущих асинхронных операций сцены.</span><span class="sxs-lookup"><span data-stu-id="43152-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="43152-109">В начале загрузки содержимого `SceneOperationProgress` значение будет равно нулю.</span><span class="sxs-lookup"><span data-stu-id="43152-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="43152-110">После полного завершения `SceneOperationProgress` будет установлено значение 1, которое останется равным 1, пока не будет выполнена следующая операция.</span><span class="sxs-lookup"><span data-stu-id="43152-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="43152-111">Обратите внимание, что только операции с сценами содержимого влияют на эти свойства.</span><span class="sxs-lookup"><span data-stu-id="43152-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="43152-112">Эти свойства отражать состояние *всей операции* от начала до конца, даже если эта операция включает несколько шагов:</span><span class="sxs-lookup"><span data-stu-id="43152-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="43152-113">Примеры хода выполнения</span><span class="sxs-lookup"><span data-stu-id="43152-113">Progress examples</span></span>

<span data-ttu-id="43152-114">`SceneOperationInProgress` может быть полезным, если действие должно быть приостановлено во время загрузки содержимого:</span><span class="sxs-lookup"><span data-stu-id="43152-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="43152-115">`SceneOperationProgress` может использоваться для вывода диалоговых окон хода выполнения:</span><span class="sxs-lookup"><span data-stu-id="43152-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="43152-116">Мониторинг с помощью действий</span><span class="sxs-lookup"><span data-stu-id="43152-116">Monitoring with actions</span></span>

<span data-ttu-id="43152-117">Система сцен предоставляет несколько действий, позволяющих получить сведения о загрузке и выгрузке сцен.</span><span class="sxs-lookup"><span data-stu-id="43152-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="43152-118">Каждое действие передает имя затрагиваемой сцены.</span><span class="sxs-lookup"><span data-stu-id="43152-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="43152-119">Если операция загрузки или выгрузки включает несколько сцен, соответствующие действия будут вызываться один раз для каждой затронутой сцены.</span><span class="sxs-lookup"><span data-stu-id="43152-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="43152-120">Они также вызываются сразу после завершения операции загрузки или выгрузки *.*</span><span class="sxs-lookup"><span data-stu-id="43152-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="43152-121">По этой причине рекомендуется использовать действия *онвиллунлоад* для обнаружения содержимого, которое *будет* уничтожено, в отличие от использования *onunloadных* действий для обнаружения уничтоженного содержимого после факта.</span><span class="sxs-lookup"><span data-stu-id="43152-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="43152-122">На стороне отразится, *так как операции, загруженные* с помощью команды, вызываются только в том случае, если все монтажные кадры активированы и полностью загружены *, использование* запущенных действий для обнаружения и использования нового содержимого гарантирует безопасность.</span><span class="sxs-lookup"><span data-stu-id="43152-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="43152-123">Действие</span><span class="sxs-lookup"><span data-stu-id="43152-123">Action</span></span> | <span data-ttu-id="43152-124">При вызове</span><span class="sxs-lookup"><span data-stu-id="43152-124">When it's invoked</span></span> | <span data-ttu-id="43152-125">Сцены содержимого</span><span class="sxs-lookup"><span data-stu-id="43152-125">Content Scenes</span></span> | <span data-ttu-id="43152-126">Освещение сцен</span><span class="sxs-lookup"><span data-stu-id="43152-126">Lighting Scenes</span></span> | <span data-ttu-id="43152-127">Сцены диспетчера</span><span class="sxs-lookup"><span data-stu-id="43152-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="43152-128">Непосредственно перед нагрузкой сцены содержимого</span><span class="sxs-lookup"><span data-stu-id="43152-128">Just prior to a content scene load</span></span> | <span data-ttu-id="43152-129">•</span><span class="sxs-lookup"><span data-stu-id="43152-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="43152-130">После полной загрузки и активации всех сцен содержимого в операции загрузки</span><span class="sxs-lookup"><span data-stu-id="43152-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="43152-131">•</span><span class="sxs-lookup"><span data-stu-id="43152-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="43152-132">Непосредственно перед операцией выгрузки сцены содержимого</span><span class="sxs-lookup"><span data-stu-id="43152-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="43152-133">•</span><span class="sxs-lookup"><span data-stu-id="43152-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="43152-134">После полной выгрузки всех сцен содержимого в операции выгрузки</span><span class="sxs-lookup"><span data-stu-id="43152-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="43152-135">•</span><span class="sxs-lookup"><span data-stu-id="43152-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="43152-136">Непосредственно перед загрузкой сцены освещения</span><span class="sxs-lookup"><span data-stu-id="43152-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="43152-137">•</span><span class="sxs-lookup"><span data-stu-id="43152-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="43152-138">После полной загрузки и активации сцены освещения</span><span class="sxs-lookup"><span data-stu-id="43152-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="43152-139">•</span><span class="sxs-lookup"><span data-stu-id="43152-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="43152-140">Непосредственно перед выгрузкой сцены освещения</span><span class="sxs-lookup"><span data-stu-id="43152-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="43152-141">•</span><span class="sxs-lookup"><span data-stu-id="43152-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="43152-142">После полной выгрузки сцены освещения</span><span class="sxs-lookup"><span data-stu-id="43152-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="43152-143">•</span><span class="sxs-lookup"><span data-stu-id="43152-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="43152-144">Непосредственно перед загрузкой сцены</span><span class="sxs-lookup"><span data-stu-id="43152-144">Just prior to a scene load</span></span> | <span data-ttu-id="43152-145">•</span><span class="sxs-lookup"><span data-stu-id="43152-145">•</span></span> | <span data-ttu-id="43152-146">•</span><span class="sxs-lookup"><span data-stu-id="43152-146">•</span></span> | <span data-ttu-id="43152-147">•</span><span class="sxs-lookup"><span data-stu-id="43152-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="43152-148">После полной загрузки и активации всех сцен в операции</span><span class="sxs-lookup"><span data-stu-id="43152-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="43152-149">•</span><span class="sxs-lookup"><span data-stu-id="43152-149">•</span></span> | <span data-ttu-id="43152-150">•</span><span class="sxs-lookup"><span data-stu-id="43152-150">•</span></span> | <span data-ttu-id="43152-151">•</span><span class="sxs-lookup"><span data-stu-id="43152-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="43152-152">Непосредственно перед выгрузкой сцены</span><span class="sxs-lookup"><span data-stu-id="43152-152">Just prior to a scene unload</span></span> | <span data-ttu-id="43152-153">•</span><span class="sxs-lookup"><span data-stu-id="43152-153">•</span></span> | <span data-ttu-id="43152-154">•</span><span class="sxs-lookup"><span data-stu-id="43152-154">•</span></span> | <span data-ttu-id="43152-155">•</span><span class="sxs-lookup"><span data-stu-id="43152-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="43152-156">После полной выгрузки сцены</span><span class="sxs-lookup"><span data-stu-id="43152-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="43152-157">•</span><span class="sxs-lookup"><span data-stu-id="43152-157">•</span></span> | <span data-ttu-id="43152-158">•</span><span class="sxs-lookup"><span data-stu-id="43152-158">•</span></span> | <span data-ttu-id="43152-159">•</span><span class="sxs-lookup"><span data-stu-id="43152-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="43152-160">Примеры действий</span><span class="sxs-lookup"><span data-stu-id="43152-160">Action examples</span></span>

<span data-ttu-id="43152-161">Другой пример диалогового окна хода выполнения с использованием действий и соподпрограммы вместо обновления:</span><span class="sxs-lookup"><span data-stu-id="43152-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="43152-162">Управление активацией сцены</span><span class="sxs-lookup"><span data-stu-id="43152-162">Controlling scene activation</span></span>

<span data-ttu-id="43152-163">По умолчанию для сцен содержимого задается значение активировать при загрузке.</span><span class="sxs-lookup"><span data-stu-id="43152-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="43152-164">Если требуется управлять активацией сцены вручную, можно передать `SceneActivationToken` любой метод загрузки содержимого.</span><span class="sxs-lookup"><span data-stu-id="43152-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="43152-165">Если несколько сцен содержимого загружаются одной операцией, этот маркер активации будет применяться ко всем монтажным кадрам.</span><span class="sxs-lookup"><span data-stu-id="43152-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="43152-166">Проверка загруженного содержимого</span><span class="sxs-lookup"><span data-stu-id="43152-166">Checking which content is loaded</span></span>

<span data-ttu-id="43152-167">`ContentSceneNames`Свойство предоставляет массив доступных сцен содержимого в порядке построения индекса.</span><span class="sxs-lookup"><span data-stu-id="43152-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="43152-168">Можно проверить, загружены ли эти сцены с помощью `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="43152-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
