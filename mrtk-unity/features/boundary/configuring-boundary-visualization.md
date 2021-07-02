---
title: Настройка визуализации границ
description: Сведения о настройке системы границ в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, система границ,
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177092"
---
# <a name="configuring-boundary-visualization"></a><span data-ttu-id="f143d-104">Настройка визуализации границ</span><span class="sxs-lookup"><span data-stu-id="f143d-104">Configuring boundary visualization</span></span>

<span data-ttu-id="f143d-105">*Профиль визуализации границ* предоставляет параметры для настройки визуального эстетичность и других связанных параметров для системы границ.</span><span class="sxs-lookup"><span data-stu-id="f143d-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="f143d-106">Визуализации границ присоединяются к объекту Mixed Reality Плайспаце в сцене и телепортируйтесь с пользователем.</span><span class="sxs-lookup"><span data-stu-id="f143d-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="f143d-107">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="f143d-107">General settings</span></span>

![общие Параметры визуализации границ](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="f143d-109">Высота границы</span><span class="sxs-lookup"><span data-stu-id="f143d-109">Boundary height</span></span>

<span data-ttu-id="f143d-110">Высота границы обозначает расстояние над плоскостью этажа, на которой должно быть визуализировано пороговое значение границы.</span><span class="sxs-lookup"><span data-stu-id="f143d-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="f143d-111">Значение по умолчанию — 3 м.</span><span class="sxs-lookup"><span data-stu-id="f143d-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="f143d-112">Параметры этажа</span><span class="sxs-lookup"><span data-stu-id="f143d-112">Floor settings</span></span>

![Параметры этажа визуализации границы](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="f143d-114">**Показать**</span><span class="sxs-lookup"><span data-stu-id="f143d-114">**Show**</span></span>

<span data-ttu-id="f143d-115">Указывает, нужно ли создать плоскость этажа и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="f143d-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="f143d-116">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="f143d-116">The default value is true.</span></span>

<span data-ttu-id="f143d-117">**Материал**</span><span class="sxs-lookup"><span data-stu-id="f143d-117">**Material**</span></span>

<span data-ttu-id="f143d-118">Указывает материал, который следует использовать при создании плоскости этажа.</span><span class="sxs-lookup"><span data-stu-id="f143d-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="f143d-119">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="f143d-119">**Scale**</span></span>

<span data-ttu-id="f143d-120">Указывает размер создаваемой плоскости этажа в метрах.</span><span class="sxs-lookup"><span data-stu-id="f143d-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="f143d-121">Масштаб по умолчанию — 3 метра x 3 измерительного квадрата.</span><span class="sxs-lookup"><span data-stu-id="f143d-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="f143d-122">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="f143d-122">**Physics Layer**</span></span>

<span data-ttu-id="f143d-123">Слой, на котором должна быть установлена плоскость этажа.</span><span class="sxs-lookup"><span data-stu-id="f143d-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="f143d-124">Значение по умолчанию — уровень *по умолчанию* .</span><span class="sxs-lookup"><span data-stu-id="f143d-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="f143d-125">Параметры области воспроизведения</span><span class="sxs-lookup"><span data-stu-id="f143d-125">Play area settings</span></span>

![Параметры области визуализации границы](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="f143d-127">**Показать**</span><span class="sxs-lookup"><span data-stu-id="f143d-127">**Show**</span></span>

<span data-ttu-id="f143d-128">Указывает, создается ли прямоугольник области воспроизведения и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="f143d-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="f143d-129">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="f143d-129">The default value is true.</span></span>

<span data-ttu-id="f143d-130">**Материал**</span><span class="sxs-lookup"><span data-stu-id="f143d-130">**Material**</span></span>

<span data-ttu-id="f143d-131">Указывает материал, который следует использовать при создании объекта области воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="f143d-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="f143d-132">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="f143d-132">**Physics Layer**</span></span>

<span data-ttu-id="f143d-133">Слой, на котором должна быть установлена область воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="f143d-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="f143d-134">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="f143d-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="f143d-135">Параметры отслеживающей области</span><span class="sxs-lookup"><span data-stu-id="f143d-135">Tracked area settings</span></span>

![Параметры области с отслеживанием границ](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="f143d-137">**Показать**</span><span class="sxs-lookup"><span data-stu-id="f143d-137">**Show**</span></span>

<span data-ttu-id="f143d-138">Указывает, создается ли контур области отслеживания и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="f143d-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="f143d-139">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="f143d-139">The default value is true.</span></span>

<span data-ttu-id="f143d-140">**Материал**</span><span class="sxs-lookup"><span data-stu-id="f143d-140">**Material**</span></span>

<span data-ttu-id="f143d-141">Указывает материал, который следует использовать при создании структуры отслеживающей области.</span><span class="sxs-lookup"><span data-stu-id="f143d-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="f143d-142">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="f143d-142">**Physics Layer**</span></span>

<span data-ttu-id="f143d-143">Слой, в котором должны быть настраивается область с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="f143d-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="f143d-144">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="f143d-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="f143d-145">Параметры стены границ</span><span class="sxs-lookup"><span data-stu-id="f143d-145">Boundary wall settings</span></span>

![Параметры стены границы визуализации границы](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="f143d-147">**Показать**</span><span class="sxs-lookup"><span data-stu-id="f143d-147">**Show**</span></span>

<span data-ttu-id="f143d-148">Указывает, должны ли создаваться и добавляться на сцену граничные плоскости.</span><span class="sxs-lookup"><span data-stu-id="f143d-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="f143d-149">Значение по умолчанию — false.</span><span class="sxs-lookup"><span data-stu-id="f143d-149">The default value is false.</span></span>

<span data-ttu-id="f143d-150">**Материал**</span><span class="sxs-lookup"><span data-stu-id="f143d-150">**Material**</span></span>

<span data-ttu-id="f143d-151">Указывает материал, который следует использовать при создании плоскостей границы.</span><span class="sxs-lookup"><span data-stu-id="f143d-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="f143d-152">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="f143d-152">**Physics Layer**</span></span>

<span data-ttu-id="f143d-153">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="f143d-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="f143d-154">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="f143d-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="f143d-155">Установка компонента границ границы на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="f143d-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="f143d-156">Параметры потолка границ</span><span class="sxs-lookup"><span data-stu-id="f143d-156">Boundary ceiling settings</span></span>

![Параметры границы визуализации границы](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="f143d-158">**Показать**</span><span class="sxs-lookup"><span data-stu-id="f143d-158">**Show**</span></span>

<span data-ttu-id="f143d-159">Указывает, следует ли создать плоскость границы и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="f143d-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="f143d-160">Значение по умолчанию — false.</span><span class="sxs-lookup"><span data-stu-id="f143d-160">The default value is false.</span></span>

<span data-ttu-id="f143d-161">**Материал**</span><span class="sxs-lookup"><span data-stu-id="f143d-161">**Material**</span></span>

<span data-ttu-id="f143d-162">Указывает материал, который следует использовать при создании плоскости граничного потолка.</span><span class="sxs-lookup"><span data-stu-id="f143d-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="f143d-163">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="f143d-163">**Physics Layer**</span></span>

<span data-ttu-id="f143d-164">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="f143d-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="f143d-165">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="f143d-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="f143d-166">Установка компонента граничного потолка на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="f143d-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="f143d-167">См. также:</span><span class="sxs-lookup"><span data-stu-id="f143d-167">See also</span></span>

- [<span data-ttu-id="f143d-168">Документация по API границ</span><span class="sxs-lookup"><span data-stu-id="f143d-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="f143d-169">Система границ</span><span class="sxs-lookup"><span data-stu-id="f143d-169">Boundary System</span></span>](boundary-system-getting-started.md)
