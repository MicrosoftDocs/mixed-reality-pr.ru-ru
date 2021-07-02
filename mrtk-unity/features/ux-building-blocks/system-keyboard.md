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
# <a name="system-keyboard"></a><span data-ttu-id="94de7-104">Системная клавиатура</span><span class="sxs-lookup"><span data-stu-id="94de7-104">System keyboard</span></span>

![Системная клавиатура](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="94de7-106">Приложение Unity может вызывать системную клавиатуру в любое время.</span><span class="sxs-lookup"><span data-stu-id="94de7-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="94de7-107">обратите внимание, что системная клавиатура работает в соответствии с возможностями целевой платформы, например, клавиатура на HoloLens 2 будет поддерживать прямое взаимодействие, а клавиатура на HoloLens (1-й) будет поддерживать ггв (взгляд, жест и голоса)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="94de7-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="94de7-108">Кроме того, системная клавиатура не будет отображаться при выполнении [удаленного взаимодействия Unity](../tools/holographic-remoting.md) из редактора с HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94de7-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="94de7-109">Вызов системной клавиатуры</span><span class="sxs-lookup"><span data-stu-id="94de7-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="94de7-110">Чтение входных данных</span><span class="sxs-lookup"><span data-stu-id="94de7-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="94de7-111">Пример системной клавиатуры</span><span class="sxs-lookup"><span data-stu-id="94de7-111">System keyboard example</span></span>

<span data-ttu-id="94de7-112">Вы можете увидеть простой пример того, как открыть системную клавиатуру в `MixedRealityKeyboard.cs` (Assets/мртк/SDK/эксперименталь/Features/UX/микседреалитикэйбоард. cs).</span><span class="sxs-lookup"><span data-stu-id="94de7-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="94de7-113">См. также:</span><span class="sxs-lookup"><span data-stu-id="94de7-113">See Also</span></span>

- [<span data-ttu-id="94de7-114">Вспомогательные классы клавиатуры для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="94de7-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
