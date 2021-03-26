---
title: Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как использовать Пространственные привязки Azure для привязки объектов в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: ab216fc89c7161e4b3e7ee6fd9bcf9022b83c7fa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "103574960"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="97a88-104">2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="97a88-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="97a88-105">В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="97a88-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="97a88-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="97a88-106">Objectives</span></span>

* <span data-ttu-id="97a88-107">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="97a88-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="97a88-108">Узнайте, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="97a88-109">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="97a88-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="97a88-110">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="97a88-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="97a88-111">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="97a88-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="97a88-112">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="97a88-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="97a88-113">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="97a88-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="97a88-114">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="97a88-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="97a88-115">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="97a88-115">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="97a88-116">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="97a88-116">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="97a88-117">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpatialAnchors.*</span><span class="sxs-lookup"><span data-stu-id="97a88-117">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="97a88-118">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="97a88-118">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="97a88-119">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="97a88-119">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="97a88-120">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="97a88-120">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="97a88-121">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="97a88-121">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="97a88-122">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="97a88-122">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="97a88-124">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="97a88-124">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="97a88-125">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="97a88-125">Importing the tutorial assets</span></span>

<span data-ttu-id="97a88-126">Добавьте пакет SDK AzurespatialAnchors 2.7.1 в свой проект Unity с помощью этого [учебника](https://docs.microsoft.com/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="97a88-126">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="97a88-127">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="97a88-127">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>


* <span data-ttu-id="97a88-128">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="97a88-128">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* [<span data-ttu-id="97a88-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="97a88-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage)

<span data-ttu-id="97a88-130">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="97a88-130">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="97a88-132">Если вы видите предупреждение CS0618 о том, что параметр WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) устарел, его можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="97a88-132">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="97a88-133">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="97a88-133">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="97a88-134">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="97a88-134">Preparing the scene</span></span>

<span data-ttu-id="97a88-135">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="97a88-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="97a88-136">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="97a88-136">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="97a88-137">**ButtonParent;**</span><span class="sxs-lookup"><span data-stu-id="97a88-137">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="97a88-138">**DebugWindow;**</span><span class="sxs-lookup"><span data-stu-id="97a88-138">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="97a88-139">**Instructions;**</span><span class="sxs-lookup"><span data-stu-id="97a88-139">**Instructions** prefabs</span></span>
* <span data-ttu-id="97a88-140">**ParentAnchor.**</span><span class="sxs-lookup"><span data-stu-id="97a88-140">**ParentAnchor** prefabs</span></span>

![Unity с выбранными добавленными заготовками](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="97a88-142">Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="97a88-142">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="97a88-143">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="97a88-143">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="97a88-144">В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="97a88-144">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="97a88-145">В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-145">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-146">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-146">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-147">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-147">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StartAzureSession](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="97a88-149">В окне иерархии выберите следующую кнопку с именем **StopAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-149">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-150">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-150">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-151">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-151">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StopAzureSession](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="97a88-153">В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-153">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-154">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-154">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-155">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-155">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="97a88-156">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="97a88-156">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки CreateAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="97a88-158">В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-158">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-159">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-159">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-160">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-160">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="97a88-161">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="97a88-161">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки RemoveLocalAnchor](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="97a88-163">В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-163">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-164">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-164">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-165">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-165">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки FindAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="97a88-167">В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97a88-167">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="97a88-168">В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.</span><span class="sxs-lookup"><span data-stu-id="97a88-168">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="97a88-169">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="97a88-169">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки DeleteAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="97a88-171">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="97a88-171">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="97a88-172">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="97a88-172">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="97a88-173">Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="97a88-173">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="97a88-174">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-174">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="97a88-175">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-175">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="97a88-176">В поле **Spatial Anchors Account Domain** (Домен учетной записи пространственных привязок) укажите **домен учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-176">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity с настроенным диспетчером пространственных привязок](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="97a88-178">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="97a88-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="97a88-179">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="97a88-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="97a88-180">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="97a88-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="97a88-181">Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="97a88-182">Переместите куб в другое расположение.</span><span class="sxs-lookup"><span data-stu-id="97a88-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="97a88-183">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-183">Start Azure Session</span></span>
1. <span data-ttu-id="97a88-184">Создайте привязку Azure (она создается в расположении, где находится куб).</span><span class="sxs-lookup"><span data-stu-id="97a88-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="97a88-185">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-185">Stop Azure Session</span></span>
1. <span data-ttu-id="97a88-186">Удалите локальную привязку (позволяет пользователю перемещать куб).</span><span class="sxs-lookup"><span data-stu-id="97a88-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="97a88-187">Переместите куб в другое место.</span><span class="sxs-lookup"><span data-stu-id="97a88-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="97a88-188">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-188">Start Azure Session</span></span>
1. <span data-ttu-id="97a88-189">Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).</span><span class="sxs-lookup"><span data-stu-id="97a88-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="97a88-190">Удалите привязку Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="97a88-191">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-191">Stop Azure session</span></span>

![Unity с выбранным объектом Instructions](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="97a88-193">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="97a88-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="97a88-194">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="97a88-194">Anchoring an experience</span></span>

<span data-ttu-id="97a88-195">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="97a88-196">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="97a88-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="97a88-197">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="97a88-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="97a88-198">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора настройте компонент **Transform** (Преобразование).</span><span class="sxs-lookup"><span data-stu-id="97a88-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="97a88-199">Измените значение **Scale X** (Масштаб Х) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="97a88-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="97a88-200">Измените значение **Scale Z** (Масштаб Z) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="97a88-200">Change **Scale Z** to 1.1</span></span>

![Unity с выбранным объектом ParentAnchor, для которого выполнено позиционирование и масштабирование](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="97a88-202">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="97a88-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity с выбранной добавленной заготовкой RoverExplorer_Complete](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="97a88-204">Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor**, чтобы сделать его дочерним объектом объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="97a88-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity с объектом RoverExplorer_Complete, настроенным как дочерний объект ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="97a88-206">Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.</span><span class="sxs-lookup"><span data-stu-id="97a88-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="97a88-207">Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом учебнике), включение ограничивающего элемента вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="97a88-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="97a88-208">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="97a88-208">Congratulations</span></span>

<span data-ttu-id="97a88-209">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="97a88-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="97a88-210">В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure,</span><span class="sxs-lookup"><span data-stu-id="97a88-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="97a88-211">а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="97a88-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="97a88-212">В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="97a88-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="97a88-213">Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="97a88-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
