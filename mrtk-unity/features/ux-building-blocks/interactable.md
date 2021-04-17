---
title: Интерактивный объект
description: Общие сведения об интерактивном компоненте скрипта в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, взаимодействие, события,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581566"
---
# <a name="interactable"></a><span data-ttu-id="d76dc-104">Интерактивный объект</span><span class="sxs-lookup"><span data-stu-id="d76dc-104">Interactable</span></span>

![Интерактивный объект](../images/interactable/InteractableExamples.png)

<span data-ttu-id="d76dc-106">[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)Компонент является контейнером "все в одном", чтобы любой объект мог легко *взаимодействовать* и реагировать на входные данные.</span><span class="sxs-lookup"><span data-stu-id="d76dc-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="d76dc-107">Взаимодействие действует как перехватывать все типы входных данных, включая сенсорный ввод, лучи, речь и т. д., и передают эти взаимодействия в [события](#events) и ответы на [визуальные темы](visual-themes.md) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="d76dc-108">Этот компонент предоставляет простой способ создания кнопок, изменения цвета объектов с фокусом и т. д.</span><span class="sxs-lookup"><span data-stu-id="d76dc-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="d76dc-109">Настройка взаимодействующих</span><span class="sxs-lookup"><span data-stu-id="d76dc-109">How to configure Interactable</span></span>

<span data-ttu-id="d76dc-110">Компонент позволяет создавать три основных раздела конфигурации:</span><span class="sxs-lookup"><span data-stu-id="d76dc-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="d76dc-111">Общая конфигурация ввода</span><span class="sxs-lookup"><span data-stu-id="d76dc-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="d76dc-112">[Визуальные темы](visual-themes.md) , предназначенные для нескольких объекты gameobject</span><span class="sxs-lookup"><span data-stu-id="d76dc-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="d76dc-113">Обработчики событий</span><span class="sxs-lookup"><span data-stu-id="d76dc-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="d76dc-114">Общие параметры ввода</span><span class="sxs-lookup"><span data-stu-id="d76dc-114">General input settings</span></span>

