---
title: Инстинктивное взаимодействие
description: Платформа Mixed Reality построена на принципах простого инстинктивного взаимодействия.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: смешанная реальность, взгляд, нацеливание взглядом, взаимодействие, проектирование, hololens, ММR, мультимодальный, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens
ms.openlocfilehash: 37ac7475172977c8741c17817568cc9b5ad2a4e5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "97847287"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="d2a25-104">Знакомство с инстинктивным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="d2a25-104">Introducing instinctual interactions</span></span>

![Манипулирование на большом расстоянии с помощью рук](images/04_InteractionFundamentals.png)

<span data-ttu-id="d2a25-106">Платформа Mixed Reality (MR) построена на принципах простого инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="d2a25-107">Мы сделали три шага, чтобы разработчики и конструкторы приложений могли предоставлять своим клиентам простые и понятные механизмы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="d2a25-108">Сначала мы убедились, что наши датчики и технологии ввода объединены в многомодальные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-108">First, we've made sure our sensors and input technologies combine into multimodal interaction models.</span></span> <span data-ttu-id="d2a25-109">Такие модели взаимодействия включают отслеживание рук и взгляда, а также ввод на естественном языке.</span><span class="sxs-lookup"><span data-stu-id="d2a25-109">These interaction models include hand and eye tracking along with natural language input.</span></span> <span data-ttu-id="d2a25-110">Мы ведем исследования, создаем проекты и разрабатываем решения на базе мультимодальной платформы, а не на основе индивидуальных входных данных. Такой подход — ключ к созданию возможностей инстинктивного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-110">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="d2a25-111">Во-вторых, мы учитываем, что многие разработчики ориентированы на несколько устройств HoloLens, таких как HoloLens 2 и HoloLens (1-го поколения) или HoloLens и виртуальная реальность.</span><span class="sxs-lookup"><span data-stu-id="d2a25-111">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span> <span data-ttu-id="d2a25-112">Поэтому мы разработали модели взаимодействия для работы на разных устройствах, даже если технология ввода зависит от устройства.</span><span class="sxs-lookup"><span data-stu-id="d2a25-112">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span> <span data-ttu-id="d2a25-113">Например, при удаленном взаимодействии иммерсивной гарнитуры Windows с контроллером 6DoF и при удаленном взаимодействии с HoloLens 2 используются одинаковые возможности и шаблоны.</span><span class="sxs-lookup"><span data-stu-id="d2a25-113">For example, far interaction on a Windows Immersive headset with a 6DoF controller and HoloLens 2 both use identical affordances and patterns.</span></span> <span data-ttu-id="d2a25-114">Это упрощает разработку приложений на нескольких устройствах и позволяет сделать взаимодействия естественными.</span><span class="sxs-lookup"><span data-stu-id="d2a25-114">This makes it easy for cross-device application development and provides a natural feel to user interactions.</span></span> 

<span data-ttu-id="d2a25-115">Хотя мы признаем, что в смешанной реальности возможны тысячи эффективных, увлекательных и магических взаимодействий, мы обнаружили, что преднамеренное использование единой модели взаимодействия в приложении — это лучший способ обеспечить успешную и комфортную работу пользователей.</span><span class="sxs-lookup"><span data-stu-id="d2a25-115">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="d2a25-116">Поэтому в это руководство по взаимодействию мы включили три вещи.</span><span class="sxs-lookup"><span data-stu-id="d2a25-116">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="d2a25-117">Специальные указания по трем основным моделям взаимодействия, а также по компонентам и шаблонам, необходимым для каждого.</span><span class="sxs-lookup"><span data-stu-id="d2a25-117">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="d2a25-118">Дополнительное описание других преимуществ, которые предоставляет наша платформа.</span><span class="sxs-lookup"><span data-stu-id="d2a25-118">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="d2a25-119">Общие инструкции по выбору подходящей модели взаимодействия для конкретного сценария разработки.</span><span class="sxs-lookup"><span data-stu-id="d2a25-119">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="d2a25-120">Модели мультимодальных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="d2a25-120">Multimodal interaction models</span></span>

