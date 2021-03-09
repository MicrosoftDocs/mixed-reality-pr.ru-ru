---
title: Непосредственное манипулирование руками
description: Сведения о непосредственном управлении, модели ввода, в которой пользователи касаются голограмм непосредственно своими руками.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, взгляд, выбор целевого объекта взглядом, взаимодействие, проектирование, манипулирование руками, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, MRTK, Mixed Reality Toolkit, кнопка, коллайдеры, ограничивающий прямоугольник, двумерные объекты, инстинктивные жесты
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759326"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="e147c-104">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="e147c-104">Direct manipulation with hands</span></span>

![Кнопка](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="e147c-106">Непосредственное манипулирование —это модель ввода, которая предполагает прикосновение к голограммам непосредственно руками.</span><span class="sxs-lookup"><span data-stu-id="e147c-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="e147c-107">Суть этого принципа состоит в том, что объекты ведут себя так же, как в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="e147c-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="e147c-108">Кнопки можно активировать, просто нажимая их, объекты можно выбирать, хватая их, а двумерное содержимое ведет себя как виртуальный сенсорный экран.</span><span class="sxs-lookup"><span data-stu-id="e147c-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="e147c-109">Непосредственное манипулирование основано на возможностях интерфейса, и оно удобно для пользователей.</span><span class="sxs-lookup"><span data-stu-id="e147c-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="e147c-110">Оно не подразумевает символические жесты.</span><span class="sxs-lookup"><span data-stu-id="e147c-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="e147c-111">Все взаимодействия построены вокруг визуального элемента, который вы можете тронуть или схватить.</span><span class="sxs-lookup"><span data-stu-id="e147c-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="e147c-112">Оно считается моделью "ближнего" ввода. Это означает, что непосредственное манипулирование лучше всего использовать для взаимодействия с содержимым, которое находится в пределах досягаемости.</span><span class="sxs-lookup"><span data-stu-id="e147c-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="e147c-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="e147c-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="e147c-114"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="e147c-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="e147c-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e147c-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="e147c-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e147c-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="e147c-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="e147c-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="e147c-118">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="e147c-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="e147c-119">❌ Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="e147c-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="e147c-120">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="e147c-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="e147c-121">➕ Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="e147c-121">➕ Supported.</span></span>  <span data-ttu-id="e147c-122">Для пользовательского интерфейса рекомендуем использовать <a href="point-and-commit.md">наведение и фиксацию с помощью рук</a>.</span><span class="sxs-lookup"><span data-stu-id="e147c-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="e147c-123">Непосредственное манипулирование является основной моделью ввода в HoloLens 2, где используется новая система отслеживания рук.</span><span class="sxs-lookup"><span data-stu-id="e147c-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="e147c-124">Модель ввода также доступна для иммерсивных гарнитур благодаря использованию контроллеров движений, но не рекомендуется в качестве основного средства взаимодействия за рамками манипулирования объектами.</span><span class="sxs-lookup"><span data-stu-id="e147c-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="e147c-125">Непосредственное манипулирование недоступно в HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="e147c-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="e147c-126">Кончик пальца с обратной связью</span><span class="sxs-lookup"><span data-stu-id="e147c-126">Collidable fingertip</span></span>

<span data-ttu-id="e147c-127">На устройстве HoloLens 2 руки пользователя распознаются и интерпретируются как модели скелета левой и правой руки.</span><span class="sxs-lookup"><span data-stu-id="e147c-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="e147c-128">Чтобы реализовать идею прикосновения к голограммам непосредственно с помощью рук, в идеале можно прикрепить пять индикаторов обратной связи к пяти кончикам пальцев каждой скелетной модели руки.</span><span class="sxs-lookup"><span data-stu-id="e147c-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="e147c-129">Однако из-за отсутствия тактильной обратной связи с десятью кончиками пальцев могли возникать неожиданные и непредсказуемые столкновения с голограммами.</span><span class="sxs-lookup"><span data-stu-id="e147c-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="e147c-130">Следовательно, мы предлагаем размещать коллайдер только на каждый указательный палец.</span><span class="sxs-lookup"><span data-stu-id="e147c-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="e147c-131">Кончики указательных пальцев с регистрацией столкновений также можно использовать в качестве активных точек касания для различных жестов с касаниями, при которых участвуют другие пальцы.</span><span class="sxs-lookup"><span data-stu-id="e147c-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="e147c-132">Жесты касания включают в себя нажатие одним пальцем, прикосновение одним пальцем, нажатие двумя пальцами, а также нажатие пятью пальцами, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="e147c-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e147c-133">![Кончик пальца с обратной связью](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="e147c-134">**Кончик пальца с обратной связью**</span><span class="sxs-lookup"><span data-stu-id="e147c-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-135">![Нажатие одним пальцем](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="e147c-136">**Нажатие одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="e147c-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-137">![Касание одним пальцем](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="e147c-138">**Касание одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="e147c-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-139">![Нажатие пятью пальцами](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="e147c-140">**Нажатие пятью пальцами**</span><span class="sxs-lookup"><span data-stu-id="e147c-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="e147c-141">Сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="e147c-141">Sphere collider</span></span>

<span data-ttu-id="e147c-142">Вместо случайной универсальной формы мы предлагаем использовать сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="e147c-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="e147c-143">и визуализировать его, чтобы обеспечить лучшее восприятие ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="e147c-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="e147c-144">Диаметр сферы должен соответствовать толщине указательного пальца, чтобы повысить точность касания.</span><span class="sxs-lookup"><span data-stu-id="e147c-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="e147c-145">Получить переменную толщину пальца будет легче, вызвав API для работы с руками.</span><span class="sxs-lookup"><span data-stu-id="e147c-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="e147c-146">Курсор для кончика пальца</span><span class="sxs-lookup"><span data-stu-id="e147c-146">Fingertip cursor</span></span>

<span data-ttu-id="e147c-147">Помимо рендеринга сферы с регистрацией столкновений для кончика указательного пальца, мы создали продвинутый курсор для кончика пальца, чтобы оптимизировать возможности ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="e147c-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="e147c-148">Это указатель в форме кольца, прикрепленный к кончику указательного пальца.</span><span class="sxs-lookup"><span data-stu-id="e147c-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="e147c-149">По мере приближения он динамически реагирует на цель с точки зрения ориентации и размера, как описано ниже:</span><span class="sxs-lookup"><span data-stu-id="e147c-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="e147c-150">Когда указательный палец приближается к голограмме, курсор всегда параллелен поверхности голограммы и постепенно уменьшается в размере.</span><span class="sxs-lookup"><span data-stu-id="e147c-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="e147c-151">Как только палец касается поверхности, курсор сжимается до точки и создается событие касания.</span><span class="sxs-lookup"><span data-stu-id="e147c-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="e147c-152">Благодаря интерактивной обратной связи пользователи могут достигать высокой точности при выполнении задач ближнего прицеливания, таких как запуск гиперссылки на странице или нажатие кнопки, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="e147c-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="e147c-153">![Курсор для кончика пальца вдали](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="e147c-154">**Курсор для кончика пальца вдали**</span><span class="sxs-lookup"><span data-stu-id="e147c-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-155">![Курсор для кончика пальца близко](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="e147c-156">**Курсор для кончика пальца близко**</span><span class="sxs-lookup"><span data-stu-id="e147c-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-157">![Контакт курсора для кончика пальца](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="e147c-158">**Контакт курсора для кончика пальца**</span><span class="sxs-lookup"><span data-stu-id="e147c-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="e147c-159">Ограничивающая рамка с шейдером приближения</span><span class="sxs-lookup"><span data-stu-id="e147c-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="e147c-160">Для самой голограммы также требуется способность обеспечивать как визуальную, так и звуковую обратную связь, чтобы компенсировать отсутствие тактильной обратной связи.</span><span class="sxs-lookup"><span data-stu-id="e147c-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="e147c-161">Для этого мы придумали концепцию ограничивающей рамки с шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="e147c-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="e147c-162">Ограничивающая рамка — это минимальная объемная область, включающая трехмерный объект.</span><span class="sxs-lookup"><span data-stu-id="e147c-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="e147c-163">Ограничивающая рамка имеет интерактивный механизм визуализации, называемый шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="e147c-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="e147c-164">Поведение шейдера приближения:</span><span class="sxs-lookup"><span data-stu-id="e147c-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e147c-165">![Наведение (издали) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="e147c-166">**Наведение (издали)**</span><span class="sxs-lookup"><span data-stu-id="e147c-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="e147c-167">Когда указательный палец находится в пределах диапазона, указатель кончика пальца проецируется на поверхность ограничивающей рамки.</span><span class="sxs-lookup"><span data-stu-id="e147c-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-168">![Наведение (вблизи) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="e147c-169">**Наведение (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="e147c-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="e147c-170">Когда кончик пальца приближается к поверхности, указатель сжимается.</span><span class="sxs-lookup"><span data-stu-id="e147c-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-171">![Контакт начинается](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="e147c-172">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="e147c-172">**Contact begins**</span></span><br>
       <span data-ttu-id="e147c-173">Как только кончик пальца коснется поверхности, вся ограничивающая рамка изменит цвет или создаст визуальный эффект для индикации состояния касания.</span><span class="sxs-lookup"><span data-stu-id="e147c-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-174">![Контакт завершается](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="e147c-175">**Контакт завершается**</span><span class="sxs-lookup"><span data-stu-id="e147c-175">**Contact ends**</span></span><br>
       <span data-ttu-id="e147c-176">Для усиления визуальной обратной связи касания можно активировать звуковой эффект.</span><span class="sxs-lookup"><span data-stu-id="e147c-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="e147c-177">Нажимаемая кнопка</span><span class="sxs-lookup"><span data-stu-id="e147c-177">Pressable button</span></span>

<span data-ttu-id="e147c-178">Благодаря обратной связи с помощью кончика пальца пользователи могут взаимодействовать с основополагающим компонентом голографического интерфейса — нажимаемой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="e147c-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="e147c-179">Нажимаемая кнопка — это голографическая кнопка, предназначенная для непосредственного нажатия пальцем.</span><span class="sxs-lookup"><span data-stu-id="e147c-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="e147c-180">Опять же, из-за отсутствия тактильной обратной связи нажимаемая кнопка оснащена несколькими механизмами для решения проблем, связанных с тактильной обратной связью.</span><span class="sxs-lookup"><span data-stu-id="e147c-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="e147c-181">Первый механизм — это ограничивающий прямоугольник с шейдером приближения. Этот механизм подробно описан в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="e147c-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="e147c-182">Он служит для того, чтобы пользователи чувствовали приближение и контакт с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="e147c-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="e147c-183">Второй механизм — надавливание.</span><span class="sxs-lookup"><span data-stu-id="e147c-183">The second mechanism is depression.</span></span> <span data-ttu-id="e147c-184">Он создает ощущение нажатия после контакта пальца с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="e147c-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="e147c-185">Механизм обеспечивает перемещение кнопки вплотную к кончику пальца вдоль оси глубины.</span><span class="sxs-lookup"><span data-stu-id="e147c-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="e147c-186">Кнопка может сработать, когда она достигает выбранной глубины (при нажатии) или поднимается (при отпускании) после прохождения через нее.</span><span class="sxs-lookup"><span data-stu-id="e147c-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="e147c-187">Для улучшения обратной связи нужно добавить звуковой эффект, активируемый при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="e147c-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e147c-188">![Нажимаемая кнопка вдали](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="e147c-189">**Палец вдали**</span><span class="sxs-lookup"><span data-stu-id="e147c-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-190">![Нажимаемая кнопка близко](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="e147c-191">**Палец приближается**</span><span class="sxs-lookup"><span data-stu-id="e147c-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-192">![Начинается контакт с нажимаемой кнопкой](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="e147c-193">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="e147c-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-194">![Нажатие нажимаемой кнопки](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="e147c-195">**Нажатие**</span><span class="sxs-lookup"><span data-stu-id="e147c-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="e147c-196">Взаимодействие с двумерным экраном</span><span class="sxs-lookup"><span data-stu-id="e147c-196">2D slate interaction</span></span>

<span data-ttu-id="e147c-197">Двухмерный [экран](slate.md) — это голографический контейнер, используемый для размещения содержимого двухмерных приложений, таких как веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="e147c-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="e147c-198">Концепция для взаимодействия с двумерным экраном с помощью непосредственного манипулирования не отличается от взаимодействия с физическим сенсорным экраном.</span><span class="sxs-lookup"><span data-stu-id="e147c-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="e147c-199">Для взаимодействия с экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="e147c-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e147c-200">![Сенсорный ввод](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="e147c-201">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="e147c-201">**Touch**</span></span><br>
       <span data-ttu-id="e147c-202">Используйте указательный палец, чтобы нажать гиперссылку или кнопку.</span><span class="sxs-lookup"><span data-stu-id="e147c-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-203">![Прокрутка](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="e147c-204">**Прокрутка**</span><span class="sxs-lookup"><span data-stu-id="e147c-204">**Scroll**</span></span><br>
        <span data-ttu-id="e147c-205">Используйте указательный палец для прокрутки содержимого экрана вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="e147c-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-206">![Масштабирование](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="e147c-207">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="e147c-207">**Zoom**</span></span><br>
       <span data-ttu-id="e147c-208">С помощью двух указательных пальцев пользователя можно увеличивать и уменьшать содержимое экрана в соответствии с относительным движением пальцев.</span><span class="sxs-lookup"><span data-stu-id="e147c-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="e147c-209">Для манипуляции самим двумерным экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="e147c-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e147c-210">![Рисунок с функцией захвата и перетаскивания](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="e147c-211">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="e147c-211">**Move**</span></span><br>
       <span data-ttu-id="e147c-212">Поднесите руки к углам и краям, чтобы выявить самые близкие возможности для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="e147c-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="e147c-213">Захватите голографическую панель в верхней части двумерного экрана планшета, что позволит переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="e147c-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-214">![Рисунок с функцией масштабирования](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="e147c-215">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="e147c-215">**Scale**</span></span><br>
        <span data-ttu-id="e147c-216">Захватите возможности для манипуляции и выполните равномерное масштабирование с помощью угловых возможностей.</span><span class="sxs-lookup"><span data-stu-id="e147c-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-217">![Адаптация](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="e147c-218">**Адаптация**</span><span class="sxs-lookup"><span data-stu-id="e147c-218">**Reflow**</span></span><br>
       <span data-ttu-id="e147c-219">Захватите возможности для манипуляции и выполните адаптацию с помощью возможностей граней.</span><span class="sxs-lookup"><span data-stu-id="e147c-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="e147c-220">Манипуляция трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="e147c-220">3D object manipulation</span></span>

<span data-ttu-id="e147c-221">HoloLens 2 позволяет пользователям с помощью рук управлять трехмерными голографическими объектами, применяя ограничивающий прямоугольник к каждому такому объекту.</span><span class="sxs-lookup"><span data-stu-id="e147c-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="e147c-222">Ограничивающая рамка обеспечивает лучшее восприятие глубины благодаря шейдеру приближения.</span><span class="sxs-lookup"><span data-stu-id="e147c-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="e147c-223">С ограничивающей рамкой доступно два подхода для манипулирования трехмерными объектами.</span><span class="sxs-lookup"><span data-stu-id="e147c-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="e147c-224">Манипуляция на основе возможностей</span><span class="sxs-lookup"><span data-stu-id="e147c-224">Affordance-based manipulation</span></span>

<span data-ttu-id="e147c-225">Манипулирование на основе возможностей позволяет манипулировать трехмерным объектом с помощью ограничивающей рамки и возможностей для манипулирования вокруг него.</span><span class="sxs-lookup"><span data-stu-id="e147c-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="e147c-226">![Рисунок с ограничивающим прямоугольником объектов и функцией перемещения](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="e147c-227">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="e147c-227">**Move**</span></span><br>
       <span data-ttu-id="e147c-228">Как только рука пользователя приближается к трехмерному объекту, появляются ограничивающая рамка и ближайшая возможность.</span><span class="sxs-lookup"><span data-stu-id="e147c-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="e147c-229">Пользователи могут захватить ограничивающий прямоугольник, чтобы переместить весь объект.</span><span class="sxs-lookup"><span data-stu-id="e147c-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-230">![Рисунок с пользователем, который захватывает край объекта для поворота](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="e147c-231">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="e147c-231">**Rotate**</span></span><br>
        <span data-ttu-id="e147c-232">Пользователи могут захватить крайние возможности, чтобы выполнить поворот.</span><span class="sxs-lookup"><span data-stu-id="e147c-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-233">![Рисунок с пользователем, который захватывает угол объекта для масштабирования](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="e147c-234">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="e147c-234">**Scale**</span></span><br>
       <span data-ttu-id="e147c-235">Пользователи могут захватить угловые возможности, чтобы выполнить равномерное масштабирование.</span><span class="sxs-lookup"><span data-stu-id="e147c-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="e147c-236">Манипуляция без использования возможностей</span><span class="sxs-lookup"><span data-stu-id="e147c-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="e147c-237">При таком манипулировании возможности не прикрепляются к ограничивающему прямоугольнику.</span><span class="sxs-lookup"><span data-stu-id="e147c-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="e147c-238">Пользователи могут только отобразить ограничивающую рамку, а затем напрямую взаимодействовать с ней.</span><span class="sxs-lookup"><span data-stu-id="e147c-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="e147c-239">Если ограничивающая рамка захватывается одной рукой, перемещение и вращение объекта связаны с движением и ориентацией руки.</span><span class="sxs-lookup"><span data-stu-id="e147c-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="e147c-240">Когда объект хватается двумя руками, пользователи могут переносить, масштабировать и вращать его в соответствии с относительными движениями двух рук.</span><span class="sxs-lookup"><span data-stu-id="e147c-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="e147c-241">Для определенных манипуляций требуется точность.</span><span class="sxs-lookup"><span data-stu-id="e147c-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="e147c-242">Рекомендуется использовать **манипулирование на основе возможностей**, так как оно обеспечивает высокий уровень точности.</span><span class="sxs-lookup"><span data-stu-id="e147c-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="e147c-243">Для гибкого манипулирования мы рекомендуем использовать **манипулирование без использования возможностей**, так как оно позволяет получить мгновенные и забавные эффекты.</span><span class="sxs-lookup"><span data-stu-id="e147c-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="e147c-244">Инстинктивные жесты</span><span class="sxs-lookup"><span data-stu-id="e147c-244">Instinctual gestures</span></span>

<span data-ttu-id="e147c-245">При работе с HoloLens (1-го поколения) мы обучили пользователей нескольким предопределенным жестам, таким как раскрытие ладони и касание.</span><span class="sxs-lookup"><span data-stu-id="e147c-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="e147c-246">В случае с HoloLens 2 мы не просим пользователей запоминать какие-либо символические жесты.</span><span class="sxs-lookup"><span data-stu-id="e147c-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="e147c-247">Все необходимые жесты пользователя, с помощью которых можно взаимодействовать с голограммами и содержимым, являются инстинктивными.</span><span class="sxs-lookup"><span data-stu-id="e147c-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="e147c-248">Способ достижения инстинктивного жеста состоит в том, чтобы побуждать пользователей выполнять жесты на основе дизайна возможностей пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e147c-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="e147c-249">Например, если нам требуется, чтобы пользователь захватил объект или контрольную точку двумя пальцами, объект или контрольная точка должны быть маленькими.</span><span class="sxs-lookup"><span data-stu-id="e147c-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="e147c-250">Если мы хотим, чтобы пользователь захватил элемент пятью пальцами, объект или контрольная точка должны быть относительно большими.</span><span class="sxs-lookup"><span data-stu-id="e147c-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="e147c-251">Аналогично кнопкам, маленькая кнопка потребует от пользователя нажатия одним пальцем.</span><span class="sxs-lookup"><span data-stu-id="e147c-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="e147c-252">Большая кнопка потребует от пользователя нажатия ладонью.</span><span class="sxs-lookup"><span data-stu-id="e147c-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="e147c-253">![Рисунок с пользователем, захватывающем небольшие объекты для перемещения](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="e147c-254">**Маленький объект**</span><span class="sxs-lookup"><span data-stu-id="e147c-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-255">![Рисунок с пользователем, захватывающем объекты среднего размера для перемещения](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="e147c-256">**Средний объект**</span><span class="sxs-lookup"><span data-stu-id="e147c-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e147c-257">![Рисунок с пользователем, захватывающем объекты большого размера для перемещения](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="e147c-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="e147c-258">**Крупный объект**</span><span class="sxs-lookup"><span data-stu-id="e147c-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="e147c-259">Симметричный дизайн для работы с помощью рук и контроллеров с шестью степенями свободы</span><span class="sxs-lookup"><span data-stu-id="e147c-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="e147c-260">Возможно, вы заметили параллели при взаимодействии с помощью рук в дополненной реальности и контроллерами движений в виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="e147c-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="e147c-261">Оба способа ввода можно использовать для выполнения непосредственного манипулирования в соответствующих средах.</span><span class="sxs-lookup"><span data-stu-id="e147c-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="e147c-262">В HoloLens 2 захват и перетаскивание руками на близком расстоянии работает почти так же, как кнопка захвата на контроллерах движения в WMR.</span><span class="sxs-lookup"><span data-stu-id="e147c-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="e147c-263">Это позволяет пользователям лучше понять разницу взаимодействия между двумя платформами и может оказаться полезным, если вы когда-нибудь решите перенести свое приложение из одной из них в другую.</span><span class="sxs-lookup"><span data-stu-id="e147c-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="e147c-264">Оптимизация с помощью отслеживания глаз</span><span class="sxs-lookup"><span data-stu-id="e147c-264">Optimize with eye tracking</span></span>

<span data-ttu-id="e147c-265">Непосредственное манипулирование может показаться магией, если оно работает так, как задумано.</span><span class="sxs-lookup"><span data-stu-id="e147c-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="e147c-266">Но если при любом движении рук непреднамеренно активируется голограмма, это может раздражать.</span><span class="sxs-lookup"><span data-stu-id="e147c-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="e147c-267">Отслеживание глаз потенциально может помочь лучше определить намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="e147c-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="e147c-268">**Если**. Уменьшение непреднамеренного срабатывания ответа на действие манипулирования.</span><span class="sxs-lookup"><span data-stu-id="e147c-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="e147c-269">Отслеживание глаз позволяет лучше понять, что в настоящее время интересует пользователя.</span><span class="sxs-lookup"><span data-stu-id="e147c-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="e147c-270">Например, представьте, что вы читаете голографический (учебный) текст и протягиваете руку, чтобы схватить реальный рабочий инструмент.</span><span class="sxs-lookup"><span data-stu-id="e147c-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="e147c-271">Таким образом вы случайно перемещаете руку над различными интерактивными голографическими кнопками, на которые вы не обращали внимания</span><span class="sxs-lookup"><span data-stu-id="e147c-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="e147c-272">(например, они могут быть вне поля зрения пользователя).</span><span class="sxs-lookup"><span data-stu-id="e147c-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="e147c-273">Если пользователь некоторое время не смотрел на голограмму, но было обнаружено событие касания или захвата, вероятно, взаимодействие не было намеренным.</span><span class="sxs-lookup"><span data-stu-id="e147c-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="e147c-274">**Который элемент**.  Помимо ложноположительных активаций, иногда требуется более совершенное определение голограмм, которые нужно захватить или активировать, так как точная точка пересечения может быть неясной с вашей точки зрения, особенно если несколько голограмм расположены близко друг к другу.</span><span class="sxs-lookup"><span data-stu-id="e147c-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="e147c-275">Хотя отслеживание взгляда в HoloLens 2 имеет ограничение точности определения его направления, оно все равно может быть очень полезно для близких взаимодействий из-за дисбаланса глубины при взаимодействии посредством ввода руками.</span><span class="sxs-lookup"><span data-stu-id="e147c-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="e147c-276">Это означает, что иногда трудно определить, где находится ваша рука (позади или перед голограммой), чтобы, например, точно захватить виджет манипулирования.</span><span class="sxs-lookup"><span data-stu-id="e147c-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="e147c-277">**Где**. Использование информации о том, на что смотрит пользователь, выполняющий быстрые жесты.</span><span class="sxs-lookup"><span data-stu-id="e147c-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="e147c-278">Захватите голограмму и небрежно переместите ее в место назначения.</span><span class="sxs-lookup"><span data-stu-id="e147c-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="e147c-279">Иногда это работает, но быстрое выполнение жестов руками может привести к очень неточному определению направлений.</span><span class="sxs-lookup"><span data-stu-id="e147c-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="e147c-280">Тем не менее, отслеживание глаз может повысить точность жестов.</span><span class="sxs-lookup"><span data-stu-id="e147c-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e147c-281">Манипуляции в MRTK (наборе средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="e147c-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e147c-282">В **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно легко настроить типичное поведение при манипуляции, используя скрипт **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="e147c-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="e147c-283">Благодаря ObjectManipulator можно захватывать и перемещать объекты непосредственно руками или с помощью телекинеза.</span><span class="sxs-lookup"><span data-stu-id="e147c-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="e147c-284">Этот скрипт также поддерживает манипуляции двумя руками для масштабирования и поворота объекта.</span><span class="sxs-lookup"><span data-stu-id="e147c-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="e147c-285">MRTK — манипуляции</span><span class="sxs-lookup"><span data-stu-id="e147c-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a><span data-ttu-id="e147c-286">См. также статью</span><span class="sxs-lookup"><span data-stu-id="e147c-286">See also</span></span>

* [<span data-ttu-id="e147c-287">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="e147c-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e147c-288">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="e147c-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="e147c-289">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="e147c-289">Instinctual interactions</span></span>](interaction-fundamentals.md)