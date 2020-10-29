---
title: Общие сведения об MRTK. Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, МRТК, Набор средств для смешанной реальности, Windows Mixed Reality, проектирование, пример приложения, элементы управления
ms.localizationpriority: high
ms.openlocfilehash: bd0b3104d48ce3fbd836e7294ab5b816a486847a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701041"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="575a1-104">Общие сведения об MRTK. Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="575a1-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="575a1-106">Сведения о том, как использовать МRТК для достижения некоторых распространенных моделей взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="575a1-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="575a1-107">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="575a1-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="575a1-108">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="575a1-108">How to grab and move an object?</span></span>
- <span data-ttu-id="575a1-109">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="575a1-109">How to resize an object?</span></span>
- <span data-ttu-id="575a1-110">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="575a1-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="575a1-111">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="575a1-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="575a1-112">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="575a1-112">How to add visual feedback?</span></span>
- <span data-ttu-id="575a1-113">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="575a1-113">How to add audio feedback?</span></span>
- <span data-ttu-id="575a1-114">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="575a1-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="575a1-115">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="575a1-115">How to make an object follow you?</span></span>
- <span data-ttu-id="575a1-116">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="575a1-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="575a1-117">Как имитировать взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="575a1-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="575a1-118">МRТК поддерживает имитацию входных данных в редакторе.</span><span class="sxs-lookup"><span data-stu-id="575a1-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="575a1-119">Просто запустите сцену, нажав кнопку воспроизведения в Unity.</span><span class="sxs-lookup"><span data-stu-id="575a1-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="575a1-120">Следующие клавиши позволяют имитировать входные данные.</span><span class="sxs-lookup"><span data-stu-id="575a1-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="575a1-121">Чтобы переместить камеру, нажимайте клавиши W, A, S, D.</span><span class="sxs-lookup"><span data-stu-id="575a1-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="575a1-122">Чтобы посмотреть по сторонам, перемещайте мышь при нажатой правой кнопке мыши.</span><span class="sxs-lookup"><span data-stu-id="575a1-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="575a1-123">Чтобы имитировать поднятие рук вверх, нажмите клавишу пробела (для правой руки) или левую клавишу SHIFT (для левой руки). Чтобы имитировать удержание рук в зоне видимости, нажмите клавишу "T" или "Y", а чтобы имитировать поворот рук, нажимайте клавиши "Q" и "E" (горизонтально) или "R" и "F" (вертикально).</span><span class="sxs-lookup"><span data-stu-id="575a1-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="575a1-124">Дополнительные сведения об имитации входных данных см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="575a1-125">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="575a1-125">How to grab and move an object?</span></span>
<span data-ttu-id="575a1-126">Чтобы объект поддерживал захват и перемещение, назначьте ему следующие два скрипта: ManipulationHandler.cs и NearInteractionGrabbable.cs (для прямого захвата при отслеживании ввода с помощью рук). ManipulationHandler поддерживает как близкие, так и дальние взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="575a1-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="575a1-127">Вы можете захватить и переместить объект с использованием ввода с помощью рук в HoloLens 2 (ближнее), телекинеза (дальнее), сигнала контроллера движения (дальнее), курсора взгляда HoloLens, а также касания (дальнее).</span><span class="sxs-lookup"><span data-stu-id="575a1-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="575a1-128">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="575a1-128">How to resize an object?</span></span>
<span data-ttu-id="575a1-129">ManipulationHandler.cs поддерживает масштабирование и вращение двумя руками.</span><span class="sxs-lookup"><span data-stu-id="575a1-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="575a1-130">Это работает с разными типами входных данных, например ввод с помощью рук в HoloLens 2, ввод с помощью взгляда и жестов в HoloLens 1 или контроллера движений иммерсивной гарнитуры в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="575a1-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="575a1-131">Дополнительные сведения об обработчике манипулирования см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="575a1-132">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="575a1-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="575a1-133">Назначьте BoundingBox.cs объекту для использования ограничивающего прямоугольника, который представляет собой интерфейс для масштабирования и вращения объекта.</span><span class="sxs-lookup"><span data-stu-id="575a1-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="575a1-134">По умолчанию в нем отображаются синие маркеры и границы, как в HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="575a1-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="575a1-135">Чтобы использовать анимированные маркеры с учетом расстояния до объекта в стиле HoloLens 2, необходимо назначить заготовки и материалы.</span><span class="sxs-lookup"><span data-stu-id="575a1-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="575a1-136">Дополнительные сведения о конфигурации см. в [документации по ограничивающему прямоугольнику](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) и в примере сцены BoundingBoxExamples.unity.</span><span class="sxs-lookup"><span data-stu-id="575a1-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="575a1-137">Дополнительные сведения об ограничивающем прямоугольнике см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="575a1-138">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="575a1-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="575a1-139">Назначьте объекту PointerHandler.cs.</span><span class="sxs-lookup"><span data-stu-id="575a1-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="575a1-140">В инспекторе вы сможете применить события OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Чтобы использовать эти события в скрипте, реализуйте IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="575a1-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="575a1-141">Дополнительные сведения о системе ввода см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="575a1-142">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="575a1-142">How to add visual feedback?</span></span>
<span data-ttu-id="575a1-143">Присвойте объекту Interactable.cs.</span><span class="sxs-lookup"><span data-stu-id="575a1-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="575a1-144">В инспекторе создайте новую тему.</span><span class="sxs-lookup"><span data-stu-id="575a1-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="575a1-145">С помощью интерактивных профилей темы вы сможете легко добавить визуальный отклик для всех доступных состояний взаимодействий ввода.</span><span class="sxs-lookup"><span data-stu-id="575a1-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="575a1-146">Интерактивный объект предоставляет несколько типов тем, в том числе тему shader, которая позволяет управлять параметрами текстуры для каждого состояния взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="575a1-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="575a1-147">Дополнительные сведения об интерактивном объекте см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="575a1-148">Еще один важный строительный блок для создания визуального отклика — стандартный построитель текстуры MRTK.</span><span class="sxs-lookup"><span data-stu-id="575a1-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="575a1-149">С помощью шейдера MRTK Standard можно легко добавлять визуальные эффекты для отклика, например эффект указателя и подсветки при приближении.</span><span class="sxs-lookup"><span data-stu-id="575a1-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="575a1-150">Стандартный шейдер MRTK выполняет намного меньше вычислений, чем стандартный шейдер Unity, поэтому позволяет создать высокопроизводительную среду взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="575a1-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="575a1-151">Создайте новый материал и выберите шейдер Mixed Reality Toolkit > Standard (Набор средств для смешанной реальности > Стандартный).</span><span class="sxs-lookup"><span data-stu-id="575a1-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="575a1-152">Вы также можете выбрать любой из существующих материалов, для которых настроен стандартный шейдер MRTK.</span><span class="sxs-lookup"><span data-stu-id="575a1-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="575a1-153">Дополнительные сведения о стандартном шейдере MRTK см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="575a1-154">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="575a1-154">How to add audio feedback?</span></span>
<span data-ttu-id="575a1-155">Поместите AudioSource в объект.</span><span class="sxs-lookup"><span data-stu-id="575a1-155">Add AudioSource to an object.</span></span> <span data-ttu-id="575a1-156">Затем в скриптах, которые предоставляют нужные события ввода (например, Interactable.cs или PointerHandler.cs), присвойте объекту событие и выберите AudioSource.PlayOneShot().</span><span class="sxs-lookup"><span data-stu-id="575a1-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="575a1-157">Вы можете использовать собственные звуковые клипы или выбрать подходящий из числа звуковых активов MRTK.</span><span class="sxs-lookup"><span data-stu-id="575a1-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="575a1-158">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="575a1-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="575a1-159">MRTK предоставляет несколько типов кнопок в стиле оболочки (ОС) HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="575a1-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="575a1-160">Они поддерживают сложные типы визуального отклика, например подсветка при приближении, прямоугольник сжатия и эффект ряби на поверхности кнопки.</span><span class="sxs-lookup"><span data-stu-id="575a1-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="575a1-161">Вам нужно лишь перетащить любую из заготовок нажимаемых кнопок в стиле HoloLens 2 в сцену.</span><span class="sxs-lookup"><span data-stu-id="575a1-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="575a1-162">В заготовках используется описанный выше Interactable.cs.</span><span class="sxs-lookup"><span data-stu-id="575a1-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="575a1-163">Вы можете предоставлять в интерактивном объекте события для запуска действий, например OnClick().</span><span class="sxs-lookup"><span data-stu-id="575a1-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="575a1-164">Дополнительные сведения о заготовках кнопок см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="575a1-165">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="575a1-165">How to make an object follow you?</span></span>
<span data-ttu-id="575a1-166">Присвойте объекту RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="575a1-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="575a1-167">Это часть целой серии скриптов Solver, которые позволяют использовать разные типы размещения объектов в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="575a1-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="575a1-168">SolverHandler.cs будет добавлен автоматически.</span><span class="sxs-lookup"><span data-stu-id="575a1-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="575a1-169">Ниже вы видите пример конфигурации RadialView, которая позволяет добиться поведения "ленивое следование", например начальное меню в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="575a1-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="575a1-170">Вы можете указать минимальную и максимальную дистанцию, а также минимальный и максимальный угол обзора.</span><span class="sxs-lookup"><span data-stu-id="575a1-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="575a1-171">В следующем примере представлен объект с расстоянием от 0,4 до 0,8 м и диапазоном углов 15°.</span><span class="sxs-lookup"><span data-stu-id="575a1-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="575a1-172">Измените значение параметра Lerp Time (Время линейной интерполяции), чтобы изменение положения выполнялось быстрее или медленнее.</span><span class="sxs-lookup"><span data-stu-id="575a1-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="575a1-173">Дополнительные сведения о инструменте решения см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="575a1-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="575a1-174">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="575a1-174">How to make an object face you?</span></span>
<span data-ttu-id="575a1-175">Присвойте объекту скрипт Billboard.cs.</span><span class="sxs-lookup"><span data-stu-id="575a1-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="575a1-176">Теперь этот объект всегда будет развернут к вам, независимо от вашего положения.</span><span class="sxs-lookup"><span data-stu-id="575a1-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="575a1-177">Вы можете указать расположение оси вращения.</span><span class="sxs-lookup"><span data-stu-id="575a1-177">You can specify the pivot axis option.</span></span>

