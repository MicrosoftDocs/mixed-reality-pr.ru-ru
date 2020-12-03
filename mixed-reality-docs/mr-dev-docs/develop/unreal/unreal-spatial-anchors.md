---
title: Локальные пространственные привязки в Unreal
description: Руководство по применению пространственных привязок в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственные привязки, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 8be1521d44a9dda521c1570d3ac55955e475bc30
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354520"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="ae677-104">Локальные пространственные привязки в Unreal</span><span class="sxs-lookup"><span data-stu-id="ae677-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="ae677-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="ae677-105">Overview</span></span>

<span data-ttu-id="ae677-106">Пространственные привязки используются для размещения в реальных пространствах голограмм, которые сохраняются между сеансами работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="ae677-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="ae677-107">Они предоставляются в Unreal в виде элементов **ARPin** и сохраняются в хранилище привязок HoloLens, которое загружается в последующих сеансах.</span><span class="sxs-lookup"><span data-stu-id="ae677-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="ae677-108">Локальные привязки идеально подходят для тех случаев, когда подключение к Интернету отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ae677-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="ae677-109">Функции объектов из UE 4.25 считаются устаревшими в 4.26. Используйте новые функции.</span><span class="sxs-lookup"><span data-stu-id="ae677-109">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ae677-110">Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке.</span><span class="sxs-lookup"><span data-stu-id="ae677-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="ae677-111">Если вы хотите использовать облачные службы Azure для хранения привязок, мы предоставляем документ, который поможем вам в интеграции [Пространственных привязок Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="ae677-111">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="ae677-112">Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.</span><span class="sxs-lookup"><span data-stu-id="ae677-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="ae677-113">Проверка хранилища привязок</span><span class="sxs-lookup"><span data-stu-id="ae677-113">Checking the anchor store</span></span>

<span data-ttu-id="ae677-114">Перед сохранением или загрузкой привязок обязательно убедитесь, что хранилище привязок подготовлено.</span><span class="sxs-lookup"><span data-stu-id="ae677-114">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="ae677-115">Попытка вызвать любую из функций привязки в HoloLens при неготовности хранилища завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="ae677-115">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="ae677-116">Сохранение привязок</span><span class="sxs-lookup"><span data-stu-id="ae677-116">Saving anchors</span></span>

<span data-ttu-id="ae677-117">Когда в приложении появится компонент, который нужно прикрепить к положению в реальном мире, сохраните его в хранилище привязок с помощью следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="ae677-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="ae677-118">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="ae677-118">Breaking this down:</span></span>
1. <span data-ttu-id="ae677-119">Породите субъект в известном расположении.</span><span class="sxs-lookup"><span data-stu-id="ae677-119">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="ae677-120">Создайте элемент **ARPin** с этим расположением и именем, основанным на классе субъекта.</span><span class="sxs-lookup"><span data-stu-id="ae677-120">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="ae677-121">Добавьте соответствующий субъект в **ARPin** и сохраните полученный элемент в хранилище привязок HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ae677-121">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="ae677-122">Для привязки необходимо выбрать уникальное имя, поэтому в нашем примере к имени добавляется текущая метка времени.</span><span class="sxs-lookup"><span data-stu-id="ae677-122">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="ae677-123">Привязка, успешно сохраненная в хранилище, становится доступной для проверки на портале устройства HoloLens в разделе **System > Map manager > Anchor Files Saved On Device** (Система > Диспетчер карт > Сохраненные на устройстве файлы привязок).</span><span class="sxs-lookup"><span data-stu-id="ae677-123">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="ae677-124">Загрузка привязок</span><span class="sxs-lookup"><span data-stu-id="ae677-124">Loading anchors</span></span>

<span data-ttu-id="ae677-125">При запуске приложения можно вызвать следующую схему, чтобы восстановить все компоненты в местах соответствующих привязок:</span><span class="sxs-lookup"><span data-stu-id="ae677-125">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="ae677-126">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="ae677-126">Breaking this down:</span></span>
1. <span data-ttu-id="ae677-127">Выполните перечисленные ниже шаги для всех привязок в хранилище.</span><span class="sxs-lookup"><span data-stu-id="ae677-127">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="ae677-128">Породите субъект без преобразований.</span><span class="sxs-lookup"><span data-stu-id="ae677-128">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="ae677-129">Прикрепите субъект к элементу **ARPin** из хранилища привязок.</span><span class="sxs-lookup"><span data-stu-id="ae677-129">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="ae677-130">Здесь важно порождать субъект без преобразований, так как привязка отвечает за размещение голограммы в мире в том месте, где она была сохранена.</span><span class="sxs-lookup"><span data-stu-id="ae677-130">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="ae677-131">Любое преобразование на этом этапе добавит к нашей привязке ненужное смещение.</span><span class="sxs-lookup"><span data-stu-id="ae677-131">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="ae677-132">Идентификатор привязки также запрашивается, чтобы мы могли порождать разные субъекты в зависимости от сохраненного имени привязки.</span><span class="sxs-lookup"><span data-stu-id="ae677-132">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="ae677-133">Удаление привязок</span><span class="sxs-lookup"><span data-stu-id="ae677-133">Removing anchors</span></span> 

<span data-ttu-id="ae677-134">Когда вы закончите с привязкой, то можете очистить отдельные привязки или очистить все хранилище привязок с помощью компонентов **Remove ARPin from WMRAnchor Store** (Удаление ARPin из хранилища WMRAnchor) и **Remove All ARPins from WMRAnchor Store** (Удаление всех элементов ARPin из хранилища WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="ae677-134">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="ae677-135">Имейте в виду, что функциональность пространственных привязок находится пока в стадии бета-версии, поэтому стоит возвращаться сюда время от времени за новой информацией.</span><span class="sxs-lookup"><span data-stu-id="ae677-135">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ae677-136">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="ae677-136">Next Development Checkpoint</span></span>

<span data-ttu-id="ae677-137">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="ae677-137">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="ae677-138">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="ae677-138">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae677-139">Пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="ae677-139">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="ae677-140">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="ae677-140">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae677-141">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="ae677-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="ae677-142">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="ae677-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae677-143">См. также статью</span><span class="sxs-lookup"><span data-stu-id="ae677-143">See also</span></span>
* [<span data-ttu-id="ae677-144">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="ae677-144">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="ae677-145">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="ae677-145">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="ae677-146">Системы координат</span><span class="sxs-lookup"><span data-stu-id="ae677-146">Coordinate systems</span></span>](../../design/coordinate-systems.md)
