---
title: Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как использовать Пространственные привязки Azure для привязки объектов в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: a31d398621c581460e49ed81d23c446e60bc530f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008514"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="47b1e-104">2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="47b1e-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="47b1e-105">В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="47b1e-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="47b1e-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="47b1e-106">Objectives</span></span>

* <span data-ttu-id="47b1e-107">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="47b1e-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="47b1e-108">Узнайте, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="47b1e-109">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="47b1e-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="47b1e-110">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="47b1e-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="47b1e-111">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="47b1e-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="47b1e-112">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="47b1e-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="47b1e-113">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="47b1e-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="47b1e-114">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="47b1e-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="47b1e-115">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="47b1e-115">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="47b1e-116">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="47b1e-116">Configuring the Unity project</span></span>](mr-learning-base-02.md#selecting-mrtk-and-project-settings)
6. <span data-ttu-id="47b1e-117">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpatialAnchors.*</span><span class="sxs-lookup"><span data-stu-id="47b1e-117">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="47b1e-118">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="47b1e-118">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="47b1e-119">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-119">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="47b1e-120">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="47b1e-120">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="47b1e-121">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="47b1e-121">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="47b1e-122">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="47b1e-122">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="47b1e-124">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-124">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="47b1e-125">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="47b1e-125">Importing the tutorial assets</span></span>

<span data-ttu-id="47b1e-126">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="47b1e-126">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="47b1e-127">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (версия 2.2.1);</span><span class="sxs-lookup"><span data-stu-id="47b1e-127">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* <span data-ttu-id="47b1e-128">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="47b1e-128">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="47b1e-129">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="47b1e-129">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)</span></span>

<span data-ttu-id="47b1e-130">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="47b1e-130">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="47b1e-132">Если вы видите предупреждение CS0618 о том, что параметр WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) устарел, его можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="47b1e-132">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="47b1e-133">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="47b1e-133">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="47b1e-134">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="47b1e-134">Preparing the scene</span></span>

<span data-ttu-id="47b1e-135">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="47b1e-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="47b1e-136">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="47b1e-136">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="47b1e-137">**ButtonParent;**</span><span class="sxs-lookup"><span data-stu-id="47b1e-137">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="47b1e-138">**DebugWindow;**</span><span class="sxs-lookup"><span data-stu-id="47b1e-138">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="47b1e-139">**Instructions;**</span><span class="sxs-lookup"><span data-stu-id="47b1e-139">**Instructions** prefabs</span></span>
* <span data-ttu-id="47b1e-140">**ParentAnchor.**</span><span class="sxs-lookup"><span data-stu-id="47b1e-140">**ParentAnchor** prefabs</span></span>

![Unity с выбранными добавленными заготовками](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="47b1e-142">Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="47b1e-142">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="47b1e-143">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="47b1e-143">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="47b1e-144">В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="47b1e-144">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="47b1e-145">В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-145">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-146">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-146">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-147">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-147">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StartAzureSession](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="47b1e-149">В окне иерархии выберите следующую кнопку с именем **StopAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-149">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-150">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-150">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-151">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-151">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StopAzureSession](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="47b1e-153">В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-153">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-154">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-154">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-155">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-155">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="47b1e-156">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="47b1e-156">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки CreateAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="47b1e-158">В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-158">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-159">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-159">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-160">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-160">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="47b1e-161">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="47b1e-161">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки RemoveLocalAnchor](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="47b1e-163">В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-163">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-164">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-164">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-165">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-165">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки FindAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="47b1e-167">В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="47b1e-167">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="47b1e-168">В поле **None (Object)** (Отсутствует (объект)) укажите объект **DeleteAzureAnchor**.</span><span class="sxs-lookup"><span data-stu-id="47b1e-168">Assign the **DeleteAzureAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="47b1e-169">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="47b1e-169">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки DeleteAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="47b1e-171">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="47b1e-171">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="47b1e-172">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="47b1e-172">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="47b1e-173">Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="47b1e-173">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="47b1e-174">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-174">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="47b1e-175">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-175">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Unity с настроенным диспетчером пространственных привязок](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="47b1e-177">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="47b1e-177">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="47b1e-178">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="47b1e-178">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="47b1e-179">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2]((mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="47b1e-179">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="47b1e-180">Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-180">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="47b1e-181">Переместите куб в другое расположение.</span><span class="sxs-lookup"><span data-stu-id="47b1e-181">Move the cube to a different location</span></span>
1. <span data-ttu-id="47b1e-182">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-182">Start Azure Session</span></span>
1. <span data-ttu-id="47b1e-183">Создайте привязку Azure (она создается в расположении, где находится куб).</span><span class="sxs-lookup"><span data-stu-id="47b1e-183">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="47b1e-184">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-184">Stop Azure Session</span></span>
1. <span data-ttu-id="47b1e-185">Удалите локальную привязку (позволяет пользователю перемещать куб).</span><span class="sxs-lookup"><span data-stu-id="47b1e-185">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="47b1e-186">Переместите куб в другое место.</span><span class="sxs-lookup"><span data-stu-id="47b1e-186">Move the cube somewhere else</span></span>
1. <span data-ttu-id="47b1e-187">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-187">Start Azure Session</span></span>
1. <span data-ttu-id="47b1e-188">Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).</span><span class="sxs-lookup"><span data-stu-id="47b1e-188">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="47b1e-189">Удалите привязку Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-189">Delete Azure Anchor</span></span>
1. <span data-ttu-id="47b1e-190">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-190">Stop Azure session</span></span>

![Unity с выбранным объектом Instructions](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="47b1e-192">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="47b1e-192">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="47b1e-193">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="47b1e-193">Anchoring an experience</span></span>

<span data-ttu-id="47b1e-194">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-194">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47b1e-195">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="47b1e-195">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="47b1e-196">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="47b1e-196">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="47b1e-197">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора настройте компонент **Transform** (Преобразование).</span><span class="sxs-lookup"><span data-stu-id="47b1e-197">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="47b1e-198">Измените значение **Scale X** (Масштаб Х) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="47b1e-198">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="47b1e-199">Измените значение **Scale Z** (Масштаб Z) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="47b1e-199">Change **Scale Z** to 1.1</span></span>

![Unity с выбранным объектом ParentAnchor, для которого выполнено позиционирование и масштабирование](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="47b1e-201">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="47b1e-201">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity с выбранной добавленной заготовкой RoverExplorer_Complete](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="47b1e-203">Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor**, чтобы сделать его дочерним объектом объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="47b1e-203">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity с объектом RoverExplorer_Complete, настроенным как дочерний объект ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="47b1e-205">Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.</span><span class="sxs-lookup"><span data-stu-id="47b1e-205">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="47b1e-206">Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом руководстве), включение ограничивающего прямоугольника вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="47b1e-206">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="47b1e-207">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="47b1e-207">Congratulations</span></span>

<span data-ttu-id="47b1e-208">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="47b1e-208">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47b1e-209">В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure,</span><span class="sxs-lookup"><span data-stu-id="47b1e-209">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="47b1e-210">а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="47b1e-210">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="47b1e-211">В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="47b1e-211">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="47b1e-212">Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="47b1e-212">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
