---
title: Клавиатура смешанной реальности
description: Описание использования клавиатуры смешанной реальности
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466234"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>вспомогательные классы клавиатуры для смешанной реальности и HoloLens

МРТК предоставляет несколько экспериментальных вспомогательных компонентов для помощи при запуске и чтении текста с [системной клавиатуры](../ux-building-blocks/system-keyboard.md).

обратите внимание, что системная клавиатура будет вести себя в соответствии с возможностями целевой платформы, например, клавиатура на HoloLens 2 будет поддерживать прямое взаимодействие, а клавиатура на HoloLens (1-й общий) будет поддерживать ггв<sup>[1](/windows/mixed-reality/gaze)</sup>. Кроме того, системная клавиатура не будет отображаться при выполнении [удаленного взаимодействия Unity](../tools/holographic-remoting.md) из редактора с HoloLens.

## <a name="mixedrealitykeyboard"></a>микседреалитикэйбоард

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) — это компонент, предоставляющий методы для запуска и закрытия системной клавиатуры, а также для взаимодействия с текстом, вводимым с клавиатуры.  

### <a name="how-to-use"></a>Использование

1. Присоедините [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) компонент к любому объекту.
2. Вызовите функцию, `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` чтобы показать и скрыть клавиатуру, а также обработайте `OnShowKeyboard` события и, чтобы обрабатывались `OnHideKeyboard` `OnCommitText` , когда клавиатура отображается, скрыта и когда нажата клавиша ВВОД.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Поля ввода TMP_KeyboardInputField и UI_KeyboardInputField

[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)Классы и [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) — это компоненты, которые можно добавить в текстовые поля ввода для автоматического вызова системной клавиатуры при щелчке и обновления содержимого текстового поля ввода при вводе текста пользователем.

### <a name="how-to-use"></a>Использование

1. Создайте поле ввода для Унитюи или Текстмешпро.
2. Добавьте соответствующий [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) компонент или [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) в игровой объект поля ввода.

Prefabs для полей ввода Унитюи и полей ввода Текстмешпро (Тмпро) доступны по адресу "Ассетс\мртк\експериментал\микседреалитикэйбоард\префабс".

Пример использования TMP_KeyboardInputField и UI_KeyboardInputField в "Ассетс\мртк\ексамплес\експериментал\микседреалитикэйбоард\сценес\микседреалитикэйбоардексампле.Унити"