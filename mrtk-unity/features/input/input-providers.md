---
title: Поставщики входных данных
description: Документация по различным типам поставщиков входных данных в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176753"
---
# <a name="input-providers"></a><span data-ttu-id="f07d8-104">Поставщики входных данных</span><span class="sxs-lookup"><span data-stu-id="f07d8-104">Input providers</span></span>

<span data-ttu-id="f07d8-105">поставщики входных данных зарегистрированы в **профиле зарегистрированных поставщиков служб**, который находится в компоненте набор средств смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="f07d8-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="f07d8-106">Это поставщики входных данных, доступные из комплекта, вместе с соответствующими контроллерами:</span><span class="sxs-lookup"><span data-stu-id="f07d8-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="f07d8-107">Поставщик входных данных</span><span class="sxs-lookup"><span data-stu-id="f07d8-107">Input Provider</span></span> | <span data-ttu-id="f07d8-108">Контроллеры</span><span class="sxs-lookup"><span data-stu-id="f07d8-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="f07d8-109">Имитация руки</span><span class="sxs-lookup"><span data-stu-id="f07d8-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="f07d8-110">Мышь</span><span class="sxs-lookup"><span data-stu-id="f07d8-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="f07d8-111">Generic опенвр, naopak палочка, naopak кнукклес, окулус Touch, окулус Remote, Windows Mixed Reality опенвр</span><span class="sxs-lookup"><span data-stu-id="f07d8-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="f07d8-112">Универсальный джойстик</span><span class="sxs-lookup"><span data-stu-id="f07d8-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="f07d8-113">Сенсорный контроллер Unity</span><span class="sxs-lookup"><span data-stu-id="f07d8-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="f07d8-114">*Нет*</span><span class="sxs-lookup"><span data-stu-id="f07d8-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="f07d8-115">ВМРая рука, ВМР контроллер, ВМР ГГВ (взгляд, жест и речь)</span><span class="sxs-lookup"><span data-stu-id="f07d8-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="f07d8-116">*Нет*</span><span class="sxs-lookup"><span data-stu-id="f07d8-116">*None*</span></span> |

<span data-ttu-id="f07d8-117">Поставщики диктовки и речи не создают контроллеры, они создают собственные специализированные события ввода.</span><span class="sxs-lookup"><span data-stu-id="f07d8-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="f07d8-118">Пользовательские поставщики входных данных могут быть созданы путем реализации [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f07d8-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="f07d8-119">Дополнительные сведения см. в разделе [Создание входного системного поставщика данных](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f07d8-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
