---
title: Наведение и фиксация с использованием рук
description: Общие сведения о модели ввода с наведением и фиксацией
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Смешанная реальность, взаимодействие, проектирование, HoloLens, руки, вдали, указание и фиксация
ms.openlocfilehash: 5baf625127b1c1757bb6ae82473adcb8329746cd
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699448"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="a3652-104">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="a3652-104">Point and commit with hands</span></span>

![Курсоры](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="a3652-106">Наведение и фиксация с использованием рук представляет собой модель ввода, которая позволяет пользователям нацеливаться на двухмерное содержимое и трехмерные объекты, а также выделять их и управлять ими на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="a3652-106">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="a3652-107">Этот способ удаленного взаимодействия характерен только для смешанной реальности. В реальном мире люди не взаимодействуют так с объектами.</span><span class="sxs-lookup"><span data-stu-id="a3652-107">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="a3652-108">Например, в фильме о супергероях *Люди Икс* персонаж [Магнето](https://en.wikipedia.org/wiki/Magneto_(comics)) способен дотягиваться до удаленных объектов и манипулировать ими на расстоянии с использованием рук.</span><span class="sxs-lookup"><span data-stu-id="a3652-108">For example, in the super hero movie, *X-Men* , the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="a3652-109">Это не то, что люди могут делать в реальности.</span><span class="sxs-lookup"><span data-stu-id="a3652-109">This is not something humans can do in reality.</span></span> <span data-ttu-id="a3652-110">В HoloLens (AR) и смешанной реальности (MR) мы снабжаем пользователей этой магической силой, преодолевающей физические ограничения реального мира не только для работы с голографическим содержимым, но и для более эффективного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a3652-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="a3652-111">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="a3652-111">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="a3652-112"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="a3652-112"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="a3652-113"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a3652-113"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="a3652-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a3652-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="a3652-115"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="a3652-115"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="a3652-116">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="a3652-116">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="a3652-117">❌ Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="a3652-117">❌ Not supported</span></span></td>
     <td><span data-ttu-id="a3652-118">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a3652-118">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="a3652-119">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a3652-119">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="a3652-120">_Наведение и фиксация_  — одна из появившихся возможностей, использующих новую систему отслеживания рук.</span><span class="sxs-lookup"><span data-stu-id="a3652-120">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="a3652-121">Это основная модель ввода в иммерсивных гарнитурах, использующих контроллеры движений.</span><span class="sxs-lookup"><span data-stu-id="a3652-121">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="a3652-122">Лучи рук</span><span class="sxs-lookup"><span data-stu-id="a3652-122">Hand rays</span></span>

<span data-ttu-id="a3652-123">В HoloLens 2 мы разработали функцию телекинеза. При ее применении для пользователя отображается луч, исходящий из центра его ладони.</span><span class="sxs-lookup"><span data-stu-id="a3652-123">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="a3652-124">Этот луч рассматривается как продолжение руки.</span><span class="sxs-lookup"><span data-stu-id="a3652-124">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="a3652-125">Курсор в виде кольца присоединяется к концу луча, указывая расположение, в котором луч пересекается с целевым объектом.</span><span class="sxs-lookup"><span data-stu-id="a3652-125">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="a3652-126">После этого объект, на котором размещается курсор, может получать жестовые команды от руки.</span><span class="sxs-lookup"><span data-stu-id="a3652-126">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="a3652-127">Эта базовая жестовая команда запускается действием касания с помощью большого и указательного пальца.</span><span class="sxs-lookup"><span data-stu-id="a3652-127">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="a3652-128">Используя телекинез для наведения и подтверждения, пользователи могут активировать кнопку или гиперссылку.</span><span class="sxs-lookup"><span data-stu-id="a3652-128">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="a3652-129">С помощью более сложных жестов пользователи могут переходить по веб-содержимому и управлять трехмерными объектами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="a3652-129">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="a3652-130">Визуальный дизайн луча руки также должен реагировать на эти состояния наведения и фиксации, как описано и показано ниже.</span><span class="sxs-lookup"><span data-stu-id="a3652-130">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="a3652-131">![Указывающий телекинез](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-131">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="a3652-132">**Состояние указания**</span><span class="sxs-lookup"><span data-stu-id="a3652-132">**Pointing state**</span></span><br>
        <span data-ttu-id="a3652-133">В состоянии *указания* луч представлен штриховой линией, а курсор — в форме кольца.</span><span class="sxs-lookup"><span data-stu-id="a3652-133">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a3652-134">![Фиксация телекинеза](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-134">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="a3652-135">**Состояние фиксации**</span><span class="sxs-lookup"><span data-stu-id="a3652-135">**Commit state**</span></span><br>
        <span data-ttu-id="a3652-136">В состоянии *фиксации* луч превращается в сплошную линию, а курсор сжимается в точку.</span><span class="sxs-lookup"><span data-stu-id="a3652-136">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="a3652-137">Переход между "близко" и "далеко"</span><span class="sxs-lookup"><span data-stu-id="a3652-137">Transition between near and far</span></span>

<span data-ttu-id="a3652-138">Мы разработали луч, исходящий из центра ладони, что освобождает пять пальцев для более манипулятивных жестов, таких как сжатие и захват. Благодаря этому вам не нужно направлять луч с помощью определенных жестов, таких как наведение указательным пальцем.</span><span class="sxs-lookup"><span data-stu-id="a3652-138">Instead of using specific gestures, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="a3652-139">При такой структуре мы создаем только одну ментальную модель, в которой один и тот же набор жестов руками используется для близкого и удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a3652-139">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="a3652-140">Для управления объектами на различных расстояниях можно использовать один и тот же жест захвата.</span><span class="sxs-lookup"><span data-stu-id="a3652-140">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="a3652-141">Вызов лучей происходит автоматически и зависит от расстояния до объекта, как указано ниже:</span><span class="sxs-lookup"><span data-stu-id="a3652-141">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a3652-142">![Манипуляция вблизи](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-142">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="a3652-143">**Манипуляция вблизи**</span><span class="sxs-lookup"><span data-stu-id="a3652-143">**Near manipulation**</span></span><br>
        <span data-ttu-id="a3652-144">Если объект находится на расстоянии вытянутой руки (примерно 50 см), лучи автоматически отключаются, побуждая к близкому взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="a3652-144">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a3652-145">![Манипуляция вдали](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-145">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="a3652-146">**Манипуляция вдали**</span><span class="sxs-lookup"><span data-stu-id="a3652-146">**Far manipulation**</span></span><br>
        <span data-ttu-id="a3652-147">Если объект находится дальше, чем на расстоянии 50 см, лучи включаются.</span><span class="sxs-lookup"><span data-stu-id="a3652-147">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="a3652-148">Переход должен быть плавным и легким.</span><span class="sxs-lookup"><span data-stu-id="a3652-148">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="a3652-149">Взаимодействие с двумерным экраном</span><span class="sxs-lookup"><span data-stu-id="a3652-149">2D slate interaction</span></span>

<span data-ttu-id="a3652-150">Двухмерный экран — это голографический контейнер с содержимым двухмерных приложений, такой как веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="a3652-150">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="a3652-151">Концепция разработки удаленного взаимодействия с двухмерным экраном заключается в использовании лучей рук для наведения и касании для выделения.</span><span class="sxs-lookup"><span data-stu-id="a3652-151">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="a3652-152">После наведения на цель луча руки пользователи могут с помощью касания активировать гиперссылку или кнопку.</span><span class="sxs-lookup"><span data-stu-id="a3652-152">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="a3652-153">Они могут использовать одну руку для касания и захвата, чтобы прокрутить содержимое экрана вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="a3652-153">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="a3652-154">Относительное движение при использовании обеих рук для касания и захвата может увеличить и уменьшить масштаб содержимого экрана.</span><span class="sxs-lookup"><span data-stu-id="a3652-154">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="a3652-155">При нацеливании луча руки на углы и края появляется отображение ближайших возможностей для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a3652-155">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="a3652-156">Возможности захвата и перетаскивания позволяют пользователям выполнять равномерное масштабирование (движения от углов или к углам) и адаптировать экран (движения от краев или к краям).</span><span class="sxs-lookup"><span data-stu-id="a3652-156">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="a3652-157">Путем захвата и перетаскивания голографической панели в верхней части двухмерного экрана пользователи могут переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="a3652-157">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a3652-158">![Взаимодействие щелчком с двухмерным экраном планшета](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-158">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="a3652-159">**Щелчок**</span><span class="sxs-lookup"><span data-stu-id="a3652-159">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-160">![Взаимодействие прокруткой с двухмерным экраном планшета](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-160">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="a3652-161">**Прокрутка**</span><span class="sxs-lookup"><span data-stu-id="a3652-161">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-162">![Взаимодействие масштабированием с двухмерным экраном планшета](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-162">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="a3652-163">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="a3652-163">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="a3652-164">**Для манипуляции двухмерным экраном планшета** :</span><span class="sxs-lookup"><span data-stu-id="a3652-164">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="a3652-165">Пользователи нацеливают луч руки на углы и края, чтобы появилось отображение ближайших возможностей для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a3652-165">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="a3652-166">Применяя жест манипуляции к возможности, пользователи могут выполнить равномерное масштабирование (движения от углов или к углам) и адаптировать экран (движения от краев или к краям).</span><span class="sxs-lookup"><span data-stu-id="a3652-166">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="a3652-167">Применяя жест манипуляции к голографической панели в верхней части двухмерного экрана, пользователи могут переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="a3652-167">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="a3652-168">Манипуляция трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="a3652-168">3D object manipulation</span></span>

<span data-ttu-id="a3652-169">Есть два способа не манипуляции трехмерными объектами: манипуляция на основе возможностей и манипуляция без использования возможностей.</span><span class="sxs-lookup"><span data-stu-id="a3652-169">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="a3652-170">В модели наведения и фиксации пользователи могут выполнять точно такие же задачи с помощью лучей рук.</span><span class="sxs-lookup"><span data-stu-id="a3652-170">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="a3652-171">Дополнительное обучение не требуется.</span><span class="sxs-lookup"><span data-stu-id="a3652-171">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="a3652-172">Манипуляция на основе возможностей</span><span class="sxs-lookup"><span data-stu-id="a3652-172">Affordance-based manipulation</span></span>
<span data-ttu-id="a3652-173">Пользователи используют лучи рук, чтобы навести и выявить ограничивающую рамку и возможности для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a3652-173">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="a3652-174">Пользователи могут применить жест манипуляции к ограничивающей рамке, чтобы переместить весь объект; к краям, чтобы активировать возможности поворота; и к углам, чтобы активировать возможности для равномерного масштабирования.</span><span class="sxs-lookup"><span data-stu-id="a3652-174">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="a3652-175">![Манипулирование трехмерным объектом: перемещение издалека](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-175">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="a3652-176">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="a3652-176">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-177">![Манипулирование трехмерным объектом: поворот издалека](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-177">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="a3652-178">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="a3652-178">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-179">![Манипулирование трехмерным объектом: масштабирование издалека](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-179">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="a3652-180">**Масштаб**</span><span class="sxs-lookup"><span data-stu-id="a3652-180">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="a3652-181">Манипуляция без использования возможностей</span><span class="sxs-lookup"><span data-stu-id="a3652-181">Non-affordance based manipulation</span></span>
<span data-ttu-id="a3652-182">Пользователи наводят лучи рук, чтобы появилось отображение ограничивающей рамки, а затем к нему непосредственно применяют жесты манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a3652-182">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="a3652-183">При использовании одной руки перемещение и вращение объекта связаны с движением и ориентацией руки.</span><span class="sxs-lookup"><span data-stu-id="a3652-183">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="a3652-184">При использовании обеих рук пользователи могут перемещать, масштабировать и вращать объект в соответствии с относительными движениями обеих рук.</span><span class="sxs-lookup"><span data-stu-id="a3652-184">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="a3652-185">Инстинктивные жесты</span><span class="sxs-lookup"><span data-stu-id="a3652-185">Instinctual gestures</span></span>
<span data-ttu-id="a3652-186">Концепция инстинктивных жестов для наведения и подтверждения аналогична [непосредственной манипуляции](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="a3652-186">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="a3652-187">Жесты, которые пользователи могут применять к трехмерному объекту, определяются структурой возможностей пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a3652-187">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="a3652-188">Например, небольшая контрольная точка может побуждать пользователей сжать объект с помощью большого и указательного пальцев, в то время как для захвата объекта большего размера пользователь может предпочесть использовать все пять пальцев.</span><span class="sxs-lookup"><span data-stu-id="a3652-188">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a3652-189">![Управление маленьким объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-189">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="a3652-190">**Маленький объект**</span><span class="sxs-lookup"><span data-stu-id="a3652-190">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-191">![Управление средним объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-191">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="a3652-192">**Средний объект**</span><span class="sxs-lookup"><span data-stu-id="a3652-192">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a3652-193">![Управление крупным объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-193">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="a3652-194">**Крупный объект**</span><span class="sxs-lookup"><span data-stu-id="a3652-194">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="a3652-195">Симметричный дизайн для работы с помощью рук и контроллеров с шестью степенями свободы</span><span class="sxs-lookup"><span data-stu-id="a3652-195">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="a3652-196">Концепция наведения и подтверждения для удаленного взаимодействия изначально была создана и определена для Портала смешанной реальности (MRP), где пользователь надевает иммерсивную гарнитуру и работает с трехмерными объектами через контроллеры движений.</span><span class="sxs-lookup"><span data-stu-id="a3652-196">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="a3652-197">Контроллеры движений выпускают лучи для наведения на дальние объекты и манипулирования ими.</span><span class="sxs-lookup"><span data-stu-id="a3652-197">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="a3652-198">На контроллерах есть кнопки для выполнения различных действий.</span><span class="sxs-lookup"><span data-stu-id="a3652-198">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="a3652-199">Мы используем модель взаимодействия с помощью лучей и прикрепляем их к обеим рукам.</span><span class="sxs-lookup"><span data-stu-id="a3652-199">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="a3652-200">При такой симметричной структуре пользователям, знакомым с MRP, не понадобится изучать другую модель взаимодействия для удаленного наведения и манипуляции при использовании HoloLen 2 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="a3652-200">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="a3652-201">![Симметричная структура лучей для контроллеров](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-201">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="a3652-202">**Лучи контроллера**</span><span class="sxs-lookup"><span data-stu-id="a3652-202">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a3652-203">![Симметричная структура лучей для рук](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3652-203">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="a3652-204">**Лучи рук**</span><span class="sxs-lookup"><span data-stu-id="a3652-204">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a3652-205">Телекинез в MRTK (наборе средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="a3652-205">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a3652-206">По умолчанию в MRTK предоставляется заготовка для телекинеза ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)), которая имеет то же визуальное состояние, что и телекинез в системе оболочки.</span><span class="sxs-lookup"><span data-stu-id="a3652-206">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="a3652-207">Она назначается в профиле ввода данных в MRTK в разделе "Указатели".</span><span class="sxs-lookup"><span data-stu-id="a3652-207">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="a3652-208">В иммерсивной гарнитуре для контроллеров движений используются такие же лучи.</span><span class="sxs-lookup"><span data-stu-id="a3652-208">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="a3652-209">MRTK — профиль указателя</span><span class="sxs-lookup"><span data-stu-id="a3652-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="a3652-210">MRTK — система ввода</span><span class="sxs-lookup"><span data-stu-id="a3652-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="a3652-211">MRTK — указатели</span><span class="sxs-lookup"><span data-stu-id="a3652-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="a3652-212">См. также</span><span class="sxs-lookup"><span data-stu-id="a3652-212">See also</span></span>
* [<span data-ttu-id="a3652-213">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="a3652-213">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a3652-214">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="a3652-214">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a3652-215">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="a3652-215">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a3652-216">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="a3652-216">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a3652-217">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a3652-217">Instinctual interactions</span></span>](interaction-fundamentals.md)
