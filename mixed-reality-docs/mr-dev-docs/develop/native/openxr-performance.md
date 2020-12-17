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
# <a name="openxr-performance"></a>Производительность OpenXR

В HoloLens 2 существует несколько способов отправки данных композиции с помощью `xrEndFrame` , что может привести к снижению производительности после обработки.
Чтобы избежать снижения производительности, [отправьте единое `XrCompositionProjectionLayer` значение](openxr-best-practices.md#use-a-single-projection-layer) со следующими характеристиками:
* [Использование имеющуюся цепочку буферов массива текстуры](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Использовать формат имеющуюся цепочку буферов основного цвета](openxr-best-practices.md#select-a-swapchain-format)
* [Использование рекомендуемых измерений представления](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Не задавать `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` флаг
* Задайте для параметра значение `XrCompositionLayerDepthInfoKHR` `minDepth` 0,0 f и `maxDepth` значение 1,0 f.

Для повышения производительности учитывайте следующее.
* [Использование 16-разрядного формата глубины](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Создание экземпляров Draw](openxr-best-practices.md#render-with-texture-array-and-vprt)
