---
title: Создание приложения для голографического удаленного взаимодействия с компьютером
description: Пройдите этот курс, чтобы узнать, как создать приложение для ПК с реализацией удаленного взаимодействия в режиме смешанной реальности между вашим компьютером и HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, голографическое удаленное взаимодействие с компьютером, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392543"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="5f715-104">2. Создание приложения для голографического удаленного взаимодействия с компьютером</span><span class="sxs-lookup"><span data-stu-id="5f715-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="5f715-105">Из этого руководства вы узнаете, как создать приложение для компьютера, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5f715-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="5f715-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="5f715-106">Objectives</span></span>

* <span data-ttu-id="5f715-107">Настроить Unity для голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="5f715-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="5f715-108">Научиться создать и развертывать приложения с использованием Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f715-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="5f715-109">Научиться развертывать приложения для голографического удаленного взаимодействия и подключение к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f715-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="5f715-110">Настройка функциональных возможностей</span><span class="sxs-lookup"><span data-stu-id="5f715-110">Configuring the capabilities</span></span>

<span data-ttu-id="5f715-111">В окне **Project Settings** (Параметры проекта) разверните пункт **Publishing Settings** (Параметры публикации), прокрутите вниз к разделу Capabilities (Возможности) и установите приведенный ниже флажок возможности (в дополнение к существующим).</span><span class="sxs-lookup"><span data-stu-id="5f715-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="5f715-112">Интернет (клиент и сервер)</span><span class="sxs-lookup"><span data-stu-id="5f715-112">Internet Clint server</span></span>
* <span data-ttu-id="5f715-113">Частная сеть (клиент и сервер)</span><span class="sxs-lookup"><span data-stu-id="5f715-113">Private Network Client Server</span></span>

![Включение возможностей](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="5f715-115">Разработка приложения для компьютера</span><span class="sxs-lookup"><span data-stu-id="5f715-115">Build your application to PC</span></span>

<span data-ttu-id="5f715-116">Ваше приложение для голографического удаленного взаимодействия готово к сборке на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5f715-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="5f715-117">Выполните приведенные ниже инструкции и внесите необходимые изменения, чтобы выполнить сборку этого приложения на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="5f715-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="5f715-118">Проверка приложения для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="5f715-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="5f715-119">Чтобы подключить свое приложение для компьютера к HoloLens 2, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="5f715-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="5f715-120">1. Установка приложения Remoting Player на устройство HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5f715-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="5f715-121">На устройстве HoloLens 2 перейдите к приложению Store и выполните поиск по фразе "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="5f715-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="5f715-122">Выберите приложение **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="5f715-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="5f715-123">Коснитесь элемента **Install** (Установить), чтобы скачать и установить приложение.</span><span class="sxs-lookup"><span data-stu-id="5f715-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="5f715-124">2. Подключение приложения для голографического удаленного взаимодействия с компьютером к Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="5f715-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="5f715-125">Запустите **Remoting Player** на устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f715-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="5f715-126">Запишите **IP-адрес** HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f715-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="5f715-127">Он отобразится в **Remoting Player** в виде голограммы сразу же после запуска.</span><span class="sxs-lookup"><span data-stu-id="5f715-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="5f715-128">Откройте приложение для голографического удаленного взаимодействия на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5f715-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="5f715-129">Когда приложение запустится, введите **IP-адрес** и нажмите кнопку **Connect** (Подключиться), чтобы установить подключение.</span><span class="sxs-lookup"><span data-stu-id="5f715-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5f715-130">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="5f715-130">Congratulations</span></span>

<span data-ttu-id="5f715-131">Из этого руководства вы узнали, как создать удаленное приложение, которое обеспечивает голографическое удаленное взаимодействие и подключение к HoloLens 2 в любой момент для визуализации трехмерного содержимого в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5f715-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="5f715-132">Когда устройство HoloLens будет подключено к приложению для голографического удаленного взаимодействия с компьютером, должна начаться потоковая передача данных смешанной реальности на устройство HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5f715-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
