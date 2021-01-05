---
title: Создание голограмм
description: Узнайте о смешанной реальности с помощью нового приложения разработки голограмм Майкрософт.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: МРТК, набор средств для смешанной реальности, голограммы, проектирование голограмм, обучение, пример приложения, гарнитура смешанной реальности, гарнитура виртуальной реальности, что такое виртуальная реальность
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757762"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="edcb9-104">Создание голограмм</span><span class="sxs-lookup"><span data-stu-id="edcb9-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="edcb9-105">Разрешите небольшое окно загрузки, чтобы учитывать все интересные GIF и внедренные видео на этой странице.</span><span class="sxs-lookup"><span data-stu-id="edcb9-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="edcb9-106">Изучение процесса проектирования для смешанной реальности может быть трудной, поскольку носитель не всегда преобразуется в процессы 2D-проектирования.</span><span class="sxs-lookup"><span data-stu-id="edcb9-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="edcb9-107">В корпорации Майкрософт мы создали бесплатное приложение для HoloLens 2, которое поможет вам понять основы разработки UX в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="edcb9-108">Уникальный подход к созданию подробно приложений, а также советы и рекомендации, позволяющие создавать привлекательные и невероятные приложения HoloLens.</span><span class="sxs-lookup"><span data-stu-id="edcb9-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="edcb9-109">Бесплатно скачайте приложение из Microsoft Store и узнайте от группы проектирования смешанной реальности Майкрософт!</span><span class="sxs-lookup"><span data-stu-id="edcb9-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="edcb9-110">Скачайте приложение разработки голограмм</span><span class="sxs-lookup"><span data-stu-id="edcb9-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Анимированный GIF-файл сцены с отслеживанием головной части в демонстрационной комнате конструирования](images/designing-holograms/demo-room.gif)

<span data-ttu-id="edcb9-112">*Проектирование демонстрационной комнаты с голограммами (также известной как кукол House)*</span><span class="sxs-lookup"><span data-stu-id="edcb9-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="edcb9-113">Разработка для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="edcb9-113">Designing for mixed reality</span></span>

<span data-ttu-id="edcb9-114">Как и многие из вас, я использовался для проектирования мобильных приложений.</span><span class="sxs-lookup"><span data-stu-id="edcb9-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="edcb9-115">Поступающие из 2D-мира, вы полностью пойдете на пространственные вычисления, где все будет в мире, было значительным сдвигом.</span><span class="sxs-lookup"><span data-stu-id="edcb9-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="edcb9-116">В смешанной реальности приложения больше не превышены на 2D-экран; на самом деле они почти свободны, помещаются в реальном мире и взаимодействуют с реальными объектами.</span><span class="sxs-lookup"><span data-stu-id="edcb9-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="edcb9-117">Для меня подключение трехмерных возможностей к традиционным процессам 2D-проектирования является наиболее сложным аспектом разработки смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="edcb9-118">В беседах с клиентами я буду слышать такие вещи, как «я знал, какие функции следует включить, и как их запустить.</span><span class="sxs-lookup"><span data-stu-id="edcb9-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="edcb9-119">Это код, который я могу проследить за документацией и учебниками, а также с опытом взаимодействия с пользователем?</span><span class="sxs-lookup"><span data-stu-id="edcb9-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="edcb9-120">Таким образом, многие функции, различные входные параметры, различные сценарии и физические среды, загружают ".</span><span class="sxs-lookup"><span data-stu-id="edcb9-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="edcb9-121">![Образ из семинара по проектированию HoloLens 2 в Сан – ](images/designing-holograms/workshop.jpeg)
 *образе из семинара по созданию hololens 2 в Сан — Франциско*</span><span class="sxs-lookup"><span data-stu-id="edcb9-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="edcb9-122">Возможность обучения</span><span class="sxs-lookup"><span data-stu-id="edcb9-122">An opportunity to teach</span></span>

