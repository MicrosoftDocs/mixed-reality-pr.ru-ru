---
title: Входные действия
description: Документация по созданию входных действий в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, инпутактионс,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176811"
---
# <a name="input-actions"></a><span data-ttu-id="dbd1c-104">Входные действия</span><span class="sxs-lookup"><span data-stu-id="dbd1c-104">Input actions</span></span>

<span data-ttu-id="dbd1c-105">[**Входные действия**](input-actions.md) — это абстракции для необработанных входных данных, которые предназначены для изоляции логики приложения от определенных входных источников, производящих входные данные.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="dbd1c-106">Это может быть полезно, например, для определения действия *SELECT* и его соотнесения с левой кнопкой мыши, кнопкой на игровом поле и триггером в 6 ДОФ контроллере.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="dbd1c-107">Затем можно настроить для приложения логику прослушивания событий *выбора* входных действий вместо того, чтобы знать все различные входные данные, которые могут его создать.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="dbd1c-108">Создание действия ввода</span><span class="sxs-lookup"><span data-stu-id="dbd1c-108">Creating an input action</span></span>

<span data-ttu-id="dbd1c-109">входные действия настраиваются в **профиле входных действий** во *входном системном профиле* в компоненте набор средств смешанной реальности указание имени действия и типа входных данных (*ограничение оси*), с которым она может быть сопоставлена:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="dbd1c-110">Это наиболее часто используемые значения для **ограничения оси**:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="dbd1c-111">Ограничение оси</span><span class="sxs-lookup"><span data-stu-id="dbd1c-111">Axis Constraint</span></span> | <span data-ttu-id="dbd1c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="dbd1c-112">Description</span></span>
--- | ---
<span data-ttu-id="dbd1c-113">Цифровой</span><span class="sxs-lookup"><span data-stu-id="dbd1c-113">Digital</span></span> | <span data-ttu-id="dbd1c-114">Включение и выключение входных данных, таких как двоичная кнопка на планшете или в мыши.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="dbd1c-115">Одна ось</span><span class="sxs-lookup"><span data-stu-id="dbd1c-115">Single Axis</span></span> | <span data-ttu-id="dbd1c-116">Аналоговый ввод на одной оси, например Аналоговый триггер на игровом планшете.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="dbd1c-117">Двойная ось</span><span class="sxs-lookup"><span data-stu-id="dbd1c-117">Dual Axis</span></span> | <span data-ttu-id="dbd1c-118">Аналоговый ввод с двойной оси, например аналоговый стик.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="dbd1c-119">Шесть ДОФ</span><span class="sxs-lookup"><span data-stu-id="dbd1c-119">Six Dof</span></span> | <span data-ttu-id="dbd1c-120">Трехмерная часть с переводом и поворотом, например с помощью 6 ДОФ контроллеров.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="dbd1c-121">Полный список можно найти в [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="dbd1c-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="dbd1c-122">Сопоставление входных данных с действиями</span><span class="sxs-lookup"><span data-stu-id="dbd1c-122">Mapping input to actions</span></span>

<span data-ttu-id="dbd1c-123">Способ соответствия входных данных и действий зависит от типа источника входных данных.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="dbd1c-124">Входные данные контроллера</span><span class="sxs-lookup"><span data-stu-id="dbd1c-124">Controller input</span></span>

<span data-ttu-id="dbd1c-125">Перейдите в **профиль сопоставления входных данных контроллера** в *системном профиле входной системы*.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="dbd1c-126">Здесь вы найдете список всех поддерживаемых контроллеров:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="dbd1c-127">Выберите тот, который требуется настроить, и появится диалоговое окно со всеми входными данными контроллера, позволяющими задать действие для каждого из них:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="dbd1c-128">Ввод речи</span><span class="sxs-lookup"><span data-stu-id="dbd1c-128">Speech input</span></span>

<span data-ttu-id="dbd1c-129">В **профиле команды распознавания речи** в *системном профиле входной системы* можно найти список команд речи, определенных в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="dbd1c-130">Чтобы связать один из них с действием, просто выберите его в раскрывающемся списке *действий* .</span><span class="sxs-lookup"><span data-stu-id="dbd1c-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="dbd1c-131">Ввод с жестом</span><span class="sxs-lookup"><span data-stu-id="dbd1c-131">Gesture input</span></span>

<span data-ttu-id="dbd1c-132">**Профиль жестов** в *системном профиле входных данных* содержит все определенные жесты.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="dbd1c-133">Каждое из них можно связать с действием, выбрав его в раскрывающемся списке *действий* .</span><span class="sxs-lookup"><span data-stu-id="dbd1c-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="dbd1c-134">Обработка входных действий</span><span class="sxs-lookup"><span data-stu-id="dbd1c-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="dbd1c-135">В настоящее время только входные действия *цифрового* типа могут обрабатываться с помощью методов, описанных в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="dbd1c-136">Для других типов действий необходимо вместо этого выполнять обработку непосредственно событий для соответствующих входных данных.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="dbd1c-137">Например, для выполнения 6 действия ДОФ, сопоставленного с входными данными контроллера, необходимо использовать [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) с T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="dbd1c-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="dbd1c-138">Самый простой способ обработать входные действия — использовать [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) сценарий.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="dbd1c-139">Это позволяет определить действие, которое требуется прослушивать и реагировать на события, запущенные и завершенные действием, с помощью событий Unity.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="dbd1c-140">Если требуется больший контроль, можно реализовать [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) интерфейс непосредственно в скрипте.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="dbd1c-141">Дополнительные сведения об обработке событий с помощью интерфейсов обработчиков см. в разделе [**входные события**](input-events.md) .</span><span class="sxs-lookup"><span data-stu-id="dbd1c-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="dbd1c-142">Примеры</span><span class="sxs-lookup"><span data-stu-id="dbd1c-142">Examples</span></span>

<span data-ttu-id="dbd1c-143">См `MRTK/Examples/Demos/Input/Scenes/InputActions` . пример сцены, показывающий, как создать действие, преобразовать его в входные данные контроллера, речи и жестов и использовать для поворота объекта в команде.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
