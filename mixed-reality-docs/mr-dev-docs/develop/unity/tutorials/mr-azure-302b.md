---
title: 302b. Смешанная реальность и Azure — пользовательское визуальное распознавание
description: Пройдите этот курс, чтобы научиться обучить модель машинного обучения, а затем использовать обученную модель для распознавания похожих объектов в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, пользовательское видение, hololens, иммерсивное, VR, Windows 10, Visual Studio
ms.openlocfilehash: cba2df5841911df6d60a7060a70f835975a21f62
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583401"
---
# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="10489-104">302b. Смешанная реальность и Azure: пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-104">MR and Azure 302b: Custom vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="10489-105">Руководства Mixed Reality Academy были разработаны для иммерсивных гарнитур HoloLens (1-го поколения) и иммерсивных гарнитур Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="10489-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10489-106">Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="10489-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10489-107">Данные руководства **_не_** будут обновляться с учетом последних наборов инструментов или возможностей взаимодействия для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="10489-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10489-108">Они будут сохранены для работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="10489-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10489-109">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="10489-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="10489-110">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="10489-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>


<span data-ttu-id="10489-111">В этом курсе вы узнаете, как распознать пользовательское визуальное содержимое в предоставленном образе, используя возможности Пользовательское визуальное распознавание Azure в приложении смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="10489-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="10489-112">Эта служба позволит обучить модель машинного обучения с помощью образов объектов.</span><span class="sxs-lookup"><span data-stu-id="10489-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="10489-113">После этого обученная модель будет использоваться для распознавания похожих объектов, как это обеспечивается с помощью камеры Microsoft HoloLens или камеры, подключенной к компьютеру для использования в качестве впечатляющих (VR) гарнитур.</span><span class="sxs-lookup"><span data-stu-id="10489-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![результат курса](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="10489-115">Azure Пользовательское визуальное распознавание — это служба Microsoft, которая позволяет разработчикам создавать пользовательские классификаторы изображений.</span><span class="sxs-lookup"><span data-stu-id="10489-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="10489-116">Эти классификаторы можно использовать с новыми образами для распознавания или классификации объектов внутри этого нового изображения.</span><span class="sxs-lookup"><span data-stu-id="10489-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="10489-117">Служба предоставляет простой, простой в использовании веб-портал для упрощения процесса.</span><span class="sxs-lookup"><span data-stu-id="10489-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="10489-118">Дополнительные сведения см. на [странице Пользовательская служба визуального распознавания Azure](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="10489-118">For more information, visit the [Azure Custom Vision Service page](/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="10489-119">После завершения этого курса у вас будет приложение смешанной реальности, которое сможет работать в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="10489-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="10489-120">**Режим анализа**. Настройка пользовательская служба визуального распознавания вручную путем отправки образов, создания тегов и обучения службы для распознавания различных объектов (в данном случае это мышь и клавиатура).</span><span class="sxs-lookup"><span data-stu-id="10489-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="10489-121">Затем вы создадите приложение HoloLens, которое будет записывать изображения с помощью камеры и попытается распознать эти объекты в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="10489-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="10489-122">**Режим обучения**. Вы будете реализовывать код, который включит режим обучения в приложении.</span><span class="sxs-lookup"><span data-stu-id="10489-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="10489-123">Режим обучения позволяет записывать изображения с помощью камеры HoloLens, передавать записанные образы в службу и обучить пользовательскую модель концепции.</span><span class="sxs-lookup"><span data-stu-id="10489-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="10489-124">В этом курсе вы узнаете, как получить результаты из Пользовательская служба визуального распознавания в пример приложения на основе Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="10489-125">Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.</span><span class="sxs-lookup"><span data-stu-id="10489-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="10489-126">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="10489-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10489-127">Курс</span><span class="sxs-lookup"><span data-stu-id="10489-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10489-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10489-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10489-129"><a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="10489-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="10489-130">302b. Смешанная реальность и Azure: пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="10489-131">✔️</span><span class="sxs-lookup"><span data-stu-id="10489-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10489-132">✔️</span><span class="sxs-lookup"><span data-stu-id="10489-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="10489-133">Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR).</span><span class="sxs-lookup"><span data-stu-id="10489-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="10489-134">Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="10489-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="10489-135">При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).</span><span class="sxs-lookup"><span data-stu-id="10489-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10489-136">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="10489-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="10489-137">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="10489-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="10489-138">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="10489-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="10489-139">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](../../install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="10489-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="10489-140">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="10489-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="10489-141">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="10489-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="10489-142">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="10489-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10489-143">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="10489-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10489-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="10489-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10489-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10489-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="10489-146">Высокодоступная [гарнитура Windows Mixed Reality (VR)](../../../discover/immersive-headset-hardware-details.md) или [Microsoft HoloLens](/hololens/hololens1-hardware) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="10489-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="10489-147">Камера, подключенная к компьютеру (для разработки в увлекательной гарнитуре)</span><span class="sxs-lookup"><span data-stu-id="10489-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="10489-148">Доступ к Интернету для установки Azure и получение API Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="10489-149">Последовательность из пяти (5) образов (рекомендуется десять (10)) для каждого объекта, который вы хотите Пользовательская служба визуального распознавания распознать.</span><span class="sxs-lookup"><span data-stu-id="10489-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="10489-150">При желании вы можете использовать образы, [которые уже предоставлены в этом курсе (мышь компьютера и клавиатура) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="10489-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="10489-151">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="10489-151">Before you start</span></span>

