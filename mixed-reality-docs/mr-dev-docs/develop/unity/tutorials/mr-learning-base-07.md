---
title: Взаимодействие с трехмерными объектами
description: Из этого курса вы узнаете, как использовать Mixed Reality Toolkit (MRTK) для взаимодействия с трехмерными объектами и манипулирования ими в приложениях смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, взаимодействие с объектами, ограничивающие прямоугольники
ms.localizationpriority: high
ms.openlocfilehash: c9acb72b2ad961737f5ce3f21c048fc80024b49d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007934"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="cf86d-104">7. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="cf86d-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="cf86d-105">В этом учебнике вы узнаете, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="cf86d-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="cf86d-106">Вы также узнаете, как добавлять ограничивающие рамки вокруг трехмерных объектов, чтобы упростить управление манипулированием объектов.</span><span class="sxs-lookup"><span data-stu-id="cf86d-106">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="cf86d-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="cf86d-107">Objectives</span></span>

* <span data-ttu-id="cf86d-108">Узнайте, как настроить трехмерные объекты, чтобы с ними можно было взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="cf86d-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="cf86d-109">Узнайте, как добавить ограничивающие рамки для трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="cf86d-109">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="cf86d-110">Работа с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="cf86d-110">Manipulating 3D objects</span></span>

