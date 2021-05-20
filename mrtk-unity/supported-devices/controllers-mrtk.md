---
title: Контроллеры в МРТК
description: Документация по использованию различных контроллеров с МРТК
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, контроллеры, HP REVERB, Окулус, HTC Naopak, руки
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145489"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="4a4ba-104">Контроллеры в МРТК</span><span class="sxs-lookup"><span data-stu-id="4a4ba-104">Controllers in MRTK</span></span>

<span data-ttu-id="4a4ba-105">МРТК поддерживает множество различных контроллеров.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="4a4ba-106">Многие контроллеры, такие как HTC Naopak Кнукклес и HTC Naopak, будут работать изначально, как только приложение, созданное с помощью МРТК, будет запущено на совместимом устройстве.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="4a4ba-107">Другие контроллеры, например, наокулусные руки и контроллеры HP, G2, потребовали дополнительных пакетов, прежде чем они будут распознаны МРТК.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="4a4ba-108">В этом документе описаны распространенные сценарии, в которых необходимо установить дополнительные пакеты.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="4a4ba-109">Дополнительные сведения об контроллерах см. на [**странице функций**](../features/input/controllers.md).</span><span class="sxs-lookup"><span data-stu-id="4a4ba-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="4a4ba-110">Сведения об отладке проблем с контроллерами см. в разделе [ **средство сопоставления контроллеров** .](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="4a4ba-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="4a4ba-111">HP reverbы G2 контроллеры</span><span class="sxs-lookup"><span data-stu-id="4a4ba-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="4a4ba-112">Для обнаружения и отображения контроллеров команды HP с переглаголом G2 при использовании МРТК выполните следующие действия, чтобы установить пакет [**Microsoft. микседреалити. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) .</span><span class="sxs-lookup"><span data-stu-id="4a4ba-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="4a4ba-113">После установки этого пакета никакие другие изменения профилей по умолчанию не требуются, чтобы контроллеры отображались в переглаголе HP.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="4a4ba-114">Чтобы отобразить контроллеры в редакторе, необходимо убедиться, что используется [**подключаемый модуль опенкср**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span><span class="sxs-lookup"><span data-stu-id="4a4ba-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="4a4ba-115">Контроллеры Окулус</span><span class="sxs-lookup"><span data-stu-id="4a4ba-115">Oculus Controllers</span></span> 

<span data-ttu-id="4a4ba-116">Для визуализации моделей контроллеров Окулус следуйте инструкциям по развертыванию Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="4a4ba-117">Если вы хотите отображать виртуальные руки при использовании контроллеров, убедитесь, что в разделе XR SDK диспетчер устройств Окулус, который используется для отображения **аватара, вместо контроллеров** выбрана проверка.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="4a4ba-118">В противном случае снимите этот флажок.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-118">Otherwise, uncheck this option.</span></span>

![окулусдевицеманажервисуализатионсеттингс](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
