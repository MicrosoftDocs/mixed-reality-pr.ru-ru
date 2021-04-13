---
title: Проектирование содержимого для голографического дисплея
description: Ознакомьтесь с рекомендациями по проектированию и рекомендациями по работе с holographic на устройствах HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Проектирование пользовательского интерфейса, holographic, проектирование содержимого, темная тема, светлая тема, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств для смешанной реальности, дизайн, пикселы
ms.openlocfilehash: 325b7bf6318d1b54c4b4c33aa58faea7388e0864
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300039"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="0a36a-104">Проектирование содержимого для голографического дисплея</span><span class="sxs-lookup"><span data-stu-id="0a36a-104">Designing content for holographic display</span></span>

![Расположение с улнар стороны](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="0a36a-106">При проектировании содержимого для более holographic см существует несколько элементов, которые необходимо учитывать для достижения наилучшего опыта.</span><span class="sxs-lookup"><span data-stu-id="0a36a-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="0a36a-107">Ниже мы рассмотрели некоторые из наших рекомендаций, и вы можете узнать больше о характеристиках holographic на странице [цвет, освещение и материалы](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="0a36a-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="0a36a-108">Трудности с ярким цветом на большой поверхности</span><span class="sxs-lookup"><span data-stu-id="0a36a-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="0a36a-109">На основе нашего исследования и тестирования HoloLens мы обнаружили, что использование ярких цветов в большой области экрана может привести к появлению нескольких проблем:</span><span class="sxs-lookup"><span data-stu-id="0a36a-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="0a36a-110">**Выносливости глаз**</span><span class="sxs-lookup"><span data-stu-id="0a36a-110">**Eye fatigue**</span></span> 

<span data-ttu-id="0a36a-111">Так как holographic — аддитивный, голограммы с яркими цветами используют более светлое изображение.</span><span class="sxs-lookup"><span data-stu-id="0a36a-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="0a36a-112">Яркий, однородный цвет в большой области экрана может легко привести к выносливости глазу для пользователя.</span><span class="sxs-lookup"><span data-stu-id="0a36a-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="0a36a-113">**Рука перекрытия**</span><span class="sxs-lookup"><span data-stu-id="0a36a-113">**Hand occlusion**</span></span> 

<span data-ttu-id="0a36a-114">Яркий цвет затрудняет для пользователя возможность видеть свои руки при непосредственном взаимодействии с объектами.</span><span class="sxs-lookup"><span data-stu-id="0a36a-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="0a36a-115">Поскольку пользователь не может видеть свои руки, он затрудняет воспринимать глубину и расстояние между рукой или пальцем на целевую поверхность.</span><span class="sxs-lookup"><span data-stu-id="0a36a-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="0a36a-116">Курсор пальца помогает компенсировать эту ошибку, но по-прежнему может быть непростой на светлой белой поверхности.</span><span class="sxs-lookup"><span data-stu-id="0a36a-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="0a36a-117">![Цвет и рука перекрытия затрудняют прокрасить ](images/color_handocclusion.jpg)
 *руку на экранную отпечатку содержимого*</span><span class="sxs-lookup"><span data-stu-id="0a36a-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="0a36a-118">**Единообразие цвета**</span><span class="sxs-lookup"><span data-stu-id="0a36a-118">**Color uniformity**</span></span>

<span data-ttu-id="0a36a-119">Из-за характеристик holographic дисплеев может стать блотчи большой яркий участок на экране.</span><span class="sxs-lookup"><span data-stu-id="0a36a-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="0a36a-120">Используя темные цветовые схемы, можно избежать этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="0a36a-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="0a36a-121">Рекомендации по проектированию для выбора цвета</span><span class="sxs-lookup"><span data-stu-id="0a36a-121">Design guidelines for color choices</span></span>

<span data-ttu-id="0a36a-122">**Использовать темный цвет для фона пользовательского интерфейса**</span><span class="sxs-lookup"><span data-stu-id="0a36a-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="0a36a-123">С помощью темной цветовой схемы можно сократить выносливости глаз и повысить уверенность в взаимодействии Direct руки.</span><span class="sxs-lookup"><span data-stu-id="0a36a-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="0a36a-124">![Примеры темного цвета, используемые для фона содержимого ](images/color_dark_examples.jpg)
 *примеры темных цветов, используемых для фона содержимого*</span><span class="sxs-lookup"><span data-stu-id="0a36a-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="0a36a-125">**Использовать полужирный или жирный шрифт**</span><span class="sxs-lookup"><span data-stu-id="0a36a-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="0a36a-126">HoloLens позволяет отображать привлекательный текст с высоким разрешением.</span><span class="sxs-lookup"><span data-stu-id="0a36a-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="0a36a-127">Однако рекомендуется избегать тонких весов шрифтов, таких как светлое или частичное освещение, поскольку вертикальные штрихи могут заменяться небольшим размером шрифта.</span><span class="sxs-lookup"><span data-stu-id="0a36a-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="0a36a-128">![Жирный или плотный жирный шрифт (Верхняя панель) улучшает ](images/color_font_examples.jpg)
 *выделение полужирным шрифтом или плотного начертания шрифта (Верхняя панель) улучшает читаемость* .</span><span class="sxs-lookup"><span data-stu-id="0a36a-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="0a36a-129">**Использование Холографикбаккплате материала МРТК**</span><span class="sxs-lookup"><span data-stu-id="0a36a-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="0a36a-130">Материал Холографикбаккплате применяется к нескольким панелям пользовательского интерфейса в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a36a-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="0a36a-131">Одной из его функций является иридесценцеый результат, видимый пользователям при сдвиге их расположения на основе панели.</span><span class="sxs-lookup"><span data-stu-id="0a36a-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="0a36a-132">Цвет экранной формы немного смещается по заранее заданному спектру, создавая эффектный и динамический визуальные эффекты, не мешая удобочитаемости содержимого.</span><span class="sxs-lookup"><span data-stu-id="0a36a-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="0a36a-133">Эта тонкая смена цвета также позволяет компенсировать незначительное нерегулярность цвета.</span><span class="sxs-lookup"><span data-stu-id="0a36a-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="0a36a-134">Трудности с прозрачной или полупрозрачной интерфейсной службой пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="0a36a-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="0a36a-135">![Прозрачные примеры пользовательского интерфейса ](images/color_transparent_examples.jpg)
 *примеры прозрачной формы интерфейса пользователя*</span><span class="sxs-lookup"><span data-stu-id="0a36a-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="0a36a-136">**Сложность и специальные возможности визуального элемента**</span><span class="sxs-lookup"><span data-stu-id="0a36a-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="0a36a-137">С тех пор, как и в случае с физической средой, было бы снижено читаемость содержимого или пользовательского интерфейса в прозрачных или полупрозрачных окнах.</span><span class="sxs-lookup"><span data-stu-id="0a36a-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="0a36a-138">Кроме того, если прозрачные объекты помещаются поверх других, это может усложнить взаимодействие пользователя из-за непонятной глубины.</span><span class="sxs-lookup"><span data-stu-id="0a36a-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="0a36a-139">**Производительность**</span><span class="sxs-lookup"><span data-stu-id="0a36a-139">**Performance**</span></span>

<span data-ttu-id="0a36a-140">Чтобы прозрачные или полупрозрачные объекты отображались правильно, они должны быть отсортированы и смешиваться с любыми объектами, которые существуют в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="0a36a-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="0a36a-141">Сортировка прозрачных объектов требует снижения затрат ресурсов ЦП, так как смешивание имеет существенные затраты на GPU, так как не позволяет GPU выполнять скрытое удаление поверхности через z-отбор (т. е.</span><span class="sxs-lookup"><span data-stu-id="0a36a-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="0a36a-142">Тестирование глубины).</span><span class="sxs-lookup"><span data-stu-id="0a36a-142">depth testing).</span></span> <span data-ttu-id="0a36a-143">Отсутствие разрешения на удаление скрытой поверхности увеличивает количество операций, необходимых для окончательной отрисовки пикселя.</span><span class="sxs-lookup"><span data-stu-id="0a36a-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="0a36a-144">Это обеспечивает дополнительные ограничения частоты заполнения.</span><span class="sxs-lookup"><span data-stu-id="0a36a-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="0a36a-145">**Нестабильность с голограммами с ЛСР технологией глубины**</span><span class="sxs-lookup"><span data-stu-id="0a36a-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="0a36a-146">Для повышения стабильной репроецирования или голограммы в области стабильности приложение может отправить в систему буфер глубины для каждого отображаемого кадра.</span><span class="sxs-lookup"><span data-stu-id="0a36a-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="0a36a-147">При использовании буфера глубины для РЕПРОЕКЦИИ необходимо написать буфер глубины для каждого отображаемого цвета в пикселях соответствующей глубины.</span><span class="sxs-lookup"><span data-stu-id="0a36a-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="0a36a-148">Любой пиксель с значением глубины также должен иметь значение Color.</span><span class="sxs-lookup"><span data-stu-id="0a36a-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="0a36a-149">Если приведенное выше руководство не соблюдается, области готовых к просмотру образа, в которых отсутствуют допустимые сведения о глубине, могут быть переработаны таким образом, что создает артефакты, которые часто отображаются как искажения в виде волнового вида.</span><span class="sxs-lookup"><span data-stu-id="0a36a-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="0a36a-150">Рекомендации по проектированию прозрачных элементов</span><span class="sxs-lookup"><span data-stu-id="0a36a-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="0a36a-151">**Использовать прозрачный фон пользовательского интерфейса**</span><span class="sxs-lookup"><span data-stu-id="0a36a-151">**Use opaque UI background**</span></span>