<span data-ttu-id="d2a25-121">Основываясь на наших исследованиях и отзывах клиентов, мы определили, что для реализации большинства возможностей смешанной реальности подходят три основные модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-121">Based on our research and feedback from customers, we've discovered that three primary interaction models suit most mixed reality experiences.</span></span> <span data-ttu-id="d2a25-122">Во многих отношениях модель взаимодействия — это модель мышления пользователя для выполнения своего рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d2a25-122">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="d2a25-123">Каждая из этих моделей взаимодействия оптимизирована для ряда потребностей клиентов. При правильном применении каждая из них является простой, мощной и удобной в использовании.</span><span class="sxs-lookup"><span data-stu-id="d2a25-123">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="d2a25-124">Диаграмма ниже представляет собой упрощенный обзор.</span><span class="sxs-lookup"><span data-stu-id="d2a25-124">The chart below is a simplified overview.</span></span> <span data-ttu-id="d2a25-125">Подробная информация об использовании каждой модели взаимодействия приведена ниже на страницах с изображениями и примерами кода.</span><span class="sxs-lookup"><span data-stu-id="d2a25-125">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2a25-126"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-126"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d2a25-127"><strong>Примеры сценариев</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-127"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="d2a25-128"><strong>Совпадение</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-128"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="d2a25-129"><strong>Оборудование</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-129"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-130"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-130"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="d2a25-131">Возможности трехмерного пространства, такие как пространственная структура и конструктор, манипулирование содержимым или симуляция.</span><span class="sxs-lookup"><span data-stu-id="d2a25-131">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="d2a25-132">В сочетании с системой голосовой связи, отслеживанием взгляда или направления головы отлично подходит для новых пользователей.</span><span class="sxs-lookup"><span data-stu-id="d2a25-132">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="d2a25-133">Низкий порог вхождения.</span><span class="sxs-lookup"><span data-stu-id="d2a25-133">Low learning curve.</span></span> <span data-ttu-id="d2a25-134">Последовательное взаимодействие с пользователем для отслеживания рук и контроллеров 6DoF.</span><span class="sxs-lookup"><span data-stu-id="d2a25-134">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="d2a25-135">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2a25-135">HoloLens 2</span></span><br><span data-ttu-id="d2a25-136">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="d2a25-136">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-137"><a href="hands-free.md">Режимы без использования рук</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-137"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="d2a25-138">Контекстуальные возможности, когда руки пользователя заняты, например, обучением на рабочем месте и обслуживанием.</span><span class="sxs-lookup"><span data-stu-id="d2a25-138">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="d2a25-139">Требуется некоторое обучение.</span><span class="sxs-lookup"><span data-stu-id="d2a25-139">Some learning required.</span></span> <span data-ttu-id="d2a25-140">Если руки должны быть свободны, устройство обеспечивает удобное управление с помощью голоса и естественного языка.</span><span class="sxs-lookup"><span data-stu-id="d2a25-140">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="d2a25-141">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2a25-141">HoloLens 2</span></span><br><span data-ttu-id="d2a25-142">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d2a25-142">HoloLens (1st gen)</span></span><br><span data-ttu-id="d2a25-143">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="d2a25-143">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-144"><a href="gaze-and-commit.md">Взгляд и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-144"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d2a25-145">Взаимодействия по щелчку, например трехмерные презентации, демонстрации.</span><span class="sxs-lookup"><span data-stu-id="d2a25-145">Click-through experiences, for example, 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="d2a25-146">Требуется обучение на HMD, но не на мобильном.</span><span class="sxs-lookup"><span data-stu-id="d2a25-146">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="d2a25-147">Лучшее для доступных контроллеров.</span><span class="sxs-lookup"><span data-stu-id="d2a25-147">Best for accessible controllers.</span></span> <span data-ttu-id="d2a25-148">Лучшее для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d2a25-148">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="d2a25-149">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2a25-149">HoloLens 2</span></span><br><span data-ttu-id="d2a25-150">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="d2a25-150">HoloLens (1st gen)</span></span><br><span data-ttu-id="d2a25-151">Иммерсивные гарнитуры</span><span class="sxs-lookup"><span data-stu-id="d2a25-151">Immersive headsets</span></span><br><span data-ttu-id="d2a25-152">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="d2a25-152">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="d2a25-153">Чтобы избежать несоответствий в механизме взаимодействия с пользователем, на всех этапах следуйте инструкциям, касающимся одной и той же модели.</span><span class="sxs-lookup"><span data-stu-id="d2a25-153">To avoid gaps in the user interaction experience, it's best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="d2a25-154">В следующих разделах рассматриваются этапы выбора и реализации одной из этих моделей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-154">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a><span data-ttu-id="d2a25-155">Ознакомившись с инструкциями на этой странице, вы узнаете, как выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="d2a25-155">By the end of this page, you'll understand our guidance on:</span></span>
 
