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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Вспомогательные классы клавиатуры для смешанной реальности и HoloLens

МРТК предоставляет несколько экспериментальных вспомогательных компонентов для помощи при запуске и чтении текста с [системной клавиатуры](../ux-building-blocks/system-keyboard.md).

Обратите внимание, что системная клавиатура будет работать в соответствии с возможностями целевой платформы. Например, клавиатура в HoloLens 2 будет поддерживать прямые взаимодействия, а клавиатура на HoloLens (1-й) будет поддерживать ГГВ<sup>[1](/windows/mixed-reality/gaze)</sup>. Кроме того, системная клавиатура не будет отображаться при выполнении [удаленного взаимодействия Unity](../tools/holographic-remoting.md) из редактора с HoloLens.

## <a name="mixedrealitykeyboard"></a>микседреалитикэйбоард

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) — это компонент, предоставляющий методы для запуска и закрытия системной клавиатуры, а также для взаимодействия с текстом, вводимым с клавиатуры.  

### <a name="how-to-use"></a>Использование

1. Присоедините [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) компонент к любому объекту.
2. Вызовите функцию, `Show()` `Hide()` чтобы показать и скрыть клавиатуру, а также обработайте `OnShowKeyboard` события и, чтобы обрабатывались `OnHideKeyboard` `OnCommitText` , когда клавиатура отображается, скрыта и когда нажата клавиша ВВОД.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Поля ввода TMP_KeyboardInputField и UI_KeyboardInputField

[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)Классы и [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) — это компоненты, которые можно добавить в текстовые поля ввода для автоматического вызова системной клавиатуры при щелчке и обновления содержимого текстового поля ввода при вводе текста пользователем.

### <a name="how-to-use"></a>Использование

1. Создайте поле ввода для Унитюи или Текстмешпро.
2. Добавьте соответствующий [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) компонент или [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) в игровой объект поля ввода.

Prefabs для полей ввода Унитюи и полей ввода Текстмешпро (Тмпро) доступны по адресу "Ассетс\мртк\експериментал\микседреалитикэйбоард\префабс".

Пример использования TMP_KeyboardInputField и UI_KeyboardInputField в "Ассетс\мртк\ексамплес\експериментал\микседреалитикэйбоард\сценес\микседреалитикэйбоардексампле.Унити"