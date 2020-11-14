---
title: Что такое голограмма?
description: HoloLens позволяет просматривать трехмерные голограммы и работать с ними, объекты со светлой и звуковой частью, отображаемые по всему миру.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, голограммы, проектирование, взаимодействие
ms.openlocfilehash: f902639e66246c9184750ebc58dbad1c04b2bb5a
ms.sourcegitcommit: cc27d31f0cebaf9fc4221a3300a9e3d73230b367
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631472"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="dd845-104">Что такое голограмма?</span><span class="sxs-lookup"><span data-stu-id="dd845-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="dd845-105">HoloLens позволяет создавать **голограммы** , объекты света и звук, которые отображаются в мире, как будто они являются реальными объектами.</span><span class="sxs-lookup"><span data-stu-id="dd845-105">HoloLens lets you create **holograms** , objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="dd845-106">Голограммы отвечают на [взгляд](../design/gaze-and-commit.md), [жесты](../design/gaze-and-commit.md#composite-gestures) и [команды](../design/voice-input.md), а также могут взаимодействовать с [реальными областями](../design/spatial-mapping.md) по всему миру.</span><span class="sxs-lookup"><span data-stu-id="dd845-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures) and [voice commands](../design/voice-input.md), and can interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="dd845-107">Благодаря голограммам вы можете создавать цифровые объекты, которые являются частью окружающего мира.</span><span class="sxs-lookup"><span data-stu-id="dd845-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="dd845-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="dd845-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dd845-109"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="dd845-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="dd845-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd845-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="dd845-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="dd845-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="dd845-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd845-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dd845-113">Holograms (Голограммы)</span><span class="sxs-lookup"><span data-stu-id="dd845-113">Holograms</span></span></td>
        <td><span data-ttu-id="dd845-114">✔️</span><span class="sxs-lookup"><span data-stu-id="dd845-114">✔️</span></span></td>
        <td><span data-ttu-id="dd845-115">✔️</span><span class="sxs-lookup"><span data-stu-id="dd845-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="dd845-116">Голограмма состоит из светлого и звукового</span><span class="sxs-lookup"><span data-stu-id="dd845-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="dd845-117">Голограммы [, отображаемые HoloLens,](../develop/platform-capabilities-and-apis/rendering.md) отображаются в списке holographic непосредственно перед глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd845-117">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="dd845-118">Голограммы добавляют свет в мир, что означает, что вы видите как свет с экрана, так и свет из окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="dd845-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="dd845-119">HoloLens не удаляет освещение от глаз, поэтому голограммы нельзя визуализировать с черным цветом.</span><span class="sxs-lookup"><span data-stu-id="dd845-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="dd845-120">Вместо этого черная содержимое отображается как прозрачное.</span><span class="sxs-lookup"><span data-stu-id="dd845-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="dd845-121">Голограммы могут иметь много различных представлений и поведений.</span><span class="sxs-lookup"><span data-stu-id="dd845-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="dd845-122">Некоторые из них реалистичны, а другие — мультипликационные и ethereal.</span><span class="sxs-lookup"><span data-stu-id="dd845-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="dd845-123">Голограммы могут выделять функции в окружающей обстановке, и они могут быть элементами в пользовательском интерфейсе приложения.</span><span class="sxs-lookup"><span data-stu-id="dd845-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![Руки, работающие с голограммой](images/hologram-hands-940px.jpg)

<span data-ttu-id="dd845-125">Голограммы также могут делать [звуки](../design/spatial-sound.md), которые будут поступать из определенного места в окружающей обстановке.</span><span class="sxs-lookup"><span data-stu-id="dd845-125">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="dd845-126">В HoloLens звук поступает из двух динамиков, расположенных непосредственно над ушки, и не охватывает их.</span><span class="sxs-lookup"><span data-stu-id="dd845-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="dd845-127">Как и на экранах, динамики являются аддитивными, добавляя новые звуки, не блокируя звуки в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="dd845-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="dd845-128">Голограмму можно поместить в мир или тег вместе с вами.</span><span class="sxs-lookup"><span data-stu-id="dd845-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="dd845-129">При наличии определенного расположения, в котором вы хотите создать голограмму, его можно [разместить](../design/coordinate-systems.md) в любом месте мира.</span><span class="sxs-lookup"><span data-stu-id="dd845-129">When you have a particular location where you want a hologram, you can [place](../design/coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="dd845-130">По мере того как вы просматриваете эту голограмму, она будет выглядеть стабильно по сравнению с окружающим миром.</span><span class="sxs-lookup"><span data-stu-id="dd845-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="dd845-131">Если вы используете [пространственное привязку](../design/coordinate-systems.md#spatial-anchors) для того, чтобы закрепить этот объект в мире, система может даже запоминать, где он остался, когда вы поступите позже.</span><span class="sxs-lookup"><span data-stu-id="dd845-131">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![Два мужчин, использующих макет Microsoft Dynamics 365 в сфере розничной торговли](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="dd845-133">Некоторые голограммы следуют пользователю.</span><span class="sxs-lookup"><span data-stu-id="dd845-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="dd845-134">Эти пометки на основе тегов располагаются относительно пользователя, независимо от того, где они проходят.</span><span class="sxs-lookup"><span data-stu-id="dd845-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="dd845-135">Вы можете даже добавить голограмму в течение определенного промежутка, а затем поместить ее на стене после перехода в другую комнату.</span><span class="sxs-lookup"><span data-stu-id="dd845-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="dd845-136">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="dd845-136">**Best practices**</span></span>
* <span data-ttu-id="dd845-137">Некоторые сценарии могут потребовать, чтобы голограммы были легко обнаруживаемыми или видимыми на протяжении всего процесса.</span><span class="sxs-lookup"><span data-stu-id="dd845-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="dd845-138">Существует два высокоуровневого подхода к такому размещению.</span><span class="sxs-lookup"><span data-stu-id="dd845-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="dd845-139">Назовем их **«Отображение-блокировка»** и **«текст заблокирован»**.</span><span class="sxs-lookup"><span data-stu-id="dd845-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="dd845-140">При отображении содержимое, заблокированное на экране, располагается на экране на устройстве.</span><span class="sxs-lookup"><span data-stu-id="dd845-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="dd845-141">Это непросто по ряду причин, включая неестественное чувство «клингинесс», которое делает множество пользователей неразочарованными и желаете «встряхните».</span><span class="sxs-lookup"><span data-stu-id="dd845-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="dd845-142">Как правило, многие разработчики обнаружили, что лучше избегать содержимого блокировки с отображением.</span><span class="sxs-lookup"><span data-stu-id="dd845-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="dd845-143">Подход с блокировкой текста гораздо более форгивабле.</span><span class="sxs-lookup"><span data-stu-id="dd845-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="dd845-144">Блокировка текста заключается в том, что голограмма связана с телом пользователя или с вектором взгляда, но размещается в трехмерном пространстве вокруг пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd845-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="dd845-145">Многие опыт применяют поведение блокировки текста, при котором под голограммой «пользователи» следует поворачивать, что позволяет пользователю вращать текст и перемещаться по месту, не теряя голограммы.</span><span class="sxs-lookup"><span data-stu-id="dd845-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="dd845-146">Включение задержки позволяет более естественным движением голограмм.</span><span class="sxs-lookup"><span data-stu-id="dd845-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="dd845-147">Например, в некоторых основных пользовательских интерфейсах ОС Windows holographic используется разновидность блокировки тела, которая после взгляда пользователя получает доброй, эластичную задержку, когда пользователь превращает свою головку.</span><span class="sxs-lookup"><span data-stu-id="dd845-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="dd845-148">Разместите голограмму на удобном для просмотра расстоянии, обычно около 1-2 метров от головного.</span><span class="sxs-lookup"><span data-stu-id="dd845-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="dd845-149">Укажите степень отклонения элементов, которые должны постоянно находиться в holographicом кадре, или можно анимировать содержимое на одной стороне экрана, когда пользователь изменяет точку зрения.</span><span class="sxs-lookup"><span data-stu-id="dd845-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="dd845-150">**Размещайте голограммы в оптимальной зоне — между 1,25 m и 5 мин**</span><span class="sxs-lookup"><span data-stu-id="dd845-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="dd845-151">Два счетчика являются наиболее оптимальными, и работа с ними приведет к снижению производительности, чем в одном из показателей.</span><span class="sxs-lookup"><span data-stu-id="dd845-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="dd845-152">На расстоянии вблизи от одного метра самые новые, скорее всего, будут проблематичными, чем у стационарных голограмм.</span><span class="sxs-lookup"><span data-stu-id="dd845-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="dd845-153">Рассмотрите возможность аккуратного обрезки и исчезновения содержимого, когда оно слишком близко, чтобы не соблюдать непредсказуемый опыт пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd845-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![Оптимальное расстояние для размещения голограмм от пользователя.](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="dd845-155">Голограмма взаимодействует с вами и вашим миром</span><span class="sxs-lookup"><span data-stu-id="dd845-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="dd845-156">Голограммы не только освещены и не имеют звука; Они также являются активной частью вашего мира.</span><span class="sxs-lookup"><span data-stu-id="dd845-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="dd845-157">Взгляните на голограмму и жест с рукой, а голограмма может начать следовать вам.</span><span class="sxs-lookup"><span data-stu-id="dd845-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="dd845-158">Дайте голосовую команду на голограмму, и она может ответить.</span><span class="sxs-lookup"><span data-stu-id="dd845-158">Give a voice command to a hologram, and it can reply.</span></span>

![Группа сотрудников служебной программы для государственных организаций, использующих Microsoft HoloLens 2 для совместной работы в проекте разработки на основе фермы "Ветер"](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="dd845-160">Голограммы позволяют использовать персональные взаимодействия, которые не могут быть в других местах.</span><span class="sxs-lookup"><span data-stu-id="dd845-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="dd845-161">Так как HoloLens знает, где он находится в мире, то с точки зрения прохождения в комнате с помощью этого символа можно увидеть, что он находится в разных местах.</span><span class="sxs-lookup"><span data-stu-id="dd845-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="dd845-162">Голограмма может также взаимодействовать с окружающей обстановкой.</span><span class="sxs-lookup"><span data-stu-id="dd845-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="dd845-163">Например, можно разместить holographic-движущийся шарик над таблицей.</span><span class="sxs-lookup"><span data-stu-id="dd845-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="dd845-164">Затем, выполнив [касание](../design/gaze-and-commit.md#composite-gestures), обратите внимание на шарик и вынимайте звук при попадании в таблицу.</span><span class="sxs-lookup"><span data-stu-id="dd845-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="dd845-165">Голограммы также могут перекрыто в реальных объектах.</span><span class="sxs-lookup"><span data-stu-id="dd845-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="dd845-166">Например, holographic-символ может пройти через дверцу и позади стены.</span><span class="sxs-lookup"><span data-stu-id="dd845-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="dd845-167">**Советы по интеграции голограмм и реального мира**</span><span class="sxs-lookup"><span data-stu-id="dd845-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="dd845-168">Выровняйте до гравитатионал правил упрощает связь с голограммами и более белиевабле.</span><span class="sxs-lookup"><span data-stu-id="dd845-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="dd845-169">Пример: Разместите holographic-собака на земле & Васе в таблице, а не заключайте в них место.</span><span class="sxs-lookup"><span data-stu-id="dd845-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="dd845-170">Многие дизайнеры обнаружили, что они могут даже более белиевабли интегрировать голограммы, создавая «негативную тень» на той поверхности, где находится голограмма.</span><span class="sxs-lookup"><span data-stu-id="dd845-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="dd845-171">Для этого создается мягкое свечение вокруг голограммы, а затем вычитается "тень" из свечения.</span><span class="sxs-lookup"><span data-stu-id="dd845-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="dd845-172">Мягкое свечение интегрируется с освещением от реального мира, а теневое — с голограммой в среде.</span><span class="sxs-lookup"><span data-stu-id="dd845-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="dd845-173">Голограмма — это любой</span><span class="sxs-lookup"><span data-stu-id="dd845-173">A hologram is whatever</span></span> <br><span data-ttu-id="dd845-174">Вы можете заниматься</span><span class="sxs-lookup"><span data-stu-id="dd845-174">you can dream up</span></span><br>
        <span data-ttu-id="dd845-175">Как holographic-разработчик, вы можете разбить свои творческие способности на плоские экраны и в мир по всему миру.</span><span class="sxs-lookup"><span data-stu-id="dd845-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="dd845-176">Что будет *построено* ?</span><span class="sxs-lookup"><span data-stu-id="dd845-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="dd845-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="dd845-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="dd845-178">![Holographic воображаемый мир в гостиной](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd845-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="dd845-179">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="dd845-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="dd845-180">Если вы следуете изложенному нами [плану обучения](get-started-with-mr.md), сейчас вы находитесь в середине своего пути знакомства с основами смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="dd845-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="dd845-181">Отсюда вы можете перейти к следующей основной теме:</span><span class="sxs-lookup"><span data-stu-id="dd845-181">From here, you can proceed to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="dd845-182">Расширение процесса разработки</span><span class="sxs-lookup"><span data-stu-id="dd845-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)

