---
title: Ввод с клавиатуры в Unity
description: Unity предоставляет класс Таучскринкэйбоард для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: клавиатура, вход, Unity, таучскринкэйбоард, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098276"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="f65bd-104">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="f65bd-104">Keyboard input in Unity</span></span>

<span data-ttu-id="f65bd-105">**Пространство имен:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="f65bd-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="f65bd-106">**Тип**: *[таучскринкэйбоард](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="f65bd-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="f65bd-107">Хотя HoloLens поддерживает многие виды входных данных, включая клавиатуры Bluetooth, большинство приложений не может предположить, что у всех пользователей есть доступная физическая клавиатура.</span><span class="sxs-lookup"><span data-stu-id="f65bd-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="f65bd-108">Если приложению требуются текстовые входные данные, необходимо предоставить некоторую форму экранной клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f65bd-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="f65bd-109">Unity предоставляет класс *[таучскринкэйбоард](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f65bd-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="f65bd-110">Поведение системной клавиатуры HoloLens в Unity</span><span class="sxs-lookup"><span data-stu-id="f65bd-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="f65bd-111">В HoloLens *таучскринкэйбоард* использует экранную клавиатуру системы и прямо накладывается поверх объемные представления приложения Mr.</span><span class="sxs-lookup"><span data-stu-id="f65bd-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="f65bd-112">Взаимодействие аналогично использованию клавиатуры во встроенных приложениях HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f65bd-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="f65bd-113">Обратите внимание, что системная клавиатура будет вести себя в соответствии с возможностями целевой платформы. Например, клавиатура в HoloLens 2 будет поддерживать прямые взаимодействия, тогда как клавиатура на HoloLens (1-й) будет поддерживать ГГВ (взгляд, жест и голоса).</span><span class="sxs-lookup"><span data-stu-id="f65bd-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="f65bd-114">Кроме того, системная клавиатура не будет отображаться при выполнении удаленного взаимодействия Unity из редактора с HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f65bd-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="f65bd-115">Использование системной клавиатуры в приложении Unity</span><span class="sxs-lookup"><span data-stu-id="f65bd-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="f65bd-116">Объявление клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f65bd-116">Declare the keyboard</span></span>

<span data-ttu-id="f65bd-117">В классе объявите переменную для хранения *таучскринкэйбоард* и переменную для хранения строки, возвращаемой клавиатурой.</span><span class="sxs-lookup"><span data-stu-id="f65bd-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="f65bd-118">Вызов клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f65bd-118">Invoke the keyboard</span></span>

<span data-ttu-id="f65bd-119">Когда событие возникает при запросе ввода с клавиатуры, используйте следующую для отображения клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f65bd-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="f65bd-120">Можно использовать дополнительные параметры, передаваемые в `TouchScreenKeyboard.Open` функцию, чтобы управлять поведением клавиатуры (например, задавать текст заполнителя или поддерживать автозамену).</span><span class="sxs-lookup"><span data-stu-id="f65bd-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="f65bd-121">Полный список параметров см. в [документации Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="f65bd-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="f65bd-122">Получение типизированного содержимого</span><span class="sxs-lookup"><span data-stu-id="f65bd-122">Retrieve typed contents</span></span>

<span data-ttu-id="f65bd-123">Содержимое можно просто извлечь путем вызова метода `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="f65bd-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="f65bd-124">Может потребоваться получить содержимое для каждого кадра или только после закрытия клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f65bd-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="f65bd-125">Альтернативные параметры клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f65bd-125">Alternative keyboard options</span></span>

<span data-ttu-id="f65bd-126">Кроме непосредственного использования класса *таучскринкэйбоард* , можно получить ввод пользователя, используя *поле ввода пользовательского интерфейса* Unity или *поле ввода текстмешпро*.</span><span class="sxs-lookup"><span data-stu-id="f65bd-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="f65bd-127">Кроме того, существует реализация, основанная на *таучскринкэйбоард* в [хандинтерактионексамплес сцене](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) [мртк](/windows/mixed-reality/mrtk-unity) (в левой части есть пример взаимодействия с клавиатурой).</span><span class="sxs-lookup"><span data-stu-id="f65bd-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f65bd-128">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="f65bd-128">Next Development Checkpoint</span></span>

<span data-ttu-id="f65bd-129">Если вы подготовились к расположению разработки Unity, мы собрались изучить возможности и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f65bd-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="f65bd-130">Здесь можно перейти к любому [разделу](unity-development-overview.md#3-advanced-features) или перейти непосредственно к развертыванию приложения на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="f65bd-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f65bd-131">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f65bd-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
