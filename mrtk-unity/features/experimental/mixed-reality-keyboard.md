---
title: Клавиатура смешанной реальности
description: Описание использования клавиатуры смешанной реальности
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143394"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="27134-104">Вспомогательные классы клавиатуры для смешанной реальности и HoloLens</span><span class="sxs-lookup"><span data-stu-id="27134-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="27134-105">МРТК предоставляет несколько экспериментальных вспомогательных компонентов для помощи при запуске и чтении текста с [системной клавиатуры](../ux-building-blocks/system-keyboard.md).</span><span class="sxs-lookup"><span data-stu-id="27134-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="27134-106">Обратите внимание, что системная клавиатура будет работать в соответствии с возможностями целевой платформы. Например, клавиатура в HoloLens 2 будет поддерживать прямые взаимодействия, а клавиатура на HoloLens (1-й) будет поддерживать ГГВ<sup>[1](/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="27134-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="27134-107">Кроме того, системная клавиатура не будет отображаться при выполнении [удаленного взаимодействия Unity](../tools/holographic-remoting.md) из редактора с HoloLens.</span><span class="sxs-lookup"><span data-stu-id="27134-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="27134-108">микседреалитикэйбоард</span><span class="sxs-lookup"><span data-stu-id="27134-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="27134-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) — это компонент, предоставляющий методы для запуска и закрытия системной клавиатуры, а также для взаимодействия с текстом, вводимым с клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="27134-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="27134-110">Использование</span><span class="sxs-lookup"><span data-stu-id="27134-110">How to Use</span></span>

1. <span data-ttu-id="27134-111">Присоедините [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) компонент к любому объекту.</span><span class="sxs-lookup"><span data-stu-id="27134-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="27134-112">Вызовите функцию, `Show()` `Hide()` чтобы показать и скрыть клавиатуру, а также обработайте `OnShowKeyboard` события и, чтобы обрабатывались `OnHideKeyboard` `OnCommitText` , когда клавиатура отображается, скрыта и когда нажата клавиша ВВОД.</span><span class="sxs-lookup"><span data-stu-id="27134-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="27134-113">Поля ввода TMP_KeyboardInputField и UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="27134-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="27134-114">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)Классы и [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) — это компоненты, которые можно добавить в текстовые поля ввода для автоматического вызова системной клавиатуры при щелчке и обновления содержимого текстового поля ввода при вводе текста пользователем.</span><span class="sxs-lookup"><span data-stu-id="27134-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="27134-115">Использование</span><span class="sxs-lookup"><span data-stu-id="27134-115">How to use</span></span>

1. <span data-ttu-id="27134-116">Создайте поле ввода для Унитюи или Текстмешпро.</span><span class="sxs-lookup"><span data-stu-id="27134-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="27134-117">Добавьте соответствующий [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) компонент или [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) в игровой объект поля ввода.</span><span class="sxs-lookup"><span data-stu-id="27134-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="27134-118">Prefabs для полей ввода Унитюи и полей ввода Текстмешпро (Тмпро) доступны по адресу "Ассетс\мртк\експериментал\микседреалитикэйбоард\префабс".</span><span class="sxs-lookup"><span data-stu-id="27134-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="27134-119">Пример использования TMP_KeyboardInputField и UI_KeyboardInputField в "Ассетс\мртк\ексамплес\експериментал\микседреалитикэйбоард\сценес\микседреалитикэйбоардексампле.Унити"</span><span class="sxs-lookup"><span data-stu-id="27134-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>