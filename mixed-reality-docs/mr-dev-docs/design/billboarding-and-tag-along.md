---
title: Биллбординг и закрепление элемента в пространстве
description: Узнайте, как использовать объекты с рекламой, которые всегда ориентированы на себя для пользователя в приложениях смешанной реальности.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Реклама на щитах, пометка, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 48c7aa28217a38c6c226b65a6e16ed7c950cec59
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299889"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="9d84d-104">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="9d84d-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="9d84d-105">Что такое объявление?</span><span class="sxs-lookup"><span data-stu-id="9d84d-105">What is billboarding?</span></span>

<span data-ttu-id="9d84d-106">Объявление — это концепция поведения, которую можно применить к объектам в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9d84d-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="9d84d-107">Объекты с рекламой всегда ориентированы на себя для пользователя.</span><span class="sxs-lookup"><span data-stu-id="9d84d-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="9d84d-108">Текстовые системы и меню — это распространенные варианты использования, где статические объекты, помещаемые в среду пользователя (блокировка по всему миру), в противном случае будут скрыты или нечитаемы при перемещении пользователей.</span><span class="sxs-lookup"><span data-stu-id="9d84d-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="9d84d-109">Объекты с включенным объявлением можно свободно переворачивать в пользовательской среде.</span><span class="sxs-lookup"><span data-stu-id="9d84d-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="9d84d-110">Они также могут быть ограничены одной осью в зависимости от особенностей проектирования.</span><span class="sxs-lookup"><span data-stu-id="9d84d-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="9d84d-111">Не забывайте, что объявленные объекты могут вырезать или окклуде себя, если они слишком близки к другим объектам или в HoloLens, слишком близко к отсканированным областям.</span><span class="sxs-lookup"><span data-stu-id="9d84d-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="9d84d-112">Чтобы избежать этого, подумайте об общем объеме места, которое может создать объект при повороте на оси, включенной для использования в качестве рекламного объявления.</span><span class="sxs-lookup"><span data-stu-id="9d84d-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="9d84d-113">Что такое тег — вместе?</span><span class="sxs-lookup"><span data-stu-id="9d84d-113">What is a tag-along?</span></span>

