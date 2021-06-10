---
title: Управляемая отладка с помощью Unity
description: В этой статье описывается, как запустить управляемый отладчик в проекте UWP для Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, отладка, il2cpp, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547081"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="1a2e4-104">Управляемая отладка с помощью Unity</span><span class="sxs-lookup"><span data-stu-id="1a2e4-104">Managed debugging with Unity</span></span>

<span data-ttu-id="1a2e4-105">Выполните следующие действия, чтобы подключить управляемый отладчик к сборке UWP в Unity IL2CPP для HoloLens и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="1a2e4-106">Необходимо находиться в сети, поддерживающей [многоадресную рассылку](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="1a2e4-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="1a2e4-107">Перейдите к разделу **возможности публикации UWP параметры** и проверьте **интернетклиентсервер** и **приватенетворкклиентсервер**.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Возможности параметров публикации UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="1a2e4-109">Настройте параметры сборки UWP для Unity:</span><span class="sxs-lookup"><span data-stu-id="1a2e4-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="1a2e4-110">Сборка для разработки</span><span class="sxs-lookup"><span data-stu-id="1a2e4-110">Development Build</span></span>
    - <span data-ttu-id="1a2e4-111">Отладка сценария</span><span class="sxs-lookup"><span data-stu-id="1a2e4-111">Script Debugging</span></span>
    - <span data-ttu-id="1a2e4-112">Ожидание управляемого отладчика (необязательно)</span><span class="sxs-lookup"><span data-stu-id="1a2e4-112">Wait for Managed Debugger (optional)</span></span>

    ![Параметры сборки UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="1a2e4-114">Сборка в Unity.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-114">Build in Unity.</span></span>
5. <span data-ttu-id="1a2e4-115">Выполните сборку и развертывание из решения Visual Studio на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="1a2e4-116">Необходимо выполнить сборку с конфигурациями **отладки** или **выпуска** .</span><span class="sxs-lookup"><span data-stu-id="1a2e4-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="1a2e4-117">**Основная** конфигурация отключает профилировщик Unity и может предотвратить оптимальную отладку.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="1a2e4-118">При необходимости проверьте **Интернет (клиент & сервер)** и **частные сети (клиент & сервер)** в списке возможностей в Package. appxmanifest в решении.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="1a2e4-119">Убедитесь, что устройство подключено к той же сети, что и ваш компьютер, и запустите приложение на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="1a2e4-120">Убедитесь, что устройство **не** подключено к компьютеру через USB.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="1a2e4-121">Дважды щелкните один из скриптов в Unity и перейдите к решению Visual Studio, которое открывается для просмотра и редактирования.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="1a2e4-122">Отладка — > присоединить отладчик Unity.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-122">Debug -> Attach Unity Debugger.</span></span>

    ![Присоединить отладчик Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="1a2e4-124">Выберите устройство в списке и нажмите кнопку "ОК", чтобы присоединиться.</span><span class="sxs-lookup"><span data-stu-id="1a2e4-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Список устройств](images/il2cpp-debugging-machines.png)
