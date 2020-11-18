---
title: Визуализация пространственной сетки
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Смешанная реальность, HoloLens, элементы управления ИП, взаимодействие, Пользовательский интерфейс, UX, проектирование UX, пространственный пользовательский интерфейс, пространственное взаимодействие, трехмерный Пользовательский интерфейс, трехмерный UI, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: ec887f73b8561e0a91740d612227411683707364
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703300"
---
# <a name="spatial-mesh"></a><span data-ttu-id="f7e2a-103">Виртуальная сетка</span><span class="sxs-lookup"><span data-stu-id="f7e2a-103">Spatial mesh</span></span>

![Виртуальная сетка](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="f7e2a-105">С помощью визуализации пространственной сетки пользователь может узнать, как устройство воспринимает и понимает физическую среду.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="f7e2a-106">В дополнение к пространственному контексту, правильная визуализация пространственной сетки может создавать удобство и Magical интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="f7e2a-107">Рекомендации по проектированию</span><span class="sxs-lookup"><span data-stu-id="f7e2a-107">Design guideline</span></span>
<span data-ttu-id="f7e2a-108">Поскольку важно позволить пользователю сосредоточиться на содержимом и взаимодействовать с ним, непрерывная и повторная визуализация пространственной сетки в фоновом режиме может отвлечь вас.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="f7e2a-109">Рекомендуется как можно реже визуализировать среду, либо только один раз при первом запуске, либо когда пользователь показывает четкую намерение для просмотра сети окружающей среды, нацеливание на место и касание воздуха.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="f7e2a-110">Это поведение можно наблюдать в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f7e2a-111">Визуализация пространственной сетки в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="f7e2a-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="f7e2a-112">МРТК предоставляет несколько материалов для визуализации пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="f7e2a-113">**MRTK_Wireframe. материально, MRTK_Wireframe.** Material: материал статической пространственной сетки по умолчанию, который показывает контур сетки без анимации.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="f7e2a-114">Этот материал полезен в целях отладки, так как он отображает все геометрические объекты сетки.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="f7e2a-115">Однако не рекомендуется для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="f7e2a-116">**MRTK_SurfaceReconstruction.** материально. этот материал предоставляет анимированный импульсный результат для пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="f7e2a-117">Вы можете использовать этот материал для визуализации среды на конкретный момент работы или на входе пользователя в Air.</span><span class="sxs-lookup"><span data-stu-id="f7e2a-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="f7e2a-118">Примеры см. в сцене **пулсешадерексамплес. Unity** .</span><span class="sxs-lookup"><span data-stu-id="f7e2a-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="f7e2a-119">Дополнительные сведения см. в разделе [мртк-spatial осведомленность](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) и [Мртк-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="f7e2a-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="f7e2a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f7e2a-120">See also</span></span>

* [<span data-ttu-id="f7e2a-121">Курсоры</span><span class="sxs-lookup"><span data-stu-id="f7e2a-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f7e2a-122">Телекинез</span><span class="sxs-lookup"><span data-stu-id="f7e2a-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f7e2a-123">Кнопка</span><span class="sxs-lookup"><span data-stu-id="f7e2a-123">Button</span></span>](button.md)
* [<span data-ttu-id="f7e2a-124">Активный объект</span><span class="sxs-lookup"><span data-stu-id="f7e2a-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f7e2a-125">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="f7e2a-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f7e2a-126">Оперирование</span><span class="sxs-lookup"><span data-stu-id="f7e2a-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f7e2a-127">Меню руки</span><span class="sxs-lookup"><span data-stu-id="f7e2a-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f7e2a-128">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="f7e2a-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f7e2a-129">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="f7e2a-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f7e2a-130">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="f7e2a-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f7e2a-131">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="f7e2a-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f7e2a-132">Подсказка</span><span class="sxs-lookup"><span data-stu-id="f7e2a-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f7e2a-133">Планшет</span><span class="sxs-lookup"><span data-stu-id="f7e2a-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="f7e2a-134">Ползунок</span><span class="sxs-lookup"><span data-stu-id="f7e2a-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="f7e2a-135">Шейдер</span><span class="sxs-lookup"><span data-stu-id="f7e2a-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="f7e2a-136">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="f7e2a-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f7e2a-137">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="f7e2a-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f7e2a-138">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="f7e2a-138">Surface magnetism</span></span>](surface-magnetism.md)
