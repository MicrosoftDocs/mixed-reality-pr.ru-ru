---
title: Производительность OpenXR
description: Отлаживать производительность приложений Опенкср в графическом процессоре.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, производительность, оптимизация, отладка GPU, Рендердок, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691476"
---
# <a name="openxr-performance"></a>Производительность OpenXR

В HoloLens 2 существует несколько способов отправки данных композиции `xrEndFrame` , в результате которых будет возникать заметное снижение производительности.
Чтобы избежать штрафов в производительности, [отправьте единое `XrCompositionProjectionLayer` значение](openxr-best-practices.md#use-a-single-projection-layer) со следующими характеристиками:
* [Использование имеющуюся цепочку буферов массива текстуры](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Использовать формат имеющуюся цепочку буферов основного цвета](openxr-best-practices.md#select-a-swapchain-format)
* [Использование рекомендуемых измерений представления](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Не устанавливайте `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` флаг
* Задайте для параметра значение `XrCompositionLayerDepthInfoKHR` `minDepth` 0,0 f и `maxDepth` значение 1,0 f.

Дополнительные соображения приводят к лучшей производительности:
* [Использовать 16-разрядный формат глубины](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Сделать экземпляры вызовов Draw](openxr-best-practices.md#render-with-texture-array-and-vprt)
