---
title: Что такое смешанная реальность?
description: В этой статье приведено определение смешанной реальности и показано, в какой точке спектра смешанной реальности находятся устройства дополненной и виртуальной реальности.
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Смешанная реальность, голографический, AR, VR, MR, XR, дополненная реальность, виртуальная реальность, объяснение
ms.localizationpriority: high
ms.openlocfilehash: 44ef30925f8429628ebeb2c5f367d379a8ab102f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700853"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="fd30a-104">Что такое смешанная реальность?</span><span class="sxs-lookup"><span data-stu-id="fd30a-104">What is Mixed Reality?</span></span>

![Наведение и фиксация с использованием рук на HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="fd30a-106">Смешанная реальность — это сочетание физического и цифрового миров, позволяющее реализовать возможности взаимодействия между человеком, компьютером и средой.</span><span class="sxs-lookup"><span data-stu-id="fd30a-106">Mixed Reality is a blend of physical and digital worlds, unlocking the links between human, computer, and environment interaction.</span></span> <span data-ttu-id="fd30a-107">Такая новая реальность стала возможной благодаря развитию систем компьютерного зрения, графической вычислительной мощности, технологий для дисплеев и систем ввода.</span><span class="sxs-lookup"><span data-stu-id="fd30a-107">This new reality is based on advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="fd30a-108">Термин *смешанная реальность* впервые появился в документе 1994 года [A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321) (Таксономия визуальных дисплеев для смешанной реальности) за авторством Пола Милграма (Paul Milgram) и Фумио Кисино (Fumio Kishino).</span><span class="sxs-lookup"><span data-stu-id="fd30a-108">However, the term *Mixed Reality* was introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)."</span></span> <span data-ttu-id="fd30a-109">В этом документе они описали концепцию *виртуального континуума* и применение таксономии этой классификации к дисплеям.</span><span class="sxs-lookup"><span data-stu-id="fd30a-109">Their paper explored the concept of the *virtuality continuum* and the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="fd30a-110">С тех пор смешанная реальность начала применяться не только к дисплеям и теперь включает следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="fd30a-110">Since then, the application of Mixed Reality has gone beyond displays to include:</span></span>
* <span data-ttu-id="fd30a-111">ввод через взаимодействие со средой;</span><span class="sxs-lookup"><span data-stu-id="fd30a-111">Environmental input</span></span>
* <span data-ttu-id="fd30a-112">пространственный звук</span><span class="sxs-lookup"><span data-stu-id="fd30a-112">Spatial sound</span></span>
* <span data-ttu-id="fd30a-113">расположение и позиционирование в реальном и виртуальном пространствах.</span><span class="sxs-lookup"><span data-stu-id="fd30a-113">Locations and positioning in both real and virtual spaces</span></span>

