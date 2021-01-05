---
title: Активный объект
description: Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире. В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, подсказки, Пользовательский интерфейс, UX, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, аудио
ms.openlocfilehash: fb7004c22602683e4edb1e38784cac5c0b7479c4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847861"
---
# <a name="interactable-object"></a><span data-ttu-id="c01a1-105">Активный объект</span><span class="sxs-lookup"><span data-stu-id="c01a1-105">Interactable object</span></span>

![Объекты интерактибле](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="c01a1-107">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="c01a1-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="c01a1-108">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="c01a1-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="c01a1-109">Любой может быть **взаимодействующим объектом** , запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="c01a1-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="c01a1-110">Взаимодействующий объект может быть любым объектом из чашк кофе в таблице на всплывающую подсказку в мидаир.</span><span class="sxs-lookup"><span data-stu-id="c01a1-110">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="c01a1-111">Мы по-прежнему используем традиционные кнопки в определенных ситуациях, например в пользовательском интерфейсе диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="c01a1-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="c01a1-112">Визуальное представление кнопки зависит от контекста.</span><span class="sxs-lookup"><span data-stu-id="c01a1-112">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="c01a1-113">Важные свойства взаимодействующего объекта</span><span class="sxs-lookup"><span data-stu-id="c01a1-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="c01a1-114">Визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="c01a1-114">Visual cues</span></span>

<span data-ttu-id="c01a1-115">Визуальные подсказки являются подсказками датчиков, которые получаются глазом и обрабатываются визуальной системой во время визуального восприятия.</span><span class="sxs-lookup"><span data-stu-id="c01a1-115">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="c01a1-116">Так как визуальная система находится во многих виды цветов, особенно для людей, визуальные подсказки представляют собой большой источник информации о том, как воспринимается мир.</span><span class="sxs-lookup"><span data-stu-id="c01a1-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="c01a1-117">Поскольку holographic объектов смешиваются с реальной средой в смешанной реальности, может быть трудно понять, с какими объектами можно взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="c01a1-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="c01a1-118">Для любых взаимодействующих объектов важно предоставить дифференцированные визуальные подсказки для каждого входного состояния.</span><span class="sxs-lookup"><span data-stu-id="c01a1-118">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="c01a1-119">Это помогает пользователю понять, какая часть вашего интерфейса является взаимодействующей, и делает пользователя уверенным, используя согласованный метод взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c01a1-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="c01a1-120">Дальнее взаимодействие</span><span class="sxs-lookup"><span data-stu-id="c01a1-120">Far interactions</span></span>

<span data-ttu-id="c01a1-121">Для любых объектов, с которыми пользователь может взаимодействовать с помощью элемента управления "взгляд, рука и луч контроллера движения", рекомендуется использовать разные визуальные подсказки для этих трех входных состояний:</span><span class="sxs-lookup"><span data-stu-id="c01a1-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c01a1-122">![интерактиблеобжект — состояния — по умолчанию](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="c01a1-123">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="c01a1-124">Состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c01a1-124">Default idle state of the object.</span></span>
    <span data-ttu-id="c01a1-125">Курсор не находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="c01a1-125">The cursor isn't on the object.</span></span> <span data-ttu-id="c01a1-126">Рука не обнаружена.</span><span class="sxs-lookup"><span data-stu-id="c01a1-126">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c01a1-127">![интерактиблеобжект — целевое состояние](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="c01a1-128">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="c01a1-129">Когда объект ориентирован на курсор «взгляд», указатель мыши на палец или контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="c01a1-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="c01a1-130">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="c01a1-130">The cursor is on the object.</span></span> <span data-ttu-id="c01a1-131">Обнаружена, готова.</span><span class="sxs-lookup"><span data-stu-id="c01a1-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c01a1-132">![интерактиблеобжект-с нажатием состояния](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="c01a1-133">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="c01a1-133">**Pressed state**</span></span><br>
        <span data-ttu-id="c01a1-134">Когда объект нажимается с помощью жеста касания, нажмите кнопку "выбрать" для сенсорного экрана.</span><span class="sxs-lookup"><span data-stu-id="c01a1-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="c01a1-135">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="c01a1-135">The cursor is on the object.</span></span> <span data-ttu-id="c01a1-136">Обнаружена рука, касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="c01a1-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="c01a1-137">Вы можете использовать такие методы, как выделение или масштабирование, чтобы обеспечить визуальные подсказки для состояния ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="c01a1-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="c01a1-138">В смешанной реальности можно найти примеры визуализации различных состояний ввода в меню "Пуск" и с кнопками панели приложений.</span><span class="sxs-lookup"><span data-stu-id="c01a1-138">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="c01a1-139">Вот как эти состояния выглядят на **кнопке holographic**:</span><span class="sxs-lookup"><span data-stu-id="c01a1-139">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c01a1-140">![интерактиблеобжект — состояния — по умолчанию](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="c01a1-141">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c01a1-142">![интерактиблеобжект — целевое состояние](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="c01a1-143">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c01a1-144">![интерактиблеобжект-с нажатием состояния](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="c01a1-145">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="c01a1-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="c01a1-146">Близкое взаимодействие (Direct)</span><span class="sxs-lookup"><span data-stu-id="c01a1-146">Near interactions (direct)</span></span> 

<span data-ttu-id="c01a1-147">HoloLens 2 поддерживает вводные данные отслеживания, которые позволяют взаимодействовать с объектами.</span><span class="sxs-lookup"><span data-stu-id="c01a1-147">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="c01a1-148">Без хаптик отзывов и более глубокого восприятия может быть трудно понять, насколько далеко от него покидает объект или вы намерены его касаться.</span><span class="sxs-lookup"><span data-stu-id="c01a1-148">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="c01a1-149">Важно обеспечить достаточное количество визуальных подсказок для передачи состояния объекта, в частности состояние ваших рук на основе этого объекта.</span><span class="sxs-lookup"><span data-stu-id="c01a1-149">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="c01a1-150">Используйте визуальную обратную связь для передачи следующих состояний:</span><span class="sxs-lookup"><span data-stu-id="c01a1-150">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="c01a1-151">**По умолчанию (наблюдение)**: состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c01a1-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="c01a1-152">**Наведение указателя мыши**: когда руку приближается к голограмме, измените визуальные элементы так, чтобы они могли взаимодействовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="c01a1-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="c01a1-153">**Расстояние и точка взаимодействия**: как рука приближается к голограмме, вы отдаете отзыв о проектировании, чтобы сообщить о предполагаемой точке взаимодействия и насколько далеко от объекта.</span><span class="sxs-lookup"><span data-stu-id="c01a1-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="c01a1-154">**Начало контакта**: измените визуальные элементы (светло, Color), чтобы сообщить о том, что произошло касание.</span><span class="sxs-lookup"><span data-stu-id="c01a1-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="c01a1-155">Повышено **: изменение** визуальных элементов (светлое, цветное) при проходе на объект</span><span class="sxs-lookup"><span data-stu-id="c01a1-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="c01a1-156">**Окончание связи**: изменение визуальных элементов (светлое, цветное) при завершении сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="c01a1-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="c01a1-157">![Наведение (далеко)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="c01a1-158">**Наведение (далеко)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="c01a1-159">Выделение на основе сходства руки.</span><span class="sxs-lookup"><span data-stu-id="c01a1-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c01a1-160">![Наведение указателя мыши (вблизи)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="c01a1-161">**Наведение указателя мыши (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="c01a1-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="c01a1-162">Выделяйте изменения размера в зависимости от расстояния от руки.</span><span class="sxs-lookup"><span data-stu-id="c01a1-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="c01a1-163">![Сенсорный ввод/нажатие](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="c01a1-164">**Сенсорный ввод/нажатие**</span><span class="sxs-lookup"><span data-stu-id="c01a1-164">**Touch / press**</span></span><br>
        <span data-ttu-id="c01a1-165">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="c01a1-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c01a1-166">![Осознавать](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="c01a1-167">**Осознавать**</span><span class="sxs-lookup"><span data-stu-id="c01a1-167">**Grasp**</span></span><br>
        <span data-ttu-id="c01a1-168">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="c01a1-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="c01a1-169">[Кнопка в HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) представляет собой пример визуализации различных состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c01a1-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c01a1-170">![по умолчанию](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="c01a1-171">**Default**</span><span class="sxs-lookup"><span data-stu-id="c01a1-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c01a1-172">![Наведение](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="c01a1-173">**Наведение**</span><span class="sxs-lookup"><span data-stu-id="c01a1-173">**Hover**</span></span><br>
        <span data-ttu-id="c01a1-174">Показать эффекты освещения на основе близости.</span><span class="sxs-lookup"><span data-stu-id="c01a1-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="c01a1-175">![Сенсорный ввод](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="c01a1-176">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="c01a1-176">**Touch**</span></span><br>
        <span data-ttu-id="c01a1-177">Отображать эффекты Ripple.</span><span class="sxs-lookup"><span data-stu-id="c01a1-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c01a1-178">![Сочетание клавиш](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="c01a1-179">**Сочетание клавиш**</span><span class="sxs-lookup"><span data-stu-id="c01a1-179">**Press**</span></span><br>
        <span data-ttu-id="c01a1-180">Переместите переднюю форму.</span><span class="sxs-lookup"><span data-stu-id="c01a1-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="c01a1-181">Визуальная подсказка кольца в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c01a1-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="c01a1-182">В HoloLens 2 есть еще одна визуальная подсказка, которая помогает восприятие пользователя.</span><span class="sxs-lookup"><span data-stu-id="c01a1-182">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="c01a1-183">Кольцо рядом с ним отображается и масштабируется по мере того, как прокрутка будет ближе к объекту.</span><span class="sxs-lookup"><span data-stu-id="c01a1-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="c01a1-184">В конечном итоге, если достигнуто нажатое состояние, кольцо будет находиться в точке.</span><span class="sxs-lookup"><span data-stu-id="c01a1-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="c01a1-185">Этот визуальный подход позволяет пользователю понять, насколько далеко они от объекта.</span><span class="sxs-lookup"><span data-stu-id="c01a1-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="c01a1-186">*Цикл видео. пример визуальной обратной связи на основе сходства с ограничивающим прямоугольником*</span><span class="sxs-lookup"><span data-stu-id="c01a1-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="c01a1-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="c01a1-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="c01a1-188">![Визуальный отзыв о близком к рукой](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="c01a1-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="c01a1-189">Звуковые подсказки</span><span class="sxs-lookup"><span data-stu-id="c01a1-189">Audio cues</span></span>

<span data-ttu-id="c01a1-190">При прямом взаимодействии руки правильная обратная связь может значительно улучшить взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="c01a1-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="c01a1-191">Используйте отзыв о звуке, чтобы сообщить следующие подсказки:</span><span class="sxs-lookup"><span data-stu-id="c01a1-191">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="c01a1-192">**Начало контакта**: воспроизведение звука при начале сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="c01a1-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="c01a1-193">**Окончание контакта**: воспроизведение звука в сенсорном конце</span><span class="sxs-lookup"><span data-stu-id="c01a1-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="c01a1-194">**Начало захвата**: воспроизведение звука при начале</span><span class="sxs-lookup"><span data-stu-id="c01a1-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="c01a1-195">**Конец захвата**: воспроизведение звука при завершении захвата</span><span class="sxs-lookup"><span data-stu-id="c01a1-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="c01a1-196">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="c01a1-196">Voice commanding</span></span><br>
        <span data-ttu-id="c01a1-197">Для любых взаимодействующих объектов важно поддерживать альтернативные варианты взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c01a1-197">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="c01a1-198">По умолчанию рекомендуется поддерживать [командную команду Voice](../out-of-scope/voice-design.md) для всех объектов, которые являются взаимодействующими.</span><span class="sxs-lookup"><span data-stu-id="c01a1-198">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="c01a1-199">Чтобы улучшить возможность обнаружения, можно также предоставить подсказку во время наведения указателя мыши.</span><span class="sxs-lookup"><span data-stu-id="c01a1-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="c01a1-200">*Изображение: подсказка для команды Voice*</span><span class="sxs-lookup"><span data-stu-id="c01a1-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![голосовое командое](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="c01a1-202">Рекомендации относительно размеров</span><span class="sxs-lookup"><span data-stu-id="c01a1-202">Sizing recommendations</span></span> 

<span data-ttu-id="c01a1-203">Чтобы можно было легко затронуть все взаимодействующие объекты, рекомендуется убедиться, что они соответствуют минимальному размеру в зависимости от того, какое расстояние он помещает от пользователя.</span><span class="sxs-lookup"><span data-stu-id="c01a1-203">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="c01a1-204">Визуальный угол часто измеряется в градусах визуального дуги. Визуальный угол основан на расстоянии между глазами пользователя и объектом и остается постоянным, а физический размер целевого объекта может измениться по мере изменения расстояния от пользователя.</span><span class="sxs-lookup"><span data-stu-id="c01a1-204">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="c01a1-205">Чтобы определить необходимый физический размер объекта на основе расстояния от пользователя, попробуйте использовать визуальный калькулятор [угла, такой как.](https://elvers.us/perception/visualAngle/)</span><span class="sxs-lookup"><span data-stu-id="c01a1-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="c01a1-206">Ниже приведены рекомендации для минимального размера взаимодействующего содержимого.</span><span class="sxs-lookup"><span data-stu-id="c01a1-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="c01a1-207">Целевой размер для взаимодействия непосредственно с рукой</span><span class="sxs-lookup"><span data-stu-id="c01a1-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="c01a1-208">расстояние;</span><span class="sxs-lookup"><span data-stu-id="c01a1-208">Distance</span></span> | <span data-ttu-id="c01a1-209">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="c01a1-209">Viewing angle</span></span> | <span data-ttu-id="c01a1-210">Размер</span><span class="sxs-lookup"><span data-stu-id="c01a1-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="c01a1-211">45 cm</span><span class="sxs-lookup"><span data-stu-id="c01a1-211">45 cm</span></span>  | <span data-ttu-id="c01a1-212">не меньше 2 °</span><span class="sxs-lookup"><span data-stu-id="c01a1-212">no smaller than 2°</span></span> | <span data-ttu-id="c01a1-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="c01a1-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="c01a1-214">![Целевой размер для взаимодействия непосредственно с рукой](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="c01a1-215">*Целевой размер для взаимодействия непосредственно с рукой*</span><span class="sxs-lookup"><span data-stu-id="c01a1-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="c01a1-216">Целевой размер для кнопок</span><span class="sxs-lookup"><span data-stu-id="c01a1-216">Target size for buttons</span></span>

<span data-ttu-id="c01a1-217">При создании кнопок для прямого взаимодействия рекомендуется увеличить минимальный размер 3,2 x 3,2 cm, чтобы убедиться в наличии достаточного места для размещения значка и потенциального текста.</span><span class="sxs-lookup"><span data-stu-id="c01a1-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="c01a1-218">расстояние;</span><span class="sxs-lookup"><span data-stu-id="c01a1-218">Distance</span></span> | <span data-ttu-id="c01a1-219">Минимальный размер</span><span class="sxs-lookup"><span data-stu-id="c01a1-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="c01a1-220">45 cm</span><span class="sxs-lookup"><span data-stu-id="c01a1-220">45 cm</span></span>  | <span data-ttu-id="c01a1-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="c01a1-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="c01a1-222">![Целевой размер для кнопок](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="c01a1-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="c01a1-223">*Целевой размер для кнопок*</span><span class="sxs-lookup"><span data-stu-id="c01a1-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="c01a1-224">Целевой размер для взаимодействия "рука" или "взгляд"</span><span class="sxs-lookup"><span data-stu-id="c01a1-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="c01a1-225">расстояние;</span><span class="sxs-lookup"><span data-stu-id="c01a1-225">Distance</span></span> | <span data-ttu-id="c01a1-226">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="c01a1-226">Viewing angle</span></span> | <span data-ttu-id="c01a1-227">Размер</span><span class="sxs-lookup"><span data-stu-id="c01a1-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="c01a1-228">2 м</span><span class="sxs-lookup"><span data-stu-id="c01a1-228">2 m</span></span>  | <span data-ttu-id="c01a1-229">не меньше 1 °</span><span class="sxs-lookup"><span data-stu-id="c01a1-229">no smaller than 1°</span></span> | <span data-ttu-id="c01a1-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="c01a1-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="c01a1-231">![Целевой размер для взаимодействия "рука" или "взгляд"](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="c01a1-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="c01a1-232">*Целевой размер для взаимодействия "рука" или "взгляд"*</span><span class="sxs-lookup"><span data-stu-id="c01a1-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c01a1-233">Взаимодействующий объект в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="c01a1-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="c01a1-234">В **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно использовать [**взаимодействие**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) с скриптом, чтобы объекты отвечали на различные типы состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c01a1-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="c01a1-235">Он поддерживает различные типы тем, которые позволяют определять визуальные состояния, управляя свойствами объектов, такими как цвет, размер, материал и шейдер.</span><span class="sxs-lookup"><span data-stu-id="c01a1-235">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="c01a1-236">Элементом</span><span class="sxs-lookup"><span data-stu-id="c01a1-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="c01a1-237">Button</span><span class="sxs-lookup"><span data-stu-id="c01a1-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="c01a1-238">Сцены с примерами взаимодействия руки</span><span class="sxs-lookup"><span data-stu-id="c01a1-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="c01a1-239">Стандартный шейдер Микседреалититулкит предоставляет различные параметры, такие как **освещение** , позволяющее создавать визуальные и звуковые подсказки.</span><span class="sxs-lookup"><span data-stu-id="c01a1-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="c01a1-240">Стандартный шейдер МРТК</span><span class="sxs-lookup"><span data-stu-id="c01a1-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="c01a1-241">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c01a1-241">See also</span></span>

* [<span data-ttu-id="c01a1-242">Курсоры</span><span class="sxs-lookup"><span data-stu-id="c01a1-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c01a1-243">Телекинез</span><span class="sxs-lookup"><span data-stu-id="c01a1-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c01a1-244">Кнопка</span><span class="sxs-lookup"><span data-stu-id="c01a1-244">Button</span></span>](button.md)
* [<span data-ttu-id="c01a1-245">Активный объект</span><span class="sxs-lookup"><span data-stu-id="c01a1-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c01a1-246">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="c01a1-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c01a1-247">Оперирование</span><span class="sxs-lookup"><span data-stu-id="c01a1-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c01a1-248">Меню руки</span><span class="sxs-lookup"><span data-stu-id="c01a1-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c01a1-249">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="c01a1-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c01a1-250">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="c01a1-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c01a1-251">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="c01a1-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c01a1-252">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="c01a1-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c01a1-253">Подсказка</span><span class="sxs-lookup"><span data-stu-id="c01a1-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c01a1-254">Планшет</span><span class="sxs-lookup"><span data-stu-id="c01a1-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="c01a1-255">Ползунок</span><span class="sxs-lookup"><span data-stu-id="c01a1-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="c01a1-256">Шейдер</span><span class="sxs-lookup"><span data-stu-id="c01a1-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="c01a1-257">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="c01a1-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c01a1-258">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="c01a1-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c01a1-259">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="c01a1-259">Surface magnetism</span></span>](surface-magnetism.md)
