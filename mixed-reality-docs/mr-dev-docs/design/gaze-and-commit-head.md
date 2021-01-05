---
title: Направление головы и фиксация
description: Общие сведения о входной модели "Head-взгляд" и "фиксация".
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, определение целевой платформы, взаимодействие, проектирование, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, цель, фокус, сглаживание
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847885"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="7f4b3-104">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="7f4b3-104">Head-gaze and commit</span></span>

<span data-ttu-id="7f4b3-105">« _Head-взгляд» и «фиксация_ » — это особый случай входной модели « [взгляд» и «фиксация](gaze-and-commit.md) », которая включает в себя целевой объект с направлением заголовка пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="7f4b3-106">Вы можете работать с целевым объектом, используя вторичные входные данные, такие как жесты или команды "выбрать" в воздухе.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="7f4b3-107">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="7f4b3-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7f4b3-108"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="7f4b3-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="7f4b3-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7f4b3-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7f4b3-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7f4b3-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7f4b3-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="7f4b3-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7f4b3-112">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="7f4b3-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="7f4b3-113">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="7f4b3-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="7f4b3-114">✔ Рекомендуется (третий вариант <a href="interaction-fundamentals.md">см. в разделе других возможностей</a>)</span><span class="sxs-lookup"><span data-stu-id="7f4b3-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7f4b3-115">➕ Альтернативный вариант</span><span class="sxs-lookup"><span data-stu-id="7f4b3-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="7f4b3-116">Изменение размера цели и обратная связь</span><span class="sxs-lookup"><span data-stu-id="7f4b3-116">Target sizing and feedback</span></span>

