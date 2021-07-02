---
title: Системная клавиатура
description: Обзор системной платы с системным ключом в МРТК
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, системная клавиатура,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176491"
---
# <a name="system-keyboard"></a>Системная клавиатура

![Системная клавиатура](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Приложение Unity может вызывать системную клавиатуру в любое время. обратите внимание, что системная клавиатура работает в соответствии с возможностями целевой платформы, например, клавиатура на HoloLens 2 будет поддерживать прямое взаимодействие, а клавиатура на HoloLens (1-й) будет поддерживать ггв (взгляд, жест и голоса)<sup>[1](/windows/mixed-reality/gaze)</sup>. Кроме того, системная клавиатура не будет отображаться при выполнении [удаленного взаимодействия Unity](../tools/holographic-remoting.md) из редактора с HoloLens.

## <a name="how-to-invoke-the-system-keyboard"></a>Вызов системной клавиатуры

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Чтение входных данных

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a>Пример системной клавиатуры

Вы можете увидеть простой пример того, как открыть системную клавиатуру в `MixedRealityKeyboard.cs` (Assets/мртк/SDK/эксперименталь/Features/UX/микседреалитикэйбоард. cs).

## <a name="see-also"></a>См. также:

- [Вспомогательные классы клавиатуры для смешанной реальности](../experimental/mixed-reality-keyboard.md)
