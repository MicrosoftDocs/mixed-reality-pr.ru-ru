---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475082"
---
# <a name="mrtk"></a>[<span data-ttu-id="2b060-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="2b060-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="2b060-102">виндовсмикседреалитютилитиес</span><span class="sxs-lookup"><span data-stu-id="2b060-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="2b060-103">**Пространство имен:** *Microsoft. микседреалити. Toolkit. виндовсмикседреалити*</span><span class="sxs-lookup"><span data-stu-id="2b060-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="2b060-104">**Тип:** *виндовсмикседреалитютилитиес*</span><span class="sxs-lookup"><span data-stu-id="2b060-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="2b060-105">МРТК предоставляет уже Упакованные типы как в устаревших пакетах WSA, так и в пакете SDK XR с помощью класса **виндовсмикседреалитютилитиес** .</span><span class="sxs-lookup"><span data-stu-id="2b060-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="2b060-106">ПАКЕТ SDK ДЛЯ XR</span><span class="sxs-lookup"><span data-stu-id="2b060-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="2b060-107">виндовсмренвиронмент</span><span class="sxs-lookup"><span data-stu-id="2b060-107">WindowsMREnvironment</span></span>

<span data-ttu-id="2b060-108">**Пространство имен:** *UnityEngine. XR. виндовсмр*</span><span class="sxs-lookup"><span data-stu-id="2b060-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="2b060-109">**Тип:** *виндовсмренвиронмент*</span><span class="sxs-lookup"><span data-stu-id="2b060-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="2b060-110">Статический класс **виндовсмренвиронмент** предоставляет доступ к нескольким собственным указателям.</span><span class="sxs-lookup"><span data-stu-id="2b060-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="2b060-111">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="2b060-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="2b060-112">ксрдевице</span><span class="sxs-lookup"><span data-stu-id="2b060-112">XRDevice</span></span>

<span data-ttu-id="2b060-113">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="2b060-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2b060-114">**Тип:** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="2b060-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="2b060-115">Тип <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**ксрдевице**</a> позволяет получить доступ к базовым машинным объектам с помощью метода <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">жетнативептр</a> .</span><span class="sxs-lookup"><span data-stu-id="2b060-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="2b060-116">Возвращаемые Жетнативептр различаются между различными платформами.</span><span class="sxs-lookup"><span data-stu-id="2b060-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="2b060-117">На универсальная платформа Windows при нацеливании на Windows Mixed Reality функция Ксрдевице. Жетнативептр возвращает указатель (IntPtr) в следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="2b060-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

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

<span data-ttu-id="2b060-118">Его можно преобразовать в Холографикфраменативедата с помощью метода Marshal. PtrToStructure нарушают:</span><span class="sxs-lookup"><span data-stu-id="2b060-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="2b060-119">***Ихолографиккамераптр** — это массив IntPtr, упакованный как UnmanagedType. ByValArray с длиной, равной макснумберофкамерас*</span><span class="sxs-lookup"><span data-stu-id="2b060-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
