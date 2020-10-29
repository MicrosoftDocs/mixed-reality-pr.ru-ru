---
title: Шрифтовое оформление
description: Текст — важный элемент для доставки информации в приложении.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, проектирование, стиль, шрифт, типография, Пользовательский интерфейс, UX
ms.openlocfilehash: 59c7796998ac01fcbb5c9dc418da6454c8c74d12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692541"
---
# <a name="typography"></a><span data-ttu-id="175dc-104">Шрифтовое оформление</span><span class="sxs-lookup"><span data-stu-id="175dc-104">Typography</span></span>

![Пример оформления в HoloLens](images/typography-cover.png)<br>


<span data-ttu-id="175dc-106">Текст — важный элемент для доставки информации в приложении.</span><span class="sxs-lookup"><span data-stu-id="175dc-106">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="175dc-107">Как и в случае с оформлением на двухмерных экранах, ваша цель — предоставить понятную и удобочитаемую информацию.</span><span class="sxs-lookup"><span data-stu-id="175dc-107">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="175dc-108">Благодаря трехмерному пространству смешанной реальности существует возможность значительно улучшить текст и общее взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="175dc-108">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="175dc-109">Когда речь идет о типе в 3D, мы будем думать вытягивание, объемные трехмерный текст.</span><span class="sxs-lookup"><span data-stu-id="175dc-109">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="175dc-110">За исключением некоторых Logotype и некоторых других ограниченных приложений, вытягивание текста, как правило, понизить удобочитаемость текста.</span><span class="sxs-lookup"><span data-stu-id="175dc-110">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="175dc-111">Несмотря на то, что мы создаем возможности для трехмерной графики, мы используем 2D для типа, так как он более нагляден и проще в чтении.</span><span class="sxs-lookup"><span data-stu-id="175dc-111">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="175dc-112">В HoloLens тип создается с голограммами с использованием освещения на основе аддитивной цветовой системы.</span><span class="sxs-lookup"><span data-stu-id="175dc-112">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="175dc-113">Как и другие голограммы, тип можно поместить в фактическую среду, где он может быть заблокирован и наблюдаться с любого угла.</span><span class="sxs-lookup"><span data-stu-id="175dc-113">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="175dc-114">Воздействие [фокусировки](https://en.wikipedia.org/wiki/Parallax) между типом и средой также увеличивает глубину работы.</span><span class="sxs-lookup"><span data-stu-id="175dc-114">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="175dc-115">Оформление в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="175dc-115">Typography in mixed reality</span></span>

<span data-ttu-id="175dc-116">Типографские правила в смешанной реальности не отличаются от других мест.</span><span class="sxs-lookup"><span data-stu-id="175dc-116">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="175dc-117">Текст как в физическом мире, так и в виртуальном мире должен быть читаемым и читаемым.</span><span class="sxs-lookup"><span data-stu-id="175dc-117">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="175dc-118">Текст может находиться на стене или накладываться на физический объект.</span><span class="sxs-lookup"><span data-stu-id="175dc-118">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="175dc-119">Он может быть плавающим и цифровым пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="175dc-119">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="175dc-120">Независимо от контекста мы применяем те же типографские правила для чтения и распознавания.</span><span class="sxs-lookup"><span data-stu-id="175dc-120">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="175dc-121">Создать очистку иерархии</span><span class="sxs-lookup"><span data-stu-id="175dc-121">Create clear hierarchy</span></span>

<span data-ttu-id="175dc-122">Контрастность и иерархия построения с использованием различных размеров и весов типов.</span><span class="sxs-lookup"><span data-stu-id="175dc-122">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="175dc-123">Определение пандуса типа и его последующее применение в процессе работы приложения обеспечит удобство работы пользователя с согласованной иерархией информации.</span><span class="sxs-lookup"><span data-stu-id="175dc-123">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="175dc-124">![Примеры пандуса типов](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="175dc-124">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="175dc-125">*Определите шкалу типа и следуйте ей в процессе работы приложения.*</span><span class="sxs-lookup"><span data-stu-id="175dc-125">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="175dc-126">Ограничение шрифтов</span><span class="sxs-lookup"><span data-stu-id="175dc-126">Limit your fonts</span></span>

<span data-ttu-id="175dc-127">Старайтесь не использовать более двух различных семейств шрифтов в одном контексте.</span><span class="sxs-lookup"><span data-stu-id="175dc-127">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="175dc-128">Это приведет к нарушению гармонии и согласованности вашего опыта и затрудняет использование информации.</span><span class="sxs-lookup"><span data-stu-id="175dc-128">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="175dc-129">В HoloLens, поскольку информация перемещается поверх физической среды, использование слишком большого количества стилей шрифта приведет к ухудшению работы.</span><span class="sxs-lookup"><span data-stu-id="175dc-129">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="175dc-130">Segoe UI — это шрифт для всех цифровых дизайнов Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="175dc-130">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="175dc-131">Он постоянно используется в оболочке Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="175dc-131">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="175dc-132">Файл шрифта Segoe UI можно загрузить на [странице Windows Design Toolkit](https://docs.microsoft.com/windows/uwp/design-downloads/).</span><span class="sxs-lookup"><span data-stu-id="175dc-132">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="175dc-133">Дополнительные сведения о гарнитуре Segoe UI</span><span class="sxs-lookup"><span data-stu-id="175dc-133">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="175dc-134">Избегайте тонких весов шрифтов</span><span class="sxs-lookup"><span data-stu-id="175dc-134">Avoid thin font weights</span></span>

<span data-ttu-id="175dc-135">Старайтесь не использовать насыщенность шрифта Light или Semilight для размеров типов в 42pt, так как тонкие вертикальные штрихи вибрировало и снижают разборчивость.</span><span class="sxs-lookup"><span data-stu-id="175dc-135">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="175dc-136">Современные шрифты с достаточной толщиной обводки хорошо работают.</span><span class="sxs-lookup"><span data-stu-id="175dc-136">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="175dc-137">Например, шрифты Helvetica и Arial очень разборчиво работают в HoloLens с использованием обычных или полужирных весов.</span><span class="sxs-lookup"><span data-stu-id="175dc-137">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="175dc-138">Color</span><span class="sxs-lookup"><span data-stu-id="175dc-138">Color</span></span>

<span data-ttu-id="175dc-139">В HoloLens, так как голограммы созданы с применением аддитивной системы освещения, белый текст очень разборчиво.</span><span class="sxs-lookup"><span data-stu-id="175dc-139">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="175dc-140">Примеры белого текста можно найти в меню "Пуск" и на панели приложений.</span><span class="sxs-lookup"><span data-stu-id="175dc-140">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="175dc-141">Хотя белый текст хорошо работает без резервной формы на HoloLens, сложный физический фон может усложнить чтение типа.</span><span class="sxs-lookup"><span data-stu-id="175dc-141">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="175dc-142">Чтобы улучшить фокус пользователя и уменьшить вычитание из физического фона, мы рекомендуем использовать белый текст на темной или цветной печатной панели.</span><span class="sxs-lookup"><span data-stu-id="175dc-142">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


<span data-ttu-id="175dc-143">![Мы рекомендуем использовать белый текст на темной или цветной печатной панели. ](images/typography-whiteonblack2-1000px.jpg)
 *Примеры белого текста на темной или цветной печатной панели.*</span><span class="sxs-lookup"><span data-stu-id="175dc-143">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="175dc-144">Чтобы использовать темный текст, следует использовать ярко-печатную пластину, чтобы сделать ее доступной для чтения.</span><span class="sxs-lookup"><span data-stu-id="175dc-144">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="175dc-145">В аддитивных цветовых системах черный отображается как прозрачный.</span><span class="sxs-lookup"><span data-stu-id="175dc-145">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="175dc-146">Это означает, что вы не сможете увидеть черный текст без цветной печатной панели.</span><span class="sxs-lookup"><span data-stu-id="175dc-146">This means you will not be able to see the black text without a colored back plate.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="175dc-147">![Примеры черного текста](images/typography-whiteonblack.png)</span><span class="sxs-lookup"><span data-stu-id="175dc-147">![Black text examples](images/typography-whiteonblack.png)</span></span><br>
        <span data-ttu-id="175dc-148">*Примеры белого цвета на черном и черном фоне белого текста*</span><span class="sxs-lookup"><span data-stu-id="175dc-148">*Examples of white on black and black on white text*</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="175dc-149">![Примеры черного текста](images/640px-typography-blackonwhite.jpg)</span><span class="sxs-lookup"><span data-stu-id="175dc-149">![Black text examples](images/640px-typography-blackonwhite.jpg)</span></span><br>
        <span data-ttu-id="175dc-150">*Примеры черного текста в приложениях для хранения и настройки*</span><span class="sxs-lookup"><span data-stu-id="175dc-150">*Examples of black text in the system apps - Store and Settings*</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a><span data-ttu-id="175dc-151">Рекомендуемый размер шрифта</span><span class="sxs-lookup"><span data-stu-id="175dc-151">Recommended font size</span></span>

<span data-ttu-id="175dc-152">Как можно рассчитывать, размеры типов, используемые на ПК или планшетном устройстве (обычно от 12 – отступ), выглядят очень маленькими на расстоянии 2 метров.</span><span class="sxs-lookup"><span data-stu-id="175dc-152">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="175dc-153">Это зависит от характеристик каждого шрифта, но в общем случае рекомендуемый минимальный угол просмотра и высота шрифта для разборчиво 0,35 °-0,4 °/12.21-13.97mm на основе наших исследований исследования пользователей.</span><span class="sxs-lookup"><span data-stu-id="175dc-153">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="175dc-154">Это около 35-40pt с коэффициентом масштабирования, представленным в [тексте на странице Unity](../develop/unity/text-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="175dc-154">It is about 35-40pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md) page.</span></span> 

<span data-ttu-id="175dc-155">Для близкого взаимодействия на 0.45 m (45cm) минимальный угол просмотра и высоту шрифта — 0,4 °-0,5 °/3,14 – 3,9 мм.</span><span class="sxs-lookup"><span data-stu-id="175dc-155">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="175dc-156">Это около 9-12pt с коэффициентом масштабирования, представленным в [тексте в Unity](../develop/unity/text-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="175dc-156">It is about 9-12pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md).</span></span>

<span data-ttu-id="175dc-157">![Содержимое диапазона практически и дальнего взаимодействия ](images/typography-distance-1000px.jpg)
 *в пределах диапазона практически и дальнего взаимодействия*</span><span class="sxs-lookup"><span data-stu-id="175dc-157">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="175dc-158">Минимальный размер неудобочитаемого шрифта</span><span class="sxs-lookup"><span data-stu-id="175dc-158">The minimum legible font size</span></span>
| <span data-ttu-id="175dc-159">расстояние;</span><span class="sxs-lookup"><span data-stu-id="175dc-159">Distance</span></span> | <span data-ttu-id="175dc-160">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="175dc-160">Viewing angle</span></span> | <span data-ttu-id="175dc-161">Высота текста</span><span class="sxs-lookup"><span data-stu-id="175dc-161">Text height</span></span> | <span data-ttu-id="175dc-162">Размер шрифта \* \*</span><span class="sxs-lookup"><span data-stu-id="175dc-162">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="175dc-163">45cm (расстояние прямого манипулирования)</span><span class="sxs-lookup"><span data-stu-id="175dc-163">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="175dc-164">0,4 ° — 0,5 °</span><span class="sxs-lookup"><span data-stu-id="175dc-164">0.4°-0.5°</span></span> | <span data-ttu-id="175dc-165">3,14 — 3,9 мм</span><span class="sxs-lookup"><span data-stu-id="175dc-165">3.14–3.9mm</span></span> | <span data-ttu-id="175dc-166">8.9 — 11.13 PT</span><span class="sxs-lookup"><span data-stu-id="175dc-166">8.9–11.13pt</span></span> |
| <span data-ttu-id="175dc-167">2</span><span class="sxs-lookup"><span data-stu-id="175dc-167">2m</span></span> | <span data-ttu-id="175dc-168">0,35 °-0,4 °</span><span class="sxs-lookup"><span data-stu-id="175dc-168">0.35°-0.4°</span></span> | <span data-ttu-id="175dc-169">12.21 – 13.97 мм</span><span class="sxs-lookup"><span data-stu-id="175dc-169">12.21–13.97mm</span></span> | <span data-ttu-id="175dc-170">34.63-39.58 PT</span><span class="sxs-lookup"><span data-stu-id="175dc-170">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="175dc-171">Удобно, чтобы размер шрифта разборчиво</span><span class="sxs-lookup"><span data-stu-id="175dc-171">The comfortably legible font size</span></span>
| <span data-ttu-id="175dc-172">расстояние;</span><span class="sxs-lookup"><span data-stu-id="175dc-172">Distance</span></span> | <span data-ttu-id="175dc-173">Угол просмотра</span><span class="sxs-lookup"><span data-stu-id="175dc-173">Viewing angle</span></span> | <span data-ttu-id="175dc-174">Высота текста</span><span class="sxs-lookup"><span data-stu-id="175dc-174">Text height</span></span> | <span data-ttu-id="175dc-175">Размер шрифта \* \*</span><span class="sxs-lookup"><span data-stu-id="175dc-175">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="175dc-176">45cm (расстояние прямого манипулирования)</span><span class="sxs-lookup"><span data-stu-id="175dc-176">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="175dc-177">0.65 °-0,8 °</span><span class="sxs-lookup"><span data-stu-id="175dc-177">0.65°-0.8°</span></span> | <span data-ttu-id="175dc-178">5.1 – 6.3 мм</span><span class="sxs-lookup"><span data-stu-id="175dc-178">5.1-6.3mm</span></span> | <span data-ttu-id="175dc-179">14.47-17.8 PT</span><span class="sxs-lookup"><span data-stu-id="175dc-179">14.47-17.8pt</span></span> |
| <span data-ttu-id="175dc-180">2</span><span class="sxs-lookup"><span data-stu-id="175dc-180">2m</span></span> | <span data-ttu-id="175dc-181">0,6 °-0,75 °</span><span class="sxs-lookup"><span data-stu-id="175dc-181">0.6°-0.75°</span></span> | <span data-ttu-id="175dc-182">20,9-26,2 мм</span><span class="sxs-lookup"><span data-stu-id="175dc-182">20.9-26.2mm</span></span> | <span data-ttu-id="175dc-183">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="175dc-183">59.4-74.2pt</span></span> |


<span data-ttu-id="175dc-184">Segoe UI (шрифт по умолчанию для Windows) хорошо работает в большинстве случаев.</span><span class="sxs-lookup"><span data-stu-id="175dc-184">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="175dc-185">Однако старайтесь не использовать светло-или светлое семейство шрифтов в небольшом размере, так как тонкие вертикальные штрихи будут вибрировало, и это приведет к ухудшению читаемости.</span><span class="sxs-lookup"><span data-stu-id="175dc-185">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="175dc-186">Современные шрифты с достаточной толщиной обводки хорошо работают.</span><span class="sxs-lookup"><span data-stu-id="175dc-186">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="175dc-187">Например, Helvetica и Arial выглядят прекрасные и очень разборчиво в HoloLens с обычными или полужирными плотностьми.</span><span class="sxs-lookup"><span data-stu-id="175dc-187">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="175dc-188">**Более подробные сведения о вычислении размера текста в Unity см. в разделе [текст в Unity](../develop/unity/text-in-unity.md) .**</span><span class="sxs-lookup"><span data-stu-id="175dc-188">**For more detailed information about text size calculation in Unity, please refer to [Text in Unity](../develop/unity/text-in-unity.md)**</span></span>

<span data-ttu-id="175dc-189">![Просмотр угла ](images/Text_In_Unity_ViewingAngle.jpg)
 *просмотра расстояния, угла и высоты текста*</span><span class="sxs-lookup"><span data-stu-id="175dc-189">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

<br>

---

## <a name="resources"></a><span data-ttu-id="175dc-190">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="175dc-190">Resources</span></span>

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[<span data-ttu-id="175dc-191">Шрифты Segoe</span><span class="sxs-lookup"><span data-stu-id="175dc-191">Segoe fonts</span></span>](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    <span data-ttu-id="175dc-192">(ZIP-файл)</span><span class="sxs-lookup"><span data-stu-id="175dc-192">(Zip file)</span></span><br>
    ### <a name="hololens-fontbr"></a>[<span data-ttu-id="175dc-193">Шрифт HoloLens</span><span class="sxs-lookup"><span data-stu-id="175dc-193">HoloLens font</span></span>](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    <span data-ttu-id="175dc-194">(ZIP-файл)</span><span class="sxs-lookup"><span data-stu-id="175dc-194">(Zip file)</span></span><br>
    <br>
    <span data-ttu-id="175dc-195">*Изображение. шрифт HoloLens дает вам глифы символов, используемые в Windows Mixed Reality.*</span><span class="sxs-lookup"><span data-stu-id="175dc-195">*Image: The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>
    :::column-end:::
        :::column:::
        ![Шрифт HoloLens предоставляет глифы символов, используемые в Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a><span data-ttu-id="175dc-197">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="175dc-197">See also</span></span>
* [<span data-ttu-id="175dc-198">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="175dc-198">Text in Unity</span></span>](../develop/unity/text-in-unity.md)
* [<span data-ttu-id="175dc-199">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="175dc-199">Color, light and materials</span></span>](../color,-light-and-materials.md)
