---
title: Контроллеры, указатели и фокус
description: Взаимодействие с контроллерами, указателями и фокусом.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, указатели, контроллеры
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121622"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="ebc34-104">Контроллеры, указатели и фокус</span><span class="sxs-lookup"><span data-stu-id="ebc34-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="ebc34-105">Контроллеры, указатели и фокус — это концепции более высокого уровня, основанные на фундаменте, установленном основной системой ввода.</span><span class="sxs-lookup"><span data-stu-id="ebc34-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="ebc34-106">Вместе они предоставляют большую часть механизма для взаимодействия с объектами в сцене.</span><span class="sxs-lookup"><span data-stu-id="ebc34-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="ebc34-107">Контроллеры</span><span class="sxs-lookup"><span data-stu-id="ebc34-107">Controllers</span></span>

<span data-ttu-id="ebc34-108">Контроллеры представляют собой представления физического контроллера (6-градусы свободы, шарнирные руки и т. д.).</span><span class="sxs-lookup"><span data-stu-id="ebc34-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="ebc34-109">Они создаются диспетчерами устройств и отвечают за взаимодействие с соответствующей базовой системой и перевод этих данных в МРТК данные и события в форме.</span><span class="sxs-lookup"><span data-stu-id="ebc34-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="ebc34-110">Например, на платформе Windows Mixed Reality [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) — это контроллер, который отвечает за взаимодействие с базовыми [API-интерфейсами отслеживания](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Windows, чтобы получить сведения о соединениях, методах и других свойствах руки.</span><span class="sxs-lookup"><span data-stu-id="ebc34-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="ebc34-111">Он отвечает за преобразование этих данных в соответствующие события МРТК (например, путем вызова Раисепосеинпутчанжед или Раисеханджоинтсупдатед) и путем обновления собственного внутреннего состояния, чтобы запросы [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) возвращали правильные данные.</span><span class="sxs-lookup"><span data-stu-id="ebc34-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="ebc34-112">Как правило, жизненный цикл контроллера будет содержать:</span><span class="sxs-lookup"><span data-stu-id="ebc34-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="ebc34-113">Контроллер создается диспетчером устройств при обнаружении нового источника (например, диспетчер устройств обнаруживает и начинает отслеживание руки).</span><span class="sxs-lookup"><span data-stu-id="ebc34-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="ebc34-114">В цикле Update () контроллера он вызывает свою базовую систему API.</span><span class="sxs-lookup"><span data-stu-id="ebc34-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="ebc34-115">В том же цикле обновления он создает изменения событий ввода, вызывая непосредственно в основную систему ввода (например, вызывая Хандмешупдатед или Ханджоинтсупдатед).</span><span class="sxs-lookup"><span data-stu-id="ebc34-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="ebc34-116">Указатели и фокус</span><span class="sxs-lookup"><span data-stu-id="ebc34-116">Pointers and focus</span></span>

<span data-ttu-id="ebc34-117">Указатели используются для взаимодействия с игровыми объектами.</span><span class="sxs-lookup"><span data-stu-id="ebc34-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="ebc34-118">В этом разделе описывается, как создаются указатели, как они обновляются и как они определяют объекты, направляются в фокус.</span><span class="sxs-lookup"><span data-stu-id="ebc34-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="ebc34-119">Кроме того, будут рассмотрены различные типы существующих указателей и сценарии, в которых они активны.</span><span class="sxs-lookup"><span data-stu-id="ebc34-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="ebc34-120">Категории указателей</span><span class="sxs-lookup"><span data-stu-id="ebc34-120">Pointer categories</span></span>

<span data-ttu-id="ebc34-121">Обычно указатели делятся на одну из следующих категорий:</span><span class="sxs-lookup"><span data-stu-id="ebc34-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="ebc34-122">**Дальнее указатели**</span><span class="sxs-lookup"><span data-stu-id="ebc34-122">**Far pointers**</span></span>

  <span data-ttu-id="ebc34-123">Эти типы указателей используются для взаимодействия с объектами, далеко от пользователя (далеко не определяется как "не приближается").</span><span class="sxs-lookup"><span data-stu-id="ebc34-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="ebc34-124">Эти типы указателей обычно обходят строки, которые могут попасть в мир, и позволяют пользователю взаимодействовать с объектами, которые непосредственно не находятся рядом с ними, и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="ebc34-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="ebc34-125">**Близкие указатели**</span><span class="sxs-lookup"><span data-stu-id="ebc34-125">**Near pointers**</span></span>

  <span data-ttu-id="ebc34-126">Эти типы указателей используются для взаимодействия с объектами, достаточно близкими для того, чтобы пользователь мог захватить, коснуться и манипулировать.</span><span class="sxs-lookup"><span data-stu-id="ebc34-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="ebc34-127">Как правило, эти типы указателей взаимодействуют с объектами путем поиска объектов в соседних (путем выполнения райкастинг на небольших расстояниях, выполнения сферического приведения для поиска объектов в окружении или перечисления списков объектов, которые считаются перечисленными или сенсорными).</span><span class="sxs-lookup"><span data-stu-id="ebc34-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="ebc34-128">**Указатели телепортируйтесь**</span><span class="sxs-lookup"><span data-stu-id="ebc34-128">**Teleport pointers**</span></span>

  <span data-ttu-id="ebc34-129">Эти типы указателей подключаются к системе телетранспорта для управления перемещением пользователя в расположение, на которое указывает указатель.</span><span class="sxs-lookup"><span data-stu-id="ebc34-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="ebc34-130">Устранение указателя</span><span class="sxs-lookup"><span data-stu-id="ebc34-130">Pointer mediation</span></span>

<span data-ttu-id="ebc34-131">Поскольку один контроллер может иметь несколько указателей (например, у руки может быть как близко, так и далеко), существует компонент, который отвечает за обрабатывают, какой указатель должен быть активным.</span><span class="sxs-lookup"><span data-stu-id="ebc34-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="ebc34-132">Например, когда рука пользователя приближается к нажатой кнопке, элемент [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) должен перестать отображаться, а также [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) должен быть вовлечен.</span><span class="sxs-lookup"><span data-stu-id="ebc34-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="ebc34-133">Это обрабатывается объектом [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) , который отвечает за определение активных указателей на основе состояния всех указателей.</span><span class="sxs-lookup"><span data-stu-id="ebc34-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="ebc34-134">Одно из ключевых моментов заключается в отключении дальнего указателя, когда близкого указателя близко к объекту (см. раздел [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="ebc34-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="ebc34-135">Можно предоставить альтернативную реализацию указателя медиатора, изменив [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) свойство в профиле указателя.</span><span class="sxs-lookup"><span data-stu-id="ebc34-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="ebc34-136">Как отключить указатели</span><span class="sxs-lookup"><span data-stu-id="ebc34-136">How to disable pointers</span></span>

<span data-ttu-id="ebc34-137">Так как указатель медиатора запускает каждый кадр, он начинает управлять состоянием "активный" или "Неактивный" всех указателей.</span><span class="sxs-lookup"><span data-stu-id="ebc34-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="ebc34-138">Таким образом, если задать свойство Исинтерактионенаблед указателя в коде, оно будет перезаписано указателем медиатора каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="ebc34-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="ebc34-139">Вместо этого можно указать, следует [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) ли включить или отключить указатели.</span><span class="sxs-lookup"><span data-stu-id="ebc34-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="ebc34-140">Обратите внимание, что это будет работать только при использовании по умолчанию [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) и [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) в мртк.</span><span class="sxs-lookup"><span data-stu-id="ebc34-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="ebc34-141">Пример. Отключение луча с рукой в МРТК</span><span class="sxs-lookup"><span data-stu-id="ebc34-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="ebc34-142">Следующий код отключит лучи руки в МРТК:</span><span class="sxs-lookup"><span data-stu-id="ebc34-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="ebc34-143">Приведенный ниже код возвратит значения по умолчанию к их поведению в МРТК:</span><span class="sxs-lookup"><span data-stu-id="ebc34-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="ebc34-144">Приведенный ниже код будет вынужден быть включенным, независимо от того, находится ли рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="ebc34-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="ebc34-145">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Дополнительные примеры см. в разделе и.</span><span class="sxs-lookup"><span data-stu-id="ebc34-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="ebc34-146">фокуспровидер</span><span class="sxs-lookup"><span data-stu-id="ebc34-146">FocusProvider</span></span>

<span data-ttu-id="ebc34-147">[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)— Это основных, отвечающий за итерацию по списку всех указателей и вычисление объекта, на который нацелен объект, для каждого указателя.</span><span class="sxs-lookup"><span data-stu-id="ebc34-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="ebc34-148">В каждом `Update()` вызове будет следующее:</span><span class="sxs-lookup"><span data-stu-id="ebc34-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="ebc34-149">Обновляет все указатели, райкастинг и выполняя обнаружение попаданий, настроенное самим указателем (например, указатель сферы может указывать Сфереоверлап Райкастмоде, поэтому Фокуспровидер выполнит конфликт на основе сферы).</span><span class="sxs-lookup"><span data-stu-id="ebc34-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="ebc34-150">Обновление объекта с фокусом на основе каждого указателя (т. е. Если объект получит фокус, он также запустит события для этого объекта, если объект потерял фокус, он вызовет потерю фокуса и т. д.).</span><span class="sxs-lookup"><span data-stu-id="ebc34-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="ebc34-151">Конфигурация указателя и жизненный цикл</span><span class="sxs-lookup"><span data-stu-id="ebc34-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="ebc34-152">[Указатели можно настраивать](../features/input/pointers.md) в разделе *указатели* входного системного профиля.</span><span class="sxs-lookup"><span data-stu-id="ebc34-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="ebc34-153">Как правило, время существования указателя является следующим:</span><span class="sxs-lookup"><span data-stu-id="ebc34-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="ebc34-154">Диспетчер устройств обнаружит наличие контроллера.</span><span class="sxs-lookup"><span data-stu-id="ebc34-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="ebc34-155">Этот диспетчер устройств создаст набор указателей, связанных с контроллером, с помощью вызова [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="ebc34-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="ebc34-156">Фокуспровидер в цикле Update () перебирает все допустимые указатели и выполняет связанную логику обнаружения райкаст или попадания.</span><span class="sxs-lookup"><span data-stu-id="ebc34-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="ebc34-157">Используется для определения объекта, на который нацелен каждый конкретный указатель.</span><span class="sxs-lookup"><span data-stu-id="ebc34-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="ebc34-158">Так как может быть активировано несколько источников входных данных одновременно (например, две руки), можно также иметь несколько объектов, имеющих фокус одновременно.</span><span class="sxs-lookup"><span data-stu-id="ebc34-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="ebc34-159">Диспетчер устройств при обнаружении потери источника контроллера приведет к разрыву указателей, связанных с потерянным контроллером.</span><span class="sxs-lookup"><span data-stu-id="ebc34-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>