---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, проектирование, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, коллекция объектов, 2D, 3D, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 53ec99b998f1c65fdd3ca8b5d935b43ff0070500
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759155"
---
# <a name="object-collection"></a><span data-ttu-id="19346-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="19346-104">Object collection</span></span>

![Коллекция объектов, используемая в периодической таблице приложения Elements](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="19346-106">Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.</span><span class="sxs-lookup"><span data-stu-id="19346-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="19346-107">Он поддерживает различные стили поверхности — \* \* плоскость, цилиндр, шар и **радиальный**.</span><span class="sxs-lookup"><span data-stu-id="19346-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="19346-108">Вы можете настроить радиус и размер объектов, а также пространство между ними.</span><span class="sxs-lookup"><span data-stu-id="19346-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="19346-109">Коллекция объектов поддерживает любой объект из Unity — как 2D, так и 3D.</span><span class="sxs-lookup"><span data-stu-id="19346-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="19346-110">В **[наборе средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** мы создали скрипт Unity и примеры, которые помогут создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="19346-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="19346-111">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="19346-111">Object collection examples</span></span>

<span data-ttu-id="19346-112">[Периодическая таблица элементов](../develop/unity/periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий работу коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="19346-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="19346-113">Он использует коллекцию объектов для размещения трехмерных визуальных полей в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="19346-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="19346-114">![Примеры коллекции объектов, показанные в периодической таблице приложения Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="19346-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="19346-115">*Примеры коллекции объектов, показанные в периодической таблице примера приложения Elements*</span><span class="sxs-lookup"><span data-stu-id="19346-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="19346-116">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="19346-116">3D objects</span></span>

<span data-ttu-id="19346-117">Коллекцию объектов можно использовать для размещения импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="19346-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="19346-118">В приведенном ниже примере показана плоскость и макет цилиндра для некоторых объектов трехмерного стула.</span><span class="sxs-lookup"><span data-stu-id="19346-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="19346-119">![Примеры плоскости и цилиндрических макетов трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="19346-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="19346-120">*Примеры плоскости и цилиндрических макетов трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="19346-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="19346-121">Двумерные объекты</span><span class="sxs-lookup"><span data-stu-id="19346-121">2D objects</span></span>

<span data-ttu-id="19346-122">Также можно использовать 2D-изображения с коллекцией объектов.</span><span class="sxs-lookup"><span data-stu-id="19346-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="19346-123">В приведенных ниже примерах показано, как можно отобразить 2D-изображения в сетке.</span><span class="sxs-lookup"><span data-stu-id="19346-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример двумерных изображений с коллекцией объектов](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="19346-125">![Примеры использования коллекции объектов с 2D-изображениями](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="19346-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="19346-126">*Примеры использования коллекции объектов с 2D-изображениями*</span><span class="sxs-lookup"><span data-stu-id="19346-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="19346-127">Коллекция объектов в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="19346-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="19346-128">МРТК — коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="19346-128">MRTK - Object collection</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="19346-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="19346-129">See also</span></span>

* [<span data-ttu-id="19346-130">Курсоры</span><span class="sxs-lookup"><span data-stu-id="19346-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="19346-131">Телекинез</span><span class="sxs-lookup"><span data-stu-id="19346-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="19346-132">Кнопка</span><span class="sxs-lookup"><span data-stu-id="19346-132">Button</span></span>](button.md)
* [<span data-ttu-id="19346-133">Активный объект</span><span class="sxs-lookup"><span data-stu-id="19346-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="19346-134">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="19346-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="19346-135">Оперирование</span><span class="sxs-lookup"><span data-stu-id="19346-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="19346-136">Меню руки</span><span class="sxs-lookup"><span data-stu-id="19346-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="19346-137">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="19346-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="19346-138">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="19346-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="19346-139">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="19346-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="19346-140">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="19346-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="19346-141">Подсказка</span><span class="sxs-lookup"><span data-stu-id="19346-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="19346-142">Планшет</span><span class="sxs-lookup"><span data-stu-id="19346-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="19346-143">Ползунок</span><span class="sxs-lookup"><span data-stu-id="19346-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="19346-144">Шейдер</span><span class="sxs-lookup"><span data-stu-id="19346-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="19346-145">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="19346-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="19346-146">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="19346-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="19346-147">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="19346-147">Surface magnetism</span></span>](surface-magnetism.md)
