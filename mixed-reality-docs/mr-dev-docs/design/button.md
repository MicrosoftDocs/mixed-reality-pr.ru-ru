---
title: Кнопка
description: Узнайте, как запустить немедленное действие с кнопками, которые являются одним из базовых компонентов смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, кнопка
ms.openlocfilehash: 9e4d0637d8c10c3cd23bd2ee1369fd57137af795
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759430"
---
# <a name="button"></a><span data-ttu-id="4d2a5-104">Button</span><span class="sxs-lookup"><span data-stu-id="4d2a5-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="4d2a5-106">Кнопка позволяет пользователям запускать немедленные действия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4d2a5-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="4d2a5-107">В HoloLens 2 кнопки имеют визуальные подсказки и аффорданцес, помогающие повысить степень взаимодействия с пользователями.</span><span class="sxs-lookup"><span data-stu-id="4d2a5-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="4d2a5-108">![Кнопка с отображаемым рядом эффектов](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d2a5-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="4d2a5-109">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="4d2a5-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4d2a5-110">![Кнопка, выбранная с отображаемым результатом выделения фокуса](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d2a5-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="4d2a5-111">**Выделение фокуса**</span><span class="sxs-lookup"><span data-stu-id="4d2a5-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="4d2a5-112">![Нажатая кнопка с показанным эффектов сжатия](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d2a5-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="4d2a5-113">**Сжатие контейнера**</span><span class="sxs-lookup"><span data-stu-id="4d2a5-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4d2a5-114">![Нажатая кнопка с показанным импульсом триггера](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d2a5-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="4d2a5-115">**Импульс на триггере**</span><span class="sxs-lookup"><span data-stu-id="4d2a5-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="4d2a5-116">Кнопка в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="4d2a5-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="4d2a5-117">**[Мртк для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет различные типы кнопок Prefabs, включая кнопки в стиле оболочки для hololens 2 и hololens (1-й общий).</span><span class="sxs-lookup"><span data-stu-id="4d2a5-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="4d2a5-118">Кнопка HoloLens 2 prefab содержит несколько подробных аффорданцес, помогающих повысить уверенность пользователей:</span><span class="sxs-lookup"><span data-stu-id="4d2a5-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="4d2a5-119">Выделение на основе близости</span><span class="sxs-lookup"><span data-stu-id="4d2a5-119">Proximity-based highlight</span></span>
* <span data-ttu-id="4d2a5-120">Сжатие передней части корпуса</span><span class="sxs-lookup"><span data-stu-id="4d2a5-120">Compressing front cage</span></span>
* <span data-ttu-id="4d2a5-121">Импульсный результат для триггера.</span><span class="sxs-lookup"><span data-stu-id="4d2a5-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="4d2a5-122">Чтобы получить дополнительные инструкции и настраиваемые примеры, ознакомьтесь с [мртк-кнопкой](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) .</span><span class="sxs-lookup"><span data-stu-id="4d2a5-122">Check out the [MRTK - Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="4d2a5-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4d2a5-123">See also</span></span>

* [<span data-ttu-id="4d2a5-124">Курсоры</span><span class="sxs-lookup"><span data-stu-id="4d2a5-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4d2a5-125">Телекинез</span><span class="sxs-lookup"><span data-stu-id="4d2a5-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4d2a5-126">Кнопка</span><span class="sxs-lookup"><span data-stu-id="4d2a5-126">Button</span></span>](button.md)
* [<span data-ttu-id="4d2a5-127">Активный объект</span><span class="sxs-lookup"><span data-stu-id="4d2a5-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4d2a5-128">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="4d2a5-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4d2a5-129">Оперирование</span><span class="sxs-lookup"><span data-stu-id="4d2a5-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4d2a5-130">Меню руки</span><span class="sxs-lookup"><span data-stu-id="4d2a5-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4d2a5-131">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="4d2a5-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4d2a5-132">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="4d2a5-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4d2a5-133">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="4d2a5-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4d2a5-134">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="4d2a5-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4d2a5-135">Подсказка</span><span class="sxs-lookup"><span data-stu-id="4d2a5-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4d2a5-136">Планшет</span><span class="sxs-lookup"><span data-stu-id="4d2a5-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="4d2a5-137">Ползунок</span><span class="sxs-lookup"><span data-stu-id="4d2a5-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="4d2a5-138">Шейдер</span><span class="sxs-lookup"><span data-stu-id="4d2a5-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="4d2a5-139">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="4d2a5-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4d2a5-140">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="4d2a5-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4d2a5-141">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="4d2a5-141">Surface magnetism</span></span>](surface-magnetism.md)
