---
title: Общие сведения о переносе
description: Общие сведения о различных вариантах переноса для использования существующих приложений в смешанной реальности для HoloLens и VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Перенос, Unity, по промежуточного слоя, ядро, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042275"
---
# <a name="porting-overview"></a><span data-ttu-id="a0290-104">Общие сведения о переносе</span><span class="sxs-lookup"><span data-stu-id="a0290-104">Porting overview</span></span>

<span data-ttu-id="a0290-105">Когда речь идет о переносе или обновлении существующих проектов для смешанной реальности, ваш путь переноса зависит от того, создано ли приложение с помощью Unity или нереального механизма, и целевые объекты HoloLens (1 Gen) или HoloLens 2 или Стеамвр.</span><span class="sxs-lookup"><span data-stu-id="a0290-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="a0290-106">На этой странице обзора приведены текущие рекомендации для каждой платформы и устройства. Убедитесь, что эти процессы постоянно изменяются.</span><span class="sxs-lookup"><span data-stu-id="a0290-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="a0290-107">Сначала настройте целевой объект проекта на основе нашего [Unity](#unity) и [нереальных](#unreal) рекомендаций, а затем выполните один или несколько сценариев переноса:</span><span class="sxs-lookup"><span data-stu-id="a0290-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="a0290-108">HoloLens (1-й общий) в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a0290-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="a0290-109">Иммерсивные гарнитуры виртуальной реальности</span><span class="sxs-lookup"><span data-stu-id="a0290-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="a0290-110">Двумерные приложения UWP</span><span class="sxs-lookup"><span data-stu-id="a0290-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="a0290-111">Рекомендуемые целевые объекты проекта</span><span class="sxs-lookup"><span data-stu-id="a0290-111">Recommended project targets</span></span>

<span data-ttu-id="a0290-112">Важно регулярно обновляйте свои проекты, будь то перенос приложения на другое целевое устройство.</span><span class="sxs-lookup"><span data-stu-id="a0290-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="a0290-113">Для наших текущих рекомендаций см. Приведенные ниже ресурсы на основе подсистемы.</span><span class="sxs-lookup"><span data-stu-id="a0290-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="a0290-114">Unity</span><span class="sxs-lookup"><span data-stu-id="a0290-114">Unity</span></span>

<span data-ttu-id="a0290-115">Последние руководства по рекомендуемым версиям Unity и МРТК см. на странице [Выбор версии Unity](../unity/choosing-unity-version.md) .</span><span class="sxs-lookup"><span data-stu-id="a0290-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="a0290-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="a0290-116">Unreal</span></span>

<span data-ttu-id="a0290-117">Последние руководства по рекомендуемым и нереальным версиям и МРТК см. на странице [Настройка нереального проекта](../unreal/unreal-project-setup.md) .</span><span class="sxs-lookup"><span data-stu-id="a0290-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="a0290-118">Сценарии переноса</span><span class="sxs-lookup"><span data-stu-id="a0290-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="a0290-119">Приложения Unity (1-го поколения) для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a0290-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="a0290-120">При наличии существующего приложения Unity (1-го поколения), которое вы хотите перенести в HoloLens 2, следуйте инструкциям в [статье о переносе hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="a0290-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="a0290-121">Иммерсивные гарнитуры виртуальной реальности</span><span class="sxs-lookup"><span data-stu-id="a0290-121">Immersive VR headsets</span></span>

<span data-ttu-id="a0290-122">Если вы создали содержимое для других устройств версии VR, вам потребуется перенацелить пакеты SDK для версий VR, относящиеся к конкретному поставщику, и потенциальные API-интерфейсы сопоставления ввода.</span><span class="sxs-lookup"><span data-stu-id="a0290-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="a0290-123">Сведения о сценариях Unity и нереальном переносе можно найти в статье о [переносе приложений в иммерсивное приложение](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="a0290-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="a0290-124">Сведения о Стеамврх, которые вы хотите обновить для головных телефонов Windows Mixed Reality, см. в нашем [руководстве по обновлению стеамвр](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="a0290-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="a0290-125">Двумерные универсальные приложения Windows</span><span class="sxs-lookup"><span data-stu-id="a0290-125">2D Universal Windows applications</span></span>

<span data-ttu-id="a0290-126">Если у вас есть приложение 2D-приложения UWP, которое вы хотите перенести на иммерсивное или HoloLens Windows Mixed Reality, следуйте инструкциям по [переносу двумерных приложений UWP для Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="a0290-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>