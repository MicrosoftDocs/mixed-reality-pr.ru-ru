---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748496"
---
# <a name="mrtk"></a>[<span data-ttu-id="db7ea-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="db7ea-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="db7ea-102">МРТК будет автоматически выполнять определенные настройки камеры в зависимости от [конфигурации в профиле системы камеры](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="db7ea-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="db7ea-103">**Пространство имен:** *Microsoft. микседреалити. Toolkit. камерасистем*</span><span class="sxs-lookup"><span data-stu-id="db7ea-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="db7ea-104">**Тип:** *микседреалитикамерасистем*</span><span class="sxs-lookup"><span data-stu-id="db7ea-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="db7ea-105">Чтобы проверить непрозрачность камеры, система Микседреалитикамера имеет [ `IsOpaque` свойство](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="db7ea-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="db7ea-106">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="db7ea-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="db7ea-107">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="db7ea-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="db7ea-108">**Тип:** *ксрдисплайсубсистем*</span><span class="sxs-lookup"><span data-stu-id="db7ea-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="db7ea-109">Вы можете использовать код скрипта, чтобы определить во время выполнения, является ли гарнитура впечатляющим или holographic, проверив [дисплайопакуе](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) на активном [ксрдисплайсубсистем](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="db7ea-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="db7ea-110">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="db7ea-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="db7ea-111">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="db7ea-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="db7ea-112">**Тип:** *холографиксеттингс*</span><span class="sxs-lookup"><span data-stu-id="db7ea-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="db7ea-113">Вы можете использовать код скрипта, чтобы определить во время выполнения, является ли гарнитура увлекательной или holographic, проверив [холографиксеттингс. исдисплайопакуе](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="db7ea-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>