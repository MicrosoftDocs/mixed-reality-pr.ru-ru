---
title: Потеря службы отслеживания
description: Обзор службы Лосттраккинг в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176219"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="c6862-104">Потеря службы отслеживания</span><span class="sxs-lookup"><span data-stu-id="c6862-104">Lost tracking service</span></span>

![Отслеживание потерянных](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="c6862-106">потерянная служба расширения отслеживания предоставляет HoloLens анимированный визуальный элемент стиля оболочки для потерянного состояния отслеживания.</span><span class="sxs-lookup"><span data-stu-id="c6862-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="c6862-107">Использование потерянных расширений отслеживания</span><span class="sxs-lookup"><span data-stu-id="c6862-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="c6862-108">В профиле МРТК добавьте **потерянную службу отслеживания** в расширения.</span><span class="sxs-lookup"><span data-stu-id="c6862-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="c6862-109">Назначьте **дефаултлосттраккингсервицепрофиле** , включающий **лосттраккингвисуалпрефаб**.</span><span class="sxs-lookup"><span data-stu-id="c6862-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
