---
title: Жест запуска
description: Жест запуска для вызова меню "Пуск".
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, жесты, взаимодействие, проектирование, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, раскрытия
ms.openlocfilehash: 9df8d54dcf63c13dedabdbf55300b3516a2c9bf1
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848160"
---
# <a name="start-gesture"></a><span data-ttu-id="40a77-104">Жест запуска</span><span class="sxs-lookup"><span data-stu-id="40a77-104">Start gesture</span></span>

<span data-ttu-id="40a77-105">Жест запуска — это жест руки, используемый для вызова меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="40a77-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="40a77-106">Это эквивалентно нажатию клавиши Windows на клавиатуре, кнопки Xbox на контроллерах Xbox или кнопки Windows на современных контроллерах движения головного телефона.</span><span class="sxs-lookup"><span data-stu-id="40a77-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="40a77-107">Обратите особое внимание на зарезервированные системные жесты на каждом устройстве смешанной реальности, чтобы избежать конфликтов при проектировании взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="40a77-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="40a77-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="40a77-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="40a77-109"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="40a77-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="40a77-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="40a77-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="40a77-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="40a77-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="40a77-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="40a77-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="40a77-113">Цветение</span><span class="sxs-lookup"><span data-stu-id="40a77-113">Bloom</span></span></td>
        <td><span data-ttu-id="40a77-114">✔️</span><span class="sxs-lookup"><span data-stu-id="40a77-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="40a77-115">Кнопка "назначить"</span><span class="sxs-lookup"><span data-stu-id="40a77-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="40a77-116">✔️</span><span class="sxs-lookup"><span data-stu-id="40a77-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="40a77-117">Взгляд на глаза и ручное сжатие</span><span class="sxs-lookup"><span data-stu-id="40a77-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="40a77-118">✔️</span><span class="sxs-lookup"><span data-stu-id="40a77-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="40a77-119">Цветение</span><span class="sxs-lookup"><span data-stu-id="40a77-119">Bloom</span></span>

<span data-ttu-id="40a77-120">Мы разработали «раскрытия», чтобы открыть меню «Пуск» в HoloLens (1-й), которое является символом, копируя цветок цветок.</span><span class="sxs-lookup"><span data-stu-id="40a77-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="40a77-121">Он различен для обязательного использования, упрощения и быстрого отзыва.</span><span class="sxs-lookup"><span data-stu-id="40a77-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="40a77-122">Чтобы использовать жест, держите руку на своем ПК и проведите его под рукой, а затем откройте руку, добавив пальцы.</span><span class="sxs-lookup"><span data-stu-id="40a77-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="40a77-123">![Раскрытия закрыть](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="40a77-124">**Шаг 1. поладонь с помощью совместного воссоздания**</span><span class="sxs-lookup"><span data-stu-id="40a77-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40a77-125">![Раскрытия открыть](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="40a77-126">**Шаг 2. Ручная разворота**</span><span class="sxs-lookup"><span data-stu-id="40a77-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="40a77-127">Жест запуска</span><span class="sxs-lookup"><span data-stu-id="40a77-127">Start gesture</span></span>

<span data-ttu-id="40a77-128">В HoloLens 2 мы заменили жест раскрытия на виртуальную кнопку, которая более инстинктуал для пользователей.</span><span class="sxs-lookup"><span data-stu-id="40a77-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="40a77-129">Показывая пользователям кнопку на ручную, они могут быть понятными и нажимать их с другой стороны.</span><span class="sxs-lookup"><span data-stu-id="40a77-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="40a77-130">![Кнопка "воготовить"](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="40a77-131">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="40a77-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40a77-132">![Нажатие кнопки "нажимает"](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="40a77-133">**Шаг 2. Нажмите кнопку "нажимаю"**</span><span class="sxs-lookup"><span data-stu-id="40a77-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="40a77-134">Жест запуска с одной рукой</span><span class="sxs-lookup"><span data-stu-id="40a77-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40a77-135">Для работы с однократным жестом запуска:</span><span class="sxs-lookup"><span data-stu-id="40a77-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="40a77-136">Необходимо обновить до обновления за ноябрь 2019 (сборка 18363,1039) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="40a77-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="40a77-137">Ваши глаза должны быть откалиброваны на устройстве, чтобы отслеживание взгляда было правильно работать.</span><span class="sxs-lookup"><span data-stu-id="40a77-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="40a77-138">Если вы не видите точки вокруг значка «начало», то при просмотре на устройстве ваши глаза не будут откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="40a77-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="40a77-139">Можно также использовать жест запуска только с одной рукой.</span><span class="sxs-lookup"><span data-stu-id="40a77-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="40a77-140">Проанализируйте свою руку с помощью карманного компьютера и взгляните на **значок запуска** на своем внутреннем компьютере.</span><span class="sxs-lookup"><span data-stu-id="40a77-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="40a77-141">**В то же время следите за значком**, сохранив палец и проиндексировать пальца вместе.</span><span class="sxs-lookup"><span data-stu-id="40a77-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="40a77-142">![Кнопка "воготовить"](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="40a77-143">**Шаг 1. Palm, чтобы отобразить кнопку "ручная"**</span><span class="sxs-lookup"><span data-stu-id="40a77-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40a77-144">![Автосжатие кнопки](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="40a77-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="40a77-145">**Шаг 2. взгляд на кнопку, затем сжатие**</span><span class="sxs-lookup"><span data-stu-id="40a77-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="40a77-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="40a77-146">See also</span></span>

* [<span data-ttu-id="40a77-147">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="40a77-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="40a77-148">Взгляд — взгляд</span><span class="sxs-lookup"><span data-stu-id="40a77-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="40a77-149">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="40a77-149">Voice input</span></span>](voice-input.md)
