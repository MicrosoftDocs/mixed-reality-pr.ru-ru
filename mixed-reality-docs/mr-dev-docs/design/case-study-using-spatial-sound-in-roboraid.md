---
title: Пример использования. использование пространственного звука в Робораид
description: Пространственный звук — одна из самых интересных возможностей Microsoft HoloLens, которая позволяет пользователям воспринимать все, что происходит, когда объекты находятся за пределами.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Робораид, Пространственный звук
ms.openlocfilehash: 1482c914d261cae698a1460873b217b0683cd16b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692133"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a><span data-ttu-id="d04d3-104">Пример использования. использование пространственного звука в Робораид</span><span class="sxs-lookup"><span data-stu-id="d04d3-104">Case study - Using spatial sound in RoboRaid</span></span>

<span data-ttu-id="d04d3-105">В этой статье описываются уникальные проблемы, с которыми сталкиваются группы разработчиков Microsoft HoloLens при создании звука для [робораид](https://www.microsoft.com/p/roboraid/9nblggh5fv3j), кораблей в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d04d3-105">This article describes the unique challenges that the Microsoft HoloLens Experience Team encountered when creating audio for [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j), a mixed-reality first-person shooter.</span></span>

## <a name="the-tech"></a><span data-ttu-id="d04d3-106">Технический</span><span class="sxs-lookup"><span data-stu-id="d04d3-106">The tech</span></span>

<span data-ttu-id="d04d3-107">[Пространственный звук](spatial-sound.md) — одна из самых интересных возможностей Microsoft HoloLens, которая позволяет пользователям воспринимать все, что происходит, когда объекты находятся за пределами.</span><span class="sxs-lookup"><span data-stu-id="d04d3-107">[Spatial sound](spatial-sound.md) is one of the most exciting features of Microsoft HoloLens, providing a way for users to perceive what's going on around them when objects are out of the line of sight.</span></span>

<span data-ttu-id="d04d3-108">В Робораид наиболее очевидным и эффективным использованием пространственного звука является оповещение проигрывателя о том, что что-то произошло за пределами вашего периферийного пользователя.</span><span class="sxs-lookup"><span data-stu-id="d04d3-108">In RoboRaid, the most obvious and effective use of spatial sound is to alert the player to something happening outside of the user's peripheral vision.</span></span> <span data-ttu-id="d04d3-109">Например, злоумышленник может ввести любую из отсканированных стен в комнате, но если вы не находитесь в расположении, где она вводится, вы можете пропустить ее.</span><span class="sxs-lookup"><span data-stu-id="d04d3-109">For example, the Breacher can enter from any of the scanned walls in the room, but if you're not facing the location where it's entering, you might miss it.</span></span> <span data-ttu-id="d04d3-110">Чтобы предупредить вас на эту инвасион, вы узнаете о том, что вы пойдете из места, где находится нарушение, что позволит вам быстро приступить к его устранению.</span><span class="sxs-lookup"><span data-stu-id="d04d3-110">To alert you to this invasion, you'll hear a distinct bit of audio coming from where the Breacher is entering, which lets you know that you need to act quickly to stop it.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="d04d3-111">Сопутствующие ресурсы</span><span class="sxs-lookup"><span data-stu-id="d04d3-111">Behind the scenes</span></span>

<span data-ttu-id="d04d3-112">Процесс создания пространственного звука для приложений HoloLens — это новый и уникальный, и отсутствие в прошлом проектах, используемых для ссылки, может привести к большому началу работы при возникновении проблемы.</span><span class="sxs-lookup"><span data-stu-id="d04d3-112">The process of creating spatial sound for HoloLens apps is so new and unique and the lack of past projects to use for reference can lead to a lot of head scratching when you run into a problem.</span></span> <span data-ttu-id="d04d3-113">Надеюсь, эти примеры проблем со звуком, которые мы столкнулись при создании Робораид, помогут вам создать звук для своих приложений.</span><span class="sxs-lookup"><span data-stu-id="d04d3-113">Hopefully, these examples of the audio challenges we faced while making RoboRaid will help you as you create audio for your own apps.</span></span>

### <a name="be-mindful-of-taxing-the-cpu"></a><span data-ttu-id="d04d3-114">Учитывать объем ЦП</span><span class="sxs-lookup"><span data-stu-id="d04d3-114">Be mindful of taxing the CPU</span></span>

<span data-ttu-id="d04d3-115">Пространственный звук может затребоваться на ЦП.</span><span class="sxs-lookup"><span data-stu-id="d04d3-115">Spatial sound can be demanding on the CPU.</span></span> <span data-ttu-id="d04d3-116">Для занятых возможностей, таких как Робораид, было крайне важно, чтобы экземпляры пространственного звука были на 8 раз в любой момент времени.</span><span class="sxs-lookup"><span data-stu-id="d04d3-116">For a busy experience like RoboRaid it was crucial to keep the instances of spatial sound to under eight at any given time.</span></span> <span data-ttu-id="d04d3-117">В большинстве случаев это было так же просто, как Установка предельного количества экземпляров различных событий аудио, чтобы все экземпляры, происходящие после достижения предела, были уничтожены.</span><span class="sxs-lookup"><span data-stu-id="d04d3-117">For the most part, it was as easy as setting the limit of instances of different audio events so that any instances that happen after the limit is reached are killed.</span></span> <span data-ttu-id="d04d3-118">Например, при дроны порождении их скреамс ограничены тремя экземплярами в любое заданное время.</span><span class="sxs-lookup"><span data-stu-id="d04d3-118">For example, when drones spawn, their screams are limited to three instances at any given time.</span></span> <span data-ttu-id="d04d3-119">Принимая во внимание только четыре дроны, которые могут быть порождены одновременно, три скреамс являются небольшими, так как вы не сможете легко отследить такое большое количество звуковых событий.</span><span class="sxs-lookup"><span data-stu-id="d04d3-119">Considering only about four drones can spawn at once, three screams are plenty since there’s no way your brain can keep track of that many similar-sounding audio events.</span></span> <span data-ttu-id="d04d3-120">Это освобождает ресурсы для других пространственных событий, таких как врагов взрывы или противников, которые подготавливают к прокрутку.</span><span class="sxs-lookup"><span data-stu-id="d04d3-120">This freed up resources for other spatial sound events, like enemy explosions or enemies preparing to shoot.</span></span>

### <a name="rewarding-a-successful-dodge"></a><span data-ttu-id="d04d3-121">Вознаграждается успешного осветления</span><span class="sxs-lookup"><span data-stu-id="d04d3-121">Rewarding a successful dodge</span></span>

<span data-ttu-id="d04d3-122">Додгинг механику является одним из наиболее важных аспектов игрового процесса в Робораид, а также что-то, что мы казалось уникальными для работы HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d04d3-122">The dodging mechanic is one of the most important aspects of gameplay in RoboRaid, and also something that we felt was truly unique to the HoloLens experience.</span></span> <span data-ttu-id="d04d3-123">Таким образом, мы хотели сделать успешное подлинное Осветление для игрока.</span><span class="sxs-lookup"><span data-stu-id="d04d3-123">As such, we wanted to make successful dodges very rewarding to the player.</span></span> <span data-ttu-id="d04d3-124">Мы получили Doppler «вхизз-by» для того, чтобы на ранних этапах разработки было достаточно.</span><span class="sxs-lookup"><span data-stu-id="d04d3-124">We got the Doppler "whizz-by" to sound compelling fairly early on in the development.</span></span> <span data-ttu-id="d04d3-125">Изначально мой план использовал цикл и манипулировать им в режиме реального времени, используя громкость, шаг и фильтр.</span><span class="sxs-lookup"><span data-stu-id="d04d3-125">Initially, my plan was to use a loop and manipulate it in real-time using volume, pitch, and filter.</span></span> <span data-ttu-id="d04d3-126">Реализация для этого была бы очень тщательной, поэтому перед фиксацией ресурсов для фактической сборки мы создали дешевый прототип с помощью ресурса с Dopplerным результатом помогут, чтобы узнать, как это пройдет \*.</span><span class="sxs-lookup"><span data-stu-id="d04d3-126">The implementation for this was going to be very elaborate, so before committing resources to actually build this we created a cheap prototype using an asset with the Doppler effect baked in just to find out how it felt\*.</span></span> <span data-ttu-id="d04d3-127">Наше талантливыеное разработчик сделало это таким образом, чтобы этот вхизз ресурс воспроизводился в течение 0,7 секунд, прежде чем прожектиле будет передаваться по удивительному игроку, а результаты на самом деле впечатляют!</span><span class="sxs-lookup"><span data-stu-id="d04d3-127">Our talented dev made it so that this whizz-by asset would play back exactly 0.7 seconds before the projectile will have passed by the player’s ear and the results felt really amazing!</span></span> <span data-ttu-id="d04d3-128">Нет необходимости говорить, что мы дитчед более сложное решение и реализовали прототип.</span><span class="sxs-lookup"><span data-stu-id="d04d3-128">Needless to say, we ditched the more complex solution and implemented the prototype.</span></span>

<span data-ttu-id="d04d3-129">*(Дополнительные сведения о создании звукового ресурса с встроенным Dopplerным результатом см. [в разделе 100 вхушес за 2 минуты](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
</span><span class="sxs-lookup"><span data-stu-id="d04d3-129">*(For more information about creating an audio asset with the Doppler effect built in, see [100 Whooshes in 2 Minutes](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
</span></span><br>
<span data-ttu-id="d04d3-130">![Успешно додгинг прожектиле врагов, чтобы игрок заработал вхизз.](images/successful-dodge-roboraid-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d04d3-130">![Successfully dodging an enemy's projectile rewards the player with a satisfying whizz-by sound.](images/successful-dodge-roboraid-500px.jpg)</span></span>

### <a name="ditching-ineffective-sounds"></a><span data-ttu-id="d04d3-131">Дитчинг неэффективное звуковое сопровождение</span><span class="sxs-lookup"><span data-stu-id="d04d3-131">Ditching ineffective sounds</span></span>

<span data-ttu-id="d04d3-132">Первоначально нам пришлось воспроизводить звук развертывания за проигрывателем после того, как он успешно выделил врагов прожектиле, но мы решили выделить это по нескольким причинам.</span><span class="sxs-lookup"><span data-stu-id="d04d3-132">Originally, we had wanted to play an explosion sound behind the player once they’ve successfully dodged the enemy projectile, but we decided to ditch this for several reasons.</span></span> <span data-ttu-id="d04d3-133">Во-первых, это не так эффективно, как вхизза SFX, используемая для осветления.</span><span class="sxs-lookup"><span data-stu-id="d04d3-133">First, it didn’t feel as effective as the whizz-by SFX we used for the dodge.</span></span> <span data-ttu-id="d04d3-134">К тому времени, когда прожектиле попадает на стену, что-то еще могло бы произойти в игре, которая бы сильно маскирует этот звук.</span><span class="sxs-lookup"><span data-stu-id="d04d3-134">By the time the projectile hits a wall behind you, something else would have happened in the game that would pretty much mask that sound.</span></span> <span data-ttu-id="d04d3-135">Во вторых, у нас не было конфликтов на этаж, поэтому нам не удалось получить развертывание, когда прожектиле попадают в этаж, а не на стены.</span><span class="sxs-lookup"><span data-stu-id="d04d3-135">Secondly, we didn’t have collision on the floor, so we couldn’t get the explosion to play when the projectile hit the floor instead of the walls.</span></span> <span data-ttu-id="d04d3-136">И, наконец, были стоимость ЦП пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="d04d3-136">And finally, there was the CPU cost of spatial sound.</span></span> <span data-ttu-id="d04d3-137">Elite Скорпион врагов (один, который может обходить внутри стены) имеет специальную атаку, которая пропустила около восьми снаряды.</span><span class="sxs-lookup"><span data-stu-id="d04d3-137">The Elite Scorpion enemy (one that can crawl inside the wall) has a special attack that shoots about eight projectiles.</span></span> <span data-ttu-id="d04d3-138">Это не только усложняет создание огромных ресурсов, но и ужасные кракклинг, так как он был слишком сложным.</span><span class="sxs-lookup"><span data-stu-id="d04d3-138">Not only did that make a huge mess in the mix, it also introduced awful crackling because it was hitting the CPU too hard.</span></span>

### <a name="communicating-a-hit"></a><span data-ttu-id="d04d3-139">Связь с нажатием</span><span class="sxs-lookup"><span data-stu-id="d04d3-139">Communicating a hit</span></span>

<span data-ttu-id="d04d3-140">Интересной проблемой, с которой мы столкнулись, это было уникально для работы с HoloLens, было сложно связаться с игроками, на которые они столкнулись.</span><span class="sxs-lookup"><span data-stu-id="d04d3-140">An interesting issue we ran into, which we felt was unique to the HoloLens experience, was the difficulty of effectively communicating to the players that they have been hit.</span></span> <span data-ttu-id="d04d3-141">Что делает работу в смешанной реальности успешной.</span><span class="sxs-lookup"><span data-stu-id="d04d3-141">What makes a mixed reality experience successful is the feeling that the story is happening to you.</span></span> <span data-ttu-id="d04d3-142">Это означает, что вы должны поверить, что вы инопланетянин робота инвасион в собственной гостиной.</span><span class="sxs-lookup"><span data-stu-id="d04d3-142">That means that you have to believe that YOU are fighting an alien robot invasion in your own living room.</span></span>

<span data-ttu-id="d04d3-143">Очевидно, что игроки не сталкиваются с тем, что они попадают, так что нам пришлось бы найти способ уверенности проигрывателя о том, что к ним хаппед.</span><span class="sxs-lookup"><span data-stu-id="d04d3-143">Players obviously won't feel anything when they get hit, so we had to find a way to really convince the player that something bad had happed to them.</span></span> <span data-ttu-id="d04d3-144">В обычных играх вы можете увидеть анимацию, которая позволит вам узнать, что ваш символ был нажат, или экран красным, и ваш символ может grunt немного.</span><span class="sxs-lookup"><span data-stu-id="d04d3-144">In conventional games you might see an animation that lets you know your character has taken a hit, or the screen might flash red and your character might grunt a little.</span></span> <span data-ttu-id="d04d3-145">Так как эти типы подсказок не работают в смешанной реальности, мы решили объединить визуальную подсказку с реально преувеличенныхным звуком, что говорит о том, что вы сделали ущерб.</span><span class="sxs-lookup"><span data-stu-id="d04d3-145">Since these types of cues don't work in a mixed reality experience, we decided to combine the visual cue with a really exaggerated sound that indicates you've taken damage.</span></span> <span data-ttu-id="d04d3-146">Я создал большой звук и сделал его заметным в сочетании с тем, что он дуккед все.</span><span class="sxs-lookup"><span data-stu-id="d04d3-146">I created a big sound, and made it so prominent in the mix that it ducked everything down.</span></span> <span data-ttu-id="d04d3-147">Затем, чтобы сделать его еще более заметным, мы добавили короткое предупреждение, как если бы ядерная подсистема была в состоянии приемника.</span><span class="sxs-lookup"><span data-stu-id="d04d3-147">Then, to make it stand out even more, we added a short warning sound as if a nuclear sub was sinking.</span></span> 
<br>
<span data-ttu-id="d04d3-148">![Когда игрок прийдет к Робораид, он увидит визуальную подсказку, но также получит звуковой Cue преувеличенных, указывающий на то, что они внесли ущерб.](images/player-hit-roboraid-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d04d3-148">![When a player gets hit in RoboRaid, they see a visual cue, but also get an exaggerated audio cue that tells them they've taken damage.](images/player-hit-roboraid-500px.jpg)</span></span>

### <a name="getting-big-sound-from-small-speakers"></a><span data-ttu-id="d04d3-149">Получение большого звука от мелких динамиков</span><span class="sxs-lookup"><span data-stu-id="d04d3-149">Getting big sound from small speakers</span></span>

<span data-ttu-id="d04d3-150">Динамики HoloLens являются небольшими и небольшими в соответствии с потребностями устройства, поэтому вы не сможете слышать слишком мало усилий.</span><span class="sxs-lookup"><span data-stu-id="d04d3-150">HoloLens speakers are small and light to suit the needs of the device, so you can’t expect to hear too much low-end.</span></span> <span data-ttu-id="d04d3-151">Как и при разработке для смарт-телефонов или карманных игровых устройств, проектировщики и композиторы должны быть учитыватьют частоту их звучания.</span><span class="sxs-lookup"><span data-stu-id="d04d3-151">Similar to developing for smart phones or handheld gaming devices, sound designers and composers have to be mindful of the frequency content of their audio.</span></span> <span data-ttu-id="d04d3-152">Я всегда разрабатывать звуки или записывать музыку с полным диапазоном частот, так как людьминые наушники являются вариантом для пользователей.</span><span class="sxs-lookup"><span data-stu-id="d04d3-152">I always design sounds or write music with full frequency range because wearing headphones is an option for the users.</span></span> <span data-ttu-id="d04d3-153">Тем не менее, чтобы обеспечить совместимость с докладчиками HoloLens, я могу выполнить тест время от времени, поместив EQ в главную часть любого Джон, с которой я работаю.</span><span class="sxs-lookup"><span data-stu-id="d04d3-153">However, to ensure compatibility with HoloLens speakers, I run a test occasionally by putting an EQ in the master of any DAW I happen to be working in.</span></span> <span data-ttu-id="d04d3-154">Параметр EQ состоит из высококачественного фильтра с 600 до 700 Гц (неслишком много) и низкого уровня фильтра около 10 000 (очень очень много).</span><span class="sxs-lookup"><span data-stu-id="d04d3-154">The EQ setting consists of a high-pass filter around 600 to 700 Hz (not too steep) and low-pass filter at around 10K (very steep).</span></span> <span data-ttu-id="d04d3-155">Это должно дать вам примерную представление о том, как звуки будут воспроизводиться на устройстве.</span><span class="sxs-lookup"><span data-stu-id="d04d3-155">That should give you a ballpark idea of how your sounds will playback on the device.</span></span>

<span data-ttu-id="d04d3-156">Если вы полагаетесь на низкие значения, чтобы придать смысл при смене кабеля в музыке, вы можете обнаружить, что моя музыка полностью теряет смысл корня при применении этого параметра EQ.</span><span class="sxs-lookup"><span data-stu-id="d04d3-156">If you are relying on bass to give the sense of chord changing in your music, you may find that your music completely loses the sense of root when you apply this EQ setting.</span></span> <span data-ttu-id="d04d3-157">Чтобы устранить эту проблему, я добавил еще один слой на низкие уровни, которые Октава выше (с некоторыми широкими гармониями) и смешанные ИТ, чтобы получить представление об корневой обратной стороне.</span><span class="sxs-lookup"><span data-stu-id="d04d3-157">To remedy this, I added another layer to the bass that is one octave higher (with some rich harmonics) and mixed it to get the sense of root back.</span></span> <span data-ttu-id="d04d3-158">Иногда использование искажений для управления гармониями повлечет за собой достаточное количество содержимого частоты в верхнем диапазоне, чтобы сделать наш мозг думаю, что в нем есть что-то.</span><span class="sxs-lookup"><span data-stu-id="d04d3-158">Sometimes using distortion to amp up the harmonics will give enough frequency content in the upper range to make our brain think that there’s something underneath it.</span></span> <span data-ttu-id="d04d3-159">Это справедливо для SFX, таких как влияние, взрывные или звуковые сигналы, на специальное время, например Суперпользователи-атаки начальника.</span><span class="sxs-lookup"><span data-stu-id="d04d3-159">This is true for SFX like impacts, explosions, or sounds for special moments, such as a boss' super attacks.</span></span> <span data-ttu-id="d04d3-160">Вы действительно не можете полагаться на низкую часть, чтобы дать игроку представление о влиянии или весе.</span><span class="sxs-lookup"><span data-stu-id="d04d3-160">You really can’t rely on the low-end to give the player a sense of impact or weight.</span></span> <span data-ttu-id="d04d3-161">Как и в случае с музыкальными файлами, использование искажений позволяет значительно добиться небольшого объема уплотнения.</span><span class="sxs-lookup"><span data-stu-id="d04d3-161">As with music, using distortion to give a little bit of crunch definitely helped.</span></span>

### <a name="making-your-audio-cues-stand-out"></a><span data-ttu-id="d04d3-162">Выделяйте звуковые подсказки</span><span class="sxs-lookup"><span data-stu-id="d04d3-162">Making your audio cues stand out</span></span>

<span data-ttu-id="d04d3-163">Естественно, все участники группы хотели бомбастик музыку, громкое гнутье и сумасшедшийное развертывание. но они также хотят иметь возможность слышать VoiceOver или любые другие критически важные для игры звуковые подсказки.</span><span class="sxs-lookup"><span data-stu-id="d04d3-163">Naturally, everyone on the team wanted bombastic music, loud guns, and crazy explosions; but they also wanted to be able to hear voiceover or any other game-critical audio cues.</span></span>

<span data-ttu-id="d04d3-164">В игре в консоли с полным диапазоном частот вы можете использовать дополнительные параметры для разделения частоты в зависимости от важности звука.</span><span class="sxs-lookup"><span data-stu-id="d04d3-164">On a console game with full range of frequency you have more options to divide frequencies up depending on the importance of the sound.</span></span> <span data-ttu-id="d04d3-165">Однако для Робораид я ограничил количество диапазонов частот, которые можно было бы расизгибовать от звуков.</span><span class="sxs-lookup"><span data-stu-id="d04d3-165">For RoboRaid, however, I was limited in the number of ranges of frequencies I could curve out from sounds.</span></span> <span data-ttu-id="d04d3-166">Например, если вы используете фильтр низкого уровня и Кривое слишком много от более высокого конца спектра, вы не будете оставлять ничего на звуковом уровне, так как это не слишком мало.</span><span class="sxs-lookup"><span data-stu-id="d04d3-166">For instance, if you use low-pass filter and curve out too much from the higher end of the spectrum, you won’t have anything left on the sound because there’s not much low-end.</span></span>

<span data-ttu-id="d04d3-167">Чтобы сделать Робораидный звук максимально большим, чем на устройстве, нам пришлось понизить динамический диапазон всей работы и значительно использовать дуккинг, создав четкое иерархию важности для различных типов звуков.</span><span class="sxs-lookup"><span data-stu-id="d04d3-167">In order to make RoboRaid sound as big as it can on the device, we had to lower the dynamic range of the whole experience and made extensive use of ducking by creating a clear hierarchy of importance for different types of sounds.</span></span> <span data-ttu-id="d04d3-168">Я установил дуккинг с-2 на-6 dB в зависимости от важности.</span><span class="sxs-lookup"><span data-stu-id="d04d3-168">I set the ducking from -2 to -6 dB depending on the importance.</span></span> <span data-ttu-id="d04d3-169">Мне лично не нравится очевидный дуккинг в играх, поэтому я тратил массу времени на настройку времени постепенного и выходного эффекта и объема ослабления громкости.</span><span class="sxs-lookup"><span data-stu-id="d04d3-169">I personally don’t like obvious ducking in games, so I spent a lot of time tuning the fade in/out timing and the amount of volume attenuation.</span></span> <span data-ttu-id="d04d3-170">Мы настроили отдельные шины для пространственного звука, непространственного звука, во и сухой шины без редействия для музыки, а затем создали очень высокий приоритет, критически важные и некритические шины.</span><span class="sxs-lookup"><span data-stu-id="d04d3-170">We set up separate busses for spatial sound, non-spatial sound, VO, and dry bus without reverb for music, then created very high priority, critical, and non-critical busses.</span></span> <span data-ttu-id="d04d3-171">Затем ресурсы были настроены для перехода на соответствующие шины.</span><span class="sxs-lookup"><span data-stu-id="d04d3-171">The assets were then set up to go to their appropriate busses.</span></span>

<span data-ttu-id="d04d3-172">Я надеюсь, что у ИТ-специалистов будет столько удовольствия и приятно работать над собственными приложениями, как я работал над Робораид.</span><span class="sxs-lookup"><span data-stu-id="d04d3-172">I hope audio professionals out there will have as much fun and excitement working on their own apps as I did working on RoboRaid.</span></span> <span data-ttu-id="d04d3-173">Я не могу ждать (и слышать!) о том, какие талантливые люди за пределами Майкрософт появятся для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d04d3-173">I can’t wait to see (and hear!) what the talented folks outside Microsoft will come up with for HoloLens.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="d04d3-174">Попробуйте сами</span><span class="sxs-lookup"><span data-stu-id="d04d3-174">Do it yourself</span></span>

<span data-ttu-id="d04d3-175">Одна из приемов, которую я обнаружил, чтобы сделать определенные события (например, взрывы) звуком «больше», как при заполнении комнаты, — создать ресурс Mono для пространственного звука и смешать его с помощью 2D-актива, который будет воспроизводиться в трехмерном виде.</span><span class="sxs-lookup"><span data-stu-id="d04d3-175">One trick I discovered to make certain events (such as explosions) sound "bigger"—like they're filling up the room—was to create a mono asset for the spatial sound and mix it with a 2D stereo asset, to be played back in 3D.</span></span> <span data-ttu-id="d04d3-176">Это занимает некоторую настройку, так как слишком большое количество информации в стерео содержимом уменьшает направленность ресурсов Mono.</span><span class="sxs-lookup"><span data-stu-id="d04d3-176">It does take some tuning, since having too much information in the stereo content will lessen the directionality of the mono assets.</span></span> <span data-ttu-id="d04d3-177">Однако получение правого баланса приведет к созданию огромных звуков, позволяющих игрокам превратить свои головки в нужное направление.</span><span class="sxs-lookup"><span data-stu-id="d04d3-177">However, getting the balance right will result in huge sounds that will get players to turn their heads in the right direction.</span></span>

<span data-ttu-id="d04d3-178">Вы можете попробовать это с помощью звуковых ресурсов, приведенных ниже:</span><span class="sxs-lookup"><span data-stu-id="d04d3-178">You can try this yourself using the audio assets below:</span></span>

<span data-ttu-id="d04d3-179">**Ситуация 1**</span><span class="sxs-lookup"><span data-stu-id="d04d3-179">**Scenario 1**</span></span>
1. <span data-ttu-id="d04d3-180">Скачайте [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) и задайте для него воспроизведение с помощью пространственного звука и назначьте его событию.</span><span class="sxs-lookup"><span data-stu-id="d04d3-180">Download [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) and set to playback through spatial sound and assign it to an event.</span></span>
2. <span data-ttu-id="d04d3-181">Скачайте [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) и задайте для параметра Воспроизведение на 2D-стерео и назначьте тому же событию, которое было указано выше.</span><span class="sxs-lookup"><span data-stu-id="d04d3-181">Download [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) and set to playback in 2D stereo and assign to the same event as above.</span></span> <span data-ttu-id="d04d3-182">Так как эти ресурсы нормализованы до Unity, то громкость обоих ресурсов не обрезается.</span><span class="sxs-lookup"><span data-stu-id="d04d3-182">Because these assets are normalized to Unity, attenuate volume of both assets so that it doesn’t clip.</span></span>
3. <span data-ttu-id="d04d3-183">Воспроизводить оба звука вместе.</span><span class="sxs-lookup"><span data-stu-id="d04d3-183">Play both sounds together.</span></span> <span data-ttu-id="d04d3-184">Переместите свой заголовок, чтобы показалось, как пространственный ИТ.</span><span class="sxs-lookup"><span data-stu-id="d04d3-184">Move your head around to feel how spatial it sounds.</span></span>

<span data-ttu-id="d04d3-185">**Ситуация 2**</span><span class="sxs-lookup"><span data-stu-id="d04d3-185">**Scenario 2**</span></span>
1. <span data-ttu-id="d04d3-186">Скачайте [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) и задайте для него воспроизведение с помощью пространственного звука и назначьте событию.</span><span class="sxs-lookup"><span data-stu-id="d04d3-186">Download [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) and set to playback through spatial sound and assign to an event.</span></span>
2. <span data-ttu-id="d04d3-187">Воспроизведите этот ресурс отдельно, а затем сравните его с событием из сценария 1.</span><span class="sxs-lookup"><span data-stu-id="d04d3-187">Play this asset by itself then compare it to the event from Scenario 1.</span></span>
3. <span data-ttu-id="d04d3-188">Попробуйте использовать разные балансы Mono и стерео-файлов.</span><span class="sxs-lookup"><span data-stu-id="d04d3-188">Try different balance of mono and stereo files.</span></span>



## <a name="see-also"></a><span data-ttu-id="d04d3-189">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d04d3-189">See also</span></span>
* [<span data-ttu-id="d04d3-190">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="d04d3-190">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d04d3-191">Робораид для Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="d04d3-191">RoboRaid for Microsoft HoloLens</span></span>](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)