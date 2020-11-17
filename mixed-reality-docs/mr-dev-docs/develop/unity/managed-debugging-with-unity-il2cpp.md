---
title: Управляемая отладка с помощью Unity IL2CPP
description: В этой статье описывается, как запустить управляемый отладчик в проекте UWP для Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, отладка, il2cpp, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, UWP
ms.openlocfilehash: 96a2c21fc6f8b2bdab199e65c9b1a31ffb6e029b
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678593"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="baca9-104">Управляемая отладка с помощью Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="baca9-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="baca9-105">Выполните следующие действия, чтобы подключить управляемый отладчик к сборке UWP в Unity IL2CPP.</span><span class="sxs-lookup"><span data-stu-id="baca9-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="baca9-106">Это руководством изначально было разработано для HoloLens и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="baca9-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="baca9-107">Необходимо находиться в сети, поддерживающей [многоадресную рассылку](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="baca9-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="baca9-108">Убедитесь, что **интернетклиентсервер** и **приватенетворкклиентсервер** проверяются в Unity в соответствии с возможностями параметров публикации UWP.</span><span class="sxs-lookup"><span data-stu-id="baca9-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Возможности параметров публикации UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="baca9-110">Настройте параметры сборки UWP для Unity:</span><span class="sxs-lookup"><span data-stu-id="baca9-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="baca9-111">Сборка для разработки</span><span class="sxs-lookup"><span data-stu-id="baca9-111">Development Build</span></span>
    - <span data-ttu-id="baca9-112">Отладка сценария</span><span class="sxs-lookup"><span data-stu-id="baca9-112">Script Debugging</span></span>
    - <span data-ttu-id="baca9-113">Ожидание управляемого отладчика (необязательно)</span><span class="sxs-lookup"><span data-stu-id="baca9-113">Wait for Managed Debugger (optional)</span></span>

    ![Параметры сборки UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="baca9-115">Сборка в Unity.</span><span class="sxs-lookup"><span data-stu-id="baca9-115">Build in Unity.</span></span>
1. <span data-ttu-id="baca9-116">Выполните сборку и развертывание из решения Visual Studio на устройстве.</span><span class="sxs-lookup"><span data-stu-id="baca9-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="baca9-117">Необходимо выполнить сборку с конфигурациями **отладки** или **выпуска** .</span><span class="sxs-lookup"><span data-stu-id="baca9-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="baca9-118">**Основная** конфигурация отключает профилировщик Unity и может предотвратить оптимальную отладку.</span><span class="sxs-lookup"><span data-stu-id="baca9-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="baca9-119">При необходимости проверьте **Интернет (клиент & сервер)** и **частные сети (клиент & сервер)** в списке возможностей в Package. appxmanifest в решении.</span><span class="sxs-lookup"><span data-stu-id="baca9-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="baca9-120">Запустите приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="baca9-120">Start the app on your device.</span></span> <span data-ttu-id="baca9-121">Убедитесь, что устройство подключено к той же сети, что и ваш компьютер.</span><span class="sxs-lookup"><span data-stu-id="baca9-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="baca9-122">Убедитесь, что устройство **не** подключено к компьютеру через USB.</span><span class="sxs-lookup"><span data-stu-id="baca9-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="baca9-123">Перейдите к решению Visual Studio, созданному при двойном щелчке скрипта в Unity, где можно просматривать и редактировать скрипты C#.</span><span class="sxs-lookup"><span data-stu-id="baca9-123">Go to the Visual Studio solution that's created when you double-click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="baca9-124">Отладка — > присоединить отладчик Unity.</span><span class="sxs-lookup"><span data-stu-id="baca9-124">Debug -> Attach Unity Debugger.</span></span>

    ![Присоединить отладчик Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="baca9-126">Выберите устройство в списке и нажмите кнопку "ОК", чтобы присоединиться.</span><span class="sxs-lookup"><span data-stu-id="baca9-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Список устройств](images/il2cpp-debugging-machines.png)
