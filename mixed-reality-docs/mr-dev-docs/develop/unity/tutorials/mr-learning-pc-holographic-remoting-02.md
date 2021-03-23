---
title: Создание приложения для голографического удаленного взаимодействия с компьютером
description: Пройдите этот курс, чтобы узнать, как создать приложение для ПК с реализацией удаленного взаимодействия в режиме смешанной реальности между вашим компьютером и HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, голографическое удаленное взаимодействие с компьютером, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590306"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="461ab-104">2. Создание приложения для голографического удаленного взаимодействия с компьютером</span><span class="sxs-lookup"><span data-stu-id="461ab-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="461ab-105">Из этого руководства вы узнаете, как создать приложение для компьютера, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="461ab-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="461ab-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="461ab-106">Objectives</span></span>

* <span data-ttu-id="461ab-107">Настроить Unity для голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="461ab-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="461ab-108">Научиться создать и развертывать приложения с использованием Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="461ab-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="461ab-109">Научиться развертывать приложения для голографического удаленного взаимодействия и подключение к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="461ab-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="461ab-110">Настройка сцены для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="461ab-110">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="461ab-111">В рамках этого раздела вы настроите проект для потоковой передачи данных смешанной реальности на устройство HoloLens 2 с компьютера в режиме реального времени с помощью подключения Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="461ab-111">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="461ab-112">В окне Project (Проект) перейдите к папке **Assets (Активы)**  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs (Заготовки)** . Затем перетащите заготовку **HolographicRemoting** в свою сцену.</span><span class="sxs-lookup"><span data-stu-id="461ab-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![Unity с выбранной добавленной заготовкой HolographicRemoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="461ab-114">Разработка приложения для компьютера</span><span class="sxs-lookup"><span data-stu-id="461ab-114">Build your application to PC</span></span>

<span data-ttu-id="461ab-115">Ваше приложение для голографического удаленного взаимодействия готово к сборке на компьютере.</span><span class="sxs-lookup"><span data-stu-id="461ab-115">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="461ab-116">Выполните приведенные ниже инструкции и внесите необходимые изменения, чтобы выполнить сборку этого приложения на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="461ab-116">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="461ab-117">1. Настройка параметров проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="461ab-117">1. Set the player settings</span></span>

<span data-ttu-id="461ab-118">В меню Unity последовательно выберите элементы Edit (Правка) > Project Settings... (Параметры проекта...), чтобы открыть окно параметров проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="461ab-118">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="461ab-119">В окне Project Settings (Параметры проекта) разверните пункт **Publishing Settings** (Параметры публикации), прокрутите вниз к разделу **Capabilities** (Возможности) и установите приведенный ниже флажок возможности (в дополнение к существующим).</span><span class="sxs-lookup"><span data-stu-id="461ab-119">In the Project Settings window, expand the **Publishing Settings**, scroll down to the **Capabilities** section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="461ab-120">Интернет (клиент и сервер)</span><span class="sxs-lookup"><span data-stu-id="461ab-120">Internet Clint server</span></span>
* <span data-ttu-id="461ab-121">Частная сеть (клиент и сервер)</span><span class="sxs-lookup"><span data-stu-id="461ab-121">Private Network Client Server</span></span>

<span data-ttu-id="461ab-122">В разделе **XR Settings** (Параметры XR) установите флажок **WSA Holographic Remoting Supported** (Поддержка голографического удаленного взаимодействия WSA) и включите функцию голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="461ab-122">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Окно параметров смешанной реальности Unity с включенной поддержкой удаленного голографического взаимодействия WSA](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="461ab-124">2. Создание проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="461ab-124">2. Build the Unity Project</span></span>

<span data-ttu-id="461ab-125">В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="461ab-125">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="461ab-126">В окне Build Settings (Параметры сборки) нажмите кнопку \***Add Open Scenes** _ (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены).</span><span class="sxs-lookup"><span data-stu-id="461ab-126">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="461ab-127">В списке Build (Сборка) нажмите кнопку _ *_Build_*\* (Сборка), чтобы открыть окно Build Universal Windows Platform (Создание приложений универсальной платформы Windows):</span><span class="sxs-lookup"><span data-stu-id="461ab-127">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Окно параметров сборки Unity с добавленной сценой](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="461ab-129">В окне Build Universal Windows Platform (Создание приложений универсальной платформы Windows) выберите подходящее расположение для хранения своей сборки, например Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="461ab-129">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="461ab-130">Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="461ab-130">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="461ab-131">Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="461ab-131">Then click the ***Select Folder*** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="461ab-133">Подождите, пока Unity завершит сборку.</span><span class="sxs-lookup"><span data-stu-id="461ab-133">Wait for Unity to finish the build process.</span></span>

![Unity выполняет сборку](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="461ab-135">3. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="461ab-135">3. Build and deploy the application</span></span>

<span data-ttu-id="461ab-136">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="461ab-136">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="461ab-137">Перейдите к папке и дважды щелкните файл SLN, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="461ab-137">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Проводник Windows с выбранным созданным решением Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="461ab-139">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по установке средств.</span><span class="sxs-lookup"><span data-stu-id="461ab-139">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="461ab-140">Настройте Visual Studio для компьютера, выбрав конфигурацию "Выпуск" архитектуру x64 и целевой объект "Локальный компьютер":</span><span class="sxs-lookup"><span data-stu-id="461ab-140">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Среда Visual Studio, настроенная для локального компьютера](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="461ab-142">Нажмите кнопку ***Локальный компьютер***.</span><span class="sxs-lookup"><span data-stu-id="461ab-142">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="461ab-143">Запустится сборка и развертывание приложения на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="461ab-143">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="461ab-144">Приложение будет установлено на ваш компьютер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="461ab-144">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="461ab-145">Проверка приложения для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="461ab-145">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="461ab-146">Чтобы подключить свое приложение для компьютера к HoloLens 2, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="461ab-146">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="461ab-147">1. Установка приложения Remoting Player на устройство HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="461ab-147">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="461ab-148">На устройстве HoloLens 2 перейдите к приложению Store и выполните поиск по фразе "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="461ab-148">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="461ab-149">Выберите приложение **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="461ab-149">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="461ab-150">Коснитесь элемента **Install** (Установить), чтобы скачать и установить приложение.</span><span class="sxs-lookup"><span data-stu-id="461ab-150">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="461ab-151">2. Подключение приложения для голографического удаленного взаимодействия с компьютером к Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="461ab-151">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="461ab-152">Запустите **Remoting Player** на устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="461ab-152">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="461ab-153">Запишите **IP-адрес** HoloLens.</span><span class="sxs-lookup"><span data-stu-id="461ab-153">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="461ab-154">Он отобразится в **Remoting Player** в виде голограммы сразу же после запуска.</span><span class="sxs-lookup"><span data-stu-id="461ab-154">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="461ab-155">Откройте приложение для голографического удаленного взаимодействия на компьютере.</span><span class="sxs-lookup"><span data-stu-id="461ab-155">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="461ab-156">Когда приложение запустится, введите **IP-адрес** и нажмите кнопку **Connect** (Подключиться), чтобы установить подключение.</span><span class="sxs-lookup"><span data-stu-id="461ab-156">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="461ab-157">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="461ab-157">Congratulations</span></span>

<span data-ttu-id="461ab-158">Из этого руководства вы узнали, как создать удаленное приложение, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="461ab-158">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="461ab-159">Когда устройство HoloLens будет подключено к приложению для голографического удаленного взаимодействия с компьютером, должна начаться потоковая передача данных смешанной реальности на устройство HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="461ab-159">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
