---
title: Интеграция Службы Azure Bot c помощью LUIS
description: Пройдите этот курс, чтобы узнать, как реализовать Службу Azure Bot и возможность распознавания естественного языка в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, HoloLens 2, служба Azure Bot, LUIS, естественный язык, чат-бот, облачные службы Azure, Пользовательское визуальное распознавание Azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 70d136467bc677c028614429e6e197ce25b30327
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008254"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="4f8fc-104">5. Интеграция Службы Azure Bot</span><span class="sxs-lookup"><span data-stu-id="4f8fc-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="4f8fc-105">Из этого учебника вы узнаете, как использовать **Службу Azure Bot** в демонстрационном приложении **HoloLens 2**, чтобы добавить возможность распознавания речи (LUIS) и разрешить боту помогать пользователю во время поиска **отслеживаемых объектов**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="4f8fc-106">Этот учебник состоит из двух частей. В первой части вы создадите бота с помощью приложения [Bot Composer](https://docs.microsoft.com/composer/introduction) в качестве решения без кода и выполните краткий обзор Функции Azure, которая предоставляет боту необходимые данные.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="4f8fc-107">Во второй части вы будете использовать компонент **BotManager (script)** (Диспетчер ботов — скрипт) в проекте Unity для использования размещенной Службы Bot.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="4f8fc-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="4f8fc-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="4f8fc-109">Часть 1</span><span class="sxs-lookup"><span data-stu-id="4f8fc-109">Part 1</span></span>

* <span data-ttu-id="4f8fc-110">Получите основные сведения о Службе Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="4f8fc-111">Узнайте, как создать бота с помощью приложения Bot Composer.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="4f8fc-112">Узнайте, как использовать функцию Azure для предоставления данных из службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="4f8fc-113">Часть 2</span><span class="sxs-lookup"><span data-stu-id="4f8fc-113">Part 2</span></span>

* <span data-ttu-id="4f8fc-114">Узнайте, как настроить сцену для использования Службы Azure Bot в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="4f8fc-115">Узнайте, как настроить и найти объекты с помощью бота.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="4f8fc-116">Общие сведения о Службе Azure Bot</span><span class="sxs-lookup"><span data-stu-id="4f8fc-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="4f8fc-117">**Служба Azure Bot** позволяет разработчикам создавать интеллектуальных ботов, которые могут поддерживать естественное общение с пользователями благодаря **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="4f8fc-118">Чат-бот — это отличный способ расширить возможности взаимодействия пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="4f8fc-119">Бот можно использовать в качестве базы знаний с помощью [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) для поддержания сложного разговора с использованием службы [распознавания речи (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="4f8fc-120">Дополнительные сведения о [Службе Azure Bot](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4f8fc-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="4f8fc-121">Часть 1. Создание бота</span><span class="sxs-lookup"><span data-stu-id="4f8fc-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="4f8fc-122">Прежде чем использовать бота в приложении Unity, его необходимо разработать, предоставить ему данные и разместить в **Azure**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="4f8fc-123">Цель бота — оценить количество *отслеживаемых объектов*, хранимых в базе данных, найти *отслеживаемый объект* по его имени и сообщить пользователю базовую информацию о нем.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="4f8fc-124">Краткий обзор функции отслеживаемых объектов в Azure</span><span class="sxs-lookup"><span data-stu-id="4f8fc-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="4f8fc-125">Вы собираетесь приступить к созданию бота, но чтобы сделать его полезным, необходимо предоставить ресурс, из которого он может извлекать данные.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="4f8fc-126">Так как *бот* сможет подсчитать количество **отслеживаемых объектов**, найти конкретные объекты по имени и сообщить подробности, вы будете использовать простую Функцию Azure с доступом к **хранилищу таблиц Azure**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="4f8fc-127">Скачайте проект функции Azure отслеживаемых объектов: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip). Затем извлеките его на свой жесткий диск.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="4f8fc-128">Эта функция Azure может выполнять действия **подсчета** и **поиска**, которые можно вызвать с помощью базовых вызовов *HTTP* *GET*.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="4f8fc-129">Код можно проверить в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="4f8fc-130">Дополнительные сведения о [функциях Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="4f8fc-131">Функция **Count** запрашивает из **хранилища таблиц** все **отслеживаемые объекты**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="4f8fc-132">С другой стороны, функция **Find** принимает параметр запроса *имени* из запроса *GET* и запрашивает **хранилище таблиц** для сопоставления **отслеживаемых объектов** и возвращает DTO в виде JSON.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="4f8fc-133">Вы можете развернуть эту **Функцию Azure** непосредственно из **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="4f8fc-134">Здесь вы найдете все сведения о [развертывании Функции Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-134">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span></span>

<span data-ttu-id="4f8fc-135">После завершения развертывания на **портале Azure** откройте соответствующий ресурс и выберите вкладку **Конфигурация** в разделе *Параметры*.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="4f8fc-136">На вкладке **Параметры приложения** необходимо предоставить *строку подключения* для **хранилища Azure**, где хранятся **отслеживаемые объекты**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="4f8fc-137">Щелкните элемент **Новый параметр приложения** и в качестве имени введите: **AzureStorageConnectionString**, а в качестве значения предоставьте правильную *строку подключения*.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="4f8fc-138">После этого нажмите на кнопку **Сохранить**, и **Функция Azure** будет готова к размещению *бота* на сервере, который вы создадите далее.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="4f8fc-139">Создание чат-бота</span><span class="sxs-lookup"><span data-stu-id="4f8fc-139">Creating a conversation Bot</span></span>

<span data-ttu-id="4f8fc-140">Существует несколько способов разработки чат-бота на основе платформы Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="4f8fc-141">На этом уроке вы будете использовать классическое приложение [Bot Framework Composer](https://docs.microsoft.com/composer/), которое является визуальным конструктором и идеально подходит для быстрой разработки.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-141">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="4f8fc-142">Последние выпуски можно скачать из [репозитория GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="4f8fc-143">Он доступен для Windows, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="4f8fc-144">После установки **Bot Framework Composer** запустите приложение, и вы увидите этот интерфейс:</span><span class="sxs-lookup"><span data-stu-id="4f8fc-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Bot Framework Composer — домашняя страница](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="4f8fc-146">Мы подготовили проект Bot Composer, который предоставляет необходимые диалоги и триггеры для работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="4f8fc-147">Скачайте проект Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip). Затем извлеките его на свой жесткий диск.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="4f8fc-148">На верхней панели нажмите кнопку **Open** (Открыть) и выберите скачанный проект Bot Framework с именем **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="4f8fc-149">После полной загрузки проекта вы увидите, что проект готов.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-149">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer с открытым проектом TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="4f8fc-151">Обратите внимание на **панель диалогов** в левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="4f8fc-152">Здесь расположено диалоговое окно **TrackedObjectsBot**, в котором можно увидеть несколько **триггеров**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="4f8fc-153">Дополнительные сведения об [основных понятиях Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-153">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="4f8fc-154">Эти триггеры выполняют следующие действия:</span><span class="sxs-lookup"><span data-stu-id="4f8fc-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="4f8fc-155">Приветствие</span><span class="sxs-lookup"><span data-stu-id="4f8fc-155">Greeting</span></span>

<span data-ttu-id="4f8fc-156">Это точка входа *чат-бота*, когда какой-либо *пользователь* инициирует диалог.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Диалоговое окно проекта TrackedObjectsBot с возможностью выбора триггера — приветствие](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="4f8fc-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="4f8fc-158">AskingForCount</span></span>

<span data-ttu-id="4f8fc-159">Это диалоговое окно активируется, когда *пользователь* запрашивает подсчет всех **отслеживаемых объектов**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="4f8fc-160">Ниже приведены триггерные фразы:</span><span class="sxs-lookup"><span data-stu-id="4f8fc-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="4f8fc-161">count me all (подсчитать все);</span><span class="sxs-lookup"><span data-stu-id="4f8fc-161">count me all</span></span>
>* <span data-ttu-id="4f8fc-162">how many are stored (количество хранимых).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-162">how many are stored</span></span>

![Диалоговое окно проекта TrackedObjectsBot — AskForCount](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="4f8fc-164">Благодаря [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) *пользователю* не нужно запрашивать фразы естественным для *пользователя* способом.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-164">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="4f8fc-165">В этом диалоговом окне *бот* также будет обращаться к Функции Azure **Count**. Дополнительные сведения об этом см. ниже.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="4f8fc-166">Неизвестная цель</span><span class="sxs-lookup"><span data-stu-id="4f8fc-166">Unknown Intent</span></span>

<span data-ttu-id="4f8fc-167">Это диалоговое окно запускается, если входные данные *пользователя* не соответствуют никаким другим условиям триггера, и просит пользователя повторно задать свой вопрос.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Диалоговое окно проекта TrackedObjectsBot с возможностью выбора триггера — неизвестное намерение](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="4f8fc-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="4f8fc-169">FindEntity</span></span>

<span data-ttu-id="4f8fc-170">Последнее диалоговое окно более сложное. Здесь приведены функции ветвления и хранения данных в памяти *ботов*.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="4f8fc-171">Оно запрашивает у пользователя *имя* **отслеживаемого объекта**, о котором необходимо узнать больше информации, выполняет запрос Функции Azure **Find** и использует ответ для продолжения разговора.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Диалоговое окно проекта TrackedObjectsBot с возможностью выбора триггера — FindEntity](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="4f8fc-173">Если **отслеживаемый объект** не найден, пользователь получает уведомление, а разговор завершается.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="4f8fc-174">Когда рассматриваемый **отслеживаемый объект** будет найден, загрузчик проверит, какие свойства доступны, и сообщит о них.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="4f8fc-175">Адаптация бота</span><span class="sxs-lookup"><span data-stu-id="4f8fc-175">Adapting the Bot</span></span>

<span data-ttu-id="4f8fc-176">Триггерам **AskingForCount** и **FindEntity** необходимо взаимодействовать с серверной частью. Это означает, что необходимо добавить правильный URL-адрес **Функции Azure**, развернутой ранее.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="4f8fc-177">На панели диалоговых окон щелкните **AskingForCount** и выберите действие *Send an HTTP request* (Отправить HTTP-запрос). Здесь можно увидеть поле **URL**, в которое необходимо ввести правильный URL-адрес конечной точки функции **Count**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Диалоговое окно AskingForCount проекта TrackedObjectsBot с возможностью выбора триггера — конфигурация конечной точки](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="4f8fc-179">Наконец, найдите триггер **FindEntity** и действие *Send an HTTP request* (Отправить HTTP-запрос). В поле **URL** замените URL-адрес конечной точкой функции **Count**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Диалоговое окно FindEntity проекта TrackedObjectsBot с возможностью выбора триггера — конфигурация конечной точки](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="4f8fc-181">Теперь все готово к развертыванию бота.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="4f8fc-182">Так как у вас установлена программа Bot Framework Composer, его можно опубликовать непосредственно из нее.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="4f8fc-183">Дополнительные сведения о [публикации бота с помощью программы Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-183">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="4f8fc-184">Вы можете поэкспериментировать с ботом, добавив дополнительные триггерные фразы, новые ответы или ветвление диалога.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="4f8fc-185">Часть 2. Размещение всех элементов в Unity</span><span class="sxs-lookup"><span data-stu-id="4f8fc-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="4f8fc-186">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="4f8fc-186">Preparing the scene</span></span>

<span data-ttu-id="4f8fc-187">В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Окно проекта Unity с выбранной заготовкой ChatBotManager](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="4f8fc-189">После этого переместите заготовку **ChatBotManager** в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="4f8fc-190">Добавив ChatBotManager в сцену, щелкните компонент **Chat Bot Manager** (Диспетчер чат-ботов).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="4f8fc-191">В окне Inspector (Инспектор) вы увидите, что имеется пустое поле **Direct Line Secret Key** (Секретный ключ прямой линии), которое необходимо заполнить.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="4f8fc-192">Вы можете получить *секретный ключ* на портале Azure, выполнив поиск ресурса типа **регистрации каналов ботов**, созданного в первой части этого учебника.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity с добавленной заготовкой ChatBotManager](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="4f8fc-194">Теперь вы подключите объект **ChatBotManager** с компонентом **ChatBotController**, присоединенным к объекту **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="4f8fc-195">В окне Hierarchy (Иерархия) выберите **ChatBotPanel**, и вы увидите пустое поле **Chat Bot Manager** (Диспетчер чат-ботов). Перетащите объект **ChatBotManager** в пустое поле **Chat Bot Manager** (Диспетчер чат-ботов).</span><span class="sxs-lookup"><span data-stu-id="4f8fc-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity с настроенным объектом ChatBotPanel](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="4f8fc-197">Далее необходимо открыть объект **ChatBotPanel**, чтобы пользователь мог взаимодействовать с ним.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="4f8fc-198">В окне Scene (Сцена) вы могли заметить, что в объекте **MainMenu** есть кнопка *Chat Bot* (Чат-бот), которая будет использоваться для решения этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="4f8fc-199">В окне Hierarchy (Иерархия) откройте папку **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** и найдите в окне Inspector (Инспектор) скрипт *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="4f8fc-200">Там вы увидите пустой слот в функции обратного вызова события **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="4f8fc-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="4f8fc-201">Перетащите **ChatBotPanel** в область событий, из раскрывающегося списка выберите *GameObject*, а затем в подменю выберите *SetActive (bool)* (SetActive (логическое)) и установите флажок.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity с настроенным объектом ButtonChatBot](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="4f8fc-203">Теперь чат-бот можно запустить из главного меню, а сцена готова к использованию.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="4f8fc-204">Тестирование чат-бота</span><span class="sxs-lookup"><span data-stu-id="4f8fc-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="4f8fc-205">Запрос количества отслеживаемых объектов</span><span class="sxs-lookup"><span data-stu-id="4f8fc-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="4f8fc-206">Сначала вы проверите, сколько **отслеживаемых объектов** хранится в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="4f8fc-207">На этот раз необходимо запустить приложение из HoloLens 2, так как такие службы, как *преобразование текста в речь*, могут быть недоступны в вашей системе.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="4f8fc-208">Запустите приложение в HoloLens 2 и нажмите кнопку *Chat Bot* (Чат-бот) рядом с главным меню.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="4f8fc-209">Чат-бот поприветствует вас. Спросите, **сколько имеется объектов?**</span><span class="sxs-lookup"><span data-stu-id="4f8fc-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="4f8fc-210">Он должен сообщить их количество и завершить диалог.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="4f8fc-211">Запрос отслеживаемого объекта</span><span class="sxs-lookup"><span data-stu-id="4f8fc-211">Asking about a tracked object</span></span>

<span data-ttu-id="4f8fc-212">Теперь запустите приложение еще раз и попросите **найти отслеживаемый объект**. Чат-бот запросит название, на которое следует ответить, например введите "автомобиль", или имя другого *отслеживаемого объекта*, который есть в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="4f8fc-213">Бот отобразит его описание и сведения о наличии пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="4f8fc-214">Попробуйте запросить **отслеживаемые объекты**, которые не существуют в базе, и посмотрите на ответ бота.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4f8fc-215">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="4f8fc-215">Congratulations</span></span>

<span data-ttu-id="4f8fc-216">Из этого учебника вы узнали, как можно использовать платформу Azure Bot Framework для взаимодействия с приложением с помощью естественного языка.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="4f8fc-217">Вы узнали, как разрабатывать собственных ботов и как они работают.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="4f8fc-218">Заключение</span><span class="sxs-lookup"><span data-stu-id="4f8fc-218">Conclusion</span></span>

<span data-ttu-id="4f8fc-219">В рамках этой серии учебников вы узнали, как **облачные службы Azure** применяют новые интересные функции к вашему приложению.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="4f8fc-220">Теперь вы можете хранить данные и изображения в облаке **хранилища Azure**, использовать **Пользовательское визуальное распознавание Azure** для связывания изображений и обучения модели, передавать объекты в локальный контекст с помощью **Пространственных привязок Azure** и реализовать **Azure Bot Framework на платформе LUIS**, чтобы добавить чат-бота в новый и естественный шаблон взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4f8fc-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
