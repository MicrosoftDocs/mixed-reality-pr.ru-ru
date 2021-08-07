---
title: HP Reverb G2 — контроллеры в Unity
description: узнайте, как настроить и использовать новые контроллеры HP reverb G2 в стеамвр и Windows Mixed Reality приложениях Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, переглагол, переглаголы G2, HP reverbы G2, Mixed Reality, разработка, контроллеры движения, ввод данных, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр
ms.openlocfilehash: 4e561cb1e46fe487f1b25ed526f0adeafc2de6c525835ffe3b1871d7516b233e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215628"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>HP Reverb G2 — контроллеры в Unity

HP Motion controllers — это новый тип контроллеров Windows Mixed Reality: все технологии отслеживания с слегка отличающимся набором доступных входных данных: 

* Сенсорная панель была заменена двумя кнопками: A и B для правильного контроллера, а также X и Y для левого контроллера. 
* Теперь это триггер, который публикует поток значений между 0,0 и 1,0 вместо кнопки с нажатыми и не нажимаемыми состояниями. 

так как новые входные данные недоступны через существующие интерфейсы api Windows и Unity, необходим выделенный пакет **Microsoft. микседреалити. Input** упм. 

> [!IMPORTANT]
> **классы в этом пакете не заменяют существующие интерфейсы api Windows и Unity, но дополняют их.** функции, которые обычно доступны как классическим контроллерам Windows Mixed Reality, так и HP Motion controller, доступны через один и тот же путь кода с помощью существующих api. Только новые входные данные должны использовать дополнительный пакет Microsoft. Микседреалити. input. 

## <a name="hp-motion-controller-overview"></a>Обзор контроллера движения HP

*Microsoft. микседреалити. input. мотионконтроллер* представляет контроллер движения. Каждый экземпляр *мотионконтроллер* имеет *XR. Головк. Узел input. Интерактионсаурце* , который можно связать с помощью правой или левой, идентификатора поставщика, идентификатора продукта и версии. 

Экземпляры Мотионконтроллер можно захватить, создав *мотионконтроллерватчер* и подписавшись на его события, аналогично использованию событий *интерактионманажер* для обнаружения новых экземпляров *интерактионсаурце* . Методы и свойства Мотионконтроллер описывают входные данные, поддерживаемые контроллером, включая его кнопки, триггеры, двухмерную ось и аналоговый стик. Класс Мотионконтроллер также предоставляет методы для доступа к входным состояниям через класс *мотионконтроллерреадинг* . Класс Мотионконтроллерреадинг представляет моментальный снимок состояния контроллера в заданный момент времени. 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a>Установка Microsoft. Микседреалити. input с помощью инструмента "функция смешанной реальности"

Установите подключаемый модуль Microsoft. Микседреалити. input, используя новое приложение средства "функция смешанной реальности". следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите **входной пакет mixed reality** в категории набор средств смешанной реальности:

![Окно пакетов инструмента "функция смешанной реальности" с выделенным входом смешанной реальности](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a>Использование Microsoft. Микседреалити. input 

### <a name="input-values"></a>Входные значения

Мотионконтроллер может предоставлять два вида входных данных: 

* Кнопки и состояния триггера выражаются уникальным значением float от 0,0 до 1,0, которое указывает, сколько их нажато.
    * Кнопка может возвращать 0,0 (если не нажата) или 1,0 (при нажатии), в то время как триггер может возвращать непрерывные значения между 0,0 (полностью освобожденными) и 1,0 (полностью нажатым). 
* Состояние аналогового стика выражается Vector2, чьи компоненты X и Y находятся в диапазоне от-1,0 до 1,0. 

*Мотионконтроллер. жетпрессаблеинпутс ()* можно использовать для получения списка входных данных, возвращающих нажатое значение (кнопки и триггеры) или метода *мотионконтроллер. жетксинпутс ()* для возврата списка входных данных, возвращающих значение из двух осей. 

Экземпляр Мотионконтроллерреадинг представляет состояние контроллера в определенный момент времени: 

* *Жетпресседвалуе ()* получает состояние кнопки или триггера. 
* *Жетксивалуе ()* получает состояние аналогового стика. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Создание кэша для обслуживания коллекции экземпляров Мотионконтроллер и их состояний 

Начните с создания экземпляра Мотионконтроллерватчер и регистрации обработчиков для своих событий *мотионконтроллераддед* и *мотионконтроллерремовед* , чтобы удержать кэш доступных экземпляров мотионконтроллер. Этот кэш должен быть неограниченным поведением, присоединенным к GameObject, как показано в следующем коде:

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>Чтение новых входных данных путем опроса 

Текущее состояние каждого из известных контроллеров можно прочитать с помощью *мотионконтроллер. трижетреадингаттиме* в методе *Update* класса «одновременный режим». Необходимо передать *DateTime. Now* в качестве параметра timestamp, чтобы обеспечить чтение последнего состояния контроллера. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Вы можете захватить текущее входное значение контроллеров с помощью правой или левой контроллера: 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

Например, для чтения аналогового значения Интерактионсаурце: 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>Создание событий на основе новых входных данных 

Вместо того чтобы опрашивать состояние контроллера по одному разу для каждого кадра, вы можете обрабатывать все изменения состояния как события, что позволяет выполнять даже самые быстрые действия, продолжающиеся меньше, чем кадр. Чтобы этот подход работал, в кэше контроллеров движения необходимо обработать все состояния, опубликованные контроллером с момента последнего кадра, что можно сделать, сохранив метку времени последнего Мотионконтроллерреадинг, полученного из Мотионконтроллер, и вызвав *мотионконтроллер. трижетреадингафтертиме ()*: 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

Теперь, когда вы обновили внутренние классы кэша, класс однорежимного поведения может предоставлять два события — нажатые и освобожденные — и порождать их из метода Update (): 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Структура в приведенном выше примере кода делает регистрацию событий более удобочитаемой: 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>См. также раздел

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->