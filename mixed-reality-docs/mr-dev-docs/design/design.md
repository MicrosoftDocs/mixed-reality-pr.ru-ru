---
title: Начните проектировать и создавать прототипы
description: Если вы готовы создать что-нибудь, изучите основные понятия, необходимые для начала разработки и создания прототипов.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, обнаружение, распространение, указатель, целевая страница, проектирование, разработка, учебники, примеры приложений, основы, примеры использования, ресурсы, практические руководства по HoloLens, проекты с открытым кодом, основные понятия, взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f4a4ea50c45263f18079da76dd8dfd5f31e2af44
ms.sourcegitcommit: 44d0f2873c75003caf9d8d244ceaeb3faa89df63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2021
ms.locfileid: "98110452"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="82e0e-104">Начните проектировать и создавать прототипы</span><span class="sxs-lookup"><span data-stu-id="82e0e-104">Start designing and prototyping</span></span>

![фрагмент проекта смешанной реальности](images/design-hero-image.png)

<span data-ttu-id="82e0e-106">Приложения смешанной реальности на сегодня не имеют аналогий, а их разработка требует значительных усилий.</span><span class="sxs-lookup"><span data-stu-id="82e0e-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="82e0e-107">Ведь вам не только приходится учитывать разные сочетания реальных и виртуальных миров, но и обеспечиваемые ими способы взаимодействия с пользователями.</span><span class="sxs-lookup"><span data-stu-id="82e0e-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new user experiences they afford.</span></span> <span data-ttu-id="82e0e-108">Так как смешанная реальность — это очень обширная тема, мы выделили несколько важных аспектов проектирования и изложили их ниже в виде контрольных точек.</span><span class="sxs-lookup"><span data-stu-id="82e0e-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="82e0e-109">Мы приводим их в определенном порядке, но, если вы уже знакомы со смешанной реальностью, вы можете изучать их в любой последовательности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span> 

<span data-ttu-id="82e0e-110">Посмотрите наше видео с обзором проектирования, чтобы начать работу:</span><span class="sxs-lookup"><span data-stu-id="82e0e-110">Take a look at our design overview video to get started:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a><span data-ttu-id="82e0e-111">Этапы проектирования</span><span class="sxs-lookup"><span data-stu-id="82e0e-111">Design checkpoints</span></span>

<span data-ttu-id="82e0e-112">Используйте следующие контрольные точки, чтобы реализовать свои идеи и концепции в мире смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-112">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="82e0e-113">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="82e0e-113">1. Getting started</span></span>

<span data-ttu-id="82e0e-114">Как и со всеми обширными темами, ознакомление с проектированием приложений смешанной реальности начинается с основ.</span><span class="sxs-lookup"><span data-stu-id="82e0e-114">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="82e0e-115">Мы рекомендуем вам ознакомиться со статьями [Что такое смешанная реальность](../discover/mixed-reality.md) и [Что такое голограмма?](../discover/hologram.md), чтобы вы поняли, как проектируется иммерсивное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="82e0e-115">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="82e0e-116">После этого можете приступать к изучению принципов проектирования для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-116">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![Начало работы с GIF в приложении для создания голограмм](images/HandTracking2.gif)

