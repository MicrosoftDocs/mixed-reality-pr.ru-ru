---
title: Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175916"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="2259d-104">2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="2259d-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="2259d-105">Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки набора средств для смешанной реальности (MRTK) и импортировать MRTK.</span><span class="sxs-lookup"><span data-stu-id="2259d-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="2259d-106">Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2259d-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="2259d-107">Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2259d-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2259d-108">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="2259d-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="2259d-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="2259d-109">Objectives</span></span>

* <span data-ttu-id="2259d-110">Узнайте, как настроить Unity для разработки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2259d-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="2259d-111">Узнайте, как создать и развернуть приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2259d-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="2259d-112">Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2259d-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="2259d-113">Обзор шагов</span><span class="sxs-lookup"><span data-stu-id="2259d-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="2259d-114">![Обзор шага 1 ](images/mr-learning-base/base-02-overview-step1.png) **1. Создание проекта Unity**</span><span class="sxs-lookup"><span data-stu-id="2259d-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2259d-115">![Обзор шага 2](images/mr-learning-base/base-02-overview-step2.png) **2. Импорт MRTK в проект**</span><span class="sxs-lookup"><span data-stu-id="2259d-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2259d-116">![Обзор шага 3](images/mr-learning-base/base-02-overview-step3.png) **3. Настройка новой сцены с помощью MRTK**</span><span class="sxs-lookup"><span data-stu-id="2259d-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="2259d-117">![Обзор шага 4](images/mr-learning-base/base-02-overview-step4.png) **4. Сборка проекта Unity**</span><span class="sxs-lookup"><span data-stu-id="2259d-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2259d-118">![Обзор шага 5](images/mr-learning-base/base-02-overview-step5.png) **5. Сборка проекта UWP**</span><span class="sxs-lookup"><span data-stu-id="2259d-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2259d-119">![Обзор шага 6](images/mr-learning-base/base-02-overview-step6.png) **6. Запуск проекта на устройстве**</span><span class="sxs-lookup"><span data-stu-id="2259d-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="2259d-120">Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="2259d-120">Creating the Unity project</span></span>

<span data-ttu-id="2259d-121">Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):</span><span class="sxs-lookup"><span data-stu-id="2259d-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="2259d-122">В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="2259d-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="2259d-123">Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.</span><span class="sxs-lookup"><span data-stu-id="2259d-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="2259d-124">В окне Create a new project (Создание нового проекта) сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="2259d-124">In the Create a new project window:</span></span>

* <span data-ttu-id="2259d-125">Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="2259d-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="2259d-126">Укажите понятное **имя проекта**, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="2259d-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="2259d-127">Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="2259d-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="2259d-128">Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.</span><span class="sxs-lookup"><span data-stu-id="2259d-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="2259d-129">В Windows для переменной MAX_PATH есть ограничение в 255 символов.</span><span class="sxs-lookup"><span data-stu-id="2259d-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="2259d-130">Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.</span><span class="sxs-lookup"><span data-stu-id="2259d-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="2259d-131">Подождите, пока Unity создаст проект:</span><span class="sxs-lookup"><span data-stu-id="2259d-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="2259d-132">Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="2259d-132">Switching the build platform</span></span>

