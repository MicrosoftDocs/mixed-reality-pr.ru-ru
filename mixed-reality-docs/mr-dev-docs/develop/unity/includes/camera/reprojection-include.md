---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636362"
---
# <a name="mrtk"></a>[<span data-ttu-id="7161c-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="7161c-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7161c-102">МРТК в настоящее время не имеет вспомогательных функций для режима РЕПРОЕКЦИИ.</span><span class="sxs-lookup"><span data-stu-id="7161c-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="7161c-103">Дополнительные сведения см. на одной из других вкладок.</span><span class="sxs-lookup"><span data-stu-id="7161c-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="7161c-104">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="7161c-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7161c-105">Режим перепроекции можно настроить, задав для [ксрдисплайсубсистем. репрожектионмоде](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="7161c-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="7161c-106">Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [репрожектионмоде. ориентатиононли](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="7161c-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="7161c-107">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="7161c-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7161c-108">Режим перепроекции можно настроить, задав для [холографиксеттингс. репрожектионмоде](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="7161c-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="7161c-109">Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [холографикрепрожектионмоде. ориентатиононли](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="7161c-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>