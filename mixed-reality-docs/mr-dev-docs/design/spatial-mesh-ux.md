---
title: Визуализация пространственной сетки
description: Сведения о том, как устройства понимают физические среды с помощью пространственных сеток.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Смешанная реальность, HoloLens, элементы управления ИП, взаимодействие, Пользовательский интерфейс, UX, проектирование UX, пространственный пользовательский интерфейс, пространственное взаимодействие, трехмерный Пользовательский интерфейс, трехмерный UI, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848192"
---
# <a name="spatial-mesh"></a><span data-ttu-id="6bb6d-104">Виртуальная сетка</span><span class="sxs-lookup"><span data-stu-id="6bb6d-104">Spatial mesh</span></span>

![Виртуальная сетка](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="6bb6d-106">Пользователи узнают, как устройство воспринимает и понимает физическую среду с помощью визуализации пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="6bb6d-107">Правильная визуализация пространственной сетки может создать удобство и Magical при предоставлении пространственного контекста.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="6bb6d-108">Рекомендации по проектированию</span><span class="sxs-lookup"><span data-stu-id="6bb6d-108">Design guideline</span></span>

<span data-ttu-id="6bb6d-109">Важно позволить пользователю сосредоточиться на содержимом и взаимодействовать с ним.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="6bb6d-110">Непрерывная визуализация пространственной сетки в фоновом режиме может отвлечь внимание.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="6bb6d-111">Мы рекомендуем визуализировать среду экономно, либо только один раз при первом запуске, либо когда пользователь четко показывает, что им нужно видеть сетку окружающей среды, нацеливание и касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="6bb6d-112">Это поведение можно наблюдать на портале Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6bb6d-113">Визуализация пространственной сетки в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="6bb6d-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="6bb6d-114">МРТК предоставляет несколько материалов для визуализации пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="6bb6d-115">**MRTK_Wireframe. материально, MRTK_Wireframe.** Material: сведения о статической пространственной сетке по умолчанию, которые показывают контуры сетки без анимации.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="6bb6d-116">Этот материал полезен в целях отладки, так как он отображает все геометрические объекты сетки.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="6bb6d-117">Однако это не рекомендуется для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="6bb6d-118">**MRTK_SurfaceReconstruction.** материально. этот материал предоставляет анимированный импульсный результат для пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="6bb6d-119">Этот материал можно использовать для визуализации среды на заданный момент времени или на входе пользователя в Air.</span><span class="sxs-lookup"><span data-stu-id="6bb6d-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="6bb6d-120">Примеры см. в сцене **пулсешадерексамплес. Unity** .</span><span class="sxs-lookup"><span data-stu-id="6bb6d-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="6bb6d-121">Дополнительные сведения см. в разделе [мртк-пространственное осведомленность](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) и [Мртк-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span><span class="sxs-lookup"><span data-stu-id="6bb6d-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="6bb6d-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6bb6d-122">See also</span></span>

* [<span data-ttu-id="6bb6d-123">Курсоры</span><span class="sxs-lookup"><span data-stu-id="6bb6d-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6bb6d-124">Телекинез</span><span class="sxs-lookup"><span data-stu-id="6bb6d-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6bb6d-125">Кнопка</span><span class="sxs-lookup"><span data-stu-id="6bb6d-125">Button</span></span>](button.md)
* [<span data-ttu-id="6bb6d-126">Активный объект</span><span class="sxs-lookup"><span data-stu-id="6bb6d-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6bb6d-127">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="6bb6d-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6bb6d-128">Оперирование</span><span class="sxs-lookup"><span data-stu-id="6bb6d-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6bb6d-129">Меню руки</span><span class="sxs-lookup"><span data-stu-id="6bb6d-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6bb6d-130">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="6bb6d-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6bb6d-131">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="6bb6d-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6bb6d-132">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="6bb6d-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6bb6d-133">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="6bb6d-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6bb6d-134">Подсказка</span><span class="sxs-lookup"><span data-stu-id="6bb6d-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6bb6d-135">Планшет</span><span class="sxs-lookup"><span data-stu-id="6bb6d-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="6bb6d-136">Ползунок</span><span class="sxs-lookup"><span data-stu-id="6bb6d-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="6bb6d-137">Шейдер</span><span class="sxs-lookup"><span data-stu-id="6bb6d-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="6bb6d-138">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="6bb6d-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6bb6d-139">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="6bb6d-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6bb6d-140">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="6bb6d-140">Surface magnetism</span></span>](surface-magnetism.md)
