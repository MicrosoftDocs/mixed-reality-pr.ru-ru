---
title: Что такое голограмма?
description: HoloLens позволяет просматривать трехмерные голограммы и работать с ними, объекты со светлой и звуковой частью, отображаемые по всему миру.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, голограммы, проектирование, взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, что является дополненным
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583344"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="373e6-104">Что такое голограмма?</span><span class="sxs-lookup"><span data-stu-id="373e6-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="373e6-105">HoloLens позволяет создавать **голограммы**, представляющие собой объекты света и звука, которые отображаются в мире, как и реальные объекты.</span><span class="sxs-lookup"><span data-stu-id="373e6-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="373e6-106">Голограммы отвечают на [взгляд](../design/gaze-and-commit.md), [жесты](../design/gaze-and-commit.md#composite-gestures)и [команды Voice](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="373e6-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="373e6-107">Они даже могут взаимодействовать с [реальными областями](../design/spatial-mapping.md) по всему миру.</span><span class="sxs-lookup"><span data-stu-id="373e6-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="373e6-108">Благодаря голограммам вы можете создавать цифровые объекты, которые являются частью окружающего мира.</span><span class="sxs-lookup"><span data-stu-id="373e6-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="373e6-109">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="373e6-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="373e6-110"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="373e6-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="373e6-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="373e6-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="373e6-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="373e6-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="373e6-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="373e6-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="373e6-114">Holograms (Голограммы)</span><span class="sxs-lookup"><span data-stu-id="373e6-114">Holograms</span></span></td>
        <td><span data-ttu-id="373e6-115">✔️</span><span class="sxs-lookup"><span data-stu-id="373e6-115">✔️</span></span></td>
        <td><span data-ttu-id="373e6-116">✔️</span><span class="sxs-lookup"><span data-stu-id="373e6-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="373e6-117">Голограмма состоит из светлого и звукового</span><span class="sxs-lookup"><span data-stu-id="373e6-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="373e6-118">Голограммы [, отображаемые HoloLens,](../develop/platform-capabilities-and-apis/rendering.md) отображаются в списке holographic непосредственно перед глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="373e6-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="373e6-119">Голограммы добавляют свет в мир, что означает, что вы видите как свет с экрана, так и свет из окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="373e6-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="373e6-120">HoloLens не удаляет освещение от глаз, поэтому голограммы нельзя визуализировать с черным цветом.</span><span class="sxs-lookup"><span data-stu-id="373e6-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="373e6-121">Вместо этого черная содержимое отображается как прозрачное.</span><span class="sxs-lookup"><span data-stu-id="373e6-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="373e6-122">Голограммы могут иметь много различных представлений и поведений.</span><span class="sxs-lookup"><span data-stu-id="373e6-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="373e6-123">Некоторые из них реалистичны, а другие — мультипликационные и ethereal.</span><span class="sxs-lookup"><span data-stu-id="373e6-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="373e6-124">Голограммы можно использовать для выделения компонентов в окружающей обстановке или использования их в качестве элементов пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="373e6-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![Руки, работающие с голограммой](images/hologram-hands-940px.jpg)

