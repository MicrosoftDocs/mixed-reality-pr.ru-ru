---
title: Начало работы с голографическим удаленным взаимодействием с ПК
description: Пройдите этот курс, чтобы узнать, как обеспечить потоковую передачу приложений смешанной реальности с компьютера на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, Hololens, удаленное взаимодействие с компьютером, подсказки, отслеживание глаз
ms.localizationpriority: high
ms.openlocfilehash: 05831ff19a998bd5e99ab5d20c3fb045a09c55e9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175445"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="22051-104">1. Начало работы с голографическим удаленным взаимодействием с ПК</span><span class="sxs-lookup"><span data-stu-id="22051-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="22051-105">Вас приветствует серия учебников по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="22051-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="22051-106">Из этой серии учебников из двух частей вы узнаете, как выполнить демонстрацию взаимодействия со смешанной реальностью и как создать приложение на ПК для голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="22051-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="22051-107">Из этого учебника вы узнаете, как создать интерфейс смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="22051-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="22051-108">Здесь будут продемонстрированы элементы пользовательского интерфейса, функции управления трехмерными моделями, обрезки моделей, а также функции отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="22051-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="22051-109">Во втором учебнике вы научитесь [создавать приложение на ПК для голографического удаленного взаимодействия](mr-learning-pc-holographic-remoting-02.md)</span><span class="sxs-lookup"><span data-stu-id="22051-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="22051-110">и подключаться к HoloLens 2 в любой момент с помощью визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="22051-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="22051-111">Задачи</span><span class="sxs-lookup"><span data-stu-id="22051-111">Objectives</span></span>

* <span data-ttu-id="22051-112">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="22051-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="22051-113">Взаимодействие с голограммами через кнопки и элементы пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="22051-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="22051-114">Настройка трехмерных объектов для функции обрезки.</span><span class="sxs-lookup"><span data-stu-id="22051-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="22051-115">Получение сведений об активации подсказок с помощью отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="22051-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22051-116">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="22051-116">Prerequisites</span></span>

* <span data-ttu-id="22051-117">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="22051-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="22051-118">Базовые навыки работы с C#.</span><span class="sxs-lookup"><span data-stu-id="22051-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="22051-119">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="22051-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="22051-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020/2019 LTS и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="22051-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="22051-121">Мы **настоятельно рекомендуем** предварительно ознакомиться с серией учебников [по началу работы](mr-learning-base-01.md) или иметь хотя бы базовый опыт работы с Unity и MRTK.</span><span class="sxs-lookup"><span data-stu-id="22051-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="22051-122">В этой серии руководств учитывается поддержка Unity 2020 LTS (в настоящее время 2020.3.x), если вы используете Open XR, и Unity 2019 LTS (в настоящее время 2019.4.x), если вы используете устаревшую версию WSA. Это заменяет любые требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="22051-122">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR and Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="22051-123">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="22051-123">Creating and preparing the Unity project</span></span>

