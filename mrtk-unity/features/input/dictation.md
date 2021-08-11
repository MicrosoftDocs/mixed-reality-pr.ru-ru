---
title: Диктовка
description: Докумментатион о записи аудиоклипов и получении транскрипции в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220011"
---
# <a name="dictation"></a>Диктовка

Диктовка позволяет пользователям записывать аудиоклипы и получать транскрипцию. Чтобы использовать его, убедитесь, что система диктовки зарегистрирована во *входном системном профиле*. **Windowsный поставщик входных данных диктофона** — это система диктовки, предоставляемая из комплекта, но для реализации можно создать альтернативные системы диктовки [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Требования

система диктовки использует [диктатионрекогнизер](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) Unity, который сам использует базовые интерфейсы api распознавания Windows для обработки диктовки. обратите внимание, что это означает, что эта функция имеется только на платформах на основе Windows.

Для использования системы диктовки требуются возможности приложения "Интернет-клиент" и "микрофон" в [разделе плайерсеттингс-capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
дополнительные сведения о голосовом вводе в Unity см. в [Windows Mixed Reality документации](/windows/mixed-reality/voice-input-in-unity#dictation) .

## <a name="configuration"></a>Конфигурация

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

После настройки службы диктовки можно использовать [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) сценарий для запуска и завершения записи сеансов, а также получения результатов транскрипции через унитевентс.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **Гипотеза диктовки** создается по мере того, как пользователь сразу же говорит о том, что проводятся предварительные записи звука, полученные на данный момент.
- **Результат диктовки** создается в конце каждого предложения (т. е. когда пользователь приостанавливает работу) с завершающим обработкой звука, записываемого на данный момент.
- **Диктовка по завершении** создается в конце сеанса записи с полной и окончательной обработкой звука.
- **Ошибка диктовки** возникает, чтобы сообщить об ошибках в службе диктофона. Транскрипция в этом случае содержит описание ошибки.

## <a name="example-scene"></a>Пример сцены

В сцене **диктовки** в `MRTK/Examples/Demos/Input/Scenes/Dictation` показывает, какой `DictationHandler` сценарий используется. Если требуется больший контроль, можно либо расширить этот скрипт, либо создать собственную реализацию [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) для получения событий диктовки напрямую.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