<span data-ttu-id="9d84d-114">Tag — это понятие поведения, которое можно добавить в голограммы.</span><span class="sxs-lookup"><span data-stu-id="9d84d-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="9d84d-115">Объект, расположенный на теге, пытается остаться в диапазоне, который позволяет пользователю взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="9d84d-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="9d84d-116">![Панель ПИН-кодов HoloLens — это отличный пример принципа работы тега](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9d84d-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="9d84d-117">*Меню Пуск HoloLens — это отличный пример поведения тегов.*</span><span class="sxs-lookup"><span data-stu-id="9d84d-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="9d84d-118">У объектов-тегов есть параметры, которые могут точно настраивать способ их поведения.</span><span class="sxs-lookup"><span data-stu-id="9d84d-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="9d84d-119">Содержимое может находиться в строке пользователя или выходить за него, в то время как пользователь перемещается вокруг своей среды.</span><span class="sxs-lookup"><span data-stu-id="9d84d-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="9d84d-120">При перемещении содержимое попытается остаться в периферийноее пользователя, продвигаясь по краям представления.</span><span class="sxs-lookup"><span data-stu-id="9d84d-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="9d84d-121">Содержимое может быть временно недоступно в зависимости от скорости перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="9d84d-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="9d84d-122">Когда пользователь рассматривает объект на основе тега, он становится более полным.</span><span class="sxs-lookup"><span data-stu-id="9d84d-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="9d84d-123">Содержимое всегда является «кратким», поэтому пользователи никогда не забывают, в каком направлении их содержимого.</span><span class="sxs-lookup"><span data-stu-id="9d84d-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="9d84d-124">С помощью дополнительных параметров можно присоединить к заголовку пользователя объект с тегами, используя резиновую полосу.</span><span class="sxs-lookup"><span data-stu-id="9d84d-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="9d84d-125">Ускорение или замедление приводят к повесу объекта, что делает его более физическим.</span><span class="sxs-lookup"><span data-stu-id="9d84d-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="9d84d-126">Эта пружинное поведение является дополнением, помогающим пользователю создать точную модель с точностью работы тега.</span><span class="sxs-lookup"><span data-stu-id="9d84d-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="9d84d-127">Звук помогает предоставлять другие подсказки о том, когда пользователи имеют объекты в режиме "тег".</span><span class="sxs-lookup"><span data-stu-id="9d84d-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="9d84d-128">Звук должен усилить скорость перемещения; Быстрый переход на новую головку должен обеспечить более заметный звуковой эффект, в то время как при прохождении естественного ускорения звуковые эффекты должны быть минимальными или нет.</span><span class="sxs-lookup"><span data-stu-id="9d84d-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="9d84d-129">Как и в случае с содержимым, заблокированным в голову, объекты-Теги могут доказать или наусеатинг, если они слишком сильно перемещаются в представлении пользователя.</span><span class="sxs-lookup"><span data-stu-id="9d84d-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="9d84d-130">По мере того как пользователь выполнит поиск, он быстро остановится, после чего он покажет, что они были остановлены.</span><span class="sxs-lookup"><span data-stu-id="9d84d-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="9d84d-131">Их баланс информирует о том, что их головной компьютер прекратил свою работу, и их концепция видит остановку мира.</span><span class="sxs-lookup"><span data-stu-id="9d84d-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="9d84d-132">Однако если тег () поддерживает перемещение при остановке пользователя, он может запутать свое значение.</span><span class="sxs-lookup"><span data-stu-id="9d84d-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9d84d-133">Реклама и теги — вместе с МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="9d84d-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="9d84d-134">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет скрипты для поведения на основе объявлений и тегов.</span><span class="sxs-lookup"><span data-stu-id="9d84d-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="9d84d-135">Назначьте скрипт объявления. cs для любого объекта, чтобы добавить поведение объявления и сделать объект всегда лицом к вам.</span><span class="sxs-lookup"><span data-stu-id="9d84d-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="9d84d-136">Чтобы добавить поведение тегов, используйте сценарий Радиалвиев. cs.</span><span class="sxs-lookup"><span data-stu-id="9d84d-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="9d84d-137">Можно настроить различные параметры, например время лерпинг, расстояние и степень.</span><span class="sxs-lookup"><span data-stu-id="9d84d-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="9d84d-138">МРТК-радиальный просмотр решения</span><span class="sxs-lookup"><span data-stu-id="9d84d-138">MRTK - Radial View Solver</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="9d84d-139">МРТК-сценарий для рекламы</span><span class="sxs-lookup"><span data-stu-id="9d84d-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="9d84d-140">См. также</span><span class="sxs-lookup"><span data-stu-id="9d84d-140">See also</span></span>

* [<span data-ttu-id="9d84d-141">Курсоры</span><span class="sxs-lookup"><span data-stu-id="9d84d-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9d84d-142">Телекинез</span><span class="sxs-lookup"><span data-stu-id="9d84d-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9d84d-143">Кнопка</span><span class="sxs-lookup"><span data-stu-id="9d84d-143">Button</span></span>](button.md)
* [<span data-ttu-id="9d84d-144">Активный объект</span><span class="sxs-lookup"><span data-stu-id="9d84d-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9d84d-145">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="9d84d-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9d84d-146">Оперирование</span><span class="sxs-lookup"><span data-stu-id="9d84d-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9d84d-147">Меню руки</span><span class="sxs-lookup"><span data-stu-id="9d84d-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9d84d-148">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="9d84d-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9d84d-149">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="9d84d-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9d84d-150">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="9d84d-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9d84d-151">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="9d84d-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9d84d-152">Подсказка</span><span class="sxs-lookup"><span data-stu-id="9d84d-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9d84d-153">Планшет</span><span class="sxs-lookup"><span data-stu-id="9d84d-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="9d84d-154">Ползунок</span><span class="sxs-lookup"><span data-stu-id="9d84d-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="9d84d-155">Шейдер</span><span class="sxs-lookup"><span data-stu-id="9d84d-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="9d84d-156">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="9d84d-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9d84d-157">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="9d84d-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9d84d-158">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="9d84d-158">Surface magnetism</span></span>](surface-magnetism.md)
