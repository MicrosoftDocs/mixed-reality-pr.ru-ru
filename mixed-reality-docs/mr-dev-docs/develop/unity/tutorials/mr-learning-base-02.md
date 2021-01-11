---
title: Руководства по MRTK — 2 Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859533"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="0b22d-105">2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="0b22d-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="0b22d-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="0b22d-106">Overview</span></span>

<span data-ttu-id="0b22d-107">Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b22d-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="0b22d-108">Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0b22d-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="0b22d-109">Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="0b22d-110">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="0b22d-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="0b22d-111">Задачи</span><span class="sxs-lookup"><span data-stu-id="0b22d-111">Objectives</span></span>

* <span data-ttu-id="0b22d-112">Узнайте, как настроить Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="0b22d-113">Узнайте, как создать и развернуть приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="0b22d-114">Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0b22d-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="0b22d-115">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="0b22d-115">Creating the Unity project</span></span>

1. <span data-ttu-id="0b22d-116">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты), а затем щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="0b22d-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Unity Hub с выделенной стрелкой вниз для кнопки "Создать"](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="0b22d-118">В раскрывающемся списке выберите версию Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="0b22d-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Выбор версии Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="0b22d-120">Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="0b22d-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="0b22d-121">В окне **Create a new project** (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0b22d-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="0b22d-122">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="0b22d-123">В поле **Project Name** (Имя проекта) введите подходящее имя для проекта (например, "MRTK Tutorials").</span><span class="sxs-lookup"><span data-stu-id="0b22d-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="0b22d-124">Нажмите кнопку с тремя точками рядом с элементом **Location** (Расположение), а затем перейдите к папке, в которой нужно сохранить проект.</span><span class="sxs-lookup"><span data-stu-id="0b22d-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="0b22d-125">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="0b22d-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="0b22d-126">Поэтому проект Unity желательно сохранять ближе к корневому каталогу диска.</span><span class="sxs-lookup"><span data-stu-id="0b22d-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="0b22d-127">Нажмите кнопку **Создать** .</span><span class="sxs-lookup"><span data-stu-id="0b22d-127">Click the **Create** button.</span></span> <span data-ttu-id="0b22d-128">Будет создан и запущен новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="0b22d-128">This creates and launches your new Unity project.</span></span>

