---
title: Жесты в Unity
description: Узнайте, как принять меры для вашего взгляда в Unity с помощью ввода жестов, используя XR и общие API кнопок и осей.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: жесты, Unity, Взгляните, ввод, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600643"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="7bcaa-104">Жесты в Unity</span><span class="sxs-lookup"><span data-stu-id="7bcaa-104">Gestures in Unity</span></span>

<span data-ttu-id="7bcaa-105">Существует два основных способа выполнения действий с вашим [взглядом в Unity](gaze-in-unity.md), [жестами](../../design/gaze-and-commit.md#composite-gestures) и [контроллерами движения](../../design/motion-controllers.md) в HoloLens и иммерсивное ХМД.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="7bcaa-106">Доступ к данным для обоих источников пространственных данных осуществляется через одни и те же API в Unity.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="7bcaa-107">Unity предоставляет два основных способа доступа к данным пространственного ввода для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="7bcaa-108">Общие *входные API-интерфейсы input. "input. Axis"* работают в нескольких пакетах SDK для Unity XR, а API *интерактионманажер/GestureRecognizer* , относящийся к Windows Mixed Reality, предоставляет полный набор пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="7bcaa-109">Интерфейсы API составных жестов высокого уровня (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="7bcaa-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="7bcaa-110">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7bcaa-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7bcaa-111">**Типы**: *GestureRecognizer*, *жестуресеттингс*, *интерактионсаурцекинд*</span><span class="sxs-lookup"><span data-stu-id="7bcaa-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="7bcaa-112">Приложение может также распознать составные жесты более высокого уровня для пространственных источников входных данных, а также жесты касания, удержания, манипуляции и перемещения.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="7bcaa-113">Эти составные жесты можно распознавать как в движении, [так и в](../../design/gaze-and-commit.md#composite-gestures) [контроллерах движения](../../design/motion-controllers.md) с помощью GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="7bcaa-114">Каждое событие жеста в GestureRecognizer предоставляет Саурцекинд для входных данных, а также целевой заголовочный элемент на момент события.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="7bcaa-115">Некоторые события предоставляют дополнительные сведения, относящиеся к контексту.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="7bcaa-116">Для записи жестов с помощью распознавателя жестов требуется всего несколько действий:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="7bcaa-117">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="7bcaa-118">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="7bcaa-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="7bcaa-119">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="7bcaa-120">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="7bcaa-121">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="7bcaa-122">Чтобы использовать *GestureRecognizer*, необходимо создать *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="7bcaa-123">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="7bcaa-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="7bcaa-124">Укажите жесты, которые вас интересуют, с помощью *сетрекогнизаблежестурес ()*:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="7bcaa-125">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="7bcaa-126">Подпишитесь на события для тех жестов, которые вас интересуют.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-126">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="7bcaa-127">Жесты навигации и манипуляции являются взаимоисключающими в экземпляре *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="7bcaa-128">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-128">Start capturing gestures</span></span>

<span data-ttu-id="7bcaa-129">По умолчанию *GestureRecognizer* не отслеживает входные данные до тех пор, пока не будет вызван *старткаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="7bcaa-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="7bcaa-130">Возможно, что событие жеста может быть создано после вызова *стопкаптурингжестурес ()* , если входные данные были выполнены до того, как был обработан *стопкаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="7bcaa-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="7bcaa-131">*GestureRecognizer* будет запоминать, была ли она включена или отключена во время предыдущего кадра, в котором он действительно выполнялся, и поэтому его можно легко запускать и прекращать, исходя из этого кадра.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="7bcaa-132">Завершение записи жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-132">Stop capturing gestures</span></span>

<span data-ttu-id="7bcaa-133">Чтобы отключить распознавание жестов, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="7bcaa-134">Удаление распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="7bcaa-135">Не забудьте отказаться от подписки на подписанные события перед уничтожением объекта *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="7bcaa-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="7bcaa-136">Подготовка модели контроллера движения к просмотру в Unity</span><span class="sxs-lookup"><span data-stu-id="7bcaa-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="7bcaa-137">![Модель контроллера движения и телеперенос](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7bcaa-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="7bcaa-138">*Модель контроллера движения и телеперенос*</span><span class="sxs-lookup"><span data-stu-id="7bcaa-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="7bcaa-139">Для подготовки к просмотру в приложении контроллеров движения, соответствующих физическим контроллерам, которые хранятся и обрабатываются при нажатии различных кнопок, можно использовать **prefab мотионконтроллер** в [наборе средств Mixed Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="7bcaa-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="7bcaa-140">Этот prefab динамически загружает правильную модель Глтф во время выполнения из установленного в системе драйвера контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="7bcaa-141">Важно динамически загружать эти модели, а не импортировать их вручную в редакторе, чтобы приложение показывало физически точную трехмерную модель для всех существующих и будущих контроллеров, которые могут иметь пользователи.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="7bcaa-142">Следуйте инструкциям по [Начало работы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) , чтобы скачать набор средств для смешанной реальности и добавить его в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="7bcaa-143">Если вы заменили камеру на *микседреалитикамерапарент* prefab в рамках начало работы действий, то можете продолжить!</span><span class="sxs-lookup"><span data-stu-id="7bcaa-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="7bcaa-144">Этот prefab включает визуализацию контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="7bcaa-145">В противном случае добавьте *Assets/холотулкит/input/Prefabs/мотионконтроллерс. prefab* в сцену из области проекта.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="7bcaa-146">Вам потребуется добавить prefab в качестве дочернего объекта для того, чтобы перемещать камеру, когда у пользователя есть телепередачи в пределах сцены, чтобы контроллеры поступали вместе с пользователем.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="7bcaa-147">Если ваше приложение не предусматривает телеперенос, просто добавьте prefab в корень сцены.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="7bcaa-148">Создание вызывающих объектов</span><span class="sxs-lookup"><span data-stu-id="7bcaa-148">Throwing objects</span></span>

<span data-ttu-id="7bcaa-149">Создание объектов в Virtual Reality сложнее, чем может показаться на первый взгляд.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="7bcaa-150">Как и в случае с наиболее частыми взаимодействиями, когда вызов в игре происходит непредвиденным образом, он немедленно становится очевидным и нарушается.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="7bcaa-151">Мы потратили некоторое время на обдумывание того, как представить физически правильное поведение при вызове и получили несколько рекомендаций по обновлению нашей платформы, которые мы бы хотели поделиться с вами.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="7bcaa-152">Вы можете найти пример того, как мы рекомендуем реализовать [это](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)создание.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="7bcaa-153">Этот пример соответствует следующим четырем рекомендациям:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="7bcaa-154">**Используйте *скорость* контроллера вместо расположения**.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="7bcaa-155">В ноябре-обновлении Windows мы предоставили изменение в поведении, когда в [позиционированном состоянии отслеживания "приближено](../../design/motion-controllers.md#controller-tracking-state)".</span><span class="sxs-lookup"><span data-stu-id="7bcaa-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="7bcaa-156">В этом состоянии информация о скорости контроллера будет по-прежнему отображаться до тех пор, пока мы считаем высокую точность, которая чаще всего превышает точность.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="7bcaa-157">**Внедрение *угловой скорости* контроллера**.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="7bcaa-158">Эта логика хранится в `throwing.cs` файле в `GetThrownObjectVelAngVel` статическом методе в связанном выше пакете.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="7bcaa-159">По мере того, как угловая скорость сохраняется, создаваемый объект должен поддерживать ту же угловую скорость, что и в момент создания: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7bcaa-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="7bcaa-160">Поскольку центр массы создаваемого объекта, скорее всего, не находится на происхождении захвата, он, вероятно, имеет разную скорость, чем контроллер в кадре ссылки пользователя.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="7bcaa-161">Часть скорости объекта, созданная таким образом, является мгновенно отношения скоростью центра массы создаваемого объекта по отношению к источнику контроллера.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="7bcaa-162">Отношения скорость — это перекрестное произведение угловой скорости контроллера с вектором, представляющим расстояние между источником контроллера и центром массы создаваемого объекта.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="7bcaa-163">Общая скорость создаваемого объекта — это сумма скорости контроллера и этой отношения скорости: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7bcaa-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="7bcaa-164">**Обратите особое внимание на *время* , когда мы применяем скорость**.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="7bcaa-165">При нажатии кнопки может пройти до 20 мс, чтобы это событие было переработано с помощью Bluetooth к операционной системе.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="7bcaa-166">Это означает, что если вы опрашиваете изменение состояния контроллера с нажатия на не нажимаете или наоборот, сведения об этом контроллере, которые вы получаете вместе с ним, будут действительно впереди этого изменения в состоянии.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="7bcaa-167">Кроме того, контроллер, представленный нашим API-интерфейсом опроса, передается в прогноз, чтобы отразить на момент отображения кадра, который может быть более 20 мс в будущем.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="7bcaa-168">Это хорошо подходит для *визуализации* удерживаемых объектов, но создает *задачу по времени для объекта* , так как вычисляется траекторию на момент, когда пользователь выпустил исключение.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="7bcaa-169">К счастью, при обновлении за Ноябрьское событие при отправке события Unity, такого как *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* , состояние включает данные предыстории с обратной стороны при нажатии или отпускании кнопки.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="7bcaa-170">Чтобы получить наиболее точную визуализацию контроллера и нацеливание контроллера во время возникновения исключения, необходимо правильно использовать опрос и события, если это уместно:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="7bcaa-171">Для **отрисовки** каждого кадра на контроллере приложение должно располагать *GameObject* контроллера на переphotonном контроллере в течение текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="7bcaa-172">Эти данные можно получить из API опроса Unity, например *[XR. Инпуттраккинг. Жетлокалпоситион](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или *[XR. Головк. Входные данные. Интерактионманажер. Жеткуррентреадинг](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="7bcaa-173">Для **нацеливания контроллера** на нажатие или выпуск ваше приложение должно райкаст и вычислять траекторий на основе данных о том, что такое событие выпусков.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="7bcaa-174">Эти данные можно получить из API-интерфейсов Unity, таких как *[интерактионманажер. интерактионсаурцепрессед](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="7bcaa-175">**Использование захвата**.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-175">**Use the grip pose**.</span></span> <span data-ttu-id="7bcaa-176">Угловая скорость и скорость отмечаются относительно захвата, а не указателя.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="7bcaa-177">Порождение продолжит совершенствоваться с будущими обновлениями Windows, и вы сможете найти дополнительные сведения здесь.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="7bcaa-178">Жесты и контроллеры движения в МРТК</span><span class="sxs-lookup"><span data-stu-id="7bcaa-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="7bcaa-179">Вы можете получить доступ к жестам и контроллеру движения из диспетчера ввода.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="7bcaa-180">Жест в МРТК</span><span class="sxs-lookup"><span data-stu-id="7bcaa-180">Gesture in MRTK</span></span>](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="7bcaa-181">Контроллер движения в МРТК</span><span class="sxs-lookup"><span data-stu-id="7bcaa-181">Motion Controller in MRTK</span></span>](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="7bcaa-182">Обучение по руководствам</span><span class="sxs-lookup"><span data-stu-id="7bcaa-182">Follow along with tutorials</span></span>

<span data-ttu-id="7bcaa-183">Пошаговые учебники с более подробными примерами настройки доступны в Academyе Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="7bcaa-184">211. Ввод в смешанной реальности: жест</span><span class="sxs-lookup"><span data-stu-id="7bcaa-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="7bcaa-185">213. Ввод в смешанной реальности: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="7bcaa-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="7bcaa-186">[![MR-вход 213 — контроллер движения](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="7bcaa-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="7bcaa-187">*MR-вход 213 — контроллер движения*</span><span class="sxs-lookup"><span data-stu-id="7bcaa-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7bcaa-188">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="7bcaa-188">Next Development Checkpoint</span></span>

<span data-ttu-id="7bcaa-189">Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core.</span><span class="sxs-lookup"><span data-stu-id="7bcaa-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7bcaa-190">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7bcaa-191">Отслеживание рук и взгляда</span><span class="sxs-lookup"><span data-stu-id="7bcaa-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="7bcaa-192">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="7bcaa-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="7bcaa-193">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="7bcaa-193">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="7bcaa-194">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="7bcaa-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bcaa-195">См. также статью</span><span class="sxs-lookup"><span data-stu-id="7bcaa-195">See also</span></span>

* [<span data-ttu-id="7bcaa-196">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="7bcaa-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7bcaa-197">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="7bcaa-197">Motion controllers</span></span>](../../design/motion-controllers.md)