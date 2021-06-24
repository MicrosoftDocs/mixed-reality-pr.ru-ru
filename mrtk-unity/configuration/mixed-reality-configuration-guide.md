---
title: Рекомендации по настройке смешанной реальности
description: Документация по настройке МРТК в Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК,
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588866"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="5ff95-104">Рекомендации по настройке профиля набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5ff95-104">Mixed Reality Toolkit profile configuration guide</span></span>

<span data-ttu-id="5ff95-105">Набор средств для смешанной реальности централизует как можно больше конфигурации, необходимой для управления набором средств (за исключением истинной среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="5ff95-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="5ff95-106">Это простое пошаговое руководство для каждого экрана профиля конфигурации, доступного для набора средств.</span><span class="sxs-lookup"><span data-stu-id="5ff95-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="5ff95-107">Основной профиль конфигурации набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5ff95-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="5ff95-108">Главный профиль конфигурации, присоединенный к *микседреалититулкит* GameObject в сцене, предоставляет главную точку входа для набора инструментов в проекте.</span><span class="sxs-lookup"><span data-stu-id="5ff95-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff95-109">Набор средств Mixed Reality "блокирует" экраны конфигурации по умолчанию, чтобы гарантировать, что у вас всегда есть общая начальная точка для проекта, и рекомендуется приступить к определению собственных параметров по мере развития проекта.</span><span class="sxs-lookup"><span data-stu-id="5ff95-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="5ff95-110">Конфигурация МРТК не редактируется в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="5ff95-110">The MRTK configuration is not editable during play-mode.</span></span>

![Профиль конфигурации МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="5ff95-112">Все профили "по умолчанию" для набора средств Mixed Reality можно найти в проекте SDK в папке Assets/МРТК/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="5ff95-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ff95-113">DefaultHoloLens2ConfigurationProfile оптимизирован для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5ff95-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="5ff95-114">Дополнительные сведения см. в разделе [Профили](../features/profiles/profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff95-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="5ff95-115">При открытии главного профиля конфигурации набора средств для смешанной реальности в инспекторе отображается следующий экран:</span><span class="sxs-lookup"><span data-stu-id="5ff95-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="5ff95-116">Если вы выберете ресурс Микседреалититулкитконфигуратионпрофиле без Микседреалититулкит в сцене, то запросите, хотите ли вы, чтобы МРТК автоматически настроить сцену.</span><span class="sxs-lookup"><span data-stu-id="5ff95-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="5ff95-117">Это необязательно, однако в сцене должен быть активный объект Микседреалититулкит для доступа ко всем экранам конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5ff95-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="5ff95-118">Он содержит текущую активную конфигурацию среды выполнения для проекта.</span><span class="sxs-lookup"><span data-stu-id="5ff95-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="5ff95-119">Здесь можно переходить ко всем профилям конфигурации для МРТК, включая:</span><span class="sxs-lookup"><span data-stu-id="5ff95-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="5ff95-120">Рекомендации по настройке профиля набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5ff95-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="5ff95-121">Основной профиль конфигурации набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5ff95-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="5ff95-122">Параметры работы</span><span class="sxs-lookup"><span data-stu-id="5ff95-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="5ff95-123">Параметры камеры</span><span class="sxs-lookup"><span data-stu-id="5ff95-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="5ff95-124">Параметры системы ввода</span><span class="sxs-lookup"><span data-stu-id="5ff95-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="5ff95-125">Параметры визуализации границ</span><span class="sxs-lookup"><span data-stu-id="5ff95-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="5ff95-126">Выбор системы для пропорций</span><span class="sxs-lookup"><span data-stu-id="5ff95-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="5ff95-127">Параметры пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="5ff95-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="5ff95-128">Параметры диагностики</span><span class="sxs-lookup"><span data-stu-id="5ff95-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="5ff95-129">Параметры системы сцены</span><span class="sxs-lookup"><span data-stu-id="5ff95-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="5ff95-130">Дополнительные параметры служб</span><span class="sxs-lookup"><span data-stu-id="5ff95-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="5ff95-131">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="5ff95-132">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="5ff95-133">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="5ff95-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="5ff95-134">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="5ff95-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="5ff95-135">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="5ff95-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="5ff95-136">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="5ff95-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="5ff95-137">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="5ff95-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="5ff95-138">Служебные программы редактора</span><span class="sxs-lookup"><span data-stu-id="5ff95-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="5ff95-139">Инспекторы служб</span><span class="sxs-lookup"><span data-stu-id="5ff95-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="5ff95-140">Модуль подготовки буфера глубины</span><span class="sxs-lookup"><span data-stu-id="5ff95-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="5ff95-141">Изменение профилей во время выполнения</span><span class="sxs-lookup"><span data-stu-id="5ff95-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="5ff95-142">Параметр профиля инициализации pre МРТК</span><span class="sxs-lookup"><span data-stu-id="5ff95-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="5ff95-143">Переключатель активного профиля</span><span class="sxs-lookup"><span data-stu-id="5ff95-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="5ff95-144">См. также:</span><span class="sxs-lookup"><span data-stu-id="5ff95-144">See also</span></span>](#see-also)

<span data-ttu-id="5ff95-145">Эти профили конфигурации описаны ниже в соответствующих разделах.</span><span class="sxs-lookup"><span data-stu-id="5ff95-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="5ff95-146">Параметры работы</span><span class="sxs-lookup"><span data-stu-id="5ff95-146">Experience settings</span></span>

<span data-ttu-id="5ff95-147">Этот параметр, расположенный на главной странице конфигурации набора средств смешанной реальности, определяет операцию по умолчанию для [масштаба среды Mixed Reality](/windows/mixed-reality/coordinate-systems-in-unity) для проекта.</span><span class="sxs-lookup"><span data-stu-id="5ff95-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="5ff95-148">Параметры камеры</span><span class="sxs-lookup"><span data-stu-id="5ff95-148">Camera settings</span></span>

<span data-ttu-id="5ff95-149">Параметры камеры определяют, как будет настроена камера для проекта смешанной реальности, определяя общие параметры обрезки, качества и прозрачности.</span><span class="sxs-lookup"><span data-stu-id="5ff95-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="5ff95-150">Параметры системы ввода</span><span class="sxs-lookup"><span data-stu-id="5ff95-150">Input system settings</span></span>

<span data-ttu-id="5ff95-151">Проект Mixed Reality предоставляет надежную и хорошо обученную входную систему для маршрутизации всех событий ввода вокруг проекта, выбранного по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5ff95-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="5ff95-152">За входной системой, предоставляемой МРТК, относятся несколько других систем, которые помогают управлять сложными взаимными настройками, необходимыми для абстракции сложностей многоплатформенных и смешанных сред.</span><span class="sxs-lookup"><span data-stu-id="5ff95-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="5ff95-153">Каждый из отдельных профилей описан ниже.</span><span class="sxs-lookup"><span data-stu-id="5ff95-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="5ff95-154">Параметры фокуса</span><span class="sxs-lookup"><span data-stu-id="5ff95-154">Focus Settings</span></span>
- [<span data-ttu-id="5ff95-155">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="5ff95-156">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="5ff95-157">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="5ff95-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="5ff95-158">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="5ff95-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="5ff95-159">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="5ff95-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="5ff95-160">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="5ff95-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="5ff95-161">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="5ff95-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="5ff95-162">Параметры визуализации границ</span><span class="sxs-lookup"><span data-stu-id="5ff95-162">Boundary visualization settings</span></span>

<span data-ttu-id="5ff95-163">Система границ преобразует воспринимаемую границу, сообщаемую базовой системой границ и системы защиты платформ.</span><span class="sxs-lookup"><span data-stu-id="5ff95-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="5ff95-164">Конфигурация визуализатора границы дает возможность автоматически отображать записанную границу в сцене относительно положения пользователя. Граница также будет реагировать на изменения и обновляться в зависимости от того, где находятся телепорты пользователя в сцене.</span><span class="sxs-lookup"><span data-stu-id="5ff95-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="5ff95-165">Выбор системы для пропорций</span><span class="sxs-lookup"><span data-stu-id="5ff95-165">Teleportation system selection</span></span>

<span data-ttu-id="5ff95-166">Проект Mixed Reality предоставляет полнофункциональную систему для управления событиями передачи в проекте, которая выбрана по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5ff95-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="5ff95-167">Параметры пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="5ff95-167">Spatial awareness settings</span></span>

<span data-ttu-id="5ff95-168">Проект Mixed Reality предоставляет перестроенную систему пространственной информации для работы с системами пространственного сканирования в проекте, выбранном по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5ff95-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="5ff95-169">Конфигурация пространственной осведомленности в наборе средств Mixed Reality позволяет настраивать способ запуска системы, независимо от того, запускается ли она автоматически при запуске приложения или более поздней версии, а также при установке экстентов для поля представления.</span><span class="sxs-lookup"><span data-stu-id="5ff95-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="5ff95-170">Кроме того, она позволяет настроить параметры сетки и зоны, а также настраивать то, как проект понимает среду.</span><span class="sxs-lookup"><span data-stu-id="5ff95-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="5ff95-171">Это применимо только к устройствам, которые могут предоставлять сканированную среду.</span><span class="sxs-lookup"><span data-stu-id="5ff95-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="5ff95-172">Параметры диагностики</span><span class="sxs-lookup"><span data-stu-id="5ff95-172">Diagnostics settings</span></span>

<span data-ttu-id="5ff95-173">Необязательная, но очень полезная функция МРТК — это функция диагностики подключаемого модуля.</span><span class="sxs-lookup"><span data-stu-id="5ff95-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="5ff95-174">Профиль диагностики предоставляет несколько простых систем для наблюдения за выполнением проекта, включая удобный переключатель вкл./выкл. для включения и отключения панели отображения в сцене.</span><span class="sxs-lookup"><span data-stu-id="5ff95-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="5ff95-175">Параметры системы сцены</span><span class="sxs-lookup"><span data-stu-id="5ff95-175">Scene system settings</span></span>

<span data-ttu-id="5ff95-176">МРТК предоставляет эту необязательную службу, которая помогает управлять сложной загрузкой и выгрузке сложных вспомогательных сцен.</span><span class="sxs-lookup"><span data-stu-id="5ff95-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="5ff95-177">Чтобы решить, подходит ли система сцен для вашего проекта, ознакомьтесь с [руководством по начало работыию сцены.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="5ff95-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="5ff95-178">Дополнительные параметры служб</span><span class="sxs-lookup"><span data-stu-id="5ff95-178">Additional services settings</span></span>

<span data-ttu-id="5ff95-179">Одной из более сложных областей набора средств Mixed Reality является реализация [шаблона локатора служб](https://en.wikipedia.org/wiki/Service_locator_pattern) , которая позволяет зарегистрировать любую "службу" в инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="5ff95-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="5ff95-180">Это позволяет легко расширять платформу с помощью новых функций и систем, но также позволяет проектам использовать эти возможности для регистрации собственных компонентов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5ff95-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="5ff95-181">Любая зарегистрированная служба по-прежнему получает все преимущества всех событий Unity без издержек и затрат на реализацию одноэлементных шаблонов неуклюжим.</span><span class="sxs-lookup"><span data-stu-id="5ff95-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="5ff95-182">Это позволяет выполнять чисто компоненты C# без издержек на сцены для выполнения фоновых и задних процессов, например порождение систем, логика игры среды выполнения или практически любые другие.</span><span class="sxs-lookup"><span data-stu-id="5ff95-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="5ff95-183">Параметры входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-183">Input actions settings</span></span>

<span data-ttu-id="5ff95-184">Входные действия предоставляют способ абстрактного взаимодействия с любыми физическими взаимодействиями и входными данными из проекта среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5ff95-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="5ff95-185">Все физические входные данные (от контроллеров, руки и мыши/т. д.) преобразуются в логические действия ввода для использования в проекте среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5ff95-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="5ff95-186">Это гарантирует неважность, откуда поступают входные данные. проект просто реализует эти действия в фоновом режиме в виде «вещей» или «взаимодействие с».</span><span class="sxs-lookup"><span data-stu-id="5ff95-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="5ff95-187">Чтобы создать новое действие ввода, просто нажмите кнопку "добавить новое действие" и введите понятное текстовое имя для того, что оно представляет.</span><span class="sxs-lookup"><span data-stu-id="5ff95-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="5ff95-188">Затем нужно выбрать только ось (тип данных), которую должно передать действие, или, в случае физического контроллера, физический тип входных данных, к которому можно присоединиться, например:</span><span class="sxs-lookup"><span data-stu-id="5ff95-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="5ff95-189">Ограничение оси</span><span class="sxs-lookup"><span data-stu-id="5ff95-189">Axis Constraint</span></span> | <span data-ttu-id="5ff95-190">Тип данных</span><span class="sxs-lookup"><span data-stu-id="5ff95-190">Data Type</span></span> | <span data-ttu-id="5ff95-191">Описание</span><span class="sxs-lookup"><span data-stu-id="5ff95-191">Description</span></span> | <span data-ttu-id="5ff95-192">Пример использования</span><span class="sxs-lookup"><span data-stu-id="5ff95-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="5ff95-193">Нет</span><span class="sxs-lookup"><span data-stu-id="5ff95-193">None</span></span> | <span data-ttu-id="5ff95-194">Нет данных</span><span class="sxs-lookup"><span data-stu-id="5ff95-194">No data</span></span> | <span data-ttu-id="5ff95-195">Используется для пустого действия или события</span><span class="sxs-lookup"><span data-stu-id="5ff95-195">Used for an empty action or event</span></span> | <span data-ttu-id="5ff95-196">Триггер события</span><span class="sxs-lookup"><span data-stu-id="5ff95-196">Event Trigger</span></span> |
| <span data-ttu-id="5ff95-197">Необработанный (зарезервированный)</span><span class="sxs-lookup"><span data-stu-id="5ff95-197">Raw (reserved)</span></span> | <span data-ttu-id="5ff95-198">объект</span><span class="sxs-lookup"><span data-stu-id="5ff95-198">object</span></span> | <span data-ttu-id="5ff95-199">Зарезервировано для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="5ff95-199">Reserved for future use</span></span> | <span data-ttu-id="5ff95-200">Недоступно</span><span class="sxs-lookup"><span data-stu-id="5ff95-200">N/A</span></span> |
| <span data-ttu-id="5ff95-201">Цифровой</span><span class="sxs-lookup"><span data-stu-id="5ff95-201">Digital</span></span> | <span data-ttu-id="5ff95-202">bool</span><span class="sxs-lookup"><span data-stu-id="5ff95-202">bool</span></span> | <span data-ttu-id="5ff95-203">Логическое значение ON или Off типа Data</span><span class="sxs-lookup"><span data-stu-id="5ff95-203">A boolean on or off type data</span></span> | <span data-ttu-id="5ff95-204">Кнопка контроллера</span><span class="sxs-lookup"><span data-stu-id="5ff95-204">A controller button</span></span> |
| <span data-ttu-id="5ff95-205">Одна ось</span><span class="sxs-lookup"><span data-stu-id="5ff95-205">Single Axis</span></span> | <span data-ttu-id="5ff95-206">FLOAT</span><span class="sxs-lookup"><span data-stu-id="5ff95-206">float</span></span> | <span data-ttu-id="5ff95-207">Одно значение данных точности</span><span class="sxs-lookup"><span data-stu-id="5ff95-207">A single precision data value</span></span> | <span data-ttu-id="5ff95-208">Входной диапазон, например триггер</span><span class="sxs-lookup"><span data-stu-id="5ff95-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="5ff95-209">Двойная ось</span><span class="sxs-lookup"><span data-stu-id="5ff95-209">Dual Axis</span></span> | <span data-ttu-id="5ff95-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="5ff95-210">Vector2</span></span> | <span data-ttu-id="5ff95-211">Тип данных Dual float для нескольких осей</span><span class="sxs-lookup"><span data-stu-id="5ff95-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="5ff95-212">Dpad или аналоговый стик</span><span class="sxs-lookup"><span data-stu-id="5ff95-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="5ff95-213">3 ДОФ</span><span class="sxs-lookup"><span data-stu-id="5ff95-213">Three Dof Position</span></span> | <span data-ttu-id="5ff95-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="5ff95-214">Vector3</span></span> | <span data-ttu-id="5ff95-215">Данные о позиционированном типе из с 3 осью с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="5ff95-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="5ff95-216">Контроллер только с трехмерным положением</span><span class="sxs-lookup"><span data-stu-id="5ff95-216">3D position style only controller</span></span> |
| <span data-ttu-id="5ff95-217">Тройной поворот ДОФ</span><span class="sxs-lookup"><span data-stu-id="5ff95-217">Three Dof Rotation</span></span> | <span data-ttu-id="5ff95-218">Quaternion</span><span class="sxs-lookup"><span data-stu-id="5ff95-218">Quaternion</span></span> | <span data-ttu-id="5ff95-219">Только поворот входных данных с 4 осью с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="5ff95-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="5ff95-220">Контроллер в стиле с тремя степенями, например контроллер Окулус Go</span><span class="sxs-lookup"><span data-stu-id="5ff95-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="5ff95-221">Шесть ДОФ</span><span class="sxs-lookup"><span data-stu-id="5ff95-221">Six Dof</span></span> | <span data-ttu-id="5ff95-222">"Смешанная реальность" (Vector3, кватернион)</span><span class="sxs-lookup"><span data-stu-id="5ff95-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="5ff95-223">Входные данные в стиле расположения и поворота с помощью компонентов Vector3 и кватернион</span><span class="sxs-lookup"><span data-stu-id="5ff95-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="5ff95-224">Контроллер или указатель движения</span><span class="sxs-lookup"><span data-stu-id="5ff95-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="5ff95-225">События, использующие входные действия, не ограничиваются физическими контроллерами и могут по-прежнему использоваться в проекте для того, чтобы эффекты среды выполнения создавали новые действия.</span><span class="sxs-lookup"><span data-stu-id="5ff95-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff95-226">Входные действия — это один из нескольких компонентов, которые нельзя изменять во время выполнения, они являются только конфигурацией времени разработки.</span><span class="sxs-lookup"><span data-stu-id="5ff95-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="5ff95-227">Этот профиль не следует переключать в силу того, что проект работает из-за зависимости платформы (и ваших проектов) от идентификатора, созданного для каждого действия.</span><span class="sxs-lookup"><span data-stu-id="5ff95-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="5ff95-228">Правила для входных действий</span><span class="sxs-lookup"><span data-stu-id="5ff95-228">Input actions rules</span></span>

<span data-ttu-id="5ff95-229">Правила входных действий предоставляют способ автоматического преобразования события, вызванного одним входным действием, в различные действия на основе его значения данных.</span><span class="sxs-lookup"><span data-stu-id="5ff95-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="5ff95-230">Они легко управляются в рамках платформы и не вызывают никаких затрат на производительность.</span><span class="sxs-lookup"><span data-stu-id="5ff95-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="5ff95-231">Например, преобразование одного входного события двойной оси из DPad в в 4 соответствующие действия «Dpad up»/«DPad Down»/«Dpad Left»/«Dpad Right» (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="5ff95-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="5ff95-232">Это также можно сделать в собственном коде.</span><span class="sxs-lookup"><span data-stu-id="5ff95-232">This could also be done in your own code.</span></span> <span data-ttu-id="5ff95-233">Однако, так как это был очень распространенный шаблон, платформа предоставляет механизм для выполнения этой задачи «не из этого».</span><span class="sxs-lookup"><span data-stu-id="5ff95-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="5ff95-234">Правила входных действий можно настроить для любой доступной входной оси.</span><span class="sxs-lookup"><span data-stu-id="5ff95-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="5ff95-235">Однако действия ввода из одного типа оси можно перевести в другое Входное действие того же типа оси.</span><span class="sxs-lookup"><span data-stu-id="5ff95-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="5ff95-236">Действие двойной оси можно связать с другим действием двойной оси, но не с цифровым действием или без него.</span><span class="sxs-lookup"><span data-stu-id="5ff95-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Профиль правил входных действий](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="5ff95-238">Конфигурация указателя</span><span class="sxs-lookup"><span data-stu-id="5ff95-238">Pointer configuration</span></span>

<span data-ttu-id="5ff95-239">Указатели используются для взаимодействия в сцене на любом устройстве ввода, предоставляя направление и проверку нажатия для любого объекта в сцене (с присоединенным объектом или компонентом пользовательского интерфейса).</span><span class="sxs-lookup"><span data-stu-id="5ff95-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="5ff95-240">Указатели по умолчанию автоматически настраиваются для контроллеров, гарнитур (взгляд/Focus) и ввод с клавиатуры и сенсорного ввода.</span><span class="sxs-lookup"><span data-stu-id="5ff95-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="5ff95-241">Указатели можно также выработать в активной сцене с помощью одного из многих компонентов строк, предоставляемых набором средств Mixed Reality, или любого собственного компонента, если они реализуют интерфейс МРТК Имикседреалитипоинтер.</span><span class="sxs-lookup"><span data-stu-id="5ff95-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="5ff95-242">Геообъектная область: определяет глобальную указывающую экстент для всех указателей, включая взгляд.</span><span class="sxs-lookup"><span data-stu-id="5ff95-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="5ff95-243">Райкаст Layer Маскируетs: определяет, для каких слоев указатели будут райкаст.</span><span class="sxs-lookup"><span data-stu-id="5ff95-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="5ff95-244">Отладка направленных вниз отрисованных лучей: вспомогательный модуль отладки для визуализации луча, используемых для райкастинг.</span><span class="sxs-lookup"><span data-stu-id="5ff95-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="5ff95-245">Отладка рисуемых отлучающих лучей цветов: набор цветов, используемых для визуализации.</span><span class="sxs-lookup"><span data-stu-id="5ff95-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="5ff95-246">Взгляните на курсор Prefab: позволяет легко указать глобальный курсор взгляда для любой сцены.</span><span class="sxs-lookup"><span data-stu-id="5ff95-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="5ff95-247">Есть дополнительная вспомогательная кнопка, позволяющая быстро перейти к поставщику взгляда, чтобы переопределить некоторые конкретные значения для взгляда при необходимости.</span><span class="sxs-lookup"><span data-stu-id="5ff95-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="5ff95-248">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="5ff95-248">Gestures configuration</span></span>

<span data-ttu-id="5ff95-249">Жесты — это специальная реализация системы, позволяющая назначать входные действия различным входным методам "жеста", предоставляемым различными пакетами SDK (например, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="5ff95-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="5ff95-250">Текущая реализация жестов предназначена только для HoloLens и будет улучшена для других систем, так как они будут добавлены в набор средств в будущем (пока нет дат).</span><span class="sxs-lookup"><span data-stu-id="5ff95-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="5ff95-251">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="5ff95-251">Speech commands</span></span>

<span data-ttu-id="5ff95-252">Как и жесты, некоторые платформы среды выполнения также предоставляют интеллектуальные функции "речь — текст" с возможностью создания команд, которые могут быть получены проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="5ff95-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="5ff95-253">Этот профиль конфигурации позволяет настроить следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="5ff95-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="5ff95-254">Общие параметры. для параметра "поведение при запуске" задайте значение "автоматический запуск" или "запуск вручную". определяет, следует ли инициализировать Кэйвордрекогнизер при запуске системы ввода или разрешить проекту решать, когда инициализировать Кэйвордрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="5ff95-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="5ff95-255">"Уровень достоверности распознавания" используется для инициализации [API Кэйвордрекогнизер](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="5ff95-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="5ff95-256">Речевые команды — регистрируют слова и переводит их в для ввода действий, которые могут быть получены проектом.</span><span class="sxs-lookup"><span data-stu-id="5ff95-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="5ff95-257">Они также могут быть присоединены к действиям клавиатуры, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="5ff95-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ff95-258">В настоящее время система поддерживает только распознавание речи при работе на платформах Windows 10, например HoloLens и Windows 10 Desktop, и будет улучшена для других систем, так как они будут добавлены в МРТК в будущем (даты пока не указаны).</span><span class="sxs-lookup"><span data-stu-id="5ff95-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="5ff95-259">Конфигурация сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="5ff95-259">Controller mapping configuration</span></span>

<span data-ttu-id="5ff95-260">Одним из основных экранов настройки набора средств Mixed Reality является возможность настраивать и сопоставлять различные типы контроллеров, которые могут использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="5ff95-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="5ff95-261">На следующем экране настройки можно настроить любой контроллер, распознаваемый в настоящий момент набором.</span><span class="sxs-lookup"><span data-stu-id="5ff95-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="5ff95-262">МРТК предоставляет конфигурацию по умолчанию для следующих контроллеров и систем:</span><span class="sxs-lookup"><span data-stu-id="5ff95-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="5ff95-263">Мышь (включая поддержку трехмерной пространственной мыши)</span><span class="sxs-lookup"><span data-stu-id="5ff95-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="5ff95-264">Сенсорный экран</span><span class="sxs-lookup"><span data-stu-id="5ff95-264">Touch Screen</span></span>
- <span data-ttu-id="5ff95-265">Контроллеры Xbox</span><span class="sxs-lookup"><span data-stu-id="5ff95-265">Xbox controllers</span></span>
- <span data-ttu-id="5ff95-266">Контроллеры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5ff95-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="5ff95-267">Жесты HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ff95-267">HoloLens Gestures</span></span>
- <span data-ttu-id="5ff95-268">Контроллеры HTC Naopak палочки</span><span class="sxs-lookup"><span data-stu-id="5ff95-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="5ff95-269">Окулус Touch Controllers</span><span class="sxs-lookup"><span data-stu-id="5ff95-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="5ff95-270">Удаленный контроллер Окулус</span><span class="sxs-lookup"><span data-stu-id="5ff95-270">Oculus Remote controller</span></span>
- <span data-ttu-id="5ff95-271">Универсальные устройства Опенвр (только для опытных пользователей)</span><span class="sxs-lookup"><span data-stu-id="5ff95-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="5ff95-272">Если щелкнуть изображение для любой из предварительно созданных систем контроллеров, можно настроить одно входное действие для всех соответствующих входных данных, например, на экране Настройки сенсорного контроллера Окулус ниже:</span><span class="sxs-lookup"><span data-stu-id="5ff95-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="5ff95-273">Также имеется расширенный экран для настройки других входных контроллеров Опенвр или Unity, которые не определены выше.</span><span class="sxs-lookup"><span data-stu-id="5ff95-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="5ff95-274">Параметры визуализации контроллера</span><span class="sxs-lookup"><span data-stu-id="5ff95-274">Controller visualization settings</span></span>

<span data-ttu-id="5ff95-275">Помимо сопоставления контроллеров, предоставляется отдельный профиль конфигурации для настройки способа представления контроллеров в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="5ff95-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="5ff95-276">Это можно настроить в "глобальном" (все экземпляры контроллера для конкретной руки) или только для отдельного типа контроллера/вручную.</span><span class="sxs-lookup"><span data-stu-id="5ff95-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="5ff95-277">МРТК также поддерживает собственные модели контроллера SDK для Windows Mixed Reality и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="5ff95-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="5ff95-278">Они загружаются в виде объекты gameobject в сцене и размещаются с помощью отслеживания контроллера платформы.</span><span class="sxs-lookup"><span data-stu-id="5ff95-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="5ff95-279">Если представление контроллера в сцене должно быть смещено от позиции физического контроллера, то просто задайте это смещение относительно prefab модели контроллера (например, установив расположение преобразования контроллера prefab со смещением позиции).</span><span class="sxs-lookup"><span data-stu-id="5ff95-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="5ff95-280">Служебные программы редактора</span><span class="sxs-lookup"><span data-stu-id="5ff95-280">Editor utilities</span></span>

<span data-ttu-id="5ff95-281">Следующие служебные программы работают только в редакторе и полезны для повышения производительности разработки.</span><span class="sxs-lookup"><span data-stu-id="5ff95-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Служебные программы настройки редактора МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="5ff95-283">Инспекторы служб</span><span class="sxs-lookup"><span data-stu-id="5ff95-283">Service inspectors</span></span>

<span data-ttu-id="5ff95-284">Инспекторы служб — это функция только редактора, которая создает объекты в сцене, представляющие активные службы.</span><span class="sxs-lookup"><span data-stu-id="5ff95-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="5ff95-285">При выборе этих объектов отображаются инспекторы, предлагающие ссылки на документацию, управление визуализациями редактора и понимание состояния службы.</span><span class="sxs-lookup"><span data-stu-id="5ff95-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="5ff95-286">Инспекторы служб можно включить, установив флажок *использовать инспекторы служб* в разделе *Параметры редактора* в профиле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5ff95-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="5ff95-287">Модуль подготовки буфера глубины</span><span class="sxs-lookup"><span data-stu-id="5ff95-287">Depth buffer renderer</span></span>

<span data-ttu-id="5ff95-288">Совместное использование буфера глубины с некоторыми платформами смешанной реальности может повысить [голограмму стабилизации](../performance/hologram-stabilization.md).</span><span class="sxs-lookup"><span data-stu-id="5ff95-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="5ff95-289">Например, платформа Windows Mixed Reality может изменить отображаемую сцену на пиксель, чтобы учитывать незначительные движения головного подразделения в течение времени, когда оно потребовалось для отрисовки кадра.</span><span class="sxs-lookup"><span data-stu-id="5ff95-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="5ff95-290">Однако для этих методов требуются буферы глубины с точными данными, чтобы понять, где и насколько далеко от пользователя.</span><span class="sxs-lookup"><span data-stu-id="5ff95-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="5ff95-291">Чтобы обеспечить визуализацию сцены всех необходимых данных в буфер глубины, разработчики могут переключать функцию *буфера глубины рендеринга* в разделе *Параметры редактора* в профиле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5ff95-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="5ff95-292">Это займет текущий буфер глубины и выводит его в виде цвета в представление сцены, применяя к основной камере результат последующей обработки [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) .</span><span class="sxs-lookup"><span data-stu-id="5ff95-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="5ff95-293">![Программа буфера глубины прорисовки ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>синий цилиндр в сцене содержит материал с зврите, поэтому данные глубины не записываются</sup> .</span><span class="sxs-lookup"><span data-stu-id="5ff95-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="5ff95-294">Изменение профилей во время выполнения</span><span class="sxs-lookup"><span data-stu-id="5ff95-294">Changing profiles at runtime</span></span>

<span data-ttu-id="5ff95-295">Можно обновлять профили во время выполнения, и в большинстве случаев это полезно в двух разных сценариях.</span><span class="sxs-lookup"><span data-stu-id="5ff95-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="5ff95-296">**Параметр предварительной инициализации профиля мртк**: при запуске перед инициализацией мртк и переводом профиля в состояние "неиспользуемый" заменяется для включения и отключения различных функций в зависимости от возможностей устройства.</span><span class="sxs-lookup"><span data-stu-id="5ff95-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="5ff95-297">Например, если опыт работает в VR без оборудования пространственного сопоставления, вероятно, не имеет смысла включать компонент пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="5ff95-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="5ff95-298">**Переключатель активного профиля**: после запуска, после инициализации мртк и активации профиля, переключать профиль, используемый в настоящий момент, для изменения способа работы определенных функций.</span><span class="sxs-lookup"><span data-stu-id="5ff95-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="5ff95-299">Например, в приложении может быть определен конкретный вспомогательный интерфейс, который должен полностью удалить указатели.</span><span class="sxs-lookup"><span data-stu-id="5ff95-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="5ff95-300">Параметр профиля инициализации pre МРТК</span><span class="sxs-lookup"><span data-stu-id="5ff95-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="5ff95-301">Это можно сделать, присоединив незавершенное поведение (пример ниже), которое выполняется перед инициализацией МРТК (т. е. в спящем режиме ()).</span><span class="sxs-lookup"><span data-stu-id="5ff95-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="5ff95-302">Обратите внимание, что сценарий (т. е. вызов `SetProfileBeforeInitialization` ) должен выполняться раньше `MixedRealityToolkit` , чем скрипт, который можно получить, установив [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="5ff95-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="5ff95-303">Вместо «Профилетаусе» можно иметь произвольный набор профилей, применяемых к определенным платформам (например, один для HoloLens 1, один для VR, один для HoloLens 2 и т. д.).</span><span class="sxs-lookup"><span data-stu-id="5ff95-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="5ff95-304">Можно использовать различные другие индикаторы (например https://docs.unity3d.com/ScriptReference/SystemInfo.html , независимо от того, является ли камера непрозрачной или прозрачной), чтобы определить, какой профиль нужно загрузить.</span><span class="sxs-lookup"><span data-stu-id="5ff95-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="5ff95-305">Переключатель активного профиля</span><span class="sxs-lookup"><span data-stu-id="5ff95-305">Active profile switch</span></span>

<span data-ttu-id="5ff95-306">Это можно сделать, задав `MixedRealityToolkit.Instance.ActiveProfile` для свойства новый профиль, заменяющий активный профиль.</span><span class="sxs-lookup"><span data-stu-id="5ff95-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="5ff95-307">Обратите внимание `ActiveProfile` , что при настройке во время выполнения уничтожение выполняющихся служб будет происходить после последней латеупдате () всех служб, а создание и инициализацию служб, связанных с новым профилем, будет происходить до первого обновления () всех служб.</span><span class="sxs-lookup"><span data-stu-id="5ff95-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="5ff95-308">Во время этого процесса может возникнуть заметная колебание приложения.</span><span class="sxs-lookup"><span data-stu-id="5ff95-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="5ff95-309">Кроме того, любой сценарий с более высоким приоритетом, чем `MixedRealityToolkit` скрипт, может ввести его обновление, прежде чем новый профиль будет правильно настроен.</span><span class="sxs-lookup"><span data-stu-id="5ff95-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="5ff95-310">Дополнительные сведения о приоритете скрипта см. в разделе [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html) .</span><span class="sxs-lookup"><span data-stu-id="5ff95-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="5ff95-311">В процессе переключения профиля существующая Камера интерфейса пользователя останется без изменений, гарантируя, что компоненты пользовательского интерфейса Unity, требующие Canvas, по-прежнему будут работать после параметра.</span><span class="sxs-lookup"><span data-stu-id="5ff95-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ff95-312">См. также</span><span class="sxs-lookup"><span data-stu-id="5ff95-312">See also</span></span>

- [<span data-ttu-id="5ff95-313">Стабилизация голограмм</span><span class="sxs-lookup"><span data-stu-id="5ff95-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)