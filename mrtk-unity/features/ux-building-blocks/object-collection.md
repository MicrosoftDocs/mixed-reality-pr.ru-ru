---
title: Коллекция объектов
description: Общие сведения о коллекции объектов в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, коллекция объектов
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177054"
---
# <a name="object-collection"></a><span data-ttu-id="de2b3-104">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-104">Object collection</span></span>

![Коллекция объектов](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="de2b3-106">Коллекция объектов — это скрипт, помогающий разместить массив объектов в предопределенных трехмерных фигурах.</span><span class="sxs-lookup"><span data-stu-id="de2b3-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="de2b3-107">Он поддерживает различные стили поверхности, включая плоскость, цилиндр, шар и радиальный.</span><span class="sxs-lookup"><span data-stu-id="de2b3-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="de2b3-108">Так как он поддерживает любой объект в Unity, он может использоваться для размещения как двумерных, так и трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="de2b3-109">Скрипты коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-109">Object collection scripts</span></span>

- <span data-ttu-id="de2b3-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) поддерживает цилиндры, плоскости, сферы, типы радиальных поверхностей</span><span class="sxs-lookup"><span data-stu-id="de2b3-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="de2b3-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) поддерживает коллекцию с разбросанными стилями</span><span class="sxs-lookup"><span data-stu-id="de2b3-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="de2b3-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) предоставляет некоторые дополнительные параметры для Гридобжектколлектион.</span><span class="sxs-lookup"><span data-stu-id="de2b3-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="de2b3-113">**Примечание.** Тилегридобжектколлектион не расширяется [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) и содержит несколько ошибок (см. [выпуск 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span><span class="sxs-lookup"><span data-stu-id="de2b3-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="de2b3-114">Поэтому рекомендуется использовать [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="de2b3-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Коллекция объектов Grid — цилиндр](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="de2b3-116">Коллекция объектов Grid — цилиндр</span><span class="sxs-lookup"><span data-stu-id="de2b3-116">Grid Object Collection - Cylinder</span></span> | ![Коллекция объектов Grid — сфера](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="de2b3-118">Коллекция объектов Grid — сфера</span><span class="sxs-lookup"><span data-stu-id="de2b3-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Коллекция объектов Grid — радиальная](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="de2b3-120">Коллекция объектов Grid — радиальная</span><span class="sxs-lookup"><span data-stu-id="de2b3-120">Grid Object Collection - Radial</span></span> | ![Коллекция объектов Grid — плоскость](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="de2b3-122">Коллекция объектов Grid — плоскость</span><span class="sxs-lookup"><span data-stu-id="de2b3-122">Grid Object Collection - Plane</span></span> |
|![Коллекция разбросанных объектов](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="de2b3-124">Коллекция разбросанных объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-124">Scattered Object Collection</span></span> | ![Коллекция объектов сетки мозаики](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="de2b3-126">Коллекция объектов сетки мозаики</span><span class="sxs-lookup"><span data-stu-id="de2b3-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="de2b3-127">Использование коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-127">How to use an object collection</span></span>

<span data-ttu-id="de2b3-128">Чтобы создать коллекцию, создайте пустую GameObject и присвойте ей один из скриптов коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="de2b3-129">Любые объекты можно добавить в качестве дочернего элемента для GameObject.</span><span class="sxs-lookup"><span data-stu-id="de2b3-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="de2b3-130">После завершения добавления дочерних объектов нажмите кнопку *обновить коллекцию* на панели инспектора, чтобы создать коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="de2b3-131">Объекты будут размещены в сцене в соответствии с параметрами коллекции.</span><span class="sxs-lookup"><span data-stu-id="de2b3-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="de2b3-132">Доступ к коллекции обновлений можно получить и с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="de2b3-132">Update Collection can be accessed through the code too.</span></span>

![Скрипт коллекции объектов](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="de2b3-134">`GridObjectCollection` выравнивание содержимого</span><span class="sxs-lookup"><span data-stu-id="de2b3-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="de2b3-135">Содержимое в Гридобжектколлектион можно выровнять таким образом, чтобы родительский объект был привязан к верхнему или среднему или нижнему краю, а также по левому центру или правому краю коллекции.</span><span class="sxs-lookup"><span data-stu-id="de2b3-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="de2b3-136">Используйте свойство **Anchor** для указания выравнивания содержимого.</span><span class="sxs-lookup"><span data-stu-id="de2b3-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="de2b3-137">`GridObjectCollection` порядок расположения</span><span class="sxs-lookup"><span data-stu-id="de2b3-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="de2b3-138">Используйте поле **Layout (макет** ), чтобы указать порядок строк или столбцов, в котором размещаются дочерние элементы:</span><span class="sxs-lookup"><span data-stu-id="de2b3-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="de2b3-139">**Строка** — дочерние строки сначала размещаются горизонтально (по столбцу), а затем по вертикали (по строкам).</span><span class="sxs-lookup"><span data-stu-id="de2b3-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="de2b3-140">Для указания числа столбцов в сетке используйте свойство **num Columns** (или свойства Columns в коде).</span><span class="sxs-lookup"><span data-stu-id="de2b3-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Столбец, затем макет строки](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="de2b3-142">**Столбец** — дочерние столбцы сначала размещаются вертикально (по строкам), затем по горизонтали (по столбцам).</span><span class="sxs-lookup"><span data-stu-id="de2b3-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="de2b3-143">Используйте число **строк** (или свойство Rows в коде), чтобы указать количество строк в сетке.</span><span class="sxs-lookup"><span data-stu-id="de2b3-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Строка, затем макет столбца](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="de2b3-145">**Горизонтальные** — дочерние элементы размещаются в одной строке с использованием только столбцов</span><span class="sxs-lookup"><span data-stu-id="de2b3-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="de2b3-146">**По вертикали** — дочерние элементы размещаются в одном столбце только с помощью строк.</span><span class="sxs-lookup"><span data-stu-id="de2b3-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="de2b3-147">Примеры коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-147">Object collection examples</span></span>

<span data-ttu-id="de2b3-148">`ObjectCollectionExamples`Пример сцены (Assets/мртк/examples/демонстрация/UX/Collections/сцены/обжектколлектионексамплес. Unity) содержит различные примеры типов коллекций объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="de2b3-149">[Периодическая таблица элементов](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) — это пример приложения, демонстрирующий работу коллекций объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="de2b3-150">В нем используется коллекция объектов для размещения трехмерных элементов в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="de2b3-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="de2b3-151">Типы коллекций объектов</span><span class="sxs-lookup"><span data-stu-id="de2b3-151">Object collection types</span></span>

<span data-ttu-id="de2b3-152">**Трехмерные объекты**</span><span class="sxs-lookup"><span data-stu-id="de2b3-152">**3D objects**</span></span>

<span data-ttu-id="de2b3-153">Коллекцию объектов можно использовать для разметки импортированных трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="de2b3-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="de2b3-154">В приведенном ниже примере показаны плоскость и цилиндрические макеты объектов модели трехмерного стула с помощью коллекции.</span><span class="sxs-lookup"><span data-stu-id="de2b3-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Объемная коллекция объектов](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="de2b3-156">**Двумерные объекты**</span><span class="sxs-lookup"><span data-stu-id="de2b3-156">**2D Objects**</span></span>

<span data-ttu-id="de2b3-157">Коллекцию объектов также можно создавать из двумерных изображений.</span><span class="sxs-lookup"><span data-stu-id="de2b3-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="de2b3-158">Например, в стиле сетки можно разместить несколько изображений.</span><span class="sxs-lookup"><span data-stu-id="de2b3-158">For example, multiple images can be placed in a grid style.</span></span>

![Двухмерная коллекция объектов](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
