---
title: Поставщики входных данных
description: Документация по различным типам поставщиков входных данных в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145262"
---
# <a name="input-providers"></a><span data-ttu-id="ec99f-104">Поставщики входных данных</span><span class="sxs-lookup"><span data-stu-id="ec99f-104">Input providers</span></span>

<span data-ttu-id="ec99f-105">Поставщики входных данных регистрируются в **профиле зарегистрированных поставщиков служб**, который находится в компоненте набора средств Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="ec99f-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="ec99f-106">Это поставщики входных данных, доступные из комплекта, вместе с соответствующими контроллерами:</span><span class="sxs-lookup"><span data-stu-id="ec99f-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="ec99f-107">Поставщик входных данных</span><span class="sxs-lookup"><span data-stu-id="ec99f-107">Input Provider</span></span> | <span data-ttu-id="ec99f-108">Контроллеры</span><span class="sxs-lookup"><span data-stu-id="ec99f-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="ec99f-109">Имитация руки</span><span class="sxs-lookup"><span data-stu-id="ec99f-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="ec99f-110">Мышь</span><span class="sxs-lookup"><span data-stu-id="ec99f-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="ec99f-111">Generic Опенвр, Naopak палочка, Naopak Кнукклес, Окулус Touch, Окулус Remote, Windows Mixed Reality Опенвр</span><span class="sxs-lookup"><span data-stu-id="ec99f-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="ec99f-112">Универсальный джойстик</span><span class="sxs-lookup"><span data-stu-id="ec99f-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="ec99f-113">Сенсорный контроллер Unity</span><span class="sxs-lookup"><span data-stu-id="ec99f-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="ec99f-114">*Нет*</span><span class="sxs-lookup"><span data-stu-id="ec99f-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="ec99f-115">ВМРая рука, ВМР контроллер, ВМР ГГВ (взгляд, жест и речь)</span><span class="sxs-lookup"><span data-stu-id="ec99f-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="ec99f-116">*Нет*</span><span class="sxs-lookup"><span data-stu-id="ec99f-116">*None*</span></span> |

<span data-ttu-id="ec99f-117">Поставщики диктовки и речи не создают контроллеры, они создают собственные специализированные события ввода.</span><span class="sxs-lookup"><span data-stu-id="ec99f-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="ec99f-118">Пользовательские поставщики входных данных могут быть созданы путем реализации [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec99f-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="ec99f-119">Дополнительные сведения см. в разделе [Создание входного системного поставщика данных](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ec99f-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
