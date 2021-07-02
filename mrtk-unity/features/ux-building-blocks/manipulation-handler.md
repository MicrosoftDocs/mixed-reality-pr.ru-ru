---
title: Обработчик манипуляции
description: Документация по обработчику манипуляции в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, манипуляция
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176635"
---
# <a name="manipulation-handler"></a><span data-ttu-id="c01ac-104">Обработчик манипуляции</span><span class="sxs-lookup"><span data-stu-id="c01ac-104">Manipulation handler</span></span>

![Обработчик манипуляции](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="c01ac-106">Сценарий *манипулатионхандлер* позволяет сделать объект перемещаемым, масштабируемым и ротатабле, используя одну или две руки.</span><span class="sxs-lookup"><span data-stu-id="c01ac-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="c01ac-107">Манипуляции могут быть ограничены, так что она допускает только определенные виды преобразования.</span><span class="sxs-lookup"><span data-stu-id="c01ac-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="c01ac-108">этот сценарий работает с различными типами входных данных, в том числе HoloLens 2ным вводом, HoloLensом (1) входным жестом, а также с помощью впечатляющих входных контроллеров гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="c01ac-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="c01ac-109">Использование обработчика манипуляции</span><span class="sxs-lookup"><span data-stu-id="c01ac-109">How to use the manipulation handler</span></span>

<span data-ttu-id="c01ac-110">Добавьте `ManipulationHandler` компонент скрипта в GameObject.</span><span class="sxs-lookup"><span data-stu-id="c01ac-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="c01ac-111">Не забудьте добавить к объекту объект, соответствующий заданным границам.</span><span class="sxs-lookup"><span data-stu-id="c01ac-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="c01ac-112">Чтобы сделать объект ответом на близкие входные данные, добавьте `NearInteractionGrabbable` также скрипт.</span><span class="sxs-lookup"><span data-stu-id="c01ac-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Использование обработчика манипуляции в редакторе Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="c01ac-114">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="c01ac-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="c01ac-115">**Преобразование узла** Преобразование, которое будет перенесено.</span><span class="sxs-lookup"><span data-stu-id="c01ac-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="c01ac-116">По умолчанию используется объект компонента.</span><span class="sxs-lookup"><span data-stu-id="c01ac-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="c01ac-117">**Тип манипуляции** Указывает, можно ли манипулировать объектом с помощью одной руки, двух рук или и того, и другого.</span><span class="sxs-lookup"><span data-stu-id="c01ac-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="c01ac-118">*Только один рукой*</span><span class="sxs-lookup"><span data-stu-id="c01ac-118">*One handed only*</span></span>
* <span data-ttu-id="c01ac-119">*Только две руки*</span><span class="sxs-lookup"><span data-stu-id="c01ac-119">*Two handed only*</span></span>
* <span data-ttu-id="c01ac-120">*Один и два руки*</span><span class="sxs-lookup"><span data-stu-id="c01ac-120">*One and Two handed*</span></span>

<span data-ttu-id="c01ac-121">**Тип двунаправленной манипуляции**</span><span class="sxs-lookup"><span data-stu-id="c01ac-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="c01ac-122">*Scale*: разрешено только масштабирование.</span><span class="sxs-lookup"><span data-stu-id="c01ac-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="c01ac-123">*Поворот*: разрешен только поворот.</span><span class="sxs-lookup"><span data-stu-id="c01ac-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="c01ac-124">*Перемещение шкалы*: перемещение и масштабирование разрешены.</span><span class="sxs-lookup"><span data-stu-id="c01ac-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="c01ac-125">*Перемещение вращения*. Допускается перемещение и вращение.</span><span class="sxs-lookup"><span data-stu-id="c01ac-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="c01ac-126">*Вращение шкалы*. Допускается вращение и масштабирование.</span><span class="sxs-lookup"><span data-stu-id="c01ac-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="c01ac-127">*Перемещение вращения шкалы*. Допускается перемещение, вращение и масштабирование.</span><span class="sxs-lookup"><span data-stu-id="c01ac-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Обработчик манипуляции](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="c01ac-129">**Разрешить далекое манипуляции** Указывает, можно ли выполнять манипуляции с помощью дальнего взаимодействия с указателями.</span><span class="sxs-lookup"><span data-stu-id="c01ac-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="c01ac-130">**Режим поворота одного руки рядом с** Указывает, как будет вести себя объект, когда он помещается с одной рукой или контроллером вблизи.</span><span class="sxs-lookup"><span data-stu-id="c01ac-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="c01ac-131">**Режим поворота одного руки** Указывает, как будет вести себя объект, когда он заменяется одной рукой или контроллером.</span><span class="sxs-lookup"><span data-stu-id="c01ac-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="c01ac-132">**Параметры режима поворота одного руки** Указывает, как объект будет вращаться, когда он помещается с одной рукой.</span><span class="sxs-lookup"><span data-stu-id="c01ac-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="c01ac-133">*Сохранить исходный поворот*: объект не вращается при перемещении</span><span class="sxs-lookup"><span data-stu-id="c01ac-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="c01ac-134">*Поддерживать поворот на пользователя*: сохраняет исходный поворот объекта для оси X/Y для пользователя</span><span class="sxs-lookup"><span data-stu-id="c01ac-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="c01ac-135">*По центру тяжести поддерживать поворот на пользователя*: исходный поворот объекта выполняется пользователем, но делает объект вертикальным.</span><span class="sxs-lookup"><span data-stu-id="c01ac-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="c01ac-136">Используется для объектов с элементом управления "границы".</span><span class="sxs-lookup"><span data-stu-id="c01ac-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="c01ac-137">*Пользователь лица*: гарантирует, что объект всегда является пользователем.</span><span class="sxs-lookup"><span data-stu-id="c01ac-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="c01ac-138">Полезно для планшетов и панелей.</span><span class="sxs-lookup"><span data-stu-id="c01ac-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="c01ac-139">*Лицевой стороной от пользователя*: гарантирует, что объект всегда будет отказываться от пользователя.</span><span class="sxs-lookup"><span data-stu-id="c01ac-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="c01ac-140">Полезно для планшетов и панелей, которые настроены в обратном направлении.</span><span class="sxs-lookup"><span data-stu-id="c01ac-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="c01ac-141">*Повернуть на центр Object Center*: работает только для четко сформулированных рук и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="c01ac-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="c01ac-142">Поворот объекта с помощью поворота руки или контроллера, но с точки зрения центра объектов.</span><span class="sxs-lookup"><span data-stu-id="c01ac-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="c01ac-143">Полезно для проверки на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="c01ac-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="c01ac-144">*Повернуть точку захвата*: работает только для четко сформулированных рук и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="c01ac-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="c01ac-145">Поворачивайте объект так, как если бы он удерживался вручную или контроллером.</span><span class="sxs-lookup"><span data-stu-id="c01ac-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="c01ac-146">Полезно для проверки.</span><span class="sxs-lookup"><span data-stu-id="c01ac-146">Useful for inspection.</span></span>

<span data-ttu-id="c01ac-147">**Поведение выпуска** При освобождении объекта укажите его поведение физического перемещения.</span><span class="sxs-lookup"><span data-stu-id="c01ac-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="c01ac-148">Требуется компонент RigidBody для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="c01ac-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="c01ac-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="c01ac-149">*Nothing*</span></span>
* <span data-ttu-id="c01ac-150">*Все*</span><span class="sxs-lookup"><span data-stu-id="c01ac-150">*Everything*</span></span>
* <span data-ttu-id="c01ac-151">*Удерживать скорость*</span><span class="sxs-lookup"><span data-stu-id="c01ac-151">*Keep Velocity*</span></span>
* <span data-ttu-id="c01ac-152">*обеспечение скорости Angular*</span><span class="sxs-lookup"><span data-stu-id="c01ac-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="c01ac-153">**Ограничения при повороте** Указывает, на какой оси объект будет вращаться при взаимодействии с.</span><span class="sxs-lookup"><span data-stu-id="c01ac-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="c01ac-154">*Нет*</span><span class="sxs-lookup"><span data-stu-id="c01ac-154">*None*</span></span>
* <span data-ttu-id="c01ac-155">*Только ось X*</span><span class="sxs-lookup"><span data-stu-id="c01ac-155">*X-Axis Only*</span></span>
* <span data-ttu-id="c01ac-156">*Только ось Y*</span><span class="sxs-lookup"><span data-stu-id="c01ac-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="c01ac-157">*Только ось Z*</span><span class="sxs-lookup"><span data-stu-id="c01ac-157">*Z-Axis Only*</span></span>

<span data-ttu-id="c01ac-158">**Использовать локальное пространство для ограничения** Переключатель для переключения между применением ограничений в отношении оси мира или локальной оси пространства.</span><span class="sxs-lookup"><span data-stu-id="c01ac-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="c01ac-159">**Ограничения на перемещение**</span><span class="sxs-lookup"><span data-stu-id="c01ac-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="c01ac-160">*Нет*</span><span class="sxs-lookup"><span data-stu-id="c01ac-160">*None*</span></span>
* <span data-ttu-id="c01ac-161">*Исправление расстояния от головного заголовков*</span><span class="sxs-lookup"><span data-stu-id="c01ac-161">*Fix distance from head*</span></span>

<span data-ttu-id="c01ac-162">**Сглаживание активно** Указывает, активно ли сглаживание.</span><span class="sxs-lookup"><span data-stu-id="c01ac-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="c01ac-163">**Величина сглаживания одна рука** Объем сглаживания, применяемый к перемещению, масштабированию, повороту.</span><span class="sxs-lookup"><span data-stu-id="c01ac-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="c01ac-164">Сглаживание 0 означает отсутствие сглаживания.</span><span class="sxs-lookup"><span data-stu-id="c01ac-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="c01ac-165">Максимальное значение означает отсутствие изменений в значении.</span><span class="sxs-lookup"><span data-stu-id="c01ac-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="c01ac-166">События</span><span class="sxs-lookup"><span data-stu-id="c01ac-166">Events</span></span>

<span data-ttu-id="c01ac-167">Обработчик манипуляции предоставляет следующие события:</span><span class="sxs-lookup"><span data-stu-id="c01ac-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="c01ac-168">*Онманипулатионстартед*: срабатывает при начале манипуляции.</span><span class="sxs-lookup"><span data-stu-id="c01ac-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="c01ac-169">*Онманипулатионендед*: активируется по окончании манипуляции.</span><span class="sxs-lookup"><span data-stu-id="c01ac-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="c01ac-170">*Онховерстартед*: срабатывает, когда рука или контроллер наводит указатель мыши на манипулятор, NEAR или FAR.</span><span class="sxs-lookup"><span data-stu-id="c01ac-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="c01ac-171">*Онховерендед*: срабатывает, когда рукой или контроллер отменяет наведение указателя мыши на манипулятор, NEAR или FAR.</span><span class="sxs-lookup"><span data-stu-id="c01ac-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
