---
title: Пример использования. использование плоскости стабилизации для сокращения турбуленце
description: Использование плоскости стабилизации для уменьшения голографической турбулентности
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, голограммы, стабилизации, пример внедрения
ms.openlocfilehash: 4eb61cb37ef087dc5fbeb6b4ef6ca1c507719205
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691457"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a><span data-ttu-id="3fe22-104">Пример использования. использование плоскости стабилизации для сокращения турбуленце</span><span class="sxs-lookup"><span data-stu-id="3fe22-104">Case study - Using the stabilization plane to reduce holographic turbulence</span></span>

<span data-ttu-id="3fe22-105">Работа с голограммами может быть непростой.</span><span class="sxs-lookup"><span data-stu-id="3fe22-105">Working with holograms can be tricky.</span></span> <span data-ttu-id="3fe22-106">Тот факт, что вы можете перемещаться вокруг своего пространства и видеть самые голограммы из всех разных углов, обеспечивает уровень погружения, который нельзя получить с помощью обычного экрана компьютера.</span><span class="sxs-lookup"><span data-stu-id="3fe22-106">The fact that you can move around your space and see your holograms from all different angles provides a level of immersion that you can’t get with a normal computer screen.</span></span> <span data-ttu-id="3fe22-107">Благодаря хранению этих голограмм и постановке реалистичных выпусков, достижением как оборудование Microsoft HoloLens, так и интеллектуальное проектирование holographic приложений.</span><span class="sxs-lookup"><span data-stu-id="3fe22-107">Keeping these holograms in place and looking realistic is a technical feat accomplished by both the Microsoft HoloLens hardware and the intelligent design of holographic apps.</span></span>

## <a name="the-tech"></a><span data-ttu-id="3fe22-108">Технический</span><span class="sxs-lookup"><span data-stu-id="3fe22-108">The tech</span></span>

<span data-ttu-id="3fe22-109">Чтобы создать голограммы, так как они фактически совместно используют пространство, они должны отображаться правильно, без разделения цвета.</span><span class="sxs-lookup"><span data-stu-id="3fe22-109">To make holograms appear as though they're actually sharing the space with you, they should render properly, without color separation.</span></span> <span data-ttu-id="3fe22-110">Это достигается за счет встроенной технологии для оборудования HoloLens, которая сохраняет голограммы, привязанные к тому, что мы вызываем [плоскость стабилизации](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="3fe22-110">This is achieved, in part, by technology built-in to the HoloLens hardware which keeps holograms anchored on what we call a [stabilization plane](hologram-stability.md#reprojection).</span></span>

<span data-ttu-id="3fe22-111">Плоскость определяется точкой и нормальным, но так как мы всегда хотим, чтобы плоскость находилась на камере, мы просто работаем с установкой точки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-111">A plane is defined by a point and a normal, but since we always want the plane to face the camera, we're really just concerned with setting the plane's point.</span></span> <span data-ttu-id="3fe22-112">Мы можем сообщить HoloLens, что нужно сосредоточиться на обработке, чтобы обеспечить все привязку и стабильность, но как установить эту контрольную точку в зависимости от приложения, а также сделать или прервать работу приложения в соответствии с содержимым.</span><span class="sxs-lookup"><span data-stu-id="3fe22-112">We can tell HoloLens which point to focus its processing on to keep everything anchored and stable, but how to set this focus point is app-specific, and can make or break your app depending on the content.</span></span>

<span data-ttu-id="3fe22-113">В двух словах, самые голограммы лучше работают при правильном применении плоскости стабилизации, но на самом деле это зависит от типа создаваемого приложения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-113">In a nutshell, holograms work best when the stabilization plane is properly applied, but what that actually means depends on the type of application you’re creating.</span></span> <span data-ttu-id="3fe22-114">Давайте посмотрим, как некоторые из приложений, доступных в настоящее время для HoloLens, могут справиться с этой проблемой.</span><span class="sxs-lookup"><span data-stu-id="3fe22-114">Let’s take a look at how some of the apps currently available for HoloLens tackle this problem.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="3fe22-115">Сопутствующие ресурсы</span><span class="sxs-lookup"><span data-stu-id="3fe22-115">Behind the scenes</span></span>

