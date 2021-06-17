---
title: Ограничивающая рамка и панель приложения
description: Панель приложения — это меню уровня объекта, содержащее ряд кнопок, отображаемых на нижней границе границ голограммы.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, панель приложений, ограничивающий прямоугольник, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110096"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="38e72-104">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="38e72-104">Bounding box and App bar</span></span>
<span data-ttu-id="38e72-105">![Это стандартный интерфейс для манипуляций с объектами в смешанной реальности.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="38e72-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="38e72-106">Что такое ограничивающий прямоугольник?</span><span class="sxs-lookup"><span data-stu-id="38e72-106">What is the Bounding box?</span></span>

<span data-ttu-id="38e72-107">Это стандартный интерфейс для манипуляций с объектами в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="38e72-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="38e72-108">Эта функция предоставляет пользователю визуальную подсказку о том, что объект в данный момент является изменяемым.</span><span class="sxs-lookup"><span data-stu-id="38e72-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="38e72-109">В HoloLens 2 ограничивающий прямоугольник работает с непосредственной манипуляцией и реагирует на финжер'с пользователя.</span><span class="sxs-lookup"><span data-stu-id="38e72-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="38e72-110">Он показывает визуальную обратную связь, которая помогает пользователю воспринимать расстояние от объекта.</span><span class="sxs-lookup"><span data-stu-id="38e72-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="38e72-111">Масштабирование объекта</span><span class="sxs-lookup"><span data-stu-id="38e72-111">Scaling an object</span></span><br>
        <span data-ttu-id="38e72-112">Углы ограничивающего прямоугольника указывают пользователю, что объект может масштабироваться.</span><span class="sxs-lookup"><span data-stu-id="38e72-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="38e72-113">Дескрипторы соответствуют широкому понятному шаблону для настройки масштабирования.</span><span class="sxs-lookup"><span data-stu-id="38e72-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="38e72-114">Эта визуальная подсказка отображает общую область объекта, даже если она не видна за пределами режима коррекции.</span><span class="sxs-lookup"><span data-stu-id="38e72-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="38e72-115">Без этой функции объект, привязанный к другому объекту или поверхности, может показаться похожим на пространство, которое не должно быть.</span><span class="sxs-lookup"><span data-stu-id="38e72-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="38e72-116">*Цикл видео: масштабирование объекта через ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="38e72-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="38e72-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="38e72-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="38e72-118">![Точка HoloLens — представление масштабирования объекта через ограничивающий прямоугольник](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="38e72-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="38e72-119">Вращение объекта</span><span class="sxs-lookup"><span data-stu-id="38e72-119">Rotating an object</span></span><br>
        <span data-ttu-id="38e72-120">Вертикальная прямоугольная аффорданцес на краях ограничивающего прямоугольника — это индикаторы вращения.</span><span class="sxs-lookup"><span data-stu-id="38e72-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="38e72-121">Это дает пользователю более точную корректировку по своим голограммам.</span><span class="sxs-lookup"><span data-stu-id="38e72-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="38e72-122">Можно не только настраивать и масштабировать, но и теперь также вращать.</span><span class="sxs-lookup"><span data-stu-id="38e72-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="38e72-123">*Цикл видео: поворот объекта через ограничивающий прямоугольник*</span><span class="sxs-lookup"><span data-stu-id="38e72-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="38e72-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="38e72-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="38e72-125">![Точка HoloLens — вид поворота объекта через ограничивающий прямоугольник](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="38e72-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="38e72-126">Визуальная обратная связь с учетом расположения HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="38e72-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="38e72-127">В HoloLens 2 есть еще одна визуальная подсказка, которая помогает восприятие пользователя.</span><span class="sxs-lookup"><span data-stu-id="38e72-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="38e72-128">Кольцо рядом с ним отображается и масштабируется по мере того, как прокрутка будет ближе к объекту.</span><span class="sxs-lookup"><span data-stu-id="38e72-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="38e72-129">В конечном итоге, если достигнуто нажатое состояние, кольцо будет находиться в точке.</span><span class="sxs-lookup"><span data-stu-id="38e72-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="38e72-130">Этот визуальный подход позволяет пользователю понять, насколько далеко они от объекта.</span><span class="sxs-lookup"><span data-stu-id="38e72-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="38e72-131">*Цикл видео. пример визуальной обратной связи на основе сходства с ограничивающим прямоугольником*</span><span class="sxs-lookup"><span data-stu-id="38e72-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="38e72-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="38e72-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="38e72-133">![Визуальный отзыв о близком к рукой](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="38e72-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="38e72-134">**Сведения о разработке приложений Unity см [. в разделе ограничивающий прямоугольник в наборе средств для смешанной реальности — Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span><span class="sxs-lookup"><span data-stu-id="38e72-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="38e72-135">Что такое панель приложений?</span><span class="sxs-lookup"><span data-stu-id="38e72-135">What is the App bar?</span></span>

<span data-ttu-id="38e72-136">Панель приложения — это меню уровня объекта, которое содержит ряд кнопок, отображаемых на нижней границе границ голограммы.</span><span class="sxs-lookup"><span data-stu-id="38e72-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="38e72-137">Этот шаблон обычно используется, чтобы позволить пользователям удалять и изменять голограммы.</span><span class="sxs-lookup"><span data-stu-id="38e72-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="38e72-138">Панель приложений была разработана в основном как способ управления размещенными объектами в среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="38e72-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="38e72-139">В сочетании с ограничивающим прямоугольником пользователь имеет полный контроль над тем, где и как объекты ориентированы в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="38e72-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="38e72-140">Панель приложений следует за пользователем</span><span class="sxs-lookup"><span data-stu-id="38e72-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="38e72-141">Так как этот шаблон используется с объектами, которые заблокированы в мире, по мере того как пользователь перемещается по объекту, панель приложения всегда будет отображаться на стороне объектов, ближайшей к пользователю.</span><span class="sxs-lookup"><span data-stu-id="38e72-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="38e72-142">Хотя это и не технически ВС, эта функция эффективно достигает того же результата.</span><span class="sxs-lookup"><span data-stu-id="38e72-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="38e72-143">Запрет на положение пользователя в окклуде или блокировать функциональность, которая в противном случае будет доступна из другого расположения в своей среде.</span><span class="sxs-lookup"><span data-stu-id="38e72-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="38e72-144">*Цикл видео. обходится голограмма, следующая панель приложения*</span><span class="sxs-lookup"><span data-stu-id="38e72-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="38e72-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="38e72-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="38e72-146">![Проход вокруг голограммы.</span><span class="sxs-lookup"><span data-stu-id="38e72-146">![Walking around a hologram.</span></span> <span data-ttu-id="38e72-147">Ниже приведена панель приложений.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="38e72-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="38e72-148">Ограничивающий прямоугольник в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="38e72-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="38e72-149">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет скрипты и Prefabs для ограничивающего прямоугольника и панели приложений.</span><span class="sxs-lookup"><span data-stu-id="38e72-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="38e72-150">Ограничивающий прямоугольник можно добавить, назначив скрипт BoundingBox. cs на любой объект.</span><span class="sxs-lookup"><span data-stu-id="38e72-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="38e72-151">МРТК-ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="38e72-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="38e72-152">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="38e72-152">See also</span></span>

* [<span data-ttu-id="38e72-153">Курсоры</span><span class="sxs-lookup"><span data-stu-id="38e72-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="38e72-154">Телекинез</span><span class="sxs-lookup"><span data-stu-id="38e72-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="38e72-155">Кнопка</span><span class="sxs-lookup"><span data-stu-id="38e72-155">Button</span></span>](button.md)
* [<span data-ttu-id="38e72-156">Активный объект</span><span class="sxs-lookup"><span data-stu-id="38e72-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="38e72-157">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="38e72-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="38e72-158">Оперирование</span><span class="sxs-lookup"><span data-stu-id="38e72-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="38e72-159">Меню руки</span><span class="sxs-lookup"><span data-stu-id="38e72-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="38e72-160">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="38e72-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="38e72-161">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="38e72-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="38e72-162">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="38e72-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="38e72-163">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="38e72-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="38e72-164">Подсказка</span><span class="sxs-lookup"><span data-stu-id="38e72-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="38e72-165">Планшет</span><span class="sxs-lookup"><span data-stu-id="38e72-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="38e72-166">Ползунок</span><span class="sxs-lookup"><span data-stu-id="38e72-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="38e72-167">Шейдер</span><span class="sxs-lookup"><span data-stu-id="38e72-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="38e72-168">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="38e72-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="38e72-169">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="38e72-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="38e72-170">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="38e72-170">Surface magnetism</span></span>](surface-magnetism.md)