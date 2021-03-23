---
title: Взаимодействие с трехмерными объектами
description: Из этого курса вы узнаете, как использовать Mixed Reality Toolkit (MRTK) для взаимодействия с трехмерными объектами и манипулирования ими в приложениях смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, взаимодействие с объектами, ограничивающие элементы управления
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237245"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="eeaff-104">7. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="eeaff-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="eeaff-105">В этом учебнике вы узнаете, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="eeaff-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="eeaff-106">Вы также узнаете, как добавлять ограничивающие элементы управления вокруг трехмерных объектов, чтобы упростить манипулирование этими объектами.</span><span class="sxs-lookup"><span data-stu-id="eeaff-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="eeaff-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="eeaff-107">Objectives</span></span>

* <span data-ttu-id="eeaff-108">Узнайте, как настроить трехмерные объекты, чтобы с ними можно было взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="eeaff-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="eeaff-109">Узнайте, как добавлять ограничивающие элементы управления к трехмерным объектам.</span><span class="sxs-lookup"><span data-stu-id="eeaff-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="eeaff-110">Работа с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="eeaff-110">Manipulating 3D objects</span></span>

<span data-ttu-id="eeaff-111">В этом разделе вы добавите возможность манипулирования всеми деталями лунохода, упорядоченными в таблице, во время работы с [учебником по размещению объектов в сцене](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="eeaff-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="eeaff-112">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="eeaff-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="eeaff-113">Добавить компонент Object Manipulator (Script) (Манипулятор объектами — скрипт) ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="eeaff-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="eeaff-114">Добавить компонент NearInteractionGrabbable ко всем объектам деталей.</span><span class="sxs-lookup"><span data-stu-id="eeaff-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="eeaff-115">Настройте компонент Object Manipulator (Script) (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="eeaff-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="eeaff-116">Чтобы **объект поддерживал манипуляции**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="eeaff-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="eeaff-117">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="eeaff-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="eeaff-118">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="eeaff-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="eeaff-119">Чтобы **объект поддерживал манипуляции** и **захват отслеживаемыми руками**, он должен иметь следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="eeaff-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="eeaff-120">компонент **Collider** (Коллайдер), например Box Collider;</span><span class="sxs-lookup"><span data-stu-id="eeaff-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="eeaff-121">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="eeaff-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="eeaff-122">компонент **NearInteractionGrabbable**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="eeaff-123">Кроме того, необходимо настроить обозреватель лунохода, чтобы можно было разместить детали лунохода и выполнить его полноценную сборку.</span><span class="sxs-lookup"><span data-stu-id="eeaff-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="eeaff-124">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все дочерние объекты деталей лунохода и **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="eeaff-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="eeaff-125">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт);</span><span class="sxs-lookup"><span data-stu-id="eeaff-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="eeaff-126">компонент **NearInteractionGrabbable**;</span><span class="sxs-lookup"><span data-stu-id="eeaff-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="eeaff-127">компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт).</span><span class="sxs-lookup"><span data-stu-id="eeaff-127">**Part Assembly Controller (Script)** component</span></span>

![Unity с выбранным объектом RoverAssembly и всеми частями лунохода и добавленными компонентами](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="eeaff-129">Чтобы выбрать несколько объектов, которые не расположены рядом, нажмите и удерживайте клавишу CTRL и выберите любой объект с помощью кнопки мыши.</span><span class="sxs-lookup"><span data-stu-id="eeaff-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="eeaff-130">В нашем примере, когда добавляется компонент Object Manipulator (Script), автоматически добавляется и компонент Constraint Manager (Script), от которого тот зависит.</span><span class="sxs-lookup"><span data-stu-id="eeaff-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="eeaff-131">Для выполнения задач этого учебника к деталям лунохода уже добавлены коллайдеры.</span><span class="sxs-lookup"><span data-stu-id="eeaff-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="eeaff-132">Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="eeaff-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="eeaff-133">Элемент управления сборкой деталей (скрипт) не является частью МRТК, но включен в активы учебника.</span><span class="sxs-lookup"><span data-stu-id="eeaff-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="eeaff-134">Выбрав все объекты деталей лунохода и объект RoverAssembly, в окне Inspector (Инспектор) настройте компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="eeaff-135">В раскрывающемся списке **Two Handed Manipulation Type** (Тип манипуляции двумя руками), снимите флажок Scale (Масштаб), чтобы были выбраны только параметры **Move** (Перемещение) и **Rotate** (Поворот).</span><span class="sxs-lookup"><span data-stu-id="eeaff-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity с настроенным типом манипуляции двумя руками](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="eeaff-137">На этом этапе вы включили манипулирование объектами для всех объектов деталей лунохода и объекта RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="eeaff-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="eeaff-138">В окне Project (Проект) перейдите к папке **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio**, где находятся аудиоклипы:</span><span class="sxs-lookup"><span data-stu-id="eeaff-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![Окно проекта Unity с выбранной папкой аудио](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="eeaff-140">В окне Hierarchy (Иерархия) выберите все **объекты деталей лунохода**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Audio Sources** (Источники аудио) и настроить его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="eeaff-141">В поле **AudioClip** укажите аудиоклип **MRTK_Scale_Start**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="eeaff-142">Снимите флажок **Play On Awake** (Воспроизвести при загрузке).</span><span class="sxs-lookup"><span data-stu-id="eeaff-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="eeaff-143">Для параметра **Spatial Blend** (Пространственное наложение) установите значение 1.</span><span class="sxs-lookup"><span data-stu-id="eeaff-143">Change **Spatial Blend** to 1</span></span>

![Unity с выбранными всеми частями лунохода и добавленным и настроенным компонентом Audio Source](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="eeaff-145">В окне Hierarchy (Иерархия) разверните объект RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**, чтобы отобразить все объекты указания расположения, а затем выберите первую деталь лунохода, RoverParts > **Camera_Part** и настройте компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="eeaff-146">В поле **Location To Place** (Расположение для размещения) укажите объект **Camera_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity с настроенным компонентом Camera_Part PartAssemblyController](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="eeaff-148">**Повторите** это действие для каждого из оставшихся объектов деталей лунохода и объекта RoverAssembly, чтобы настроить компонент **Part Assembly Controller (Script)** (Элемент управления сборкой деталей — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="eeaff-149">Для **Generator_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Generator_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="eeaff-150">Для **Lights_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Lights_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="eeaff-151">Для **UHFAntenna_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **UHFAntenna_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="eeaff-152">Для **Spectrometer_Part** в поле **Location To Place** (Расположение для размещения) укажите объект **Spectrometer_PlacementHint**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="eeaff-153">Для **RoverAssembly** укажите сам объект, т. е. тот же объект **RoverAssembly** в поле **Location To Place** (Расположение для размещения).</span><span class="sxs-lookup"><span data-stu-id="eeaff-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="eeaff-154">В окне Hierarchy (Иерархия) выберите RoverExplorer > Buttons (Кнопки) > объект кнопки **Reset** (Сброс), затем в окне Inspector (Инспектор) настройте интерактивное событие **OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="eeaff-155">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="eeaff-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PartAssemblyController** > **ResetPlacement ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="eeaff-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием Reset для объекта кнопки OnClick](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="eeaff-158">Теперь, войдя в игровой режим, вы сможете поместить детали на луноход в режиме ближнего или дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="eeaff-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="eeaff-159">Когда деталь будет близка к соответствующей подсказке о размещении, она автоматически закрепится в нужном месте и станет деталью лунохода.</span><span class="sxs-lookup"><span data-stu-id="eeaff-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="eeaff-160">Чтобы сбросить параметры размещения, нажмите кнопку Reset (Сброс):</span><span class="sxs-lookup"><span data-stu-id="eeaff-160">To reset the placements, you can press the Reset button:</span></span>

![Разделенное представление Unity в режиме воспроизведения с нажатой кнопкой Reset](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="eeaff-162">Дополнительные сведения о компоненте Object Manipulator (Манипулятор объектами) и его свойствах вы можете получить в [этом учебнике](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) на [портале документации по MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span><span class="sxs-lookup"><span data-stu-id="eeaff-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="eeaff-163">Добавление ограничивающего элемента управления</span><span class="sxs-lookup"><span data-stu-id="eeaff-163">Adding Bounds Control</span></span>

<span data-ttu-id="eeaff-164">Ограничивающие элементы управления делают манипулирование объектами одной рукой более простым и интуитивно понятным при ближнем и дальнем взаимодействии, предоставляя маркеры для масштабирования и вращения.</span><span class="sxs-lookup"><span data-stu-id="eeaff-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="eeaff-165">В нашем примере вы добавите ограничивающий элемент управления в объект RoverExplorer, чтобы легко перемещать, вращать и масштабировать любые элементы среды.</span><span class="sxs-lookup"><span data-stu-id="eeaff-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="eeaff-166">Кроме того, вы добавите в меню возможность включать и отключать ограничивающий элемент управления.</span><span class="sxs-lookup"><span data-stu-id="eeaff-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="eeaff-167">В окне Hierarchy (Иерархия) выберите объект **RoverExplorer**, а затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="eeaff-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="eeaff-168">компонент **BoundsControl**;</span><span class="sxs-lookup"><span data-stu-id="eeaff-168">**BoundsControl** component</span></span>
* <span data-ttu-id="eeaff-169">компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).</span><span class="sxs-lookup"><span data-stu-id="eeaff-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="eeaff-170">Затем **снимите флажки** рядом со всеми компонентами, чтобы они были **отключены** по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="eeaff-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![Unity с выбранным объектом RoverExplorer и добавленными и отключенными компонентами](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="eeaff-172">Визуализация ограничивающего элемента управления создается только во время выполнения, поэтому вы не увидите его до переключения в игровой режим.</span><span class="sxs-lookup"><span data-stu-id="eeaff-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="eeaff-173">Компонент Object Manipulator (Script) автоматически добавляет компонент Constraint Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="eeaff-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="eeaff-174">В окне Hierarchy (Иерархия) разверните в меню объект **ButtonCollection**, чтобы отобразить четыре кнопки и переименовать третью кнопку на **BoundsControl_Enable**. Затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="eeaff-175">Установите для параметра **Main Label Text** (Текст основной метки) значение **Enable** (Включить).</span><span class="sxs-lookup"><span data-stu-id="eeaff-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="eeaff-176">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="eeaff-177">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundsControl** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="eeaff-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="eeaff-178">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="eeaff-179">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="eeaff-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="eeaff-180">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="eeaff-181">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="eeaff-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="eeaff-182">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="eeaff-183">В области **Icon** (Значок) сохраните значок куба без ограничивающего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eeaff-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![Unity с выбранным объектом кнопки BoundsControl_Enable и настроенным компонентом Button Config Helper](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="eeaff-185">Переименуйте четвертую и последнюю кнопку на **BoundsControl_Disable**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Помощник настройки кнопки — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eeaff-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="eeaff-186">Установите для параметра **Main Label Text** (Текст основной метки) значение **Disable** (Отключить).</span><span class="sxs-lookup"><span data-stu-id="eeaff-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="eeaff-187">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="eeaff-188">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundsControl** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="eeaff-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="eeaff-189">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="eeaff-190">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="eeaff-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="eeaff-191">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="eeaff-192">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="eeaff-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="eeaff-193">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="eeaff-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="eeaff-194">В области **Icon** (Значок) выберите значок куба с ограничивающим элементом управления.</span><span class="sxs-lookup"><span data-stu-id="eeaff-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![Unity с выбранным объектом кнопки BoundsControl_Disable и настроенным компонентом Button Config Helper](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="eeaff-196">Теперь, переключившись в игровой режим и включив ограничивающий элемент управления нажатием кнопки Enable (Включить), вы можете использовать режим ближнего или дальнего взаимодействия для перемещения, вращения и масштабирования ограничивающего элемента управления. Чтобы повторно отключить ограничивающий элемент управления, нажмите кнопку Disable (Отключить):</span><span class="sxs-lookup"><span data-stu-id="eeaff-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![Разделенное представление Unity в режиме воспроизведения с изменением ограничивающего элемента управления](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="eeaff-198">Дополнительные сведения о компоненте BoundsControl и его свойствах см. в [этом руководстве](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) на [портале документации по MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span><span class="sxs-lookup"><span data-stu-id="eeaff-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="eeaff-199">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="eeaff-199">Congratulations</span></span>

<span data-ttu-id="eeaff-200">В этом учебнике вы узнали, как включить манипулирование дальними и ближними трехмерными объектами и ограничить допустимые типы манипуляций.</span><span class="sxs-lookup"><span data-stu-id="eeaff-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="eeaff-201">Вы также узнали, как добавлять ограничивающие элементы управления вокруг трехмерных объектов, чтобы упростить манипулирование этими объектами.</span><span class="sxs-lookup"><span data-stu-id="eeaff-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eeaff-202">Следующее руководство: 8. Использование отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="eeaff-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
