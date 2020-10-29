---
title: Руководства по использованию службы "Речь" в Azure, часть 4 Настройка намерения и распознавания естественного языка
description: В рамках этого курса вы узнаете, как реализовать пакет SDK службы "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701304"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="d877f-105">4. Настройка намерения и распознавания естественного языка</span><span class="sxs-lookup"><span data-stu-id="d877f-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="d877f-106">В этом руководстве вы изучите распознавание намерений в службе "Речь" Azure.</span><span class="sxs-lookup"><span data-stu-id="d877f-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="d877f-107">Распознавание намерения позволяет реализовать в приложениях речевые команды на основе искусственного интеллекта, благодаря которым пользователи смогут произносить неспециализированные речевые команды для успешной передачи своих намерений системе.</span><span class="sxs-lookup"><span data-stu-id="d877f-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="d877f-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="d877f-108">Objectives</span></span>

* <span data-ttu-id="d877f-109">Узнайте, как настроить на портале LUIS намерения, сущности и речевые фрагменты.</span><span class="sxs-lookup"><span data-stu-id="d877f-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="d877f-110">Узнайте, как реализовать в приложении распознавание намерений и понимание естественного языка.</span><span class="sxs-lookup"><span data-stu-id="d877f-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d877f-111">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="d877f-111">Preparing the scene</span></span>

