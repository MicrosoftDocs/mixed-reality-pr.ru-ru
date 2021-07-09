---
title: Непосредственное манипулирование руками
description: Сведения о непосредственном управлении, модели ввода, в которой пользователи касаются голограмм непосредственно своими руками.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, взгляд, выбор целевого объекта взглядом, взаимодействие, проектирование, манипулирование руками, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, MRTK, Mixed Reality Toolkit, кнопка, коллайдеры, ограничивающий прямоугольник, двумерные объекты, инстинктивные жесты
ms.openlocfilehash: 7a689f887bfd358b0d6e0826d41ef409bf887042
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600473"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="29c46-104">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="29c46-104">Direct manipulation with hands</span></span>

![Кнопка](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="29c46-106">Непосредственное манипулирование —это модель ввода, которая предполагает прикосновение к голограммам непосредственно руками.</span><span class="sxs-lookup"><span data-stu-id="29c46-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="29c46-107">Суть этого принципа состоит в том, что объекты ведут себя так же, как в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="29c46-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="29c46-108">Кнопки можно активировать, просто нажимая их, объекты можно выбирать, хватая их, а двумерное содержимое ведет себя как виртуальный сенсорный экран.</span><span class="sxs-lookup"><span data-stu-id="29c46-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="29c46-109">Непосредственное манипулирование основано на возможностях интерфейса, и оно удобно для пользователей.</span><span class="sxs-lookup"><span data-stu-id="29c46-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="29c46-110">Оно не подразумевает символические жесты.</span><span class="sxs-lookup"><span data-stu-id="29c46-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="29c46-111">Все взаимодействия построены вокруг визуального элемента, который вы можете тронуть или схватить.</span><span class="sxs-lookup"><span data-stu-id="29c46-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="29c46-112">Оно считается моделью "ближнего" ввода. Это означает, что непосредственное манипулирование лучше всего использовать для взаимодействия с содержимым, которое находится в пределах досягаемости.</span><span class="sxs-lookup"><span data-stu-id="29c46-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="29c46-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="29c46-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="29c46-114"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="29c46-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="29c46-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="29c46-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="29c46-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="29c46-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="29c46-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="29c46-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="29c46-118">Непосредственное манипулирование руками</span><span class="sxs-lookup"><span data-stu-id="29c46-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="29c46-119">❌ Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="29c46-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="29c46-120">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="29c46-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="29c46-121">➕ Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="29c46-121">➕ Supported.</span></span>  <span data-ttu-id="29c46-122">Для пользовательского интерфейса рекомендуем использовать <a href="point-and-commit.md">наведение и фиксацию с помощью рук</a>.</span><span class="sxs-lookup"><span data-stu-id="29c46-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="29c46-123">Непосредственное манипулирование является основной моделью ввода в HoloLens 2, где используется новая система отслеживания рук.</span><span class="sxs-lookup"><span data-stu-id="29c46-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="29c46-124">Модель ввода также доступна для иммерсивных гарнитур благодаря использованию контроллеров движений, но не рекомендуется в качестве основного средства взаимодействия за рамками манипулирования объектами.</span><span class="sxs-lookup"><span data-stu-id="29c46-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="29c46-125">Непосредственное манипулирование недоступно в HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="29c46-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="29c46-126">Основы отслеживания рук и инстинктивное взаимодействие — демонстрация</span><span class="sxs-lookup"><span data-stu-id="29c46-126">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="29c46-127">Если вы хотите посмотреть, как работает отслеживание головы и взгляда, ознакомьтесь с нашей видеодемонстрацией **Designing Holograms - Head Tracking and Eye Tracking** (Создание голограмм — отслеживание головы и взгляда) ниже.</span><span class="sxs-lookup"><span data-stu-id="29c46-127">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="29c46-128">По завершении продолжите изучать другие темы.</span><span class="sxs-lookup"><span data-stu-id="29c46-128">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="29c46-129">*Это видео из приложения Designing Holograms для HoloLens 2. Скачайте и воспользуйтесь всеми его возможностями [здесь](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="29c46-129">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="collidable-fingertip"></a><span data-ttu-id="29c46-130">Кончик пальца с обратной связью</span><span class="sxs-lookup"><span data-stu-id="29c46-130">Collidable fingertip</span></span>

<span data-ttu-id="29c46-131">На устройстве HoloLens 2 руки пользователя распознаются и интерпретируются как модели скелета левой и правой руки.</span><span class="sxs-lookup"><span data-stu-id="29c46-131">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="29c46-132">Чтобы реализовать идею прикосновения к голограммам непосредственно с помощью рук, в идеале можно прикрепить пять индикаторов обратной связи к пяти кончикам пальцев каждой скелетной модели руки.</span><span class="sxs-lookup"><span data-stu-id="29c46-132">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="29c46-133">Однако из-за отсутствия тактильной обратной связи с десятью кончиками пальцев могли возникать неожиданные и непредсказуемые столкновения с голограммами.</span><span class="sxs-lookup"><span data-stu-id="29c46-133">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="29c46-134">Следовательно, мы предлагаем размещать коллайдер только на каждый указательный палец.</span><span class="sxs-lookup"><span data-stu-id="29c46-134">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="29c46-135">Кончики указательных пальцев с регистрацией столкновений также можно использовать в качестве активных точек касания для различных жестов с касаниями, при которых участвуют другие пальцы.</span><span class="sxs-lookup"><span data-stu-id="29c46-135">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="29c46-136">Жесты касания включают в себя нажатие одним пальцем, прикосновение одним пальцем, нажатие двумя пальцами, а также нажатие пятью пальцами, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="29c46-136">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="29c46-137">![Кончик пальца с обратной связью](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-137">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="29c46-138">**Кончик пальца с обратной связью**</span><span class="sxs-lookup"><span data-stu-id="29c46-138">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-139">![Нажатие одним пальцем](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-139">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="29c46-140">**Нажатие одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="29c46-140">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-141">![Касание одним пальцем](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-141">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="29c46-142">**Касание одним пальцем**</span><span class="sxs-lookup"><span data-stu-id="29c46-142">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-143">![Нажатие пятью пальцами](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-143">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="29c46-144">**Нажатие пятью пальцами**</span><span class="sxs-lookup"><span data-stu-id="29c46-144">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="29c46-145">Сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="29c46-145">Sphere collider</span></span>

<span data-ttu-id="29c46-146">Вместо случайной универсальной формы мы предлагаем использовать сферический индикатор обратной связи</span><span class="sxs-lookup"><span data-stu-id="29c46-146">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="29c46-147">и визуализировать его, чтобы обеспечить лучшее восприятие ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="29c46-147">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="29c46-148">Диаметр сферы должен соответствовать толщине указательного пальца, чтобы повысить точность касания.</span><span class="sxs-lookup"><span data-stu-id="29c46-148">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="29c46-149">Получить переменную толщину пальца будет легче, вызвав API для работы с руками.</span><span class="sxs-lookup"><span data-stu-id="29c46-149">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="29c46-150">Курсор для кончика пальца</span><span class="sxs-lookup"><span data-stu-id="29c46-150">Fingertip cursor</span></span>

<span data-ttu-id="29c46-151">Помимо рендеринга сферы с регистрацией столкновений для кончика указательного пальца, мы создали продвинутый курсор для кончика пальца, чтобы оптимизировать возможности ближнего прицеливания.</span><span class="sxs-lookup"><span data-stu-id="29c46-151">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="29c46-152">Это указатель в форме кольца, прикрепленный к кончику указательного пальца.</span><span class="sxs-lookup"><span data-stu-id="29c46-152">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="29c46-153">По мере приближения он динамически реагирует на цель с точки зрения ориентации и размера, как описано ниже:</span><span class="sxs-lookup"><span data-stu-id="29c46-153">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="29c46-154">Когда указательный палец приближается к голограмме, курсор всегда параллелен поверхности голограммы и постепенно уменьшается в размере.</span><span class="sxs-lookup"><span data-stu-id="29c46-154">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="29c46-155">Как только палец касается поверхности, курсор сжимается до точки и создается событие касания.</span><span class="sxs-lookup"><span data-stu-id="29c46-155">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="29c46-156">Благодаря интерактивной обратной связи пользователи могут достигать высокой точности при выполнении задач ближнего прицеливания, таких как запуск гиперссылки на странице или нажатие кнопки, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="29c46-156">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="29c46-157">![Курсор для кончика пальца вдали](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-157">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="29c46-158">**Курсор для кончика пальца вдали**</span><span class="sxs-lookup"><span data-stu-id="29c46-158">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-159">![Курсор для кончика пальца близко](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-159">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="29c46-160">**Курсор для кончика пальца близко**</span><span class="sxs-lookup"><span data-stu-id="29c46-160">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-161">![Контакт курсора для кончика пальца](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-161">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="29c46-162">**Контакт курсора для кончика пальца**</span><span class="sxs-lookup"><span data-stu-id="29c46-162">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="29c46-163">Ограничивающая рамка с шейдером приближения</span><span class="sxs-lookup"><span data-stu-id="29c46-163">Bounding box with proximity shader</span></span>

<span data-ttu-id="29c46-164">Для самой голограммы также требуется способность обеспечивать как визуальную, так и звуковую обратную связь, чтобы компенсировать отсутствие тактильной обратной связи.</span><span class="sxs-lookup"><span data-stu-id="29c46-164">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="29c46-165">Для этого мы придумали концепцию ограничивающей рамки с шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="29c46-165">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="29c46-166">Ограничивающая рамка — это минимальная объемная область, включающая трехмерный объект.</span><span class="sxs-lookup"><span data-stu-id="29c46-166">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="29c46-167">Ограничивающая рамка имеет интерактивный механизм визуализации, называемый шейдером приближения.</span><span class="sxs-lookup"><span data-stu-id="29c46-167">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="29c46-168">Поведение шейдера приближения:</span><span class="sxs-lookup"><span data-stu-id="29c46-168">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="29c46-169">![Наведение (издали) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-169">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="29c46-170">**Наведение (издали)**</span><span class="sxs-lookup"><span data-stu-id="29c46-170">**Hover (far)**</span></span><br>
       <span data-ttu-id="29c46-171">Когда указательный палец находится в пределах диапазона, указатель кончика пальца проецируется на поверхность ограничивающей рамки.</span><span class="sxs-lookup"><span data-stu-id="29c46-171">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-172">![Наведение (вблизи) с визуальной обратной связью](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-172">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="29c46-173">**Наведение (вблизи)**</span><span class="sxs-lookup"><span data-stu-id="29c46-173">**Hover (near)**</span></span><br>
        <span data-ttu-id="29c46-174">Когда кончик пальца приближается к поверхности, указатель сжимается.</span><span class="sxs-lookup"><span data-stu-id="29c46-174">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-175">![Контакт начинается](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-175">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="29c46-176">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="29c46-176">**Contact begins**</span></span><br>
       <span data-ttu-id="29c46-177">Как только кончик пальца коснется поверхности, вся ограничивающая рамка изменит цвет или создаст визуальный эффект для индикации состояния касания.</span><span class="sxs-lookup"><span data-stu-id="29c46-177">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-178">![Контакт завершается](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-178">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="29c46-179">**Контакт завершается**</span><span class="sxs-lookup"><span data-stu-id="29c46-179">**Contact ends**</span></span><br>
       <span data-ttu-id="29c46-180">Для усиления визуальной обратной связи касания можно активировать звуковой эффект.</span><span class="sxs-lookup"><span data-stu-id="29c46-180">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="29c46-181">Нажимаемая кнопка</span><span class="sxs-lookup"><span data-stu-id="29c46-181">Pressable button</span></span>

<span data-ttu-id="29c46-182">Благодаря обратной связи с помощью кончика пальца пользователи могут взаимодействовать с основополагающим компонентом голографического интерфейса — нажимаемой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="29c46-182">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="29c46-183">Нажимаемая кнопка — это голографическая кнопка, предназначенная для непосредственного нажатия пальцем.</span><span class="sxs-lookup"><span data-stu-id="29c46-183">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="29c46-184">Опять же, из-за отсутствия тактильной обратной связи нажимаемая кнопка оснащена несколькими механизмами для решения проблем, связанных с тактильной обратной связью.</span><span class="sxs-lookup"><span data-stu-id="29c46-184">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="29c46-185">Первый механизм — это ограничивающий прямоугольник с шейдером приближения. Этот механизм подробно описан в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="29c46-185">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="29c46-186">Он служит для того, чтобы пользователи чувствовали приближение и контакт с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="29c46-186">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="29c46-187">Второй механизм — надавливание.</span><span class="sxs-lookup"><span data-stu-id="29c46-187">The second mechanism is depression.</span></span> <span data-ttu-id="29c46-188">Он создает ощущение нажатия после контакта пальца с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="29c46-188">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="29c46-189">Механизм обеспечивает перемещение кнопки вплотную к кончику пальца вдоль оси глубины.</span><span class="sxs-lookup"><span data-stu-id="29c46-189">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="29c46-190">Кнопка может сработать, когда она достигает выбранной глубины (при нажатии) или поднимается (при отпускании) после прохождения через нее.</span><span class="sxs-lookup"><span data-stu-id="29c46-190">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="29c46-191">Для улучшения обратной связи нужно добавить звуковой эффект, активируемый при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="29c46-191">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="29c46-192">![Нажимаемая кнопка вдали](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-192">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="29c46-193">**Палец вдали**</span><span class="sxs-lookup"><span data-stu-id="29c46-193">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-194">![Нажимаемая кнопка близко](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-194">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="29c46-195">**Палец приближается**</span><span class="sxs-lookup"><span data-stu-id="29c46-195">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-196">![Начинается контакт с нажимаемой кнопкой](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-196">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="29c46-197">**Контакт начинается**</span><span class="sxs-lookup"><span data-stu-id="29c46-197">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-198">![Нажатие нажимаемой кнопки](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-198">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="29c46-199">**Нажатие**</span><span class="sxs-lookup"><span data-stu-id="29c46-199">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="29c46-200">Взаимодействие с двумерным экраном</span><span class="sxs-lookup"><span data-stu-id="29c46-200">2D slate interaction</span></span>

<span data-ttu-id="29c46-201">Двухмерный [экран](slate.md) — это голографический контейнер, используемый для размещения содержимого двухмерных приложений, таких как веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="29c46-201">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="29c46-202">Концепция для взаимодействия с двумерным экраном с помощью непосредственного манипулирования не отличается от взаимодействия с физическим сенсорным экраном.</span><span class="sxs-lookup"><span data-stu-id="29c46-202">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="29c46-203">Для взаимодействия с экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="29c46-203">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="29c46-204">![Сенсорный ввод](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-204">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="29c46-205">**Сенсорный ввод**</span><span class="sxs-lookup"><span data-stu-id="29c46-205">**Touch**</span></span><br>
       <span data-ttu-id="29c46-206">Используйте указательный палец, чтобы нажать гиперссылку или кнопку.</span><span class="sxs-lookup"><span data-stu-id="29c46-206">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-207">![Прокрутка](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-207">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="29c46-208">**Прокрутка**</span><span class="sxs-lookup"><span data-stu-id="29c46-208">**Scroll**</span></span><br>
        <span data-ttu-id="29c46-209">Используйте указательный палец для прокрутки содержимого экрана вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="29c46-209">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-210">![Масштабирование](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-210">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="29c46-211">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="29c46-211">**Zoom**</span></span><br>
       <span data-ttu-id="29c46-212">С помощью двух указательных пальцев пользователя можно увеличивать и уменьшать содержимое экрана в соответствии с относительным движением пальцев.</span><span class="sxs-lookup"><span data-stu-id="29c46-212">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="29c46-213">Для манипуляции самим двумерным экраном планшета:</span><span class="sxs-lookup"><span data-stu-id="29c46-213">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="29c46-214">![Рисунок с функцией захвата и перетаскивания](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-214">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="29c46-215">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="29c46-215">**Move**</span></span><br>
       <span data-ttu-id="29c46-216">Поднесите руки к углам и краям, чтобы выявить самые близкие возможности для манипуляции.</span><span class="sxs-lookup"><span data-stu-id="29c46-216">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="29c46-217">Захватите голографическую панель в верхней части двумерного экрана планшета, что позволит переместить весь экран.</span><span class="sxs-lookup"><span data-stu-id="29c46-217">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-218">![Рисунок с функцией масштабирования](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-218">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="29c46-219">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="29c46-219">**Scale**</span></span><br>
        <span data-ttu-id="29c46-220">Захватите возможности для манипуляции и выполните равномерное масштабирование с помощью угловых возможностей.</span><span class="sxs-lookup"><span data-stu-id="29c46-220">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-221">![Адаптация](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-221">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="29c46-222">**Адаптация**</span><span class="sxs-lookup"><span data-stu-id="29c46-222">**Reflow**</span></span><br>
       <span data-ttu-id="29c46-223">Захватите возможности для манипуляции и выполните адаптацию с помощью возможностей граней.</span><span class="sxs-lookup"><span data-stu-id="29c46-223">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="29c46-224">Манипуляция трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="29c46-224">3D object manipulation</span></span>

<span data-ttu-id="29c46-225">HoloLens 2 позволяет пользователям с помощью рук управлять трехмерными голографическими объектами, применяя ограничивающий прямоугольник к каждому такому объекту.</span><span class="sxs-lookup"><span data-stu-id="29c46-225">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="29c46-226">Ограничивающая рамка обеспечивает лучшее восприятие глубины благодаря шейдеру приближения.</span><span class="sxs-lookup"><span data-stu-id="29c46-226">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="29c46-227">С ограничивающей рамкой доступно два подхода для манипулирования трехмерными объектами.</span><span class="sxs-lookup"><span data-stu-id="29c46-227">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="29c46-228">Манипуляция на основе возможностей</span><span class="sxs-lookup"><span data-stu-id="29c46-228">Affordance-based manipulation</span></span>

<span data-ttu-id="29c46-229">Манипулирование на основе возможностей позволяет манипулировать трехмерным объектом с помощью ограничивающей рамки и возможностей для манипулирования вокруг него.</span><span class="sxs-lookup"><span data-stu-id="29c46-229">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="29c46-230">![Рисунок с ограничивающим прямоугольником объектов и функцией перемещения](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-230">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="29c46-231">**Перемещение**</span><span class="sxs-lookup"><span data-stu-id="29c46-231">**Move**</span></span><br>
       <span data-ttu-id="29c46-232">Как только рука пользователя приближается к трехмерному объекту, появляются ограничивающая рамка и ближайшая возможность.</span><span class="sxs-lookup"><span data-stu-id="29c46-232">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="29c46-233">Пользователи могут захватить ограничивающий прямоугольник, чтобы переместить весь объект.</span><span class="sxs-lookup"><span data-stu-id="29c46-233">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-234">![Рисунок с пользователем, который захватывает край объекта для поворота](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-234">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="29c46-235">**Поворот**</span><span class="sxs-lookup"><span data-stu-id="29c46-235">**Rotate**</span></span><br>
        <span data-ttu-id="29c46-236">Пользователи могут захватить крайние возможности, чтобы выполнить поворот.</span><span class="sxs-lookup"><span data-stu-id="29c46-236">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-237">![Рисунок с пользователем, который захватывает угол объекта для масштабирования](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-237">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="29c46-238">**Масштабирование**</span><span class="sxs-lookup"><span data-stu-id="29c46-238">**Scale**</span></span><br>
       <span data-ttu-id="29c46-239">Пользователи могут захватить угловые возможности, чтобы выполнить равномерное масштабирование.</span><span class="sxs-lookup"><span data-stu-id="29c46-239">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="29c46-240">Манипуляция без использования возможностей</span><span class="sxs-lookup"><span data-stu-id="29c46-240">Non-affordance-based manipulation</span></span>

<span data-ttu-id="29c46-241">При таком манипулировании возможности не прикрепляются к ограничивающему прямоугольнику.</span><span class="sxs-lookup"><span data-stu-id="29c46-241">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="29c46-242">Пользователи могут только отобразить ограничивающую рамку, а затем напрямую взаимодействовать с ней.</span><span class="sxs-lookup"><span data-stu-id="29c46-242">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="29c46-243">Если ограничивающая рамка захватывается одной рукой, перемещение и вращение объекта связаны с движением и ориентацией руки.</span><span class="sxs-lookup"><span data-stu-id="29c46-243">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="29c46-244">Когда объект хватается двумя руками, пользователи могут переносить, масштабировать и вращать его в соответствии с относительными движениями двух рук.</span><span class="sxs-lookup"><span data-stu-id="29c46-244">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="29c46-245">Для определенных манипуляций требуется точность.</span><span class="sxs-lookup"><span data-stu-id="29c46-245">Specific manipulation requires precision.</span></span> <span data-ttu-id="29c46-246">Рекомендуется использовать **манипулирование на основе возможностей**, так как оно обеспечивает высокий уровень точности.</span><span class="sxs-lookup"><span data-stu-id="29c46-246">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="29c46-247">Для гибкого манипулирования мы рекомендуем использовать **манипулирование без использования возможностей**, так как оно позволяет получить мгновенные и забавные эффекты.</span><span class="sxs-lookup"><span data-stu-id="29c46-247">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="29c46-248">Инстинктивные жесты</span><span class="sxs-lookup"><span data-stu-id="29c46-248">Instinctual gestures</span></span>

<span data-ttu-id="29c46-249">При работе с HoloLens (1-го поколения) мы обучили пользователей нескольким предопределенным жестам, таким как раскрытие ладони и касание.</span><span class="sxs-lookup"><span data-stu-id="29c46-249">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="29c46-250">В случае с HoloLens 2 мы не просим пользователей запоминать какие-либо символические жесты.</span><span class="sxs-lookup"><span data-stu-id="29c46-250">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="29c46-251">Все необходимые жесты пользователя, с помощью которых можно взаимодействовать с голограммами и содержимым, являются инстинктивными.</span><span class="sxs-lookup"><span data-stu-id="29c46-251">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="29c46-252">Способ достижения инстинктивного жеста состоит в том, чтобы побуждать пользователей выполнять жесты на основе дизайна возможностей пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="29c46-252">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="29c46-253">Например, если нам требуется, чтобы пользователь захватил объект или контрольную точку двумя пальцами, объект или контрольная точка должны быть маленькими.</span><span class="sxs-lookup"><span data-stu-id="29c46-253">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="29c46-254">Если мы хотим, чтобы пользователь захватил элемент пятью пальцами, объект или контрольная точка должны быть относительно большими.</span><span class="sxs-lookup"><span data-stu-id="29c46-254">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="29c46-255">Аналогично кнопкам, маленькая кнопка потребует от пользователя нажатия одним пальцем.</span><span class="sxs-lookup"><span data-stu-id="29c46-255">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="29c46-256">Большая кнопка потребует от пользователя нажатия ладонью.</span><span class="sxs-lookup"><span data-stu-id="29c46-256">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="29c46-257">![Рисунок с пользователем, захватывающем небольшие объекты для перемещения](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-257">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="29c46-258">**Маленький объект**</span><span class="sxs-lookup"><span data-stu-id="29c46-258">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-259">![Рисунок с пользователем, захватывающем объекты среднего размера для перемещения](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-259">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="29c46-260">**Средний объект**</span><span class="sxs-lookup"><span data-stu-id="29c46-260">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29c46-261">![Рисунок с пользователем, захватывающем объекты большого размера для перемещения](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="29c46-261">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="29c46-262">**Крупный объект**</span><span class="sxs-lookup"><span data-stu-id="29c46-262">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="29c46-263">Симметричный дизайн для работы с помощью рук и контроллеров с шестью степенями свободы</span><span class="sxs-lookup"><span data-stu-id="29c46-263">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="29c46-264">Возможно, вы заметили параллели при взаимодействии с помощью рук в дополненной реальности и контроллерами движений в виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="29c46-264">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="29c46-265">Оба способа ввода можно использовать для выполнения непосредственного манипулирования в соответствующих средах.</span><span class="sxs-lookup"><span data-stu-id="29c46-265">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="29c46-266">В HoloLens 2 захват и перетаскивание руками на близком расстоянии работает почти так же, как кнопка захвата на контроллерах движения в WMR.</span><span class="sxs-lookup"><span data-stu-id="29c46-266">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="29c46-267">Это позволяет пользователям лучше понять разницу взаимодействия между двумя платформами и может оказаться полезным, если вы когда-нибудь решите перенести свое приложение из одной из них в другую.</span><span class="sxs-lookup"><span data-stu-id="29c46-267">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="29c46-268">Оптимизация с помощью отслеживания глаз</span><span class="sxs-lookup"><span data-stu-id="29c46-268">Optimize with eye tracking</span></span>

<span data-ttu-id="29c46-269">Непосредственное манипулирование может показаться магией, если оно работает так, как задумано.</span><span class="sxs-lookup"><span data-stu-id="29c46-269">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="29c46-270">Но если при любом движении рук непреднамеренно активируется голограмма, это может раздражать.</span><span class="sxs-lookup"><span data-stu-id="29c46-270">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="29c46-271">Отслеживание глаз потенциально может помочь лучше определить намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="29c46-271">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="29c46-272">**Если**. Уменьшение непреднамеренного срабатывания ответа на действие манипулирования.</span><span class="sxs-lookup"><span data-stu-id="29c46-272">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="29c46-273">Отслеживание глаз позволяет лучше понять, что в настоящее время интересует пользователя.</span><span class="sxs-lookup"><span data-stu-id="29c46-273">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="29c46-274">Например, представьте, что вы читаете голографический (учебный) текст и протягиваете руку, чтобы схватить реальный рабочий инструмент.</span><span class="sxs-lookup"><span data-stu-id="29c46-274">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="29c46-275">Таким образом вы случайно перемещаете руку над различными интерактивными голографическими кнопками, на которые вы не обращали внимания</span><span class="sxs-lookup"><span data-stu-id="29c46-275">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="29c46-276">(например, они могут быть вне поля зрения пользователя).</span><span class="sxs-lookup"><span data-stu-id="29c46-276">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="29c46-277">Если пользователь некоторое время не смотрел на голограмму, но было обнаружено событие касания или захвата, вероятно, взаимодействие не было намеренным.</span><span class="sxs-lookup"><span data-stu-id="29c46-277">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="29c46-278">**Который элемент**.  Помимо ложноположительных активаций, иногда требуется более совершенное определение голограмм, которые нужно захватить или активировать, так как точная точка пересечения может быть неясной с вашей точки зрения, особенно если несколько голограмм расположены близко друг к другу.</span><span class="sxs-lookup"><span data-stu-id="29c46-278">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="29c46-279">Хотя отслеживание взгляда в HoloLens 2 имеет ограничение точности определения его направления, оно все равно может быть очень полезно для близких взаимодействий из-за дисбаланса глубины при взаимодействии посредством ввода руками.</span><span class="sxs-lookup"><span data-stu-id="29c46-279">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="29c46-280">Это означает, что иногда трудно определить, где находится ваша рука (позади или перед голограммой), чтобы, например, точно захватить виджет манипулирования.</span><span class="sxs-lookup"><span data-stu-id="29c46-280">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="29c46-281">**Где**. Использование информации о том, на что смотрит пользователь, выполняющий быстрые жесты.</span><span class="sxs-lookup"><span data-stu-id="29c46-281">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="29c46-282">Захватите голограмму и небрежно переместите ее в место назначения.</span><span class="sxs-lookup"><span data-stu-id="29c46-282">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="29c46-283">Иногда это работает, но быстрое выполнение жестов руками может привести к очень неточному определению направлений.</span><span class="sxs-lookup"><span data-stu-id="29c46-283">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="29c46-284">Тем не менее, отслеживание глаз может повысить точность жестов.</span><span class="sxs-lookup"><span data-stu-id="29c46-284">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="29c46-285">Манипуляции в MRTK (наборе средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="29c46-285">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="29c46-286">В **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно легко настроить типичное поведение при манипуляции, используя скрипт **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="29c46-286">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="29c46-287">Благодаря ObjectManipulator можно захватывать и перемещать объекты непосредственно руками или с помощью телекинеза.</span><span class="sxs-lookup"><span data-stu-id="29c46-287">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="29c46-288">Этот скрипт также поддерживает манипуляции двумя руками для масштабирования и поворота объекта.</span><span class="sxs-lookup"><span data-stu-id="29c46-288">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="29c46-289">MRTK — манипуляции</span><span class="sxs-lookup"><span data-stu-id="29c46-289">MRTK - Manipulation</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="29c46-290">См. также статью</span><span class="sxs-lookup"><span data-stu-id="29c46-290">See also</span></span>

* [<span data-ttu-id="29c46-291">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="29c46-291">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="29c46-292">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="29c46-292">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="29c46-293">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="29c46-293">Instinctual interactions</span></span>](interaction-fundamentals.md)