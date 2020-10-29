---
title: Пространственные привязки Azure в Unreal
description: Общие сведения о создании пространственных привязок Azure в движке Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, разработка azure, пространственные привязки, смешанная реальность, разработка, функции, новый проект, эмулятор, документация, руководства, голограммы, разработка игр
ms.openlocfilehash: 5f1f7ef0cb55714ed87bbc3e827d77d3e2694084
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701231"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="a8178-104">Пространственные привязки Azure в Unreal</span><span class="sxs-lookup"><span data-stu-id="a8178-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a8178-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a8178-105">Overview</span></span>

<span data-ttu-id="a8178-106">Пространственные привязки Azure — это служба Microsoft Mixed Reality, позволяющая устройствам дополненной реальности обнаруживать, публиковать и сохранять точки привязок в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="a8178-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="a8178-107">В документации ниже приведены инструкции по интеграции службы "Пространственные привязки Azure" в проект Unreal.</span><span class="sxs-lookup"><span data-stu-id="a8178-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="a8178-108">Дополнительные сведения см. на странице [службы "Пространственные привязки Azure"](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="a8178-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8178-109">Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке.</span><span class="sxs-lookup"><span data-stu-id="a8178-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="a8178-110">Если вам нужно хранить привязки локально на устройстве, соответствующие инструкции приведены в документе по [локальным пространственным привязкам](unreal-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="a8178-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="a8178-111">Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.</span><span class="sxs-lookup"><span data-stu-id="a8178-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8178-112">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="a8178-112">Prerequisites</span></span>

<span data-ttu-id="a8178-113">Для работы с этим руководством вам потребуются:</span><span class="sxs-lookup"><span data-stu-id="a8178-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="a8178-114">[Unreal 4.25](https://www.unrealengine.com/get-now) или более поздней версии;</span><span class="sxs-lookup"><span data-stu-id="a8178-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="a8178-115">настройка [проекта HoloLens 2](tutorials/unreal-uxt-ch1.md) в Unreal;</span><span class="sxs-lookup"><span data-stu-id="a8178-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="a8178-116">ознакомление с [обзором пространственных привязок Azure](https://docs.microsoft.com/azure/spatial-anchors/overview);</span><span class="sxs-lookup"><span data-stu-id="a8178-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="a8178-117">базовые знания C++ и Unreal.</span><span class="sxs-lookup"><span data-stu-id="a8178-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="a8178-118">Получение сведений об учетной записи службы "Пространственные привязки Azure"</span><span class="sxs-lookup"><span data-stu-id="a8178-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="a8178-119">Прежде чем вы сможете использовать Пространственные привязки Azure в своем проекте, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="a8178-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="a8178-120">[Создайте ресурс пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) и скопируйте приведенные ниже поля учетной записи.</span><span class="sxs-lookup"><span data-stu-id="a8178-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="a8178-121">Эти значения используются для аутентификации пользователей в учетной записи приложения:</span><span class="sxs-lookup"><span data-stu-id="a8178-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="a8178-122">**идентификатор учетной записи** ;</span><span class="sxs-lookup"><span data-stu-id="a8178-122">**Account ID**</span></span>
    * <span data-ttu-id="a8178-123">**ключ учетной записи** .</span><span class="sxs-lookup"><span data-stu-id="a8178-123">**Account Key**</span></span>

<span data-ttu-id="a8178-124">Дополнительные сведения см. в документации по [аутентификации в службе "Пространственные привязки Azure"](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="a8178-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="a8178-125">Пространственные привязки Azure в Unreal 4.25 не поддерживают маркеры аутентификации Azure AD, но мы добавим поддержку такой функции в последующих выпусках.</span><span class="sxs-lookup"><span data-stu-id="a8178-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="a8178-126">Добавление подключаемых модулей службы "Пространственные привязки Azure"</span><span class="sxs-lookup"><span data-stu-id="a8178-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="a8178-127">Включите подключаемые модули службы "Пространственные привязки Azure" в Unreal Editor, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a8178-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="a8178-128">Последовательно выберите элементы **Edit (Правка) > Plugins (Подключаемые модули)** и найдите модули **AzureSpatialAnchors** и **AzureSpatialAnchorsForWMR** .</span><span class="sxs-lookup"><span data-stu-id="a8178-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR** .</span></span>
2. <span data-ttu-id="a8178-129">Установите флажок **Enabled** (Включен) для обоих модулей, чтобы разрешить доступ к библиотекам схем Пространственных привязок Azure в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="a8178-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="a8178-131">После этого перезапустите Unreal Editor, чтобы изменения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="a8178-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="a8178-132">Теперь проект готов к использованию Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="a8178-133">Запуск сеанса Пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="a8178-133">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="a8178-134">Сеанс Пространственных привязок Azure позволяет клиентским приложениям взаимодействовать со службой "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="a8178-135">Вам нужно будет создать и запустить сеанс службы "Пространственные привязки Azure" для создания, сохранения и публикации пространственных привязок Azure:</span><span class="sxs-lookup"><span data-stu-id="a8178-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="a8178-136">Откройте схему для Pawn, используемого в приложении.</span><span class="sxs-lookup"><span data-stu-id="a8178-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="a8178-137">Добавьте две строковые переменные для **идентификатора учетной записи** и **ключа учетной записи** . Назначьте соответствующие значения из учетной записи службы "Пространственные привязки Azure", чтобы аутентифицировать сеанс.</span><span class="sxs-lookup"><span data-stu-id="a8178-137">Add two string variables for the **Account ID** and **Account Key** , then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="a8178-139">Запустите сеанс Пространственных привязок Azure, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a8178-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="a8178-140">Проверьте, что **сеанс дополненной реальности** запущен в приложении HoloLens, так как сеанс Пространственных привязок Azure не может запуститься без сеанса дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="a8178-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="a8178-141">Если у вас нет единой настройки, [создайте ресурс сеанса дополненной реальности](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="a8178-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="a8178-142">Добавьте пользовательское событие **Start Azure Spatial Anchors Session** (Запуск сеанса Пространственных привязок Azure) и настройте его, как показано на снимке экрана ниже.</span><span class="sxs-lookup"><span data-stu-id="a8178-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="a8178-143">При создании сеанса он не будет запущен по умолчанию. Это позволяет разработчику настроить сеанс для аутентификации со службой "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-143">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="a8178-145">Настройте сеанс Пространственных привязок Azure, чтобы предоставить **идентификатор** и **ключ учетной записи** .</span><span class="sxs-lookup"><span data-stu-id="a8178-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key** .</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="a8178-147">Запустите сеанс Пространственных привязок Azure, разрешив приложению создавать и находить пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="a8178-149">Рекомендуется очистить ресурсы Пространственных привязок Azure в схеме графа событий, если вы больше не используете службу:</span><span class="sxs-lookup"><span data-stu-id="a8178-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="a8178-150">Остановите сеанс Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="a8178-151">Сеанс больше не будет выполняться, но связанные с ним ресурсы по-прежнему будут существовать в подключаемом модуле Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="a8178-153">Удалите сеанс Пространственных привязок Azure, чтобы очистить все его ресурсы, о которых еще известно подключаемому модулю Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="a8178-155">Схема графа событий должна выглядеть так, как показано на снимке экрана ниже:</span><span class="sxs-lookup"><span data-stu-id="a8178-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="a8178-157">Создание привязки</span><span class="sxs-lookup"><span data-stu-id="a8178-157">Creating an anchor</span></span>
<span data-ttu-id="a8178-158">Пространственная привязка Azure — это точка физического мира в пространстве приложения дополненной реальности, которая связывает содержимое дополненной реальности с расположениями в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="a8178-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="a8178-159">Пространственные привязки Azure могут совместно использовать различные пользователи.</span><span class="sxs-lookup"><span data-stu-id="a8178-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="a8178-160">Такой общий доступ позволяет размещать содержимое дополненной реальности, отображаемое на различных устройствах, в одном расположении физического мира.</span><span class="sxs-lookup"><span data-stu-id="a8178-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="a8178-161">Чтобы создать новую пространственную привязку Azure, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a8178-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="a8178-162">Убедитесь, что сеанс Пространственных привязок Azure запущен.</span><span class="sxs-lookup"><span data-stu-id="a8178-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="a8178-163">Приложение не сможет создать или сохранить пространственную привязку Azure, если сеанс Пространственных привязок Azure не запущен.</span><span class="sxs-lookup"><span data-stu-id="a8178-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="a8178-165">Создайте или получите **[компонент Scene (Сцена)](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** Unreal, расположение которого должно быть сохранено.</span><span class="sxs-lookup"><span data-stu-id="a8178-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="a8178-166">На изображении ниже **Scene Component Needing Anchor** (Компонент Scene, нуждающийся в привязке) используется в качестве переменной.</span><span class="sxs-lookup"><span data-stu-id="a8178-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="a8178-167">Компонент Unreal Scene (Сцена) необходим, чтобы сформировать преобразование мира приложения для [маркера дополненной реальности](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) и пространственной привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="a8178-169">Чтобы создать и сохранить пространственную привязку Azure для компонента Unreal Scene (Сцена), выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a8178-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="a8178-170">Вызовите [компонент Pin (Маркер)](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) для компонента Unreal Scene (Сцена) и укажите его **World Transform** (Преобразование мира) в качестве преобразования мира для маркера дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="a8178-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="a8178-171">Unreal отслеживает точки дополненной реальности в пространстве приложения с помощью маркеров дополненной реальности, которые используются для создания пространственной привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="a8178-172">В Unreal маркер дополненной реальности аналогичен объекту SpatialAnchor в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8178-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="a8178-174">Вызовите функцию **Create Cloud Anchor** (Создание облачной привязки) с помощью только что созданного маркера дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="a8178-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="a8178-175">При создании облачной привязки пространственная привязка Azure создается локально, а не в службе "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="a8178-176">Параметры для пространственной привязки Azure, например срок ее действия, можно задать до создания пространственной привязки с помощью службы.</span><span class="sxs-lookup"><span data-stu-id="a8178-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="a8178-178">Задайте срок действия пространственной привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="a8178-179">Параметр Lifetime (Время действия) этой функции позволяет разработчикам указать (в секундах), как долго привязка будет поддерживаться службой.</span><span class="sxs-lookup"><span data-stu-id="a8178-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="a8178-180">Например, срок действия длительностью в неделю будет равен 60 с x 60 мин x 24 ч x 7 дн. = 604 800 с.</span><span class="sxs-lookup"><span data-stu-id="a8178-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="a8178-182">После настройки параметров привязки объявите привязку как готовую к сохранению.</span><span class="sxs-lookup"><span data-stu-id="a8178-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="a8178-183">В примере ниже только что созданная пространственная привязка Azure добавляется к набору пространственных привязок Azure, которые требуют сохранения.</span><span class="sxs-lookup"><span data-stu-id="a8178-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="a8178-184">Этот набор объявляется как переменная для схемы Pawn.</span><span class="sxs-lookup"><span data-stu-id="a8178-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="a8178-186">Сохранение привязки</span><span class="sxs-lookup"><span data-stu-id="a8178-186">Saving an Anchor</span></span>

<span data-ttu-id="a8178-187">После настройки пространственной привязки Azure с вашими параметрами вызовите функцию **Save Cloud Anchor** (Сохранение облачной привязки).</span><span class="sxs-lookup"><span data-stu-id="a8178-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor** .</span></span> <span data-ttu-id="a8178-188">Функция Save Cloud Anchor (Сохранение облачной привязки) объявляет привязку для службы "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="a8178-189">Если вызов к этому действию был успешным, пространственная привязка Azure становится доступна другим пользователям службы "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="a8178-191">Save Cloud Anchor (Сохранение облачной привязки) — это асинхронная функция, которую можно вызвать только для события потока игры, например **EventTick** .</span><span class="sxs-lookup"><span data-stu-id="a8178-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick** .</span></span> <span data-ttu-id="a8178-192">Save Cloud Anchor может не отображаться как доступная функция схемы в пользовательских функциях схемы,</span><span class="sxs-lookup"><span data-stu-id="a8178-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="a8178-193">но она также доступна в редакторе схемы графа событий для Pawn.</span><span class="sxs-lookup"><span data-stu-id="a8178-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="a8178-194">В приведенном ниже примере пространственная привязка Azure сохраняется в наборе во время обратного вызова входного события.</span><span class="sxs-lookup"><span data-stu-id="a8178-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="a8178-195">Привязка затем сохраняется в EventTick.</span><span class="sxs-lookup"><span data-stu-id="a8178-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="a8178-196">Для сохранения пространственной привязки Azure может потребоваться несколько попыток в зависимости от объема пространственных данных, созданных в сеансе Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="a8178-197">Именно поэтому рекомендуется проверять, был ли успешным вызов сохранения.</span><span class="sxs-lookup"><span data-stu-id="a8178-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="a8178-198">Если привязка не сохранилась, повторно добавьте ее в набор привязок, требующих сохранения.</span><span class="sxs-lookup"><span data-stu-id="a8178-198">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="a8178-199">Последующий поток EventTicks будет пытаться сохранить привязку, пока она не будет успешно передана в службу "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-199">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="a8178-201">После сохранения привязки вы можете использовать преобразование маркеров дополненной реальности в качестве эталонного преобразования для размещения содержимого в приложении.</span><span class="sxs-lookup"><span data-stu-id="a8178-201">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="a8178-202">Другие пользователи могут обнаружить такую привязку и сопоставить содержимое дополненной реальности для разных устройств в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="a8178-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="a8178-203">Удаление привязки</span><span class="sxs-lookup"><span data-stu-id="a8178-203">Deleting an Anchor</span></span>

<span data-ttu-id="a8178-204">Вы можете удалить привязку из службы "Пространственные привязки Azure", вызвав функцию **Delete Cloud Anchor** (Удаление облачной привязки).</span><span class="sxs-lookup"><span data-stu-id="a8178-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor** .</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="a8178-206">Delete Cloud Anchor (Удаление облачной привязки) — это скрытая функция, которую можно вызвать только для события потока игры, например EventTick.</span><span class="sxs-lookup"><span data-stu-id="a8178-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="a8178-207">Delete Cloud Anchor может не отображаться как доступная функция схемы в пользовательских функциях схемы,</span><span class="sxs-lookup"><span data-stu-id="a8178-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="a8178-208">но она также доступна в редакторе схемы графа событий для Pawn.</span><span class="sxs-lookup"><span data-stu-id="a8178-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="a8178-209">В примере ниже привязка помечается для удаления при пользовательском событии ввода.</span><span class="sxs-lookup"><span data-stu-id="a8178-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="a8178-210">После этого предпринимается попытка удаления в EventTick.</span><span class="sxs-lookup"><span data-stu-id="a8178-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="a8178-211">В случае сбоя удаления привязки добавьте пространственную привязку Azure в набор привязок, помеченных для удаления, и повторите попытку в следующих событий EventTick.</span><span class="sxs-lookup"><span data-stu-id="a8178-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="a8178-212">Схема графа событий теперь должна выглядеть так, как показано на снимке экрана ниже:</span><span class="sxs-lookup"><span data-stu-id="a8178-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="a8178-214">Поиск существующих привязок</span><span class="sxs-lookup"><span data-stu-id="a8178-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="a8178-215">Помимо создания пространственных привязок Azure, вы можете обнаруживать привязки, созданные другими пользователями или устройствами с помощью службы "Пространственные привязки Azure":</span><span class="sxs-lookup"><span data-stu-id="a8178-215">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="a8178-216">Получите идентификатор пространственной привязки Azure, которую хотите обнаружить.</span><span class="sxs-lookup"><span data-stu-id="a8178-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="a8178-217">Идентификатор привязки можно получить для привязки, созданной устройством из предыдущего сеанса Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="a8178-218">Кроме того, его можно создать и использовать совместно с одноранговыми устройствами, взаимодействующими со службой "Пространственные привязки Azure".</span><span class="sxs-lookup"><span data-stu-id="a8178-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="a8178-220">Добавьте компонент **AzureSpatialAnchorsEvent** в свою схему Pawn.</span><span class="sxs-lookup"><span data-stu-id="a8178-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="a8178-221">Этот компонент позволяет вам подписаться на различные события Пространственных привязок Azure, например на события, вызываемые при нахождении пространственной привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="a8178-223">Подпишитесь на событие **ASAAnchor Located Delegate** (Привязкой ASAAnchor обнаружен делегат) для компонента **AzureSpatialAnchorsEvent** .</span><span class="sxs-lookup"><span data-stu-id="a8178-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="a8178-224">Делегат сообщает приложению об обнаружении новых привязок, связанных с учетной записью Пространственных привязок Azure.</span><span class="sxs-lookup"><span data-stu-id="a8178-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="a8178-225">При обратном вызове события пространственные привязки Azure, созданные другими пользователями или устройствами с помощью сеанса Пространственных привязок Azure, по умолчанию не будут включать маркеры дополненной реальности.</span><span class="sxs-lookup"><span data-stu-id="a8178-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="a8178-226">Чтобы создать маркер дополненной реальности для обнаруженной пространственной привязки Azure, разработчики могут вызвать функцию **Create ARPin Around Azure Cloud Spatial Anchor** (Создание маркера дополненной реальности в облачной пространственной привязке Azure).</span><span class="sxs-lookup"><span data-stu-id="a8178-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor** .</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="a8178-228">Чтобы найти пространственные привязки Azure, созданные другими пользователями или устройствами с помощью службы "Пространственные привязки Azure", приложению нужно создать **наблюдатель за пространственными привязками Azure** :</span><span class="sxs-lookup"><span data-stu-id="a8178-228">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher** :</span></span>
1. <span data-ttu-id="a8178-229">Убедитесь, что сеанс Пространственных привязок Azure запущен.</span><span class="sxs-lookup"><span data-stu-id="a8178-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="a8178-230">Создайте **AzureSpatialAnchorsLocateCriteria** .</span><span class="sxs-lookup"><span data-stu-id="a8178-230">Create an **AzureSpatialAnchorsLocateCriteria** .</span></span>
    * <span data-ttu-id="a8178-231">Вы можете указать различные параметры расположения, например расстояние от пользователя или от другой привязки.</span><span class="sxs-lookup"><span data-stu-id="a8178-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="a8178-232">Объявите идентификатор нужной пространственной привязки Azure в **AzureSpatialAnchorsLocateCriteria** .</span><span class="sxs-lookup"><span data-stu-id="a8178-232">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria** .</span></span>
4. <span data-ttu-id="a8178-233">Вызовите функцию **Create Watcher** (Создание наблюдателя).</span><span class="sxs-lookup"><span data-stu-id="a8178-233">Call **Create Watcher** .</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="a8178-235">Приложение теперь начнет поиск пространственных привязок Azure, о которых известно службе "Пространственные привязки Azure", благодаря чему пользователи смогут находить пространственные привязки Azure, созданные другими.</span><span class="sxs-lookup"><span data-stu-id="a8178-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="a8178-236">После обнаружения пространственной привязки Azure вызовите функцию **Stop Watcher** (Остановка наблюдателя), чтобы остановить наблюдатель за пространственными привязками Azure и очистить его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a8178-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="a8178-238">Финальная схема графа событий теперь должна выглядеть так, как показано на снимке экрана ниже:</span><span class="sxs-lookup"><span data-stu-id="a8178-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Подключаемые модули Пространственных привязок](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="a8178-240">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="a8178-240">Next Development Checkpoint</span></span>

<span data-ttu-id="a8178-241">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="a8178-241">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="a8178-242">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="a8178-242">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8178-243">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="a8178-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="a8178-244">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="a8178-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8178-245">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="a8178-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="a8178-246">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="a8178-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="a8178-247">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="a8178-247">Next steps</span></span>
* [<span data-ttu-id="a8178-248">Локальные пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="a8178-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="a8178-249">Документация по пространственным привязкам</span><span class="sxs-lookup"><span data-stu-id="a8178-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="a8178-250">Функции пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="a8178-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="a8178-251">Действующие рекомендации по работе с привязками</span><span class="sxs-lookup"><span data-stu-id="a8178-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)