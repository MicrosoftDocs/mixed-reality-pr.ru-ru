---
title: Производительность OpenXR
description: Узнайте, как выполнять отладку производительности GPU приложений Опенкср Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, производительность, оптимизация, отладка GPU, Рендердок, PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006764"
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