<span data-ttu-id="d877f-112">В окне Hierarchy (Иерархия) выберите объект **Lunarcom** , а затем в окне Inspector (Инспектор) с помощью кнопки **Добавить компонент** добавьте компонент **Lunarcom Intent Recognizer (Script)** (Распознаватель намерений Lunarcom — скрипт) к объекту Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="d877f-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="d877f-114">В окне проекта перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Заготовки) > **RocketLauncher** , перетащите заготовку **RocketLauncher_Complete** в окно Hierarchy (Иерархия) и поместите ее в приемлемое положение перед камерной, например так:</span><span class="sxs-lookup"><span data-stu-id="d877f-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="d877f-115">для параметра преобразования **Position** (Положение) укажите значения X = 0, Y = 0,4, Z = 1;</span><span class="sxs-lookup"><span data-stu-id="d877f-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="d877f-116">для параметра преобразования **Rotation** (Поворот) укажите значения X = 0, Y = 90, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="d877f-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="d877f-118">В окне Hierarchy (Иерархия) снова выберите объект **Lunarcom** , затем разверните объект **RocketLauncher_Complete** > **Button** и назначьте каждый из дочерних объектов объекта **Button** в соответствующем поле **Lunar Launcher Buttons** :</span><span class="sxs-lookup"><span data-stu-id="d877f-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="d877f-120">Создание ресурса распознавания речи в Azure</span><span class="sxs-lookup"><span data-stu-id="d877f-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="d877f-121">В этом разделе мы создадим ресурс прогнозирования Azure для приложения LUIS (Интеллектуальная служба распознавания речи), создание которого описывается в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d877f-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="d877f-122">Войдите в <a href="https://portal.azure.com" target="_blank">Azure</a> и щелкните **Создать ресурс** .</span><span class="sxs-lookup"><span data-stu-id="d877f-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource** .</span></span> <span data-ttu-id="d877f-123">Теперь найдите и выберите **Распознавание речи** :</span><span class="sxs-lookup"><span data-stu-id="d877f-123">Then search for and select **Language Understanding** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="d877f-125">Нажмите кнопку **Создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="d877f-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="d877f-127">На странице "Создание" щелкните вариант **Прогнозирование** и введите следующие значения:</span><span class="sxs-lookup"><span data-stu-id="d877f-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="d877f-128">Для параметра **Подписка** выберите **Бесплатная пробная версия** , если вы используете пробную версию подписки. Либо выберите любую другую из существующих подписок.</span><span class="sxs-lookup"><span data-stu-id="d877f-128">For **Subscription** , select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="d877f-129">В разделе **Группа ресурсов** щелкните ссылку **Создать** , введите подходящее имя, например *МРКТ-Tutorial* , а затем щелкните **ОК** .</span><span class="sxs-lookup"><span data-stu-id="d877f-129">For the **Resource group** , click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials* , and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="d877f-131">На момент написания этой статьи не нужно было создавать ресурс разработки, так как пробный ключ разработки автоматически создается в LUIS при создании службы LUIS, как описывается в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d877f-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="d877f-132">Если у вас есть другая подходящая группа ресурсов в учетной записи Azure, например, после выполнения инструкций из руководства по [Пространственным привязкам Azure](mr-learning-asa-01.md), можно использовать эту группу ресурсов вместо создания новой.</span><span class="sxs-lookup"><span data-stu-id="d877f-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="d877f-133">На странице "Создание" введите следующие значения:</span><span class="sxs-lookup"><span data-stu-id="d877f-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="d877f-134">В поле **Имя** введите подходящее имя службы, например *MRTK-Tutorials-AzureSpeechServices* .</span><span class="sxs-lookup"><span data-stu-id="d877f-134">For **Name** , enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="d877f-135">В поле **Расположение прогноза** выберите расположение, ближайшее к физическому расположению пользователей приложения, например *(США) Западная часть США* .</span><span class="sxs-lookup"><span data-stu-id="d877f-135">For **Prediction location** , choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="d877f-136">В поле **Ценовая категория прогнозирование** для работы с этим руководством выберите уровень **F0 (5 вызовов в секунду, 10 000 вызовов в месяц).**</span><span class="sxs-lookup"><span data-stu-id="d877f-136">For **Prediction pricing tier** , for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="d877f-138">Затем перейдите на вкладку **Проверка и создание** , просмотрите сведения и нажмите кнопку **Создать** в нижней части страницы, чтобы создать ресурс и новую группу ресурсов, если вы выбрали такой вариант:</span><span class="sxs-lookup"><span data-stu-id="d877f-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="d877f-140">После нажатия кнопки "Создать" вам придется подождать, пока завершится создание службы, что может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="d877f-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="d877f-141">Когда завершится создание ресурса, вы увидите сообщение **Развертывание выполнено** :</span><span class="sxs-lookup"><span data-stu-id="d877f-141">Once the resource creation process is completed, you will see the message **Your deployment is complete** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="d877f-143">Создание Интеллектуальной службы распознавания речи (LUIS)</span><span class="sxs-lookup"><span data-stu-id="d877f-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="d877f-144">В этом разделе описывается, как создать приложение LUIS, настроить и обучить в нем модель прогнозирования и подключить его к ресурсу прогнозирования Azure, который вы создали на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="d877f-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="d877f-145">В частности, вы создадите намерение, которое по речевому фрагменту пользователя о выполнении действия активирует событие Interactable.OnClick() для одной из трех красных кнопок сцены, в зависимости от того, какую из этих кнопок упоминает пользователь.</span><span class="sxs-lookup"><span data-stu-id="d877f-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="d877f-146">Например, если пользователь произносит **go ahead and launch the rocket** (поехали, запускай ракету), приложение прогнозирует, что **go ahead** (поехали) означает выполнение **действия** , и что **нужное** событие Interactable.OnClick() относится к кнопке **launch** (запуск).</span><span class="sxs-lookup"><span data-stu-id="d877f-146">For example, if the user says **go ahead and launch the rocket** , the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="d877f-147">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="d877f-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d877f-148">Создание приложения LUIS.</span><span class="sxs-lookup"><span data-stu-id="d877f-148">Create a LUIS app</span></span>
2. <span data-ttu-id="d877f-149">Создание намерений.</span><span class="sxs-lookup"><span data-stu-id="d877f-149">Create intents</span></span>
3. <span data-ttu-id="d877f-150">Создание примеров речевых фрагментов.</span><span class="sxs-lookup"><span data-stu-id="d877f-150">Create example utterances</span></span>
4. <span data-ttu-id="d877f-151">Создание сущностей.</span><span class="sxs-lookup"><span data-stu-id="d877f-151">Create entities</span></span>
5. <span data-ttu-id="d877f-152">Сопоставление сущностей и примеров речевых фрагментов.</span><span class="sxs-lookup"><span data-stu-id="d877f-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="d877f-153">Обучение, тестирование и публикация приложения.</span><span class="sxs-lookup"><span data-stu-id="d877f-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="d877f-154">Присвоение приложению ресурса прогнозирования Azure.</span><span class="sxs-lookup"><span data-stu-id="d877f-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="d877f-155">1. Создание приложения LUIS</span><span class="sxs-lookup"><span data-stu-id="d877f-155">1. Create a LUIS app</span></span>

