---
title: Интерактивный элемент
description: Документация по Интерактивилемент МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, интерактивный элемент, взаимодействие
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220606"
---
# <a name="interactive-element-experimental"></a>Interactive, элемент [экспериментальный]

Упрощенная централизованная точка входа в систему ввода МРТК. Содержит методы управления состоянием, управление событиями и логику настройки состояния для основных состояний взаимодействия.

Интерактивный элемент — это экспериментальная функция, которая поддерживается в Unity 2019,3 и выше, так как она использует возможности, новые для Unity 2019,3: [сериализация ссылки](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Интерактивный инспектор элементов

В режиме воспроизведения интерактивный инспектор элементов предоставляет визуальную обратную связь, которая указывает, является ли текущее состояние активным. Если состояние активно, оно будет выделено голубым цветом.  Если состояние неактивно, цвет не изменяется. Номера, расположенные рядом с состояниями в инспекторе, являются значениями состояния, если состояние активно, а значение равно 1, если состояние неактивно, то это значение равно 0.

![Интерактивный элемент с взаимодействием с виртуальной стороны](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Основные состояния

Интерактивный элемент содержит основные состояния и поддерживает добавление [пользовательских состояний](#custom-states).  Основное состояние — это ядро, которое уже имеет логику настройки состояния, определенную в `BaseInteractiveElement` . Ниже приведен список текущих состояний ядра на основе ввода: 

### <a name="current-core-states"></a>Текущие основные состояния

- [По умолчанию](#default-state) 

Основные состояния в ближайшем и дальнем взаимодействии:
- [Фокус](#focus-state) 

Основные состояния взаимодействия:

- [Фокус рядом](#focus-near-state)
- [Сенсорный ввод](#touch-state)

Основные состояния взаимодействия:
- [Сосредоточиться на далеком](#focus-far-state)
- [Выберите FAR](#select-far-state)

Другие основные состояния:
- [Выполнен переход](#clicked-state)
- [Включить и выключить](#toggle-on-and-toggle-off-state)
- [Ключевое слово речи](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Добавление основного состояния с помощью инспектора

1. В инспекторе для интерактивного элемента перейдите к разделу **Добавление основного состояния** .

    ![Добавление основного состояния с помощью инспектора](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Нажмите кнопку **выбрать состояние** , чтобы выбрать основное состояние для добавления. Состояния в меню сортируются по типу взаимодействия.

    ![Добавление основного состояния с помощью инспектора с выбранным состоянием](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Откройте свертывание конфигурации событий, чтобы просмотреть события и свойства, связанные с этим состоянием.

    ![Добавление основного состояния с помощью инспектора и конфигурации событий](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Добавление основного состояния с помощью скрипта

Используйте `AddNewState(stateName)` метод, чтобы добавить основное состояние. Чтобы получить список доступных имен основных состояний, используйте `CoreInteractionState` перечисление.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Внутренняя структура состояний 

Состояния в интерактивном элементе имеют тип `InteractionState` .  `InteractionState`Содержит следующие свойства:

- **Имя**: имя состояния.
- **Значение**: значение состояния.  Если состояние — ON, то значение состояния равно 1. Если состояние равно OFF, то значение состояния равно 0.
- **Активный**: состояние сейчас активно. Значение активного свойства равно true, если состояние равно ON, и false, если состояние — OFF. 
- **Тип взаимодействия**: тип взаимодействия состояния — это тип взаимодействия, для которого предназначено состояние. 
  - `None`: Не поддерживает ни одну форму взаимодействия с входными данными.
  - `Near`: Приближается поддержка взаимодействия. Входные данные считаются близкими к взаимодействию, когда у манипулятора руки есть прямое Контактное лицо с другим игровым объектом, т. е. в положении, что накрывающаяся рука близка к положению игрового объекта в мировом пространстве.
  - `Far`: Поддержка дальнего взаимодействия. Входные данные считаются намного взаимодействием, если прямое обращение к игровому объекту не требуется. Например, вход с помощью контроллера Ray или взгляда считается гораздо более безопасным входом.
  - `NearAndFar`: Включает поддержку практически и дальнего взаимодействия. 
  - `Other`: Независимая поддержка взаимодействия по указателям.
- **Конфигурация события**. Конфигурация события состояния — это точка входа в профиле сериализованных событий. 

Все эти свойства задаются внутренне в элементе, `State Manager` содержащемся в интерактивном элементе. Для изменения состояний используйте следующие вспомогательные методы:

**Вспомогательные методы настройки состояния**

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

Получение конфигурации события состояния зависит от самого состояния. Каждое основное состояние имеет конкретный тип конфигурации событий, который описан ниже в разделах, описывающих каждое состояние ядра.

Ниже приведен обобщенный пример получения конфигурации события состояния.

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Состояние по умолчанию

Состояние по умолчанию всегда имеется в интерактивном элементе.  Это состояние будет активным, только если все остальные состояния неактивны.  Если любое другое состояние становится активным, состояние по умолчанию будет отключено внутренним. 

Интерактивный элемент инициализируется с состояниями по умолчанию и фокусом, присутствующими в списке состояний. Состояние по умолчанию всегда должно присутствовать в списке состояний. 

#### <a name="getting-default-state-events"></a>Получение событий состояния по умолчанию

Тип конфигурации события для состояния по умолчанию: `StateEvents`

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

### <a name="focus-state"></a>Состояние фокусировки

Состояние фокусировки — это состояние почти и намного взаимодействий, которое можно рассматривать как эквивалентное наведении на смешанную реальность. Отличительным фактором между ближайшим и дальнеим взаимодействием для состояния фокуса является текущий активный тип указателя.  Если тип указателя для состояния фокуса является указателем на Вставка, то взаимодействие считается практически взаимодействием.  Если первичный указатель не является указателем на Вставка, взаимодействие считается далеко взаимодействием. По умолчанию состояние фокусировки представлено в интерактивном элементе.

 
 Поведение ![ состояния фокуса Состояние фокусировки с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

 
 Инспектор ![ состояния фокуса Состояние фокусировки в Инпсектор](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Получение событий состояния фокуса

Тип конфигурации события для состояния фокусировки: `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>Основное внимание уделяется Практическиму поведению фокуса VS 

![Сосредоточьтесь рядом с взаимодействием Virtual руки](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Фокус рядом с состоянием

Фокус находится рядом с состоянием, когда возникает событие Focus, а первичный указатель — это указатель, указывающий на приближение взаимодействия. 

**Фокус на поведение** 
 ![ близкого состояния Сосредоточьтесь рядом с состоянием и взаимодействием с виртуальной рукой](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Сфокусироваться рядом с инспектором состояний** 
 ![ Фокус на компоненте, расположенном в инспекторе](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Получение событий состояния Фокуснеар

Тип конфигурации события для состояния Фокуснеар: `FocusEvents`

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

### <a name="focus-far-state"></a>Фокус на далеком состоянии

Состояние "фокус находится далеко" устанавливается, когда основной указатель не является указателем на Вставка.  Например, указатель по умолчанию на луч и указатель на ГГВ (взгляд, жест, голоса) рассматриваются как дальнее несколько указателей взаимодействия.

**Поведение при наведении** 
 ![ фокуса на состояние Состояние фокусировки с взаимодействием Virtual руки](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

 
 Инспектор ![ состояния фокуса Фокус на далеком компоненте в инспекторе](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Получение событий состояния фокуса

Тип конфигурации события для состояния Фокусфар: `FocusEvents`

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

### <a name="touch-state"></a>Состояние касания

Сенсорный режим — это состояние близкого взаимодействия, которое задается, когда Наладонная рука обращается к объекту напрямую.  Прямое касание означает, что палец указателя руки очень близко к всему миру объекта. По умолчанию `NearInteractionTouchableVolume` компонент прикрепляется к объекту, если в список состояний добавляется сенсорный режим.  `NearInteractionTouchableVolume` `NearInteractionTouchable` Для обнаружения событий касания требуется наличие компонента или.  Разница между `NearInteractionTouchableVolume` и заключается в том `NearInteractionTouchable` , что `NearInteractionTouchableVolume` обнаруживает касание на основе конфликтующего объекта и `NearInteractionTouchable` обнаруживает касание в определенной области плоскости.

 
 Поведение ![ сенсорного состояния Сенсорный режим с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

 
 Инспектор ![ состояния касания Компонент состояния касания в инспекторе](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Получение событий состояния касания

Тип конфигурации событий для состояния касания: `TouchEvents`

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

### <a name="select-far-state"></a>Выбор дальнего состояния

Область выбор дальнего состояния является полевой `IMixedRealityPointerHandler` .  Это состояние является гораздо более взаимодействием, которое обнаруживает гораздо взаимодействие щелчком мыши (AIR-TAP) и удерживается с помощью дальнего указателя взаимодействия, такого как указатель на контроллер по умолчанию или указатель ГГВ.  В поле Выбор дальнего состояния есть параметр под заголовком конфигурация события с именем `Global` . Если `Global` имеет значение true, то `IMixedRealityPointerHandler` регистрируется как глобальный обработчик входных данных.  Фокус на объекте не требуется для активации входных системных событий, если обработчик зарегистрирован как глобальный.  Например, если пользователь хочет, чтобы во время выполнения жеста воздушного касания/выбора захотелся, независимо от объекта в фокусе, установите значение `Global` true. 

**Выбор состояния дальнего действия** 
 ![ Выберите далеко с помощью взаимодействия Virtual рука](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Выбрать инспектор** 
 ![ дальнего состояния Выбор дальнего компонента в инспекторе](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Получение событий выбора дальнего состояния

Тип конфигурации события для состояния Селектфар: `SelectFarEvents`

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

### <a name="clicked-state"></a>Выбранное состояние

Выбранное состояние активируется при дальнем взаимодействии по умолчанию (выбор дальнего состояния).  Это состояние внутренне переключается в on, вызывает событие onclickd и сразу же переключается на OFF. 

> [!NOTE]
> Визуальная обратная связь в инспекторе, основанном на действии состояния, отсутствует для состояния щелчка, так как она переключается, а затем немедленно выключается. 

 
 Поведение ![ при выборе состояния Выбранное состояние с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

 
 Инспектор ![ состояний нажатия Щелкните компонент состояния в инспекторе.](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Пример состояния "почти и далеко"**  
Выбранное состояние можно активировать с помощью дополнительных точек входа с помощью `interactiveElement.TriggerClickedState()` метода.  Например, если пользователю требуется близкое взаимодействие для активации щелчка на объекте, то он будет добавлять `TriggerClickedState()` метод в качестве прослушивателя в состоянии касания.   

![Почти и далеко с взаимодействием с виртуальными руками](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Получение событий состояния щелчков

Тип конфигурации событий для состояния щелчка: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Включение и выключение состояния

Переключатели и выключенные состояния являются парой и должны быть представлены для поведений переключения.  По умолчанию состояния переключателя и выключения запускаются с помощью дальнего щелчка (выберите дальнее состояние).  По умолчанию состояние отключения включается при запуске, что означает, что переключатель будет инициализирован в OFF.  Если пользователь хочет, чтобы состояние переключения было активным при запуске, в окне переключение в состояние установлено значение `IsSelectedOnStart` true.

**Тогглеон и отключение поведения состояния** 
 ![ Включение и отключение переключателей с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**Тогглеон и переключение инспектора состояний** 
 ![ Переключить компонент в инспекторе](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Пример состояния переключателя NEAR и Far**  
Как и в случае щелчка состояния, параметр переключения состояния может иметь несколько точек входа с помощью `interactiveElement.SetToggleStates()` метода. Например, если пользователь хочет коснуться в качестве дополнительной точки входа для задания состояния переключения, они добавляют `SetToggleStates()` метод к одному из событий в состоянии касания. 

![Переключение почти и далеко с помощью взаимодействия между виртуальными руками](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Получение или выключение событий состояния

Тип конфигурации события для состояния Тогглеон: `ToggleOnEvents`  
Тип конфигурации события для состояния Тогглеофф: `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>Состояние ключевого слова речи

Состояние ключевого слова речи прослушивает ключевые слова, определенные в профиле речи смешанной реальности. Все новые ключевые слова должны быть зарегистрированы в профиле голосовых команд до выполнения (шаги ниже). 

Поведение состояния ключевого **слова речи** 
 ![ Ключевое слово Speech с виртуальным взаимодействием](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

Инспектор состояния ключевого **слова речи** 
 ![ Компонент голосовых ключевых слов в инспекторе](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> Состояние ключевого слова речи было активировано в редакторе, нажав клавишу F5 в приведенном выше GIF. Настройка в редакторе тестирование распознавания речи описана ниже. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Как зарегистрировать голосовую команду или ключевое слово

1. Выбор игрового объекта **микседреалититулкит**

1. Выберите **Копировать и настроить** текущий профиль

1. Перейдите к разделу вход и выберите **клонировать** , чтобы разрешить изменение входного профиля.

1. Прокрутите вниз до раздела "речь" во входном профиле и клонировать профиль речи

    ![Профиль ключевых слов речи в игровом объекте МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Выберите команду "добавить новую речь"

    ![Добавление нового ключевого слова для речи в профиле МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Введите ключевое слово New. Необязательно. Измените значение KeyCode на F5 (или другой KeyCode), чтобы разрешить тестирование в редакторе. 

    ![Настройка ключевого слова речи в профиле МРТК](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Вернитесь к инспектору состояний ключевых слов интерактивного речевого элемента и выберите **Добавить ключевое слово** . 

    ![Добавление ключевого слова в компонент интерактивного элемента](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Проверка и регистрация ключевых слов](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Введите новое ключевое слово, которое было только что зарегистрировано в профиле речи

    ![Ввод ключевого слова New Speech](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Чтобы проверить состояние ключевого слова речи в редакторе, нажмите кнопку KeyCode, которая была определена на шаге 6 (F5), чтобы имитировать событие распознавания ключевого слова Speech.

#### <a name="getting-speech-keyword-state-events&quot;></a>Получение событий состояния ключевого слова речи

Тип конфигурации события для состояния Спичкэйворд: `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

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

## <a name="custom-states"></a>Пользовательские состояния

### <a name="how-to-create-a-custom-state-via-inspector"></a>Создание пользовательского состояния с помощью инспектора 

Пользовательское состояние, созданное с помощью инспектора, будет инициализировано с конфигурацией событий состояния по умолчанию. Конфигурация событий по умолчанию для пользовательского состояния имеет тип `StateEvents` и содержит события онстатеон и онстатеофф.

1. Перейдите к разделу **Создание настраиваемого состояния** в инспекторе для интерактивного элемента.
    
    ![Создание пользовательского состояния](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Введите имя нового состояния. Это имя должно быть уникальным и не может совпадать с существующими основными состояниями. 
    
    ![Ввод имени нового пользовательского состояния](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Выберите **задать имя состояния** , чтобы добавить его в список состояний.
    
    ![Добавить пользовательское состояние в список состояний](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Это пользовательское состояние инициализируется с `StateEvents` конфигурацией событий по умолчанию, которая содержит `OnStateOn` `OnStateOff` события и. Сведения о создании конфигурации настраиваемого события для нового состояния см. в статье [Создание пользовательского состояния с настраиваемой конфигурацией событий](#creating-a-custom-state-with-a-custom-event-configuration).
    
    ![Новое состояние, отображаемое в компоненте интерактивного элемента](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Создание пользовательского состояния с помощью скрипта

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Создание пользовательского состояния с настраиваемой конфигурацией событий 

Примеры файлов для пользовательского состояния с именем **Keyboard** находятся здесь: мртк\сдк\експериментал\интерактивилемент\ексамплес\скриптс\кустомстатиксампле.

В следующих шагах рассматривается существующий пример создания пользовательской конфигурации события состояния и файлов получателей.

1. Представьте имя состояния.  Это имя должно быть уникальным и не может совпадать с существующими основными состояниями. В этом примере имя состояния будет иметь значение **Клавиатура**.

1. Создайте два файла CS с именем State + "получатель" и именем состояния + "события". Имена этих файлов учитываются во внутреннем процессе и должны соответствовать соглашению о названии состояния + события/получателя. 

    ![Сценарии состояния клавиатуры](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Дополнительные сведения о содержимом файлов см. в файлах Кэйбоардевентс. cs и Кэйбоардрецеивер. cs. Новые классы конфигурации событий должны наследовать от `BaseInteractionEventConfiguration` , а новые классы приемников событий должны наследоваться от `BaseEventReceiver` .  Примеры параметров состояния для состояния клавиатуры находятся в `CustomStateSettingExample.cs` файле. 

1. Добавление состояния в интерактивный элемент с помощью имени состояния имя состояния будет распознано, если существуют файлы конфигурации событий и приемника событий.  Свойства в файле конфигурации пользовательского события должны отображаться в инспекторе.

    ![Добавление пользовательского состояния в интерактивное ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ настраиваемое состояние элемента, распознаваемое в интерактивном элементе](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Дополнительные примеры файлов конфигурации событий и приемников событий см. в файлах по следующим путям:    
- мртк\сдк\експериментал\интерактивилемент\интерактивилемент\евентс\евентконфигуратионс
- мртк\сдк\експериментал\интерактивилемент\интерактивилемент\евентс\евентрецеиверс

## <a name="example-scene"></a>Пример сцены 

Пример сцены для визуализатора интерактивного элемента и состояния расположен здесь: Мртк\сдк\експериментал\интерактивилемент\ексамплес\интерактивилементексамплесцене.Унити

![Пример сцены с интерактивным визуализатором элемента и состояния](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Сжатая кнопка

Пример сцены содержит Prefabs с именем `CompressableButton` и `CompressableButtonToggle` , эти Prefabs зеркально отражают поведение `PressableButtonHoloLens2` кнопок, созданных с помощью интерактивного элемента и визуализатора состояния. В `CompressableButton` настоящее время компонент является сочетанием `PressableButton`  +  `PressableButtonHoloLens2` с `BaseInteractiveElement` базовым классом. 

## <a name="state-visualizer-experimental"></a>Визуализатор состояния [экспериментальный]

Компонент визуализатора состояния добавляет анимацию в объект на основе состояний, определенных в связанном компоненте интерактивного элемента. Этот компонент создает ресурсы анимации, помещает их в папку Микседреалититулкит. Generated и включает упрощенную настройку опорного кадра анимации путем добавления свойств анимации к целевому объекту игры. Чтобы включить переходы анимации между состояниями, создается ресурс контроллера аниматор и создается конечный автомат по умолчанию со связанными параметрами и любыми переходами состояния.  Конечный автомат можно просмотреть в окне аниматор Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Визуализатор состояния и система анимации Unity

В настоящее время визуализатор состояния использует систему анимации Unity. 

При нажатии кнопки **создать новые фрагменты анимации** в визуализаторе состояния создаются новые материалы анимации на основе имен состояний в интерактивном элементе и помещаются в папку Микседреалититулкит. Generated. Свойство фрагмента анимации в каждом контейнере состояния устанавливается в соответствующий анимированный ролик.

![Анимированные клипы в компоненте визуализатора состояния](../images/interactive-element/StateVisualizer/AnimationClips.png)

Кроме того, для управления плавными переходами между фрагментами анимации также создается [конечный автомат аниматор](https://docs.unity3d.com/Manual/AnimationOverview.html) .  По умолчанию конечный автомат использует [любое состояние](https://docs.unity3d.com/Manual/class-State.html) , чтобы разрешить переходы между любым состоянием в интерактивном элементе. 

[Визуализаторы состояний, активируемые в аниматор](https://docs.unity3d.com/Manual/AnimationParameters.html) , также формируются для каждого состояния. параметры триггера используются в визуализаторе состояний для запуска анимации.

![Конечный автомат Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Ограничения среды выполнения 

Визуализатор состояния должен быть добавлен в объект через инспектор и не может быть добавлен с помощью скрипта.  Свойства, изменяющие Аниматорстатемачине/Аниматионконтроллер, содержатся в пространстве имен редактора ( `UnityEditor.Animations` ), которое удаляется при сборке приложения.

## <a name="how-to-use-the-state-visualizer"></a>Использование визуализатора состояния

1. Создание куба
1. Присоединить интерактивный элемент
1. Присоединить визуализатор состояний
1. Выберите **создать новые анимационные клипы**

    ![Создание новых анимированных клипов](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Отображение созданных анимированных роликов в визуализаторе и компонентах интерактивного элемента](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. В контейнере состояние фокуса выберите **добавить целевой объект** .

    ![Добавление целевого объекта визуализатора состояния](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Перетащите текущий объект Game в целевое поле 

    ![Задание целевого объекта визуализатора состояния](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Открытие свертывания свойств куба
1. Выберите раскрывающееся меню анимированное свойство и выберите **Цвет** .

    ![Настройка цвета визуализатора состояния](../images/interactive-element/StateVisualizer/SetColor.png)

1. Выберите **Добавить свойство для анимации цвета** .

    ![Выбор анимированного свойства "цвет визуализатора"](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Выбор цвета 

    ![Выбор цвета визуализатора из цветового круга](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Нажмите кнопку Воспроизведение и обратите внимание на изменение переходного цвета.

    ![Пример изменения цветового перехода с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Свойства с анимацией

Основным назначением свойств, которые можно анимировать, является упрощение настройки опорного кадра анимации.  если пользователь знаком с системой анимации Unity и предпочитает непосредственно задавать опорные кадры на созданных роликах анимации, они могут просто не добавлять анимированные свойства в целевой объект и открывать клип в окне анимации Unity (Windows > анимации > анимации). 

Если для анимации используются анимированные свойства, для типа кривой устанавливается значение Еасеинаут.

**Текущие свойства для анимации:**
- [Смещение шкалы](#scale-offset)
- [Смещение позиции](#position-offset)
- [Цвет](#color)
- [Цвет шейдера](#shader-color)
- [Построитель текстуры с плавающей запятой](#shader-float)
- [Вектор шейдера](#shader-vector)

### <a name="scale-offset"></a>Смещение шкалы

Свойство с анимацией смещения шкалы принимает текущий масштаб объекта и добавляет заданное смещение.

![Смещение шкалы с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Смещение позиции

Свойство "смещение позиции", которое используется для анимации, принимает текущую позиции объекта и добавляет заданное смещение.

![Смещение позиции с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

Свойство "анимация цвета" представляет основной цвет материала, если материал имеет свойство основного цвета. Это свойство анимирует `material._Color` свойство.

![Изменение цвета фокуса с помощью взаимодействия виртуальной руки](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Цвет шейдера

Свойство анимированного цвета шейдера ссылается на свойство шейдера типа Color. Имя свойства является обязательным для всех свойств шейдера. Приведенный ниже GIF-файл демонстрирует анимацию свойства цвета шейдера с именем Fill_Color, который не является основным цветом материала.  Изучите изменяющиеся значения в инспекторе материалов.

![Цвет тени с использованием виртуальной руки](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Построитель текстуры с плавающей запятой

Анимированное свойство Shader с плавающей запятой ссылается на свойство шейдера типа float. Имя свойства является обязательным для всех свойств шейдера. В приведенном ниже GIF-файле Обратите внимание на изменение значений в инспекторе материалов для свойства «металл». 

![Построитель текстуры с плавающей точкой с виртуальной рукой](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Вектор шейдера

Анимированное свойство вектора шейдера ссылается на свойство шейдера типа Vector4. Имя свойства является обязательным для всех свойств шейдера. В приведенном ниже GIF-файле Обратите внимание на изменение значений в инспекторе материалов для свойства мозаичного заполнения (главное Tex_ST). 

![Вектор шейдера с взаимодействием виртуальной руки](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Как найти имена свойств анимированного шейдера

1. Переход к окну > анимации > анимация
1. Убедитесь, что в иерархии выбран объект с визуализатором состояния.
1. Выбор любого клипа анимации в окне "анимация"
1. Выберите **Добавить свойство**, откройте свертывание модуля подготовки сетки. 

    ![Добавление свойства анимации в окно аниматор](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Этот список содержит имена всех свойств анимации. 

    ![Свойства анимации модуля подготовки сетки в окне аниматор](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>См. также раздел

- [**Кнопки**](../ux-building-blocks/button.md)
- [**Элемент управления Bounds**](../ux-building-blocks/bounds-control.md)
- [**Коллекция объектов Grid**](../ux-building-blocks/object-collection.md)
- [**Поиск решения Радиалвиев**](../ux-building-blocks/solvers/solver.md)
