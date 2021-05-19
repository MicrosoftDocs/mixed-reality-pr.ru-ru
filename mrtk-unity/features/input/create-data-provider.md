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
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="54ba6-104">Создание поставщика входных системных данных</span><span class="sxs-lookup"><span data-stu-id="54ba6-104">Creating an input system data provider</span></span>

<span data-ttu-id="54ba6-105">Система ввода набора средств Mixed Reality — это расширяемая система для включения поддержки устройств ввода.</span><span class="sxs-lookup"><span data-stu-id="54ba6-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="54ba6-106">Для добавления поддержки новой аппаратной платформы может потребоваться настраиваемый поставщик входных данных.</span><span class="sxs-lookup"><span data-stu-id="54ba6-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="54ba6-107">В этой статье описывается создание пользовательских поставщиков данных, также называемых диспетчерами устройств, для входной системы.</span><span class="sxs-lookup"><span data-stu-id="54ba6-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="54ba6-108">Приведенный ниже пример кода относится к [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="54ba6-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="54ba6-109">Полный код, используемый в этом примере, можно найти в папке МРТК/providers/Виндовсмикседреалити.</span><span class="sxs-lookup"><span data-stu-id="54ba6-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="54ba6-110">Пространство имен и структура папок</span><span class="sxs-lookup"><span data-stu-id="54ba6-110">Namespace and folder structure</span></span>

<span data-ttu-id="54ba6-111">Поставщики данных могут распространяться как надстройки сторонних разработчиков или как часть набора средств Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="54ba6-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="54ba6-112">Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения.</span><span class="sxs-lookup"><span data-stu-id="54ba6-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="54ba6-113">Если поставщик входных системных данных отправляется в [репозиторий смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity), пространство имен **должно** начинаться с Microsoft. микседреалити. Toolkit (например: Microsoft. Микседреалити. Toolkit. виндовсмикседреалити), а код должен находиться в папке, расположенной под разрядом "мртк/поставщики" (например, мртк/providers/виндовсмикседреалити).</span><span class="sxs-lookup"><span data-stu-id="54ba6-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="54ba6-114">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="54ba6-114">Namespace</span></span>

<span data-ttu-id="54ba6-115">Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен.</span><span class="sxs-lookup"><span data-stu-id="54ba6-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="54ba6-116">Рекомендуется, чтобы пространство имен включало следующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="54ba6-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="54ba6-117">Название организации</span><span class="sxs-lookup"><span data-stu-id="54ba6-117">Company name</span></span>
- <span data-ttu-id="54ba6-118">Область применения компонента</span><span class="sxs-lookup"><span data-stu-id="54ba6-118">Feature area</span></span>

<span data-ttu-id="54ba6-119">Например, поставщик входных данных, созданный компанией Contoso, может иметь значение contoso. Микседреалити. Toolkit. input.</span><span class="sxs-lookup"><span data-stu-id="54ba6-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="54ba6-120">Рекомендуемая структура папок</span><span class="sxs-lookup"><span data-stu-id="54ba6-120">Recommended folder structure</span></span>