<span data-ttu-id="fd30a-114">![Изображение со спектром смешанной реальности](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="fd30a-114">![The Mixed Reality spectrum image](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="fd30a-115">*Изображение: смешанная реальность является результатом смешения физического и цифрового миров.*</span><span class="sxs-lookup"><span data-stu-id="fd30a-115">*Image: Mixed Reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="fd30a-116">Ввод и восприятие через окружающую среду</span><span class="sxs-lookup"><span data-stu-id="fd30a-116">Environmental input and perception</span></span>

<span data-ttu-id="fd30a-117">За последние десятилетия исследование связей между человеческим и компьютерным вводом выделилось в отдельную дисциплину — *человеко-машинное взаимодействие* (HCI).</span><span class="sxs-lookup"><span data-stu-id="fd30a-117">Over the past several decades, exploration into the relationship between human and computer input has continued, leading to the discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="fd30a-118">Человек может вводить данные через разные средства, включая клавиатуры, мыши, касание, рукописный ввод, речь и даже отслеживание движений с помощью Kinect.</span><span class="sxs-lookup"><span data-stu-id="fd30a-118">Human input happens through different means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="fd30a-119">Развитие технологий датчиков и обработки зарождает новую эру ввода данных в компьютеры через взаимодействие со средой.</span><span class="sxs-lookup"><span data-stu-id="fd30a-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="fd30a-120">Взаимодействие между компьютерами и средой фактически подразумевает анализ среды или ее *восприятие* . Именно поэтому API в Windows, которые предоставляют информацию о среде, называются [API восприятия](https://docs.microsoft.com/uwp/api/Windows.Perception).</span><span class="sxs-lookup"><span data-stu-id="fd30a-120">The interaction between computers and environments is effectively environmental understanding or *perception* , which is why the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="fd30a-121">Ввод через окружающую среду позволяет собрать такие данные, как расположение человека в реальном мире (например, [отслеживание головы](../design/coordinate-systems.md)), поверхности и границы (например, [пространственное картирование](../design/spatial-mapping.md) и [интерпретация сцены](../design/scene-understanding.md)), общее освещение, пространственный звук, распознавание объектов и расположение.</span><span class="sxs-lookup"><span data-stu-id="fd30a-121">Environmental input captures things like a person's position in the world ([head tracking](../design/coordinate-systems.md)), surfaces and boundaries ([spatial mapping](../design/spatial-mapping.md) and [scene understanding](../design/scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="fd30a-122">![Диаграмма Венна по взаимодействию между компьютерами, людьми и средами](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="fd30a-122">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="fd30a-123"> \
*Изображение: взаимодействие между компьютерами, людьми и средами.*</span><span class="sxs-lookup"><span data-stu-id="fd30a-123"> \
*Image: The interactions between computers, humans, and environments.*</span></span>

<br>

<span data-ttu-id="fd30a-124">Сочетание трех элементов — **компьютерные вычисления, введенные пользователем сведения и сведения о среде**  — позволяет создавать полноценные взаимодействия смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fd30a-124">The combination of all three - **computer processing, human input, and environmental input** - sets the stage for creating true Mixed Reality experiences.</span></span> <span data-ttu-id="fd30a-125">Перемещение по физическому миру может преобразовываться в движение в цифровом мире.</span><span class="sxs-lookup"><span data-stu-id="fd30a-125">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="fd30a-126">Границы физического мира могут повлиять на работу приложений в цифровом мире, например игр.</span><span class="sxs-lookup"><span data-stu-id="fd30a-126">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="fd30a-127">Без ввода через окружающую среду невозможно сочетать взаимодействия с физическим и цифровым мирами.</span><span class="sxs-lookup"><span data-stu-id="fd30a-127">Without environmental input, experiences can't blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="fd30a-128">Спектр смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="fd30a-128">The Mixed Reality spectrum</span></span>

<span data-ttu-id="fd30a-129">Так как смешанная реальность объединяет физические и цифровые миры, эти две реальности определяют противоположные концы спектра, называемого континуумом виртуальности.</span><span class="sxs-lookup"><span data-stu-id="fd30a-129">Since Mixed Reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="fd30a-130">Мы называем набор реальностей *спектром смешанной реальности* .</span><span class="sxs-lookup"><span data-stu-id="fd30a-130">We refer to the array of realities as the *Mixed Reality spectrum* .</span></span> <span data-ttu-id="fd30a-131">На одном конце находится физическая реальность, в которой существуют люди.</span><span class="sxs-lookup"><span data-stu-id="fd30a-131">On the left-hand side, we have the physical reality that we as humans exist in.</span></span> <span data-ttu-id="fd30a-132">На другом — соответствующая цифровая реальность.</span><span class="sxs-lookup"><span data-stu-id="fd30a-132">On the right-hand side, we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="fd30a-133">Дополненная и виртуальная реальность</span><span class="sxs-lookup"><span data-stu-id="fd30a-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="fd30a-134">Большинство мобильных телефонов, доступных сейчас на рынке, почти не имеют возможностей для восприятия окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="fd30a-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="fd30a-135">Они не способны обеспечить взаимодействие, сочетающее физический и цифровой миры.</span><span class="sxs-lookup"><span data-stu-id="fd30a-135">The experiences they offer can't mix physical and digital realities.</span></span> <span data-ttu-id="fd30a-136">Взаимодействия, включающие наложение графики на видеопотоки из физического мира, называются *дополненной реальностью* .</span><span class="sxs-lookup"><span data-stu-id="fd30a-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality* .</span></span> <span data-ttu-id="fd30a-137">Взаимодействия, в которых ваш взгляд на физический мир перекрывается цифровым устройством, — это *виртуальная реальность* .</span><span class="sxs-lookup"><span data-stu-id="fd30a-137">The experiences that occlude your view to present a digital experience are *virtual reality* .</span></span> <span data-ttu-id="fd30a-138">Взаимодействия, реализованные между дополненной и виртуальной реальностями, формируют *смешанную реальность* :</span><span class="sxs-lookup"><span data-stu-id="fd30a-138">The experiences enabled between augmented and virtual reality form *Mixed Reality* :</span></span>
* <span data-ttu-id="fd30a-139">Физический мир берется за основу, и в нем размещается цифровой объект (голограмма), как будто он на самом деле присутствует там.</span><span class="sxs-lookup"><span data-stu-id="fd30a-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was there.</span></span>
* <span data-ttu-id="fd30a-140">Физический мир берется за основу, и в нем размещается представление другого человека (аватар), которое обозначает расположение этого человека при создании заметок.</span><span class="sxs-lookup"><span data-stu-id="fd30a-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="fd30a-141">Иными словами, эти взаимодействия поддерживают асинхронную совместную работу в разные моменты времени.</span><span class="sxs-lookup"><span data-stu-id="fd30a-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="fd30a-142">Физический мир берется за основу, и его реальные границы и препятствия (например, стены и мебель) отображаются в цифровом представлении так, чтобы пользователь мог избегать реальных объектов.</span><span class="sxs-lookup"><span data-stu-id="fd30a-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="fd30a-143">![Спектр смешанной реальности](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="fd30a-143">![The Mixed Reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="fd30a-144">*Изображение: спектр смешанной реальности*</span><span class="sxs-lookup"><span data-stu-id="fd30a-144">*Image: The Mixed Reality spectrum*</span></span>

<br>

<span data-ttu-id="fd30a-145">Большинство существующих предложений для дополненной и виртуальной реальности отражают лишь малую часть этого спектра и считаются составляющей более широкого спектра смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fd30a-145">Most augmented reality and virtual reality offerings available today represent a small part of this spectrum and are considered subsets of the larger Mixed Reality spectrum.</span></span> <span data-ttu-id="fd30a-146">Windows 10 создавалась с учетом всего этого спектра и позволяет организовать полноценное смешение цифровых представлений людей, мест и объектов с реальным миром.</span><span class="sxs-lookup"><span data-stu-id="fd30a-146">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>


## <a name="devices-and-experiences"></a><span data-ttu-id="fd30a-147">Устройства и взаимодействия</span><span class="sxs-lookup"><span data-stu-id="fd30a-147">Devices and experiences</span></span>

<span data-ttu-id="fd30a-148">Существует два основных типа устройств, которые поддерживают взаимодействия Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="fd30a-148">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="fd30a-149">**Голографические устройства**  — устройства, способные размещать цифровое содержимое в реальном мире так, как если бы оно существовало там на самом деле.</span><span class="sxs-lookup"><span data-stu-id="fd30a-149">**Holographic devices** are characterized by the device's ability to place digital content in the real world as if it were there.</span></span>
2. <span data-ttu-id="fd30a-150">**Иммерсивные устройства**  — устройства, способные создавать ощущение присутствия, то есть полностью скрывать реальный мир и заменять его цифровым взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="fd30a-150">**Immersive devices** are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="fd30a-151">Характеристика</span><span class="sxs-lookup"><span data-stu-id="fd30a-151">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="fd30a-152">Голографические устройства</span><span class="sxs-lookup"><span data-stu-id="fd30a-152">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="fd30a-153">Иммерсивные устройства</span><span class="sxs-lookup"><span data-stu-id="fd30a-153">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="fd30a-154"><strong>Примеры устройств</strong></span><span class="sxs-lookup"><span data-stu-id="fd30a-154"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="fd30a-155">Microsoft HoloLens;</span><span class="sxs-lookup"><span data-stu-id="fd30a-155">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="fd30a-156">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="fd30a-156">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="fd30a-157"><strong>Дисплей</strong></span><span class="sxs-lookup"><span data-stu-id="fd30a-157"><strong>Display</strong></span></span></td><td> <span data-ttu-id="fd30a-158">Прозрачный дисплей.</span><span class="sxs-lookup"><span data-stu-id="fd30a-158">See-through display.</span></span> <span data-ttu-id="fd30a-159">Позволяет пользователю с гарнитурой видеть реальную физическую среду.</span><span class="sxs-lookup"><span data-stu-id="fd30a-159">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="fd30a-160">Непрозрачный дисплей.</span><span class="sxs-lookup"><span data-stu-id="fd30a-160">Opaque display.</span></span> <span data-ttu-id="fd30a-161">Блокирует реальную физическую среду для пользователя с гарнитурой.</span><span class="sxs-lookup"><span data-stu-id="fd30a-161">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="fd30a-162"><strong>Перемещение</strong></span><span class="sxs-lookup"><span data-stu-id="fd30a-162"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="fd30a-163">Перемещения с шестью степенями свободы, включая вращение и преобразование.</span><span class="sxs-lookup"><span data-stu-id="fd30a-163">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="fd30a-164">Перемещения с шестью степенями свободы, включая вращение и преобразование.</span><span class="sxs-lookup"><span data-stu-id="fd30a-164">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table> 


> <span data-ttu-id="fd30a-165">[ПРИМЕЧАНИЕ] Возможность подключения устройства к отдельному компьютеру по USB-кабелю или через Wi-Fi и (или) работы в автономном режиме без подключения не дают никакой информации о том, является ли устройство голографическим или иммерсивным.</span><span class="sxs-lookup"><span data-stu-id="fd30a-165">[NOTE] Whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) doesn't reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="fd30a-166">Любые возможности для повышения мобильности улучшают качество взаимодействия. Но как голографические, так и иммерсивные устройства могут быть подключаемыми или не подключаемыми.</span><span class="sxs-lookup"><span data-stu-id="fd30a-166">Features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>

<span data-ttu-id="fd30a-167">Технологические усовершенствования сделали возможным взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fd30a-167">Technological advancement is what has enabled Mixed Reality experiences.</span></span> <span data-ttu-id="fd30a-168">Пока что не существует устройств, способных организовать взаимодействие по всему спектру.</span><span class="sxs-lookup"><span data-stu-id="fd30a-168">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="fd30a-169">Windows 10 предоставляет производителям устройств и разработчикам ПО единую платформу для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fd30a-169">Windows 10 provides a common Mixed Reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="fd30a-170">Современные устройства могут поддерживать лишь определенный сегмент из спектра смешанной реальности, но в новых устройствах он расширен.</span><span class="sxs-lookup"><span data-stu-id="fd30a-170">Devices today can support a specific range within the Mixed Reality spectrum, with new devices expanding that range.</span></span> <span data-ttu-id="fd30a-171">В будущем голографические устройства станут более иммерсивными, а иммерсивные — более голографическими.</span><span class="sxs-lookup"><span data-stu-id="fd30a-171">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="fd30a-172">![Типы устройств в спектре смешанной реальности](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="fd30a-172">![Device types in the Mixed Reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="fd30a-173">*Изображение: расположение устройств в спектре смешанной реальности*</span><span class="sxs-lookup"><span data-stu-id="fd30a-173">*Image: Where devices exist on the Mixed Reality spectrum*</span></span>

<span data-ttu-id="fd30a-174">Оптимально, если разработчики заранее определяют, какой тип взаимодействия будет реализован в приложении или игре.</span><span class="sxs-lookup"><span data-stu-id="fd30a-174">It's best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="fd30a-175">Эти взаимодействия будут соответствовать определенной точке или сегменту нашего спектра.</span><span class="sxs-lookup"><span data-stu-id="fd30a-175">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="fd30a-176">Затем разработчикам необходимо оценить возможности тех устройств, для которых разрабатывается приложение.</span><span class="sxs-lookup"><span data-stu-id="fd30a-176">Developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="fd30a-177">Взаимодействия на основе реального мира лучше всего выполнять на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd30a-177">Experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="fd30a-178">**Ближе к левому краю (физическая реальность).**</span><span class="sxs-lookup"><span data-stu-id="fd30a-178">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="fd30a-179">Пользователь остается в своей физической среде и никогда не получает оснований думать, что покидает ее.</span><span class="sxs-lookup"><span data-stu-id="fd30a-179">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="fd30a-180">**В середине (полноценная смешанная реальность).**</span><span class="sxs-lookup"><span data-stu-id="fd30a-180">**In the middle (fully Mixed Reality).**</span></span> <span data-ttu-id="fd30a-181">В этих взаимодействиях реальный и цифровой мир переплетаются друг с другом.</span><span class="sxs-lookup"><span data-stu-id="fd30a-181">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="fd30a-182">Те, кто смотрел фильм [Джуманджи](https://en.wikipedia.org/wiki/Jumanji), могут вспомнить смешение физической структуры дома, в котором происходят события, с джунглями из игры.</span><span class="sxs-lookup"><span data-stu-id="fd30a-182">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="fd30a-183">**Ближе к правому краю (почти цифровая реальность).**</span><span class="sxs-lookup"><span data-stu-id="fd30a-183">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="fd30a-184">Пользователи взаимодействуют с цифровой средой и не отслеживают, что окружает их в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="fd30a-184">Users experience a digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="fd30a-185">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fd30a-185">See also</span></span>

* [<span data-ttu-id="fd30a-186">Что такое голограмма?</span><span class="sxs-lookup"><span data-stu-id="fd30a-186">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="fd30a-187">Основные концепции смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="fd30a-187">Understand the basics of Mixed Reality</span></span>](get-started-with-mr.md#understand-the-basics)
* [<span data-ttu-id="fd30a-188">Начало разработки и создания прототипов</span><span class="sxs-lookup"><span data-stu-id="fd30a-188">Start creating and prototyping</span></span>](../design/design.md)
* [<span data-ttu-id="fd30a-189">Изучение инструментов и архитектуры</span><span class="sxs-lookup"><span data-stu-id="fd30a-189">Learn the tools and architecture</span></span>](../develop/development.md)
