---
title: Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: b0b8d97471dfae9d6dc6bbee26079af04f97de62
ms.sourcegitcommit: 94ae851f78e5b861af601b445f8f0a3405197c40
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107716025"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="ad42d-104">2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="ad42d-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="ad42d-105">Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad42d-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="ad42d-106">Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ad42d-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="ad42d-107">Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad42d-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="ad42d-108">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="ad42d-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="ad42d-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="ad42d-110">Objectives</span></span>

* <span data-ttu-id="ad42d-111">Узнайте, как настроить Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad42d-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="ad42d-112">Узнайте, как создать и развернуть приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad42d-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="ad42d-113">Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ad42d-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="ad42d-114">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="ad42d-114">Creating the Unity project</span></span>

<span data-ttu-id="ad42d-115">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="ad42d-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub с выделенной кнопкой создания](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="ad42d-117">В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="ad42d-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub с раскрывающимся селектором версии NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="ad42d-119">Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="ad42d-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="ad42d-120">В окне Create a new project (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ad42d-120">In the Create a new project window:</span></span>

* <span data-ttu-id="ad42d-121">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="ad42d-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="ad42d-122">Укажите понятное **имя проекта**, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="ad42d-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="ad42d-123">Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="ad42d-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="ad42d-124">Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="ad42d-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub с окном создания проекта с внесенными данными](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="ad42d-126">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="ad42d-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="ad42d-127">Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.</span><span class="sxs-lookup"><span data-stu-id="ad42d-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="ad42d-128">Подождите, пока Unity создаст проект:</span><span class="sxs-lookup"><span data-stu-id="ad42d-128">Wait for Unity to create the project:</span></span>

![Unity выполняет создание проекта](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="ad42d-130">Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="ad42d-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="ad42d-131">Импорт требуемых ресурсов TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="ad42d-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="ad42d-132">В меню Unity выберите **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP), чтобы открыть окно Import Unity Package (Импорт пакета Unity):</span><span class="sxs-lookup"><span data-stu-id="ad42d-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="ad42d-134">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="ad42d-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="ad42d-136">Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad42d-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="ad42d-137">Этот шаг можно пропустить, если вы не планируете использовать элементы пользовательского интерфейса MRTK в проекте.</span><span class="sxs-lookup"><span data-stu-id="ad42d-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="ad42d-138">Импорт набора средств для смешанной реальности (MRTK)</span><span class="sxs-lookup"><span data-stu-id="ad42d-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="ad42d-139">Чтобы импортировать Mixed Reality Toolkit в проект Unity, необходимо использовать [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), которое позволяет разработчикам обнаруживать, обновлять и добавлять пакеты компонентов Смешанной реальности в проекты Unity.</span><span class="sxs-lookup"><span data-stu-id="ad42d-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="ad42d-140">Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.</span><span class="sxs-lookup"><span data-stu-id="ad42d-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="ad42d-141">Скачайте последнюю версию средства Mixed Reality Feature Tool из [Центра загрузки Майкрософт](https://aka.ms/MRFeatureTool). По завершении скачивания разархивируйте файл и сохраните его на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="ad42d-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="ad42d-142">Перед запуском средства Mixed Reality Feature Tool установите [среду выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0).</span><span class="sxs-lookup"><span data-stu-id="ad42d-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="ad42d-143">Mixed Reality Feature Tool сейчас работает только в Windows. Для MacOS выполните [эту процедуру](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages), чтобы скачать и импортировать Mixed Reality Toolkit в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="ad42d-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="ad42d-144">Откройте исполняемый файл **MixedRealityFeatureTool** из скачанной папки, чтобы запустить Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ad42d-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Открытие MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="ad42d-146">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="ad42d-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="ad42d-147">1. Применение параметров конфигуратора проекта MRTK</span><span class="sxs-lookup"><span data-stu-id="ad42d-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="ad42d-148">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad42d-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ad42d-149">В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).</span><span class="sxs-lookup"><span data-stu-id="ad42d-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="ad42d-151">В окне конфигуратора проектов MRTK разверните раздел **Modify Configurations** (Изменение конфигураций), убедитесь, что все флажки включены, и нажмите кнопку **Apply**(Применить), чтобы применить эти параметры:</span><span class="sxs-lookup"><span data-stu-id="ad42d-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="ad42d-153">Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:</span><span class="sxs-lookup"><span data-stu-id="ad42d-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="ad42d-154">Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки.</span><span class="sxs-lookup"><span data-stu-id="ad42d-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="ad42d-155">Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="ad42d-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="ad42d-156">Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="ad42d-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="ad42d-157">Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).</span><span class="sxs-lookup"><span data-stu-id="ad42d-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="ad42d-158">2. Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="ad42d-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="ad42d-159">Создание сцены и настройка MRTK</span><span class="sxs-lookup"><span data-stu-id="ad42d-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="ad42d-160">Чтобы создать сцену, в меню Unity выберите **File** > **New Scene** (Файл > Новая сцена):</span><span class="sxs-lookup"><span data-stu-id="ad42d-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="ad42d-162">В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:</span><span class="sxs-lookup"><span data-stu-id="ad42d-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="ad42d-164">В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:</span><span class="sxs-lookup"><span data-stu-id="ad42d-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="ad42d-166">Уменьшать разрядность глубины до 16 битов необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="ad42d-166">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="ad42d-167">Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">производительности MRTK</a>.</span><span class="sxs-lookup"><span data-stu-id="ad42d-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ad42d-169">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="ad42d-169">Importing the tutorial assets</span></span>

<span data-ttu-id="ad42d-170">Скачайте следующий пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="ad42d-170">Download the following Unity custom package:</span></span>

* <span data-ttu-id="ad42d-171">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ad42d-171">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)</span></span>

<span data-ttu-id="ad42d-172">Чтобы импортировать пользовательский пакет Unity, в меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:</span><span class="sxs-lookup"><span data-stu-id="ad42d-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Импорт настраиваемого пакета](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="ad42d-174">В окне Import package (Импорт пакета) выберите скачанный файл **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** и нажмите кнопку Open (Открыть):</span><span class="sxs-lookup"><span data-stu-id="ad42d-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Выбор пакета ресурсов](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="ad42d-176">В окне импорта пакета Unity нажмите кнопку All (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку Import (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="ad42d-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Выбор всех ресурсов для импорта](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="ad42d-178">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="ad42d-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Окно проекта Unity после импорта ресурсов](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="ad42d-180">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="ad42d-180">Configuring the Scene</span></span>

<span data-ttu-id="ad42d-181">В окне Project (Проект) перейдите к папке Assets (Ресурсы ) > MRTK.Tutorials.GettingStarted > Prefabs (Заготовки):</span><span class="sxs-lookup"><span data-stu-id="ad42d-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="ad42d-182">В окне Project (Проект) щелкните и перетащите заготовку **Cube** в окно Hierarchy (Иерархия). Затем в окне Inspector (Инспектор) настройте ее компонент **Transform** (Трансформация) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ad42d-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="ad42d-183">**Position** (Положение): X = 0, Y = 0, Z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="ad42d-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="ad42d-184">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="ad42d-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ad42d-185">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="ad42d-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Добавление объекта Cube в сцену](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="ad42d-187">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **Cube**, а затем снова немного увеличьте масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="ad42d-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="ad42d-188">Чтобы вы могли взаимодействовать с объектом и захватывать его с поддержкой отслеживания рук, в объекте должен быть компонент Collider (Коллайдер), например **Box Collider** (Прямоугольный коллайдер), компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт) и компонент **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт).</span><span class="sxs-lookup"><span data-stu-id="ad42d-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="ad42d-189">Оставив выбранным объект **Cube** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор). Затем найдите и выберите скрипт **Object Manipulator** (Манипулятор объектами), чтобы добавить его в объект Cube.</span><span class="sxs-lookup"><span data-stu-id="ad42d-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Добавление скрипта Object Manipulator (Манипулятор объектами) в объект Cube](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="ad42d-191">Повторите те же действия, чтобы добавить в объект Cube скрипт **Near Interaction Grabbable** (Возможность захвата при близком взаимодействии).</span><span class="sxs-lookup"><span data-stu-id="ad42d-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Добавление скрипта Near Interaction Grabbable (Возможность захвата при близком взаимодействии) в объект Cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="ad42d-193">В нашем примере, когда добавляется компонент Object Manipulator (Script), автоматически добавляется и компонент Constraint Manager (Script), от которого тот зависит.</span><span class="sxs-lookup"><span data-stu-id="ad42d-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="ad42d-194">Для выполнения задач этого руководства в объект Cube уже добавлены коллайдеры.</span><span class="sxs-lookup"><span data-stu-id="ad42d-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="ad42d-195">Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="ad42d-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="ad42d-196">Чтобы проверить это в редакторе Unity, можно перейти в режим воспроизведения и удерживать клавишу **SHIFT** слева или **ПРОБЕЛ** для включения контроллера. Контроллер можно перемещать, передвигая мышь, а приближать его к камере или удалять от нее вы можете с помощью колесика мыши.</span><span class="sxs-lookup"><span data-stu-id="ad42d-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="ad42d-197">Наведите указатель на объект Cube, а затем нажмите и удерживайте **левую кнопку мыши**, чтобы переместить объект Cube.</span><span class="sxs-lookup"><span data-stu-id="ad42d-197">Once the pointer is on the Cube  press and hold **Left Mouse Button** to move the the Cube object.</span></span>

![Режим игры](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="ad42d-199">Создание приложения в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ad42d-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="ad42d-200">1. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="ad42d-200">1. Build the Unity project</span></span>

<span data-ttu-id="ad42d-201">В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="ad42d-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="ad42d-202">В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="ad42d-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Окно параметров сборки Unity с выбранным вариантом UWP](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="ad42d-204">В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="ad42d-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="ad42d-206">Подождите, пока Unity завершит сборку:</span><span class="sxs-lookup"><span data-stu-id="ad42d-206">Wait for Unity to finish the build process:</span></span>

![Unity выполняет сборку](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="ad42d-208">2. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="ad42d-208">2. Build and deploy the application</span></span>

<span data-ttu-id="ad42d-209">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="ad42d-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="ad42d-210">Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="ad42d-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Проводник Windows с выбранным созданным решением Visual Studio](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ad42d-212">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="ad42d-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="ad42d-213">Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):</span><span class="sxs-lookup"><span data-stu-id="ad42d-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Среда Visual Studio, настроенная для развертывания в HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="ad42d-215">Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.</span><span class="sxs-lookup"><span data-stu-id="ad42d-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="ad42d-216">В HoloLens обычно выполняется сборка для архитектуры ARM.</span><span class="sxs-lookup"><span data-stu-id="ad42d-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="ad42d-217">Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad42d-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="ad42d-218">Рекомендуемое решение — выполните сборку для ARM64.</span><span class="sxs-lookup"><span data-stu-id="ad42d-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="ad42d-219">Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.</span><span class="sxs-lookup"><span data-stu-id="ad42d-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="ad42d-220">Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP.</span><span class="sxs-lookup"><span data-stu-id="ad42d-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="ad42d-221">Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="ad42d-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="ad42d-222">Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:</span><span class="sxs-lookup"><span data-stu-id="ad42d-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="ad42d-224">Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="ad42d-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="ad42d-225">Оба эти действия можно выполнить, следуя [этим инструкциям](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ad42d-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="ad42d-226">Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.</span><span class="sxs-lookup"><span data-stu-id="ad42d-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="ad42d-227">Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad42d-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="ad42d-228">Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="ad42d-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="ad42d-229">В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="ad42d-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="ad42d-230">В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность.</span><span class="sxs-lookup"><span data-stu-id="ad42d-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="ad42d-231">Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="ad42d-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="ad42d-232">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ad42d-232">Congratulations</span></span>

<span data-ttu-id="ad42d-233">Вы развернули свое первое приложение HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad42d-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="ad42d-234">Когда приложение откроется, перед вами должен отобразиться объект Cube. С ним можно взаимодействовать, перемещая его. Кроме того, когда вы будете передвигаться, должна отображаться сетка пространственного сопоставления, которая покрывает поверхности, воспринимаемые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad42d-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="ad42d-235">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="ad42d-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="ad42d-236">Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad42d-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="ad42d-237">В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad42d-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad42d-238">Следующее руководство: 3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="ad42d-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
