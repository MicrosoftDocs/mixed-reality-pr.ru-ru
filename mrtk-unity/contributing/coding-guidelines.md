---
title: Рекомендации по программированию
description: Принципы программирования и соглашения, которым следует следовать при участии в МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, C#,
ms.openlocfilehash: c14f5f72d391c5474a01c798bfdaa5529700a509
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175332"
---
# <a name="coding-guidelines"></a>Рекомендации по программированию

В этом документе описываются принципы и соглашения по написанию кода, которым следует следовать при добавлении в МРТК.

---

## <a name="philosophy"></a>Подход

### <a name="be-concise-and-strive-for-simplicity"></a>Будьте кратко и стремитесь к простоте

Наиболее простым решением зачастую является лучшее решение. Это переопределение предназначено для этих рекомендаций и должно быть целью всего действия кодирования. Часть простой является краткой и согласуется с существующим кодом. Постарайтесь не усложнять свой код.

Читатели должны столкнуться только с артефактами, которые предоставляют полезную информацию. Например, комментарии, изменяющие, что очевидны, не предоставляют дополнительных сведений и увеличивают коэффициент шума до сигнала.

Старайтесь не усложнять логику кода. Обратите внимание, что это не инструкция по использованию минимального числа строк, минимизации размера имен идентификаторов или стиля фигурных скобок, но об уменьшении числа концепций и максимизации видимости этих элементов с помощью привычных шаблонов.

### <a name="produce-consistent-readable-code"></a>Создание единообразного, доступного для чтения кода

Удобочитаемость кода соотносится с низкой частотой дефектов. Стремитесь создавать код, который легко читать. Стремитесь создавать код, который имеет простую логику и повторно использует существующие компоненты, так как он также позволяет гарантировать правильность.

Все сведения о коде, которые вы создаете, от самых основных сведений о правильности до единообразного стиля и форматирования. Стиль написания кода следует использовать в соответствии с уже существующим, даже если он не соответствует вашим предпочтениям. Это повышает удобочитаемость общей базы кода.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Поддержка настройки компонентов как в редакторе, так и во время выполнения

МРТК поддерживает различные пользователи — люди, предпочитающие настраивать компоненты в редакторе Unity и загрузку Prefabs, а также пользователей, которым необходимо создавать экземпляры и настраивать объекты во время выполнения.

Весь код должен работать как при добавлении компонента к GameObject в сохраненной сцене, так и при создании экземпляра этого компонента в коде. Тесты должны включать тестовый случай как для создания экземпляра Prefabs, так и для создания экземпляра, настройки компонента во время выполнения.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Первая и Основная целевая платформа для воспроизведения в редакторе

Воспроизведение в редакторе — это самый быстрый способ выполнить итерацию в Unity. Предоставить нашим клиентам возможность быстро и быстро разрабатывать решения, а затем испытать другие идеи. Другими словами, увеличение скорости итерации повышает эффективность наших клиентов.

Сделайте все работу в редакторе, а затем убедитесь, что она работает на любой другой платформе. Не отключайте его работу в редакторе. Можно легко добавить новую платформу для воспроизведения в редакторе. Если приложение работает только на устройстве, работа в редакторе очень сложна.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Добавлять новые открытые поля, свойства, методы и сериализованные закрытые поля с осторожностью

Каждый раз, когда вы добавляете открытый метод, поле, свойство, он станет частью общедоступной области API МРТК. Закрытые поля, помеченные как, `[SerializeField]` также предоставляют поля для редактора и являются частью общедоступной области API. Другие пользователи могут использовать этот открытый метод, настраивать пользовательский Prefabs с помощью общедоступного поля и зависеть от него.

Новые открытые члены следует тщательно проверять. Любое общедоступное поле должно поддерживаться в будущем. Помните, что если тип открытого поля (или сериализованного закрытого поля) изменяется или удаляется из одноименного поведения, это может нарушить работу других пользователей. Поле должно быть рекомендовано к выпуску, а код для переноса изменений для людей, которые затратили зависимости, должен быть предоставлен.

### <a name="prioritize-writing-tests"></a>Определение приоритетов при написании тестов

МРТК — это проект сообщества, который изменяется различными участниками. Эти участники могут не иметь сведений об исправлении или функции, а также случайно привести к нарушению работы функции. [Мртк выполняет тесты непрерывной интеграции](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) перед выполнением каждого запроса на включение внесенных изменений. Изменения, которые нарушают тесты, не могут быть возвращены. Таким образом, тесты являются лучшим способом гарантировать, что другие пользователи не нарушат вашу функцию.

