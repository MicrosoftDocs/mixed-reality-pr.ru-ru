---
title: Знакомство с руководствами по Пространственным привязкам Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, iOS, Android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6ac412913f8d475d213a26cb4f9f82e12d129b82
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008404"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="ec26f-104">1. Знакомство с руководствами по Пространственным привязкам Azure</span><span class="sxs-lookup"><span data-stu-id="ec26f-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="ec26f-105">Добро пожаловать в руководства по Пространственным привязкам Azure!</span><span class="sxs-lookup"><span data-stu-id="ec26f-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="ec26f-106">Из этой серии руководств вы узнаете о <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Пространственных привязках Azure</a> (ASA) и о том, как использовать возможности смешанной реальности в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="ec26f-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="ec26f-107">Вы также узнаете, как развернуть проект в Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="ec26f-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="ec26f-108">Руководства в этой серии:</span><span class="sxs-lookup"><span data-stu-id="ec26f-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="ec26f-109">[Введение](mr-learning-asa-01.md) (вы уже здесь)</span><span class="sxs-lookup"><span data-stu-id="ec26f-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="ec26f-110">Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="ec26f-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="ec26f-111">Сохранение, получение и совместное использование Пространственных привязок Azure</span><span class="sxs-lookup"><span data-stu-id="ec26f-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="ec26f-112">Отображение сведений о Пространственных привязках Azure</span><span class="sxs-lookup"><span data-stu-id="ec26f-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="ec26f-113">Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="ec26f-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="ec26f-114">Задачи</span><span class="sxs-lookup"><span data-stu-id="ec26f-114">Objectives</span></span>

* <span data-ttu-id="ec26f-115">Узнать, как создавать пространственные привязки и получать их из Azure.</span><span class="sxs-lookup"><span data-stu-id="ec26f-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="ec26f-116">Узнать, как обеспечить пространственное выравнивание в сеансах приложения.</span><span class="sxs-lookup"><span data-stu-id="ec26f-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="ec26f-117">Узнать, как реализовать пространственное выравнивание на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="ec26f-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="ec26f-118">Узнать, как подготовить, создать и развернуть проект в Android и iOS.</span><span class="sxs-lookup"><span data-stu-id="ec26f-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec26f-119">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="ec26f-119">Prerequisites</span></span>

* <span data-ttu-id="ec26f-120">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ec26f-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="ec26f-121">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="ec26f-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="ec26f-122">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="ec26f-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="ec26f-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="ec26f-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="ec26f-124">Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="ec26f-124">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="ec26f-125">Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.</span><span class="sxs-lookup"><span data-stu-id="ec26f-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="ec26f-126">Если планируется развертывание на устройствах Android и HoloLens</span><span class="sxs-lookup"><span data-stu-id="ec26f-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="ec26f-127">Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.</span><span class="sxs-lookup"><span data-stu-id="ec26f-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="ec26f-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="ec26f-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="ec26f-129">Если планируется развертывание на устройствах iOS и HoloLens</span><span class="sxs-lookup"><span data-stu-id="ec26f-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="ec26f-130">Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.</span><span class="sxs-lookup"><span data-stu-id="ec26f-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="ec26f-131"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.</span><span class="sxs-lookup"><span data-stu-id="ec26f-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="ec26f-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.3.15 и модулем iOS Build Support.</span><span class="sxs-lookup"><span data-stu-id="ec26f-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="ec26f-133">Рекомендуемая версия набора средств для смешанной реальности для этой серии руководств — МРТК 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="ec26f-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="ec26f-134">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="ec26f-134">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="ec26f-135">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="ec26f-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec26f-136">Следующее руководство: 2. Начало работы с Пространственными привязками Azure</span><span class="sxs-lookup"><span data-stu-id="ec26f-136">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
