---
title: Общие сведения о переносе
description: Общие сведения о различных вариантах переноса для использования существующих приложений в смешанной реальности для HoloLens и VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Перенос, Unity, по промежуточного слоя, ядро, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600503"
---
# <a name="porting-overview"></a><span data-ttu-id="ef743-104">Общие сведения о переносе</span><span class="sxs-lookup"><span data-stu-id="ef743-104">Porting overview</span></span>

<span data-ttu-id="ef743-105">Когда речь идет о переносе или обновлении существующих проектов для смешанной реальности, ваш путь переноса зависит от того, создано ли приложение с помощью Unity или нереального механизма, и целевые объекты HoloLens (1 Gen) или HoloLens 2 или Стеамвр.</span><span class="sxs-lookup"><span data-stu-id="ef743-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="ef743-106">На этой странице обзора приведены текущие рекомендации для каждой платформы и устройства. Убедитесь, что эти процессы постоянно изменяются.</span><span class="sxs-lookup"><span data-stu-id="ef743-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="ef743-107">Сначала настройте целевой объект проекта на основе нашего [Unity](#unity) и [нереальных](#unreal) рекомендаций, а затем выполните один или несколько сценариев переноса:</span><span class="sxs-lookup"><span data-stu-id="ef743-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="ef743-108">HoloLens (1-й общий) в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ef743-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="ef743-109">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="ef743-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="ef743-110">Приложения Стеамвр</span><span class="sxs-lookup"><span data-stu-id="ef743-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="ef743-111">Двумерные приложения UWP</span><span class="sxs-lookup"><span data-stu-id="ef743-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="ef743-112">Рекомендуемые целевые объекты проекта</span><span class="sxs-lookup"><span data-stu-id="ef743-112">Recommended project targets</span></span>

<span data-ttu-id="ef743-113">Важно регулярно обновляйте свои проекты, будь то перенос приложения на другое целевое устройство.</span><span class="sxs-lookup"><span data-stu-id="ef743-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="ef743-114">Для наших текущих рекомендаций см. Приведенные ниже ресурсы на основе подсистемы.</span><span class="sxs-lookup"><span data-stu-id="ef743-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="ef743-115">Unity</span><span class="sxs-lookup"><span data-stu-id="ef743-115">Unity</span></span>

<span data-ttu-id="ef743-116">Текущая рекомендация по разработке Unity в смешанной реальности — **Unity 2019 LTS с использованием устаревшего пакета XR**.</span><span class="sxs-lookup"><span data-stu-id="ef743-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="ef743-117">Если в проекте используется набор средств Mixed Reality, убедитесь, что вы используете последнюю версию, которая в настоящее время **мртк-Unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="ef743-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="ef743-118">Хотя пакет SDK для XR доступен в этой версии Unity, пространственные привязки Azure в настоящее время не совместимы с этой программой установки.</span><span class="sxs-lookup"><span data-stu-id="ef743-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="ef743-119">Эта рекомендация будет обновлена в будущем выпуске пакета пространственных привязок Azure для Unity.</span><span class="sxs-lookup"><span data-stu-id="ef743-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="ef743-120">Если вы не хотите получать пространственные привязки Azure, вы можете [настроить проект Unity для XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) и приступить [к работе с МРТК и XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span><span class="sxs-lookup"><span data-stu-id="ef743-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="ef743-121">Если вы используете в проекте пакет SDK для XR и хотите использовать пространственные привязки Azure, удалите пакет SDK для XR и переустановите устаревший пакет XR, чтобы отменить параметры проекта.</span><span class="sxs-lookup"><span data-stu-id="ef743-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="ef743-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="ef743-122">Unreal</span></span>

<span data-ttu-id="ef743-123">Наша текущая рекомендация по нереальному развитию в смешанной реальности — это **нереалный механизм 4,26**.</span><span class="sxs-lookup"><span data-stu-id="ef743-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="ef743-124">Если в проекте используются средства UX набора средств для смешанной реальности, убедитесь, что вы используете последнюю версию, которая в настоящее время **укст 0,10**.</span><span class="sxs-lookup"><span data-stu-id="ef743-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="ef743-125">Сценарии переноса</span><span class="sxs-lookup"><span data-stu-id="ef743-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="ef743-126">Приложения Unity (1-го поколения) для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ef743-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="ef743-127">При наличии существующего приложения Unity (1-го поколения), которое вы хотите перенести в HoloLens 2, следуйте инструкциям в [статье о переносе hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="ef743-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="ef743-128">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="ef743-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="ef743-129">Если вы создали содержимое для других устройств, например Окулус Рифт или HP reverbа G2, вам потребуется перенацелить пакеты SDK для версий VR, зависящие от поставщика, и потенциальные API-интерфейсы сопоставления ввода.</span><span class="sxs-lookup"><span data-stu-id="ef743-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="ef743-130">Сведения о сценариях Unity и нереальном переносе можно найти в статье о [переносе приложений в иммерсивное приложение](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="ef743-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="ef743-131">Стеамвр приложения</span><span class="sxs-lookup"><span data-stu-id="ef743-131">SteamVR applications</span></span>

<span data-ttu-id="ef743-132">Сведения о Стеамврх, которые вы хотите обновить для головных телефонов Windows Mixed Reality, см. в нашем [руководстве по обновлению стеамвр](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="ef743-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="ef743-133">Двумерные универсальные приложения Windows</span><span class="sxs-lookup"><span data-stu-id="ef743-133">2D Universal Windows applications</span></span>

<span data-ttu-id="ef743-134">Если у вас есть приложение 2D-приложения UWP, которое вы хотите перенести на иммерсивное или HoloLens Windows Mixed Reality, следуйте инструкциям по [переносу двумерных приложений UWP для Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="ef743-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>