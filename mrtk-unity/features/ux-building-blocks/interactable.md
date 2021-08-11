---
title: Интерактивный объект
description: Общие сведения об интерактивном компоненте скрипта в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, взаимодействие, события,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206814"
---
# <a name="interactable"></a>Интерактивный объект

![Интерактивный объект](../images/interactable/InteractableExamples.png)

[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)Компонент является контейнером "все в одном", чтобы любой объект мог легко *взаимодействовать* и реагировать на входные данные. Взаимодействие действует как перехватывать все типы входных данных, включая сенсорный ввод, лучи, речь и т. д., и передают эти взаимодействия в [события](#events) и ответы на [визуальные темы](visual-themes.md) . Этот компонент предоставляет простой способ создания кнопок, изменения цвета объектов с фокусом и т. д.

## <a name="how-to-configure-interactable"></a>Настройка взаимодействующих

Компонент позволяет создавать три основных раздела конфигурации:

1) [Общая конфигурация ввода](#general-input-settings)
1) [Визуальные темы](visual-themes.md) , предназначенные для нескольких объекты gameobject
1) [Обработчики событий](#events)

### <a name="general-input-settings"></a>Общие параметры ввода

![общие взаимодействующие Параметры](../images/interactable/InputFeatures_short.png)

**Состояния**

*Состояния* — это параметр [скриптаблеобжект](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , определяющий этапы взаимодействия, такие как нажатие или наблюдающие, для [взаимодействующих профилей](#interactable-profiles) и [визуальных тем](visual-themes.md).

**Дефаултинтерактаблестатес** (Assets/МРТК/SDK/Features/UX/взаимодействующие/штатыs/дефаултинтерактаблестатес. Asset) поставляется вместе с мртк и является параметром по умолчанию для *взаимодействующих* компонентов.

![Пример состояния Скриптаблеобжект в инспекторе](../images/interactable/DefaultInteractableStates.png)

Ресурс *дефаултинтерактаблестатес* содержит четыре состояния и использует [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) реализацию модели состояний.

* **По умолчанию**: ничего не происходит, это наиболее изолированное базовое состояние.

* **Фокус**: объект указывает на. Это одно состояние, другие состояния в настоящее время не заданы, но значение по умолчанию будет рангом.

* **Нажмите клавишу**: объект указывает на, а кнопка или руки нажата. По умолчанию и фокус выжимает состояние. Это состояние также будет установлено в качестве резервного для физического нажатия.

* **Отключено**. кнопка не должна быть интерактивной, и визуальная обратная связь позволит пользователю узнать, по какой причине эта кнопка не используется в данный момент. Теоретически отключенное состояние может содержать все остальные состояния, но если включен, отключенное состояние замещает все остальные состояния.

Значение бита (#) присваивается состоянию в зависимости от порядка в списке.

> [!NOTE]
> При создании *взаимодействующих* компонентов, как правило, рекомендуется использовать **дефаултинтерактаблестатес** (Assets/Мртк/SDK/Features/UX/взаимодействовать/States/дефаултинтерактаблестатес. Asset).
>
> Однако доступно 17 взаимодействующих состояний, которые можно использовать для работы с темами, хотя некоторые из них предназначены для других компонентов. Ниже приведен список встроенных функций.
>
> * Посещено: выбрано взаимодействие.
> * Переключено: кнопка находится в переключенном состоянии или индексе измерения нечетное число.
> * Жест: была нажата рука или контроллер и перемещена из исходной должности.
> * Воицекомманд: для активации взаимодействия используется Голосовая команда.
> * Фисикалтауч: в настоящее время обнаружен сенсорный ввод, используется [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) для включения.
> * Захват: Сейчас в границах объекта передается рука, используется [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) для включения

**Включен**

Указывает, включен ли режим взаимодействия. Это соответствует [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) в коде.

Свойство, доступное *для взаимодействия* , отличается от свойства Enabled, настроенного через GameObject/Component (т. е. Сетактиве и т. д.). Отключение GameObject или *интерактивного* режима работы приведет к отключению всех элементов класса от выполнения, включая входные данные, визуальные темы, события и т. д. Отключение через [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) приведет к отключению максимальной обработки ввода, сбросу связанных состояний ввода. Однако класс по-прежнему будет выполнять все кадры и получать события ввода, которые будут игнорироваться. Это полезно для отображения взаимодействия в отключенном состоянии, которое можно выполнить с помощью визуальных тем. Типичным примером этого является Кнопка Submit, ожидающая завершения всех обязательных полей ввода.

**Входные действия**

Выберите [Входное действие](../input/input-actions.md) из профиля входной конфигурации или сопоставления контроллера, к которому должен реагировать *взаимодействующий* компонент.

Это свойство может быть настроено во время выполнения в коде через [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

Если значение — true, компонент будет помечен как глобальный входной прослушиватель для выбранного [действия ввода](../input/input-actions.md). Поведение по умолчанию — false, которое ограничивает входные данные только этим *взаимодействующим* конфликтующим или GameObject.

Это свойство может быть настроено во время выполнения в коде через [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Голосовая команда**

[Голосовая команда](../input/speech.md), из профиля команд распознавания речи мртк, чтобы активировать событие OnClick для голосового взаимодействия.

Это свойство может быть настроено во время выполнения в коде через [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Требуется фокус**

Если значение — true, команда Voice активирует только *взаимодействующий* только в том случае, если она уже имеет фокус от указателя. Если значение равно false, то *взаимодействие* будет действовать как глобальный прослушиватель для выбранной команды Voice. Поведение по умолчанию — true, так как несколько глобальных прослушивателей речи могут быть трудно организованы в сцене.

Это свойство может быть настроено во время выполнения в коде через [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Режим выбора**

Это свойство определяет логику выбора. Когда вы щелкнули *взаимодействие* , он перебирается в следующий уровень *измерения* . *Измерения* похожи на ранжирование и определяют состояние за пределами входных данных (т. е. фокус, нажмите и т. д.). Они полезны для определения состояния переключения или других многоранговых состояний, связанных с кнопкой. Текущий уровень измерения отдается по `Interactable.DimensionIndex` .

Доступны следующие режимы выбора:

* **Кнопка "**  -  *Измерения* = 1, простой *Интерактивный* щелчок
* **Переключатель**  -  *Измерения* = 2, *взаимодействующие* альтернативы *в* / *отключенном* состоянии
* Многомерное **измерение**  -  *Измерения* >= 3, каждый щелчок увеличивает текущий уровень измерения + 1. Полезно для определения состояния кнопки в списке и т. д.

Возможность *взаимодействия* позволяет определить несколько тем для каждого *измерения*. Например, если параметр *SelectionMode = Toggle*, то можно применить одну тему, когда будет отменена возможность *взаимодействия* *и была* применена другая тема при *выборе* компонента.

Текущий режим выбора можно запросить во время выполнения с помощью [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . Обновление режима во время выполнения может быть достигнуто путем задания  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) свойства в соответствии с требуемой функциональностью. Кроме того, доступ к текущему измерению, полезному для *переключения* и режимов с *несколькими измерениями* , можно получить с помощью [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Взаимодействующие профили

*Профили* — это элементы, которые создают связь между GameObject и [визуальной темой](visual-themes.md). Профиль определяет, какое содержимое будет управляться темой при [изменении состояния](#general-input-settings).

Темы работают очень похоже на материалы. Они являются объектами, поддерживающими скрипты, которые содержат список свойств, которые будут назначены объекту на основе текущего состояния. Темы также можно повторно использовать и назначать в нескольких *взаимодействующих* объектах UX.

**Сброс при уничтожении**

Визуальные темы изменяют различные свойства целевого GameObject, зависящие от класса и типа выбранного обработчика тем. Если параметр *Reset в результате уничтожения* имеет значение true при уничтожении взаимодействующего компонента, компонент сбрасывает все измененные свойства из активных тем в исходные значения. В противном случае при удалении взаимодействующего компонента все измененные свойства будут оставлены как есть. В этом последнем случае Последнее состояние значений будет сохранено, если только не изменится другим внешним компонентом. Значение по умолчанию – false.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>События

Каждый *взаимодействующий* компонент имеет событие *OnClick* , которое срабатывает при простом выборе компонента. Однако *взаимодействие* можно использовать для обнаружения событий ввода, отличных от простого *щелчка*.

Нажмите кнопку *Добавить событие* , чтобы добавить новый тип определения приемника событий. После добавления выберите нужный тип события.

![Пример событий](../images/interactable/Events.png))

Существуют различные типы приемников событий для реагирования на различные типы входных данных. МРТК поставляется со следующим набором получателей.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Пользовательский приемник можно создать, сделав новый класс, который расширяет [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Пример приемника событий для переключателя](../images/interactable/Event_toggle.png)

*Пример приемника событий переключателя*

### <a name="interactable-receivers"></a>Взаимодействующие получатели

 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)Компонент позволяет определять события за пределами исходного *взаимодействующего* компонента. *Интерактаблерецеивер* будет прослушивать тип отфильтрованного события, запущенного другим *взаимодействующим*. Если *взаимодействующее* свойство не назначено напрямую, свойство *области поиска* определяет направление, в котором *интерактаблерецеивер* прослушивает события, которые находятся либо в самом родительском объекте, либо в дочернем GameObject.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) действует так же, как и список соответствующих событий.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Создание пользовательских событий

Как и в случае с [визуальными темами](visual-themes.md#custom-theme-engines), события могут быть расширены для обнаружения любого шаблона состояния или для предоставления функциональных возможностей.

Пользовательские события могут создаваться двумя основными способами.

1) Расширьте [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) класс, чтобы создать пользовательское событие, которое будет отображаться в раскрывающемся списке типов событий. Событие Unity предоставляется по умолчанию, но можно добавлять дополнительные события Unity, а также можно задать событие, чтобы скрыть события Unity. Эта функция позволяет конструктору работать с инженером в проекте для создания пользовательского события, которое конструктор может настроить в редакторе.

1) Расширьте [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) класс, чтобы создать полностью настраиваемый компонент событий, который может располагаться в *взаимодействующем* или другом объекте. [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)Будет ссылаться на *взаимодействие* для обнаружения изменений состояния.

#### <a name="example-of-extending-receiverbase"></a>Пример расширения `ReceiverBase`

[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)Класс отображает сведения о состоянии *взаимодействия* и представляет собой пример создания пользовательского приемника событий.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Следующие методы полезны для переопределения или реализации при создании пользовательского приемника событий. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) — Это абстрактный метод, который можно использовать для обнаружения шаблонов состояний и переходов. Кроме того, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) методы и полезны для создания пользовательской логики событий при выборе *взаимодействия* .

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Отображение настраиваемых полей приемника событий в инспекторе

Сценарии *рецеивербасе* используют [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) атрибуты для предоставления пользовательских свойств в инспекторе. Ниже приведен пример Vector3, настраиваемого свойства с информацией о подсказке и метке. Это свойство будет отображаться как настраиваемое в инспекторе, если выбрано *взаимодействующее* GameObject и добавлен связанный тип *приемника событий* .

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Использование взаимодействующих

### <a name="building-a-simple-button"></a>Создание простой кнопки

Можно создать простую кнопку, добавив *взаимодействующий* компонент в GameObject, настроенный для получения входных событий. Для получения входных данных у него может быть или потомок. Если вы используете *взаимодействие* с объекты gameobject на основе пользовательского интерфейса Unity, он должен находиться под GameObject Canvas.

Переведите кнопку на один шаг дальше, создав новый профиль, назначив сам GameObject и создав новую тему. Более того, используйте событие *OnClick* , чтобы сделать что-то произошло.

> [!NOTE]
> Для нажатия [кнопки](button.md) требуется [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) компонент. Кроме того, [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) компонент необходим для того, чтобы перенажимать события в *взаимодействующий* компонент.

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Создание переключателей и кнопок с несколькими измерениями

#### <a name="toggle-button"></a>Выключатель

Чтобы включить переключатель, измените [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) поле на тип `Toggle` . В разделе *Профили* добавляется новая переключаемая тема для каждого профиля, используемого при переключении на *взаимодействие* .

Хотя [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) для задано значение переключателя, флажок «с *переключателем* » можно использовать для установки значения по умолчанию элемента управления во время инициализации среды выполнения.

*Канселект* означает, что возможность *взаимодействия* может быть *отключена* *, а* *кандеселект* — обратным.

![Пример с переключением визуальных тем для профиля](../images/interactable/Profile_toggle.png)

Разработчики могут использовать [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) интерфейсы и [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) для получения или установки состояния переключения, *взаимодействующего* через код.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Переключить коллекцию кнопок

Обычно имеется список выключателей, где только один из них может быть активным в любой момент времени, также известный как радиальный набор или переключатели и т. д.

Используйте [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) компонент, чтобы включить эту функцию. Этот элемент управления гарантирует, что в любой момент времени переключается только одна *взаимодействующая* . « *Радиальный* » (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/радиальный. prefab) также является великолепной отправной точкой.

Чтобы создать пользовательскую радиальную группу кнопок, сделайте следующее:

1) Создание нескольких *взаимодействующих* объекты gameobject/кнопок
1) Задайте каждый *взаимодействующий* с *SelectionMode* = Toggle, *канселект* = true и *кандеселект* = false.
1) Создание пустой родительской GameObject для всех *интерактаблес* и Добавление компонента *интерактаблетогглеколлектион*
1) Добавить все *интерактаблес* в *тогглелист* на *интерактаблетогглеколлектион*
1) Задайте свойство *интерактаблетогглеколлектион. куррентиндекс* , чтобы определить, какая кнопка выбрана по умолчанию при запуске.

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Многомерная кнопка

