---
title: Создание пользовательских интерфейсов
description: Из этого курса вы узнаете, как с помощью Mixed Reality Toolkit (MRTK) создавать статические и динамические пользовательские интерфейсы.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, заготовки, голограммы, советы
ms.localizationpriority: high
ms.openlocfilehash: 989de4871332608448619e75ffd760c616332533
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008064"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="8a58d-104">6. Создание пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="8a58d-104">6. Creating user interfaces</span></span>

<span data-ttu-id="8a58d-105">В этом учебнике показано, как создать простой пользовательский интерфейс, используя кнопки MRTK и заготовки меню вместе с компонентом Unity TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="8a58d-105">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="8a58d-106">Кроме того, здесь приведены сведения о том, как настроить кнопки для запуска событий и добавить динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="8a58d-106">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="8a58d-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="8a58d-107">Objectives</span></span>

* <span data-ttu-id="8a58d-108">Упорядочивание кнопок в коллекции</span><span class="sxs-lookup"><span data-stu-id="8a58d-108">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="8a58d-109">Использование заготовок меню MRTK</span><span class="sxs-lookup"><span data-stu-id="8a58d-109">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="8a58d-110">Взаимодействие с голограммами через кнопки и меню элементов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="8a58d-110">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="8a58d-111">Добавление текстовых элементов</span><span class="sxs-lookup"><span data-stu-id="8a58d-111">Learn how to add text elements</span></span>
* <span data-ttu-id="8a58d-112">Динамическое создание подсказок для объектов</span><span class="sxs-lookup"><span data-stu-id="8a58d-112">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="8a58d-113">Создание статической панели кнопок</span><span class="sxs-lookup"><span data-stu-id="8a58d-113">Creating a static panel of buttons</span></span>

<span data-ttu-id="8a58d-114">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **RoverExplorer** и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в качестве дочернего объекта RoverExplorer, присвойте имя объекту **Buttons** (Кнопки) и настройте компонент **Transform** (Преобразование), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-114">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="8a58d-115">**Position** (Положение): X = –0,6, Y = 0,036, Z = –0,5</span><span class="sxs-lookup"><span data-stu-id="8a58d-115">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="8a58d-116">**Rotation** (Поворот): X = 90, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="8a58d-116">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="8a58d-117">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="8a58d-117">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity с выбранным и расположенным новым объектом Buttons](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="8a58d-119">В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, щелкните и перетащите заготовку **PressableRoundButton** к объекту **Buttons** (Кнопки), затем щелкните правой кнопкой мыши объект PressableRoundButton и выберите **Duplicate** (Дублировать), чтобы создать копию. Повторяйте эти действия до тех пор, пока у вас не будет три объекта PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="8a58d-119">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![Unity с новыми заготовками PressableRoundButton](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="8a58d-121">В окне Hierarchy (Иерархия) выберите объект **Buttons** (Кнопки), затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **GridObjectCollection** и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-121">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="8a58d-122">**Sort Type** (Тип сортировки): Child Order (В порядке дочерних объектов)</span><span class="sxs-lookup"><span data-stu-id="8a58d-122">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="8a58d-123">**Layout** (Макет): По горизонтали</span><span class="sxs-lookup"><span data-stu-id="8a58d-123">**Layout**: Horizontal</span></span>
* <span data-ttu-id="8a58d-124">**Cell Width** (Ширина ячейки): 0,2</span><span class="sxs-lookup"><span data-stu-id="8a58d-124">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="8a58d-125">**Anchor** (Привязка): Посередине слева</span><span class="sxs-lookup"><span data-stu-id="8a58d-125">**Anchor**: Middle Left</span></span>

