---
title: Настройка визуализации границ
description: Сведения о настройке системы границ в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, система границ,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144494"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="9a4cd-104">Настройка визуализации границ</span><span class="sxs-lookup"><span data-stu-id="9a4cd-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="9a4cd-105">*Профиль визуализации границ* предоставляет параметры для настройки визуального эстетичность и других связанных параметров для системы границ.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="9a4cd-106">Визуализации границ присоединяются к объекту Mixed Reality Плайспаце в сцене и телепортируйтесь с пользователем.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="9a4cd-107">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="9a4cd-107">General settings</span></span>

![Общие параметры визуализации границ](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="9a4cd-109">Высота границы</span><span class="sxs-lookup"><span data-stu-id="9a4cd-109">Boundary height</span></span>

<span data-ttu-id="9a4cd-110">Высота границы обозначает расстояние над плоскостью этажа, на которой должно быть визуализировано пороговое значение границы.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="9a4cd-111">Значение по умолчанию — 3 м.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="9a4cd-112">Параметры этажа</span><span class="sxs-lookup"><span data-stu-id="9a4cd-112">Floor settings</span></span>

![Параметры этажа визуализации границы](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="9a4cd-114">**Показать**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-114">**Show**</span></span>

<span data-ttu-id="9a4cd-115">Указывает, нужно ли создать плоскость этажа и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="9a4cd-116">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-116">The default value is true.</span></span>

<span data-ttu-id="9a4cd-117">**Материал**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-117">**Material**</span></span>

<span data-ttu-id="9a4cd-118">Указывает материал, который следует использовать при создании плоскости этажа.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="9a4cd-119">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-119">**Scale**</span></span>

<span data-ttu-id="9a4cd-120">Указывает размер создаваемой плоскости этажа в метрах.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="9a4cd-121">Масштаб по умолчанию — 3 метра x 3 измерительного квадрата.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="9a4cd-122">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-122">**Physics Layer**</span></span>

<span data-ttu-id="9a4cd-123">Слой, на котором должна быть установлена плоскость этажа.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="9a4cd-124">Значение по умолчанию — уровень *по умолчанию* .</span><span class="sxs-lookup"><span data-stu-id="9a4cd-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="9a4cd-125">Параметры области воспроизведения</span><span class="sxs-lookup"><span data-stu-id="9a4cd-125">Play area settings</span></span>

![Параметры области воспроизведения границы](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="9a4cd-127">**Показать**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-127">**Show**</span></span>

<span data-ttu-id="9a4cd-128">Указывает, создается ли прямоугольник области воспроизведения и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="9a4cd-129">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-129">The default value is true.</span></span>

<span data-ttu-id="9a4cd-130">**Материал**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-130">**Material**</span></span>

<span data-ttu-id="9a4cd-131">Указывает материал, который следует использовать при создании объекта области воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="9a4cd-132">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-132">**Physics Layer**</span></span>

<span data-ttu-id="9a4cd-133">Слой, на котором должна быть установлена область воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="9a4cd-134">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="9a4cd-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="9a4cd-135">Параметры отслеживающей области</span><span class="sxs-lookup"><span data-stu-id="9a4cd-135">Tracked area settings</span></span>

![Параметры отслеживающей области визуализации границ](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="9a4cd-137">**Показать**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-137">**Show**</span></span>

<span data-ttu-id="9a4cd-138">Указывает, создается ли контур области отслеживания и добавляется в сцену.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="9a4cd-139">Значение по умолчанию — true.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-139">The default value is true.</span></span>

<span data-ttu-id="9a4cd-140">**Материал**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-140">**Material**</span></span>

<span data-ttu-id="9a4cd-141">Указывает материал, который следует использовать при создании структуры отслеживающей области.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="9a4cd-142">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-142">**Physics Layer**</span></span>

<span data-ttu-id="9a4cd-143">Слой, в котором должны быть настраивается область с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="9a4cd-144">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="9a4cd-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="9a4cd-145">Параметры стены границ</span><span class="sxs-lookup"><span data-stu-id="9a4cd-145">Boundary wall settings</span></span>

![Параметры стены границы визуализации границы](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="9a4cd-147">**Показать**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-147">**Show**</span></span>

<span data-ttu-id="9a4cd-148">Указывает, должны ли создаваться и добавляться на сцену граничные плоскости.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="9a4cd-149">Значением по умолчанию является false.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-149">The default value is false.</span></span>

<span data-ttu-id="9a4cd-150">**Материал**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-150">**Material**</span></span>

<span data-ttu-id="9a4cd-151">Указывает материал, который следует использовать при создании плоскостей границы.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="9a4cd-152">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-152">**Physics Layer**</span></span>

<span data-ttu-id="9a4cd-153">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="9a4cd-154">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="9a4cd-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="9a4cd-155">Установка компонента границ границы на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="9a4cd-156">Параметры потолка границ</span><span class="sxs-lookup"><span data-stu-id="9a4cd-156">Boundary ceiling settings</span></span>

![Параметры потолка границы визуализации границы](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="9a4cd-158">**Показать**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-158">**Show**</span></span>

<span data-ttu-id="9a4cd-159">Указывает, следует ли создать плоскость границы и добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="9a4cd-160">Значением по умолчанию является false.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-160">The default value is false.</span></span>

<span data-ttu-id="9a4cd-161">**Материал**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-161">**Material**</span></span>

<span data-ttu-id="9a4cd-162">Указывает материал, который следует использовать при создании плоскости граничного потолка.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="9a4cd-163">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="9a4cd-163">**Physics Layer**</span></span>

<span data-ttu-id="9a4cd-164">Слой, на котором должны быть установлены граничные стены.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="9a4cd-165">Значение по умолчанию — « *игнорировать слой райкаст* ».</span><span class="sxs-lookup"><span data-stu-id="9a4cd-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="9a4cd-166">Установка компонента граничного потолка на физический уровень, отличный от *Ignore райкаст* , может препятствовать взаимодействию пользователей с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="9a4cd-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4cd-167">См. также</span><span class="sxs-lookup"><span data-stu-id="9a4cd-167">See also</span></span>

- [<span data-ttu-id="9a4cd-168">Документация по API границ</span><span class="sxs-lookup"><span data-stu-id="9a4cd-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="9a4cd-169">Система границ</span><span class="sxs-lookup"><span data-stu-id="9a4cd-169">Boundary System</span></span>](boundary-system-getting-started.md)
