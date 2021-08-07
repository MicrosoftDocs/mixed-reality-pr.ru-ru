---
title: Система сцен — ход выполнения загрузки
description: Документация по загрузке содержимого сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 1d2382e11092b20aca5bf8480ade521ffb94a70a325540e70487d7f581e8cf15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186620"
---
# <a name="monitoring-content-loading"></a>Мониторинг загрузки содержимого

## <a name="scene-operation-progress"></a>Ход выполнения операции сцены

При загрузке или выгрузке содержимого `SceneOperationInProgress` свойство будет возвращать значение true. Ход выполнения этой операции можно отслеживать с помощью `SceneOperationProgress` Свойства.

`SceneOperationProgress`Значение является средним значением всех текущих асинхронных операций сцены. В начале загрузки содержимого `SceneOperationProgress` значение будет равно нулю. После полного завершения `SceneOperationProgress` будет установлено значение 1, которое останется равным 1, пока не будет выполнена следующая операция. Обратите внимание, что только операции с сценами содержимого влияют на эти свойства.

Эти свойства отражать состояние *всей операции* от начала до конца, даже если эта операция включает несколько шагов:

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

### <a name="progress-examples"></a>Примеры хода выполнения

`SceneOperationInProgress` может быть полезным, если действие должно быть приостановлено во время загрузки содержимого:

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

`SceneOperationProgress` может использоваться для вывода диалоговых окон хода выполнения:

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

## <a name="monitoring-with-actions"></a>Мониторинг с помощью действий

Система сцен предоставляет несколько действий, позволяющих получить сведения о загрузке и выгрузке сцен. Каждое действие передает имя затрагиваемой сцены.

Если операция загрузки или выгрузки включает несколько сцен, соответствующие действия будут вызываться один раз для каждой затронутой сцены. Они также вызываются сразу после завершения операции загрузки или выгрузки *.* По этой причине рекомендуется использовать действия *онвиллунлоад* для обнаружения содержимого, которое *будет* уничтожено, в отличие от использования *onunloadных* действий для обнаружения уничтоженного содержимого после факта.

На стороне отразится, *так как операции, загруженные* с помощью команды, вызываются только в том случае, если все монтажные кадры активированы и полностью загружены *, использование* запущенных действий для обнаружения и использования нового содержимого гарантирует безопасность.

Действие | При вызове | Сцены содержимого | Освещение сцен | Сцены диспетчера
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Непосредственно перед нагрузкой сцены содержимого | • | |  
`OnContentLoaded` | После полной загрузки и активации всех сцен содержимого в операции загрузки | • | |
`OnWillUnloadContent` | Непосредственно перед операцией выгрузки сцены содержимого | • | |
`OnContentUnloaded` | После полной выгрузки всех сцен содержимого в операции выгрузки | • | |
`OnWillLoadLighting` | Непосредственно перед загрузкой сцены освещения | | • |
`OnLightingLoaded` | После полной загрузки и активации сцены освещения| | • |
`OnWillUnloadLighting` | Непосредственно перед выгрузкой сцены освещения | | • |
`OnLightingUnloaded` | После полной выгрузки сцены освещения | | • |
`OnWillLoadScene` | Непосредственно перед загрузкой сцены | • | • | •
`OnSceneLoaded` | После полной загрузки и активации всех сцен в операции | • | • | •
`OnWillUnloadScene` | Непосредственно перед выгрузкой сцены | • | • | •
`OnSceneUnloaded` | После полной выгрузки сцены |  • | • | •

### <a name="action-examples"></a>Примеры действий

Другой пример диалогового окна хода выполнения с использованием действий и соподпрограммы вместо обновления:

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

## <a name="controlling-scene-activation"></a>Управление активацией сцены

По умолчанию для сцен содержимого задается значение активировать при загрузке. Если требуется управлять активацией сцены вручную, можно передать `SceneActivationToken` любой метод загрузки содержимого. Если несколько сцен содержимого загружаются одной операцией, этот маркер активации будет применяться ко всем монтажным кадрам.

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

## <a name="checking-which-content-is-loaded"></a>Проверка загруженного содержимого

`ContentSceneNames`Свойство предоставляет массив доступных сцен содержимого в порядке построения индекса. Можно проверить, загружены ли эти сцены с помощью `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
