---
title: Создание поставщиков входных данных
description: Документация по созданию системы ввода и поставщика данных в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144071"
---
# <a name="creating-an-input-system-data-provider"></a>Создание поставщика входных системных данных

Система ввода набора средств Mixed Reality — это расширяемая система для включения поддержки устройств ввода. Для добавления поддержки новой аппаратной платформы может потребоваться настраиваемый поставщик входных данных.

В этой статье описывается создание пользовательских поставщиков данных, также называемых диспетчерами устройств, для входной системы. Приведенный ниже пример кода относится к [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> Полный код, используемый в этом примере, можно найти в папке МРТК/providers/Виндовсмикседреалити.

## <a name="namespace-and-folder-structure"></a>Пространство имен и структура папок

Поставщики данных могут распространяться как надстройки сторонних разработчиков или как часть набора средств Microsoft Mixed Reality. Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения.

> [!Important]
> Если поставщик входных системных данных отправляется в [репозиторий смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity), пространство имен **должно** начинаться с Microsoft. микседреалити. Toolkit (например: Microsoft. Микседреалити. Toolkit. виндовсмикседреалити), а код должен находиться в папке, расположенной под разрядом "мртк/поставщики" (например, мртк/providers/виндовсмикседреалити).

### <a name="namespace"></a>Пространство имен

Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен. Рекомендуется, чтобы пространство имен включало следующие компоненты.

- Название организации
- Область применения компонента

Например, поставщик входных данных, созданный компанией Contoso, может иметь значение contoso. Микседреалити. Toolkit. input.

### <a name="recommended-folder-structure"></a>Рекомендуемая структура папок

Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.

![Пример структуры папок](../images/input/ExampleProviderFolderStructure.png)

Где Контосоинпут содержит реализацию поставщика данных, папка редактора содержит инспектор (и любой другой код, специфичный для редактора Unity), папка текстуры содержит изображения поддерживаемых контроллеров, а профили содержат один или несколько предварительно сделанных профилей.

> [!Note]
> Некоторые образы общих контроллеров можно найти в папке Микседреалититулкит\стандардассетс\текстурес

## <a name="implement-the-data-provider"></a>Реализация поставщика данных

### <a name="specify-interface-andor-base-class-inheritance"></a>Укажите наследование интерфейса и/или базового класса

Все поставщики входных системных данных должны реализовывать [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейс, который указывает минимальную функциональность, необходимую для входной системы. МРТК Foundation включает класс, [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) который предоставляет реализацию по умолчанию для необходимых функциональных возможностей. Для устройств, построенных на основе класса Уинпут Unity, [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) класс можно использовать в качестве базового класса.

> [!Note]
> `BaseInputDeviceManager`Классы и `UnityJoystickManager` предоставляют необходимую `IMixedRealityInputDeviceManager` реализацию.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` используется в, `WindowsMixedRealityDeviceManager` чтобы указать, что он обеспечивает поддержку для набора входных возможностей, в частности, для наладонных руки, движений-жестов и контроллеров движения.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Применение атрибута Микседреалитидатапровидер

Ключевым шагом при создании входного системного поставщика данных является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу. Этот шаг включает настройку профиля и платформ по умолчанию для поставщика при выборе во входном системном профиле.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Реализация методов Имикседреалитидатапровидер

После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.

> [!Note]
> `BaseInputDeviceManager`Класс через `BaseService` класс предоставляет только пустые реализации `IMixedRealityDataProvider` методов. Сведения об этих методах обычно относятся к конкретному поставщику данных.

Поставщик данных должен реализовать следующие методы:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Реализация логики поставщика данных

Следующим шагом является добавление логики для управления устройствами ввода, включая все поддерживаемые контроллеры.

### <a name="implement-the-controller-classes"></a>Реализация классов контроллеров

 В примере `WindowsMixedRealityDeviceManager` определяются и реализуются следующие классы контроллеров.

> Исходный код для каждого из этих классов можно найти в папке МРТК/providers/Виндовсмикседреалити.

- Виндовсмикседреалитяртикулатедханд. CS
- Виндовсмикседреалитиконтроллер. CS
- Виндовсмикседреалитиггвханд. CS

> [!Note]
> Не все диспетчеры устройств будут поддерживать несколько типов контроллеров.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Применение атрибута Микседреалитиконтроллер

Затем примените [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) атрибут к классу. Этот атрибут указывает тип контроллера (например, с назначением руки), правой или левой (пример: Left или right) и необязательный образ контроллера.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Настройка сопоставлений взаимодействия

Следующим шагом является определение набора сопоставлений взаимодействий, поддерживаемых контроллером. Для устройств, которые получают данные через класс ввода Unity, [средство сопоставления контроллеров](../tools/controller-mapping-tool.md) является полезным ресурсом для подтверждения правильности сопоставлений осей и кнопок для назначения взаимодействию.

Приведенный ниже пример является сокращенным из `GenericOpenVRController` класса, расположенного в папке мртк/providers/опенвр.

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)Класс предоставляет символьные константы для определения входной оси Unity и кнопки.

### <a name="raise-notification-events"></a>Создавать события уведомления

Чтобы позволить приложениям реагировать на ввод пользователя, поставщик данных создает события уведомления, соответствующие изменениям состояния контроллера, как определено в [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) интерфейсах и.

Для элементов управления типа Digital (Button) создайте события Онинпутдовн и Онинпутуп.

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

Для аналоговых элементов управления (например, расположения сенсорной панели) должно быть вызвано событие Инпутчанжед.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Добавить инструментирование профилировщика Unity

В приложениях смешанной реальности важна производительность. Каждый компонент добавляет некоторый объем издержек, при которых должны быть учетные записи приложений. Для этого важно, чтобы все поставщики входных данных содержат инструментирование профилировщика Unity во внутреннем цикле и часто используемые пути кода.

Рекомендуется реализовать шаблон, используемый МРТК при инструментировании настраиваемых поставщиков.

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> Имя, используемое для распознавания маркера профилировщика, является произвольным. МРТК использует следующий шаблон.
>
> "[Product] className. methodName-необязательное примечание"
>
> Для упрощения идентификации конкретных компонентов и методов при анализе трассировок рекомендуется использовать пользовательские поставщики данных с похожим шаблоном.

## <a name="create-the-profile-and-inspector"></a>Создание профиля и инспектора

В наборе средств для смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).

Поставщики данных с дополнительными параметрами конфигурации (например, [инпутсимулатионсервице](../input-simulation/input-simulation-service.md)) должны создать профиль и инспектор, чтобы позволить клиентам изменять поведение в соответствии с потребностями приложения.

> Полный код для примера в этом разделе можно найти в МРТК. Папка Services/Инпутсимулатион.

### <a name="define-the-profile"></a>Определение профиля

Содержимое профиля должно отражать доступные свойства наблюдателя (например, интервал обновления). Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, должны содержаться в профиле.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

`CreateAssetMenu`Атрибут может быть применен к классу Profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню " **создать > активы > смешанной реальности набор профилей >** ".

### <a name="implement-the-inspector"></a>Реализация инспектора

Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля. Каждый инспектор профилей должен расширять класс [басемикседреалититулкитконфигуратионпрофилеинспектор](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.

## <a name="create-assembly-definitions"></a>Создание определений сборок

Набор средств Mixed Reality использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.

Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.

Используя [структуру папок](#recommended-folder-structure) в предыдущем примере, для поставщика данных контосоинпут требуется два асмдеф файла.

Первое определение сборки предназначено для поставщика данных. В этом примере он будет называться Контосоинпут и будет находиться в папке Контосоинпут в примере.
Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. Toolkit и других сборок, от которых он зависит.

В определении сборки Контосоинпутедитор будет указан инспектор профилей и код конкретного редактора. Этот файл должен находиться в корневой папке кода редактора. В этом примере файл будет находиться в папке Контосоинпут\едитор Это определение сборки будет содержать ссылку на сборку Контосоинпут, а также:

- Microsoft. Микседреалити. Toolkit
- Microsoft. Микседреалити. Toolkit. Editor. Инспекторы
- Microsoft. Микседреалити. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Регистрация поставщика данных

После создания поставщик данных может быть зарегистрирован в системе ввода и использоваться в приложении.

![Зарегистрированные поставщики входных системных данных](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Упаковка и распространение

Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика. Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.

Если поставщик данных отправлен и принят как часть пакета Microsoft Mixed Reality Toolkit, группа Microsoft МРТК будет упаковывать и распространять ее в рамках предложений МРТК.

## <a name="see-also"></a>См. также

- [Входная система](overview.md)
- [Класс `BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` взаимодействия](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` взаимодействия](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` взаимодействия](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` взаимодействия](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` взаимодействия](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Средство сопоставления контроллеров](../tools/controller-mapping-tool.md)
