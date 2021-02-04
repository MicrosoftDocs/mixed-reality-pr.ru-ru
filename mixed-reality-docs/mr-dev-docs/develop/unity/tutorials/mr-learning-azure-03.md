---
title: Интеграция Пользовательского визуального распознавания Azure
description: Пройдите этот курс, и вы узнаете, как реализовать Пользовательское визуальное распознавание Azure в приложении смешанной реальности HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, HoloLens 2, Пользовательское визуальное распознавание Azure, Azure Cognitive Services, облачные службы Azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7676a55a2276b88f3bc123dda90a1b8d39536a61
ms.sourcegitcommit: daa45a19a3a353334380cda78fee7fa149f0e48b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2021
ms.locfileid: "98981723"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="ecbbe-104">3. Интеграция Пользовательского визуального распознавания Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="ecbbe-105">В этом руководстве показано, как использовать **Пользовательское визуальное распознавание Azure**. Вы отправите набор фотографий, чтобы связать их с *отслеживаемым объектом*, передать их в службу **Пользовательское визуальное распознавание** и начать процесс обучения.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="ecbbe-106">Затем вы будете использовать службу для обнаружения *отслеживаемого объекта* путем записи фотографий из веб-канала веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="ecbbe-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="ecbbe-107">Objectives</span></span>

