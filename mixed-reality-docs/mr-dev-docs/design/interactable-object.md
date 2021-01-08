---
title: Активный объект
description: Узнайте, как запускать события, предоставлять визуальные подсказки и взаимодействовать с объектами в приложениях смешанной реальности.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, подсказки, Пользовательский интерфейс, UX, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, аудио
ms.openlocfilehash: d0dc8ce6425d597d04b47a6c8b08f72534488594
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007204"
---
# <a name="interactable-object"></a><span data-ttu-id="f9be4-104">Активный объект</span><span class="sxs-lookup"><span data-stu-id="f9be4-104">Interactable object</span></span>

![Объекты интерактибле](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="f9be4-106">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="f9be4-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="f9be4-107">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="f9be4-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="f9be4-108">Любой может быть **взаимодействующим объектом** , запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="f9be4-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="f9be4-109">Взаимодействующий объект может быть любым объектом из чашк кофе в таблице на всплывающую подсказку в мидаир.</span><span class="sxs-lookup"><span data-stu-id="f9be4-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="f9be4-110">Мы по-прежнему используем традиционные кнопки в определенных ситуациях, например в пользовательском интерфейсе диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="f9be4-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="f9be4-111">Визуальное представление кнопки зависит от контекста.</span><span class="sxs-lookup"><span data-stu-id="f9be4-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="f9be4-112">Важные свойства взаимодействующего объекта</span><span class="sxs-lookup"><span data-stu-id="f9be4-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="f9be4-113">Визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="f9be4-113">Visual cues</span></span>

<span data-ttu-id="f9be4-114">Визуальные подсказки являются подсказками датчиков, которые получаются глазом и обрабатываются визуальной системой во время визуального восприятия.</span><span class="sxs-lookup"><span data-stu-id="f9be4-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="f9be4-115">Так как визуальная система находится во многих виды цветов, особенно для людей, визуальные подсказки представляют собой большой источник информации о том, как воспринимается мир.</span><span class="sxs-lookup"><span data-stu-id="f9be4-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="f9be4-116">Поскольку holographic объектов смешиваются с реальной средой в смешанной реальности, может быть трудно понять, с какими объектами можно взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="f9be4-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="f9be4-117">Для любых взаимодействующих объектов важно предоставить дифференцированные визуальные подсказки для каждого входного состояния.</span><span class="sxs-lookup"><span data-stu-id="f9be4-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="f9be4-118">Это помогает пользователю понять, какая часть вашего интерфейса является взаимодействующей, и делает пользователя уверенным, используя согласованный метод взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f9be4-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="f9be4-119">Дальнее взаимодействие</span><span class="sxs-lookup"><span data-stu-id="f9be4-119">Far interactions</span></span>

<span data-ttu-id="f9be4-120">Для любых объектов, с которыми пользователь может взаимодействовать с помощью элемента управления "взгляд, рука и луч контроллера движения", рекомендуется использовать разные визуальные подсказки для этих трех входных состояний:</span><span class="sxs-lookup"><span data-stu-id="f9be4-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f9be4-121">![интерактиблеобжект — состояния — по умолчанию](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-121">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="f9be4-122">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="f9be4-123">Состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f9be4-123">Default idle state of the object.</span></span>
    <span data-ttu-id="f9be4-124">Курсор не находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f9be4-124">The cursor isn't on the object.</span></span> <span data-ttu-id="f9be4-125">Рука не обнаружена.</span><span class="sxs-lookup"><span data-stu-id="f9be4-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f9be4-126">![интерактиблеобжект — целевое состояние](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-126">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="f9be4-127">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="f9be4-128">Когда объект ориентирован на курсор «взгляд», указатель мыши на палец или контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="f9be4-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="f9be4-129">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f9be4-129">The cursor is on the object.</span></span> <span data-ttu-id="f9be4-130">Обнаружена, готова.</span><span class="sxs-lookup"><span data-stu-id="f9be4-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f9be4-131">![интерактиблеобжект-с нажатием состояния](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-131">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="f9be4-132">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="f9be4-132">**Pressed state**</span></span><br>
        <span data-ttu-id="f9be4-133">Когда объект нажимается с помощью жеста касания, нажмите кнопку "выбрать" для сенсорного экрана.</span><span class="sxs-lookup"><span data-stu-id="f9be4-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="f9be4-134">Курсор находится на объекте.</span><span class="sxs-lookup"><span data-stu-id="f9be4-134">The cursor is on the object.</span></span> <span data-ttu-id="f9be4-135">Обнаружена рука, касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="f9be4-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="f9be4-136">Вы можете использовать такие методы, как выделение или масштабирование, чтобы обеспечить визуальные подсказки для состояния ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="f9be4-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="f9be4-137">В смешанной реальности можно найти примеры визуализации различных состояний ввода в меню "Пуск" и с кнопками панели приложений.</span><span class="sxs-lookup"><span data-stu-id="f9be4-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="f9be4-138">Вот как эти состояния выглядят на **кнопке holographic**:</span><span class="sxs-lookup"><span data-stu-id="f9be4-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f9be4-139">![интерактиблеобжект — состояния — по умолчанию](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-139">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="f9be4-140">**Состояние по умолчанию (наблюдение)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f9be4-141">![интерактиблеобжект — целевое состояние](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-141">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="f9be4-142">**Целевое состояние (наведение указателя)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f9be4-143">![интерактиблеобжект-с нажатием состояния](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-143">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="f9be4-144">**Нажатое состояние**</span><span class="sxs-lookup"><span data-stu-id="f9be4-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="f9be4-145">Близкое взаимодействие (Direct)</span><span class="sxs-lookup"><span data-stu-id="f9be4-145">Near interactions (direct)</span></span> 

<span data-ttu-id="f9be4-146">HoloLens 2 поддерживает вводные данные отслеживания, которые позволяют взаимодействовать с объектами.</span><span class="sxs-lookup"><span data-stu-id="f9be4-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="f9be4-147">Без хаптик отзывов и более глубокого восприятия может быть трудно понять, насколько далеко от него покидает объект или вы намерены его касаться.</span><span class="sxs-lookup"><span data-stu-id="f9be4-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="f9be4-148">Важно обеспечить достаточное количество визуальных подсказок для передачи состояния объекта, в частности состояние ваших рук на основе этого объекта.</span><span class="sxs-lookup"><span data-stu-id="f9be4-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="f9be4-149">Используйте визуальную обратную связь для передачи следующих состояний:</span><span class="sxs-lookup"><span data-stu-id="f9be4-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="f9be4-150">**По умолчанию (наблюдение)**: состояние простоя объекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f9be4-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="f9be4-151">**Наведение указателя мыши**: когда руку приближается к голограмме, измените визуальные элементы так, чтобы они могли взаимодействовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="f9be4-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="f9be4-152">**Расстояние и точка взаимодействия**: как рука приближается к голограмме, вы отдаете отзыв о проектировании, чтобы сообщить о предполагаемой точке взаимодействия и насколько далеко от объекта.</span><span class="sxs-lookup"><span data-stu-id="f9be4-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="f9be4-153">**Начало контакта**: измените визуальные элементы (светло, Color), чтобы сообщить о том, что произошло касание.</span><span class="sxs-lookup"><span data-stu-id="f9be4-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="f9be4-154">Повышено **: изменение** визуальных элементов (светлое, цветное) при проходе на объект</span><span class="sxs-lookup"><span data-stu-id="f9be4-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="f9be4-155">**Окончание связи**: изменение визуальных элементов (светлое, цветное) при завершении сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="f9be4-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="f9be4-156">![Наведение (далеко)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="f9be4-157">**Наведение (далеко)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="f9be4-158">Выделение на основе сходства руки.</span><span class="sxs-lookup"><span data-stu-id="f9be4-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f9be4-159">![Наведение указателя мыши (вблизи)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="f9be4-160">**Наведение указателя мыши (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="f9be4-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="f9be4-161">Выделяйте изменения размера в зависимости от расстояния от руки.</span><span class="sxs-lookup"><span data-stu-id="f9be4-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="f9be4-162">![Сенсорный ввод/нажатие](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="f9be4-163">**Сенсорный ввод/нажатие**</span><span class="sxs-lookup"><span data-stu-id="f9be4-163">**Touch / press**</span></span><br>
        <span data-ttu-id="f9be4-164">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="f9be4-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f9be4-165">![Осознавать](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="f9be4-166">**Осознавать**</span><span class="sxs-lookup"><span data-stu-id="f9be4-166">**Grasp**</span></span><br>
        <span data-ttu-id="f9be4-167">Визуальная и обратная связь.</span><span class="sxs-lookup"><span data-stu-id="f9be4-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="f9be4-168">[Кнопка в HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) представляет собой пример визуализации различных состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f9be4-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f9be4-169">![по умолчанию](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="f9be4-170">**Default**</span><span class="sxs-lookup"><span data-stu-id="f9be4-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f9be4-171">![Наведение](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="f9be4-172">**Наведение**</span><span class="sxs-lookup"><span data-stu-id="f9be4-172">**Hover**</span></span><br>
        <span data-ttu-id="f9be4-173">Показать эффекты освещения на основе близости.</span><span class="sxs-lookup"><span data-stu-id="f9be4-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="f9be4-174">![Сенсорный ввод](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="f9be4-175">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="f9be4-175">**Touch**</span></span><br>
        <span data-ttu-id="f9be4-176">Отображать эффекты Ripple.</span><span class="sxs-lookup"><span data-stu-id="f9be4-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f9be4-177">![Сочетание клавиш](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="f9be4-178">**Сочетание клавиш**</span><span class="sxs-lookup"><span data-stu-id="f9be4-178">**Press**</span></span><br>
        <span data-ttu-id="f9be4-179">Переместите переднюю форму.</span><span class="sxs-lookup"><span data-stu-id="f9be4-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="f9be4-180">Визуальная подсказка кольца в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f9be4-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="f9be4-181">В HoloLens 2 есть еще одна визуальная подсказка, которая помогает восприятие пользователя.</span><span class="sxs-lookup"><span data-stu-id="f9be4-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="f9be4-182">Кольцо рядом с ним отображается и масштабируется по мере того, как прокрутка будет ближе к объекту.</span><span class="sxs-lookup"><span data-stu-id="f9be4-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="f9be4-183">В конечном итоге, если достигнуто нажатое состояние, кольцо будет находиться в точке.</span><span class="sxs-lookup"><span data-stu-id="f9be4-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="f9be4-184">Этот визуальный подход позволяет пользователю понять, насколько далеко они от объекта.</span><span class="sxs-lookup"><span data-stu-id="f9be4-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="f9be4-185">*Цикл видео. пример визуальной обратной связи на основе сходства с ограничивающим прямоугольником*</span><span class="sxs-lookup"><span data-stu-id="f9be4-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f9be4-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f9be4-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f9be4-187">![Визуальный отзыв о близком к рукой](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="f9be4-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="f9be4-188">Звуковые подсказки</span><span class="sxs-lookup"><span data-stu-id="f9be4-188">Audio cues</span></span>

<span data-ttu-id="f9be4-189">При прямом взаимодействии руки правильная обратная связь может значительно улучшить взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="f9be4-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="f9be4-190">Используйте отзыв о звуке, чтобы сообщить следующие подсказки:</span><span class="sxs-lookup"><span data-stu-id="f9be4-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="f9be4-191">**Начало контакта**: воспроизведение звука при начале сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="f9be4-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="f9be4-192">**Окончание контакта**: воспроизведение звука в сенсорном конце</span><span class="sxs-lookup"><span data-stu-id="f9be4-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="f9be4-193">**Начало захвата**: воспроизведение звука при начале</span><span class="sxs-lookup"><span data-stu-id="f9be4-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="f9be4-194">**Конец захвата**: воспроизведение звука при завершении захвата</span><span class="sxs-lookup"><span data-stu-id="f9be4-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="f9be4-195">Голосовые команды</span><span class="sxs-lookup"><span data-stu-id="f9be4-195">Voice commanding</span></span><br>
        <span data-ttu-id="f9be4-196">Для любых взаимодействующих объектов важно поддерживать альтернативные варианты взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f9be4-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="f9be4-197">По умолчанию рекомендуется поддерживать [командную команду Voice](../out-of-scope/voice-design.md) для всех объектов, которые являются взаимодействующими.</span><span class="sxs-lookup"><span data-stu-id="f9be4-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="f9be4-198">Чтобы улучшить возможность обнаружения, можно также предоставить подсказку во время наведения указателя мыши.</span><span class="sxs-lookup"><span data-stu-id="f9be4-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="f9be4-199">*Изображение: подсказка для команды Voice*</span><span class="sxs-lookup"><span data-stu-id="f9be4-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![голосовое командое](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="f9be4-201">Рекомендации относительно размеров</span><span class="sxs-lookup"><span data-stu-id="f9be4-201">Sizing recommendations</span></span> 

<span data-ttu-id="f9be4-202">Чтобы можно было легко затронуть все взаимодействующие объекты, рекомендуется убедиться, что они соответствуют минимальному размеру в зависимости от того, какое расстояние он помещает от пользователя.</span><span class="sxs-lookup"><span data-stu-id="f9be4-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="f9be4-203">Визуальный угол часто измеряется в градусах визуального дуги. Визуальный угол основан на расстоянии между глазами пользователя и объектом и остается постоянным, а физический размер целевого объекта может измениться по мере изменения расстояния от пользователя.</span><span class="sxs-lookup"><span data-stu-id="f9be4-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="f9be4-204">Чтобы определить необходимый физический размер объекта на основе расстояния от пользователя, попробуйте использовать визуальный калькулятор [угла, такой как.](https://elvers.us/perception/visualAngle/)</span><span class="sxs-lookup"><span data-stu-id="f9be4-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="f9be4-205">Ниже приведены рекомендации для минимального размера взаимодействующего содержимого.</span><span class="sxs-lookup"><span data-stu-id="f9be4-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="f9be4-206">Целевой размер для взаимодействия непосредственно с рукой</span><span class="sxs-lookup"><span data-stu-id="f9be4-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="f9be4-207">расстояние;</span><span class="sxs-lookup"><span data-stu-id="f9be4-207">Distance</span></span> | <span data-ttu-id="f9be4-208">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="f9be4-208">Viewing angle</span></span> | <span data-ttu-id="f9be4-209">Размер</span><span class="sxs-lookup"><span data-stu-id="f9be4-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="f9be4-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="f9be4-210">45 cm</span></span>  | <span data-ttu-id="f9be4-211">не меньше 2 °</span><span class="sxs-lookup"><span data-stu-id="f9be4-211">no smaller than 2°</span></span> | <span data-ttu-id="f9be4-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="f9be4-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="f9be4-213">![Целевой размер для взаимодействия непосредственно с рукой](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="f9be4-214">*Целевой размер для взаимодействия непосредственно с рукой*</span><span class="sxs-lookup"><span data-stu-id="f9be4-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="f9be4-215">Целевой размер для кнопок</span><span class="sxs-lookup"><span data-stu-id="f9be4-215">Target size for buttons</span></span>

<span data-ttu-id="f9be4-216">При создании кнопок для прямого взаимодействия рекомендуется увеличить минимальный размер 3,2 x 3,2 cm, чтобы убедиться в наличии достаточного места для размещения значка и потенциального текста.</span><span class="sxs-lookup"><span data-stu-id="f9be4-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="f9be4-217">расстояние;</span><span class="sxs-lookup"><span data-stu-id="f9be4-217">Distance</span></span> | <span data-ttu-id="f9be4-218">Минимальный размер</span><span class="sxs-lookup"><span data-stu-id="f9be4-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="f9be4-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="f9be4-219">45 cm</span></span>  | <span data-ttu-id="f9be4-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="f9be4-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="f9be4-221">![Целевой размер для кнопок](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="f9be4-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="f9be4-222">*Целевой размер для кнопок*</span><span class="sxs-lookup"><span data-stu-id="f9be4-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="f9be4-223">Целевой размер для взаимодействия "рука" или "взгляд"</span><span class="sxs-lookup"><span data-stu-id="f9be4-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="f9be4-224">расстояние;</span><span class="sxs-lookup"><span data-stu-id="f9be4-224">Distance</span></span> | <span data-ttu-id="f9be4-225">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="f9be4-225">Viewing angle</span></span> | <span data-ttu-id="f9be4-226">Размер</span><span class="sxs-lookup"><span data-stu-id="f9be4-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="f9be4-227">2 м</span><span class="sxs-lookup"><span data-stu-id="f9be4-227">2 m</span></span>  | <span data-ttu-id="f9be4-228">не меньше 1 °</span><span class="sxs-lookup"><span data-stu-id="f9be4-228">no smaller than 1°</span></span> | <span data-ttu-id="f9be4-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="f9be4-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="f9be4-230">![Целевой размер для взаимодействия "рука" или "взгляд"](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9be4-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="f9be4-231">*Целевой размер для взаимодействия "рука" или "взгляд"*</span><span class="sxs-lookup"><span data-stu-id="f9be4-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f9be4-232">Взаимодействующий объект в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="f9be4-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="f9be4-233">В **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно использовать [**взаимодействие**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) с скриптом, чтобы объекты отвечали на различные типы состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f9be4-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="f9be4-234">Он поддерживает различные типы тем, которые позволяют определять визуальные состояния, управляя свойствами объектов, такими как цвет, размер, материал и шейдер.</span><span class="sxs-lookup"><span data-stu-id="f9be4-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="f9be4-235">Элементом</span><span class="sxs-lookup"><span data-stu-id="f9be4-235">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="f9be4-236">Button</span><span class="sxs-lookup"><span data-stu-id="f9be4-236">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="f9be4-237">Сцены с примерами взаимодействия руки</span><span class="sxs-lookup"><span data-stu-id="f9be4-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="f9be4-238">Стандартный шейдер Микседреалититулкит предоставляет различные параметры, такие как **освещение** , позволяющее создавать визуальные и звуковые подсказки.</span><span class="sxs-lookup"><span data-stu-id="f9be4-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="f9be4-239">Стандартный шейдер МРТК</span><span class="sxs-lookup"><span data-stu-id="f9be4-239">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="f9be4-240">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f9be4-240">See also</span></span>

* [<span data-ttu-id="f9be4-241">Курсоры</span><span class="sxs-lookup"><span data-stu-id="f9be4-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f9be4-242">Телекинез</span><span class="sxs-lookup"><span data-stu-id="f9be4-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f9be4-243">Кнопка</span><span class="sxs-lookup"><span data-stu-id="f9be4-243">Button</span></span>](button.md)
* [<span data-ttu-id="f9be4-244">Активный объект</span><span class="sxs-lookup"><span data-stu-id="f9be4-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f9be4-245">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="f9be4-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f9be4-246">Оперирование</span><span class="sxs-lookup"><span data-stu-id="f9be4-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f9be4-247">Меню руки</span><span class="sxs-lookup"><span data-stu-id="f9be4-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f9be4-248">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="f9be4-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f9be4-249">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="f9be4-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f9be4-250">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="f9be4-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f9be4-251">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="f9be4-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f9be4-252">Подсказка</span><span class="sxs-lookup"><span data-stu-id="f9be4-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f9be4-253">Планшет</span><span class="sxs-lookup"><span data-stu-id="f9be4-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="f9be4-254">Ползунок</span><span class="sxs-lookup"><span data-stu-id="f9be4-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="f9be4-255">Шейдер</span><span class="sxs-lookup"><span data-stu-id="f9be4-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="f9be4-256">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="f9be4-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f9be4-257">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="f9be4-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f9be4-258">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="f9be4-258">Surface magnetism</span></span>](surface-magnetism.md)
