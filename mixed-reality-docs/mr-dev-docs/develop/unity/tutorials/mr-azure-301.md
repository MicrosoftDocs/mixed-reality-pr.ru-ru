---
title: 301. Смешанная реальность и Azure — перевод на другие языки
description: Пройдите этот курс, чтобы узнать, как реализовать API перевода текстов Azure в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, текст переводчика, hololens, иммерсивное, VR, языковой перевод, Windows 10, Visual Studio
ms.openlocfilehash: 0b7e7c2e4146d3c60e62c25764aae48260fdf3ef
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583290"
---
# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="451cf-104">301. Смешанная реальность и Azure: перевод с одного языка на другой</span><span class="sxs-lookup"><span data-stu-id="451cf-104">MR and Azure 301: Language translation</span></span>

<br>

>[!NOTE]
><span data-ttu-id="451cf-105">Руководства Mixed Reality Academy были разработаны для иммерсивных гарнитур HoloLens (1-го поколения) и иммерсивных гарнитур Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="451cf-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="451cf-106">Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="451cf-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="451cf-107">Данные руководства **_не_** будут обновляться с учетом последних наборов инструментов или возможностей взаимодействия для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="451cf-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="451cf-108">Они будут сохранены для работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="451cf-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="451cf-109">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="451cf-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="451cf-110">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="451cf-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="451cf-111">В этом курсе вы узнаете, как добавлять возможности перевода в приложение смешанной реальности с помощью Cognitive Services Azure с API перевода текстов.</span><span class="sxs-lookup"><span data-stu-id="451cf-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Окончательный продукт](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="451cf-113">API перевода текстов — это служба перевода, которая работает практически в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="451cf-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="451cf-114">Служба является облачной, и с помощью REST APIного вызова приложение может использовать технологию нейронного машинного перевода для перевода текста на другой язык.</span><span class="sxs-lookup"><span data-stu-id="451cf-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="451cf-115">Дополнительные сведения см. на [странице API перевода текстов Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="451cf-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="451cf-116">После завершения этого курса у вас будет приложение смешанной реальности, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="451cf-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="451cf-117">Пользователь будет говорить на микрофон, подключенный к головной гарнитуре (VR) (или встроенному микрофону HoloLens).</span><span class="sxs-lookup"><span data-stu-id="451cf-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="451cf-118">Приложение запишет диктовку и отправит ее в API перевода текстов Azure.</span><span class="sxs-lookup"><span data-stu-id="451cf-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="451cf-119">Результат перевода будет отображаться в простой группе пользовательского интерфейса в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="451cf-120">В этом курсе вы узнаете, как получить результаты из службы переводчиков в примере приложения на основе Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="451cf-121">Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.</span><span class="sxs-lookup"><span data-stu-id="451cf-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="451cf-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="451cf-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="451cf-123">Курс</span><span class="sxs-lookup"><span data-stu-id="451cf-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="451cf-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="451cf-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="451cf-125"><a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="451cf-125"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="451cf-126">301. Смешанная реальность и Azure: перевод с одного языка на другой</span><span class="sxs-lookup"><span data-stu-id="451cf-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="451cf-127">✔️</span><span class="sxs-lookup"><span data-stu-id="451cf-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="451cf-128">✔️</span><span class="sxs-lookup"><span data-stu-id="451cf-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="451cf-129">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="451cf-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="451cf-130">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="451cf-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="451cf-131">При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="451cf-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="451cf-132">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="451cf-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="451cf-133">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="451cf-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="451cf-134">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="451cf-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="451cf-135">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](../../install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="451cf-135">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="451cf-136">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="451cf-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="451cf-137">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="451cf-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="451cf-138">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="451cf-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="451cf-139">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="451cf-139">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="451cf-140">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="451cf-140">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="451cf-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="451cf-141">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="451cf-142">Высокодоступная [гарнитура Windows Mixed Reality (VR)](../../../discover/immersive-headset-hardware-details.md) или [Microsoft HoloLens](/hololens/hololens1-hardware) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="451cf-142">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="451cf-143">Набор наушников со встроенным микрофоном (если у гарнитуры нет встроенного MIC и динамиков);</span><span class="sxs-lookup"><span data-stu-id="451cf-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="451cf-144">Доступ к Интернету для получения сведений о настройке и переводе Azure</span><span class="sxs-lookup"><span data-stu-id="451cf-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="451cf-145">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="451cf-145">Before you start</span></span>

- <span data-ttu-id="451cf-146">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="451cf-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="451cf-147">Код в этом учебнике позволит вам записывать данные с микрофона по умолчанию, подключенного к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="451cf-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="451cf-148">Убедитесь, что в качестве устройства микрофона по умолчанию выбрано устройство, которое планируется использовать для записи голоса.</span><span class="sxs-lookup"><span data-stu-id="451cf-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="451cf-149">Чтобы разрешить компьютеру Включить диктовку, перейдите в раздел **параметры > конфиденциальность > речь, ввод рукописных данных & ввода** и нажмите кнопку **включить речевые службы и введите предложения**.</span><span class="sxs-lookup"><span data-stu-id="451cf-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="451cf-150">Если вы используете микрофон и наушники, подключенные к гарнитуре (или встроенные в), убедитесь, что параметр "при износе гарнитуры, переключиться на микрофон гарнитуры" включен в **параметрах > смешанной реальности > аудио и речь**.</span><span class="sxs-lookup"><span data-stu-id="451cf-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Параметры смешанной реальности](images/AzureLabs-Lab1-00-5.png)

   ![Настройка микрофона](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="451cf-153">Имейте в виду, что если вы разрабатываете для использования в этой лаборатории экспериментальной гарнитуры, вы можете столкнуться с проблемами устройств вывода звука.</span><span class="sxs-lookup"><span data-stu-id="451cf-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="451cf-154">Это вызвано проблемой с Unity, которая исправлена в более поздних версиях Unity (Unity 2018,2).</span><span class="sxs-lookup"><span data-stu-id="451cf-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="451cf-155">Эта ошибка предотвращает изменение устройства выхода звука по умолчанию во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="451cf-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="451cf-156">Для решения этой проблемы убедитесь, что вы выполнили описанные выше действия, а затем закройте и снова откройте редактор, когда эта проблема будет представлена.</span><span class="sxs-lookup"><span data-stu-id="451cf-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="451cf-157">Глава 1 — портал Azure</span><span class="sxs-lookup"><span data-stu-id="451cf-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="451cf-158">Чтобы использовать API-интерфейс Azure Translator, необходимо настроить экземпляр службы, чтобы сделать его доступным для приложения.</span><span class="sxs-lookup"><span data-stu-id="451cf-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="451cf-159">Войдите на  [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="451cf-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="451cf-160">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="451cf-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="451cf-161">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="451cf-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="451cf-162">После входа щелкните **New (создать** ) в левом верхнем углу и выполните поиск по запросу «API перевода текстов».</span><span class="sxs-lookup"><span data-stu-id="451cf-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="451cf-163">Нажмите клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="451cf-163">Select **Enter**.</span></span>

    ![Новый ресурс](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="451cf-165">Слово **New** может быть заменено на **создать ресурс** в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="451cf-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="451cf-166">На новой странице будет представлено описание службы *API перевода текстов* .</span><span class="sxs-lookup"><span data-stu-id="451cf-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="451cf-167">В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="451cf-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Создание службы API перевода текстов](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="451cf-169">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="451cf-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="451cf-170">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="451cf-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="451cf-171">Выберите подходящую **подписку**.</span><span class="sxs-lookup"><span data-stu-id="451cf-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="451cf-172">Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете *службу перевод текстов*, вам будет доступен бесплатный уровень (с именем F0).</span><span class="sxs-lookup"><span data-stu-id="451cf-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="451cf-173">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="451cf-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="451cf-174">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="451cf-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="451cf-175">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="451cf-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="451cf-176">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="451cf-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="451cf-177">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="451cf-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="451cf-178">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="451cf-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="451cf-179">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="451cf-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="451cf-180">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="451cf-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="451cf-181">Нажмите кнопку **создания**.</span><span class="sxs-lookup"><span data-stu-id="451cf-181">Select **Create**.</span></span>

        ![Нажмите кнопку Создать.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="451cf-183">После нажатия кнопки **создать** необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="451cf-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="451cf-184">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="451cf-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Уведомление о создании службы Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="451cf-186">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="451cf-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Перейдите к всплывающему окну ресурсов.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="451cf-188">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="451cf-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="451cf-189">Вы будете перенаправлены на новый экземпляр службы API перевода текстов.</span><span class="sxs-lookup"><span data-stu-id="451cf-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Страница службы API перевода текстов](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="451cf-191">В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="451cf-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="451cf-192">На странице *быстрого запуска* службы *перевод текстов* перейдите к первому шагу, *Возьмите ключи* и щелкните **ключи** (это можно также сделать, щелкнув синие клавиши-гиперссылки, расположенные в меню навигации службы, обозначенном значком ключа).</span><span class="sxs-lookup"><span data-stu-id="451cf-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="451cf-193">При этом будут раскрыты *ключи* службы.</span><span class="sxs-lookup"><span data-stu-id="451cf-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="451cf-194">Сделайте копию одного из отображаемых ключей, так как это потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="451cf-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="451cf-195">Глава 2 — Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="451cf-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="451cf-196">Настройка и тестирование иммерсивного наушников смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="451cf-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="451cf-197">Для этого курса не потребуется контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="451cf-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="451cf-198">Если вам нужна поддержка настройки иммерсивного головного телефона, выполните следующие [действия](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="451cf-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="451cf-199">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности и, как таковая, является хорошим шаблоном для других проектов:</span><span class="sxs-lookup"><span data-stu-id="451cf-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="451cf-200">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="451cf-200">Open *Unity* and click **New**.</span></span> 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="451cf-202">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="451cf-203">Вставка **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="451cf-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="451cf-204">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="451cf-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="451cf-205">Задайте для *расположения нужное расположение* (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="451cf-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="451cf-206">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="451cf-206">Then, click **Create project**.</span></span>

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="451cf-208">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="451cf-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="451cf-209">Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="451cf-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="451cf-210">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="451cf-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="451cf-211">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="451cf-211">Close the **Preferences** window.</span></span>

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="451cf-213">Затем перейдите в раздел **файл > параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора платформы** .</span><span class="sxs-lookup"><span data-stu-id="451cf-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="451cf-215">Перейдите в раздел **файл > параметры сборки** и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="451cf-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="451cf-216">**Целевое устройство** настроено для **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="451cf-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="451cf-217">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="451cf-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="451cf-218">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="451cf-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="451cf-219">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="451cf-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="451cf-220">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="451cf-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="451cf-221">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="451cf-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="451cf-222">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="451cf-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="451cf-223">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="451cf-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="451cf-224">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="451cf-224">A save window will appear.</span></span>

            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="451cf-226">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="451cf-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создать новую папку скриптов](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="451cf-228">Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_TranslationScene**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="451cf-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="451cf-230">Помните, что сцены Unity необходимо сохранять в папке *Assets* , так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="451cf-231">Создание папки «сцены» (и других аналогичных папок) — типичный способ структуризации проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="451cf-232">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="451cf-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="451cf-233">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="451cf-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="451cf-235">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="451cf-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="451cf-236">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="451cf-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="451cf-237">**Версия среды выполнения сценариев** должна быть **стабильной** (эквивалент .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="451cf-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="451cf-238">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="451cf-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="451cf-239">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="451cf-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="451cf-241">На вкладке **Параметры публикации** в разделе **возможности** установите флажок:</span><span class="sxs-lookup"><span data-stu-id="451cf-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="451cf-242">**InternetClient**;</span><span class="sxs-lookup"><span data-stu-id="451cf-242">**InternetClient**</span></span>
        2. <span data-ttu-id="451cf-243">**Микрофон**</span><span class="sxs-lookup"><span data-stu-id="451cf-243">**Microphone**</span></span>

            ![Обновляются параметры публикации.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="451cf-245">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность** Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="451cf-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновите параметры X R.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="451cf-247">Вернемся к **параметрам сборки**. *проекты C# для Unity* больше не заключаются; Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="451cf-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="451cf-248">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="451cf-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="451cf-249">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="451cf-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="451cf-250">Глава 3 — Настройка основной камеры</span><span class="sxs-lookup"><span data-stu-id="451cf-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="451cf-251">Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, [Скачайте этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), импортируйте его в проект как [*пользовательский пакет*](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="451cf-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="451cf-252">Вам все равно придется создать проект Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="451cf-253">На *панели Иерархия* вы найдете объект с названием **Главная камера**, этот объект представляет "головную точку представления", когда вы "внутри приложения".</span><span class="sxs-lookup"><span data-stu-id="451cf-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="451cf-254">На панели мониторинга Unity перед вами выберите **основную камеру GameObject**.</span><span class="sxs-lookup"><span data-stu-id="451cf-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="451cf-255">Вы заметите, что на *панели инспектора* (как правило, на панели мониторинга) отображаются различные компоненты этого *GameObject*, с помощью кнопки *преобразовывать* в верхней части, за которой следует *Камера* и некоторые другие компоненты.</span><span class="sxs-lookup"><span data-stu-id="451cf-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="451cf-256">Необходимо будет сбросить преобразование основной камеры, чтобы она правильно расположиться.</span><span class="sxs-lookup"><span data-stu-id="451cf-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="451cf-257">Для этого щелкните значок **шестеренки** рядом с компонентом *преобразования* камеры и выберите **Сброс**.</span><span class="sxs-lookup"><span data-stu-id="451cf-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Сброс основного преобразования камеры.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="451cf-259">Компонент *преобразования* должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="451cf-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="451cf-260">Для этой *должности* задано значение **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="451cf-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="451cf-261">Для *вращения* задано значение **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="451cf-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="451cf-262">Для параметра *Scale* устанавливается значение **1, 1, 1** .</span><span class="sxs-lookup"><span data-stu-id="451cf-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Сведения о преобразовании для камеры](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="451cf-264">Затем, выбрав **основной объект Camera** , ознакомьтесь с разрядом с кнопкой **Добавить компонент** , расположенной в самом низу *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="451cf-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="451cf-265">Выберите эту кнопку и выполните поиск (для этого введите " *аудио-источник* " в поле поиска или перейдите к разделам) для компонента с названием " **источник звука** ", как показано ниже, и выберите его (нажмите клавишу ВВОД на нем).</span><span class="sxs-lookup"><span data-stu-id="451cf-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="451cf-266">Компонент " *звуковый источник* " будет добавлен на **основную камеру**, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="451cf-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Добавьте компонент "источник звука".](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="451cf-268">Для Microsoft HoloLens необходимо также изменить следующие компоненты, которые являются частью компонента **камеры** на **основной камере**:</span><span class="sxs-lookup"><span data-stu-id="451cf-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="451cf-269">**Снять флаги:** Сплошной цвет.</span><span class="sxs-lookup"><span data-stu-id="451cf-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="451cf-270">**Фоновый режим** "Черный, альфа 0" — шестнадцатеричный цвет: #00000000.</span><span class="sxs-lookup"><span data-stu-id="451cf-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="451cf-271">Глава 4 — настройка отладочного холста</span><span class="sxs-lookup"><span data-stu-id="451cf-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="451cf-272">Чтобы отобразить входные и выходные данные перевода, необходимо создать базовый пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="451cf-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="451cf-273">В этом курсе вы создадите объект пользовательского интерфейса Canvas с несколькими объектами "Text" для отображения данных.</span><span class="sxs-lookup"><span data-stu-id="451cf-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="451cf-274">Щелкните правой кнопкой мыши пустую область *панели Иерархия*, в разделе **Пользовательский интерфейс** добавьте **холст**.</span><span class="sxs-lookup"><span data-stu-id="451cf-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Добавить новый объект пользовательского интерфейса Canvas.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="451cf-276">Выбрав объект Canvas, на *панели инспектора* (в компоненте Canvas) измените **режим рендеринга** на **мировое пространство**.</span><span class="sxs-lookup"><span data-stu-id="451cf-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="451cf-277">Затем измените следующие параметры в *преобразовании Rect на панели инспектора*:</span><span class="sxs-lookup"><span data-stu-id="451cf-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="451cf-278">*POS-терминал*  -   **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="451cf-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="451cf-279">*Ширина* — 500</span><span class="sxs-lookup"><span data-stu-id="451cf-279">*Width* -    500</span></span>
    3. <span data-ttu-id="451cf-280">*Высота* 300</span><span class="sxs-lookup"><span data-stu-id="451cf-280">*Height* -   300</span></span>
    4. <span data-ttu-id="451cf-281">*Масштаб*  -  **X** 0,13 **Y** 0,13 **Z** 0,13</span><span class="sxs-lookup"><span data-stu-id="451cf-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Обновите преобразование Rect для холста.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="451cf-283">Щелкните правой кнопкой мыши **холст** на *панели Иерархия*, в разделе **Пользовательский интерфейс** и добавьте **панель**.</span><span class="sxs-lookup"><span data-stu-id="451cf-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="451cf-284">Эта **панель** предоставит фон текста, который будет отображаться в сцене.</span><span class="sxs-lookup"><span data-stu-id="451cf-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="451cf-285">Щелкните правой кнопкой мыши **панель** на *панели Иерархия*, в разделе **Пользовательский интерфейс** и добавьте **текстовый объект**.</span><span class="sxs-lookup"><span data-stu-id="451cf-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="451cf-286">Повторяйте тот же процесс, пока вы не создадите четыре текстовых объекта пользовательского интерфейса в целом (Подсказка: если у вас есть первый объект "Text", можно просто нажать клавишу **"Ctrl" + "+ 'd"**, чтобы продублировать его, пока не будет всего четыре).</span><span class="sxs-lookup"><span data-stu-id="451cf-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="451cf-287">Для каждого **текстового объекта** выберите его и используйте приведенные ниже таблицы, чтобы задать параметры на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="451cf-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="451cf-288">Для компонента *преобразования Rect* :</span><span class="sxs-lookup"><span data-stu-id="451cf-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="451cf-289">Имя</span><span class="sxs-lookup"><span data-stu-id="451cf-289">Name</span></span>                   | <span data-ttu-id="451cf-290">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="451cf-290">Transform - *Position*</span></span>             | <span data-ttu-id="451cf-291">Ширина</span><span class="sxs-lookup"><span data-stu-id="451cf-291">Width</span></span>      | <span data-ttu-id="451cf-292">Высота:</span><span class="sxs-lookup"><span data-stu-id="451cf-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="451cf-293">микрофонестатуслабел</span><span class="sxs-lookup"><span data-stu-id="451cf-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="451cf-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="451cf-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="451cf-295">300</span><span class="sxs-lookup"><span data-stu-id="451cf-295">300</span></span>        | <span data-ttu-id="451cf-296">30</span><span class="sxs-lookup"><span data-stu-id="451cf-296">30</span></span>        |
        | <span data-ttu-id="451cf-297">азуререспонселабел</span><span class="sxs-lookup"><span data-stu-id="451cf-297">AzureResponseLabel</span></span>     | <span data-ttu-id="451cf-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="451cf-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="451cf-299">300</span><span class="sxs-lookup"><span data-stu-id="451cf-299">300</span></span>        | <span data-ttu-id="451cf-300">30</span><span class="sxs-lookup"><span data-stu-id="451cf-300">30</span></span>        |
        | <span data-ttu-id="451cf-301">диктатионлабел</span><span class="sxs-lookup"><span data-stu-id="451cf-301">DictationLabel</span></span>         | <span data-ttu-id="451cf-302">**X** -80 **Y** – 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="451cf-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="451cf-303">300</span><span class="sxs-lookup"><span data-stu-id="451cf-303">300</span></span>        | <span data-ttu-id="451cf-304">30</span><span class="sxs-lookup"><span data-stu-id="451cf-304">30</span></span>        |
        | <span data-ttu-id="451cf-305">транслатионресултлабел</span><span class="sxs-lookup"><span data-stu-id="451cf-305">TranslationResultLabel</span></span> | <span data-ttu-id="451cf-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="451cf-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="451cf-307">300</span><span class="sxs-lookup"><span data-stu-id="451cf-307">300</span></span>        | <span data-ttu-id="451cf-308">30</span><span class="sxs-lookup"><span data-stu-id="451cf-308">30</span></span>        |


    2. <span data-ttu-id="451cf-309">Для компонента **Text (script)** :</span><span class="sxs-lookup"><span data-stu-id="451cf-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="451cf-310">Имя</span><span class="sxs-lookup"><span data-stu-id="451cf-310">Name</span></span>                   | <span data-ttu-id="451cf-311">Текст</span><span class="sxs-lookup"><span data-stu-id="451cf-311">Text</span></span>               | <span data-ttu-id="451cf-312">Размер шрифта</span><span class="sxs-lookup"><span data-stu-id="451cf-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="451cf-313">микрофонестатуслабел</span><span class="sxs-lookup"><span data-stu-id="451cf-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="451cf-314">Состояние микрофона:</span><span class="sxs-lookup"><span data-stu-id="451cf-314">Microphone Status:</span></span> | <span data-ttu-id="451cf-315">20</span><span class="sxs-lookup"><span data-stu-id="451cf-315">20</span></span>           |
        | <span data-ttu-id="451cf-316">азуререспонселабел</span><span class="sxs-lookup"><span data-stu-id="451cf-316">AzureResponseLabel</span></span>     | <span data-ttu-id="451cf-317">Веб-ответ Azure</span><span class="sxs-lookup"><span data-stu-id="451cf-317">Azure Web Response</span></span> | <span data-ttu-id="451cf-318">20</span><span class="sxs-lookup"><span data-stu-id="451cf-318">20</span></span>           |
        | <span data-ttu-id="451cf-319">диктатионлабел</span><span class="sxs-lookup"><span data-stu-id="451cf-319">DictationLabel</span></span>         |   <span data-ttu-id="451cf-320">Вы только что сказали:</span><span class="sxs-lookup"><span data-stu-id="451cf-320">You just said:</span></span>   | <span data-ttu-id="451cf-321">20</span><span class="sxs-lookup"><span data-stu-id="451cf-321">20</span></span>           |
        | <span data-ttu-id="451cf-322">транслатионресултлабел</span><span class="sxs-lookup"><span data-stu-id="451cf-322">TranslationResultLabel</span></span> |    <span data-ttu-id="451cf-323">Перевод:</span><span class="sxs-lookup"><span data-stu-id="451cf-323">Translation:</span></span>    | <span data-ttu-id="451cf-324">20</span><span class="sxs-lookup"><span data-stu-id="451cf-324">20</span></span>           |

        ![Введите соответствующие значения для меток пользовательского интерфейса.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="451cf-326">Кроме того, сделайте шрифт **полужирным**.</span><span class="sxs-lookup"><span data-stu-id="451cf-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="451cf-327">Это упростит чтение текста.</span><span class="sxs-lookup"><span data-stu-id="451cf-327">This will make the text easier to read.</span></span>

        ![Полужирный шрифт.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="451cf-329">Для каждого *объекта текста пользовательского интерфейса* , созданного в [главе 5](#chapter-5--create-the-results-class), создайте новый *дочерний* **текстовый объект пользовательского интерфейса**.</span><span class="sxs-lookup"><span data-stu-id="451cf-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="451cf-330">Эти дочерние элементы будут отображать выходные данные приложения.</span><span class="sxs-lookup"><span data-stu-id="451cf-330">These children will display the output of the application.</span></span> <span data-ttu-id="451cf-331">Создайте *дочерние* объекты, щелкнув правой кнопкой мыши предполагаемый родительский объект (например, *микрофонестатуслабел*), а затем выберите пункт **Пользовательский интерфейс** , а затем выберите пункт **текст**.</span><span class="sxs-lookup"><span data-stu-id="451cf-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="451cf-332">Для каждого из этих дочерних элементов выберите его и используйте приведенные ниже таблицы, чтобы задать параметры на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="451cf-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="451cf-333">Для компонента **преобразования Rect** :</span><span class="sxs-lookup"><span data-stu-id="451cf-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="451cf-334">Имя</span><span class="sxs-lookup"><span data-stu-id="451cf-334">Name</span></span>                  | <span data-ttu-id="451cf-335">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="451cf-335">Transform - *Position*</span></span> | <span data-ttu-id="451cf-336">Ширина</span><span class="sxs-lookup"><span data-stu-id="451cf-336">Width</span></span>      | <span data-ttu-id="451cf-337">Высота:</span><span class="sxs-lookup"><span data-stu-id="451cf-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="451cf-338">микрофонестатустекст</span><span class="sxs-lookup"><span data-stu-id="451cf-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="451cf-339">X 0 Y – 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="451cf-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="451cf-340">300</span><span class="sxs-lookup"><span data-stu-id="451cf-340">300</span></span>        | <span data-ttu-id="451cf-341">30</span><span class="sxs-lookup"><span data-stu-id="451cf-341">30</span></span>        |
        | <span data-ttu-id="451cf-342">азуререспонсетекст</span><span class="sxs-lookup"><span data-stu-id="451cf-342">AzureResponseText</span></span>     | <span data-ttu-id="451cf-343">X 0 Y – 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="451cf-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="451cf-344">300</span><span class="sxs-lookup"><span data-stu-id="451cf-344">300</span></span>        | <span data-ttu-id="451cf-345">30</span><span class="sxs-lookup"><span data-stu-id="451cf-345">30</span></span>        |
        | <span data-ttu-id="451cf-346">диктатионтекст</span><span class="sxs-lookup"><span data-stu-id="451cf-346">DictationText</span></span>         | <span data-ttu-id="451cf-347">X 0 Y – 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="451cf-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="451cf-348">300</span><span class="sxs-lookup"><span data-stu-id="451cf-348">300</span></span>        | <span data-ttu-id="451cf-349">30</span><span class="sxs-lookup"><span data-stu-id="451cf-349">30</span></span>        |
        | <span data-ttu-id="451cf-350">транслатионресулттекст</span><span class="sxs-lookup"><span data-stu-id="451cf-350">TranslationResultText</span></span> | <span data-ttu-id="451cf-351">X 0 Y – 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="451cf-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="451cf-352">300</span><span class="sxs-lookup"><span data-stu-id="451cf-352">300</span></span>        | <span data-ttu-id="451cf-353">30</span><span class="sxs-lookup"><span data-stu-id="451cf-353">30</span></span>        |

    2. <span data-ttu-id="451cf-354">Для компонента **Text (script)** :</span><span class="sxs-lookup"><span data-stu-id="451cf-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="451cf-355">Имя</span><span class="sxs-lookup"><span data-stu-id="451cf-355">Name</span></span>                  | <span data-ttu-id="451cf-356">Текст</span><span class="sxs-lookup"><span data-stu-id="451cf-356">Text</span></span>          | <span data-ttu-id="451cf-357">Размер шрифта</span><span class="sxs-lookup"><span data-stu-id="451cf-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="451cf-358">микрофонестатустекст</span><span class="sxs-lookup"><span data-stu-id="451cf-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="451cf-359">??</span><span class="sxs-lookup"><span data-stu-id="451cf-359">??</span></span>       | <span data-ttu-id="451cf-360">20</span><span class="sxs-lookup"><span data-stu-id="451cf-360">20</span></span>           |
        | <span data-ttu-id="451cf-361">азуререспонсетекст</span><span class="sxs-lookup"><span data-stu-id="451cf-361">AzureResponseText</span></span>     |      <span data-ttu-id="451cf-362">??</span><span class="sxs-lookup"><span data-stu-id="451cf-362">??</span></span>       | <span data-ttu-id="451cf-363">20</span><span class="sxs-lookup"><span data-stu-id="451cf-363">20</span></span>           |
        | <span data-ttu-id="451cf-364">диктатионтекст</span><span class="sxs-lookup"><span data-stu-id="451cf-364">DictationText</span></span>         |      <span data-ttu-id="451cf-365">??</span><span class="sxs-lookup"><span data-stu-id="451cf-365">??</span></span>       | <span data-ttu-id="451cf-366">20</span><span class="sxs-lookup"><span data-stu-id="451cf-366">20</span></span>           |
        | <span data-ttu-id="451cf-367">транслатионресулттекст</span><span class="sxs-lookup"><span data-stu-id="451cf-367">TranslationResultText</span></span> |      <span data-ttu-id="451cf-368">??</span><span class="sxs-lookup"><span data-stu-id="451cf-368">??</span></span>       | <span data-ttu-id="451cf-369">20</span><span class="sxs-lookup"><span data-stu-id="451cf-369">20</span></span>           |

9. <span data-ttu-id="451cf-370">Затем выберите параметр выравнивания "центр" для каждого текстового компонента:</span><span class="sxs-lookup"><span data-stu-id="451cf-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Выровняйте текст.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="451cf-372">Чтобы обеспечить простоту чтения **дочерних объектов пользовательского интерфейса** , измените их *Цвет*.</span><span class="sxs-lookup"><span data-stu-id="451cf-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="451cf-373">Для этого щелкните полосу (в настоящий момент черная) рядом с пунктом *Цвет*.</span><span class="sxs-lookup"><span data-stu-id="451cf-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Введите соответствующие значения для вывода текста пользовательского интерфейса.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="451cf-375">Затем в окне новое, небольшое *цветовое* значение измените *шестнадцатеричный цвет* на: **0032EAFF** .</span><span class="sxs-lookup"><span data-stu-id="451cf-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Измените цвет на синий.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="451cf-377">Ниже показано, как должен выглядеть **Пользовательский интерфейс** .</span><span class="sxs-lookup"><span data-stu-id="451cf-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="451cf-378">На *панели Иерархия*:</span><span class="sxs-lookup"><span data-stu-id="451cf-378">In the *Hierarchy Panel*:</span></span>

        ![Иметь иерархию в предоставленной структуре.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="451cf-380">В *представлениях* *сцены* и игры:</span><span class="sxs-lookup"><span data-stu-id="451cf-380">In the *Scene* and *Game Views*:</span></span>

        ![Отображение сцен и игровых представлений в одной и той же структуре.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="451cf-382">Глава 5 — Создание класса Results</span><span class="sxs-lookup"><span data-stu-id="451cf-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="451cf-383">Первый скрипт, который необходимо создать, — это класс *Results* , который отвечает за предоставление способа просмотра результатов перевода.</span><span class="sxs-lookup"><span data-stu-id="451cf-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="451cf-384">Класс сохраняет и отображает следующее:</span><span class="sxs-lookup"><span data-stu-id="451cf-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="451cf-385">Результат ответа из Azure.</span><span class="sxs-lookup"><span data-stu-id="451cf-385">The response result from Azure.</span></span>
- <span data-ttu-id="451cf-386">Состояние микрофона.</span><span class="sxs-lookup"><span data-stu-id="451cf-386">The microphone status.</span></span> 
- <span data-ttu-id="451cf-387">Результат диктовки (Voice to Text).</span><span class="sxs-lookup"><span data-stu-id="451cf-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="451cf-388">Результат перевода.</span><span class="sxs-lookup"><span data-stu-id="451cf-388">The result of the translation.</span></span>

<span data-ttu-id="451cf-389">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="451cf-389">To create this class:</span></span> 

1.  <span data-ttu-id="451cf-390">Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте > папку**.</span><span class="sxs-lookup"><span data-stu-id="451cf-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="451cf-391">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="451cf-391">Name the folder **Scripts**.</span></span> 
 
    ![Создайте папку Scripts.](images/AzureLabs-Lab1-31.png)

    ![Откройте папку «скрипты».](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="451cf-394">Создав папку **Scripts** , дважды щелкните ее, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="451cf-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="451cf-395">Затем в этой папке щелкните правой кнопкой мыши и выберите **создать >** затем **скрипт C#**.</span><span class="sxs-lookup"><span data-stu-id="451cf-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="451cf-396">Назовите *результаты* скрипта.</span><span class="sxs-lookup"><span data-stu-id="451cf-396">Name the script *Results*.</span></span> 

    ![Создайте первый скрипт.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="451cf-398">Дважды щелкните новый скрипт *Results* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="451cf-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="451cf-399">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="451cf-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="451cf-400">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="451cf-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="451cf-401">Затем добавьте метод " *спящий ()* ", который будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="451cf-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="451cf-402">Наконец, добавьте методы, которые отвечают за вывод различных сведений о результатах в пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="451cf-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="451cf-403">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="451cf-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="451cf-404">Глава 6 — создание класса *микрофонеманажер*</span><span class="sxs-lookup"><span data-stu-id="451cf-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="451cf-405">Второй класс, который предстоит создать, — это *микрофонеманажер*.</span><span class="sxs-lookup"><span data-stu-id="451cf-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="451cf-406">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="451cf-406">This class is responsible for:</span></span>

- <span data-ttu-id="451cf-407">Обнаружение устройства записи, подключенного к гарнитуре или компьютеру (в зависимости от значения по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="451cf-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="451cf-408">Запишите звук (голосовой) и используйте диктовку, чтобы сохранить ее в виде строки.</span><span class="sxs-lookup"><span data-stu-id="451cf-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="451cf-409">После приостановки голоса отправьте диктовку в класс Translator.</span><span class="sxs-lookup"><span data-stu-id="451cf-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="451cf-410">Разместите метод, который может при необходимости прекращать запись речи.</span><span class="sxs-lookup"><span data-stu-id="451cf-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="451cf-411">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="451cf-411">To create this class:</span></span> 
1.  <span data-ttu-id="451cf-412">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="451cf-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="451cf-413">Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать > скрипт C#**.</span><span class="sxs-lookup"><span data-stu-id="451cf-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="451cf-414">Назовите сценарий *микрофонеманажер*.</span><span class="sxs-lookup"><span data-stu-id="451cf-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="451cf-415">Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="451cf-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="451cf-416">Обновите пространства имен, как показано ниже, в верхней части класса *микрофонеманажер* :</span><span class="sxs-lookup"><span data-stu-id="451cf-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="451cf-417">Затем добавьте следующие переменные в класс *микрофонеманажер* :</span><span class="sxs-lookup"><span data-stu-id="451cf-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="451cf-418">Теперь необходимо добавить код для методов *спящего режима ()* и *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="451cf-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="451cf-419">Они будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="451cf-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="451cf-420">Метод *Update ()* можно *Удалить* , так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="451cf-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="451cf-421">Теперь вам потребуются методы, которые приложение использует для запуска и завершения записи речи, и передайте его классу *Translator* , который вы будете создавать в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="451cf-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="451cf-422">Скопируйте приведенный ниже код и вставьте его под методом *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="451cf-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="451cf-423">Несмотря на то, что это приложение не будет использовать его, в этой статье также приведен метод *стопкаптурингаудио ()* , который позволяет реализовать возможность отмены записи звука в приложении.</span><span class="sxs-lookup"><span data-stu-id="451cf-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="451cf-424">Теперь необходимо добавить обработчик диктовки, который будет вызываться при остановке голоса.</span><span class="sxs-lookup"><span data-stu-id="451cf-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="451cf-425">Затем этот метод передает продиктованный текст классу *Translator* .</span><span class="sxs-lookup"><span data-stu-id="451cf-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="451cf-426">Не забудьте сохранить изменения в Visual Studio перед возвратом в Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="451cf-427">На этом этапе вы увидите ошибку на панели *консоли редактора Unity* ("имя" Translator "не существует...").</span><span class="sxs-lookup"><span data-stu-id="451cf-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="451cf-428">Это обусловлено тем, что код ссылается на класс *Translator* , который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="451cf-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="451cf-429">Глава 7 — вызов службы Azure и переводчика</span><span class="sxs-lookup"><span data-stu-id="451cf-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="451cf-430">Последний скрипт, который необходимо создать, — это класс *Translator* .</span><span class="sxs-lookup"><span data-stu-id="451cf-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="451cf-431">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="451cf-431">This class is responsible for:</span></span>

-   <span data-ttu-id="451cf-432">Проверка подлинности приложения в *Azure* в Exchange для **токена проверки** подлинности.</span><span class="sxs-lookup"><span data-stu-id="451cf-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="451cf-433">Используйте **токен проверки подлинности** для передачи текста (полученного от класса *микрофонеманажер* ) для перевода.</span><span class="sxs-lookup"><span data-stu-id="451cf-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="451cf-434">Получение переведенного результата и передача его в класс *Results* для визуализации в пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="451cf-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="451cf-435">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="451cf-435">To create this Class:</span></span> 
1.  <span data-ttu-id="451cf-436">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="451cf-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="451cf-437">Щелкните правой кнопкой мыши на **панели проект**, **Создайте > скрипт C#**.</span><span class="sxs-lookup"><span data-stu-id="451cf-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="451cf-438">Вызовите *транслятор* скриптов.</span><span class="sxs-lookup"><span data-stu-id="451cf-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="451cf-439">Дважды щелкните новый скрипт *переводчика* , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="451cf-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="451cf-440">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="451cf-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="451cf-441">Затем добавьте следующие переменные в класс *Translator* :</span><span class="sxs-lookup"><span data-stu-id="451cf-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="451cf-442">Языки, вставленные в **перечисление** языков, являются просто примерами.</span><span class="sxs-lookup"><span data-stu-id="451cf-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="451cf-443">Вы можете добавить дополнительные сведения, если хотите. [API поддерживает более 60 языков](/azure/cognitive-services/translator/languages) (включая марсианского)!</span><span class="sxs-lookup"><span data-stu-id="451cf-443">Feel free to add more if you wish; the [API supports over 60 languages](/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="451cf-444">Существует [более интерактивная страница, охватывающая доступные языки](https://www.microsoft.com/translator/business/languages/), хотя имейте в виду, что страница работает только в том случае, если для языка сайта задано значение "" (а веб-сайт Майкрософт, скорее всего, перенаправляется на ваш собственный язык).</span><span class="sxs-lookup"><span data-stu-id="451cf-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to '' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="451cf-445">Язык сайта можно изменить в нижней части страницы или путем изменения URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="451cf-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="451cf-446">Значение **authorizationkey согласно инструкциям** в приведенном выше фрагменте кода должно быть **ключом**  , полученным при оформлении подписки на *API перевода текстов Azure*.</span><span class="sxs-lookup"><span data-stu-id="451cf-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="451cf-447">Это было рассмотрено в [главе 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="451cf-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="451cf-448">Теперь необходимо добавить код для методов *спящего режима ()* и *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="451cf-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="451cf-449">В этом случае код выполнит вызов *Azure* с помощью ключа авторизации, чтобы получить *маркер*.</span><span class="sxs-lookup"><span data-stu-id="451cf-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="451cf-450">Срок действия маркера истечет через 10 минут.</span><span class="sxs-lookup"><span data-stu-id="451cf-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="451cf-451">В зависимости от сценария для приложения может потребоваться несколько раз выполнять один и тот же соподпрограммный вызов.</span><span class="sxs-lookup"><span data-stu-id="451cf-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="451cf-452">Для получения маркера используется следующая соподпрограмма:</span><span class="sxs-lookup"><span data-stu-id="451cf-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="451cf-453">При изменении имени метода IEnumerator **жеттокенкораутине ()** необходимо обновить значения строк вызова *старткораутине* и *стопкораутине* в приведенном выше коде.</span><span class="sxs-lookup"><span data-stu-id="451cf-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="451cf-454">Как и в случае с [документацией Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), для отмены конкретной *соподпрограммы* необходимо использовать метод строкового значения.</span><span class="sxs-lookup"><span data-stu-id="451cf-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="451cf-455">Затем добавьте соподпрограмму (с помощью метода потока поддержки прямо под ним), чтобы получить перевод текста, полученного классом *микрофонеманажер* .</span><span class="sxs-lookup"><span data-stu-id="451cf-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="451cf-456">Этот код создает строку запроса для отправки в *API перевода текстов Azure*, а затем использует внутренний класс Unity унитивебрекуест для выполнения вызова Get к конечной точке со строкой запроса.</span><span class="sxs-lookup"><span data-stu-id="451cf-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="451cf-457">Затем результат используется для задания перевода в объекте Results.</span><span class="sxs-lookup"><span data-stu-id="451cf-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="451cf-458">В приведенном ниже коде показана реализация:</span><span class="sxs-lookup"><span data-stu-id="451cf-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="451cf-459">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="451cf-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="451cf-460">Глава 8 — Настройка сцены Unity</span><span class="sxs-lookup"><span data-stu-id="451cf-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="451cf-461">В редакторе Unity щелкните и перетащите класс *Results* *из* папки **сценарии** в объект **Main** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="451cf-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="451cf-462">Щелкните **основную камеру** и посмотрите на *Панель инспектора*.</span><span class="sxs-lookup"><span data-stu-id="451cf-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="451cf-463">Вы заметите, что в вновь добавленном компоненте *скрипта* есть четыре поля с пустыми значениями.</span><span class="sxs-lookup"><span data-stu-id="451cf-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="451cf-464">Это выходные ссылки на свойства в коде.</span><span class="sxs-lookup"><span data-stu-id="451cf-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="451cf-465">Перетащите соответствующие **текстовые** объекты с *панели Иерархия* в эти четыре слота, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="451cf-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Обновить ссылки на целевые объекты указанными значениями.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="451cf-467">Затем перетащите класс *Translator* из папки **Scripts** в **главный объект Camera** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="451cf-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="451cf-468">Затем перетащите класс *микрофонеманажер* из папки **Scripts** в **основной объект Camera** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="451cf-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="451cf-469">Наконец, щелкните **основную камеру** и посмотрите на *Панель инспектора*.</span><span class="sxs-lookup"><span data-stu-id="451cf-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="451cf-470">Вы заметите, что в скрипте, который вы перетащили, есть два раскрывающихся списка, которые позволяют задать языки.</span><span class="sxs-lookup"><span data-stu-id="451cf-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Убедитесь, что нужные языки перевода введены.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="451cf-472">Глава 9 — тестирование в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="451cf-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="451cf-473">На этом этапе необходимо проверить, правильно ли реализована сцена.</span><span class="sxs-lookup"><span data-stu-id="451cf-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="451cf-474">Убедитесь в следующем:</span><span class="sxs-lookup"><span data-stu-id="451cf-474">Ensure that:</span></span>

- <span data-ttu-id="451cf-475">Все параметры, упомянутые в [главе 1](#chapter-1--the-azure-portal) , заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="451cf-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="451cf-476">*Результаты*, *переводчики* и *микрофонеманажер* присоединяются к **главному объекту Camera** .</span><span class="sxs-lookup"><span data-stu-id="451cf-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="451cf-477">Вы поместили **ключ** службы *API перевода текстов Azure* в переменную **authorizationkey согласно инструкциям** в скрипте *переводчика* .</span><span class="sxs-lookup"><span data-stu-id="451cf-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="451cf-478">Все поля на *панели инспектора основной камеры* назначены должным образом.</span><span class="sxs-lookup"><span data-stu-id="451cf-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="451cf-479">Микрофон работает при запуске сцены (если нет, убедитесь, что подключенный микрофон является устройством *по умолчанию* и что вы [правильно настроили его в Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="451cf-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="451cf-480">Можно протестировать иммерсивное гарнитуру, нажав кнопку **воспроизвести** в *редакторе Unity*.</span><span class="sxs-lookup"><span data-stu-id="451cf-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="451cf-481">Приложение должно работать через присоединенную иммерсивное гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="451cf-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="451cf-482">Если в консоли Unity появляется сообщение об ошибке о смене звукового устройства по умолчанию, возможно, сцена не работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="451cf-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="451cf-483">Это связано с тем, как портал смешанной реальности работает со встроенными микротелефонами для гарнитур, имеющих их.</span><span class="sxs-lookup"><span data-stu-id="451cf-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="451cf-484">Если вы видите эту ошибку, просто закройте сцену и снова запустите ее, и она должна работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="451cf-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="451cf-485">Глава 10 — Создание решения UWP и загружать неопубликованные на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="451cf-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="451cf-486">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="451cf-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="451cf-487">Выберите **параметры сборки**: **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="451cf-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="451cf-488">В окне " **параметры сборки** " щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="451cf-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Создание сцены Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="451cf-490">Если это еще не так, то **проект Tick Unity C#**.</span><span class="sxs-lookup"><span data-stu-id="451cf-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="451cf-491">Щелкните **Построить**.</span><span class="sxs-lookup"><span data-stu-id="451cf-491">Click **Build**.</span></span> <span data-ttu-id="451cf-492">Unity запустит окно *проводника* , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="451cf-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="451cf-493">Создайте эту папку сейчас и назовите ее *app* Name.</span><span class="sxs-lookup"><span data-stu-id="451cf-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="451cf-494">Затем выберите папку *приложения* и нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="451cf-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="451cf-495">Unity начнет сборку проекта в папку *приложения* .</span><span class="sxs-lookup"><span data-stu-id="451cf-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="451cf-496">После того как Unity завершит сборку (может занять некоторое время), он откроет окно *проводника* в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="451cf-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="451cf-497">Глава 11 — развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="451cf-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="451cf-498">Чтобы развернуть приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="451cf-498">To deploy your application:</span></span>

1.  <span data-ttu-id="451cf-499">Перейдите к новой сборке Unity (папка *приложения* ) и откройте файл решения в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="451cf-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="451cf-500">В конфигурации решения выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="451cf-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="451cf-501">На платформе решения выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="451cf-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="451cf-502">Для Microsoft HoloLens может быть проще установить этот параметр на *Удаленный компьютер*, чтобы вы не были подключены к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="451cf-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="451cf-503">Однако необходимо также выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="451cf-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="451cf-504">Определите **IP-адрес** HoloLens, который можно найти в *параметрах > сети & интернет > Wi-Fi > дополнительные параметры*. IPv4 — это адрес, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="451cf-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="451cf-505">Убедитесь, **что включен** *режим разработчика* ; находится в *параметрах > Update & > безопасности для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="451cf-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="451cf-507">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютер.</span><span class="sxs-lookup"><span data-stu-id="451cf-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="451cf-508">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="451cf-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="451cf-509">После запуска приложение предложит авторизовать доступ к микрофону.</span><span class="sxs-lookup"><span data-stu-id="451cf-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="451cf-510">Обязательно нажмите кнопку « **Да** ».</span><span class="sxs-lookup"><span data-stu-id="451cf-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="451cf-511">Теперь вы готовы начать трансляцию!</span><span class="sxs-lookup"><span data-stu-id="451cf-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="451cf-512">Законченное приложение API для перевода текста</span><span class="sxs-lookup"><span data-stu-id="451cf-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="451cf-513">Поздравляем! вы создали приложение смешанной реальности, которое использует API перевода текста Azure для преобразования речи в переведенный текст.</span><span class="sxs-lookup"><span data-stu-id="451cf-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Окончательный продукт.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="451cf-515">Дополнительные упражнения</span><span class="sxs-lookup"><span data-stu-id="451cf-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="451cf-516">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="451cf-516">Exercise 1</span></span>

<span data-ttu-id="451cf-517">Можно ли добавить в приложение функции преобразования текста в речь, чтобы возвращаемый текст был произнесен?</span><span class="sxs-lookup"><span data-stu-id="451cf-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="451cf-518">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="451cf-518">Exercise 2</span></span>

<span data-ttu-id="451cf-519">Предоставление пользователю возможности изменять языки исходного и выходного кода ("с" и "на") в самом приложении, поэтому не требуется перестраивать приложение каждый раз, когда необходимо изменить языки.</span><span class="sxs-lookup"><span data-stu-id="451cf-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>