<span data-ttu-id="cf86d-111">В этом разделе вы добавите возможность манипулирования всеми деталями лунохода, упорядоченными в таблице, во время работы с [учебником по размещению объектов в сцене](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="cf86d-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="cf86d-112">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="cf86d-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="cf86d-113">Добавить компонент Object Manipulator (Script) (Манипулятор объектами — скрипт) ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="cf86d-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="cf86d-114">Добавить компонент NearInteractionGrabbable ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="cf86d-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="cf86d-115">Настройте компонент Object Manipulator (Script) (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cf86d-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="cf86d-116">Чтобы **объект поддерживал манипуляции**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="cf86d-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cf86d-117">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="cf86d-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="cf86d-118">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cf86d-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="cf86d-119">Чтобы **объект поддерживал манипуляции** и **захват отслеживаемыми руками**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="cf86d-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cf86d-120">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="cf86d-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="cf86d-121">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="cf86d-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="cf86d-122">компонент **NearInteractionGrabbable**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="cf86d-123">Кроме того, необходимо настроить обозреватель лунохода, чтобы можно было разместить детали лунохода и выполнить его полноценную сборку.</span><span class="sxs-lookup"><span data-stu-id="cf86d-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="cf86d-124">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все дочерние объекты деталей лунохода и **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="cf86d-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="cf86d-125">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="cf86d-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="cf86d-126">компонент **NearInteractionGrabbable**;</span><span class="sxs-lookup"><span data-stu-id="cf86d-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="cf86d-127">компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cf86d-127">**Part Assembly Controller (Script)** component</span></span>

![Unity с выбранным объектом RoverAssembly и всеми частями лунохода и добавленными компонентами](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="cf86d-129">Чтобы выбрать несколько объектов, которые не расположены рядом, нажмите и удерживайте клавишу CTRL и выберите любой объект с помощью кнопки мыши.</span><span class="sxs-lookup"><span data-stu-id="cf86d-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="cf86d-130">Для выполнения задач этого учебника к деталям лунохода уже добавлены коллайдеры.</span><span class="sxs-lookup"><span data-stu-id="cf86d-130">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="cf86d-131">Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="cf86d-131">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="cf86d-132">Элемент управления сборкой деталей (скрипт) не является частью МRТК, но включен в активы учебника.</span><span class="sxs-lookup"><span data-stu-id="cf86d-132">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="cf86d-133">Выбрав все объекты деталей лунохода и объект RoverAssembly, в окне Inspector (Инспектор) настройте компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-133">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="cf86d-134">В раскрывающемся списке **Two Handed Manipulation Type** (Тип манипуляции двумя руками), снимите флажок Scale (Масштаб), чтобы были выбраны только параметры **Move** (Перемещение) и **Rotate** (Поворот).</span><span class="sxs-lookup"><span data-stu-id="cf86d-134">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity с настроенным типом манипуляции двумя руками](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="cf86d-136">На этом этапе вы включили манипулирование объектами для всех объектов деталей лунохода и объекта RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="cf86d-136">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="cf86d-137">В окне проекта перейдите к папке **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio**, чтобы найти аудиоклипы:</span><span class="sxs-lookup"><span data-stu-id="cf86d-137">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![Окно проекта Unity с выбранной папкой аудио](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="cf86d-139">В окне Hierarchy (Иерархия) выберите все **объекты деталей лунохода**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Audio Sources** (Источники аудио) и настроить его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-139">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="cf86d-140">В поле **AudioClip** укажите аудиоклип **MRTK_Scale_Start**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-140">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="cf86d-141">Снимите флажок **Play On Awake** (Воспроизвести при загрузке).</span><span class="sxs-lookup"><span data-stu-id="cf86d-141">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="cf86d-142">Для параметра **Spatial Blend** (Пространственное наложение) установите значение 1.</span><span class="sxs-lookup"><span data-stu-id="cf86d-142">Change **Spatial Blend** to 1</span></span>

![Unity с выбранными всеми частями лунохода и добавленным и настроенным компонентом Audio Source](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="cf86d-144">В окне Hierarchy (Иерархия) разверните объект RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**, чтобы отобразить все объекты указания расположения, а затем выберите первую деталь лунохода, RoverParts > **Camera_Part** и настройте компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-144">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="cf86d-145">В поле **Location To Place** (Расположение для размещения) укажите объект **Camera_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-145">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity с настроенным компонентом Camera_Part PartAssemblyController](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="cf86d-147">**Повторите** это действие для каждого из оставшихся объектов деталей лунохода и объекта RoverAssembly, чтобы настроить компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-147">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="cf86d-148">Для **Generator_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Generator_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-148">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="cf86d-149">Для **Lights_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Lights_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-149">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="cf86d-150">Для **UHFAntenna_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **UHFAntenna_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-150">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="cf86d-151">Для **Spectrometer_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Spectrometer_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-151">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="cf86d-152">Для **RoverAssembly** укажите сам объект, т. е. тот же объект **RoverAssembly** в поле **Location To Place** (Расположение для размещения).</span><span class="sxs-lookup"><span data-stu-id="cf86d-152">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="cf86d-153">В окне Hierarchy (Иерархия) выберите RoverExplorer > Buttons (Кнопки) > объект кнопки **Reset** (Сброс), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-153">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="cf86d-154">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-154">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cf86d-155">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PartAssemblyController** > **ResetPlacement ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="cf86d-155">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием Reset для объекта кнопки OnClick](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="cf86d-157">Теперь, войдя в игровой режим, вы сможете поместить детали на луноход в режиме ближнего или дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="cf86d-157">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="cf86d-158">Когда деталь будет близка к соответствующей подсказке о размещении, она автоматически закрепится в нужном месте и станет деталью лунохода.</span><span class="sxs-lookup"><span data-stu-id="cf86d-158">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="cf86d-159">Чтобы сбросить параметры размещения, нажмите кнопку Reset (Сброс):</span><span class="sxs-lookup"><span data-stu-id="cf86d-159">To reset the placements, you can press the Reset button:</span></span>

![Разделенное представление Unity в режиме воспроизведения с нажатой кнопкой Reset](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="cf86d-161">Дополнительные сведения о компоненте Object Manipulator (Манипулятор объектами) и его свойствах вы можете получить в [этом учебнике](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="cf86d-161">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="cf86d-162">Добавление ограничивающих рамок</span><span class="sxs-lookup"><span data-stu-id="cf86d-162">Adding bounding boxes</span></span>

<span data-ttu-id="cf86d-163">Ограничивающие рамки делают манипулирование объектами одной рукой более простым и интуитивно понятным при ближнем и дальнем взаимодействии, предоставляя маркеры для масштабирования и вращения.</span><span class="sxs-lookup"><span data-stu-id="cf86d-163">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="cf86d-164">В этом примере в объект RoverExplorer будет добавлена ограничивающая рамка, чтобы можно было легко использовать все возможности для перемещения, вращения и масштабирования деталей.</span><span class="sxs-lookup"><span data-stu-id="cf86d-164">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="cf86d-165">Кроме того, вы настроите параметры меню, чтобы можно было включить и отключить ограничивающую рамку.</span><span class="sxs-lookup"><span data-stu-id="cf86d-165">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="cf86d-166">В окне Hierarchy (Иерархия) выберите объект **RoverExplorer**, а затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="cf86d-166">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="cf86d-167">компонент **BoundingBox**;</span><span class="sxs-lookup"><span data-stu-id="cf86d-167">**BoundingBox** component</span></span>
* <span data-ttu-id="cf86d-168">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="cf86d-168">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="cf86d-169">Затем **снимите флажок** рядом с компонентами, чтобы **отключить** их по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="cf86d-169">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![Unity с выбранным объектом RoverExplorer и добавленными и отключенными компонентами](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cf86d-171">Визуализация ограничивающей рамки создается во время выполнения. Поэтому вы не увидите ее до входа в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="cf86d-171">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="cf86d-172">Компонент BoundingBox будет автоматически добавлять компонент NearInteractionGrabbable во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cf86d-172">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="cf86d-173">Поэтому не нужно добавлять этот компонент для захвата вложенных объектов с помощью отслеживаемых рук.</span><span class="sxs-lookup"><span data-stu-id="cf86d-173">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="cf86d-174">В окне Hierarchy (Иерархия) разверните в меню объект **ButtonCollection**, чтобы отобразить четыре кнопки и переименовать третью кнопку на **BoundingBox_Enable**. Затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="cf86d-175">Установите для параметра **Main Label Text** (Текст основной метки) значение **Enable** (Включить).</span><span class="sxs-lookup"><span data-stu-id="cf86d-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="cf86d-176">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cf86d-177">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="cf86d-177">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cf86d-178">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="cf86d-179">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="cf86d-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="cf86d-180">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cf86d-181">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="cf86d-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cf86d-182">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="cf86d-183">Оставьте **значок** куба с ограничивающей рамкой.</span><span class="sxs-lookup"><span data-stu-id="cf86d-183">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![Unity с выбранным объектом кнопки BoundingBox_Enable и настроенным компонентом Button Config Helper](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="cf86d-185">Переименуйте четвертую и последнюю кнопку на **BoundingBox_Disable**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cf86d-185">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="cf86d-186">Установите для параметра **Main Label Text** (Текст основной метки) значение **Disable** (Отключить).</span><span class="sxs-lookup"><span data-stu-id="cf86d-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="cf86d-187">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cf86d-188">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="cf86d-188">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cf86d-189">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="cf86d-190">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="cf86d-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="cf86d-191">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cf86d-192">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="cf86d-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cf86d-193">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="cf86d-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="cf86d-194">Измените **значок** на значок куба с ограничивающей рамкой.</span><span class="sxs-lookup"><span data-stu-id="cf86d-194">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![Unity с выбранным объектом кнопки BoundingBox_Disable и настроенным компонентом Button Config Helper](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="cf86d-196">Теперь, войдя в игровой режим и включив ограничивающую рамку, нажав кнопку Enable (Включить), вы можете использовать режим ближнего или дальнего взаимодействия для перемещения, вращения и масштабирования ограничивающей рамки. Чтобы повторно отключить ограничивающую рамку, нажмите кнопку Disable (Отключить):</span><span class="sxs-lookup"><span data-stu-id="cf86d-196">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![Разделенное представление Unity в режиме воспроизведения с изменением ограничивающего прямоугольника](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="cf86d-198">Дополнительные сведения о компоненте Bounding Box (Ограничивающая рамка) и его свойствах вы можете получить в [этом руководстве](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="cf86d-198">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="cf86d-199">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cf86d-199">Congratulations</span></span>

<span data-ttu-id="cf86d-200">В этом учебнике вы узнали, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="cf86d-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="cf86d-201">Вы также узнали, как добавлять ограничивающие рамки вокруг трехмерных объектов, чтобы упростить управление манипулированием объектов.</span><span class="sxs-lookup"><span data-stu-id="cf86d-201">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf86d-202">Следующее руководство: 8. Использование отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="cf86d-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
