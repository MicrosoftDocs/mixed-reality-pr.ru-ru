---
title: Речь
description: Настройка речевого ввода в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, речь
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228419"
---
# <a name="speech"></a>Речь

![Быстрое меню](../images/input/MRTK_Input_Speech.png)

поставщики речевого ввода, такие как *Windows речевого ввода*, не создают контроллеры, а позволяют определять ключевые слова, которые будут вызывать события речевого ввода при распознавании. **Профиль команд распознавания речи** во *входном системном профиле* — это место, где вы настраиваете ключевые слова для распознавания. Для каждой команды можно также:

- Выберите **действие ввода** для его отображения. Таким образом, можно использовать ключевое слово *SELECT* для того, чтобы тот же результат, что и при щелчке левой кнопкой мыши, путем сопоставления обоих и того же действия.
- Укажите **код ключа** , при нажатии которого будет выдаваться то же событие речи.
- Добавьте **ключ локализации** , который будет использоваться в приложениях UWP для получения локализованного ключевого слова из ресурсов приложения.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Обработка речевого ввода

[**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler)Скрипт можно добавить в GameObject для обработки речевых команд с помощью [**унитевентс**](https://docs.unity3d.com/Manual/UnityEvents.html). В нем автоматически отображается список определенных ключевых слов из **профиля голосовых команд**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Назначение необязательного **спичконфирматионтултип. prefab** для показа метки всплывающей подсказки с анимированным подтверждением при распознавании.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

Кроме того, разработчики могут реализовать [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) интерфейс в пользовательском компоненте скрипта для [обработки событий речевого ввода](input-events.md#input-event-interface-example).

## <a name="example-scene"></a>Пример сцены

В **спичинпутексампле** сцене (в `MRTK/Examples/Demos/Input/Scenes/Speech` ) показано, как использовать речь. Можно также прослушивать события команды распознавания речи непосредственно в собственном скрипте, реализовав [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (см. таблицу [обработчиков событий](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
