---
title: Параметры камеры Unity AR
description: Документация по использованию камеры AR в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, AR Camera,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121202"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="5af36-104">Поставщик параметров камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="5af36-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="5af36-105">Поставщик параметров для камеры Unity AR — это экспериментальный компонент МРТК, который позволяет приложениям смешанной реальности работать на устройствах Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="5af36-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="5af36-106">Параметры поставщика параметров камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="5af36-106">Unity AR camera settings provider options</span></span>

![Настройка параметров камеры Unity AR](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="5af36-108">Руководство по добавлению поставщика в сцену: [Настройка мртк для iOS и Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="5af36-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="5af36-109">Параметры отслеживания</span><span class="sxs-lookup"><span data-stu-id="5af36-109">Tracking settings</span></span>

<span data-ttu-id="5af36-110">Поставщик параметров Unity AR Camera позволяет настроить параметры отслеживания.</span><span class="sxs-lookup"><span data-stu-id="5af36-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="5af36-111">Эти параметры относятся к реализации поставщика параметров Unity AR Camera.</span><span class="sxs-lookup"><span data-stu-id="5af36-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="5af36-112">**Источник уничтожения**</span><span class="sxs-lookup"><span data-stu-id="5af36-112">**Pose Source**</span></span>

<span data-ttu-id="5af36-113">Источник «ликвидация» определяет доступные типы дополнений, которые были расширены функцией отслеживания реальность.</span><span class="sxs-lookup"><span data-stu-id="5af36-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="5af36-114">В общем случае эти значения сопоставляются с компонентом устройства, на котором выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="5af36-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="5af36-115">Доступные параметры описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="5af36-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="5af36-116">Параметр</span><span class="sxs-lookup"><span data-stu-id="5af36-116">Option</span></span> | <span data-ttu-id="5af36-117">Описание</span><span class="sxs-lookup"><span data-stu-id="5af36-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5af36-118">Center</span><span class="sxs-lookup"><span data-stu-id="5af36-118">Center</span></span> | <span data-ttu-id="5af36-119">Центр видимости головного подключенного устройства.</span><span class="sxs-lookup"><span data-stu-id="5af36-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="5af36-120">Цветовая Камера</span><span class="sxs-lookup"><span data-stu-id="5af36-120">Color Camera</span></span> | <span data-ttu-id="5af36-121">Цветовая камера мобильного устройства.</span><span class="sxs-lookup"><span data-stu-id="5af36-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="5af36-122">Head</span><span class="sxs-lookup"><span data-stu-id="5af36-122">Head</span></span> | <span data-ttu-id="5af36-123">Головной взгляд на головной подключенный устройство, как правило, немного выше, чем глаз.</span><span class="sxs-lookup"><span data-stu-id="5af36-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="5af36-124">Левый глаз</span><span class="sxs-lookup"><span data-stu-id="5af36-124">Left Eye</span></span> | <span data-ttu-id="5af36-125">Левый взгляд на головной подключенный устройство.</span><span class="sxs-lookup"><span data-stu-id="5af36-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="5af36-126">Слева</span><span class="sxs-lookup"><span data-stu-id="5af36-126">Left Pose</span></span> | <span data-ttu-id="5af36-127">Элемент управления левой стороны контроллера.</span><span class="sxs-lookup"><span data-stu-id="5af36-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="5af36-128">Правильный взгляд</span><span class="sxs-lookup"><span data-stu-id="5af36-128">Right Eye</span></span> | <span data-ttu-id="5af36-129">Правильный взгляд на головной подключенный устройство.</span><span class="sxs-lookup"><span data-stu-id="5af36-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="5af36-130">Правая</span><span class="sxs-lookup"><span data-stu-id="5af36-130">Right Pose</span></span> | <span data-ttu-id="5af36-131">Объект с правой стороны контроллера.</span><span class="sxs-lookup"><span data-stu-id="5af36-131">The right hand controller pose.</span></span> |

<span data-ttu-id="5af36-132">Значением по умолчанию для источника «ликвидация» является **цветовая Камера**, чтобы обеспечить прозрачное отображение на мобильных устройствах, таких как телефон или планшет.</span><span class="sxs-lookup"><span data-stu-id="5af36-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="5af36-133">**Тип отслеживания**</span><span class="sxs-lookup"><span data-stu-id="5af36-133">**Tracking Type**</span></span>

<span data-ttu-id="5af36-134">Тип отслеживания определяет части объекта, которые будут использоваться для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="5af36-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="5af36-135">Доступные параметры описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="5af36-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="5af36-136">Параметр</span><span class="sxs-lookup"><span data-stu-id="5af36-136">Option</span></span> | <span data-ttu-id="5af36-137">Описание</span><span class="sxs-lookup"><span data-stu-id="5af36-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5af36-138">Положение</span><span class="sxs-lookup"><span data-stu-id="5af36-138">Position</span></span> | <span data-ttu-id="5af36-139">Расположение устройства.</span><span class="sxs-lookup"><span data-stu-id="5af36-139">The position of the device.</span></span> |
| <span data-ttu-id="5af36-140">Поворот</span><span class="sxs-lookup"><span data-stu-id="5af36-140">Rotation</span></span> | <span data-ttu-id="5af36-141">Поворот устройства.</span><span class="sxs-lookup"><span data-stu-id="5af36-141">The rotation of the device.</span></span> |
| <span data-ttu-id="5af36-142">Поворот и позиционирование</span><span class="sxs-lookup"><span data-stu-id="5af36-142">Rotation And Position</span></span> | <span data-ttu-id="5af36-143">Расположение и поворот устройства.</span><span class="sxs-lookup"><span data-stu-id="5af36-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="5af36-144">Значение по умолчанию для типа отслеживания — **поворот и размещение**, чтобы обеспечить наиболее широкие возможности отслеживания.</span><span class="sxs-lookup"><span data-stu-id="5af36-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="5af36-145">**Тип обновления**</span><span class="sxs-lookup"><span data-stu-id="5af36-145">**Update Type**</span></span>

<span data-ttu-id="5af36-146">Тип обновления определяет, на каких точках во время обработки кадров будут выдаваться данные о выборке.</span><span class="sxs-lookup"><span data-stu-id="5af36-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="5af36-147">Доступные параметры описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="5af36-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="5af36-148">Параметр</span><span class="sxs-lookup"><span data-stu-id="5af36-148">Option</span></span> | <span data-ttu-id="5af36-149">Описание</span><span class="sxs-lookup"><span data-stu-id="5af36-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5af36-150">Перед отрисовкой</span><span class="sxs-lookup"><span data-stu-id="5af36-150">Before Render</span></span> | <span data-ttu-id="5af36-151">Непосредственно перед отрисовкой.</span><span class="sxs-lookup"><span data-stu-id="5af36-151">Just before rendering.</span></span> |
| <span data-ttu-id="5af36-152">Update</span><span class="sxs-lookup"><span data-stu-id="5af36-152">Update</span></span> | <span data-ttu-id="5af36-153">На этапе обновления рамки.</span><span class="sxs-lookup"><span data-stu-id="5af36-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="5af36-154">Обновление и подготовка к просмотру</span><span class="sxs-lookup"><span data-stu-id="5af36-154">Update And Before Render</span></span> | <span data-ttu-id="5af36-155">На этапе обновления и непосредственно перед отрисовкой.</span><span class="sxs-lookup"><span data-stu-id="5af36-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="5af36-156">Значение по умолчанию для типа отслеживания — **Update и перед отрисовкой**, чтобы обеспечить наименьшую задержку отслеживания.</span><span class="sxs-lookup"><span data-stu-id="5af36-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="5af36-157">См. также</span><span class="sxs-lookup"><span data-stu-id="5af36-157">See also</span></span>

- [<span data-ttu-id="5af36-158">Обзор системы поддержки камер</span><span class="sxs-lookup"><span data-stu-id="5af36-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="5af36-159">Создание поставщика параметров камеры</span><span class="sxs-lookup"><span data-stu-id="5af36-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
