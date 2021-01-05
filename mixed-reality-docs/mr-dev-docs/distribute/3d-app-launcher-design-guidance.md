---
title: Руководство по проектированию средств запуска трехмерных приложений
description: Средство запуска 3D-приложений — это «физический» объект в мире смешанной реальности пользователя, который можно выбрать для запуска приложения.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, средство запуска приложений для трехмерной графики, иммерсивное головной телефон, активный куб, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, UWP, Win32, освещение, цвет
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757732"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="1c51a-104">Руководство по проектированию средств запуска трехмерных приложений</span><span class="sxs-lookup"><span data-stu-id="1c51a-104">3D app launcher design guidance</span></span>

<span data-ttu-id="1c51a-105">Когда вы Помещаетесь на гарнитуру Windows Mixed Reality (VR), вы переходите на домашнюю страницу Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1c51a-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home.</span></span> <span data-ttu-id="1c51a-106">Домашняя страница отображается в виде дома на клиффе, окружающем горы и воду, но вы можете [выбрать другие среды и даже создать собственные](../design/add-custom-home-environments.md).</span><span class="sxs-lookup"><span data-stu-id="1c51a-106">The home is visualized as a house on a cliff surrounded by mountains and water, but you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="1c51a-107">В сфере дома пользователь может размещать и упорядочивать трехмерные объекты и приложения, которые им нужны.</span><span class="sxs-lookup"><span data-stu-id="1c51a-107">Within the home's space, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="1c51a-108">**Средство запуска 3D-приложений** — это «физический» объект в мире смешанной реальности пользователя, который можно выбрать для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="1c51a-108">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="1c51a-109">![Пример: средство запуска многомерных приложений с плавающей запятой](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-109">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c51a-110">*Пример средства запуска приложения 3D с плавающей высоты (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="1c51a-110">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="1c51a-111">процесс создания средства запуска приложений 3D</span><span class="sxs-lookup"><span data-stu-id="1c51a-111">3D app launcher creation process</span></span>

