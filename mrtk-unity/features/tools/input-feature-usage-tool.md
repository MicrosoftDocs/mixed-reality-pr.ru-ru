---
title: Средство использования функции ввода
description: Средство Инпутфеатуреусаже документации в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145015"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="f8637-104">Средство Инпутфеатуреусаже</span><span class="sxs-lookup"><span data-stu-id="f8637-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="f8637-105">Средство Инпутфеатуреусаже — это среда выполнения (на устройстве или в редакторе), которая позволяет разработчикам быстро определить доступный Инпутфеатуреусажес Unity для обнаруженного источника входных данных (например, контроллера движения или руки).</span><span class="sxs-lookup"><span data-stu-id="f8637-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="f8637-106">Эта сцена работает только в Unity 2019,3 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f8637-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="f8637-107">Это средство очень полезно при разработке поддержки нового аппаратного контроллера.</span><span class="sxs-lookup"><span data-stu-id="f8637-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="f8637-108">Кроме того, он может помочь в подтверждении проблемы сопоставления элементов управления в классе поддержки для существующего контроллера.</span><span class="sxs-lookup"><span data-stu-id="f8637-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Средство Инпутфеатуреусаже](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="f8637-110">Использование средства Инпутфеатуреусаже</span><span class="sxs-lookup"><span data-stu-id="f8637-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="f8637-111">Чтобы приступить к работе с инструментом Инпутфеатуреусаже, перейдите в раздел **мртк/Tools/рунтиметулс/Tools/инпутфеатуреусажетул** и откройте сцену **инпутфеатуреусажетул** .</span><span class="sxs-lookup"><span data-stu-id="f8637-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="f8637-112">После загрузки сцены проект можно либо запустить в редакторе, использовать режим воспроизведения, либо построить и запустить на устройстве.</span><span class="sxs-lookup"><span data-stu-id="f8637-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="f8637-113">Чтобы проверить сопоставления Unity для контроллера, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="f8637-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="f8637-114">Подключение контроллера</span><span class="sxs-lookup"><span data-stu-id="f8637-114">Connect the controller</span></span>
- <span data-ttu-id="f8637-115">Нажмите каждую кнопку и переместите каждую ось.</span><span class="sxs-lookup"><span data-stu-id="f8637-115">Press each button and move each axis</span></span>
- <span data-ttu-id="f8637-116">Обратите внимание на использование функций на экране.</span><span class="sxs-lookup"><span data-stu-id="f8637-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="f8637-117">Обновление сопоставлений элементов управления в поставщике входных системных данных для контроллера</span><span class="sxs-lookup"><span data-stu-id="f8637-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="f8637-118">Средство Инпутфеатуреусаже не использует компоненты набора средств Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f8637-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="f8637-119">Он напрямую взаимодействует с Unity для определения и вывода сведений об использовании компонентов.</span><span class="sxs-lookup"><span data-stu-id="f8637-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="f8637-120">Панели</span><span class="sxs-lookup"><span data-stu-id="f8637-120">Panels</span></span>

<span data-ttu-id="f8637-121">Панели отображают текущее состояние всех сообщаемых Инпутфеатуреусажес во всех обнаруженных источниках входных данных Unity.</span><span class="sxs-lookup"><span data-stu-id="f8637-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="f8637-122">На панели меньшего размера вверху перечислены имена всех обнаруженных источников.</span><span class="sxs-lookup"><span data-stu-id="f8637-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8637-123">См. также</span><span class="sxs-lookup"><span data-stu-id="f8637-123">See also</span></span>

- [<span data-ttu-id="f8637-124">Создание поставщика входных системных данных</span><span class="sxs-lookup"><span data-stu-id="f8637-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="f8637-125">Средство сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="f8637-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
