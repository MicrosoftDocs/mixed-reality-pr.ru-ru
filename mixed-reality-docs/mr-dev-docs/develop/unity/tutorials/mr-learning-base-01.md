---
title: Введение в учебники по MRTK
description: Из этого курса вы узнаете, как с помощью набора Mixed Reality Toolkit (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, решатели, отслеживание взгляда, голосовые команды
ms.localizationpriority: high
ms.openlocfilehash: 27a5f2cae4f08fbc142c8b872c22d23ab41cdc62
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008084"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="87cca-104">1. Введение в учебники по MRTK</span><span class="sxs-lookup"><span data-stu-id="87cca-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="87cca-105">Приветствуем вас в серии руководств по началу работы!</span><span class="sxs-lookup"><span data-stu-id="87cca-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="87cca-106">Из этих руководств вы узнаете о наборе средств для смешанной реальности (MRTK) и некоторых его функциях.</span><span class="sxs-lookup"><span data-stu-id="87cca-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="87cca-107">Кроме того, вы создадите взаимодействие в смешанной реальности, чтобы пользователи могли рассмотреть голограмму, созданную по модели марсохода NASA Curiosity.</span><span class="sxs-lookup"><span data-stu-id="87cca-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="87cca-108">Пройдя эту серию, вы сможете уверенно работать с MRTK и ускорите процесс разработки.</span><span class="sxs-lookup"><span data-stu-id="87cca-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="87cca-109">Руководства в этой серии идут последовательно, поэтому изучайте их в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="87cca-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="87cca-110">[Введение](mr-learning-base-01.md) (вы уже здесь)</span><span class="sxs-lookup"><span data-stu-id="87cca-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="87cca-111">Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="87cca-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="87cca-112">Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="87cca-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="87cca-113">Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="87cca-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="87cca-114">Создание динамического содержимого с помощью решателей</span><span class="sxs-lookup"><span data-stu-id="87cca-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="87cca-115">Создание пользовательских взаимодействий</span><span class="sxs-lookup"><span data-stu-id="87cca-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="87cca-116">Взаимодействие с трехмерными объектами</span><span class="sxs-lookup"><span data-stu-id="87cca-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="87cca-117">Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="87cca-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="87cca-118">Использование голосовых команд</span><span class="sxs-lookup"><span data-stu-id="87cca-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="87cca-119">Задачи</span><span class="sxs-lookup"><span data-stu-id="87cca-119">Objectives</span></span>

* <span data-ttu-id="87cca-120">Узнать, как настроить Unity для MRTK.</span><span class="sxs-lookup"><span data-stu-id="87cca-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="87cca-121">Узнать, как выполнять сборку и развертывание на устройстве.</span><span class="sxs-lookup"><span data-stu-id="87cca-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="87cca-122">Узнать, как использовать некоторые из основных функций MRTK.</span><span class="sxs-lookup"><span data-stu-id="87cca-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="87cca-123">Создать полное взаимодействие смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="87cca-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87cca-124">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="87cca-124">Prerequisites</span></span>

* <span data-ttu-id="87cca-125">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="87cca-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="87cca-126">[Пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="87cca-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="87cca-127">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="87cca-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="87cca-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем поддержки сборки универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="87cca-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="87cca-129">Рекомендуемая версия MRTK для этой серии руководств — MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="87cca-129">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="87cca-130">Рекомендуемая версия Unity для этой серии руководств — Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="87cca-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="87cca-131">Это заменяет все требования к версии Unity, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="87cca-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87cca-132">Следующее руководство: 2. Инициализация проекта и развертывание первого приложения</span><span class="sxs-lookup"><span data-stu-id="87cca-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)

