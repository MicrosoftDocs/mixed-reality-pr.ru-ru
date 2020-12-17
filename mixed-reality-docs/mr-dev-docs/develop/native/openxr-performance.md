---
title: Производительность OpenXR
description: Отлаживать производительность приложений Опенкср в графическом процессоре.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, производительность, оптимизация, отладка GPU, Рендердок, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613178"
---
# <a name="openxr-performance"></a><span data-ttu-id="d5751-104">Производительность OpenXR</span><span class="sxs-lookup"><span data-stu-id="d5751-104">OpenXR performance</span></span>

<span data-ttu-id="d5751-105">В HoloLens 2 существует несколько способов отправки данных композиции с помощью `xrEndFrame` , что может привести к снижению производительности после обработки.</span><span class="sxs-lookup"><span data-stu-id="d5751-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="d5751-106">Чтобы избежать снижения производительности, [отправьте единое `XrCompositionProjectionLayer` значение](openxr-best-practices.md#use-a-single-projection-layer) со следующими характеристиками:</span><span class="sxs-lookup"><span data-stu-id="d5751-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="d5751-107">Использование имеющуюся цепочку буферов массива текстуры</span><span class="sxs-lookup"><span data-stu-id="d5751-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="d5751-108">Использовать формат имеющуюся цепочку буферов основного цвета</span><span class="sxs-lookup"><span data-stu-id="d5751-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="d5751-109">Использование рекомендуемых измерений представления</span><span class="sxs-lookup"><span data-stu-id="d5751-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="d5751-110">Не задавать `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` флаг</span><span class="sxs-lookup"><span data-stu-id="d5751-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="d5751-111">Задайте для параметра значение `XrCompositionLayerDepthInfoKHR` `minDepth` 0,0 f и `maxDepth` значение 1,0 f.</span><span class="sxs-lookup"><span data-stu-id="d5751-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="d5751-112">Для повышения производительности учитывайте следующее.</span><span class="sxs-lookup"><span data-stu-id="d5751-112">For better performance, consider:</span></span>
* [<span data-ttu-id="d5751-113">Использование 16-разрядного формата глубины</span><span class="sxs-lookup"><span data-stu-id="d5751-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="d5751-114">Создание экземпляров Draw</span><span class="sxs-lookup"><span data-stu-id="d5751-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
