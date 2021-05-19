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
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="00ead-104">Пример однопользовательского соединения Часер</span><span class="sxs-lookup"><span data-stu-id="00ead-104">Hand joint chaser example</span></span>

<span data-ttu-id="00ead-105">![Геосоединения ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) . в этом примере сцены показано, как использовать поиск решения для присоединения объектов к стыкам.</span><span class="sxs-lookup"><span data-stu-id="00ead-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="00ead-106">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="00ead-106">Example scene</span></span>

<span data-ttu-id="00ead-107">Пример сцены **ханджоинтчасерексампле** можно найти в `Assets/MRTK/Examples` папке в разделе `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="00ead-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="00ead-108">Обработчик поиска решений</span><span class="sxs-lookup"><span data-stu-id="00ead-108">Solver handler</span></span>

<span data-ttu-id="00ead-109">Щелкните элемент **Tracked (отслеживание), чтобы создать ссылку** , и выберите соединение с правой или **левой** стороны **соединения**.</span><span class="sxs-lookup"><span data-stu-id="00ead-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="00ead-110">Вы сможете увидеть раскрывающийся список " **Отслеживание соединений** ".</span><span class="sxs-lookup"><span data-stu-id="00ead-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="00ead-111">В раскрывающемся списке можно выбрать конкретное соединение для отслеживания. Этот пример сцены использует радиальный поисковый объект для создания объекта после целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="00ead-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="00ead-112">Дополнительные сведения см. на странице [поиска решения](../ux-building-blocks/solvers/solver.md) .</span><span class="sxs-lookup"><span data-stu-id="00ead-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Совместный поиск решения](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