<span data-ttu-id="54ba6-121">Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="54ba6-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Пример структуры папок](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="54ba6-123">Где Контосоинпут содержит реализацию поставщика данных, папка редактора содержит инспектор (и любой другой код, специфичный для редактора Unity), папка текстуры содержит изображения поддерживаемых контроллеров, а профили содержат один или несколько предварительно сделанных профилей.</span><span class="sxs-lookup"><span data-stu-id="54ba6-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="54ba6-124">Некоторые образы общих контроллеров можно найти в папке Микседреалититулкит\стандардассетс\текстурес</span><span class="sxs-lookup"><span data-stu-id="54ba6-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="54ba6-125">Реализация поставщика данных</span><span class="sxs-lookup"><span data-stu-id="54ba6-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="54ba6-126">Укажите наследование интерфейса и/или базового класса</span><span class="sxs-lookup"><span data-stu-id="54ba6-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="54ba6-127">Все поставщики входных системных данных должны реализовывать [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейс, который указывает минимальную функциональность, необходимую для входной системы.</span><span class="sxs-lookup"><span data-stu-id="54ba6-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="54ba6-128">МРТК Foundation включает класс, [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) который предоставляет реализацию по умолчанию для необходимых функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="54ba6-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="54ba6-129">Для устройств, построенных на основе класса Уинпут Unity, [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) класс можно использовать в качестве базового класса.</span><span class="sxs-lookup"><span data-stu-id="54ba6-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="54ba6-130">`BaseInputDeviceManager`Классы и `UnityJoystickManager` предоставляют необходимую `IMixedRealityInputDeviceManager` реализацию.</span><span class="sxs-lookup"><span data-stu-id="54ba6-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="54ba6-131">`IMixedRealityCapabilityCheck` используется в, `WindowsMixedRealityDeviceManager` чтобы указать, что он обеспечивает поддержку для набора входных возможностей, в частности, для наладонных руки, движений-жестов и контроллеров движения.</span><span class="sxs-lookup"><span data-stu-id="54ba6-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="54ba6-132">Применение атрибута Микседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="54ba6-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="54ba6-133">Ключевым шагом при создании входного системного поставщика данных является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу.</span><span class="sxs-lookup"><span data-stu-id="54ba6-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="54ba6-134">Этот шаг включает настройку профиля и платформ по умолчанию для поставщика при выборе во входном системном профиле.</span><span class="sxs-lookup"><span data-stu-id="54ba6-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="54ba6-135">Реализация методов Имикседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="54ba6-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="54ba6-136">После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="54ba6-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="54ba6-137">`BaseInputDeviceManager`Класс через `BaseService` класс предоставляет только пустые реализации `IMixedRealityDataProvider` методов.</span><span class="sxs-lookup"><span data-stu-id="54ba6-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="54ba6-138">Сведения об этих методах обычно относятся к конкретному поставщику данных.</span><span class="sxs-lookup"><span data-stu-id="54ba6-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="54ba6-139">Поставщик данных должен реализовать следующие методы:</span><span class="sxs-lookup"><span data-stu-id="54ba6-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="54ba6-140">Реализация логики поставщика данных</span><span class="sxs-lookup"><span data-stu-id="54ba6-140">Implement the data provider logic</span></span>

<span data-ttu-id="54ba6-141">Следующим шагом является добавление логики для управления устройствами ввода, включая все поддерживаемые контроллеры.</span><span class="sxs-lookup"><span data-stu-id="54ba6-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="54ba6-142">Реализация классов контроллеров</span><span class="sxs-lookup"><span data-stu-id="54ba6-142">Implement the controller classes</span></span>

 <span data-ttu-id="54ba6-143">В примере `WindowsMixedRealityDeviceManager` определяются и реализуются следующие классы контроллеров.</span><span class="sxs-lookup"><span data-stu-id="54ba6-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="54ba6-144">Исходный код для каждого из этих классов можно найти в папке МРТК/providers/Виндовсмикседреалити.</span><span class="sxs-lookup"><span data-stu-id="54ba6-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="54ba6-145">Виндовсмикседреалитяртикулатедханд. CS</span><span class="sxs-lookup"><span data-stu-id="54ba6-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="54ba6-146">Виндовсмикседреалитиконтроллер. CS</span><span class="sxs-lookup"><span data-stu-id="54ba6-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="54ba6-147">Виндовсмикседреалитиггвханд. CS</span><span class="sxs-lookup"><span data-stu-id="54ba6-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="54ba6-148">Не все диспетчеры устройств будут поддерживать несколько типов контроллеров.</span><span class="sxs-lookup"><span data-stu-id="54ba6-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="54ba6-149">Применение атрибута Микседреалитиконтроллер</span><span class="sxs-lookup"><span data-stu-id="54ba6-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="54ba6-150">Затем примените [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) атрибут к классу.</span><span class="sxs-lookup"><span data-stu-id="54ba6-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="54ba6-151">Этот атрибут указывает тип контроллера (например, с назначением руки), правой или левой (пример: Left или right) и необязательный образ контроллера.</span><span class="sxs-lookup"><span data-stu-id="54ba6-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="54ba6-152">Настройка сопоставлений взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-152">Configure the interaction mappings</span></span>

