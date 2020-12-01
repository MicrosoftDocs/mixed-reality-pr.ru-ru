---
title: Общие сведения о переносе
description: Общие сведения о различных вариантах переноса для переноса существующих приложений в смешанную реальность.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: Перенос, Unity, по промежуточного слоя, ядро, UWP, Win32
ms.openlocfilehash: 074e0792a5ed43bb56b8f337613234efbd166eb7
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443542"
---
# <a name="porting-overview"></a><span data-ttu-id="123b4-104">Общие сведения о переносе</span><span class="sxs-lookup"><span data-stu-id="123b4-104">Porting overview</span></span>

<span data-ttu-id="123b4-105">Когда речь идет о переносе или обновлении существующих проектов для смешанной реальности, в зависимости от того, было ли приложение создано с помощью Unity или нереального модуля, HoloLens (1 Gen) или HoloLens 2 или Стеамвр, могут применяться несколько сценариев.</span><span class="sxs-lookup"><span data-stu-id="123b4-105">When it comes to porting or upgrading your existing projects for Mixed Reality, several scenarios may apply depending on whether your app was built with Unity or Unreal Engine, HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="123b4-106">На этой странице обзора приведены текущие рекомендации для каждой платформы и устройства. Убедитесь, что эти процессы постоянно изменяются.</span><span class="sxs-lookup"><span data-stu-id="123b4-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="123b4-107">Сначала настройте целевую платформу проекта на основе нашего [Unity](#unity) и [нереальных](#unreal) рекомендаций, а затем выполните один или несколько сценариев переноса:</span><span class="sxs-lookup"><span data-stu-id="123b4-107">First, setup your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="123b4-108">HoloLens (1-й общий) в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="123b4-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="123b4-109">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="123b4-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="123b4-110">Приложения Стеамвр</span><span class="sxs-lookup"><span data-stu-id="123b4-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="123b4-111">Двумерные приложения UWP</span><span class="sxs-lookup"><span data-stu-id="123b4-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="123b4-112">Рекомендуемые целевые объекты проекта</span><span class="sxs-lookup"><span data-stu-id="123b4-112">Recommended project targets</span></span>

<span data-ttu-id="123b4-113">Важно регулярно обновляйте свои проекты, независимо от того, перенесено ли приложение на другое целевое устройство.</span><span class="sxs-lookup"><span data-stu-id="123b4-113">It's important to keep your projects up-to-date, whether or not your porting an app to another target device.</span></span> <span data-ttu-id="123b4-114">Для наших текущих рекомендаций см. Приведенные ниже ресурсы на основе подсистемы.</span><span class="sxs-lookup"><span data-stu-id="123b4-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="123b4-115">Unity</span><span class="sxs-lookup"><span data-stu-id="123b4-115">Unity</span></span>

<span data-ttu-id="123b4-116">Текущая рекомендация по разработке Unity в смешанной реальности — **Unity 2019 LTS с использованием устаревшего пакета XR**.</span><span class="sxs-lookup"><span data-stu-id="123b4-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="123b4-117">Если в проекте используется набор средств Mixed Reality, убедитесь, что вы используете последнюю версию, которая в настоящее время **мртк-Unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="123b4-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="123b4-118">Хотя пакет SDK для XR доступен в этой версии Unity, пространственные привязки Azure в настоящее время не совместимы с этой программой установки.</span><span class="sxs-lookup"><span data-stu-id="123b4-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="123b4-119">Эта рекомендация будет обновлена в будущем выпуске пакета пространственных привязок Azure для Unity.</span><span class="sxs-lookup"><span data-stu-id="123b4-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="123b4-120">Если вы не хотите получать пространственные привязки Azure, вы можете [настроить проект Unity для XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) и приступить [к работе с МРТК и XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span><span class="sxs-lookup"><span data-stu-id="123b4-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="123b4-121">Если вы используете в проекте пакет SDK для XR и хотите использовать пространственные привязки Azure, удалите пакет SDK для XR и переустановите устаревший пакет XR, чтобы отменить параметры проекта.</span><span class="sxs-lookup"><span data-stu-id="123b4-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="123b4-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="123b4-122">Unreal</span></span> 

<span data-ttu-id="123b4-123">Наша текущая рекомендация по нереальному развитию в смешанной реальности — это **нереалный механизм 4,26**.</span><span class="sxs-lookup"><span data-stu-id="123b4-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="123b4-124">Если в проекте используются средства UX набора средств для смешанной реальности, убедитесь, что вы используете последнюю версию, которая в настоящее время **укст 0,10**.</span><span class="sxs-lookup"><span data-stu-id="123b4-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="123b4-125">Сценарии переноса</span><span class="sxs-lookup"><span data-stu-id="123b4-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="123b4-126">Приложения Unity (1-го поколения) для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="123b4-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="123b4-127">При наличии существующего приложения Unity (1-го поколения), которое вы хотите перенести в HoloLens 2, следуйте инструкциям в [статье о переносе hololens](../unity/mrtk-porting-guide.md).</span><span class="sxs-lookup"><span data-stu-id="123b4-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="123b4-128">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="123b4-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="123b4-129">Если вы создали содержимое для других устройств, например Окулус Рифт или HP reverbа G2, вам потребуется перенацелить пакеты SDK для версий VR, зависящие от поставщика, и потенциальное сопоставление входных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="123b4-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to re-target vendor-specific VR SDKs and potentially input mapping APIs.</span></span> <span data-ttu-id="123b4-130">Сведения о сценариях Unity и нереальном переносе можно найти в статье о [переносе приложений в иммерсивное приложение](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="123b4-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="123b4-131">Стеамвр приложения</span><span class="sxs-lookup"><span data-stu-id="123b4-131">SteamVR applications</span></span>

<span data-ttu-id="123b4-132">Сведения о Стеамврх, которые вы хотите обновить для головных телефонов Windows Mixed Reality, см. в нашем [руководстве по обновлению стеамвр](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="123b4-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="123b4-133">Двумерные универсальные приложения Windows</span><span class="sxs-lookup"><span data-stu-id="123b4-133">2D Universal Windows applications</span></span>

<span data-ttu-id="123b4-134">Если у вас есть приложение 2D-приложения UWP, которое вы хотите перенести на иммерсивное или HoloLens Windows Mixed Reality, следуйте инструкциям в статье [о переносе приложений из 2D UWP для Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="123b4-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow the instructions in our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) article.</span></span>

