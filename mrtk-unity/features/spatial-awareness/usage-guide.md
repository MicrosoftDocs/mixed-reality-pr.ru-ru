---
title: усинггуиде
description: Описывает ключевые механизмы и API-интерфейсы для программной настройки системы поддержки пространственной информации.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204126"
---
# <a name="configuring-mesh-observers-via-code"></a>Настройка наблюдателей сетки с помощью кода

В этой статье обсуждаются некоторые ключевые механизмы и API-интерфейсы для программной настройки [системы пространственной](spatial-awareness-getting-started.md) информации и связанных поставщиков данных *наблюдателя сети* .

## <a name="accessing-mesh-observers"></a>Доступ к наблюдателям сетки

Классы наблюдателя сетки, реализующие [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) интерфейс, предоставляют системе пространственной связи данные сетки, относящиеся к конкретной платформе. В профиле сведений о пространственной поддержке можно настроить несколько наблюдателей.

доступ к поставщикам данных системы пространственной информации в основном такой же, как и для любой другой службы набор средств смешанной реальности. Служба пространственной осведомленности должна быть приведена к [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) интерфейсу для доступа через `GetDataProvider<T>` API-интерфейсы, которые затем можно использовать для доступа к объектам наблюдателя сетки непосредственно во время выполнения.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`Вспомогательный метод упрощает этот шаблон доступа, как показано ниже.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Запуск и остановка наблюдения за сетями

Одна из наиболее распространенных задач при работе с системой пространственной информации заключается в том, что она включается динамически во время выполнения. Это делается для наблюдателя с помощью API- [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) интерфейсов и.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Эта функциональность кода также может быть упрощена посредством доступа непосредственно через систему пространственной информации.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Запуск и остановка наблюдения за всеми сетками

Как правило, удобно запускать и прекращать наблюдение за сеткой в приложении. Это можно сделать с помощью полезных системных API-интерфейсов пространственного отслеживания [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) и [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Перечисление и доступ к сеткам

Доступ к сетке можно выполнить для наблюдателя, а затем перечислить через сетку, известные этому наблюдателю сетки через [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.

При запуске в редакторе один из них может использовать [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) для сохранения `Mesh` объекта в файл ресурса.

При запуске на устройстве существует множество сообществ и доступных подключаемых модулей для сериализации `MeshFilter` данных в тип файла модели ([Пример obj](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Отображение и скрытие пространственной сетки

Можно программно скрыть или показать сетки, используя приведенный ниже образец кода.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Регистрация для событий наблюдения в сети

Компоненты могут реализовывать `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` и затем регистрироваться в системе пространственной осведомленности для получения событий наблюдения в сетке.

`DemoSpatialMeshHandler`Скрипт (Assets/мртк/examples/спатиалаваренесс/Scripts) — это полезный пример и отправная точка для прослушивания событий наблюдателя сетки.

Это упрощенный пример прослушивания событий *демоспатиалмешхандлер* для сценария и сетки.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>См. также раздел

- [начало работы пространственной осведомленности](spatial-awareness-getting-started.md)
- [Настройка наблюдателя сетки с поддержкой пространственного расположения](configuring-spatial-awareness-mesh-observer.md)
- [Документация по API пространственной осведомленности](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