![Unity Hub с указанными значениями в окне "Create a new project" (Создание нового проекта)](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="0b22d-130">Строка состояния позволяет отслеживать ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="0b22d-130">The status bar keeps you updated on your progress.</span></span>

![Индикатор выполнения Unity постоянно информирует вас о состоянии процесса создания проекта](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="0b22d-132">Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="0b22d-132">Switching the build platform</span></span>

1. <span data-ttu-id="0b22d-133">В строке меню выберите **File** > **Build Settings...** (Файл > Параметры сборки...).</span><span class="sxs-lookup"><span data-stu-id="0b22d-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="0b22d-135">В окне **Build Settings** (Параметры сборки) щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу).</span><span class="sxs-lookup"><span data-stu-id="0b22d-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="0b22d-137">Дождитесь, пока Unity завершит переключение платформы, а затем закройте окно **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="0b22d-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="0b22d-138">Импорт требуемых ресурсов TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="0b22d-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="0b22d-139">Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b22d-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="0b22d-140">Этот шаг можно пропустить, если вы не намерены использовать элементы пользовательского интерфейса MRTK в проекте.</span><span class="sxs-lookup"><span data-stu-id="0b22d-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="0b22d-141">На панели меню щелкните **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP):</span><span class="sxs-lookup"><span data-stu-id="0b22d-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="0b22d-143">В окне **Import Unity Package** (Импорт пакета Unity) нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их:</span><span class="sxs-lookup"><span data-stu-id="0b22d-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="0b22d-145">Импорт набора средств для смешанной реальности (MRTK)</span><span class="sxs-lookup"><span data-stu-id="0b22d-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="0b22d-146">Скачайте пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="0b22d-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="0b22d-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="0b22d-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="0b22d-148">В строке меню щелкните **Assets** > **Import Package** > **Custom Package...** (Активы > Импортировать пакеты > Пользовательский пакет...).</span><span class="sxs-lookup"><span data-stu-id="0b22d-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="0b22d-149">В диалоговом окне **Import package...** (Импорт пакета...) перейдите к расположению только что скачанного пакета, выберите его и нажмите кнопку **Open** (Открыть).</span><span class="sxs-lookup"><span data-stu-id="0b22d-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="0b22d-150">В окне **Import Unity Package** (Импорт пакета Unity) нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="0b22d-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="0b22d-151">Выбор MRTK и параметров проекта</span><span class="sxs-lookup"><span data-stu-id="0b22d-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="0b22d-152">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно **MRTK Project Configurator** (Конфигуратор проекта MRTK).</span><span class="sxs-lookup"><span data-stu-id="0b22d-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="0b22d-153">В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).</span><span class="sxs-lookup"><span data-stu-id="0b22d-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="0b22d-155">Если потребуется, в окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) разверните раздел **Modify Configurations** (Изменение конфигураций) и убедитесь, что выбраны все параметры.</span><span class="sxs-lookup"><span data-stu-id="0b22d-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Окно конфигуратора проекта MRTK, где отображается раздел Modify Configurations (Изменение конфигураций)](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="0b22d-157">Чтобы применить параметры, нажмите кнопку **Apply** (Применить).</span><span class="sxs-lookup"><span data-stu-id="0b22d-157">To apply the settings, click the **Apply** button.</span></span>

![Кнопка Apply (Применить) в MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="0b22d-159">Вы используете встроенные устаревшие возможности смешанной реальности в Unity, а не новую систему подключаемого модуля смешанной реальности, так как новая система не обеспечивает полную совместимость с [рекомендуемыми версиями Unity и MRTK](mr-learning-base-01.md#prerequisites), которые используются при работе с этой серией руководств.</span><span class="sxs-lookup"><span data-stu-id="0b22d-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="0b22d-160">Если поступят предупреждения об устаревании встроенных средств XR, их можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="0b22d-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="0b22d-161">Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:</span><span class="sxs-lookup"><span data-stu-id="0b22d-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="0b22d-162">Enable legacy XR (Включить традиционные возможности смешанной реальности): позволяет включить возможности виртуальной реальности для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="0b22d-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="0b22d-163">Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки.</span><span class="sxs-lookup"><span data-stu-id="0b22d-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="0b22d-164">Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).</span><span class="sxs-lookup"><span data-stu-id="0b22d-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="0b22d-165">Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="0b22d-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="0b22d-166">Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).</span><span class="sxs-lookup"><span data-stu-id="0b22d-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="0b22d-167">В строке меню выберите **Edit** > **Project Settings...** (Правка > Параметры проекта...).</span><span class="sxs-lookup"><span data-stu-id="0b22d-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="0b22d-168">В окне **Project Settings** (Параметры проекта) выберите элемент **Player** (Воспроизведение), затем откройте раскрывающийся список **XR Settings** (Параметры XR) и установите флажок рядом с параметром **Virtual Reality Supported** (Поддержка виртуальной реальности):</span><span class="sxs-lookup"><span data-stu-id="0b22d-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Параметры XR в Unity, где отображается флажок Virtual Reality Supported (Поддержка виртуальной реальности)](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="0b22d-170">Это действие позволяет импортировать пакет SDK для Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="0b22d-170">This imports the Windows Mixed Reality SDK:</span></span>

![Параметры XR в Unity, где отображаются пакеты SDK для виртуальной реальности](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="0b22d-172">Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно **MRTK Project Configurator** (Конфигуратор проекта MRTK).</span><span class="sxs-lookup"><span data-stu-id="0b22d-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="0b22d-173">Если окно не отображается, откройте его вручную. Для этого выберите элементы **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств смешанной реальности > Средства > Настройка проекта Unity).</span><span class="sxs-lookup"><span data-stu-id="0b22d-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="0b22d-174">В окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) щелкните раскрывающийся список **Audio spatializer** (Аудиоспатиалайзер) и выберите вариант **MS HRTF Spatializer** (Спатиалайзер MS HRTF).</span><span class="sxs-lookup"><span data-stu-id="0b22d-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Параметры проекта, где отображаются варианты аудиоспатиалайзера](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="0b22d-176">Нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-176">Click the **Apply** button.</span></span> <span data-ttu-id="0b22d-177">Окно **MRTK Project Configurator** (Конфигурация проекта MRTK) будет закрыто.</span><span class="sxs-lookup"><span data-stu-id="0b22d-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="0b22d-178">Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте.</span><span class="sxs-lookup"><span data-stu-id="0b22d-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="0b22d-179">Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity.</span><span class="sxs-lookup"><span data-stu-id="0b22d-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="0b22d-180">Дополнительные сведения см. в руководствах по пространственному звуку.</span><span class="sxs-lookup"><span data-stu-id="0b22d-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="0b22d-181">В окне **Project Settings** (Параметры проекта) щелкните раскрывающийся список **Depth Format** (Формат глубины) и выберите вариант **16-bit depth** (16-битная глубина).</span><span class="sxs-lookup"><span data-stu-id="0b22d-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Параметры XR в Unity с выбранной 16-битной глубиной.":::

    > [!TIP]
    > <span data-ttu-id="0b22d-183">Уменьшать разрядность глубины до 16 битов необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="0b22d-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="0b22d-184">Дополнительные сведения см. в разделе [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) (Совместное использование буфера глубины в HoloLens) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).</span><span class="sxs-lookup"><span data-stu-id="0b22d-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="0b22d-185">Щелкните раскрывающийся список **Publishing Settings** (Параметры публикации), а затем в поле **Package name** (Имя пакета) введите подходящее имя (например, "MRTK-Tutorials-Getting-Started").</span><span class="sxs-lookup"><span data-stu-id="0b22d-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Параметры публикации Unity с настроенным именем пакета":::

    <span data-ttu-id="0b22d-187">**Имя пакета и название продукта**</span><span class="sxs-lookup"><span data-stu-id="0b22d-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="0b22d-188">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="0b22d-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="0b22d-189">Создайте этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="0b22d-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="0b22d-190">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="0b22d-191">Чтобы упростить размещение приложения во время разработки, можно добавить перед именем символ подчеркивания, чтобы при сортировке это имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="0b22d-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Параметры проекта Unity с настроенным именем продукта.":::

9. <span data-ttu-id="0b22d-193">Закройте окно **Project Settings** (Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="0b22d-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="0b22d-194">Создание и настройка сцены</span><span class="sxs-lookup"><span data-stu-id="0b22d-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="0b22d-195">В строке меню выберите элементы **File** > **New Scene** (Файл > Новая сцена).</span><span class="sxs-lookup"><span data-stu-id="0b22d-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="0b22d-196">Чтобы добавить MRTK в текущую сцену, в строке меню щелкните элемент **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности >Добавить в сцену и настроить).</span><span class="sxs-lookup"><span data-stu-id="0b22d-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Путь в меню Unity &quot;Add to Scene and Configure...&quot; (Добавить в сцену и настроить)":::

3. <span data-ttu-id="0b22d-198">Убедитесь, что в окне **Hierarchy** (Иерархия) выбран элемент **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Убедитесь, что выбран элемент MixedRealityTookit.":::

4. <span data-ttu-id="0b22d-200">В окне **Inspector** (Инспектор), в разделе **MixedRealityToolkit** проверьте, установлен ли профиль конфигурации **DefaultMixedRealityToolkitConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile":::

    > [!IMPORTANT]
    > <span data-ttu-id="0b22d-202">Как правило, при разработке для HoloLens используется DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="0b22d-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="0b22d-203">Но для работы с этим руководством вы будете использовать DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="0b22d-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="0b22d-204">В следующем руководстве [Настройка профилей MRTK](mr-learning-base-03.md) вы измените это значение на DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="0b22d-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="0b22d-205">В строке меню выберите **File** > **Save As...** (Файл > Сохранить как).</span><span class="sxs-lookup"><span data-stu-id="0b22d-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="0b22d-206">В диалоговом окне **Save Scene** (Сохранение сцены) перейдите к папке проекта **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="0b22d-207">В поле **File name** (Имя файла) укажите подходящее имя сцены (например, \_GettingStarted\_) и нажмите кнопку **Save** (Сохранить).</span><span class="sxs-lookup"><span data-stu-id="0b22d-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Окно Unity с запросом на сохранение сцены":::.

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="0b22d-209">Сборка и развертывание для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0b22d-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="0b22d-210">Перед сборкой для устройства убедитесь, что выполняются следующие условия:</span><span class="sxs-lookup"><span data-stu-id="0b22d-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="0b22d-211">Устройство находится в режиме разработчика.</span><span class="sxs-lookup"><span data-stu-id="0b22d-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="0b22d-212">Устройство связано с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="0b22d-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="0b22d-213">Если это не так, в процессе сборки в Visual Studio отобразится следующее диалоговое окно:</span><span class="sxs-lookup"><span data-stu-id="0b22d-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Ввод ПИН-кода для связывания устройств](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="0b22d-215">Дополнительные сведения об этих действиях см. в статье [Развертывание и отладка с помощью Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0b22d-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="0b22d-216">В строке меню выберите **File** > **Build Settings...** (Файл > Параметры сборки...).</span><span class="sxs-lookup"><span data-stu-id="0b22d-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="0b22d-217">В окне **Build Settings** (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="0b22d-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Добавление текущей сцены в список Scenes In Build (Сцены в сборке)](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="0b22d-219">Нажмите кнопку **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Нажмите кнопку Сборка.":::

4. <span data-ttu-id="0b22d-221">В диалоговом окне **Build Universal Windows Platform** (Сборка для универсальной платформы Windows) выберите подходящее расположение для хранения сборки (например, создайте подпапку Builds в папке "MRTK Tutorials").</span><span class="sxs-lookup"><span data-stu-id="0b22d-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="0b22d-222">Создайте новую папку и присвойте ей подходящее имя (например, GettingStarted), выберите эту папку и нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="0b22d-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Окно сборки Unity, где отображается папка сборки.":::

    <span data-ttu-id="0b22d-224">Появится строка состояния с постоянно обновляемой информацией о ходе выполнения сборки.</span><span class="sxs-lookup"><span data-stu-id="0b22d-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Отображение сведений о состоянии сборки в Unity":::

    > [!TIP]
    > <span data-ttu-id="0b22d-226">Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.</span><span class="sxs-lookup"><span data-stu-id="0b22d-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="0b22d-227">Когда сборка завершится, в проводнике перейдите к расположению, где сохранена сборка, и двойным щелчком откройте файл решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b22d-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Проводник Windows с выбранным файлом решения Visual Studio":::

    > [!NOTE]
    > <span data-ttu-id="0b22d-229">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="0b22d-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="0b22d-230">Настройте Visual Studio для устройства HoloLens. Для этого выберите конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство).</span><span class="sxs-lookup"><span data-stu-id="0b22d-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="0b22d-231">Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Среда Visual Studio, настроенная для развертывания в HoloLens 2":::

    > [!NOTE]
    > <span data-ttu-id="0b22d-233">В HoloLens обычно выполняется сборка для архитектуры ARM.</span><span class="sxs-lookup"><span data-stu-id="0b22d-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="0b22d-234">Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b22d-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="0b22d-235">Рекомендуемое решение — выполните сборку для ARM64.</span><span class="sxs-lookup"><span data-stu-id="0b22d-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="0b22d-236">Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.</span><span class="sxs-lookup"><span data-stu-id="0b22d-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0b22d-237">Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP.</span><span class="sxs-lookup"><span data-stu-id="0b22d-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="0b22d-238">Для этого в обозревателе решений щелкните правой кнопкой мыши имя проекта (YourProjectName), в нашем примере это "Universal Windows", и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="0b22d-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="0b22d-239">Подключите HoloLens к локальному компьютеру и выполните одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="0b22d-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="0b22d-240">Чтобы скомпилировать приложение, развернуть его в HoloLens и автоматически запустить без отладчика Visual Studio, выберите в строке меню **Debug** > **Start Without Debugging** (Отладка > Начать без отладки).</span><span class="sxs-lookup"><span data-stu-id="0b22d-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio":::

- <span data-ttu-id="0b22d-242">Чтобы выполнить сборку и развертывание приложения в HoloLens, не запуская его автоматически, выберите в строке меню **Build > Deploy Solution** (Сборка > Развернуть решение).</span><span class="sxs-lookup"><span data-stu-id="0b22d-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="0b22d-243">В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="0b22d-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="0b22d-244">В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность.</span><span class="sxs-lookup"><span data-stu-id="0b22d-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="0b22d-245">Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="0b22d-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="0b22d-246">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0b22d-246">Congratulations</span></span>

<span data-ttu-id="0b22d-247">Вы развернули свое первое приложение HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="0b22d-248">Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b22d-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="0b22d-249">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="0b22d-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="0b22d-250">Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b22d-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="0b22d-251">В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b22d-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b22d-252">Следующее руководство: 3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="0b22d-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