<span data-ttu-id="3fe22-116">При разработке следующих приложений мы заметили, что когда мы не использовали плоскость, объекты были бы Sway, когда наш головной элемент переместился, и мы увидим выделение цветом с помощью быстрых или голограммных перемещений.</span><span class="sxs-lookup"><span data-stu-id="3fe22-116">When developing the following apps, we noticed that when we didn't use the plane, objects would sway when our head moved and we'd see color separation with quick head or hologram movements.</span></span> <span data-ttu-id="3fe22-117">В течение периода разработки мы узнали по пробной версии и ошибке, как лучше всего использовать плоскость стабилизации и как проектировать наши приложения по решению проблем, которые она не может исправить.</span><span class="sxs-lookup"><span data-stu-id="3fe22-117">Over the course of the development timeframe, we learned through trial and error how to best use the stabilization plane and how to design our apps around the problems that it can't fix.</span></span>

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a><span data-ttu-id="3fe22-118">Обозреватель Galaxy: стационарное содержимое, трехмерное интерактивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="3fe22-118">Galaxy Explorer: Stationary content, 3D interactivity</span></span>

<span data-ttu-id="3fe22-119">В сцене [Galaxy Explorer](../unity/galaxy-explorer.md) есть два основных элемента: основное представление содержимого целестиал и панель инструментов мелкого пользовательского интерфейса, которая следует за вашим взглядом.</span><span class="sxs-lookup"><span data-stu-id="3fe22-119">[Galaxy Explorer](../unity/galaxy-explorer.md) has two major elements in the scene: The main view of the celestial content and the small UI toolbar that follows your gaze.</span></span> <span data-ttu-id="3fe22-120">Для логики стабилизации мы взглянем на то, что текущий вектор взгляда пересекается в каждом кадре, чтобы определить, будет ли он найден на указанном уровне конфликтов.</span><span class="sxs-lookup"><span data-stu-id="3fe22-120">For the stabilization logic, we look at what your current gaze vector intersects with in each frame to determine if it hits anything on a specified collision layer.</span></span> <span data-ttu-id="3fe22-121">В этом случае нужные вам слои — планеты, поэтому если взгляд на планеты становится Планета, в нем размещается плоскость стабилизации.</span><span class="sxs-lookup"><span data-stu-id="3fe22-121">In this case, the layers we’re interested in are the planets, so if your gaze falls on a planet, the stabilization plane is placed there.</span></span> <span data-ttu-id="3fe22-122">Если ни один из объектов на целевом уровне конфликтов не достигнут, приложение использует дополнительный уровень "план B".</span><span class="sxs-lookup"><span data-stu-id="3fe22-122">If none of the objects in the target collision layer are hit, the app uses a secondary “plan B” layer.</span></span> <span data-ttu-id="3fe22-123">Если ничего не газед, плоскость стабилизации сохраняется на том же расстоянии, что и когда облаками на содержимом.</span><span class="sxs-lookup"><span data-stu-id="3fe22-123">If nothing is being gazed at, the stabilization plane is kept at the same distance as it was when gazing at the content.</span></span> <span data-ttu-id="3fe22-124">Средства пользовательского интерфейса выделены как мишень-плоскость, так как мы обнаружили переход между ближайшими и значительно уменьшили стабильность общей сцены.</span><span class="sxs-lookup"><span data-stu-id="3fe22-124">The UI tools are left out as a plane target as we found the jump between near and far reduced the stability of the overall scene.</span></span>

