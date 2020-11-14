---
title: Руководства по облачным службам Azure, часть 4. Интеграция Пространственных привязок Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, unity, руководство, hololens, hololens 2, пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: f8271fe3b3b9549d6c95707466db9af3d312fab7
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353252"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="d69b7-105">4. Интеграция Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d69b7-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="d69b7-106">Из этого руководства вы узнаете, как использовать **Пространственные привязки Azure**.</span><span class="sxs-lookup"><span data-stu-id="d69b7-106">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="d69b7-107">Вы сохраните данные расположения **отслеживаемого объекта** в виде пространственной привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="d69b7-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="d69b7-108">После отправки запроса к привязке появится стрелка, указывающая на расположение.</span><span class="sxs-lookup"><span data-stu-id="d69b7-108">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="d69b7-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="d69b7-109">Objectives</span></span>

* <span data-ttu-id="d69b7-110">Изучите основные сведения о Пространственных привязках Azure.</span><span class="sxs-lookup"><span data-stu-id="d69b7-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="d69b7-111">Узнайте, как настроить сцену для использования Пространственных привязок Azure в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="d69b7-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="d69b7-112">Узнайте, как выполнить интеграцию для хранения и запрашивания данных расположения.</span><span class="sxs-lookup"><span data-stu-id="d69b7-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="d69b7-113">Основные сведения о Пространственных привязках Azure</span><span class="sxs-lookup"><span data-stu-id="d69b7-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="d69b7-114">**Пространственные привязки Azure**  — это часть семейства облачных служб Azure. Решение позволяет сохранять данные расположения привязок.</span><span class="sxs-lookup"><span data-stu-id="d69b7-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="d69b7-115">Сохраненные данные расположений привязок можно получить из облака на основе *идентификатора привязки*.</span><span class="sxs-lookup"><span data-stu-id="d69b7-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="d69b7-116">К этим данным расположения привязок можно предоставить доступ многоплатформенным устройствам, таким как HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="d69b7-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="d69b7-117">Ознакомьтесь с дополнительными сведениями о [Пространственных привязках Azure](https://docs.microsoft.com/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="d69b7-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="d69b7-118">Подготовка Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="d69b7-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="d69b7-119">Перед началом работы создайте ресурс пространственной привязки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="d69b7-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="d69b7-120">Узнайте, как создать [ресурс пространственной привязки](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="d69b7-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d69b7-121">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="d69b7-121">Preparing the scene</span></span>

<span data-ttu-id="d69b7-122">Из этого раздела вы узнаете, как настроить сцену и внести необходимые изменения.</span><span class="sxs-lookup"><span data-stu-id="d69b7-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="d69b7-123">В окне Project (Проект) последовательно выберите **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager** (Активы > MRTK.Tutorials.AzureCloudServices > Заготовки > Диспетчер).</span><span class="sxs-lookup"><span data-stu-id="d69b7-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity с выбранной заготовкой AnchorManager](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="d69b7-125">В папке **Manager** (Диспетчер) перетащите заготовку **Anchor Manager** (Диспетчер привязок) в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="d69b7-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="d69b7-126">В окне Hierarchy (Иерархия) выберите объект GameObject **Anchor Manager** (Диспетчер привязок). В разделе Inspector (Инспектор) найдите элемент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок (скрипт)).</span><span class="sxs-lookup"><span data-stu-id="d69b7-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="d69b7-127">Найдите поля идентификатора и ключа учетной записи. Добавьте учетные данные, созданные ранее в рамках выполнения предварительных требований.</span><span class="sxs-lookup"><span data-stu-id="d69b7-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity со все еще выбранной добавленной заготовкой AnchorManager](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="d69b7-129">В иерархии сцены найдите объект **Scene Controller** (Контроллер сцены) и выберите его.</span><span class="sxs-lookup"><span data-stu-id="d69b7-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="d69b7-130">Отобразится окно инспектора **Scene Controller** (Контроллер сцены).</span><span class="sxs-lookup"><span data-stu-id="d69b7-130">You will see the **Scene Controller** Inspector.</span></span>

![Unity с настроенным компонентом скрипта SceneController](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="d69b7-132">Вы увидите, что поле **Anchor Manager** (Диспетчер привязок) в компоненте **Scene Controller** (Контроллер сцены) не заполнено. Перетащите **диспетчер привязок** из окна Hierarchy (Иерархия) в сцене в это поле и сохраните сцену.</span><span class="sxs-lookup"><span data-stu-id="d69b7-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="d69b7-133">Создание и развертывание приложения на устройстве HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d69b7-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="d69b7-134">Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам придется развернуть проект на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d69b7-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="d69b7-135">Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d69b7-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="d69b7-136">Запустите приложение на HoloLens 2 и следуйте предоставленным инструкциям</span><span class="sxs-lookup"><span data-stu-id="d69b7-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="d69b7-137">Создание привязки для хранения данных расположения</span><span class="sxs-lookup"><span data-stu-id="d69b7-137">Create an anchor to store a location</span></span>

<span data-ttu-id="d69b7-138">Из этого раздела вы узнаете, как сохранить данные расположения объекта.</span><span class="sxs-lookup"><span data-stu-id="d69b7-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="d69b7-139">Запустите приложение и щелкните элемент **Set Object** (Задать объект) в главном меню интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d69b7-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="d69b7-140">Присвойте **имя** объекту, который нужно сохранить, и щелкните элемент **Set Object** (Задать объект), чтобы продолжить.</span><span class="sxs-lookup"><span data-stu-id="d69b7-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="d69b7-141">Чтобы добавить дополнительные сведения об объекте, выберите **изображение** и опишите объект.</span><span class="sxs-lookup"><span data-stu-id="d69b7-141">To add more information about the object, select the **image** , and describe the object.</span></span>

<span data-ttu-id="d69b7-142">Чтобы сохранить данные расположения, щелкните **Save Location** (Сохранить данные расположения).</span><span class="sxs-lookup"><span data-stu-id="d69b7-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="d69b7-143">Отобразится **указатель привязки** , который можно переместить и установить в расположение, данные которого вам нужно сохранить.</span><span class="sxs-lookup"><span data-stu-id="d69b7-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="d69b7-144">После этого отобразится всплывающее окно с подтверждением.</span><span class="sxs-lookup"><span data-stu-id="d69b7-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="d69b7-145">Если вы хотите подтвердить и сохранить данные расположения, щелкните **Yes** (Да). Если нет, вы можете изменить расположение, щелкнув **No** (Нет) и выбрав расположение повторно.</span><span class="sxs-lookup"><span data-stu-id="d69b7-145">If you want to confirm and save the location, click on **Yes** ; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="d69b7-146">Когда вы подтвердите расположение, щелкнув **Yes** (Да), данные расположения и идентификатор привязки будут сохранены в облачном хранилище Azure.</span><span class="sxs-lookup"><span data-stu-id="d69b7-146">Once you confirm the location by clicking on **Yes** , the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="d69b7-147">После их сохранения в привязке отобразится **тег объекта** с его именем.</span><span class="sxs-lookup"><span data-stu-id="d69b7-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="d69b7-148">Теперь данные расположения объекта успешно сохранены.</span><span class="sxs-lookup"><span data-stu-id="d69b7-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="d69b7-149">Запрашивание данных расположения привязки</span><span class="sxs-lookup"><span data-stu-id="d69b7-149">Query for finding an anchor location</span></span>

<span data-ttu-id="d69b7-150">После успешного сохранения данных расположения привязки вы можете узнать это расположение, выбрав **Search Object** (Поиск объекта) в главном меню.</span><span class="sxs-lookup"><span data-stu-id="d69b7-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="d69b7-151">После щелчка элемента **Search Object** (Поиск объекта) откроется новое всплывающее окно, в котором нужно указать имя искомого объекта.</span><span class="sxs-lookup"><span data-stu-id="d69b7-151">After clicking on **Search Object** , a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="d69b7-152">Введите имя объекта и щелкните **Search Object** (Поиск объекта).</span><span class="sxs-lookup"><span data-stu-id="d69b7-152">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="d69b7-153">Если объект предварительно сохранен и был обнаружен в базе данных, вы получите карту объекта со всеми сведениями о нем, которые вы сохранили ранее.</span><span class="sxs-lookup"><span data-stu-id="d69b7-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="d69b7-154">Теперь щелкните элемент **Show Location** (Показать расположение), чтобы найти объект.</span><span class="sxs-lookup"><span data-stu-id="d69b7-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="d69b7-155">Когда вы щелкнете **Show Location** (Показать расположение), система подаст запрос на местоположение объекта в облачном хранилище.</span><span class="sxs-lookup"><span data-stu-id="d69b7-155">Once you click on **Show Location** , the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="d69b7-156">После успешного получения данных расположения **стрелка** направит вас к расположению объекта.</span><span class="sxs-lookup"><span data-stu-id="d69b7-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="d69b7-157">Следуйте за знаком стрелки, пока не найдете расположение объекта.</span><span class="sxs-lookup"><span data-stu-id="d69b7-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="d69b7-158">Когда вы найдете объект, сверху отобразится его имя и знак стрелки исчезнет. Теперь можно щелкнуть **тег объекта** , чтобы просмотреть сведения о нем.</span><span class="sxs-lookup"><span data-stu-id="d69b7-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d69b7-159">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d69b7-159">Congratulations</span></span>

<span data-ttu-id="d69b7-160">Из этого руководства вы узнали, как в Пространственных привязках Azure можно сохранять и извлекать данные расположения объектов на устройстве Hololense 2.</span><span class="sxs-lookup"><span data-stu-id="d69b7-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="d69b7-161">С помощью заключительного руководства вы научитесь добавлять естественный язык как новый метод взаимодействия для своего приложения с помощью **Службы Azure Bot**.</span><span class="sxs-lookup"><span data-stu-id="d69b7-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d69b7-162">Следующее руководство: 5. Интеграция Службы Azure Bot c LUIS</span><span class="sxs-lookup"><span data-stu-id="d69b7-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
