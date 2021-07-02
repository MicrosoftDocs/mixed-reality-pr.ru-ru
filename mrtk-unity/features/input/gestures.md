---
title: Жесты
description: Докумментатион для жестов и его событий в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, жесты,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176885"
---
# <a name="gestures"></a><span data-ttu-id="6fd75-104">Жесты</span><span class="sxs-lookup"><span data-stu-id="6fd75-104">Gestures</span></span>

<span data-ttu-id="6fd75-105">Жесты являются событиями ввода на основе человеческого руки.</span><span class="sxs-lookup"><span data-stu-id="6fd75-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="6fd75-106">Существует два типа устройств, которые вызывают события ввода жестов в МРТК:</span><span class="sxs-lookup"><span data-stu-id="6fd75-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="6fd75-107">Windows Mixed Reality такие устройства, как HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6fd75-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="6fd75-108">Это описывает сжатие движений ("Air TAP") и жесты касания и удерживания.</span><span class="sxs-lookup"><span data-stu-id="6fd75-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="6fd75-109">дополнительные сведения о HoloLens жестах см. в [документации по жестам Windows Mixed Reality](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="6fd75-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="6fd75-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)заключает XR Unity в оболочку [. Головк. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) для использования событий жестов Unity с устройств HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6fd75-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="6fd75-111">Устройства сенсорного экрана.</span><span class="sxs-lookup"><span data-stu-id="6fd75-111">Touch screen devices.</span></span>

  <span data-ttu-id="6fd75-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) заключает [класс касаний Unity](https://docs.unity3d.com/ScriptReference/Touch.html) , который поддерживает физические экраны сенсорного ввода.</span><span class="sxs-lookup"><span data-stu-id="6fd75-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="6fd75-113">оба источника входных данных используют Параметры профиле _жеста_ для преобразования событий касаний и жестов Unity соответственно в [действия ввода](input-actions.md)мртк.</span><span class="sxs-lookup"><span data-stu-id="6fd75-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="6fd75-114">этот профиль можно найти в профиле _входной системы Параметры_ .</span><span class="sxs-lookup"><span data-stu-id="6fd75-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="6fd75-115">События жестов</span><span class="sxs-lookup"><span data-stu-id="6fd75-115">Gesture events</span></span>

