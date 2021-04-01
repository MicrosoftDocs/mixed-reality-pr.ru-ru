---
title: Настройка Photon Unity Networking
description: Пройдите этот курс, и вы узнаете, как реализовать Photon Unity Network в приложении смешанной реальности HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, многопользовательские возможности, Photon, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, PUN
ms.localizationpriority: high
ms.openlocfilehash: dd4eb8400a7aac491cb893d19e18afc6d6401d1b
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550244"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="de0e3-104">2. Настройка Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="de0e3-104">2. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="de0e3-105">В этом учебнике показано, как подготовиться к созданию совместного взаимодействия с помощью Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="de0e3-105">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="de0e3-106">Вы узнаете, как создать приложение PUN, импортировать активы PUN в проект Unity и подключить проект Unity к приложению PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-106">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="de0e3-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="de0e3-107">Objectives</span></span>

* <span data-ttu-id="de0e3-108">Узнать, как создать приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-108">Learn how to create a PUN app</span></span>
* <span data-ttu-id="de0e3-109">Узнать, как найти и импортировать активы PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-109">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="de0e3-110">Узнать, как подключить проект Unity к приложению PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-110">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="de0e3-111">Создание и подготовка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="de0e3-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="de0e3-112">В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.</span><span class="sxs-lookup"><span data-stu-id="de0e3-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="de0e3-113">Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:</span><span class="sxs-lookup"><span data-stu-id="de0e3-113">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="de0e3-114">[Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="de0e3-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="de0e3-115">Переключение платформы сборки.</span><span class="sxs-lookup"><span data-stu-id="de0e3-115">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="de0e3-116">Импорт требуемых ресурсов TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="de0e3-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="de0e3-117">Импорт набора средств для Смешанной реальности (MRTK).</span><span class="sxs-lookup"><span data-stu-id="de0e3-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="de0e3-118">Настройка проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="de0e3-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="de0e3-119">[Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *MultiUserCapabilities*.</span><span class="sxs-lookup"><span data-stu-id="de0e3-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="de0e3-120">Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):</span><span class="sxs-lookup"><span data-stu-id="de0e3-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="de0e3-121">Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="de0e3-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="de0e3-122">Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).</span><span class="sxs-lookup"><span data-stu-id="de0e3-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="de0e3-123">Включение дополнительных возможностей</span><span class="sxs-lookup"><span data-stu-id="de0e3-123">Enabling additional capabilities</span></span>

<span data-ttu-id="de0e3-124">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).</span><span class="sxs-lookup"><span data-stu-id="de0e3-124">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Параметры проигрывателя Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="de0e3-126">В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient**, **Microphone**, **SpatialPerception** и **GazeInput**, которые вы включили при выполнении шага [Настройка проекта Unity](mr-learning-base-02.md#configuring-the-unity-project) ранее.</span><span class="sxs-lookup"><span data-stu-id="de0e3-126">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="de0e3-127">Затем включите следующие дополнительные возможности:</span><span class="sxs-lookup"><span data-stu-id="de0e3-127">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="de0e3-128">возможность **InternetClientServer**;</span><span class="sxs-lookup"><span data-stu-id="de0e3-128">**InternetClientServer** capability</span></span>
* <span data-ttu-id="de0e3-129">возможность **PrivateNetworkClientServer**.</span><span class="sxs-lookup"><span data-stu-id="de0e3-129">**PrivateNetworkClientServer** capability</span></span>

![Настройки возможностей Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="de0e3-131">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="de0e3-131">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="de0e3-132">В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="de0e3-132">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="de0e3-134">Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="de0e3-134">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="de0e3-135">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="de0e3-135">Importing the tutorial assets</span></span>

<span data-ttu-id="de0e3-136">Добавьте пакет SDK AzurespatialAnchors 2.7.1 в свой проект Unity с помощью этого [учебника](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="de0e3-136">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>


<span data-ttu-id="de0e3-137">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="de0e3-137">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>
 
* <span data-ttu-id="de0e3-138">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="de0e3-138">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="de0e3-139">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="de0e3-139">[MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)</span></span>
* <span data-ttu-id="de0e3-140">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="de0e3-140">[MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)</span></span>

<span data-ttu-id="de0e3-141">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="de0e3-141">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="de0e3-143">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="de0e3-143">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="de0e3-144">После импорта пакета учебных активов MultiUserCapabilities в окне консоли появятся несколько ошибок [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246). Они указывают на отсутствие типа или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="de0e3-144">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="de0e3-145">Это ожидаемое поведение, и ошибки будут устранены при работе со следующим разделом при импорте активов PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-145">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="de0e3-146">Импорт активов PUN</span><span class="sxs-lookup"><span data-stu-id="de0e3-146">Importing the PUN assets</span></span>

<span data-ttu-id="de0e3-147">В меню Unity последовательно выберите **Window** > **Asset Store** (Окно > Asset Store), чтобы открыть окно Asset Store. Найдите и выберите актив **PUN 2 — FREE** от Exit Games, а затем нажмите кнопку **Download** (Скачать), чтобы скачать пакет активов в учетную запись Unity.</span><span class="sxs-lookup"><span data-stu-id="de0e3-147">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="de0e3-148">После скачивания нажмите кнопку **Импорт**, чтобы открыть окно Import Unity Package (Импорт пакета Unity).</span><span class="sxs-lookup"><span data-stu-id="de0e3-148">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![Хранилище Unity Asset Store с PUN 2 (бесплатно)](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="de0e3-150">В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.</span><span class="sxs-lookup"><span data-stu-id="de0e3-150">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity с окном импорта PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="de0e3-152">Когда в Unity завершится процесс импорта, появится окно мастера PUN с открытым меню PUN Setup (Настройка PUN). На данный момент вы можете проигнорировать или закрыть это окно.</span><span class="sxs-lookup"><span data-stu-id="de0e3-152">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![Unity с окном настройки PUN](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="de0e3-154">Создание приложения PUN</span><span class="sxs-lookup"><span data-stu-id="de0e3-154">Creating the PUN application</span></span>

<span data-ttu-id="de0e3-155">В этом разделе показано, как создать учетную запись Photon, если у вас ее еще нет, а также приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-155">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="de0e3-156">Перейдите на <a href="https://dashboard.photonengine.com/account/signin" target="_blank">панель мониторинга</a> Photon и войдите в систему, если у вас уже есть учетная запись, которую вы хотите использовать. В противном случае щелкните ссылку **Создать** и следуйте инструкциям, чтобы зарегистрировать новую учетную запись.</span><span class="sxs-lookup"><span data-stu-id="de0e3-156">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Страница входа в Photon](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="de0e3-158">После входа нажмите кнопку **Создать приложение**.</span><span class="sxs-lookup"><span data-stu-id="de0e3-158">Once signed in, click the **Create a New App** button:</span></span>

![Страница приветствия панели мониторинга Photon](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="de0e3-160">На странице создания приложения введите приведенные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="de0e3-160">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="de0e3-161">В раскрывающемся списке Photon Type (Тип Photon) выберите PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-161">For Photon Type, select PUN</span></span>
* <span data-ttu-id="de0e3-162">В поле "Имя" введите подходящее имя, например _MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="de0e3-162">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="de0e3-163">В поле "Описание" можно ввести описание (необязательно).</span><span class="sxs-lookup"><span data-stu-id="de0e3-163">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="de0e3-164">Поле "URL-адрес" оставьте пустым.</span><span class="sxs-lookup"><span data-stu-id="de0e3-164">For Url, leave the field empty</span></span>

<span data-ttu-id="de0e3-165">Затем нажмите кнопку **Create** (Создать), чтобы создать приложение.</span><span class="sxs-lookup"><span data-stu-id="de0e3-165">Then click the **Create** button to create the new app:</span></span>

![Страница создания приложения Photon](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="de0e3-167">Когда Photon завершит процесс создания, на панели мониторинга появится новое приложение PUN.</span><span class="sxs-lookup"><span data-stu-id="de0e3-167">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Страница приложения Photon](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="de0e3-169">Подключение проекта Unity к приложению PUN</span><span class="sxs-lookup"><span data-stu-id="de0e3-169">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="de0e3-170">В этом разделе показано, как подключить проект Unity к приложению PUN, которое вы создали при работе с предыдущим разделом.</span><span class="sxs-lookup"><span data-stu-id="de0e3-170">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="de0e3-171">На панели мониторинга Photon щелкните поле **ИД приложения**, чтобы отобразить идентификатор приложения, а затем скопируйте его в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="de0e3-171">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![Страница приложения Photon с выбранным идентификатором приложения](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="de0e3-173">В меню Unity последовательно выберите **Window** > **Photon Unity Networking** > **PUN Wizard** (Окно > Photon Unity Networking > Мастер PUN), чтобы открыть окно мастера PUN. Затем нажмите кнопку **Проект установки**, чтобы открыть меню PUN Setup (Настройка PUN), и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="de0e3-173">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="de0e3-174">В поле **AppId or Email** (Идентификатор приложения или адрес электронной почты) вставьте идентификатор приложения PUN, скопированный на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="de0e3-174">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="de0e3-175">Затем нажмите кнопку **Проект установки**, чтобы применить идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="de0e3-175">Then click the **Setup Project** button to apply the app ID:</span></span>

![Окно настройки PUN в Unity с заполненным идентификатором приложения](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="de0e3-177">Когда в Unity завершится процесс настройки PUN, в меню PUN Setup (Настройка PUN) появится сообщение **Готово!**</span><span class="sxs-lookup"><span data-stu-id="de0e3-177">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="de0e3-178">В окне Project (Проект) будет автоматически выбран актив **PhotonServerSettings**, чтобы в окне Inspector (Инспектор) отображались его свойства.</span><span class="sxs-lookup"><span data-stu-id="de0e3-178">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![Окно настройки PUN в Unity с примененным проектом установки](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="de0e3-180">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="de0e3-180">Congratulations</span></span>

<span data-ttu-id="de0e3-181">Вы успешно создали приложение PUN и подключили его к проекту Unity.</span><span class="sxs-lookup"><span data-stu-id="de0e3-181">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="de0e3-182">Следующим шагом будет разрешение подключений для других пользователей, чтобы несколько пользователей могли видеть работу друг друга.</span><span class="sxs-lookup"><span data-stu-id="de0e3-182">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de0e3-183">Следующее руководство: 3. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="de0e3-183">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)