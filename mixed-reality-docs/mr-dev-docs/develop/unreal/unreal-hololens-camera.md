---
title: Фото- и видеокамера HoloLens в Unreal
description: Руководство по работе с фото- и видеокамерой HoloLens в Unreal
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера, фото-/видеокамера, MRC, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: fb7bbf5a0f41c15d73e59226dad32cda8764e6cc
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926100"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="ddf82-104">Фото- и видеокамера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="ddf82-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="ddf82-105">Устройство HoloLens оборудовано фотовидеокамерой, установленной на видоискателе, которую можно использовать для съемки смешанной реальности и для поиска объектов в мировом пространстве Unreal по пиксельным координатам в кадре камеры.</span><span class="sxs-lookup"><span data-stu-id="ddf82-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddf82-106">Фото-/видеокамера не поддерживается в голографическом удаленном взаимодействии, но вы можете использовать веб-камеру, подключенную к компьютеру, для имитации функциональности фото-/видеокамеры в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ddf82-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="ddf82-107">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="ddf82-107">Next Development Checkpoint</span></span>

<span data-ttu-id="ddf82-108">Если вы следуете изложенной нами стратегии разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="ddf82-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ddf82-109">Вы можете перейти к следующей статье:</span><span class="sxs-lookup"><span data-stu-id="ddf82-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ddf82-110">QR-коды</span><span class="sxs-lookup"><span data-stu-id="ddf82-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="ddf82-111">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="ddf82-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ddf82-112">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="ddf82-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="ddf82-113">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="ddf82-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddf82-114">См. также статью</span><span class="sxs-lookup"><span data-stu-id="ddf82-114">See also</span></span>
* [<span data-ttu-id="ddf82-115">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="ddf82-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="ddf82-116">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="ddf82-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
