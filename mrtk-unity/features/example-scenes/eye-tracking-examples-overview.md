---
title: Обзор примера отслеживания взгляда
description: Пример создания эйетраккинг в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144685"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="596f6-104">Примеры отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="596f6-104">Eye tracking examples</span></span>

<span data-ttu-id="596f6-105">В этом разделе описывается, как быстро приступить к работе с отслеживанием взгляда в МРТК, создав МРТК примеры отслеживания взглядов (Asset/МРТК/examples/демонстрация/Эйетраккинг).</span><span class="sxs-lookup"><span data-stu-id="596f6-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="596f6-106">Эти примеры позволяют увидеть одну из наших новых возможностей ввода Magical: **Отслеживание глаз**!</span><span class="sxs-lookup"><span data-stu-id="596f6-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="596f6-107">Демонстрация включает в себя различные варианты использования, от неявных активаций на основе взгляда до того, как легко объединять информацию о том, что вы видите с помощью **голоса** и **руки** .</span><span class="sxs-lookup"><span data-stu-id="596f6-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="596f6-108">Это позволяет пользователям быстро и без труда выбирать и перемещать holographic содержимое в своем представлении, просто просматривая цель и произнося _«SELECT»_ или выполнив жест руки.</span><span class="sxs-lookup"><span data-stu-id="596f6-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="596f6-109">В демонстрационных роликах также содержится пример прокрутки, панорамы и масштабирования текста и изображений на планшете.</span><span class="sxs-lookup"><span data-stu-id="596f6-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="596f6-110">Наконец, приведен пример для записи и визуализации визуального внимания пользователя на 2D-планшете.</span><span class="sxs-lookup"><span data-stu-id="596f6-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="596f6-111">В следующем разделе вы найдете дополнительные сведения о том, какие из различных примеров в примере пакета отслеживания взгляда МРТК (Assets/МРТК/examples/Samples/Эйетраккинг) включают:</span><span class="sxs-lookup"><span data-stu-id="596f6-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Список сцен отслеживания взгляда](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="596f6-113">В следующем разделе приведены краткие сведения о том, что представляют собой демонстрационные сцены индивидуального отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="596f6-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="596f6-114">Демонстрационные сцены отслеживания взгляда МРТК [загружаются аддитивным](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), что мы объясним ниже, как настроить.</span><span class="sxs-lookup"><span data-stu-id="596f6-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="596f6-115">Обзор демонстрационных примеров по отслеживанию взглядов</span><span class="sxs-lookup"><span data-stu-id="596f6-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="596f6-116">**Глаз — поддерживаемый Выбор целевого объекта**</span><span class="sxs-lookup"><span data-stu-id="596f6-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="596f6-117">В этом учебнике демонстрируется простота доступа к данным взгляда на выбор целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="596f6-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="596f6-118">Он содержит пример для незаметной, но мощной обратной связи, чтобы предоставить пользователю уверенность в том, что целевой объект не является огромным.</span><span class="sxs-lookup"><span data-stu-id="596f6-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="596f6-119">Кроме того, существует простой пример интеллектуальных уведомлений, которые автоматически исчезают после чтения.</span><span class="sxs-lookup"><span data-stu-id="596f6-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="596f6-120">**Сводка**: быстрый и простой выбор целевых объектов с помощью сочетания глаз, голоса и руки ввода.</span><span class="sxs-lookup"><span data-stu-id="596f6-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="596f6-121">**Поддерживаемая Навигация**</span><span class="sxs-lookup"><span data-stu-id="596f6-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="596f6-122">Представьте, что вы читаете какую-либо информацию на удаленном дисплее или на устройстве чтения, а когда дойдете до конца отображаемого текста, текст автоматически прокручивается, чтобы показать больше содержимого.</span><span class="sxs-lookup"><span data-stu-id="596f6-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="596f6-123">Или как насчет волшебного масштабирования непосредственно в сторону того, где вы искали?</span><span class="sxs-lookup"><span data-stu-id="596f6-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="596f6-124">Ниже приведены некоторые примеры, представленные в этом учебнике для навигации с поддержкой взгляда.</span><span class="sxs-lookup"><span data-stu-id="596f6-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="596f6-125">Кроме того, есть пример, позволяющий бесплатно вращать трехмерные голограммы, автоматически поворачивать их в соответствии с текущим фокусом.</span><span class="sxs-lookup"><span data-stu-id="596f6-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="596f6-126">**Сводка**: прокрутка, сдвиг, масштаб, трехмерное вращение с помощью сочетания глаз, голоса и руки ввода.</span><span class="sxs-lookup"><span data-stu-id="596f6-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="596f6-127">**Позиционирование с поддержкой глаз**</span><span class="sxs-lookup"><span data-stu-id="596f6-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="596f6-128">В этом учебнике показан входной сценарий с названием «датировано» [,](https://youtu.be/CbIn8p4_4CQ) с помощью которого можно вернуться к исследованию из лаборатории мультимедиа MIT в начале 1980 с глазом, рукой и голосовым входом.</span><span class="sxs-lookup"><span data-stu-id="596f6-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="596f6-129">Идея проста: Воспользуйтесь преимуществами ваших глаз для быстрого выбора целевых объектов и позиционирования.</span><span class="sxs-lookup"><span data-stu-id="596f6-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="596f6-130">Просто взгляните на голограмму и скажите _«поместить сюда_», Взгляните на место, где вы хотите его разместить, и скажите _«!»_.</span><span class="sxs-lookup"><span data-stu-id="596f6-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="596f6-131">Для более точного размещения голограммы можно использовать дополнительные входные данные из руки, голоса или контроллеров.</span><span class="sxs-lookup"><span data-stu-id="596f6-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="596f6-132">**Сводка**: размещение голограмм с помощью глаз, голоса и руки (*перетаскивание*).</span><span class="sxs-lookup"><span data-stu-id="596f6-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="596f6-133">Поддерживаемые в глаза ползунки с использованием глаз + руки.</span><span class="sxs-lookup"><span data-stu-id="596f6-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="596f6-134">**Визуализация визуального внимания**</span><span class="sxs-lookup"><span data-stu-id="596f6-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="596f6-135">Данные в зависимости от того, где пользователи выглядят, делают чрезвычайно мощным средством для оценки удобства использования проекта и выявления проблем в эффективных рабочих потоках.</span><span class="sxs-lookup"><span data-stu-id="596f6-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="596f6-136">В этом учебнике рассматриваются различные визуализации отслеживания взгляда и их соответствие различным потребностям.</span><span class="sxs-lookup"><span data-stu-id="596f6-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="596f6-137">Мы предоставляем основные примеры для ведения журнала и загрузки данных отслеживания взгляда и примеры их визуализации.</span><span class="sxs-lookup"><span data-stu-id="596f6-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="596f6-138">**Сводка**. двухмерная схема внимания (тепловые карты) на планшетах.</span><span class="sxs-lookup"><span data-stu-id="596f6-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="596f6-139">Запись & воспроизведением данных отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="596f6-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="596f6-140">Настройка образцов отслеживания взгляда МРТК</span><span class="sxs-lookup"><span data-stu-id="596f6-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="596f6-141">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="596f6-141">Prerequisites</span></span>

<span data-ttu-id="596f6-142">Обратите внимание, что для использования примеров отслеживания взгляда на устройстве требуется HoloLens 2 и пример пакета приложения, построенный с помощью функции "взгляд ввода", в AppXManifest пакета.</span><span class="sxs-lookup"><span data-stu-id="596f6-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="596f6-143">Чтобы использовать эти образцы отслеживания взгляда на устройстве, перед созданием приложения в Visual Studio обязательно выполните следующие [действия](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) .</span><span class="sxs-lookup"><span data-stu-id="596f6-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="596f6-144">1. Load Эйетраккингдемо-00-Рутсцене. Unity</span><span class="sxs-lookup"><span data-stu-id="596f6-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="596f6-145">*Эйетраккингдемо-00-рутсцене* — это базовая (_корневая_) сцена, в которую входят все основные компоненты мртк.</span><span class="sxs-lookup"><span data-stu-id="596f6-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="596f6-146">Это сцена, которую необходимо загрузить в первую очередь и из которой будут запускаться демонстрации отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="596f6-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="596f6-147">Он содержит графическое меню сцены, позволяющее легко переключаться между различными образцами отслеживания взгляда, которые будут [загружаться аддитивно](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span><span class="sxs-lookup"><span data-stu-id="596f6-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Меню "сцена" в примере "Отслеживание глаз"](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="596f6-149">В корневой сцене содержится несколько основных компонентов, которые будут сохраняться во всех аддитивных сценах, таких как настроенные профили МРТК и камера сцены.</span><span class="sxs-lookup"><span data-stu-id="596f6-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="596f6-150">_Микседреалитибасиксценесетуп_ (см. снимок экрана ниже) включает сценарий, который автоматически загружает сцену, на которую указывает ссылка при запуске.</span><span class="sxs-lookup"><span data-stu-id="596f6-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="596f6-151">По умолчанию это _эйетраккингдемо-02-таржетселектион_.</span><span class="sxs-lookup"><span data-stu-id="596f6-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Пример сценария Онлоадстартсцене](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="596f6-153">2. добавление сцен в меню "сборка"</span><span class="sxs-lookup"><span data-stu-id="596f6-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="596f6-154">Чтобы загрузить Аддитивные сцены во время выполнения, необходимо добавить эти сцены в _параметры сборки — сначала > сцены в меню Сборка_ .</span><span class="sxs-lookup"><span data-stu-id="596f6-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="596f6-155">Важно, чтобы корневая сцена отображалась в виде первой сцены в списке:</span><span class="sxs-lookup"><span data-stu-id="596f6-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Меню сцены параметров сборки для образцов отслеживания взгляда](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="596f6-157">3. Воспроизведение образцов отслеживания взгляда в редакторе Unity</span><span class="sxs-lookup"><span data-stu-id="596f6-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="596f6-158">После добавления сцен отслеживания взгляда в параметры сборки и загрузки _эйетраккингдемо-00-рутсцене_ есть еще одна вещь, которую вы можете проверить: — это сценарий _онлоадстартсцене_ , присоединенный к _микседреалитибасиксценесетуп_ GameObject.</span><span class="sxs-lookup"><span data-stu-id="596f6-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="596f6-159">Это позволяет корневой сцене понять, какая демонстрационная сцена должна быть загружена в первую очередь.</span><span class="sxs-lookup"><span data-stu-id="596f6-159">This is to let the root scene know which demo scene to load first.</span></span>

![Пример скрипта OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="596f6-161">Поехали!</span><span class="sxs-lookup"><span data-stu-id="596f6-161">Let's roll!</span></span> <span data-ttu-id="596f6-162">Нажмите _"Воспроизвести"_!</span><span class="sxs-lookup"><span data-stu-id="596f6-162">Hit _"Play"_!</span></span>
<span data-ttu-id="596f6-163">Должно отобразиться несколько драгоценных камней, а в верхней части — меню сцены.</span><span class="sxs-lookup"><span data-stu-id="596f6-163">You should see several gems appear and the scene menu at the top.</span></span>

![Пример снимка экрана с целевым объектом ET выбор сцены](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="596f6-165">Кроме того, обратите внимание на небольшой полупрозрачный круг в центре игрового представления.</span><span class="sxs-lookup"><span data-stu-id="596f6-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="596f6-166">Это является индикатором (курсором) _имитации глаз_: просто нажмите _правую кнопку мыши_ и наведите указатель мыши, чтобы изменить его положение.</span><span class="sxs-lookup"><span data-stu-id="596f6-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="596f6-167">Когда курсор наведен на драгоценные камни, вы заметите, что он будет привязан к центру текущего драгоценного камень.</span><span class="sxs-lookup"><span data-stu-id="596f6-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="596f6-168">Это отличный способ проверки, если события запускаются ожидаемым образом при _поиске_ на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="596f6-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="596f6-169">Имейте в виду, что _имитация взгляда_ с помощью мыши — это довольно неплохое дополнение к нашим быстрому и непреднамеренному перемещению глаз.</span><span class="sxs-lookup"><span data-stu-id="596f6-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="596f6-170">Однако это очень удобно для тестирования базовой функциональности перед итерацией проекта, развернув его на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="596f6-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="596f6-171">Возврат к нашему образцу сцены отслеживания взгляда: драгоценный камень поворачивается, пока он просматривается и может быть уничтожен «поиском» в нем и...</span><span class="sxs-lookup"><span data-stu-id="596f6-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="596f6-172">Нажатие клавиши _Ввод_ (имитируется с произнесением "Select")</span><span class="sxs-lookup"><span data-stu-id="596f6-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="596f6-173">Слово _"выбрать"_ в микрофон</span><span class="sxs-lookup"><span data-stu-id="596f6-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="596f6-174">Удерживая нажатой клавишу _пробел_ для отображения имитации руки, нажмите левую кнопку мыши, чтобы выполнить имитацию сжатия.</span><span class="sxs-lookup"><span data-stu-id="596f6-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="596f6-175">Мы подробно рассмотрим, как можно достичь этих взаимодействий в учебнике [**Выбор целевого объекта с поддержкой взгляда**](../input/eye-tracking/eye-tracking-target-selection.md) .</span><span class="sxs-lookup"><span data-stu-id="596f6-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="596f6-176">При перемещении курсора вверх в верхнюю строку меню сцены вы заметите, что элемент, находящегося под указателем, выделит немного.</span><span class="sxs-lookup"><span data-stu-id="596f6-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="596f6-177">Выделенный в данный момент элемент можно выбрать с помощью одного из описанных выше методов фиксации (например, нажатием клавиши _Ввод_).</span><span class="sxs-lookup"><span data-stu-id="596f6-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="596f6-178">Таким образом можно переключаться между различными примерами сцен отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="596f6-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="596f6-179">4. тестирование конкретных подмонтажных кадров</span><span class="sxs-lookup"><span data-stu-id="596f6-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="596f6-180">При работе с конкретным сценарием Вы можете не захотеть использовать меню "сцена" каждый раз.</span><span class="sxs-lookup"><span data-stu-id="596f6-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="596f6-181">Вместо этого может потребоваться запустить непосредственно из сцены, над которой вы работаете в данный момент при нажатии кнопки _воспроизведения_ .</span><span class="sxs-lookup"><span data-stu-id="596f6-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="596f6-182">Это не проблема!</span><span class="sxs-lookup"><span data-stu-id="596f6-182">No problem!</span></span> <span data-ttu-id="596f6-183">Вот что можно сделать:</span><span class="sxs-lookup"><span data-stu-id="596f6-183">Here is what you can do:</span></span>

1. <span data-ttu-id="596f6-184">Загрузка _корневой_ сцены</span><span class="sxs-lookup"><span data-stu-id="596f6-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="596f6-185">В _корневой_ сцене отключите сценарий _"онлоадстартсцене"_ .</span><span class="sxs-lookup"><span data-stu-id="596f6-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="596f6-186">_Перетащите_ один из сцен теста отслеживания взгляда, описанный ниже (или любую другую сцену), в представление _иерархии_ , как показано на снимке экрана ниже.</span><span class="sxs-lookup"><span data-stu-id="596f6-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Пример для аддитивной сцены](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="596f6-188">Нажмите кнопку _Воспроизведение_</span><span class="sxs-lookup"><span data-stu-id="596f6-188">Press _Play_</span></span>

<span data-ttu-id="596f6-189">Обратите внимание, что загрузка вспомогательной сцены, например, не является постоянной: это означает, что при развертывании приложения на устройстве HoloLens 2 будет загружена только корневая сцена (предполагая, что она отображается в верхней части параметров сборки).</span><span class="sxs-lookup"><span data-stu-id="596f6-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="596f6-190">Кроме того, при совместном использовании проекта с другими пользователями подпрограммы не загружаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="596f6-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="596f6-191">Теперь, когда вы умеете работать с примерами МРТК для отслеживания взгляда, давайте продолжим углубляться в изучение того, как выбирать голограммы с глазами: [поддерживаемый Выбор целевого объекта](../input/eye-tracking/eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="596f6-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="596f6-192">Вернуться к "Отслеживание взглядов в Микседреалититулкит"</span><span class="sxs-lookup"><span data-stu-id="596f6-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
