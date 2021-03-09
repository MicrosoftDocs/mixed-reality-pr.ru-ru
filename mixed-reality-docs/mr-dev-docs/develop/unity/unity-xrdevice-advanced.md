---
title: Собственные объекты смешанной реальности в Unity
description: Узнайте, как получить доступ к базовым объектам holographic в Unity с помощью пространства имен XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, Mixed Reality, Native, ксрдевице, спатиалкурдинатесистем, холографикфраме, холографиккамера, испатиалкурдинатесистем, iholographicframe, iholographiccamera, getnativeptr, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475081"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="0c4f7-104">Встроенное взаимодействие смешанной реальности в Unity</span><span class="sxs-lookup"><span data-stu-id="0c4f7-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="0c4f7-105">Каждое приложение смешанной реальности [получает холографикспаце,](../native/getting-a-holographicspace.md) прежде чем оно начнет получать данные камеры и кадры визуализации.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="0c4f7-106">В Unity подсистема выполняет эти действия для вас, обрабатывая holographic и внутренне обновление как часть цикла подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="0c4f7-107">Однако в сложных сценариях может потребоваться получить доступ к базовым собственным объектам, таким как <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">холографиккамера</a> и Current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a>.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="0c4f7-108">Распаковка собственных указателей</span><span class="sxs-lookup"><span data-stu-id="0c4f7-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="0c4f7-109">После получения `IntPtr` из одного из методов, приведенных выше (не требуется для мртк), используйте приведенные ниже фрагменты кода, чтобы маршалировать их в управляемые объекты.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="0c4f7-110">При использовании [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)можно создать управляемый объект из собственного указателя с помощью `FromNativePtr()` метода:</span><span class="sxs-lookup"><span data-stu-id="0c4f7-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="0c4f7-111">В противном случае используйте `Marshal.GetObjectForIUnknown()` и выполните приведение к нужному типу:</span><span class="sxs-lookup"><span data-stu-id="0c4f7-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="0c4f7-112">Преобразование между системами координат</span><span class="sxs-lookup"><span data-stu-id="0c4f7-112">Converting between coordinate systems</span></span>

<span data-ttu-id="0c4f7-113">Unity использует левую систему координат, а API-интерфейсы восприятия Windows — для использования правильных систем координат.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="0c4f7-114">Для преобразования между этими двумя соглашениями можно использовать следующие вспомогательные методы:</span><span class="sxs-lookup"><span data-stu-id="0c4f7-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="0c4f7-115">Использование собственных данных Холографикфраме</span><span class="sxs-lookup"><span data-stu-id="0c4f7-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="0c4f7-116">Изменение состояния собственных объектов, полученных через Холографикфраменативедата, может привести к непредсказуемому поведению и артефактам отрисовки, особенно если Unity также является причиной того же состояния.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="0c4f7-117">Например, не следует вызывать Холографикфраме. Упдатекуррентпредиктион, или, в противном случае прогнозирование, которое Unity визуализирует с этим кадром, будет не синхронизировано с объектом, который ожидается Windows, что снизит [стабильность](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="0c4f7-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="0c4f7-118">Если вам нужен доступ к собственным интерфейсам для подготовки к просмотру или отладке, используйте данные из Холографикфраменативедата в собственных подключаемых модулях или коде C#.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="0c4f7-119">Ниже приведен пример того, как можно использовать Холографикфраменативедата для получения прогноза текущего кадра для времени Photon с помощью расширений пакета SDK XR.</span><span class="sxs-lookup"><span data-stu-id="0c4f7-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="0c4f7-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0c4f7-120">See Also</span></span>

* [<span data-ttu-id="0c4f7-121">Использование пространства имен Windows с приложениями Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="0c4f7-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="0c4f7-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a></span><span class="sxs-lookup"><span data-stu-id="0c4f7-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="0c4f7-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="0c4f7-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="0c4f7-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="0c4f7-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="0c4f7-125">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="0c4f7-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