При исправлении ошибки напишите тест, чтобы убедиться в том, что она не будет регрессия в будущем. При добавлении функции напишите тесты, которые проверяют работу функции. Это необходимо для всех функций UX, за исключением экспериментальных функций.

## <a name="c-coding-conventions"></a>Соглашения о написании кода на C#

### <a name="script-license-information-headers"></a>Создать скрипт для заголовков лицензионных данных

Все сотрудники корпорации Майкрософт, которые вносят новые файлы, должны добавить следующий стандартный заголовок лицензии в начало всех новых файлов, как показано ниже:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Заголовки сводных сведений о функциях и методах

Все открытые классы, структуры, перечисления, функции, свойства, поля, публикуемые в МРТК, должны быть описаны в соответствии с их целями и использованием, как показано ниже:

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

Это гарантирует правильную создание и распространение документации для всех классов, методов и свойств.

Все файлы скриптов, отправленные без соответствующих тегов сводки, будут отклонены.

### <a name="mrtk-namespace-rules"></a>Правила пространства имен МРТК

набор средств смешанной реальности использует модель пространства имен на основе компонентов, где все базовые пространства имен начинаются с "Microsoft. микседреалити". набор средств ". В общем случае в пространствах имен не нужно указывать уровень набора средств (например, ядра, поставщиков, служб).

В настоящее время определены следующие пространства имен:

- Microsoft. Микседреалити. набор средств
- Microsoft. Микседреалити. набор средств. Границ
- Microsoft. Микседреалити. набор средств. Выполняет
- Microsoft. Микседреалити. набор средств. Редактор
- Microsoft. Микседреалити. набор средств. Входной
- Microsoft. Микседреалити. набор средств. спатиалаваренесс
- Microsoft. Микседреалити. набор средств. Телепортируйтесь
- Microsoft. Микседреалити. набор средств. Служебные программы

Для пространств имен с большим количеством типов можно создать ограниченное число подпространств имен, чтобы помочь в области использования.

Пропуск пространства имен для интерфейса, класса или типа данных приведет к блокировке изменения.

### <a name="adding-new-monobehaviour-scripts"></a>Добавление новых скриптов с несложным поведением

При добавлении новых скриптов с поддержкой проведений с запросом на включение внесенных изменений убедитесь, что [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) атрибут применяется ко всем применимым файлам. Это гарантирует, что компонент будет легко обнаруживаться в редакторе при нажатии кнопки *Добавить компонент* . Флаг атрибута не требуется, если компонент не может отображаться в редакторе, например в абстрактном классе.

В приведенном ниже примере *пакет* должен быть заполнен расположением пакета компонента. Если поместить элемент в папку *мртк/SDK* , пакет будет иметь значение *SDK*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Добавление новых скриптов инспектора Unity

Как правило, старайтесь не создавать пользовательские скрипты инспектора для компонентов МРТК. Он добавляет дополнительную нагрузку и управление базой кода, которая может обрабатываться подсистемой Unity.