Режим выбора с несколькими измерениями используется для создания последовательных кнопок или для кнопки, которая содержит более двух шагов, например для управления скоростью с тремя значениями: быстрый (1x), быстрый (2x) или самый быстрый (3 раза).

Если измерение является числовым значением, можно добавить до 9 тем, чтобы управлять текстовой меткой или текстурой кнопки для каждого параметра скорости, используя разные темы для каждого шага.

Каждое событие нажатия переходит на `DimensionIndex` 1 во время выполнения, пока `Dimensions` не будет достигнуто значение. Затем цикл сбрасывается в 0.

![Пример многомерного профиля](../images/interactable/Profile_multiDimensions.png)

Разработчики могут оценить, [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) чтобы определить, какое измерение в настоящее время активно.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Создание взаимодействующих во время выполнения

*Взаимодействие* можно легко добавить в любой GameObject во время выполнения. В следующем примере показано, как назначить профиль с помощью [визуальной темы](visual-themes.md).

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

### <a name="interactable-events-via-code"></a>Взаимодействующие события с помощью кода

Один из них может добавить действие к базовому [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) событию с помощью кода в следующем примере.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Используйте [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) функцию, чтобы динамически добавлять приемники событий во время выполнения.

В приведенном ниже примере кода показано, как добавить [интерактаблеонфокусрецеивер](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), который прослушивает фокус ввода/вывода, а также определяет код действия, выполняемого при срабатывании экземпляров событий.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

В приведенном ниже примере кода показано, как добавить [интерактаблеонтогглерецеивер](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), который прослушивает выбранные/снятые переходы состояния при переключении *интерактаблес*, а также определяет код действия, выполняемый при срабатывании экземпляров событий.

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

## <a name="see-also"></a>См. также раздел

* [Визуальные темы](visual-themes.md)
* [Входные действия](../input/input-actions.md)
* [Речевые команды](../input/speech.md)
* [Кнопки](button.md)
* [Стандартный шейдер МРТК](../rendering/MRTK-standard-shader.md)
