---
title: Индикация хода выполнения
description: Узнайте, как элементы управления хода выполнения предоставляют отзыв пользователю о выполнении длительной операции в приложениях смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, элементы управления, Пользовательский интерфейс, UX, индикатор выполнения, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600553"
---
# <a name="progress-indicator"></a><span data-ttu-id="33503-104">Индикатор хода выполнения</span><span class="sxs-lookup"><span data-stu-id="33503-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="33503-105">Элемент управления выполнением предоставляет отзыв о выполнении длительной операции.</span><span class="sxs-lookup"><span data-stu-id="33503-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="33503-106">Когда индикатор хода выполнения отображается, пользователи могут видеть время ожидания и не могут взаимодействовать с приложением.</span><span class="sxs-lookup"><span data-stu-id="33503-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="33503-107">Типы хода выполнения</span><span class="sxs-lookup"><span data-stu-id="33503-107">Types of progress</span></span>

<span data-ttu-id="33503-108">Важно предоставить пользователю сведения о том, что происходит.</span><span class="sxs-lookup"><span data-stu-id="33503-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="33503-109">В смешанной реальности пользователи могут легко отвлекаться от физической среды или объектов, если ваше приложение не имеет хорошего визуального отзыва.</span><span class="sxs-lookup"><span data-stu-id="33503-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="33503-110">В ситуациях, которые могут занять несколько секунд, например при загрузке данных или обновлении сцены, рекомендуется отобразить визуальный индикатор.</span><span class="sxs-lookup"><span data-stu-id="33503-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="33503-111">Существует два варианта отображения пользователя, выполняющего операцию — **индикатор выполнения** или **круг хода выполнения**.</span><span class="sxs-lookup"><span data-stu-id="33503-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="33503-112">Индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="33503-112">Progress bar</span></span><br>
        <span data-ttu-id="33503-113">Индикатор выполнения показывает процент завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="33503-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="33503-114">Его следует использовать во время операции, длительность которой известно (прерывается), но ход выполнения не должен блокировать взаимодействие пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="33503-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="33503-115">*Изображение: пример индикатора выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="33503-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="33503-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="33503-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="33503-117">![Пример индикатора выполнения в HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="33503-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="33503-118">Кольцевой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="33503-118">Progress ring</span></span><br>
        <span data-ttu-id="33503-119">Круг выполнения имеет неопределенное состояние, и его следует использовать, когда взаимодействие с пользователем блокируется до завершения операции.</span><span class="sxs-lookup"><span data-stu-id="33503-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="33503-120">*Изображение: пример круга хода выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="33503-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="33503-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="33503-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="33503-122">![Пример круга хода выполнения на устройстве HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="33503-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="33503-123">Ход выполнения с пользовательским объектом</span><span class="sxs-lookup"><span data-stu-id="33503-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="33503-124">Вы можете добавить в свое собственное удостоверение приложения и фирменную символику, настроив управление ходом выполнения с помощью собственных двумерных или трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="33503-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="33503-125">*Изображение: ход выполнения с примером настраиваемой сетки в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="33503-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="33503-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="33503-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="33503-127">![Пример нестандартной сетки в HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="33503-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="33503-128">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="33503-128">Best practices</span></span>

* <span data-ttu-id="33503-129">Тесное связывание [объявления или тега](billboarding-and-tag-along.md) с отображением хода выполнения, так как пользователь может легко переместить свой заголовок в пустое место и потерять контекст.</span><span class="sxs-lookup"><span data-stu-id="33503-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="33503-130">Приложение может выглядеть аварийно, если пользователь не увидит ничего.</span><span class="sxs-lookup"><span data-stu-id="33503-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="33503-131">Всплывающие окна и теги встроены в prefab хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="33503-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="33503-132">Всегда удобно предоставлять сведения о состоянии, что происходит с пользователем.</span><span class="sxs-lookup"><span data-stu-id="33503-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="33503-133">Prefab выполнения предоставляет различные визуальные стили, включая ход выполнения стандартного звонка Windows для предоставления состояния.</span><span class="sxs-lookup"><span data-stu-id="33503-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="33503-134">Вы также можете использовать настраиваемую сетку с анимацией, если хотите, чтобы стиль выполнения совпадал с торговой маркой приложения.</span><span class="sxs-lookup"><span data-stu-id="33503-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="33503-135">Индикатор выполнения в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="33503-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="33503-136">МРТК — индикатор выполнения Prefabs</span><span class="sxs-lookup"><span data-stu-id="33503-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="33503-137">МРТК — служба перехода на сцену</span><span class="sxs-lookup"><span data-stu-id="33503-137">MRTK - Scene transition service</span></span>](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="33503-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="33503-138">See also</span></span>

* [<span data-ttu-id="33503-139">Курсоры</span><span class="sxs-lookup"><span data-stu-id="33503-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="33503-140">Телекинез</span><span class="sxs-lookup"><span data-stu-id="33503-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="33503-141">Кнопка</span><span class="sxs-lookup"><span data-stu-id="33503-141">Button</span></span>](button.md)
* [<span data-ttu-id="33503-142">Активный объект</span><span class="sxs-lookup"><span data-stu-id="33503-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="33503-143">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="33503-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="33503-144">Оперирование</span><span class="sxs-lookup"><span data-stu-id="33503-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="33503-145">Меню руки</span><span class="sxs-lookup"><span data-stu-id="33503-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="33503-146">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="33503-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="33503-147">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="33503-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="33503-148">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="33503-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="33503-149">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="33503-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="33503-150">Подсказка</span><span class="sxs-lookup"><span data-stu-id="33503-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="33503-151">Планшет</span><span class="sxs-lookup"><span data-stu-id="33503-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="33503-152">Ползунок</span><span class="sxs-lookup"><span data-stu-id="33503-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="33503-153">Шейдер</span><span class="sxs-lookup"><span data-stu-id="33503-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="33503-154">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="33503-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="33503-155">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="33503-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="33503-156">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="33503-156">Surface magnetism</span></span>](surface-magnetism.md)