---
title: Что такое голограмма?
description: HoloLens позволяет просматривать трехмерные голограммы и работать с ними, объекты со светлой и звуковой частью, отображаемые вокруг вас.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, голограммы, проектирование, взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed reality, что является дополненным
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634335"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="925a8-104">Что такое голограмма?</span><span class="sxs-lookup"><span data-stu-id="925a8-104">What is a hologram?</span></span>

<span data-ttu-id="925a8-105">HoloLens позволяет просматривать **голограммы**, представляющие собой объекты света и звука, которые отображаются в мире, как и реальные объекты.</span><span class="sxs-lookup"><span data-stu-id="925a8-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="925a8-106">Голограммы может отвечать [на ваши](../design/gaze-and-commit.md)команды, [жесты](../design/gaze-and-commit.md#composite-gestures)и [голоса](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="925a8-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="925a8-107">Они даже могут взаимодействовать с [реальными областями](../design/spatial-mapping.md) по всему миру.</span><span class="sxs-lookup"><span data-stu-id="925a8-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="925a8-108">Голограммы являются цифровыми объектами, которые являются частью вашего мира.</span><span class="sxs-lookup"><span data-stu-id="925a8-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="925a8-109">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="925a8-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="925a8-110"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="925a8-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="925a8-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="925a8-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="925a8-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="925a8-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="925a8-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="925a8-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="925a8-114">Holograms (Голограммы)</span><span class="sxs-lookup"><span data-stu-id="925a8-114">Holograms</span></span></td>
        <td><span data-ttu-id="925a8-115">✔️</span><span class="sxs-lookup"><span data-stu-id="925a8-115">✔️</span></span></td>
        <td><span data-ttu-id="925a8-116">✔️</span><span class="sxs-lookup"><span data-stu-id="925a8-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="925a8-117">Голограмма состоит из светлого и звукового</span><span class="sxs-lookup"><span data-stu-id="925a8-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="925a8-118">Светлая</span><span class="sxs-lookup"><span data-stu-id="925a8-118">Light</span></span>