* <span data-ttu-id="d2a25-156">Выбор модели взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="d2a25-156">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="d2a25-157">Реализация модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d2a25-157">Implementing the interaction model</span></span>
* <span data-ttu-id="d2a25-158">Переход между моделями взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d2a25-158">Transitioning between interaction models</span></span>
* <span data-ttu-id="d2a25-159">Следующие шаги конструктора</span><span class="sxs-lookup"><span data-stu-id="d2a25-159">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="d2a25-160">Выберите модель взаимодействия для вашего клиента</span><span class="sxs-lookup"><span data-stu-id="d2a25-160">Choose an interaction model for your customer</span></span>

<span data-ttu-id="d2a25-161">Как правило, разработчики и проектировщики решений продумывают типы взаимодействия, ориентируясь на потребности клиента.</span><span class="sxs-lookup"><span data-stu-id="d2a25-161">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="d2a25-162">Чтобы поощрить такой подход к проектированию, мы рекомендуем следовать приведенным ниже инструкциям по выбору модели взаимодействия, оптимизированной для вашего клиента.</span><span class="sxs-lookup"><span data-stu-id="d2a25-162">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="d2a25-163">Почему нужно следовать руководству?</span><span class="sxs-lookup"><span data-stu-id="d2a25-163">Why follow this guidance?</span></span>

