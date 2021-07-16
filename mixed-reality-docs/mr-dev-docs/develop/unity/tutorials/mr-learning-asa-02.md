---
title: Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как использовать Пространственные привязки Azure для привязки объектов в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656644"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="b37cf-104">2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="b37cf-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="b37cf-105">В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="b37cf-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="b37cf-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="b37cf-106">Objectives</span></span>

* <span data-ttu-id="b37cf-107">Изучите основы разработки Пространственных привязок Azure для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b37cf-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="b37cf-108">Узнайте, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="b37cf-109">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="b37cf-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="b37cf-110">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="b37cf-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="b37cf-111">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="b37cf-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="b37cf-112">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="b37cf-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="b37cf-113">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="b37cf-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="b37cf-114">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="b37cf-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="b37cf-115">Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="b37cf-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="b37cf-116">[Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и присвоение ей понятного имени, например *AzureSpatialAnchors.*</span><span class="sxs-lookup"><span data-stu-id="b37cf-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="b37cf-117">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены и значение **Occlusion** (Загораживание) для параметра отображения сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="b37cf-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="b37cf-118">Установка встроенных пакетов Unity и импорт учебных ресурсов</span><span class="sxs-lookup"><span data-stu-id="b37cf-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="b37cf-119">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="b37cf-119">Preparing the scene</span></span>

<span data-ttu-id="b37cf-120">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="b37cf-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="b37cf-121">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="b37cf-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="b37cf-122">**ButtonParent;**</span><span class="sxs-lookup"><span data-stu-id="b37cf-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="b37cf-123">**DebugWindow;**</span><span class="sxs-lookup"><span data-stu-id="b37cf-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="b37cf-124">**Instructions;**</span><span class="sxs-lookup"><span data-stu-id="b37cf-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="b37cf-125">**ParentAnchor.**</span><span class="sxs-lookup"><span data-stu-id="b37cf-125">**ParentAnchor** prefabs</span></span>

![Unity с выбранными добавленными заготовками](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="b37cf-127">Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="b37cf-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="b37cf-128">Выберите объект **MixedRealityToolkit** в окне Hierarchy (Иерархия) и нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор), чтобы добавить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="b37cf-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="b37cf-129">диспетчер привязок AR (скрипт);</span><span class="sxs-lookup"><span data-stu-id="b37cf-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="b37cf-130">DisableDiagnosticsSystem (скрипт).</span><span class="sxs-lookup"><span data-stu-id="b37cf-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="b37cf-131">Объект MixedRealityToolkit в Unity с добавленными компонентами AR Anchor Manager и DisableDiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="b37cf-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="b37cf-132">Существует известная ошибка в ASA v2.9.0 и v2.10.0-preview.1, которая требует размещения в сцене двух дополнительных объектов.</span><span class="sxs-lookup"><span data-stu-id="b37cf-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="b37cf-133">Нажмите кнопку **Add Component** (Добавить компонент) в окне инспектора, чтобы добавить в объект **MixedRealityToolkit** диспетчер камер AR Camera Manager (скрипт) и сеанс AR Session (скрипт).</span><span class="sxs-lookup"><span data-stu-id="b37cf-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="b37cf-134">Не забудьте отключить камеру, которая создается автоматически при добавлении диспетчера AR Camera Manager (скрипт), сняв флажок рядом с объектом Camera в окне инспектора.</span><span class="sxs-lookup"><span data-stu-id="b37cf-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="b37cf-135">Эта проблема будет устранена в полном выпуске ASA v2.10.0.</span><span class="sxs-lookup"><span data-stu-id="b37cf-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
>

> [!NOTE]
> <span data-ttu-id="b37cf-136">При добавлении компонента диспетчера привязок AR Anchor Manager (скрипт) автоматически добавляется компонент источника сеанса AR Session Origin (скрипт), так как он необходим компоненту диспетчера привязок AR (скрипт).</span><span class="sxs-lookup"><span data-stu-id="b37cf-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="b37cf-137">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="b37cf-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="b37cf-138">В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.</span><span class="sxs-lookup"><span data-stu-id="b37cf-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="b37cf-139">В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-140">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-140">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-141">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StartAzureSession](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="b37cf-143">В окне иерархии выберите следующую кнопку с именем **StopAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-144">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-144">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-145">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки StopAzureSession](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="b37cf-147">В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-148">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-148">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-149">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b37cf-150">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="b37cf-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки CreateAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="b37cf-152">В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-153">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-153">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-154">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b37cf-155">В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="b37cf-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity с настроенным событием OnClick для кнопки RemoveLocalAnchor](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="b37cf-157">В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-158">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-158">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-159">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки FindAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="b37cf-161">В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b37cf-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="b37cf-162">Назначьте объект **ParentAnchor** в качестве прослушивателя для события On Click (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="b37cf-162">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="b37cf-163">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.</span><span class="sxs-lookup"><span data-stu-id="b37cf-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для кнопки DeleteAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="b37cf-165">Подключение сцены к ресурсу Azure</span><span class="sxs-lookup"><span data-stu-id="b37cf-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="b37cf-166">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт).</span><span class="sxs-lookup"><span data-stu-id="b37cf-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="b37cf-167">Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.</span><span class="sxs-lookup"><span data-stu-id="b37cf-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="b37cf-168">В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="b37cf-169">В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="b37cf-170">В поле **Spatial Anchors Account Domain** (Домен учетной записи пространственных привязок) укажите **домен учетной записи** Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity с настроенным диспетчером пространственных привязок](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="b37cf-172">Изучение базового поведения Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="b37cf-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="b37cf-173">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="b37cf-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="b37cf-174">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="b37cf-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="b37cf-175">Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="b37cf-176">Переместите куб в другое расположение.</span><span class="sxs-lookup"><span data-stu-id="b37cf-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="b37cf-177">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-177">Start Azure Session</span></span>
3. <span data-ttu-id="b37cf-178">Создайте привязку Azure (она создается в расположении, где находится куб).</span><span class="sxs-lookup"><span data-stu-id="b37cf-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="b37cf-179">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-179">Stop Azure Session</span></span>
5. <span data-ttu-id="b37cf-180">Удалите локальную привязку (позволяет пользователю перемещать куб).</span><span class="sxs-lookup"><span data-stu-id="b37cf-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="b37cf-181">Переместите куб в другое место.</span><span class="sxs-lookup"><span data-stu-id="b37cf-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="b37cf-182">Запустите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-182">Start Azure Session</span></span>
8. <span data-ttu-id="b37cf-183">Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).</span><span class="sxs-lookup"><span data-stu-id="b37cf-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="b37cf-184">Удалите привязку Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="b37cf-185">Завершите сеанс Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-185">Stop Azure session</span></span>

