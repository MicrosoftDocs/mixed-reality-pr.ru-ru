---
title: Направление головы и остановка
description: Общие сведения о модели направления головы и остановки
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, вдаваясь, взаимодействие, проектирование, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, UX, рекомендации, представление списка
ms.openlocfilehash: 060d78ec629905ac9f2134851998ec131d85f0cd
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847375"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="771fe-104">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="771fe-104">Head-gaze and dwell</span></span>

<span data-ttu-id="771fe-105">Когда руки заняты инструментами и деталями, жестикулировать может быть сложно или невозможно.</span><span class="sxs-lookup"><span data-stu-id="771fe-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="771fe-106">При определенных обстоятельствах, например в чрезмерно шумных условиях, на голосовые команды, такие как жесты, нельзя положиться.</span><span class="sxs-lookup"><span data-stu-id="771fe-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="771fe-107">Кроме того, использование голоса для управления компьютерами не всегда доступно, но оно, безусловно, становится более популярным!</span><span class="sxs-lookup"><span data-stu-id="771fe-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="771fe-108">"Направление головы и остановка" предлагает наиболее знакомый и простой в освоении механизм для работы в режиме "внимание" и "громкая связь" на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="771fe-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="771fe-109">Кроме того, опция "Направление головы и остановка" на 100 % надежна, независимо от шумовых помех и проблем с тишиной в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="771fe-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="771fe-110">Сценарии</span><span class="sxs-lookup"><span data-stu-id="771fe-110">Scenarios</span></span>

<span data-ttu-id="771fe-111">Head-взгляд и вдаваясь отлично подходят в ситуациях, когда руки человека заняты другими задачами.</span><span class="sxs-lookup"><span data-stu-id="771fe-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="771fe-112">Эта функция также полезна, если речь не 100% надежности или доступности в связи с ограничениями на окружающую среду или социальные сети.</span><span class="sxs-lookup"><span data-stu-id="771fe-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="771fe-113">Хорошим примером является пользователь, носящий HoloLens для получения справочной информации при ремонте двигателя автомобиля.</span><span class="sxs-lookup"><span data-stu-id="771fe-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="771fe-114">Их руки заняты инструментами или поддержкой своего тела, когда они нагибаются в моторный отсек.</span><span class="sxs-lookup"><span data-stu-id="771fe-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="771fe-115">Гараж — шумный, с постоянным грохотом и гудением инструментов, что создает помехи голосовым командам.</span><span class="sxs-lookup"><span data-stu-id="771fe-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="771fe-116">Head-взгляд и вдаваясь позволяют пользователю, использующему HoloLens, уверенно перемещаться по справочным материалам, не прерывая рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="771fe-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="771fe-117">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="771fe-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="771fe-118"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="771fe-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="771fe-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="771fe-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="771fe-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="771fe-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="771fe-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="771fe-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="771fe-122">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="771fe-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="771fe-123">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="771fe-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="771fe-124">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="771fe-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="771fe-125">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="771fe-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="771fe-126">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="771fe-126">Design principles</span></span>

<span data-ttu-id="771fe-127">**Избегайте "взгляда, как оружие"**</span><span class="sxs-lookup"><span data-stu-id="771fe-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="771fe-128">"Направление головы и остановка" требует, чтобы визуальный отзыв был понятным, но слишком перенасыщенный отзыв может вызвать беспокойство.</span><span class="sxs-lookup"><span data-stu-id="771fe-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="771fe-129">Обратная связь должна помочь пользователю понять, что они нацелены на, но не выбирает их в соответствии с намерением.</span><span class="sxs-lookup"><span data-stu-id="771fe-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="771fe-130">При чтении текста, значков и меток необходимо предоставить пользователям время для получения данных перед выбором.</span><span class="sxs-lookup"><span data-stu-id="771fe-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="771fe-131">**Поиск безопасной скорости**</span><span class="sxs-lookup"><span data-stu-id="771fe-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="771fe-132">Взаимодействия с остановкой могут иметь разные таймеры, основанные на влиянии навигации. Более часто используемые функции обычно выигрывают от более короткого времени заполнения, в то время как более последовательные функции могут выиграть от более длительного времени заполнения.</span><span class="sxs-lookup"><span data-stu-id="771fe-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="771fe-133">При использовании способа заполнения для отображения этих таймеров анимационные кривые цвета заполнения могут положительно влиять на ощущение более короткого времени заполнения.</span><span class="sxs-lookup"><span data-stu-id="771fe-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="771fe-134">Необходимо принять во внимание возможность принятия пользователем решения по переопределению скорости заполнения в пользу быстрой, средней или медленной.</span><span class="sxs-lookup"><span data-stu-id="771fe-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="771fe-135">**Скажите "нет-нет" эффекту йо-йо**</span><span class="sxs-lookup"><span data-stu-id="771fe-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="771fe-136">Воздействие Yo-Yo является неудобной схемой перемещения в головном офисе, которая происходит, когда элементы управления размещением содержимого и Head-взгляд/вдаваясь задают пользователям несколько раз выполнять поиск и уменьшение.</span><span class="sxs-lookup"><span data-stu-id="771fe-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="771fe-137">Например, в списке на панели навигации с кнопкой Head-взгляд и вдаваясь в нижней части вызывается цикл-Поиск в вдаваясь, поиск в результатах, поиск в вдаваясь и т. д.</span><span class="sxs-lookup"><span data-stu-id="771fe-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="771fe-138">Итоговый шаблон некомфортен, поэтому мы рекомендуем размещать элементы управления для навигации в централизованном расположении, требующем меньшего резервного копирования.</span><span class="sxs-lookup"><span data-stu-id="771fe-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="771fe-139">Размещение кнопок вдаваясь в зависимости от их последствий для удобства играет важную роль.</span><span class="sxs-lookup"><span data-stu-id="771fe-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="771fe-140">s</span><span class="sxs-lookup"><span data-stu-id="771fe-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="771fe-141">Руководства и рекомендации по взаимодействию с пользователем</span><span class="sxs-lookup"><span data-stu-id="771fe-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="771fe-142">Размеры цели</span><span class="sxs-lookup"><span data-stu-id="771fe-142">Target sizes</span></span>