<span data-ttu-id="d877f-156">Используя ту же учетную запись, с которой вы создавали ресурс Azure в предыдущем разделе, войдите в службу <a href="https://www.luis.ai" target="_blank">LUIS</a>, выберите страну и подтвердите согласие с условиями использования.</span><span class="sxs-lookup"><span data-stu-id="d877f-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="d877f-157">На следующем этапе в ответ на предложение **привязать учетную запись Azure** выберите вариант **Continue using your trial key** (Продолжить использование ключа пробной версии), чтобы использовать ресурс разработки Azure.</span><span class="sxs-lookup"><span data-stu-id="d877f-157">In the next step, when asked to **Link your Azure account** , choose **Continue using your trial key** , to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="d877f-158">Если вы ранее регистрировались в LUIS и срок вашего ключа пробной версии уже истек, воспользуйтесь документацией [по переходу на использование ключа создания ресурса Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring), чтобы переместить ресурс разработки LUIS в Azure.</span><span class="sxs-lookup"><span data-stu-id="d877f-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="d877f-159">Выполнив вход, перейдите на страницу **Мои приложения** , щелкните **Создать новое приложение** и введите следующие значения во всплывающем окне **Создать новое приложение** .</span><span class="sxs-lookup"><span data-stu-id="d877f-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="d877f-160">В поле **Имя** введите подходящее имя, например *MRTK Tutorials — AzureSpeechServices* .</span><span class="sxs-lookup"><span data-stu-id="d877f-160">For **Name** , enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="d877f-161">В поле **Язык и региональные параметры** выберите **Английский** .</span><span class="sxs-lookup"><span data-stu-id="d877f-161">For **Culture** , select **English**</span></span>
* <span data-ttu-id="d877f-162">В поле **Описание** можно ввести описание (необязательно).</span><span class="sxs-lookup"><span data-stu-id="d877f-162">For **Description** , optionally enter a suitable description</span></span>

<span data-ttu-id="d877f-163">Теперь нажмите кнопку **Готово** , чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="d877f-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="d877f-165">Когда создание приложения завершится, вы автоматически перейдете на страницу **Панель мониторинга** этого приложения.</span><span class="sxs-lookup"><span data-stu-id="d877f-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="d877f-167">2. Создание намерений</span><span class="sxs-lookup"><span data-stu-id="d877f-167">2. Create intents</span></span>

<span data-ttu-id="d877f-168">На странице Dashboard (Панель мониторинга) откройте Build (Сборка) > App Assets (Активы приложения) > **Intents** (Намерения), затем щелкните **Create new intent** (Создать новое намерение) и введите следующие значения во всплывающем окне **Create new intent** (Создать новое намерение):</span><span class="sxs-lookup"><span data-stu-id="d877f-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="d877f-169">В поле **Имя намерения** введите **PressButton** .</span><span class="sxs-lookup"><span data-stu-id="d877f-169">For **Intent name** , enter **PressButton**</span></span>

<span data-ttu-id="d877f-170">Теперь нажмите кнопку **Готово** , чтобы создать намерение.</span><span class="sxs-lookup"><span data-stu-id="d877f-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="d877f-172">В рамках этого руководства проект Unity будет ссылаться на это намерение по имени, вот так: "PressButton".</span><span class="sxs-lookup"><span data-stu-id="d877f-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="d877f-173">Следовательно, крайне важно присвоить намерению точно такое же имя.</span><span class="sxs-lookup"><span data-stu-id="d877f-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="d877f-174">Когда создание намерения завершится, вы автоматически перейдете на страницу этого намерения.</span><span class="sxs-lookup"><span data-stu-id="d877f-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="d877f-176">3. Создание примеров речевых фрагментов</span><span class="sxs-lookup"><span data-stu-id="d877f-176">3. Create example utterances</span></span>