1.  <span data-ttu-id="10489-152">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="10489-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="10489-153">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10489-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="10489-154">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="10489-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="10489-155">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="10489-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="10489-156">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](/hololens/hololens-calibration#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="10489-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="10489-157">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](/hololens/hololens-updates).</span><span class="sxs-lookup"><span data-stu-id="10489-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="10489-158">Глава 1. портал Пользовательская служба визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="10489-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="10489-159">Чтобы использовать *Пользовательская служба визуального распознавания* в Azure, необходимо настроить экземпляр службы, чтобы сделать его доступным для приложения.</span><span class="sxs-lookup"><span data-stu-id="10489-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="10489-160">Сначала [перейдите на главную страницу *Пользовательская служба визуального распознавания*](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="10489-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="10489-161">Нажмите кнопку " **начать работу** ".</span><span class="sxs-lookup"><span data-stu-id="10489-161">Click on the **Get Started** button.</span></span>

    ![Начало работы с Пользовательская служба визуального распознавания](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="10489-163">Войдите на портал *Пользовательская служба визуального распознавания* .</span><span class="sxs-lookup"><span data-stu-id="10489-163">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![Вход на портал](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="10489-165">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="10489-165">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="10489-166">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="10489-166">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="10489-167">После первого входа в систему вам будет предложено ввести *условия использования панели Сервис* .</span><span class="sxs-lookup"><span data-stu-id="10489-167">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="10489-168">Установите флажок, чтобы принять условия.</span><span class="sxs-lookup"><span data-stu-id="10489-168">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="10489-169">Затем нажмите кнопку **принимаю**.</span><span class="sxs-lookup"><span data-stu-id="10489-169">Then click on **I agree**.</span></span>

    ![Условия предоставления услуг](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="10489-171">Принимаю условия, вы будете переходить к разделу *проекты* на портале.</span><span class="sxs-lookup"><span data-stu-id="10489-171">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="10489-172">Щелкните **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="10489-172">Click on **New Project**.</span></span>

    ![Создание нового проекта](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="10489-174">На правой стороне появится вкладка, в которой будет предложено указать некоторые поля для проекта.</span><span class="sxs-lookup"><span data-stu-id="10489-174">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="10489-175">Вставьте *имя* проекта.</span><span class="sxs-lookup"><span data-stu-id="10489-175">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="10489-176">Вставьте *Описание* проекта (*необязательно*).</span><span class="sxs-lookup"><span data-stu-id="10489-176">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="10489-177">Выберите *группу ресурсов* или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="10489-177">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="10489-178">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="10489-178">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10489-179">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="10489-179">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="10489-180">Задание *типов проектов* для **классификации**</span><span class="sxs-lookup"><span data-stu-id="10489-180">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="10489-181">Задайте *домены* как **Общие**.</span><span class="sxs-lookup"><span data-stu-id="10489-181">Set the *Domains* as **General**.</span></span>

        ![Настройка доменов](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="10489-183">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="10489-183">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="10489-184">По завершении нажмите кнопку **создать проект**. Вы будете перенаправлены на страницу пользовательская служба визуального распознавания, проект.</span><span class="sxs-lookup"><span data-stu-id="10489-184">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="10489-185">Глава 2. обучение проекта Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-185">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="10489-186">На портале Пользовательское визуальное распознавание основной целью является обучение проекта для распознавания конкретных объектов в изображениях.</span><span class="sxs-lookup"><span data-stu-id="10489-186">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="10489-187">Требуется по крайней мере пять образов (5), хотя для каждого объекта, который нужно распознать, рекомендуется использовать по меньшей мере десять (10).</span><span class="sxs-lookup"><span data-stu-id="10489-187">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="10489-188">[Вы можете использовать образы, предоставляемые в этом курсе (мышь компьютера и клавиатура)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="10489-188">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="10489-189">Обучение проекта Пользовательская служба визуального распознавания:</span><span class="sxs-lookup"><span data-stu-id="10489-189">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="10489-190">Нажмите кнопку **+** рядом с пунктом **теги.**</span><span class="sxs-lookup"><span data-stu-id="10489-190">Click on the **+** button next to **Tags.**</span></span>

    ![Добавление нового тега](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="10489-192">Добавьте **имя** объекта, который вы хотите распознать.</span><span class="sxs-lookup"><span data-stu-id="10489-192">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="10489-193">Щелкните **Save**(Сохранить).</span><span class="sxs-lookup"><span data-stu-id="10489-193">Click on **Save**.</span></span>

    ![Добавить имя объекта и сохранить](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="10489-195">Обратите внимание, что добавлен **тег** (может потребоваться перезагрузить страницу, чтобы она отображалась).</span><span class="sxs-lookup"><span data-stu-id="10489-195">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="10489-196">Установите флажок рядом с новым тегом, если он еще не установлен.</span><span class="sxs-lookup"><span data-stu-id="10489-196">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![Включить новый тег](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="10489-198">Щелкните **Добавить изображения** в центре страницы.</span><span class="sxs-lookup"><span data-stu-id="10489-198">Click on **Add Images** in the center of the page.</span></span>

    ![Добавление изображений.](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="10489-200">Щелкните **Обзор локальные файлы**, найдите, а затем выберите изображения, которые нужно передать, с минимальным числом (5).</span><span class="sxs-lookup"><span data-stu-id="10489-200">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="10489-201">Помните, что все эти образы должны содержать объект для обучения.</span><span class="sxs-lookup"><span data-stu-id="10489-201">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="10489-202">Для отправки можно выбрать несколько образов за раз.</span><span class="sxs-lookup"><span data-stu-id="10489-202">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="10489-203">Просмотрев изображения на вкладке, выберите соответствующий тег в поле **Мои теги** .</span><span class="sxs-lookup"><span data-stu-id="10489-203">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![Выбор тегов](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="10489-205">Щелкните **upload Files (отправить файлы**).</span><span class="sxs-lookup"><span data-stu-id="10489-205">Click on **Upload files**.</span></span> <span data-ttu-id="10489-206">Файлы начнут отправляться.</span><span class="sxs-lookup"><span data-stu-id="10489-206">The files will begin uploading.</span></span> <span data-ttu-id="10489-207">Получив подтверждение отправки, нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="10489-207">Once you have confirmation of the upload, click **Done**.</span></span>

    ![Отправка файлов](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="10489-209">Повторите тот же процесс, чтобы создать новый **тег** с именем **Keyboard** и загрузить в него соответствующие фотографии.</span><span class="sxs-lookup"><span data-stu-id="10489-209">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="10489-210">После создания новых тегов снимите **флажок** *мыши* , чтобы отобразить окно *Добавление изображений* .</span><span class="sxs-lookup"><span data-stu-id="10489-210">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="10489-211">После настройки обоих тегов щелкните " **обучение**", после чего начнется создание первой итерации для обучения.</span><span class="sxs-lookup"><span data-stu-id="10489-211">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![Включить итерацию обучения](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="10489-213">После его создания вы увидите две кнопки с именем сделать **URL-адрес** **по умолчанию** и прогноз.</span><span class="sxs-lookup"><span data-stu-id="10489-213">Once it's built, you'll be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="10489-214">Щелкните сначала **создать значение по умолчанию** , а затем щелкните **URL-адрес прогноза**.</span><span class="sxs-lookup"><span data-stu-id="10489-214">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![Сделать URL-адрес по умолчанию и прогноз](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="10489-216">В качестве URL-адреса конечной точки, предоставленной из этого, задается любая *Итерация* , помеченная как используемая по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="10489-216">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="10489-217">Таким образом, если позднее вы выполните новую *итерацию* и обновите ее по умолчанию, вам не потребуется изменять код.</span><span class="sxs-lookup"><span data-stu-id="10489-217">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="10489-218">После того как вы щелкнули *URL-адрес прогноза*, откройте *Блокнот*, скопируйте и вставьте **URL-адрес** и **ключ прогноза**, чтобы его можно было извлечь, когда он понадобится позже в коде.</span><span class="sxs-lookup"><span data-stu-id="10489-218">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![Копирование и вставка URL-адреса и Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="10489-220">Щелкните **шестеренки** в правом верхнем углу экрана.</span><span class="sxs-lookup"><span data-stu-id="10489-220">Click on the **Cog** at the top right of the screen.</span></span>

    ![Щелкните значок шестеренки, чтобы открыть параметры.](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="10489-222">Скопируйте **ключ обучения** и вставьте его в *Блокнот* для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="10489-222">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![Копировать ключ обучения](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="10489-224">Также скопируйте **идентификатор проекта**, а также вставьте его в файл *блокнота* для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="10489-224">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![Копировать идентификатор проекта](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="10489-226">Глава 3. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="10489-226">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="10489-227">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="10489-227">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="10489-228">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="10489-228">Open *Unity* and click **New**.</span></span>

    ![Создание проекта Unity](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="10489-230">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-230">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="10489-231">Вставьте **азурекустомвисион.**</span><span class="sxs-lookup"><span data-stu-id="10489-231">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="10489-232">Убедитесь, что для шаблона проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="10489-232">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="10489-233">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="10489-233">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="10489-234">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="10489-234">Then, click **Create project**.</span></span>

    ![Настройка параметров проекта](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="10489-236">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-236">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="10489-237">Перейдите к разделу **изменение*  >  *настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="10489-237">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="10489-238">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="10489-238">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="10489-239">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="10489-239">Close the **Preferences** window.</span></span>

    ![Настройка внешних средств](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="10489-241">Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.</span><span class="sxs-lookup"><span data-stu-id="10489-241">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![<span data-ttu-id="10489-242">Настройка параметров сборки</span><span class="sxs-lookup"><span data-stu-id="10489-242">Configure build settings</span></span> ](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="10489-243">Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="10489-243">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="10489-244">**Целевое устройство** имеет значение **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="10489-244">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="10489-245">Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.</span><span class="sxs-lookup"><span data-stu-id="10489-245">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="10489-246">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="10489-246">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="10489-247">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="10489-247">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="10489-248">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="10489-248">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="10489-249">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="10489-249">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="10489-250">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="10489-250">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="10489-251">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="10489-251">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="10489-252">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="10489-252">A save window will appear.</span></span>

            ![Добавить открытую сцену в список сборки](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="10489-254">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="10489-254">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создать новую папку сцены](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="10489-256">Откройте созданную папку **сцены** , а затем в текстовом поле *имя файла* введите **Кустомвисионсцене**, а затем щелкните **Save (сохранить**).</span><span class="sxs-lookup"><span data-stu-id="10489-256">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![Имя новый файл сцены](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="10489-258">Помните, что сцены Unity необходимо сохранять в папке *Assets* , так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-258">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="10489-259">Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-259">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="10489-260">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="10489-260">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![Параметры сборки по умолчанию](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="10489-262">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="10489-262">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="10489-263">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="10489-263">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="10489-264">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="10489-264">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="10489-265">**Версия среды выполнения сценариев** должна быть **экспериментальной (эквивалент .NET 4,6)**, что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="10489-265">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="10489-266">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="10489-266">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="10489-267">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="10489-267">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Задать API компантиблити](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="10489-269">На вкладке **Параметры публикации** в разделе **возможности** установите флажок:</span><span class="sxs-lookup"><span data-stu-id="10489-269">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="10489-270">**InternetClient**;</span><span class="sxs-lookup"><span data-stu-id="10489-270">**InternetClient**</span></span>

        2.  <span data-ttu-id="10489-271">**Веб-камера**</span><span class="sxs-lookup"><span data-stu-id="10489-271">**Webcam**</span></span>

        3. <span data-ttu-id="10489-272">**Микрофон**</span><span class="sxs-lookup"><span data-stu-id="10489-272">**Microphone**</span></span>

        ![Настройка параметров публикации](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="10489-274">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность** Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="10489-274">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![Настройка параметров XR](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="10489-276">Назад в *параметрах сборки* *\# проекты Unity C* больше не заключаются; установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="10489-276">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="10489-277">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="10489-277">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="10489-278">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="10489-278">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="10489-279">Глава 4. Импорт библиотеки DLL Newtonsoft в Unity</span><span class="sxs-lookup"><span data-stu-id="10489-279">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10489-280">Если вы хотите пропустить установленный в этом курсе компонент *установки Unity* и продолжить работу с кодом, скачайте этот [Azure-MR-302B. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="10489-280">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="10489-281">Для работы с этим курсом необходимо использовать библиотеку **Newtonsoft** , которую можно добавить в ресурсы в качестве библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="10489-281">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="10489-282">Пакет, содержащий [эту библиотеку, можно скачать по этой ссылке](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="10489-282">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="10489-283">Чтобы импортировать библиотеку Newtonsoft в проект, используйте пакет Unity, прилагаемый к этому курсу.</span><span class="sxs-lookup"><span data-stu-id="10489-283">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="10489-284">Добавьте *. пакет unitypackage* в Unity с помощью команды меню \* >     >  *Настраиваемый* *пакет* импорт *активов*\* .</span><span class="sxs-lookup"><span data-stu-id="10489-284">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="10489-285">В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).</span><span class="sxs-lookup"><span data-stu-id="10489-285">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Импортировать все элементы пакета](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="10489-287">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="10489-287">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="10489-288">Перейдите в папку **Newtonsoft** в разделе **подключаемые модули** в представлении проекта и выберите *Newtonsoft.Jsпо подключаемому модулю*.</span><span class="sxs-lookup"><span data-stu-id="10489-288">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![Выбор подключаемого модуля Newtonsoft](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="10489-290">Выбрав *Newtonsoft.Jsпо выбранному подключаемому модулю* , убедитесь, что **все платформы** **не установлены**, убедитесь, что также не установлен **флажок** **всаплайер** , а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="10489-290">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="10489-291">Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="10489-291">This is just to confirm that the files are configured correctly.</span></span>

    ![Настройка подключаемого модуля Newtonsoft](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="10489-293">Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-293">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="10489-294">В папке WSA имеется другой набор, который будет использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="10489-294">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="10489-295">Далее необходимо открыть папку **WSA** в папке **Newtonsoft**</span><span class="sxs-lookup"><span data-stu-id="10489-295">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="10489-296">Вы увидите копию того же файла, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="10489-296">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="10489-297">Выберите файл, а затем в инспекторе убедитесь, что</span><span class="sxs-lookup"><span data-stu-id="10489-297">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="10489-298">**Все платформы** не **отмечены**</span><span class="sxs-lookup"><span data-stu-id="10489-298">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="10489-299">**проверяется** **только** **всаплайер**</span><span class="sxs-lookup"><span data-stu-id="10489-299">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="10489-300">**Установлен** **процесс не**</span><span class="sxs-lookup"><span data-stu-id="10489-300">**Dont process** is **checked**</span></span>

    ![Настройка параметров платформы подключаемого модуля Newtonsoft](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="10489-302">Глава 5 — Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="10489-302">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="10489-303">На панели Иерархия выберите *основную камеру*.</span><span class="sxs-lookup"><span data-stu-id="10489-303">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="10489-304">После выбора вы сможете увидеть все компоненты *основной камеры* на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="10489-304">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="10489-305">Объект *Camera* должен называться **основной камерой** (Обратите внимание на орфографию!)</span><span class="sxs-lookup"><span data-stu-id="10489-305">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="10489-306">Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на правописание).</span><span class="sxs-lookup"><span data-stu-id="10489-306">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="10489-307">Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .</span><span class="sxs-lookup"><span data-stu-id="10489-307">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="10489-308">Установите для параметра **сбросить флаги** **сплошной цвет** (не обращайте внимания на иммерсивное гарнитуру).</span><span class="sxs-lookup"><span data-stu-id="10489-308">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="10489-309">Задайте черный цвет **фона** для компонента камеры **, альфа-канал 0 (шестнадцатеричный код: #00000000)** (не учитывать это для иммерсивного головного телефона).</span><span class="sxs-lookup"><span data-stu-id="10489-309">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![Настройка свойств компонента камеры](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="10489-311">Глава 6. Создание класса Кустомвисионаналисер.</span><span class="sxs-lookup"><span data-stu-id="10489-311">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="10489-312">На этом этапе вы готовы написать некоторый код.</span><span class="sxs-lookup"><span data-stu-id="10489-312">At this point you are ready to write some code.</span></span>

<span data-ttu-id="10489-313">Вы начнете с класса *кустомвисионаналисер* .</span><span class="sxs-lookup"><span data-stu-id="10489-313">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="10489-314">Вызовы **Пользовательская служба визуального распознавания** , выполненные в приведенном ниже коде, выполняются с помощью **REST API пользовательское визуальное распознавание**.</span><span class="sxs-lookup"><span data-stu-id="10489-314">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="10489-315">С помощью этой функции вы узнаете, как реализовать этот API и использовать его (это полезно для понимания того, как реализовать что-то подобное).</span><span class="sxs-lookup"><span data-stu-id="10489-315">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="10489-316">Имейте в виду, что корпорация Майкрософт предлагает **пакет SDK для пользовательская служба визуального распознавания** , который также можно использовать для вызова службы.</span><span class="sxs-lookup"><span data-stu-id="10489-316">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="10489-317">Дополнительные сведения см. в статье [ПОЛЬЗОВАТЕЛЬСКАЯ служба визуального распознавания SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .</span><span class="sxs-lookup"><span data-stu-id="10489-317">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="10489-318">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="10489-318">This class is responsible for:</span></span>

-   <span data-ttu-id="10489-319">Загрузка последнего образа, записанного в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="10489-319">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="10489-320">Отправка массива байтов в экземпляр *Пользовательская служба визуального распознавания* Azure для анализа.</span><span class="sxs-lookup"><span data-stu-id="10489-320">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="10489-321">Получение ответа в виде строки JSON.</span><span class="sxs-lookup"><span data-stu-id="10489-321">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="10489-322">Десериализация ответа и передача полученного *прогноза* классу *сценеорганисер* , который будет позаботиться о том, как должен отображаться ответ.</span><span class="sxs-lookup"><span data-stu-id="10489-322">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="10489-323">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-323">To create this class:</span></span>

1.  <span data-ttu-id="10489-324">Щелкните правой кнопкой мыши *папку Asset* , расположенную на *панели проект*, и выберите команду **создать > папку**.</span><span class="sxs-lookup"><span data-stu-id="10489-324">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="10489-325">Вызовите **скрипты** папки.</span><span class="sxs-lookup"><span data-stu-id="10489-325">Call the folder **Scripts**.</span></span>

    ![Создать папку скриптов](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="10489-327">Дважды щелкните только что созданную папку, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="10489-327">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="10489-328">Щелкните правой кнопкой мыши внутри папки и выберите команду **создать**  >  **\# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-328">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="10489-329">Назовите сценарий *кустомвисионаналисер*.</span><span class="sxs-lookup"><span data-stu-id="10489-329">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="10489-330">Дважды щелкните новый скрипт *кустомвисионаналисер* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-330">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="10489-331">Обновите пространства имен в верхней части файла, чтобы они соответствовали следующим условиям.</span><span class="sxs-lookup"><span data-stu-id="10489-331">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="10489-332">В классе *кустомвисионаналисер* добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="10489-332">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="10489-333">Убедитесь, что вы вставили **ключ прогноза** в переменную **Предиктионкэй** и свою **конечную точку прогнозирования** в переменную **предиктионендпоинт** .</span><span class="sxs-lookup"><span data-stu-id="10489-333">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="10489-334">Вы скопировали их в *Блокнот* ранее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="10489-334">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="10489-335">Необходимо добавить код для " **спящего" ()** , чтобы инициализировать переменную экземпляра:</span><span class="sxs-lookup"><span data-stu-id="10489-335">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="10489-336">Удалите методы **Start ()** и **Update ()**.</span><span class="sxs-lookup"><span data-stu-id="10489-336">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="10489-337">Затем добавьте соподпрограмму (с помощью статического метода **жетимажеасбитеаррай ()** ниже), который будет получать результаты анализа изображения, захваченного классом *имажекаптуре* .</span><span class="sxs-lookup"><span data-stu-id="10489-337">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="10489-338">В соподпрограмме **аналисеимажекаптуре** есть вызов класса *сценеорганисер* , который вы еще создали.</span><span class="sxs-lookup"><span data-stu-id="10489-338">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="10489-339">Поэтому **оставьте эти строки комментариями в настоящий момент**.</span><span class="sxs-lookup"><span data-stu-id="10489-339">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="10489-340">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10489-340">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="10489-341">Глава 7. Создание класса Кустомвисионобжектс</span><span class="sxs-lookup"><span data-stu-id="10489-341">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="10489-342">Класс, который вы создадите, теперь является классом *кустомвисионобжектс* .</span><span class="sxs-lookup"><span data-stu-id="10489-342">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="10489-343">Этот скрипт содержит несколько объектов, используемых другими классами для сериализации и десериализации вызовов, выполненных в *Пользовательская служба визуального распознавания*.</span><span class="sxs-lookup"><span data-stu-id="10489-343">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="10489-344">Важно отметить конечную точку, которую предоставляет Пользовательская служба визуального распознавания, так как следующая структура JSON настроена для работы с [*пользовательское визуальное распознавание PREDICTION v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="10489-344">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="10489-345">Если у вас другая версия, может потребоваться обновить приведенную ниже структуру.</span><span class="sxs-lookup"><span data-stu-id="10489-345">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="10489-346">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-346">To create this class:</span></span>

1.  <span data-ttu-id="10489-347">Щелкните правой кнопкой мыши в папке **Scripts** , а затем выберите команду **создать**  >  **\# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-347">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="10489-348">Вызовите скрипт *кустомвисионобжектс*.</span><span class="sxs-lookup"><span data-stu-id="10489-348">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="10489-349">Дважды щелкните новый скрипт **кустомвисионобжектс** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-349">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="10489-350">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="10489-350">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="10489-351">Удалите методы **Start ()** и **Update ()** внутри класса *кустомвисионобжектс* . Этот класс теперь должен быть пустым.</span><span class="sxs-lookup"><span data-stu-id="10489-351">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="10489-352">Добавьте следующие классы **за пределами** класса *кустомвисионобжектс* .</span><span class="sxs-lookup"><span data-stu-id="10489-352">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="10489-353">Эти объекты используются библиотекой *Newtonsoft* для сериализации и десериализации данных ответа:</span><span class="sxs-lookup"><span data-stu-id="10489-353">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="10489-354">Глава 8. Создание класса Воицерекогнизер</span><span class="sxs-lookup"><span data-stu-id="10489-354">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="10489-355">Этот класс будет распознавать речевой ввод пользователя.</span><span class="sxs-lookup"><span data-stu-id="10489-355">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="10489-356">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-356">To create this class:</span></span>

1.  <span data-ttu-id="10489-357">Щелкните правой кнопкой мыши в папке **Scripts** , а затем выберите команду **создать**  >  **\# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-357">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="10489-358">Вызовите скрипт *воицерекогнизер*.</span><span class="sxs-lookup"><span data-stu-id="10489-358">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="10489-359">Дважды щелкните новый скрипт **воицерекогнизер** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-359">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="10489-360">Добавьте следующие пространства имен над классом *воицерекогнизер* :</span><span class="sxs-lookup"><span data-stu-id="10489-360">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="10489-361">Затем добавьте следующие переменные в класс *воицерекогнизер* над методом *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="10489-361">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="10489-362">Добавьте методы " **спящий ()** " и " **Начало" ()** , второй из которых будет настраивать *Ключевые слова* пользователя, распознаваемые при связывании тега с изображением:</span><span class="sxs-lookup"><span data-stu-id="10489-362">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="10489-363">Удалите метод **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-363">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="10489-364">Добавьте следующий обработчик, вызываемый при распознавании речевого ввода:</span><span class="sxs-lookup"><span data-stu-id="10489-364">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="10489-365">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10489-365">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="10489-366">Не беспокойтесь о коде, который может показаться ошибочным, так как в ближайшее время будут предоставлены дальнейшие занятия, которые будут устранены.</span><span class="sxs-lookup"><span data-stu-id="10489-366">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="10489-367">Глава 9. Создание класса Кустомвисионтраинер</span><span class="sxs-lookup"><span data-stu-id="10489-367">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="10489-368">Этот класс будет связывать серию веб-вызовов для обучения *Пользовательская служба визуального распознавания*.</span><span class="sxs-lookup"><span data-stu-id="10489-368">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="10489-369">Каждый вызов будет подробно рассмотрен прямо над кодом.</span><span class="sxs-lookup"><span data-stu-id="10489-369">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="10489-370">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-370">To create this class:</span></span>

1.  <span data-ttu-id="10489-371">Щелкните правой кнопкой мыши в папке **Scripts** , а затем выберите команду **создать**  >  **\# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-371">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="10489-372">Вызовите скрипт *кустомвисионтраинер*.</span><span class="sxs-lookup"><span data-stu-id="10489-372">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="10489-373">Дважды щелкните новый скрипт *кустомвисионтраинер* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-373">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="10489-374">Добавьте следующие пространства имен над классом *кустомвисионтраинер* :</span><span class="sxs-lookup"><span data-stu-id="10489-374">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="10489-375">Затем добавьте следующие переменные в класс *кустомвисионтраинер* над методом **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-375">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="10489-376">URL-адрес обучения, используемый здесь, приведен в документации по *пользовательское визуальное распознавание обучения 1,2* и имеет структуру: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="10489-376">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="10489-377">Дополнительные сведения см. в [*справочном справочнике по пользовательское визуальное распознавание Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="10489-377">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="10489-378">Важно отметить, что конечная точка, предоставляемая Пользовательская служба визуального распознавания, обеспечивает режим обучения, так как используемая структура JSON (в классе **кустомвисионобжектс** ) настроена для работы с [*пользовательское визуальное распознавание Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="10489-378">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="10489-379">При наличии другой версии может потребоваться обновить структуру *объектов* .</span><span class="sxs-lookup"><span data-stu-id="10489-379">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="10489-380">Убедитесь, что вы добавили **ключ службы** (ключ обучения) и значение **идентификатора проекта** , которое вы заговорили ранее. Это значения, [собранные на портале ранее в ходе курса (глава 2, шаг 10 и выше)](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="10489-380">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="10489-381">Добавьте следующие методы **Start ()** и **спящего режима ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-381">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="10489-382">Эти методы вызываются при инициализации и содержат вызов для настройки пользовательского интерфейса:</span><span class="sxs-lookup"><span data-stu-id="10489-382">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="10489-383">Удалите метод **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-383">Delete the **Update()** method.</span></span> <span data-ttu-id="10489-384">Этот класс не будет нужен.</span><span class="sxs-lookup"><span data-stu-id="10489-384">This class will not need it.</span></span>

7.  <span data-ttu-id="10489-385">Добавьте метод **рекуесттагселектион ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-385">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="10489-386">Этот метод является первым, который вызывается, когда изображение было записано и сохранено на устройстве и теперь готово к отправке в *Пользовательская служба визуального распознавания*, чтобы обучить его.</span><span class="sxs-lookup"><span data-stu-id="10489-386">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="10489-387">Этот метод отображает в пользовательском интерфейсе обучения набор ключевых слов, которые пользователь может использовать для отметки записанного изображения.</span><span class="sxs-lookup"><span data-stu-id="10489-387">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="10489-388">Он также оповещает класс *воицерекогнизер* , чтобы начать прослушивание пользователя для ввода голоса.</span><span class="sxs-lookup"><span data-stu-id="10489-388">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="10489-389">Добавьте метод **верифитаг ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-389">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="10489-390">Этот метод будет принимать ввод голоса, распознаваемый классом **воицерекогнизер** , и проверять его допустимость, а затем начинать процесс обучения.</span><span class="sxs-lookup"><span data-stu-id="10489-390">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="10489-391">Добавьте метод **субмитимажефортраининг ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-391">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="10489-392">Этот метод начнет процесс обучения Пользовательская служба визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="10489-392">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="10489-393">Первым шагом является получение **идентификатора тега** из службы, связанной с проверенным речевым входом пользователя.</span><span class="sxs-lookup"><span data-stu-id="10489-393">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="10489-394">Затем **идентификатор тега** будет отправлен вместе с изображением.</span><span class="sxs-lookup"><span data-stu-id="10489-394">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="10489-395">Добавьте метод **траинкустомвисионпрожект ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-395">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="10489-396">После отправки и пометки образа будет вызван этот метод.</span><span class="sxs-lookup"><span data-stu-id="10489-396">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="10489-397">Он создаст новую итерацию, которая будет обучена всеми предыдущими изображениями, отправленными в службу, а также только что отправленное изображение.</span><span class="sxs-lookup"><span data-stu-id="10489-397">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="10489-398">После завершения обучения этот метод вызывает метод, чтобы задать созданную **итерацию** **по умолчанию**, чтобы конечная точка, используемая для анализа, была последней обученной итерацией.</span><span class="sxs-lookup"><span data-stu-id="10489-398">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="10489-399">Добавьте метод **сетдефаултитератион ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-399">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="10489-400">Этот метод задаст ранее созданную и обученную итерацию *по умолчанию*.</span><span class="sxs-lookup"><span data-stu-id="10489-400">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="10489-401">После завершения этот метод должен удалить предыдущую итерацию, существующую в службе.</span><span class="sxs-lookup"><span data-stu-id="10489-401">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="10489-402">На момент написания этого курса в службе можно одновременно использовать не более десяти итераций (10) одновременно.</span><span class="sxs-lookup"><span data-stu-id="10489-402">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="10489-403">Добавьте метод **делетепревиауситератион ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-403">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="10489-404">Этот метод найдет и удалит предыдущую нестандартную итерацию:</span><span class="sxs-lookup"><span data-stu-id="10489-404">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="10489-405">Последний метод для добавления в этом классе — метод **жетимажеасбитеаррай ()** , используемый в веб-вызовах для преобразования изображения, захваченного в массив байтов.</span><span class="sxs-lookup"><span data-stu-id="10489-405">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="10489-406">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10489-406">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="10489-407">Глава 10. Создание класса Сценеорганисер</span><span class="sxs-lookup"><span data-stu-id="10489-407">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="10489-408">Этот класс будет:</span><span class="sxs-lookup"><span data-stu-id="10489-408">This class will:</span></span>

-   <span data-ttu-id="10489-409">Создайте объект **курсора** для присоединения к основной камере.</span><span class="sxs-lookup"><span data-stu-id="10489-409">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="10489-410">Создайте объект **Label** , который будет отображаться, когда служба распознает реальные объекты.</span><span class="sxs-lookup"><span data-stu-id="10489-410">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="10489-411">Настройте основную камеру, присоединив к ней соответствующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="10489-411">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="10489-412">В **режиме анализа**, порождение меток во время выполнения, в соответствующем мировом пространстве относительно положения основной камеры и вывода данных, полученных от пользовательская служба визуального распознавания.</span><span class="sxs-lookup"><span data-stu-id="10489-412">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="10489-413">В **режиме обучения** Порождение пользовательского интерфейса, в котором будут отображаться различные этапы процесса обучения.</span><span class="sxs-lookup"><span data-stu-id="10489-413">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="10489-414">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-414">To create this class:</span></span>

1.  <span data-ttu-id="10489-415">Щелкните правой кнопкой мыши в папке **Scripts** , а затем выберите команду **создать**  >  **\# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-415">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="10489-416">Назовите сценарий *сценеорганисер*.</span><span class="sxs-lookup"><span data-stu-id="10489-416">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="10489-417">Дважды щелкните новый скрипт *сценеорганисер* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-417">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="10489-418">Вам потребуется только одно пространство имен, удалите остальные из класса *сценеорганисер* .</span><span class="sxs-lookup"><span data-stu-id="10489-418">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="10489-419">Затем добавьте следующие переменные в класс *сценеорганисер* над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="10489-419">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="10489-420">Удалите методы **Start ()** и **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="10489-420">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="10489-421">Непосредственно под переменными добавьте метод " **спящий ()** ", который инициализирует класс и настраивает сцену.</span><span class="sxs-lookup"><span data-stu-id="10489-421">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="10489-422">Теперь добавьте метод **креатекамеракурсор ()** , который создает и позиционирует основной курсор камеры, и метод **CreateLabel ()** , который создает объект **метки анализа** .</span><span class="sxs-lookup"><span data-stu-id="10489-422">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="10489-423">Добавьте метод **сеткамерастатус ()** , который будет работать с сообщениями, предназначенными для сетки текста, предоставляющей состояние камеры.</span><span class="sxs-lookup"><span data-stu-id="10489-423">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="10489-424">Добавьте методы **плацеаналисислабел ()** и **сеттагстоластлабел ()** , которые будут порождать и отображать данные из пользовательская служба визуального распознавания в сцене.</span><span class="sxs-lookup"><span data-stu-id="10489-424">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="10489-425">Наконец, добавьте метод **креатетраинингуи ()** , который ПОРОЖДАЕТ пользовательский интерфейс, отображающий несколько стадий процесса обучения, когда приложение находится в режиме обучения.</span><span class="sxs-lookup"><span data-stu-id="10489-425">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="10489-426">Этот метод также будет использоваться для создания объекта состояния камеры.</span><span class="sxs-lookup"><span data-stu-id="10489-426">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="10489-427">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10489-427">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10489-428">Прежде чем продолжить, откройте класс **кустомвисионаналисер** и в методе **аналиселастимажекаптуред ()** *раскомментируйте* следующие строки:</span><span class="sxs-lookup"><span data-stu-id="10489-428">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="10489-429">Глава 11. Создание класса Имажекаптуре</span><span class="sxs-lookup"><span data-stu-id="10489-429">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="10489-430">Следующий класс, который предстоит создать, — это класс *имажекаптуре* .</span><span class="sxs-lookup"><span data-stu-id="10489-430">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="10489-431">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="10489-431">This class is responsible for:</span></span>

-   <span data-ttu-id="10489-432">Запись изображения с помощью камеры HoloLens и сохранение его в папке *приложения* .</span><span class="sxs-lookup"><span data-stu-id="10489-432">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="10489-433">Обработка жестов касания от пользователя.</span><span class="sxs-lookup"><span data-stu-id="10489-433">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="10489-434">Поддержание значения *перечисления* , определяющего, будет ли приложение запускаться в режиме *анализа* или *обучения* .</span><span class="sxs-lookup"><span data-stu-id="10489-434">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="10489-435">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10489-435">To create this class:</span></span>

1.  <span data-ttu-id="10489-436">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="10489-436">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="10489-437">Щелкните правой кнопкой мыши внутри папки и выберите команду **создать > \# Сценарий C**.</span><span class="sxs-lookup"><span data-stu-id="10489-437">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="10489-438">Назовите сценарий *имажекаптуре*.</span><span class="sxs-lookup"><span data-stu-id="10489-438">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="10489-439">Дважды щелкните новый скрипт **имажекаптуре** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-439">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="10489-440">Замените пространства имен в верхней части файла следующим:</span><span class="sxs-lookup"><span data-stu-id="10489-440">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="10489-441">Затем добавьте следующие переменные в класс *имажекаптуре* над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="10489-441">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="10489-442">Теперь необходимо добавить код для методов **"спящий" ()** и **"начало" ()** :</span><span class="sxs-lookup"><span data-stu-id="10489-442">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="10489-443">Реализуйте обработчик, который будет вызываться при возникновении жеста касания.</span><span class="sxs-lookup"><span data-stu-id="10489-443">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="10489-444">В режиме *анализа* метод **тафандлер** выступает в качестве параметра для запуска или завершения цикла записи фотографий.</span><span class="sxs-lookup"><span data-stu-id="10489-444">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="10489-445">В режиме *обучения* он будет записывать изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="10489-445">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="10489-446">Когда курсор горит зеленым, это означает, что Камера доступна для получения образа.</span><span class="sxs-lookup"><span data-stu-id="10489-446">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="10489-447">Красный цвет курсора означает, что камера занята.</span><span class="sxs-lookup"><span data-stu-id="10489-447">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="10489-448">Добавьте метод, используемый приложением для запуска процесса записи образа и сохранения образа.</span><span class="sxs-lookup"><span data-stu-id="10489-448">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="10489-449">Добавьте обработчики, которые будут вызываться при записи фотографии и при ее готовности к анализу.</span><span class="sxs-lookup"><span data-stu-id="10489-449">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="10489-450">Затем результат передается в *кустомвисионаналисер* или *кустомвисионтраинер* в зависимости от того, в каком режиме установлен код.</span><span class="sxs-lookup"><span data-stu-id="10489-450">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="10489-451">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10489-451">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="10489-452">Теперь, когда все сценарии завершены, вернитесь в редактор Unity, а затем перетащите класс **сценеорганисер** из папки **Scripts** в **основной объект Camera** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="10489-452">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="10489-453">Глава 12-перед сборкой</span><span class="sxs-lookup"><span data-stu-id="10489-453">Chapter 12 - Before building</span></span>

<span data-ttu-id="10489-454">Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10489-454">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="10489-455">Перед этим убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="10489-455">Before you do, ensure that:</span></span>

- <span data-ttu-id="10489-456">Все параметры, упомянутые в [главе 2](#chapter-2---training-your-custom-vision-project) , заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="10489-456">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="10489-457">Все поля на **главной камере**, панели инспектора, назначаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="10489-457">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="10489-458">**Сценеорганисер** скрипта прикреплен к **главному объекту Camera** .</span><span class="sxs-lookup"><span data-stu-id="10489-458">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="10489-459">Убедитесь, что вы вставили **ключ прогноза** в переменную **предиктионкэй** .</span><span class="sxs-lookup"><span data-stu-id="10489-459">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="10489-460">Вы вставили **конечную точку прогнозирования** в переменную **предиктионендпоинт** .</span><span class="sxs-lookup"><span data-stu-id="10489-460">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="10489-461">Вы вставили **ключ обучения** в переменную **траинингкэй** класса *кустомвисионтраинер* .</span><span class="sxs-lookup"><span data-stu-id="10489-461">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="10489-462">Вы вставили **идентификатор проекта** в переменную **projectId** класса *кустомвисионтраинер* .</span><span class="sxs-lookup"><span data-stu-id="10489-462">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="10489-463">Глава 13. Создание и загружать неопубликованные приложения</span><span class="sxs-lookup"><span data-stu-id="10489-463">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="10489-464">Чтобы начать процесс *сборки* :</span><span class="sxs-lookup"><span data-stu-id="10489-464">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="10489-465">Выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="10489-465">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="10489-466">**\# Проекты тактов Unity C**.</span><span class="sxs-lookup"><span data-stu-id="10489-466">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="10489-467">Щелкните **Построить**.</span><span class="sxs-lookup"><span data-stu-id="10489-467">Click **Build**.</span></span> <span data-ttu-id="10489-468">Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="10489-468">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="10489-469">Создайте эту папку сейчас и назовите ее **app** Name.</span><span class="sxs-lookup"><span data-stu-id="10489-469">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="10489-470">Затем в выбранной папке **приложения** щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="10489-470">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="10489-471">Unity начнет сборку проекта в папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="10489-471">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="10489-472">После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="10489-472">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="10489-473">Для развертывания на HoloLens выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="10489-473">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="10489-474">Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**.</span><span class="sxs-lookup"><span data-stu-id="10489-474">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="10489-475">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="10489-475">To do this:</span></span>

    1.  <span data-ttu-id="10489-476">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="10489-476">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="10489-477">Выберите **Сетевые &**  >    >  **Дополнительные параметры** сети Интернет Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="10489-477">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="10489-478">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="10489-478">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="10489-479">Затем вернитесь к **параметрам** и **Обновите & безопасности**  >  **для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="10489-479">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="10489-480">Задайте **режим разработчика на**.</span><span class="sxs-lookup"><span data-stu-id="10489-480">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="10489-481">Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10489-481">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="10489-482">В *конфигурации решения* выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="10489-482">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="10489-483">На *платформе решения* выберите **x86, удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="10489-483">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="10489-484">Вам будет предложено вставить **IP-адрес** удаленного устройства (в данном случае это HoloLens).</span><span class="sxs-lookup"><span data-stu-id="10489-484">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![Задание IP-адреса](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="10489-486">Перейдите в меню **Сборка** и щелкните **Развернуть решение** , чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10489-486">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="10489-487">Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="10489-487">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="10489-488">Чтобы выполнить развертывание в иммерсивное *виртуальную* гарнитуру, задайте для **платформы решения** значение локальный компьютер и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**).</span><span class="sxs-lookup"><span data-stu-id="10489-488">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="10489-489">Затем выполните развертывание на локальном компьютере с помощью пункта меню " **Сборка** " и выберите *Развернуть решение*.</span><span class="sxs-lookup"><span data-stu-id="10489-489">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="10489-490">Чтобы использовать приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="10489-490">To use the application:</span></span>

<span data-ttu-id="10489-491">Чтобы переключить функциональные возможности приложения между режимом *обучения* и режимом *прогнозирования* , необходимо обновить переменную **аппмоде** , расположенную в методе **спящего режима ()** , расположенном в классе *имажекаптуре* .</span><span class="sxs-lookup"><span data-stu-id="10489-491">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="10489-492">или</span><span class="sxs-lookup"><span data-stu-id="10489-492">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="10489-493">В режиме *обучения* :</span><span class="sxs-lookup"><span data-stu-id="10489-493">In *Training* mode:</span></span>

- <span data-ttu-id="10489-494">Взгляните на **мышь** или **клавиатуру** и используйте **жест касания**.</span><span class="sxs-lookup"><span data-stu-id="10489-494">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="10489-495">Затем появится текст с запросом на указание тега.</span><span class="sxs-lookup"><span data-stu-id="10489-495">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="10489-496">Например, с помощью **мыши** или **клавиатуры**.</span><span class="sxs-lookup"><span data-stu-id="10489-496">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="10489-497">В режиме *прогнозирования* :</span><span class="sxs-lookup"><span data-stu-id="10489-497">In *Prediction* mode:</span></span>

- <span data-ttu-id="10489-498">Взгляните на объект и используйте **жест касания**.</span><span class="sxs-lookup"><span data-stu-id="10489-498">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="10489-499">Появится текст, предоставляющий обнаруженный объект, с наибольшей вероятностью (это нормализованное значение).</span><span class="sxs-lookup"><span data-stu-id="10489-499">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="10489-500">Глава 14. Оценка и усовершенствование модели Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-500">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="10489-501">Чтобы сделать службу более точной, необходимо продолжить обучение модели, используемой для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="10489-501">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="10489-502">Это достигается благодаря использованию нового приложения, в котором используются оба режима *обучения* и *прогнозирования* , при этом требуется посетить портал, что рассматривается в этой главе.</span><span class="sxs-lookup"><span data-stu-id="10489-502">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="10489-503">Будьте готовы к повторному посещению портала, чтобы постоянно улучшать модель.</span><span class="sxs-lookup"><span data-stu-id="10489-503">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="10489-504">Снова перейдите на портал Azure Пользовательское визуальное распознавание и в проекте выберите вкладку *прогнозы* (в верхнем центре страницы):</span><span class="sxs-lookup"><span data-stu-id="10489-504">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![Выбор вкладки "прогнозы"](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="10489-506">Вы увидите все образы, которые были отправлены в вашу службу во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="10489-506">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="10489-507">При наведении указателя мыши на изображения они будут предоставлять прогнозы, сделанные для этого образа:</span><span class="sxs-lookup"><span data-stu-id="10489-507">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![Список прогнозирующих изображений](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="10489-509">Выберите один из образов, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="10489-509">Select one of your images to open it.</span></span> <span data-ttu-id="10489-510">После открытия вы увидите прогнозы, сделанные для этого изображения справа.</span><span class="sxs-lookup"><span data-stu-id="10489-510">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="10489-511">Если прогнозы были правильными и вы хотите добавить этот образ в модель обучения службы, щелкните поле ввода " *Мои теги* " и выберите тег, который нужно связать.</span><span class="sxs-lookup"><span data-stu-id="10489-511">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="10489-512">По завершении нажмите кнопку *сохранить и закрыть* в правом нижнем углу и продолжайте переходить к следующему изображению.</span><span class="sxs-lookup"><span data-stu-id="10489-512">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![Выберите изображение для открытия](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="10489-514">Когда вы вернетесь к сетке изображений, вы заметите, что изображения, в которые были добавлены теги (и сохранены), будут удалены.</span><span class="sxs-lookup"><span data-stu-id="10489-514">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="10489-515">Если вы нашли какие-либо изображения, на которых нет элемента с тегами, их можно удалить, щелкнув такт на этом изображении (это можно сделать для нескольких изображений), а затем нажать кнопку *Удалить* в правом верхнем углу страницы сетки.</span><span class="sxs-lookup"><span data-stu-id="10489-515">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="10489-516">В следующем всплывающем окне можно щелкнуть *Да, удалить* или *нет*, чтобы подтвердить удаление или отменить его соответственно.</span><span class="sxs-lookup"><span data-stu-id="10489-516">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![Удаление изображений](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="10489-518">Когда вы будете готовы к продолжению, нажмите зеленую кнопку « *обучение* » в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="10489-518">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="10489-519">Модель службы будет обучена всеми предоставленными вами образами (что сделает его более точным).</span><span class="sxs-lookup"><span data-stu-id="10489-519">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="10489-520">После завершения обучения обязательно нажмите кнопку *сделать по умолчанию* , чтобы ваш *прогнозирующий URL-адрес* продолжал использовать самую последнюю итерацию службы.</span><span class="sxs-lookup"><span data-stu-id="10489-520">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="10489-521">![Начать обучение модель службы ](images/AzureLabs-Lab302b-39.png) ![ Выбор параметра «сделать по умолчанию»](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="10489-521">![Start training service model](images/AzureLabs-Lab302b-39.png) ![Select make default option](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="10489-522">Законченное приложение API Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="10489-522">Your finished Custom Vision API application</span></span>

<span data-ttu-id="10489-523">Поздравляем! вы создали приложение для смешанной реальности, которое использует API Azure Пользовательское визуальное распознавание для распознавания реальных объектов, обучения модели службы и получения уверенности в том, что появлялось.</span><span class="sxs-lookup"><span data-stu-id="10489-523">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![Пример проекта завершен](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="10489-525">Дополнительные упражнения</span><span class="sxs-lookup"><span data-stu-id="10489-525">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="10489-526">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="10489-526">Exercise 1</span></span>

<span data-ttu-id="10489-527">Обучить **Пользовательская служба визуального распознавания** для распознавания большего числа объектов.</span><span class="sxs-lookup"><span data-stu-id="10489-527">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="10489-528">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="10489-528">Exercise 2</span></span>

<span data-ttu-id="10489-529">Чтобы расширить свои знания, выполните следующие упражнения.</span><span class="sxs-lookup"><span data-stu-id="10489-529">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="10489-530">Подавать звуковой сигнал при распознавании объекта.</span><span class="sxs-lookup"><span data-stu-id="10489-530">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="10489-531">Упражнение 3</span><span class="sxs-lookup"><span data-stu-id="10489-531">Exercise 3</span></span>

<span data-ttu-id="10489-532">Используйте API для переобучения службы с теми же изображениями, которые анализирует приложение, чтобы сделать службу более точной (одновременное прогнозирование и обучение).</span><span class="sxs-lookup"><span data-stu-id="10489-532">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>