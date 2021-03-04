---
title: Настройка проекта без МРТК
description: Узнайте, как настроить новый проект Unity для Windows Mixed Reality без набора средств Mixed Reality.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Mixed Reality, разработка, начало работы, новый проект, Windows Mixed Reality, UWP, XR, производительность
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117628"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="24294-104">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="24294-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="24294-105">Windows Mixed Reality (ВМР) — это платформа Майкрософт, представленная в составе операционной системы Windows 10.</span><span class="sxs-lookup"><span data-stu-id="24294-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="24294-106">Платформа ВМР позволяет создавать приложения, отображающие цифровое содержимое на устройствах с дисплеем holographic и VR.</span><span class="sxs-lookup"><span data-stu-id="24294-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="24294-107">Хотя корпорация Майкрософт и сообщество создали средства конвертер, такие как набор средств для [смешанной реальности (мртк)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , который автоматически настраивает среду ВМР, многие разработчики хотят создавать свои впечатления с нуля.</span><span class="sxs-lookup"><span data-stu-id="24294-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="24294-108">В следующей документации показано, как правильно настроить проект для разработки смешанной реальности независимо от того, используется ли МРТК.</span><span class="sxs-lookup"><span data-stu-id="24294-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="24294-109">Параметры, которые необходимо изменить, разбиваются на две категории: параметры для каждого проекта и параметры на сцене.</span><span class="sxs-lookup"><span data-stu-id="24294-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="24294-110">Вы всегда можете импортировать МРТК позже, так что нет никаких штрафов на предварительный маршрут вручную.</span><span class="sxs-lookup"><span data-stu-id="24294-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="24294-111">Если выбрать настройку ВМР вручную, то параметры, которые необходимо изменить, разбиваются на две категории: на проект и на сцену.</span><span class="sxs-lookup"><span data-stu-id="24294-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="24294-112">Параметры отдельных проектов</span><span class="sxs-lookup"><span data-stu-id="24294-112">Per-project settings</span></span>

<span data-ttu-id="24294-113">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="24294-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="24294-115">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="24294-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="24294-116">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="24294-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="24294-117">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="24294-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="24294-118">Установка **архитектуры** **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="24294-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="24294-119">Задать **целевое устройство** в **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="24294-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="24294-120">Задать для **типа сборки** **D3D**</span><span class="sxs-lookup"><span data-stu-id="24294-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="24294-121">Установить **последнюю версию** **пакета SDK для UWP**</span><span class="sxs-lookup"><span data-stu-id="24294-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="24294-122">Задать для **конфигурации сборки** значение **Release** , так как имеются известные проблемы с производительностью при отладке</span><span class="sxs-lookup"><span data-stu-id="24294-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

<span data-ttu-id="24294-124">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="24294-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="24294-125">Для КСРСДК</span><span class="sxs-lookup"><span data-stu-id="24294-125">For XRSDK</span></span> 

1. <span data-ttu-id="24294-126">В редакторе Unity перейдите к разделу **правка > параметры проекта** и выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="24294-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="24294-127">Выберите **установить управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="24294-127">Select **Install XR Plugin Management**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](images/wmr-config-img-5.png)

3. <span data-ttu-id="24294-129">Выберите **инициализировать XR при запуске** и **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="24294-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](images/wmr-config-img-7.png)

4. <span data-ttu-id="24294-131">Разверните раздел **Управление подключаемым модулем XR** и выберите **универсальной на вкладке параметры платформы Windows** .</span><span class="sxs-lookup"><span data-stu-id="24294-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="24294-132">Если вы используете Unity 2020 или более поздней версии, вы увидите параметры для проверки **опенкср (Предварительная версия)** или **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="24294-132">If you are using Unity 2020 or later, you will see the options to check **OpenXR (preview)** or **Windows Mixed Reality**</span></span>
6. <span data-ttu-id="24294-133">Можно выбрать любую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="24294-133">You can choose either runtime.</span></span>  <span data-ttu-id="24294-134">Если вы специально разрабатываете для HoloLens 2 или HP reverbа G2 и решите опробовать **опенкср (Предварительная версия)**, выберите поле опенкср (Предварительная версия) и просмотрите наше руководство по [использованию подключаемого модуля опенкср Mixed Reality для Unity](openxr-getting-started.md) , чтобы обеспечить правильную настройку этих устройств перед возвратом в этом учебнике.</span><span class="sxs-lookup"><span data-stu-id="24294-134">If you are specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR (preview)**, select the OpenXR (preview) box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>
7. <span data-ttu-id="24294-135">Если вы решили выбрать подключаемый модуль **Windows Mixed Reality** , установите флажок все флажки и задайте для параметра **режим отправки глубины** значение **глубиной 16 бит** .</span><span class="sxs-lookup"><span data-stu-id="24294-135">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом Windows Mixed Reality](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="24294-137">Для устаревших XR</span><span class="sxs-lookup"><span data-stu-id="24294-137">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="24294-138">Устаревший XR является устаревшим в Unity 2019 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="24294-138">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="24294-139">Открыть **Параметры проигрывателя...** из **параметров сборки... и разверните** группу **параметров XR**</span><span class="sxs-lookup"><span data-stu-id="24294-139">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="24294-140">В разделе **Параметры XR** выберите **Виртуальная реальность поддержка** , чтобы добавить список устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="24294-140">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="24294-141">Установка **16-разрядного** **формата глубины** и включение **общего доступа к буферу глубины**</span><span class="sxs-lookup"><span data-stu-id="24294-141">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="24294-142">Задать **режим отображения стерео** для **одного экземпляра Pass**</span><span class="sxs-lookup"><span data-stu-id="24294-142">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="24294-143">Выберите **WSA holographic Remoting поддерживается** , если вы хотите использовать удаленное взаимодействие с holographic</span><span class="sxs-lookup"><span data-stu-id="24294-143">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом параметров проигрывателя](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="24294-145">Обновление манифеста</span><span class="sxs-lookup"><span data-stu-id="24294-145">Updating the manifest</span></span>

<span data-ttu-id="24294-146">Теперь приложение может работать с более holographic, а также с пространственными входными данными.</span><span class="sxs-lookup"><span data-stu-id="24294-146">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="24294-147">Однако приложению необходимо объявить соответствующие возможности в своем манифесте, чтобы воспользоваться преимуществами определенных функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="24294-147">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="24294-148">Чтобы найти возможности проектов, перейдите в **Параметры проигрывателя > параметры для универсальная платформа Windows > параметры публикации > возможности**.</span><span class="sxs-lookup"><span data-stu-id="24294-148">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="24294-149">Рекомендуется сделать объявления манифеста в Unity, чтобы включить их во все будущие проекты, которые вы экспортируете.</span><span class="sxs-lookup"><span data-stu-id="24294-149">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="24294-150">Ниже перечислены применимые возможности для включения часто используемых интерфейсов API Unity для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="24294-150">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="24294-151">Функция</span><span class="sxs-lookup"><span data-stu-id="24294-151">Capability</span></span>  |  <span data-ttu-id="24294-152">API, которым требуются возможности</span><span class="sxs-lookup"><span data-stu-id="24294-152">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="24294-153">SpatialPerception;</span><span class="sxs-lookup"><span data-stu-id="24294-153">SpatialPerception</span></span>  |  <span data-ttu-id="24294-154">Сурфацеобсервер (доступ к сеткам [пространственных сопоставлений](../../design/spatial-mapping.md) в HoloLens) &mdash; *не требуется никаких возможностей для общего пространственного отслеживания гарнитуры*</span><span class="sxs-lookup"><span data-stu-id="24294-154">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="24294-155">Бесед</span><span class="sxs-lookup"><span data-stu-id="24294-155">WebCam</span></span>  |  <span data-ttu-id="24294-156">Фотозапись и Видеокаптуре</span><span class="sxs-lookup"><span data-stu-id="24294-156">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="24294-157">Пиктуреслибрари/Видеослибрари</span><span class="sxs-lookup"><span data-stu-id="24294-157">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="24294-158">Фотозахват или Видеокаптуре, соответственно (при сохранении захваченного содержимого);</span><span class="sxs-lookup"><span data-stu-id="24294-158">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="24294-159">микрофон</span><span class="sxs-lookup"><span data-stu-id="24294-159">Microphone</span></span>  |  <span data-ttu-id="24294-160">Видеокаптуре (при записи звука), Диктатионрекогнизер, Граммаррекогнизер и Кэйвордрекогнизер</span><span class="sxs-lookup"><span data-stu-id="24294-160">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="24294-161">InternetClient</span><span class="sxs-lookup"><span data-stu-id="24294-161">InternetClient</span></span>  |  <span data-ttu-id="24294-162">Диктатионрекогнизер (и использование профилировщика Unity)</span><span class="sxs-lookup"><span data-stu-id="24294-162">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="24294-163">Параметры качества</span><span class="sxs-lookup"><span data-stu-id="24294-163">Quality settings</span></span>

<span data-ttu-id="24294-164">HoloLens имеет графический процессор класса для мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="24294-164">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="24294-165">Если приложение предназначено для HoloLens, необходимо начать с параметров качества в приложении, настроенных для обеспечения максимальной производительности, чтобы обеспечить полную скорость кадров.</span><span class="sxs-lookup"><span data-stu-id="24294-165">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="24294-166">После того, как вы научитесь выполнять разработку, вы можете рассмотреть возможность проверки связи с параметрами качества, чтобы найти правильный баланс качества и производительности.</span><span class="sxs-lookup"><span data-stu-id="24294-166">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="24294-167">Выберите **изменить > параметры проекта > качество**</span><span class="sxs-lookup"><span data-stu-id="24294-167">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="24294-168">Выберите **раскрывающийся список** в эмблеме  **магазина Windows**   и выберите  **очень низкий**.</span><span class="sxs-lookup"><span data-stu-id="24294-168">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="24294-169">Вы узнаете, что параметр применяется правильно, если ячейка в столбце магазина Windows и очень низкая строка имеет значение зеленый.</span><span class="sxs-lookup"><span data-stu-id="24294-169">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="24294-170">В разделе **Shadows (тени**   ) выберите **Disable Shadows (отключить тени** ).</span><span class="sxs-lookup"><span data-stu-id="24294-170">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="24294-171">![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом параметров качества](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="24294-171">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="24294-172">*Параметры качества Unity*</span><span class="sxs-lookup"><span data-stu-id="24294-172">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="24294-173">Параметры на сцене</span><span class="sxs-lookup"><span data-stu-id="24294-173">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="24294-174">Параметры камеры Unity</span><span class="sxs-lookup"><span data-stu-id="24294-174">Unity camera settings</span></span>

<span data-ttu-id="24294-175">Если установлен флажок с **поддержкой Virtual Reality** , компонент [камеры Unity](camera-in-unity.md) обрабатывает [Отслеживание Head и отрисовку стереоскопик](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="24294-175">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="24294-176">Это означает, что вам не нужно заменять основной объект Camera на пользовательскую камеру.</span><span class="sxs-lookup"><span data-stu-id="24294-176">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="24294-177">Если приложение предназначено для HoloLens в частности, необходимо изменить несколько параметров, чтобы оптимизировать отображение прозрачных экранов устройства.</span><span class="sxs-lookup"><span data-stu-id="24294-177">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="24294-178">Эти параметры позволяют пропускать все, что можно сделать в отношении физического мира:</span><span class="sxs-lookup"><span data-stu-id="24294-178">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="24294-179">В **иерархии** выберите **основную камеру** .</span><span class="sxs-lookup"><span data-stu-id="24294-179">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="24294-180">На панели **инспектора** задайте для параметра **положение** преобразования значение **0, 0, 0,** чтобы расположение заголовка пользователя начиналось в точке мира Unity.</span><span class="sxs-lookup"><span data-stu-id="24294-180">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="24294-181">Замените **clear flags** на **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="24294-181">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="24294-182">Измените цвет **фона** на **RGBA 0, 0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="24294-182">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="24294-183">Черный цвет отображается как прозрачный в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="24294-183">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="24294-184">Изменение **обтравочных плоскостей — приближается** к [HoloLens, рекомендуемому](camera-in-unity.md#clip-planes) 0,85 (метрах).</span><span class="sxs-lookup"><span data-stu-id="24294-184">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="24294-185">![Снимок экрана: вкладка инспектора открыта в редакторе Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="24294-185">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="24294-186">*Параметры камеры Unity*</span><span class="sxs-lookup"><span data-stu-id="24294-186">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24294-187">Если вы удалите и создадите новую камеру, убедитесь, что новая камера помечена как **маинкамера**.</span><span class="sxs-lookup"><span data-stu-id="24294-187">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="24294-188">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="24294-188">Next steps</span></span>

<span data-ttu-id="24294-189">Теперь, когда проект готов, вы можете приступить к разработке среды смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="24294-189">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="24294-190">Добавление [основных стандартных блоков](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="24294-190">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="24294-191">Ознакомьтесь с доступными [возможностями платформы и интерфейсами API](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="24294-191">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="24294-192">Сведения о [развертывании приложения](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="24294-192">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="24294-193">Использование [симулятора смешанной реальности](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="24294-193">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="24294-194">См. также статью</span><span class="sxs-lookup"><span data-stu-id="24294-194">See also</span></span>
* [<span data-ttu-id="24294-195">Установка средств</span><span class="sxs-lookup"><span data-stu-id="24294-195">Install the tools</span></span>](../install-the-tools.md)