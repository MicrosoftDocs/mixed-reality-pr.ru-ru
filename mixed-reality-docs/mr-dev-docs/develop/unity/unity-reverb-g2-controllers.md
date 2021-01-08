---
title: HP reverbы G2 Controllers в Unity
description: Узнайте, как настроить и использовать новые контроллеры HP reverbы G2 в приложениях Unity Стеамвр и Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, переглагол, переглаголы G2, HP reverbы G2, Mixed Reality, разработка, контроллеры движения, ввод данных, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр
ms.openlocfilehash: 1c9d8f1279f81ea1d8020e2a3c689dae86496221
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009834"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="994f5-104">HP reverbы G2 Controllers в Unity</span><span class="sxs-lookup"><span data-stu-id="994f5-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="994f5-105">HP Motion Controllers — это новый тип контроллеров Windows Mixed Reality: все те же технологии отслеживания с слегка отличающимся набором доступных входных данных:</span><span class="sxs-lookup"><span data-stu-id="994f5-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="994f5-106">Сенсорная панель была заменена двумя кнопками: A и B для правильного контроллера, а также X и Y для левого контроллера.</span><span class="sxs-lookup"><span data-stu-id="994f5-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="994f5-107">Теперь это триггер, который публикует поток значений между 0,0 и 1,0 вместо кнопки с нажатыми и не нажимаемыми состояниями.</span><span class="sxs-lookup"><span data-stu-id="994f5-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="994f5-108">Так как новые входные данные недоступны через существующие API-интерфейсы Windows и Unity, необходим выделенный пакет **Microsoft. микседреалити. Input** УПМ.</span><span class="sxs-lookup"><span data-stu-id="994f5-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="994f5-109">**Классы в этом пакете не заменяют существующие интерфейсы API Windows и Unity, но дополняют их.**</span><span class="sxs-lookup"><span data-stu-id="994f5-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="994f5-110">Функции, которые обычно доступны как классическим контроллерам Windows Mixed Reality, так и HP Motion Controller, доступны через один и тот же путь кода с помощью существующих API.</span><span class="sxs-lookup"><span data-stu-id="994f5-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="994f5-111">Только новые входные данные должны использовать дополнительный пакет Microsoft. Микседреалити. input.</span><span class="sxs-lookup"><span data-stu-id="994f5-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="994f5-112">Обзор контроллера движения HP</span><span class="sxs-lookup"><span data-stu-id="994f5-112">HP Motion Controller overview</span></span>

<span data-ttu-id="994f5-113">*Microsoft. микседреалити. input. мотионконтроллер* представляет контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="994f5-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="994f5-114">Каждый экземпляр *мотионконтроллер* имеет *XR. Головк. Узел input. Интерактионсаурце* , который можно связать с помощью правой или левой, идентификатора поставщика, идентификатора продукта и версии.</span><span class="sxs-lookup"><span data-stu-id="994f5-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="994f5-115">Экземпляры Мотионконтроллер можно захватить, создав *мотионконтроллерватчер* и подписавшись на его события, аналогично использованию событий *интерактионманажер* для обнаружения новых экземпляров *интерактионсаурце* .</span><span class="sxs-lookup"><span data-stu-id="994f5-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="994f5-116">Методы и свойства Мотионконтроллер описывают входные данные, поддерживаемые контроллером, включая его кнопки, триггеры, двухмерную ось и аналоговый стик.</span><span class="sxs-lookup"><span data-stu-id="994f5-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="994f5-117">Класс Мотионконтроллер также предоставляет методы для доступа к входным состояниям через класс *мотионконтроллерреадинг* .</span><span class="sxs-lookup"><span data-stu-id="994f5-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="994f5-118">Класс Мотионконтроллерреадинг представляет моментальный снимок состояния контроллера в заданный момент времени.</span><span class="sxs-lookup"><span data-stu-id="994f5-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="994f5-119">Установка Microsoft. Микседреалити. input с помощью диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="994f5-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="994f5-120">Диспетчер пакетов Unity использует [файл манифеста](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.jsв) для определения устанавливаемых пакетов и реестров (серверов), из которых они могут быть установлены.</span><span class="sxs-lookup"><span data-stu-id="994f5-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="994f5-121">Прежде чем можно будет использовать пакет Microsoft. Микседреалити. input, необходимо зарегистрировать сервер компонентов смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="994f5-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="994f5-122">Регистрация сервера компонентов смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="994f5-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="994f5-123">Для каждого проекта, который будет использовать входной пакет Mixed Reality, для manifest.jsфайла (в папке пакеты) требуется добавленный реестр с областью действия Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="994f5-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="994f5-124">Чтобы правильно изменить manifest.jsдля поддержки смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="994f5-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="994f5-125">Откройте <projectRoot> /паккажес/manifest.jsв текстовом редакторе, например Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="994f5-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="994f5-126">В верхней части файла манифеста добавьте сервер Mixed Reality в раздел реестра с заданной областью и сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="994f5-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="994f5-127">Добавление пакета Microsoft. Микседреалити. input</span><span class="sxs-lookup"><span data-stu-id="994f5-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="994f5-128">Измените раздел Dependencies в <projectRoot> /паккажес/manifest.json File в текстовом редакторе, чтобы добавить пакет com. Microsoft. микседреалити. input, и сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="994f5-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="994f5-129">Использование Microsoft. Микседреалити. input</span><span class="sxs-lookup"><span data-stu-id="994f5-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="994f5-130">Входные значения</span><span class="sxs-lookup"><span data-stu-id="994f5-130">Input values</span></span>

