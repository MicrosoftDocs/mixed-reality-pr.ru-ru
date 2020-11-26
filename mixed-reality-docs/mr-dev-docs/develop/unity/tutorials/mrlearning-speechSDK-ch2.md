---
title: Руководства по использованию службы "Речь" в Azure, часть 2. Добавление автономного режима для преобразования речи в текст в локальной среде
description: В рамках этого курса вы узнаете, как реализовать пакет SDK "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, распознавание речи, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: d5b0e5140c698996c051eab10064d99280482886
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679733"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. Использование функции распознавания речи для выполнения команд

В этом руководстве вы добавите возможность выполнения команд с помощью распознавания речи Azure, что позволит выполнять действия по определенным в приложении словам или фразам.

## <a name="objectives"></a>Задачи

* Изучение возможностей по применению распознавания речи Azure для выполнения команд

## <a name="instructions"></a>Инструкции

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Wake Word Recognizer (Script)** (Распознаватель слова для пробуждения Lunarcom — скрипт) к объекту Lunarcom и настройте его, как показано ниже.

* В поле **Wake Word** (Слово для пробуждения) введите подходящую фразу, например _Activate terminal_ (Активировать терминал).
* В поле **Dismiss Word** (Слово для отключения) введите подходящую фразу, например _Dismiss terminal_ (Отключить терминал).

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Компонент Lunarcom Wake Word Recognizer (Script) (Распознаватель слова для пробуждения Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Если теперь вы входите в игровой режим, как описано в предыдущем руководстве, панель терминала будет по умолчанию включена, но вы сможете ее отключить, произнеся настроенное слово для отключения **Dismiss terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Чтобы снова включить терминал, произнесите слово для пробуждения **Activate terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.

> [!TIP]
> Если вы ожидаете, что подключение к Azure часто будет невозможным, речевые команды можно реализовать с помощью МRТК по инструкциям из статьи [Использование голосовых команд](mr-learning-base-09.md).

## <a name="congratulations"></a>Поздравляем!

Вы успешно реализовали функцию речевых команд на платформе Azure. Запустите приложение на устройстве и убедитесь, что все работает правильно.

В следующем учебнике вы узнаете, как переводить текст с помощью распознавания речи Azure.

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Добавление компонента перевода речи Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
