---
title: Коллекция объектов
description: Общие сведения о коллекции объектов в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, коллекция объектов
ms.openlocfilehash: d9956ec7069b8351f4493bc50a41498a245a91d1
ms.sourcegitcommit: 3c7d44efd7d7ac02a36e830b28d75fd0e0502349
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2021
ms.locfileid: "130058419"
---
# <a name="object-collection"></a>Коллекция объектов

![Коллекция объектов](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

Коллекция объектов — это скрипт, помогающий разместить массив объектов в предопределенных трехмерных фигурах. Он поддерживает различные стили поверхности, включая плоскость, цилиндр, шар и радиальный. Так как он поддерживает любой объект в Unity, он может использоваться для размещения как двумерных, так и трехмерных объектов.

## <a name="object-collection-scripts"></a>Скрипты коллекции объектов

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) поддерживает цилиндры, плоскости, сферы, типы радиальных поверхностей
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) поддерживает коллекцию с разбросанными стилями  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) предоставляет некоторые дополнительные параметры для Гридобжектколлектион. **Примечание.** Тилегридобжектколлектион не расширяется [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) и содержит несколько ошибок (см. [выпуск 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). Поэтому рекомендуется использовать [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

:::row:::
    :::column:::  
    ![Коллекция объектов Grid — цилиндр](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Коллекция объектов Grid — цилиндр
    :::column-end:::
    :::column:::
    ![Коллекция объектов Grid — сфера](../images/object-collection/MRTK_ObjectCollectionSphere.png) Коллекция объектов Grid — сфера
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Коллекция объектов Grid — радиальная](../images/object-collection/MRTK_ObjectCollectionRadial.png) Коллекция объектов Grid — радиальная
    :::column-end:::
    :::column:::
    ![Коллекция объектов Grid — плоскость](../images/object-collection/MRTK_ObjectCollectionPlane.png) Коллекция объектов Grid — плоскость
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Коллекция разбросанных объектов](../images/object-collection/MRTK_ObjectCollectionScattered.png) Коллекция разбросанных объектов
    :::column-end:::
    :::column:::
    ![Коллекция объектов сетки мозаики](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Коллекция объектов сетки мозаики
    :::column-end:::
:::row-end:::



## <a name="how-to-use-an-object-collection"></a>Использование коллекции объектов

Чтобы создать коллекцию, создайте пустую GameObject и присвойте ей один из скриптов коллекции объектов. Любые объекты можно добавить в качестве дочернего элемента для GameObject. После завершения добавления дочерних объектов нажмите кнопку *обновить коллекцию* на панели инспектора, чтобы создать коллекцию объектов. Объекты будут размещены в сцене в соответствии с параметрами коллекции. Доступ к коллекции обновлений можно получить и с помощью кода.

![Скрипт коллекции объектов](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` выравнивание содержимого

Содержимое в Гридобжектколлектион можно выровнять таким образом, чтобы родительский объект был привязан к верхнему или среднему или нижнему краю, а также по левому центру или правому краю коллекции. Используйте свойство **Anchor** для указания выравнивания содержимого.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` порядок расположения

Используйте поле **Layout (макет** ), чтобы указать порядок строк или столбцов, в котором размещаются дочерние элементы:

**Строка** — дочерние строки сначала размещаются горизонтально (по столбцу), а затем по вертикали (по строкам). Для указания числа столбцов в сетке используйте свойство **num Columns** (или свойства Columns в коде).

![Столбец, затем макет строки](../images/object-collection/MRTK_ColumnThenRow.png)

**Столбец** — дочерние столбцы сначала размещаются вертикально (по строкам), затем по горизонтали (по столбцам). Используйте число **строк** (или свойство Rows в коде), чтобы указать количество строк в сетке.

![Строка, затем макет столбца](../images/object-collection/MRTK_RowThenColumn.png)

**Горизонтальные** — дочерние элементы размещаются в одной строке с использованием только столбцов

**По вертикали** — дочерние элементы размещаются в одном столбце только с помощью строк.

## <a name="object-collection-examples"></a>Примеры коллекции объектов

`ObjectCollectionExamples`Пример сцены (Assets/мртк/examples/демонстрация/UX/Collections/сцены/обжектколлектионексамплес. Unity) содержит различные примеры типов коллекций объектов.

[Периодическая таблица элементов](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) — это пример приложения, демонстрирующий работу коллекций объектов. В нем используется коллекция объектов для размещения трехмерных элементов в различных фигурах.

## <a name="object-collection-types"></a>Типы коллекций объектов

**Трехмерные объекты**

Коллекцию объектов можно использовать для разметки импортированных трехмерных объектов. В приведенном ниже примере показаны плоскость и цилиндрические макеты объектов модели трехмерного стула с помощью коллекции.

![Объемная коллекция объектов](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Двумерные объекты**

Коллекцию объектов также можно создавать из двумерных изображений. Например, в стиле сетки можно разместить несколько изображений.

![Двухмерная коллекция объектов](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