![Общие взаимодействующие параметры](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="d76dc-116">**Состояния**</span><span class="sxs-lookup"><span data-stu-id="d76dc-116">**States**</span></span>

<span data-ttu-id="d76dc-117">*Состояния* — это параметр [скриптаблеобжект](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , определяющий этапы взаимодействия, такие как нажатие или наблюдающие, для [взаимодействующих профилей](#interactable-profiles) и [визуальных тем](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="d76dc-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="d76dc-118">**Дефаултинтерактаблестатес** (Assets/МРТК/SDK/Features/UX/взаимодействующие/штатыs/дефаултинтерактаблестатес. Asset) поставляется вместе с мртк и является параметром по умолчанию для *взаимодействующих* компонентов.</span><span class="sxs-lookup"><span data-stu-id="d76dc-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Пример состояния Скриптаблеобжект в инспекторе](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="d76dc-120">Ресурс *дефаултинтерактаблестатес* содержит четыре состояния и использует [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) реализацию модели состояний.</span><span class="sxs-lookup"><span data-stu-id="d76dc-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="d76dc-121">**По умолчанию**: ничего не происходит, это наиболее изолированное базовое состояние.</span><span class="sxs-lookup"><span data-stu-id="d76dc-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="d76dc-122">**Фокус**: объект указывает на.</span><span class="sxs-lookup"><span data-stu-id="d76dc-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="d76dc-123">Это одно состояние, другие состояния в настоящее время не заданы, но значение по умолчанию будет рангом.</span><span class="sxs-lookup"><span data-stu-id="d76dc-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="d76dc-124">**Нажмите клавишу**: объект указывает на, а кнопка или руки нажата.</span><span class="sxs-lookup"><span data-stu-id="d76dc-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="d76dc-125">По умолчанию и фокус выжимает состояние.</span><span class="sxs-lookup"><span data-stu-id="d76dc-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="d76dc-126">Это состояние также будет установлено в качестве резервного для физического нажатия.</span><span class="sxs-lookup"><span data-stu-id="d76dc-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="d76dc-127">**Отключено**. кнопка не должна быть интерактивной, и визуальная обратная связь позволит пользователю узнать, по какой причине эта кнопка не используется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="d76dc-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="d76dc-128">Теоретически отключенное состояние может содержать все остальные состояния, но если включен, отключенное состояние замещает все остальные состояния.</span><span class="sxs-lookup"><span data-stu-id="d76dc-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="d76dc-129">Значение бита (#) присваивается состоянию в зависимости от порядка в списке.</span><span class="sxs-lookup"><span data-stu-id="d76dc-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="d76dc-130">При создании *взаимодействующих* компонентов, как правило, рекомендуется использовать **дефаултинтерактаблестатес** (Assets/Мртк/SDK/Features/UX/взаимодействовать/States/дефаултинтерактаблестатес. Asset).</span><span class="sxs-lookup"><span data-stu-id="d76dc-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="d76dc-131">Однако доступно 17 взаимодействующих состояний, которые можно использовать для работы с темами, хотя некоторые из них предназначены для других компонентов.</span><span class="sxs-lookup"><span data-stu-id="d76dc-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="d76dc-132">Ниже приведен список встроенных функций.</span><span class="sxs-lookup"><span data-stu-id="d76dc-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="d76dc-133">Посещено: выбрано взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="d76dc-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="d76dc-134">Переключено: кнопка находится в переключенном состоянии или индексе измерения нечетное число.</span><span class="sxs-lookup"><span data-stu-id="d76dc-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="d76dc-135">Жест: была нажата рука или контроллер и перемещена из исходной должности.</span><span class="sxs-lookup"><span data-stu-id="d76dc-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="d76dc-136">Воицекомманд: для активации взаимодействия используется Голосовая команда.</span><span class="sxs-lookup"><span data-stu-id="d76dc-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="d76dc-137">Фисикалтауч: в настоящее время обнаружен сенсорный ввод, используется [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) для включения.</span><span class="sxs-lookup"><span data-stu-id="d76dc-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="d76dc-138">Захват: Сейчас в границах объекта передается рука, используется [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) для включения</span><span class="sxs-lookup"><span data-stu-id="d76dc-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="d76dc-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d76dc-139">**Enabled**</span></span>

<span data-ttu-id="d76dc-140">Указывает, включен ли режим взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d76dc-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="d76dc-141">Это соответствует [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) в коде.</span><span class="sxs-lookup"><span data-stu-id="d76dc-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="d76dc-142">Свойство, доступное *для взаимодействия* , отличается от свойства Enabled, настроенного через GameObject/Component (т. е.</span><span class="sxs-lookup"><span data-stu-id="d76dc-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="d76dc-143">Сетактиве и т. д.).</span><span class="sxs-lookup"><span data-stu-id="d76dc-143">SetActive etc).</span></span> <span data-ttu-id="d76dc-144">Отключение GameObject или *интерактивного* режима работы приведет к отключению всех элементов класса от выполнения, включая входные данные, визуальные темы, события и т. д. Отключение через [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) приведет к отключению максимальной обработки ввода, сбросу связанных состояний ввода.</span><span class="sxs-lookup"><span data-stu-id="d76dc-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="d76dc-145">Однако класс по-прежнему будет выполнять все кадры и получать события ввода, которые будут игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="d76dc-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="d76dc-146">Это полезно для отображения взаимодействия в отключенном состоянии, которое можно выполнить с помощью визуальных тем.</span><span class="sxs-lookup"><span data-stu-id="d76dc-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="d76dc-147">Типичным примером этого является Кнопка Submit, ожидающая завершения всех обязательных полей ввода.</span><span class="sxs-lookup"><span data-stu-id="d76dc-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="d76dc-148">**Действия ввода**</span><span class="sxs-lookup"><span data-stu-id="d76dc-148">**Input Actions**</span></span>

<span data-ttu-id="d76dc-149">Выберите [Входное действие](../input/input-actions.md) из профиля входной конфигурации или сопоставления контроллера, к которому должен реагировать *взаимодействующий* компонент.</span><span class="sxs-lookup"><span data-stu-id="d76dc-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="d76dc-150">Это свойство может быть настроено во время выполнения в коде через [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="d76dc-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="d76dc-151">**IsGlobal**</span></span>

<span data-ttu-id="d76dc-152">Если значение — true, компонент будет помечен как глобальный входной прослушиватель для выбранного [действия ввода](../input/input-actions.md).</span><span class="sxs-lookup"><span data-stu-id="d76dc-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="d76dc-153">Поведение по умолчанию — false, которое ограничивает входные данные только этим *взаимодействующим* конфликтующим или GameObject.</span><span class="sxs-lookup"><span data-stu-id="d76dc-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="d76dc-154">Это свойство может быть настроено во время выполнения в коде через [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="d76dc-155">**Голосовая команда**</span><span class="sxs-lookup"><span data-stu-id="d76dc-155">**Speech Command**</span></span>

<span data-ttu-id="d76dc-156">[Голосовая команда](../input/speech.md), из профиля команд распознавания речи мртк, чтобы активировать событие OnClick для голосового взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d76dc-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="d76dc-157">Это свойство может быть настроено во время выполнения в коде через [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="d76dc-158">**Требуется фокус**</span><span class="sxs-lookup"><span data-stu-id="d76dc-158">**Requires Focus**</span></span>

<span data-ttu-id="d76dc-159">Если значение — true, команда Voice активирует только *взаимодействующий* только в том случае, если она уже имеет фокус от указателя.</span><span class="sxs-lookup"><span data-stu-id="d76dc-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="d76dc-160">Если значение равно false, то *взаимодействие* будет действовать как глобальный прослушиватель для выбранной команды Voice.</span><span class="sxs-lookup"><span data-stu-id="d76dc-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="d76dc-161">Поведение по умолчанию — true, так как несколько глобальных прослушивателей речи могут быть трудно организованы в сцене.</span><span class="sxs-lookup"><span data-stu-id="d76dc-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="d76dc-162">Это свойство может быть настроено во время выполнения в коде через [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="d76dc-163">**Режим выбора**</span><span class="sxs-lookup"><span data-stu-id="d76dc-163">**Selection Mode**</span></span>

<span data-ttu-id="d76dc-164">Это свойство определяет логику выбора.</span><span class="sxs-lookup"><span data-stu-id="d76dc-164">This property defines the selection logic.</span></span> <span data-ttu-id="d76dc-165">Когда вы щелкнули *взаимодействие* , он перебирается в следующий уровень *измерения* .</span><span class="sxs-lookup"><span data-stu-id="d76dc-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="d76dc-166">*Измерения* похожи на ранжирование и определяют состояние за пределами входных данных (т. е.</span><span class="sxs-lookup"><span data-stu-id="d76dc-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="d76dc-167">фокус, нажмите и т. д.).</span><span class="sxs-lookup"><span data-stu-id="d76dc-167">focus, press etc).</span></span> <span data-ttu-id="d76dc-168">Они полезны для определения состояния переключения или других многоранговых состояний, связанных с кнопкой.</span><span class="sxs-lookup"><span data-stu-id="d76dc-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="d76dc-169">Текущий уровень измерения отдается по `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="d76dc-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="d76dc-170">Доступны следующие режимы выбора:</span><span class="sxs-lookup"><span data-stu-id="d76dc-170">The selection modes available are:</span></span>

* <span data-ttu-id="d76dc-171">**Кнопка "**  -  *Измерения* = 1, простой *Интерактивный* щелчок</span><span class="sxs-lookup"><span data-stu-id="d76dc-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="d76dc-172">**Переключатель**  -  *Измерения* = 2, *взаимодействующие* альтернативы *в* / *отключенном* состоянии</span><span class="sxs-lookup"><span data-stu-id="d76dc-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="d76dc-173">Многомерное **измерение**  -  *Измерения* >= 3, каждый щелчок увеличивает текущий уровень измерения + 1.</span><span class="sxs-lookup"><span data-stu-id="d76dc-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="d76dc-174">Полезно для определения состояния кнопки в списке и т. д.</span><span class="sxs-lookup"><span data-stu-id="d76dc-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="d76dc-175">Возможность *взаимодействия* позволяет определить несколько тем для каждого *измерения*.</span><span class="sxs-lookup"><span data-stu-id="d76dc-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="d76dc-176">Например, если параметр *SelectionMode = Toggle*, то можно применить одну тему, когда будет отменена возможность *взаимодействия* *и была* применена другая тема при *выборе* компонента.</span><span class="sxs-lookup"><span data-stu-id="d76dc-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="d76dc-177">Текущий режим выбора можно запросить во время выполнения с помощью [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="d76dc-178">Обновление режима во время выполнения может быть достигнуто путем задания  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) свойства в соответствии с требуемой функциональностью.</span><span class="sxs-lookup"><span data-stu-id="d76dc-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="d76dc-179">Кроме того, доступ к текущему измерению, полезному для *переключения* и режимов с *несколькими измерениями* , можно получить с помощью [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="d76dc-180">Взаимодействующие профили</span><span class="sxs-lookup"><span data-stu-id="d76dc-180">Interactable profiles</span></span>

<span data-ttu-id="d76dc-181">*Профили* — это элементы, которые создают связь между GameObject и [визуальной темой](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="d76dc-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="d76dc-182">Профиль определяет, какое содержимое будет управляться темой при [изменении состояния](#general-input-settings).</span><span class="sxs-lookup"><span data-stu-id="d76dc-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="d76dc-183">Темы работают очень похоже на материалы.</span><span class="sxs-lookup"><span data-stu-id="d76dc-183">Themes work a lot like materials.</span></span> <span data-ttu-id="d76dc-184">Они являются объектами, поддерживающими скрипты, которые содержат список свойств, которые будут назначены объекту на основе текущего состояния.</span><span class="sxs-lookup"><span data-stu-id="d76dc-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="d76dc-185">Темы также можно повторно использовать и назначать в нескольких *взаимодействующих* объектах UX.</span><span class="sxs-lookup"><span data-stu-id="d76dc-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="d76dc-186">**Сброс при уничтожении**</span><span class="sxs-lookup"><span data-stu-id="d76dc-186">**Reset On Destroy**</span></span>

<span data-ttu-id="d76dc-187">Визуальные темы изменяют различные свойства целевого GameObject, зависящие от класса и типа выбранного обработчика тем.</span><span class="sxs-lookup"><span data-stu-id="d76dc-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="d76dc-188">Если параметр *Reset в результате уничтожения* имеет значение true при уничтожении взаимодействующего компонента, компонент сбрасывает все измененные свойства из активных тем в исходные значения.</span><span class="sxs-lookup"><span data-stu-id="d76dc-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="d76dc-189">В противном случае при удалении взаимодействующего компонента все измененные свойства будут оставлены как есть.</span><span class="sxs-lookup"><span data-stu-id="d76dc-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="d76dc-190">В этом последнем случае Последнее состояние значений будет сохранено, если только не изменится другим внешним компонентом.</span><span class="sxs-lookup"><span data-stu-id="d76dc-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="d76dc-191">Значение по умолчанию – false.</span><span class="sxs-lookup"><span data-stu-id="d76dc-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="d76dc-192">События</span><span class="sxs-lookup"><span data-stu-id="d76dc-192">Events</span></span>

<span data-ttu-id="d76dc-193">Каждый *взаимодействующий* компонент имеет событие *OnClick* , которое срабатывает при простом выборе компонента.</span><span class="sxs-lookup"><span data-stu-id="d76dc-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="d76dc-194">Однако *взаимодействие* можно использовать для обнаружения событий ввода, отличных от простого *щелчка*.</span><span class="sxs-lookup"><span data-stu-id="d76dc-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="d76dc-195">Нажмите кнопку *Добавить событие* , чтобы добавить новый тип определения приемника событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="d76dc-196">После добавления выберите нужный тип события.</span><span class="sxs-lookup"><span data-stu-id="d76dc-196">Once added, select the type of Event desired.</span></span>

![Пример событий](../images/interactable/Events.png)<span data-ttu-id="d76dc-198">)</span><span class="sxs-lookup"><span data-stu-id="d76dc-198">)</span></span>

<span data-ttu-id="d76dc-199">Существуют различные типы приемников событий для реагирования на различные типы входных данных.</span><span class="sxs-lookup"><span data-stu-id="d76dc-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="d76dc-200">МРТК поставляется со следующим набором получателей.</span><span class="sxs-lookup"><span data-stu-id="d76dc-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="d76dc-201">Пользовательский приемник можно создать, сделав новый класс, который расширяет [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="d76dc-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Пример приемника событий для переключателя](../images/interactable/Event_toggle.png)

<span data-ttu-id="d76dc-203">*Пример приемника событий переключателя*</span><span class="sxs-lookup"><span data-stu-id="d76dc-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="d76dc-204">Взаимодействующие получатели</span><span class="sxs-lookup"><span data-stu-id="d76dc-204">Interactable receivers</span></span>

 <span data-ttu-id="d76dc-205">[`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)Компонент позволяет определять события за пределами исходного *взаимодействующего* компонента.</span><span class="sxs-lookup"><span data-stu-id="d76dc-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="d76dc-206">*Интерактаблерецеивер* будет прослушивать тип отфильтрованного события, запущенного другим *взаимодействующим*.</span><span class="sxs-lookup"><span data-stu-id="d76dc-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="d76dc-207">Если *взаимодействующее* свойство не назначено напрямую, свойство *области поиска* определяет направление, в котором *интерактаблерецеивер* прослушивает события, которые находятся либо в самом родительском объекте, либо в дочернем GameObject.</span><span class="sxs-lookup"><span data-stu-id="d76dc-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="d76dc-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) действует так же, как и список соответствующих событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="d76dc-209">Создание пользовательских событий</span><span class="sxs-lookup"><span data-stu-id="d76dc-209">Create custom events</span></span>

<span data-ttu-id="d76dc-210">Как и в случае с [визуальными темами](visual-themes.md#custom-theme-engines), события могут быть расширены для обнаружения любого шаблона состояния или для предоставления функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="d76dc-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="d76dc-211">Пользовательские события могут создаваться двумя основными способами.</span><span class="sxs-lookup"><span data-stu-id="d76dc-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="d76dc-212">Расширьте [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) класс, чтобы создать пользовательское событие, которое будет отображаться в раскрывающемся списке типов событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="d76dc-213">Событие Unity предоставляется по умолчанию, но можно добавлять дополнительные события Unity, а также можно задать событие, чтобы скрыть события Unity.</span><span class="sxs-lookup"><span data-stu-id="d76dc-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="d76dc-214">Эта функция позволяет конструктору работать с инженером в проекте для создания пользовательского события, которое конструктор может настроить в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d76dc-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="d76dc-215">Расширьте [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) класс, чтобы создать полностью настраиваемый компонент событий, который может располагаться в *взаимодействующем* или другом объекте.</span><span class="sxs-lookup"><span data-stu-id="d76dc-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="d76dc-216">[`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)Будет ссылаться на *взаимодействие* для обнаружения изменений состояния.</span><span class="sxs-lookup"><span data-stu-id="d76dc-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="d76dc-217">Пример расширения `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="d76dc-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="d76dc-218">[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)Класс отображает сведения о состоянии *взаимодействия* и представляет собой пример создания пользовательского приемника событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="d76dc-219">Следующие методы полезны для переопределения или реализации при создании пользовательского приемника событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="d76dc-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) — Это абстрактный метод, который можно использовать для обнаружения шаблонов состояний и переходов.</span><span class="sxs-lookup"><span data-stu-id="d76dc-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="d76dc-221">Кроме того, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) методы и полезны для создания пользовательской логики событий при выборе *взаимодействия* .</span><span class="sxs-lookup"><span data-stu-id="d76dc-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="d76dc-222">Отображение настраиваемых полей приемника событий в инспекторе</span><span class="sxs-lookup"><span data-stu-id="d76dc-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="d76dc-223">Сценарии *рецеивербасе* используют [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) атрибуты для предоставления пользовательских свойств в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="d76dc-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="d76dc-224">Ниже приведен пример Vector3, настраиваемого свойства с информацией о подсказке и метке.</span><span class="sxs-lookup"><span data-stu-id="d76dc-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="d76dc-225">Это свойство будет отображаться как настраиваемое в инспекторе, если выбрано *взаимодействующее* GameObject и добавлен связанный тип *приемника событий* .</span><span class="sxs-lookup"><span data-stu-id="d76dc-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="d76dc-226">Использование взаимодействующих</span><span class="sxs-lookup"><span data-stu-id="d76dc-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="d76dc-227">Создание простой кнопки</span><span class="sxs-lookup"><span data-stu-id="d76dc-227">Building a simple button</span></span>

<span data-ttu-id="d76dc-228">Можно создать простую кнопку, добавив *взаимодействующий* компонент в GameObject, настроенный для получения входных событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="d76dc-229">Для получения входных данных у него может быть или потомок.</span><span class="sxs-lookup"><span data-stu-id="d76dc-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="d76dc-230">Если вы используете *взаимодействие* с объекты gameobject на основе пользовательского интерфейса Unity, он должен находиться под GameObject Canvas.</span><span class="sxs-lookup"><span data-stu-id="d76dc-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="d76dc-231">Переведите кнопку на один шаг дальше, создав новый профиль, назначив сам GameObject и создав новую тему.</span><span class="sxs-lookup"><span data-stu-id="d76dc-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="d76dc-232">Более того, используйте событие *OnClick* , чтобы сделать что-то произошло.</span><span class="sxs-lookup"><span data-stu-id="d76dc-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="d76dc-233">Для нажатия [кнопки](button.md) требуется [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) компонент.</span><span class="sxs-lookup"><span data-stu-id="d76dc-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="d76dc-234">Кроме того, [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) компонент необходим для того, чтобы перенажимать события в *взаимодействующий* компонент.</span><span class="sxs-lookup"><span data-stu-id="d76dc-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="d76dc-235">Создание переключателей и кнопок с несколькими измерениями</span><span class="sxs-lookup"><span data-stu-id="d76dc-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="d76dc-236">Выключатель</span><span class="sxs-lookup"><span data-stu-id="d76dc-236">Toggle button</span></span>

<span data-ttu-id="d76dc-237">Чтобы включить переключатель, измените [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) поле на тип `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="d76dc-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="d76dc-238">В разделе *Профили* добавляется новая переключаемая тема для каждого профиля, используемого при переключении на *взаимодействие* .</span><span class="sxs-lookup"><span data-stu-id="d76dc-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="d76dc-239">Хотя [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) для задано значение переключателя, флажок «с *переключателем* » можно использовать для установки значения по умолчанию элемента управления во время инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="d76dc-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="d76dc-240">*Канселект* означает, что возможность *взаимодействия* может быть *отключена* *, а* *кандеселект* — обратным.</span><span class="sxs-lookup"><span data-stu-id="d76dc-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Пример с переключением визуальных тем для профиля](../images/interactable/Profile_toggle.png)

<span data-ttu-id="d76dc-242">Разработчики могут использовать [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) интерфейсы и [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) для получения или установки состояния переключения, *взаимодействующего* через код.</span><span class="sxs-lookup"><span data-stu-id="d76dc-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="d76dc-243">Переключить коллекцию кнопок</span><span class="sxs-lookup"><span data-stu-id="d76dc-243">Toggle button collection</span></span>

<span data-ttu-id="d76dc-244">Обычно имеется список выключателей, где только один из них может быть активным в любой момент времени, также известный как радиальный набор или переключатели и т. д.</span><span class="sxs-lookup"><span data-stu-id="d76dc-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="d76dc-245">Используйте [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) компонент, чтобы включить эту функцию.</span><span class="sxs-lookup"><span data-stu-id="d76dc-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="d76dc-246">Этот элемент управления гарантирует, что в любой момент времени переключается только одна *взаимодействующая* .</span><span class="sxs-lookup"><span data-stu-id="d76dc-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="d76dc-247">« *Радиальный* » (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/радиальный. prefab) также является великолепной отправной точкой.</span><span class="sxs-lookup"><span data-stu-id="d76dc-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="d76dc-248">Чтобы создать пользовательскую радиальную группу кнопок, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d76dc-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="d76dc-249">Создание нескольких *взаимодействующих* объекты gameobject/кнопок</span><span class="sxs-lookup"><span data-stu-id="d76dc-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="d76dc-250">Задайте каждый *взаимодействующий* с *SelectionMode* = Toggle, *канселект* = true и *кандеселект* = false.</span><span class="sxs-lookup"><span data-stu-id="d76dc-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="d76dc-251">Создание пустой родительской GameObject для всех *интерактаблес* и Добавление компонента *интерактаблетогглеколлектион*</span><span class="sxs-lookup"><span data-stu-id="d76dc-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="d76dc-252">Добавить все *интерактаблес* в *тогглелист* на *интерактаблетогглеколлектион*</span><span class="sxs-lookup"><span data-stu-id="d76dc-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="d76dc-253">Задайте свойство *интерактаблетогглеколлектион. куррентиндекс* , чтобы определить, какая кнопка выбрана по умолчанию при запуске.</span><span class="sxs-lookup"><span data-stu-id="d76dc-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="d76dc-254">Многомерная кнопка</span><span class="sxs-lookup"><span data-stu-id="d76dc-254">Multi-dimensional button</span></span>

<span data-ttu-id="d76dc-255">Режим выбора с несколькими измерениями используется для создания последовательных кнопок или для кнопки, которая содержит более двух шагов, например для управления скоростью с тремя значениями: быстрый (1x), быстрый (2x) или самый быстрый (3 раза).</span><span class="sxs-lookup"><span data-stu-id="d76dc-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="d76dc-256">Если измерение является числовым значением, можно добавить до 9 тем, чтобы управлять текстовой меткой или текстурой кнопки для каждого параметра скорости, используя разные темы для каждого шага.</span><span class="sxs-lookup"><span data-stu-id="d76dc-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="d76dc-257">Каждое событие нажатия переходит на `DimensionIndex` 1 во время выполнения, пока `Dimensions` не будет достигнуто значение.</span><span class="sxs-lookup"><span data-stu-id="d76dc-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="d76dc-258">Затем цикл сбрасывается в 0.</span><span class="sxs-lookup"><span data-stu-id="d76dc-258">Then the cycle will reset to 0.</span></span>

![Пример многомерного профиля](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="d76dc-260">Разработчики могут оценить, [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) чтобы определить, какое измерение в настоящее время активно.</span><span class="sxs-lookup"><span data-stu-id="d76dc-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="d76dc-261">Создание взаимодействующих во время выполнения</span><span class="sxs-lookup"><span data-stu-id="d76dc-261">Create Interactable at runtime</span></span>

<span data-ttu-id="d76dc-262">*Взаимодействие* можно легко добавить в любой GameObject во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d76dc-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="d76dc-263">В следующем примере показано, как назначить профиль с помощью [визуальной темы](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="d76dc-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="d76dc-264">Взаимодействующие события с помощью кода</span><span class="sxs-lookup"><span data-stu-id="d76dc-264">Interactable events via code</span></span>

<span data-ttu-id="d76dc-265">Один из них может добавить действие к базовому [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) событию с помощью кода в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d76dc-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="d76dc-266">Используйте [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) функцию, чтобы динамически добавлять приемники событий во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d76dc-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="d76dc-267">В приведенном ниже примере кода показано, как добавить [интерактаблеонфокусрецеивер](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), который прослушивает фокус ввода/вывода, а также определяет код действия, выполняемого при срабатывании экземпляров событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="d76dc-268">В приведенном ниже примере кода показано, как добавить [интерактаблеонтогглерецеивер](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), который прослушивает выбранные/снятые переходы состояния при переключении *интерактаблес*, а также определяет код действия, выполняемый при срабатывании экземпляров событий.</span><span class="sxs-lookup"><span data-stu-id="d76dc-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="d76dc-269">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d76dc-269">See also</span></span>

* [<span data-ttu-id="d76dc-270">Визуальные темы</span><span class="sxs-lookup"><span data-stu-id="d76dc-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="d76dc-271">Действия ввода</span><span class="sxs-lookup"><span data-stu-id="d76dc-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="d76dc-272">Речевые команды</span><span class="sxs-lookup"><span data-stu-id="d76dc-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="d76dc-273">Кнопки</span><span class="sxs-lookup"><span data-stu-id="d76dc-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="d76dc-274">Стандартный шейдер MRTK</span><span class="sxs-lookup"><span data-stu-id="d76dc-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
