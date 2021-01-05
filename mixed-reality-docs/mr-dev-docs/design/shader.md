---
title: Шейдер
description: Стандартный шейдер набора средств для смешанной реальности предоставляет различные типы визуальных эффектов, которые можно использовать с голограммами.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Смешанная реальность, элементы управления, взаимодействие, UI, UX, шейдер, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, визуальные эффекты
ms.openlocfilehash: 08701fb48d633f7de75b74b5e44655c3a01fade8
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848243"
---
# <a name="shader"></a><span data-ttu-id="7704e-104">Шейдер</span><span class="sxs-lookup"><span data-stu-id="7704e-104">Shader</span></span>

![Шейдер](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="7704e-106">Так как holographic объектов вместе с физическими в реальной среде, важно предоставить пользователю визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="7704e-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="7704e-107">Стандартный шейдер набора средств Mixed Reality предоставляет различные типы визуальных эффектов для использования с голограммами.</span><span class="sxs-lookup"><span data-stu-id="7704e-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="7704e-108">Система заливки использует один гибкий шейдер для достижения визуальных элементов, аналогичных стандартному шейдеру Unity.</span><span class="sxs-lookup"><span data-stu-id="7704e-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="7704e-109">Шейдер реализует собственные [принципы разработки системы](https://www.microsoft.com/design/fluent/#/) и продолжает работать на устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7704e-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="7704e-110">Примеры визуальных эффектов с использованием стандартного шейдера МРТК (набор средств Mixed Reality)</span><span class="sxs-lookup"><span data-stu-id="7704e-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="7704e-111">![Перемещение](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7704e-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="7704e-112">**Неблизкое освещение**</span><span class="sxs-lookup"><span data-stu-id="7704e-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7704e-113">![Поворот](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7704e-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="7704e-114">**Источник границы**</span><span class="sxs-lookup"><span data-stu-id="7704e-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="7704e-115">Стандартный шейдер в МРТК для Unity</span><span class="sxs-lookup"><span data-stu-id="7704e-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="7704e-116">МРТК — Стандартный шейдер</span><span class="sxs-lookup"><span data-stu-id="7704e-116">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="7704e-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7704e-117">See also</span></span>

* [<span data-ttu-id="7704e-118">Курсоры</span><span class="sxs-lookup"><span data-stu-id="7704e-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7704e-119">Телекинез</span><span class="sxs-lookup"><span data-stu-id="7704e-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="7704e-120">Кнопка</span><span class="sxs-lookup"><span data-stu-id="7704e-120">Button</span></span>](button.md)
* [<span data-ttu-id="7704e-121">Активный объект</span><span class="sxs-lookup"><span data-stu-id="7704e-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="7704e-122">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="7704e-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7704e-123">Оперирование</span><span class="sxs-lookup"><span data-stu-id="7704e-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7704e-124">Меню руки</span><span class="sxs-lookup"><span data-stu-id="7704e-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="7704e-125">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="7704e-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="7704e-126">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="7704e-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7704e-127">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="7704e-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="7704e-128">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="7704e-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="7704e-129">Подсказка</span><span class="sxs-lookup"><span data-stu-id="7704e-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="7704e-130">Планшет</span><span class="sxs-lookup"><span data-stu-id="7704e-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="7704e-131">Ползунок</span><span class="sxs-lookup"><span data-stu-id="7704e-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="7704e-132">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="7704e-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="7704e-133">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="7704e-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="7704e-134">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="7704e-134">Surface magnetism</span></span>](surface-magnetism.md)
