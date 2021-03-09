---
title: Наведение и фиксация с использованием рук
description: Сведения об основах модели ввода с наведением и фиксацией для поддержки жестов в приложениях смешанной реальности.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, взаимодействие, проектирование, HoloLens, руки, дальность, наведение и фиксация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, телекинез, манипулирование объектами, MRTK, Mixed Reality Toolkit, степень свободы
ms.openlocfilehash: 8196b67f103bae346ba4da065ee6045ff231b004
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759870"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="20bbe-104">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="20bbe-104">Point and commit with hands</span></span>

![Курсоры](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="20bbe-106">Модель ввода с наведением и фиксацией при помощи рук позволяет пользователям нацеливаться на двумерные и трехмерные объекты, расположенные вне пределов прямой досягаемости, выделять их и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="20bbe-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="20bbe-107">Этот способ "дальнего" взаимодействия характерен только для смешанной реальности, поскольку в реальном мире люди не могут так взаимодействовать с объектами.</span><span class="sxs-lookup"><span data-stu-id="20bbe-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="20bbe-108">Например, в фильме о супергероях *Люди Икс* персонаж [Магнето](https://en.wikipedia.org/wiki/Magneto_(comics)) может манипулировать удаленными объектами на расстоянии, используя жесты рук.</span><span class="sxs-lookup"><span data-stu-id="20bbe-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="20bbe-109">В реальной жизни у людей нет таких способностей.</span><span class="sxs-lookup"><span data-stu-id="20bbe-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="20bbe-110">При использовании технологий дополненной реальности (HoloLens) или смешанной реальности пользователи могут применять эти волшебные способности, выходя за пределы физических ограничений реального мира.</span><span class="sxs-lookup"><span data-stu-id="20bbe-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="20bbe-111">Эти возможности делают голографическое взаимодействие не только веселым, но и более эффективным.</span><span class="sxs-lookup"><span data-stu-id="20bbe-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="20bbe-112">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="20bbe-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="20bbe-113"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="20bbe-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="20bbe-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="20bbe-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="20bbe-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="20bbe-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="20bbe-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="20bbe-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="20bbe-117">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="20bbe-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="20bbe-118">❌ Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="20bbe-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="20bbe-119">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="20bbe-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="20bbe-120">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="20bbe-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="20bbe-121">_Наведение и фиксация_ — одна из новых возможностей, которая основана на новой системе отслеживания рук.</span><span class="sxs-lookup"><span data-stu-id="20bbe-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="20bbe-122">Она используется как основная модель ввода в иммерсивных гарнитурах с применением контроллеров движений.</span><span class="sxs-lookup"><span data-stu-id="20bbe-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="20bbe-123">Лучи рук</span><span class="sxs-lookup"><span data-stu-id="20bbe-123">Hand rays</span></span>

<span data-ttu-id="20bbe-124">В HoloLens 2 мы разработали функцию телекинеза. При ее применении для пользователя отображается луч, исходящий из центра его ладони.</span><span class="sxs-lookup"><span data-stu-id="20bbe-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="20bbe-125">Этот луч рассматривается как продолжение руки.</span><span class="sxs-lookup"><span data-stu-id="20bbe-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="20bbe-126">Курсор в виде кольца присоединяется к концу луча, указывая расположение, в котором луч пересекается с целевым объектом.</span><span class="sxs-lookup"><span data-stu-id="20bbe-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="20bbe-127">После этого объект, на котором размещается курсор, может получать жестовые команды от руки.</span><span class="sxs-lookup"><span data-stu-id="20bbe-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="20bbe-128">Эта базовая жестовая команда запускается действием касания с помощью большого и указательного пальца.</span><span class="sxs-lookup"><span data-stu-id="20bbe-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="20bbe-129">Используя телекинез для наведения и подтверждения, пользователи могут активировать кнопку или гиперссылку.</span><span class="sxs-lookup"><span data-stu-id="20bbe-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="20bbe-130">С помощью более сложных жестов пользователи могут просматривать веб-содержимое и управлять трехмерными объектами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="20bbe-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="20bbe-131">Визуальный дизайн луча руки также должен реагировать на эти состояния наведения и фиксации, как описано и показано ниже.</span><span class="sxs-lookup"><span data-stu-id="20bbe-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="20bbe-132">![Указывающий телекинез](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="20bbe-133">**Состояние указания**</span><span class="sxs-lookup"><span data-stu-id="20bbe-133">**Pointing state**</span></span><br>
        <span data-ttu-id="20bbe-134">В состоянии *указания* луч представлен штриховой линией, а курсор — в форме кольца.</span><span class="sxs-lookup"><span data-stu-id="20bbe-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20bbe-135">![Фиксация телекинеза](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="20bbe-136">**Состояние фиксации**</span><span class="sxs-lookup"><span data-stu-id="20bbe-136">**Commit state**</span></span><br>
        <span data-ttu-id="20bbe-137">В состоянии *фиксации* луч превращается в сплошную линию, а курсор сжимается в точку.</span><span class="sxs-lookup"><span data-stu-id="20bbe-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="20bbe-138">Переход между "близко" и "далеко"</span><span class="sxs-lookup"><span data-stu-id="20bbe-138">Transition between near and far</span></span>

<span data-ttu-id="20bbe-139">Вместо специальных методов для выбора направления луча, например жестов указательным пальцем, мы используем луч, исходящий из центра ладони пользователя.</span><span class="sxs-lookup"><span data-stu-id="20bbe-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="20bbe-140">Это позволяет освободить все пять пальцев для резервирования жестов, соответствующих более конкретным манипуляциям, таким как сжатие и захват.</span><span class="sxs-lookup"><span data-stu-id="20bbe-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="20bbe-141">При такой структуре мы создаем только одну ментальную модель, в которой один и тот же набор жестов руками используется для близкого и удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="20bbe-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="20bbe-142">Для управления объектами на различных расстояниях можно использовать один и тот же жест захвата.</span><span class="sxs-lookup"><span data-stu-id="20bbe-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="20bbe-143">Вызов лучей происходит автоматически и зависит от расстояния до объекта, как указано ниже:</span><span class="sxs-lookup"><span data-stu-id="20bbe-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="20bbe-144">![Манипуляция вблизи](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="20bbe-145">**Манипуляция вблизи**</span><span class="sxs-lookup"><span data-stu-id="20bbe-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="20bbe-146">Если объект находится на расстоянии вытянутой руки (примерно 50 см), лучи автоматически отключаются, побуждая к близкому взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="20bbe-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20bbe-147">![Манипуляция вдали](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="20bbe-148">**Манипуляция вдали**</span><span class="sxs-lookup"><span data-stu-id="20bbe-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="20bbe-149">Если объект находится дальше, чем на расстоянии 50 см, лучи включаются.</span><span class="sxs-lookup"><span data-stu-id="20bbe-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="20bbe-150">Переход должен быть плавным и легким.</span><span class="sxs-lookup"><span data-stu-id="20bbe-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="20bbe-151">Взаимодействие с двумерным экраном</span><span class="sxs-lookup"><span data-stu-id="20bbe-151">2D slate interaction</span></span>

<span data-ttu-id="20bbe-152">Двухмерный экран — это голографический контейнер с содержимым двухмерных приложений, такой как веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="20bbe-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="20bbe-153">Концепция разработки удаленного взаимодействия с двухмерным экраном заключается в использовании лучей рук для наведения и касании для выделения.</span><span class="sxs-lookup"><span data-stu-id="20bbe-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="20bbe-154">После наведения на цель луча руки пользователи могут с помощью касания активировать гиперссылку или кнопку.</span><span class="sxs-lookup"><span data-stu-id="20bbe-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="20bbe-155">Они могут использовать одну руку для касания и захвата, чтобы прокрутить содержимое экрана вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="20bbe-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="20bbe-156">Относительное движение при использовании обеих рук для касания и захвата может увеличить и уменьшить масштаб содержимого экрана.</span><span class="sxs-lookup"><span data-stu-id="20bbe-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="20bbe-157">При нацеливании луча руки на углы и края появляется отображение ближайших возможностей для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="20bbe-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="20bbe-158">Применяя к этим возможностям действия захвата и перетаскивания, пользователь может выполнять равномерное масштабирование (угловые возможности) и изменять пропорции (возможности граней).</span><span class="sxs-lookup"><span data-stu-id="20bbe-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="20bbe-159">Путем захвата и перетаскивания голографической панели в верхней части двухмерного экрана пользователи могут переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="20bbe-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="20bbe-160">![Взаимодействие щелчком с двухмерным экраном планшета](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="20bbe-161">**Щелчок**</span><span class="sxs-lookup"><span data-stu-id="20bbe-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-162">![Взаимодействие прокруткой с двухмерным экраном планшета](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="20bbe-163">**Прокрутка**</span><span class="sxs-lookup"><span data-stu-id="20bbe-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-164">![Взаимодействие масштабированием с двухмерным экраном планшета](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="20bbe-165">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="20bbe-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="20bbe-166">**Для манипуляции двухмерным экраном планшета**:</span><span class="sxs-lookup"><span data-stu-id="20bbe-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="20bbe-167">Пользователи нацеливают луч руки на углы и края, чтобы появилось отображение ближайших возможностей для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="20bbe-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="20bbe-168">Применяя к этим возможностям действия манипуляции, пользователь может выполнять равномерное масштабирование (угловые возможности) и изменять пропорции (возможности граней).</span><span class="sxs-lookup"><span data-stu-id="20bbe-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="20bbe-169">Применяя жест манипуляции к голографической панели в верхней части двухмерного экрана, пользователи могут переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="20bbe-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="20bbe-170">Манипуляция трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="20bbe-170">3D object manipulation</span></span>

<span data-ttu-id="20bbe-171">Есть два способа не манипуляции трехмерными объектами: манипуляция на основе возможностей и манипуляция без использования возможностей.</span><span class="sxs-lookup"><span data-stu-id="20bbe-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="20bbe-172">В модели наведения и фиксации пользователи могут выполнять точно такие же задачи с помощью телекинеза.</span><span class="sxs-lookup"><span data-stu-id="20bbe-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="20bbe-173">Дополнительного обучения не требуется.</span><span class="sxs-lookup"><span data-stu-id="20bbe-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="20bbe-174">Манипуляция на основе возможностей</span><span class="sxs-lookup"><span data-stu-id="20bbe-174">Affordance-based manipulation</span></span>

<span data-ttu-id="20bbe-175">Пользователи используют лучи рук, чтобы навести и выявить ограничивающую рамку и возможности для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="20bbe-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="20bbe-176">Пользователи могут применить жест манипуляции к ограничивающей рамке, чтобы переместить весь объект; к краям, чтобы активировать возможности поворота; и к углам, чтобы активировать возможности для равномерного масштабирования.</span><span class="sxs-lookup"><span data-stu-id="20bbe-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="20bbe-177">![Манипулирование трехмерным объектом: перемещение издалека](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="20bbe-178">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="20bbe-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-179">![Манипулирование трехмерным объектом: поворот издалека](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="20bbe-180">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="20bbe-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-181">![Манипулирование трехмерным объектом: масштабирование издалека](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="20bbe-182">**Масштаб**</span><span class="sxs-lookup"><span data-stu-id="20bbe-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="20bbe-183">Манипуляция без использования возможностей</span><span class="sxs-lookup"><span data-stu-id="20bbe-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="20bbe-184">Пользователи наводят лучи рук, чтобы появилось отображение ограничивающей рамки, а затем к нему непосредственно применяют жесты манипуляции.</span><span class="sxs-lookup"><span data-stu-id="20bbe-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="20bbe-185">При использовании одной руки перемещение и вращение объекта связаны с движением и ориентацией руки.</span><span class="sxs-lookup"><span data-stu-id="20bbe-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="20bbe-186">При использовании обеих рук пользователи могут перемещать, масштабировать и вращать объект в соответствии с относительными движениями обеих рук.</span><span class="sxs-lookup"><span data-stu-id="20bbe-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="20bbe-187">Инстинктивные жесты</span><span class="sxs-lookup"><span data-stu-id="20bbe-187">Instinctual gestures</span></span>

<span data-ttu-id="20bbe-188">Концепция инстинктивных жестов для наведения и подтверждения аналогична [непосредственной манипуляции](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="20bbe-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="20bbe-189">Жесты, которые пользователи могут применять к трехмерному объекту, определяются структурой возможностей пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="20bbe-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="20bbe-190">Например, небольшая контрольная точка провоцирует сжать объект с помощью большого и указательного пальцев, а для захвата большого объекта интуитивно привычнее использовать все пять пальцев.</span><span class="sxs-lookup"><span data-stu-id="20bbe-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="20bbe-191">![Управление маленьким объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="20bbe-192">**Маленький объект**</span><span class="sxs-lookup"><span data-stu-id="20bbe-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-193">![Управление средним объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="20bbe-194">**Средний объект**</span><span class="sxs-lookup"><span data-stu-id="20bbe-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20bbe-195">![Управление крупным объектом издалека с помощью инстинктивных жестов](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="20bbe-196">**Крупный объект**</span><span class="sxs-lookup"><span data-stu-id="20bbe-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="20bbe-197">Симметричный дизайн для работы с помощью рук и контроллеров с шестью степенями свободы</span><span class="sxs-lookup"><span data-stu-id="20bbe-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="20bbe-198">Концепция наведения и фиксации для дальнего взаимодействия была создана и определена для Портала смешанной реальности (MRP).</span><span class="sxs-lookup"><span data-stu-id="20bbe-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="20bbe-199">В этом сценарии пользователь применяет иммерсивную гарнитуру и контроллеры движения для взаимодействия с трехмерными объектами.</span><span class="sxs-lookup"><span data-stu-id="20bbe-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="20bbe-200">Контроллеры движений выпускают лучи для наведения на дальние объекты и манипулирования ими.</span><span class="sxs-lookup"><span data-stu-id="20bbe-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="20bbe-201">На контроллерах есть кнопки для выполнения различных действий.</span><span class="sxs-lookup"><span data-stu-id="20bbe-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="20bbe-202">Мы применяем модель взаимодействия с помощью лучей, прикрепленных к обеим рукам.</span><span class="sxs-lookup"><span data-stu-id="20bbe-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="20bbe-203">При такой симметричной структуре пользователям, знакомым с MRP, не понадобится изучать другую модель взаимодействия для удаленного наведения и манипуляции при использовании HoloLens 2 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="20bbe-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="20bbe-204">![Симметричная структура лучей для контроллеров](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="20bbe-205">**Лучи контроллера**</span><span class="sxs-lookup"><span data-stu-id="20bbe-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20bbe-206">![Симметричная структура лучей для рук](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="20bbe-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="20bbe-207">**Лучи рук**</span><span class="sxs-lookup"><span data-stu-id="20bbe-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="20bbe-208">Телекинез в MRTK (наборе средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="20bbe-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="20bbe-209">По умолчанию в MRTK предоставляется заготовка для телекинеза ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)), которая имеет то же визуальное состояние, что и телекинез в системе оболочки.</span><span class="sxs-lookup"><span data-stu-id="20bbe-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="20bbe-210">Она назначается в профиле ввода данных в MRTK, в разделе "Указатели".</span><span class="sxs-lookup"><span data-stu-id="20bbe-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="20bbe-211">В иммерсивной гарнитуре для контроллеров движений используются такие же лучи.</span><span class="sxs-lookup"><span data-stu-id="20bbe-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="20bbe-212">MRTK — профиль указателя</span><span class="sxs-lookup"><span data-stu-id="20bbe-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="20bbe-213">MRTK — система ввода</span><span class="sxs-lookup"><span data-stu-id="20bbe-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="20bbe-214">MRTK — указатели</span><span class="sxs-lookup"><span data-stu-id="20bbe-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="20bbe-215">См. также</span><span class="sxs-lookup"><span data-stu-id="20bbe-215">See also</span></span>
* [<span data-ttu-id="20bbe-216">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="20bbe-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="20bbe-217">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="20bbe-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="20bbe-218">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="20bbe-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="20bbe-219">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="20bbe-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="20bbe-220">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="20bbe-220">Instinctual interactions</span></span>](interaction-fundamentals.md)