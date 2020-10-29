---
title: Пример использования — уроки с кухни Лоу
description: Группа HoloLens хочет поделиться некоторыми рекомендациями, полученными из проекта HoloLens Лоу.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Лоу, HoloLens, кухни, пример внедрения
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91693280"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="ce239-104">Пример использования — уроки с кухни Лоу</span><span class="sxs-lookup"><span data-stu-id="ce239-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="ce239-105">Группа HoloLens хочет поделиться некоторыми рекомендациями, полученными из проекта HoloLens Лоу.</span><span class="sxs-lookup"><span data-stu-id="ce239-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="ce239-106">Ниже приведено видео о Лоу HoloLens, которое было показано на выступлении 2016 Сатья Ignite.</span><span class="sxs-lookup"><span data-stu-id="ce239-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="ce239-107">Рекомендации по HoloLens для лоу</span><span class="sxs-lookup"><span data-stu-id="ce239-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="ce239-108">В двух видеороликах рассматриваются лучшие методики, полученные из пилотной программы Лоу HoloLens, которая была в двух магазинах лоу с апреля 2016.</span><span class="sxs-lookup"><span data-stu-id="ce239-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="ce239-109">Основные темы:</span><span class="sxs-lookup"><span data-stu-id="ce239-109">The key topics are:</span></span>
* <span data-ttu-id="ce239-110">Максимальная производительность мобильного устройства</span><span class="sxs-lookup"><span data-stu-id="ce239-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="ce239-111">Создание методов UX с помощью полного holographic-кадра (2-й разговор)</span><span class="sxs-lookup"><span data-stu-id="ce239-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="ce239-112">Выравнивание точности (второе обсуждение)</span><span class="sxs-lookup"><span data-stu-id="ce239-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="ce239-113">Общие holographic-опытные работы (2-й разговор)</span><span class="sxs-lookup"><span data-stu-id="ce239-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="ce239-114">Взаимодействие с клиентами (2-й разговор)</span><span class="sxs-lookup"><span data-stu-id="ce239-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="ce239-115">Видео 1</span><span class="sxs-lookup"><span data-stu-id="ce239-115">Video 1</span></span>

<span data-ttu-id="ce239-116">**Максимальная производительность мобильного устройства** HoloLens — это неподключенное устройство, для которого выполняется вся обработка на устройстве.</span><span class="sxs-lookup"><span data-stu-id="ce239-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="ce239-117">Для этого требуется Мобильная платформа, и для создания мобильных приложений необходимо иметь такое же разрешение.</span><span class="sxs-lookup"><span data-stu-id="ce239-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="ce239-118">Корпорация Майкрософт рекомендует, чтобы приложение HoloLens поддерживало 60FPS, чтобы обеспечить заманчивые взаимодействие с пользователями.</span><span class="sxs-lookup"><span data-stu-id="ce239-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="ce239-119">Недостаток кадров в кадре может привести к нестабильной голограмме.</span><span class="sxs-lookup"><span data-stu-id="ce239-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="ce239-120">Некоторые из наиболее важных моментов, которые следует рассмотреть при разработке на HoloLens, — это оптимизация или децимации ресурсов, использующая пользовательские шейдеры (доступные бесплатно в [наборе средств HoloLens](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="ce239-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="ce239-121">Еще одним важным моментом является измерение частоты кадров от самого начала проекта.</span><span class="sxs-lookup"><span data-stu-id="ce239-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="ce239-122">В зависимости от проекта порядок отображения ресурсов также может быть большим участником</span><span class="sxs-lookup"><span data-stu-id="ce239-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="ce239-123">Видео 2</span><span class="sxs-lookup"><span data-stu-id="ce239-123">Video 2</span></span>

<span data-ttu-id="ce239-124">**Создание методов UX с помощью полного пакета holographic** Важно понимать размещение голограмм в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="ce239-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="ce239-125">С лоу, мы поговорим о различных методах UX, которые помогают пользователям столкнуться с голограммами, и вы по-прежнему видите общую среду голограмм.</span><span class="sxs-lookup"><span data-stu-id="ce239-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="ce239-126">**Выравнивание точности** Для сценария Лоу он был очень по важному, чтобы иметь возможность точного выравнивания голограмм с физическим кухни.</span><span class="sxs-lookup"><span data-stu-id="ce239-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="ce239-127">Мы обсудим методы, позволяющие гарантировать, что пользователи будут испытывать изменения в физической среде.</span><span class="sxs-lookup"><span data-stu-id="ce239-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="ce239-128">**Общие holographic** Пары — это основной способ использования Лоу.</span><span class="sxs-lookup"><span data-stu-id="ce239-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="ce239-129">Один пользователь может изменить каунтертоп, и другой пользователь увидит изменения.</span><span class="sxs-lookup"><span data-stu-id="ce239-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="ce239-130">Мы назвали этот "общий опыт".</span><span class="sxs-lookup"><span data-stu-id="ce239-130">We called this "shared experiences".</span></span>

<span data-ttu-id="ce239-131">**Взаимодействие с клиентами** Конструкторы Лоу не используют HoloLens, но они должны видеть, что видят клиенты.</span><span class="sxs-lookup"><span data-stu-id="ce239-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="ce239-132">Мы покажем, как записать, что клиент видит в приложении UWP.</span><span class="sxs-lookup"><span data-stu-id="ce239-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