* <span data-ttu-id="d2a25-164">Мы проверяем наши модели взаимодействия по объективным и субъективным критериям, таким как физические и когнитивные трудозатраты, простота восприятия и обучаемость.</span><span class="sxs-lookup"><span data-stu-id="d2a25-164">We test our interaction models for objective and subjective criteria, including physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="d2a25-165">Так как есть множество способов взаимодействия, визуальные и звуковые возможности, а также поведение объекта отличаются в зависимости от конкретной модели.</span><span class="sxs-lookup"><span data-stu-id="d2a25-165">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="d2a25-166">Объединение частей нескольких моделей взаимодействия создает риск конкурирующих возможностей, таких как одновременное срабатывание телекинеза и курсора направления головы.</span><span class="sxs-lookup"><span data-stu-id="d2a25-166">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="d2a25-167">Это может быть сложным для восприятия пользователей.</span><span class="sxs-lookup"><span data-stu-id="d2a25-167">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="d2a25-168">Ниже приведены несколько примеров того, как возможности и расширения функциональности оптимизируются для каждой модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-168">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="d2a25-169">Мы часто видим, что у новых пользователей возникают похожие вопросы, например: "_Как я узнаю, что система работает_, _как мне узнать, что я могу сделать_, и _как узнать, поняла ли она мое действие?_ "</span><span class="sxs-lookup"><span data-stu-id="d2a25-169">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2a25-170"><strong>Модель</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-170"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d2a25-171"><strong>Как мне узнать, что она работает?</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-171"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="d2a25-172"><strong>Как мне узнать, что я могу сделать?</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-172"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="d2a25-173"><strong>Как мне узнать, что я только что сделал?</strong></span><span class="sxs-lookup"><span data-stu-id="d2a25-173"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-174"><a href="hands-and-tools.md">Руки и контроллеры движения</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-174"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="d2a25-175">Я вижу виртуальную руку, возможность курсора для кончика пальца или телекинез либо лучи контроллера движений.</span><span class="sxs-lookup"><span data-stu-id="d2a25-175">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="d2a25-176">Когда моя рука рядом с объектом, я вижу захватные маркеры или появление ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="d2a25-176">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="d2a25-177">Я слышу звуковые сигналы и вижу анимацию при захвате и выпуске.</span><span class="sxs-lookup"><span data-stu-id="d2a25-177">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-178"><a href="gaze-and-commit.md">Направление головы и фиксация</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-178"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d2a25-179">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="d2a25-179">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d2a25-180">Курсор изменяется над определенными объектами.</span><span class="sxs-lookup"><span data-stu-id="d2a25-180">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="d2a25-181">Я вижу визуальные подтверждения или слышу звуковые подтверждения при определенных действиях.</span><span class="sxs-lookup"><span data-stu-id="d2a25-181">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="d2a25-182"><a href="hands-free.md">Без использования рук (Направление головы и остановка)</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-182"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="d2a25-183">Я вижу курсор в центре моей видимой зоны.</span><span class="sxs-lookup"><span data-stu-id="d2a25-183">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d2a25-184">Я вижу индикатор хода выполнения, когда останавливаюсь на интерактивном объекте.</span><span class="sxs-lookup"><span data-stu-id="d2a25-184">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="d2a25-185">Я вижу визуальные подтверждения или слышу звуковые подтверждения при определенных действиях.</span><span class="sxs-lookup"><span data-stu-id="d2a25-185">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d2a25-186"><a href="hands-free.md">Без использования рук (Голосовые команды)</a></span><span class="sxs-lookup"><span data-stu-id="d2a25-186"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="d2a25-187">Я вижу индикатор прослушивания и заголовки, которые показывают, что слышала система.</span><span class="sxs-lookup"><span data-stu-id="d2a25-187">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="d2a25-188">Я получаю голосовые приглашения и указания.</span><span class="sxs-lookup"><span data-stu-id="d2a25-188">I get voice prompts and hints.</span></span> <span data-ttu-id="d2a25-189">Когда я говорю: "Что можно говорить?"</span><span class="sxs-lookup"><span data-stu-id="d2a25-189">When I say: "What can I say?"</span></span> <span data-ttu-id="d2a25-190">Я вижу отзыв.</span><span class="sxs-lookup"><span data-stu-id="d2a25-190">I see feedback.</span></span></td>
        <td><span data-ttu-id="d2a25-191">Я вижу или слышу визуальные и звуковые подтверждения, когда даю команду, или пользовательский интерфейс устраняет неоднозначность, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="d2a25-191">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="d2a25-192">Ниже приведены вопросы, которые, по нашему мнению, помогут командам выбрать модель взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-192">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="d2a25-193">Вопрос.  Хотят ли мои пользователи хотят дотрагиваться до голограмм и выполнять точные голографические операции?</span><span class="sxs-lookup"><span data-stu-id="d2a25-193">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="d2a25-194">Ответ.  Если это так, ознакомьтесь с моделью взаимодействия "Руки и контроллеры движений" для точного нацеливания и манипулирования.</span><span class="sxs-lookup"><span data-stu-id="d2a25-194">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="d2a25-195">Вопрос.  Должны ли руки пользователей быть свободны, чтобы они могли выполнять определенные задачи в реальности?</span><span class="sxs-lookup"><span data-stu-id="d2a25-195">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="d2a25-196">Ответ.  Если это так, обратите внимание на модель "Без использования рук", которая обеспечивает отличные возможности взаимодействия на основе направления взгляда и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="d2a25-196">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="d2a25-197">Вопрос.  У моих пользователей есть время, чтобы освоить работу с моим приложением MR, или им нужно взаимодействие с минимальным периодом обучения?</span><span class="sxs-lookup"><span data-stu-id="d2a25-197">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="d2a25-198">Ответ.  Рекомендуем использовать модель "Контроллеры движения и жестов". Обучение работе с ней не занимает много времени, и она обеспечивает наиболее интуитивно простое взаимодействие, если пользователи могут задействовать руки.</span><span class="sxs-lookup"><span data-stu-id="d2a25-198">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users can use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="d2a25-199">Вопрос.  Используют ли мои пользователи контроллеры движения для указывания и операций?</span><span class="sxs-lookup"><span data-stu-id="d2a25-199">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="d2a25-200">Ответ.  Для модели "Руки и контроллеры движений" предоставляются полные инструкции, которые обеспечат успешную работу с контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="d2a25-200">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="d2a25-201">Вопрос.  Используют ли мои пользователи контроллер специальных возможностей или обычный контроллер Bluetooth, такой как кликер?</span><span class="sxs-lookup"><span data-stu-id="d2a25-201">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="d2a25-202">Ответ.  Мы рекомендуем использовать модель "Направление головы и подтверждение" для всех контроллеров, которые не отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="d2a25-202">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="d2a25-203">Она обеспечивает полное взаимодействие пользователя с системой с помощью простого механизма нацеливания и подтверждения.</span><span class="sxs-lookup"><span data-stu-id="d2a25-203">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="d2a25-204">Вопрос. Мои пользователи будут работать только с помощью "переходов" (например, в среде, похожей на слайд-шоу в трехмерном пространстве), не используя навигацию по многоуровневым элементам управления пользовательского интерфейса?</span><span class="sxs-lookup"><span data-stu-id="d2a25-204">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="d2a25-205">Ответ.  Если пользователям не нужно управлять большим числом объектов пользовательского интерфейса, "Направление головы и фиксация" предлагает удобный для изучения вариант, в котором пользователям не нужно беспокоиться о нацеливании.</span><span class="sxs-lookup"><span data-stu-id="d2a25-205">A:  If users don't need to control a lot of UI, Head-gaze and commit offers a learnable option where users don't have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="d2a25-206">Вопрос.  Используют ли мои пользователи как HoloLens (1-го поколения), так и HoloLens 2 или иммерсивные гарнитуры (гарнитуры виртуальной реальности) Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="d2a25-206">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="d2a25-207">Ответ.  Так как "Направление головы и фиксация" — это модель взаимодействия для HoloLens (1-го поколения), мы рекомендуем, чтобы разработчики, которые используют HoloLens (1-го поколения), применяли модель "Направление головы и фиксация" для любых функций или режимов, с которыми пользователи будут работать на гарнитуре HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="d2a25-207">A:  Since Head-gaze and commit are the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="d2a25-208">Подробные сведения о том, что нужно для комфортной работы с HoloLens разных поколений, см. в следующем разделе *Переходные модели взаимодействия*.</span><span class="sxs-lookup"><span data-stu-id="d2a25-208">See the next section on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="d2a25-209">Вопрос. Есть ли различия между моделями для пользователей, которые обычно работают в большом пространстве или перемещаются между разными пространствами, и пользователей, которые обычно работают в одном пространстве?</span><span class="sxs-lookup"><span data-stu-id="d2a25-209">Q: What about users who are mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="d2a25-210">Ответ.  Любая из моделей взаимодействия подойдет этим пользователям.</span><span class="sxs-lookup"><span data-stu-id="d2a25-210">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="d2a25-211">[В ближайшее время](../out-of-scope/news.md) появятся дополнительные руководства, касающиеся дизайна приложения.</span><span class="sxs-lookup"><span data-stu-id="d2a25-211">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="d2a25-212">Переходные модели взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d2a25-212">Transitioning interaction models</span></span>
