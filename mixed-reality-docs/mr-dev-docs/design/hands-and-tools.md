---
title: Руки и контроллеры движений
description: Сведения о моделях взаимодействия с моделями и контроллерами движения, которые могут удалить границу между виртуальными и физическими.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанная реальность, руки, контроллеры движения, взаимодействие, проектирование, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847324"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="e4d15-104">Руки и контроллеры движений</span><span class="sxs-lookup"><span data-stu-id="e4d15-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="e4d15-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="e4d15-105">Scenarios</span></span>

<span data-ttu-id="e4d15-106">Прочитав [Обзор взаимодействия](interaction-fundamentals.md), вы выбираете модель взаимодействия между рукой и контроллером движения.</span><span class="sxs-lookup"><span data-stu-id="e4d15-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="e4d15-107">Это означает, что вы разрабатываете приложение, которое требует от пользователей использовать две руки для взаимодействия с жизнь Holographic.</span><span class="sxs-lookup"><span data-stu-id="e4d15-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="e4d15-108">В приложении будет достигнута цель удаления границы между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="e4d15-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="e4d15-109">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="e4d15-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="e4d15-110">Предоставление информационных работников на двухмерных виртуальных экранах с возможностью пользовательского интерфейса для просмотра содержимого и управления им.</span><span class="sxs-lookup"><span data-stu-id="e4d15-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="e4d15-111">Руководства и руководства для сотрудников первой строки для заводской сборки</span><span class="sxs-lookup"><span data-stu-id="e4d15-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="e4d15-112">Разработка профессиональных средств для помощи медицинским специалистам и их обучения.</span><span class="sxs-lookup"><span data-stu-id="e4d15-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="e4d15-113">Использование трехмерных виртуальных объектов для украшения реального мира или для создания альтернативного.</span><span class="sxs-lookup"><span data-stu-id="e4d15-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="e4d15-114">Создание служб и игр на основе местоположения с использованием реального мира в качестве фона.</span><span class="sxs-lookup"><span data-stu-id="e4d15-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="e4d15-115">Руки и контроллеры движения модальностей</span><span class="sxs-lookup"><span data-stu-id="e4d15-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e4d15-116">[![Непосредственное манипулирование с помощью рук](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="e4d15-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="e4d15-117">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="e4d15-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="e4d15-118">Модальность применения рук, которые пользователи могут использовать для касания голограмм и управления ими.</span><span class="sxs-lookup"><span data-stu-id="e4d15-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="e4d15-119">Используя ежедневные возможности и предоставляя верные визуальные аффорданцес, пользователи могут использовать тот же способ управления реальными объектами для взаимодействия с виртуальными.</span><span class="sxs-lookup"><span data-stu-id="e4d15-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d15-120">[![Указание и фиксация с помощью рук](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="e4d15-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="e4d15-121">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="e4d15-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="e4d15-122">Такое модальность позволяет пользователям взаимодействовать с голограммами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="e4d15-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="e4d15-123">Он позволяет пользователям лучше использовать окружающую подстановку.</span><span class="sxs-lookup"><span data-stu-id="e4d15-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="e4d15-124">Пользователи могут размещать голограммы в любом месте и по-прежнему обращаться к ним с любого расстояния.</span><span class="sxs-lookup"><span data-stu-id="e4d15-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="e4d15-125">Модели и жесты, используемые для управления и манипулирования плоскими и трехмерными голограммами, высоко синхронизированы с этими моделями с прямой манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="e4d15-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d15-126">[![Контроллеры движений](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="e4d15-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="e4d15-127">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="e4d15-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="e4d15-128">Контроллеры движения расширяют физические возможности пользователя с помощью точных взаимодействий на различных расстояниях, используя одну или обе руки.</span><span class="sxs-lookup"><span data-stu-id="e4d15-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="e4d15-129">Эти аксессуары оборудования предоставляют ярлыки для многих часто используемых взаимодействий и предоставляют тактиле отзыв о различных действиях.</span><span class="sxs-lookup"><span data-stu-id="e4d15-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="e4d15-130">В настоящее время контроллеры движения доступны только для сценариев Windows Mixed Reality (ВМР).</span><span class="sxs-lookup"><span data-stu-id="e4d15-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="e4d15-131">См. также статью</span><span class="sxs-lookup"><span data-stu-id="e4d15-131">See also</span></span>
* [<span data-ttu-id="e4d15-132">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="e4d15-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e4d15-133">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="e4d15-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e4d15-134">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="e4d15-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e4d15-135">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="e4d15-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="e4d15-136">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="e4d15-136">Hands-free</span></span>](hands-free.md)