|  <span data-ttu-id="82e0e-118">Контрольная точка</span><span class="sxs-lookup"><span data-stu-id="82e0e-118">Checkpoint</span></span>  |  <span data-ttu-id="82e0e-119">Результат</span><span class="sxs-lookup"><span data-stu-id="82e0e-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="82e0e-120">Расширение процесса разработки</span><span class="sxs-lookup"><span data-stu-id="82e0e-120">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="82e0e-121">Сведения о процессе проектирования для Смешанной реальности, которыми делятся дизайнеры из Майкрософт и других компаний.</span><span class="sxs-lookup"><span data-stu-id="82e0e-121">Get a first-hand look at design process for Mixed Reality, gathered from designers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="82e0e-122">Типы приложений смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="82e0e-122">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="82e0e-123">Определение того, какого именно типа приложение вы хотите создать.</span><span class="sxs-lookup"><span data-stu-id="82e0e-123">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="82e0e-124">Приложение для создания голограмм</span><span class="sxs-lookup"><span data-stu-id="82e0e-124">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="82e0e-125">Изучите основные принципы разработки пользовательского интерфейса смешанной реальности на практике, а также получите советы и рекомендации для создания впечатляющих приложений HoloLens (доступно для скачивания в Microsoft Store в разделе HoloLens 2).</span><span class="sxs-lookup"><span data-stu-id="82e0e-125">Learn the fundamentals of Mixed Reality UX Design by experiencing with behaviors, tips, and recommendations for creating amazing HoloLens apps (available for download from Microsoft Store in HoloLens 2)</span></span> |
| [<span data-ttu-id="82e0e-126">Центр с примерами MRTK</span><span class="sxs-lookup"><span data-stu-id="82e0e-126">MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | <span data-ttu-id="82e0e-127">Изучите популярные пространственные взаимодействия и базовые блоки пользовательского интерфейса для смешанной реальности (доступно для скачивания из Microsoft Store в HoloLens 2).</span><span class="sxs-lookup"><span data-stu-id="82e0e-127">Experience common spatial interactions and UX building blocks for Mixed Reality (available for download from Microsoft Store in HoloLens 2)</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="82e0e-128">2. Основные понятия</span><span class="sxs-lookup"><span data-stu-id="82e0e-128">2. Core concepts</span></span>

<span data-ttu-id="82e0e-129">Независимо от того, выполняете ли вы разработку для виртуальной или дополненной реальности, существует несколько основных концепций, которые применяются к проектированию удобных иммерсивных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="82e0e-129">Whether you're developing for VR or AR, there are several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="82e0e-130">Понимание точки зрения пользователя, позиционирование объектов и обеспечение комфорта и безопасности являются вашими основными приоритетами на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="82e0e-130">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="82e0e-131">Изучив этот раздел, вы сможете с уверенностью проектировать взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="82e0e-131">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![Изображение с примерами основных концепций](images/fragments-750px.jpg)

|  <span data-ttu-id="82e0e-133">Концепция</span><span class="sxs-lookup"><span data-stu-id="82e0e-133">Concept</span></span>  |  <span data-ttu-id="82e0e-134">Результат</span><span class="sxs-lookup"><span data-stu-id="82e0e-134">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="82e0e-135">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="82e0e-135">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="82e0e-136">Понимание того, как пользователи видят ваше содержимое, наложенное на реальный мир, при использовании гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="82e0e-136">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="82e0e-137">Системы координат</span><span class="sxs-lookup"><span data-stu-id="82e0e-137">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="82e0e-138">Сведения о том, как позиционировать голограммы в значимых местах мира, будь то физическое помещение или созданная вами виртуальная область.</span><span class="sxs-lookup"><span data-stu-id="82e0e-138">Learn how to position holograms in meaningful places in the world, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="82e0e-139">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="82e0e-139">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="82e0e-140">Реализация привязки объектов в мире пользователя и использование физических поверхностей из реального мира.</span><span class="sxs-lookup"><span data-stu-id="82e0e-140">Anchor objects in the user's world and take advantage of real world's physical surfaces</span></span> |
| [<span data-ttu-id="82e0e-141">Вопросы комфорта</span><span class="sxs-lookup"><span data-stu-id="82e0e-141">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="82e0e-142">Обеспечение комфорта и безопасности пользователей за счет создания и представления иммерсивного содержимого способами, которые имитируют реальный мир.</span><span class="sxs-lookup"><span data-stu-id="82e0e-142">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="82e0e-143">3. Проектирование взаимодействия</span><span class="sxs-lookup"><span data-stu-id="82e0e-143">3. Interaction design</span></span>

<span data-ttu-id="82e0e-144">Какой бы красивой визуально и иммерсивной не была виртуальная реальность, без возможностей взаимодействия она бесполезна.</span><span class="sxs-lookup"><span data-stu-id="82e0e-144">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="82e0e-145">В этом разделе рассматриваются основные модели взаимодействия, контроллеры движений и жестов, использование голосового ввода, а также сбор данных об отслеживании взгляда пользователей.</span><span class="sxs-lookup"><span data-stu-id="82e0e-145">This section will walk you through basic interaction models, hand and motion controllers, voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="82e0e-146">Изучив этот раздел, вы будете знать достаточно о проектировании, чтобы создавать пользовательские взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="82e0e-146">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![Факторы, влияющие на проектирование взаимодействия](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="82e0e-148">Концепция</span><span class="sxs-lookup"><span data-stu-id="82e0e-148">Concept</span></span>  |  <span data-ttu-id="82e0e-149">Результат</span><span class="sxs-lookup"><span data-stu-id="82e0e-149">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="82e0e-150">Модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="82e0e-150">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="82e0e-151">Предоставление пользователям возможности инстинктивных взаимодействий посредством рук, взгляда и голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="82e0e-151">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="82e0e-152">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="82e0e-152">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="82e0e-153">Сведения о том, как взаимодействовать с голограммами на близком расстоянии с помощью рук или на дальнем расстоянии с помощью точных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="82e0e-153">Learn how to interact with holograms at close range with a user' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="82e0e-154">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="82e0e-154">Voice input</span></span>](voice-input.md) | <span data-ttu-id="82e0e-155">Использование голосовых команд в качестве средства ввода в иммерсивных приложениях для управления голограммами и средами.</span><span class="sxs-lookup"><span data-stu-id="82e0e-155">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="82e0e-156">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="82e0e-156">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="82e0e-157">Добавление нового уровня понимания контекста и намерений человека в голографическом взаимодействии с учетом информации о том, куда смотрят пользователи.</span><span class="sxs-lookup"><span data-stu-id="82e0e-157">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="82e0e-158">4. Элементы пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="82e0e-158">4. User experience elements</span></span>

<span data-ttu-id="82e0e-159">Освоив базовые взаимодействия, вы можете сфокусироваться на особенностях элементов пользовательского интерфейса и способах их адаптации к уникальным средам смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-159">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="82e0e-160">Вы узнаете о распространенных моделях поведения, проектировании активов, масштабировании объектов и типографии, что поможет вам сделать приложения максимально интуитивно понятными для пользователей.</span><span class="sxs-lookup"><span data-stu-id="82e0e-160">You'll cover common behaviors, asset design, object scaling, and typography, while making the experience intuitive for your users.</span></span> <span data-ttu-id="82e0e-161">Этот раздел завершает официальные рекомендации по проектированию для смешанной реальности, но вы можете воспользоваться дополнительными ресурсами в разделе [Дальнейшие действия](#whats-next).</span><span class="sxs-lookup"><span data-stu-id="82e0e-161">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![Элементы взаимодействия с пользователем](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="82e0e-163">Концепция</span><span class="sxs-lookup"><span data-stu-id="82e0e-163">Concept</span></span>  |  <span data-ttu-id="82e0e-164">Результат</span><span class="sxs-lookup"><span data-stu-id="82e0e-164">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="82e0e-165">Распространенные элементы управления и режимы поведения</span><span class="sxs-lookup"><span data-stu-id="82e0e-165">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="82e0e-166">Изучение часто используемых пространственных взаимодействий и стандартных блоков пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="82e0e-166">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="82e0e-167">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="82e0e-167">Color, light, and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="82e0e-168">Проектирование качественных ресурсов для смешанной реальности, которые учитывают цвет, освещение и материал.</span><span class="sxs-lookup"><span data-stu-id="82e0e-168">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="82e0e-169">Масштабирование объектов</span><span class="sxs-lookup"><span data-stu-id="82e0e-169">Object scale</span></span>](scale.md) | <span data-ttu-id="82e0e-170">Внедрение как можно большего числа визуальных подсказок (из реального мира), которые помогут пользователям понять, где находятся объекты, насколько они велики и из чего они сделаны.</span><span class="sxs-lookup"><span data-stu-id="82e0e-170">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="82e0e-171">Оформление текста</span><span class="sxs-lookup"><span data-stu-id="82e0e-171">Typography</span></span>](typography.md) | <span data-ttu-id="82e0e-172">Использование четкого читаемого текста в трехмерном пространстве для отображения важной информации.</span><span class="sxs-lookup"><span data-stu-id="82e0e-172">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="82e0e-173">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="82e0e-173">What's next?</span></span>

<span data-ttu-id="82e0e-174">Проектировщику всегда будет чем заняться, особенно при изучении создания иммерсивных взаимодействий в новой парадигме.</span><span class="sxs-lookup"><span data-stu-id="82e0e-174">A designer's job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="82e0e-175">Приведенные ниже разделы предназначены для более опытных проектировщиков. Они включают сведения о разработке для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-175">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="82e0e-176">Эти темы и ресурсы не имеют определенного порядка, поэтому вы можете изучать их в любой последовательности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-176">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="82e0e-177">Выбор варианта создания прототипа</span><span class="sxs-lookup"><span data-stu-id="82e0e-177">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
       <span data-ttu-id="82e0e-178">[![Дополнительные сведения о Unity](images/logo-unity.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="82e0e-178">[![Learn Unity](images/logo-unity.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="82e0e-179">**[Дополнительные сведения о Unity](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-179">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="82e0e-180">Узнайте, как создавать интерактивные интерфейсы с помощью Unity.</span><span class="sxs-lookup"><span data-stu-id="82e0e-180">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="82e0e-181">Научитесь этому, выполнив процесс с начала и до конца.</span><span class="sxs-lookup"><span data-stu-id="82e0e-181">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="82e0e-182">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="82e0e-182">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="82e0e-183">**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-183">**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span></span><br>  
        <span data-ttu-id="82e0e-184">Благодаря пространственному взаимодействию и стандартным блокам пользовательского интерфейса, вы можете быстро начать проектирование и разработку смешанной реальности с помощью Unity.</span><span class="sxs-lookup"><span data-stu-id="82e0e-184">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="82e0e-185">[![Лаборатории проектирования смешанной реальности](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="82e0e-185">[![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="82e0e-186">**[Лаборатории проектирования смешанной реальности](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-186">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span></span><br>  
        <span data-ttu-id="82e0e-187">Получите примеры приложений, демонстрирующие использование стандартных блоков МРТК для создания привлекательных интерфейсов смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-187">Get sample apps that show you how to use MRTK's building blocks to create beautiful mixed reality experiences.</span></span>
    :::column-end:::        
    :::column:::    
        <span data-ttu-id="82e0e-188">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="82e0e-188">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="82e0e-189">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-189">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="82e0e-190">Разработка для виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-190">Design for VR.</span></span> <span data-ttu-id="82e0e-191">Microsoft Maquette делает создание пространственных прототипов более простым, быстрым и иммерсивным.</span><span class="sxs-lookup"><span data-stu-id="82e0e-191">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a><span data-ttu-id="82e0e-192">Другие ресурсы</span><span class="sxs-lookup"><span data-stu-id="82e0e-192">Other resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="82e0e-193">[![Изучение основ](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="82e0e-193">[![Understand the basics](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="82e0e-194">**[Изучение основ](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-194">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="82e0e-195">Получите более полное представление о том, что определяет смешанную реальность и как она используется.</span><span class="sxs-lookup"><span data-stu-id="82e0e-195">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="82e0e-196">[![Посетите мероприятие](images/74-16.png)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="82e0e-196">[![Come to an event](images/74-16.png)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="82e0e-197">**[Посетите мероприятие](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-197">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="82e0e-198">Ознакомьтесь с оборудованием и получите практическое руководство по созданию первого приложения HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="82e0e-198">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="82e0e-199">[![Установка инструментов](images/74-17.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="82e0e-199">[![Install the tools](images/74-17.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="82e0e-200">**[Установка инструментов](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-200">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="82e0e-201">Используйте контрольный список установки, чтобы получить инструменты, необходимые для создания приложений для HoloLens и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="82e0e-201">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="82e0e-202">[![Приступите к разработке](images/74-18.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="82e0e-202">[![Start developing](images/74-18.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="82e0e-203">**[Приступите к разработке](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="82e0e-203">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="82e0e-204">Выберите путь разработки в зависимости от своего уровня навыков, стиля работы или платформы.</span><span class="sxs-lookup"><span data-stu-id="82e0e-204">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>
