---
title: Руководства по использованию службы "Речь" в Azure, часть 3. Добавление компонента перевода речи Azure Cognitive Services
description: В этом курсе вы узнаете, как реализовать пакет SDK "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, распознавание речи, Windows 10, перевод речи
ms.localizationpriority: high
ms.openlocfilehash: 1139da69b27352b996d57184e21e9d6291d26fce
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679923"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Добавление компонента перевода речи Azure Cognitive Services

В этом учебнике вы добавите в проект возможность перевода речи, которая позволит переводить и расшифровывать речь на трех разных языках.

## <a name="objectives"></a>Задачи

* Изучение возможностей по интеграции перевода речи Azure

## <a name="instructions"></a>Инструкции

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Translation Recognizer (Script)** (Распознаватель перевода Lunarcom — скрипт) к объекту Lunarcom и настройте его, как показано ниже.

* Укажите любое удобное значение **Target Language** (Целевой язык), например _German_ (Немецкий).

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> Компонент Lunarcom Translation Recognizer (Script) (Распознаватель перевода Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Войдя в игровой режим, вы сможете проверить перевод речи. Для начала нажмите кнопку спутника. Теперь, если на компьютере подключен микрофон, любой сказанный вами текст будет автоматически переводиться на выбранный язык и выводиться на панель терминала:

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.

## <a name="congratulations"></a>Поздравляем!

Теперь ваш проект может успешно переводить произносимые слова на несколько разных языков. Запустите приложение на устройстве и убедитесь, что все работает правильно.

> [!div class="nextstepaction"]
> [Следующее руководство: 4. Настройка намерения и распознавание естественного языка](mrlearning-speechSDK-ch4.md)