<span data-ttu-id="0a36a-152">По умолчанию прозрачные или полупрозрачные объекты не записывают глубину, чтобы обеспечить правильное смешение.</span><span class="sxs-lookup"><span data-stu-id="0a36a-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="0a36a-153">Способы устранения этой проблемы: использование непрозрачных объектов, обеспечение того, что прозрачные объекты появляются близко к непрозрачным объектам (например, полупрозрачную кнопку перед непрозрачной заменой), заставляя прозрачные объекты для записи глубины (неприменимы во всех сценариях) или выводят объекты прокси-сервера, которые вносят в конец фрейма только значения глубины.</span><span class="sxs-lookup"><span data-stu-id="0a36a-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="0a36a-154">Решения в МРТК — Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="0a36a-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="0a36a-155">Используя сплошную и непрозрачную форму, можно защититься от четкости и уверенности в взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="0a36a-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="0a36a-156">**Уменьшение количества затронутых пикселов**</span><span class="sxs-lookup"><span data-stu-id="0a36a-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="0a36a-157">Если проект должен использовать прозрачные объекты, попробуйте максимально ограничить число затронутых пикселов.</span><span class="sxs-lookup"><span data-stu-id="0a36a-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="0a36a-158">Например, если объект отображается только при определенных условиях (например, в эффекте свечения), отключите объект, если он полностью невидимый (вместо присвоения цвету аддитивного цвета черному).</span><span class="sxs-lookup"><span data-stu-id="0a36a-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="0a36a-159">Для простых двумерных фигур, созданных с помощью «Quad» с альфа-маской, рассмотрите возможность создания сетки фигуры с непрозрачным шейдером.</span><span class="sxs-lookup"><span data-stu-id="0a36a-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0a36a-160">Темные примеры пользовательского интерфейса в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="0a36a-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="0a36a-161">**[Мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** предоставляет множество примеров стандартных блоков пользовательского интерфейса на основе темных цветовых схем.</span><span class="sxs-lookup"><span data-stu-id="0a36a-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="0a36a-162">Ближайшее меню</span><span class="sxs-lookup"><span data-stu-id="0a36a-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="0a36a-163">Диалоговое окно</span><span class="sxs-lookup"><span data-stu-id="0a36a-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="0a36a-164">Меню руки</span><span class="sxs-lookup"><span data-stu-id="0a36a-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="0a36a-165">См. также</span><span class="sxs-lookup"><span data-stu-id="0a36a-165">See also</span></span>

* [<span data-ttu-id="0a36a-166">Цвет, свет и материалы</span><span class="sxs-lookup"><span data-stu-id="0a36a-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="0a36a-167">Курсоры</span><span class="sxs-lookup"><span data-stu-id="0a36a-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0a36a-168">Телекинез</span><span class="sxs-lookup"><span data-stu-id="0a36a-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="0a36a-169">Кнопка</span><span class="sxs-lookup"><span data-stu-id="0a36a-169">Button</span></span>](button.md)
* [<span data-ttu-id="0a36a-170">Активный объект</span><span class="sxs-lookup"><span data-stu-id="0a36a-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0a36a-171">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="0a36a-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="0a36a-172">Оперирование</span><span class="sxs-lookup"><span data-stu-id="0a36a-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0a36a-173">Меню руки</span><span class="sxs-lookup"><span data-stu-id="0a36a-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="0a36a-174">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="0a36a-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="0a36a-175">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="0a36a-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="0a36a-176">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="0a36a-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="0a36a-177">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="0a36a-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="0a36a-178">Подсказка</span><span class="sxs-lookup"><span data-stu-id="0a36a-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="0a36a-179">Планшет</span><span class="sxs-lookup"><span data-stu-id="0a36a-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="0a36a-180">Ползунок</span><span class="sxs-lookup"><span data-stu-id="0a36a-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="0a36a-181">Шейдер</span><span class="sxs-lookup"><span data-stu-id="0a36a-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="0a36a-182">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="0a36a-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="0a36a-183">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="0a36a-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="0a36a-184">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="0a36a-184">Surface magnetism</span></span>](surface-magnetism.md)
