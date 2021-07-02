---
title: Обзор системы камеры
description: Целевая страница для системы камеры в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, камера,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177039"
---
# <a name="camera-system-overview"></a><span data-ttu-id="d3b70-104">Обзор системы камеры</span><span class="sxs-lookup"><span data-stu-id="d3b70-104">Camera system overview</span></span>

<span data-ttu-id="d3b70-105">система камеры позволяет набор средств Microsoft Mixed reality настраивать и оптимизировать камеру приложения для использования в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d3b70-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="d3b70-106">используя систему камеры, приложения можно писать для поддержки как непрозрачных (например, виртуальных реальность), так и прозрачных (Microsoft HoloLens) устройств без необходимости написания кода для различения и размещения каждого типа дисплея.</span><span class="sxs-lookup"><span data-stu-id="d3b70-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="d3b70-107">Включение системы камеры</span><span class="sxs-lookup"><span data-stu-id="d3b70-107">Enabling the camera system</span></span>

<span data-ttu-id="d3b70-108">Системой камеры управляет объект Микседреалититулкит (или другой компонент регистратора служб).</span><span class="sxs-lookup"><span data-stu-id="d3b70-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="d3b70-109">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="d3b70-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="d3b70-110">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="d3b70-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="d3b70-111">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="d3b70-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="d3b70-113">Перейдите на панель инспектора к разделу система камеры и убедитесь, что установлен флажок **включить систему камеры** .</span><span class="sxs-lookup"><span data-stu-id="d3b70-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Включение системы камеры](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="d3b70-115">Выберите реализацию системы камеры.</span><span class="sxs-lookup"><span data-stu-id="d3b70-115">Select the camera system implementation.</span></span> <span data-ttu-id="d3b70-116">Реализацией класса по умолчанию, предоставляемой МРТК, является `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="d3b70-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Выбор реализации системы камеры](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="d3b70-118">Выберите профиль требуемой конфигурации</span><span class="sxs-lookup"><span data-stu-id="d3b70-118">Select the desired configuration profile</span></span>

    ![Выбор профиля системы камеры](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="d3b70-120">Настройка системы камеры</span><span class="sxs-lookup"><span data-stu-id="d3b70-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="d3b70-121">поставщики Параметры</span><span class="sxs-lookup"><span data-stu-id="d3b70-121">Settings providers</span></span>

![поставщики Параметры камеры](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="d3b70-123">Поставщики параметров камеры позволяют настроить конфигурацию камеры для конкретной платформы.</span><span class="sxs-lookup"><span data-stu-id="d3b70-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="d3b70-124">Эти параметры могут включать настраиваемые этапы настройки и (или) компоненты.</span><span class="sxs-lookup"><span data-stu-id="d3b70-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="d3b70-125">поставщики можно добавить, нажав кнопку **добавить камеру Параметры поставщика** .</span><span class="sxs-lookup"><span data-stu-id="d3b70-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="d3b70-126">Их можно удалить, нажав **-** кнопку справа от имени поставщика.</span><span class="sxs-lookup"><span data-stu-id="d3b70-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="d3b70-127">Не для всех платформ потребуется поставщик параметров камеры.</span><span class="sxs-lookup"><span data-stu-id="d3b70-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="d3b70-128">если нет поставщиков, совместимых с платформой, на которой выполняется приложение, то набор средств Microsoft Mixed Reality будет применять базовые значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d3b70-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="d3b70-129">Параметры отображения</span><span class="sxs-lookup"><span data-stu-id="d3b70-129">Display settings</span></span>

![Параметры дисплея камеры](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="d3b70-131">параметры отображения указываются как для непрозрачных (например, для виртуальной реальности), так и для прозрачных (например: Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="d3b70-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="d3b70-132">При использовании этих параметров Камера настраивается во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d3b70-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="d3b70-133">**Близкий клип**</span><span class="sxs-lookup"><span data-stu-id="d3b70-133">**Near Clip**</span></span>

<span data-ttu-id="d3b70-134">Ближайшая плоскость обрезки — это ближайший, в метрах, виртуальный объект, который может быть на камере и по-прежнему подготовлен к просмотру.</span><span class="sxs-lookup"><span data-stu-id="d3b70-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="d3b70-135">Для наибольшего удобства пользователей рекомендуется сделать это значение больше нуля.</span><span class="sxs-lookup"><span data-stu-id="d3b70-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="d3b70-136">Предыдущий образ содержит значения, которые должны быть удобны на различных устройствах.</span><span class="sxs-lookup"><span data-stu-id="d3b70-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="d3b70-137">**Клип FAR**</span><span class="sxs-lookup"><span data-stu-id="d3b70-137">**Far Clip**</span></span>

<span data-ttu-id="d3b70-138">Далеко плоскость обрезки — это самый дальнеий, в метрах, что виртуальный объект может быть на камере и по-прежнему подготовлен к просмотру.</span><span class="sxs-lookup"><span data-stu-id="d3b70-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="d3b70-139">Для прозрачных устройств рекомендуется, чтобы это значение было относительно близко, а не превышать реальное пространство и приостанавливать иммерсивное качество приложения.</span><span class="sxs-lookup"><span data-stu-id="d3b70-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="d3b70-140">**Снять флаги**</span><span class="sxs-lookup"><span data-stu-id="d3b70-140">**Clear Flags**</span></span>

<span data-ttu-id="d3b70-141">Значение Clear flags показывает, как изображение будет очищено при его прорисовке.</span><span class="sxs-lookup"><span data-stu-id="d3b70-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="d3b70-142">Для возможностей виртуальной реальности это значение чаще всего устанавливается в Скибокс.</span><span class="sxs-lookup"><span data-stu-id="d3b70-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="d3b70-143">Для прозрачных экранов рекомендуется задать для этого параметра значение Color.</span><span class="sxs-lookup"><span data-stu-id="d3b70-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="d3b70-144">**Цвет фона**</span><span class="sxs-lookup"><span data-stu-id="d3b70-144">**Background Color**</span></span>

<span data-ttu-id="d3b70-145">Если для флагов Clear не задано значение Скибокс, будет отображаться свойство цвет фона.</span><span class="sxs-lookup"><span data-stu-id="d3b70-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="d3b70-146">**качество Параметры**</span><span class="sxs-lookup"><span data-stu-id="d3b70-146">**Quality Settings**</span></span>

<span data-ttu-id="d3b70-147">Значение параметров качества указывает качество графики, которое Unity должно использовать при отрисовке сцены.</span><span class="sxs-lookup"><span data-stu-id="d3b70-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="d3b70-148">Уровень качества является параметром уровня проекта и не относится к одной камере.</span><span class="sxs-lookup"><span data-stu-id="d3b70-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="d3b70-149">Дополнительные сведения см. в статье о [контроле качества](https://docs.unity3d.com/Manual/class-QualitySettings.html) в документации Unity.</span><span class="sxs-lookup"><span data-stu-id="d3b70-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3b70-150">См. также:</span><span class="sxs-lookup"><span data-stu-id="d3b70-150">See also</span></span>

- [<span data-ttu-id="d3b70-151">Документация по API системы камеры</span><span class="sxs-lookup"><span data-stu-id="d3b70-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="d3b70-152">создание поставщика Параметры камеры</span><span class="sxs-lookup"><span data-stu-id="d3b70-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
