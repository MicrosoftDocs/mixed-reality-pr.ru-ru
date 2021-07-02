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
# <a name="bounding-box"></a><span data-ttu-id="e2ab0-104">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="e2ab0-104">Bounding box</span></span>

![Ограничивающий прямоугольник](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="e2ab0-106">Ограничивающий прямоугольник является устаревшим и заменяется [элементом управления "границы](bounds-control.md)последователя".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="e2ab0-107">Используйте [один из вариантов миграции](#migrating-to-bounds-control) для обновления существующих объектов игры.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="e2ab0-108">[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)Скрипт предоставляет базовые функциональные возможности для преобразования объектов в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="e2ab0-109">Ограничивающий прямоугольник будет отображать куб вокруг голограммы, чтобы указать, что он может взаимодействовать с.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="e2ab0-110">Маркеры на углах и краях Куба допускают масштабирование или вращение объекта.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="e2ab0-111">Ограничивающий прямоугольник также реагирует на ввод пользователя.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="e2ab0-112">в HoloLens 2, например, ограничивающий прямоугольник реагирует на близость пальца, предоставляя визуальную обратную связь для получения расстояния от объекта.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="e2ab0-113">Все взаимодействия и визуальные элементы можно легко настроить.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="e2ab0-114">дополнительные сведения см. в разделе [ограничивающий прямоугольник и панель приложений](/windows/mixed-reality/app-bar-and-bounding-box) в Центр разработкие Windows.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="e2ab0-115">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="e2ab0-115">Example scene</span></span>

<span data-ttu-id="e2ab0-116">Примеры конфигураций ограничивающих прямоугольников можно найти в `BoundingBoxExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="e2ab0-117">Добавление и настройка ограничивающего прямоугольника с помощью инспектора Unity</span><span class="sxs-lookup"><span data-stu-id="e2ab0-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="e2ab0-118">Добавить в объект конфликт Box</span><span class="sxs-lookup"><span data-stu-id="e2ab0-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="e2ab0-119">Назначение `BoundingBox` скрипта объекту</span><span class="sxs-lookup"><span data-stu-id="e2ab0-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="e2ab0-120">Настройка параметров, таких как методы активации (см. раздел [Свойства инспектора](#inspector-properties) ниже).</span><span class="sxs-lookup"><span data-stu-id="e2ab0-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="e2ab0-121">Используемых назначение prefabs и материалов для ограничивающего прямоугольника стиля HoloLens 2 (см. раздел [стили маркеров](#handle-styles) ниже)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="e2ab0-122">Используйте поле *Переопределение* *целевого объекта* и границ в инспекторе, чтобы назначить определенный объект и конфликтующее значение в объекте с несколькими дочерними компонентами.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Ограничивающий прямоугольник 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="e2ab0-124">Добавление и настройка ограничивающего прямоугольника в коде</span><span class="sxs-lookup"><span data-stu-id="e2ab0-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="e2ab0-125">Создание экземпляра куба GameObject</span><span class="sxs-lookup"><span data-stu-id="e2ab0-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="e2ab0-126">Назначение `BoundingBox` скрипта объекту с помощью функции AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="e2ab0-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="e2ab0-127">Настройка параметров (см. раздел [Свойства инспектора](#inspector-properties) ниже)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="e2ab0-128">Используемых назначьте prefabs и материалы для ограничивающего прямоугольника стиля HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="e2ab0-129">Это по-прежнему требует назначений через инспектор, так как материалы и Prefabs должны загружаться динамически.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="e2ab0-130">Использование папки "Resources" или [шейдера Unity.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) не рекомендуется искать динамически загружаемые шейдеры, так как в среде выполнения могут отсутствовать перестановки шейдеров.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="e2ab0-131">Пример: Установка минимального, максимального масштаба ограничивающего прямоугольника с помощью Минмаксскалеконстраинт</span><span class="sxs-lookup"><span data-stu-id="e2ab0-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="e2ab0-132">Чтобы задать минимальный и максимальный масштаб, используйте [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="e2ab0-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="e2ab0-133">Минмаксскалеконстраинт также можно использовать для установки минимального и максимального масштаба для [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="e2ab0-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="e2ab0-134">Пример: Добавление ограничивающего прямоугольника вокруг игрового объекта</span><span class="sxs-lookup"><span data-stu-id="e2ab0-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="e2ab0-135">Чтобы добавить ограничивающий прямоугольник вокруг объекта, просто добавьте `BoundingBox` в него компонент:</span><span class="sxs-lookup"><span data-stu-id="e2ab0-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="e2ab0-136">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="e2ab0-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="e2ab0-137">Целевой объект</span><span class="sxs-lookup"><span data-stu-id="e2ab0-137">Target object</span></span>

<span data-ttu-id="e2ab0-138">Это свойство указывает, какой объект будет преобразован с помощью манипуляции ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="e2ab0-139">Если объект не задан, то ограничивающий прямоугольник по умолчанию принимает значение объекта Owner.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="e2ab0-140">Переопределение границ</span><span class="sxs-lookup"><span data-stu-id="e2ab0-140">Bounds override</span></span>

<span data-ttu-id="e2ab0-141">Устанавливает блочный объект для вычисления границ объекта.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="e2ab0-142">Поведение при активации</span><span class="sxs-lookup"><span data-stu-id="e2ab0-142">Activation behavior</span></span>

<span data-ttu-id="e2ab0-143">Существует несколько вариантов активации интерфейса ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="e2ab0-144">*Активировать при запуске*: ограничивающий прямоугольник становится видимым после запуска сцены.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="e2ab0-145">*Активировать по сходству*: ограничивающий прямоугольник становится видимым, когда накрывающаяся рука близко к объекту.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="e2ab0-146">*Активировать по указателю*: ограничивающий прямоугольник становится видимым, если он предназначен для указателя типа «рука-Ray».</span><span class="sxs-lookup"><span data-stu-id="e2ab0-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="e2ab0-147">*Активировать вручную*: ограничивающий прямоугольник не становится видимым автоматически.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="e2ab0-148">Вы можете активировать его вручную с помощью скрипта, обратившись к свойству boundingBox. Active.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="e2ab0-149">Минимум шкалы</span><span class="sxs-lookup"><span data-stu-id="e2ab0-149">Scale minimum</span></span>

<span data-ttu-id="e2ab0-150">Минимальный допустимый масштаб.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-150">The minimum allowed scale.</span></span> <span data-ttu-id="e2ab0-151">Это свойство является устаревшим и предпочтительно добавить [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) скрипт.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="e2ab0-152">При добавлении этого скрипта минимальный масштаб будет взят из него, а не из ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="e2ab0-153">Максимальный масштаб</span><span class="sxs-lookup"><span data-stu-id="e2ab0-153">Scale maximum</span></span>

<span data-ttu-id="e2ab0-154">Максимально допустимый масштаб.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-154">The maximum allowed scale.</span></span> <span data-ttu-id="e2ab0-155">Это свойство является устаревшим и предпочтительно добавить [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) скрипт.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="e2ab0-156">Если этот скрипт добавлен, вместо ограничивающего прямоугольника будет получен максимальный масштаб.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="e2ab0-157">Отображение Box</span><span class="sxs-lookup"><span data-stu-id="e2ab0-157">Box display</span></span>

<span data-ttu-id="e2ab0-158">Различные параметры визуализации ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="e2ab0-159">Если для оси плоской диаграммы задано значение *автоматическое сведение*, скрипт не сможет управлять по оси с наименьшим экстентом.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="e2ab0-160">Это приводит к созданию двухмерного ограничивающего прямоугольника, который обычно используется для тонких объектов.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="e2ab0-161">Маркеры</span><span class="sxs-lookup"><span data-stu-id="e2ab0-161">Handles</span></span>

<span data-ttu-id="e2ab0-162">Можно назначить материал и prefab, чтобы переопределить стиль маркера.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="e2ab0-163">Если дескрипторы не назначены, они будут отображаться в стиле по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="e2ab0-164">События</span><span class="sxs-lookup"><span data-stu-id="e2ab0-164">Events</span></span>

<span data-ttu-id="e2ab0-165">Ограничивающий прямоугольник предоставляет следующие события.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-165">Bounding box provides the following events.</span></span> <span data-ttu-id="e2ab0-166">В этом примере эти события используются для воспроизведения звуковых отзывов.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="e2ab0-167">**Начало** вращения: срабатывает при начале вращения.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="e2ab0-168">**Поворот завершен**: срабатывает при завершении вращения.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="e2ab0-169">**Масштабирование начато**: активируется при запуске масштабирования.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="e2ab0-170">Окончание **масштабирования**: срабатывает при завершении масштабирования.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="e2ab0-171">Стили обработчиков</span><span class="sxs-lookup"><span data-stu-id="e2ab0-171">Handle styles</span></span>

<span data-ttu-id="e2ab0-172">по умолчанию при простом назначении [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) сценария будет показан дескриптор HoloLens 1-го стиля.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="e2ab0-173">чтобы использовать HoloLens 2 дескрипторы стилей, необходимо назначить соответствующие дескрипторы prefabs и материалы.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Стили маркера ограничивающего прямоугольника](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="e2ab0-175">ниже приведены prefabs, материалы и значения масштабирования для маркеров ограничивающего прямоугольника стиля HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="e2ab0-176">Этот пример можно найти в `BoundingBoxExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="e2ab0-177">дескрипторы (программа установки для стиля HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="e2ab0-178">**Обрабатывающий материал**: баундингбоксхандлевхите.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="e2ab0-179">**Обработано извлеченный материал**: баундингбоксхандлеблуеграббед.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="e2ab0-180">**Маркер масштабирования prefab**: MRTK_BoundingBox_ScaleHandle. prefab</span><span class="sxs-lookup"><span data-stu-id="e2ab0-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="e2ab0-181">MRTK_BoundingBox_ScaleHandle_Slate prefab. prefab на **планшетном маркере масштабирования**.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="e2ab0-182">**Размер маркера масштабирования**: 0,016 (1.6 cm)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="e2ab0-183">**Коэффициент масштабирования**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="e2ab0-184">**Маркер вращения prefab**: MRTK_BoundingBox_RotateHandle. prefab</span><span class="sxs-lookup"><span data-stu-id="e2ab0-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="e2ab0-185">**Размер маркера вращения**: 0,016</span><span class="sxs-lookup"><span data-stu-id="e2ab0-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="e2ab0-186">**Маркер поворота**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="e2ab0-187">близость (программа установки для стиля HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="e2ab0-188">Отображение и скрытие маркеров с анимацией на основе расстояния от руки.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="e2ab0-189">Он имеет двустороннюю анимацию масштабирования.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="e2ab0-190">**Активно воздействие на близкое** использование: Включение активации с помощью маркеров с учетом расположения</span><span class="sxs-lookup"><span data-stu-id="e2ab0-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="e2ab0-191">**Средний уровень сходства**: расстояние для первого шага масштабирования</span><span class="sxs-lookup"><span data-stu-id="e2ab0-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="e2ab0-192">**Обработайте близко близко**: расстояние для второго шага масштабирования</span><span class="sxs-lookup"><span data-stu-id="e2ab0-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="e2ab0-193">**Далеко масштаб**: значение масштаба по умолчанию для ресурса-маркера, если руки выходят за пределы диапазона взаимодействия ограничивающего прямоугольника (расстояние, определенное выше с помощью "маркер среднего сходства").</span><span class="sxs-lookup"><span data-stu-id="e2ab0-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="e2ab0-194">Использовать 0 для скрытия обработчика по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="e2ab0-195">**Средняя шкала**: значение масштаба ресурса маркера, когда руки находятся в диапазоне взаимодействия ограничивающего прямоугольника (расстояние, определенное выше с помощью маркера близкого сходства).</span><span class="sxs-lookup"><span data-stu-id="e2ab0-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="e2ab0-196">Чтобы отобразить нормальный размер, используйте значение 1.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="e2ab0-197">**Закрытие шкалы**: масштабирование значения ресурса-маркера, когда руки находятся в диапазоне взаимодействия (расстояние, определенное выше с помощью маркера близкого сходства).</span><span class="sxs-lookup"><span data-stu-id="e2ab0-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="e2ab0-198">Используйте 1. x, чтобы отобразить больший размер)</span><span class="sxs-lookup"><span data-stu-id="e2ab0-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="e2ab0-199">Создание объекта, перемещаемого с помощью обработчика манипуляции</span><span class="sxs-lookup"><span data-stu-id="e2ab0-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="e2ab0-200">Ограничивающий прямоугольник можно сочетать с [`ManipulationHandler.cs`](manipulation-handler.md) , чтобы сделать объект перемещаемым с помощью дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="e2ab0-201">Обработчик манипуляции поддерживает как одно, так и два действия.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="e2ab0-202">[Отслеживание вручную](../input/hand-tracking.md) можно использовать для взаимодействия с объектом по закрытию.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="e2ab0-203">Чтобы границы ограничивающего прямоугольника могли работать одинаково при перемещении с помощью [`ManipulationHandler`](manipulation-handler.md) дальнего взаимодействия, рекомендуется соединить свои события для *манипуляции, начатой* для  /  *манипуляции* , которые заканчиваются `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` соответственно, как показано на снимке экрана выше.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="e2ab0-204">Миграция в элемент управления "границы"</span><span class="sxs-lookup"><span data-stu-id="e2ab0-204">Migrating to bounds control</span></span>

<span data-ttu-id="e2ab0-205">Существующие Prefabs и экземпляры, использующие [ограничивающий прямоугольник](bounding-box.md) , можно обновить до нового элемента управления "границы" через [окно миграции](../tools/migration-window.md) , которое является частью пакета средств мртк.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="e2ab0-206">Для обновления отдельных экземпляров ограничивающего прямоугольника также существует параметр миграции в инспекторе свойств компонента.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
