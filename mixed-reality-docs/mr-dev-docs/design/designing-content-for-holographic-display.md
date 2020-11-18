---
title: Проектирование содержимого для голографического дисплея
description: Рекомендации по проектированию и рекомендации для holographic
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Проектирование пользовательского интерфейса, holographic, проектирование содержимого, темная тема, светлая тема, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, дизайн, пикселы
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702640"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="b8b53-104">Проектирование содержимого для голографического дисплея</span><span class="sxs-lookup"><span data-stu-id="b8b53-104">Designing content for holographic display</span></span>

![Расположение с улнар стороны](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="b8b53-106">При проектировании содержимого для более holographic см существует несколько элементов, которые необходимо учитывать для достижения наилучшего опыта.</span><span class="sxs-lookup"><span data-stu-id="b8b53-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="b8b53-107">Ниже мы рассмотрели некоторые из наших рекомендаций, и вы можете узнать больше о характеристиках holographic на странице [цвет, освещение и материалы](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="b8b53-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="b8b53-108">Трудности с ярким цветом на большой поверхности</span><span class="sxs-lookup"><span data-stu-id="b8b53-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="b8b53-109">Основываясь на исследовании пользователей и тестировании на различных типах возможностей HoloLens, мы обнаружили, что использование ярких цветов в большой области экрана может привести к появлению нескольких проблем:</span><span class="sxs-lookup"><span data-stu-id="b8b53-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="b8b53-110">**Выносливости глаз**</span><span class="sxs-lookup"><span data-stu-id="b8b53-110">**Eye fatigue**</span></span> 

<span data-ttu-id="b8b53-111">Так как holographic-дисплей является аддитивным, яркий цвет использует более светлое изображение для показа голограмм.</span><span class="sxs-lookup"><span data-stu-id="b8b53-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="b8b53-112">Яркий, однородный цвет в большой области экрана может легко привести к выносливости глазу для пользователя.</span><span class="sxs-lookup"><span data-stu-id="b8b53-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="b8b53-113">**Рука перекрытия**</span><span class="sxs-lookup"><span data-stu-id="b8b53-113">**Hand occlusion**</span></span> 

<span data-ttu-id="b8b53-114">Яркий цвет затрудняет для пользователя возможность видеть свои руки при непосредственном взаимодействии с объектами.</span><span class="sxs-lookup"><span data-stu-id="b8b53-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="b8b53-115">Поскольку пользователь не может видеть свои руки, он затрудняет воспринимать глубину и расстояние между рукой или пальцем на целевую поверхность.</span><span class="sxs-lookup"><span data-stu-id="b8b53-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="b8b53-116">Курсор пальца помогает компенсировать эту ошибку, но по-прежнему может быть непростой на светлой белой поверхности.</span><span class="sxs-lookup"><span data-stu-id="b8b53-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="b8b53-117">![Цвет и рука перекрытия затрудняют прокрасить ](images/color_handocclusion.jpg)
 *руку на экранную отпечатку содержимого*</span><span class="sxs-lookup"><span data-stu-id="b8b53-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="b8b53-118">**Единообразие цвета**</span><span class="sxs-lookup"><span data-stu-id="b8b53-118">**Color uniformity**</span></span>

<span data-ttu-id="b8b53-119">Из-за характеристик holographic дисплеев может стать блотчи большой яркий участок на экране.</span><span class="sxs-lookup"><span data-stu-id="b8b53-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="b8b53-120">Используя темные цветовые схемы, можно избежать этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="b8b53-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="b8b53-121">Рекомендации по проектированию</span><span class="sxs-lookup"><span data-stu-id="b8b53-121">Design guidelines</span></span>

<span data-ttu-id="b8b53-122">**Использовать темный цвет для фона пользовательского интерфейса**</span><span class="sxs-lookup"><span data-stu-id="b8b53-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="b8b53-123">С помощью темной цветовой схемы можно сократить выносливости глаз и повысить уверенность в взаимодействии Direct руки.</span><span class="sxs-lookup"><span data-stu-id="b8b53-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="b8b53-124">![Темные примеры пользовательского интерфейса ](images/color_dark_examples.jpg)
 *примеры темного цвета, используемые для фона содержимого*</span><span class="sxs-lookup"><span data-stu-id="b8b53-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="b8b53-125">**Использовать полужирный или жирный шрифт**</span><span class="sxs-lookup"><span data-stu-id="b8b53-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="b8b53-126">HoloLens позволяет отображать привлекательный текст с высоким разрешением.</span><span class="sxs-lookup"><span data-stu-id="b8b53-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="b8b53-127">Однако рекомендуется избегать тонких весов шрифтов, например светлой или частичной плотности, поскольку вертикальные штрихи могут заменяться небольшим размером шрифта.</span><span class="sxs-lookup"><span data-stu-id="b8b53-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="b8b53-128">![Темные примеры пользовательского интерфейса ](images/color_font_examples.jpg)
 *полужирный или плотный шрифт (Верхняя панель) улучшает читаемость*</span><span class="sxs-lookup"><span data-stu-id="b8b53-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="b8b53-129">**Использование Холографикбаккплате материала МРТК**</span><span class="sxs-lookup"><span data-stu-id="b8b53-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="b8b53-130">Материал Холографикбаккплате применяется к нескольким панелям пользовательского интерфейса в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b8b53-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="b8b53-131">Одной из его функций является иридесценцеый результат, видимый пользователям по мере сдвига их расположения относительно панели.</span><span class="sxs-lookup"><span data-stu-id="b8b53-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="b8b53-132">Цвет экранной формы немного смещается по заранее заданному спектру, создавая эффектный и динамический визуальные эффекты, не мешая удобочитаемости содержимого.</span><span class="sxs-lookup"><span data-stu-id="b8b53-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="b8b53-133">Эта тонкая смена цвета также позволяет компенсировать незначительное нерегулярность цвета.</span><span class="sxs-lookup"><span data-stu-id="b8b53-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="b8b53-134">Трудности с прозрачной или полупрозрачной интерфейсной службой пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="b8b53-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="b8b53-135">![Прозрачные примеры пользовательского интерфейса ](images/color_transparent_examples.jpg)
 *примеры прозрачной формы интерфейса пользователя*</span><span class="sxs-lookup"><span data-stu-id="b8b53-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="b8b53-136">**Сложность и специальные возможности визуального элемента**</span><span class="sxs-lookup"><span data-stu-id="b8b53-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="b8b53-137">Поскольку holographic объектов смешиваются с физической средой, может быть снижена читаемость содержимого или пользовательского интерфейса в прозрачном или полупрозрачном окне.</span><span class="sxs-lookup"><span data-stu-id="b8b53-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="b8b53-138">Кроме того, если прозрачные объекты помещаются поверх других, это может усложнить взаимодействие пользователя из-за непонятной глубины.</span><span class="sxs-lookup"><span data-stu-id="b8b53-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="b8b53-139">**Производительность**</span><span class="sxs-lookup"><span data-stu-id="b8b53-139">**Performance**</span></span>

<span data-ttu-id="b8b53-140">Чтобы прозрачные или полупрозрачные объекты отображались правильно, они должны быть отсортированы и смешиваться с любыми объектами, которые существуют в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="b8b53-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="b8b53-141">Сортировка прозрачных объектов требует снижения затрат ресурсов ЦП, так как смешивание имеет существенные затраты на GPU, так как не позволяет GPU выполнять скрытое удаление поверхности с помощью исключения z (т. е.</span><span class="sxs-lookup"><span data-stu-id="b8b53-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="b8b53-142">Тестирование глубины).</span><span class="sxs-lookup"><span data-stu-id="b8b53-142">depth testing).</span></span> <span data-ttu-id="b8b53-143">Отсутствие разрешения на удаление скрытой поверхности увеличивает количество операций, которые необходимо вычислить для окончательного визуализированного пикселя, и тем самым накладывает большую нагрузку на ограничения скорости заполнения.</span><span class="sxs-lookup"><span data-stu-id="b8b53-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="b8b53-144">**Нестабильность с голограммами с ЛСР технологией глубины**</span><span class="sxs-lookup"><span data-stu-id="b8b53-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="b8b53-145">Для повышения стабильной репроецирования или голограммы в области стабильности приложение может отправить в систему буфер глубины для каждого отображаемого кадра.</span><span class="sxs-lookup"><span data-stu-id="b8b53-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="b8b53-146">При использовании буфера глубины для РЕПРОЕКЦИИ одно правило состоит в том, что для каждого цветового пикселя, отображаемого в качестве значения глубины, должно быть записано в буфер глубины (а в любом пикселе со значением глубины также должно быть значение цвета).</span><span class="sxs-lookup"><span data-stu-id="b8b53-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="b8b53-147">Если приведенное выше руководство не соблюдается, области подготовленного к просмотру изображения, которые не имеют допустимых сведений о глубине, могут быть перепроецированы таким образом, что создает артефакты (часто отображаются как искажения в виде волнового типа).</span><span class="sxs-lookup"><span data-stu-id="b8b53-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="b8b53-148">Рекомендации по проектированию</span><span class="sxs-lookup"><span data-stu-id="b8b53-148">Design guidelines</span></span>
<span data-ttu-id="b8b53-149">**Использовать прозрачный фон пользовательского интерфейса**</span><span class="sxs-lookup"><span data-stu-id="b8b53-149">**Use opaque UI background**</span></span>