<span data-ttu-id="d877f-177">Для намерения **PressButton** добавьте в список **Example utterance** (Примеры речевых фрагментов) следующие примеры речевых фрагментов:</span><span class="sxs-lookup"><span data-stu-id="d877f-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="d877f-178">activate launch sequence</span><span class="sxs-lookup"><span data-stu-id="d877f-178">activate launch sequence</span></span>
* <span data-ttu-id="d877f-179">show me a placement hint</span><span class="sxs-lookup"><span data-stu-id="d877f-179">show me a placement hint</span></span>
* <span data-ttu-id="d877f-180">initiate the launch sequence</span><span class="sxs-lookup"><span data-stu-id="d877f-180">initiate the launch sequence</span></span>
* <span data-ttu-id="d877f-181">press placement hints button</span><span class="sxs-lookup"><span data-stu-id="d877f-181">press placement hints button</span></span>
* <span data-ttu-id="d877f-182">give me a hint</span><span class="sxs-lookup"><span data-stu-id="d877f-182">give me a hint</span></span>
* <span data-ttu-id="d877f-183">push the launch button</span><span class="sxs-lookup"><span data-stu-id="d877f-183">push the launch button</span></span>
* <span data-ttu-id="d877f-184">i need a hint</span><span class="sxs-lookup"><span data-stu-id="d877f-184">i need a hint</span></span>
* <span data-ttu-id="d877f-185">press the reset button</span><span class="sxs-lookup"><span data-stu-id="d877f-185">press the reset button</span></span>
* <span data-ttu-id="d877f-186">time to reset the experience</span><span class="sxs-lookup"><span data-stu-id="d877f-186">time to reset the experience</span></span>
* <span data-ttu-id="d877f-187">go ahead and launch the rocket</span><span class="sxs-lookup"><span data-stu-id="d877f-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="d877f-188">Когда вы завершите добавление примеров речевых фрагментов, страница намерения PressButton будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d877f-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="d877f-190">В рамках этого руководства в проекте Unity будут использоваться слова hint, hints, reset и launch.</span><span class="sxs-lookup"><span data-stu-id="d877f-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="d877f-191">Следовательно, крайне важно правильно и точно внести эти слова в список.</span><span class="sxs-lookup"><span data-stu-id="d877f-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="d877f-192">4. Создание сущностей</span><span class="sxs-lookup"><span data-stu-id="d877f-192">4. Create entities</span></span>

<span data-ttu-id="d877f-193">На странице намерения PressButton откройте Build (Сборка) > App Assets (Активы приложения) > **Entities** (Сущности), затем щелкните **Create new entity** (Создать новую сущность) и введите следующие значения во всплывающем окне **Create new entity** (Создать новую сущность):</span><span class="sxs-lookup"><span data-stu-id="d877f-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="d877f-194">В поле **Имя сущности** введите **Action** .</span><span class="sxs-lookup"><span data-stu-id="d877f-194">For **Entity name** , enter **Action**</span></span>
* <span data-ttu-id="d877f-195">В поле **Тип сущности** выберите **Простая** .</span><span class="sxs-lookup"><span data-stu-id="d877f-195">For **Entity type** , select **Simple**</span></span>

