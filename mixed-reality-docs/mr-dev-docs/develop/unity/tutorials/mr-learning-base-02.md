---
title: Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ff479df81316ab5ceeabf045ad1bbae007190ed4
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238153"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="9f814-104">2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="9f814-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="9f814-105">Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="9f814-106">Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9f814-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="9f814-107">Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9f814-108">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="9f814-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="9f814-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="9f814-109">Objectives</span></span>

* <span data-ttu-id="9f814-110">Узнайте, как настроить Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="9f814-111">Узнайте, как создать и развернуть приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="9f814-112">Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9f814-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9f814-113">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="9f814-113">Creating the Unity project</span></span>

<span data-ttu-id="9f814-114">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="9f814-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub с выделенной кнопкой создания](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="9f814-116">В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="9f814-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub с раскрывающимся селектором версии NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="9f814-118">Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="9f814-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="9f814-119">В окне Create a new project (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="9f814-119">In the Create a new project window:</span></span>

* <span data-ttu-id="9f814-120">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="9f814-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="9f814-121">Укажите понятное **имя проекта**, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="9f814-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="9f814-122">Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="9f814-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="9f814-123">Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="9f814-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub с окном создания проекта с внесенными данными](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9f814-125">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="9f814-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="9f814-126">Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.</span><span class="sxs-lookup"><span data-stu-id="9f814-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="9f814-127">Подождите, пока Unity создаст проект:</span><span class="sxs-lookup"><span data-stu-id="9f814-127">Wait for Unity to create the project:</span></span>

![Unity выполняет создание проекта](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="9f814-129">Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="9f814-129">Switching the build platform</span></span>

<span data-ttu-id="9f814-130">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="9f814-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="9f814-132">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="9f814-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="9f814-134">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="9f814-134">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="9f814-136">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="9f814-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Окно сборки Unity с выделенным значком закрытия](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="9f814-138">Импорт требуемых ресурсов TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="9f814-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="9f814-139">В меню Unity выберите **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP), чтобы открыть окно Import Unity Package (Импорт пакета Unity):</span><span class="sxs-lookup"><span data-stu-id="9f814-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="9f814-141">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="9f814-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="9f814-143">Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="9f814-144">Этот шаг можно пропустить, если вы не планируете использовать элементы пользовательского интерфейса MRTK в проекте.</span><span class="sxs-lookup"><span data-stu-id="9f814-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="9f814-145">Импорт набора средств для смешанной реальности (MRTK)</span><span class="sxs-lookup"><span data-stu-id="9f814-145">Importing the Mixed Reality Toolkit</span></span>

### <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="9f814-146">Использование Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="9f814-146">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="9f814-147">Чтобы установить MRTK с помощью нашего нового приложения Mixed Reality Feature Tool, следуйте [инструкциям по установке и использованию](../welcome-to-mr-feature-tool.md) и выберите пакет **Mixed Reality Toolkit Foundation** в категории Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="9f814-147">To install MRTK with our new Mixed Reality Feature Tool application, follow our [installation and usage instructions](../welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

### <a name="using-unity-packages"></a><span data-ttu-id="9f814-148">Использование пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="9f814-148">Using Unity Packages</span></span>

<span data-ttu-id="9f814-149">Чтобы установить MRTK с пользовательским пакетом, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9f814-149">To install MRTK with a custom package:</span></span>

* [<span data-ttu-id="9f814-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9f814-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="9f814-151">В меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:</span><span class="sxs-lookup"><span data-stu-id="9f814-151">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Выбор импорта пользовательского пакета в меню Unity](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="9f814-153">В окне Import package (Импорт пакета) выберите скачанный файл **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** и нажмите кнопку **Open** (Открыть):</span><span class="sxs-lookup"><span data-stu-id="9f814-153">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![Окно с запросом открытия пользовательского пакета при импорте в Unity](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="9f814-155">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="9f814-155">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Окно импорта MRTK Foundation в Unity](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="9f814-157">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="9f814-157">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="9f814-158">1. Применение параметров конфигуратора проекта MRTK</span><span class="sxs-lookup"><span data-stu-id="9f814-158">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="9f814-159">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-159">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="9f814-160">В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).</span><span class="sxs-lookup"><span data-stu-id="9f814-160">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="9f814-162">В окне конфигуратора проектов MRTK разверните раздел **Modify Configurations** (Изменение конфигураций), убедитесь, что все флажки включены, и нажмите кнопку **Apply**(Применить), чтобы применить эти параметры:</span><span class="sxs-lookup"><span data-stu-id="9f814-162">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="9f814-164">Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:</span><span class="sxs-lookup"><span data-stu-id="9f814-164">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="9f814-165">Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки.</span><span class="sxs-lookup"><span data-stu-id="9f814-165">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="9f814-166">Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).</span><span class="sxs-lookup"><span data-stu-id="9f814-166">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="9f814-167">Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9f814-167">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="9f814-168">Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).</span><span class="sxs-lookup"><span data-stu-id="9f814-168">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="9f814-169">2. Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="9f814-169">2. Configure additional project settings</span></span>

