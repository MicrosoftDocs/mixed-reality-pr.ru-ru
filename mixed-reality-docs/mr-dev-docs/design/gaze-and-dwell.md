---
title: Взгляните и вдаваясь
description: Общие сведения о модели входных данных (глаз/Head) и вдаваясь
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, вдаваясь, взаимодействие, проектирование, отслеживание глаз, отслеживание головок
ms.openlocfilehash: ee8b6487079a071fe84606949314f2dd315df45f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91693049"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="04cb1-104">Взгляните и вдаваясь</span><span class="sxs-lookup"><span data-stu-id="04cb1-104">Gaze and dwell</span></span>

<span data-ttu-id="04cb1-105">Когда руки заняты инструментами и деталями, жестикулировать может быть сложно или невозможно.</span><span class="sxs-lookup"><span data-stu-id="04cb1-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="04cb1-106">Команды Voice также могут быть ненадежны в определенных контекстах, например в условиях чрезмерно громкой ситуации.</span><span class="sxs-lookup"><span data-stu-id="04cb1-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="04cb1-107">Взгляните и вдаваясь предлагает знакомый и простой механизм для работы с заголовком и практически без участия в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="04cb1-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="04cb1-108">Кроме того, взгляните и вдаваясь — это отличная резервная версия, которая не зависит от помех шума или ограничений тишины в операционной среде.</span><span class="sxs-lookup"><span data-stu-id="04cb1-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="04cb1-109">Мы определяем два варианта _взгляда и вдаваясь_ : [head-взгляд и вдаваясь](gaze-and-dwell-head.md) , [глаза-взгляд и вдаваясь](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="04cb1-109">We distinguish two variants of _gaze and dwell_ : [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="04cb1-110">Сценарии</span><span class="sxs-lookup"><span data-stu-id="04cb1-110">Scenarios</span></span>

<span data-ttu-id="04cb1-111">Взгляните и вдаваясь предназначен в сценариях, где руки человека заняты другими задачами, а речь не 100% надежна или недоступна из-за ограничений среды или социальных сетей.</span><span class="sxs-lookup"><span data-stu-id="04cb1-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span>
<span data-ttu-id="04cb1-112">Хорошим примером является пользователь, носящий HoloLens для получения справочной информации при ремонте двигателя автомобиля.</span><span class="sxs-lookup"><span data-stu-id="04cb1-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="04cb1-113">Их руки заняты инструментами или поддержкой своего тела, когда они нагибаются в моторный отсек.</span><span class="sxs-lookup"><span data-stu-id="04cb1-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="04cb1-114">Гараж — шумный, с постоянным грохотом и гудением инструментов, что создает помехи голосовым командам.</span><span class="sxs-lookup"><span data-stu-id="04cb1-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="04cb1-115">Взгляните и вдаваясь позволяет пользователю, использующему HoloLens, уверенно перемещаться по справочным материалам, не прерывая рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="04cb1-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="04cb1-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="04cb1-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="04cb1-117"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="04cb1-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="04cb1-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="04cb1-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="04cb1-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="04cb1-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="04cb1-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="04cb1-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="04cb1-121">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="04cb1-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="04cb1-122">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="04cb1-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="04cb1-123">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="04cb1-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="04cb1-124">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="04cb1-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="04cb1-125">Определение направления взгляда и остановка</span><span class="sxs-lookup"><span data-stu-id="04cb1-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="04cb1-126">❌ Недоступно</span><span class="sxs-lookup"><span data-stu-id="04cb1-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="04cb1-127">✔️ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="04cb1-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="04cb1-128">❌ Недоступно</span><span class="sxs-lookup"><span data-stu-id="04cb1-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="04cb1-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="04cb1-129">See also</span></span>
* [<span data-ttu-id="04cb1-130">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="04cb1-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="04cb1-131">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="04cb1-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="04cb1-132">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="04cb1-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="04cb1-133">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="04cb1-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="04cb1-134">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="04cb1-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="04cb1-135">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="04cb1-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="04cb1-136">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="04cb1-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="04cb1-137">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="04cb1-137">Voice input</span></span>](voice-input.md)
