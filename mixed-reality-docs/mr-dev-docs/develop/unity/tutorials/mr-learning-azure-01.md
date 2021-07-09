---
title: Облачные службы Azure для HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать различные службы Azure в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Azure, смешанная реальность, Unity, учебник, Hololens, Hololens 2, хранилище BLOB-объектов Azure, табличное хранилище Azure, Пространственные привязки Azure, Azure Bot Framework, облачные службы Azure, Пользовательское визуальное распознавание Azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: c38f3102adfb5178a4d2b5429eeb24c0733db50a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175531"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="73a31-104">1. Облачные службы Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="73a31-104">1. Azure Cloud Services for HoloLens 2</span></span>

<span data-ttu-id="73a31-105">Представляем вашему вниманию серию учебников, посвященных переносу **облачных служб Azure** в приложение **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="73a31-105">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="73a31-106">Из этой серии учебников в пяти частях вы узнаете, как интегрировать несколько **облачных служб Azure** в проект **Unity** для **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="73a31-106">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="73a31-107">В каждой из последующих глав будут добавляться новые **облачные службы Azure** для расширения возможностей приложений и взаимодействий с пользователем. Кроме того, вы узнаете об основных принципах роботы **облачной службы Azure**.</span><span class="sxs-lookup"><span data-stu-id="73a31-107">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="73a31-108">В этой серии учебников основное внимание уделяется **HoloLens 2**, но из-за межплатформенного характера Unity большая часть материалов будет также применяться для классических приложений и смартфонов.</span><span class="sxs-lookup"><span data-stu-id="73a31-108">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="73a31-109">В этом первом учебнике описано назначение этой серии и каждой облачной службы Azure, которую вы будете использовать, а также настройка первоначального проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="73a31-109">In this first tutorial, you'll be introduced to the goals of the series and each Azure Cloud service you'll be using, as well as setting up the initial Unity project.</span></span>

<span data-ttu-id="73a31-110">При работе со вторым учебником, [Интеграция службы хранилища Azure](mr-learning-azure-02.md), вы выполните интеграцию службы хранилища Azure в качестве решения для сохранения данных для демонстрационного приложения.</span><span class="sxs-lookup"><span data-stu-id="73a31-110">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you'll start off by integrating Azure Storage as the persistence solution for the demo application.</span></span> <span data-ttu-id="73a31-111">Вы также узнаете о различиях между Хранилищем BLOB-объектов и Хранилищем таблиц, выполните подготовку нужных ресурсов проекта и настроите сцену.</span><span class="sxs-lookup"><span data-stu-id="73a31-111">You'll also learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene.</span></span> <span data-ttu-id="73a31-112">Наконец, вы научитесь проверять операции считывания, обновления и удаления данных.</span><span class="sxs-lookup"><span data-stu-id="73a31-112">Finally, you'll learn how to verify the read, update, and delete data operations.</span></span>

<span data-ttu-id="73a31-113">Продолжая работу с третьим учебником [Интеграция Пользовательского визуального распознавания Azure](mr-learning-azure-03.md), вы будете использовать Пользовательское визуальное распознавание Azure для обучения и обнаружения изображений в приложении HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="73a31-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="73a31-114">В начале главы приведены сведения о настройке ресурса "Пользовательское визуальное распознавание Azure", подготовке компонентов сцены и действия для обучения и обнаружения изображений в приложении.</span><span class="sxs-lookup"><span data-stu-id="73a31-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="73a31-115">Далее в четвертом учебнике [Интеграция пространственных привязок Azure](mr-learning-azure-04.md) вы изучите службы пространственных привязок Azure для сохранения и поиска расположений, а также основные концепции, подготовите необходимые ресурсы, настроите сцены и приступите к использованию новой функции в приложении.</span><span class="sxs-lookup"><span data-stu-id="73a31-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="73a31-116">С помощью пятого руководства [Интеграция службы Azure Bot с LUIS](mr-learning-azure-05.md) вы завершите обучение, предоставляя приложению новый метод взаимодействия с пользователем с использованием естественного языка.</span><span class="sxs-lookup"><span data-stu-id="73a31-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="73a31-117">Эта функция будет реализована с помощью платформы Azure Bot Framework, а также службы "Распознавания речи" (LUIS).</span><span class="sxs-lookup"><span data-stu-id="73a31-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="73a31-118">В этой заключительной главе рассказывается о принципах работы службы Azure Bot и ускорении процесса, который вы будете использовать в качестве решения с нулевым кодом с помощью Bot Framework Composer.</span><span class="sxs-lookup"><span data-stu-id="73a31-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="73a31-119">После создания бота вы интегрируете его в сцену и запустите его на завершающем этапе приложения HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="73a31-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="73a31-120">Цели приложения</span><span class="sxs-lookup"><span data-stu-id="73a31-120">Application goals</span></span>

