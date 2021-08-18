---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2021
ms.locfileid: "122264803"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>виндовсмикседреалитютилитиес

**пространство имен:** *Microsoft. микседреалити. набор средств. Виндовсмикседреалити*<br>
**Тип:** *виндовсмикседреалитютилитиес*

МРТК предоставляет уже Упакованные типы как в устаревших пакетах WSA, так и в пакете SDK XR с помощью класса **виндовсмикседреалитютилитиес** .

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="windows-xr-plugin"></a>[Windows Подключаемый модуль XR](#tab/xr)

## <a name="windowsmrenvironment"></a>виндовсмренвиронмент

**Пространство имен:** *UnityEngine. XR. виндовсмр*<br>
**Тип:** *виндовсмренвиронмент*

Статический класс **виндовсмренвиронмент** предоставляет доступ к нескольким собственным указателям.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

## <a name="xrdevice"></a>ксрдевице

**Пространство имен:** *UnityEngine. XR*<br>
**Тип:** *ксрдевице*

Тип <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**ксрдевице**</a> позволяет получить доступ к базовым машинным объектам с помощью метода <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">жетнативептр</a> . Возвращаемые Жетнативептр различаются между различными платформами. в универсальная платформа Windows при нацеливании на Windows Mixed Reality ксрдевице. жетнативептр возвращает указатель (IntPtr) в следующую структуру:

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

Его можно преобразовать в Холографикфраменативедата с помощью метода Marshal. PtrToStructure нарушают:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***Ихолографиккамераптр** — это массив IntPtr, упакованный как UnmanagedType. ByValArray с длиной, равной макснумберофкамерас*