<span data-ttu-id="1c51a-112">Создание средства запуска 3D-приложений состоит из трех этапов.</span><span class="sxs-lookup"><span data-stu-id="1c51a-112">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="1c51a-113">Проектирование и концепция (в этой статье)</span><span class="sxs-lookup"><span data-stu-id="1c51a-113">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="1c51a-114">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="1c51a-114">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="1c51a-115">Интеграция этого приложения в приложение:</span><span class="sxs-lookup"><span data-stu-id="1c51a-115">Integrating it into your application:</span></span>
    * [<span data-ttu-id="1c51a-116">Приложения UWP</span><span class="sxs-lookup"><span data-stu-id="1c51a-116">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="1c51a-117">Приложения Win32</span><span class="sxs-lookup"><span data-stu-id="1c51a-117">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="1c51a-118">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="1c51a-118">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="1c51a-119">Самое хорошо знакомое</span><span class="sxs-lookup"><span data-stu-id="1c51a-119">Fantastic yet familiar</span></span>

<span data-ttu-id="1c51a-120">Среда Windows Mixed Reality, в которой находится средство запуска приложений, является знакомой, а часть — более понятная или Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="1c51a-120">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="1c51a-121">Лучшие средства запуска следуют правилам этого мира.</span><span class="sxs-lookup"><span data-stu-id="1c51a-121">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="1c51a-122">Подумайте о том, как можно взять привычный репрезентативный объект из своего приложения, но с изгибим некоторые правила фактической реальности.</span><span class="sxs-lookup"><span data-stu-id="1c51a-122">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="1c51a-123">Результат будет волшебным.</span><span class="sxs-lookup"><span data-stu-id="1c51a-123">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="1c51a-124">Точки</span><span class="sxs-lookup"><span data-stu-id="1c51a-124">Intuitive</span></span>

<span data-ttu-id="1c51a-125">При просмотре средства запуска приложения его назначение — запуск приложения — должно быть очевидным и не должно вызывать путаницы.</span><span class="sxs-lookup"><span data-stu-id="1c51a-125">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="1c51a-126">Например, убедитесь, что средство запуска является очевидным характером приложения, которое не будет путать с дéкором в Клифф дома.</span><span class="sxs-lookup"><span data-stu-id="1c51a-126">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="1c51a-127">Средство запуска приложений должно пригласить людей для касания или выбора.</span><span class="sxs-lookup"><span data-stu-id="1c51a-127">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="1c51a-128">![Пример: Новая заметка. средство запуска приложений 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-128">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c51a-129">*Последнее Примечание. Пример средства запуска приложения 3D (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="1c51a-129">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="1c51a-130">Масштаб домашней страницы</span><span class="sxs-lookup"><span data-stu-id="1c51a-130">Home scale</span></span>

<span data-ttu-id="1c51a-131">программы запуска 3D-приложений в Клифф дома и их размер по умолчанию должны иметь смысл с другими «физическими» объектами в пространстве.</span><span class="sxs-lookup"><span data-stu-id="1c51a-131">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="1c51a-132">Если вы размещаете средство запуска рядом, скажем, дома или в какой-либо мебели, оно должно иметь вид дома и на уровне.</span><span class="sxs-lookup"><span data-stu-id="1c51a-132">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="1c51a-133">Хорошей отправной точкой является просмотр того, как он выглядит на 30 кубических сантиметрах, но помните, что пользователи могут масштабировать его в любое время.</span><span class="sxs-lookup"><span data-stu-id="1c51a-133">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="1c51a-134">Собственное — возможно</span><span class="sxs-lookup"><span data-stu-id="1c51a-134">Own-able</span></span>

<span data-ttu-id="1c51a-135">Средство запуска приложений должно иметь такое же значение, как объект.</span><span class="sxs-lookup"><span data-stu-id="1c51a-135">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="1c51a-136">Они будут практически соседними с этими объектами, поэтому средство запуска должно быть похоже на то, что пользователь думал, чтобы находить и хранить поблизости.</span><span class="sxs-lookup"><span data-stu-id="1c51a-136">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="1c51a-137">![Пример: астро деформация 3D App Launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-137">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c51a-138">*Пример средства запуска Астро деформации 3D-приложения (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="1c51a-138">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="1c51a-139">Распознаваемое</span><span class="sxs-lookup"><span data-stu-id="1c51a-139">Recognizable</span></span>

<span data-ttu-id="1c51a-140">Программа запуска 3D-приложений должна мгновенно выразить "марку вашего приложения" пользователям, которые ее видят.</span><span class="sxs-lookup"><span data-stu-id="1c51a-140">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="1c51a-141">Если в приложении есть символ звездочки или особенно идентифицируемый объект, мы рекомендуем использовать его в качестве значительной части проекта.</span><span class="sxs-lookup"><span data-stu-id="1c51a-141">If you have a star character or an especially identifiable object in your app, we recommend using that as a significant part of your design.</span></span> <span data-ttu-id="1c51a-142">В мире смешанной реальности объект будет вырисовывать больше пользователей, чем только эмблема.</span><span class="sxs-lookup"><span data-stu-id="1c51a-142">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="1c51a-143">Распознаваемые объекты быстро и четко обмениваются торговыми марками.</span><span class="sxs-lookup"><span data-stu-id="1c51a-143">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="1c51a-144">Объемные</span><span class="sxs-lookup"><span data-stu-id="1c51a-144">Volumetric</span></span>

<span data-ttu-id="1c51a-145">Ваше приложение заслуживает больше, чем просто поместите эмблему на плоскую плоскость и вызовите ее в день.</span><span class="sxs-lookup"><span data-stu-id="1c51a-145">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="1c51a-146">Средство запуска должно иметь вид привлекательного, трехмерного, физического объекта в пространстве пользователя.</span><span class="sxs-lookup"><span data-stu-id="1c51a-146">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="1c51a-147">Хорошим подходом является Представьте, что ваше приложение помаци в день благодарения параде.</span><span class="sxs-lookup"><span data-stu-id="1c51a-147">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="1c51a-148">Спросите себя, что же в том, что люди на самом деле не поступили на улице?</span><span class="sxs-lookup"><span data-stu-id="1c51a-148">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="1c51a-149">Что будет великолепно выглядеть со всех углов просмотра?</span><span class="sxs-lookup"><span data-stu-id="1c51a-149">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1c51a-150">![Только эмблема с логотипом ](images/20171016-140436-mixedreality-640px.jpg) </span><span class="sxs-lookup"><span data-stu-id="1c51a-150">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1c51a-151">![Более понятное знакомство с ](images/20171016-140557-mixedreality-640px.jpg) *символом*</span><span class="sxs-lookup"><span data-stu-id="1c51a-151">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="1c51a-152">![Плоский подход, не удивительно, обычный плоский ](images/20171016-155101-mixedreality-640px.jpg) *подход, не удивительно, кажется плоским*</span><span class="sxs-lookup"><span data-stu-id="1c51a-152">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1c51a-153">![Объемные подход лучше наглядно демонстрирует ваше приложение, ](images/20171016-161407-mixedreality-640px.jpg) *объемные подход к демонстрации вашего приложения* .</span><span class="sxs-lookup"><span data-stu-id="1c51a-153">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="1c51a-154">Советы по использованию эффективных трехмерных моделей</span><span class="sxs-lookup"><span data-stu-id="1c51a-154">Tips for good 3D models</span></span>

* <span data-ttu-id="1c51a-155">При планировании измерений для средства запуска приложения пропускная поддержка для приблизительного Куба с 30 cm.</span><span class="sxs-lookup"><span data-stu-id="1c51a-155">When planning dimensions for your app launcher, shoot for roughly a 30-cm cube.</span></span> <span data-ttu-id="1c51a-156">Таким образом, соотношение размера 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="1c51a-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="1c51a-157">Модели должны иметь 10 000 многоугольников.</span><span class="sxs-lookup"><span data-stu-id="1c51a-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="1c51a-158">Дополнительные сведения о счетчиках и уровнях сведений о треугольниках (Лодс)</span><span class="sxs-lookup"><span data-stu-id="1c51a-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="1c51a-159">Протестируйте иммерсивное головной телефон.</span><span class="sxs-lookup"><span data-stu-id="1c51a-159">Test on an immersive headset.</span></span>
* <span data-ttu-id="1c51a-160">Сведения о сборке в своей геометрической модели, где это возможно — не полагайтесь на текстуры для получения подробных сведений.</span><span class="sxs-lookup"><span data-stu-id="1c51a-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="1c51a-161">Создание закрытой геометрии с жесткой наводами.</span><span class="sxs-lookup"><span data-stu-id="1c51a-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="1c51a-162">Нет дыр, которые не моделируются в.</span><span class="sxs-lookup"><span data-stu-id="1c51a-162">No holes that aren't modeled in.</span></span>
* <span data-ttu-id="1c51a-163">Использование природных материалов в объекте.</span><span class="sxs-lookup"><span data-stu-id="1c51a-163">Use natural materials in your object.</span></span> <span data-ttu-id="1c51a-164">Представьте себе создание ИТ в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="1c51a-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="1c51a-165">Убедитесь, что модель хорошо читается на разных расстояниях и размерах.</span><span class="sxs-lookup"><span data-stu-id="1c51a-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="1c51a-166">Когда модель будет готова к работе, ознакомьтесь с [рекомендациями по экспорту ресурсов](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="1c51a-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="1c51a-167">![Модель с незначительными деталями в текстуре](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c51a-168">*Модель с незначительными деталями в текстуре*</span><span class="sxs-lookup"><span data-stu-id="1c51a-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="1c51a-169">Чего следует избегать</span><span class="sxs-lookup"><span data-stu-id="1c51a-169">What to avoid</span></span>

* <span data-ttu-id="1c51a-170">Не используйте подробные сведения о высокой контрастности или небольшие, занятые шаблоны и текстуры.</span><span class="sxs-lookup"><span data-stu-id="1c51a-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="1c51a-171">Не используйте тонкую геометрию — она не работает на расстоянии, и псевдоним будет неплохой.</span><span class="sxs-lookup"><span data-stu-id="1c51a-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="1c51a-172">Не разрешите, чтобы части модели не превышают размер 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="1c51a-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="1c51a-173">При этом создаются проблемы масштабирования.</span><span class="sxs-lookup"><span data-stu-id="1c51a-173">It will create scaling problems.</span></span>

<span data-ttu-id="1c51a-174">![Старайтесь не использовать высококонтрастные шаблоны с малым уровнем доступности](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c51a-175">*Избегайте высокой контрастности, мелких, занятых шаблонов*</span><span class="sxs-lookup"><span data-stu-id="1c51a-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="1c51a-176">Как обрабатывает тип</span><span class="sxs-lookup"><span data-stu-id="1c51a-176">How to handle type</span></span>

* <span data-ttu-id="1c51a-177">Рекомендуется, чтобы ваш тип занимать около 1/3 приложения (или более).</span><span class="sxs-lookup"><span data-stu-id="1c51a-177">We recommend your type takes up about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="1c51a-178">Тип — это основная вещь, которая дает пользователям представление о том, что средство запуска, на самом деле, является средством запуска, чтобы было замечательно, если оно существенно.</span><span class="sxs-lookup"><span data-stu-id="1c51a-178">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s substantial.</span></span>
* <span data-ttu-id="1c51a-179">Старайтесь не делать этот тип очень широким — старайтесь не использовать его в пределах основных измерений запуска приложения (более или меньше).</span><span class="sxs-lookup"><span data-stu-id="1c51a-179">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="1c51a-180">Неструктурированный тип может работать, но может быть трудно просматривать из определенных углов и в определенных средах.</span><span class="sxs-lookup"><span data-stu-id="1c51a-180">Flat type can work, but it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="1c51a-181">Вы можете попытаться поместить его в сплошной объект или заднем плане, чтобы помочь в этом.</span><span class="sxs-lookup"><span data-stu-id="1c51a-181">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="1c51a-182">Добавление измерения к типу отлично выглядит в трехмерном виде.</span><span class="sxs-lookup"><span data-stu-id="1c51a-182">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="1c51a-183">Заливка сторон типа, более темного цвета, может помочь в удобочитаемости.</span><span class="sxs-lookup"><span data-stu-id="1c51a-183">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1c51a-184">![Неструктурированный тип без задника может быть трудно просмотреть из определенных углов, а в некоторых средах ](images/flattype-640px.png) *— Неструктурированный тип без предварительного просмотра с определенным углом и в определенных средах* .</span><span class="sxs-lookup"><span data-stu-id="1c51a-184">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1c51a-185">![Тип с встроенным подготовкой может хорошо работать ](images/flattypeandbkg-640px.png) *с встроенным заднем*</span><span class="sxs-lookup"><span data-stu-id="1c51a-185">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1c51a-186">![Вытянутый тип может быть хорошо работать, если закрашенный ](images/20171016-160221-mixedreality-640px.jpg) *тип сторон может работать, если затенить стороны*</span><span class="sxs-lookup"><span data-stu-id="1c51a-186">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="1c51a-187">**Введите цвета, которые работают**</span><span class="sxs-lookup"><span data-stu-id="1c51a-187">**Type colors that work**</span></span>

* <span data-ttu-id="1c51a-188">White</span><span class="sxs-lookup"><span data-stu-id="1c51a-188">White</span></span>
* <span data-ttu-id="1c51a-189">Черный</span><span class="sxs-lookup"><span data-stu-id="1c51a-189">Black</span></span>
* <span data-ttu-id="1c51a-190">Яркий насыщенный цвет</span><span class="sxs-lookup"><span data-stu-id="1c51a-190">Bright semi-saturated color</span></span>

<span data-ttu-id="1c51a-191">![Введите цвета, которые работают.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-191">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c51a-192">*Введите цвета, которые работают*</span><span class="sxs-lookup"><span data-stu-id="1c51a-192">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="1c51a-193">Цвета, которые следует избегать</span><span class="sxs-lookup"><span data-stu-id="1c51a-193">Colors to avoid</span></span>

<span data-ttu-id="1c51a-194">Типы цветов, вызывающие проблемы, включают:</span><span class="sxs-lookup"><span data-stu-id="1c51a-194">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="1c51a-195">Средние тона</span><span class="sxs-lookup"><span data-stu-id="1c51a-195">Mid-tones</span></span>
* <span data-ttu-id="1c51a-196">Серый</span><span class="sxs-lookup"><span data-stu-id="1c51a-196">Gray</span></span>
* <span data-ttu-id="1c51a-197">Чрезмерно насыщенные цвета или ненасыщенные цвета</span><span class="sxs-lookup"><span data-stu-id="1c51a-197">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="1c51a-198">![Введите цвета, вызывающие проблемы.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-198">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="1c51a-199">*Типы цветов, вызывающие проблемы*</span><span class="sxs-lookup"><span data-stu-id="1c51a-199">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="1c51a-200">Освещение</span><span class="sxs-lookup"><span data-stu-id="1c51a-200">Lighting</span></span>

<span data-ttu-id="1c51a-201">Освещение для программы запуска приложений поступает из среды Клифф House.</span><span class="sxs-lookup"><span data-stu-id="1c51a-201">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="1c51a-202">Обязательно протестируйте средство запуска в нескольких местах дома, чтобы оно хорошо выглядело как светлое, так и темнее.</span><span class="sxs-lookup"><span data-stu-id="1c51a-202">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="1c51a-203">Хорошая новость состоит в том, что, если вы уже использовали другие рекомендации по проектированию в этом документе, средство запуска должно быть хорошо знакомым для большинства освещения в Клифф дома.</span><span class="sxs-lookup"><span data-stu-id="1c51a-203">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="1c51a-204">Для проверки того, как средство запуска выполняет поиск различных источников света в среде, это среда, комната мультимедиа, где-то вне и обратно патио (конкретная область с зеленая трава).</span><span class="sxs-lookup"><span data-stu-id="1c51a-204">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="1c51a-205">Еще один хороший тест — поместив его на половину светлой и половинной тени и посмотрим, как он выглядит.</span><span class="sxs-lookup"><span data-stu-id="1c51a-205">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="1c51a-206">![Убедитесь, что средство запуска хорошо смотрится как в светлых, так и в тенях.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1c51a-206">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="1c51a-207">*Убедитесь, что средство запуска хорошо смотрится как на светлой, так и в тенях.*</span><span class="sxs-lookup"><span data-stu-id="1c51a-207">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="1c51a-208">Текстуризации</span><span class="sxs-lookup"><span data-stu-id="1c51a-208">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="1c51a-209">Создание текстур</span><span class="sxs-lookup"><span data-stu-id="1c51a-209">Authoring your textures</span></span>

<span data-ttu-id="1c51a-210">В качестве конечного формата средства запуска 3D-приложений будет использоваться файл. GLBA, который выполняется с помощью конвейера PBR (с физическим рендерингом).</span><span class="sxs-lookup"><span data-stu-id="1c51a-210">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="1c51a-211">Это может быть непростой процесс. Теперь вы можете использовать технический исполнитель, если вы еще этого не сделали.</span><span class="sxs-lookup"><span data-stu-id="1c51a-211">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="1c51a-212">Если вы дивный DIY-ER, то сможете [исследовать и изучать терминологию PBR](https://wiki.polycount.com/wiki/PBR) , а также узнать о том, что происходит, прежде чем приступать к работе, поможет избежать распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="1c51a-212">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="1c51a-213">![Пример: новое приложение для заметок](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="1c51a-213">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="1c51a-214">*Последнее Примечание. Пример средства запуска приложения 3D (вымышленное приложение)*</span><span class="sxs-lookup"><span data-stu-id="1c51a-214">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="1c51a-215">Рекомендуемое средство разработки</span><span class="sxs-lookup"><span data-stu-id="1c51a-215">Recommended authoring tool</span></span>

<span data-ttu-id="1c51a-216">Мы рекомендуем использовать [веществ по образцу](https://www.allegorithmic.com/products/substance-painter) аллегорисмик для создания окончательного файла.</span><span class="sxs-lookup"><span data-stu-id="1c51a-216">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="1c51a-217">Если вы не знакомы с созданием шейдеров PBR в веществ по образцу, ознакомьтесь с [руководством](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="1c51a-217">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="1c51a-218">(Как вариант [трехмерной](https://3dcoat.com/home/), так и [куиксел Suite 2](https://quixel.se/suite2/)или [Мармосет тулбаг](https://www.marmoset.co/toolbag/) также будут работать, если вы более знакомы с одним из них.)</span><span class="sxs-lookup"><span data-stu-id="1c51a-218">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="1c51a-219">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="1c51a-219">Best practices</span></span>

* <span data-ttu-id="1c51a-220">Если объект запуска приложения был создан для PBR, он должен просто преобразовать его для среды Клифф House.</span><span class="sxs-lookup"><span data-stu-id="1c51a-220">If your app launcher object was authored for PBR, it should be straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="1c51a-221">Наш шейдер ожидает рабочий поток "металл/грубая" — недействительный шейдер PBR является закрытым факсом.</span><span class="sxs-lookup"><span data-stu-id="1c51a-221">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="1c51a-222">При экспорте текстур учитывайте [Рекомендуемые размеры текстур](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="1c51a-222">When exporting your textures, keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="1c51a-223">Не забудьте собрать объекты для освещения в режиме реального времени — это означает:</span><span class="sxs-lookup"><span data-stu-id="1c51a-223">Make sure to build your objects for real-time lighting—this means:</span></span>
  * <span data-ttu-id="1c51a-224">Избегайте помогут теней — или нарисованных теней</span><span class="sxs-lookup"><span data-stu-id="1c51a-224">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="1c51a-225">Предотвращение помогут освещения текстур</span><span class="sxs-lookup"><span data-stu-id="1c51a-225">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="1c51a-226">Используйте один из пакетов для создания данных типа PBR, чтобы получить правильные карты, созданные для нашего шейдера.</span><span class="sxs-lookup"><span data-stu-id="1c51a-226">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="1c51a-227">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1c51a-227">See also</span></span>

* [<span data-ttu-id="1c51a-228">Создание трехмерных моделей для использования на домашней странице смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1c51a-228">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="1c51a-229">Реализация средств запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="1c51a-229">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="1c51a-230">Реализация средств запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="1c51a-230">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