<span data-ttu-id="994f5-131">Мотионконтроллер может предоставлять два вида входных данных:</span><span class="sxs-lookup"><span data-stu-id="994f5-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="994f5-132">Кнопки и состояния триггера выражаются уникальным значением float от 0,0 до 1,0, которое указывает, сколько их нажато.</span><span class="sxs-lookup"><span data-stu-id="994f5-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="994f5-133">Кнопка может возвращать 0,0 (если не нажата) или 1,0 (при нажатии), в то время как триггер может возвращать непрерывные значения между 0,0 (полностью освобожденными) и 1,0 (полностью нажатым).</span><span class="sxs-lookup"><span data-stu-id="994f5-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="994f5-134">Состояние аналогового стика выражается Vector2, чьи компоненты X и Y находятся в диапазоне от-1,0 до 1,0.</span><span class="sxs-lookup"><span data-stu-id="994f5-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="994f5-135">*Мотионконтроллер. жетпрессаблеинпутс ()* можно использовать для получения списка входных данных, возвращающих нажатое значение (кнопки и триггеры) или метода *мотионконтроллер. жетксинпутс ()* для возврата списка входных данных, возвращающих значение из двух осей.</span><span class="sxs-lookup"><span data-stu-id="994f5-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="994f5-136">Экземпляр Мотионконтроллерреадинг представляет состояние контроллера в определенный момент времени:</span><span class="sxs-lookup"><span data-stu-id="994f5-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="994f5-137">*Жетпресседвалуе ()* получает состояние кнопки или триггера.</span><span class="sxs-lookup"><span data-stu-id="994f5-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="994f5-138">*Жетксивалуе ()* получает состояние аналогового стика.</span><span class="sxs-lookup"><span data-stu-id="994f5-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="994f5-139">Создание кэша для обслуживания коллекции экземпляров Мотионконтроллер и их состояний</span><span class="sxs-lookup"><span data-stu-id="994f5-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="994f5-140">Начните с создания экземпляра Мотионконтроллерватчер и регистрации обработчиков для своих событий *мотионконтроллераддед* и *мотионконтроллерремовед* , чтобы удержать кэш доступных экземпляров мотионконтроллер.</span><span class="sxs-lookup"><span data-stu-id="994f5-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="994f5-141">Этот кэш должен быть неограниченным поведением, присоединенным к GameObject, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="994f5-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="994f5-142">Чтение новых входных данных путем опроса</span><span class="sxs-lookup"><span data-stu-id="994f5-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="994f5-143">Текущее состояние каждого из известных контроллеров можно прочитать с помощью *мотионконтроллер. трижетреадингаттиме* в методе *Update* класса «одновременный режим».</span><span class="sxs-lookup"><span data-stu-id="994f5-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="994f5-144">Необходимо передать *DateTime. Now* в качестве параметра timestamp, чтобы обеспечить чтение последнего состояния контроллера.</span><span class="sxs-lookup"><span data-stu-id="994f5-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="994f5-145">Вы можете захватить текущее входное значение контроллеров с помощью правой или левой контроллера:</span><span class="sxs-lookup"><span data-stu-id="994f5-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="994f5-146">Например, для чтения аналогового значения Интерактионсаурце:</span><span class="sxs-lookup"><span data-stu-id="994f5-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="994f5-147">Создание событий на основе новых входных данных</span><span class="sxs-lookup"><span data-stu-id="994f5-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="994f5-148">Вместо того чтобы опрашивать состояние контроллера по одному разу для каждого кадра, вы можете обрабатывать все изменения состояния как события, что позволяет выполнять даже самые быстрые действия, продолжающиеся меньше, чем кадр.</span><span class="sxs-lookup"><span data-stu-id="994f5-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="994f5-149">Чтобы этот подход работал, в кэше контроллеров движения необходимо обработать все состояния, опубликованные контроллером с момента последнего кадра, что можно сделать, сохранив метку времени последнего Мотионконтроллерреадинг, полученного из Мотионконтроллер, и вызвав *мотионконтроллер. трижетреадингафтертиме ()*:</span><span class="sxs-lookup"><span data-stu-id="994f5-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="994f5-150">Теперь, когда вы обновили внутренние классы кэша, класс однорежимного поведения может предоставлять два события — нажатые и освобожденные — и порождать их из метода Update ():</span><span class="sxs-lookup"><span data-stu-id="994f5-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="994f5-151">Структура в приведенном выше примере кода делает регистрацию событий более удобочитаемой:</span><span class="sxs-lookup"><span data-stu-id="994f5-151">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="994f5-152">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="994f5-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->