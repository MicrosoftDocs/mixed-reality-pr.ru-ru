---
title: Локальные пространственные привязки в Unreal
description: Сведения о том, как использовать, сохранять пространственные привязки в приложениях смешанной реальности Unreal, а также как управлять ими.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственные привязки, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98009984"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="89477-104">Локальные пространственные привязки в Unreal</span><span class="sxs-lookup"><span data-stu-id="89477-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="89477-105">Пространственные привязки позволяют размещать в реальных пространствах голограммы, которые сохраняются между сеансами работы с приложением как **ARPin**.</span><span class="sxs-lookup"><span data-stu-id="89477-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="89477-106">После сохранения в хранилище привязок HoloLens ARPin можно загрузить в будущие сеансы. Это идеальный вариант отката при отсутствии подключения к Интернету.</span><span class="sxs-lookup"><span data-stu-id="89477-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="89477-107">Функции объектов из UE 4.25 считаются устаревшими в 4.26. Используйте новые функции.</span><span class="sxs-lookup"><span data-stu-id="89477-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="89477-108">Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке.</span><span class="sxs-lookup"><span data-stu-id="89477-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="89477-109">Если вы хотите использовать облачные службы Azure для хранения привязок, мы предоставляем документ, который поможем вам в интеграции [Пространственных привязок Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="89477-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="89477-110">Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.</span><span class="sxs-lookup"><span data-stu-id="89477-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="89477-111">Проверка хранилища привязок</span><span class="sxs-lookup"><span data-stu-id="89477-111">Checking the anchor store</span></span>

<span data-ttu-id="89477-112">Перед сохранением или загрузкой привязок обязательно убедитесь, что хранилище привязок подготовлено.</span><span class="sxs-lookup"><span data-stu-id="89477-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="89477-113">Попытка вызвать любую из функций привязки в HoloLens при неготовности хранилища завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="89477-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="89477-114">Сохранение привязок</span><span class="sxs-lookup"><span data-stu-id="89477-114">Saving anchors</span></span>

<span data-ttu-id="89477-115">Когда в приложении появится компонент, который вам нужно будет прикрепить к положению в реальном мире, сохраните его в хранилище привязок с помощью следующей последовательности:</span><span class="sxs-lookup"><span data-stu-id="89477-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="89477-116">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="89477-116">Breaking this down:</span></span>
1. <span data-ttu-id="89477-117">Породите субъект в известном расположении.</span><span class="sxs-lookup"><span data-stu-id="89477-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="89477-118">Создайте элемент **ARPin** с этим расположением и именем, основанным на классе субъекта.</span><span class="sxs-lookup"><span data-stu-id="89477-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="89477-119">Добавьте соответствующий субъект в **ARPin** и сохраните полученный элемент в хранилище привязок HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89477-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="89477-120">Для привязки необходимо выбрать уникальное имя, поэтому в нашем примере к имени добавляется текущая метка времени.</span><span class="sxs-lookup"><span data-stu-id="89477-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="89477-121">Привязка, успешно сохраненная в хранилище, отображается на портале устройства HoloLens в разделе **System > Map manager > Anchor Files Saved On Device** (Система > Диспетчер карт > Сохраненные на устройстве файлы привязок).</span><span class="sxs-lookup"><span data-stu-id="89477-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="89477-122">Загрузка привязок</span><span class="sxs-lookup"><span data-stu-id="89477-122">Loading anchors</span></span>

<span data-ttu-id="89477-123">При запуске приложения можно вызвать следующую схему, чтобы восстановить все компоненты в местах соответствующих привязок:</span><span class="sxs-lookup"><span data-stu-id="89477-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="89477-124">Порядок действий:</span><span class="sxs-lookup"><span data-stu-id="89477-124">Breaking this down:</span></span>
1. <span data-ttu-id="89477-125">Выполните перечисленные ниже шаги для всех привязок в хранилище.</span><span class="sxs-lookup"><span data-stu-id="89477-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="89477-126">Породите субъект без преобразований.</span><span class="sxs-lookup"><span data-stu-id="89477-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="89477-127">Прикрепите субъект к элементу **ARPin** из хранилища привязок.</span><span class="sxs-lookup"><span data-stu-id="89477-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="89477-128">Здесь важно порождать субъект без преобразований, так как привязка отвечает за размещение голограммы в мире в том месте, где она была сохранена.</span><span class="sxs-lookup"><span data-stu-id="89477-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="89477-129">Любое преобразование на этом этапе добавит к нашей привязке ненужное смещение.</span><span class="sxs-lookup"><span data-stu-id="89477-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="89477-130">Идентификатор привязки также запрашивается, чтобы мы могли порождать разные субъекты в зависимости от сохраненного имени привязки.</span><span class="sxs-lookup"><span data-stu-id="89477-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="89477-131">Удаление привязок</span><span class="sxs-lookup"><span data-stu-id="89477-131">Removing anchors</span></span> 

<span data-ttu-id="89477-132">Когда вы закончите с привязкой, то можете очистить отдельные привязки или очистить все хранилище привязок с помощью компонентов **Remove ARPin from WMRAnchor Store** (Удаление ARPin из хранилища WMRAnchor) и **Remove All ARPins from WMRAnchor Store** (Удаление всех элементов ARPin из хранилища WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="89477-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="89477-133">Имейте в виду, что функциональность пространственных привязок находится пока в стадии бета-версии, поэтому стоит возвращаться сюда время от времени за новой информацией.</span><span class="sxs-lookup"><span data-stu-id="89477-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="89477-134">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="89477-134">Next Development Checkpoint</span></span>

<span data-ttu-id="89477-135">Если вы следуете изложенным нами инструкциям по разработке для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="89477-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="89477-136">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="89477-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="89477-137">Пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="89477-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="89477-138">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="89477-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="89477-139">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="89477-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="89477-140">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="89477-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="89477-141">См. также статью</span><span class="sxs-lookup"><span data-stu-id="89477-141">See also</span></span>

* [<span data-ttu-id="89477-142">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="89477-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="89477-143">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="89477-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="89477-144">Системы координат</span><span class="sxs-lookup"><span data-stu-id="89477-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