<img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="575a1-178">Вы готовы создать великолепные взаимодействия для смешанной реальности?</span><span class="sxs-lookup"><span data-stu-id="575a1-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="575a1-179">Изучите предложенные ниже страницы, чтобы получить дополнительные сведения об MRTK и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="575a1-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="575a1-180">Об авторе</span><span class="sxs-lookup"><span data-stu-id="575a1-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="575a1-181"><b>Дон Юн Парк</b> (Dong Yoon Park)</span><span class="sxs-lookup"><span data-stu-id="575a1-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="575a1-182">Разработчик средств взаимодействия с пользователем @Microsoft</span><span class="sxs-lookup"><span data-stu-id="575a1-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="575a1-183">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="575a1-183">Next Development Checkpoint</span></span>

<span data-ttu-id="575a1-184">Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="575a1-184">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="575a1-185">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="575a1-185">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="575a1-186">Камера</span><span class="sxs-lookup"><span data-stu-id="575a1-186">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="575a1-187">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="575a1-187">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="575a1-188">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="575a1-188">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="575a1-189">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="575a1-189">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="575a1-190">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="575a1-190">See also</span></span>

* <span data-ttu-id="575a1-191">[Набор средств для смешанной реальности (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="575a1-191">[Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span>
* [<span data-ttu-id="575a1-192">Портал документации по MRTK</span><span class="sxs-lookup"><span data-stu-id="575a1-192">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="575a1-193">Начало работы с MRTK</span><span class="sxs-lookup"><span data-stu-id="575a1-193">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="575a1-194">Рекомендации по переносу кода с HoloToolKit на MRTK</span><span class="sxs-lookup"><span data-stu-id="575a1-194">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