<span data-ttu-id="54ba6-153">Следующим шагом является определение набора сопоставлений взаимодействий, поддерживаемых контроллером.</span><span class="sxs-lookup"><span data-stu-id="54ba6-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="54ba6-154">Для устройств, которые получают данные через класс ввода Unity, [средство сопоставления контроллеров](../tools/controller-mapping-tool.md) является полезным ресурсом для подтверждения правильности сопоставлений осей и кнопок для назначения взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="54ba6-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="54ba6-155">Приведенный ниже пример является сокращенным из `GenericOpenVRController` класса, расположенного в папке мртк/providers/опенвр.</span><span class="sxs-lookup"><span data-stu-id="54ba6-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

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
><span data-ttu-id="54ba6-156">[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)Класс предоставляет символьные константы для определения входной оси Unity и кнопки.</span><span class="sxs-lookup"><span data-stu-id="54ba6-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="54ba6-157">Создавать события уведомления</span><span class="sxs-lookup"><span data-stu-id="54ba6-157">Raise notification events</span></span>

<span data-ttu-id="54ba6-158">Чтобы позволить приложениям реагировать на ввод пользователя, поставщик данных создает события уведомления, соответствующие изменениям состояния контроллера, как определено в [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) интерфейсах и.</span><span class="sxs-lookup"><span data-stu-id="54ba6-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="54ba6-159">Для элементов управления типа Digital (Button) создайте события Онинпутдовн и Онинпутуп.</span><span class="sxs-lookup"><span data-stu-id="54ba6-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

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

<span data-ttu-id="54ba6-160">Для аналоговых элементов управления (например, расположения сенсорной панели) должно быть вызвано событие Инпутчанжед.</span><span class="sxs-lookup"><span data-stu-id="54ba6-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="54ba6-161">Добавить инструментирование профилировщика Unity</span><span class="sxs-lookup"><span data-stu-id="54ba6-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="54ba6-162">В приложениях смешанной реальности важна производительность.</span><span class="sxs-lookup"><span data-stu-id="54ba6-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="54ba6-163">Каждый компонент добавляет некоторый объем издержек, при которых должны быть учетные записи приложений.</span><span class="sxs-lookup"><span data-stu-id="54ba6-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="54ba6-164">Для этого важно, чтобы все поставщики входных данных содержат инструментирование профилировщика Unity во внутреннем цикле и часто используемые пути кода.</span><span class="sxs-lookup"><span data-stu-id="54ba6-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="54ba6-165">Рекомендуется реализовать шаблон, используемый МРТК при инструментировании настраиваемых поставщиков.</span><span class="sxs-lookup"><span data-stu-id="54ba6-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

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
> <span data-ttu-id="54ba6-166">Имя, используемое для распознавания маркера профилировщика, является произвольным.</span><span class="sxs-lookup"><span data-stu-id="54ba6-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="54ba6-167">МРТК использует следующий шаблон.</span><span class="sxs-lookup"><span data-stu-id="54ba6-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="54ba6-168">"[Product] className. methodName-необязательное примечание"</span><span class="sxs-lookup"><span data-stu-id="54ba6-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="54ba6-169">Для упрощения идентификации конкретных компонентов и методов при анализе трассировок рекомендуется использовать пользовательские поставщики данных с похожим шаблоном.</span><span class="sxs-lookup"><span data-stu-id="54ba6-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="54ba6-170">Создание профиля и инспектора</span><span class="sxs-lookup"><span data-stu-id="54ba6-170">Create the profile and inspector</span></span>

<span data-ttu-id="54ba6-171">В наборе средств для смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="54ba6-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="54ba6-172">Поставщики данных с дополнительными параметрами конфигурации (например, [инпутсимулатионсервице](../input-simulation/input-simulation-service.md)) должны создать профиль и инспектор, чтобы позволить клиентам изменять поведение в соответствии с потребностями приложения.</span><span class="sxs-lookup"><span data-stu-id="54ba6-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="54ba6-173">Полный код для примера в этом разделе можно найти в МРТК. Папка Services/Инпутсимулатион.</span><span class="sxs-lookup"><span data-stu-id="54ba6-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="54ba6-174">Определение профиля</span><span class="sxs-lookup"><span data-stu-id="54ba6-174">Define the profile</span></span>

<span data-ttu-id="54ba6-175">Содержимое профиля должно отражать доступные свойства наблюдателя (например, интервал обновления).</span><span class="sxs-lookup"><span data-stu-id="54ba6-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="54ba6-176">Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, должны содержаться в профиле.</span><span class="sxs-lookup"><span data-stu-id="54ba6-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="54ba6-177">`CreateAssetMenu`Атрибут может быть применен к классу Profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню " **создать > активы > смешанной реальности набор профилей >** ".</span><span class="sxs-lookup"><span data-stu-id="54ba6-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="54ba6-178">Реализация инспектора</span><span class="sxs-lookup"><span data-stu-id="54ba6-178">Implement the inspector</span></span>

