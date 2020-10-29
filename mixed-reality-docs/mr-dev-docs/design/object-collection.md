---
title: Коллекция объектов
description: Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, элементы управления, проектирование
ms.openlocfilehash: 5859f7141e8fa0ea27f142981e2cbd05b8da53bf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691604"
---
# <a name="object-collection"></a><span data-ttu-id="64d8c-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="64d8c-104">Object collection</span></span>

![Коллекция объектов, используемая в периодической таблице приложения Elements](images/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="64d8c-106">Коллекция объектов — это элемент управления макета, который помогает размещать массив объектов в предопределенной трехмерной форме.</span><span class="sxs-lookup"><span data-stu-id="64d8c-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="64d8c-107">Он поддерживает различные стили поверхности — **плоскость, цилиндр, шар** и **радиальный** .</span><span class="sxs-lookup"><span data-stu-id="64d8c-107">It supports various surface styles - **plane, cylinder, sphere** and **radial** .</span></span> <span data-ttu-id="64d8c-108">Вы можете настроить радиус и размер объектов, а также пространство между ними.</span><span class="sxs-lookup"><span data-stu-id="64d8c-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="64d8c-109">Коллекция объектов поддерживает любой объект из Unity — как 2D, так и 3D.</span><span class="sxs-lookup"><span data-stu-id="64d8c-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="64d8c-110">В **[наборе средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** мы создали скрипт Unity и примеры, которые помогут создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="64d8c-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="64d8c-111">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="64d8c-111">Object collection examples</span></span>

<span data-ttu-id="64d8c-112">[Периодическая таблица элементов](../develop/unity/periodic-table-of-the-elements.md) — это пример приложения, демонстрирующий работу коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="64d8c-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="64d8c-113">Он использует коллекцию объектов для размещения трехмерных визуальных полей в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="64d8c-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="64d8c-114">![Примеры коллекции объектов, показанные в периодической таблице приложения Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="64d8c-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="64d8c-115">*Примеры коллекции объектов, показанные в периодической таблице примера приложения Elements*</span><span class="sxs-lookup"><span data-stu-id="64d8c-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="64d8c-116">Трехмерные объекты</span><span class="sxs-lookup"><span data-stu-id="64d8c-116">3D objects</span></span>

<span data-ttu-id="64d8c-117">Коллекцию объектов можно использовать для размещения импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="64d8c-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="64d8c-118">В приведенном ниже примере показана плоскость и макет цилиндра для некоторых объектов трехмерного стула.</span><span class="sxs-lookup"><span data-stu-id="64d8c-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="64d8c-119">![Примеры плоскости и цилиндрических макетов трехмерных объектов](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="64d8c-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="64d8c-120">*Примеры плоскости и цилиндрических макетов трехмерных объектов*</span><span class="sxs-lookup"><span data-stu-id="64d8c-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="64d8c-121">Двумерные объекты</span><span class="sxs-lookup"><span data-stu-id="64d8c-121">2D objects</span></span>

<span data-ttu-id="64d8c-122">Также можно использовать 2D-изображения с коллекцией объектов.</span><span class="sxs-lookup"><span data-stu-id="64d8c-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="64d8c-123">В приведенных ниже примерах показано, как можно отобразить 2D-изображения в сетке.</span><span class="sxs-lookup"><span data-stu-id="64d8c-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Пример двумерных изображений с коллекцией объектов](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="64d8c-125">![Пример двумерных изображений с коллекцией объектов](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="64d8c-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="64d8c-126">*Примеры использования коллекции объектов с 2D-изображениями*</span><span class="sxs-lookup"><span data-stu-id="64d8c-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="64d8c-127">Коллекция объектов в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="64d8c-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="64d8c-128">МРТК — коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="64d8c-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="64d8c-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="64d8c-129">See also</span></span>

* [<span data-ttu-id="64d8c-130">Курсоры</span><span class="sxs-lookup"><span data-stu-id="64d8c-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="64d8c-131">Телекинез</span><span class="sxs-lookup"><span data-stu-id="64d8c-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="64d8c-132">Кнопка</span><span class="sxs-lookup"><span data-stu-id="64d8c-132">Button</span></span>](button.md)
* [<span data-ttu-id="64d8c-133">Активный объект</span><span class="sxs-lookup"><span data-stu-id="64d8c-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="64d8c-134">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="64d8c-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="64d8c-135">Оперирование</span><span class="sxs-lookup"><span data-stu-id="64d8c-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="64d8c-136">Меню руки</span><span class="sxs-lookup"><span data-stu-id="64d8c-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="64d8c-137">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="64d8c-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="64d8c-138">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="64d8c-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="64d8c-139">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="64d8c-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="64d8c-140">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="64d8c-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="64d8c-141">Подсказка</span><span class="sxs-lookup"><span data-stu-id="64d8c-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="64d8c-142">Планшет</span><span class="sxs-lookup"><span data-stu-id="64d8c-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="64d8c-143">Ползунок</span><span class="sxs-lookup"><span data-stu-id="64d8c-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="64d8c-144">Шейдер</span><span class="sxs-lookup"><span data-stu-id="64d8c-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="64d8c-145">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="64d8c-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="64d8c-146">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="64d8c-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="64d8c-147">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="64d8c-147">Surface magnetism</span></span>](surface-magnetism.md)
