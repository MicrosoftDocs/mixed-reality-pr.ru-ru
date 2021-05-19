---
title: Руководство по настройке смешанной реальности
description: Документация по настройке МРТК в Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143575"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="aadeb-104">Рекомендации по настройке профиля набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aadeb-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Логотип МРТК](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="aadeb-106">Набор средств для смешанной реальности централизует как можно больше конфигурации, необходимой для управления набором средств (за исключением истинной среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="aadeb-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="aadeb-107">Это простое пошаговое руководство для каждого экрана профиля конфигурации, доступного для набора средств.</span><span class="sxs-lookup"><span data-stu-id="aadeb-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="aadeb-108">Основной профиль конфигурации набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="aadeb-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="aadeb-109">Главный профиль конфигурации, присоединенный к *микседреалититулкит* GameObject в сцене, предоставляет главную точку входа для набора инструментов в проекте.</span><span class="sxs-lookup"><span data-stu-id="aadeb-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="aadeb-110">Набор средств Mixed Reality "блокирует" экраны конфигурации по умолчанию, чтобы гарантировать, что у вас всегда есть общая начальная точка для проекта, и рекомендуется приступить к определению собственных параметров по мере развития проекта.</span><span class="sxs-lookup"><span data-stu-id="aadeb-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="aadeb-111">Конфигурация МРТК не редактируется в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="aadeb-111">The MRTK configuration is not editable during play-mode.</span></span>

