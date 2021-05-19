---
title: Выбор целевого объекта отслеживания взгляда
description: Как получить доступ к данным и отдельным событиям взгляда на глаза для выбора целевых объектов в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144191"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="644e4-104">Глаз — поддерживаемый Выбор целевого объекта</span><span class="sxs-lookup"><span data-stu-id="644e4-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="644e4-106">На этой странице обсуждаются различные варианты доступа к данным взгляда на глаза и события взгляда на глаза для выбора целевых объектов в МРТК.</span><span class="sxs-lookup"><span data-stu-id="644e4-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="644e4-107">Отслеживание взгляда позволяет быстро и легко выбирать целевые объекты, используя сочетание сведений о том, что видят пользователи, с дополнительными входными данными, такими как _Отслеживание_ и _команды голоса_:</span><span class="sxs-lookup"><span data-stu-id="644e4-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="644e4-108">Искать & скажите _"Select"_ (голосовая команда по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="644e4-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="644e4-109">Взгляните & скажите _"раскрыть"_ или _"Pop"_ (пользовательские голосовые команды)</span><span class="sxs-lookup"><span data-stu-id="644e4-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="644e4-110">Поиск & кнопки Bluetooth</span><span class="sxs-lookup"><span data-stu-id="644e4-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="644e4-111">Взгляните & сжатие (т. е. Держите руку перед вами и перенесите палец и проведите указатель пальца).</span><span class="sxs-lookup"><span data-stu-id="644e4-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="644e4-112">Обратите внимание, что чтобы это работало, [необходимо отключить лучи в руки](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) .</span><span class="sxs-lookup"><span data-stu-id="644e4-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="644e4-113">Чтобы выбрать holographic содержимое с помощью глаза, существует несколько вариантов:</span><span class="sxs-lookup"><span data-stu-id="644e4-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="644e4-114">**1. Используйте основной указатель фокуса:**</span><span class="sxs-lookup"><span data-stu-id="644e4-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="644e4-115">Он может быть понятен по приоритетному курсору.</span><span class="sxs-lookup"><span data-stu-id="644e4-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="644e4-116">По умолчанию, если руки находятся в представлении, это может быть некоторая рука.</span><span class="sxs-lookup"><span data-stu-id="644e4-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="644e4-117">Если в представлении нет ни одной руки, то указатель с приоритетом будет иметь вид "руководитель" или "глаз".</span><span class="sxs-lookup"><span data-stu-id="644e4-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="644e4-118">Таким образом, обратите внимание, что на основе текущей схемы проектирования или взгляда на глаза в качестве входных данных курсора поподавляется, если используются лучи.</span><span class="sxs-lookup"><span data-stu-id="644e4-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="644e4-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="644e4-119">For example:</span></span>

<span data-ttu-id="644e4-120">Пользователь хочет выбрать удаленную кнопку Holographic.</span><span class="sxs-lookup"><span data-stu-id="644e4-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="644e4-121">Разработчику необходимо предоставить гибкое решение, позволяющее пользователю выполнять эти задачи в различных условиях:</span><span class="sxs-lookup"><span data-stu-id="644e4-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="644e4-122">Пошаговое руководство по кнопке</span><span class="sxs-lookup"><span data-stu-id="644e4-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="644e4-123">Взгляните на него с расстояния и скажите «SELECT»</span><span class="sxs-lookup"><span data-stu-id="644e4-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="644e4-124">Нацеливание на кнопку с помощью руки и выполнения сжатия в этом случае самым гибким решением является использование основного обработчика фокуса, так как он уведомляет вас каждый раз, когда основной указатель фокуса в данный момент инициирует событие.</span><span class="sxs-lookup"><span data-stu-id="644e4-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="644e4-125">Обратите внимание, что если вы намерены использовать лучи, указатель фокуса будет отключен, как только руки появятся в представлении.</span><span class="sxs-lookup"><span data-stu-id="644e4-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="644e4-126">Обратите внимание, что если вы намерены использовать лучи, указатель фокуса будет отключен, как только руки появятся в представлении.</span><span class="sxs-lookup"><span data-stu-id="644e4-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="644e4-127">Если требуется поддержка [взаимодействия _"внешний вид и сжатие_ ", необходимо отключить руку](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span><span class="sxs-lookup"><span data-stu-id="644e4-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="644e4-128">В нашем примере с отслеживанием взглядов мы отключили руку, чтобы показать более широкие возможности взаимодействия с помощью глаз и движений руки — см. пример [позиционирования с поддержкой глаз](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="644e4-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="644e4-129">**2. одновременно используйте фокус глаза и лучи.**</span><span class="sxs-lookup"><span data-stu-id="644e4-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="644e4-130">Могут существовать экземпляры, которые должны быть более конкретными, указывающие, какой тип указателей фокуса может активировать определенные события и разрешить одновременно использовать несколько методов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="644e4-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="644e4-131">Например, в приложении пользователь может использовать крайнее расстояние для управления некоторыми более отдаленными механическими настройками, например, захватить и удержать несколько удаленных частей holographic и удерживать их на месте.</span><span class="sxs-lookup"><span data-stu-id="644e4-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="644e4-132">При этом пользователь должен пройти несколько инструкций и записать ход выполнения, пометив некоторые флажки.</span><span class="sxs-lookup"><span data-stu-id="644e4-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="644e4-133">Если пользователь или его руки _не заняты_, это было бы инстинктуал, чтобы просто коснуться флажка или выбрать его с помощью руки.</span><span class="sxs-lookup"><span data-stu-id="644e4-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="644e4-134">Тем не менее, если у пользователя есть и его руки, как в нашем случае с разделом с более тесными компонентами, необходимо предоставить пользователю возможность беспрепятственно прокручивать инструкции с помощью взгляда на глаза и просто взглянуть на флажок и сказать «проверить!».</span><span class="sxs-lookup"><span data-stu-id="644e4-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="644e4-135">Для этого необходимо использовать сценарий Эйетраккингтаржет, зависящий от глаза, который не зависит от основной МРТК Фокушандлерс и будет рассмотрен далее.</span><span class="sxs-lookup"><span data-stu-id="644e4-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="644e4-136">1. Использование универсальных обработчиков фокуса и указателей</span><span class="sxs-lookup"><span data-stu-id="644e4-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="644e4-137">Если отслеживание взгляда настроено правильно (см. раздел [Базовая настройка мртк для использования отслеживания взгляда](eye-tracking-basic-setup.md)), предоставление пользователям возможности выбирать самые голограммы в глаза будет таким же, как и для любого другого ввода фокуса (например, с помощью головного взгляда или руки). Это предоставляет отличное преимущество гибкого способа взаимодействия с голограммами путем определения основного типа фокуса в профиле указателя ввода МРТК в зависимости от потребностей пользователя, при этом код не затрагивается.</span><span class="sxs-lookup"><span data-stu-id="644e4-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="644e4-138">Это позволяет переключаться между обработкой головного взгляда или глаза без изменения строки кода или замены руки с целью взгляда для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="644e4-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="644e4-139">Сосредоточение на голограмме</span><span class="sxs-lookup"><span data-stu-id="644e4-139">Focusing on a hologram</span></span>

<span data-ttu-id="644e4-140">Чтобы определить, когда находится голограмма, используйте интерфейс _"имикседреалитифокушандлер"_ , который предоставляет два члена интерфейса: _онфокусентер_ и _онфокусексит_.</span><span class="sxs-lookup"><span data-stu-id="644e4-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="644e4-141">Ниже приведен простой пример из [колортап. CS](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) для изменения цвета голограммы при просмотре.</span><span class="sxs-lookup"><span data-stu-id="644e4-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="644e4-142">Выбор голограммы с упором</span><span class="sxs-lookup"><span data-stu-id="644e4-142">Selecting a focused hologram</span></span>

<span data-ttu-id="644e4-143">Чтобы выбрать голограмму с фокусом, используйте _поинтерхандлер_ , чтобы прослушивать входные события для подтверждения выбора.</span><span class="sxs-lookup"><span data-stu-id="644e4-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="644e4-144">Например, если добавить _имикседреалитипоинтерхандлер_ , они будут реагировать на простые входные указатели.</span><span class="sxs-lookup"><span data-stu-id="644e4-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="644e4-145">Интерфейс _имикседреалитипоинтерхандлер_ требует реализации следующих трех членов интерфейса: _онпоинтеруп_, _онпоинтердовн_ и _онпоинтеркликкед_.</span><span class="sxs-lookup"><span data-stu-id="644e4-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="644e4-146">В приведенном ниже примере мы изменим цвет голограммы, взглянув на него и отменив или выполнив слово SELECT.</span><span class="sxs-lookup"><span data-stu-id="644e4-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="644e4-147">Действие, необходимое для запуска события, определяется тем, что `eventData.MixedRealityInputAction == selectAction` мы можем задать тип `selectAction` в редакторе Unity — по умолчанию это действие "Select".</span><span class="sxs-lookup"><span data-stu-id="644e4-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="644e4-148">Типы доступных [микседреалитинпутактионс](../input-actions.md) можно настроить в профиле мртк с помощью действий ввода   ->  _входных_  ->  _данных_ профиля конфигурации мртк.</span><span class="sxs-lookup"><span data-stu-id="644e4-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="644e4-149">Взгляд на Басиефокушандлер</span><span class="sxs-lookup"><span data-stu-id="644e4-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="644e4-150">Учитывая, что взгляд на глаза может сильно отличаться от других входных указателей, может возникнуть необходимость реагирования на ввод фокуса, если _взгляд_ воспринимается, и в данный момент является первичным указателем ввода.</span><span class="sxs-lookup"><span data-stu-id="644e4-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="644e4-151">Для этой цели следует использовать объект, [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) который относится к отслеживанию глаз и является производным от [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="644e4-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="644e4-152">Как упоминалось ранее, он срабатывает только в том случае, если нацеливание на глаз в настоящее время является первичным указателем (т. е. ни один входной луч не активен).</span><span class="sxs-lookup"><span data-stu-id="644e4-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="644e4-153">Дополнительные сведения см. [в разделе Поддержка жестов глазного взгляда и руки](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="644e4-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="644e4-154">Ниже приведен пример из `EyeTrackingDemo-03-Navigation` (Assets/мртк/examples/демонстрации/эйетраккинг/сцены).</span><span class="sxs-lookup"><span data-stu-id="644e4-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="644e4-155">В этой демонстрации есть две трехмерные голограммы, которые будут переноситься в зависимости от того, какая часть объекта будет выглядеть: Если пользователь просматривает левую часть голограммы, то эта часть будет медленно перемещаться к лицевой стороне пользователя.</span><span class="sxs-lookup"><span data-stu-id="644e4-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="644e4-156">Если просматривается правая сторона, то эта часть будет медленно перемещена на передний план.</span><span class="sxs-lookup"><span data-stu-id="644e4-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="644e4-157">Это поведение, которое может быть нежелательно, если вы не хотите, чтобы они были активны постоянно, а также что-то, что вы не хотите случайно активировать с помощью луча или головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="644e4-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="644e4-158">[`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze)Если присоединиться, GameObject будет вращаться во время поиска.</span><span class="sxs-lookup"><span data-stu-id="644e4-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="644e4-159">Полный список доступных событий можно найти в документации по API [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="644e4-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="644e4-160">**Онэйефокусстарт:** Активируется после того, как элемент лучей глаза *начинает* пересекаться с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="644e4-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="644e4-161">**Онэйефокусстай:** Активируется, *когда* наблюдатель глаза пересекается с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="644e4-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="644e4-162">**Онэйефокусстоп:** Активируется после того, как наблюдатель глаза *перестанет* пересекаться с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="644e4-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="644e4-163">**Онэйефокусдвелл:** Активируется после того, как наблюдатель глаза пересекается с этим объектом в течение указанного промежутка времени.</span><span class="sxs-lookup"><span data-stu-id="644e4-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="644e4-164">2. Независимый взгляд на Эйетраккингтаржет</span><span class="sxs-lookup"><span data-stu-id="644e4-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="644e4-165">Наконец, мы предоставляем решение, которое позволяет обрабатывать входные данные на основе взгляда полностью независимо от других указателей фокуса с помощью [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) сценария.</span><span class="sxs-lookup"><span data-stu-id="644e4-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="644e4-166">Это имеет три _преимущества_:</span><span class="sxs-lookup"><span data-stu-id="644e4-166">This has three _advantages_:</span></span>

- <span data-ttu-id="644e4-167">Можно убедиться, что голограмма будет перереагировать только на взгляд пользователя.</span><span class="sxs-lookup"><span data-stu-id="644e4-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="644e4-168">Это не зависит от текущего активного ввода.</span><span class="sxs-lookup"><span data-stu-id="644e4-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="644e4-169">Таким образом, можно обрабатывать сразу несколько входов, например сочетание быстрого взгляда с жестами руки.</span><span class="sxs-lookup"><span data-stu-id="644e4-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="644e4-170">Несколько событий Unity уже настроены для быстрой и удобной обработки и повторного использования существующих поведений в редакторе Unity или коде.</span><span class="sxs-lookup"><span data-stu-id="644e4-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="644e4-171">Существуют также некоторые _недостатки._</span><span class="sxs-lookup"><span data-stu-id="644e4-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="644e4-172">Дополнительные усилия по обработке отдельных входов по отдельности.</span><span class="sxs-lookup"><span data-stu-id="644e4-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="644e4-173">Без элегантного ухудшения: он поддерживает только определение целей для глаз.</span><span class="sxs-lookup"><span data-stu-id="644e4-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="644e4-174">Если отслеживание взгляда не работает, потребуется дополнительное резервное действие.</span><span class="sxs-lookup"><span data-stu-id="644e4-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="644e4-175">Как и _басефокушандлер_, _эйетраккингтаржет_ поставляется с несколькими событиями Unity, специфичными для глаз, которые можно прослушать либо с помощью редактора Unity (см. пример ниже), либо с помощью _аддлистенер ()_ в коде:</span><span class="sxs-lookup"><span data-stu-id="644e4-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="644e4-176">Онлукатстарт ()</span><span class="sxs-lookup"><span data-stu-id="644e4-176">OnLookAtStart()</span></span>
- <span data-ttu-id="644e4-177">Вхилелукингаттаржет ()</span><span class="sxs-lookup"><span data-stu-id="644e4-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="644e4-178">Онлукавай ()</span><span class="sxs-lookup"><span data-stu-id="644e4-178">OnLookAway()</span></span>
- <span data-ttu-id="644e4-179">Ондвелл ()</span><span class="sxs-lookup"><span data-stu-id="644e4-179">OnDwell()</span></span>
- <span data-ttu-id="644e4-180">Selectd ()</span><span class="sxs-lookup"><span data-stu-id="644e4-180">OnSelected()</span></span>

<span data-ttu-id="644e4-181">В следующем примере мы рассмотрим несколько примеров использования _эйетраккингтаржет_.</span><span class="sxs-lookup"><span data-stu-id="644e4-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="644e4-182">Пример #1: Поддерживаемые смарт-уведомления</span><span class="sxs-lookup"><span data-stu-id="644e4-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="644e4-183">В `EyeTrackingDemo-02-TargetSelection` (Assets/мртк/examples/эйетраккинг/сцены) можно найти пример для _"Smart внимательный Notifications"_ , который реагирует на взгляд.</span><span class="sxs-lookup"><span data-stu-id="644e4-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="644e4-184">Это трехмерные текстовые поля, которые можно поместить в сцену, что будет плавно увеличиваться и поворачиваться для удобства пользователя при просмотре.</span><span class="sxs-lookup"><span data-stu-id="644e4-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="644e4-185">При чтении уведомления пользователь получает четкие и четко отображаемые данные.</span><span class="sxs-lookup"><span data-stu-id="644e4-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="644e4-186">После того как вы прочитаете его и выйдете из уведомления, уведомление автоматически закрывается и исчезает. Для этого существует несколько сценариев универсального поведения, которые не относятся к отслеживанию глаз, например:</span><span class="sxs-lookup"><span data-stu-id="644e4-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="644e4-187">Преимуществом этого подхода является то, что одни и те же скрипты могут повторно использоваться различными событиями.</span><span class="sxs-lookup"><span data-stu-id="644e4-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="644e4-188">Например, голограмма может начинаться с пользователя на основе голосовых команд или после нажатия виртуальной кнопки.</span><span class="sxs-lookup"><span data-stu-id="644e4-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="644e4-189">Чтобы активировать эти события, можно просто ссылаться на методы, которые должны выполняться в [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) скрипте, присоединенном к GameObject.</span><span class="sxs-lookup"><span data-stu-id="644e4-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="644e4-190">В качестве примера _"Smart внимательный Notifications"_ происходит следующее:</span><span class="sxs-lookup"><span data-stu-id="644e4-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="644e4-191">**Онлукатстарт ()**: начинается уведомление...</span><span class="sxs-lookup"><span data-stu-id="644e4-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="644e4-192">*Фацеусер. привлекать:* ... Превратите пользователя в сторону.</span><span class="sxs-lookup"><span data-stu-id="644e4-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="644e4-193">*Чанжесизе. привлекать:* ... увеличение размера _(до указанного максимального масштаба)_.</span><span class="sxs-lookup"><span data-stu-id="644e4-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="644e4-194">*Наложение. привлекать:* ... начинает переходить в другое _состояние (после того, как оно находится в более тонком состоянии простоя)_.</span><span class="sxs-lookup"><span data-stu-id="644e4-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="644e4-195">**Ондвелл ()**: информирует сценарий _перехода_ о том, что уведомление было достаточно.</span><span class="sxs-lookup"><span data-stu-id="644e4-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="644e4-196">**Онлукавай ()**: начинается уведомление...</span><span class="sxs-lookup"><span data-stu-id="644e4-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="644e4-197">*Фацеусер. ClassInterfaceAttribute отключите:* ... Вернитесь к исходной ориентации.</span><span class="sxs-lookup"><span data-stu-id="644e4-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="644e4-198">*Чанжесизе. ClassInterfaceAttribute отключите:* ... уменьшение до исходного размера.</span><span class="sxs-lookup"><span data-stu-id="644e4-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="644e4-199">*Наложение. ClassInterfaceAttribute отключите:* ... Начало смешения. Если _ондвелл ()_ был активирован, то разложение полностью и уничтожается, в противном случае обратно в состояние простоя.</span><span class="sxs-lookup"><span data-stu-id="644e4-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="644e4-200">**Вопросы проектирования:** Ключом к приятной работе здесь является тщательная настройка скорости любого из этих поведений, чтобы избежать возникновения дискомфорти, так как в этом случае не придется перереагировать на взгляд пользователя.</span><span class="sxs-lookup"><span data-stu-id="644e4-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="644e4-201">В противном случае это может быстро привести к чрезмерному переполнению.</span><span class="sxs-lookup"><span data-stu-id="644e4-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="644e4-202">Пример #2: holographic драгоценный камень медленно вращается при просмотре</span><span class="sxs-lookup"><span data-stu-id="644e4-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="644e4-203">Как и в примере #1, мы можем легко создать отзыв о наведении для наших драгоценных камней в `EyeTrackingDemo-02-TargetSelection` (Assets/мртк/examples/эйетраккинг/сцены), который постепенно поворачивается в постоянном направлении и на постоянной скорости (в отличие от примера вращения выше) при просмотре.</span><span class="sxs-lookup"><span data-stu-id="644e4-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="644e4-204">Все, что нужно, — активировать поворот holographic-драгоценного камень из события _вхилелукингаттаржет ()_ _эйетраккингтаржет_.</span><span class="sxs-lookup"><span data-stu-id="644e4-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="644e4-205">Ниже приведены некоторые дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="644e4-205">Here are a few more details:</span></span>

1. <span data-ttu-id="644e4-206">Создайте универсальный скрипт, содержащий открытую функцию для поворота GameObject, к которой он присоединен.</span><span class="sxs-lookup"><span data-stu-id="644e4-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="644e4-207">Ниже приведен пример из _ротатевисконстспиддир. CS_ , где можно настроить направление вращения и скорость работы в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="644e4-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="644e4-208">Добавьте [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) скрипт в целевую GameObject и сослаться на функцию _ротатетаржет ()_ в триггере унитевент, как показано на следующем снимке экрана:</span><span class="sxs-lookup"><span data-stu-id="644e4-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Пример Эйетраккингтаржет](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="644e4-210">Пример #3: POP эти драгоценные камни представляют собой _поддерживаемый целевой объект с несколькими модальными глазами-взглядами_</span><span class="sxs-lookup"><span data-stu-id="644e4-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="644e4-211">В предыдущем примере мы показали, насколько просто определить, просматривается ли цель и как активировать реакцию на нее.</span><span class="sxs-lookup"><span data-stu-id="644e4-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="644e4-212">Далее создадим драгоценные камни, развернутые с помощью события _OnSelected ()_ из [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="644e4-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="644e4-213">Интересная часть заключается в *том, как* активируется выбор.</span><span class="sxs-lookup"><span data-stu-id="644e4-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="644e4-214">[`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)Позволяет быстро назначать различные способы вызова выбора:</span><span class="sxs-lookup"><span data-stu-id="644e4-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="644e4-215">_Жест сжатия_: Если задать для параметра "выбрать действие" значение "Select", будет использоваться жест по умолчанию, чтобы активировать выбор.</span><span class="sxs-lookup"><span data-stu-id="644e4-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="644e4-216">Это означает, что пользователь может просто поднять свою руку и просжатие бегунка и указатель пальца, чтобы подтвердить выбор.</span><span class="sxs-lookup"><span data-stu-id="644e4-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="644e4-217">Скажите _"выбрать"_: используйте голосовую команду по умолчанию _"Select"_ для выбора голограммы.</span><span class="sxs-lookup"><span data-stu-id="644e4-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="644e4-218">Скажем, _"взрыв_ " или _"Pop"_: для использования пользовательских голосовых команд необходимо выполнить два шага:</span><span class="sxs-lookup"><span data-stu-id="644e4-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="644e4-219">Настройка настраиваемого действия, например _"дестройтаржет"_</span><span class="sxs-lookup"><span data-stu-id="644e4-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="644e4-220">Перейдите в раздел _мртк-> input-> input Actions_ .</span><span class="sxs-lookup"><span data-stu-id="644e4-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="644e4-221">Щелкните "добавить новое действие".</span><span class="sxs-lookup"><span data-stu-id="644e4-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="644e4-222">Настройте команды Voice, которые активируют это действие, например _"раскрыть"_ или _"Pop"_ .</span><span class="sxs-lookup"><span data-stu-id="644e4-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="644e4-223">Перейдите к _мртк-> input-> Speech_</span><span class="sxs-lookup"><span data-stu-id="644e4-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="644e4-224">Щелкните "добавить новую голосовую команду".</span><span class="sxs-lookup"><span data-stu-id="644e4-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="644e4-225">Связывание только что созданного действия</span><span class="sxs-lookup"><span data-stu-id="644e4-225">Associate the action you just created</span></span>
            - <span data-ttu-id="644e4-226">Назначение _keyCode_ для включения действия с помощью нажатия кнопки</span><span class="sxs-lookup"><span data-stu-id="644e4-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Образец Эйетраккингтаржет Voice Commands](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="644e4-228">Если выбран драгоценный камень, он разворачивается, выполнит звук и исчезнет.</span><span class="sxs-lookup"><span data-stu-id="644e4-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="644e4-229">Это обрабатывается [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) сценарием.</span><span class="sxs-lookup"><span data-stu-id="644e4-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="644e4-230">Имеются две возможности.</span><span class="sxs-lookup"><span data-stu-id="644e4-230">You have two options:</span></span>

- <span data-ttu-id="644e4-231">**В редакторе Unity:** Можно просто связать сценарий, прикрепленный к каждому из наших шаблонов, с событием Unity () в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="644e4-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="644e4-232">**В коде:** Если вы не хотите перетаскивать объекты gameobject, вы также можете просто добавить прослушиватель событий непосредственно в сценарий.</span><span class="sxs-lookup"><span data-stu-id="644e4-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="644e4-233">Ниже приведен пример того, как мы сделали это в [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) сценарии:</span><span class="sxs-lookup"><span data-stu-id="644e4-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="644e4-234">Пример #4: входные данные с использованием луча и глазного взгляда</span><span class="sxs-lookup"><span data-stu-id="644e4-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="644e4-235">Лучи имеют приоритет над нацеливанием на головной взгляд и глаз.</span><span class="sxs-lookup"><span data-stu-id="644e4-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="644e4-236">Это означает, что если вы наберете лучи, то в то время, когда они появятся, руку будет действовать как основной указатель.</span><span class="sxs-lookup"><span data-stu-id="644e4-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="644e4-237">Однако могут возникнуть ситуации, в которых вы хотите использовать лучи и при этом определить, просматриваете ли пользователь определенную голограмму.</span><span class="sxs-lookup"><span data-stu-id="644e4-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="644e4-238">Легко!</span><span class="sxs-lookup"><span data-stu-id="644e4-238">Easy!</span></span> <span data-ttu-id="644e4-239">По сути, требуется выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="644e4-239">Essentially you require two steps:</span></span>

<span data-ttu-id="644e4-240">**1. включить элемент** управления "рука". чтобы включить луч, перейдите в раздел " _Смешанная реальность" Toolkit-> "входные > указатели_".</span><span class="sxs-lookup"><span data-stu-id="644e4-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="644e4-241">В _эйетраккингдемо-00-рутсцене_ , где набор средств Mixed Reality настроен один раз для всех демонстрационных сцен отслеживания взгляда, вы должны увидеть _эйетраккингдемопоинтерпрофиле_.</span><span class="sxs-lookup"><span data-stu-id="644e4-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="644e4-242">Можно либо создать новый _входной профиль_ с нуля, либо адаптировать отслеживание текущего взгляда:</span><span class="sxs-lookup"><span data-stu-id="644e4-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="644e4-243">**С нуля:** На вкладке _указатели_ выберите _дефаултмикседреалитинпутпоинтерпрофиле_ в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="644e4-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="644e4-244">Это профиль указателя по умолчанию, в котором уже включен параметр руки.</span><span class="sxs-lookup"><span data-stu-id="644e4-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="644e4-245">Чтобы изменить курсор по умолчанию (непрозрачную белую точку), достаточно клонировать профиль и создать собственный профиль пользовательского указателя.</span><span class="sxs-lookup"><span data-stu-id="644e4-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="644e4-246">Затем замените _дефаулткурсор_ на _эйегазекурсор_ в разделе _Взгляните prefab_.</span><span class="sxs-lookup"><span data-stu-id="644e4-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="644e4-247">**На основе существующих _эйетраккингдемопоинтерпрофиле_:** дважды щелкните _эйетраккингдемопоинтерпрофиле_ и добавьте следующую запись в разделе _Параметры указателя_:</span><span class="sxs-lookup"><span data-stu-id="644e4-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="644e4-248">**Тип контроллера:** "Руки", "Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="644e4-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="644e4-249">**Правой или левой:** Всеми</span><span class="sxs-lookup"><span data-stu-id="644e4-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="644e4-250">**Prefab указателя:** дефаултконтроллерпоинтер</span><span class="sxs-lookup"><span data-stu-id="644e4-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="644e4-251">**2. Обнаружение голограммы:** используйте [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) сценарий, чтобы разрешить обнаружение голограммы, как описано выше.</span><span class="sxs-lookup"><span data-stu-id="644e4-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="644e4-252">Вы также можете взглянуть на `FollowEyeGaze` Пример сценария для создания идей, так как это показывает голограмму, следующую за взглядом на глаза (например, курсором), включены ли лучи.</span><span class="sxs-lookup"><span data-stu-id="644e4-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="644e4-253">Теперь, когда вы запускаете демонстрационные сцены отслеживания взгляда, вы должны увидеть луч, поступающий из руки.</span><span class="sxs-lookup"><span data-stu-id="644e4-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="644e4-254">Например, в демонстрационном примере выбора цели отслеживания взгляда полупрозрачный круг по-прежнему отслеживается на взгляде глаза, а драгоценные камни реагируют на то, где они просматривается, а в меню верхней сцены используется первичный указатель ввода (руки).</span><span class="sxs-lookup"><span data-stu-id="644e4-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="644e4-255">Вернуться к "Отслеживание взглядов в Микседреалититулкит"</span><span class="sxs-lookup"><span data-stu-id="644e4-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