Если требуется класс инспектора, попробуйте использовать Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) . Это опять упрощает класс инспектора и оставляет большую часть работы в Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Если в классе инспектора требуется пользовательская отрисовка, попробуйте использовать [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) и [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . Это обеспечит правильную обработку Unity вложенных Prefabs и измененных значений.

Если [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) не может использоваться из-за необходимости в пользовательской логике, убедитесь, что все сведения об использовании заключены в оболочку [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . Это обеспечит правильное отображение инспектора для вложенных Prefabs и измененных значений с заданным свойством.

Более того, попробуйте снабдить пользовательский класс инспектора [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) . Этот тег гарантирует, что несколько объектов с этим компонентом в сцене можно будет выбрать и изменить вместе. Все новые классы инспектора должны проверять, работает ли код в этой ситуации в сцене.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>Добавление нового Скриптаблеобжектс

При добавлении новых скриптов Скриптаблеобжект убедитесь, что [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) атрибут применяется ко всем применимым файлам. Это гарантирует, что компонент легко обнаруживается в редакторе с помощью меню создания ресурсов. Флаг атрибута не требуется, если компонент не может отображаться в редакторе, например в абстрактном классе.

В приведенном ниже примере *вложенная папка* должна быть заполнена вложенной папкой мртк, если это применимо. Если поместить элемент в папку *мртк/providers* , пакет будет иметь *поставщики*. Если поместить элемент в папку *мртк/Core* , задайте для него значение "Profiles".

В приведенном ниже примере — *MyNewService | Миневпровидер* должен быть заполнен новым классом Name (если применимо). Если поместить элемент в папку *микседреалититулкит* , оставьте эту строку.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Ведение журнала

При добавлении новых или обновлении существующих компонентов рекомендуется добавить журналы Дебугутилитиес. Логвербосе в интересный код, который может быть полезен для последующей отладки. Существует компромисс между добавлением журналов и дополнительными помехами и недостаточным протоколированием (что затрудняет диагностику).

Интересный пример, где полезно ведение журнала (вместе с интересующими полезными данными):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Этот тип ведения журнала может помочь в перехвате таких проблем [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) , как, вызванных несоответствием обнаруженных источников и потерянными событиями источника.

Не добавляйте журналы для данных и событий, происходящих при каждом кадре, в идеале, должны охватывать «интересные» события, управляемые различными входными данными пользователя (т. е. «щелчок» пользователем, а также набор изменений и событий, происходящих в журнале). Текущее состояние "пользователь по-прежнему удерживает жест" записал каждый кадр в журнал не интересно, и журналы будут переполнены.

Обратите внимание, что это подробное ведение журнала не включено по умолчанию (оно должно быть включено в [параметрах системы диагностики](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)).

### <a name="spaces-vs-tabs"></a>Пробелы и знаки табуляции

При участии в этом проекте обязательно используйте 4 пробела вместо вкладок.

### <a name="spacing"></a>Интервал

Не добавляйте дополнительные пробелы между квадратными скобками и круглыми скобками:

#### <a name="dont"></a>Не рекомендуется

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>Рекомендуется

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Соглашения об именах

Всегда используйте `PascalCase` для свойств. Используется `camelCase` для большинства полей, за исключением использования `PascalCase` для `static readonly` `const` полей и. Единственным исключением из этого является структура данных, требующая сериализации полей с помощью `JsonUtility` .

#### <a name="dont"></a>Не рекомендуется

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>Рекомендуется

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Модификаторы доступа

Всегда объявляйте модификатор доступа для всех полей, свойств и методов.

- Все методы API Unity должны быть по `private` умолчанию, если их не нужно переопределять в производном классе. В этом случае `protected` следует использовать.

- Поля всегда должны иметь `private` значение, со `public` свойствами или с помощью `protected` методов доступа к свойствам.

- По возможности используйте [элементы Expression-воплощающего](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) и [автоматические свойства](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) .

#### <a name="dont"></a>Не рекомендуется

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>Рекомендуется

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>Использовать фигурные скобки

Всегда используйте фигурные скобки после каждого блока операторов и поместите их на следующую строку.

#### <a name="dont"></a>Не рекомендуется

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>Не рекомендуется

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>Рекомендуется

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Открытые классы, структуры и перечисления должны поступать в свои файлы

Если класс, структура или перечисление могут быть сделаны частными, то их можно добавить в один и тот же файл.  Это позволяет избежать проблем с компиляцией с Unity и обеспечить правильную абстракцию кода, а также снизить вероятность конфликтов и критических изменений, когда необходимо изменить код.

#### <a name="dont"></a>Не рекомендуется

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>Рекомендуется

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>Рекомендуется

MyStruct. CS

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

Менумтипе. CS

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass. CS

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Инициализация перечислений

Чтобы убедиться, что все перечисления инициализированы правильно, начиная с 0, .NET предоставляет сокращенное сочетание клавиш для автоматической инициализации перечисления путем добавления первого (начального) значения. (например, значение 1 = 0 оставшиеся значения не требуются)

#### <a name="dont"></a>Не рекомендуется

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>Рекомендуется

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Упорядочение перечислений для соответствующего расширения

Очень важно, что если перечисление, скорее всего, будет расширено в будущем, чтобы упорядочить значения по умолчанию в верхней части перечисления, это гарантирует, что новые дополнения не затрагивают индексы перечисления.

#### <a name="dont"></a>Не рекомендуется

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>Рекомендуется

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>Проверка использования перечисления для битовых полей

Если существует возможность, чтобы перечисление требовало несколько состояний в качестве значения, например правой или левой = Left & right. Затем необходимо правильно настроить перечисление с помощью Битфлагс, чтобы его можно было использовать правильно.

Файл правой или левой. CS имеет конкретную реализацию для этого

### <a name="dont"></a>Не рекомендуется

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>Рекомендуется

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>Жестко запрограммированные пути к файлам

При создании путей к файловым строкам и, в частности, при записи жестко запрограммированных строковых путей, выполните следующие действия.

1. Используйте API- [ `Path` интерфейсы](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) C# везде, где это возможно, например `Path.Combine` или `Path.GetFullPath` .
1. Используйте/или [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) вместо \ или \\ \\ .

эти действия гарантируют, что мртк работает как в Windows, так и на системах Unix.

### <a name="dont"></a>Не рекомендуется

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>Рекомендуется

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Рекомендации, включая рекомендации Unity

Для некоторых целевых платформ этого проекта необходимо учитывать производительность. Учитывая это, всегда будьте внимательны при выделении памяти в часто именуемом коде в тесном цикле обновления или алгоритмах.

### <a name="encapsulation"></a>Инкапсуляция

Всегда используйте закрытые поля и открытые свойства, если доступ к полю требуется извне класса или структуры.  Не забудьте разместить закрытое поле и открытое свойство. Это упрощает наглядное представление, что обеспечивает обратную передачу свойства и поля, изменяемые сценарием.

> [!NOTE]
> Единственным исключением из этого является структура данных, для которой требуется сериализация полей в `JsonUtility` , где класс данных должен иметь все открытые поля для работы сериализации.

#### <a name="dont"></a>Не рекомендуется

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>Рекомендуется

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Значения кэша и сериализуются их в сцене или prefab, когда это возможно

с учетом HoloLens лучше оптимизировать для производительности и ссылок на кэш в сцене или prefab, чтобы ограничить выделение памяти во время выполнения.

#### <a name="dont"></a>Не рекомендуется

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>Рекомендуется

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Кэшировать ссылки на материалы, не вызывайте ". Material" каждый раз

Unity создаст новый материал каждый раз при использовании ". Material", что приведет к утечке памяти при неправильной очистке.

#### <a name="dont"></a>Не рекомендуется

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>Рекомендуется

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> Кроме того, можно использовать свойство "Шаредматериал" Unity, которое не создает новый материал при каждом обращении.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>использовать [зависимую от платформы компиляцию](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) для того, чтобы набор средств не нарушат сборку на другой платформе

- Используйте `WINDOWS_UWP` для использования интерфейсов API, относящихся к UWP, не относящимся к Unity. Это предотвратит попытку запуска в редакторе или на неподдерживаемых платформах. Это эквивалентно `UNITY_WSA && !UNITY_EDITOR` и должно использоваться в пользу.
- Используйте `UNITY_WSA` для использования интерфейсов API Unity, зависящих от UWP, таких как `UnityEngine.XR.WSA` пространство имен. Это будет выполняться в редакторе, если платформа имеет значение UWP, а также в созданных приложениях UWP.

Эта диаграмма поможет вам выбрать нужный `#if` вариант в зависимости от ваших вариантов использования и ожидаемых параметров сборки.

|Платформа | IL2CPP UWP | UWP .NET | Редактор |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | Неверно | False | Да |
| `UNITY_WSA` | Да | Да | Да |
| `WINDOWS_UWP` | Да | Да | False |
| `UNITY_WSA && !UNITY_EDITOR` | Да | Да | False |
| `ENABLE_WINMD_SUPPORT` | Да | Да | Неверно |
| `NETFX_CORE` | False | Да | Неверно |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Предпочитать DateTime. UtcNow через DateTime. Now

DateTime. UtcNow работает быстрее, чем DateTime. Now. В предыдущем исследовании производительности мы обнаружили, что использование DateTime. теперь добавляет значительные издержки, особенно при использовании в цикле Update (). [Другие пользователи столкнулись с той же проблемой](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).

Предпочитать использование DateTime. UtcNow, если вам действительно не требуется локализованное время (по законным причинам может потребоваться отобразить текущее время в часовом поясе пользователя). Если вы работаете с относительным временем (т. е. разностью между последним обновлением и сейчас), лучше использовать DateTime. UtcNow, чтобы избежать издержек, связанных с преобразованиями часовых поясов.

## <a name="powershell-coding-conventions"></a>Соглашения о написании кода PowerShell

Подмножество базы кода МРТК использует PowerShell для инфраструктуры конвейера и различных сценариев и служебных программ. Новый код PowerShell должен соответствовать [стилю пошкоде](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>См. также:

 [Соглашения о написании кода на C# из MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