<span data-ttu-id="771fe-143">Для простоты в доступе целевые объекты Head-взгляд и вдаваясь должны быть достаточно большими, чтобы их можно было легко найти, а на целевом уровне — в течение определенного времени.</span><span class="sxs-lookup"><span data-stu-id="771fe-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="771fe-144">Для достижения наиболее удобного интерфейса рекомендуется использовать минимальный целевой размер в 2 градусах.</span><span class="sxs-lookup"><span data-stu-id="771fe-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="771fe-145">Визуальная обратная связь</span><span class="sxs-lookup"><span data-stu-id="771fe-145">Visual feedback</span></span>

<span data-ttu-id="771fe-146">При использовании радиальной заливки для представления таймера остановки начинайте с центра кнопки.</span><span class="sxs-lookup"><span data-stu-id="771fe-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="771fe-147">Последовательный ответ меньше сбивает с толку, чем все разные направления на разных кнопках.</span><span class="sxs-lookup"><span data-stu-id="771fe-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="771fe-148">Это правило может быть разорвано для направленного взаимодействия (например, через навигацию вверх/вниз, влево или вправо и т. д.).</span><span class="sxs-lookup"><span data-stu-id="771fe-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="771fe-149">Например, "Руководство по Microsoft Dynamics 365" делает исключение для ДАЛЕЕ/НАЗАД при заливке слева направо.</span><span class="sxs-lookup"><span data-stu-id="771fe-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="771fe-150">Рассмотрите возможность инвертирования радиальной заливки извне для таких сценариев, как переключение кнопки.</span><span class="sxs-lookup"><span data-stu-id="771fe-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="771fe-151">Ощущение инверсии после нажатия кнопки — хороший визуальный шаблон, который следует поддерживать.</span><span class="sxs-lookup"><span data-stu-id="771fe-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="771fe-152">Поэтапное представление информации</span><span class="sxs-lookup"><span data-stu-id="771fe-152">Progressive disclosure</span></span>

<span data-ttu-id="771fe-153">Поэтапное представление информации означает только представление того количества деталей, которое уместно на каждом этапе взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="771fe-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="771fe-154">Для вдаваясь это означает, что целевой объект вдаваясь раскрывается по выделению (например, в элементе управления "список").</span><span class="sxs-lookup"><span data-stu-id="771fe-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="771fe-155">Целевые объекты слишком большого размера</span><span class="sxs-lookup"><span data-stu-id="771fe-155">Oversized targets</span></span>

