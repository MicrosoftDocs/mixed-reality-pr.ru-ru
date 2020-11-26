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
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="54ee9-105">2. Использование функции распознавания речи для выполнения команд</span><span class="sxs-lookup"><span data-stu-id="54ee9-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="54ee9-106">В этом руководстве вы добавите возможность выполнения команд с помощью распознавания речи Azure, что позволит выполнять действия по определенным в приложении словам или фразам.</span><span class="sxs-lookup"><span data-stu-id="54ee9-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="54ee9-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="54ee9-107">Objectives</span></span>

* <span data-ttu-id="54ee9-108">Изучение возможностей по применению распознавания речи Azure для выполнения команд</span><span class="sxs-lookup"><span data-stu-id="54ee9-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="54ee9-109">Инструкции</span><span class="sxs-lookup"><span data-stu-id="54ee9-109">Instructions</span></span>

<span data-ttu-id="54ee9-110">В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Wake Word Recognizer (Script)** (Распознаватель слова для пробуждения Lunarcom — скрипт) к объекту Lunarcom и настройте его, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="54ee9-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="54ee9-111">В поле **Wake Word** (Слово для пробуждения) введите подходящую фразу, например _Activate terminal_ (Активировать терминал).</span><span class="sxs-lookup"><span data-stu-id="54ee9-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="54ee9-112">В поле **Dismiss Word** (Слово для отключения) введите подходящую фразу, например _Dismiss terminal_ (Отключить терминал).</span><span class="sxs-lookup"><span data-stu-id="54ee9-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="54ee9-114">Компонент Lunarcom Wake Word Recognizer (Script) (Распознаватель слова для пробуждения Lunarcom — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="54ee9-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="54ee9-115">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="54ee9-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="54ee9-116">Если теперь вы входите в игровой режим, как описано в предыдущем руководстве, панель терминала будет по умолчанию включена, но вы сможете ее отключить, произнеся настроенное слово для отключения **Dismiss terminal**:</span><span class="sxs-lookup"><span data-stu-id="54ee9-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="54ee9-118">Чтобы снова включить терминал, произнесите слово для пробуждения **Activate terminal**:</span><span class="sxs-lookup"><span data-stu-id="54ee9-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="54ee9-120">Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.</span><span class="sxs-lookup"><span data-stu-id="54ee9-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="54ee9-121">Если вы ожидаете, что подключение к Azure часто будет невозможным, речевые команды можно реализовать с помощью МRТК по инструкциям из статьи [Использование голосовых команд](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="54ee9-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54ee9-122">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="54ee9-122">Congratulations</span></span>

<span data-ttu-id="54ee9-123">Вы успешно реализовали функцию речевых команд на платформе Azure.</span><span class="sxs-lookup"><span data-stu-id="54ee9-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="54ee9-124">Запустите приложение на устройстве и убедитесь, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="54ee9-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="54ee9-125">В следующем учебнике вы узнаете, как переводить текст с помощью распознавания речи Azure.</span><span class="sxs-lookup"><span data-stu-id="54ee9-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54ee9-126">Следующее руководство: 3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="54ee9-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