<span data-ttu-id="d2a25-213">Иногда нужно использовать более одной модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d2a25-213">There are also use cases that might require using more than one interaction model.</span></span> <span data-ttu-id="d2a25-214">Например, при создании приложения используется модель _Контроллеры движений и жестов_, но вам нужно применить режим "без использования рук" для выездных техников.</span><span class="sxs-lookup"><span data-stu-id="d2a25-214">For example, your application's creation flow uses the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span> <span data-ttu-id="d2a25-215">Если ваш интерфейс требует нескольких моделей взаимодействия, пользователи могут столкнуться с трудностями при переходе от одной модели к другой, особенно если они недавно начали использовать смешанную реальность.</span><span class="sxs-lookup"><span data-stu-id="d2a25-215">If your experience does require multiple interaction models, users might have difficulty transitioning from one model to another, especially when they're new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="d2a25-216">Мы постоянно предоставляем разработчикам и дизайнерам дополнительные рекомендации относительно способов, сценариев и целей использования нескольких моделей взаимодействия MR.</span><span class="sxs-lookup"><span data-stu-id="d2a25-216">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="d2a25-217">См. также статью</span><span class="sxs-lookup"><span data-stu-id="d2a25-217">See also</span></span>
* [<span data-ttu-id="d2a25-218">Комфорт</span><span class="sxs-lookup"><span data-stu-id="d2a25-218">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="d2a25-219">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="d2a25-219">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="d2a25-220">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2a25-220">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d2a25-221">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="d2a25-221">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d2a25-222">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="d2a25-222">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="d2a25-223">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="d2a25-223">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d2a25-224">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="d2a25-224">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d2a25-225">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="d2a25-225">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="d2a25-226">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="d2a25-226">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d2a25-227">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="d2a25-227">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="d2a25-228">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="d2a25-228">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="d2a25-229">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="d2a25-229">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="d2a25-230">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="d2a25-230">Voice input</span></span>](voice-input.md)