<span data-ttu-id="73a31-121">В этой серии учебников вы создадите приложение **HoloLens 2**, которое может обнаруживать объекты на изображениях и находить их пространственное положение.</span><span class="sxs-lookup"><span data-stu-id="73a31-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="73a31-122">Чтобы установить язык домена, необходимо вызвать такие сущности из **отслеживаемого объекта**.</span><span class="sxs-lookup"><span data-stu-id="73a31-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="73a31-123">Пользователь может создать **отслеживаемый объект**, чтобы связать набор изображений с помощью компьютерного зрения или пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="73a31-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="73a31-124">Все данные должны быть сохранены в облаке.</span><span class="sxs-lookup"><span data-stu-id="73a31-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="73a31-125">Кроме того, некоторые аспекты приложения будут дополнительно контролироваться естественным языком с помощью бота.</span><span class="sxs-lookup"><span data-stu-id="73a31-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="73a31-126">Возможности</span><span class="sxs-lookup"><span data-stu-id="73a31-126">Features</span></span>

* <span data-ttu-id="73a31-127">Базовое управление данными и изображениями.</span><span class="sxs-lookup"><span data-stu-id="73a31-127">Basic managing of data and images</span></span>
* <span data-ttu-id="73a31-128">Обучение и обнаружение изображений.</span><span class="sxs-lookup"><span data-stu-id="73a31-128">Image training and detection</span></span>
* <span data-ttu-id="73a31-129">Хранение пространственного положения и инструкций.</span><span class="sxs-lookup"><span data-stu-id="73a31-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="73a31-130">Бот-помощник для использования некоторых возможностей с помощью естественного языка.</span><span class="sxs-lookup"><span data-stu-id="73a31-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="73a31-131">Облачные службы Azure</span><span class="sxs-lookup"><span data-stu-id="73a31-131">Azure Cloud services</span></span>

<span data-ttu-id="73a31-132">Вы будете использовать следующие **облачные службы Azure** для реализации приведенных выше функций:</span><span class="sxs-lookup"><span data-stu-id="73a31-132">You'll use the following **Azure Cloud** services to implement the above features:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="73a31-133">Служба хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="73a31-133">Azure Storage</span></span>

