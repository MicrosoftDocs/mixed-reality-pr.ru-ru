---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: Добавьте подключаемый модуль Microsoft Спатиализер в проект Unity, чтобы получить доступ к аппаратной разгрузке HoloLens 2 ХРТФ.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: 1eb2913f1953e334cfe75b786f96bb51a9852fc5
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578459"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="3bded-105">1. Добавление пространственного звука в проект Unity</span><span class="sxs-lookup"><span data-stu-id="3bded-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="3bded-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="3bded-106">Overview</span></span>

<span data-ttu-id="3bded-107">Добро пожаловать в учебник по пространственному аудио для Unity в HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3bded-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="3bded-108">В этой серии руководств вы узнаете, как использовать разгрузку функций передачи, связанных с HEAD (ХРТФ), в HoloLens 2 и как включить пересылку при использовании разгрузки ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="3bded-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="3bded-109">В [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.</span><span class="sxs-lookup"><span data-stu-id="3bded-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="3bded-110">Сведения о том, что означает спатиализеие звуков с помощью технологий пространственности на основе ХРТФ и рекомендации по их полезности, см. в статье о [проектировании пространственных звуков](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="3bded-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="3bded-111">Что такое разгрузка ХРТФ?</span><span class="sxs-lookup"><span data-stu-id="3bded-111">What is HRTF offload?</span></span>

<span data-ttu-id="3bded-112">Для обработки звука с использованием алгоритмов на основе ХРТФ требуется большой объем специализированных вычислений.</span><span class="sxs-lookup"><span data-stu-id="3bded-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="3bded-113">HoloLens 2 включает выделенное оборудование, которое можно использовать, чтобы избежать перегрузки процессора приложений, таким путем «разложить» обработку алгоритмов на основе ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="3bded-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="3bded-114">Подключаемый модуль Microsoft спатиализер предоставляет приложению простой способ воспользоваться преимуществами выделенного оборудования ХРТФ, чтобы приложение могла использовать больше процессоров приложений для операций, отличных от пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="3bded-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="3bded-115">Задачи</span><span class="sxs-lookup"><span data-stu-id="3bded-115">Objectives</span></span>

* <span data-ttu-id="3bded-116">Импорт и Включение подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="3bded-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="3bded-117">Включение пространственного звука на рабочей станции разработчика</span><span class="sxs-lookup"><span data-stu-id="3bded-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3bded-118">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="3bded-118">Prerequisites</span></span>

* <span data-ttu-id="3bded-119">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3bded-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="3bded-120">Базовые навыки работы с C#.</span><span class="sxs-lookup"><span data-stu-id="3bded-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="3bded-121">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="3bded-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="3bded-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="3bded-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="3bded-123">Прежде чем продолжить, мы **настоятельно рекомендуем** завершить серию руководств по [началу](mr-learning-base-01.md) работы или выполнить некоторые базовые опыт работы с Unity и мртк.</span><span class="sxs-lookup"><span data-stu-id="3bded-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="3bded-124">Рекомендуемая версия Unity для этой серии руководств — Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="3bded-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="3bded-125">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="3bded-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="3bded-126">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="3bded-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="3bded-127">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="3bded-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="3bded-128">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="3bded-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="3bded-129">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="3bded-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="3bded-130">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="3bded-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="3bded-131">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="3bded-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="3bded-132">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="3bded-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="3bded-133">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="3bded-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="3bded-134">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвойте сцене подходящее имя, например *спатиалаудио*</span><span class="sxs-lookup"><span data-stu-id="3bded-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="3bded-135">Затем выполните инструкции по [изменению параметра "Показать сведения о пространственной поддержке](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) ", чтобы убедиться, что профиль конфигурации мртк для сцены **дефаултксрсдкконфигуратионпрофиле** , и измените параметры экрана для сетки пространственной поддержки на **перекрытия**.</span><span class="sxs-lookup"><span data-stu-id="3bded-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultXRSDKConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="3bded-136">Добавление Microsoft Спатиализер в проект</span><span class="sxs-lookup"><span data-stu-id="3bded-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="3bded-137">Скачайте и импортируйте Microsoft Спатиализер  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. спатиалаудио. спатиализер. Unity. 1.0.18. пакет unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="3bded-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="3bded-138">Чтобы вспомнить, как правильно импортировать пользовательский пакет Unity, воспользуйтесь инструкциями из статьи об [импорте Набора средств Смешанной реальности (MRTK)](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="3bded-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="3bded-139">Включение подключаемого модуля Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="3bded-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="3bded-140">После импорта **Microsoft спатиализер** необходимо включить его.</span><span class="sxs-lookup"><span data-stu-id="3bded-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="3bded-141">Откройте **> параметры проекта-> аудио** и измените **подключаемый модуль Спатиализер** на "Microsoft спатиализер".</span><span class="sxs-lookup"><span data-stu-id="3bded-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Параметры проекта, отображающие подключаемый модуль спатиализер](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="3bded-143">Включение пространственного звука на рабочей станции</span><span class="sxs-lookup"><span data-stu-id="3bded-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="3bded-144">В настольных версиях Windows Пространственный звук по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="3bded-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="3bded-145">Включите его, щелкнув значок тома правой кнопкой мыши на панели задач.</span><span class="sxs-lookup"><span data-stu-id="3bded-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="3bded-146">Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Пространственный звук — > Windows Sonic для наушников**.</span><span class="sxs-lookup"><span data-stu-id="3bded-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Параметры пространственного звука рабочего стола](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3bded-148">Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="3bded-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3bded-149">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="3bded-149">Congratulations</span></span>

<span data-ttu-id="3bded-150">В этом учебнике вы узнаете, как импортировать и включить подключаемый модуль Microsoft Спатиализер, а также включить Пространственный звук на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="3bded-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="3bded-151">В следующем учебнике вы узнаете, как добавить пространственный звук в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="3bded-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3bded-152">Следующее руководство: 2. звуковое взаимодействие кнопки Спатиализинг</span><span class="sxs-lookup"><span data-stu-id="3bded-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
