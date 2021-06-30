---
title: Настройка визуализации границ
description: Сведения о настройке системы границ в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, система границ,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121252"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="8df2c-104">Настройка визуализации границ</span><span class="sxs-lookup"><span data-stu-id="8df2c-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="8df2c-105">*Профиль визуализации границ* предоставляет параметры для настройки визуального эстетичность и других связанных параметров для системы границ.</span><span class="sxs-lookup"><span data-stu-id="8df2c-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="8df2c-106">Визуализации границ присоединяются к объекту Mixed Reality Плайспаце в сцене и телепортируйтесь с пользователем.</span><span class="sxs-lookup"><span data-stu-id="8df2c-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="8df2c-107">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="8df2c-107">General settings</span></span>

![Общие параметры визуализации границ](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="8df2c-109">Высота границы</span><span class="sxs-lookup"><span data-stu-id="8df2c-109">Boundary height</span></span>

<span data-ttu-id="8df2c-110">Высота границы обозначает расстояние над плоскостью этажа, на которой должно быть визуализировано пороговое значение границы.</span><span class="sxs-lookup"><span data-stu-id="8df2c-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="8df2c-111">Значение по умолчанию — 3 м.</span><span class="sxs-lookup"><span data-stu-id="8df2c-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="8df2c-112">Параметры этажа</span><span class="sxs-lookup"><span data-stu-id="8df2c-112">Floor settings</span></span>

![Параметры этажа визуализации границы](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="8df2c-114">**Показать**</span><span class="sxs-lookup"><span data-stu-id="8df2c-114">**Show**</span></span>

<span data-ttu-id="8df2c-115">Указывает, нужно ли создать плоскость этажа и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="8df2c-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="8df2c-116">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="8df2c-116">The default value is true.</span></span>

<span data-ttu-id="8df2c-117">**Материал**</span><span class="sxs-lookup"><span data-stu-id="8df2c-117">**Material**</span></span>

<span data-ttu-id="8df2c-118">Указывает материал, который следует использовать при создании плоскости этажа.</span><span class="sxs-lookup"><span data-stu-id="8df2c-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="8df2c-119">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="8df2c-119">**Scale**</span></span>

<span data-ttu-id="8df2c-120">Указывает размер создаваемой плоскости этажа в метрах.</span><span class="sxs-lookup"><span data-stu-id="8df2c-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="8df2c-121">Масштаб по умолчанию — 3 метра x 3 измерительного квадрата.</span><span class="sxs-lookup"><span data-stu-id="8df2c-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="8df2c-122">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="8df2c-122">**Physics Layer**</span></span>

<span data-ttu-id="8df2c-123">Слой, на котором должна быть установлена плоскость этажа.</span><span class="sxs-lookup"><span data-stu-id="8df2c-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="8df2c-124">Значение по умолчанию — уровень *по умолчанию* .</span><span class="sxs-lookup"><span data-stu-id="8df2c-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="8df2c-125">Параметры области воспроизведения</span><span class="sxs-lookup"><span data-stu-id="8df2c-125">Play area settings</span></span>

![Параметры области воспроизведения границы](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="8df2c-127">**Показать**</span><span class="sxs-lookup"><span data-stu-id="8df2c-127">**Show**</span></span>

<span data-ttu-id="8df2c-128">Указывает, создается ли прямоугольник области воспроизведения и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="8df2c-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="8df2c-129">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="8df2c-129">The default value is true.</span></span>

<span data-ttu-id="8df2c-130">**Материал**</span><span class="sxs-lookup"><span data-stu-id="8df2c-130">**Material**</span></span>

<span data-ttu-id="8df2c-131">Указывает материал, который следует использовать при создании объекта области воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="8df2c-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="8df2c-132">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="8df2c-132">**Physics Layer**</span></span>

<span data-ttu-id="8df2c-133">Слой, на котором должна быть установлена область воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="8df2c-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="8df2c-134">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="8df2c-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="8df2c-135">Параметры отслеживающей области</span><span class="sxs-lookup"><span data-stu-id="8df2c-135">Tracked area settings</span></span>

![Параметры отслеживающей области визуализации границ](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="8df2c-137">**Показать**</span><span class="sxs-lookup"><span data-stu-id="8df2c-137">**Show**</span></span>

<span data-ttu-id="8df2c-138">Указывает, создается ли контур области отслеживания и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="8df2c-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="8df2c-139">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="8df2c-139">The default value is true.</span></span>

<span data-ttu-id="8df2c-140">**Материал**</span><span class="sxs-lookup"><span data-stu-id="8df2c-140">**Material**</span></span>

<span data-ttu-id="8df2c-141">Указывает материал, который следует использовать при создании структуры отслеживающей области.</span><span class="sxs-lookup"><span data-stu-id="8df2c-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="8df2c-142">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="8df2c-142">**Physics Layer**</span></span>

<span data-ttu-id="8df2c-143">Слой, в котором должны быть настраивается область с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="8df2c-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="8df2c-144">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="8df2c-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="8df2c-145">Параметры стены границ</span><span class="sxs-lookup"><span data-stu-id="8df2c-145">Boundary wall settings</span></span>

![Параметры стены границы визуализации границы](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="8df2c-147">**Показать**</span><span class="sxs-lookup"><span data-stu-id="8df2c-147">**Show**</span></span>

<span data-ttu-id="8df2c-148">Указывает, должны ли создаваться и добавляться на сцену граничные плоскости.</span><span class="sxs-lookup"><span data-stu-id="8df2c-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="8df2c-149">Значение по умолчанию — false.</span><span class="sxs-lookup"><span data-stu-id="8df2c-149">The default value is false.</span></span>

<span data-ttu-id="8df2c-150">**Материал**</span><span class="sxs-lookup"><span data-stu-id="8df2c-150">**Material**</span></span>

<span data-ttu-id="8df2c-151">Указывает материал, который следует использовать при создании плоскостей границы.</span><span class="sxs-lookup"><span data-stu-id="8df2c-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="8df2c-152">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="8df2c-152">**Physics Layer**</span></span>

<span data-ttu-id="8df2c-153">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="8df2c-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="8df2c-154">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="8df2c-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="8df2c-155">Установка компонента границ границы на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="8df2c-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="8df2c-156">Параметры потолка границ</span><span class="sxs-lookup"><span data-stu-id="8df2c-156">Boundary ceiling settings</span></span>

![Параметры потолка границы визуализации границы](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="8df2c-158">**Показать**</span><span class="sxs-lookup"><span data-stu-id="8df2c-158">**Show**</span></span>

<span data-ttu-id="8df2c-159">Указывает, следует ли создать плоскость границы и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="8df2c-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="8df2c-160">Значение по умолчанию — false.</span><span class="sxs-lookup"><span data-stu-id="8df2c-160">The default value is false.</span></span>

<span data-ttu-id="8df2c-161">**Материал**</span><span class="sxs-lookup"><span data-stu-id="8df2c-161">**Material**</span></span>

<span data-ttu-id="8df2c-162">Указывает материал, который следует использовать при создании плоскости граничного потолка.</span><span class="sxs-lookup"><span data-stu-id="8df2c-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="8df2c-163">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="8df2c-163">**Physics Layer**</span></span>

<span data-ttu-id="8df2c-164">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="8df2c-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="8df2c-165">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="8df2c-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="8df2c-166">Установка компонента граничного потолка на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="8df2c-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="8df2c-167">См. также</span><span class="sxs-lookup"><span data-stu-id="8df2c-167">See also</span></span>

- [<span data-ttu-id="8df2c-168">Документация по API границ</span><span class="sxs-lookup"><span data-stu-id="8df2c-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="8df2c-169">Система границ</span><span class="sxs-lookup"><span data-stu-id="8df2c-169">Boundary System</span></span>](boundary-system-getting-started.md)
