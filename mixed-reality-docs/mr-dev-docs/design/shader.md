---
title: Шейдер
description: Узнайте, как стандартный шейдер набора средств для смешанной реальности предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами в приложениях смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, UI, UX, шейдер, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, визуальные эффекты
ms.openlocfilehash: 046969d1d16c2bddcf5b0a392d721c291b945a94
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759125"
---
# <a name="shader"></a><span data-ttu-id="0fb89-104">Шейдер</span><span class="sxs-lookup"><span data-stu-id="0fb89-104">Shader</span></span>

![Шейдер](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="0fb89-106">Так как holographic объектов вместе с физическими в реальной среде, важно предоставить пользователю визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="0fb89-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="0fb89-107">Стандартный шейдер набора средств Mixed Reality предоставляет различные типы визуальных эффектов для использования с голограммами.</span><span class="sxs-lookup"><span data-stu-id="0fb89-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="0fb89-108">Система заливки использует один гибкий шейдер для достижения визуальных элементов, аналогичных стандартному шейдеру Unity.</span><span class="sxs-lookup"><span data-stu-id="0fb89-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="0fb89-109">Шейдер реализует собственные [принципы разработки системы](https://www.microsoft.com/design/fluent/#/) и продолжает работать на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0fb89-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="0fb89-110">Примеры визуальных эффектов с использованием стандартного шейдера МРТК (набор средств Mixed Reality)</span><span class="sxs-lookup"><span data-stu-id="0fb89-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="0fb89-111">![Перемещение](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="0fb89-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="0fb89-112">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="0fb89-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0fb89-113">![Поворот](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="0fb89-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="0fb89-114">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="0fb89-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="0fb89-115">Стандартный шейдер в МРТК для Unity</span><span class="sxs-lookup"><span data-stu-id="0fb89-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="0fb89-116">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="0fb89-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="0fb89-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0fb89-117">See also</span></span>

* [<span data-ttu-id="0fb89-118">Курсоры</span><span class="sxs-lookup"><span data-stu-id="0fb89-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0fb89-119">Телекинез</span><span class="sxs-lookup"><span data-stu-id="0fb89-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="0fb89-120">Кнопка</span><span class="sxs-lookup"><span data-stu-id="0fb89-120">Button</span></span>](button.md)
* [<span data-ttu-id="0fb89-121">Активный объект</span><span class="sxs-lookup"><span data-stu-id="0fb89-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0fb89-122">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="0fb89-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="0fb89-123">Оперирование</span><span class="sxs-lookup"><span data-stu-id="0fb89-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0fb89-124">Меню руки</span><span class="sxs-lookup"><span data-stu-id="0fb89-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="0fb89-125">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="0fb89-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="0fb89-126">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="0fb89-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="0fb89-127">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="0fb89-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="0fb89-128">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="0fb89-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="0fb89-129">Подсказка</span><span class="sxs-lookup"><span data-stu-id="0fb89-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="0fb89-130">Планшет</span><span class="sxs-lookup"><span data-stu-id="0fb89-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="0fb89-131">Ползунок</span><span class="sxs-lookup"><span data-stu-id="0fb89-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="0fb89-132">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="0fb89-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="0fb89-133">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="0fb89-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="0fb89-134">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="0fb89-134">Surface magnetism</span></span>](surface-magnetism.md)
