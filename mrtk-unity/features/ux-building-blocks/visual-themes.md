---
title: Визуальные темы
description: Обзор визуальных тем. гибкое управление ресурсами UX в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, мртк темы
ms.openlocfilehash: f7e0b10f51947884c4d23191fd147315084c5295e9b48953bb5de10b7cbc0d22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223976"
---
# <a name="visual-themes"></a>Визуальные темы

Темы позволяют гибко управлять ресурсами UX в ответ на различные переходы состояний. Это может привести к изменению цвета кнопки, изменению размера элемента в ответ на фокус и т. д. Платформа визуальных тем состоит из двух основных частей: 1) конфигурации и 2) ядер среды выполнения.

[Конфигурации тем](#theme-configuration) являются определениями свойств и типов, тогда как [обработчики тем](#theme-engines) являются классами, использующими конфигурации, и реализуют логику для обновления преобразований, материалов и других возможностей во время выполнения.

## <a name="theme-configuration"></a>Конфигурация темы

Конфигурации темы — это [скриптаблеобжектс](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , которые определяют, как обработчики тем будут инициализироваться во время выполнения. Они определяют, какие свойства и значения следует использовать в ответ на ввод или другие изменения состояния при запуске приложения. Как [скриптаблеобжектс](https://docs.unity3d.com/Manual/class-ScriptableObject.html) активы, конфигурации тем можно определить один раз, а затем повторно использовать в разных компонентах UX.

Чтобы создать новый [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ресурс, сделайте следующее:

1) щелчок правой кнопкой мыши в *окне Project*
1) выберите **создание**  >  **темы набор средств смешанной реальности**  >  

Примеры ресурсов конфигурации темы можно найти в разделе `MRTK/SDK/Features/UX/Interactable/Themes` .

![Пример Скриптаблеобжект темы в инспекторе](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Состояния

При создании нового [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) необходимо установить, какие состояния доступны. Свойство *statess* указывает, сколько значений должна определяться конфигурацией темы, так как для каждого состояния будет одно значение. В приведенном выше примере показано состояние по умолчанию, [заданное для взаимодействующего](interactable.md#general-input-settings) компонента: *по умолчанию*, *фокус*, *Нажатие* и *Отключение*. Они определены в файле ресурсов `DefaultInteractableStates` (Asset/мртк/SDK/Features/UX/States).

Чтобы создать новый [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ресурс, сделайте следующее:

1) щелчок правой кнопкой мыши в *окне Project*
1) выбор **состояния создания**  >  **смешанной реальности набор средств**  >  

![Пример состояния Скриптаблеобжект в инспекторе](../images/interactable/DefaultInteractableStates.png)

[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)Скриптаблеобжект определяет как список состояний, так и тип *статемодел* , который создается для этих состояний. *Статемодел* — это класс, который расширяет [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) и реализует логику конечного автомата для создания текущего состояния во время выполнения. Текущее состояние из этого класса обычно используется обработчиками тем во время выполнения, чтобы определить, какие значения следует задать для свойств материала, преобразования GameObject и многое другое.

### <a name="theme-engine-properties"></a>Свойства обработчика тем

За пределами *состояний*, [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ресурс также определяет список обработчиков тем и связанных с ними свойств для этих ядер. [Механизм тем](#theme-engines) еще раз определяет логику установки правильных значений для GameObject во время выполнения.

[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)Ресурс может определять несколько ядер тем, чтобы добиться сложных переходов визуальных состояний, нацеленных на несколько свойств GameObject.

**Среда выполнения темы**

Определяет тип класса создаваемого обработчика тем

**Медлен**

Некоторые *механизмы тем*, если они определяют свойство [исеасингсуппортед](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) как true, поддерживают ускорение между состояниями. Например, лерпинг между двумя цветами при изменении состояния. *Длительность* определяет время в секундах, по истечении которого начинается с начального значения до конечного значения, а *Кривая анимации* определяет частоту изменений за этот период времени.

**Свойства шейдера**

Некоторые *обработчики тем*, если они определяют свойство [арешадерссуппортед](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) как true, будут изменять определенные свойства шейдера во время выполнения. *Шейдер* и поля *свойств* определяют целевое свойство шейдера.

### <a name="create-a-theme-configuration-via-code"></a>Создание конфигурации темы с помощью кода

В целом, проще проектировать конфигурации тем с помощью инспектора Unity, но бывают случаи, когда темы должны динамически создаваться во время выполнения через код. Приведенный ниже фрагмент кода позволяет получить пример выполнения этой задачи.

Чтобы упростить разработку, следующие вспомогательные методы полезны для упрощения установки.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) — Создает новое состояние Скриптаблеобжект с четырьмя значениями состояния по умолчанию, используемыми в [взаимодействующем](interactable.md) компоненте.

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) — Каждый механизм темы определяет конфигурацию по умолчанию с правильными свойствами, необходимыми для этого типа среды выполнения темы. Этот вспомогательный метод создает определение для данного типа механизма темы.

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

## <a name="theme-engines"></a>Обработчики тем

[Механизм темы](#theme-engines) — это класс, который расширяется из [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) класса. Экземпляры этих классов создаются во время выполнения и настраиваются с помощью [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) объекта, как описано выше.

### <a name="default-theme-engines"></a>Модули темы по умолчанию

МРТК поставляется со стандартным набором обработчиков тем, которые перечислены ниже:

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

Модули темы по умолчанию можно найти в разделе `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Пользовательские обработчики тем

Как уже говорилось, обработчик темы определяется как класс, который расширяется из [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) класса. Таким образом, новому ядру темы требуется только расширение этого класса и реализация следующего:

#### <a name="mandatory-implementations"></a>Обязательные реализации

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе. SetValue)

Для данного свойства, которое может быть идентифицировано `ThemeStateProperty.Name` , установите его текущее значение состояния на целевом узле GameObject (т. е. Задайте цвет материала и т. д.). *Индекс* указывает текущее значение состояния, к которому осуществляется доступ, и *процентное соотношение* между 0 и 1 используется для ускорения и лерпинг между значениями.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе.-свойство)

Для данного свойства, которое может быть идентифицировано `ThemeStateProperty.Name` , возвращает текущее значение, установленное на целевом узле GameObject (т. е. текущий цвет материала, текущее смещение локальной позиции и т. д. Это в основном используется для кэширования начального значения при замедлении между состояниями.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref: Microsoft. Микседреалити. набор средств. Интерфейса. Интерактаблесемебасе. Жетдефаултсемедефинитион)

Возвращает [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) объект, который определяет свойства по умолчанию и конфигурацию, необходимые для пользовательской темы

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Защищенный вариант открытого `SetValue()` определения, за исключением того, что семепропертивалуе задается вместо направления использования индекса и (или) процентной конфигурации.

#### <a name="recommended-overrides"></a>Рекомендуемые переопределения

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Выполните все этапы инициализации, предназначенные для указанного параметра *GameObject* , используя свойства и конфигурации, определенные в параметре *семедефинитион* . Рекомендуется вызывать `base.Init(host, settings)` в начале переопределения.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Значение, если механизм пользовательской темы может поддерживать замедление между значениями, настроенными с помощью [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) Свойства.

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Если пользовательский обработчик тем может поддерживать целевые свойства шейдера. Рекомендуется использовать [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) существующую инфраструктуру для эффективного задания и получения свойств шейдера через [материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). Сведения о свойствах шейдера хранятся в каждом [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) с помощью и [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> При расширении [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) также может быть полезно переопределить [Интерактаблешадерсеме. дефаултшадерпроперти](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) с помощью *New*.
>
> Пример кода: `protected new const string DefaultShaderProperty = "_Color";`
>
> Более того, следующие классы расширяют [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) класс, который снова использует [материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) для изменения значений свойств шейдера. Такой подход [позволяет снизить производительность](https://docs.unity3d.com/Manual/DrawCallBatching.html) , так как *материалпропертиблоккс* не создает новые экземпляры материалов при изменении значений. Однако доступ к стандартным свойствам класса [Material](https://docs.unity3d.com/ScriptReference/Material.html) не возвратит ожидаемые значения. Используйте *материалпропертиблоккс* для получения и проверки текущих значений свойств материалов (например, *_Color* или *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Направляет тему сбрасывать измененные свойства обратно к исходным значениям, заданным на узле GameObject при инициализации этого обработчика тем.  

### <a name="custom-theme-engine-example"></a>Пример пользовательской подсистемы тем

Ниже приведен пример пользовательского механизма новой темы. Эта реализация найдет компонент [мешрендерер](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) на инициализированном объекте узла и будет контролировать его видимость на основе текущего состояния.

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

## <a name="end-to-end-example"></a>Комплексный пример

За пределами пользовательского механизма пользовательской темы, определенного в предыдущем разделе, в приведенном ниже примере кода показано, как управлять этой темой во время выполнения. В частности, как установить текущее состояние темы таким образом, чтобы видимость Мешрендерер была обновлена соответствующим образом.

> [!NOTE]
> `theme.OnUpdate(state,force)` обычно должен вызываться в методе Update () для поддержки обработчиков тем, использующих ускорение и лерпинг между значениями.

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

## <a name="see-also"></a>См. также раздел

- [Интерактивный объект](interactable.md)