<span data-ttu-id="b8b53-150">По умолчанию прозрачные или полупрозрачные объекты не записывают глубину, чтобы обеспечить правильное смешение.</span><span class="sxs-lookup"><span data-stu-id="b8b53-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="b8b53-151">Способы устранения этой проблемы: использование непрозрачных объектов, обеспечение того, что прозрачные объекты появляются близко к непрозрачным объектам (например, полупрозрачную кнопку перед непрозрачной заменой), заставляя прозрачные объекты для записи глубины (неприменимы во всех сценариях) или выводят объекты прокси, которые вносят в конец фрейма только значения глубины.</span><span class="sxs-lookup"><span data-stu-id="b8b53-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="b8b53-152">Решения в МРТК — Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="b8b53-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="b8b53-153">Используя сплошную и непрозрачную форму, можно защититься от четкости и уверенности в взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="b8b53-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="b8b53-154">**Уменьшение количества затронутых пикселов**</span><span class="sxs-lookup"><span data-stu-id="b8b53-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="b8b53-155">Если проект должен использовать прозрачные объекты, попробуйте максимально ограничить число затронутых пикселов.</span><span class="sxs-lookup"><span data-stu-id="b8b53-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="b8b53-156">Например, если объект отображается только при определенных условиях (например, в эффекте свечения), отключите объект, если он полностью невидимый (вместо присвоения цвету аддитивного цвета черному).</span><span class="sxs-lookup"><span data-stu-id="b8b53-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="b8b53-157">Для простых двумерных фигур, созданных с помощью «Quad» с альфа-маской, рассмотрите возможность создания сетки фигуры с непрозрачным шейдером.</span><span class="sxs-lookup"><span data-stu-id="b8b53-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="b8b53-158">Темные примеры пользовательского интерфейса в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="b8b53-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="b8b53-159">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет множество примеров стандартных блоков пользовательского интерфейса на основе темных цветовых схем.</span><span class="sxs-lookup"><span data-stu-id="b8b53-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="b8b53-160">Ближайшее меню</span><span class="sxs-lookup"><span data-stu-id="b8b53-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="b8b53-161">Диалоговое окно</span><span class="sxs-lookup"><span data-stu-id="b8b53-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="b8b53-162">Меню руки</span><span class="sxs-lookup"><span data-stu-id="b8b53-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="b8b53-163">См. также</span><span class="sxs-lookup"><span data-stu-id="b8b53-163">See also</span></span>
* [<span data-ttu-id="b8b53-164">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="b8b53-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="b8b53-165">Курсоры</span><span class="sxs-lookup"><span data-stu-id="b8b53-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b8b53-166">Телекинез</span><span class="sxs-lookup"><span data-stu-id="b8b53-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="b8b53-167">Кнопка</span><span class="sxs-lookup"><span data-stu-id="b8b53-167">Button</span></span>](button.md)
* [<span data-ttu-id="b8b53-168">Активный объект</span><span class="sxs-lookup"><span data-stu-id="b8b53-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b8b53-169">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="b8b53-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b8b53-170">Оперирование</span><span class="sxs-lookup"><span data-stu-id="b8b53-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b8b53-171">Меню руки</span><span class="sxs-lookup"><span data-stu-id="b8b53-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="b8b53-172">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="b8b53-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="b8b53-173">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="b8b53-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b8b53-174">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="b8b53-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="b8b53-175">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="b8b53-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="b8b53-176">Подсказка</span><span class="sxs-lookup"><span data-stu-id="b8b53-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="b8b53-177">Планшет</span><span class="sxs-lookup"><span data-stu-id="b8b53-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="b8b53-178">Ползунок</span><span class="sxs-lookup"><span data-stu-id="b8b53-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="b8b53-179">Шейдер</span><span class="sxs-lookup"><span data-stu-id="b8b53-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="b8b53-180">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="b8b53-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b8b53-181">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="b8b53-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="b8b53-182">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="b8b53-182">Surface magnetism</span></span>](surface-magnetism.md)
