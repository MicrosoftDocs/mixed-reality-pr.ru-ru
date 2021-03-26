---
title: Создание динамического содержимого с помощью решателей
description: Из этого курса вы узнаете, как с помощью решателей Mixed Reality Toolkit (MRTK) создавать динамическое содержимое.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, решатели
ms.localizationpriority: high
ms.openlocfilehash: 11d25a13e679308ef7f0f4302dd7df29e413a435
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237067"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="07d6c-104">5. Создание динамического содержимого с помощью решателей</span><span class="sxs-lookup"><span data-stu-id="07d6c-104">5. Creating dynamic content using Solvers</span></span>

<span data-ttu-id="07d6c-105">В этом учебнике мы рассмотрим способы динамического помещения голограмм с помощью доступных инструментов размещения MRTK, известных как "решатели" и предназначенных для сложных сценариев пространственного размещения.</span><span class="sxs-lookup"><span data-stu-id="07d6c-105">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="07d6c-106">В MRTK решатели — это система сценариев и поведений, которые мы используем, чтобы разрешить объектам следовать за вами, пользователем или другими игровыми объектами на сцене.</span><span class="sxs-lookup"><span data-stu-id="07d6c-106">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="07d6c-107">С их помощью также можно выполнить прикрепление к определенной позиции, что делает приложение интуитивно понятным.</span><span class="sxs-lookup"><span data-stu-id="07d6c-107">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="07d6c-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="07d6c-108">Objectives</span></span>

