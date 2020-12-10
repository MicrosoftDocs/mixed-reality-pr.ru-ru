---
title: Общий доступ в Unity
description: Совместное использование одних и тех же голограмм между несколькими пользователями в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR — совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, Azure, пространственные привязки Azure, ASA, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 46588f84c39a48e22147d0fc246ceb8d5ee7c47d
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010094"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="7fa51-104">Общий доступ в Unity</span><span class="sxs-lookup"><span data-stu-id="7fa51-104">Shared experiences in Unity</span></span>

<span data-ttu-id="7fa51-105">Общий опыт позволяет нескольким пользователям, каждому из которых присвоено собственное устройство HoloLens, iOS или Android, совместно просматривать и взаимодействовать с одной голограммой.</span><span class="sxs-lookup"><span data-stu-id="7fa51-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="7fa51-106">Голограммы располагаются в фиксированной точке в пространстве посредством общего доступа к пространственной привязке.</span><span class="sxs-lookup"><span data-stu-id="7fa51-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="7fa51-107">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="7fa51-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="7fa51-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a>создают устойчивые облачные якорные привязки, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="7fa51-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="7fa51-109">При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="7fa51-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="7fa51-110">Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> для асинхронного сохранения голограмм на устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="7fa51-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="7fa51-111">При совместном использовании пространственной геодоступной облачной привязки несколько устройств могут отслеживать одну и ту же голограмму с течением времени, даже если эти устройства не присутствуют одновременно.</span><span class="sxs-lookup"><span data-stu-id="7fa51-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="7fa51-112">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="7fa51-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="7fa51-113">После настройки пространственных привязок Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="7fa51-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="7fa51-114">Передача локальных привязок</span><span class="sxs-lookup"><span data-stu-id="7fa51-114">Local anchor transfers</span></span>

<span data-ttu-id="7fa51-115">В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](../../out-of-scope/local-anchor-transfers-in-unity.md) подключения позволяет одному устройству hololens экспортировать привязку, чтобы второй hololens мог его импортировать.</span><span class="sxs-lookup"><span data-stu-id="7fa51-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="7fa51-116">Этот подход не поддерживается на устройствах iOS и Android и обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="7fa51-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7fa51-117">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="7fa51-117">Next Development Checkpoint</span></span>

<span data-ttu-id="7fa51-118">Если вы подготовились к расположению разработки Unity, мы собрались изучить возможности и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7fa51-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="7fa51-119">Отсюда можно перейти к следующему разделу:</span><span class="sxs-lookup"><span data-stu-id="7fa51-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7fa51-120">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="7fa51-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="7fa51-121">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="7fa51-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7fa51-122">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7fa51-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="7fa51-123">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="7fa51-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fa51-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7fa51-124">See also</span></span>
* [<span data-ttu-id="7fa51-125">Общий доступ в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="7fa51-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="7fa51-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="7fa51-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="7fa51-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a></span><span class="sxs-lookup"><span data-stu-id="7fa51-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
