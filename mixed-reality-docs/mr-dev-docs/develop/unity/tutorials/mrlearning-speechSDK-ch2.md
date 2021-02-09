---
title: Добавление автономного режима для преобразования речи в текст в локальной среде
description: Пройдите этот курс, чтобы узнать, как добавить автономный режим для локального перевода речи в текст в приложениях смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, распознавание речи, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590156"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="54f4c-104">2. Добавление автономного режима для преобразования речи в текст в локальной среде</span><span class="sxs-lookup"><span data-stu-id="54f4c-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="54f4c-105">В этом руководстве вы добавите возможность выполнения команд с помощью распознавания речи Azure, что позволит выполнять действия по определенным в приложении словам или фразам.</span><span class="sxs-lookup"><span data-stu-id="54f4c-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="54f4c-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="54f4c-106">Objectives</span></span>

* <span data-ttu-id="54f4c-107">Изучение возможностей по применению распознавания речи Azure для выполнения команд</span><span class="sxs-lookup"><span data-stu-id="54f4c-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="54f4c-108">Инструкции</span><span class="sxs-lookup"><span data-stu-id="54f4c-108">Instructions</span></span>

<span data-ttu-id="54f4c-109">В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Wake Word Recognizer (Script)** (Распознаватель слова для пробуждения Lunarcom — скрипт) к объекту Lunarcom и настройте его, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="54f4c-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="54f4c-110">В поле **Wake Word** (Слово для пробуждения) введите подходящую фразу, например _Activate terminal_ (Активировать терминал).</span><span class="sxs-lookup"><span data-stu-id="54f4c-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="54f4c-111">В поле **Dismiss Word** (Слово для отключения) введите подходящую фразу, например _Dismiss terminal_ (Отключить терминал).</span><span class="sxs-lookup"><span data-stu-id="54f4c-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Редактор Unity с выделенным компонентом скрипта Lunarcom Wake Word Recognizer](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="54f4c-113">Компонент Lunarcom Wake Word Recognizer (Script) (Распознаватель слова для пробуждения Lunarcom — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="54f4c-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="54f4c-114">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="54f4c-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="54f4c-115">Если теперь вы входите в игровой режим, как описано в предыдущем руководстве, панель терминала будет по умолчанию включена, но вы сможете ее отключить, произнеся настроенное слово для отключения **Dismiss terminal**:</span><span class="sxs-lookup"><span data-stu-id="54f4c-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Редактор Unity в режиме воспроизведения с используемой функцией распознавания речи](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="54f4c-117">Чтобы снова включить терминал, произнесите слово для пробуждения **Activate terminal**:</span><span class="sxs-lookup"><span data-stu-id="54f4c-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Редактор Unity в режиме воспроизведения с активным терминалом](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="54f4c-119">Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.</span><span class="sxs-lookup"><span data-stu-id="54f4c-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="54f4c-120">Если вы ожидаете, что подключение к Azure часто будет невозможным, речевые команды можно реализовать с помощью МRТК по инструкциям из статьи [Использование голосовых команд](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="54f4c-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54f4c-121">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="54f4c-121">Congratulations</span></span>

<span data-ttu-id="54f4c-122">Вы успешно реализовали функцию речевых команд на платформе Azure.</span><span class="sxs-lookup"><span data-stu-id="54f4c-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="54f4c-123">Запустите приложение на устройстве и убедитесь, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="54f4c-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="54f4c-124">В следующем учебнике вы узнаете, как переводить текст с помощью распознавания речи Azure.</span><span class="sxs-lookup"><span data-stu-id="54f4c-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54f4c-125">Следующее руководство: 3. Добавление компонента перевода речи Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="54f4c-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