<span data-ttu-id="373e6-126">Голограммы также могут делать [звуки](../design/spatial-sound.md), которые будут поступать из определенного места в окружающей обстановке.</span><span class="sxs-lookup"><span data-stu-id="373e6-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="373e6-127">В HoloLens звук поступает из двух динамиков, расположенных непосредственно над ушки, и не охватывает их.</span><span class="sxs-lookup"><span data-stu-id="373e6-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="373e6-128">Как и на экранах, динамики являются аддитивными, добавляя новые звуки, не блокируя звуки в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="373e6-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="373e6-129">Голограмму можно поместить в мир или тег вместе с вами.</span><span class="sxs-lookup"><span data-stu-id="373e6-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="373e6-130">Если у вас есть определенное расположение голограммы, его можно [разместить](../design/coordinate-systems.md) на этом этапе мира.</span><span class="sxs-lookup"><span data-stu-id="373e6-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="373e6-131">По мере прочего, голограмма будет выглядеть стабильно в зависимости от окружающего мира.</span><span class="sxs-lookup"><span data-stu-id="373e6-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="373e6-132">Если для закрепления объекта используется [пространственное](../design/coordinate-systems.md#spatial-anchors) прикрепление, система может даже запоминать, где он остался, когда вы поступите позже.</span><span class="sxs-lookup"><span data-stu-id="373e6-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Два мужчин, использующих макет Microsoft Dynamics 365 в сфере розничной торговли](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="373e6-134">Некоторые голограммы следуют пользователю, но сами по себе разводятся на основе пользователя независимо от того, где они проходят.</span><span class="sxs-lookup"><span data-stu-id="373e6-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="373e6-135">Вы можете даже добавить голограмму в течение определенного промежутка, а затем поместить ее на стене после перехода в другую комнату.</span><span class="sxs-lookup"><span data-stu-id="373e6-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="373e6-136">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="373e6-136">**Best practices**</span></span>
* <span data-ttu-id="373e6-137">Некоторые сценарии могут потребовать, чтобы голограммы были легко обнаруживаемыми или видимыми на протяжении всего процесса.</span><span class="sxs-lookup"><span data-stu-id="373e6-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="373e6-138">Существует два высокоуровневого подхода к такому размещению.</span><span class="sxs-lookup"><span data-stu-id="373e6-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="373e6-139">Назовем их **«Отображение-блокировка»** и **«текст заблокирован»**.</span><span class="sxs-lookup"><span data-stu-id="373e6-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="373e6-140">При отображении содержимое, заблокированное на экране, располагается на экране на устройстве.</span><span class="sxs-lookup"><span data-stu-id="373e6-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="373e6-141">Этот тип содержимого сложнее по ряду причин, включая неестественное чувство «клингинесс», которое делает множество пользователей беспроблемными и хотят «встряхните».</span><span class="sxs-lookup"><span data-stu-id="373e6-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="373e6-142">Как правило, многие разработчики обнаружили, что лучше избегать содержимого блокировки с отображением.</span><span class="sxs-lookup"><span data-stu-id="373e6-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="373e6-143">Подход с блокировкой текста гораздо более форгивабле.</span><span class="sxs-lookup"><span data-stu-id="373e6-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="373e6-144">Блокировка текста — это то, что вы выдаете голограмму на тело пользователя или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="373e6-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="373e6-145">Многие опыт применяют поведение блокировки текста, при котором под голограммой «пользователи» следует поворачивать, что позволяет пользователю вращать текст и перемещаться по месту, не теряя голограммы.</span><span class="sxs-lookup"><span data-stu-id="373e6-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="373e6-146">Включение задержки позволяет более естественным движением голограмм.</span><span class="sxs-lookup"><span data-stu-id="373e6-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="373e6-147">Например, в некоторых основных пользовательских интерфейсах ОС Windows holographic используется разновидность блокировки тела, которая после взгляда пользователя получает доброй, эластичную задержку, когда пользователь превращает свою головку.</span><span class="sxs-lookup"><span data-stu-id="373e6-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="373e6-148">Разместите голограмму на удобном для просмотра расстоянии, обычно около 1-2 метров от головного.</span><span class="sxs-lookup"><span data-stu-id="373e6-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="373e6-149">Укажите величину отклонения для элементов, которые должны постоянно находиться в holographicом кадре, или можно анимировать содержимое на одной стороне экрана, когда пользователь изменяет точку зрения.</span><span class="sxs-lookup"><span data-stu-id="373e6-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="373e6-150">**Размещайте голограммы в оптимальной зоне — от 1,25 м до 5 м**</span><span class="sxs-lookup"><span data-stu-id="373e6-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="373e6-151">Два счетчика являются наиболее оптимальными, и работа с ними приведет к снижению качества, чем на 1 единицу измерения.</span><span class="sxs-lookup"><span data-stu-id="373e6-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="373e6-152">С расстояниями вблизи от 1 метра голограммы, которые регулярно переходят по глубине, скорее всего, будут проблематичными, чем стационарные голограммы.</span><span class="sxs-lookup"><span data-stu-id="373e6-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="373e6-153">Рекомендуется аккуратно обрезать или выпустить содержимое, когда оно получится слишком близко, чтобы пользователь не был в процессе работы.</span><span class="sxs-lookup"><span data-stu-id="373e6-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![Оптимальное расстояние для размещения голограмм от пользователя.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="373e6-155">Голограмма взаимодействует с вами и вашим миром</span><span class="sxs-lookup"><span data-stu-id="373e6-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="373e6-156">Голограммы не только освещены и не имеют звука; Они также являются активной частью вашего мира.</span><span class="sxs-lookup"><span data-stu-id="373e6-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="373e6-157">Взгляните на голограмму и жест с рукой, а голограмма может начать следовать вам.</span><span class="sxs-lookup"><span data-stu-id="373e6-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="373e6-158">Дайте голосовую команду на голограмму, и она может ответить.</span><span class="sxs-lookup"><span data-stu-id="373e6-158">Give a voice command to a hologram, and it can reply.</span></span>

![Группа сотрудников служебной программы для государственных организаций, использующих Microsoft HoloLens 2 для совместной работы в проекте разработки на основе фермы "Ветер"](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="373e6-160">Голограммы позволяют использовать персональные взаимодействия, которые не могут быть в других местах.</span><span class="sxs-lookup"><span data-stu-id="373e6-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="373e6-161">Так как HoloLens знает, где он находится в мире, то с точки зрения прохождения в комнате с помощью этого символа можно увидеть, что он находится в разных местах.</span><span class="sxs-lookup"><span data-stu-id="373e6-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="373e6-162">Голограмма может также взаимодействовать с окружающей обстановкой.</span><span class="sxs-lookup"><span data-stu-id="373e6-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="373e6-163">Например, можно разместить holographic-движущийся шарик над таблицей.</span><span class="sxs-lookup"><span data-stu-id="373e6-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="373e6-164">Затем, выполнив [касание](../design/gaze-and-commit.md#composite-gestures), посмотрите на шарик и сделайте звук, когда он достигнет таблицы.</span><span class="sxs-lookup"><span data-stu-id="373e6-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="373e6-165">Голограммы также могут перекрыто в реальных объектах.</span><span class="sxs-lookup"><span data-stu-id="373e6-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="373e6-166">Например, holographic-символ может пройти через дверцу и позади стены.</span><span class="sxs-lookup"><span data-stu-id="373e6-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="373e6-167">**Советы по интеграции голограмм и реального мира**</span><span class="sxs-lookup"><span data-stu-id="373e6-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="373e6-168">Выровняйте до гравитатионал правил упрощает связь с голограммами и более белиевабле.</span><span class="sxs-lookup"><span data-stu-id="373e6-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="373e6-169">Например: Разместите holographic-собака на земле & Васе в таблице, а не заключайте в них место.</span><span class="sxs-lookup"><span data-stu-id="373e6-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="373e6-170">Многие дизайнеры обнаружили, что они могут интегрировать больше голограмм белиевабле, создав «негативную тень» на поверхности, на которой находится голограмма.</span><span class="sxs-lookup"><span data-stu-id="373e6-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="373e6-171">Для этого создается мягкое свечение вокруг голограммы, а затем вычитается "тень" из свечения.</span><span class="sxs-lookup"><span data-stu-id="373e6-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="373e6-172">Мягкое свечение интегрируется с освещением от реального мира, в котором используется тень, чтобы наземный голограмму в среде.</span><span class="sxs-lookup"><span data-stu-id="373e6-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="373e6-173">Голограмма — это любой</span><span class="sxs-lookup"><span data-stu-id="373e6-173">A hologram is whatever</span></span> <br><span data-ttu-id="373e6-174">Вы можете заниматься</span><span class="sxs-lookup"><span data-stu-id="373e6-174">you can dream up</span></span><br>
        <span data-ttu-id="373e6-175">Как holographic-разработчик, вы можете разбить свои творческие способности на плоские экраны и в мир по всему миру.</span><span class="sxs-lookup"><span data-stu-id="373e6-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="373e6-176">Что будет *построено* ?</span><span class="sxs-lookup"><span data-stu-id="373e6-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="373e6-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="373e6-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="373e6-178">![Holographic воображаемый мир в гостиной](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="373e6-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="373e6-179">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="373e6-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="373e6-180">Если вы следуете изложенному нами [плану обучения](get-started-with-mr.md), сейчас вы находитесь в середине своего пути знакомства с основами смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="373e6-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="373e6-181">Отсюда вы можете перейти к следующей основной теме:</span><span class="sxs-lookup"><span data-stu-id="373e6-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="373e6-182">Расширение процесса разработки</span><span class="sxs-lookup"><span data-stu-id="373e6-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)