<span data-ttu-id="d877f-196">Теперь нажмите кнопку **Готово** , чтобы создать сущность.</span><span class="sxs-lookup"><span data-stu-id="d877f-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="d877f-198">**Повторите** описанный выше шаг, чтобы создать еще одну сущность с именем **Target** . Теперь у вас будет две сущности с именами Action и Target:</span><span class="sxs-lookup"><span data-stu-id="d877f-198">**Repeat** the previous step to create another entity named **Target** , so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="d877f-200">В рамках этого руководства проект Unity будет ссылаться на эти сущности по именам, вот так: Action и Target.</span><span class="sxs-lookup"><span data-stu-id="d877f-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="d877f-201">Следовательно, крайне важно присвоить точно такие же имена.</span><span class="sxs-lookup"><span data-stu-id="d877f-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="d877f-202">5. Сопоставление сущностей и примеров речевых фрагментов</span><span class="sxs-lookup"><span data-stu-id="d877f-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="d877f-203">Со страницы "Сущности" вернитесь на страницу намерения **PressButton** .</span><span class="sxs-lookup"><span data-stu-id="d877f-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="d877f-204">На странице намерения PressButton щелкните слово **go** , а затем слово **ahead** , и выберите **Action (Простая)** из контекстного всплывающего меню, чтобы обозначить **go ahead** как значение сущности **Action** :</span><span class="sxs-lookup"><span data-stu-id="d877f-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead** , and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="d877f-206">Теперь речевой фрагмент **go ahead** определен как значение сущности **Action** .</span><span class="sxs-lookup"><span data-stu-id="d877f-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="d877f-207">Если вы наведете курсор мыши на имя сущности Action, вы увидите сопоставленное значение сущности Action:</span><span class="sxs-lookup"><span data-stu-id="d877f-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="d877f-209">Красная черта под меткой на изображении выше обозначает, что это значение сущности еще не было спрогнозировано, этим вопросом мы займемся на этапе обучения модели, описанном в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d877f-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="d877f-210">Теперь щелкните слово **launch** и выберите **Target (Простая)** из контекстного всплывающего меню, чтобы обозначить **launch** как значение сущности **Target** :</span><span class="sxs-lookup"><span data-stu-id="d877f-210">Next, click on the word **launch** , and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="d877f-212">Теперь слово **launch** определено как значение сущности **Target** .</span><span class="sxs-lookup"><span data-stu-id="d877f-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="d877f-213">Если вы наведете курсор мыши на имя сущности Target, вы увидите сопоставленное значение сущности Target:</span><span class="sxs-lookup"><span data-stu-id="d877f-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="d877f-215">Теперь для намерения PressButton пример речевого фрагмента "go ahead and launch the rocket" будет спрогнозирован следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d877f-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="d877f-216">Намерение: PressButton.</span><span class="sxs-lookup"><span data-stu-id="d877f-216">Intent: PressButton</span></span>
* <span data-ttu-id="d877f-217">Сущность Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="d877f-217">Action entity: go ahead</span></span>
* <span data-ttu-id="d877f-218">Сущность Target: launch</span><span class="sxs-lookup"><span data-stu-id="d877f-218">Target entity: launch</span></span>

