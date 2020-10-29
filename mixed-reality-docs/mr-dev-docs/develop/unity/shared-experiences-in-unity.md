---
title: Общий доступ в Unity
description: Совместное использование одних и тех же голограмм между несколькими пользователями в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, Azure, пространственные привязки Azure, ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691964"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="2075b-104">Общий доступ в Unity</span><span class="sxs-lookup"><span data-stu-id="2075b-104">Shared experiences in Unity</span></span>

<span data-ttu-id="2075b-105">Совместный опыт — это один из нескольких пользователей, каждый из которых имеет собственное устройство HoloLens, iOS или Android, совместное представление и взаимодействие с одной голограммой, которая находится в фиксированном месте.</span><span class="sxs-lookup"><span data-stu-id="2075b-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="2075b-106">Это достигается благодаря совместному использованию пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="2075b-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="2075b-107">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="2075b-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="2075b-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания устойчивых облачных пространственных привязок, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="2075b-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2075b-109">При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="2075b-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="2075b-110">Это позволяет обмениваться опытом в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="2075b-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="2075b-111"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно также использовать для сохранения асинхронной голограммы на устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="2075b-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2075b-112">Благодаря совместному использованию надежной облачной пространственной привязки несколько устройств могут наблюдать одну и ту же постоянную голограмму с течением времени, даже если они находятся в разное время в разных местах.</span><span class="sxs-lookup"><span data-stu-id="2075b-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="2075b-113">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="2075b-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2075b-114">После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2075b-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="2075b-115">Передача локальных привязок</span><span class="sxs-lookup"><span data-stu-id="2075b-115">Local anchor transfers</span></span>

<span data-ttu-id="2075b-116">В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](../../out-of-scope/local-anchor-transfers-in-unity.md) подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.</span><span class="sxs-lookup"><span data-stu-id="2075b-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="2075b-117">Обратите внимание, что этот подход обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure, а устройства iOS и Android не поддерживаются этим подходом.</span><span class="sxs-lookup"><span data-stu-id="2075b-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2075b-118">Контрольная точка следующей разработки</span><span class="sxs-lookup"><span data-stu-id="2075b-118">Next Development Checkpoint</span></span>

<span data-ttu-id="2075b-119">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="2075b-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2075b-120">Отсюда можно перейти к следующему разделу:</span><span class="sxs-lookup"><span data-stu-id="2075b-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2075b-121">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="2075b-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="2075b-122">Или непосредственно перейти к развертыванию приложения на устройстве или в эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="2075b-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2075b-123">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2075b-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="2075b-124">Вы всегда можете вернуться к [контрольным точкам разработки Unity](unity-development-overview.md#3-platform-capabilities-and-apis) в любое время.</span><span class="sxs-lookup"><span data-stu-id="2075b-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2075b-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2075b-125">See also</span></span>
* [<span data-ttu-id="2075b-126">Общий доступ в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="2075b-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="2075b-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="2075b-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2075b-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a></span><span class="sxs-lookup"><span data-stu-id="2075b-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>