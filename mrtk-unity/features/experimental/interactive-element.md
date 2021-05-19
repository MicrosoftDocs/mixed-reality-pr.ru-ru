---
title: Интерактивный элемент
description: Документация по Интерактивилемент МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, интерактивный элемент, взаимодействие
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144767"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="739bb-104">Interactive, элемент [экспериментальный]</span><span class="sxs-lookup"><span data-stu-id="739bb-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="739bb-105">Упрощенная централизованная точка входа в систему ввода МРТК.</span><span class="sxs-lookup"><span data-stu-id="739bb-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="739bb-106">Содержит методы управления состоянием, управление событиями и логику настройки состояния для основных состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="739bb-107">Интерактивный элемент — это экспериментальная функция, которая поддерживается в Unity 2019,3 и выше, так как она использует возможности, новые для Unity 2019,3: [сериализация ссылки](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="739bb-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="739bb-108">Интерактивный инспектор элементов</span><span class="sxs-lookup"><span data-stu-id="739bb-108">Interactive Element Inspector</span></span>

<span data-ttu-id="739bb-109">В режиме воспроизведения интерактивный инспектор элементов предоставляет визуальную обратную связь, которая указывает, является ли текущее состояние активным.</span><span class="sxs-lookup"><span data-stu-id="739bb-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="739bb-110">Если состояние активно, оно будет выделено голубым цветом.</span><span class="sxs-lookup"><span data-stu-id="739bb-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="739bb-111">Если состояние неактивно, цвет не изменяется.</span><span class="sxs-lookup"><span data-stu-id="739bb-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="739bb-112">Номера, расположенные рядом с состояниями в инспекторе, являются значениями состояния, если состояние активно, а значение равно 1, если состояние неактивно, то это значение равно 0.</span><span class="sxs-lookup"><span data-stu-id="739bb-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Интерактивный элемент с взаимодействием с виртуальной стороны](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="739bb-114">Основные состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-114">Core States</span></span>

<span data-ttu-id="739bb-115">Интерактивный элемент содержит основные состояния и поддерживает добавление [пользовательских состояний](#custom-states).</span><span class="sxs-lookup"><span data-stu-id="739bb-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="739bb-116">Основное состояние — это ядро, которое уже имеет логику настройки состояния, определенную в `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="739bb-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="739bb-117">Ниже приведен список текущих состояний ядра на основе ввода:</span><span class="sxs-lookup"><span data-stu-id="739bb-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="739bb-118">Текущие основные состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-118">Current Core States</span></span>

- [<span data-ttu-id="739bb-119">Default</span><span class="sxs-lookup"><span data-stu-id="739bb-119">Default</span></span>](#default-state) 

<span data-ttu-id="739bb-120">Основные состояния в ближайшем и дальнем взаимодействии:</span><span class="sxs-lookup"><span data-stu-id="739bb-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="739bb-121">Фокус</span><span class="sxs-lookup"><span data-stu-id="739bb-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="739bb-122">Основные состояния взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="739bb-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="739bb-123">Фокус рядом</span><span class="sxs-lookup"><span data-stu-id="739bb-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="739bb-124">Сенсорный ввод</span><span class="sxs-lookup"><span data-stu-id="739bb-124">Touch</span></span>](#touch-state)

<span data-ttu-id="739bb-125">Основные состояния взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="739bb-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="739bb-126">Сосредоточиться на далеком</span><span class="sxs-lookup"><span data-stu-id="739bb-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="739bb-127">Выберите FAR</span><span class="sxs-lookup"><span data-stu-id="739bb-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="739bb-128">Другие основные состояния:</span><span class="sxs-lookup"><span data-stu-id="739bb-128">Other Core States:</span></span>
- [<span data-ttu-id="739bb-129">Выполнен переход</span><span class="sxs-lookup"><span data-stu-id="739bb-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="739bb-130">Включить и выключить</span><span class="sxs-lookup"><span data-stu-id="739bb-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="739bb-131">Ключевое слово речи</span><span class="sxs-lookup"><span data-stu-id="739bb-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="739bb-132">Добавление основного состояния с помощью инспектора</span><span class="sxs-lookup"><span data-stu-id="739bb-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="739bb-133">В инспекторе для интерактивного элемента перейдите к разделу **Добавление основного состояния** .</span><span class="sxs-lookup"><span data-stu-id="739bb-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Добавление основного состояния с помощью инспектора](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="739bb-135">Нажмите кнопку **выбрать состояние** , чтобы выбрать основное состояние для добавления.</span><span class="sxs-lookup"><span data-stu-id="739bb-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="739bb-136">Состояния в меню сортируются по типу взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-136">The states in the menu are sorted by interaction type.</span></span>

    ![Добавление основного состояния с помощью инспектора с выбранным состоянием](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="739bb-138">Откройте свертывание конфигурации событий, чтобы просмотреть события и свойства, связанные с этим состоянием.</span><span class="sxs-lookup"><span data-stu-id="739bb-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Добавление основного состояния с помощью инспектора и конфигурации событий](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="739bb-140">Добавление основного состояния с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="739bb-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="739bb-141">Используйте `AddNewState(stateName)` метод, чтобы добавить основное состояние.</span><span class="sxs-lookup"><span data-stu-id="739bb-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="739bb-142">Чтобы получить список доступных имен основных состояний, используйте `CoreInteractionState` перечисление.</span><span class="sxs-lookup"><span data-stu-id="739bb-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="739bb-143">Внутренняя структура состояний</span><span class="sxs-lookup"><span data-stu-id="739bb-143">States Internal Structure</span></span> 

<span data-ttu-id="739bb-144">Состояния в интерактивном элементе имеют тип `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="739bb-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="739bb-145">`InteractionState`Содержит следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="739bb-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="739bb-146">**Имя**: имя состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="739bb-147">**Значение**: значение состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-147">**Value**: The state value.</span></span>  <span data-ttu-id="739bb-148">Если состояние — ON, то значение состояния равно 1.</span><span class="sxs-lookup"><span data-stu-id="739bb-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="739bb-149">Если состояние равно OFF, то значение состояния равно 0.</span><span class="sxs-lookup"><span data-stu-id="739bb-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="739bb-150">**Активный**: состояние сейчас активно.</span><span class="sxs-lookup"><span data-stu-id="739bb-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="739bb-151">Значение активного свойства равно true, если состояние равно ON, и false, если состояние — OFF.</span><span class="sxs-lookup"><span data-stu-id="739bb-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="739bb-152">**Тип взаимодействия**: тип взаимодействия состояния — это тип взаимодействия, для которого предназначено состояние.</span><span class="sxs-lookup"><span data-stu-id="739bb-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="739bb-153">`None`: Не поддерживает ни одну форму взаимодействия с входными данными.</span><span class="sxs-lookup"><span data-stu-id="739bb-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="739bb-154">`Near`: Приближается поддержка взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="739bb-155">Входные данные считаются близкими к взаимодействию, когда у манипулятора руки есть прямое Контактное лицо с другим игровым объектом, т. е. в положении, что накрывающаяся рука близка к положению игрового объекта в мировом пространстве.</span><span class="sxs-lookup"><span data-stu-id="739bb-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="739bb-156">`Far`: Поддержка дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="739bb-157">Входные данные считаются намного взаимодействием, если прямое обращение к игровому объекту не требуется.</span><span class="sxs-lookup"><span data-stu-id="739bb-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="739bb-158">Например, вход с помощью контроллера Ray или взгляда считается гораздо более безопасным входом.</span><span class="sxs-lookup"><span data-stu-id="739bb-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="739bb-159">`NearAndFar`: Включает поддержку практически и дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="739bb-160">`Other`: Независимая поддержка взаимодействия по указателям.</span><span class="sxs-lookup"><span data-stu-id="739bb-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="739bb-161">**Конфигурация события**. Конфигурация события состояния — это точка входа в профиле сериализованных событий.</span><span class="sxs-lookup"><span data-stu-id="739bb-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="739bb-162">Все эти свойства задаются внутренне в элементе, `State Manager` содержащемся в интерактивном элементе.</span><span class="sxs-lookup"><span data-stu-id="739bb-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="739bb-163">Для изменения состояний используйте следующие вспомогательные методы:</span><span class="sxs-lookup"><span data-stu-id="739bb-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="739bb-164">**Вспомогательные методы настройки состояния**</span><span class="sxs-lookup"><span data-stu-id="739bb-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="739bb-165">Получение конфигурации события состояния зависит от самого состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="739bb-166">Каждое основное состояние имеет конкретный тип конфигурации событий, который описан ниже в разделах, описывающих каждое состояние ядра.</span><span class="sxs-lookup"><span data-stu-id="739bb-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="739bb-167">Ниже приведен обобщенный пример получения конфигурации события состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="739bb-168">Состояние по умолчанию</span><span class="sxs-lookup"><span data-stu-id="739bb-168">Default State</span></span>

<span data-ttu-id="739bb-169">Состояние по умолчанию всегда имеется в интерактивном элементе.</span><span class="sxs-lookup"><span data-stu-id="739bb-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="739bb-170">Это состояние будет активным, только если все остальные состояния неактивны.</span><span class="sxs-lookup"><span data-stu-id="739bb-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="739bb-171">Если любое другое состояние становится активным, состояние по умолчанию будет отключено внутренним.</span><span class="sxs-lookup"><span data-stu-id="739bb-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="739bb-172">Интерактивный элемент инициализируется с состояниями по умолчанию и фокусом, присутствующими в списке состояний.</span><span class="sxs-lookup"><span data-stu-id="739bb-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="739bb-173">Состояние по умолчанию всегда должно присутствовать в списке состояний.</span><span class="sxs-lookup"><span data-stu-id="739bb-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="739bb-174">Получение событий состояния по умолчанию</span><span class="sxs-lookup"><span data-stu-id="739bb-174">Getting Default State Events</span></span>

<span data-ttu-id="739bb-175">Тип конфигурации события для состояния по умолчанию: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="739bb-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="739bb-176">Состояние фокусировки</span><span class="sxs-lookup"><span data-stu-id="739bb-176">Focus State</span></span>

<span data-ttu-id="739bb-177">Состояние фокусировки — это состояние почти и намного взаимодействий, которое можно рассматривать как эквивалентное наведении на смешанную реальность.</span><span class="sxs-lookup"><span data-stu-id="739bb-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="739bb-178">Отличительным фактором между ближайшим и дальнеим взаимодействием для состояния фокуса является текущий активный тип указателя.</span><span class="sxs-lookup"><span data-stu-id="739bb-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="739bb-179">Если тип указателя для состояния фокуса является указателем на Вставка, то взаимодействие считается практически взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="739bb-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="739bb-180">Если первичный указатель не является указателем на Вставка, взаимодействие считается далеко взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="739bb-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="739bb-181">По умолчанию состояние фокусировки представлено в интерактивном элементе.</span><span class="sxs-lookup"><span data-stu-id="739bb-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="739bb-182"> 
 Поведение ![ состояния фокуса Состояние фокусировки с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="739bb-183"> 
 Инспектор ![ состояния фокуса Состояние фокусировки в Инпсектор](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;739bb-184&quot;>Получение событий состояния фокуса</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;739bb-185&quot;>Тип конфигурации события для состояния фокусировки: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="739bb-186">Основное внимание уделяется Практическиму поведению фокуса VS</span><span class="sxs-lookup"><span data-stu-id="739bb-186">Focus Near vs Focus Far Behavior</span></span> 

![Сосредоточьтесь рядом с взаимодействием Virtual руки](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="739bb-188">Фокус рядом с состоянием</span><span class="sxs-lookup"><span data-stu-id="739bb-188">Focus Near State</span></span>

<span data-ttu-id="739bb-189">Фокус находится рядом с состоянием, когда возникает событие Focus, а первичный указатель — это указатель, указывающий на приближение взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="739bb-190">**Фокус на поведение** 
 ![ близкого состояния Сосредоточьтесь рядом с состоянием и взаимодействием с виртуальной рукой](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="739bb-191">**Сфокусироваться рядом с инспектором состояний** 
 ![ Фокус на компоненте, расположенном в инспекторе](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;739bb-192&quot;>Получение событий состояния Фокуснеар</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;739bb-193&quot;>Тип конфигурации события для состояния Фокуснеар: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="739bb-194">Фокус на далеком состоянии</span><span class="sxs-lookup"><span data-stu-id="739bb-194">Focus Far State</span></span>

<span data-ttu-id="739bb-195">Состояние "фокус находится далеко" устанавливается, когда основной указатель не является указателем на Вставка.</span><span class="sxs-lookup"><span data-stu-id="739bb-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="739bb-196">Например, указатель по умолчанию на луч и указатель на ГГВ (взгляд, жест, голоса) рассматриваются как дальнее несколько указателей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="739bb-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="739bb-197">**Поведение при наведении** 
 ![ фокуса на состояние Состояние фокусировки с взаимодействием Virtual руки](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="739bb-198"> 
 Инспектор ![ состояния фокуса Фокус на далеком компоненте в инспекторе](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;739bb-199&quot;>Получение событий состояния фокуса</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;739bb-200&quot;>Тип конфигурации события для состояния Фокусфар: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="739bb-201">Состояние касания</span><span class="sxs-lookup"><span data-stu-id="739bb-201">Touch State</span></span>

<span data-ttu-id="739bb-202">Сенсорный режим — это состояние близкого взаимодействия, которое задается, когда Наладонная рука обращается к объекту напрямую.</span><span class="sxs-lookup"><span data-stu-id="739bb-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="739bb-203">Прямое касание означает, что палец указателя руки очень близко к всему миру объекта.</span><span class="sxs-lookup"><span data-stu-id="739bb-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="739bb-204">По умолчанию `NearInteractionTouchableVolume` компонент прикрепляется к объекту, если в список состояний добавляется сенсорный режим.</span><span class="sxs-lookup"><span data-stu-id="739bb-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="739bb-205">`NearInteractionTouchableVolume` `NearInteractionTouchable` Для обнаружения событий касания требуется наличие компонента или.</span><span class="sxs-lookup"><span data-stu-id="739bb-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="739bb-206">Разница между `NearInteractionTouchableVolume` и заключается в том `NearInteractionTouchable` , что `NearInteractionTouchableVolume` обнаруживает касание на основе конфликтующего объекта и `NearInteractionTouchable` обнаруживает касание в определенной области плоскости.</span><span class="sxs-lookup"><span data-stu-id="739bb-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="739bb-207"> 
 Поведение ![ сенсорного состояния Сенсорный режим с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="739bb-208"> 
 Инспектор ![ состояния касания Компонент состояния касания в инспекторе](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;739bb-209&quot;>Получение событий состояния касания</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;739bb-210&quot;>Тип конфигурации событий для состояния касания: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="739bb-211">Выбор дальнего состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-211">Select Far State</span></span>

<span data-ttu-id="739bb-212">Область выбор дальнего состояния является полевой `IMixedRealityPointerHandler` .</span><span class="sxs-lookup"><span data-stu-id="739bb-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="739bb-213">Это состояние является гораздо более взаимодействием, которое обнаруживает гораздо взаимодействие щелчком мыши (AIR-TAP) и удерживается с помощью дальнего указателя взаимодействия, такого как указатель на контроллер по умолчанию или указатель ГГВ.</span><span class="sxs-lookup"><span data-stu-id="739bb-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="739bb-214">В поле Выбор дальнего состояния есть параметр под заголовком конфигурация события с именем `Global` .</span><span class="sxs-lookup"><span data-stu-id="739bb-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="739bb-215">Если `Global` имеет значение true, то `IMixedRealityPointerHandler` регистрируется как глобальный обработчик входных данных.</span><span class="sxs-lookup"><span data-stu-id="739bb-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="739bb-216">Фокус на объекте не требуется для активации входных системных событий, если обработчик зарегистрирован как глобальный.</span><span class="sxs-lookup"><span data-stu-id="739bb-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="739bb-217">Например, если пользователь хочет, чтобы во время выполнения жеста воздушного касания/выбора захотелся, независимо от объекта в фокусе, установите значение `Global` true.</span><span class="sxs-lookup"><span data-stu-id="739bb-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="739bb-218">**Выбор состояния дальнего действия** 
 ![ Выберите далеко с помощью взаимодействия Virtual рука](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="739bb-219">**Выбрать инспектор** 
 ![ дальнего состояния Выбор дальнего компонента в инспекторе](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;739bb-220&quot;>Получение событий выбора дальнего состояния</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;739bb-221&quot;>Тип конфигурации события для состояния Селектфар: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="739bb-222">Выбранное состояние</span><span class="sxs-lookup"><span data-stu-id="739bb-222">Clicked State</span></span>

<span data-ttu-id="739bb-223">Выбранное состояние активируется при дальнем взаимодействии по умолчанию (выбор дальнего состояния).</span><span class="sxs-lookup"><span data-stu-id="739bb-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="739bb-224">Это состояние внутренне переключается в on, вызывает событие onclickd и сразу же переключается на OFF.</span><span class="sxs-lookup"><span data-stu-id="739bb-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="739bb-225">Визуальная обратная связь в инспекторе, основанном на действии состояния, отсутствует для состояния щелчка, так как она переключается, а затем немедленно выключается.</span><span class="sxs-lookup"><span data-stu-id="739bb-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="739bb-226"> 
 Поведение ![ при выборе состояния Выбранное состояние с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="739bb-227"> 
 Инспектор ![ состояний нажатия Щелкните компонент состояния в инспекторе.](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="739bb-228">**Пример состояния "почти и далеко"**</span><span class="sxs-lookup"><span data-stu-id="739bb-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="739bb-229">Выбранное состояние можно активировать с помощью дополнительных точек входа с помощью `interactiveElement.TriggerClickedState()` метода.</span><span class="sxs-lookup"><span data-stu-id="739bb-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="739bb-230">Например, если пользователю требуется близкое взаимодействие для активации щелчка на объекте, то он будет добавлять `TriggerClickedState()` метод в качестве прослушивателя в состоянии касания.</span><span class="sxs-lookup"><span data-stu-id="739bb-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![Почти и далеко с взаимодействием с виртуальными руками](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;739bb-232&quot;>Получение событий состояния щелчков</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;739bb-233&quot;>Тип конфигурации событий для состояния щелчка: `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="739bb-234">Включение и выключение состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="739bb-235">Переключатели и выключенные состояния являются парой и должны быть представлены для поведений переключения.</span><span class="sxs-lookup"><span data-stu-id="739bb-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="739bb-236">По умолчанию состояния переключателя и выключения запускаются с помощью дальнего щелчка (выберите дальнее состояние).</span><span class="sxs-lookup"><span data-stu-id="739bb-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="739bb-237">По умолчанию состояние отключения включается при запуске, что означает, что переключатель будет инициализирован в OFF.</span><span class="sxs-lookup"><span data-stu-id="739bb-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="739bb-238">Если пользователь хочет, чтобы состояние переключения было активным при запуске, в окне переключение в состояние установлено значение `IsSelectedOnStart` true.</span><span class="sxs-lookup"><span data-stu-id="739bb-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="739bb-239">**Тогглеон и отключение поведения состояния** 
 ![ Включение и отключение переключателей с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="739bb-240">**Тогглеон и переключение инспектора состояний** 
 ![ Переключить компонент в инспекторе](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="739bb-241">**Пример состояния переключателя NEAR и Far**</span><span class="sxs-lookup"><span data-stu-id="739bb-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="739bb-242">Как и в случае щелчка состояния, параметр переключения состояния может иметь несколько точек входа с помощью `interactiveElement.SetToggleStates()` метода.</span><span class="sxs-lookup"><span data-stu-id="739bb-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="739bb-243">Например, если пользователь хочет коснуться в качестве дополнительной точки входа для задания состояния переключения, они добавляют `SetToggleStates()` метод к одному из событий в состоянии касания.</span><span class="sxs-lookup"><span data-stu-id="739bb-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Переключение почти и далеко с помощью взаимодействия между виртуальными руками](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;739bb-245&quot;>Получение или выключение событий состояния</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;739bb-246&quot;>Тип конфигурации события для состояния Тогглеон: `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;739bb-247&quot;>Тип конфигурации события для состояния Тогглеофф: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="739bb-248">Состояние ключевого слова речи</span><span class="sxs-lookup"><span data-stu-id="739bb-248">Speech Keyword State</span></span>

<span data-ttu-id="739bb-249">Состояние ключевого слова речи прослушивает ключевые слова, определенные в профиле речи смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="739bb-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="739bb-250">Все новые ключевые слова должны быть зарегистрированы в профиле голосовых команд до выполнения (шаги ниже).</span><span class="sxs-lookup"><span data-stu-id="739bb-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="739bb-251">Поведение состояния ключевого **слова речи** 
 ![ Ключевое слово Speech с виртуальным взаимодействием](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="739bb-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="739bb-252">Инспектор состояния ключевого **слова речи** 
 ![ Компонент голосовых ключевых слов в инспекторе](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="739bb-253">Состояние ключевого слова речи было активировано в редакторе, нажав клавишу F5 в приведенном выше GIF.</span><span class="sxs-lookup"><span data-stu-id="739bb-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="739bb-254">Настройка в редакторе тестирование распознавания речи описана ниже.</span><span class="sxs-lookup"><span data-stu-id="739bb-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="739bb-255">Как зарегистрировать голосовую команду или ключевое слово</span><span class="sxs-lookup"><span data-stu-id="739bb-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="739bb-256">Выбор игрового объекта **микседреалититулкит**</span><span class="sxs-lookup"><span data-stu-id="739bb-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="739bb-257">Выберите **Копировать и настроить** текущий профиль</span><span class="sxs-lookup"><span data-stu-id="739bb-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="739bb-258">Перейдите к разделу вход и выберите **клонировать** , чтобы разрешить изменение входного профиля.</span><span class="sxs-lookup"><span data-stu-id="739bb-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="739bb-259">Прокрутите вниз до раздела "речь" во входном профиле и клонировать профиль речи</span><span class="sxs-lookup"><span data-stu-id="739bb-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Профиль ключевых слов речи в игровом объекте МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="739bb-261">Выберите команду "добавить новую речь"</span><span class="sxs-lookup"><span data-stu-id="739bb-261">Select Add a New Speech Command</span></span>

    ![Добавление нового ключевого слова для речи в профиле МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="739bb-263">Введите ключевое слово New.</span><span class="sxs-lookup"><span data-stu-id="739bb-263">Enter the new keyword.</span></span> <span data-ttu-id="739bb-264">Необязательно. Измените значение KeyCode на F5 (или другой KeyCode), чтобы разрешить тестирование в редакторе.</span><span class="sxs-lookup"><span data-stu-id="739bb-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Настройка ключевого слова речи в профиле МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="739bb-266">Вернитесь к инспектору состояний ключевых слов интерактивного речевого элемента и выберите **Добавить ключевое слово** .</span><span class="sxs-lookup"><span data-stu-id="739bb-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Добавление ключевого слова в компонент интерактивного элемента](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Проверка и регистрация ключевых слов](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="739bb-269">Введите новое ключевое слово, которое было только что зарегистрировано в профиле речи</span><span class="sxs-lookup"><span data-stu-id="739bb-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Ввод ключевого слова New Speech](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="739bb-271">Чтобы проверить состояние ключевого слова речи в редакторе, нажмите кнопку KeyCode, которая была определена на шаге 6 (F5), чтобы имитировать событие распознавания ключевого слова Speech.</span><span class="sxs-lookup"><span data-stu-id="739bb-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="739bb-272">Получение событий состояния ключевого слова речи</span><span class="sxs-lookup"><span data-stu-id="739bb-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="739bb-273">Тип конфигурации события для состояния Спичкэйворд: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="739bb-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="739bb-274">Пользовательские состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="739bb-275">Создание пользовательского состояния с помощью инспектора</span><span class="sxs-lookup"><span data-stu-id="739bb-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="739bb-276">Пользовательское состояние, созданное с помощью инспектора, будет инициализировано с конфигурацией событий состояния по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="739bb-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="739bb-277">Конфигурация событий по умолчанию для пользовательского состояния имеет тип `StateEvents` и содержит события онстатеон и онстатеофф.</span><span class="sxs-lookup"><span data-stu-id="739bb-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="739bb-278">Перейдите к разделу **Создание настраиваемого состояния** в инспекторе для интерактивного элемента.</span><span class="sxs-lookup"><span data-stu-id="739bb-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Создание пользовательского состояния](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="739bb-280">Введите имя нового состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-280">Enter the name of the new state.</span></span> <span data-ttu-id="739bb-281">Это имя должно быть уникальным и не может совпадать с существующими основными состояниями.</span><span class="sxs-lookup"><span data-stu-id="739bb-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Ввод имени нового пользовательского состояния](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="739bb-283">Выберите **задать имя состояния** , чтобы добавить его в список состояний.</span><span class="sxs-lookup"><span data-stu-id="739bb-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Добавить пользовательское состояние в список состояний](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="739bb-285">Это пользовательское состояние инициализируется с `StateEvents` конфигурацией событий по умолчанию, которая содержит `OnStateOn` `OnStateOff` события и.</span><span class="sxs-lookup"><span data-stu-id="739bb-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="739bb-286">Сведения о создании конфигурации настраиваемого события для нового состояния см. в статье [Создание пользовательского состояния с настраиваемой конфигурацией событий](#creating-a-custom-state-with-a-custom-event-configuration).</span><span class="sxs-lookup"><span data-stu-id="739bb-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Новое состояние, отображаемое в компоненте интерактивного элемента](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;739bb-288&quot;>Создание пользовательского состояния с помощью скрипта</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;739bb-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="739bb-289">Создание пользовательского состояния с настраиваемой конфигурацией событий</span><span class="sxs-lookup"><span data-stu-id="739bb-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="739bb-290">Примеры файлов для пользовательского состояния с именем **Keyboard** находятся здесь: мртк\сдк\експериментал\интерактивилемент\ексамплес\скриптс\кустомстатиксампле.</span><span class="sxs-lookup"><span data-stu-id="739bb-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="739bb-291">В следующих шагах рассматривается существующий пример создания пользовательской конфигурации события состояния и файлов получателей.</span><span class="sxs-lookup"><span data-stu-id="739bb-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="739bb-292">Представьте имя состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-292">Think of a state name.</span></span>  <span data-ttu-id="739bb-293">Это имя должно быть уникальным и не может совпадать с существующими основными состояниями.</span><span class="sxs-lookup"><span data-stu-id="739bb-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="739bb-294">В этом примере имя состояния будет иметь значение **Клавиатура**.</span><span class="sxs-lookup"><span data-stu-id="739bb-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="739bb-295">Создайте два файла CS с именем State + "получатель" и именем состояния + "события".</span><span class="sxs-lookup"><span data-stu-id="739bb-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="739bb-296">Имена этих файлов учитываются во внутреннем процессе и должны соответствовать соглашению о названии состояния + события/получателя.</span><span class="sxs-lookup"><span data-stu-id="739bb-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Сценарии состояния клавиатуры](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="739bb-298">Дополнительные сведения о содержимом файлов см. в файлах Кэйбоардевентс. cs и Кэйбоардрецеивер. cs.</span><span class="sxs-lookup"><span data-stu-id="739bb-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="739bb-299">Новые классы конфигурации событий должны наследовать от `BaseInteractionEventConfiguration` , а новые классы приемников событий должны наследоваться от `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="739bb-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="739bb-300">Примеры параметров состояния для состояния клавиатуры находятся в `CustomStateSettingExample.cs` файле.</span><span class="sxs-lookup"><span data-stu-id="739bb-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="739bb-301">Добавление состояния в интерактивный элемент с помощью имени состояния имя состояния будет распознано, если существуют файлы конфигурации событий и приемника событий.</span><span class="sxs-lookup"><span data-stu-id="739bb-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="739bb-302">Свойства в файле конфигурации пользовательского события должны отображаться в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="739bb-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="739bb-303">![Добавление пользовательского состояния в интерактивное ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ настраиваемое состояние элемента, распознаваемое в интерактивном элементе](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="739bb-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="739bb-304">Дополнительные примеры файлов конфигурации событий и приемников событий см. в файлах по следующим путям:</span><span class="sxs-lookup"><span data-stu-id="739bb-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="739bb-305">мртк\сдк\експериментал\интерактивилемент\интерактивилемент\евентс\евентконфигуратионс</span><span class="sxs-lookup"><span data-stu-id="739bb-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="739bb-306">мртк\сдк\експериментал\интерактивилемент\интерактивилемент\евентс\евентрецеиверс</span><span class="sxs-lookup"><span data-stu-id="739bb-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="739bb-307">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="739bb-307">Example Scene</span></span> 

<span data-ttu-id="739bb-308">Пример сцены для визуализатора интерактивного элемента и состояния расположен здесь: Мртк\сдк\експериментал\интерактивилемент\ексамплес\интерактивилементексамплесцене.Унити</span><span class="sxs-lookup"><span data-stu-id="739bb-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Пример сцены с интерактивным визуализатором элемента и состояния](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="739bb-310">Сжатая кнопка</span><span class="sxs-lookup"><span data-stu-id="739bb-310">Compressable Button</span></span>

<span data-ttu-id="739bb-311">Пример сцены содержит Prefabs с именем `CompressableButton` и `CompressableButtonToggle` , эти Prefabs зеркально отражают поведение `PressableButtonHoloLens2` кнопок, созданных с помощью интерактивного элемента и визуализатора состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="739bb-312">В `CompressableButton` настоящее время компонент является сочетанием `PressableButton`  +  `PressableButtonHoloLens2` с `BaseInteractiveElement` базовым классом.</span><span class="sxs-lookup"><span data-stu-id="739bb-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="739bb-313">Визуализатор состояния [экспериментальный]</span><span class="sxs-lookup"><span data-stu-id="739bb-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="739bb-314">Компонент визуализатора состояния добавляет анимацию в объект на основе состояний, определенных в связанном компоненте интерактивного элемента.</span><span class="sxs-lookup"><span data-stu-id="739bb-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="739bb-315">Этот компонент создает ресурсы анимации, помещает их в папку Микседреалититулкит. Generated и включает упрощенную настройку опорного кадра анимации путем добавления свойств анимации к целевому объекту игры.</span><span class="sxs-lookup"><span data-stu-id="739bb-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="739bb-316">Чтобы включить переходы анимации между состояниями, создается ресурс контроллера аниматор и создается конечный автомат по умолчанию со связанными параметрами и любыми переходами состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="739bb-317">Конечный автомат можно просмотреть в окне аниматор Unity.</span><span class="sxs-lookup"><span data-stu-id="739bb-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="739bb-318">Визуализатор состояния и система анимации Unity</span><span class="sxs-lookup"><span data-stu-id="739bb-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="739bb-319">В настоящее время визуализатор состояния использует систему анимации Unity.</span><span class="sxs-lookup"><span data-stu-id="739bb-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="739bb-320">При нажатии кнопки **создать новые фрагменты анимации** в визуализаторе состояния создаются новые материалы анимации на основе имен состояний в интерактивном элементе и помещаются в папку Микседреалититулкит. Generated.</span><span class="sxs-lookup"><span data-stu-id="739bb-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="739bb-321">Свойство фрагмента анимации в каждом контейнере состояния устанавливается в соответствующий анимированный ролик.</span><span class="sxs-lookup"><span data-stu-id="739bb-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Анимированные клипы в компоненте визуализатора состояния](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="739bb-323">Кроме того, для управления плавными переходами между фрагментами анимации также создается [конечный автомат аниматор](https://docs.unity3d.com/Manual/AnimationOverview.html) .</span><span class="sxs-lookup"><span data-stu-id="739bb-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="739bb-324">По умолчанию конечный автомат использует [любое состояние](https://docs.unity3d.com/Manual/class-State.html) , чтобы разрешить переходы между любым состоянием в интерактивном элементе.</span><span class="sxs-lookup"><span data-stu-id="739bb-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="739bb-325">[Визуализаторы состояний, активируемые в аниматор](https://docs.unity3d.com/Manual/AnimationParameters.html) , также формируются для каждого состояния. параметры триггера используются в визуализаторе состояний для запуска анимации.</span><span class="sxs-lookup"><span data-stu-id="739bb-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Конечный автомат Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="739bb-327">Ограничения среды выполнения</span><span class="sxs-lookup"><span data-stu-id="739bb-327">Runtime Limitations</span></span> 

<span data-ttu-id="739bb-328">Визуализатор состояния должен быть добавлен в объект через инспектор и не может быть добавлен с помощью скрипта.</span><span class="sxs-lookup"><span data-stu-id="739bb-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="739bb-329">Свойства, изменяющие Аниматорстатемачине/Аниматионконтроллер, содержатся в пространстве имен редактора ( `UnityEditor.Animations` ), которое удаляется при сборке приложения.</span><span class="sxs-lookup"><span data-stu-id="739bb-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="739bb-330">Использование визуализатора состояния</span><span class="sxs-lookup"><span data-stu-id="739bb-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="739bb-331">Создание куба</span><span class="sxs-lookup"><span data-stu-id="739bb-331">Create a Cube</span></span>
1. <span data-ttu-id="739bb-332">Присоединить интерактивный элемент</span><span class="sxs-lookup"><span data-stu-id="739bb-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="739bb-333">Присоединить визуализатор состояний</span><span class="sxs-lookup"><span data-stu-id="739bb-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="739bb-334">Выберите **создать новые анимационные клипы**</span><span class="sxs-lookup"><span data-stu-id="739bb-334">Select **Generate New Animation Clips**</span></span>

    ![Создание новых анимированных клипов](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Отображение созданных анимированных роликов в визуализаторе и компонентах интерактивного элемента](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="739bb-337">В контейнере состояние фокуса выберите **добавить целевой объект** .</span><span class="sxs-lookup"><span data-stu-id="739bb-337">In the Focus state container, select **Add Target**</span></span>

    ![Добавление целевого объекта визуализатора состояния](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="739bb-339">Перетащите текущий объект Game в целевое поле</span><span class="sxs-lookup"><span data-stu-id="739bb-339">Drag the current game object to the target field</span></span> 

    ![Задание целевого объекта визуализатора состояния](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="739bb-341">Открытие свертывания свойств куба</span><span class="sxs-lookup"><span data-stu-id="739bb-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="739bb-342">Выберите раскрывающееся меню анимированное свойство и выберите **Цвет** .</span><span class="sxs-lookup"><span data-stu-id="739bb-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Настройка цвета визуализатора состояния](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="739bb-344">Выберите **Добавить свойство для анимации цвета** .</span><span class="sxs-lookup"><span data-stu-id="739bb-344">Select **Add the Color Animatable Property**</span></span>

    ![Выбор анимированного свойства "цвет визуализатора"](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="739bb-346">Выбор цвета</span><span class="sxs-lookup"><span data-stu-id="739bb-346">Choose a Color</span></span> 

    ![Выбор цвета визуализатора из цветового круга](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="739bb-348">Нажмите кнопку Воспроизведение и обратите внимание на изменение переходного цвета.</span><span class="sxs-lookup"><span data-stu-id="739bb-348">Press play and observe the transitional color change</span></span>

    ![Пример изменения цветового перехода с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="739bb-350">Свойства с анимацией</span><span class="sxs-lookup"><span data-stu-id="739bb-350">Animatable Properties</span></span>

<span data-ttu-id="739bb-351">Основным назначением свойств, которые можно анимировать, является упрощение настройки опорного кадра анимации.</span><span class="sxs-lookup"><span data-stu-id="739bb-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="739bb-352">Если пользователь знаком с системой анимации Unity и предпочитает непосредственно задавать опорные кадры на созданных роликах анимации, они могут просто не добавлять анимированные свойства в целевой объект и открывать клип в окне анимации Unity (анимация Windows > анимации >).</span><span class="sxs-lookup"><span data-stu-id="739bb-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="739bb-353">Если для анимации используются анимированные свойства, для типа кривой устанавливается значение Еасеинаут.</span><span class="sxs-lookup"><span data-stu-id="739bb-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="739bb-354">**Текущие свойства для анимации:**</span><span class="sxs-lookup"><span data-stu-id="739bb-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="739bb-355">Смещение шкалы</span><span class="sxs-lookup"><span data-stu-id="739bb-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="739bb-356">Смещение позиции</span><span class="sxs-lookup"><span data-stu-id="739bb-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="739bb-357">Цвет</span><span class="sxs-lookup"><span data-stu-id="739bb-357">Color</span></span>](#color)
- [<span data-ttu-id="739bb-358">Цвет шейдера</span><span class="sxs-lookup"><span data-stu-id="739bb-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="739bb-359">Построитель текстуры с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="739bb-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="739bb-360">Вектор шейдера</span><span class="sxs-lookup"><span data-stu-id="739bb-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="739bb-361">Смещение шкалы</span><span class="sxs-lookup"><span data-stu-id="739bb-361">Scale Offset</span></span>

<span data-ttu-id="739bb-362">Свойство с анимацией смещения шкалы принимает текущий масштаб объекта и добавляет заданное смещение.</span><span class="sxs-lookup"><span data-stu-id="739bb-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Смещение шкалы с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="739bb-364">Смещение позиции</span><span class="sxs-lookup"><span data-stu-id="739bb-364">Position Offset</span></span>

<span data-ttu-id="739bb-365">Свойство "смещение позиции", которое используется для анимации, принимает текущую позиции объекта и добавляет заданное смещение.</span><span class="sxs-lookup"><span data-stu-id="739bb-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Смещение позиции с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="739bb-367">Цвет</span><span class="sxs-lookup"><span data-stu-id="739bb-367">Color</span></span>

<span data-ttu-id="739bb-368">Свойство "анимация цвета" представляет основной цвет материала, если материал имеет свойство основного цвета.</span><span class="sxs-lookup"><span data-stu-id="739bb-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="739bb-369">Это свойство анимирует `material._Color` свойство.</span><span class="sxs-lookup"><span data-stu-id="739bb-369">This property animates the `material._Color` property.</span></span>

![Изменение цвета фокуса с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="739bb-371">Цвет шейдера</span><span class="sxs-lookup"><span data-stu-id="739bb-371">Shader Color</span></span>

<span data-ttu-id="739bb-372">Свойство анимированного цвета шейдера ссылается на свойство шейдера типа Color.</span><span class="sxs-lookup"><span data-stu-id="739bb-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="739bb-373">Имя свойства является обязательным для всех свойств шейдера.</span><span class="sxs-lookup"><span data-stu-id="739bb-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="739bb-374">Приведенный ниже GIF-файл демонстрирует анимацию свойства цвета шейдера с именем Fill_Color, который не является основным цветом материала.</span><span class="sxs-lookup"><span data-stu-id="739bb-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="739bb-375">Изучите изменяющиеся значения в инспекторе материалов.</span><span class="sxs-lookup"><span data-stu-id="739bb-375">Observe the changing values in the material inspector.</span></span>

![Цвет тени с использованием виртуальной руки](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="739bb-377">Построитель текстуры с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="739bb-377">Shader Float</span></span>

<span data-ttu-id="739bb-378">Анимированное свойство Shader с плавающей запятой ссылается на свойство шейдера типа float.</span><span class="sxs-lookup"><span data-stu-id="739bb-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="739bb-379">Имя свойства является обязательным для всех свойств шейдера.</span><span class="sxs-lookup"><span data-stu-id="739bb-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="739bb-380">В приведенном ниже GIF-файле Обратите внимание на изменение значений в инспекторе материалов для свойства «металл».</span><span class="sxs-lookup"><span data-stu-id="739bb-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Построитель текстуры с плавающей точкой с виртуальной рукой](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="739bb-382">Вектор шейдера</span><span class="sxs-lookup"><span data-stu-id="739bb-382">Shader Vector</span></span>

<span data-ttu-id="739bb-383">Анимированное свойство вектора шейдера ссылается на свойство шейдера типа Vector4.</span><span class="sxs-lookup"><span data-stu-id="739bb-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="739bb-384">Имя свойства является обязательным для всех свойств шейдера.</span><span class="sxs-lookup"><span data-stu-id="739bb-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="739bb-385">В приведенном ниже GIF-файле Обратите внимание на изменение значений в инспекторе материалов для свойства мозаичного заполнения (главное Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="739bb-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Вектор шейдера с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="739bb-387">Как найти имена свойств анимированного шейдера</span><span class="sxs-lookup"><span data-stu-id="739bb-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="739bb-388">Переход к окну > анимации > анимация</span><span class="sxs-lookup"><span data-stu-id="739bb-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="739bb-389">Убедитесь, что в иерархии выбран объект с визуализатором состояния.</span><span class="sxs-lookup"><span data-stu-id="739bb-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="739bb-390">Выбор любого клипа анимации в окне "анимация"</span><span class="sxs-lookup"><span data-stu-id="739bb-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="739bb-391">Выберите **Добавить свойство**, откройте свертывание модуля подготовки сетки.</span><span class="sxs-lookup"><span data-stu-id="739bb-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Добавление свойства анимации в окно аниматор](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="739bb-393">Этот список содержит имена всех свойств анимации.</span><span class="sxs-lookup"><span data-stu-id="739bb-393">This list contains the names of all the Animatable property names</span></span> 

    ![Свойства анимации модуля подготовки сетки в окне аниматор](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="739bb-395">См. также</span><span class="sxs-lookup"><span data-stu-id="739bb-395">See also</span></span>

- [<span data-ttu-id="739bb-396">**Кнопки**</span><span class="sxs-lookup"><span data-stu-id="739bb-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="739bb-397">**Элемент управления границами**</span><span class="sxs-lookup"><span data-stu-id="739bb-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="739bb-398">**Коллекция объектов Grid**</span><span class="sxs-lookup"><span data-stu-id="739bb-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="739bb-399">**Поиск решения Радиалвиев**</span><span class="sxs-lookup"><span data-stu-id="739bb-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
