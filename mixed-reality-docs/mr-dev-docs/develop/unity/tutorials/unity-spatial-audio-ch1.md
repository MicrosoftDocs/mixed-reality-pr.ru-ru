---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: добавьте подключаемый модуль Microsoft спатиализер в проект Unity, чтобы получить доступ к разгрузки HoloLens 2 хртф оборудования.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, unity, учебник, hololens2, пространственный аудио, мртк, набор средств для смешанной реальности, UWP, Windows 10, хртф, функция передачи, связанная с head, переглагол, Microsoft спатиализер
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175375"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="5e985-105">1. Добавление пространственного звука в проект Unity</span><span class="sxs-lookup"><span data-stu-id="5e985-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="5e985-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="5e985-106">Overview</span></span>

<span data-ttu-id="5e985-107">Добро пожаловать в учебник по пространственному аудио для Unity в HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="5e985-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="5e985-108">в этой серии руководств вы узнаете, как использовать разгрузку функций передачи, связанных с head (хртф), в HoloLens 2 и как включить пересылку при использовании разгрузки хртф.</span><span class="sxs-lookup"><span data-stu-id="5e985-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="5e985-109">в [репозитории Microsoft спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.</span><span class="sxs-lookup"><span data-stu-id="5e985-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="5e985-110">Сведения о том, что означает спатиализеие звуков с помощью технологий пространственности на основе ХРТФ и рекомендации по их полезности, см. в статье о [проектировании пространственных звуков](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="5e985-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="5e985-111">Что такое разгрузка ХРТФ?</span><span class="sxs-lookup"><span data-stu-id="5e985-111">What is HRTF offload?</span></span>

<span data-ttu-id="5e985-112">Для обработки звука с использованием алгоритмов на основе ХРТФ требуется большой объем специализированных вычислений.</span><span class="sxs-lookup"><span data-stu-id="5e985-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="5e985-113">HoloLens 2 включает выделенное оборудование, которое можно использовать, чтобы избежать перегрузки процессора приложений, что позволяет «разгружать» обработку алгоритмов на основе хртф.</span><span class="sxs-lookup"><span data-stu-id="5e985-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="5e985-114">Подключаемый модуль Microsoft спатиализер предоставляет приложению простой способ воспользоваться преимуществами выделенного оборудования ХРТФ, чтобы приложение могла использовать больше процессоров приложений для операций, отличных от пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="5e985-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="5e985-115">Задачи</span><span class="sxs-lookup"><span data-stu-id="5e985-115">Objectives</span></span>

* <span data-ttu-id="5e985-116">Импорт и Включение подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="5e985-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="5e985-117">Включение пространственного звука на рабочей станции разработчика</span><span class="sxs-lookup"><span data-stu-id="5e985-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e985-118">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="5e985-118">Prerequisites</span></span>

* <span data-ttu-id="5e985-119">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5e985-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="5e985-120">Базовые навыки работы с C#.</span><span class="sxs-lookup"><span data-stu-id="5e985-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="5e985-121">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="5e985-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5e985-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">центр unity</a> с unity 2020/2019 LTS, подключенный, и добавлен модуль поддержки универсальная платформа Windows сборки</span><span class="sxs-lookup"><span data-stu-id="5e985-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="5e985-123">Прежде чем продолжить, мы **настоятельно рекомендуем** завершить серию руководств по [началу](mr-learning-base-01.md) работы или выполнить некоторые базовые опыт работы с Unity и мртк.</span><span class="sxs-lookup"><span data-stu-id="5e985-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="5e985-124">эта серия руководств поддерживает поддержку unity 2020 LTS (в настоящее время 2020.3. x), если используется подключаемый модуль Open XR или Windows XR, а также Unity 2019 LTS (в настоящее время 2019.4. x), если используется устаревший подключаемый модуль WSA или Windows XR.</span><span class="sxs-lookup"><span data-stu-id="5e985-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="5e985-125">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="5e985-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="5e985-126">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="5e985-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="5e985-127">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="5e985-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="5e985-128">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="5e985-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="5e985-129">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="5e985-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="5e985-130">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="5e985-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="5e985-131">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="5e985-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="5e985-132">импорт набор средств смешанной реальности и настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="5e985-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="5e985-133">[Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и присвойте сцене подходящее имя, например *спатиалаудио*</span><span class="sxs-lookup"><span data-stu-id="5e985-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="5e985-134">Затем выполните инструкции по [изменению параметра "Показать сведения о пространственной поддержке](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) ", чтобы убедиться, что профиль конфигурации мртк для сцены **DefaultHoloLens2ConfigurationProfile** , и измените параметры экрана для сетки пространственной поддержки на **перекрытия**.</span><span class="sxs-lookup"><span data-stu-id="5e985-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="5e985-135">Добавление Microsoft Спатиализер в Project</span><span class="sxs-lookup"><span data-stu-id="5e985-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="5e985-136">Скачайте и импортируйте Microsoft Спатиализер  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. спатиалаудио. спатиализер. Unity. 1.0.18. пакет unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="5e985-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="5e985-137">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="5e985-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="5e985-138">Включение подключаемого модуля Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="5e985-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="5e985-139">после импорта microsoft спатиализер в проект unity появится окно **конфигуратора мртк Project** , чтобы выбрать **Microsoft спатиализер**, а  затем нажать кнопку применить, чтобы применить параметр:</span><span class="sxs-lookup"><span data-stu-id="5e985-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![конфигуратор Project мртк](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="5e985-141">вы также можете вручную включить microsoft спатиализер: Open **Edit-> Project Параметры-> Audio**, а также изменить **подключаемый модуль спатиализер** на "Microsoft спатиализер".</span><span class="sxs-lookup"><span data-stu-id="5e985-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Project Параметры показан подключаемый модуль спатиализер](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="5e985-143">Включение пространственного звука на рабочей станции</span><span class="sxs-lookup"><span data-stu-id="5e985-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="5e985-144">в настольных версиях Windows пространственный звук по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="5e985-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="5e985-145">Включите его, щелкнув значок тома правой кнопкой мыши на панели задач.</span><span class="sxs-lookup"><span data-stu-id="5e985-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="5e985-146">чтобы получить лучшее представление о том, что вы услышите на HoloLens 2, выберите **Windows Sonic для наушников пространственный звук — >**.</span><span class="sxs-lookup"><span data-stu-id="5e985-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Параметры пространственного звука рабочего стола](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="5e985-148">Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="5e985-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5e985-149">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="5e985-149">Congratulations</span></span>

<span data-ttu-id="5e985-150">В этом учебнике вы узнаете, как импортировать и включить подключаемый модуль Microsoft Спатиализер, а также включить Пространственный звук на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="5e985-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="5e985-151">В следующем учебнике вы узнаете, как добавить пространственный звук в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="5e985-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e985-152">Следующее руководство: 2. звуковое взаимодействие кнопки Спатиализинг</span><span class="sxs-lookup"><span data-stu-id="5e985-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
