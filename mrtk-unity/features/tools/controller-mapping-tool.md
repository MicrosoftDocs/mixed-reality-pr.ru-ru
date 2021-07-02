---
title: Средство сопоставления контроллеров
description: Документация по средству сопоставления контроллеров в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176172"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="fa882-104">Средство сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="fa882-104">Controller mapping tool</span></span>

<span data-ttu-id="fa882-105">Средство сопоставления контроллеров — это среда выполнения (на устройстве или в редакторе), позволяющая разработчикам быстро определять сопоставления входной оси и кнопки Unity для контроллера оборудования (например, контроллера движения).</span><span class="sxs-lookup"><span data-stu-id="fa882-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="fa882-106">Это средство очень полезно при разработке поддержки нового аппаратного контроллера.</span><span class="sxs-lookup"><span data-stu-id="fa882-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="fa882-107">Кроме того, он может помочь в подтверждении проблемы сопоставления элементов управления в классе поддержки для существующего контроллера.</span><span class="sxs-lookup"><span data-stu-id="fa882-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Средство сопоставления контроллеров](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="fa882-109">Использование средства сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="fa882-109">Using the controller mapping tool</span></span>

<span data-ttu-id="fa882-110">Чтобы начать работу с средством сопоставления контроллеров, перейдите в раздел **мртк/Tools/рунтиметулс/Tools/контроллермаппингтул** и откройте сцену **контроллермаппингтул** .</span><span class="sxs-lookup"><span data-stu-id="fa882-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="fa882-111">После загрузки сцены проект можно либо запустить в редакторе, использовать режим воспроизведения, либо построить и запустить на устройстве.</span><span class="sxs-lookup"><span data-stu-id="fa882-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="fa882-112">Чтобы проверить сопоставления Unity для контроллера, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="fa882-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="fa882-113">Подключение контроллера</span><span class="sxs-lookup"><span data-stu-id="fa882-113">Connect the controller</span></span>
- <span data-ttu-id="fa882-114">Нажмите каждую кнопку и переместите каждую ось.</span><span class="sxs-lookup"><span data-stu-id="fa882-114">Press each button and move each axis</span></span>
- <span data-ttu-id="fa882-115">Обратите внимание на сопоставления в отображении</span><span class="sxs-lookup"><span data-stu-id="fa882-115">Note the mappings in the display</span></span>
- <span data-ttu-id="fa882-116">Обновление сопоставлений элементов управления в поставщике входных системных данных для контроллера</span><span class="sxs-lookup"><span data-stu-id="fa882-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="fa882-117">средство сопоставления контроллеров не использует компоненты набор средств Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fa882-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="fa882-118">Он напрямую взаимодействует с Unity для определения и отображения сопоставлений элементов управления.</span><span class="sxs-lookup"><span data-stu-id="fa882-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="fa882-119">Все элементы управления отображаются</span><span class="sxs-lookup"><span data-stu-id="fa882-119">All controls display</span></span>

<span data-ttu-id="fa882-120">Большая панель отображения сообщает состояние всех определенных входных осей и кнопок Unity (например, ось 10, кнопка 3).</span><span class="sxs-lookup"><span data-stu-id="fa882-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="fa882-121">Эта панель обеспечивает полное представление состояния контроллера.</span><span class="sxs-lookup"><span data-stu-id="fa882-121">This panel provides a complete view of the state of the controller.</span></span>

![Все элементы управления отображаются](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="fa882-123">Отображение активных элементов управления</span><span class="sxs-lookup"><span data-stu-id="fa882-123">Active controls display</span></span>

<span data-ttu-id="fa882-124">Меньшая, узкая панель отображения показывает входные аксед и кнопки Unity, которые находятся в активном состоянии (например, нажата кнопка).</span><span class="sxs-lookup"><span data-stu-id="fa882-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="fa882-125">Отображение активных элементов управления позволяет легко читать сводное представление состояния контроллера.</span><span class="sxs-lookup"><span data-stu-id="fa882-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Отображение активных элементов управления](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="fa882-127">См. также:</span><span class="sxs-lookup"><span data-stu-id="fa882-127">See also</span></span>

- [<span data-ttu-id="fa882-128">Создание поставщика входных системных данных</span><span class="sxs-lookup"><span data-stu-id="fa882-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="fa882-129">Средство Инпутфеатуреусаже</span><span class="sxs-lookup"><span data-stu-id="fa882-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