<span data-ttu-id="54ba6-179">Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля.</span><span class="sxs-lookup"><span data-stu-id="54ba6-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="54ba6-180">Каждый инспектор профилей должен расширять класс [басемикседреалититулкитконфигуратионпрофилеинспектор](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .</span><span class="sxs-lookup"><span data-stu-id="54ba6-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="54ba6-181">`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.</span><span class="sxs-lookup"><span data-stu-id="54ba6-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="54ba6-182">Создание определений сборок</span><span class="sxs-lookup"><span data-stu-id="54ba6-182">Create assembly definition(s)</span></span>

<span data-ttu-id="54ba6-183">Набор средств Mixed Reality использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="54ba6-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="54ba6-184">Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.</span><span class="sxs-lookup"><span data-stu-id="54ba6-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="54ba6-185">Используя [структуру папок](#recommended-folder-structure) в предыдущем примере, для поставщика данных контосоинпут требуется два асмдеф файла.</span><span class="sxs-lookup"><span data-stu-id="54ba6-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="54ba6-186">Первое определение сборки предназначено для поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="54ba6-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="54ba6-187">В этом примере он будет называться Контосоинпут и будет находиться в папке Контосоинпут в примере.</span><span class="sxs-lookup"><span data-stu-id="54ba6-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="54ba6-188">Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. Toolkit и других сборок, от которых он зависит.</span><span class="sxs-lookup"><span data-stu-id="54ba6-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="54ba6-189">В определении сборки Контосоинпутедитор будет указан инспектор профилей и код конкретного редактора.</span><span class="sxs-lookup"><span data-stu-id="54ba6-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="54ba6-190">Этот файл должен находиться в корневой папке кода редактора.</span><span class="sxs-lookup"><span data-stu-id="54ba6-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="54ba6-191">В этом примере файл будет находиться в папке Контосоинпут\едитор</span><span class="sxs-lookup"><span data-stu-id="54ba6-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="54ba6-192">Это определение сборки будет содержать ссылку на сборку Контосоинпут, а также:</span><span class="sxs-lookup"><span data-stu-id="54ba6-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="54ba6-193">Microsoft. Микседреалити. Toolkit</span><span class="sxs-lookup"><span data-stu-id="54ba6-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="54ba6-194">Microsoft. Микседреалити. Toolkit. Editor. Инспекторы</span><span class="sxs-lookup"><span data-stu-id="54ba6-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="54ba6-195">Microsoft. Микседреалити. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="54ba6-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="54ba6-196">Регистрация поставщика данных</span><span class="sxs-lookup"><span data-stu-id="54ba6-196">Register the data provider</span></span>

<span data-ttu-id="54ba6-197">После создания поставщик данных может быть зарегистрирован в системе ввода и использоваться в приложении.</span><span class="sxs-lookup"><span data-stu-id="54ba6-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Зарегистрированные поставщики входных системных данных](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="54ba6-199">Упаковка и распространение</span><span class="sxs-lookup"><span data-stu-id="54ba6-199">Packaging and distribution</span></span>

<span data-ttu-id="54ba6-200">Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика.</span><span class="sxs-lookup"><span data-stu-id="54ba6-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="54ba6-201">Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.</span><span class="sxs-lookup"><span data-stu-id="54ba6-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="54ba6-202">Если поставщик данных отправлен и принят как часть пакета Microsoft Mixed Reality Toolkit, группа Microsoft МРТК будет упаковывать и распространять ее в рамках предложений МРТК.</span><span class="sxs-lookup"><span data-stu-id="54ba6-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="54ba6-203">См. также</span><span class="sxs-lookup"><span data-stu-id="54ba6-203">See also</span></span>

- [<span data-ttu-id="54ba6-204">Входная система</span><span class="sxs-lookup"><span data-stu-id="54ba6-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="54ba6-205">Класс `BaseInputDeviceManager`</span><span class="sxs-lookup"><span data-stu-id="54ba6-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="54ba6-206">`IMixedRealityInputDeviceManager` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="54ba6-207">`IMixedRealityInputHandler` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="54ba6-208">`IMixedRealityInputHandler<T>` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="54ba6-209">`IMixedRealityDataProvider` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="54ba6-210">`IMixedRealityCapabilityCheck` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="54ba6-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="54ba6-211">Средство сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="54ba6-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
