---
title: События ввода
description: Документация по Инпутевентс в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, события
ms.openlocfilehash: 25ac5bd4a4f5d5678a80ec362512ce7daac791a17e93944aa4832d9d09c02ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208336"
---
# <a name="input-events"></a>События ввода

В следующем списке перечислены все доступные интерфейсы входных событий, которые должны быть реализованы в пользовательском компоненте с нестандартным поведением. Эти интерфейсы будут вызываться входной системой МРТК для обработки пользовательской логики приложения на основе взаимодействия с пользовательским входом. [События ввода указателя](pointers.md#pointer-event-interfaces) обрабатываются немного иначе, чем стандартные типы событий ввода, приведенные ниже.

> [!IMPORTANT]
> По умолчанию скрипт будет получать входные события только в том случае, если это GameObject фокус на указатель или родительский элемент GameObject в фокусе.

| Обработчик | События | Description |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Источник обнаружен/потерян | Возникает при обнаружении или утере источника входных данных, например при обнаружении или потере наподобие руки. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Исходное удаление изменено | Возникает при изменениях исходного объекта. Исходная единица представляет собой общую часть источника входных данных. Конкретные удаления, например захват или указатель на шести ДОФ контроллере, можно получить с помощью `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Ввод вниз/вверх | Возникает при изменениях бинарных входных данных, таких как кнопки. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Ввод изменен | Возникает при изменениях входных данных заданного типа. **T** может принимать следующие значения: <br/> - *float* (например, возвращает Аналоговый триггер)<br/> - *Vector2* (например, Возвращает направление аналогового стика планшета) <br/> - *Vector3* (например, возвращаемое расположение отслеживания устройства) <br/> - *Кватернион* (например, возвращает ориентацию отслеживающего устройства)<br/> - [Микседреалитипосе](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (например, возвращает полностью отслеживание устройства) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Распознанное ключевое слово речи | Возникает при распознавании одного из ключевых слов, настроенных в *профиле голосовых команд*. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Диктовка<br/> Гипотеза <br/> Результат <br/> Завершить <br/> Ошибка | Вызывается системами диктовки для передачи результатов сеанса диктовки. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | События жестов в: <br/> Запуск <br/> Обновленные возможности <br/> Завершено <br/> Отменено | Вызывается при обнаружении жеста. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Жест обновлен или завершен | Возникает при обнаружении жестов, содержащих дополнительные данные заданного типа. Дополнительные сведения о возможных значениях для **T** см. в разделе [**события жестов**](gestures.md#gesture-events) . |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Обновлено соединений с руки | Генерируется с помощью манипуляторов контроллеров, когда обновляются соединения. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Сетка "руки" обновлена | Вызывается контроллерами с выявлением руки при обновлении сетки типа "рука". |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Действие запущено/завершено | Вызывает, чтобы указать начало и конец действия для входных данных, сопоставленных с действиями. |

## <a name="input-events-in-action"></a>Входные события в действии

На уровне скрипта входные события могут быть использованы путем реализации одного из интерфейсов обработчика событий, показанных в приведенной выше таблице. Когда событие ввода вызывается через взаимодействие с пользователем, происходит следующее:

1. Система ввода МРТК распознает, что произошло событие ввода.
1. Входная система МРТК запускает соответствующую функцию интерфейса входного события во все [зарегистрированные глобальные входные обработчики](#register-for-global-input-events) .
1. Для каждого активного указателя, зарегистрированного в системе ввода:
    1. Входная система определяет, на какой GameObject фокус находится текущий указатель.
    1. Входная система использует [систему событий Unity](https://docs.unity3d.com/Manual/EventSystem.html) для запуска соответствующей функции интерфейса для всех совпадающих компонентов в фокусе GameObject.
    1. Если в любой момент входное событие было [помечено как используемое](#how-to-stop-input-events), процесс завершится, а последующие объекты gameobject не получат обратные вызовы.
        - Пример. [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) при распознавании речевой команды будет выполнен поиск компонентов, реализующих интерфейс.
        - Примечание. Система событий Unity будет выполнять поиск в родительском GameObject, если ни один из компонентов, соответствующих требуемому интерфейсу, не найден в текущем GameObject.
1. Если не зарегистрированы глобальные входные обработчики и не найден GameObject с соответствующим компонентом или интерфейсом, то входная система будет вызывать каждый резервный обработчик входных данных.

> [!NOTE]
> [События ввода указателя](pointers.md#pointer-event-interfaces) обрабатываются немного иначе, чем указанные выше интерфейсы входных событий. В частности, входные события указателя обрабатываются только GameObject фокусом указателя, который активировал событие ввода, а также любыми глобальными обработчиками ввода. Обычные события ввода обрабатываются объекты gameobject в фокусе для всех активных указателей.

### <a name="input-event-interface-example"></a>Пример интерфейса входных событий

В приведенном ниже коде показано использование [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) интерфейса. Когда пользователь говорит слова «меньше» или «больше» при GameObjectе с этим `ShowHideSpeechHandler` классом, GameObject будет масштабироваться вдвое или вдвое больше.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) для входных событий требуется, чтобы требуемые ключевые слова были предварительно зарегистрированы в [профиле голосовых команд мртк](speech.md).

## <a name="register-for-global-input-events"></a>Регистрация для глобальных входных событий

Чтобы создать компонент, который прослушивает глобальные входные события, не относящийся к GameObject, компонент должен зарегистрироваться в системе ввода. После регистрации все экземпляры этого одноименного поведения будут получать события ввода и все GameObject, на данный момент находящиеся в фокусе, и другие глобальные зарегистрированные прослушиватели.

Если событие ввода было [помечено как используемое](#how-to-stop-input-events), глобальные зарегистрированные обработчики все равно будут принимать обратные вызовы. Однако ни один из объекты gameobject не получит событие.

### <a name="global-input-registration-example"></a>Пример глобальной регистрации входных данных

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

## <a name="register-for-fallback-input-events"></a>Регистрация для резервных событий ввода

Резервные обработчики ввода похожи на зарегистрированные глобальные обработчики ввода, но обрабатываются как Последнее средство обработки входных событий. Только если не найдены глобальные входные обработчики и в фокусе нет объекты gameobject, будут использоваться резервные обработчики ввода.

### <a name="fallback-input-handler-example"></a>Пример резервного обработчика входных данных

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

## <a name="how-to-stop-input-events"></a>Как прерывать события ввода

Каждый интерфейс входных событий предоставляет [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) объект данных в качестве параметра для каждой функции в интерфейсе. Этот объект данных события дополняется собственным объектом Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .

Чтобы предотвратить распространение события ввода через его выполнение, [как описано](#input-events-in-action), компонент может вызвать, [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) чтобы пометить событие как используемое. Это приведет к отмене всех остальных объекты gameobject от получения текущего события ввода, за исключением глобальных входных обработчиков.

> [!NOTE]
> Компонент, вызывающий `Use()` метод, будет прекращать объекты gameobject от его получения. Однако другие компоненты текущего GameObject будут по-прежнему принимать входные события и срабатывать на любые связанные функции интерфейса.

## <a name="see-also"></a>См. также раздел

- [Указатели](pointers.md)
- [Речь](speech.md)
- [Входное состояние](input-state.md)