* <span data-ttu-id="ecbbe-108">Узнать о Пользовательском визуальном распознавании Azure.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="ecbbe-109">Узнать, как настроить сцену для работы с Пользовательским визуальным распознаванием в этом проекте.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="ecbbe-110">Узнать, как интегрировать передачу, обучение и обнаружение изображений.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="ecbbe-111">Общие сведения о Пользовательском визуальном распознавании Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="ecbbe-112">**Пользовательское визуальное распознавание Azure** входит в семейство служб **Cognitive Services** и используется для обучения классификаторов изображений.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="ecbbe-113">Классификатор изображений — это служба ИИ, которая использует обученную модель для применения соответствующих тегов.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="ecbbe-114">Эта функция классификации будет использоваться нашим приложением для обнаружения *отслеживаемых объектов*.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="ecbbe-115">См. сведения о [Пользовательском визуальном распознавании Azure](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="ecbbe-116">Подготовка Пользовательского визуального распознавания Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="ecbbe-117">Перед началом работы нужно создать проект пользовательского визуального распознавания, и самый быстрый способ сделать это — использовать веб-портал.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="ecbbe-118">Следуйте инструкциям из этого [краткого руководства](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images), чтобы настроить учетную запись и проект (до раздела *Отправка и снабжение тегами изображений*).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="ecbbe-119">Для обучения модели необходимо иметь минимум два тега и пять изображений на каждый тег.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="ecbbe-120">Для работы с этим приложением нужно создать хотя бы один тег с пятью изображениями, чтобы последующий процесс обучения не завершился сбоем.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ecbbe-121">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="ecbbe-121">Preparing the scene</span></span>

<span data-ttu-id="ecbbe-122">В окне проекта перейдите в папку **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** (Активы > MRTK.Tutorials.AzureCloudServices > Заготовки > Диспетчер).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Unity с окном проекта, в котором отображается путь к заготовке ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="ecbbe-124">После этого перетащите заготовку **ObjectDetectionManager** в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![Unity с полями конфигурации компонента скрипта ObjectDetectionManager, отображаемыми в инспекторе](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="ecbbe-126">В окне иерархии найдите и выберите объект **ObjectDetectionManager**.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="ecbbe-127">Заготовка **ObjectDetectionManager** содержит компонент **ObjectDetectionManager (script)** (ObjectDetectionManager — скрипт). Как видно в окне Inspector (Инспектор), он зависит от параметров Azure и параметров в окне Project (Проект).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="ecbbe-128">Получение учетных данных ресурса API Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="ecbbe-129">Необходимые учетные данные для параметров **ObjectDetectionManager (script)** (ObjectDetectionManager — скрипт) можно получить на портале Azure и портале пользовательского визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="ecbbe-130">Получение учетных данных для параметров Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="ecbbe-131">Найдите ресурс пользовательского визуального распознавания типа **Cognitive Services**, созданный при работе с разделом *Подготовка сцены* этого учебника (выберите имя ресурса пользовательского визуального распознавания с *-Prediction* в конце).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="ecbbe-132">Щелкните *Overview* (Общие сведения) или *Keys and Endpoint* (Ключи и конечная точка), чтобы получить необходимые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="ecbbe-133">Получение учетных данных для параметров проекта</span><span class="sxs-lookup"><span data-stu-id="ecbbe-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="ecbbe-134">На панели мониторинга [пользовательского визуального распознавания](https://www.customvision.ai/projects) откройте созданный проект и щелкните значок шестеренки в правом верхнем углу страницы, чтобы открыть страницу параметров.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="ecbbe-135">В правой части раздела *Resources* (Ресурсы) вы найдете необходимые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="ecbbe-136">Теперь, когда объект **ObjectDetectionManager (script)** (ObjectDetectionManager — скрипт) правильно настроен, найдите и выберите в иерархии сцены объект **SceneController**.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![Unity с полями конфигурации компонента скрипта SceneController, отображаемыми в инспекторе](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="ecbbe-138">Вы увидите, что поле *Object Detection Manager* (Диспетчер обнаружения объектов) в компоненте **SceneController** пустое. Перетащите **ObjectDetectionManager** из раздела иерархии в это поле и сохраните сцену.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![Unity с настроенным компонентом скрипта SceneController](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="ecbbe-140">Получение и отправка изображений</span><span class="sxs-lookup"><span data-stu-id="ecbbe-140">Take and upload images</span></span>

<span data-ttu-id="ecbbe-141">Запустите сцену и щелкните **Set Object** (Настроить объект), а затем введите имя одного из **отслеживаемых объектов**, созданных в [предыдущем уроке](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="ecbbe-142">Теперь нажмите кнопку **Computer Vision** (Компьютерное зрение) в нижней части **карты объекта**.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="ecbbe-143">Откроется новое окно, где вам нужно взять шесть фотографий для обучения модели распознаванию изображений.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="ecbbe-144">Нажмите кнопку **Camera** (Камера) и выполните жест касания при просмотре объекта, который вы хотите отслеживать. Сделайте это шесть раз.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="ecbbe-145">Чтобы улучшить обучение модели, попробуйте использовать изображение с разными ракурсами и условиями освещения.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="ecbbe-146">Получив достаточное количество изображений, нажмите кнопку **Train** (Обучить), чтобы начать процесс обучения модели в облаке.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="ecbbe-147">При активации процесса сначала будут отправлены все изображения, а затем начнется обучение. Это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="ecbbe-148">Сообщение в меню информирует о ходе выполнения. По завершении процесса работу приложения можно остановить.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="ecbbe-149">Объект **ObjectDetectionManager (script)** (ObjectDetectionManager — скрипт) напрямую отправляет изображения в службу Пользовательского визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="ecbbe-150">В качестве альтернативы API пользовательского визуального распознавания принимает URL-адреса изображений. Вместо этого в качестве упражнения можно изменить объект **ObjectDetectionManager (script)** (ObjectDetectionManager — скрипт) для отправки изображений в Хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="ecbbe-151">Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="ecbbe-151">Detect objects</span></span>

<span data-ttu-id="ecbbe-152">Перед обнаружением объектов необходимо изменить ключ API в разделе **ObjectDetectionManager (script)** в параметрах проекта, которому уже назначен ключ пользовательского визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-152">Before detecting the objects we have to change the Api key present in  **ObjectDetectionManager (script)** under project settings that already assign with custom vision key.</span></span>

<span data-ttu-id="ecbbe-153">Найдите ресурс пользовательского визуального распознавания на портале Azure. Щелкните *Keys and Endpoint* (Ключи и конечная точка), чтобы получить ключ API и заменить старый ключ API в параметрах проекта.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-153">Find and locate the custom vision resource in Azure portal.There click on *Keys and Endpoint* to retrieve the Api key and replace with old Api key under project settings.</span></span>

<span data-ttu-id="ecbbe-154">Теперь можно применить обученную модель к тесту, запустить приложение, а затем в *главном меню* щелкнуть **Search Object** (Поиск объекта) и ввести имя **отслеживаемого объекта** в вопросе.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-154">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="ecbbe-155">Когда появится **карта объекта**, нажмите кнопку **Custom Vision** (Пользовательское визуальное распознавание).</span><span class="sxs-lookup"><span data-stu-id="ecbbe-155">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="ecbbe-156">Объект **ObjectDetectionManager** начнет создавать изображения в фоновом режиме с камеры, а в меню будет отображаться ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-156">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="ecbbe-157">Наведите камеру на объект, который использовался для обучения модели, и вы увидите, что через некоторое время она определит его.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-157">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ecbbe-158">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ecbbe-158">Congratulations</span></span>

<span data-ttu-id="ecbbe-159">В этом руководстве показано, как работать с Пользовательским визуальным распознаванием Azure для обучения изображений и использования службы классификации для обнаружения изображений, соответствующих связанному **отслеживаемому объекту**.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-159">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="ecbbe-160">В следующем руководстве будет показано, как с помощью Пространственных привязок Azure связать *отслеживаемый объект* с расположением в физическом мире и как отобразить стрелку, которая позволит пользователю вернуться к связанному расположению отслеживаемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ecbbe-160">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ecbbe-161">Следующее руководство: 4. Интеграция Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="ecbbe-161">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)