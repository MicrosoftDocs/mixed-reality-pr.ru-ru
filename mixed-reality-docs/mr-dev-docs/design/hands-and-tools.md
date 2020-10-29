---
title: Руки и контроллеры движений
description: Сведения о моделях взаимодействия с моделями и контроллерами движения, которые могут удалить границу между виртуальными и физическими.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанная реальность, руки, контроллеры движения, взаимодействие, проектирование
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91693005"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="2f163-104">Руки и контроллеры движений</span><span class="sxs-lookup"><span data-stu-id="2f163-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="2f163-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="2f163-105">Scenarios</span></span>
<span data-ttu-id="2f163-106">Если вы решили применить эту модель взаимодействия после считывания [обзора взаимодействия](interaction-fundamentals.md), это означает, что вы разрабатываете приложение, которое требует от пользователей использовать две руки для взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="2f163-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="2f163-107">В приложении будет достигнута цель удаления границы между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="2f163-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="2f163-108">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="2f163-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="2f163-109">Предоставление информационных работников на двухмерных виртуальных экранах с возможностью пользовательского интерфейса для просмотра содержимого и управления им.</span><span class="sxs-lookup"><span data-stu-id="2f163-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="2f163-110">Руководства и руководства для сотрудников первой строки для заводской сборки</span><span class="sxs-lookup"><span data-stu-id="2f163-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="2f163-111">Разработка профессиональных средств для помощи медицинским специалистам и их обучения.</span><span class="sxs-lookup"><span data-stu-id="2f163-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="2f163-112">Использование трехмерных виртуальных объектов для украшения реального мира или для создания альтернативного.</span><span class="sxs-lookup"><span data-stu-id="2f163-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="2f163-113">Создание служб и игр на основе местоположения с использованием реального мира в качестве фона.</span><span class="sxs-lookup"><span data-stu-id="2f163-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="2f163-114">Руки и контроллеры движения модальностей</span><span class="sxs-lookup"><span data-stu-id="2f163-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2f163-115">[![Непосредственное манипулирование с помощью рук](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="2f163-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="2f163-116">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="2f163-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="2f163-117">Это модальность, использующая возможности руки, с помощью которых пользователи могут касаться голограмм и манипулировать ими напрямую.</span><span class="sxs-lookup"><span data-stu-id="2f163-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="2f163-118">Используя ежедневные возможности и предоставляя верные визуальные аффорданцес, пользователи могут использовать тот же способ управления реальными объектами для взаимодействия с виртуальными.</span><span class="sxs-lookup"><span data-stu-id="2f163-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2f163-119">[![Указание и фиксация с помощью рук](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="2f163-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="2f163-120">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="2f163-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="2f163-121">Такое модальность позволяет пользователям взаимодействовать с голограммами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="2f163-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="2f163-122">Он позволяет пользователям лучше использовать окружающую подстановку.</span><span class="sxs-lookup"><span data-stu-id="2f163-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="2f163-123">Пользователи могут размещать голограммы в любом месте и по-прежнему обращаться к ним с любого расстояния.</span><span class="sxs-lookup"><span data-stu-id="2f163-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="2f163-124">Модели и жесты, используемые для управления и манипулирования плоскими и трехмерными голограммами, высоко синхронизированы с этими моделями с прямой манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="2f163-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2f163-125">[![Контроллеры движений](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="2f163-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="2f163-126">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="2f163-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="2f163-127">Контроллеры движения — это средства, расширяющие физические возможности пользователя путем предоставления точных взаимодействий между большим диапазоном расстояний при использовании одной или обеих стрелок.</span><span class="sxs-lookup"><span data-stu-id="2f163-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="2f163-128">Эти аксессуары оборудования предоставляют ярлыки для многих часто используемых взаимодействий и предоставляют сурефутед, тактиле Отзывы о различных действиях.</span><span class="sxs-lookup"><span data-stu-id="2f163-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="2f163-129">В настоящее время контроллеры движения доступны только для сценариев Windows Mixed Reality (ВМР).</span><span class="sxs-lookup"><span data-stu-id="2f163-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="2f163-130">См. также статью</span><span class="sxs-lookup"><span data-stu-id="2f163-130">See also</span></span>
* [<span data-ttu-id="2f163-131">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="2f163-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2f163-132">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="2f163-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="2f163-133">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="2f163-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2f163-134">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="2f163-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="2f163-135">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="2f163-135">Hands-free</span></span>](hands-free.md)
