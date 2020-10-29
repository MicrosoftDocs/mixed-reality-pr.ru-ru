---
title: Жест запуска
description: Жест запуска для вызова меню "Пуск".
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, жесты, взаимодействие, проектирование
ms.openlocfilehash: 909472abfec34f75a2f5fa810f87003978cc6a5e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692577"
---
# <a name="start-gesture"></a><span data-ttu-id="46c30-104">Жест запуска</span><span class="sxs-lookup"><span data-stu-id="46c30-104">Start gesture</span></span>

<span data-ttu-id="46c30-105">Жест запуска — это жест руки, используемый для вызова меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="46c30-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="46c30-106">Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллере Xbox или кнопки Windows на контроллере движения головного телефона.</span><span class="sxs-lookup"><span data-stu-id="46c30-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="46c30-107">Важно понимать, какие жесты зарезервированы для системы на каждом устройстве смешанной реальности, чтобы предотвратить конфликты при проектировании взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="46c30-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="46c30-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="46c30-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="46c30-109"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="46c30-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="46c30-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="46c30-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="46c30-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="46c30-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="46c30-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="46c30-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="46c30-113">Цветение</span><span class="sxs-lookup"><span data-stu-id="46c30-113">Bloom</span></span></td>
        <td><span data-ttu-id="46c30-114">✔️</span><span class="sxs-lookup"><span data-stu-id="46c30-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="46c30-115">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="46c30-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="46c30-116">✔️</span><span class="sxs-lookup"><span data-stu-id="46c30-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="46c30-117">Взгляд на глаза и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="46c30-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="46c30-118">✔️</span><span class="sxs-lookup"><span data-stu-id="46c30-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="46c30-119">Цветение</span><span class="sxs-lookup"><span data-stu-id="46c30-119">Bloom</span></span>
<span data-ttu-id="46c30-120">Чтобы открыть меню "Пуск" в HoloLens (1-й общий), мы разработали "раскрытия", который представляет собой символическое действие, копируя цветок цветок.</span><span class="sxs-lookup"><span data-stu-id="46c30-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="46c30-121">Это отличительная необходимость в взаимодействии с сурефутед, простоте выполнения и быстром отзыве.</span><span class="sxs-lookup"><span data-stu-id="46c30-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="46c30-122">Чтобы выполнить жест раскрытия на HoloLens (1-й общий), проведите руку с помощью карманного ПК, а затем откройте руку, добавив пальцы.</span><span class="sxs-lookup"><span data-stu-id="46c30-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="46c30-123">![Раскрытия закрыть](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="46c30-124">**Шаг 1. поладонь с помощью совместного воссоздания**</span><span class="sxs-lookup"><span data-stu-id="46c30-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="46c30-125">![Раскрытия открыть](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="46c30-126">**Шаг 2. Ручная разворота**</span><span class="sxs-lookup"><span data-stu-id="46c30-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="46c30-127">Жест запуска</span><span class="sxs-lookup"><span data-stu-id="46c30-127">Start gesture</span></span>
<span data-ttu-id="46c30-128">В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая обеспечивает более инстинктуалные взаимодействия, не требующие дополнительной обучения.</span><span class="sxs-lookup"><span data-stu-id="46c30-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="46c30-129">Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="46c30-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="46c30-130">![Кнопка "воготовить"](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="46c30-131">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="46c30-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="46c30-132">![Нажатие кнопки "нажимает"](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="46c30-133">**Шаг 2. Нажмите кнопку "нажимаю"**</span><span class="sxs-lookup"><span data-stu-id="46c30-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="46c30-134">Жест запуска с одной рукой</span><span class="sxs-lookup"><span data-stu-id="46c30-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46c30-135">Для работы с однократным жестом запуска:</span><span class="sxs-lookup"><span data-stu-id="46c30-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="46c30-136">Необходимо обновить до обновления за ноябрь 2019 (сборка 18363,1039) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="46c30-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="46c30-137">Ваши глаза должны быть откалиброваны на устройстве, чтобы отслеживание взгляда было правильно работать.</span><span class="sxs-lookup"><span data-stu-id="46c30-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="46c30-138">Если вы не видите точки вокруг значка «начало», то при просмотре на устройстве ваши глаза не будут откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="46c30-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="46c30-139">Вы также можете выполнить жест запуска только с одной рукой.</span><span class="sxs-lookup"><span data-stu-id="46c30-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="46c30-140">Чтобы сделать это, проделайте свое руки и взгляните на **значок "начало** " на своем внутреннем кармане.</span><span class="sxs-lookup"><span data-stu-id="46c30-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="46c30-141">**В то же время следите за значком** , сохранив палец и проиндексировать пальца вместе.</span><span class="sxs-lookup"><span data-stu-id="46c30-141">**While keeping your eye on the icon** , pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="46c30-142">![Кнопка "воготовить"](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="46c30-143">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="46c30-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="46c30-144">![Автосжатие кнопки](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="46c30-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="46c30-145">**Шаг 2. взгляд на кнопку, затем сжатие**</span><span class="sxs-lookup"><span data-stu-id="46c30-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="46c30-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="46c30-146">See also</span></span>

* [<span data-ttu-id="46c30-147">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="46c30-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="46c30-148">Взгляд — взгляд</span><span class="sxs-lookup"><span data-stu-id="46c30-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="46c30-149">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="46c30-149">Voice input</span></span>](voice-input.md)
