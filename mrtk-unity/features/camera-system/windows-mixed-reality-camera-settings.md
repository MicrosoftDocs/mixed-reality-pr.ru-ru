---
title: Параметры камеры Windows Mixed Reality
description: Документация по использованию параметров камеры Windows Mixed Reality в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, Камера,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121642"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="4345d-104">Поставщик параметров камеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4345d-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="4345d-105">Поставщик параметров камеры Windows Mixed Reality определяет тип устройства, на котором выполняется приложение, и применяет соответствующие параметры конфигурации, основанные на отображении (прозрачном или непрозрачном).</span><span class="sxs-lookup"><span data-stu-id="4345d-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="4345d-106">Включение поставщика параметров камеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4345d-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="4345d-107">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="4345d-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="4345d-108">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="4345d-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="4345d-109">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="4345d-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="4345d-111">Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="4345d-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Разверните узел Параметры поставщики.](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="4345d-113">Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="4345d-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Развернуть поставщик новых параметров](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="4345d-115">Выберите поставщик параметров камеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4345d-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Выберите поставщик параметров Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="4345d-117">При использовании профилей Microsoft Mixed Reality Toolkit по умолчанию поставщик параметров камеры Windows Mixed Reality уже будет включен и настроен.</span><span class="sxs-lookup"><span data-stu-id="4345d-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="4345d-118">Настройка поставщика параметров камеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4345d-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="4345d-119">Параметры камеры Windows Mixed Reality также поддерживают профиль.</span><span class="sxs-lookup"><span data-stu-id="4345d-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="4345d-120">Этот профиль предоставляет следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="4345d-120">This profile provides the following options:</span></span>

![Конфигурация параметров камеры Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="4345d-122">Отображение записи смешанной реальности из фото-или видеокамеры</span><span class="sxs-lookup"><span data-stu-id="4345d-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="4345d-123">С помощью этого параметра в HoloLens 2 можно включить выравнивание голограмм в записи смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4345d-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="4345d-124">Если этот параметр включен, платформа предоставит дополнительные Холографиккамера для приложения при создании фотографии или видео с записью смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4345d-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="4345d-125">Этот Холографиккамера предоставляет матрицы представлений, соответствующие расположению фотографии или видеокамеры, и предоставляет матрицы проекции с помощью поля "Фото-видеокамера" представления.</span><span class="sxs-lookup"><span data-stu-id="4345d-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="4345d-126">Это обеспечит, чтобы голограммы, такие как сетки, оставались видимыми в выводе видео.</span><span class="sxs-lookup"><span data-stu-id="4345d-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="4345d-127">Метод репроекта HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4345d-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="4345d-128">Задает начальный метод для РЕПРОЕКЦИИ HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4345d-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="4345d-129">По умолчанию рекомендуется использовать репроект глубины, так как все части сцены будут независимо изменяться в зависимости от расстояния от пользователя.</span><span class="sxs-lookup"><span data-stu-id="4345d-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="4345d-130">Если голограммы по-прежнему отображаются нестабильно, попробуйте убедиться, что все объекты правильно отправили свою глубину в буфер глубины.</span><span class="sxs-lookup"><span data-stu-id="4345d-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="4345d-131">Иногда это параметр шейдера.</span><span class="sxs-lookup"><span data-stu-id="4345d-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="4345d-132">Если глубина будет правильно отправлена, а нестабильность все еще присутствует, попробуйте использовать стабилизации, который использует буфер глубины для вычисления плоскости стабилизации.</span><span class="sxs-lookup"><span data-stu-id="4345d-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="4345d-133">Если приложению не удается отправить достаточное количество данных глубины для использования одним из этих вариантов, в качестве резерва предоставляется плоская ревариантная репроецирование.</span><span class="sxs-lookup"><span data-stu-id="4345d-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="4345d-134">Этот метод будет основан на предоставленных приложением данных фокусной точки через [сетфокуспоинтфорфраме](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span><span class="sxs-lookup"><span data-stu-id="4345d-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="4345d-135">Чтобы обновить метод РЕПРОЕКЦИИ во время выполнения, `WindowsMixedRealityReprojectionUpdater` выполните следующий доступ:</span><span class="sxs-lookup"><span data-stu-id="4345d-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="4345d-136">Это необходимо обновить только один раз, а значение повторно используется для всех последующих кадров.</span><span class="sxs-lookup"><span data-stu-id="4345d-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="4345d-137">Если метод будет обновляться часто, рекомендуется кэшировать результат, `EnsureComponent` а не вызывать его часто.</span><span class="sxs-lookup"><span data-stu-id="4345d-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="4345d-138">См. также</span><span class="sxs-lookup"><span data-stu-id="4345d-138">See also</span></span>

- [<span data-ttu-id="4345d-139">Обзор системы поддержки камер</span><span class="sxs-lookup"><span data-stu-id="4345d-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="4345d-140">Создание поставщика параметров камеры</span><span class="sxs-lookup"><span data-stu-id="4345d-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="4345d-141">Визуализация записи смешанной реальности с камеры PV</span><span class="sxs-lookup"><span data-stu-id="4345d-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="4345d-142">Holographic, репроектное</span><span class="sxs-lookup"><span data-stu-id="4345d-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)