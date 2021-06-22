---
title: Ползунок
description: Обзор ползунков МРТК
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, ползунки,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426880"
---
# <a name="sliders"></a><span data-ttu-id="3e7a6-104">Ползунки</span><span class="sxs-lookup"><span data-stu-id="3e7a6-104">Sliders</span></span>

![Пример ползунка](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="3e7a6-106">Ползунки — это компоненты пользовательского интерфейса, позволяющие постоянно изменять значение, перемещая ползунок на дорожке. В настоящее время ползунок сжатия можно переместить, непосредственно изменив ползунок, напрямую или на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="3e7a6-107">Ползунки работают с AR и VR, используя контроллеры движения, руки или жест + Voice.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="3e7a6-108">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="3e7a6-108">Example scene</span></span>

<span data-ttu-id="3e7a6-109">Примеры можно найти в сцене **слидерексампле** в разделе `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="3e7a6-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="3e7a6-110">Использование ползунков</span><span class="sxs-lookup"><span data-stu-id="3e7a6-110">How to use sliders</span></span>

<span data-ttu-id="3e7a6-111">Перетащите **пинчслидер** prefab в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="3e7a6-112">Если вы хотите изменить или создать собственный ползунок, не забудьте сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="3e7a6-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="3e7a6-113">Убедитесь, что на нем есть объект-бегунок.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="3e7a6-114">В Пинчслидер prefab используется конфликт `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="3e7a6-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="3e7a6-115">Убедитесь в том, что объект, содержащий компонент, также имеет близкое к нему для захвата компонента, если вы хотите иметь возможность захватить ползунок рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="3e7a6-116">Мы также рекомендуем использовать следующую иерархию</span><span class="sxs-lookup"><span data-stu-id="3e7a6-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="3e7a6-117">Пинчслидер — содержит Слидеркомпонент</span><span class="sxs-lookup"><span data-stu-id="3e7a6-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="3e7a6-118">Таучколлидер — объект, содержащий всю выбираемую область ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="3e7a6-119">Включает поведение привязки к положению.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="3e7a6-120">Слидерсумб — содержит перемещаемый бегунок</span><span class="sxs-lookup"><span data-stu-id="3e7a6-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="3e7a6-121">Тракквисуалс — содержит запись и другие визуальные элементы.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="3e7a6-122">Осервисуалс — содержит любые другие визуальные элементы</span><span class="sxs-lookup"><span data-stu-id="3e7a6-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="3e7a6-123">События ползунка</span><span class="sxs-lookup"><span data-stu-id="3e7a6-123">Slider events</span></span>

<span data-ttu-id="3e7a6-124">Ползунки предоставляют следующие события:</span><span class="sxs-lookup"><span data-stu-id="3e7a6-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="3e7a6-125">Онвалуеупдатед — вызывается при изменении значения ползунка</span><span class="sxs-lookup"><span data-stu-id="3e7a6-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="3e7a6-126">Онинтерактионстартед — вызывается, когда пользователь захватит ползунок</span><span class="sxs-lookup"><span data-stu-id="3e7a6-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="3e7a6-127">Онинтерактионендед — вызывается, когда пользователь отпускает ползунок</span><span class="sxs-lookup"><span data-stu-id="3e7a6-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="3e7a6-128">Онховерентеред — вызывается, когда рука пользователя/контроллер наводится на ползунок с помощью близкого или дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="3e7a6-129">Онховерекситед — вызывается, когда рука пользователя или контроллер больше не находится на ползунке.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="3e7a6-130">Настройка ограничивающего ползунка и оси</span><span class="sxs-lookup"><span data-stu-id="3e7a6-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="3e7a6-131">Вы можете напрямую переместить начальную и конечную точки ползунка, переместив маркеры в сцене:</span><span class="sxs-lookup"><span data-stu-id="3e7a6-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Конфигурация ползунков](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="3e7a6-133">Можно также указать ось (в локальном пространстве) ползунка с помощью поля _ось ползунков_ .</span><span class="sxs-lookup"><span data-stu-id="3e7a6-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="3e7a6-134">Если вы не можете использовать маркеры, то можно указать начальную и конечную точки ползунка с помощью _ползунка начальная дистанция_ и _ползунка конечного расстояния_ .</span><span class="sxs-lookup"><span data-stu-id="3e7a6-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="3e7a6-135">Они указывают начальную и конечную позицию ползунка в виде расстояния от центра ползунка в области локальные координаты.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="3e7a6-136">Это означает, что после настройки начального и конечного расстояний ползунка можно масштабировать ползунок до меньшего или большего размера без необходимости обновлять начальные и конечные расстояния.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="3e7a6-137">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="3e7a6-137">Inspector properties</span></span>

<span data-ttu-id="3e7a6-138">**Корень бегунка** Gameobject, содержащий бегунок с ползунком.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="3e7a6-139">**Привязать к положению** Будет ли этот ползунок привязан к заданному положению на ползунке</span><span class="sxs-lookup"><span data-stu-id="3e7a6-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="3e7a6-140">**Является сенсорным** Является ли этот ползунок управляемым с помощью событий сенсорного ввода</span><span class="sxs-lookup"><span data-stu-id="3e7a6-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="3e7a6-141">**Конфликт Thumb** Конфликт, управляющий бегунком ползунка</span><span class="sxs-lookup"><span data-stu-id="3e7a6-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="3e7a6-142">**Сенсорный конфликт** Область ползунка, которая может быть затронута или выбрана, если параметр Привязать к положению имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="3e7a6-143">**Значение ползунка** Значение ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="3e7a6-144">**Использование подразделений шагов ползунка** Определяет, увеличивается ли этот ползунок в шагах или непрерывно.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="3e7a6-145">**Деления шагов ползунка** Число подразделений, на которых разбивается ползунок, если включен пункт "ползунки".</span><span class="sxs-lookup"><span data-stu-id="3e7a6-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="3e7a6-146">**Контроль визуальных элементов** Gameobject, содержащий нужные визуальные элементы Track, которые попадают вдоль ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="3e7a6-147">**Деления** Gameobject, содержащий нужные деления, которые попадают вдоль ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="3e7a6-148">**Визуальные элементы Thumb** Gameobject, содержащий нужный визуальный элемент, который помещается вдоль ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="3e7a6-149">**Ось ползунка** Ось, вдоль которой перемещается ползунок.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="3e7a6-150">**Начальная дистанция ползунка** Где начинается контрольная шкала, расстояние от центра вдоль оси ползунка в поле локальные единицы.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="3e7a6-151">**Конечное расстояние ползунка** Место, где заканчивается ползунок, в виде расстояния от центра вдоль ползунка в локальных единицах пространства.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="3e7a6-152">Если пользователь обновляет значение оси ползунка в редакторе, то при указании параметра Track визуализаций или визуальных элементов происходит обновление их преобразования.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="3e7a6-153">В частности, их локальная позиция сбрасывается, а их локальный поворот устанавливается в соответствии с ориентацией оси ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="3e7a6-154">Их масштаб не изменяется.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-154">Their scale isn't modified.</span></span>
<span data-ttu-id="3e7a6-155">Если деления имеют компонент коллекции объектов Grid, макет и Целлвидс или Целлхеигхт обновляются соответствующим образом в соответствии с осью ползунка.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="3e7a6-156">Примеры конфигураций ползунков</span><span class="sxs-lookup"><span data-stu-id="3e7a6-156">Example Slider Configurations</span></span>

<span data-ttu-id="3e7a6-157">Непрерывные ползунки с привязкой к ![ непрерывным ползункам](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="3e7a6-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="3e7a6-158">Ползунки шага с привязкой к положению</span><span class="sxs-lookup"><span data-stu-id="3e7a6-158">Step Sliders with Snap To Position</span></span>

![Ползунки шага](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="3e7a6-160">Сенсорные ползунки</span><span class="sxs-lookup"><span data-stu-id="3e7a6-160">Touch Sliders</span></span>

![Сенсорные ползунки](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)