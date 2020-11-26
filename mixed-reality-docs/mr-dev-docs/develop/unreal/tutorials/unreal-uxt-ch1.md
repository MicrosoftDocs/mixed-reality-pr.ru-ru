---
title: 1. Начало работы
description: Часть 1 (из 6) серии руководств по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств UX из набора средств для смешанной реальности
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, UX Tools, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: aa6d90bebbbfc10b108b97d05931a9926118ba7c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679863"
---
# <a name="1-getting-started"></a><span data-ttu-id="b87b7-104">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="b87b7-104">1. Getting started</span></span>

<span data-ttu-id="b87b7-105">Как новичкам, так и опытным специалистам по разработке приложений смешанной реальности стоит начать работу с [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) и [Unreal Engine](https://www.unrealengine.com/en-US/) отсюда.</span><span class="sxs-lookup"><span data-stu-id="b87b7-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="b87b7-106">В этой серии руководств даются пошаговые инструкции по созданию интерактивного приложения для игры в шахматы с помощью [подключаемого модуля средств UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), входящего в состав [набора средств для смешанной реальности для Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="b87b7-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="b87b7-107">Этот подключаемый модуль содержит код, схемы и примеры, которые помогут вам реализовать распространенные функции пользовательского интерфейса в своих проектах.</span><span class="sxs-lookup"><span data-stu-id="b87b7-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="b87b7-109">К концу этой серии руководств вы получите практический опыт выполнения следующих задач:</span><span class="sxs-lookup"><span data-stu-id="b87b7-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="b87b7-110">создание проекта;</span><span class="sxs-lookup"><span data-stu-id="b87b7-110">Starting a new project</span></span>
* <span data-ttu-id="b87b7-111">настройка проекта для смешанной реальности;</span><span class="sxs-lookup"><span data-stu-id="b87b7-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="b87b7-112">работа с пользовательским вводом;</span><span class="sxs-lookup"><span data-stu-id="b87b7-112">Working with user input</span></span>
* <span data-ttu-id="b87b7-113">добавление кнопок;</span><span class="sxs-lookup"><span data-stu-id="b87b7-113">Adding buttons</span></span>
* <span data-ttu-id="b87b7-114">воспроизведение на эмуляторе или устройстве.</span><span class="sxs-lookup"><span data-stu-id="b87b7-114">Playing on an emulator or device</span></span>


## <a name="prerequisites"></a><span data-ttu-id="b87b7-115">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b87b7-115">Prerequisites</span></span>
<span data-ttu-id="b87b7-116">Прежде чем приступать, убедитесь, что вы установили следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="b87b7-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="b87b7-117">Windows 10 1809 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="b87b7-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="b87b7-118">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="b87b7-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b87b7-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) версии 4.25 и выше.</span><span class="sxs-lookup"><span data-stu-id="b87b7-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="b87b7-120">Устройство Microsoft HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode), или эмулятор.</span><span class="sxs-lookup"><span data-stu-id="b87b7-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="b87b7-121">Visual Studio 2019 с указанными ниже рабочими нагрузками</span><span class="sxs-lookup"><span data-stu-id="b87b7-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="b87b7-122">Установка Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b87b7-122">Installing Visual Studio 2019</span></span>
<span data-ttu-id="b87b7-123">Нужно выполнить дополнительные шаги для проверки того, что у вас установлены все обязательные пакеты Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="b87b7-123">There are a few steps to ensure you have all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="b87b7-124">Установите последнюю версию [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="b87b7-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="b87b7-125">Установите следующие [рабочие нагрузки](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="b87b7-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="b87b7-126">"Разработка классических приложений на C++";</span><span class="sxs-lookup"><span data-stu-id="b87b7-126">Desktop development with C++</span></span>
    * <span data-ttu-id="b87b7-127">"Разработка классических приложений .NET";</span><span class="sxs-lookup"><span data-stu-id="b87b7-127">.NET desktop development</span></span>
    * <span data-ttu-id="b87b7-128">"Разработка приложений для универсальной платформы Windows".</span><span class="sxs-lookup"><span data-stu-id="b87b7-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="b87b7-129">Установите следующие [компоненты](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="b87b7-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="b87b7-130">компиляторы, средства сборки и среды выполнения > средства сборки MSVC v142 — VS 2019 C++ ARM64 (последняя версия).</span><span class="sxs-lookup"><span data-stu-id="b87b7-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="b87b7-131">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="b87b7-131">That's it!</span></span> <span data-ttu-id="b87b7-132">Можно приступать к проекту по созданию шахматного приложения.</span><span class="sxs-lookup"><span data-stu-id="b87b7-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="b87b7-133">Следующий раздел: 2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="b87b7-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)