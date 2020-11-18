---
title: Кнопка
description: Кнопка предоставляет пользователю возможность вызвать немедленное действие. Это один из самых базовых компонентов в смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, Пользовательский интерфейс, UX, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, кнопка
ms.openlocfilehash: c5e52bef8604ba4874b7f4b055107ec0db6b3683
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702860"
---
# <a name="button"></a><span data-ttu-id="bc7ad-105">Button</span><span class="sxs-lookup"><span data-stu-id="bc7ad-105">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="bc7ad-107">Кнопка предоставляет пользователю возможность вызвать немедленное действие.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-107">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="bc7ad-108">Это один из самых базовых компонентов в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-108">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="bc7ad-109">В HoloLens 2 кнопка имеет много визуальных подсказок и аффорданцес, чтобы повысить уверенность в взаимодействии пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-109">In HoloLens 2, a button has many visual cues and affordances to increase the user's interaction confidence.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="bc7ad-110">![Перемещение](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc7ad-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="bc7ad-111">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="bc7ad-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc7ad-112">![Поворот](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc7ad-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="bc7ad-113">**Выделение фокуса**</span><span class="sxs-lookup"><span data-stu-id="bc7ad-113">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="bc7ad-114">![Перемещение](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc7ad-114">![Move](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="bc7ad-115">**Сжатие контейнера**</span><span class="sxs-lookup"><span data-stu-id="bc7ad-115">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bc7ad-116">![Поворот](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc7ad-116">![Rotate](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="bc7ad-117">**Импульс на триггере**</span><span class="sxs-lookup"><span data-stu-id="bc7ad-117">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="bc7ad-118">Кнопка в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="bc7ad-118">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="bc7ad-119">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет различные типы кнопок Prefabs.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-119">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="bc7ad-120">Можно найти кнопки в стиле оболочки для HoloLens 2 и HoloLens (1 Gen), а также настроенные примеры.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-120">You can find shell-style buttons for HoloLens 2 and HoloLens (1st gen) as well as customized examples.</span></span> <span data-ttu-id="bc7ad-121">Кнопка HoloLens 2 prefab содержит множество подробных аффорданцес, помогающих повысить уверенность пользователя.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-121">HoloLens 2 button prefab contains a lot of detailed affordances that help improve the user's confidence.</span></span> <span data-ttu-id="bc7ad-122">Он включает выделение на основе близости, сжатие передней части корпуса и импульсный результат для триггера.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-122">It includes proximity-based highlight, compressing front cage, and a pulse effect on trigger.</span></span>

* [<span data-ttu-id="bc7ad-123">Кнопка МРТК</span><span class="sxs-lookup"><span data-stu-id="bc7ad-123">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="bc7ad-124">См. также</span><span class="sxs-lookup"><span data-stu-id="bc7ad-124">See also</span></span>

* [<span data-ttu-id="bc7ad-125">Курсоры</span><span class="sxs-lookup"><span data-stu-id="bc7ad-125">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bc7ad-126">Телекинез</span><span class="sxs-lookup"><span data-stu-id="bc7ad-126">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bc7ad-127">Кнопка</span><span class="sxs-lookup"><span data-stu-id="bc7ad-127">Button</span></span>](button.md)
* [<span data-ttu-id="bc7ad-128">Активный объект</span><span class="sxs-lookup"><span data-stu-id="bc7ad-128">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bc7ad-129">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="bc7ad-129">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bc7ad-130">Оперирование</span><span class="sxs-lookup"><span data-stu-id="bc7ad-130">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bc7ad-131">Меню руки</span><span class="sxs-lookup"><span data-stu-id="bc7ad-131">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bc7ad-132">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="bc7ad-132">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bc7ad-133">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="bc7ad-133">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bc7ad-134">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="bc7ad-134">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bc7ad-135">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="bc7ad-135">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bc7ad-136">Подсказка</span><span class="sxs-lookup"><span data-stu-id="bc7ad-136">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bc7ad-137">Планшет</span><span class="sxs-lookup"><span data-stu-id="bc7ad-137">Slate</span></span>](slate.md)
* [<span data-ttu-id="bc7ad-138">Ползунок</span><span class="sxs-lookup"><span data-stu-id="bc7ad-138">Slider</span></span>](slider.md)
* [<span data-ttu-id="bc7ad-139">Шейдер</span><span class="sxs-lookup"><span data-stu-id="bc7ad-139">Shader</span></span>](shader.md)
* [<span data-ttu-id="bc7ad-140">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="bc7ad-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bc7ad-141">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="bc7ad-141">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bc7ad-142">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="bc7ad-142">Surface magnetism</span></span>](surface-magnetism.md)
