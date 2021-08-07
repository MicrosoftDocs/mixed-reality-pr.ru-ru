---
title: Средство отслеживания суставов руки
description: Часер муфта в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189571"
---
# <a name="hand-joint-chaser"></a>Средство отслеживания суставов руки

![Геосоединения ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) . в этом примере сцены показано, как использовать поиск решения для присоединения объектов к стыкам.

## <a name="example-scene"></a>Пример сцены

Пример сцены **ханджоинтчасерексампле** можно найти в `Assets/MRTK/Examples` папке в разделе `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Обработчик поиска решений

Щелкните элемент **Tracked (отслеживание), чтобы создать ссылку** , и выберите соединение с правой или **левой** стороны **соединения**. Вы сможете увидеть раскрывающийся список " **Отслеживание соединений** ". В раскрывающемся списке можно выбрать конкретное соединение для отслеживания. Этот пример сцены использует радиальный поисковый объект для создания объекта после целевого объекта. Дополнительные сведения см. на странице [поиска решения](../ux-building-blocks/solvers/solver.md) .

![Совместный поиск решения](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
