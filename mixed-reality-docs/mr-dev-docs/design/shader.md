---
title: Шейдер
description: Узнайте, как стандартный шейдер набора средств для смешанной реальности предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами в приложениях смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, UI, UX, шейдер, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, визуальные эффекты
ms.openlocfilehash: 9a60c5065ddb5bcf410bb43b318575da50f7ccf8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600183"
---
# <a name="shader"></a><span data-ttu-id="d8898-104">Шейдер</span><span class="sxs-lookup"><span data-stu-id="d8898-104">Shader</span></span>

![Шейдер](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="d8898-106">Так как holographic объектов вместе с физическими в реальной среде, важно предоставить пользователю визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="d8898-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="d8898-107">Стандартный шейдер набора средств Mixed Reality предоставляет различные типы визуальных эффектов для использования с голограммами.</span><span class="sxs-lookup"><span data-stu-id="d8898-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="d8898-108">Система заливки использует один гибкий шейдер для достижения визуальных элементов, аналогичных стандартному шейдеру Unity.</span><span class="sxs-lookup"><span data-stu-id="d8898-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="d8898-109">Шейдер реализует собственные [принципы разработки системы](https://www.microsoft.com/design/fluent/#/) и продолжает работать на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d8898-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="d8898-110">Примеры визуальных эффектов с использованием стандартного шейдера МРТК (набор средств Mixed Reality)</span><span class="sxs-lookup"><span data-stu-id="d8898-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="d8898-111">![Перемещение](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8898-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="d8898-112">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="d8898-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d8898-113">![Поворот](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8898-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="d8898-114">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="d8898-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="d8898-115">Стандартный шейдер в МРТК для Unity</span><span class="sxs-lookup"><span data-stu-id="d8898-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="d8898-116">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="d8898-116">MRTK - Standard shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="d8898-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d8898-117">See also</span></span>

* [<span data-ttu-id="d8898-118">Курсоры</span><span class="sxs-lookup"><span data-stu-id="d8898-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d8898-119">Телекинез</span><span class="sxs-lookup"><span data-stu-id="d8898-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d8898-120">Кнопка</span><span class="sxs-lookup"><span data-stu-id="d8898-120">Button</span></span>](button.md)
* [<span data-ttu-id="d8898-121">Активный объект</span><span class="sxs-lookup"><span data-stu-id="d8898-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d8898-122">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="d8898-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d8898-123">Оперирование</span><span class="sxs-lookup"><span data-stu-id="d8898-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d8898-124">Меню руки</span><span class="sxs-lookup"><span data-stu-id="d8898-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d8898-125">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="d8898-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d8898-126">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="d8898-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d8898-127">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="d8898-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d8898-128">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="d8898-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d8898-129">Подсказка</span><span class="sxs-lookup"><span data-stu-id="d8898-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d8898-130">Планшет</span><span class="sxs-lookup"><span data-stu-id="d8898-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="d8898-131">Ползунок</span><span class="sxs-lookup"><span data-stu-id="d8898-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="d8898-132">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="d8898-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d8898-133">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="d8898-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d8898-134">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="d8898-134">Surface magnetism</span></span>](surface-magnetism.md)