<span data-ttu-id="9f814-170">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="9f814-170">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Выбор в меню параметров проекта Unity](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="9f814-172">В окне Project Settings (Параметры проекта) выберите **XR Plug-in Management (Управление подключаемым модулем смешанной реальности)**  > **Install XR Plug-in Management (Установить пакет для управления подключаемым модулем смешанной реальности)** :</span><span class="sxs-lookup"><span data-stu-id="9f814-172">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Параметры проекта с выбранным разделом XR Plugin Management (Управление подключаемым модулем смешанной реальности)](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="9f814-174">После установки пакета для управления подключаемым модулем смешанной реальности в Unity сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="9f814-174">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="9f814-175">Убедитесь, что вы выбрали параметр Universal Windows Platform (Универсальная платформа Windows) и установите флажок Initialize XR on Startup (Инициализировать смешанную реальность при запуске).</span><span class="sxs-lookup"><span data-stu-id="9f814-175">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Настройка управления подключаемым модулем смешанной реальности в Unity](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="9f814-177">В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), щелкните значок **+** и выберите Windows Mixed Reality, чтобы добавить пакет SDK для Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="9f814-177">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Параметры смешанной реальности Unity с выбранным меню для добавления пакета SDK Windows Mixed Reality](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="9f814-179">Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-179">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="9f814-180">Если этого не произошло, откройте его в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="9f814-180">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="9f814-181">В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:</span><span class="sxs-lookup"><span data-stu-id="9f814-181">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Окно конфигуратора проектов MRTK с выделенным свойством аудиоспатиалайзера](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="9f814-183">Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте.</span><span class="sxs-lookup"><span data-stu-id="9f814-183">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="9f814-184">Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity.</span><span class="sxs-lookup"><span data-stu-id="9f814-184">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="9f814-185">Дополнительные сведения см. в <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.</span><span class="sxs-lookup"><span data-stu-id="9f814-185">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="9f814-186">В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):</span><span class="sxs-lookup"><span data-stu-id="9f814-186">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Включение 16-разрядной глубины в Unity](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="9f814-188">Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="9f814-188">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="9f814-189">Дополнительные сведения см. в разделе <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">производительности MRTK</a>.</span><span class="sxs-lookup"><span data-stu-id="9f814-189">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="9f814-190">В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="9f814-190">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Параметры публикации Unity с настроенным именем пакета](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="9f814-192">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="9f814-192">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="9f814-193">Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="9f814-193">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="9f814-194">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-194">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="9f814-195">Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="9f814-195">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="9f814-196">Создание и настройка сцены</span><span class="sxs-lookup"><span data-stu-id="9f814-196">Creating and configuring the scene</span></span>

<span data-ttu-id="9f814-197">Чтобы создать сцену, в меню Unity выберите **File** > **New Scene** (Файл > Новая сцена):</span><span class="sxs-lookup"><span data-stu-id="9f814-197">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="9f814-199">В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:</span><span class="sxs-lookup"><span data-stu-id="9f814-199">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="9f814-201">Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), убедитесь, что профиль конфигурации **MixedRealityToolkit** имеет значение **DefaultMixedRealityToolkitConfigurationProfile** в окне Inspector (Инспектор):</span><span class="sxs-lookup"><span data-stu-id="9f814-201">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="9f814-203">В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:</span><span class="sxs-lookup"><span data-stu-id="9f814-203">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="9f814-205">В окне сохранения сцены перейдите к папке **Scenes** проекта, присвойте сцене понятное имя, например _GettingStarted_, и нажмите кнопку **Save** (Сохранить), чтобы сохранить сцену:</span><span class="sxs-lookup"><span data-stu-id="9f814-205">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="9f814-207">Создание приложения в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9f814-207">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="9f814-208">1. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="9f814-208">1. Build the Unity project</span></span>

<span data-ttu-id="9f814-209">В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="9f814-209">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="9f814-210">В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="9f814-210">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Окно параметров сборки Unity с выбранным вариантом UWP](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="9f814-212">В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="9f814-212">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="9f814-214">Подождите, пока Unity завершит сборку:</span><span class="sxs-lookup"><span data-stu-id="9f814-214">Wait for Unity to finish the build process:</span></span>

![Unity выполняет сборку](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="9f814-216">2. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="9f814-216">2. Build and deploy the application</span></span>

<span data-ttu-id="9f814-217">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="9f814-217">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="9f814-218">Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="9f814-218">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Проводник Windows с выбранным созданным решением Visual Studio](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9f814-220">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="9f814-220">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="9f814-221">Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):</span><span class="sxs-lookup"><span data-stu-id="9f814-221">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Среда Visual Studio, настроенная для развертывания в HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="9f814-223">Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.</span><span class="sxs-lookup"><span data-stu-id="9f814-223">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="9f814-224">В HoloLens обычно выполняется сборка для архитектуры ARM.</span><span class="sxs-lookup"><span data-stu-id="9f814-224">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="9f814-225">Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f814-225">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="9f814-226">Рекомендуемое решение — выполните сборку для ARM64.</span><span class="sxs-lookup"><span data-stu-id="9f814-226">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="9f814-227">Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.</span><span class="sxs-lookup"><span data-stu-id="9f814-227">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="9f814-228">Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP.</span><span class="sxs-lookup"><span data-stu-id="9f814-228">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="9f814-229">Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="9f814-229">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="9f814-230">Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:</span><span class="sxs-lookup"><span data-stu-id="9f814-230">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="9f814-232">Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="9f814-232">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="9f814-233">Оба эти действия можно выполнить, следуя [этим инструкциям](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9f814-233">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="9f814-234">Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.</span><span class="sxs-lookup"><span data-stu-id="9f814-234">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="9f814-235">Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f814-235">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="9f814-236">Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="9f814-236">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="9f814-237">В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="9f814-237">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="9f814-238">В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность.</span><span class="sxs-lookup"><span data-stu-id="9f814-238">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="9f814-239">Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="9f814-239">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9f814-240">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9f814-240">Congratulations</span></span>

<span data-ttu-id="9f814-241">Вы развернули свое первое приложение HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-241">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="9f814-242">Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f814-242">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9f814-243">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="9f814-243">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="9f814-244">Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-244">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="9f814-245">В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f814-245">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f814-246">Следующее руководство: 3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="9f814-246">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)