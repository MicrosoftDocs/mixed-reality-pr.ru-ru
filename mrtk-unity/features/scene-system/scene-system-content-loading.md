---
title: Система сцен — загрузка содержимого
description: Документация по загрузке сцен с помощью МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: df4437a0640637328c3f8f0d78be63a492d4bba15acb8a37bdf2dd3c32d89a59
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223045"
---
# <a name="scene-system-content-loading"></a>Система сцен — загрузка содержимого

Все операции загрузки содержимого являются асинхронными, и по умолчанию вся загрузка содержимого является аддитивной. Операции загрузки содержимого никогда не влияют на сцены диспетчера и освещения. Сведения о мониторинге хода загрузки и активации сцены см. в разделе [мониторинг загрузки содержимого](scene-system-load-progress.md).

## <a name="loading-content"></a>Загрузка содержимого

Чтобы загрузить сцены содержимого, используйте `LoadContent` метод:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Загрузка одного сцены

Эквивалент одной загрузки сцены можно достичь с помощью необязательного `mode` аргумента. `LoadSceneMode.Single` Сначала выгрузите все загруженные сцены содержимого, прежде чем продолжить загрузку.

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

## <a name="next--previous-scene-loading"></a>Загрузка следующего или предыдущего сцены

Содержимое может быть загружено в порядке построения индекса. Это полезно для демонстрации приложений, которые принимают пользователей через набор демонстрационных сцен по одному.

![Текущие сцены в сборке в параметрах проигрывателя](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Обратите внимание, что следующая или Предыдущая загрузка содержимого использует Лоадсценемоде. Single по умолчанию, чтобы обеспечить выгрузку предыдущего содержимого.

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

`PrevContentExists` Возвращает значение true, если существует хотя бы одна сцена содержимого с меньшим индексом сборки, чем самый низкий загруженный в данный момент индекс сборки. `NextContentExists` Возвращает значение true, если имеется хотя бы одна сцена содержимого с более высоким индексом сборки, чем у самого высокого индекса сборки, загруженного в данный момент.

Если `wrap` аргумент имеет значение true, содержимое будет циклически возвращаться к первому или последнему индексу сборки. Это избавляет от необходимости проверять следующее/предыдущее содержимое:

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

## <a name="loading-by-tag"></a>Загрузка по тегу

![Загрузка сцен содержимого по тегу](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

Иногда желательно загружать сцены содержимого в группы. Например, этап работы может состоять из нескольких сцен, каждый из которых должен загружаться одновременно для функционирования. Чтобы упростить это, можно пометить сцены, а затем загрузить их или выгрузить с помощью этого тега.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Загрузка по тегу также может быть полезной, если исполнители хотят внедрять или удалять элементы из интерфейса без необходимости изменения скриптов. Например, выполнение этого скрипта со следующими двумя наборами тегов дает разные результаты:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Тестирование содержимого

Имя сцены | Тег сцены | Загружено скриптом
---|---|---
дебугтерраинфисикс | Ландшафта | •
структуретестинг | Структуры | •
вежетатионтулс | Растительности | •
Mountain | Ландшафта | •
Кабина | Структуры | •
Деревья | Растительности | •

### <a name="final-content"></a>Окончательное содержимое

Имя сцены | Тег сцены | Загружено скриптом
---|---|---
дебугтерраинфисикс | донотинклуде |
структуретестинг | донотинклуде |
вежетатионтулс | донотинклуде |
Mountain | Ландшафта | •
Кабина | Структуры | •
Деревья | Растительности | •

---

## <a name="editor-behavior"></a>Реакция на событие редактора

Все эти операции можно выполнять в редакторе и в режиме воспроизведения с помощью [инспектора служб](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) в системе сцены. В режиме редактирования сцены загружаются мгновенно, а в режиме воспроизведения можно наблюдать за ходом загрузки и использовать [маркеры активации.](scene-system-load-progress.md)

![Система сцен в инспекторе с выделенной загрузкой содержимого](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
