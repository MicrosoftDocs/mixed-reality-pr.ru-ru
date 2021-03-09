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
# <a name="mixed-reality-native-interop-in-unity"></a>Встроенное взаимодействие смешанной реальности в Unity

Каждое приложение смешанной реальности [получает холографикспаце,](../native/getting-a-holographicspace.md) прежде чем оно начнет получать данные камеры и кадры визуализации. В Unity подсистема выполняет эти действия для вас, обрабатывая holographic и внутренне обновление как часть цикла подготовки к просмотру.

Однако в сложных сценариях может потребоваться получить доступ к базовым собственным объектам, таким как <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">холографиккамера</a> и Current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a>.

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>Распаковка собственных указателей

После получения `IntPtr` из одного из методов, приведенных выше (не требуется для мртк), используйте приведенные ниже фрагменты кода, чтобы маршалировать их в управляемые объекты.

При использовании [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)можно создать управляемый объект из собственного указателя с помощью `FromNativePtr()` метода:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

В противном случае используйте `Marshal.GetObjectForIUnknown()` и выполните приведение к нужному типу:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>Преобразование между системами координат

Unity использует левую систему координат, а API-интерфейсы восприятия Windows — для использования правильных систем координат. Для преобразования между этими двумя соглашениями можно использовать следующие вспомогательные методы:

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

### <a name="using-holographicframe-native-data"></a>Использование собственных данных Холографикфраме

> [!NOTE]
> Изменение состояния собственных объектов, полученных через Холографикфраменативедата, может привести к непредсказуемому поведению и артефактам отрисовки, особенно если Unity также является причиной того же состояния.  Например, не следует вызывать Холографикфраме. Упдатекуррентпредиктион, или, в противном случае прогнозирование, которое Unity визуализирует с этим кадром, будет не синхронизировано с объектом, который ожидается Windows, что снизит [стабильность](../platform-capabilities-and-apis/hologram-stability.md).

Если вам нужен доступ к собственным интерфейсам для подготовки к просмотру или отладке, используйте данные из Холографикфраменативедата в собственных подключаемых модулях или коде C#.

Ниже приведен пример того, как можно использовать Холографикфраменативедата для получения прогноза текущего кадра для времени Photon с помощью расширений пакета SDK XR.

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

## <a name="see-also"></a>См. также

* [Использование пространства имен Windows с приложениями Unity для HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Отрисовка в DirectX](../native/rendering-in-directx.md)