<span data-ttu-id="3fe22-125">Структура Galaxy Explorer хорошо подходит для обеспечения стабильной работы и снижения влияния цветоделения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-125">The design of Galaxy Explorer lends itself well to keeping things stable and reducing the effect of color separation.</span></span> <span data-ttu-id="3fe22-126">Пользователю рекомендуется проанализировать содержимое по орбите, а не перемещать его из стороны в сторону, и планеты на орбиту достаточно медленно, чтобы цветоделение не было заметным.</span><span class="sxs-lookup"><span data-stu-id="3fe22-126">The user is encouraged to walk around and orbit the content rather than move along it from side to side, and the planets are orbiting slowly enough that the color separation isn’t noticeable.</span></span> <span data-ttu-id="3fe22-127">Кроме того, сохраняется постоянная 60 кадров в кадре, что обеспечивает длительный способ предотвращения разделения цветов.</span><span class="sxs-lookup"><span data-stu-id="3fe22-127">Additionally, a constant 60 FPS is maintained, which goes a long way in preventing color separation from happening.</span></span>

<span data-ttu-id="3fe22-128">Чтобы проверить это самостоятельно, найдите файл с именем LSRPlaneModifier.cs в [коде обозревателя Galaxy на сайте GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).</span><span class="sxs-lookup"><span data-stu-id="3fe22-128">To check this out yourself, look for a file called LSRPlaneModifier.cs in the [Galaxy Explorer code on GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).</span></span>

### <a name="holostudio-stationary-content-with-a-ui-focus"></a><span data-ttu-id="3fe22-129">Холостудио: стационарное содержимое с фокусом пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="3fe22-129">HoloStudio: Stationary content with a UI focus</span></span>

<span data-ttu-id="3fe22-130">В Холостудио вы тратите большую часть времени на просмотр той же модели, над которой вы работаете.</span><span class="sxs-lookup"><span data-stu-id="3fe22-130">In HoloStudio, you spend most of your time looking at the same model you’re working on.</span></span> <span data-ttu-id="3fe22-131">Ваше взгляд не помещает значительных сумм, за исключением случаев, когда вы выберете новое средство или хотите перейти к пользовательскому интерфейсу, так что мы можем не усложнять логику настройки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-131">Your gaze doesn’t move a significant amount, except for when you select a new tool or want to navigate the UI, so we can keep the plane setting logic simple.</span></span> <span data-ttu-id="3fe22-132">При просмотре пользовательского интерфейса плоскость задается любым элементом пользовательского интерфейса, к которому будет привязан взгляд.</span><span class="sxs-lookup"><span data-stu-id="3fe22-132">When looking at the UI, the plane is set to whatever UI element your gaze snaps to.</span></span> <span data-ttu-id="3fe22-133">При просмотре модели плоскость представляет собой установленное расстояние, соответствующее расстоянию по умолчанию между вами и моделью.</span><span class="sxs-lookup"><span data-stu-id="3fe22-133">When looking at the model, the plane is a set distance away, corresponding with the default distance between you and the model.</span></span>

