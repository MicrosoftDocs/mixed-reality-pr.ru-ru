---
title: Отслеживание рук
description: Документация по использованию Хандтраккинг в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, отслеживание вручную
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176890"
---
# <a name="hand-tracking"></a><span data-ttu-id="11401-104">Отслеживание рук</span><span class="sxs-lookup"><span data-stu-id="11401-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="11401-105">Профиль отслеживания вручную</span><span class="sxs-lookup"><span data-stu-id="11401-105">Hand tracking profile</span></span>

<span data-ttu-id="11401-106">_Профиль отслеживания вручную_ находится в _системном профиле входной системы_.</span><span class="sxs-lookup"><span data-stu-id="11401-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="11401-107">Он содержит параметры для настройки представления руки.</span><span class="sxs-lookup"><span data-stu-id="11401-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="11401-108">Совместное Prefabs</span><span class="sxs-lookup"><span data-stu-id="11401-108">Joint prefabs</span></span>

<span data-ttu-id="11401-109">Совместное использование Prefabs с помощью простого Prefabs.</span><span class="sxs-lookup"><span data-stu-id="11401-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="11401-110">Соединения _Palm_ и _пальца_ имеют особую важность и имеют собственные prefab, тогда как все остальные соединения совместно используют один и тот же prefab.</span><span class="sxs-lookup"><span data-stu-id="11401-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="11401-111">По умолчанию стыки Prefabs являются простыми геометрическими примитивами.</span><span class="sxs-lookup"><span data-stu-id="11401-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="11401-112">При необходимости их можно заменить.</span><span class="sxs-lookup"><span data-stu-id="11401-112">These can be replaced if desired.</span></span> <span data-ttu-id="11401-113">Если не указано ни одного prefab, вместо него создаются пустые [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) .</span><span class="sxs-lookup"><span data-stu-id="11401-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="11401-114">Старайтесь не использовать сложные сценарии или дорогостоящую отрисовку в совместных Prefabs, так как совместное использование объектов преобразуются во все кадры и может иметь значительные затраты!</span><span class="sxs-lookup"><span data-stu-id="11401-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="11401-115">Представление соединения вручную по умолчанию</span><span class="sxs-lookup"><span data-stu-id="11401-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="11401-116">Совместные метки</span><span class="sxs-lookup"><span data-stu-id="11401-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="11401-117">Сетка prefab</span><span class="sxs-lookup"><span data-stu-id="11401-117">Hand mesh prefab</span></span>

<span data-ttu-id="11401-118">Сетка "рука" используется, если полностью определенные данные сетки предоставлены устройством отслеживания вручную.</span><span class="sxs-lookup"><span data-stu-id="11401-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="11401-119">Сетка, отображаемая в prefab, заменяется данными с устройства, поэтому вполне достаточно фиктивной сетки, такой как куб.</span><span class="sxs-lookup"><span data-stu-id="11401-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="11401-120">Материал prefab используется для сетки "рука".</span><span class="sxs-lookup"><span data-stu-id="11401-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="11401-121">Отображение сетки "рука" может оказать заметное влияние на производительность. по этой причине ее можно полностью отключить, отменив параметр " **включить визуализацию сетки** ".</span><span class="sxs-lookup"><span data-stu-id="11401-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="11401-122">Параметры визуализации вручную</span><span class="sxs-lookup"><span data-stu-id="11401-122">Hand visualization settings</span></span>

<span data-ttu-id="11401-123">Можно отключить или включить визуализацию в сетке и режиме отображения с помощью параметров *режима визуализации сетки* , а также использовать *режимы визуализации* , соответственно.</span><span class="sxs-lookup"><span data-stu-id="11401-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="11401-124">Эти параметры зависят от режима приложения. Это означает, что можно включить некоторые функции в редакторе (чтобы увидеть соединения с имитацией в редакторе, например), одновременно выключив те же функции при развертывании на устройстве (в сборках проигрывателя).</span><span class="sxs-lookup"><span data-stu-id="11401-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="11401-125">Обратите внимание, что в редакторе обычно рекомендуется включить совместную визуализацию (так что в имитации в редакторе будет показано, где находятся соединения с рукой) и как одноранговая визуализация, так и визуализация сетки руки отключены в проигрывателе (так как они вызывают снижение производительности).</span><span class="sxs-lookup"><span data-stu-id="11401-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="11401-126">Написание сценариев</span><span class="sxs-lookup"><span data-stu-id="11401-126">Scripting</span></span>