<span data-ttu-id="edcb9-123">В первую очередь она не была очевидна, но отличная возможность была использована для изучения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="edcb9-124">Проектирование голограмм — это визуальное взаимодействие, которое описывает концепции и рекомендации по проектированию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="edcb9-125">Это просто и виртуальный преподаватель, демонстрирующий концепции проектирования смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="edcb9-126">Все это из-за третьей перспективы, в которой работа заплотно в своем собственном пространстве.</span><span class="sxs-lookup"><span data-stu-id="edcb9-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="edcb9-127">*Видеоролик о проектировании голограмм*</span><span class="sxs-lookup"><span data-stu-id="edcb9-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="edcb9-128">Изучение кукол дома</span><span class="sxs-lookup"><span data-stu-id="edcb9-128">Exploring the doll house</span></span>

<span data-ttu-id="edcb9-129">Кукол House — это виртуальное окружение, используемое в рамках всего приложения.</span><span class="sxs-lookup"><span data-stu-id="edcb9-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="edcb9-130">Среда представляет собой миниатюрную комнату 80 x 60 x 40-cm, которая содержит основные элементы, которые часто встречаются в большинстве комнат, таких как стены, лампы, мебель, таблица и телевизор.</span><span class="sxs-lookup"><span data-stu-id="edcb9-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="edcb9-131">Кукол House — это основной протагонист работы приложения, поэтому нам нужно убедиться, что он будет работать отлично в любой среде.</span><span class="sxs-lookup"><span data-stu-id="edcb9-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="edcb9-132">Представьте себе это небольшое демонстрационное место для визуализации всех видов концепций смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="edcb9-133">*Видео о поведении коррекции Доллхаусе*</span><span class="sxs-lookup"><span data-stu-id="edcb9-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="edcb9-134">1:1. прототипы VS 1:10</span><span class="sxs-lookup"><span data-stu-id="edcb9-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="edcb9-135">Первое предположение было в том, что в 1:1 демонстраций было бы удивительно, почти похоже на взгляд на реальный учитель.</span><span class="sxs-lookup"><span data-stu-id="edcb9-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="edcb9-136">Пользователь увидит все, что преподаватель видит в реальной масштабе жизни.</span><span class="sxs-lookup"><span data-stu-id="edcb9-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="edcb9-137">Однако мы сразу же поняли, что есть несколько проблем:</span><span class="sxs-lookup"><span data-stu-id="edcb9-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="edcb9-138">Большинство разработчиков запустит свои приложения в офисах или комнатах, меньших, чем демонстрационная комната, поэтому она не поместится.</span><span class="sxs-lookup"><span data-stu-id="edcb9-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="edcb9-139">Отображаются Аддитивные, то есть вся виртуальная среда будет переключаться по комнате пользователя.</span><span class="sxs-lookup"><span data-stu-id="edcb9-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="edcb9-140">Это может сбить с толку две таблицы, возможно, двойные Дивани и стены, которые не совпадают.</span><span class="sxs-lookup"><span data-stu-id="edcb9-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="edcb9-141">И худшей из всех виртуальных сред, сильно ограниченных полем представления.</span><span class="sxs-lookup"><span data-stu-id="edcb9-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="edcb9-142">Когда мы представили мини-1:10й масштаб, результат был очень привлекательным птицным представлением реалистичной комнаты.</span><span class="sxs-lookup"><span data-stu-id="edcb9-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="edcb9-143">Можно увидеть все, что было в любом из углов, в то же время.</span><span class="sxs-lookup"><span data-stu-id="edcb9-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="edcb9-144">Наиболее удивительно, что большинство инженеров-тестировщиков обнаружили его настолько, что гораздо более увлекательно, чтобы увидеть небольшую версию, а не переключаться обратно на шкалу 1:1.</span><span class="sxs-lookup"><span data-stu-id="edcb9-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="edcb9-145">Поэтому мы решили, что в действительности выделена версия 1:1, и вы не хотите избавиться от дополнительной работы, необходимой для адаптации пользовательского интерфейса и других аспектов приложения.</span><span class="sxs-lookup"><span data-stu-id="edcb9-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="edcb9-146">![Поле представления с 1:1 масштабом ](images/designing-holograms/1-1-scale.png)
 *поля представления с 1:1*</span><span class="sxs-lookup"><span data-stu-id="edcb9-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="edcb9-147">![Поле представления с 1:10 масштабом ](images/designing-holograms/1-10-scale.png)
 *поля представления с 1:10*</span><span class="sxs-lookup"><span data-stu-id="edcb9-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="edcb9-148">Использование записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="edcb9-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="edcb9-149">Одна из важнейших характеристик этого приложения — использование записи смешанной реальности для обучения и демонстрации концепций в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="edcb9-150">В Сан-Франциско Корпорация Майкрософт выпустила студию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="edcb9-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="edcb9-151">Корпорация Майкрософт также лицензирует эту технологию другим Studios, включая измерение аватара в Вашингтоне округ Колумбия, Метастаже в Лос-Анджелес, Dimension Studios в Лондоне, SK в Сеул и Волукап в Берлин.</span><span class="sxs-lookup"><span data-stu-id="edcb9-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="edcb9-152">Дополнительные сведения о [Studios записи смешанной реальности](https://www.microsoft.com/mixed-reality/capture-studios)можно найти здесь.</span><span class="sxs-lookup"><span data-stu-id="edcb9-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="edcb9-153">*Необработанный материал Даниэль Ескудеро с одной из камер 106 в смешанной реальности в студии в Сан Франциско.*</span><span class="sxs-lookup"><span data-stu-id="edcb9-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="edcb9-154">Процесс записи создает опорную сетку, нормальную работу и текстуру, которую можно передать в виде файлов OBJ/PNG для дальнейшей подготовки после производства или готовности к воспроизведению в виде сжатого MP4-файла H. 264.</span><span class="sxs-lookup"><span data-stu-id="edcb9-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="edcb9-155">Эти файлы можно импортировать в единые, нереальные, собственные и Вебкср проекты.</span><span class="sxs-lookup"><span data-stu-id="edcb9-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="edcb9-156">Файлы могут работать в Windows, iOS, Mac, Android, Magic LEAP и PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="edcb9-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="edcb9-157">*Проигрыватель записи, предназначенный для анализа MP4 со множественной, содержащих видео с аудио и внедренными сетками.*</span><span class="sxs-lookup"><span data-stu-id="edcb9-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="edcb9-158">Управление захватами и виртуальными объектами</span><span class="sxs-lookup"><span data-stu-id="edcb9-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="edcb9-159">Записи смешанной реальности создают виртуальные представления людей или животных, но иногда эти символы могут потребоваться для взаимодействия с другими виртуальными объектами.</span><span class="sxs-lookup"><span data-stu-id="edcb9-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="edcb9-160">В двух приведенных ниже примерах демонстрируются различные способы, с помощью которых мы работаем над этим для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="edcb9-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="edcb9-161">Корректировка головного взгляда</span><span class="sxs-lookup"><span data-stu-id="edcb9-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="edcb9-162">Корректировка хеадгазе позволяет перемещать заголовку захваченного человека во время выполнения, что означает, что для пользователя может быть снят захват.</span><span class="sxs-lookup"><span data-stu-id="edcb9-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="edcb9-163">В нашем случае мы использовали его для отображения поля представления и интересующего поля.</span><span class="sxs-lookup"><span data-stu-id="edcb9-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="edcb9-164">Ниже представлено перемещение gameobject, действующего в качестве цели для головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="edcb9-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="edcb9-165">Когда целевой объект перемещается из стороны в сторону, заголовком записи будет следующий элемент.</span><span class="sxs-lookup"><span data-stu-id="edcb9-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="edcb9-166">Мы использовали этот прием, чтобы убедиться в том, что бездействующий захват всегда будет иметь самые голограммы, размещенные в разных частях кукол дома.</span><span class="sxs-lookup"><span data-stu-id="edcb9-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Головка записи, перемещаемой во время выполнения, после целевого gameobject в Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="edcb9-168">*Головка записи перемещается во время выполнения после целевого gameobject в Unity.*</span><span class="sxs-lookup"><span data-stu-id="edcb9-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="edcb9-169">Синхронизация анимированных объектов</span><span class="sxs-lookup"><span data-stu-id="edcb9-169">Syncing Animated Objects</span></span>

<span data-ttu-id="edcb9-170">Второй — анимация объектов для синхронизации с перемещением записи.</span><span class="sxs-lookup"><span data-stu-id="edcb9-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="edcb9-171">В разных частях приложения мы импортировали последовательные OBJ-файлы определенного захвата каждые пять кадров.</span><span class="sxs-lookup"><span data-stu-id="edcb9-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="edcb9-172">OBJ-файлы в сцене, чтобы убедиться, что они соответствуют соответствующему кадру записи.</span><span class="sxs-lookup"><span data-stu-id="edcb9-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="edcb9-173">Это трудоемкий процесс анимации и кэйфраминг, но результат отлично.</span><span class="sxs-lookup"><span data-stu-id="edcb9-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="edcb9-174">Теперь можно увидеть, что запись смешанной реальности взаимодействует с неотслеживаемыми объектами.</span><span class="sxs-lookup"><span data-stu-id="edcb9-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Синхронизированная анимация между записью смешанной реальности и панелью пользовательского интерфейса](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="edcb9-176">*Синхронизированная анимация между записью смешанной реальности и панелью пользовательского интерфейса*</span><span class="sxs-lookup"><span data-stu-id="edcb9-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="edcb9-177">Пользовательский интерфейс творческого процесса</span><span class="sxs-lookup"><span data-stu-id="edcb9-177">UI creative process</span></span>

<span data-ttu-id="edcb9-178">Когда мы начали разработку пользовательского интерфейса, мы хотели продемонстрировать некоторые волшебия и возможности, которые должны быть предложены голограммами.</span><span class="sxs-lookup"><span data-stu-id="edcb9-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="edcb9-179">Простое отображение статических двумерных окон и текстовых полей не имеет смысла в трехмерном мире.</span><span class="sxs-lookup"><span data-stu-id="edcb9-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="edcb9-180">Многие из возможных вариантов просто не отображаются, так что прямо с начала мы решили отказаться от него и полностью использовать более holographic-трехмерное пространство.</span><span class="sxs-lookup"><span data-stu-id="edcb9-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="edcb9-181">Сначала мы начали добавлять некоторую толщину к панелям, значкам и текстовой информации.</span><span class="sxs-lookup"><span data-stu-id="edcb9-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="edcb9-182">Тем не менее, как пользователь увидит текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="edcb9-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="edcb9-183">Текстовые поля с изображениями, но здесь нет.</span><span class="sxs-lookup"><span data-stu-id="edcb9-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="edcb9-184">Мы проделали дальнейшее использование шейдеров набора средств Mixed Reality Toolkit (МРТК).</span><span class="sxs-lookup"><span data-stu-id="edcb9-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="edcb9-185">Шейдеры МРТК стали мощным средством, и мы использовали его функции трафарета для добавления отрицательной глубины к панелям.</span><span class="sxs-lookup"><span data-stu-id="edcb9-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="edcb9-186">Это означает, что вместо добавления элементов перед текстовым полем значки теперь отображаются позади прозрачной панели.</span><span class="sxs-lookup"><span data-stu-id="edcb9-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="edcb9-187">То, что я вижу как пользователь, — это то, что я просто не могу реплицировать в реальном мире, и именно здесь было запущено holographic-волшебное событие.</span><span class="sxs-lookup"><span data-stu-id="edcb9-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="edcb9-188">Кроме того, как пользователь не хочет читать, я делаю многое уже в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="edcb9-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="edcb9-189">Очевидно, что значки работают гораздо лучше, чем простой текст. чтобы предоставить еще более широкие рекомендации, я приступил к созданию набора анимированных объектов и аватаров, каждый из которых говорит о том, что выполняется в соответствующем сценарии и как он используется.</span><span class="sxs-lookup"><span data-stu-id="edcb9-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![Анимированный GIF-файл в интерактивной системе «holographic»](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="edcb9-191">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="edcb9-191">Core concepts</span></span>

<span data-ttu-id="edcb9-192">**Голографический кадр**</span><span class="sxs-lookup"><span data-stu-id="edcb9-192">**Holographic frame**</span></span>

![Анимированный GIF-файл пользователя, который просматривает доллхаусе с выделенным кадром holographic](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="edcb9-194">**Системы координат**</span><span class="sxs-lookup"><span data-stu-id="edcb9-194">**Coordinate systems**</span></span>

![Анимированный GIF-файл пользователя, который просматривает доллхаусе с выделенными системами координат](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="edcb9-196">**Отслеживание взгляда**</span><span class="sxs-lookup"><span data-stu-id="edcb9-196">**Eye tracking**</span></span>

![Анимированный GIF-файл пользователя, просматривая стационарные голограммы с выделенным лучом.](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="edcb9-198">**Визуализация и пространственное сопоставление для просмотра комнаты**</span><span class="sxs-lookup"><span data-stu-id="edcb9-198">**Room scan visualization and spatial mapping**</span></span>

![Анимированный GIF-файл всех поверхностей в сопоставляемом доллхаусе](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="edcb9-200">**Интерпретация сцены**</span><span class="sxs-lookup"><span data-stu-id="edcb9-200">**Scene understanding**</span></span>

![Анимированный GIF объектов в доллхаусе, который распознается](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="edcb9-202">**Указание и фиксация с помощью луча**</span><span class="sxs-lookup"><span data-stu-id="edcb9-202">**Point and commit with hand rays**</span></span>

![Анимированный GIF-файл, создающий свою руку с выделенным лучом](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="edcb9-204">«Попробуйте» в секундах</span><span class="sxs-lookup"><span data-stu-id="edcb9-204">"Try it out" moments</span></span>

<span data-ttu-id="edcb9-205">При проектировании голограмм рассматриваются концепции смешанной реальности, но они также позволяют опробовать их в своей комнате.</span><span class="sxs-lookup"><span data-stu-id="edcb9-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="edcb9-206">После некоторых из этих объяснений мы приостанавливали и кукол дома и в интерактивный момент.</span><span class="sxs-lookup"><span data-stu-id="edcb9-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="edcb9-207">Ниже приведены некоторые примеры интерактивных секунд.</span><span class="sxs-lookup"><span data-stu-id="edcb9-207">Here are some examples of those interactive moments:</span></span>

![Анимированный GIF-файл кадра отслеживания руки, отображающийся при обнаружении стрелок и при вводе поля представления](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="edcb9-209">*Кадр отслеживания руки, показывающий, когда обнаруживаются руки и когда они вводят в поле представления.*</span><span class="sxs-lookup"><span data-stu-id="edcb9-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![Анимированный GIF-файл для взаимодействия с конфликтующими Кристалс с помощью дальнего взаимодействия](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="edcb9-211">*Взаимодействие с конфликтующими Кристалс с помощью дальнего взаимодействия*</span><span class="sxs-lookup"><span data-stu-id="edcb9-211">*Interacting with colliding crystals through far interaction*</span></span>

![Анимированный GIF-файл для исследования близкого взаимодействия аффорданцес](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="edcb9-213">*Изучение практических принципов взаимодействия аффорданцес*</span><span class="sxs-lookup"><span data-stu-id="edcb9-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="edcb9-214">О команде</span><span class="sxs-lookup"><span data-stu-id="edcb9-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="edcb9-215"><b>Даниэль Ескудеро</b></span><span class="sxs-lookup"><span data-stu-id="edcb9-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="edcb9-216"><i>Ведущий технический дизайнер</i></span><span class="sxs-lookup"><span data-stu-id="edcb9-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="edcb9-217">«Лондон» является творческим директором по проектированию голограмм и в настоящее время работает как руководитель по проектированию в смешанной реальности корпорации Майкрософт в Сан-Франциско, и ранее был конструктором в одной из Studiosов смешанной реальности Майкрософт в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="edcb9-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="edcb9-218"><b>Мартен Веттиг</b></span><span class="sxs-lookup"><span data-stu-id="edcb9-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="edcb9-219"><i>Старший трехмерный исполнитель</i></span><span class="sxs-lookup"><span data-stu-id="edcb9-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="edcb9-220">Модель "Мартен" приводит трехмерную иллюстрацию и разработку пользовательского интерфейса для разработки голограмм и раньше была старшим трехмерным исполнителем на одном из Studiosов в смешанной реальности Microsoft Берлин.</span><span class="sxs-lookup"><span data-stu-id="edcb9-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="edcb9-221">Огромное спасибо за участие в группе проектирования "смешанная реальность" для совместного использования, а также в [теории объектов](https://objecttheory.com/) , чтобы стать важными участниками каждого этапа проекта.</span><span class="sxs-lookup"><span data-stu-id="edcb9-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="edcb9-222">Благодарим вас за удивительного, что для вашего увлеченности и исключительного взгляда на проектирование.</span><span class="sxs-lookup"><span data-stu-id="edcb9-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="edcb9-223">Скачайте приложение разработки голограмм</span><span class="sxs-lookup"><span data-stu-id="edcb9-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)