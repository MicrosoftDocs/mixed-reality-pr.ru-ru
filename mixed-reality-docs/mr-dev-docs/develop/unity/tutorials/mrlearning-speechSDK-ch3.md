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
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="96162-105">3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="96162-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="96162-106">В этом учебнике вы добавите в проект возможность перевода речи, которая позволит переводить и расшифровывать речь на трех разных языках.</span><span class="sxs-lookup"><span data-stu-id="96162-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="96162-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="96162-107">Objectives</span></span>

* <span data-ttu-id="96162-108">Изучение возможностей по интеграции перевода речи Azure</span><span class="sxs-lookup"><span data-stu-id="96162-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="96162-109">Инструкции</span><span class="sxs-lookup"><span data-stu-id="96162-109">Instructions</span></span>

<span data-ttu-id="96162-110">В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Translation Recognizer (Script)** (Распознаватель перевода Lunarcom — скрипт) к объекту Lunarcom и настройте его, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="96162-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="96162-111">Укажите любое удобное значение **Target Language** (Целевой язык), например _German_ (Немецкий).</span><span class="sxs-lookup"><span data-stu-id="96162-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="96162-113">Компонент Lunarcom Translation Recognizer (Script) (Распознаватель перевода Lunarcom — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="96162-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="96162-114">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="96162-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="96162-115">Войдя в игровой режим, вы сможете проверить перевод речи. Для начала нажмите кнопку спутника.</span><span class="sxs-lookup"><span data-stu-id="96162-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="96162-116">Теперь, если на компьютере подключен микрофон, любой сказанный вами текст будет автоматически переводиться на выбранный язык и выводиться на панель терминала:</span><span class="sxs-lookup"><span data-stu-id="96162-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="96162-118">Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.</span><span class="sxs-lookup"><span data-stu-id="96162-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="96162-119">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="96162-119">Congratulations</span></span>

<span data-ttu-id="96162-120">Теперь ваш проект может успешно переводить произносимые слова на несколько разных языков.</span><span class="sxs-lookup"><span data-stu-id="96162-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="96162-121">Запустите приложение на устройстве и убедитесь, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="96162-121">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="96162-122">Следующее руководство: 4. Настройка намерения и распознавание естественного языка</span><span class="sxs-lookup"><span data-stu-id="96162-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