<span data-ttu-id="d877f-219">**Повторите** описанный выше процесс из двух шагов, чтобы присвоить метки сущностей Action и Target каждому примеру речевых фрагментов, обязательно добавив следующие слова в качестве сущностей **Target** :</span><span class="sxs-lookup"><span data-stu-id="d877f-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="d877f-220">**hint** (обозначает кнопку HintsButton в проекте Unity);</span><span class="sxs-lookup"><span data-stu-id="d877f-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="d877f-221">**hints** (обозначает кнопку HintsButton в проекте Unity);</span><span class="sxs-lookup"><span data-stu-id="d877f-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="d877f-222">**reset** (обозначает кнопку ResetButton в проекте Unity);</span><span class="sxs-lookup"><span data-stu-id="d877f-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="d877f-223">**launch** (обозначает кнопку LaunchButton в проекте Unity).</span><span class="sxs-lookup"><span data-stu-id="d877f-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="d877f-224">Когда вы завершите пометку примеров речевых фрагментов, страница намерения PressButton будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d877f-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="d877f-226">Есть и другой метод еще раз проверить, все ли данные внесены верно: щелкните меню **Параметры просмотра** и переключите представление на **Отобразить значения сущностей** .</span><span class="sxs-lookup"><span data-stu-id="d877f-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="d877f-228">Теперь, включив отображение значений сущностей, вы можете навести курсор мыши на любое из помеченных слов или речевых фрагментов, чтобы быстро увидеть сопоставленное имя сущности:</span><span class="sxs-lookup"><span data-stu-id="d877f-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="d877f-230">6. Обучение, тестирование и публикация приложения</span><span class="sxs-lookup"><span data-stu-id="d877f-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="d877f-231">Чтобы обучить приложение, щелкните кнопку **Обучить** и дождитесь завершения процесса обучения:</span><span class="sxs-lookup"><span data-stu-id="d877f-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="d877f-233">Как видно на изображении выше, красные линии под метками исчезли, а значит, все эти значения сущностей теперь прогнозируются.</span><span class="sxs-lookup"><span data-stu-id="d877f-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="d877f-234">Также вы можете обратить внимание на значок состояния слева от кнопки "Обучение", который теперь сменил цвет с красного на зеленый.</span><span class="sxs-lookup"><span data-stu-id="d877f-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="d877f-235">Когда завершится процесс обучения, щелкните кнопку **Тест** и введите фразу **go ahead and launch the rocket** , а затем нажмите клавишу ВВОД:</span><span class="sxs-lookup"><span data-stu-id="d877f-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="d877f-237">Когда завершится обработка тестового речевого фрагмента, щелкните **Проверить** и оцените результат:</span><span class="sxs-lookup"><span data-stu-id="d877f-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="d877f-238">Намерение: PressButton (с достоверностью 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="d877f-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="d877f-239">Сущность Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="d877f-239">Action entity: go ahead</span></span>
* <span data-ttu-id="d877f-240">Сущность Target: launch</span><span class="sxs-lookup"><span data-stu-id="d877f-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="d877f-242">Чтобы опубликовать приложение, нажмите кнопку **Опубликовать** справа вверху, затем во всплывающем окне **Choose your publishing slot and settings** (Выберите слот и параметры публикации) выберите пункт **Production** (Рабочий) и нажмите кнопку **Опубликовать** .</span><span class="sxs-lookup"><span data-stu-id="d877f-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="d877f-244">Дождитесь окончания процесса публикации.</span><span class="sxs-lookup"><span data-stu-id="d877f-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="d877f-246">7. Присвоение приложению ресурса прогнозирования Azure</span><span class="sxs-lookup"><span data-stu-id="d877f-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="d877f-247">Откройте страниц "Управление" > "Параметры приложения" > **Ресурсы Azure** :</span><span class="sxs-lookup"><span data-stu-id="d877f-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="d877f-249">На странице "Ресурсы Azure" нажмите кнопку **Add prediction resource** (Добавить ресурс прогнозирования) и выберите следующие значения во всплывающем окне **Assign a resource to your app** (Назначьте ресурс приложению).</span><span class="sxs-lookup"><span data-stu-id="d877f-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="d877f-250">В поле **Имя клиента** выберите нужное имя клиента.</span><span class="sxs-lookup"><span data-stu-id="d877f-250">For **Tenant name** , select your tenant name</span></span>
* <span data-ttu-id="d877f-251">В поле **Имя подписки** выберите ту же подписку, которую вы использовали на этапе [Создание ресурса распознавания речи в Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource).</span><span class="sxs-lookup"><span data-stu-id="d877f-251">For **Subscription Name** , select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="d877f-252">В поле **Имя ресурса LUIS** выберите тот ресурс прогнозирования, который вы создали на этапе [Создание ресурса распознавания речи в Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource).</span><span class="sxs-lookup"><span data-stu-id="d877f-252">For **LUIS resource name** , select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="d877f-253">Теперь нажмите кнопку **Назначить ресурс** , чтобы назначить ресурс прогнозирования Azure приложению:</span><span class="sxs-lookup"><span data-stu-id="d877f-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="d877f-255">Когда завершится назначение ресурса, страница "Ресурсы Azure" будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d877f-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="d877f-257">Подключение проекта Unity к приложению LUIS</span><span class="sxs-lookup"><span data-stu-id="d877f-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="d877f-258">На странице "Управление" > "Параметры приложения" > **Ресурсы Azure** щелкните значок **копирования** , чтобы скопировать значение в поле **Пример запроса** :</span><span class="sxs-lookup"><span data-stu-id="d877f-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="d877f-260">Вернитесь в проект Unity, в окне Hierarchy (Иерархия) выберите объект **Lunarcom** , а затем в окне Inspector (Инспектор) найдите компонент **Lunarcom Intent Recognizer (Script)** (Распознаватель намерений Lunarcom — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="d877f-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d877f-261">В поле **LUIS Endpoint** (Конечная точка LUIS) вставьте значение **примера запроса** , которое вы скопировали на предыдущем шаге:</span><span class="sxs-lookup"><span data-stu-id="d877f-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="d877f-263">Тестирование и улучшение распознавания намерений</span><span class="sxs-lookup"><span data-stu-id="d877f-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="d877f-264">Чтобы применить распознавание намерений прямо в редакторе Unity, необходимо разрешить использовать диктовку на компьютере разработке.</span><span class="sxs-lookup"><span data-stu-id="d877f-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="d877f-265">Чтобы проверить эту настройку, откройте **Параметры** Windows, выберите **Конфиденциальность** > **Речь** и убедитесь, что здесь включен параметр **Распознавание речи в сети** :</span><span class="sxs-lookup"><span data-stu-id="d877f-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="d877f-267">Теперь, войдя в игровой режим, вы сможете проверить распознавание намерений. Для начала нажмите кнопку ракеты.</span><span class="sxs-lookup"><span data-stu-id="d877f-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="d877f-268">Если к вашему компьютеру подключен микрофон, при произнесении первого примера речевого фрагмента **go ahead and launch the rocket** объект LunarModule будет запущен в космос:</span><span class="sxs-lookup"><span data-stu-id="d877f-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket** , you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="d877f-270">Проверьте все **примеры речевых фрагментов** , потом попробуйте **немного изменять эти примеры** , а также произнесите несколько **произвольных речевых фрагментов** .</span><span class="sxs-lookup"><span data-stu-id="d877f-270">Try all the **example utterances** , then some **variation of the example utterances** , as well as, a few **random utterances** .</span></span>