<span data-ttu-id="73a31-134">Для решения сохраняемости будет использоваться [служба хранилища Azure](https://azure.microsoft.com/services/storage/).</span><span class="sxs-lookup"><span data-stu-id="73a31-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="73a31-135">Она позволяет хранить данные в таблице и отправлять большие двоичные файлы, например изображения.</span><span class="sxs-lookup"><span data-stu-id="73a31-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="73a31-136">Пользовательское визуальное распознавание Azure</span><span class="sxs-lookup"><span data-stu-id="73a31-136">Azure Custom Vision</span></span>

<span data-ttu-id="73a31-137">С помощью [Пользовательского визуального распознавания Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (в составе [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) можно связать с *отслеживаемыми объектами* набор изображений, обучить модель машинного обучения в наборе и определить *отслеживаемый объект*.</span><span class="sxs-lookup"><span data-stu-id="73a31-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="73a31-138">Пространственные привязки Azure</span><span class="sxs-lookup"><span data-stu-id="73a31-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="73a31-139">Чтобы сохранить расположение *отслеживаемого объекта* и предоставить инструкции по его поиску, используйте [Пространственные привязки Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="73a31-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="73a31-140">Служба Azure Bot</span><span class="sxs-lookup"><span data-stu-id="73a31-140">Azure Bot Service</span></span>

<span data-ttu-id="73a31-141">Приложение в основном управляется через традиционный пользовательский интерфейс, поэтому вы используете [службу Azure Bot](https://azure.microsoft.com/services/bot-service/), чтобы добавить некоторую индивидуальность и использовать новый метод взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="73a31-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73a31-142">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="73a31-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="73a31-143">Если вы еще не прошли руководства из серии, посвященной [началу работы](mr-learning-base-01.md), мы рекомендуем начать знакомство именно с этой серии.</span><span class="sxs-lookup"><span data-stu-id="73a31-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="73a31-144">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="73a31-144">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="73a31-145">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="73a31-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="73a31-146">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="73a31-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="73a31-147">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="73a31-147">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="73a31-148">Подключенная веб-камера, если вы хотите выполнить тестирование из редактора Unity.</span><span class="sxs-lookup"><span data-stu-id="73a31-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="73a31-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем поддержки сборки универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="73a31-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="73a31-150">Рекомендуемая версия Unity для этой серии руководств — Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="73a31-150">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="73a31-151">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="73a31-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="73a31-152">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="73a31-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="73a31-153">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="73a31-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="73a31-154">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="73a31-154">First, follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="73a31-155">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *Azure Cloud Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="73a31-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="73a31-156">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="73a31-156">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="73a31-157">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="73a31-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="73a31-158">Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="73a31-158">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="73a31-159">[Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и назначение ей понятного имени, например *AzureCloudServices.*</span><span class="sxs-lookup"><span data-stu-id="73a31-159">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="73a31-160">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultXRSDKConfigurationProfile** для сцены и значение **Occlusion** (Загораживание) для параметра отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="73a31-160">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultXRSDKConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="73a31-161">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="73a31-161">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="73a31-162">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="73a31-162">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Окно диспетчера пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="73a31-164">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="73a31-164">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="73a31-165">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="73a31-165">Importing the tutorial assets</span></span>

<span data-ttu-id="73a31-166">Добавьте пакет SDK AzurespatialAnchors 2.7.1 в свой проект Unity с помощью этого [учебника](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="73a31-166">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="73a31-167">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="73a31-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="73a31-168">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="73a31-168">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="73a31-169">MRTK.Tutorials.AzureCloudServices.unitypackage</span><span class="sxs-lookup"><span data-stu-id="73a31-169">MRTK.Tutorials.AzureCloudServices.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="73a31-170">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="73a31-170">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="73a31-171">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="73a31-171">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-azure/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="73a31-173">Если вы видите предупреждение CS0618 об устаревании WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) и WorldAnchor.GetNativeSpatialAnchorPtr(), такое предупреждение можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="73a31-173">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="73a31-174">Создание и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="73a31-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="73a31-175">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="73a31-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="73a31-176">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="73a31-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="73a31-177">Удерживая нажатой клавишу CTRL, щелкните заготовки **SceneController**, **RootMenu** и **DataManager**, чтобы выбрать их:</span><span class="sxs-lookup"><span data-stu-id="73a31-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![Unity с выбранными заготовками SceneController, RootMenu и DataManager](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="73a31-179">**SceneController (prefab)** (SceneController — заготовка) содержит два скрипта: **SceneController (script)** (SceneController — скрипт) и **UnityDispatcher (script)** (UnityDispatcher — скрипт).</span><span class="sxs-lookup"><span data-stu-id="73a31-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="73a31-180">Компонент скрипта **SceneController** содержит несколько функций взаимодействия с пользователем и упрощает использование функции фотозахвата. **UnityDispatcher** является вспомогательным классом, позволяющим выполнять действия в основном потоке Unity.</span><span class="sxs-lookup"><span data-stu-id="73a31-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="73a31-181">**RootMenu (prefab)** (RootMenu — заготовка) является основной заготовкой пользовательского интерфейса, которая содержит все окна пользовательского интерфейса, подключенные друг к другу через различные небольшие компоненты скрипта и управляющие общим потоком интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="73a31-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="73a31-182">**DataManager (prefab)** (DataManager — заготовка) отвечает за взаимодействие с хранилищем Azure. Она будет описана в следующем учебнике.</span><span class="sxs-lookup"><span data-stu-id="73a31-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="73a31-183">Теперь, когда все три заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:</span><span class="sxs-lookup"><span data-stu-id="73a31-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![Unity с добавленными заготовками SceneController, RootMenu и DataManager](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="73a31-185">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **RootMenu** и немного уменьшите масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="73a31-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![Unity с выбранным объектом RootMenu](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="73a31-187">Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.</span><span class="sxs-lookup"><span data-stu-id="73a31-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="73a31-188">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="73a31-188">Configuring the scene</span></span>

<span data-ttu-id="73a31-189">В этом разделе вы будете вместе соединять объекты *SceneManager*, *DataManager* и *RootMenu*, чтобы подготовить рабочую сцену к работе со следующим учебником по [интеграции службы хранилища Azure](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="73a31-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="73a31-190">Соединение объектов</span><span class="sxs-lookup"><span data-stu-id="73a31-190">Connect the objects</span></span>

<span data-ttu-id="73a31-191">В окне Hierarchy (Иерархия) выберите объект **DataManager**:</span><span class="sxs-lookup"><span data-stu-id="73a31-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![Unity с выбранным объектом DataManager](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="73a31-193">В окне Inspector (Инспектор) найдите компонент **DataManager (Script)** (DataManager — скрипт), вы увидите пустой слот в событии **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="73a31-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="73a31-194">Теперь в окне Hierarchy (Иерархия) перетащите объект **SceneController** в событие **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="73a31-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![Unity с добавленным прослушивателем событий DataManager](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="73a31-196">Вы увидите, что раскрывающееся меню события стало активным, щелкните его и перейдите к **SceneController**. В подменю выберите параметр **init ()** :</span><span class="sxs-lookup"><span data-stu-id="73a31-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![Unity с добавленным действием события DataManager](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="73a31-198">В окне Hierarchy (Иерархия) выберите объект **SceneController**. В окне Inspector (Инспектор) вы найдете компонент **SceneController (script)** (SceneController — скрипт).</span><span class="sxs-lookup"><span data-stu-id="73a31-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![Unity с выделенным объектом SceneController](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="73a31-200">Отобразятся несколько незаполненных полей. Заполните их.</span><span class="sxs-lookup"><span data-stu-id="73a31-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="73a31-201">Переместите объект **DataManager** из окна Hierarchy (Иерархия) в поле *Data Manager* (Диспетчер данных) и переместите GameObject **RootMenu** из окна Hierarchy (Иерархия) в поле *Main Menu* (Главное меню).</span><span class="sxs-lookup"><span data-stu-id="73a31-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![Unity с настроенным объектом SceneController](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="73a31-203">Теперь сцена подготовлена для работы со следующими учебниками.</span><span class="sxs-lookup"><span data-stu-id="73a31-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="73a31-204">Не забудьте сохранить ее в проекте.</span><span class="sxs-lookup"><span data-stu-id="73a31-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="73a31-205">Подготовка конвейера сборки проекта</span><span class="sxs-lookup"><span data-stu-id="73a31-205">Prepare project build pipeline</span></span>

<span data-ttu-id="73a31-206">Хотя в проект еще нужно добавлять содержимое, выполните несколько действий, чтобы проект был готов к созданию **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="73a31-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="73a31-207">1. Добавление дополнительных требуемых возможностей</span><span class="sxs-lookup"><span data-stu-id="73a31-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="73a31-208">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="73a31-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity с открытыми параметрами проекта](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="73a31-210">В окне параметров проекта выберите элемент **Player** (Проигрыватель), а затем — **Publishing Settings** (Параметры публикации):</span><span class="sxs-lookup"><span data-stu-id="73a31-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![Unity с открытыми параметрами публикации](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="73a31-212">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые вы включили при создании проекта в начале работы с этим учебником.</span><span class="sxs-lookup"><span data-stu-id="73a31-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="73a31-213">Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента), **PrivateNetworkClientServer** (Сервер клиента частной сети) и **Webcam** (Веб-камера):</span><span class="sxs-lookup"><span data-stu-id="73a31-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![Возможности Unity](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="73a31-215">2. Разверните приложение на устройстве HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="73a31-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="73a31-216">Не все функции, которые будут использоваться в этой серии учебников, можно выполнять внутри редактора Unity. Это означает, что вам необходимо получить сведения о развертывании приложения на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="73a31-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="73a31-217">Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2) в учебнике по началу работы.</span><span class="sxs-lookup"><span data-stu-id="73a31-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="73a31-218">3. Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям</span><span class="sxs-lookup"><span data-stu-id="73a31-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="73a31-219">Все службы Azure используют Интернет, поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="73a31-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="73a31-220">Когда приложение запускается на устройстве, предоставьте доступ к следующим запрошенным возможностям:</span><span class="sxs-lookup"><span data-stu-id="73a31-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="73a31-221">микрофон</span><span class="sxs-lookup"><span data-stu-id="73a31-221">Microphone</span></span>
* <span data-ttu-id="73a31-222">Камера</span><span class="sxs-lookup"><span data-stu-id="73a31-222">Camera</span></span>

<span data-ttu-id="73a31-223">Эти функции необходимы для правильной работы таких служб, как *чат-бот* и *Пользовательское визуальное распознавание*.</span><span class="sxs-lookup"><span data-stu-id="73a31-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="73a31-224">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="73a31-224">Congratulations</span></span>

<span data-ttu-id="73a31-225">Здесь вы ознакомились с серией учебников, узнали о функциях, которые будете реализовывать, и о том, как согласовывать **облачные службы Azure**, чтобы реализовать приложение *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="73a31-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="73a31-226">Вы добавили необходимые компоненты в проект и подготовили сцену для работы с этой серией учебников.</span><span class="sxs-lookup"><span data-stu-id="73a31-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="73a31-227">На следующем уроке вы будете использовать хранилище Azure в качестве облачного решения для сохранения данных и изображений.</span><span class="sxs-lookup"><span data-stu-id="73a31-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73a31-228">Следующее руководство: 2. Интеграция службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="73a31-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)