![Плоскость стабилизации, отображаемая в Холостудио по мере того, как пользователь загляните на кнопку "Главная"](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a><span data-ttu-id="3fe22-135">Холотаур и 3D Viewer: стационарное содержимое с анимацией и фильмами</span><span class="sxs-lookup"><span data-stu-id="3fe22-135">HoloTour and 3D Viewer: Stationary content with animation and movies</span></span>

<span data-ttu-id="3fe22-136">В средстве просмотра Холотаур и 3D вы видите анимированный объект одиночные или фильм с трехмерными эффектами, добавленными поверх него.</span><span class="sxs-lookup"><span data-stu-id="3fe22-136">In HoloTour and 3D Viewer, you’re looking at a solitary animated object or movie with 3D effects added on top of it.</span></span> <span data-ttu-id="3fe22-137">Для стабилизации в этих приложениях выбрано то, что вы сейчас просматриваете.</span><span class="sxs-lookup"><span data-stu-id="3fe22-137">The stabilization in these apps is set to whatever you’re currently viewing.</span></span>

<span data-ttu-id="3fe22-138">Холотаур также предотвращает слишком далекое от вашего виртуального мира, перемещаясь с вас вместо того, чтобы направлять их в фиксированное расположение.</span><span class="sxs-lookup"><span data-stu-id="3fe22-138">HoloTour also prevents you from straying too far away from your virtual world by having it move with you instead of staying in a fixed location.</span></span> <span data-ttu-id="3fe22-139">Это гарантирует, что вы не получите достаточно места от других голограмм, чтобы избежать проблем со стабильностью в.</span><span class="sxs-lookup"><span data-stu-id="3fe22-139">This ensures that you won’t get far enough away from other holograms for stability issues to creep in.</span></span>

![В этом примере из Холотаур в качестве плоскости стабилизации был установлен этот ролик из Хадриан Pantheon.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a><span data-ttu-id="3fe22-141">Робораид: динамическое содержимое и взаимодействие с окружающей средой</span><span class="sxs-lookup"><span data-stu-id="3fe22-141">RoboRaid: Dynamic content and environmental interactions</span></span>

<span data-ttu-id="3fe22-142">Настройка плоскости стабилизации в Робораид на удивление непроста, несмотря на то, что приложение требует наиболее внезапного перемещения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-142">Setting the stabilization plane in RoboRaid is surprisingly simple, despite being the app that requires the most sudden movement.</span></span> <span data-ttu-id="3fe22-143">Плоскость предназначена для того, чтобы прикрепить к стенам или окружающим объектам и направляться на фиксированную дистанцию перед вами, если у вас далеко не хватает.</span><span class="sxs-lookup"><span data-stu-id="3fe22-143">The plane is geared towards sticking to the walls or the surrounding objects and will float at a fixed distance in front of you when you’re far enough away from them.</span></span>

<span data-ttu-id="3fe22-144">Робораид был разработан с учетом плоскости стабилизации.</span><span class="sxs-lookup"><span data-stu-id="3fe22-144">RoboRaid was designed with the stabilization plane in mind.</span></span> <span data-ttu-id="3fe22-145">Ретикле, который перемещает большинство элементов с момента блокировки, обходит это с помощью красного и синего цветов, что приводит к уменьшению любого суперсовременные цвета.</span><span class="sxs-lookup"><span data-stu-id="3fe22-145">The reticle, which moves the most since it’s head-locked, circumvents this by using only red and blue which minimizes any color bleeding.</span></span> <span data-ttu-id="3fe22-146">Он также содержит небольшой уровень глубины между частями, что позволяет свести к минимуму любой цветовой выход, который мог бы произойти путем маскирования с уже ожидаемым фокусировки эффектом.</span><span class="sxs-lookup"><span data-stu-id="3fe22-146">It also contains a small bit of depth between the pieces, minimizing any color bleed that would occur by masking it with an already expected parallax effect.</span></span> <span data-ttu-id="3fe22-147">Роботы не перемещаются очень быстро и передаются только короткие расстояния через регулярные интервалы.</span><span class="sxs-lookup"><span data-stu-id="3fe22-147">The robots don’t move very quickly and only travel short distances in regular intervals.</span></span> <span data-ttu-id="3fe22-148">Они обычно находятся на 2 метрах перед вами, где стабилизации задается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3fe22-148">They tend to stay around 2 meters in front of you, where the stabilization is set by default.</span></span>

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a><span data-ttu-id="3fe22-149">Фрагменты и Титови Конкер: динамическое содержимое с участием в окружающей среде</span><span class="sxs-lookup"><span data-stu-id="3fe22-149">Fragments and Young Conker: Dynamic content with environmental interaction</span></span>

<span data-ttu-id="3fe22-150">В асобо Studio на C++ фрагменты и Титов Конкер используют другой подход к настройке плоскости стабилизации.</span><span class="sxs-lookup"><span data-stu-id="3fe22-150">Written by Asobo Studio in C++, Fragments and Young Conker take a different approach to setting the stabilization plane.</span></span> <span data-ttu-id="3fe22-151">Интересующие вас точки (достопримечательности) определяются в коде и упорядочиваются с точки зрения приоритета.</span><span class="sxs-lookup"><span data-stu-id="3fe22-151">Points of interest (POI) are defined in the code and ordered in terms of priority.</span></span> <span data-ttu-id="3fe22-152">Интереса — это содержимое в игре, например модель Конкер в Титов Конкер, меню, надежде ретикле и логотипы.</span><span class="sxs-lookup"><span data-stu-id="3fe22-152">POIs are in-game content such as the Conker model in Young Conker, menus, the aiming reticle, and logos.</span></span> <span data-ttu-id="3fe22-153">Интереса пересекается с помощью взгляда пользователя, а плоскость устанавливается в центр объекта с наивысшим приоритетом.</span><span class="sxs-lookup"><span data-stu-id="3fe22-153">The POIs are intersected by the user’s gaze and the plane is set to the center of the object with the highest priority.</span></span> <span data-ttu-id="3fe22-154">Если пересечение не выполняется, для плоскости задается расстояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3fe22-154">If no intersection occurs, the plane is set to the default distance.</span></span>

<span data-ttu-id="3fe22-155">Фрагменты и Конкеры также размещают слишком далеко от голограмм, приостанавливая приложение, если вы перейдете за пределы того, что ранее проверялось в качестве пространства для воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-155">Fragments and Young Conker also design around you straying too far from the holograms by pausing the app if you move outside of what’s been previously scanned as your play space.</span></span> <span data-ttu-id="3fe22-156">Таким образом, они сохраняют свои границы, чтобы обеспечить наиболее устойчивый опыт работы.</span><span class="sxs-lookup"><span data-stu-id="3fe22-156">As such, they keep you within the boundaries that are found to provide the most stable experience.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="3fe22-157">Попробуйте сами</span><span class="sxs-lookup"><span data-stu-id="3fe22-157">Do it yourself</span></span>

<span data-ttu-id="3fe22-158">Если у вас есть HoloLens и вы хотите поэкспериментировать с концепциями в этой статье, вы можете скачать тестовую сцену и испытать приведенные ниже упражнения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-158">If you have a HoloLens and would like to play around with the concepts within this article, you can download a test scene and try out the exercises below.</span></span> <span data-ttu-id="3fe22-159">Он использует встроенный API гизмо Unity и должен помочь визуализировать место установки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-159">It uses Unity’s built-in gizmo API and should help you visualize where your plane is being set.</span></span> <span data-ttu-id="3fe22-160">Этот код также использовался для захвата снимков экрана в нашем примере.</span><span class="sxs-lookup"><span data-stu-id="3fe22-160">This code was also used to capture the screenshots in this case study.</span></span>
1. <span data-ttu-id="3fe22-161">Синхронизируйте последнюю версию [микседреалититулкит-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="3fe22-161">Sync the latest version of [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span>
2. <span data-ttu-id="3fe22-162">Откройте сцену [холотулкит-ексамплес/Utilities/сцены/стабилизатионпланесеттинг. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) .</span><span class="sxs-lookup"><span data-stu-id="3fe22-162">Open the [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) scene.</span></span>
3. <span data-ttu-id="3fe22-163">Создайте и настройте созданный проект.</span><span class="sxs-lookup"><span data-stu-id="3fe22-163">Build and configure the generated project.</span></span>
4. <span data-ttu-id="3fe22-164">Запустите на устройстве.</span><span class="sxs-lookup"><span data-stu-id="3fe22-164">Run on your device.</span></span>

### <a name="exercise-1"></a><span data-ttu-id="3fe22-165">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="3fe22-165">Exercise 1</span></span>

<span data-ttu-id="3fe22-166">Вы увидите несколько белых точек на разных ориентациях.</span><span class="sxs-lookup"><span data-stu-id="3fe22-166">You'll see several white dots around you at different orientations.</span></span> <span data-ttu-id="3fe22-167">Перед вами вы увидите три точки с различной глубиной.</span><span class="sxs-lookup"><span data-stu-id="3fe22-167">In front of you, you’ll see three dots at different depths.</span></span> <span data-ttu-id="3fe22-168">Коснитесь Air, чтобы изменить точку, для которой задана плоскость.</span><span class="sxs-lookup"><span data-stu-id="3fe22-168">Air tap to change which dot the plane is set to.</span></span> <span data-ttu-id="3fe22-169">В этом упражнении, а также для других двух точек переместитесь вокруг своего пространства, пока облаками в точках.</span><span class="sxs-lookup"><span data-stu-id="3fe22-169">For this exercise, and for the other two, move around your space while gazing at the dots.</span></span> <span data-ttu-id="3fe22-170">Превратите заголовок влево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="3fe22-170">Turn your head left, right, up, and down.</span></span> <span data-ttu-id="3fe22-171">Продвигайтесь ближе к точкам и дальше от нее.</span><span class="sxs-lookup"><span data-stu-id="3fe22-171">Move closer to and farther from the dots.</span></span> <span data-ttu-id="3fe22-172">Посмотрите, как они реагируют, когда для плоскости стабилизации заданы разные целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="3fe22-172">See how they react when the stabilization plane is set to different targets.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="3fe22-173">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="3fe22-173">Exercise 2</span></span>

<span data-ttu-id="3fe22-174">Теперь перемещайтесь вправо, пока не увидите две точки перемещения, один осЦиллатинг на горизонтальном пути и один на вертикальном пути.</span><span class="sxs-lookup"><span data-stu-id="3fe22-174">Now, turn to your right until you see two moving dots, one oscillating on a horizontal path and one on a vertical path.</span></span> <span data-ttu-id="3fe22-175">Опять же, Air коснитесь, чтобы изменить точку, для которой задана плоскость.</span><span class="sxs-lookup"><span data-stu-id="3fe22-175">Once again, air-tap to change which dot the plane is set to.</span></span> <span data-ttu-id="3fe22-176">Обратите внимание, как уменьшается цветоделение и отображается на точке, подключенной к плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-176">Notice how color separation is lessened and appears on the dot that is connected to the plane.</span></span> <span data-ttu-id="3fe22-177">Коснитесь еще раз, чтобы использовать скорость точки в функции настройки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-177">Tap again to use the dot’s velocity in the plane setting function.</span></span> <span data-ttu-id="3fe22-178">Этот параметр дает указание объекту HoloLens о предполагаемом перемещении объекта.</span><span class="sxs-lookup"><span data-stu-id="3fe22-178">This parameter gives a hint to HoloLens about the object’s intended motion.</span></span> <span data-ttu-id="3fe22-179">Важно помнить, когда использовать эту возможность, как можно заметить, когда скорость используется в одной точке, другая точка перемещения будет показывать больше цветов.</span><span class="sxs-lookup"><span data-stu-id="3fe22-179">It’s important to know when to use this, as you’ll notice when velocity is used on one dot, the other moving dot will show greater color separation.</span></span> <span data-ttu-id="3fe22-180">Помните об этом при проектировании приложений — наличие согласованного потока движения объектов может помочь предотвратить появление артефактов.</span><span class="sxs-lookup"><span data-stu-id="3fe22-180">Keep this in mind when designing your apps—having a cohesive flow to the motion of your objects can help prevent artifacts from appearing.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="3fe22-181">Упражнение 3</span><span class="sxs-lookup"><span data-stu-id="3fe22-181">Exercise 3</span></span>

<span data-ttu-id="3fe22-182">Снова перейдите к вам, пока не появится новая конфигурация точек.</span><span class="sxs-lookup"><span data-stu-id="3fe22-182">Turn to your right once more until you see a new configuration of dots.</span></span> <span data-ttu-id="3fe22-183">В этом случае есть точки на расстоянии и одна точка в начале и в конце.</span><span class="sxs-lookup"><span data-stu-id="3fe22-183">In this case, there are dots in the distance and one dot spiraling in and out in front of them.</span></span> <span data-ttu-id="3fe22-184">Air коснитесь, чтобы изменить точку, для которой задана плоскость, чередование точек в обратном и в точке движения.</span><span class="sxs-lookup"><span data-stu-id="3fe22-184">Air tap to change which dot the plane is set to, alternating between the dots in the back and the dot in motion.</span></span> <span data-ttu-id="3fe22-185">Обратите внимание, что Настройка расположения плоскости и скорости для точки спирали делает артефакты видимыми везде.</span><span class="sxs-lookup"><span data-stu-id="3fe22-185">Notice how setting the plane position and the velocity to that of the spiraling dot makes artifacts appear everywhere.</span></span>

<span data-ttu-id="3fe22-186">**Советы**</span><span class="sxs-lookup"><span data-stu-id="3fe22-186">**Tips**</span></span>
* <span data-ttu-id="3fe22-187">Постарайтесь упростить логику настройки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-187">Keep your plane setting logic simple.</span></span> <span data-ttu-id="3fe22-188">Как вы уже видели, для создания иммерсивного интерфейса не требуется использовать сложные алгоритмы настройки плоскости.</span><span class="sxs-lookup"><span data-stu-id="3fe22-188">As you’ve seen, you don’t need complex plane setting algorithms to make an immersive experience.</span></span> <span data-ttu-id="3fe22-189">Плоскость стабилизации — только одна часть головоломки.</span><span class="sxs-lookup"><span data-stu-id="3fe22-189">The stabilization plane is only one piece of the puzzle.</span></span>
* <span data-ttu-id="3fe22-190">По возможности всегда передвигайте плоскость между целями.</span><span class="sxs-lookup"><span data-stu-id="3fe22-190">When at all possible, always move the plane between targets smoothly.</span></span> <span data-ttu-id="3fe22-191">Мгновенное переключение удаленных целевых объектов может привести к невозможности визуального нарушения сцены.</span><span class="sxs-lookup"><span data-stu-id="3fe22-191">Instantly switching distant targets can visually disrupt the scene.</span></span>
* <span data-ttu-id="3fe22-192">Попробуйте использовать параметр в логике настройки плоскости для блокировки на очень конкретный целевой объект.</span><span class="sxs-lookup"><span data-stu-id="3fe22-192">Consider having an option in your plane setting logic to lock onto a very specific target.</span></span> <span data-ttu-id="3fe22-193">Таким образом, при необходимости плоскость может быть заблокирована на объекте, таком как логотип или титульный экран.</span><span class="sxs-lookup"><span data-stu-id="3fe22-193">That way, you can have the plane locked on an object, such as a logo or title screen, if needed.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="3fe22-194">Об авторе</span><span class="sxs-lookup"><span data-stu-id="3fe22-194">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3fe22-195"><b>Бен Струкус</b></span><span class="sxs-lookup"><span data-stu-id="3fe22-195"><b>Ben Strukus</b></span></span><br><span data-ttu-id="3fe22-196">Инженер по программному обеспечению @Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fe22-196">Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="3fe22-197">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3fe22-197">See also</span></span>
* [<span data-ttu-id="3fe22-198">100. Основы смешанной реальности: начало работы с Unity</span><span class="sxs-lookup"><span data-stu-id="3fe22-198">MR Basics 100: Getting started with Unity</span></span>](../unity/tutorials/holograms-100.md)
* [<span data-ttu-id="3fe22-199">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="3fe22-199">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="3fe22-200">Стабильность голограммы</span><span class="sxs-lookup"><span data-stu-id="3fe22-200">Hologram stability</span></span>](hologram-stability.md)