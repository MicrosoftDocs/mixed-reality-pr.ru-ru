---
title: Манипулятор объекта
description: Как использовать манипулятор объекта в МРТК
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, управление объектами
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176654"
---
# <a name="object-manipulator"></a><span data-ttu-id="65b63-104">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="65b63-104">Object manipulator</span></span>

![Манипулятор объекта](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="65b63-106">*Обжектманипулатор* — это новый компонент для поведения манипуляции, ранее обнаруженный в *манипулатионхандлер*.</span><span class="sxs-lookup"><span data-stu-id="65b63-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="65b63-107">Манипулятор объекта делает ряд улучшений и упрощений.</span><span class="sxs-lookup"><span data-stu-id="65b63-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="65b63-108">Этот компонент является заменой обработчика манипуляций, который будет считаться устаревшим.</span><span class="sxs-lookup"><span data-stu-id="65b63-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="65b63-109">Сценарий *обжектманипулатор* делает объект перемещаемым, масштабируемым и ротатабле, используя одну или две руки.</span><span class="sxs-lookup"><span data-stu-id="65b63-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="65b63-110">Манипулятор объекта можно настроить для управления тем, как объект будет отвечать на различные входные данные.</span><span class="sxs-lookup"><span data-stu-id="65b63-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="65b63-111">сценарий должен работать с большинством видов взаимодействия, например HoloLens 2 с клавиатуры, HoloLens 2 лучами, HoloLens 1 взгляд и жесты, а также ввод впечатляющих контроллеров движения гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="65b63-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="65b63-112">Использование манипулятора объекта</span><span class="sxs-lookup"><span data-stu-id="65b63-112">How to use the object manipulator</span></span>

<span data-ttu-id="65b63-113">Чтобы использовать манипулятор объекта, сначала добавьте `ObjectManipulator` компонент скрипта в GameObject.</span><span class="sxs-lookup"><span data-stu-id="65b63-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="65b63-114">Не забудьте добавить к объекту объект, соответствующий заданным границам.</span><span class="sxs-lookup"><span data-stu-id="65b63-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="65b63-115">Чтобы сделать объект ответом на близкие входные данные, добавьте `NearInteractionGrabbable` также скрипт.</span><span class="sxs-lookup"><span data-stu-id="65b63-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="65b63-116">Поведение физикы можно включить для манипулятора объекта, добавив компонент RigidBody в объект.</span><span class="sxs-lookup"><span data-stu-id="65b63-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="65b63-117">Поведение физикы, включенное добавлением этого компонента, подробно описано в разделе [*физика и конфликты*](#physics-and-collisions).</span><span class="sxs-lookup"><span data-stu-id="65b63-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="65b63-118">Кроме того, управление может быть ограничено путем добавления [компонентов ограничений манипуляции](constraint-manager.md#transform-constraints) в объект.</span><span class="sxs-lookup"><span data-stu-id="65b63-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="65b63-119">Это специальные компоненты, которые работают с манипуляцией и изменяют поведение манипуляции каким – либо образом.</span><span class="sxs-lookup"><span data-stu-id="65b63-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Использование обработчика манипуляции в редакторе Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="65b63-121">Свойства и поля инспектора</span><span class="sxs-lookup"><span data-stu-id="65b63-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="65b63-122">Общие свойства</span><span class="sxs-lookup"><span data-stu-id="65b63-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="65b63-123">Преобразование узла</span><span class="sxs-lookup"><span data-stu-id="65b63-123">Host transform</span></span>

<span data-ttu-id="65b63-124">Преобразование объекта, которое будет управляться.</span><span class="sxs-lookup"><span data-stu-id="65b63-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="65b63-125">По умолчанию используется объект компонента.</span><span class="sxs-lookup"><span data-stu-id="65b63-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="65b63-126">Тип манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-126">Manipulation type</span></span>

<span data-ttu-id="65b63-127">Указывает, можно ли манипулировать объектом с помощью одной руки или двух стрелок.</span><span class="sxs-lookup"><span data-stu-id="65b63-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="65b63-128">Так как это свойство является флагом, можно выбрать оба параметра.</span><span class="sxs-lookup"><span data-stu-id="65b63-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="65b63-129">*Один из них*: включает одну обработанную манипуляцию, если она выбрана.</span><span class="sxs-lookup"><span data-stu-id="65b63-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="65b63-130">*Две руки*: включает две манипуляции, если она выбрана.</span><span class="sxs-lookup"><span data-stu-id="65b63-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="65b63-131">Разрешить далекое манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-131">Allow far manipulation</span></span>

<span data-ttu-id="65b63-132">Указывает, можно ли выполнять манипуляции с помощью дальнего взаимодействия с указателями.</span><span class="sxs-lookup"><span data-stu-id="65b63-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="65b63-133">Одно обработанное свойство манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="65b63-134">Режим поворота одного руки рядом с</span><span class="sxs-lookup"><span data-stu-id="65b63-134">One hand rotation mode near</span></span>

<span data-ttu-id="65b63-135">Указывает, как будет вести себя объект при наличии одной руки рядом с ней.</span><span class="sxs-lookup"><span data-stu-id="65b63-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="65b63-136">Эти параметры работают только для начеткого руки.</span><span class="sxs-lookup"><span data-stu-id="65b63-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="65b63-137">*Поворот по Object Center*: объект вращается с поворотом руки, а не с точки зрения центра объектов.</span><span class="sxs-lookup"><span data-stu-id="65b63-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="65b63-138">Объект будет двигаться меньше, чем он поворачивается, но может наблюдаться ощущение несоединения между рукой и объектом.</span><span class="sxs-lookup"><span data-stu-id="65b63-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="65b63-139">Более полезно для дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="65b63-139">More useful for far interaction.</span></span>
- <span data-ttu-id="65b63-140">*Поворот точки захвата*: поворот объекта с помощью руки, посвященной точке захвата между бегунком и указателем пальца.</span><span class="sxs-lookup"><span data-stu-id="65b63-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="65b63-141">Он должен иметь вид, если объект удерживается рукой.</span><span class="sxs-lookup"><span data-stu-id="65b63-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="65b63-142">Режим поворота одного руки</span><span class="sxs-lookup"><span data-stu-id="65b63-142">One hand rotation mode far</span></span>

<span data-ttu-id="65b63-143">Указывает, как будет вести себя объект, когда он помещается с одной рукой на расстояние.</span><span class="sxs-lookup"><span data-stu-id="65b63-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="65b63-144">Эти параметры работают только для начеткого руки.</span><span class="sxs-lookup"><span data-stu-id="65b63-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="65b63-145">*Повернуть на центр Object Center*: поворот объекта с помощью поворота руки, а также от точки центра объектов.</span><span class="sxs-lookup"><span data-stu-id="65b63-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="65b63-146">Полезен для проверки на расстоянии без перемещения по центру объектов при повороте объекта.</span><span class="sxs-lookup"><span data-stu-id="65b63-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="65b63-147">*Поворот точки захвата*: поворот объекта с помощью поворота руки, а также о точке попадания в указатель луча.</span><span class="sxs-lookup"><span data-stu-id="65b63-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="65b63-148">Полезно для проверки.</span><span class="sxs-lookup"><span data-stu-id="65b63-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="65b63-149">Два свойства манипуляции с руки</span><span class="sxs-lookup"><span data-stu-id="65b63-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="65b63-150">Тип двунаправленной манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-150">Two handed manipulation type</span></span>

<span data-ttu-id="65b63-151">Указывает, как две манипуляции могут преобразовывать объект.</span><span class="sxs-lookup"><span data-stu-id="65b63-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="65b63-152">Поскольку это свойство является флагом, можно выбрать любое количество параметров.</span><span class="sxs-lookup"><span data-stu-id="65b63-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="65b63-153">*Переместить*: перемещение разрешено, если выбрано.</span><span class="sxs-lookup"><span data-stu-id="65b63-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="65b63-154">*Масштаб*. масштабирование разрешено, если выбрано.</span><span class="sxs-lookup"><span data-stu-id="65b63-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="65b63-155">*Повернуть*: поворот разрешен, если он выбран.</span><span class="sxs-lookup"><span data-stu-id="65b63-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Обработчик манипуляции](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="65b63-157">Ограничения</span><span class="sxs-lookup"><span data-stu-id="65b63-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="65b63-158">Включить ограничения</span><span class="sxs-lookup"><span data-stu-id="65b63-158">Enable constraints</span></span>

<span data-ttu-id="65b63-159">Этот параметр включит [Диспетчер связанных ограничений](constraint-manager.md).</span><span class="sxs-lookup"><span data-stu-id="65b63-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="65b63-160">Изменения преобразования будут обработаны ограничениями, зарегистрированными для выбранного [диспетчера ограничений](constraint-manager.md).</span><span class="sxs-lookup"><span data-stu-id="65b63-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="65b63-161">Диспетчер ограничений</span><span class="sxs-lookup"><span data-stu-id="65b63-161">Constraint manager</span></span>

<span data-ttu-id="65b63-162">В раскрывающемся списке можно выбрать любой из подключенных [диспетчеров ограничений](constraint-manager.md).</span><span class="sxs-lookup"><span data-stu-id="65b63-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="65b63-163">Манипулятор объекта гарантирует, что [Диспетчер ограничений](constraint-manager.md) подключен всегда.</span><span class="sxs-lookup"><span data-stu-id="65b63-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="65b63-164">Обратите внимание, что несколько компонентов одного типа будут отображаться под одним и тем же именем в Unity.</span><span class="sxs-lookup"><span data-stu-id="65b63-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="65b63-165">Чтобы упростить различение нескольких диспетчеров ограничений для одного и того же объекта, доступные параметры будут показывать указание в конфигурации выбранного диспетчера ограничений (ручной или автоматический выбор ограничений).</span><span class="sxs-lookup"><span data-stu-id="65b63-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="65b63-166">Переход к компоненту</span><span class="sxs-lookup"><span data-stu-id="65b63-166">Go to component</span></span>

<span data-ttu-id="65b63-167">Выбор диспетчера ограничений сопровождается кнопкой " *Переход к компоненту* ".</span><span class="sxs-lookup"><span data-stu-id="65b63-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="65b63-168">Эта кнопка приведет к прокрутке инспектора до выбранного компонента, чтобы его можно было настроить.</span><span class="sxs-lookup"><span data-stu-id="65b63-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="65b63-169">Физика</span><span class="sxs-lookup"><span data-stu-id="65b63-169">Physics</span></span>

<span data-ttu-id="65b63-170">Параметры в этом разделе отображаются только в том случае, если объект имеет компонент RigidBody.</span><span class="sxs-lookup"><span data-stu-id="65b63-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="65b63-171">Поведение выпуска</span><span class="sxs-lookup"><span data-stu-id="65b63-171">Release behavior</span></span>

<span data-ttu-id="65b63-172">Укажите, какие физические свойства должен иметь управляемый объект при выпуске.</span><span class="sxs-lookup"><span data-stu-id="65b63-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="65b63-173">Так как это свойство является флагом, можно выбрать оба параметра.</span><span class="sxs-lookup"><span data-stu-id="65b63-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="65b63-174">*Скорость сохранения*: при освобождении объекта, если выбран этот параметр, он сохранит линейную скорость.</span><span class="sxs-lookup"><span data-stu-id="65b63-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="65b63-175">*удерживать Angularную скорость*: при освобождении объекта, если выбран этот параметр, его угловая скорость сохраняется.</span><span class="sxs-lookup"><span data-stu-id="65b63-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="65b63-176">Использовать силы для близкой манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-176">Use forces for near manipulation</span></span>

<span data-ttu-id="65b63-177">Используются ли для перемещения объекта физические силы при выполнении практических манипуляций.</span><span class="sxs-lookup"><span data-stu-id="65b63-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="65b63-178">Если присвоить этому параметру *значение false* , объект будет напрямую подключен к пользователям.</span><span class="sxs-lookup"><span data-stu-id="65b63-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="65b63-179">Если задать для этого свойства *значение true* , будет соблюдаться масса и инерция объекта, но может показаться, что объект подключен через пружину.</span><span class="sxs-lookup"><span data-stu-id="65b63-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="65b63-180">Значение по умолчанию — *false*.</span><span class="sxs-lookup"><span data-stu-id="65b63-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="65b63-181">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="65b63-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="65b63-182">Плавное сглаживание</span><span class="sxs-lookup"><span data-stu-id="65b63-182">Smoothing far</span></span>

<span data-ttu-id="65b63-183">Включено ли независимое сглаживание кадров для дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="65b63-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="65b63-184">При этом по умолчанию включается гораздо более гладкое сглаживание.</span><span class="sxs-lookup"><span data-stu-id="65b63-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="65b63-185">Смягчение вблизи</span><span class="sxs-lookup"><span data-stu-id="65b63-185">Smoothing near</span></span>

<span data-ttu-id="65b63-186">Включено ли независимое сглаживание кадров для практических взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="65b63-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="65b63-187">Близкое сглаживание отключено по умолчанию, так как результат может считаться "отключенным" от руки.</span><span class="sxs-lookup"><span data-stu-id="65b63-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="65b63-188">Сглаживание активно</span><span class="sxs-lookup"><span data-stu-id="65b63-188">Smoothing active</span></span>

<span data-ttu-id="65b63-189">Устарело и будет удалено в следующей версии.</span><span class="sxs-lookup"><span data-stu-id="65b63-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="65b63-190">Приложения должны использовать Смусингфар, Смусингнеар или сочетание этих двух.</span><span class="sxs-lookup"><span data-stu-id="65b63-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="65b63-191">Переместить время лерп</span><span class="sxs-lookup"><span data-stu-id="65b63-191">Move lerp time</span></span>

<span data-ttu-id="65b63-192">Объем сглаживания, применяемый к перемещению.</span><span class="sxs-lookup"><span data-stu-id="65b63-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="65b63-193">Сглаживание 0 означает отсутствие сглаживания.</span><span class="sxs-lookup"><span data-stu-id="65b63-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="65b63-194">Максимальное значение означает отсутствие изменений в значении.</span><span class="sxs-lookup"><span data-stu-id="65b63-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="65b63-195">Поворот времени лерп</span><span class="sxs-lookup"><span data-stu-id="65b63-195">Rotate lerp time</span></span>

<span data-ttu-id="65b63-196">Объем сглаживания, применяемый к повороту.</span><span class="sxs-lookup"><span data-stu-id="65b63-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="65b63-197">Сглаживание 0 означает отсутствие сглаживания.</span><span class="sxs-lookup"><span data-stu-id="65b63-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="65b63-198">Максимальное значение означает отсутствие изменений в значении.</span><span class="sxs-lookup"><span data-stu-id="65b63-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="65b63-199">Масштабирование лерп времени</span><span class="sxs-lookup"><span data-stu-id="65b63-199">Scale lerp time</span></span>

<span data-ttu-id="65b63-200">Объем сглаживания, применяемый к шкале.</span><span class="sxs-lookup"><span data-stu-id="65b63-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="65b63-201">Сглаживание 0 означает отсутствие сглаживания.</span><span class="sxs-lookup"><span data-stu-id="65b63-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="65b63-202">Максимальное значение означает отсутствие изменений в значении.</span><span class="sxs-lookup"><span data-stu-id="65b63-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="65b63-203">События манипуляции</span><span class="sxs-lookup"><span data-stu-id="65b63-203">Manipulation events</span></span>

<span data-ttu-id="65b63-204">Обработчик манипуляции предоставляет следующие события:</span><span class="sxs-lookup"><span data-stu-id="65b63-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="65b63-205">*Онманипулатионстартед*: срабатывает при начале манипуляции.</span><span class="sxs-lookup"><span data-stu-id="65b63-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="65b63-206">*Онманипулатионендед*: активируется по окончании манипуляции.</span><span class="sxs-lookup"><span data-stu-id="65b63-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="65b63-207">*Онховерстартед*: срабатывает, когда рука или контроллер наводит указатель мыши на манипулятор, NEAR или FAR.</span><span class="sxs-lookup"><span data-stu-id="65b63-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="65b63-208">*Онховерендед*: срабатывает, когда рукой или контроллер отменяет наведение указателя мыши на манипулятор, NEAR или FAR.</span><span class="sxs-lookup"><span data-stu-id="65b63-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="65b63-209">Порядок запуска событий для манипуляции:</span><span class="sxs-lookup"><span data-stu-id="65b63-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="65b63-210">*Онховерстартед*  ->  *Онманипулатионстартед*  ->  *Онманипулатионендед*  ->  *Онховерендед*</span><span class="sxs-lookup"><span data-stu-id="65b63-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="65b63-211">Если манипуляции нет, события наведения указателя по-прежнему будут выполняться в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="65b63-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="65b63-212">*Онховерстартед*  ->  *Онховерендед*</span><span class="sxs-lookup"><span data-stu-id="65b63-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="65b63-213">Физика и конфликты</span><span class="sxs-lookup"><span data-stu-id="65b63-213">Physics and collisions</span></span>

<span data-ttu-id="65b63-214">Поведение физикы можно включить, добавив компонент RigidBody в тот же объект, что и манипулятор объекта.</span><span class="sxs-lookup"><span data-stu-id="65b63-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="65b63-215">Это позволяет не только включить настройку [поведения выпуска](#release-behavior) , но и конфликты.</span><span class="sxs-lookup"><span data-stu-id="65b63-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="65b63-216">Без компонента RigidBody конфликт не работает должным образом во время манипуляции:</span><span class="sxs-lookup"><span data-stu-id="65b63-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="65b63-217">Конфликты между управляемым объектом и статическим (т. е. объектом с конфликтующим, но без RigidBody) не работают, управляемый объект передается непосредственно через статический конфликт, не затронутый.</span><span class="sxs-lookup"><span data-stu-id="65b63-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="65b63-218">Конфликты между управляемым объектом и RigidBody (т. е.</span><span class="sxs-lookup"><span data-stu-id="65b63-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="65b63-219">Объект, имеющий как RigidBody, так и RigidBody, вызывает реагирование на конфликт, но отклики и неестественные ответы отходятся.</span><span class="sxs-lookup"><span data-stu-id="65b63-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="65b63-220">В управляемом объекте также нет ответа на конфликт.</span><span class="sxs-lookup"><span data-stu-id="65b63-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="65b63-221">При добавлении RigidBody конфликты должны работать правильно.</span><span class="sxs-lookup"><span data-stu-id="65b63-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="65b63-222">Без RigidBody</span><span class="sxs-lookup"><span data-stu-id="65b63-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="65b63-223">С RigidBody</span><span class="sxs-lookup"><span data-stu-id="65b63-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="65b63-224">Эластичные (экспериментальные)</span><span class="sxs-lookup"><span data-stu-id="65b63-224">Elastics (Experimental)</span></span>

<span data-ttu-id="65b63-225">Эластичные объекты можно использовать при управлении объектами с помощью манипулятора объекта.</span><span class="sxs-lookup"><span data-stu-id="65b63-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="65b63-226">Обратите внимание, что [система эластичных](../experimental/elastic-system.md) баз данных по-прежнему находится в экспериментальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="65b63-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="65b63-227">Для включения эластичных баз данных необходимо связать существующий компонент диспетчера эластичных баз данных или создать и связать новый диспетчер эластичных баз данных с помощью `Add Elastics Manager` кнопки.</span><span class="sxs-lookup"><span data-stu-id="65b63-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="65b63-228">См. также:</span><span class="sxs-lookup"><span data-stu-id="65b63-228">See also</span></span>

- [<span data-ttu-id="65b63-229">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="65b63-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="65b63-230">Диспетчер ограничений</span><span class="sxs-lookup"><span data-stu-id="65b63-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="65b63-231">Окно миграции</span><span class="sxs-lookup"><span data-stu-id="65b63-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="65b63-232">Система эластичных БД (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="65b63-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
