---
title: Курсоры
description: Курсор или индикатор целевого вектора обеспечивает непрерывную обратную связь пользователя, чтобы понять, что HoloLens понимает о своих намерения.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1-й общий), HoloLens 2, Смешанная реальность, курсоры, нацеленность, взгляд, жесты, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, лучи, входные данные
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582400"
---
# <a name="cursors"></a><span data-ttu-id="baf32-104">Курсоры</span><span class="sxs-lookup"><span data-stu-id="baf32-104">Cursors</span></span>

![Курсоры](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="baf32-106">Курсор обеспечивает непрерывную обратную связь в зависимости от того, где гарнитура считает, что текущий фокус находится на текущем этапе.</span><span class="sxs-lookup"><span data-stu-id="baf32-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="baf32-107">Обратная связь курсора включает в себя область, голограмму или точку в виртуальной среде, которая реагирует на входные данные.</span><span class="sxs-lookup"><span data-stu-id="baf32-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="baf32-108">Несмотря на то, что курсор является цифровым представлением, где устройство понимает внимание пользователя, это не то же самое, что определение намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="baf32-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="baf32-109">Обратная связь курсора также позволяет пользователям узнать, какие системные ответы следует рассчитывать.</span><span class="sxs-lookup"><span data-stu-id="baf32-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="baf32-110">Вы можете использовать отзыв, чтобы сообщить о своем намерении на устройство, что повышает уверенность пользователей.</span><span class="sxs-lookup"><span data-stu-id="baf32-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="baf32-111">Существует три вида курсоров: **палец, луч** и **head-взгляд**.</span><span class="sxs-lookup"><span data-stu-id="baf32-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="baf32-112">Эти курсоры работают с различными входными модальностей на HoloLens, HoloLens 2 и впечатляющих гарнитурах.</span><span class="sxs-lookup"><span data-stu-id="baf32-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="baf32-113">Ниже приведены рекомендации по использованию типа курсора для каждого типа гарнитуры и модели взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="baf32-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="baf32-114">В наборе средств для смешанной реальности (МРТК) мы создали модули курсоров с поддержкой перетаскивания, которые помогут вам создать правильный указатель мыши.</span><span class="sxs-lookup"><span data-stu-id="baf32-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="baf32-115">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="baf32-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="baf32-116"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="baf32-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="baf32-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="baf32-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="baf32-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="baf32-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="baf32-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="baf32-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="baf32-120">Курсор пальца</span><span class="sxs-lookup"><span data-stu-id="baf32-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="baf32-121">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="baf32-122">Лучающий курсор</span><span class="sxs-lookup"><span data-stu-id="baf32-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="baf32-123">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-123">✔️</span></span></td>
        <td><span data-ttu-id="baf32-124">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="baf32-125">Курсор Head</span><span class="sxs-lookup"><span data-stu-id="baf32-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="baf32-126">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-126">✔️</span></span></td>
        <td><span data-ttu-id="baf32-127">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-127">✔️</span></span></td>
        <td><span data-ttu-id="baf32-128">✔️</span><span class="sxs-lookup"><span data-stu-id="baf32-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="baf32-129">Курсор пальца</span><span class="sxs-lookup"><span data-stu-id="baf32-129">Finger cursor</span></span>

<span data-ttu-id="baf32-130">Курсор пальца доступен только в HoloLens 2, чтобы улучшить режим взаимодействия «[непосредственное управление](direct-manipulation.md)».</span><span class="sxs-lookup"><span data-stu-id="baf32-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="baf32-131">Мы присоединенные кольца к советам по обоим указателям, чтобы лучше понять, где наводится указатель мыши.</span><span class="sxs-lookup"><span data-stu-id="baf32-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="baf32-132">Размер кольца зависит от расстояния пальца к поверхности пользовательского интерфейса, который сжимается до маленькой точки, когда палец касается пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="baf32-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="baf32-133">Чем ближе палец, тем меньше кольцо.</span><span class="sxs-lookup"><span data-stu-id="baf32-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="baf32-134">![курсор пальца](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="baf32-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="baf32-135">**Визуальные состояния обратной связи для курсора "палец** " 1: кольцо сжимается до точки.</span><span class="sxs-lookup"><span data-stu-id="baf32-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="baf32-136">2: кольцо соответствует поверхности.</span><span class="sxs-lookup"><span data-stu-id="baf32-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="baf32-137">3: кольцо перпендикулярно вектору пальца.</span><span class="sxs-lookup"><span data-stu-id="baf32-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="baf32-138">4: нет кольца.</span><span class="sxs-lookup"><span data-stu-id="baf32-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="baf32-139">Лучающий курсор</span><span class="sxs-lookup"><span data-stu-id="baf32-139">Ray cursor</span></span>

<span data-ttu-id="baf32-140">Курсоры типа «луч» присоединяются к концу дальней точки, чтобы разрешить манипуляции с объектами, находящиеся за пределами руки.</span><span class="sxs-lookup"><span data-stu-id="baf32-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="baf32-141">В впечатляющих головных гарнитурах лучи прокрутки от контроллеров движения и заканчиваются курсорами точки.</span><span class="sxs-lookup"><span data-stu-id="baf32-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="baf32-142">В HoloLens 2 мы применяем модель для этих лучающих контроллеров движения и готовые лучи, которые берутся из Палмс и заканчиваются курсорами в форме круга, которые согласуются с курсорами пальца, используемыми в непосредственной манипуляции.</span><span class="sxs-lookup"><span data-stu-id="baf32-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="baf32-143">![Контроллер курсора Ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="baf32-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="baf32-144">**Лучаовые курсоры контроллеров движения**</span><span class="sxs-lookup"><span data-stu-id="baf32-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="baf32-145">![Рука с курсором луч](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="baf32-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="baf32-146">**Лучающие курсоры**</span><span class="sxs-lookup"><span data-stu-id="baf32-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="baf32-147">Курсор Head</span><span class="sxs-lookup"><span data-stu-id="baf32-147">Head-gaze cursor</span></span>

<span data-ttu-id="baf32-148">Курсор «Heading-взгляд» — это точка, которая подключается к концу невидимого вектора «Head-взгляд», который использует позицию и поворот головной точки.</span><span class="sxs-lookup"><span data-stu-id="baf32-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="baf32-149">Для выполнения действий этот указывающий курсор связывается с различными входными данными фиксации, такими как воздушное касание, Voice Commands, вдаваясь и нажатие кнопки.</span><span class="sxs-lookup"><span data-stu-id="baf32-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="baf32-150">В HoloLens 2 лучше всего связать с любым вводом фиксации, который не является воздушным приводами, так как между воздушным приводами и дальней наладоней возникает конфликт взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="baf32-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="baf32-151">![Рука курсора с заголовком](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="baf32-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="baf32-152">**Курсор в виде заголовка с помощью жеста руки**</span><span class="sxs-lookup"><span data-stu-id="baf32-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="baf32-153">![Проголосующий курсор головного взгляда](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="baf32-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="baf32-154">**Курсор в виде заголовка с голосовым командой**</span><span class="sxs-lookup"><span data-stu-id="baf32-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="baf32-155">Рекомендации по настройке курсора</span><span class="sxs-lookup"><span data-stu-id="baf32-155">Cursor customization recommendations</span></span>

<span data-ttu-id="baf32-156">Если вы хотите настроить поведение и внешний вид обратной связи с курсором, ниже приведены некоторые рекомендации по проектированию.</span><span class="sxs-lookup"><span data-stu-id="baf32-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="baf32-157">Масштабирование курсора</span><span class="sxs-lookup"><span data-stu-id="baf32-157">Cursor scale</span></span>

* <span data-ttu-id="baf32-158">Курсор должен быть не больше доступных целевых объектов, что позволяет пользователям легко взаимодействовать с содержимым и просматривать его.</span><span class="sxs-lookup"><span data-stu-id="baf32-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="baf32-159">В зависимости от того, что вы создаете, масштабирование курсора по мере того, как пользователь смотрит, также является важным фактором.</span><span class="sxs-lookup"><span data-stu-id="baf32-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="baf32-160">Например, по мере того, как пользователь просматривает свой опыт, курсор не должен стать слишком маленьким, чтобы он был потерян.</span><span class="sxs-lookup"><span data-stu-id="baf32-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="baf32-161">При масштабировании курсора рассмотрите возможность применения мягкой анимации к ней при масштабировании, чтобы придать ему ощущение.</span><span class="sxs-lookup"><span data-stu-id="baf32-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="baf32-162">Избегайте неблизкого содержимого.</span><span class="sxs-lookup"><span data-stu-id="baf32-162">Avoid obstructing content.</span></span> <span data-ttu-id="baf32-163">Голограммы — это то, что делает ваш опыт, и курсор не должен быть взят от них.</span><span class="sxs-lookup"><span data-stu-id="baf32-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="baf32-164">Форма двунаправленного курсора</span><span class="sxs-lookup"><span data-stu-id="baf32-164">Directionless cursor shape</span></span>

* <span data-ttu-id="baf32-165">Хотя ни одна фигура с правой стороны не существует, рекомендуется использовать форму без направления, такую как Торус.</span><span class="sxs-lookup"><span data-stu-id="baf32-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="baf32-166">Курсор, указывающий в каком-либо направлении (например, в традиционном курсоре со стрелкой), может запутать пользователя, чтобы всегда выглядеть таким образом.</span><span class="sxs-lookup"><span data-stu-id="baf32-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="baf32-167">Исключением является использование курсора для обмена инструкциями взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="baf32-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="baf32-168">Например, при масштабировании голограмм в операционной системе Mixed Reality курсор временно включает стрелки, указывающие пользователю, как переместить руку, чтобы масштабировать голограмму.</span><span class="sxs-lookup"><span data-stu-id="baf32-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="baf32-169">Внешний вид</span><span class="sxs-lookup"><span data-stu-id="baf32-169">Look and feel</span></span>

* <span data-ttu-id="baf32-170">Курсор в форме кольца или Торус работает для многих приложений.</span><span class="sxs-lookup"><span data-stu-id="baf32-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="baf32-171">Выберите цвет и форму, которые наилучшим образом представляют создаваемые вами возможности.</span><span class="sxs-lookup"><span data-stu-id="baf32-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="baf32-172">Курсоры особенно уязвимы для [разделения цветов](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="baf32-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="baf32-173">Небольшой курсор с сбалансированной непрозрачностью обеспечивает ИТ-подсистему, не наполняя визуальную иерархию.</span><span class="sxs-lookup"><span data-stu-id="baf32-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="baf32-174">Компания cognizant с помощью теней или выделений, расположенных за курсором, так как они могут помешать содержимому и отвлечь за собой ненужные задачи.</span><span class="sxs-lookup"><span data-stu-id="baf32-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="baf32-175">Курсоры должны выстроиться и Хуг поверхности в приложении.</span><span class="sxs-lookup"><span data-stu-id="baf32-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="baf32-176">Пользователи будут иметь ощущение, что система сможет увидеть, где они ищутся, но также что система осведомлена о своей окружающей обстановке.</span><span class="sxs-lookup"><span data-stu-id="baf32-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="baf32-177">Например, курсор в ОС Mixed Reality соответствует поверхности мира пользователя, создавая привлекательность мира, даже если пользователь не смотрит непосредственно на голограмме.</span><span class="sxs-lookup"><span data-stu-id="baf32-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="baf32-178">Магнитная Блокировка курсора на интерактивный элемент, когда он близко к пользователю, может помочь улучшить уверенность в том, что пользователь будет взаимодействовать с этим элементом при использовании действия выбора.</span><span class="sxs-lookup"><span data-stu-id="baf32-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="baf32-179">Визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="baf32-179">Visual cues</span></span>

* <span data-ttu-id="baf32-180">Если ваш опыт сосредоточен на одной голограмме, то курсор должен выдать и Хуг только эту голограмму и изменить форму, когда вы пройдете с этой голограммы.</span><span class="sxs-lookup"><span data-stu-id="baf32-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="baf32-181">Это может передать пользователю, что голограмма является практичной и может взаимодействовать с ней.</span><span class="sxs-lookup"><span data-stu-id="baf32-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="baf32-182">Если приложение использует пространственное сопоставление, то курсор может выстроиться и Хуг каждую отображаемую им поверхность.</span><span class="sxs-lookup"><span data-stu-id="baf32-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="baf32-183">Это дает отзыв пользователям, которые HoloLens и приложение могут видеть свое пространство.</span><span class="sxs-lookup"><span data-stu-id="baf32-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="baf32-184">Это усиливает тот факт, что голограммы являются реальными и в нашем мире, и помогают преодолеть разрыв между реальными и виртуальными.</span><span class="sxs-lookup"><span data-stu-id="baf32-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="baf32-185">Иметь представление о том, что должен делать курсор при отсутствии голограмм или поверхностей в представлении.</span><span class="sxs-lookup"><span data-stu-id="baf32-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="baf32-186">Его размещение на заранее определенном расстоянии перед пользователем является одним из вариантов.</span><span class="sxs-lookup"><span data-stu-id="baf32-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="baf32-187">Возможные действия</span><span class="sxs-lookup"><span data-stu-id="baf32-187">Possible actions</span></span>

* <span data-ttu-id="baf32-188">Курсор может быть представлен разными значками для передачи возможных действий, которые может сделать голограмма, например, масштабирования или вращения.</span><span class="sxs-lookup"><span data-stu-id="baf32-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="baf32-189">Добавляйте в курсор дополнительные сведения, если это означает что-то для пользователя.</span><span class="sxs-lookup"><span data-stu-id="baf32-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="baf32-190">В противном случае пользователи могут не заметить изменения состояния или выпутать курсор.</span><span class="sxs-lookup"><span data-stu-id="baf32-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="baf32-191">Входное состояние</span><span class="sxs-lookup"><span data-stu-id="baf32-191">Input state</span></span>

* <span data-ttu-id="baf32-192">Можно использовать курсор для отображения состояния или намерений ввода пользователя.</span><span class="sxs-lookup"><span data-stu-id="baf32-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="baf32-193">Например, можно отобразить значок, сообщающий пользователю, что система видит свое состояние, и что приложение знает, что они готовы принять меры.</span><span class="sxs-lookup"><span data-stu-id="baf32-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="baf32-194">Можно также использовать курсор для отображения пользователей, которые система прослышала системой с помощью изменения цвета</span><span class="sxs-lookup"><span data-stu-id="baf32-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="baf32-195">Следующие состояния курсора могут быть реализованы различными способами.</span><span class="sxs-lookup"><span data-stu-id="baf32-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="baf32-196">Вы можете реализовать эти различные состояния, моделирующие курсор как конечный автомат.</span><span class="sxs-lookup"><span data-stu-id="baf32-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="baf32-197">Пример:</span><span class="sxs-lookup"><span data-stu-id="baf32-197">For example:</span></span>
    * <span data-ttu-id="baf32-198">Состояние простоя показывает курсор по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="baf32-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="baf32-199">Состояние готовности — когда вы обнаружили руку пользователя в месте готовности.</span><span class="sxs-lookup"><span data-stu-id="baf32-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="baf32-200">Состояние взаимодействия — это когда пользователь выполняет определенное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="baf32-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="baf32-201">Состояние возможных действий или состояние наведения указателя — это то, что можно передать возможные действия, которые могут быть выполнены на голограмме.</span><span class="sxs-lookup"><span data-stu-id="baf32-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="baf32-202">Эти состояния также можно реализовать с помощью обложки, способной отображать различные графические ресурсы при обнаружении различных состояний.</span><span class="sxs-lookup"><span data-stu-id="baf32-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="baf32-203">Переход на «свободный курсор»</span><span class="sxs-lookup"><span data-stu-id="baf32-203">Going "cursor-free"</span></span>

<span data-ttu-id="baf32-204">Проектирование без курсора рекомендуется, если смысл возникнет в качестве ключевого компонента интерфейса и при указании взаимодействия (с помощью взгляда и жеста) не требуется значительная точность.</span><span class="sxs-lookup"><span data-stu-id="baf32-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="baf32-205">Система по-прежнему должна соответствовать обычным требованиям курсора: предоставление пользователям непрерывной обратной связи по пониманию системы и помощь им в обеспечении своих целей к системе.</span><span class="sxs-lookup"><span data-stu-id="baf32-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="baf32-206">Это может быть достижимо с помощью других заметных изменений состояния.</span><span class="sxs-lookup"><span data-stu-id="baf32-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="baf32-207">Курсор в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="baf32-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="baf32-208">По умолчанию [мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity) предоставляет курсор prefab ([дефаулткурсор. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)), который имеет то же визуальное состояние, что и системный курсор оболочки.</span><span class="sxs-lookup"><span data-stu-id="baf32-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="baf32-209">Она назначается в профиле ввода данных в MRTK, в разделе "Указатели".</span><span class="sxs-lookup"><span data-stu-id="baf32-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="baf32-210">Вы можете заменить или настроить этот курсор для работы.</span><span class="sxs-lookup"><span data-stu-id="baf32-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="baf32-211">Для удобства ввода с отслеживанием взгляда МРТК также предоставляет Эйегазекурсор, который имеет тонкий визуальный элемент, позволяющий избежать вычитания.</span><span class="sxs-lookup"><span data-stu-id="baf32-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="baf32-212">MRTK — профиль указателя</span><span class="sxs-lookup"><span data-stu-id="baf32-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="baf32-213">MRTK — система ввода</span><span class="sxs-lookup"><span data-stu-id="baf32-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="baf32-214">MRTK — указатели</span><span class="sxs-lookup"><span data-stu-id="baf32-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="baf32-215">См. также</span><span class="sxs-lookup"><span data-stu-id="baf32-215">See also</span></span>

* [<span data-ttu-id="baf32-216">Жесты</span><span class="sxs-lookup"><span data-stu-id="baf32-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="baf32-217">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="baf32-217">Head-gaze and commit</span></span>](gaze-and-commit.md)