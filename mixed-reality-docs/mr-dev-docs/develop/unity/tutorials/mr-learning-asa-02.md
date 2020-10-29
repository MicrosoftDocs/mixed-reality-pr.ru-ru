---
title: Руководства по Пространственным привязкам Azure — часть 2. Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5553df4256e0535d5becb94f22b9ce8eac228dc
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700341"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="93af6-105">2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="93af6-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="93af6-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="93af6-106">Overview</span></span>

<span data-ttu-id="93af6-107">В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="93af6-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="93af6-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="93af6-108">Objectives</span></span>

* <span data-ttu-id="93af6-109">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="93af6-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="93af6-110">Узнайте, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="93af6-111">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="93af6-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="93af6-112">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="93af6-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="93af6-113">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="93af6-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="93af6-114">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials* .</span><span class="sxs-lookup"><span data-stu-id="93af6-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="93af6-115">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="93af6-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="93af6-116">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="93af6-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="93af6-117">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="93af6-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="93af6-118">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="93af6-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="93af6-119">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpatialAnchors.*</span><span class="sxs-lookup"><span data-stu-id="93af6-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="93af6-120">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="93af6-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="93af6-121">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile** .</span><span class="sxs-lookup"><span data-stu-id="93af6-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="93af6-122">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="93af6-122">Change the **spatial awareness mesh display options** to **Occlusion** .</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="93af6-123">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="93af6-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="93af6-124">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="93af6-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="93af6-126">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="93af6-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="93af6-127">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="93af6-127">Importing the tutorial assets</span></span>

<span data-ttu-id="93af6-128">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке** :</span><span class="sxs-lookup"><span data-stu-id="93af6-128">Download and **import** the following Unity custom packages **in the order they are listed** :</span></span>

* <span data-ttu-id="93af6-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (версия 2.2.1);</span><span class="sxs-lookup"><span data-stu-id="93af6-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* <span data-ttu-id="93af6-130">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="93af6-130">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="93af6-131">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="93af6-131">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)</span></span>

<span data-ttu-id="93af6-132">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="93af6-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="93af6-134">Если вы видите предупреждение CS0618 о том, что параметр WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) устарел, его можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="93af6-134">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="93af6-135">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="93af6-135">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="93af6-136">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="93af6-136">Preparing the scene</span></span>

<span data-ttu-id="93af6-137">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="93af6-137">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="93af6-138">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="93af6-138">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="93af6-139">**ButtonParent;**</span><span class="sxs-lookup"><span data-stu-id="93af6-139">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="93af6-140">**DebugWindow;**</span><span class="sxs-lookup"><span data-stu-id="93af6-140">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="93af6-141">**Instructions;**</span><span class="sxs-lookup"><span data-stu-id="93af6-141">**Instructions** prefabs</span></span>
* <span data-ttu-id="93af6-142">**ParentAnchor.**</span><span class="sxs-lookup"><span data-stu-id="93af6-142">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="93af6-144">Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="93af6-144">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="93af6-145">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="93af6-145">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="93af6-146">В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="93af6-146">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="93af6-147">В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-147">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession** , in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-148">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-148">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-149">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-149">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="93af6-151">В окне иерархии выберите следующую кнопку с именем **StopAzureSession** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-151">In the Hierarchy window, select the next button named **StopAzureSession** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-152">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-152">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-153">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-153">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="93af6-155">В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-155">In the Hierarchy window, select the next button named **CreateAzureAnchor** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-156">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-156">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-157">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-157">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="93af6-158">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor** , чтобы сделать его аргументом функции CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="93af6-158">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="93af6-160">В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-160">In the Hierarchy window, select the next button named **RemoveLocalAnchor** ,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-161">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-161">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-162">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-162">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="93af6-163">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor** , чтобы сделать его аргументом функции RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="93af6-163">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="93af6-165">В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-165">In the Hierarchy window, select the next button named **FindAzureAnchor** ,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-166">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-166">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-167">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-167">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="93af6-169">В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor** . Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="93af6-169">In the Hierarchy window, select the next button named **DeleteAzureAnchor** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="93af6-170">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor** .</span><span class="sxs-lookup"><span data-stu-id="93af6-170">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="93af6-171">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="93af6-171">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="93af6-173">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="93af6-173">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="93af6-174">В окне иерархии выберите объект **ParentAnchor** . Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="93af6-174">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="93af6-175">Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="93af6-175">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="93af6-176">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-176">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="93af6-177">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-177">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="93af6-179">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="93af6-179">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="93af6-180">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="93af6-180">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="93af6-181">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="93af6-181">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="93af6-182">Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-182">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="93af6-183">Переместите куб в другое расположение.</span><span class="sxs-lookup"><span data-stu-id="93af6-183">Move the cube to a different location</span></span>
1. <span data-ttu-id="93af6-184">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-184">Start Azure Session</span></span>
1. <span data-ttu-id="93af6-185">Создайте привязку Azure (она создается в расположении, где находится куб).</span><span class="sxs-lookup"><span data-stu-id="93af6-185">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="93af6-186">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-186">Stop Azure Session</span></span>
1. <span data-ttu-id="93af6-187">Удалите локальную привязку (позволяет пользователю перемещать куб).</span><span class="sxs-lookup"><span data-stu-id="93af6-187">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="93af6-188">Переместите куб в другое место.</span><span class="sxs-lookup"><span data-stu-id="93af6-188">Move the cube somewhere else</span></span>
1. <span data-ttu-id="93af6-189">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-189">Start Azure Session</span></span>
1. <span data-ttu-id="93af6-190">Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).</span><span class="sxs-lookup"><span data-stu-id="93af6-190">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="93af6-191">Удалите привязку Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-191">Delete Azure Anchor</span></span>
1. <span data-ttu-id="93af6-192">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-192">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="93af6-194">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="93af6-194">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="93af6-195">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="93af6-195">Anchoring an experience</span></span>

<span data-ttu-id="93af6-196">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-196">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="93af6-197">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="93af6-197">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="93af6-198">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="93af6-198">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="93af6-199">В окне иерархии выберите объект **ParentAnchor** . Затем в окне инспектора настройте компонент **Transform** (Преобразование).</span><span class="sxs-lookup"><span data-stu-id="93af6-199">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="93af6-200">Измените значение **Scale X** (Масштаб Х) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="93af6-200">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="93af6-201">Измените значение **Scale Z** (Масштаб Z) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="93af6-201">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="93af6-203">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="93af6-203">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="93af6-205">Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor** , чтобы сделать его дочерним объектом объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="93af6-205">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="93af6-207">Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.</span><span class="sxs-lookup"><span data-stu-id="93af6-207">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="93af6-208">Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом руководстве), включение ограничивающего прямоугольника вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="93af6-208">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="93af6-209">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="93af6-209">Congratulations</span></span>

<span data-ttu-id="93af6-210">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="93af6-210">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="93af6-211">В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure,</span><span class="sxs-lookup"><span data-stu-id="93af6-211">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="93af6-212">а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="93af6-212">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="93af6-213">В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="93af6-213">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93af6-214">Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="93af6-214">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)