![Профиль конфигурации МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="aadeb-113">Все профили "по умолчанию" для набора средств Mixed Reality можно найти в проекте SDK в папке Assets/МРТК/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="aadeb-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aadeb-114">DefaultHoloLens2ConfigurationProfile оптимизирован для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aadeb-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="aadeb-115">Дополнительные сведения см. в разделе [Профили](../features/profiles/profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="aadeb-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="aadeb-116">При открытии главного профиля конфигурации набора средств для смешанной реальности в инспекторе отображается следующий экран:</span><span class="sxs-lookup"><span data-stu-id="aadeb-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="aadeb-117">Если вы выберете ресурс Микседреалититулкитконфигуратионпрофиле без Микседреалититулкит в сцене, то запросите, хотите ли вы, чтобы МРТК автоматически настроить сцену.</span><span class="sxs-lookup"><span data-stu-id="aadeb-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="aadeb-118">Это необязательно, однако в сцене должен быть активный объект Микседреалититулкит для доступа ко всем экранам конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aadeb-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="aadeb-119">Он содержит текущую активную конфигурацию среды выполнения для проекта.</span><span class="sxs-lookup"><span data-stu-id="aadeb-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="aadeb-120">Здесь можно переходить ко всем профилям конфигурации для МРТК, включая:</span><span class="sxs-lookup"><span data-stu-id="aadeb-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="aadeb-121">Рекомендации по настройке профиля набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aadeb-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="aadeb-122">Основной профиль конфигурации набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="aadeb-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="aadeb-123">Параметры работы</span><span class="sxs-lookup"><span data-stu-id="aadeb-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="aadeb-124">Параметры камеры</span><span class="sxs-lookup"><span data-stu-id="aadeb-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="aadeb-125">Параметры системы ввода</span><span class="sxs-lookup"><span data-stu-id="aadeb-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="aadeb-126">Параметры визуализации границ</span><span class="sxs-lookup"><span data-stu-id="aadeb-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="aadeb-127">Выбор системы для пропорций</span><span class="sxs-lookup"><span data-stu-id="aadeb-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="aadeb-128">Параметры пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="aadeb-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="aadeb-129">Параметры диагностики</span><span class="sxs-lookup"><span data-stu-id="aadeb-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="aadeb-130">Параметры системы сцены</span><span class="sxs-lookup"><span data-stu-id="aadeb-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="aadeb-131">Дополнительные параметры служб</span><span class="sxs-lookup"><span data-stu-id="aadeb-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="aadeb-132">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="aadeb-133">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="aadeb-134">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="aadeb-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="aadeb-135">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="aadeb-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="aadeb-136">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="aadeb-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="aadeb-137">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="aadeb-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="aadeb-138">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="aadeb-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="aadeb-139">Служебные программы редактора</span><span class="sxs-lookup"><span data-stu-id="aadeb-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="aadeb-140">Инспекторы служб</span><span class="sxs-lookup"><span data-stu-id="aadeb-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="aadeb-141">Модуль подготовки буфера глубины</span><span class="sxs-lookup"><span data-stu-id="aadeb-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="aadeb-142">Изменение профилей во время выполнения</span><span class="sxs-lookup"><span data-stu-id="aadeb-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="aadeb-143">Параметр профиля инициализации pre МРТК</span><span class="sxs-lookup"><span data-stu-id="aadeb-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="aadeb-144">Переключатель активного профиля</span><span class="sxs-lookup"><span data-stu-id="aadeb-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="aadeb-145">См. также:</span><span class="sxs-lookup"><span data-stu-id="aadeb-145">See also</span></span>](#see-also)

<span data-ttu-id="aadeb-146">Эти профили конфигурации описаны ниже в соответствующих разделах.</span><span class="sxs-lookup"><span data-stu-id="aadeb-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="aadeb-147">Параметры работы</span><span class="sxs-lookup"><span data-stu-id="aadeb-147">Experience settings</span></span>

<span data-ttu-id="aadeb-148">Этот параметр, расположенный на главной странице конфигурации набора средств смешанной реальности, определяет операцию по умолчанию для [масштаба среды Mixed Reality](/windows/mixed-reality/coordinate-systems-in-unity) для проекта.</span><span class="sxs-lookup"><span data-stu-id="aadeb-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="aadeb-149">Параметры камеры</span><span class="sxs-lookup"><span data-stu-id="aadeb-149">Camera settings</span></span>

<span data-ttu-id="aadeb-150">Параметры камеры определяют, как будет настроена камера для проекта смешанной реальности, определяя общие параметры обрезки, качества и прозрачности.</span><span class="sxs-lookup"><span data-stu-id="aadeb-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="aadeb-151">Параметры системы ввода</span><span class="sxs-lookup"><span data-stu-id="aadeb-151">Input system settings</span></span>

<span data-ttu-id="aadeb-152">Проект Mixed Reality предоставляет надежную и хорошо обученную входную систему для маршрутизации всех событий ввода вокруг проекта, выбранного по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aadeb-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="aadeb-153">За входной системой, предоставляемой МРТК, относятся несколько других систем, которые помогают управлять сложными взаимными настройками, необходимыми для абстракции сложностей многоплатформенных и смешанных сред.</span><span class="sxs-lookup"><span data-stu-id="aadeb-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="aadeb-154">Каждый из отдельных профилей описан ниже.</span><span class="sxs-lookup"><span data-stu-id="aadeb-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="aadeb-155">Параметры фокуса</span><span class="sxs-lookup"><span data-stu-id="aadeb-155">Focus Settings</span></span>
- [<span data-ttu-id="aadeb-156">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="aadeb-157">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="aadeb-158">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="aadeb-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="aadeb-159">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="aadeb-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="aadeb-160">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="aadeb-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="aadeb-161">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="aadeb-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="aadeb-162">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="aadeb-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="aadeb-163">Параметры визуализации границ</span><span class="sxs-lookup"><span data-stu-id="aadeb-163">Boundary visualization settings</span></span>

<span data-ttu-id="aadeb-164">Система границ преобразует воспринимаемую границу, сообщаемую базовой системой границ и системы защиты платформ.</span><span class="sxs-lookup"><span data-stu-id="aadeb-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="aadeb-165">Конфигурация визуализатора границы дает возможность автоматически отображать записанную границу в сцене относительно положения пользователя. Граница также будет реагировать на изменения и обновляться в зависимости от того, где находятся телепорты пользователя в сцене.</span><span class="sxs-lookup"><span data-stu-id="aadeb-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="aadeb-166">Выбор системы для пропорций</span><span class="sxs-lookup"><span data-stu-id="aadeb-166">Teleportation system selection</span></span>

<span data-ttu-id="aadeb-167">Проект Mixed Reality предоставляет полнофункциональную систему для управления событиями передачи в проекте, которая выбрана по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aadeb-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="aadeb-168">Параметры пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="aadeb-168">Spatial awareness settings</span></span>

<span data-ttu-id="aadeb-169">Проект Mixed Reality предоставляет перестроенную систему пространственной информации для работы с системами пространственного сканирования в проекте, выбранном по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aadeb-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="aadeb-170">Конфигурация пространственной осведомленности в наборе средств Mixed Reality позволяет настраивать способ запуска системы, независимо от того, запускается ли она автоматически при запуске приложения или более поздней версии, а также при установке экстентов для поля представления.</span><span class="sxs-lookup"><span data-stu-id="aadeb-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="aadeb-171">Кроме того, она позволяет настроить параметры сетки и зоны, а также настраивать то, как проект понимает среду.</span><span class="sxs-lookup"><span data-stu-id="aadeb-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="aadeb-172">Это применимо только к устройствам, которые могут предоставлять сканированную среду.</span><span class="sxs-lookup"><span data-stu-id="aadeb-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="aadeb-173">Параметры диагностики</span><span class="sxs-lookup"><span data-stu-id="aadeb-173">Diagnostics settings</span></span>

<span data-ttu-id="aadeb-174">Необязательная, но очень полезная функция МРТК — это функция диагностики подключаемого модуля.</span><span class="sxs-lookup"><span data-stu-id="aadeb-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="aadeb-175">Профиль диагностики предоставляет несколько простых систем для наблюдения за выполнением проекта, включая удобный переключатель вкл./выкл. для включения и отключения панели отображения в сцене.</span><span class="sxs-lookup"><span data-stu-id="aadeb-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="aadeb-176">Параметры системы сцены</span><span class="sxs-lookup"><span data-stu-id="aadeb-176">Scene system settings</span></span>

<span data-ttu-id="aadeb-177">МРТК предоставляет эту необязательную службу, которая помогает управлять сложной загрузкой и выгрузке сложных вспомогательных сцен.</span><span class="sxs-lookup"><span data-stu-id="aadeb-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="aadeb-178">Чтобы решить, подходит ли система сцен для вашего проекта, ознакомьтесь с [руководством по начало работыию сцены.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="aadeb-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="aadeb-179">Дополнительные параметры служб</span><span class="sxs-lookup"><span data-stu-id="aadeb-179">Additional services settings</span></span>

<span data-ttu-id="aadeb-180">Одной из более сложных областей набора средств Mixed Reality является реализация [шаблона локатора служб](https://en.wikipedia.org/wiki/Service_locator_pattern) , которая позволяет зарегистрировать любую "службу" в инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="aadeb-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="aadeb-181">Это позволяет легко расширять платформу с помощью новых функций и систем, но также позволяет проектам использовать эти возможности для регистрации собственных компонентов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="aadeb-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="aadeb-182">Любая зарегистрированная служба по-прежнему получает все преимущества всех событий Unity без издержек и затрат на реализацию одноэлементных шаблонов неуклюжим.</span><span class="sxs-lookup"><span data-stu-id="aadeb-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="aadeb-183">Это позволяет выполнять чисто компоненты C# без издержек на сцены для выполнения фоновых и задних процессов, например порождение систем, логика игры среды выполнения или практически любые другие.</span><span class="sxs-lookup"><span data-stu-id="aadeb-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="aadeb-184">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-184">Input actions settings</span></span>

<span data-ttu-id="aadeb-185">Входные действия предоставляют способ абстрактного взаимодействия с любыми физическими взаимодействиями и входными данными из проекта среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="aadeb-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="aadeb-186">Все физические входные данные (от контроллеров, руки и мыши/т. д.) преобразуются в логические действия ввода для использования в проекте среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="aadeb-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="aadeb-187">Это гарантирует неважность, откуда поступают входные данные. проект просто реализует эти действия в фоновом режиме в виде «вещей» или «взаимодействие с».</span><span class="sxs-lookup"><span data-stu-id="aadeb-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="aadeb-188">Чтобы создать новое действие ввода, просто нажмите кнопку "добавить новое действие" и введите понятное текстовое имя для того, что оно представляет.</span><span class="sxs-lookup"><span data-stu-id="aadeb-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="aadeb-189">Затем нужно выбрать только ось (тип данных), которую должно передать действие, или, в случае физического контроллера, физический тип входных данных, к которому можно присоединиться, например:</span><span class="sxs-lookup"><span data-stu-id="aadeb-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="aadeb-190">Ограничение оси</span><span class="sxs-lookup"><span data-stu-id="aadeb-190">Axis Constraint</span></span> | <span data-ttu-id="aadeb-191">Тип данных</span><span class="sxs-lookup"><span data-stu-id="aadeb-191">Data Type</span></span> | <span data-ttu-id="aadeb-192">Описание</span><span class="sxs-lookup"><span data-stu-id="aadeb-192">Description</span></span> | <span data-ttu-id="aadeb-193">Пример использования</span><span class="sxs-lookup"><span data-stu-id="aadeb-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="aadeb-194">None</span><span class="sxs-lookup"><span data-stu-id="aadeb-194">None</span></span> | <span data-ttu-id="aadeb-195">Нет данных</span><span class="sxs-lookup"><span data-stu-id="aadeb-195">No data</span></span> | <span data-ttu-id="aadeb-196">Используется для пустого действия или события</span><span class="sxs-lookup"><span data-stu-id="aadeb-196">Used for an empty action or event</span></span> | <span data-ttu-id="aadeb-197">Триггер события</span><span class="sxs-lookup"><span data-stu-id="aadeb-197">Event Trigger</span></span> |
| <span data-ttu-id="aadeb-198">Необработанный (зарезервированный)</span><span class="sxs-lookup"><span data-stu-id="aadeb-198">Raw (reserved)</span></span> | <span data-ttu-id="aadeb-199">object</span><span class="sxs-lookup"><span data-stu-id="aadeb-199">object</span></span> | <span data-ttu-id="aadeb-200">Зарезервировано для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="aadeb-200">Reserved for future use</span></span> | <span data-ttu-id="aadeb-201">Недоступно</span><span class="sxs-lookup"><span data-stu-id="aadeb-201">N/A</span></span> |
| <span data-ttu-id="aadeb-202">Цифровой</span><span class="sxs-lookup"><span data-stu-id="aadeb-202">Digital</span></span> | <span data-ttu-id="aadeb-203">bool</span><span class="sxs-lookup"><span data-stu-id="aadeb-203">bool</span></span> | <span data-ttu-id="aadeb-204">Логическое значение ON или Off типа Data</span><span class="sxs-lookup"><span data-stu-id="aadeb-204">A boolean on or off type data</span></span> | <span data-ttu-id="aadeb-205">Кнопка контроллера</span><span class="sxs-lookup"><span data-stu-id="aadeb-205">A controller button</span></span> |
| <span data-ttu-id="aadeb-206">Одна ось</span><span class="sxs-lookup"><span data-stu-id="aadeb-206">Single Axis</span></span> | <span data-ttu-id="aadeb-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="aadeb-207">float</span></span> | <span data-ttu-id="aadeb-208">Одно значение данных точности</span><span class="sxs-lookup"><span data-stu-id="aadeb-208">A single precision data value</span></span> | <span data-ttu-id="aadeb-209">Входной диапазон, например триггер</span><span class="sxs-lookup"><span data-stu-id="aadeb-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="aadeb-210">Двойная ось</span><span class="sxs-lookup"><span data-stu-id="aadeb-210">Dual Axis</span></span> | <span data-ttu-id="aadeb-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="aadeb-211">Vector2</span></span> | <span data-ttu-id="aadeb-212">Тип данных Dual float для нескольких осей</span><span class="sxs-lookup"><span data-stu-id="aadeb-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="aadeb-213">Dpad или аналоговый стик</span><span class="sxs-lookup"><span data-stu-id="aadeb-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="aadeb-214">3 ДОФ</span><span class="sxs-lookup"><span data-stu-id="aadeb-214">Three Dof Position</span></span> | <span data-ttu-id="aadeb-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="aadeb-215">Vector3</span></span> | <span data-ttu-id="aadeb-216">Данные о позиционированном типе из с 3 осью с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="aadeb-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="aadeb-217">Контроллер только с трехмерным положением</span><span class="sxs-lookup"><span data-stu-id="aadeb-217">3D position style only controller</span></span> |
| <span data-ttu-id="aadeb-218">Тройной поворот ДОФ</span><span class="sxs-lookup"><span data-stu-id="aadeb-218">Three Dof Rotation</span></span> | <span data-ttu-id="aadeb-219">Quaternion</span><span class="sxs-lookup"><span data-stu-id="aadeb-219">Quaternion</span></span> | <span data-ttu-id="aadeb-220">Только поворот входных данных с 4 осью с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="aadeb-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="aadeb-221">Контроллер в стиле с тремя степенями, например контроллер Окулус Go</span><span class="sxs-lookup"><span data-stu-id="aadeb-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="aadeb-222">Шесть ДОФ</span><span class="sxs-lookup"><span data-stu-id="aadeb-222">Six Dof</span></span> | <span data-ttu-id="aadeb-223">"Смешанная реальность" (Vector3, кватернион)</span><span class="sxs-lookup"><span data-stu-id="aadeb-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="aadeb-224">Входные данные в стиле расположения и поворота с помощью компонентов Vector3 и кватернион</span><span class="sxs-lookup"><span data-stu-id="aadeb-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="aadeb-225">Контроллер или указатель движения</span><span class="sxs-lookup"><span data-stu-id="aadeb-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="aadeb-226">События, использующие входные действия, не ограничиваются физическими контроллерами и могут по-прежнему использоваться в проекте для того, чтобы эффекты среды выполнения создавали новые действия.</span><span class="sxs-lookup"><span data-stu-id="aadeb-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="aadeb-227">Входные действия — это один из нескольких компонентов, которые нельзя изменять во время выполнения, они являются только конфигурацией времени разработки.</span><span class="sxs-lookup"><span data-stu-id="aadeb-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="aadeb-228">Этот профиль не следует переключать в силу того, что проект работает из-за зависимости платформы (и ваших проектов) от идентификатора, созданного для каждого действия.</span><span class="sxs-lookup"><span data-stu-id="aadeb-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="aadeb-229">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="aadeb-229">Input actions rules</span></span>

<span data-ttu-id="aadeb-230">Правила входных действий предоставляют способ автоматического преобразования события, вызванного одним входным действием, в различные действия на основе его значения данных.</span><span class="sxs-lookup"><span data-stu-id="aadeb-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="aadeb-231">Они легко управляются в рамках платформы и не вызывают никаких затрат на производительность.</span><span class="sxs-lookup"><span data-stu-id="aadeb-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="aadeb-232">Например, преобразование одного входного события двойной оси из DPad в в 4 соответствующие действия «Dpad up»/«DPad Down»/«Dpad Left»/«Dpad Right» (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="aadeb-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="aadeb-233">Это также можно сделать в собственном коде.</span><span class="sxs-lookup"><span data-stu-id="aadeb-233">This could also be done in your own code.</span></span> <span data-ttu-id="aadeb-234">Однако, так как это был очень распространенный шаблон, платформа предоставляет механизм для выполнения этой задачи «не из этого».</span><span class="sxs-lookup"><span data-stu-id="aadeb-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="aadeb-235">Правила входных действий можно настроить для любой доступной входной оси.</span><span class="sxs-lookup"><span data-stu-id="aadeb-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="aadeb-236">Однако действия ввода из одного типа оси можно перевести в другое Входное действие того же типа оси.</span><span class="sxs-lookup"><span data-stu-id="aadeb-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="aadeb-237">Действие двойной оси можно связать с другим действием двойной оси, но не с цифровым действием или без него.</span><span class="sxs-lookup"><span data-stu-id="aadeb-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Профиль правил входных действий](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="aadeb-239">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="aadeb-239">Pointer configuration</span></span>

<span data-ttu-id="aadeb-240">Указатели используются для взаимодействия в сцене на любом устройстве ввода, предоставляя направление и проверку нажатия для любого объекта в сцене (с присоединенным объектом или компонентом пользовательского интерфейса).</span><span class="sxs-lookup"><span data-stu-id="aadeb-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="aadeb-241">Указатели по умолчанию автоматически настраиваются для контроллеров, гарнитур (взгляд/Focus) и ввод с клавиатуры и сенсорного ввода.</span><span class="sxs-lookup"><span data-stu-id="aadeb-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="aadeb-242">Указатели можно также выработать в активной сцене с помощью одного из многих компонентов строк, предоставляемых набором средств Mixed Reality, или любого собственного компонента, если они реализуют интерфейс МРТК Имикседреалитипоинтер.</span><span class="sxs-lookup"><span data-stu-id="aadeb-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="aadeb-243">Геообъектная область: определяет глобальную указывающую экстент для всех указателей, включая взгляд.</span><span class="sxs-lookup"><span data-stu-id="aadeb-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="aadeb-244">Райкаст Layer Маскируетs: определяет, для каких слоев указатели будут райкаст.</span><span class="sxs-lookup"><span data-stu-id="aadeb-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="aadeb-245">Отладка направленных вниз отрисованных лучей: вспомогательный модуль отладки для визуализации луча, используемых для райкастинг.</span><span class="sxs-lookup"><span data-stu-id="aadeb-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="aadeb-246">Отладка рисуемых отлучающих лучей цветов: набор цветов, используемых для визуализации.</span><span class="sxs-lookup"><span data-stu-id="aadeb-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="aadeb-247">Взгляните на курсор Prefab: позволяет легко указать глобальный курсор взгляда для любой сцены.</span><span class="sxs-lookup"><span data-stu-id="aadeb-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="aadeb-248">Есть дополнительная вспомогательная кнопка, позволяющая быстро перейти к поставщику взгляда, чтобы переопределить некоторые конкретные значения для взгляда при необходимости.</span><span class="sxs-lookup"><span data-stu-id="aadeb-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="aadeb-249">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="aadeb-249">Gestures configuration</span></span>

<span data-ttu-id="aadeb-250">Жесты — это специальная реализация системы, позволяющая назначать входные действия различным входным методам "жеста", предоставляемым различными пакетами SDK (например, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="aadeb-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="aadeb-251">Текущая реализация жестов предназначена только для HoloLens и будет улучшена для других систем, так как они будут добавлены в набор средств в будущем (пока нет дат).</span><span class="sxs-lookup"><span data-stu-id="aadeb-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="aadeb-252">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="aadeb-252">Speech commands</span></span>

<span data-ttu-id="aadeb-253">Как и жесты, некоторые платформы среды выполнения также предоставляют интеллектуальные функции "речь — текст" с возможностью создания команд, которые могут быть получены проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="aadeb-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="aadeb-254">Этот профиль конфигурации позволяет настроить следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="aadeb-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="aadeb-255">Общие параметры. для параметра "поведение при запуске" задайте значение "автоматический запуск" или "запуск вручную". определяет, следует ли инициализировать Кэйвордрекогнизер при запуске системы ввода или разрешить проекту решать, когда инициализировать Кэйвордрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="aadeb-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="aadeb-256">"Уровень достоверности распознавания" используется для инициализации [API Кэйвордрекогнизер](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="aadeb-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="aadeb-257">Речевые команды — регистрируют слова и переводит их в для ввода действий, которые могут быть получены проектом.</span><span class="sxs-lookup"><span data-stu-id="aadeb-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="aadeb-258">Они также могут быть присоединены к действиям клавиатуры, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="aadeb-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aadeb-259">В настоящее время система поддерживает только распознавание речи при работе на платформах Windows 10, например HoloLens и Windows 10 Desktop, и будет улучшена для других систем, так как они будут добавлены в МРТК в будущем (даты пока не указаны).</span><span class="sxs-lookup"><span data-stu-id="aadeb-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="aadeb-260">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="aadeb-260">Controller mapping configuration</span></span>

<span data-ttu-id="aadeb-261">Одним из основных экранов настройки набора средств Mixed Reality является возможность настраивать и сопоставлять различные типы контроллеров, которые могут использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="aadeb-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="aadeb-262">На следующем экране настройки можно настроить любой контроллер, распознаваемый в настоящий момент набором.</span><span class="sxs-lookup"><span data-stu-id="aadeb-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="aadeb-263">МРТК предоставляет конфигурацию по умолчанию для следующих контроллеров и систем:</span><span class="sxs-lookup"><span data-stu-id="aadeb-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="aadeb-264">Мышь (включая поддержку трехмерной пространственной мыши)</span><span class="sxs-lookup"><span data-stu-id="aadeb-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="aadeb-265">Сенсорный экран</span><span class="sxs-lookup"><span data-stu-id="aadeb-265">Touch Screen</span></span>
- <span data-ttu-id="aadeb-266">Контроллеры Xbox</span><span class="sxs-lookup"><span data-stu-id="aadeb-266">Xbox controllers</span></span>
- <span data-ttu-id="aadeb-267">Контроллеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aadeb-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="aadeb-268">Жесты HoloLens</span><span class="sxs-lookup"><span data-stu-id="aadeb-268">HoloLens Gestures</span></span>
- <span data-ttu-id="aadeb-269">Контроллеры HTC Naopak палочки</span><span class="sxs-lookup"><span data-stu-id="aadeb-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="aadeb-270">Окулус Touch Controllers</span><span class="sxs-lookup"><span data-stu-id="aadeb-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="aadeb-271">Удаленный контроллер Окулус</span><span class="sxs-lookup"><span data-stu-id="aadeb-271">Oculus Remote controller</span></span>
- <span data-ttu-id="aadeb-272">Универсальные устройства Опенвр (только для опытных пользователей)</span><span class="sxs-lookup"><span data-stu-id="aadeb-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="aadeb-273">Если щелкнуть изображение для любой из предварительно созданных систем контроллеров, можно настроить одно входное действие для всех соответствующих входных данных, например, на экране Настройки сенсорного контроллера Окулус ниже:</span><span class="sxs-lookup"><span data-stu-id="aadeb-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="aadeb-274">Также имеется расширенный экран для настройки других входных контроллеров Опенвр или Unity, которые не определены выше.</span><span class="sxs-lookup"><span data-stu-id="aadeb-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="aadeb-275">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="aadeb-275">Controller visualization settings</span></span>

<span data-ttu-id="aadeb-276">Помимо сопоставления контроллеров, предоставляется отдельный профиль конфигурации для настройки способа представления контроллеров в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="aadeb-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="aadeb-277">Это можно настроить в "глобальном" (все экземпляры контроллера для конкретной руки) или только для отдельного типа контроллера/вручную.</span><span class="sxs-lookup"><span data-stu-id="aadeb-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="aadeb-278">МРТК также поддерживает собственные модели контроллера SDK для Windows Mixed Reality и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="aadeb-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="aadeb-279">Они загружаются в виде объекты gameobject в сцене и размещаются с помощью отслеживания контроллера платформы.</span><span class="sxs-lookup"><span data-stu-id="aadeb-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="aadeb-280">Если представление контроллера в сцене должно быть смещено от позиции физического контроллера, то просто задайте это смещение относительно prefab модели контроллера (например, установив расположение преобразования контроллера prefab со смещением позиции).</span><span class="sxs-lookup"><span data-stu-id="aadeb-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="aadeb-281">Служебные программы редактора</span><span class="sxs-lookup"><span data-stu-id="aadeb-281">Editor utilities</span></span>

<span data-ttu-id="aadeb-282">Следующие служебные программы работают только в редакторе и полезны для повышения производительности разработки.</span><span class="sxs-lookup"><span data-stu-id="aadeb-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Служебные программы настройки редактора МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="aadeb-284">Инспекторы служб</span><span class="sxs-lookup"><span data-stu-id="aadeb-284">Service inspectors</span></span>

<span data-ttu-id="aadeb-285">Инспекторы служб — это функция только редактора, которая создает объекты в сцене, представляющие активные службы.</span><span class="sxs-lookup"><span data-stu-id="aadeb-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="aadeb-286">При выборе этих объектов отображаются инспекторы, предлагающие ссылки на документацию, управление визуализациями редактора и понимание состояния службы.</span><span class="sxs-lookup"><span data-stu-id="aadeb-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="aadeb-287">Инспекторы служб можно включить, установив флажок *использовать инспекторы служб* в разделе *Параметры редактора* в профиле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aadeb-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="aadeb-288">Модуль подготовки буфера глубины</span><span class="sxs-lookup"><span data-stu-id="aadeb-288">Depth buffer renderer</span></span>

<span data-ttu-id="aadeb-289">Совместное использование буфера глубины с некоторыми платформами смешанной реальности может повысить [голограмму стабилизации](../performance/hologram-stabilization.md).</span><span class="sxs-lookup"><span data-stu-id="aadeb-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="aadeb-290">Например, платформа Windows Mixed Reality может изменить отображаемую сцену на пиксель, чтобы учитывать незначительные движения головного подразделения в течение времени, когда оно потребовалось для отрисовки кадра.</span><span class="sxs-lookup"><span data-stu-id="aadeb-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="aadeb-291">Однако для этих методов требуются буферы глубины с точными данными, чтобы понять, где и насколько далеко от пользователя.</span><span class="sxs-lookup"><span data-stu-id="aadeb-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="aadeb-292">Чтобы обеспечить визуализацию сцены всех необходимых данных в буфер глубины, разработчики могут переключать функцию *буфера глубины рендеринга* в разделе *Параметры редактора* в профиле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aadeb-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="aadeb-293">Это займет текущий буфер глубины и выводит его в виде цвета в представление сцены, применяя к основной камере результат последующей обработки [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) .</span><span class="sxs-lookup"><span data-stu-id="aadeb-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="aadeb-294">![Программа буфера глубины прорисовки ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>синий цилиндр в сцене содержит материал с зврите, поэтому данные глубины не записываются</sup> .</span><span class="sxs-lookup"><span data-stu-id="aadeb-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="aadeb-295">Изменение профилей во время выполнения</span><span class="sxs-lookup"><span data-stu-id="aadeb-295">Changing profiles at runtime</span></span>

<span data-ttu-id="aadeb-296">Можно обновлять профили во время выполнения, и в большинстве случаев это полезно в двух разных сценариях.</span><span class="sxs-lookup"><span data-stu-id="aadeb-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="aadeb-297">**Параметр предварительной инициализации профиля мртк**: при запуске перед инициализацией мртк и переводом профиля в состояние "неиспользуемый" заменяется для включения и отключения различных функций в зависимости от возможностей устройства.</span><span class="sxs-lookup"><span data-stu-id="aadeb-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="aadeb-298">Например, если опыт работает в VR без оборудования пространственного сопоставления, вероятно, не имеет смысла включать компонент пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="aadeb-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="aadeb-299">**Переключатель активного профиля**: после запуска, после инициализации мртк и активации профиля, переключать профиль, используемый в настоящий момент, для изменения способа работы определенных функций.</span><span class="sxs-lookup"><span data-stu-id="aadeb-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="aadeb-300">Например, в приложении может быть определен конкретный вспомогательный интерфейс, который должен полностью удалить указатели.</span><span class="sxs-lookup"><span data-stu-id="aadeb-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="aadeb-301">Параметр профиля инициализации pre МРТК</span><span class="sxs-lookup"><span data-stu-id="aadeb-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="aadeb-302">Это можно сделать, присоединив незавершенное поведение (пример ниже), которое выполняется перед инициализацией МРТК (т. е. в спящем режиме ()).</span><span class="sxs-lookup"><span data-stu-id="aadeb-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="aadeb-303">Обратите внимание, что сценарий (т. е. вызов `SetProfileBeforeInitialization` ) должен выполняться раньше `MixedRealityToolkit` , чем скрипт, который можно получить, установив [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="aadeb-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="aadeb-304">Вместо «Профилетаусе» можно иметь произвольный набор профилей, применяемых к определенным платформам (например, один для HoloLens 1, один для VR, один для HoloLens 2 и т. д.).</span><span class="sxs-lookup"><span data-stu-id="aadeb-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="aadeb-305">Можно использовать различные другие индикаторы (например https://docs.unity3d.com/ScriptReference/SystemInfo.html , независимо от того, является ли камера непрозрачной или прозрачной), чтобы определить, какой профиль нужно загрузить.</span><span class="sxs-lookup"><span data-stu-id="aadeb-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="aadeb-306">Переключатель активного профиля</span><span class="sxs-lookup"><span data-stu-id="aadeb-306">Active profile switch</span></span>

<span data-ttu-id="aadeb-307">Это можно сделать, задав `MixedRealityToolkit.Instance.ActiveProfile` для свойства новый профиль, заменяющий активный профиль.</span><span class="sxs-lookup"><span data-stu-id="aadeb-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="aadeb-308">Обратите внимание `ActiveProfile` , что при настройке во время выполнения уничтожение выполняющихся служб будет происходить после последней латеупдате () всех служб, а создание и инициализацию служб, связанных с новым профилем, будет происходить до первого обновления () всех служб.</span><span class="sxs-lookup"><span data-stu-id="aadeb-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="aadeb-309">Во время этого процесса может возникнуть заметная колебание приложения.</span><span class="sxs-lookup"><span data-stu-id="aadeb-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="aadeb-310">Кроме того, любой сценарий с более высоким приоритетом, чем `MixedRealityToolkit` скрипт, может ввести его обновление, прежде чем новый профиль будет правильно настроен.</span><span class="sxs-lookup"><span data-stu-id="aadeb-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="aadeb-311">Дополнительные сведения о приоритете скрипта см. в разделе [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html) .</span><span class="sxs-lookup"><span data-stu-id="aadeb-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="aadeb-312">В процессе переключения профиля существующая Камера интерфейса пользователя останется без изменений, гарантируя, что компоненты пользовательского интерфейса Unity, требующие Canvas, по-прежнему будут работать после параметра.</span><span class="sxs-lookup"><span data-stu-id="aadeb-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="aadeb-313">См. также</span><span class="sxs-lookup"><span data-stu-id="aadeb-313">See also</span></span>

- [<span data-ttu-id="aadeb-314">Стабилизация голограмм</span><span class="sxs-lookup"><span data-stu-id="aadeb-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)