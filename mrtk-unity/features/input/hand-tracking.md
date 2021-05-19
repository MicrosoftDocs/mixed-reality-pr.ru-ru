---
title: Отслеживание рук
description: Документация по использованию Хандтраккинг в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, отслеживание вручную
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143350"
---
# <a name="hand-tracking"></a>Отслеживание рук

## <a name="hand-tracking-profile"></a>Профиль отслеживания вручную

_Профиль отслеживания вручную_ находится в _системном профиле входной системы_. Он содержит параметры для настройки представления руки.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Совместное Prefabs

Совместное использование Prefabs с помощью простого Prefabs. Соединения _Palm_ и _пальца_ имеют особую важность и имеют собственные prefab, тогда как все остальные соединения совместно используют один и тот же prefab.

По умолчанию стыки Prefabs являются простыми геометрическими примитивами. При необходимости их можно заменить. Если не указано ни одного prefab, вместо него создаются пустые [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) .

> [!WARNING]
> Старайтесь не использовать сложные сценарии или дорогостоящую отрисовку в совместных Prefabs, так как совместное использование объектов преобразуются во все кадры и может иметь значительные затраты!

Представление соединения вручную по умолчанию |  Совместные метки
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Сетка prefab

Сетка "рука" используется, если полностью определенные данные сетки предоставлены устройством отслеживания вручную. Сетка, отображаемая в prefab, заменяется данными с устройства, поэтому вполне достаточно фиктивной сетки, такой как куб. Материал prefab используется для сетки "рука".

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

Отображение сетки "рука" может оказать заметное влияние на производительность. по этой причине ее можно полностью отключить, отменив параметр " **включить визуализацию сетки** ".

## <a name="hand-visualization-settings"></a>Параметры визуализации вручную

Можно отключить или включить визуализацию в сетке и режиме отображения с помощью параметров *режима визуализации сетки* , а также использовать *режимы визуализации* , соответственно. Эти параметры зависят от режима приложения. Это означает, что можно включить некоторые функции в редакторе (чтобы увидеть соединения с имитацией в редакторе, например), одновременно выключив те же функции при развертывании на устройстве (в сборках проигрывателя).

Обратите внимание, что в редакторе обычно рекомендуется включить совместную визуализацию (так что в имитации в редакторе будет показано, где находятся соединения с рукой) и как одноранговая визуализация, так и визуализация сетки руки отключены в проигрывателе (так как они вызывают снижение производительности).

## <a name="scripting"></a>Написание сценариев

В системе ввода можно запросить расположение и поворот для каждого отдельного соединения [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Кроме того, система предоставляет доступ к [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) , которые следуют за соединениями. Это может быть полезно, если другой GameObject должен постоянно относиться к совместному взаимозаписи.

Доступные соединения перечислены в [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) перечислении.

> [!NOTE]
> Совместный объект уничтожается при потере отслеживания. Убедитесь, что все скрипты, использующие совместный объект, корректно обрабатывали `null` случай, чтобы избежать ошибок.

### <a name="accessing-a-given-hand-controller"></a>Доступ к данному контроллеру

Часто доступен отдельный контроллер, например при обработке входных событий. В этом случае совместное использование данных может быть запрошено непосредственно с устройства с помощью [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) интерфейса.

#### <a name="polling-joint-pose-from-controller"></a>Опрос соединения от контроллера

[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*)Функция возвращает значение, `false` если запрошенное соединение недоступно по какой-либо причине. В этом случае итоговый объект будет иметь значение [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a>Совместное преобразование из визуализатора руки

В [визуализаторе контроллера](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)можно запросить совместное соединение объектов.

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a>Упрощенный совместный доступ к данным

Если конкретный контроллер не указан, то для удобного доступа к данным с помощью служебных программ предоставляются вспомогательные классы. Эти функции запрашивают совместное данные от первого доступного устройства, отслеживающего текущее устройство.

#### <a name="polling-joint-pose-from-handjointutils"></a>Опрос соединения a от Ханджоинтутилс

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) — Это статический класс, запрашивающий первое активное устройство.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Совместное преобразование из службы совместных соединений

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) сохраняет постоянный набор [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) для отслеживания соединений.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>События отслеживания

Входная система также предоставляет события, если не желательно выполнять опрос данных непосредственно из контроллеров.

#### <a name="joint-events"></a>Совместные события

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) обрабатывает обновления совместных позиций.

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a>События сетки

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) обрабатывает изменения в сетке с назначением руки.

Обратите внимание, что сетки "рука" не включены по умолчанию.

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a>Известные проблемы

### <a name="net-native"></a>.NET Native

В настоящее время существует известная ошибка с основными сборками, использующими серверную часть .NET. В .NET Native `IInspectable` нельзя маршалировать указатели из машинного кода в управляемый с помощью `Marshal.GetObjectForIUnknown` . МРТК использует этот метод для получения `SpatialCoordinateSystem` данных, чтобы получать данные о руки и глаз с платформы.

Мы предоставили источник DLL в качестве обходного решения для этой проблемы в [репозитории машинного кода Mixed Reality](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround). Следуйте инструкциям в файле сведений и скопируйте полученные двоичные файлы в папку plugins в ресурсах Unity. После этого сценарий Виндовсмикседреалитютилитиес, указанный в МРТК, решит проблему.

Если вы хотите создать собственную библиотеку DLL или включить в нее этот обходной путь, то основным решением этой проблемы является:

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

И его использование в коде Unity C#:

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
