---
title: Средство отслеживания суставов руки
description: Часер муфта в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144623"
---
# <a name="hand-joint-chaser-example"></a>Пример однопользовательского соединения Часер

![Геосоединения ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) . в этом примере сцены показано, как использовать поиск решения для присоединения объектов к стыкам.

## <a name="example-scene"></a>Пример сцены

Пример сцены **ханджоинтчасерексампле** можно найти в `Assets/MRTK/Examples` папке в разделе `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Обработчик поиска решений

Щелкните элемент **Tracked (отслеживание), чтобы создать ссылку** , и выберите соединение с правой или **левой** стороны **соединения**. Вы сможете увидеть раскрывающийся список " **Отслеживание соединений** ". В раскрывающемся списке можно выбрать конкретное соединение для отслеживания. Этот пример сцены использует радиальный поисковый объект для создания объекта после целевого объекта. Дополнительные сведения см. на странице [поиска решения](../ux-building-blocks/solvers/solver.md) .

![Совместный поиск решения](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