<span data-ttu-id="771fe-156">Область остановки может быть больше, чем неактивный значок, чтобы проще было использовать, например, кнопку "Назад" в Руководстве по Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="771fe-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="771fe-157">Предотвращение мерцания с помощью задержки ответа</span><span class="sxs-lookup"><span data-stu-id="771fe-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="771fe-158">Используйте короткую задержку перед началом визуального ответа, чтобы избежать мерцания, когда кто-то не заметит целевой объект остановки.</span><span class="sxs-lookup"><span data-stu-id="771fe-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="771fe-159">Для кнопок, часто взаимодействующих с, следует оставаться короткой задержкой, чтобы приложение оставалось активным.</span><span class="sxs-lookup"><span data-stu-id="771fe-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="771fe-160">Для кнопок, которые взаимодействуют с нечасто, может быть целесообразно более длительная задержка, чтобы избежать недостаточного твитчи.</span><span class="sxs-lookup"><span data-stu-id="771fe-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="771fe-161">Шаблоны пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="771fe-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="771fe-162">Высокая частота кнопок</span><span class="sxs-lookup"><span data-stu-id="771fe-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="771fe-163">Кнопки с высокой частотой — это кнопки, которые обычно используются во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="771fe-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="771fe-164">Наглядным примером являются кнопки "Далее" и "Назад" в Руководстве по Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="771fe-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="771fe-165">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="771fe-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="771fe-166">Кнопки с высокой частотой должны быть большими, проще в попадании с помощью головного взгляда</span><span class="sxs-lookup"><span data-stu-id="771fe-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="771fe-167">Оставайтесь рядом с высотой глаз, чтобы избежать эффекта эргономичного ограничения.</span><span class="sxs-lookup"><span data-stu-id="771fe-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="771fe-168">*Изображение: кнопка "Далее" руководства по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="771fe-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Кнопка "Далее" руководства по Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="771fe-170">Редко использующиеся кнопки</span><span class="sxs-lookup"><span data-stu-id="771fe-170">Low frequency buttons</span></span>

<span data-ttu-id="771fe-171">Кнопки с низкой частотой — это кнопки, которые не взаимодействуют со как регулярно в рамках всего приложения.</span><span class="sxs-lookup"><span data-stu-id="771fe-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="771fe-172">Наглядным примером может быть кнопка для доступа к меню параметров или кнопка для очистки всей работы.</span><span class="sxs-lookup"><span data-stu-id="771fe-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="771fe-173">Попытайтесь, чтобы на эти кнопки не влияла частая смена направления головы, чтобы избежать случайной активации.</span><span class="sxs-lookup"><span data-stu-id="771fe-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="771fe-174">Подтверждения</span><span class="sxs-lookup"><span data-stu-id="771fe-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="771fe-175">Если действие оказывает значительное влияние, например деньги на оплату, удаление работы или запуск длительного процесса, полезно подтвердить, что пользователь выбрал кнопку.</span><span class="sxs-lookup"><span data-stu-id="771fe-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="771fe-176">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="771fe-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="771fe-177">Показать выбранные выделения на главной кнопке.</span><span class="sxs-lookup"><span data-stu-id="771fe-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="771fe-178">Обнаружить целевой объект остановки одновременно с выбранным выделением.</span><span class="sxs-lookup"><span data-stu-id="771fe-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="771fe-179">Для дополнительной кнопки показать целевой объект остановки в направлении головы.</span><span class="sxs-lookup"><span data-stu-id="771fe-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="771fe-180">*Изображение: диалоговое окно подтверждения руководств по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="771fe-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Диалоговое окно для подтверждения руководств по Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="771fe-182">Выключатели</span><span class="sxs-lookup"><span data-stu-id="771fe-182">Toggle buttons</span></span>

<span data-ttu-id="771fe-183">Выключатели требуют некоторой детализированной логики для правильной работы.</span><span class="sxs-lookup"><span data-stu-id="771fe-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="771fe-184">Когда пользователь двеллс выключателем и активирует его, ему нужно закрыть кнопку и вернуться к перезапуску логики вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="771fe-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="771fe-185">Важно, чтобы переключатели были очищены в активном и неактивном состоянии.</span><span class="sxs-lookup"><span data-stu-id="771fe-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="771fe-186">Представления списка</span><span class="sxs-lookup"><span data-stu-id="771fe-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="771fe-187">Представления списка представляют собой определенную задачу для вдаваясь и ввода в голову.</span><span class="sxs-lookup"><span data-stu-id="771fe-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="771fe-188">Пользователи могут просматривать содержимое, не тратя на то, чтобы типтое вокруг целевых объектов вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="771fe-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="771fe-189">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="771fe-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="771fe-190">Выделяйте весь строкой, когда Head-газед, но не начинайте вдаваясь, если только Headed-взгляд находится на определенном целевом объекте вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="771fe-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="771fe-191">Отображать целевой объект вдаваясь только в том случае, если строка выделена для вырезания визуального шума.</span><span class="sxs-lookup"><span data-stu-id="771fe-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="771fe-192">Будьте понятны и соответствуют положению целевых объектов вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="771fe-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="771fe-193">Не показывать все целевые объекты вдаваясь одновременно, чтобы избежать повторения пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="771fe-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="771fe-194">Повторно используйте ту же схему, как это возможно, чтобы установить знание UX.</span><span class="sxs-lookup"><span data-stu-id="771fe-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="771fe-195">*Изображение: список руководств по Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="771fe-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Список руководств по Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="771fe-197">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="771fe-197">See also</span></span>

* [<span data-ttu-id="771fe-198">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="771fe-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="771fe-199">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="771fe-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="771fe-200">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="771fe-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="771fe-201">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="771fe-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="771fe-202">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="771fe-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="771fe-203">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="771fe-203">Voice input</span></span>](voice-input.md)