<span data-ttu-id="11401-127">В системе ввода можно запросить расположение и поворот для каждого отдельного соединения [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="11401-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="11401-128">Кроме того, система предоставляет доступ к [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) , которые следуют за соединениями.</span><span class="sxs-lookup"><span data-stu-id="11401-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="11401-129">Это может быть полезно, если другой GameObject должен постоянно относиться к совместному взаимозаписи.</span><span class="sxs-lookup"><span data-stu-id="11401-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="11401-130">Доступные соединения перечислены в [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) перечислении.</span><span class="sxs-lookup"><span data-stu-id="11401-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="11401-131">Совместный объект уничтожается при потере отслеживания.</span><span class="sxs-lookup"><span data-stu-id="11401-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="11401-132">Убедитесь, что все скрипты, использующие совместный объект, корректно обрабатывали `null` случай, чтобы избежать ошибок.</span><span class="sxs-lookup"><span data-stu-id="11401-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="11401-133">Доступ к данному контроллеру</span><span class="sxs-lookup"><span data-stu-id="11401-133">Accessing a given hand controller</span></span>

<span data-ttu-id="11401-134">Часто доступен отдельный контроллер, например при обработке входных событий.</span><span class="sxs-lookup"><span data-stu-id="11401-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="11401-135">В этом случае совместное использование данных может быть запрошено непосредственно с устройства с помощью [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="11401-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="11401-136">Опрос соединения от контроллера</span><span class="sxs-lookup"><span data-stu-id="11401-136">Polling joint pose from controller</span></span>

<span data-ttu-id="11401-137">[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*)Функция возвращает значение, `false` если запрошенное соединение недоступно по какой-либо причине.</span><span class="sxs-lookup"><span data-stu-id="11401-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="11401-138">В этом случае итоговый объект будет иметь значение [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="11401-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

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

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="11401-139">Совместное преобразование из визуализатора руки</span><span class="sxs-lookup"><span data-stu-id="11401-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="11401-140">В [визуализаторе контроллера](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)можно запросить совместное соединение объектов.</span><span class="sxs-lookup"><span data-stu-id="11401-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

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

### <a name="simplified-joint-data-access"></a><span data-ttu-id="11401-141">Упрощенный совместный доступ к данным</span><span class="sxs-lookup"><span data-stu-id="11401-141">Simplified joint data access</span></span>

<span data-ttu-id="11401-142">Если конкретный контроллер не указан, то для удобного доступа к данным с помощью служебных программ предоставляются вспомогательные классы.</span><span class="sxs-lookup"><span data-stu-id="11401-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="11401-143">Эти функции запрашивают совместное данные от первого доступного устройства, отслеживающего текущее устройство.</span><span class="sxs-lookup"><span data-stu-id="11401-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="11401-144">Опрос соединения a от Ханджоинтутилс</span><span class="sxs-lookup"><span data-stu-id="11401-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="11401-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) — Это статический класс, запрашивающий первое активное устройство.</span><span class="sxs-lookup"><span data-stu-id="11401-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="11401-146">Совместное преобразование из службы совместных соединений</span><span class="sxs-lookup"><span data-stu-id="11401-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="11401-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) сохраняет постоянный набор [объекты gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) для отслеживания соединений.</span><span class="sxs-lookup"><span data-stu-id="11401-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="11401-148">События отслеживания</span><span class="sxs-lookup"><span data-stu-id="11401-148">Hand tracking events</span></span>

<span data-ttu-id="11401-149">Входная система также предоставляет события, если не желательно выполнять опрос данных непосредственно из контроллеров.</span><span class="sxs-lookup"><span data-stu-id="11401-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="11401-150">Совместные события</span><span class="sxs-lookup"><span data-stu-id="11401-150">Joint events</span></span>

<span data-ttu-id="11401-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) обрабатывает обновления совместных позиций.</span><span class="sxs-lookup"><span data-stu-id="11401-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

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

#### <a name="mesh-events"></a><span data-ttu-id="11401-152">События сетки</span><span class="sxs-lookup"><span data-stu-id="11401-152">Mesh events</span></span>

<span data-ttu-id="11401-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) обрабатывает изменения в сетке с назначением руки.</span><span class="sxs-lookup"><span data-stu-id="11401-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="11401-154">Обратите внимание, что сетки "рука" не включены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="11401-154">Note that hand meshes are not enabled by default.</span></span>

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

## <a name="known-issues"></a><span data-ttu-id="11401-155">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="11401-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="11401-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="11401-156">.NET Native</span></span>

<span data-ttu-id="11401-157">В настоящее время существует известная ошибка с основными сборками, использующими серверную часть .NET.</span><span class="sxs-lookup"><span data-stu-id="11401-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="11401-158">в .NET Native `IInspectable` нельзя маршалировать указатели из машинного кода в управляемый с помощью `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="11401-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="11401-159">МРТК использует этот метод для получения `SpatialCoordinateSystem` данных, чтобы получать данные о руки и глаз с платформы.</span><span class="sxs-lookup"><span data-stu-id="11401-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="11401-160">мы предоставили источник DLL в качестве обходного решения для этой проблемы в [собственном репозитории набор средств смешанной реальности](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span><span class="sxs-lookup"><span data-stu-id="11401-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="11401-161">Следуйте инструкциям в файле сведений и скопируйте полученные двоичные файлы в папку plugins в ресурсах Unity.</span><span class="sxs-lookup"><span data-stu-id="11401-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="11401-162">После этого сценарий Виндовсмикседреалитютилитиес, указанный в МРТК, решит проблему.</span><span class="sxs-lookup"><span data-stu-id="11401-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="11401-163">Если вы хотите создать собственную библиотеку DLL или включить в нее этот обходной путь, то основным решением этой проблемы является:</span><span class="sxs-lookup"><span data-stu-id="11401-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="11401-164">И его использование в коде Unity C#:</span><span class="sxs-lookup"><span data-stu-id="11401-164">And its use in your C# Unity code:</span></span>

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