<span data-ttu-id="8a58d-126">Затем нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы обновить положение дочерних объектов объекта Buttons (Кнопки):</span><span class="sxs-lookup"><span data-stu-id="8a58d-126">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![Объект Buttons в Unity с добавленным, настроенным и примененным компонентом GridObjectCollection](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="8a58d-128">В окне Hierarchy (Иерархия) присвойте имя кнопкам **Hints** (Подсказки), **Explode** (Развернуть) и **Reset** (Сброс).</span><span class="sxs-lookup"><span data-stu-id="8a58d-128">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="8a58d-129">Для каждой кнопки выберите дочерний объект **SeeItSayItLabel** > **TextMeshPro**, а затем в окне Inspector (Инспектор) измените текст соответствующего компонента **TextMeshPro - Text** (TextMeshPro — текст), чтобы он соответствовал именам кнопок:</span><span class="sxs-lookup"><span data-stu-id="8a58d-129">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![Unity с настроенными текстовыми подписями кнопок](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="8a58d-131">После этого сверните дочерние объекты объекта Buttons (Кнопки).</span><span class="sxs-lookup"><span data-stu-id="8a58d-131">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="8a58d-132">В окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Подсказки), затем в окне Inspector (Инспектор) настройте событие **Interactable.OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8a58d-132">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8a58d-133">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-133">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8a58d-134">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **PlacementHintsController** > **TogglePlacementHints ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="8a58d-134">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для объекта кнопки Hints](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="8a58d-136">Компонент Interactable — это общий контейнер, который позволяет сделать любой объект интерактивным с возможностью реагирования на ввод.</span><span class="sxs-lookup"><span data-stu-id="8a58d-136">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="8a58d-137">Компонент Interactable выступает в качестве приемника всех типов ввода, в том числе прикосновений, движений руками, речи и т. д., а также передает такие взаимодействия в события и ответы визуальных тем.</span><span class="sxs-lookup"><span data-stu-id="8a58d-137">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="8a58d-138">Чтобы узнать, как настроить его для разных типов ввода и изменить визуальную тему, см. руководство по [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="8a58d-138">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="8a58d-139">В окне Hierarchy (Иерархия) выберите объект кнопки **Explode** (Развернуть), затем в окне Inspector (Инспектор) настройте событие **Interactable.OnClick ()** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8a58d-139">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8a58d-140">В поле **None (Object)** (Отсутствует (объект)) укажите объект **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-140">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8a58d-141">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ExplodedViewController** > **ToggleExplodedView ()** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="8a58d-141">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity с настроенным событием OnClick для объекта кнопки Explode](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="8a58d-143">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим. Затем нажмите и удерживайте клавишу пробела, чтобы активировать руку, и с помощью мыши нажмите кнопку **Hints** (Подсказки), чтобы переключить видимость объектов с подсказками о размещении:</span><span class="sxs-lookup"><span data-stu-id="8a58d-143">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![Разделенное представление Unity в режиме воспроизведения с нажатой кнопкой Hints](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="8a58d-145">и кнопку **Explode** (Развернуть) для включения и выключения развернутого представления:</span><span class="sxs-lookup"><span data-stu-id="8a58d-145">and the **Explode** button to toggle the exploded view on and off:</span></span>

![Разделенное представление Unity в режиме воспроизведения с нажатой кнопкой Explode](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="8a58d-147">Создание динамического меню, которое следует за пользователем</span><span class="sxs-lookup"><span data-stu-id="8a58d-147">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="8a58d-148">В окне Project (Проект) перейдите к папке **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus**, перетащите заготовку **NearMenu4x1** в окно Hierarchy (Иерархия), установите для параметра преобразования **Position** (Позиция) значения X = 0, Y = -0,4, Z = 0 и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8a58d-148">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="8a58d-149">Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).</span><span class="sxs-lookup"><span data-stu-id="8a58d-149">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="8a58d-150">Установите флажок рядом с компонентом Solver **RadialView**, чтобы он был включен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8a58d-150">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![Unity с выбранной добавленной заготовкой NearMenu](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="8a58d-152">В окне Hierarchy (Иерархия) переименуйте объект в **Menu** (Меню), затем разверните его дочерний объект **ButtonCollection**, чтобы открыть четыре кнопки:</span><span class="sxs-lookup"><span data-stu-id="8a58d-152">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Unity с выбранным объектом Menu и развернутым объектом ButtonCollection](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="8a58d-154">Переименуйте первую кнопку на **Indicator** (Индикатор), затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-154">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="8a58d-155">Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.</span><span class="sxs-lookup"><span data-stu-id="8a58d-155">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="8a58d-156">В поле **None (Object)** (Отсутствует (Объект)) укажите объект **Indicator** (Индикатор).</span><span class="sxs-lookup"><span data-stu-id="8a58d-156">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8a58d-157">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **GameObject** > **SetActive (bool)** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="8a58d-157">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="8a58d-158">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-158">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="8a58d-159">Измените параметр **Icon** (Значок) на значок поиска.</span><span class="sxs-lookup"><span data-stu-id="8a58d-159">Change the **Icon** to the 'search' icon</span></span>

![Unity с объектом кнопки Indicator с настроенным скриптом Button Config Helper](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="8a58d-161">В окне иерархии выберите объект **Indicator** (Индикатор), а затем в окне инспектора сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="8a58d-161">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="8a58d-162">Снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8a58d-162">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="8a58d-163">Добавьте компонент **Directional Indicator Controller (Script)** (Контроллер индикатора направления (скрипт)) с помощью кнопки **Add Component** (Добавить компонент).</span><span class="sxs-lookup"><span data-stu-id="8a58d-163">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Unity с выбранным и отключенным объектом Indicator и добавленным компонентом DirectionalIndicatorController](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="8a58d-165">Теперь после запуска приложения объект Indicator (Индикатор) будет по умолчанию отключен (его можно включить с помощью кнопки Indicator (Индикатор)).</span><span class="sxs-lookup"><span data-stu-id="8a58d-165">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="8a58d-166">Переименуйте вторую кнопку на **TapToPlace**, затем в окне Inspector (Инспектор) настройте компонент **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-166">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="8a58d-167">Измените значение для параметра **Main Label Text** (Текст основной метки), чтобы он соответствовал названию кнопки.</span><span class="sxs-lookup"><span data-stu-id="8a58d-167">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="8a58d-168">В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-168">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8a58d-169">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="8a58d-169">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8a58d-170">Убедитесь, что флажок аргумента **установлен**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-170">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="8a58d-171">Измените параметр **Icon** (Значок) на значок руки с лучом.</span><span class="sxs-lookup"><span data-stu-id="8a58d-171">Change the **Icon** to the 'hand with ray' icon</span></span>

![Unity с объектом кнопки TapToPlace с настроенным скриптом Button Config Helper](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="8a58d-173">В окне Hierarchy (Иерархия) выберите объект **RoverAssembly**, затем в окне Inspector (Инспектор) настройте компонент **Tap To Place (Script)** (Размещение касанием — скрипт), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-173">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="8a58d-174">Снимите флажок рядом с его именем, чтобы сделать его неактивным по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8a58d-174">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="8a58d-175">В разделе события **On Placing Stopped ()** щелкните значок **+** , чтобы добавить новое событие:</span><span class="sxs-lookup"><span data-stu-id="8a58d-175">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="8a58d-176">В поле **None (Object)** (Отсутствует (Объект)) укажите объект RoverExplorer > **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-176">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8a58d-177">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="8a58d-177">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8a58d-178">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-178">Verify that the argument checkbox is **unchecked**</span></span>

![Unity с перенастроенным компонентом TapToPlace](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="8a58d-180">Теперь при запуске приложения функция Tap to Place (Размещение касанием) будет отключена по умолчанию (ее можно включить с помощью кнопки Tap to Place (Размещение касанием)).</span><span class="sxs-lookup"><span data-stu-id="8a58d-180">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="8a58d-181">Кроме того, когда операция размещения нажатием завершена, функция отключится автоматически.</span><span class="sxs-lookup"><span data-stu-id="8a58d-181">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="8a58d-182">Добавление текста в сцену</span><span class="sxs-lookup"><span data-stu-id="8a58d-182">Adding text to the scene</span></span>

<span data-ttu-id="8a58d-183">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **Table** (Таблица) и выберите **3D Object** (Трехмерный объект) > **Text - TextMeshPro** (Текст — TextMeshPro), чтобы добавить текстовый объект в качестве дочернего для объекта Table (Таблица), а затем в окне Inspector (Инспектор) настройте компонент **Rect Transform** (Прямоугольное преобразование), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-183">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="8a58d-184">Укажите для параметра **Pos Y** (Позиция Y) значение 1.</span><span class="sxs-lookup"><span data-stu-id="8a58d-184">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="8a58d-185">Укажите для параметра **Width** (Ширина) значение 1.</span><span class="sxs-lookup"><span data-stu-id="8a58d-185">Change **Width** to 1</span></span>
* <span data-ttu-id="8a58d-186">Укажите для параметра **Height** (Высота) значение 1.</span><span class="sxs-lookup"><span data-stu-id="8a58d-186">Change **Height** to 1</span></span>
* <span data-ttu-id="8a58d-187">Укажите для параметра **Rotation X** (Поворот X) значение 90.</span><span class="sxs-lookup"><span data-stu-id="8a58d-187">Change **Rotation X** to 90</span></span>

![Unity с выбранным созданным объектом TextMeshPro](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="8a58d-189">Затем настройте компонент **TextMeshPro - Text** (TextMeshPro — текст), как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-189">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="8a58d-190">Укажите для параметра **Text** (Текст) значение Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="8a58d-190">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="8a58d-191">Укажите для параметра **Font Style** (Стиль шрифта) значение "Полужирный".</span><span class="sxs-lookup"><span data-stu-id="8a58d-191">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="8a58d-192">Укажите для параметра **Font Size** (Размер шрифта) значение 1.</span><span class="sxs-lookup"><span data-stu-id="8a58d-192">Change **Font Size** to 1</span></span>
* <span data-ttu-id="8a58d-193">Укажите для параметра Extra Settings (Дополнительные параметры) > **Margins** (Поля) значение 0,03.</span><span class="sxs-lookup"><span data-stu-id="8a58d-193">Change Extra Settings > **Margins** to 0.03</span></span>

![Unity с настроенным компонентом TextMeshPro](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="8a58d-195">Добавление подсказок</span><span class="sxs-lookup"><span data-stu-id="8a58d-195">Adding tooltips</span></span>

<span data-ttu-id="8a58d-196">В окне Project (Проект) перейдите в папку **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip**, чтобы найти заготовки подсказок:</span><span class="sxs-lookup"><span data-stu-id="8a58d-196">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Окно проекта Unity с выбранной папкой ToolTips](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="8a58d-198">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **RoverParts** и выберите все его дочерние объекты лунохода, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить **ToolTipSpawner** ко всем выбранным объектам и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-198">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="8a58d-199">Убедитесь, что установлен флажок **Focus Enabled** (Фокус включен), чтобы пользователь смог посмотреть на часть, где должна появиться подсказка.</span><span class="sxs-lookup"><span data-stu-id="8a58d-199">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="8a58d-200">Укажите заготовку **Simple Line ToolTip** (Подсказка в отдельной строке) из окна Project (Проект) в поле **Tool Tip Prefab** (Заготовка подсказки).</span><span class="sxs-lookup"><span data-stu-id="8a58d-200">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="8a58d-201">Измените значение параметра ToolTip Override Settings (Параметры переопределения подсказок) > **Settings Mode** (Режим параметров) на значение **Override** (Переопределение).</span><span class="sxs-lookup"><span data-stu-id="8a58d-201">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="8a58d-202">Измените значение параметра ToolTip Override Settings > **Manual Pivot Location Position Y** (Параметры переопределения подсказок > Позиция по оси Y расположения ручного поворота) на **1,5**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-202">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![Unity со всеми выбранными объектами частей лунохода, а также добавленным и настроенным компонентом ToolTipSpawner](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="8a58d-204">В окне Hierarchy (Иерархия) выберите первую часть лунохода (RoverParts > **Camera_Part**) и настройте компонент **ToolTipSpawner**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-204">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="8a58d-205">Измените параметр **Tool Tip Text** (Текст подсказки), чтобы в нем было указано имя части (например, **Camera** (Камера)).</span><span class="sxs-lookup"><span data-stu-id="8a58d-205">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![Unity с заданным в поле текста подсказки значением Camera (Камера)](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="8a58d-207">**Повторите** этот шаг для каждого из объектов частей лунохода, чтобы настроить компонент **ToolTipSpawner**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a58d-207">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="8a58d-208">Для объекта **Generator_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Generator**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-208">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="8a58d-209">Для объекта **Lights_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Lights**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-209">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="8a58d-210">Для объекта **UHFAntenna_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на поле **UHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-210">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="8a58d-211">Для объекта **Spectrometer_Part** измените значение параметра **Tool Tip Text** (Текст подсказки) на **Spectrometer**.</span><span class="sxs-lookup"><span data-stu-id="8a58d-211">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="8a58d-212">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, а затем нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши, пока не будет нажата одна из частей и не отобразится подсказка для этой части:</span><span class="sxs-lookup"><span data-stu-id="8a58d-212">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![Разделенное представление Unity в режиме воспроизведения с подсказкой, срабатывающей при попадании взгляда](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="8a58d-214">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="8a58d-214">Congratulations</span></span>

<span data-ttu-id="8a58d-215">Из этого учебника вы узнали, как создать простой пользовательский интерфейс с помощью предоставляемых кнопок MRTK и заготовок меню вместе с компонентом Unity TextMeshPro, а также как настроить кнопки для запуска событий при их нажатии.</span><span class="sxs-lookup"><span data-stu-id="8a58d-215">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="8a58d-216">Вы также узнали, как добавлять динамические элементы интерфейса подсказки, чтобы предоставить пользователю дополнительную информацию.</span><span class="sxs-lookup"><span data-stu-id="8a58d-216">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="8a58d-217">Следующее руководство: 7. Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="8a58d-217">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)