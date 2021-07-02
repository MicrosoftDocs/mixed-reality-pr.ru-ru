---
title: Визуальные темы
description: Обзор визуальных тем. гибкое управление ресурсами UX в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, мртк темы
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177170"
---
# <a name="visual-themes"></a><span data-ttu-id="4a9fe-104">Визуальные темы</span><span class="sxs-lookup"><span data-stu-id="4a9fe-104">Visual themes</span></span>

<span data-ttu-id="4a9fe-105">Темы позволяют гибко управлять ресурсами UX в ответ на различные переходы состояний.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="4a9fe-106">Это может привести к изменению цвета кнопки, изменению размера элемента в ответ на фокус и т. д. Платформа визуальных тем состоит из двух основных частей: 1) конфигурации и 2) ядер среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="4a9fe-107">[Конфигурации тем](#theme-configuration) являются определениями свойств и типов, тогда как [обработчики тем](#theme-engines) являются классами, использующими конфигурации, и реализуют логику для обновления преобразований, материалов и других возможностей во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="4a9fe-108">Конфигурация темы</span><span class="sxs-lookup"><span data-stu-id="4a9fe-108">Theme configuration</span></span>

<span data-ttu-id="4a9fe-109">Конфигурации темы — это [скриптаблеобжектс](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , которые определяют, как обработчики тем будут инициализироваться во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="4a9fe-110">Они определяют, какие свойства и значения следует использовать в ответ на ввод или другие изменения состояния при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="4a9fe-111">Как [скриптаблеобжектс](https://docs.unity3d.com/Manual/class-ScriptableObject.html) активы, конфигурации тем можно определить один раз, а затем повторно использовать в разных компонентах UX.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="4a9fe-112">Чтобы создать новый [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ресурс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="4a9fe-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="4a9fe-113">щелчок правой кнопкой мыши в *окне Project*</span><span class="sxs-lookup"><span data-stu-id="4a9fe-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="4a9fe-114">выберите **создание**  >  **темы набор средств смешанной реальности**  >  </span><span class="sxs-lookup"><span data-stu-id="4a9fe-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="4a9fe-115">Примеры ресурсов конфигурации темы можно найти в разделе `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="4a9fe-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Пример Скриптаблеобжект темы в инспекторе](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="4a9fe-117">Состояния</span><span class="sxs-lookup"><span data-stu-id="4a9fe-117">States</span></span>

<span data-ttu-id="4a9fe-118">При создании нового [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) необходимо установить, какие состояния доступны.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="4a9fe-119">Свойство *statess* указывает, сколько значений должна определяться конфигурацией темы, так как для каждого состояния будет одно значение.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="4a9fe-120">В приведенном выше примере показано состояние по умолчанию, [заданное для взаимодействующего](interactable.md#general-input-settings) компонента: *по умолчанию*, *фокус*, *Нажатие* и *Отключение*.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="4a9fe-121">Они определены в файле ресурсов `DefaultInteractableStates` (Asset/мртк/SDK/Features/UX/States).</span><span class="sxs-lookup"><span data-stu-id="4a9fe-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="4a9fe-122">Чтобы создать новый [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ресурс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="4a9fe-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="4a9fe-123">щелчок правой кнопкой мыши в *окне Project*</span><span class="sxs-lookup"><span data-stu-id="4a9fe-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="4a9fe-124">выбор **состояния создания**  >  **смешанной реальности набор средств**  >  </span><span class="sxs-lookup"><span data-stu-id="4a9fe-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Пример состояния Скриптаблеобжект в инспекторе](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="4a9fe-126">[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)Скриптаблеобжект определяет как список состояний, так и тип *статемодел* , который создается для этих состояний.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="4a9fe-127">*Статемодел* — это класс, который расширяет [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) и реализует логику конечного автомата для создания текущего состояния во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="4a9fe-128">Текущее состояние из этого класса обычно используется обработчиками тем во время выполнения, чтобы определить, какие значения следует задать для свойств материала, преобразования GameObject и многое другое.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="4a9fe-129">Свойства обработчика тем</span><span class="sxs-lookup"><span data-stu-id="4a9fe-129">Theme engine properties</span></span>

<span data-ttu-id="4a9fe-130">За пределами *состояний*, [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ресурс также определяет список обработчиков тем и связанных с ними свойств для этих ядер.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="4a9fe-131">[Механизм тем](#theme-engines) еще раз определяет логику установки правильных значений для GameObject во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="4a9fe-132">[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)Ресурс может определять несколько ядер тем, чтобы добиться сложных переходов визуальных состояний, нацеленных на несколько свойств GameObject.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="4a9fe-133">**Среда выполнения темы**</span><span class="sxs-lookup"><span data-stu-id="4a9fe-133">**Theme Runtime**</span></span>

<span data-ttu-id="4a9fe-134">Определяет тип класса создаваемого обработчика тем</span><span class="sxs-lookup"><span data-stu-id="4a9fe-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="4a9fe-135">**Медлен**</span><span class="sxs-lookup"><span data-stu-id="4a9fe-135">**Easing**</span></span>

<span data-ttu-id="4a9fe-136">Некоторые *механизмы тем*, если они определяют свойство [исеасингсуппортед](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) как true, поддерживают ускорение между состояниями.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="4a9fe-137">Например, лерпинг между двумя цветами при изменении состояния.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="4a9fe-138">*Длительность* определяет время в секундах, по истечении которого начинается с начального значения до конечного значения, а *Кривая анимации* определяет частоту изменений за этот период времени.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="4a9fe-139">**Свойства шейдера**</span><span class="sxs-lookup"><span data-stu-id="4a9fe-139">**Shader properties**</span></span>

<span data-ttu-id="4a9fe-140">Некоторые *обработчики тем*, если они определяют свойство [арешадерссуппортед](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) как true, будут изменять определенные свойства шейдера во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="4a9fe-141">*Шейдер* и поля *свойств* определяют целевое свойство шейдера.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="4a9fe-142">Создание конфигурации темы с помощью кода</span><span class="sxs-lookup"><span data-stu-id="4a9fe-142">Create a theme configuration via code</span></span>

<span data-ttu-id="4a9fe-143">В целом, проще проектировать конфигурации тем с помощью инспектора Unity, но бывают случаи, когда темы должны динамически создаваться во время выполнения через код.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="4a9fe-144">Приведенный ниже фрагмент кода позволяет получить пример выполнения этой задачи.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="4a9fe-145">Чтобы упростить разработку, следующие вспомогательные методы полезны для упрощения установки.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="4a9fe-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) — Создает новое состояние Скриптаблеобжект с четырьмя значениями состояния по умолчанию, используемыми в [взаимодействующем](interactable.md) компоненте.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="4a9fe-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) — Каждый механизм темы определяет конфигурацию по умолчанию с правильными свойствами, необходимыми для этого типа среды выполнения темы.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="4a9fe-148">Этот вспомогательный метод создает определение для данного типа механизма темы.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

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

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="4a9fe-149">Обработчики тем</span><span class="sxs-lookup"><span data-stu-id="4a9fe-149">Theme engines</span></span>

<span data-ttu-id="4a9fe-150">[Механизм темы](#theme-engines) — это класс, который расширяется из [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) класса.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="4a9fe-151">Экземпляры этих классов создаются во время выполнения и настраиваются с помощью [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) объекта, как описано выше.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="4a9fe-152">Модули темы по умолчанию</span><span class="sxs-lookup"><span data-stu-id="4a9fe-152">Default theme engines</span></span>

<span data-ttu-id="4a9fe-153">МРТК поставляется со стандартным набором обработчиков тем, которые перечислены ниже:</span><span class="sxs-lookup"><span data-stu-id="4a9fe-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="4a9fe-154">Модули темы по умолчанию можно найти в разделе `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="4a9fe-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="4a9fe-155">Пользовательские обработчики тем</span><span class="sxs-lookup"><span data-stu-id="4a9fe-155">Custom theme engines</span></span>

<span data-ttu-id="4a9fe-156">Как уже говорилось, обработчик темы определяется как класс, который расширяется из [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) класса.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="4a9fe-157">Таким образом, новому ядру темы требуется только расширение этого класса и реализация следующего:</span><span class="sxs-lookup"><span data-stu-id="4a9fe-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="4a9fe-158">Обязательные реализации</span><span class="sxs-lookup"><span data-stu-id="4a9fe-158">Mandatory implementations</span></span>

<span data-ttu-id="4a9fe-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе. SetValue)</span><span class="sxs-lookup"><span data-stu-id="4a9fe-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="4a9fe-160">Для данного свойства, которое может быть идентифицировано `ThemeStateProperty.Name` , установите его текущее значение состояния на целевом узле GameObject (т. е.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="4a9fe-161">Задайте цвет материала и т. д.).</span><span class="sxs-lookup"><span data-stu-id="4a9fe-161">set the material color, etc).</span></span> <span data-ttu-id="4a9fe-162">*Индекс* указывает текущее значение состояния, к которому осуществляется доступ, и *процентное соотношение* между 0 и 1 используется для ускорения и лерпинг между значениями.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="4a9fe-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе.-свойство)</span><span class="sxs-lookup"><span data-stu-id="4a9fe-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="4a9fe-164">Для данного свойства, которое может быть идентифицировано `ThemeStateProperty.Name` , возвращает текущее значение, установленное на целевом узле GameObject (т. е.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="4a9fe-165">текущий цвет материала, текущее смещение локальной позиции и т. д.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="4a9fe-166">Это в основном используется для кэширования начального значения при замедлении между состояниями.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="4a9fe-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе. Жетдефаултсемедефинитион)</span><span class="sxs-lookup"><span data-stu-id="4a9fe-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="4a9fe-168">Возвращает [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) объект, который определяет свойства по умолчанию и конфигурацию, необходимые для пользовательской темы</span><span class="sxs-lookup"><span data-stu-id="4a9fe-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="4a9fe-169">Защищенный вариант открытого `SetValue()` определения, за исключением того, что семепропертивалуе задается вместо направления использования индекса и (или) процентной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="4a9fe-170">Рекомендуемые переопределения</span><span class="sxs-lookup"><span data-stu-id="4a9fe-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="4a9fe-171">Выполните все этапы инициализации, предназначенные для указанного параметра *GameObject* , используя свойства и конфигурации, определенные в параметре *семедефинитион* .</span><span class="sxs-lookup"><span data-stu-id="4a9fe-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="4a9fe-172">Рекомендуется вызывать `base.Init(host, settings)` в начале переопределения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="4a9fe-173">Значение, если механизм пользовательской темы может поддерживать замедление между значениями, настроенными с помощью [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) Свойства.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="4a9fe-174">Если пользовательский обработчик тем может поддерживать целевые свойства шейдера.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="4a9fe-175">Рекомендуется использовать [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) существующую инфраструктуру для эффективного задания и получения свойств шейдера через [материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span><span class="sxs-lookup"><span data-stu-id="4a9fe-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="4a9fe-176">Сведения о свойствах шейдера хранятся в каждом [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) с помощью и [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="4a9fe-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="4a9fe-177">При расширении [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) также может быть полезно переопределить [Интерактаблешадерсеме. дефаултшадерпроперти](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) с помощью *New*.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="4a9fe-178">Пример кода: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="4a9fe-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="4a9fe-179">Более того, следующие классы расширяют [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) класс, который снова использует [материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) для изменения значений свойств шейдера.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="4a9fe-180">Такой подход [позволяет снизить производительность](https://docs.unity3d.com/Manual/DrawCallBatching.html) , так как *материалпропертиблоккс* не создает новые экземпляры материалов при изменении значений.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="4a9fe-181">Однако доступ к стандартным свойствам класса [Material](https://docs.unity3d.com/ScriptReference/Material.html) не возвратит ожидаемые значения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="4a9fe-182">Используйте *материалпропертиблоккс* для получения и проверки текущих значений свойств материалов (например,</span><span class="sxs-lookup"><span data-stu-id="4a9fe-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="4a9fe-183">*_Color* или *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="4a9fe-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="4a9fe-184">Направляет тему сбрасывать измененные свойства обратно к исходным значениям, заданным на узле GameObject при инициализации этого обработчика тем.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="4a9fe-185">Пример пользовательской подсистемы тем</span><span class="sxs-lookup"><span data-stu-id="4a9fe-185">Custom theme engine example</span></span>

<span data-ttu-id="4a9fe-186">Ниже приведен пример пользовательского механизма новой темы.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="4a9fe-187">Эта реализация найдет компонент [мешрендерер](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) на инициализированном объекте узла и будет контролировать его видимость на основе текущего состояния.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="4a9fe-188">Комплексный пример</span><span class="sxs-lookup"><span data-stu-id="4a9fe-188">End-to-end example</span></span>

<span data-ttu-id="4a9fe-189">За пределами пользовательского механизма пользовательской темы, определенного в предыдущем разделе, в приведенном ниже примере кода показано, как управлять этой темой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="4a9fe-190">В частности, как установить текущее состояние темы таким образом, чтобы видимость Мешрендерер была обновлена соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="4a9fe-191">`theme.OnUpdate(state,force)` обычно должен вызываться в методе Update () для поддержки обработчиков тем, использующих ускорение и лерпинг между значениями.</span><span class="sxs-lookup"><span data-stu-id="4a9fe-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="4a9fe-192">См. также:</span><span class="sxs-lookup"><span data-stu-id="4a9fe-192">See also</span></span>

- [<span data-ttu-id="4a9fe-193">Интерактивный объект</span><span class="sxs-lookup"><span data-stu-id="4a9fe-193">Interactable</span></span>](interactable.md)
