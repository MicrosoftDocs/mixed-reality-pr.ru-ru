---
title: Входные события
description: Документация по Инпутевентс в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, события
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145220"
---
# <a name="input-events"></a><span data-ttu-id="d5d9a-104">События ввода</span><span class="sxs-lookup"><span data-stu-id="d5d9a-104">Input events</span></span>

<span data-ttu-id="d5d9a-105">В следующем списке перечислены все доступные интерфейсы входных событий, которые должны быть реализованы в пользовательском компоненте с нестандартным поведением.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="d5d9a-106">Эти интерфейсы будут вызываться входной системой МРТК для обработки пользовательской логики приложения на основе взаимодействия с пользовательским входом.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="d5d9a-107">[События ввода указателя](pointers.md#pointer-event-interfaces) обрабатываются немного иначе, чем стандартные типы событий ввода, приведенные ниже.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5d9a-108">По умолчанию скрипт будет получать входные события только в том случае, если это GameObject фокус на указатель или родительский элемент GameObject в фокусе.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="d5d9a-109">Обработчик</span><span class="sxs-lookup"><span data-stu-id="d5d9a-109">Handler</span></span> | <span data-ttu-id="d5d9a-110">События</span><span class="sxs-lookup"><span data-stu-id="d5d9a-110">Events</span></span> | <span data-ttu-id="d5d9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="d5d9a-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="d5d9a-112">Источник обнаружен/потерян</span><span class="sxs-lookup"><span data-stu-id="d5d9a-112">Source Detected / Lost</span></span> | <span data-ttu-id="d5d9a-113">Возникает при обнаружении или утере источника входных данных, например при обнаружении или потере наподобие руки.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="d5d9a-114">Исходное удаление изменено</span><span class="sxs-lookup"><span data-stu-id="d5d9a-114">Source Pose Changed</span></span> | <span data-ttu-id="d5d9a-115">Возникает при изменениях исходного объекта.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-115">Raised on source pose changes.</span></span> <span data-ttu-id="d5d9a-116">Исходная единица представляет собой общую часть источника входных данных.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="d5d9a-117">Конкретные удаления, например захват или указатель на шести ДОФ контроллере, можно получить с помощью `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="d5d9a-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="d5d9a-118">Ввод вниз/вверх</span><span class="sxs-lookup"><span data-stu-id="d5d9a-118">Input Down / Up</span></span> | <span data-ttu-id="d5d9a-119">Возникает при изменениях бинарных входных данных, таких как кнопки.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="d5d9a-120">Ввод изменен</span><span class="sxs-lookup"><span data-stu-id="d5d9a-120">Input Changed</span></span> | <span data-ttu-id="d5d9a-121">Возникает при изменениях входных данных заданного типа.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="d5d9a-122">**T** может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="d5d9a-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="d5d9a-123">- *float* (например, возвращает Аналоговый триггер)</span><span class="sxs-lookup"><span data-stu-id="d5d9a-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="d5d9a-124">- *Vector2* (например, Возвращает направление аналогового стика планшета)</span><span class="sxs-lookup"><span data-stu-id="d5d9a-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="d5d9a-125">- *Vector3* (например, возвращаемое расположение отслеживания устройства)</span><span class="sxs-lookup"><span data-stu-id="d5d9a-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="d5d9a-126">- *Кватернион* (например, возвращает ориентацию отслеживающего устройства)</span><span class="sxs-lookup"><span data-stu-id="d5d9a-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="d5d9a-127">- [Микседреалитипосе](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (например, возвращает полностью отслеживание устройства)</span><span class="sxs-lookup"><span data-stu-id="d5d9a-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="d5d9a-128">Распознанное ключевое слово речи</span><span class="sxs-lookup"><span data-stu-id="d5d9a-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="d5d9a-129">Возникает при распознавании одного из ключевых слов, настроенных в *профиле голосовых команд*.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="d5d9a-130">Диктовка</span><span class="sxs-lookup"><span data-stu-id="d5d9a-130">Dictation</span></span><br/> <span data-ttu-id="d5d9a-131">Гипотеза</span><span class="sxs-lookup"><span data-stu-id="d5d9a-131">Hypothesis</span></span> <br/> <span data-ttu-id="d5d9a-132">Результат</span><span class="sxs-lookup"><span data-stu-id="d5d9a-132">Result</span></span> <br/> <span data-ttu-id="d5d9a-133">Завершить</span><span class="sxs-lookup"><span data-stu-id="d5d9a-133">Complete</span></span> <br/> <span data-ttu-id="d5d9a-134">Ошибка</span><span class="sxs-lookup"><span data-stu-id="d5d9a-134">Error</span></span> | <span data-ttu-id="d5d9a-135">Вызывается системами диктовки для передачи результатов сеанса диктовки.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="d5d9a-136">События жестов в:</span><span class="sxs-lookup"><span data-stu-id="d5d9a-136">Gesture events on:</span></span> <br/> <span data-ttu-id="d5d9a-137">Запуск</span><span class="sxs-lookup"><span data-stu-id="d5d9a-137">Started</span></span> <br/> <span data-ttu-id="d5d9a-138">Обновлено</span><span class="sxs-lookup"><span data-stu-id="d5d9a-138">Updated</span></span> <br/> <span data-ttu-id="d5d9a-139">Завершено</span><span class="sxs-lookup"><span data-stu-id="d5d9a-139">Completed</span></span> <br/> <span data-ttu-id="d5d9a-140">Отменено</span><span class="sxs-lookup"><span data-stu-id="d5d9a-140">Canceled</span></span> | <span data-ttu-id="d5d9a-141">Вызывается при обнаружении жеста.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="d5d9a-142">Жест обновлен или завершен</span><span class="sxs-lookup"><span data-stu-id="d5d9a-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="d5d9a-143">Возникает при обнаружении жестов, содержащих дополнительные данные заданного типа.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="d5d9a-144">Дополнительные сведения о возможных значениях для **T** см. в разделе [**события жестов**](gestures.md#gesture-events) .</span><span class="sxs-lookup"><span data-stu-id="d5d9a-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="d5d9a-145">Обновлено соединений с руки</span><span class="sxs-lookup"><span data-stu-id="d5d9a-145">Hand Joints Updated</span></span> | <span data-ttu-id="d5d9a-146">Генерируется с помощью манипуляторов контроллеров, когда обновляются соединения.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="d5d9a-147">Сетка "руки" обновлена</span><span class="sxs-lookup"><span data-stu-id="d5d9a-147">Hand Mesh Updated</span></span> | <span data-ttu-id="d5d9a-148">Вызывается контроллерами с выявлением руки при обновлении сетки типа "рука".</span><span class="sxs-lookup"><span data-stu-id="d5d9a-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="d5d9a-149">Действие запущено/завершено</span><span class="sxs-lookup"><span data-stu-id="d5d9a-149">Action Started / Ended</span></span> | <span data-ttu-id="d5d9a-150">Вызывает, чтобы указать начало и конец действия для входных данных, сопоставленных с действиями.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="d5d9a-151">Входные события в действии</span><span class="sxs-lookup"><span data-stu-id="d5d9a-151">Input events in action</span></span>

<span data-ttu-id="d5d9a-152">На уровне скрипта входные события могут быть использованы путем реализации одного из интерфейсов обработчика событий, показанных в приведенной выше таблице.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="d5d9a-153">Когда событие ввода вызывается через взаимодействие с пользователем, происходит следующее:</span><span class="sxs-lookup"><span data-stu-id="d5d9a-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="d5d9a-154">Система ввода МРТК распознает, что произошло событие ввода.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="d5d9a-155">Входная система МРТК запускает соответствующую функцию интерфейса входного события во все [зарегистрированные глобальные входные обработчики](#register-for-global-input-events) .</span><span class="sxs-lookup"><span data-stu-id="d5d9a-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="d5d9a-156">Для каждого активного указателя, зарегистрированного в системе ввода:</span><span class="sxs-lookup"><span data-stu-id="d5d9a-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="d5d9a-157">Входная система определяет, на какой GameObject фокус находится текущий указатель.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="d5d9a-158">Входная система использует [систему событий Unity](https://docs.unity3d.com/Manual/EventSystem.html) для запуска соответствующей функции интерфейса для всех совпадающих компонентов в фокусе GameObject.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="d5d9a-159">Если в любой момент входное событие было [помечено как используемое](#how-to-stop-input-events), процесс завершится, а последующие объекты gameobject не получат обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="d5d9a-160">Пример. [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) при распознавании речевой команды будет выполнен поиск компонентов, реализующих интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="d5d9a-161">Примечание. Система событий Unity будет выполнять поиск в родительском GameObject, если ни один из компонентов, соответствующих требуемому интерфейсу, не найден в текущем GameObject.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="d5d9a-162">Если не зарегистрированы глобальные входные обработчики и не найден GameObject с соответствующим компонентом или интерфейсом, то входная система будет вызывать каждый резервный обработчик входных данных.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="d5d9a-163">[События ввода указателя](pointers.md#pointer-event-interfaces) обрабатываются немного иначе, чем указанные выше интерфейсы входных событий.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="d5d9a-164">В частности, входные события указателя обрабатываются только GameObject фокусом указателя, который активировал событие ввода, а также любыми глобальными обработчиками ввода.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="d5d9a-165">Обычные события ввода обрабатываются объекты gameobject в фокусе для всех активных указателей.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="d5d9a-166">Пример интерфейса входных событий</span><span class="sxs-lookup"><span data-stu-id="d5d9a-166">Input event interface example</span></span>

<span data-ttu-id="d5d9a-167">В приведенном ниже коде показано использование [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="d5d9a-168">Когда пользователь говорит слова «меньше» или «больше» при GameObjectе с этим `ShowHideSpeechHandler` классом, GameObject будет масштабироваться вдвое или вдвое больше.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="d5d9a-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) для входных событий требуется, чтобы требуемые ключевые слова были предварительно зарегистрированы в [профиле голосовых команд мртк](speech.md).</span><span class="sxs-lookup"><span data-stu-id="d5d9a-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="d5d9a-170">Регистрация для глобальных входных событий</span><span class="sxs-lookup"><span data-stu-id="d5d9a-170">Register for global input events</span></span>

<span data-ttu-id="d5d9a-171">Чтобы создать компонент, который прослушивает глобальные входные события, не относящийся к GameObject, компонент должен зарегистрироваться в системе ввода.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="d5d9a-172">После регистрации все экземпляры этого одноименного поведения будут получать события ввода и все GameObject, на данный момент находящиеся в фокусе, и другие глобальные зарегистрированные прослушиватели.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="d5d9a-173">Если событие ввода было [помечено как используемое](#how-to-stop-input-events), глобальные зарегистрированные обработчики все равно будут принимать обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="d5d9a-174">Однако ни один из объекты gameobject не получит событие.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="d5d9a-175">Пример глобальной регистрации входных данных</span><span class="sxs-lookup"><span data-stu-id="d5d9a-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="d5d9a-176">Регистрация для резервных событий ввода</span><span class="sxs-lookup"><span data-stu-id="d5d9a-176">Register for fallback input events</span></span>

<span data-ttu-id="d5d9a-177">Резервные обработчики ввода похожи на зарегистрированные глобальные обработчики ввода, но обрабатываются как Последнее средство обработки входных событий.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="d5d9a-178">Только если не найдены глобальные входные обработчики и в фокусе нет объекты gameobject, будут использоваться резервные обработчики ввода.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="d5d9a-179">Пример резервного обработчика входных данных</span><span class="sxs-lookup"><span data-stu-id="d5d9a-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="d5d9a-180">Как прерывать события ввода</span><span class="sxs-lookup"><span data-stu-id="d5d9a-180">How to stop input events</span></span>

<span data-ttu-id="d5d9a-181">Каждый интерфейс входных событий предоставляет [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) объект данных в качестве параметра для каждой функции в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="d5d9a-182">Этот объект данных события дополняется собственным объектом Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .</span><span class="sxs-lookup"><span data-stu-id="d5d9a-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="d5d9a-183">Чтобы предотвратить распространение события ввода через его выполнение, [как описано](#input-events-in-action), компонент может вызвать, [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) чтобы пометить событие как используемое.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="d5d9a-184">Это приведет к отмене всех остальных объекты gameobject от получения текущего события ввода, за исключением глобальных входных обработчиков.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="d5d9a-185">Компонент, вызывающий `Use()` метод, будет прекращать объекты gameobject от его получения.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="d5d9a-186">Однако другие компоненты текущего GameObject будут по-прежнему принимать входные события и срабатывать на любые связанные функции интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d5d9a-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5d9a-187">См. также</span><span class="sxs-lookup"><span data-stu-id="d5d9a-187">See also</span></span>

- [<span data-ttu-id="d5d9a-188">Указатели</span><span class="sxs-lookup"><span data-stu-id="d5d9a-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="d5d9a-189">Речь</span><span class="sxs-lookup"><span data-stu-id="d5d9a-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="d5d9a-190">Состояние входных данных</span><span class="sxs-lookup"><span data-stu-id="d5d9a-190">Input State</span></span>](input-state.md)
