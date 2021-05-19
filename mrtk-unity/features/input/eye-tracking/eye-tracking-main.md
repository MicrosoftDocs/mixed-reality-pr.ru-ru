---
title: Отслеживание взгляда
description: Целевая страница отслеживания взгляда в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг,
ms.openlocfilehash: 2ee19cab7a7e8ec954f7694c8f06c836d5510644
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144010"
---
# <a name="eye-tracking-in-the-mixed-reality-toolkit"></a><span data-ttu-id="a12e0-104">Отслеживание взгляда в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a12e0-104">Eye tracking in the Mixed Reality Toolkit</span></span>

![Отслеживание взглядов в МРТК](../../images/eye-tracking/mrtk_et_compilation.png)

<span data-ttu-id="a12e0-106">_HoloLens 2_ предлагает привлекательный и мощный новый ввод: отслеживание взгляда!</span><span class="sxs-lookup"><span data-stu-id="a12e0-106">_HoloLens 2_ offers an exciting and powerful new input: Eye tracking!</span></span>
<span data-ttu-id="a12e0-107">Отслеживание взгляда позволяет пользователям быстро и легко привлекаться к голограммам в их представлениях и может сделать систему более эффективной, чем лучше определить намерение пользователя.</span><span class="sxs-lookup"><span data-stu-id="a12e0-107">Eye tracking enables users to quickly and effortlessly engage with holograms across their view and can make your system smarter by better identifying a user's intention.</span></span> <span data-ttu-id="a12e0-108">Дополнительные сведения см. в документации по смешанной реальности Microsoft для [отслеживания взгляда на HoloLens 2](/windows/mixed-reality/eye-tracking) , например для объяснения эффективных приложений и руководств по проектированию для отслеживания взглядов в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a12e0-108">Check out Microsoft's Mixed Reality [documentation on eye tracking on HoloLens 2](/windows/mixed-reality/eye-tracking) for more details, such as explaining powerful applications and design guidelines for eye tracking in mixed reality.</span></span>

<span data-ttu-id="a12e0-109">Не знакомы с отслеживанием взгляда?</span><span class="sxs-lookup"><span data-stu-id="a12e0-109">New to eye tracking?</span></span> <span data-ttu-id="a12e0-110">Это не проблема!</span><span class="sxs-lookup"><span data-stu-id="a12e0-110">No problem!</span></span> <span data-ttu-id="a12e0-111">Существует ряд видеороликов, руководств и примеров, которые помогут вам начать работу с [набором средств Mixed Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="a12e0-111">There are a number of videos, tutorials and samples to get you started in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)!</span></span>
<span data-ttu-id="a12e0-112">Рекомендуется начать с изучения некоторых существующих примеров отслеживания взгляда, демонстрирующих рекомендации по взаимодействию на основе взгляда.</span><span class="sxs-lookup"><span data-stu-id="a12e0-112">It is recommended to start by exploring some of the existing eye tracking samples that demonstrate best practices for eye-based interactions.</span></span> <span data-ttu-id="a12e0-113">Затем эти примеры можно использовать для извлечения частей, которые кажутся актуальными для вас в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="a12e0-113">You can then use these samples to pull the parts that seem relevant to you into your app.</span></span> <span data-ttu-id="a12e0-114">Наконец, мы также опишем, как настроить новую сцену с основными компонентами, чтобы отслеживать работу в приложении.</span><span class="sxs-lookup"><span data-stu-id="a12e0-114">Finally, we also describe how to set up a fresh scene with the core components to get eye tracking working in your app.</span></span>

1. [<span data-ttu-id="a12e0-115">Примеры отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="a12e0-115">MRTK eye tracking samples</span></span>](../../example-scenes/eye-tracking-examples-overview.md)

2. [<span data-ttu-id="a12e0-116">Настройка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="a12e0-116">MRTK eye tracking setup</span></span>](eye-tracking-basic-setup.md)

3. [<span data-ttu-id="a12e0-117">Доступ к данным отслеживания взгляда с помощью кода</span><span class="sxs-lookup"><span data-stu-id="a12e0-117">Accessing eye tracking data via Code</span></span>](eye-tracking-eye-gaze-provider.md)

4. [<span data-ttu-id="a12e0-118">Проверка калибровки отслеживания взгляда на устройстве</span><span class="sxs-lookup"><span data-stu-id="a12e0-118">Validate eye tracking calibration on device</span></span>](eye-tracking-is-user-calibrated.md)

## <a name="see-also"></a><span data-ttu-id="a12e0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a12e0-119">See also</span></span>

- [<span data-ttu-id="a12e0-120">Настройка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="a12e0-120">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="a12e0-121">Отслеживание взгляда МРТК с помощью кода</span><span class="sxs-lookup"><span data-stu-id="a12e0-121">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="a12e0-122">Калибровка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="a12e0-122">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="a12e0-123">Документация по отслеживания взгляда HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a12e0-123">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)