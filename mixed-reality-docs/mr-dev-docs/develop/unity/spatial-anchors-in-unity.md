---
title: Пространственные привязки в Unity
description: Узнайте, как создавать, хранить и извлекать пространственные привязки в приложениях Unity Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, пространственные привязки, хранилище привязок, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623624"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="e3c73-104">Пространственные привязки в Unity</span><span class="sxs-lookup"><span data-stu-id="e3c73-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="e3c73-105">Пространственные привязки сохраняют голограммы в реальных пространствах между сеансами приложения.</span><span class="sxs-lookup"><span data-stu-id="e3c73-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="e3c73-106">После сохранения в хранилище привязки HoloLens они могут быть найдены и загружены в разные сеансы и являются идеальным вариантом отката при отсутствии подключения к Интернету.</span><span class="sxs-lookup"><span data-stu-id="e3c73-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3c73-107">Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке.</span><span class="sxs-lookup"><span data-stu-id="e3c73-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="e3c73-108">Если вы хотите использовать облачные службы Azure для хранения привязок, мы предоставляем документ, который поможем вам в интеграции [Пространственных привязок Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span><span class="sxs-lookup"><span data-stu-id="e3c73-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="e3c73-109">Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.</span><span class="sxs-lookup"><span data-stu-id="e3c73-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="e3c73-110">Основные сведения о привязках</span><span class="sxs-lookup"><span data-stu-id="e3c73-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="e3c73-111">Использование Анчорсторе</span><span class="sxs-lookup"><span data-stu-id="e3c73-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="e3c73-112">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="e3c73-112">Next Development Checkpoint</span></span>

<span data-ttu-id="e3c73-113">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, то можете изучить стандартные блоки в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e3c73-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="e3c73-114">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="e3c73-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3c73-115">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="e3c73-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="e3c73-116">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="e3c73-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="e3c73-117">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="e3c73-117">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="e3c73-118">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="e3c73-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c73-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e3c73-119">See Also</span></span>
* [<span data-ttu-id="e3c73-120">Сохраняемость пространственной привязки</span><span class="sxs-lookup"><span data-stu-id="e3c73-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="e3c73-121"><a href="/azure/spatial-anchors" target="_blank">Пространственные привязки Azure.</a></span><span class="sxs-lookup"><span data-stu-id="e3c73-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="e3c73-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a></span><span class="sxs-lookup"><span data-stu-id="e3c73-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="e3c73-123">Масштабирование работы</span><span class="sxs-lookup"><span data-stu-id="e3c73-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="e3c73-124">Пространственный этап</span><span class="sxs-lookup"><span data-stu-id="e3c73-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="e3c73-125">Потеря слежения в Unity</span><span class="sxs-lookup"><span data-stu-id="e3c73-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="e3c73-126">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="e3c73-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="e3c73-127">Общий доступ в Unity</span><span class="sxs-lookup"><span data-stu-id="e3c73-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)