<span data-ttu-id="6fd75-116">События жестов получаются путем реализации одного из интерфейсов обработчика жестов: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) или [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (см. таблицу [обработчиков событий](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="6fd75-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="6fd75-117">Пример реализации обработчика событий жеста см. в [примере сцены](#example-scene) .</span><span class="sxs-lookup"><span data-stu-id="6fd75-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="6fd75-118">При реализации универсальной версии события *онжестурекомплетед* и *онжестуреупдатед* могут принимать типизированные данные следующих типов:</span><span class="sxs-lookup"><span data-stu-id="6fd75-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="6fd75-119">`Vector2` — жест 2D-расположения.</span><span class="sxs-lookup"><span data-stu-id="6fd75-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="6fd75-120">Создается сенсорными экранами для информирования о них [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="6fd75-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="6fd75-121">`Vector3` — жест трехмерного позиционирования.</span><span class="sxs-lookup"><span data-stu-id="6fd75-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="6fd75-122">создано HoloLens для информирования о:</span><span class="sxs-lookup"><span data-stu-id="6fd75-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="6fd75-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) события манипуляции</span><span class="sxs-lookup"><span data-stu-id="6fd75-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="6fd75-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) события навигации</span><span class="sxs-lookup"><span data-stu-id="6fd75-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="6fd75-125">`Quaternion` — жест поворота объемного изображения.</span><span class="sxs-lookup"><span data-stu-id="6fd75-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="6fd75-126">Доступен для пользовательских источников входных данных, но в данный момент не создается ни одним из существующих.</span><span class="sxs-lookup"><span data-stu-id="6fd75-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="6fd75-127">`MixedRealityPose` — Объединенный жест трехмерного расположения и поворота.</span><span class="sxs-lookup"><span data-stu-id="6fd75-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="6fd75-128">Доступен для пользовательских источников входных данных, но в данный момент не создается ни одним из существующих.</span><span class="sxs-lookup"><span data-stu-id="6fd75-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="6fd75-129">Порядок событий</span><span class="sxs-lookup"><span data-stu-id="6fd75-129">Order of events</span></span>

<span data-ttu-id="6fd75-130">В зависимости от введенных пользователем данных существует две основные цепочки событий:</span><span class="sxs-lookup"><span data-stu-id="6fd75-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="6fd75-131">"Удержание":</span><span class="sxs-lookup"><span data-stu-id="6fd75-131">"Hold":</span></span>
    1. <span data-ttu-id="6fd75-132">Удержание касания:</span><span class="sxs-lookup"><span data-stu-id="6fd75-132">Hold tap:</span></span>
        - <span data-ttu-id="6fd75-133">начать _манипуляцию_</span><span class="sxs-lookup"><span data-stu-id="6fd75-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="6fd75-134">Держите касание за пределами [холдстартдуратион](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="6fd75-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="6fd75-135">начать _удержание_</span><span class="sxs-lookup"><span data-stu-id="6fd75-135">start _Hold_</span></span>
    1. <span data-ttu-id="6fd75-136">Отпустите кнопку:</span><span class="sxs-lookup"><span data-stu-id="6fd75-136">Release tap:</span></span>
        - <span data-ttu-id="6fd75-137">завершить _удержание_</span><span class="sxs-lookup"><span data-stu-id="6fd75-137">complete _Hold_</span></span>
        - <span data-ttu-id="6fd75-138">завершение _манипуляции_</span><span class="sxs-lookup"><span data-stu-id="6fd75-138">complete _Manipulation_</span></span>

- <span data-ttu-id="6fd75-139">"Переместить":</span><span class="sxs-lookup"><span data-stu-id="6fd75-139">"Move":</span></span>
    1. <span data-ttu-id="6fd75-140">Удержание касания:</span><span class="sxs-lookup"><span data-stu-id="6fd75-140">Hold tap:</span></span>
        - <span data-ttu-id="6fd75-141">начать _манипуляцию_</span><span class="sxs-lookup"><span data-stu-id="6fd75-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="6fd75-142">Держите касание за пределами [холдстартдуратион](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="6fd75-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="6fd75-143">начать _удержание_</span><span class="sxs-lookup"><span data-stu-id="6fd75-143">start _Hold_</span></span>
    1. <span data-ttu-id="6fd75-144">Переместить руку за пределы [навигатионстартсрешолд](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span><span class="sxs-lookup"><span data-stu-id="6fd75-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="6fd75-145">отменить _удержание_</span><span class="sxs-lookup"><span data-stu-id="6fd75-145">cancel _Hold_</span></span>
        - <span data-ttu-id="6fd75-146">начать _навигацию_</span><span class="sxs-lookup"><span data-stu-id="6fd75-146">start _Navigation_</span></span>
    1. <span data-ttu-id="6fd75-147">Отпустите кнопку:</span><span class="sxs-lookup"><span data-stu-id="6fd75-147">Release tap:</span></span>
        - <span data-ttu-id="6fd75-148">завершение _манипуляции_</span><span class="sxs-lookup"><span data-stu-id="6fd75-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="6fd75-149">завершить _навигацию_</span><span class="sxs-lookup"><span data-stu-id="6fd75-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="6fd75-150">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="6fd75-150">Example scene</span></span>

<span data-ttu-id="6fd75-151">Сцена **хандинтерактионжестуривентсексампле** (Assets/Мртк/examples/Хандтраккинг/сцены) показывает, как использовать результат указателя для порождения объекта в месте попадания.</span><span class="sxs-lookup"><span data-stu-id="6fd75-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="6fd75-152">`GestureTester`Скрипт (Assets/мртк/examples/хандтраккинг/script) — это пример реализации для визуализации событий жестов через объекты gameobject.</span><span class="sxs-lookup"><span data-stu-id="6fd75-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="6fd75-153">Функции обработчика изменяют цвет объектов индикаторов и отображают Последнее записанное событие в текстовых объектах сцены.</span><span class="sxs-lookup"><span data-stu-id="6fd75-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