<span data-ttu-id="d877f-271">Теперь вернитесь в <a href="https://www.luis.ai" target="_blank">LUIS</a> и откройте меню "Сборка" > "Improve app performance" (Повысить производительность приложения) > **Review endpoint utterances** (Проверить речевые фрагменты конечной точки), с помощью **переключателя** перейдите из представления сущностей в **представление токенов** и изучите полученные речевые фрагменты.</span><span class="sxs-lookup"><span data-stu-id="d877f-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View** , and then review the utterances:</span></span>

* <span data-ttu-id="d877f-272">В столбце **Utterance** (Речевой фрагмент) вы можете изменять и (или) удалять присвоенные метки, чтобы они лучше соответствовали вашим намерениям.</span><span class="sxs-lookup"><span data-stu-id="d877f-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="d877f-273">В столбце **Aligned intent** (Сопоставленное намерение) убедитесь, что намерение выбрано правильно.</span><span class="sxs-lookup"><span data-stu-id="d877f-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="d877f-274">В столбце **Добавить/Удалить** можно щелкнуть зеленую галочку, чтобы добавить новый речевой фрагмент, или красный крестик, чтобы удалить речевой фрагмент.</span><span class="sxs-lookup"><span data-stu-id="d877f-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="d877f-275">Завершив изучение речевых фрагментов в удобном для вас темпе, нажмите кнопку **Обучение** , чтобы повторно обучить модель, а затем кнопку **Опубликовать** , чтобы еще раз опубликовать обновленное приложение:</span><span class="sxs-lookup"><span data-stu-id="d877f-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="d877f-277">Если речевой фрагмент конечной точки не соответствует намерению PressButton и вы хотите, чтобы модель знала об отсутствии намерений в этом речевом фрагменте, измените значение сопоставленного намерения на "Нет".</span><span class="sxs-lookup"><span data-stu-id="d877f-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="d877f-278">**Повторите** этот процесс произвольное количество раз, которое вы сочтете разумным для улучшения модели приложения.</span><span class="sxs-lookup"><span data-stu-id="d877f-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d877f-279">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d877f-279">Congratulations</span></span>

<span data-ttu-id="d877f-280">Теперь в вашем проекте реализовано понимание речевых команд, что позволит приложению распознавать намерения пользователей даже без точного совпадения с сохраненной командой.</span><span class="sxs-lookup"><span data-stu-id="d877f-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="d877f-281">Запустите приложение на устройстве и убедитесь, что все работает правильно.</span><span class="sxs-lookup"><span data-stu-id="d877f-281">Run the application on your device to ensure the feature is working properly.</span></span>
