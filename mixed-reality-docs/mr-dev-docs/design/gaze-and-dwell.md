---
title: Взгляд и остановка
description: Общие сведения о модели ввода с взглядом и вдаваясь для приложений смешанной реальности.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, вдаваясь, взаимодействие, проектирование, отслеживание взгляда, отслеживание головок, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, головной офис виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582138"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="2aa17-104">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="2aa17-104">Gaze and dwell</span></span>

<span data-ttu-id="2aa17-105">Когда руки заняты инструментами и деталями, жестикулировать может быть сложно или невозможно.</span><span class="sxs-lookup"><span data-stu-id="2aa17-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="2aa17-106">Команды Voice также могут быть ненадежны в определенных контекстах, например в условиях чрезмерно громкой ситуации.</span><span class="sxs-lookup"><span data-stu-id="2aa17-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="2aa17-107">Взгляните и вдаваясь предлагает знакомый и простой механизм для работы с заголовком и практически без участия в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2aa17-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="2aa17-108">Кроме того, взгляните и вдаваясь — это отличная резервная версия, которая не зависит от помех шума или ограничений тишины в операционной среде.</span><span class="sxs-lookup"><span data-stu-id="2aa17-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="2aa17-109">Мы определяем два варианта _взгляда и вдаваясь_: [head-взгляд и вдаваясь](gaze-and-dwell-head.md) , [глаза-взгляд и вдаваясь](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="2aa17-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="2aa17-110">Сценарии</span><span class="sxs-lookup"><span data-stu-id="2aa17-110">Scenarios</span></span>

<span data-ttu-id="2aa17-111">Взгляните и вдаваясь предназначен в сценариях, где руки человека заняты другими задачами, а речь не 100% надежна или недоступна из-за ограничений на окружающую среду или социальные сети.</span><span class="sxs-lookup"><span data-stu-id="2aa17-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="2aa17-112">Хорошим примером является пользователь, носящий HoloLens для получения справочной информации при ремонте двигателя автомобиля.</span><span class="sxs-lookup"><span data-stu-id="2aa17-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="2aa17-113">Их руки заняты инструментами или поддержкой своего тела, когда они нагибаются в моторный отсек.</span><span class="sxs-lookup"><span data-stu-id="2aa17-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="2aa17-114">Гараж — шумный, с постоянным грохотом и гудением инструментов, что создает помехи голосовым командам.</span><span class="sxs-lookup"><span data-stu-id="2aa17-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="2aa17-115">Взгляните и вдаваясь позволяет пользователю, использующему HoloLens, уверенно перемещаться по справочным материалам, не прерывая рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="2aa17-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="2aa17-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2aa17-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2aa17-117"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="2aa17-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="2aa17-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2aa17-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2aa17-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2aa17-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2aa17-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="2aa17-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2aa17-121">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="2aa17-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="2aa17-122">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="2aa17-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2aa17-123">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="2aa17-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2aa17-124">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="2aa17-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2aa17-125">Определение направления взгляда и остановка</span><span class="sxs-lookup"><span data-stu-id="2aa17-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="2aa17-126">❌ Недоступно</span><span class="sxs-lookup"><span data-stu-id="2aa17-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="2aa17-127">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="2aa17-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2aa17-128">❌ Недоступно</span><span class="sxs-lookup"><span data-stu-id="2aa17-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="2aa17-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2aa17-129">See also</span></span>

* [<span data-ttu-id="2aa17-130">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="2aa17-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="2aa17-131">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2aa17-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2aa17-132">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="2aa17-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2aa17-133">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="2aa17-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2aa17-134">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="2aa17-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2aa17-135">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="2aa17-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2aa17-136">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2aa17-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2aa17-137">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="2aa17-137">Voice input</span></span>](voice-input.md)