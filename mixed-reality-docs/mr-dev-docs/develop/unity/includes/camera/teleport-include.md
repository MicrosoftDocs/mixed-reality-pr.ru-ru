---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636374"
---
# <a name="mrtk"></a>[<span data-ttu-id="54284-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="54284-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="54284-102">МРТК предоставляет встроенную [систему телепортироваться](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) , которая автоматически работает во множестве рук и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="54284-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="54284-103">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="54284-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="54284-104">Мы рекомендуем использовать МРТКную реализацию для переноса.</span><span class="sxs-lookup"><span data-stu-id="54284-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="54284-105">Если вы решили не использовать МРТК, Unity предоставляет реализацию телетранспорта в [наборе средств XR для взаимодействия](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="54284-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="54284-106">Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую.</span><span class="sxs-lookup"><span data-stu-id="54284-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="54284-107">Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject.</span><span class="sxs-lookup"><span data-stu-id="54284-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="54284-108">Это эквивалентно Плайспаце МРТК.</span><span class="sxs-lookup"><span data-stu-id="54284-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="54284-109">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="54284-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="54284-110">Мы рекомендуем использовать МРТКную реализацию для переноса.</span><span class="sxs-lookup"><span data-stu-id="54284-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="54284-111">Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую.</span><span class="sxs-lookup"><span data-stu-id="54284-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="54284-112">Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject.</span><span class="sxs-lookup"><span data-stu-id="54284-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="54284-113">Это эквивалентно Плайспаце МРТК.</span><span class="sxs-lookup"><span data-stu-id="54284-113">This is the equivalent of MRTK's Playspace.</span></span>