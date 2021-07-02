---
title: Диспетчер ограничений
description: Общие сведения о диспетчере ограничений в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177554"
---
# <a name="constraint-manager"></a><span data-ttu-id="54a09-104">Диспетчер ограничений</span><span class="sxs-lookup"><span data-stu-id="54a09-104">Constraint manager</span></span>

<span data-ttu-id="54a09-105">Диспетчер ограничений позволяет применять к преобразованию набор компонентов ограничений.</span><span class="sxs-lookup"><span data-stu-id="54a09-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="54a09-106">[`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint)Можно принять во внимание компоненты типа, присоединенные к игровому объекту.</span><span class="sxs-lookup"><span data-stu-id="54a09-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="54a09-107">По умолчанию диспетчер ограничений автоматически соберет все [компоненты ограничений](#transform-constraints) , присоединенные к игровому объекту, и применит их к обработанным преобразованиям.</span><span class="sxs-lookup"><span data-stu-id="54a09-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="54a09-108">Однако пользователи могут явно настроить список примененных ограничений вручную и разрешить применение только подмножества присоединенных ограничений.</span><span class="sxs-lookup"><span data-stu-id="54a09-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="54a09-109">В настоящее время следующие элементы UX МРТК поддерживают диспетчер ограничений:</span><span class="sxs-lookup"><span data-stu-id="54a09-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="54a09-110">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="54a09-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="54a09-111">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="54a09-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="54a09-112">Свойства и поля инспектора</span><span class="sxs-lookup"><span data-stu-id="54a09-112">Inspector properties and fields</span></span>

<span data-ttu-id="54a09-113">Управление ограничениями может осуществляться в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="54a09-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="54a09-114">Автоматический выбор ограничений</span><span class="sxs-lookup"><span data-stu-id="54a09-114">Auto constraint selection</span></span>
- <span data-ttu-id="54a09-115">Выбор ограничений вручную</span><span class="sxs-lookup"><span data-stu-id="54a09-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="54a09-116">Автоматический выбор ограничений</span><span class="sxs-lookup"><span data-stu-id="54a09-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="54a09-117">Режим по умолчанию для диспетчера ограничений, выбор автоматического ограничения, предоставит список всех присоединенных ограничений, а также [кнопки переход к](#go-to-component) и [Добавить ограничение](#add-constraint-to-game-object).</span><span class="sxs-lookup"><span data-stu-id="54a09-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="54a09-118">Добавить ограничение к игровому объекту</span><span class="sxs-lookup"><span data-stu-id="54a09-118">Add constraint to game object</span></span>

<span data-ttu-id="54a09-119">Эта кнопка позволяет добавлять компонент ограничения непосредственно из инспектора диспетчера ограничений.</span><span class="sxs-lookup"><span data-stu-id="54a09-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="54a09-120">Все типы ограничений в проекте должны быть видимыми здесь.</span><span class="sxs-lookup"><span data-stu-id="54a09-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="54a09-121">Дополнительные сведения см. в разделе [ограничения преобразования](#transform-constraints) .</span><span class="sxs-lookup"><span data-stu-id="54a09-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="54a09-122">Переход к компоненту</span><span class="sxs-lookup"><span data-stu-id="54a09-122">Go to component</span></span>

<span data-ttu-id="54a09-123">Все ограничения, обнаруженные в объекте будет, перечислены здесь с помощью кнопки *"переход к компоненту* ".</span><span class="sxs-lookup"><span data-stu-id="54a09-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="54a09-124">Эта кнопка приведет к прокрутке инспектора до выбранного компонента ограничения, чтобы его можно было настроить.</span><span class="sxs-lookup"><span data-stu-id="54a09-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="54a09-125">Выбор ограничений вручную</span><span class="sxs-lookup"><span data-stu-id="54a09-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="54a09-126">Если для диспетчера ограничений задан режим вручную, то все ограничения, связанные в списке ограничений, обрабатываются и применяются к преобразованию.</span><span class="sxs-lookup"><span data-stu-id="54a09-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="54a09-127">В отображаемом списке будут показаны только выбранные пользователем ограничения, а также [кнопки](#go-to-component) и параметры для удаления или добавления записей.</span><span class="sxs-lookup"><span data-stu-id="54a09-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="54a09-128">При первом включении режима "вручную" Диспетчер ограничений заполнит список всеми доступными компонентами в качестве отправной точки для выбора присоединенных компонентов ограничений.</span><span class="sxs-lookup"><span data-stu-id="54a09-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="54a09-129">Удалить запись</span><span class="sxs-lookup"><span data-stu-id="54a09-129">Remove entry</span></span>

<span data-ttu-id="54a09-130">Это приведет к удалению записи из списка, выбранного вручную.</span><span class="sxs-lookup"><span data-stu-id="54a09-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="54a09-131">Обратите внимание, что этот параметр не удаляет компонент ограничения из игрового объекта.</span><span class="sxs-lookup"><span data-stu-id="54a09-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="54a09-132">Компоненты ограничений всегда необходимо удалять вручную, чтобы предотвратить случайное разбиение любого другого компонента, ссылающегося на этот компонент.</span><span class="sxs-lookup"><span data-stu-id="54a09-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="54a09-133">Добавить запись</span><span class="sxs-lookup"><span data-stu-id="54a09-133">Add entry</span></span>

<span data-ttu-id="54a09-134">Добавить запись открывает раскрывающийся список всех доступных компонентов ограничений, которые еще не включены в список вручную.</span><span class="sxs-lookup"><span data-stu-id="54a09-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="54a09-135">Щелкнув любую из записей, вы добавите этот компонент к выбранному ограничению вручную.</span><span class="sxs-lookup"><span data-stu-id="54a09-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="54a09-136">Добавить новое ограничение</span><span class="sxs-lookup"><span data-stu-id="54a09-136">Add new constraint</span></span>

<span data-ttu-id="54a09-137">Этот параметр позволяет добавить компонент выбранного типа к игровому объекту и добавить только что созданный компонент ограничения в список ручных ограничений.</span><span class="sxs-lookup"><span data-stu-id="54a09-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="54a09-138">Ограничения преобразования</span><span class="sxs-lookup"><span data-stu-id="54a09-138">Transform constraints</span></span>

<span data-ttu-id="54a09-139">Ограничения можно использовать для ограничения манипуляций.</span><span class="sxs-lookup"><span data-stu-id="54a09-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="54a09-140">Например, некоторым приложениям может потребоваться поворот, но также требуется, чтобы объект оставался вертикальным.</span><span class="sxs-lookup"><span data-stu-id="54a09-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="54a09-141">В этом случае `RotationAxisConstraint` можно добавить объект к объекту и использовать его для ограничения поворота по оси y.</span><span class="sxs-lookup"><span data-stu-id="54a09-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="54a09-142">МРТК предоставляет ряд ограничений, которые описаны ниже.</span><span class="sxs-lookup"><span data-stu-id="54a09-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="54a09-143">Кроме того, можно определить новые ограничения и использовать их для создания уникального поведения манипуляции, которое может потребоваться для некоторых приложений.</span><span class="sxs-lookup"><span data-stu-id="54a09-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="54a09-144">Для этого создайте скрипт, который наследует от [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) и реализует абстрактное `ConstraintType` свойство и абстрактный `ApplyConstraint` метод.</span><span class="sxs-lookup"><span data-stu-id="54a09-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="54a09-145">При добавлении нового ограничения к объекту оно должно ограничивать манипуляцию определенным способом.</span><span class="sxs-lookup"><span data-stu-id="54a09-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="54a09-146">Это новое ограничение должно также отображаться в [автоматическом выборе](#auto-constraint-selection) диспетчера ограничений или в раскрывающемся списке [Добавить запись](#add-entry) в ручном режиме.</span><span class="sxs-lookup"><span data-stu-id="54a09-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="54a09-147">Все ограничения, предоставляемые МРТК, имеют следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="54a09-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="54a09-148">Тип руки</span><span class="sxs-lookup"><span data-stu-id="54a09-148">Hand Type</span></span>

<span data-ttu-id="54a09-149">Указывает, используется ли ограничение для одного руки, двух операций или обоих видов манипуляций.</span><span class="sxs-lookup"><span data-stu-id="54a09-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="54a09-150">Так как это свойство является флагом, можно выбрать оба параметра.</span><span class="sxs-lookup"><span data-stu-id="54a09-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="54a09-151">*Один рукой*. ограничение будет использоваться во время одной манипуляции, если выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="54a09-152">*Два руки*: ограничение будет использоваться во время двух манипуляций, если выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="54a09-153">Тип сходства</span><span class="sxs-lookup"><span data-stu-id="54a09-153">Proximity Type</span></span>

<span data-ttu-id="54a09-154">Указывает, используется ли ограничение для обработки практически, дальнего или обоих видов.</span><span class="sxs-lookup"><span data-stu-id="54a09-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="54a09-155">Так как это свойство является флагом, можно выбрать оба параметра.</span><span class="sxs-lookup"><span data-stu-id="54a09-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="54a09-156">*NEAR*: ограничение будет использоваться во время близкой манипуляции, если оно выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="54a09-157">*FAR*: во время манипуляции будет использоваться ограничение, если оно выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="54a09-158">фацеусерконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="54a09-159">Если это ограничение прикрепляется к объекту, поворот будет ограничен, поэтому объект всегда будет лицом к пользователю.</span><span class="sxs-lookup"><span data-stu-id="54a09-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="54a09-160">Это удобно для планшетов и панелей.</span><span class="sxs-lookup"><span data-stu-id="54a09-160">This is useful for slates or panels.</span></span> <span data-ttu-id="54a09-161">`FaceUserConstraint`Ниже приведены свойства для.</span><span class="sxs-lookup"><span data-stu-id="54a09-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="54a09-162">Лицевая сторону</span><span class="sxs-lookup"><span data-stu-id="54a09-162">Face away</span></span>

<span data-ttu-id="54a09-163">Объект отрывается от пользователя, если значение равно true.</span><span class="sxs-lookup"><span data-stu-id="54a09-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="54a09-164">фикседдистанцеконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="54a09-165">Это ограничение устраняет расстояние между управляемым объектом и другим преобразованием объекта при запуске манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="54a09-166">Это полезно для такого поведения, как исправление расстояния от управляемого объекта до преобразования Head.</span><span class="sxs-lookup"><span data-stu-id="54a09-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="54a09-167">`FixedDistanceConstraint`Ниже приведены свойства для.</span><span class="sxs-lookup"><span data-stu-id="54a09-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="54a09-168">Преобразование ограничений</span><span class="sxs-lookup"><span data-stu-id="54a09-168">Constraint transform</span></span>

<span data-ttu-id="54a09-169">Это другое преобразование, в котором управляемый объект будет иметь фиксированное расстояние до.</span><span class="sxs-lookup"><span data-stu-id="54a09-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="54a09-170">По умолчанию используется преобразование Camera.</span><span class="sxs-lookup"><span data-stu-id="54a09-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="54a09-171">фикседротатионтаусерконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="54a09-172">Это ограничение исправляет относительный поворот между пользователем и управляемым объектом во время его манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="54a09-173">Это полезно для планшетов и панелей, так как это гарантирует, что управляемый объект всегда будет показывать ту же грань пользователю, что и в начале манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="54a09-174">Не `FixedRotationToUserConstraint` имеет уникальных свойств.</span><span class="sxs-lookup"><span data-stu-id="54a09-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="54a09-175">фикседротатионтоворлдконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="54a09-176">Это ограничение устраняет глобальное вращение управляемого объекта во время его манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="54a09-177">Это может быть полезно в случаях, когда вращение не должно быть частью манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="54a09-178">Не `FixedRotationToWorldConstraint` имеет уникальных свойств:</span><span class="sxs-lookup"><span data-stu-id="54a09-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="54a09-179">маинтаинаппарентсизеконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="54a09-180">Если это ограничение прикрепляется к объекту независимо от того, насколько он находится от пользователя, он будет сохранять тот же видимый размер для пользователя (т. е. он занимает ту же часть поля зрения пользователя).</span><span class="sxs-lookup"><span data-stu-id="54a09-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="54a09-181">Это можно использовать для того, чтобы панель планшета или текста оставалась доступной для чтения при манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="54a09-182">Не `MaintainApparentSizeConstraint` имеет уникальных свойств:</span><span class="sxs-lookup"><span data-stu-id="54a09-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="54a09-183">мовеаксисконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="54a09-184">Это ограничение можно использовать для исправления осей, вдоль которых можно переместить управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="54a09-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="54a09-185">Это может быть полезно для манипуляций с объектами на поверхности плоскости или вдоль линии.</span><span class="sxs-lookup"><span data-stu-id="54a09-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="54a09-186">`MoveAxisConstraint`Ниже приведены свойства для.</span><span class="sxs-lookup"><span data-stu-id="54a09-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="54a09-187">Ограничение на перемещение</span><span class="sxs-lookup"><span data-stu-id="54a09-187">Constraint on movement</span></span>

<span data-ttu-id="54a09-188">Указывает, для каких осей запрещается перемещение.</span><span class="sxs-lookup"><span data-stu-id="54a09-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="54a09-189">По умолчанию эти оси будут глобальными, а не локальными, но их можно изменить ниже.</span><span class="sxs-lookup"><span data-stu-id="54a09-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="54a09-190">Поскольку это свойство является флагом, можно выбрать любое количество параметров.</span><span class="sxs-lookup"><span data-stu-id="54a09-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="54a09-191">*Ось x*: перемещение по оси x ограничено, если оно выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="54a09-192">*Ось y*: перемещение по оси y ограничено, если оно выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="54a09-193">*Ось z*: перемещение по оси z ограничено, если оно выбрано.</span><span class="sxs-lookup"><span data-stu-id="54a09-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="54a09-194">Использовать локальное пространство для ограничения</span><span class="sxs-lookup"><span data-stu-id="54a09-194">Use local space for constraint</span></span>

<span data-ttu-id="54a09-195">При значении true ограничения для локальных преобразований управляемого объекта будут ограничены.</span><span class="sxs-lookup"><span data-stu-id="54a09-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="54a09-196">Значение по умолчанию: false.</span><span class="sxs-lookup"><span data-stu-id="54a09-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="54a09-197">ротатионаксисконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="54a09-198">Это ограничение можно использовать, чтобы исправить, какие оси можно поворачивать с помощью управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="54a09-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="54a09-199">Это может быть полезно для сохранения управляемого объекта по вертикали, но по-прежнему разрешает вращение по оси y.</span><span class="sxs-lookup"><span data-stu-id="54a09-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="54a09-200">`RotationAxisConstraint`Ниже приведены свойства для.</span><span class="sxs-lookup"><span data-stu-id="54a09-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="54a09-201">Ограничение при повороте</span><span class="sxs-lookup"><span data-stu-id="54a09-201">Constraint on rotation</span></span>

<span data-ttu-id="54a09-202">Указывает, какие оси не препятствуют повороту.</span><span class="sxs-lookup"><span data-stu-id="54a09-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="54a09-203">По умолчанию эти оси будут глобальными, а не локальными, но их можно изменить ниже.</span><span class="sxs-lookup"><span data-stu-id="54a09-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="54a09-204">Поскольку это свойство является флагом, можно выбрать любое количество параметров.</span><span class="sxs-lookup"><span data-stu-id="54a09-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="54a09-205">*Ось y*: поворот оси y ограничен, если он выбран.</span><span class="sxs-lookup"><span data-stu-id="54a09-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="54a09-206">*Ось z*: поворот оси z ограничен, если он выбран.</span><span class="sxs-lookup"><span data-stu-id="54a09-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="54a09-207">*Ось x*: поворот вокруг оси x ограничен, если он выбран.</span><span class="sxs-lookup"><span data-stu-id="54a09-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="54a09-208">Использовать локальное пространство для ограничения</span><span class="sxs-lookup"><span data-stu-id="54a09-208">Use local space for constraint</span></span>

<span data-ttu-id="54a09-209">При значении true ограничения для локальных преобразований управляемого объекта будут ограничены.</span><span class="sxs-lookup"><span data-stu-id="54a09-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="54a09-210">Значение по умолчанию: false.</span><span class="sxs-lookup"><span data-stu-id="54a09-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="54a09-211">минмаксскалеконстраинт</span><span class="sxs-lookup"><span data-stu-id="54a09-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="54a09-212">Это ограничение позволяет задать минимальное и максимальное значения для шкалы управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="54a09-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="54a09-213">Это полезно для предотвращения слишком большого или недопустимого масштабирования объектов пользователями.</span><span class="sxs-lookup"><span data-stu-id="54a09-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="54a09-214">`MinMaxScaleConstraint`Ниже приведены свойства для.</span><span class="sxs-lookup"><span data-stu-id="54a09-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="54a09-215">Минимум шкалы</span><span class="sxs-lookup"><span data-stu-id="54a09-215">Scale minimum</span></span>

<span data-ttu-id="54a09-216">Минимальное значение масштаба во время манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="54a09-217">Максимальный масштаб</span><span class="sxs-lookup"><span data-stu-id="54a09-217">Scale maximum</span></span>

<span data-ttu-id="54a09-218">Максимальное значение масштаба во время манипуляции.</span><span class="sxs-lookup"><span data-stu-id="54a09-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="54a09-219">Относительно первоначального состояния</span><span class="sxs-lookup"><span data-stu-id="54a09-219">Relative to initial state</span></span>

<span data-ttu-id="54a09-220">Если значение равно true, приведенные выше значения будут интерпретироваться как относительные от исходного масштаба объектов.</span><span class="sxs-lookup"><span data-stu-id="54a09-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="54a09-221">В противном случае они будут интерпретироваться как абсолютные значения масштаба.</span><span class="sxs-lookup"><span data-stu-id="54a09-221">Otherwise they will be interpreted as absolute scale values.</span></span>