<span data-ttu-id="925a8-119">голограммы, которые HoloLens [рендеринга](../develop/platform-capabilities-and-apis/rendering.md) , появляются в holographic кадре непосредственно перед глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="925a8-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="925a8-120">Голограммы добавить свет в мир, что означает, что вы видите как свет с экрана, так и свет из окружающего мира.</span><span class="sxs-lookup"><span data-stu-id="925a8-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="925a8-121">поскольку HoloLens использует аддитивный экран, который добавляет освещение, черный цвет будет отображен прозрачным.</span><span class="sxs-lookup"><span data-stu-id="925a8-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="925a8-122">Голограммы могут иметь очень разные внешний вид и поведение.</span><span class="sxs-lookup"><span data-stu-id="925a8-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="925a8-123">Некоторые из них реалистичны, а другие — мультипликационные и ethereal.</span><span class="sxs-lookup"><span data-stu-id="925a8-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="925a8-124">Голограммы можно использовать для выделения компонентов в среде или использования их в качестве элементов пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="925a8-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Руки, работающие с голограммой](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="925a8-126">Звук</span><span class="sxs-lookup"><span data-stu-id="925a8-126">Sound</span></span>

<span data-ttu-id="925a8-127">Голограммы также могут создавать [звуки](../design/spatial-sound.md), которые поступают из определенного места в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="925a8-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="925a8-128">на HoloLens звук поступает из двух динамиков, расположенных непосредственно над ушки.</span><span class="sxs-lookup"><span data-stu-id="925a8-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="925a8-129">То же, что и holographic, колонки являются аддитивными, поставляя новые звуки, не блокируя звуки из вашей среды.</span><span class="sxs-lookup"><span data-stu-id="925a8-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="925a8-130">Голограмму можно поместить в мир или тег вместе с вами.</span><span class="sxs-lookup"><span data-stu-id="925a8-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="925a8-131">Если у вас есть фиксированное расположение голограммы, его можно [разместить](../design/coordinate-systems.md) точно на этом этапе мира.</span><span class="sxs-lookup"><span data-stu-id="925a8-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="925a8-132">По мере прочего, голограмма выглядит как стационарный на основе всего мира, как и физический объект.</span><span class="sxs-lookup"><span data-stu-id="925a8-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="925a8-133">Если для закрепления объекта используется [пространственное](../design/coordinate-systems.md#spatial-anchors) прикрепление, система может даже запоминать, где он остался, когда вы поступите позже.</span><span class="sxs-lookup"><span data-stu-id="925a8-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Два мужчин, использующих макет Microsoft Dynamics 365 в сфере розничной торговли](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="925a8-135">Некоторые голограммы следуют пользователю.</span><span class="sxs-lookup"><span data-stu-id="925a8-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="925a8-136">Они располагаются на основе пользователя.</span><span class="sxs-lookup"><span data-stu-id="925a8-136">They position themselves based on the user.</span></span> <span data-ttu-id="925a8-137">Вы можете добавить к ней голограмму, а затем поместить ее на стене после перехода в другую комнату.</span><span class="sxs-lookup"><span data-stu-id="925a8-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="925a8-138">**Рекомендации**</span><span class="sxs-lookup"><span data-stu-id="925a8-138">**Best practices**</span></span>

* <span data-ttu-id="925a8-139">Некоторые сценарии требуют, чтобы самые голограммы были легко обнаруживаемыми или видимыми на протяжении всего процесса.</span><span class="sxs-lookup"><span data-stu-id="925a8-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="925a8-140">Существует два высокоуровневого подхода к такому размещению.</span><span class="sxs-lookup"><span data-stu-id="925a8-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="925a8-141">Назовем их **Отображение-блокировка** и блокировка **текста**.</span><span class="sxs-lookup"><span data-stu-id="925a8-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="925a8-142">**Отображаемое** содержимое заблокировано на устройстве дисплея.</span><span class="sxs-lookup"><span data-stu-id="925a8-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="925a8-143">Этот тип содержимого сложнее по ряду причин, включая неестественное чувство «клингинесс», которое делает множество пользователей беспроблемными и хотят «встряхните».</span><span class="sxs-lookup"><span data-stu-id="925a8-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="925a8-144">Как правило, разработчики обнаружили, что это лучше, чтобы избежать содержимого блокировки при просмотре.</span><span class="sxs-lookup"><span data-stu-id="925a8-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="925a8-145">Содержимое, **заблокированное телом** , может быть намного более терпим отношению.</span><span class="sxs-lookup"><span data-stu-id="925a8-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="925a8-146">Блокировка текста — это то, что вы выдаете голограмму на тело пользователя или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="925a8-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="925a8-147">Многие опыт применяют поведение блокировки текста, где голограмма следует за пользователем, что позволяет пользователю вращать текст и перемещаться по месту, не теряя голограммы.</span><span class="sxs-lookup"><span data-stu-id="925a8-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="925a8-148">Включение задержки помогает передвижениям с голограммами быть более естественными.</span><span class="sxs-lookup"><span data-stu-id="925a8-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="925a8-149">например, в некоторых основных UI-интерфейсах Windows holographic используется вариант блокировки текста, который следует за пользователем с помощью взгляда на доброй, эластичную задержку, в то время как пользователь превращает свою головку.</span><span class="sxs-lookup"><span data-stu-id="925a8-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="925a8-150">Разместите голограмму на удобном для просмотра расстоянии, обычно около 1-2 метров от головного.</span><span class="sxs-lookup"><span data-stu-id="925a8-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="925a8-151">Разрешить элементам отменять смещение, если они должны постоянно находиться в holographic кадре, или переместить содержимое на одну сторону экрана, когда пользователь изменяет точку зрения.</span><span class="sxs-lookup"><span data-stu-id="925a8-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="925a8-152">Дополнительные сведения см. в разделе [объявления и теги — вдоль](../design/billboarding-and-tag-along.md) артилце.</span><span class="sxs-lookup"><span data-stu-id="925a8-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="925a8-153">**Размещайте голограммы в оптимальной зоне — от 1,25 м до 5 м**</span><span class="sxs-lookup"><span data-stu-id="925a8-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="925a8-154">Два счетчика — это наиболее оптимальное расстояние для просмотра.</span><span class="sxs-lookup"><span data-stu-id="925a8-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="925a8-155">Работа будет снижена по мере приближения к одному показателю.</span><span class="sxs-lookup"><span data-stu-id="925a8-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="925a8-156">На расстояниях менее 1 метра самые новые, вероятнее всего, могут оказаться проблематичными, чем стационарные голограммы.</span><span class="sxs-lookup"><span data-stu-id="925a8-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="925a8-157">Рекомендуется аккуратно обрезать или выпустить содержимое, когда оно получится слишком близко, поэтому вы не jarе пользователя в неприятныее просмотра.</span><span class="sxs-lookup"><span data-stu-id="925a8-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Оптимальное расстояние для размещения голограмм от пользователя.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="925a8-159">Голограмма взаимодействует с вами и вашим миром</span><span class="sxs-lookup"><span data-stu-id="925a8-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="925a8-160">Голограммы не только интенсивность и звук; Они также являются активной частью вашего мира.</span><span class="sxs-lookup"><span data-stu-id="925a8-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="925a8-161">Взгляните на голограмму и жест с рукой, а голограмма может начать следовать вам.</span><span class="sxs-lookup"><span data-stu-id="925a8-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="925a8-162">Выдайте голосовую команду, и она может ответить на эту голограмму.</span><span class="sxs-lookup"><span data-stu-id="925a8-162">Give a voice command, and the hologram can reply.</span></span>

![группа сотрудников служебной программы правительства, использующих Microsoft HoloLens 2 для совместной работы в проекте разработки на основе фермы "ветер"](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="925a8-164">Голограммы включить персональные взаимодействия, которые не могут быть доступны в других местах.</span><span class="sxs-lookup"><span data-stu-id="925a8-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="925a8-165">так как HoloLens знает, где находится в мире, то с помощью более известного символа вы можете напрямую взглянуть на глаза и начать беседу.</span><span class="sxs-lookup"><span data-stu-id="925a8-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="925a8-166">Голограмма может также взаимодействовать с окружающей обстановкой.</span><span class="sxs-lookup"><span data-stu-id="925a8-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="925a8-167">Например, можно разместить holographic-движущийся шарик над таблицей.</span><span class="sxs-lookup"><span data-stu-id="925a8-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="925a8-168">Затем, выполнив [касание](../design/gaze-and-commit.md#composite-gestures), посмотрите, что шарик передается и делает звук по мере попадания в таблицу.</span><span class="sxs-lookup"><span data-stu-id="925a8-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="925a8-169">Голограммы также можно перекрыто реальными объектами.</span><span class="sxs-lookup"><span data-stu-id="925a8-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="925a8-170">Например, holographic-символ может пройти через дверцу и позади стены.</span><span class="sxs-lookup"><span data-stu-id="925a8-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="925a8-171">**Советы для интеграции голограмм и реального мира**</span><span class="sxs-lookup"><span data-stu-id="925a8-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="925a8-172">Выровняйте до гравитатионал правил упрощает связь с голограммами и более белиевабле.</span><span class="sxs-lookup"><span data-stu-id="925a8-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="925a8-173">Например: Разместите holographic-собака на земле & Васе в таблице, а не заключайте в них место.</span><span class="sxs-lookup"><span data-stu-id="925a8-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="925a8-174">Многие дизайнеры обнаружили, что они могут интегрировать больше голограмм белиевабле, создав «негативную тень» на поверхности, на которой находится голограмма.</span><span class="sxs-lookup"><span data-stu-id="925a8-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="925a8-175">Для этого создается мягкое свечение вокруг голограммы, а затем вычитается "тень" из свечения.</span><span class="sxs-lookup"><span data-stu-id="925a8-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="925a8-176">Мягкое свечение интегрируется с освещением от реального мира.</span><span class="sxs-lookup"><span data-stu-id="925a8-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="925a8-177">Тень используется для заземления голограммы в среде.</span><span class="sxs-lookup"><span data-stu-id="925a8-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="925a8-178">Голограмма — это то, что</span><span class="sxs-lookup"><span data-stu-id="925a8-178">A hologram is what</span></span> <br><span data-ttu-id="925a8-179">Вы можете заниматься</span><span class="sxs-lookup"><span data-stu-id="925a8-179">you can dream up</span></span><br>
        <span data-ttu-id="925a8-180">Как holographic-разработчик, вы можете разбить свои творческие способности на плоские экраны и в мир по всему миру.</span><span class="sxs-lookup"><span data-stu-id="925a8-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="925a8-181">Что будет *построено* ?</span><span class="sxs-lookup"><span data-stu-id="925a8-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="925a8-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="925a8-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="925a8-183">![Holographic воображаемый мир в гостиной](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="925a8-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="925a8-184">Следующий этап</span><span class="sxs-lookup"><span data-stu-id="925a8-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="925a8-185">Вы находитесь в [пути обнаружения](get-started-with-mr.md) и изучаете основы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="925a8-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="925a8-186">Отсюда вы можете перейти к следующей основной теме:</span><span class="sxs-lookup"><span data-stu-id="925a8-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="925a8-187">Расширение процесса разработки</span><span class="sxs-lookup"><span data-stu-id="925a8-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)