<span data-ttu-id="7f4b3-117">Вектор взгляда Head повторяется, чтобы его можно было использовать для тонкого нацеливания, но часто лучше всего подходит для валовой нацеливания — получения более крупных целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="7f4b3-118">Минимальный размер целевого объекта (от 1 до 1,5 градусов) позволяет успешно выполнять действия пользователя в большинстве сценариев, хотя целевые объекты в 3 градусах часто обеспечивают более высокую скорость.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="7f4b3-119">Размер, на который ориентирован пользователь, фактически является 2D-областью, даже для трехмерных элементов. в зависимости от проекции она должна быть целевой областью.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="7f4b3-120">Предоставление ключевые подсказки о том, что элемент является "активным" (он предназначен для пользователя), очень полезен.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="7f4b3-121">Это может включать использование, такие как видимые эффекты наведения указателя, звуковые элементы или щелчки, а также четкое выравнивание курсора с помощью элемента.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="7f4b3-122">![Оптимальный размер целевого объекта на расстоянии 2 метра](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f4b3-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="7f4b3-123">*Оптимальный размер целевого объекта на 2-м расстоянии*</span><span class="sxs-lookup"><span data-stu-id="7f4b3-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="7f4b3-124">![Пример выделения выбранного взглядом целевого объекта](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f4b3-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="7f4b3-125">*Пример выделения выбранного взглядом целевого объекта*</span><span class="sxs-lookup"><span data-stu-id="7f4b3-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="7f4b3-126">Размещение цели</span><span class="sxs-lookup"><span data-stu-id="7f4b3-126">Target placement</span></span>

<span data-ttu-id="7f4b3-127">Пользователям часто не удается найти элементы пользовательского интерфейса, расположенные слишком высоким или низким в поле зрения.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="7f4b3-128">Большая часть своего внимания заканчивается на областях вокруг основного фокуса, что приблизительно зависит от уровня взгляда.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="7f4b3-129">Размещение большинства целей в приемлемом диапазоне примерно на уровне глаз может исправить ситуацию.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="7f4b3-130">Учитывая, что пользователь может сосредоточиться на относительно небольшой визуальной области в любое время (с упором на интересующую вас концепцию – примерно 10 градусов), группирование элементов пользовательского интерфейса в степень их взаимосвязи может использовать поведение цепочки внимания от элемента к элементу по мере того, как пользователь перемещает свое взгляд в область.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="7f4b3-131">При разработке интерфейса учитывайте возможные значительные отклонения в поле зрения HoloLens и иммерсивной гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="7f4b3-132">![Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f4b3-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="7f4b3-133">*Пример сгруппированных элементов интерфейса для упрощения нацеливания взглядом в Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="7f4b3-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="7f4b3-134">Улучшение поведения выбора цели</span><span class="sxs-lookup"><span data-stu-id="7f4b3-134">Improving targeting behaviors</span></span>

<span data-ttu-id="7f4b3-135">Если целевая цель пользователя может быть определена или приблизительно приближена, может быть полезно принимать почти необработанные попытки взаимодействия, как если бы они были нацелены правильно.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="7f4b3-136">Вот несколько успешных методов, которые могут быть включены в возможности смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="7f4b3-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="7f4b3-137">Стабилизация направления головы ("колодцы гравитации")</span><span class="sxs-lookup"><span data-stu-id="7f4b3-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="7f4b3-138">Этот параметр должен быть включен в большую часть времени или полностью.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="7f4b3-139">Эта методика позволяет устранить естественные колебания и колебании горловины, которые пользователи могут иметь в качестве хорошей передвижения из-за поведения при оформлении и распознавании речи.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="7f4b3-140">Алгоритмы ближайшего звена</span><span class="sxs-lookup"><span data-stu-id="7f4b3-140">Closest link algorithms</span></span>

<span data-ttu-id="7f4b3-141">Эти алгоритмы лучше подходят для областей с разреженным интерактивным содержимым.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="7f4b3-142">Если есть высокая вероятность того, что вы можете определить, с чем пользователь пытался взаимодействовать, можно дополнить его возможностями нацеливания, предполагая определенный уровень намерения.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="7f4b3-143">Действия баккдатинг и постдатинг</span><span class="sxs-lookup"><span data-stu-id="7f4b3-143">Backdating and postdating actions</span></span>

<span data-ttu-id="7f4b3-144">Этот механизм полезен для задач, требующих скорости.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="7f4b3-145">Если пользователь перемещается по ряду нацеливания и манеуверс активации на скорости, целесообразно предположить, что она была определена намеренно.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="7f4b3-146">Кроме того, можно позволить пропущенным шагам работать с целевыми объектами, которые пользователь находил в фокусе немного раньше или немного после нажатия кнопки (50 мс до/после начала работы в ходе раннего тестирования).</span><span class="sxs-lookup"><span data-stu-id="7f4b3-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="7f4b3-147">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="7f4b3-147">Smoothing</span></span>

<span data-ttu-id="7f4b3-148">Этот механизм полезен при контуре перемещения, уменьшая незначительные колебания и вобблес из-за особенностей естественных головных элементов.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="7f4b3-149">При смягчении по контуру движения, плавное изменение размера и расстояния движений, а не со временем.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="7f4b3-150">Магнитность</span><span class="sxs-lookup"><span data-stu-id="7f4b3-150">Magnetism</span></span>

<span data-ttu-id="7f4b3-151">Этот механизм можно рассматривать как более общую версию ближайших алгоритмов связи — Рисование курсора на целевую платформу или простое увеличение хитбоксес, как видимых, так и незаметного, так как пользователи, вероятнее всего, будут использовать знания интерактивного макета, чтобы лучше подходить к намерениям пользователей.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="7f4b3-152">Это может быть мощным для небольших целей.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="7f4b3-153">Закрепление фокуса</span><span class="sxs-lookup"><span data-stu-id="7f4b3-153">Focus stickiness</span></span>

<span data-ttu-id="7f4b3-154">При определении соседних интерактивных элементов, которые следует присвоить, фокус на них обеспечивает сдвиг к элементу, который в настоящий момент находится в фокусе.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="7f4b3-155">Это помогает сократить число неустойчивых переключений фокуса при плавающей точке между двумя элементами с естественным шум.</span><span class="sxs-lookup"><span data-stu-id="7f4b3-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f4b3-156">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7f4b3-156">See also</span></span>

* [<span data-ttu-id="7f4b3-157">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="7f4b3-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="7f4b3-158">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="7f4b3-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7f4b3-159">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="7f4b3-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7f4b3-160">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="7f4b3-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7f4b3-161">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="7f4b3-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7f4b3-162">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="7f4b3-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7f4b3-163">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="7f4b3-163">Voice input</span></span>](voice-input.md)