<span data-ttu-id="22051-124">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="22051-124">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="22051-125">Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:</span><span class="sxs-lookup"><span data-stu-id="22051-125">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="22051-126">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="22051-126">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="22051-127">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="22051-127">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="22051-128">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="22051-128">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="22051-129">Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="22051-129">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="22051-130">[Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и присвоение ей подходящего имени, например **Голографическое удаленное взаимодействие с ПК**.</span><span class="sxs-lookup"><span data-stu-id="22051-130">[Creating and setting the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="22051-131">Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены.</span><span class="sxs-lookup"><span data-stu-id="22051-131">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="22051-132">Измените параметры отображения сетки отслеживания в пространстве на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="22051-132">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="22051-133">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="22051-133">Importing the tutorial assets</span></span>

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="22051-134">Настройка и подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="22051-134">Configuring and preparing the scene</span></span>

<span data-ttu-id="22051-135">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="22051-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="22051-136">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="22051-136">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="22051-137">Удерживая нажатой клавишу CTRL, щелкните шесть заготовок, перечисленных ниже.</span><span class="sxs-lookup"><span data-stu-id="22051-137">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="22051-138">ButtonParent;</span><span class="sxs-lookup"><span data-stu-id="22051-138">ButtonParent</span></span>
* <span data-ttu-id="22051-139">ClippingObjects;</span><span class="sxs-lookup"><span data-stu-id="22051-139">ClippingObjects</span></span>
* <span data-ttu-id="22051-140">HandSpatialMapButton;</span><span class="sxs-lookup"><span data-stu-id="22051-140">HandSpatialMapButton</span></span>
* <span data-ttu-id="22051-141">Инструкции</span><span class="sxs-lookup"><span data-stu-id="22051-141">Instructions</span></span>
* <span data-ttu-id="22051-142">ModelParent;</span><span class="sxs-lookup"><span data-stu-id="22051-142">ModelParent</span></span>
* <span data-ttu-id="22051-143">Платформа</span><span class="sxs-lookup"><span data-stu-id="22051-143">Platform</span></span>

![Unity с заготовками для добавления в выбранную сцену](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="22051-145">Перетащите эти модели из папки заготовок в окно **Hierarchy** (Иерархия).</span><span class="sxs-lookup"><span data-stu-id="22051-145">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![Unity с выбранными добавленными заготовками](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="22051-147">Чтобы перенести фокус на объекты сцены, дважды щелкните объект **ModelParent**, а затем снова немного увеличьте масштаб представления:</span><span class="sxs-lookup"><span data-stu-id="22051-147">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![Unity с объектом ModelParent в фокусе](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="22051-149">Если вы считаете, что большие значки в сцене (как большие "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение.</span><span class="sxs-lookup"><span data-stu-id="22051-149">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="22051-150">Настройка кнопок для управления сценой</span><span class="sxs-lookup"><span data-stu-id="22051-150">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="22051-151">В этом разделе вы добавите скрипты в сцену, чтобы создать события кнопки, демонстрирующие базовые принципы переключения моделей и функций обрезки.</span><span class="sxs-lookup"><span data-stu-id="22051-151">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="22051-152">1. Настройка компонента Interactable (Script) (Интерактивный — скрипт)</span><span class="sxs-lookup"><span data-stu-id="22051-152">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="22051-153">В окне Hierarchy (Иерархия) разверните объект **ButtonParent** и выберите **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="22051-153">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="22051-154">В окне Inspector (Инспектор) найдите компонент **Interactable (Script)** (Интерактивный — скрипт) и щелкните значок **+** в событии **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="22051-154">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![Unity с добавленным событием NextButton OnClick](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="22051-156">Сохраняя объект **NextButton** выделенным в окне Hierarchy (Иерархия), щелкните и перетащите объект **ButtonParent** из окна (Иерархия) в пустое поле **None (Object)** (Отсутствует (объект)) только что созданного события, чтобы объект ButtonParent ожидал передачи данных о событии нажатия для этой кнопки:</span><span class="sxs-lookup"><span data-stu-id="22051-156">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![Unity с настроенным прослушивателем событий NextButton OnClick](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="22051-158">Откройте раскрывающийся список **No Function** (Нет функции) того же события.</span><span class="sxs-lookup"><span data-stu-id="22051-158">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="22051-159">Затем выберите **ViewButtonControl** > **NextModel ()** , чтобы установить функцию **NextModel ()** в качестве действия, запускаемого при срабатывании события нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="22051-159">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![Выбор действия события NextButton OnClick в меню Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="22051-161">2. Настройка остальных кнопок</span><span class="sxs-lookup"><span data-stu-id="22051-161">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="22051-162">Для всех остальных кнопок повторно выполните процессы, которые описаны выше, чтобы назначить функции событиям **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22051-162">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="22051-163">Для объекта PreviousButton назначьте функцию **ViewButtonContro** l > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="22051-163">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="22051-164">Для объекта ClippingButton выберите функцию **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="22051-164">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="22051-165">3. Настройка компонентов View Button Control (Script) (Элемент управления кнопкой просмотра — скрипт) и Toggle Button (Script) (Выключатель — скрипт)</span><span class="sxs-lookup"><span data-stu-id="22051-165">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="22051-166">Теперь кнопки настроены, чтобы продемонстрировать функции переключения и обрезки модели.</span><span class="sxs-lookup"><span data-stu-id="22051-166">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="22051-167">Время добавить трехмерные модели и объекты обрезки в скрипт.</span><span class="sxs-lookup"><span data-stu-id="22051-167">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="22051-168">Мы предоставили шесть различных трехмерных моделей для демонстрации, разверните ***ModelParentobject***, чтобы предоставить эти трехмерные модели.</span><span class="sxs-lookup"><span data-stu-id="22051-168">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="22051-169">Сохраняя объект ButtonParent выделенным в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите **View Button Control (Script)** (Элемент управления кнопкой просмотра — скрипт) и разверните переменную **Models** (Модели).</span><span class="sxs-lookup"><span data-stu-id="22051-169">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="22051-170">В поле **Size** (Размер) введите число трехмерных моделей, которые будут находиться в сцене.</span><span class="sxs-lookup"><span data-stu-id="22051-170">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="22051-171">В нашем случае — 6.</span><span class="sxs-lookup"><span data-stu-id="22051-171">In this case, it would be six.</span></span> <span data-ttu-id="22051-172">Будет создано поле для добавления новых трехмерных моделей.</span><span class="sxs-lookup"><span data-stu-id="22051-172">It will create fields for adding new 3D models.</span></span>

![Unity с полями компонента скрипта ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="22051-174">Перетащите каждый дочерний объект объекта ModelParent в эти поля.</span><span class="sxs-lookup"><span data-stu-id="22051-174">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![Unity с настроенными полями компонента скрипта ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="22051-176">Перетащите объект **ClippingObjects** из окна Hierarchy (Иерархия) в компонент **Toggle Button (Script)** (Переключатель — скрипт) поля **Clipping Object** (Обрезаемый объект).</span><span class="sxs-lookup"><span data-stu-id="22051-176">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="22051-177">Старайтесь использовать только родительский объект кнопки.</span><span class="sxs-lookup"><span data-stu-id="22051-177">Stay in button parent object only.</span></span>

![Unity с настроенным полем компонента скрипта ToggleButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="22051-179">В окне Hierarchy (Иерархия) выберите заготовку **ClippingObjects** и включите ее в окне Inspector (Инспектор), чтобы включить объекты обрезки.</span><span class="sxs-lookup"><span data-stu-id="22051-179">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="22051-180">Настройка объектов обрезки для включения функции обрезки</span><span class="sxs-lookup"><span data-stu-id="22051-180">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="22051-181">В этом разделе вы добавите отрисовщик дочерних объектов MarsCuriosityRover в отдельный объект обрезки, чтобы продемонстрировать обрезку модели MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="22051-181">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="22051-182">В окне Hierarchy (Иерархия) разверните объект **ClippingObjects**, чтобы предоставить три различных объекта обрезки, которые будут использоваться в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="22051-182">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="22051-183">Чтобы настроить объект **ClippingSphere**, щелкните его, а затем в окне Inspector (Инспектор) выберите компонент **Clipping Sphere (Script)** (Обрезка сферы — скрипт).</span><span class="sxs-lookup"><span data-stu-id="22051-183">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="22051-184">Введите количество отрисовщиков в поле размера, которое необходимо добавить для трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="22051-184">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="22051-185">В этом случае для дочерних объектов MarsCuriosityRover добавьте 10 отрисовщиков.</span><span class="sxs-lookup"><span data-stu-id="22051-185">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="22051-186">Будут созданы поля для добавления отрисовщиков. Перетащите объекты дочерней модели MarsCuriosityRover в эти поля.</span><span class="sxs-lookup"><span data-stu-id="22051-186">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![Unity с настроенными полями компонента скрипта ClippingSphere](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="22051-188">Выполните тот же процесс и добавьте отрисовщики дочерних объектов MarsCuriosityRover в объекты **ClippingBox** и **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="22051-188">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="22051-189">В этом учебнике для демонстрации функции обрезки будет использоваться только модель MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="22051-189">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="22051-190">Функции обрезки были добавлены к большему количеству моделей. В результате этого размер отрисовщика увеличился и были добавлены индивидуальные отрисовщики сетки.</span><span class="sxs-lookup"><span data-stu-id="22051-190">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="22051-191">Настройка отслеживания взгляда для выделения всплывающих подсказок</span><span class="sxs-lookup"><span data-stu-id="22051-191">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="22051-192">Из этого раздела вы узнаете, как включить отслеживание взгляда в нашем демонстрационном проекте.</span><span class="sxs-lookup"><span data-stu-id="22051-192">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="22051-193">Например, вы реализуете функции, чтобы выделить прикрепленные к деталям MarsCuriosityRover подсказки, когда вы на них смотрите, и скрыть их при отводе взгляда.</span><span class="sxs-lookup"><span data-stu-id="22051-193">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="22051-194">1. Определите целевые объекты и связанные с ними подсказки.</span><span class="sxs-lookup"><span data-stu-id="22051-194">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="22051-195">В окне Hierarchy (Иерархия) выберите объект ModelParent.</span><span class="sxs-lookup"><span data-stu-id="22051-195">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="22051-196">Разверните раздел ***MarsCuriosity -> Rover** _, чтобы найти пять основных частей MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** и **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="22051-196">Expand the ***MarsCuriosity -> Rover** _ to find five main parts of the MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="22051-197">Обратите внимание на пять соответствующих объектов подсказок, связанных с деталями MarsCuriosityRover в окне Hierarchy (Иерархия).</span><span class="sxs-lookup"><span data-stu-id="22051-197">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="22051-198">Эти объекты будут настроены, чтобы выделять элементы при просмотре деталей MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="22051-198">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![Unity с выбранным и развернутым объектом Rover](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="22051-200">2. Реализация событий While Looking At Target () и On Look Away ()</span><span class="sxs-lookup"><span data-stu-id="22051-200">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="22051-201">В окне Hierarchy (Иерархия) выберите объект \***POI-Camera** _.</span><span class="sxs-lookup"><span data-stu-id="22051-201">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="22051-202">В окне Inspector (Инспектор) найдите компонент _ *Eye Tracking Target (Script)* \* (Целевой объект отслеживания взгляда — скрипт) и настройте события **While Looking At Target ()**  & **On Look Away ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22051-202">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="22051-203">В поле **None (Object)** (Отсутствует (объект)) укажите объект **POI-Camera ToolTip**.</span><span class="sxs-lookup"><span data-stu-id="22051-203">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="22051-204">В раскрывающемся списке **No Function** (Без функции) события **While Looking At Target ()** выберите **GameObject** > **SetActive (bool).**</span><span class="sxs-lookup"><span data-stu-id="22051-204">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="22051-205">Установите **флажок**, чтобы выделить всплывающую подсказку в качестве действия, запускаемого при просмотре целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="22051-205">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![Unity выполняет настройку события EyeTrackingTarget WhileLookingAtTarget](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="22051-207">Выполните тот же процесс и выберите раскрывающийся список **No Function** (Без функции) прослушивателя событий **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="22051-207">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="22051-208">Затем выберите **GameObject** > **SetActive (bool**) и снимите **флажок**, чтобы скрыть всплывающую подсказку как действие, запускаемое при отведении взгляда от целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="22051-208">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![Unity с настроенным событием EyeTrackingTarget OnLookAway](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="22051-210">Выполните тот же процесс и назначьте соответствующие объекты подсказки тем же деталям **MarsCuriosityRover** событий **While Looking At Target ()**  & **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="22051-210">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="22051-211">Чтобы включить отслеживание взгляда, следуйте приведенным [рекомендациям](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="22051-211">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="22051-212">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="22051-212">Congratulations</span></span>

<span data-ttu-id="22051-213">Из этого учебника вы узнали, как создать взаимодействие в смешанной реальности с использованием элементов пользовательского интерфейса, управления трехмерными моделями, обрезкой моделей и функции отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="22051-213">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="22051-214">В этом учебнике показано, как использовать объекты NextButton и PreviousButton, позволяющие исследовать возможности средства просмотра трехмерных моделей.</span><span class="sxs-lookup"><span data-stu-id="22051-214">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="22051-215">ClippingObjectButton позволяет включить функцию обрезки объектов и интерфейса.</span><span class="sxs-lookup"><span data-stu-id="22051-215">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="22051-216">Кроме того, в учебнике показано, как использовать элемент отслеживания взгляда, позволяющий выделять всплывающие подсказки в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="22051-216">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="22051-217">На следующем занятии вы узнаете, как создать приложение для голографического удаленного взаимодействия с ПК для подключения к HoloLens 2 в любой момент, позволяя выполнить визуализацию трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="22051-217">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22051-218">Следующий урок. 2. Создание приложения для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="22051-218">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)