---
title: Ограничивающий прямоугольник
description: Общие сведения о ограничивающем прямоугольнике в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, ограничивающий прямоугольник
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177539"
---
# <a name="bounding-box"></a>Ограничивающий прямоугольник

![Ограничивающий прямоугольник](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Ограничивающий прямоугольник является устаревшим и заменяется [элементом управления "границы](bounds-control.md)последователя". Используйте [один из вариантов миграции](#migrating-to-bounds-control) для обновления существующих объектов игры.

[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)Скрипт предоставляет базовые функциональные возможности для преобразования объектов в смешанной реальности. Ограничивающий прямоугольник будет отображать куб вокруг голограммы, чтобы указать, что он может взаимодействовать с. Маркеры на углах и краях Куба допускают масштабирование или вращение объекта. Ограничивающий прямоугольник также реагирует на ввод пользователя. в HoloLens 2, например, ограничивающий прямоугольник реагирует на близость пальца, предоставляя визуальную обратную связь для получения расстояния от объекта. Все взаимодействия и визуальные элементы можно легко настроить.

дополнительные сведения см. в разделе [ограничивающий прямоугольник и панель приложений](/windows/mixed-reality/app-bar-and-bounding-box) в Центр разработкие Windows.

## <a name="example-scene"></a>Пример сцены

Примеры конфигураций ограничивающих прямоугольников можно найти в `BoundingBoxExamples` сцене.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Добавление и настройка ограничивающего прямоугольника с помощью инспектора Unity

1. Добавить в объект конфликт Box
2. Назначение `BoundingBox` скрипта объекту
3. Настройка параметров, таких как методы активации (см. раздел [Свойства инспектора](#inspector-properties) ниже).
4. Используемых назначение prefabs и материалов для ограничивающего прямоугольника стиля HoloLens 2 (см. раздел [стили маркеров](#handle-styles) ниже)

> [!NOTE]
> Используйте поле *Переопределение* *целевого объекта* и границ в инспекторе, чтобы назначить определенный объект и конфликтующее значение в объекте с несколькими дочерними компонентами.

![Ограничивающий прямоугольник 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Добавление и настройка ограничивающего прямоугольника в коде

1. Создание экземпляра куба GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Назначение `BoundingBox` скрипта объекту с помощью функции AddComponent<> ()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Настройка параметров (см. раздел [Свойства инспектора](#inspector-properties) ниже)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. Используемых назначьте prefabs и материалы для ограничивающего прямоугольника стиля HoloLens 2. Это по-прежнему требует назначений через инспектор, так как материалы и Prefabs должны загружаться динамически.

> [!NOTE]
> Использование папки "Resources" или [шейдера Unity.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) не рекомендуется искать динамически загружаемые шейдеры, так как в среде выполнения могут отсутствовать перестановки шейдеров.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Пример: Установка минимального, максимального масштаба ограничивающего прямоугольника с помощью Минмаксскалеконстраинт

Чтобы задать минимальный и максимальный масштаб, используйте [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . Минмаксскалеконстраинт также можно использовать для установки минимального и максимального масштаба для [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Пример: Добавление ограничивающего прямоугольника вокруг игрового объекта

Чтобы добавить ограничивающий прямоугольник вокруг объекта, просто добавьте `BoundingBox` в него компонент:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Свойства инспектора

### <a name="target-object"></a>Целевой объект

Это свойство указывает, какой объект будет преобразован с помощью манипуляции ограничивающего прямоугольника. Если объект не задан, то ограничивающий прямоугольник по умолчанию принимает значение объекта Owner.

### <a name="bounds-override"></a>Переопределение границ

Устанавливает блочный объект для вычисления границ объекта.

### <a name="activation-behavior"></a>Поведение при активации

Существует несколько вариантов активации интерфейса ограничивающего прямоугольника.

* *Активировать при запуске*: ограничивающий прямоугольник становится видимым после запуска сцены.
* *Активировать по сходству*: ограничивающий прямоугольник становится видимым, когда накрывающаяся рука близко к объекту.
* *Активировать по указателю*: ограничивающий прямоугольник становится видимым, если он предназначен для указателя типа «рука-Ray».
* *Активировать вручную*: ограничивающий прямоугольник не становится видимым автоматически. Вы можете активировать его вручную с помощью скрипта, обратившись к свойству boundingBox. Active.

### <a name="scale-minimum"></a>Минимум шкалы

Минимальный допустимый масштаб. Это свойство является устаревшим и предпочтительно добавить [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) скрипт. При добавлении этого скрипта минимальный масштаб будет взят из него, а не из ограничивающего прямоугольника.

### <a name="scale-maximum"></a>Максимальный масштаб

Максимально допустимый масштаб. Это свойство является устаревшим и предпочтительно добавить [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) скрипт. Если этот скрипт добавлен, вместо ограничивающего прямоугольника будет получен максимальный масштаб.

### <a name="box-display"></a>Отображение Box

Различные параметры визуализации ограничивающего прямоугольника.

Если для оси плоской диаграммы задано значение *автоматическое сведение*, скрипт не сможет управлять по оси с наименьшим экстентом. Это приводит к созданию двухмерного ограничивающего прямоугольника, который обычно используется для тонких объектов.

### <a name="handles"></a>Маркеры

Можно назначить материал и prefab, чтобы переопределить стиль маркера. Если дескрипторы не назначены, они будут отображаться в стиле по умолчанию.

## <a name="events"></a>События

Ограничивающий прямоугольник предоставляет следующие события. В этом примере эти события используются для воспроизведения звуковых отзывов.

* **Начало** вращения: срабатывает при начале вращения.
* **Поворот завершен**: срабатывает при завершении вращения.
* **Масштабирование начато**: активируется при запуске масштабирования.
* Окончание **масштабирования**: срабатывает при завершении масштабирования.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Стили обработчиков

по умолчанию при простом назначении [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) сценария будет показан дескриптор HoloLens 1-го стиля. чтобы использовать HoloLens 2 дескрипторы стилей, необходимо назначить соответствующие дескрипторы prefabs и материалы.

![Стили маркера ограничивающего прямоугольника](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

ниже приведены prefabs, материалы и значения масштабирования для маркеров ограничивающего прямоугольника стиля HoloLens 2. Этот пример можно найти в `BoundingBoxExamples` сцене.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>дескрипторы (программа установки для стиля HoloLens 2)

* **Обрабатывающий материал**: баундингбоксхандлевхите.
* **Обработано извлеченный материал**: баундингбоксхандлеблуеграббед.
* **Маркер масштабирования prefab**: MRTK_BoundingBox_ScaleHandle. prefab
* MRTK_BoundingBox_ScaleHandle_Slate prefab. prefab на **планшетном маркере масштабирования**.
* **Размер маркера масштабирования**: 0,016 (1.6 cm)
* **Коэффициент масштабирования**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)
* **Маркер вращения prefab**: MRTK_BoundingBox_RotateHandle. prefab
* **Размер маркера вращения**: 0,016
* **Маркер поворота**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)

### <a name="proximity-setup-for-hololens-2-style"></a>близость (программа установки для стиля HoloLens 2)

Отображение и скрытие маркеров с анимацией на основе расстояния от руки. Он имеет двустороннюю анимацию масштабирования.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Активно воздействие на близкое** использование: Включение активации с помощью маркеров с учетом расположения
* **Средний уровень сходства**: расстояние для первого шага масштабирования
* **Обработайте близко близко**: расстояние для второго шага масштабирования
* **Далеко масштаб**: значение масштаба по умолчанию для ресурса-маркера, если руки выходят за пределы диапазона взаимодействия ограничивающего прямоугольника (расстояние, определенное выше с помощью "маркер среднего сходства"). Использовать 0 для скрытия обработчика по умолчанию)
* **Средняя шкала**: значение масштаба ресурса маркера, когда руки находятся в диапазоне взаимодействия ограничивающего прямоугольника (расстояние, определенное выше с помощью маркера близкого сходства). Чтобы отобразить нормальный размер, используйте значение 1.
* **Закрытие шкалы**: масштабирование значения ресурса-маркера, когда руки находятся в диапазоне взаимодействия (расстояние, определенное выше с помощью маркера близкого сходства). Используйте 1. x, чтобы отобразить больший размер)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Создание объекта, перемещаемого с помощью обработчика манипуляции

Ограничивающий прямоугольник можно сочетать с [`ManipulationHandler.cs`](manipulation-handler.md) , чтобы сделать объект перемещаемым с помощью дальнего взаимодействия. Обработчик манипуляции поддерживает как одно, так и два действия. [Отслеживание вручную](../input/hand-tracking.md) можно использовать для взаимодействия с объектом по закрытию.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Чтобы границы ограничивающего прямоугольника могли работать одинаково при перемещении с помощью [`ManipulationHandler`](manipulation-handler.md) дальнего взаимодействия, рекомендуется соединить свои события для *манипуляции, начатой* для  /  *манипуляции* , которые заканчиваются `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` соответственно, как показано на снимке экрана выше.

## <a name="migrating-to-bounds-control"></a>Миграция в элемент управления "границы"

Существующие Prefabs и экземпляры, использующие [ограничивающий прямоугольник](bounding-box.md) , можно обновить до нового элемента управления "границы" через [окно миграции](../tools/migration-window.md) , которое является частью пакета средств мртк.

Для обновления отдельных экземпляров ограничивающего прямоугольника также существует параметр миграции в инспекторе свойств компонента.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
