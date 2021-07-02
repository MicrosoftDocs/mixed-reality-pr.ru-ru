---
title: Часер муфта
description: Часер муфта в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175358"
---
# <a name="hand-joint-chaser"></a>Часер муфта

![Геосоединения ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) . в этом примере сцены показано, как использовать поиск решения для присоединения объектов к стыкам.

## <a name="example-scene"></a>Пример сцены

Пример сцены **ханджоинтчасерексампле** можно найти в `Assets/MRTK/Examples` папке в разделе `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Обработчик поиска решений

Щелкните элемент **Tracked (отслеживание), чтобы создать ссылку** , и выберите соединение с правой или **левой** стороны **соединения**. Вы сможете увидеть раскрывающийся список " **Отслеживание соединений** ". В раскрывающемся списке можно выбрать конкретное соединение для отслеживания. Этот пример сцены использует радиальный поисковый объект для создания объекта после целевого объекта. Дополнительные сведения см. на странице [поиска решения](../ux-building-blocks/solvers/solver.md) .

![Совместный поиск решения](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