* <span data-ttu-id="07d6c-109">Знакомство с решателями MRTK.</span><span class="sxs-lookup"><span data-stu-id="07d6c-109">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="07d6c-110">Узнайте, как использовать решатели для направления пользователя к объектам.</span><span class="sxs-lookup"><span data-stu-id="07d6c-110">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="07d6c-111">Узнайте, как использовать решатели для изменения расположения объектов.</span><span class="sxs-lookup"><span data-stu-id="07d6c-111">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="07d6c-112">Расположение решателей в MRTK</span><span class="sxs-lookup"><span data-stu-id="07d6c-112">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="07d6c-113">Решатели MRTK размещаются в папке пакета SDK MRTK.</span><span class="sxs-lookup"><span data-stu-id="07d6c-113">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="07d6c-114">Чтобы просмотреть доступные в проекте решатели, в окне Project (Проект) перейдите к папке **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **Utilities** > **Solvers**:</span><span class="sxs-lookup"><span data-stu-id="07d6c-114">To see the available Solvers in your project, in the Project window, navigate to **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![Окно проекта Unity с выбранной папкой решателей](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="07d6c-116">В этом учебнике мы рассмотрим реализацию решателя указателей направлений и решателя размещения касанием.</span><span class="sxs-lookup"><span data-stu-id="07d6c-116">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="07d6c-117">Чтобы получить дополнительную информацию о полном наборе решателей, доступных в MRTK, просмотрите раздел [Solvers](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) (Решатели) на [портале документации по MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span><span class="sxs-lookup"><span data-stu-id="07d6c-117">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

> [!NOTE]
> <span data-ttu-id="07d6c-118">Решатель указателей направлений не расположен в папках решателей, указанных выше. Он расположен в папках Packages > Mixed Reality Toolkit Foundation > SDK > Experimental > Features > Utilities, так как это экспериментальная функция.</span><span class="sxs-lookup"><span data-stu-id="07d6c-118">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Packages > Mixed Reality Toolkit Foundation > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="07d6c-119">Использование решателя указателей направлений для направления пользователя к объектам</span><span class="sxs-lookup"><span data-stu-id="07d6c-119">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="07d6c-120">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, щелкните и перетащите заготовку **Chevron** в окно иерархии и задайте для него преобразование **положения**, X = 0, Y = 0, Z = 2, чтобы разместить его рядом с объектом RoverExplorer:</span><span class="sxs-lookup"><span data-stu-id="07d6c-120">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![Unity с выбранной созданной заготовкой Chevron](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="07d6c-122">Если вы обнаружите, что камера или другие значки в сцене скрывают объекты или отвлекают от них внимание, их можно скрыть, <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведя манипуляторы</a> в отключенное положение, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="07d6c-122">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="07d6c-123">Дополнительные сведения о меню Gizmos (Манипуляторы) и его применении для оптимизации представления сцены вы можете найти в <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">этом разделе</a> документации.</span><span class="sxs-lookup"><span data-stu-id="07d6c-123">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="07d6c-124">Переименуйте вновь добавленный **индикатор** объекта шеврона, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить **DirectionalIndicator**.</span><span class="sxs-lookup"><span data-stu-id="07d6c-124">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator**:</span></span>

![Unity с добавленным компонентом решателя DirectionalIndicator](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="07d6c-126">При добавлении решателя (в нашем примере — DirectionalIndicator) автоматически добавляется еще компонент SolverHandler, который является обязательным для решателя.</span><span class="sxs-lookup"><span data-stu-id="07d6c-126">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="07d6c-127">Контроллер индикатора направления (скрипт) не является частью МРТК, но включен в учебные материалы.</span><span class="sxs-lookup"><span data-stu-id="07d6c-127">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="07d6c-128">Настройте компоненты DirectionalIndicator и SolverHandler следующим образом:</span><span class="sxs-lookup"><span data-stu-id="07d6c-128">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="07d6c-129">Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).</span><span class="sxs-lookup"><span data-stu-id="07d6c-129">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="07d6c-130">Назначьте параметру **DirectionalIndicator** компонента **Directional Target** (Целевое направление) значение **RoverExplorer**, перетащив его из окна иерархии в поле **None (Transform)** (Нет (преобразование)).</span><span class="sxs-lookup"><span data-stu-id="07d6c-130">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="07d6c-131">Измените значение параметра **View Offset** (Смещение вида) на 0,2.</span><span class="sxs-lookup"><span data-stu-id="07d6c-131">Change the **View Offset** to 0.2</span></span>

![Unity с настроенным компонентом решателя DirectionalIndicator](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="07d6c-133">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, затем нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши влево или вправо, чтобы повернуть направление взгляда и проверить следующее поведение.</span><span class="sxs-lookup"><span data-stu-id="07d6c-133">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="07d6c-134">Когда вы выйдете из объекта RoverExplorer, появится объект Indicator и будет указывать на объект RoverExplorer.</span><span class="sxs-lookup"><span data-stu-id="07d6c-134">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![Разделенное представление Unity в режиме воспроизведения с используемым решателем DirectionalIndicator](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="07d6c-136">Если вы не видите в окне Scene (Сцена) луч направления камеры, проверьте, включено ли меню Gizmos (Манипуляторы), как показано на изображении выше.</span><span class="sxs-lookup"><span data-stu-id="07d6c-136">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="07d6c-137">Сведения о том, как можно использовать встроенный имитатор ввода, см. в руководстве [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенному на [портале документации MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span><span class="sxs-lookup"><span data-stu-id="07d6c-137">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

> [!TIP]
> <span data-ttu-id="07d6c-138">Если на компьютере установлен микрофон, можно легко переключить активное состояние панели Diagnostics (Диагностика), отображаемой в окне Game (Игра), с помощью голосовой команды toggle diagnostics (переключить диагностику).</span><span class="sxs-lookup"><span data-stu-id="07d6c-138">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="07d6c-139">Кроме того, ее можно отключить в разделе MRTK Configuration Profile (Профиль конфигурации MRTK) > Diagnostics (Диагностика) > Enable Diagnostics System (Включить систему диагностики).</span><span class="sxs-lookup"><span data-stu-id="07d6c-139">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="07d6c-140">Обычно рекомендуется оставлять систему диагностики активной во время разработки.</span><span class="sxs-lookup"><span data-stu-id="07d6c-140">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="07d6c-141">Использование решателя размещения касанием, чтобы изменить расположение объектов</span><span class="sxs-lookup"><span data-stu-id="07d6c-141">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="07d6c-142">В окне Hierarchy (Иерархия) выберите объект RoverExplorer > **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Tap To Place (Script)** (Размещение касанием — скрипт), и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="07d6c-142">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="07d6c-143">Убедитесь, что для параметра **Tracked Target Type** (Тип отслеживаемой цели) компонента **SolverHandler** указано значение **Head** (Головной).</span><span class="sxs-lookup"><span data-stu-id="07d6c-143">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="07d6c-144">Снимите флажок **Use Default Surface Normal Offset** (Использовать стандартное смещение поверхности) и убедитесь, что для параметра **Surface Normal Offset** (Стандартное смещение нормали) установлено значение 0.</span><span class="sxs-lookup"><span data-stu-id="07d6c-144">Uncheck the **Use Default Surface Normal Offset** and ensure **Surface Normal Offset** is set to 0</span></span>
* <span data-ttu-id="07d6c-145">Установите флажок **Keep Orientation Vertical** (Оставить вертикальную ориентацию).</span><span class="sxs-lookup"><span data-stu-id="07d6c-145">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="07d6c-146">В выпадающем списке **Magnetic Surfaces** > **Element 0** (Магнитные поверхности > Элемент 0) снимите флажки всех параметров, кроме **Spatial Awareness** (Отслеживание пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="07d6c-146">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![Unity с добавленным и настроенным компонентом решателя TapToPlace](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="07d6c-148">Параметр Magnetic Surfaces (Магнитные поверхности) определяет, какие объекты может обнаружить компонент Tap To Place (Script) (Размещение касанием — скрипт) при размещении объекта.</span><span class="sxs-lookup"><span data-stu-id="07d6c-148">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="07d6c-149">Если изменить параметр на Spatial Awareness (Отслеживание пространственного положения), компонент Tap To Place (Script) (Размещение касанием — скрипт) сможет поместить луноход на объекты в слое Unity с именем Spatial Awareness (Отслеживание пространственного положения), который по умолчанию является сеткой отслеживания пространственного положения, созданной HoloLens.</span><span class="sxs-lookup"><span data-stu-id="07d6c-149">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="07d6c-150">Чтобы получить дополнительные сведения о слоях, воспользуйтесь <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">этим разделом</a> из документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="07d6c-150">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="07d6c-151">Если необходимо просмотреть сетку отслеживания пространственного положения при тестировании функций размещения касанием в HoloLens, можно временно установить для параметра отображения наблюдателя виртуальной сетки значение Visible (Видимый).</span><span class="sxs-lookup"><span data-stu-id="07d6c-151">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="07d6c-152">Чтобы вспомнить, как изменить параметр отображения, просмотрите инструкции в разделе [Изменение параметров отображения наблюдателя виртуальной сетки](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="07d6c-152">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="07d6c-153">Если в окне Hierarchy (Иерархия) все еще выбран объект RoverAssembly, в окне инспектора перейдите к событию **On Placing Started ()** и щелкните значок **+** , чтобы добавить новое событие.</span><span class="sxs-lookup"><span data-stu-id="07d6c-153">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![Unity с добавленным событием OnPlacingStarted для скрипта TapToPlace](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="07d6c-155">Настройте событие следующим образом:</span><span class="sxs-lookup"><span data-stu-id="07d6c-155">Configure the event as follows:</span></span>

* <span data-ttu-id="07d6c-156">Назначьте объект **RoverAssembly** в качестве прослушивателя для события On Placing Started (), перетащив его из окна Hierarchy (Иерархия) в поле **None (Object)** (Отсутствует (объект)).</span><span class="sxs-lookup"><span data-stu-id="07d6c-156">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="07d6c-157">В раскрывающемся списке **No Function** (Нет функции) выберите **TapToPlace** > **float SurfaceNormalOffset**, чтобы обновить значение свойства SurfaceNormalOffset при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="07d6c-157">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="07d6c-158">Убедитесь, что для аргумента задано значение **0**.</span><span class="sxs-lookup"><span data-stu-id="07d6c-158">Verify that the argument is set to **0**</span></span>

![Unity с настроенным событием OnPlacingStarted для скрипта TapToPlace](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="07d6c-160">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши пустое место и выберите **3D Object** (Трехмерный объект) > **Cube (Куб)** , чтобы создать временный объект, представляющий землю, и настройте компонент **Transform** (Преобразование) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="07d6c-160">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="07d6c-161">**Position** (Положение): X = 0, Y = –1,65, Z = 6.</span><span class="sxs-lookup"><span data-stu-id="07d6c-161">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="07d6c-162">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="07d6c-162">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="07d6c-163">**Scale** (Масштаб): X = 10, Y = 0,2, Z = 10.</span><span class="sxs-lookup"><span data-stu-id="07d6c-163">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![Unity с добавленным и расположенным объектом временного куба на поверхности](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="07d6c-165">Не отменяя выбор временного куба в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите в раскрывающимся списке **Layers** (Слои) значение, чтобы параметр слоя куба содержал только слой **Spatial Awareness** (Отслеживание пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="07d6c-165">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![Unity с объектом временного куба на поверхности, для слоя которого задано значение Spatial Awareness (Отслеживание пространственного положения)](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="07d6c-167">Нажмите кнопку Play (Воспроизведение), чтобы перейти в игровой режим, а затем нажмите и удерживайте правую кнопку мыши, пока взгляд не будет направлен на объект RoverAssembly:</span><span class="sxs-lookup"><span data-stu-id="07d6c-167">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![Разделенное представление Unity в режиме воспроизведения с объектом RoverAssembly, на который падает взгляд](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="07d6c-169">Нажмите левую кнопку мыши, чтобы запустить процесс размещения касанием:</span><span class="sxs-lookup"><span data-stu-id="07d6c-169">Click the left mouse button to start the tap-to-place process:</span></span>

![Разделенное представление Unity в режиме воспроизведения с начатым размещением TapToPlace](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="07d6c-171">Нажмите и удерживайте правую кнопку мыши, перемещая указатель мыши влево или вправо для поворота направления взгляда. Если размещение вас устраивает, нажмите левую кнопку мыши:</span><span class="sxs-lookup"><span data-stu-id="07d6c-171">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![Разделенное представление Unity в режиме воспроизведения с завершенным размещением TapToPlace](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="07d6c-173">После завершения тестирования функции в игровом режиме щелкните правой кнопкой мыши объект Cube (Куб) и нажмите кнопку **Delete** (Удалить), чтобы удалить его со сцены:</span><span class="sxs-lookup"><span data-stu-id="07d6c-173">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![Unity с выбранным объектом временного куба на поверхности с вариантом Delete (Удалить) в контекстном меню](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="07d6c-175">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="07d6c-175">Congratulations</span></span>

<span data-ttu-id="07d6c-176">Из этого учебника вы узнали, как использовать решатель указателя направления MRTK, чтобы элемент пользовательского интерфейса интуитивно направлял пользователя к объектам.</span><span class="sxs-lookup"><span data-stu-id="07d6c-176">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="07d6c-177">Вы также узнали, как использовать решатель размещения касанием, чтобы без проблем изменять расположение объектов.</span><span class="sxs-lookup"><span data-stu-id="07d6c-177">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="07d6c-178">Чтобы получить дополнительные сведения об этих и других решателях в составе MRTK, ознакомьтесь с руководством [Решатели](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) на [портале документации по MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span><span class="sxs-lookup"><span data-stu-id="07d6c-178">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="07d6c-179">Следующее руководство: 6. Создание пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="07d6c-179">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