<span data-ttu-id="2259d-133">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="2259d-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="2259d-135">В окне параметров сборки щелкните элемент **Universal Windows Platform** (Универсальная платформа Windows). Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="2259d-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="2259d-136">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="2259d-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="2259d-137">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="2259d-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="2259d-138">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="2259d-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="2259d-139">Задайте для параметра **Target SDK Version** (Целевая версия пакета SDK) значение **Latest Installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="2259d-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="2259d-140">Задайте для параметра **Minimum Platform Version** (Минимальная версия платформы) значение **10.0.1024.0**.</span><span class="sxs-lookup"><span data-stu-id="2259d-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="2259d-141">Задайте для параметра **Visual Studio Version** (Версия Visual Studio) значение **Latest Installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="2259d-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="2259d-142">Задайте для параметра **Build and Run on** (Устройство для сборки и выполнения) значение **USB Device** (USB-устройство).</span><span class="sxs-lookup"><span data-stu-id="2259d-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="2259d-143">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="2259d-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="2259d-144">Нажмите кнопку Switch Platform (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="2259d-144">Click the Switch Platform button</span></span>

![Окно параметров сборки Unity с заданным параметром Universal Windows Platform (Универсальная платформа Windows)](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="2259d-146">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="2259d-146">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="2259d-148">Когда Unity переключит платформу, щелкните значок **x**, чтобы закрыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="2259d-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="2259d-149">Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="2259d-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="2259d-150">Чтобы импортировать Mixed Reality Toolkit в проект Unity, необходимо использовать [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), которое позволяет разработчикам обнаруживать, обновлять и добавлять пакеты компонентов Смешанной реальности в проекты Unity.</span><span class="sxs-lookup"><span data-stu-id="2259d-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="2259d-151">Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.</span><span class="sxs-lookup"><span data-stu-id="2259d-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="2259d-152">Скачайте последнюю версию средства Mixed Reality Feature Tool из [Центра загрузки Майкрософт](https://aka.ms/MRFeatureTool). По завершении скачивания разархивируйте файл и сохраните его на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="2259d-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="2259d-153">Перед запуском средства Mixed Reality Feature Tool установите [среду выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer).</span><span class="sxs-lookup"><span data-stu-id="2259d-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="2259d-154">Откройте исполняемый файл **MixedRealityFeatureTool** из скачанной папки, чтобы запустить Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="2259d-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="2259d-155">Создание сцены и настройка MRTK</span><span class="sxs-lookup"><span data-stu-id="2259d-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="2259d-156">В меню Unity выберите **File**  >  **New Scene** (Файл > Новая сцена):</span><span class="sxs-lookup"><span data-stu-id="2259d-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="2259d-158">В окне **New Scene** (Новая сцена) выберите **Basic (Built-in)** (Базовая — встроенная) и щелкните **Create**, чтобы создать сцену.</span><span class="sxs-lookup"><span data-stu-id="2259d-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Окно создания сцены Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="2259d-160">Приведенный выше снимок экрана относится к Unity версии 2020. Если вы используете Unity 2019, то при нажатии кнопки **Create** будет создана пустая сцена.</span><span class="sxs-lookup"><span data-stu-id="2259d-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="2259d-161">В меню Unity щелкните **Mixed Reality**  >  **Toolkit**  >  **Add to Scene and Configure...** (Смешанная реальность > Набор средств > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:</span><span class="sxs-lookup"><span data-stu-id="2259d-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="2259d-163">Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), убедитесь, что профиль конфигурации **MixedRealityToolkit** имеет значение **DefaultMixedRealityToolkitConfigurationProfile** в окне Inspector (Инспектор):</span><span class="sxs-lookup"><span data-stu-id="2259d-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="2259d-165">В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:</span><span class="sxs-lookup"><span data-stu-id="2259d-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="2259d-167">Сохраните сцену в проекте в разделе **Asset** (Ресурсы)  >  **Scenes** (Сцены).</span><span class="sxs-lookup"><span data-stu-id="2259d-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="2259d-169">Добавление взаимодействия с рукой к объекту</span><span class="sxs-lookup"><span data-stu-id="2259d-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="2259d-170">В меню Unity выберите **GameObject**  >  **3D Object**  >  **Cube**, чтобы добавить объект куба в сцену.</span><span class="sxs-lookup"><span data-stu-id="2259d-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Добавление объекта Cube в сцену](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="2259d-172">Щелкните объект **Cube** в окне Hierarchy (Иерархия), а затем в окне инспектора настройте его компонент **Transform** (Преобразование) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2259d-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="2259d-173">**Position** (Положение): X = 0, Y = –0,1, Z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="2259d-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="2259d-174">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="2259d-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2259d-175">**Scale** (Масштаб): X = 0,1, Y = 0,1, Z = 0,1.</span><span class="sxs-lookup"><span data-stu-id="2259d-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="2259d-176">1 единица Unity — 1 метр.</span><span class="sxs-lookup"><span data-stu-id="2259d-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="2259d-177">Размер куба обновлен до 10 x 10 x 10 см, помещен в 50 см от позиции гарнитуры (0; 0; 0).</span><span class="sxs-lookup"><span data-stu-id="2259d-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="2259d-178">На 10 см ниже уровня взгляда для удобного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2259d-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="2259d-179">Если используется масштаб по умолчанию (1; 1; 1), куб будет слишком большим.</span><span class="sxs-lookup"><span data-stu-id="2259d-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="2259d-180">Если используется положение по умолчанию (0; 0; 0), куб будет размещаться в той же позиции, что и гарнитура, и вы не сможете увидеть ее, пока не переместитесь назад.</span><span class="sxs-lookup"><span data-stu-id="2259d-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Настройка сведений о преобразовании](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="2259d-182">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **Cube**, а затем снова немного увеличьте масштаб представления.</span><span class="sxs-lookup"><span data-stu-id="2259d-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="2259d-183">Также можно использовать клавишу F для масштабирования и фокусировки на объекте.</span><span class="sxs-lookup"><span data-stu-id="2259d-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="2259d-184">Для взаимодействия и захвата объекта с помощью отслеживаемых рук объект должен иметь:</span><span class="sxs-lookup"><span data-stu-id="2259d-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="2259d-185">компонент коллайдера **Box Collider** (объект куба в Unity уже имеет компонент Box Collider по умолчанию);</span><span class="sxs-lookup"><span data-stu-id="2259d-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="2259d-186">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="2259d-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="2259d-187">компонент **NearInteractionGrabbable(Script)** .</span><span class="sxs-lookup"><span data-stu-id="2259d-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="2259d-188">Сценарий MRTK **ObjectManipulator** делает объект перемещаемым, масштабируемым и вращаемым, используя одну или две руки.</span><span class="sxs-lookup"><span data-stu-id="2259d-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="2259d-189">Этот сценарий поддерживает модель ввода прямого манипулирования, так как он позволяет пользователю касаться голограммы непосредственно руками.</span><span class="sxs-lookup"><span data-stu-id="2259d-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="2259d-190">Оставив выбранным объект **Cube** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор). Затем найдите и выберите скрипт **Object Manipulator** (Манипулятор объектами), чтобы добавить его в объект Cube.</span><span class="sxs-lookup"><span data-stu-id="2259d-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Добавление скрипта Object Manipulator (Манипулятор объектами) в объект Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="2259d-192">Повторите те же действия, чтобы добавить в объект Cube скрипт **Near Interaction Grabbable** (Возможность захвата при близком взаимодействии).</span><span class="sxs-lookup"><span data-stu-id="2259d-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Добавление скрипта Near Interaction Grabbable (Возможность захвата при близком взаимодействии) в объект Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="2259d-194">В нашем примере, когда добавляется компонент Object Manipulator (Script), автоматически добавляется и компонент Constraint Manager (Script), от которого тот зависит.</span><span class="sxs-lookup"><span data-stu-id="2259d-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="2259d-195">Тестирование приложения в редакторе Unity с имитацией ввода MRTK</span><span class="sxs-lookup"><span data-stu-id="2259d-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="2259d-196">С помощью имитации ввода MRTK можно тестировать различные типы взаимодействий в редакторе Unity, не создавая и не развертывая их на устройстве.</span><span class="sxs-lookup"><span data-stu-id="2259d-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="2259d-197">Это позволяет быстро проверять свои идеи в процессе проектирования и разработки.</span><span class="sxs-lookup"><span data-stu-id="2259d-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="2259d-198">Используйте сочетания клавиш и мыши для управления имитацией входных данных.</span><span class="sxs-lookup"><span data-stu-id="2259d-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="2259d-199">Нажмите кнопку воспроизведения и войдите в режим воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="2259d-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="2259d-200">Удерживайте левую клавишу **SHIFT** или **ПРОБЕЛ**, чтобы отобразить контроллер (имитация рук). Перемещение мыши переместит контроллер, а также его можно переместить ближе к камере или дальше от нее с помощью колесика мыши.</span><span class="sxs-lookup"><span data-stu-id="2259d-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="2259d-201">Наведите указатель на объект Cube, а затем нажмите и удерживайте **левую кнопку мыши**, чтобы захватить объект Cube.</span><span class="sxs-lookup"><span data-stu-id="2259d-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="2259d-202">Чтобы переместить камеру, нажимайте клавиши **W, A, S, D, Q, E**.</span><span class="sxs-lookup"><span data-stu-id="2259d-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="2259d-203">Чтобы посмотреть по сторонам, перемещайте мышь при нажатой **правой кнопке мыши**.</span><span class="sxs-lookup"><span data-stu-id="2259d-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="2259d-204">Нажмите клавишу **ПРОБЕЛ (правой рукой)** или клавишу **SHIFT (левой рукой)** , чтобы отобразить имитацию рук.</span><span class="sxs-lookup"><span data-stu-id="2259d-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="2259d-205">Нажмите клавишу **T** или **Y**, чтобы удерживать имитацию рук в поле зрения.</span><span class="sxs-lookup"><span data-stu-id="2259d-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="2259d-206">Чтобы повернуть смоделированные руки, нажмите и удерживайте клавишу **CTRL** и перемещайте указатель мыши.</span><span class="sxs-lookup"><span data-stu-id="2259d-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Режим игры](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="2259d-208">Создание приложения в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2259d-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="2259d-209">1. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="2259d-209">1. Build the Unity project</span></span>

<span data-ttu-id="2259d-210">В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="2259d-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="2259d-211">В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="2259d-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Окно параметров сборки Unity с выбранным вариантом UWP](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="2259d-213">В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="2259d-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="2259d-215">Подождите, пока Unity завершит сборку:</span><span class="sxs-lookup"><span data-stu-id="2259d-215">Wait for Unity to finish the build process:</span></span>

![Unity выполняет сборку](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="2259d-217">2. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="2259d-217">2. Build and deploy the application</span></span>

<span data-ttu-id="2259d-218">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="2259d-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="2259d-219">Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="2259d-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Проводник Windows с выбранным созданным решением Visual Studio](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2259d-221">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="2259d-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="2259d-222">Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):</span><span class="sxs-lookup"><span data-stu-id="2259d-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Среда Visual Studio, настроенная для развертывания в HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="2259d-224">Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.</span><span class="sxs-lookup"><span data-stu-id="2259d-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="2259d-225">В HoloLens обычно выполняется сборка для архитектуры ARM.</span><span class="sxs-lookup"><span data-stu-id="2259d-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="2259d-226">Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2259d-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2259d-227">Рекомендуемое решение — выполните сборку для ARM64.</span><span class="sxs-lookup"><span data-stu-id="2259d-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="2259d-228">Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.</span><span class="sxs-lookup"><span data-stu-id="2259d-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="2259d-229">Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP.</span><span class="sxs-lookup"><span data-stu-id="2259d-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="2259d-230">Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).</span><span class="sxs-lookup"><span data-stu-id="2259d-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="2259d-231">Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:</span><span class="sxs-lookup"><span data-stu-id="2259d-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="2259d-233">Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки.</span><span class="sxs-lookup"><span data-stu-id="2259d-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="2259d-234">Оба эти действия можно выполнить, следуя [этим инструкциям](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2259d-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="2259d-235">Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.</span><span class="sxs-lookup"><span data-stu-id="2259d-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="2259d-236">Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2259d-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="2259d-237">Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="2259d-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="2259d-238">В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="2259d-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="2259d-239">В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность.</span><span class="sxs-lookup"><span data-stu-id="2259d-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="2259d-240">Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="2259d-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="2259d-241">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2259d-241">Congratulations</span></span>

<span data-ttu-id="2259d-242">Вы развернули свое первое приложение HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2259d-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="2259d-243">Когда приложение откроется, перед вами должен отобразиться объект Cube. С ним можно взаимодействовать, перемещая его. Кроме того, когда вы будете передвигаться, должна отображаться сетка пространственного сопоставления, которая покрывает поверхности, воспринимаемые HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2259d-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2259d-244">Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="2259d-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="2259d-245">Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="2259d-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="2259d-246">В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.</span><span class="sxs-lookup"><span data-stu-id="2259d-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2259d-247">Следующее руководство: 3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="2259d-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
