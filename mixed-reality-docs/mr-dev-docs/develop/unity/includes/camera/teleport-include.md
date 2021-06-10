---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748487"
---
# <a name="mrtk"></a>[<span data-ttu-id="a652b-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="a652b-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="a652b-102">МРТК предоставляет встроенную [систему телепортироваться](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) , которая автоматически работает во множестве рук и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="a652b-102">MRTK provides an in-box [teleport system](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="a652b-103">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="a652b-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="a652b-104">Мы рекомендуем использовать МРТКную реализацию для переноса.</span><span class="sxs-lookup"><span data-stu-id="a652b-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="a652b-105">Если вы решили не использовать МРТК, Unity предоставляет реализацию телетранспорта в [наборе средств XR для взаимодействия](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="a652b-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="a652b-106">Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую.</span><span class="sxs-lookup"><span data-stu-id="a652b-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="a652b-107">Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject.</span><span class="sxs-lookup"><span data-stu-id="a652b-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="a652b-108">Это эквивалентно Плайспаце МРТК.</span><span class="sxs-lookup"><span data-stu-id="a652b-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="a652b-109">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="a652b-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="a652b-110">Мы рекомендуем использовать МРТКную реализацию для переноса.</span><span class="sxs-lookup"><span data-stu-id="a652b-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="a652b-111">Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую.</span><span class="sxs-lookup"><span data-stu-id="a652b-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="a652b-112">Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject.</span><span class="sxs-lookup"><span data-stu-id="a652b-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="a652b-113">Это эквивалентно Плайспаце МРТК.</span><span class="sxs-lookup"><span data-stu-id="a652b-113">This is the equivalent of MRTK's Playspace.</span></span>