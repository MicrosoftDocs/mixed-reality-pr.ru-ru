---
title: Использование Вебкср с Windows Mixed Reality
description: Общие сведения об использовании и разработке для Вебкср в Windows Mixed Reality
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Вебкср, Винмр, Вебар, Вебвр, Виндовсмикседреалити, HoloLens, Windows Mixed Reality, веб-VR, Web XR, Web MR, Web AR, 360, 360 Video, 360 видео, 360 Photo, 360 фотографии, 360 Content, иммерсивное веб-, иммерсивевеб, IW
ms.openlocfilehash: b72d4968e59e3e631138b1ecfd17ca9bbdd95c84
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416875"
---
# <a name="webxr-overview"></a><span data-ttu-id="84cc6-104">Обзор Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="84cc6-105">Что такое Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-105">What is WebXR</span></span>

<span data-ttu-id="84cc6-106">**API устройства вебкср** предназначен для доступа к устройствам **Virtual Reality (VR)** и **дополненным (AR)** , включая **датчики** и **подключенные к головным выдисплеям** в **Интернете**.</span><span class="sxs-lookup"><span data-stu-id="84cc6-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="84cc6-107">API устройства Вебкср в настоящее время доступен в Microsoft погранично, а версия Chrome 79 и более поздних версий поддерживает Вебкср по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="84cc6-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="84cc6-108">Последнюю версию поддержки браузера для Вебкср можно узнать по адресу [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="84cc6-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="84cc6-109">Узнайте больше о [Windows Mixed Reality и новом Microsoft ребре](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)в разделе [новые](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) возможности.</span><span class="sxs-lookup"><span data-stu-id="84cc6-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="84cc6-110">Просмотр Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84cc6-111">Microsoft ребро (устаревшая версия) поддерживает только Вебвр, нерекомендуемый API, недоступный в текущих браузерах.</span><span class="sxs-lookup"><span data-stu-id="84cc6-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="84cc6-112">Однако новый **[браузер Chromium под управлением](../../whats-new/new-microsoft-edge.md)** Windows поддерживает вебкср и доступен для создания прототипов VR в операционной системе Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="84cc6-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="84cc6-113">Вебвр не будет доступен в новом браузере на основе Chromium.</span><span class="sxs-lookup"><span data-stu-id="84cc6-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="84cc6-114">Если вы ищете способ создания прототипов Вебкср в HoloLens 2 сегодня, ознакомьтесь с [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="84cc6-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="84cc6-115">Чтобы проверить, поддерживает ли ваш браузер Вебкср, перейдите к [примерам вебкср](https://immersive-web.github.io/webxr-samples/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="84cc6-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="84cc6-116">См. также:</span><span class="sxs-lookup"><span data-stu-id="84cc6-116">See Also</span></span>

* [<span data-ttu-id="84cc6-117">Спецификация API устройства Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="84cc6-118">Документация по API устройства Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="84cc6-119">Иммерсивевеб. dev</span><span class="sxs-lookup"><span data-stu-id="84cc6-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="84cc6-120">Примеры Вебкср</span><span class="sxs-lookup"><span data-stu-id="84cc6-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="84cc6-121">Windows Mixed Reality и новая Microsoft ребро</span><span class="sxs-lookup"><span data-stu-id="84cc6-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="84cc6-122">Иммерсивное веб-сайт W3C GitHub</span><span class="sxs-lookup"><span data-stu-id="84cc6-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="84cc6-123">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="84cc6-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="84cc6-124">Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета</span><span class="sxs-lookup"><span data-stu-id="84cc6-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="84cc6-125">Обработка потерянного контекста в WebGL</span><span class="sxs-lookup"><span data-stu-id="84cc6-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="84cc6-126">поинтерлокк</span><span class="sxs-lookup"><span data-stu-id="84cc6-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="84cc6-127">глтф</span><span class="sxs-lookup"><span data-stu-id="84cc6-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="84cc6-128">Использование Babylon.js для создания Вебксрных возможностей</span><span class="sxs-lookup"><span data-stu-id="84cc6-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="84cc6-129">Группа иммерсивного веб-сообщества</span><span class="sxs-lookup"><span data-stu-id="84cc6-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