![Unity с выбранным объектом Instructions](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="b37cf-187">Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="b37cf-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="b37cf-188">Привязка к взаимодействию</span><span class="sxs-lookup"><span data-stu-id="b37cf-188">Anchoring an experience</span></span>

<span data-ttu-id="b37cf-189">В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="b37cf-190">С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой.</span><span class="sxs-lookup"><span data-stu-id="b37cf-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="b37cf-191">Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="b37cf-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="b37cf-192">В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора настройте компонент **Transform** (Преобразование).</span><span class="sxs-lookup"><span data-stu-id="b37cf-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="b37cf-193">Измените значение **Scale X** (Масштаб Х) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="b37cf-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="b37cf-194">Измените значение **Scale Z** (Масштаб Z) на 1.1.</span><span class="sxs-lookup"><span data-stu-id="b37cf-194">Change **Scale Z** to 1.1</span></span>

![Unity с выбранным объектом ParentAnchor, для которого выполнено позиционирование и масштабирование](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="b37cf-196">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.</span><span class="sxs-lookup"><span data-stu-id="b37cf-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity с выбранной добавленной заготовкой RoverExplorer_Complete](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="b37cf-198">Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor**, чтобы сделать его дочерним объектом объекта ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="b37cf-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity с объектом RoverExplorer_Complete, настроенным как дочерний объект ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="b37cf-200">Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.</span><span class="sxs-lookup"><span data-stu-id="b37cf-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="b37cf-201">Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом учебнике), включение ограничивающего элемента вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.</span><span class="sxs-lookup"><span data-stu-id="b37cf-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b37cf-202">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b37cf-202">Congratulations</span></span>

<span data-ttu-id="b37cf-203">В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="b37cf-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="b37cf-204">В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure,</span><span class="sxs-lookup"><span data-stu-id="b37cf-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="b37cf-205">а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="b37cf-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="b37cf-206">В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.</span><span class="sxs-lookup"><span data-stu-id="b37cf-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b37cf-207">Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="b37cf-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
