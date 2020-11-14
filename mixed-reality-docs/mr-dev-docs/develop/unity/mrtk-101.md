---
title: Общие сведения об MRTK. Как с помощью Mixed Reality Toolkit для Unity выполнять стандартные пространственные взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, МRТК, Набор средств для смешанной реальности, Windows Mixed Reality, проектирование, пример приложения, элементы управления
ms.localizationpriority: high
ms.openlocfilehash: d10de5c9f16e0caa289d5110647b4c45a8a8fcf9
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386270"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="c3363-104">Общие сведения об MRTK. Как использовать Mixed Reality Toolkit в Unity для реализации стандартных пространственных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="c3363-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="c3363-106">Сведения о том, как использовать МRТК для достижения некоторых распространенных моделей взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c3363-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="c3363-107">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="c3363-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="c3363-108">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="c3363-108">How to grab and move an object?</span></span>
- <span data-ttu-id="c3363-109">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="c3363-109">How to resize an object?</span></span>
- <span data-ttu-id="c3363-110">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="c3363-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="c3363-111">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="c3363-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="c3363-112">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="c3363-112">How to add visual feedback?</span></span>
- <span data-ttu-id="c3363-113">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="c3363-113">How to add audio feedback?</span></span>
- <span data-ttu-id="c3363-114">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="c3363-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="c3363-115">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="c3363-115">How to make an object follow you?</span></span>
- <span data-ttu-id="c3363-116">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="c3363-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="c3363-117">Эта статья была обновлена с учетом изменений в [выпуске MRTK версии 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="c3363-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="c3363-118">Все содержимое на этой странице можно протестировать в редакторе Unity с имитацией ввода MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="c3363-119">Если вы еще не сделали этого, выполните инструкции из [руководства по установке MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), чтобы установить последнюю версию MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="c3363-120">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="c3363-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="c3363-121">МRТК поддерживает имитацию входных данных в редакторе.</span><span class="sxs-lookup"><span data-stu-id="c3363-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="c3363-122">Просто запустите сцену, нажав кнопку воспроизведения в Unity.</span><span class="sxs-lookup"><span data-stu-id="c3363-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="c3363-123">Следующие клавиши позволяют имитировать входные данные.</span><span class="sxs-lookup"><span data-stu-id="c3363-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="c3363-124">Чтобы переместить камеру, нажимайте клавиши W, A, S, D.</span><span class="sxs-lookup"><span data-stu-id="c3363-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="c3363-125">Чтобы посмотреть по сторонам, перемещайте мышь при нажатой правой кнопке мыши.</span><span class="sxs-lookup"><span data-stu-id="c3363-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="c3363-126">Чтобы имитировать поднятие рук вверх, нажмите клавишу пробела (для правой руки) или левую клавишу SHIFT (для левой руки). Чтобы имитировать удержание рук в зоне видимости, нажмите клавишу "T" или "Y", а чтобы имитировать поворот рук, нажимайте клавиши "Q" и "E" (горизонтально) или "R" и "F" (вертикально).</span><span class="sxs-lookup"><span data-stu-id="c3363-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="c3363-127">Дополнительные сведения об имитации входных данных см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="c3363-128">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="c3363-128">How to grab and move an object?</span></span>
<span data-ttu-id="c3363-129">Чтобы объект поддерживал захват и перемещение, назначьте ему следующие два скрипта: **ObjectManipulator.cs** и **NearInteractionGrabbable.cs** (для прямого захвата при отслеживании ввода с помощью рук). ObjectManipulator поддерживает как близкие, так и дальние взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c3363-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** (for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="c3363-130">Вы можете захватить и переместить объект с использованием ввода с помощью рук в HoloLens 2 (ближнее), телекинеза (дальнее), сигнала контроллера движения (дальнее), курсора взгляда HoloLens, а также касания (дальнее).</span><span class="sxs-lookup"><span data-stu-id="c3363-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="c3363-131">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="c3363-131">How to resize an object?</span></span>
<span data-ttu-id="c3363-132">**ObjectManipulator.cs** поддерживает масштабирование и вращение двумя руками.</span><span class="sxs-lookup"><span data-stu-id="c3363-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="c3363-133">Это работает с разными типами входных данных, например ввод с помощью рук в HoloLens 2, ввод с помощью взгляда и жестов в HoloLens 1 или контроллера движений иммерсивной гарнитуры в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c3363-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="c3363-134">Дополнительные сведения о компоненте Object Manipulator см. в документации по MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="c3363-135">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="c3363-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="c3363-136">Назначьте **BoundsControl.cs** объекту для использования ограничивающего прямоугольника, который представляет собой интерфейс для масштабирования и вращения объекта.</span><span class="sxs-lookup"><span data-stu-id="c3363-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="c3363-137">По умолчанию в нем отображаются синие маркеры и границы, как в HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="c3363-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="c3363-138">Чтобы использовать анимированные маркеры с учетом расстояния до объекта в стиле HoloLens 2, необходимо назначить заготовки и материалы.</span><span class="sxs-lookup"><span data-stu-id="c3363-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="c3363-139">Дополнительные сведения о компоненте Bounds Control см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="c3363-140">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="c3363-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="c3363-141">Назначьте **PointerHandler.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="c3363-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="c3363-142">В инспекторе вы сможете применить события OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Чтобы использовать эти события в скрипте, реализуйте **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="c3363-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="c3363-143">Дополнительные сведения о системе ввода см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="c3363-144">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="c3363-144">How to add visual feedback?</span></span>
<span data-ttu-id="c3363-145">Назначьте **Interactable.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="c3363-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="c3363-146">В инспекторе добавьте целевой объект и создайте тему.</span><span class="sxs-lookup"><span data-stu-id="c3363-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="c3363-147">С помощью интерактивных профилей темы вы сможете легко добавить визуальный отклик для всех доступных состояний взаимодействий ввода.</span><span class="sxs-lookup"><span data-stu-id="c3363-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="c3363-148">Интерактивный объект предоставляет несколько типов тем, в том числе тему shader, которая позволяет управлять параметрами текстуры для каждого состояния взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c3363-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="c3363-149">Дополнительные сведения об интерактивном объекте см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="c3363-150">Еще один важный строительный блок для создания визуального отклика — **стандартный шейдер MRTK**.</span><span class="sxs-lookup"><span data-stu-id="c3363-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="c3363-151">С помощью шейдера MRTK Standard можно легко добавлять визуальные эффекты для отклика, например эффект указателя и подсветки при приближении.</span><span class="sxs-lookup"><span data-stu-id="c3363-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="c3363-152">Стандартный шейдер MRTK выполняет намного меньше вычислений, чем стандартный шейдер Unity, поэтому позволяет создать высокопроизводительную среду взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="c3363-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="c3363-153">Создайте новый материал и выберите шейдер Mixed Reality Toolkit > Standard (Набор средств для смешанной реальности > Стандартный).</span><span class="sxs-lookup"><span data-stu-id="c3363-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="c3363-154">Вы также можете выбрать любой из существующих материалов, для которых настроен стандартный шейдер MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="c3363-155">Дополнительные сведения о стандартном шейдере MRTK см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="c3363-156">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="c3363-156">How to add audio feedback?</span></span>
<span data-ttu-id="c3363-157">Поместите **AudioSource** в объект.</span><span class="sxs-lookup"><span data-stu-id="c3363-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="c3363-158">Затем в скриптах, которые предоставляют нужные события ввода (например, Interactable.cs или PointerHandler.cs), назначьте объекту с AudioSource событие и выберите **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="c3363-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="c3363-159">Вы можете использовать собственные звуковые клипы или выбрать подходящий из числа звуковых активов MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="c3363-160">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="c3363-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="c3363-161">MRTK предоставляет несколько типов кнопок в стиле оболочки (ОС) HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3363-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="c3363-162">Они поддерживают сложные типы визуального отклика, например подсветка при приближении, прямоугольник сжатия и эффект ряби на поверхности кнопки, которые упрощают взаимодействие для пользователя.</span><span class="sxs-lookup"><span data-stu-id="c3363-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="c3363-163">Вам нужно лишь перетащить любую из **заготовок нажимаемых кнопок в стиле HoloLens 2** в сцену.</span><span class="sxs-lookup"><span data-stu-id="c3363-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="c3363-164">В заготовках используется описанный выше Interactable.cs.</span><span class="sxs-lookup"><span data-stu-id="c3363-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="c3363-165">Вы можете предоставлять в интерактивном объекте события для запуска действий, например OnClick().</span><span class="sxs-lookup"><span data-stu-id="c3363-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="c3363-166">Дополнительные сведения о заготовках кнопок см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="c3363-167">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="c3363-167">How to make an object follow you?</span></span>
<span data-ttu-id="c3363-168">Назначьте скрипт **RadialView.cs** или **Follow.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="c3363-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="c3363-169">Это часть целой серии скриптов Solver, которые позволяют использовать разные типы размещения объектов в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="c3363-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="c3363-170">**SolverHandler.cs** будет добавлен автоматически.</span><span class="sxs-lookup"><span data-stu-id="c3363-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="c3363-171">Ниже вы видите пример конфигурации RadialView, которая позволяет добиться поведения "ленивое следование", например начальное меню в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3363-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="c3363-172">Вы можете указать минимальную и максимальную дистанцию, а также минимальный и максимальный угол обзора.</span><span class="sxs-lookup"><span data-stu-id="c3363-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="c3363-173">В следующем примере представлен объект с расстоянием от 0,4 до 0,8 м и диапазоном углов 15°.</span><span class="sxs-lookup"><span data-stu-id="c3363-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="c3363-174">Измените значение параметра Lerp Time (Время линейной интерполяции), чтобы изменение положения выполнялось быстрее или медленнее.</span><span class="sxs-lookup"><span data-stu-id="c3363-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="c3363-175">Дополнительные сведения о инструменте решения см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="c3363-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="c3363-176">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="c3363-176">How to make an object face you?</span></span>
<span data-ttu-id="c3363-177">Назначьте скрипт **Billboard.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="c3363-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="c3363-178">Теперь этот объект всегда будет развернут к вам, независимо от вашего положения.</span><span class="sxs-lookup"><span data-stu-id="c3363-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="c3363-179">Вы можете указать расположение оси вращения.</span><span class="sxs-lookup"><span data-stu-id="c3363-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="c3363-180">Вы готовы создать великолепные взаимодействия для смешанной реальности?</span><span class="sxs-lookup"><span data-stu-id="c3363-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="c3363-181">Изучите предложенные ниже страницы, чтобы получить дополнительные сведения об MRTK и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c3363-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c3363-182">Об авторе</span><span class="sxs-lookup"><span data-stu-id="c3363-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c3363-183"><b>Дон Юн Парк</b> (Dong Yoon Park)</span><span class="sxs-lookup"><span data-stu-id="c3363-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c3363-184">Разработчик средств взаимодействия с пользователем @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c3363-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c3363-185">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="c3363-185">Next Development Checkpoint</span></span>

<span data-ttu-id="c3363-186">Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3363-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="c3363-187">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="c3363-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3363-188">Камера</span><span class="sxs-lookup"><span data-stu-id="c3363-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="c3363-189">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="c3363-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="c3363-190">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="c3363-190">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="c3363-191">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="c3363-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3363-192">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c3363-192">See also</span></span>
* [<span data-ttu-id="c3363-193">Руководство по установке MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c3363-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* <span data-ttu-id="c3363-194">[Набор средств для смешанной реальности (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="c3363-194">[Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span>
* [<span data-ttu-id="c3363-195">Портал документации по MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c3363-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="c3363-196">Рекомендации по переносу кода с HoloToolKit на MRTK</span><span class="sxs-lookup"><span data-stu-id="c3363-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
