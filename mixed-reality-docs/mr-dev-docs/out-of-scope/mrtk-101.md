---
title: Общие сведения об MRTK. Использование распространенных пространственных взаимодействий
description: Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия для HoloLens 2, HoloLens, Windows Mixed Reality и Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, проектирование, пример приложения, средства управления, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98248150"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="b9963-104">Общие сведения об MRTK. Как использовать Mixed Reality Toolkit в Unity для реализации стандартных пространственных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="b9963-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="b9963-106">Сведения о том, как использовать МRТК для достижения некоторых распространенных моделей взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b9963-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="b9963-107">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="b9963-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="b9963-108">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="b9963-108">How to grab and move an object?</span></span>
- <span data-ttu-id="b9963-109">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="b9963-109">How to resize an object?</span></span>
- <span data-ttu-id="b9963-110">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="b9963-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="b9963-111">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="b9963-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="b9963-112">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="b9963-112">How to add visual feedback?</span></span>
- <span data-ttu-id="b9963-113">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="b9963-113">How to add audio feedback?</span></span>
- <span data-ttu-id="b9963-114">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b9963-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="b9963-115">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="b9963-115">How to make an object follow you?</span></span>
- <span data-ttu-id="b9963-116">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="b9963-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="b9963-117">Эта статья была обновлена с учетом изменений в [выпуске MRTK версии 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="b9963-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="b9963-118">Все содержимое на этой странице можно протестировать в редакторе Unity с имитацией ввода MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9963-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="b9963-119">Если вы еще не сделали этого, выполните инструкции из [руководства по установке MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), чтобы установить последнюю версию MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9963-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="b9963-120">Как имитировать входные взаимодействия в редакторе Unity?</span><span class="sxs-lookup"><span data-stu-id="b9963-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="b9963-121">МRТК поддерживает имитацию входных данных в редакторе.</span><span class="sxs-lookup"><span data-stu-id="b9963-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="b9963-122">Запустите сцену, щелкнув кнопку воспроизведения в Unity, а затем примените следующие ключи для имитации ввода:</span><span class="sxs-lookup"><span data-stu-id="b9963-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="b9963-123">Чтобы переместить камеру, нажимайте клавиши W, A, S, D.</span><span class="sxs-lookup"><span data-stu-id="b9963-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="b9963-124">Чтобы посмотреть по сторонам, перемещайте мышь при нажатой правой кнопке мыши.</span><span class="sxs-lookup"><span data-stu-id="b9963-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="b9963-125">Нажмите клавишу пробела (правой рукой) или клавишу SHIFT (левой рукой), чтобы отобразить имитацию рук.</span><span class="sxs-lookup"><span data-stu-id="b9963-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="b9963-126">Нажмите клавишу T или Y, чтобы вернуть имитацию рук в поле зрения.</span><span class="sxs-lookup"><span data-stu-id="b9963-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="b9963-127">Нажимайте клавиши Q или E (горизонтальное вращение), а также R или F (вертикальное вращение), чтобы вращать имитацию рук.</span><span class="sxs-lookup"><span data-stu-id="b9963-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="b9963-128">Дополнительные сведения об имитации ввода см. в [документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span><span class="sxs-lookup"><span data-stu-id="b9963-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="b9963-129">Как взять и переместить объект?</span><span class="sxs-lookup"><span data-stu-id="b9963-129">How to grab and move an object?</span></span>

<span data-ttu-id="b9963-130">Присоедините скрипты **ObjectManipulator.cs** и **NearInteractionGrabbable.cs**, чтобы разрешить захват объектов.</span><span class="sxs-lookup"><span data-stu-id="b9963-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="b9963-131">ObjectManipulator поддерживает ближние и дальние взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b9963-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="b9963-132">Вы можете захватить и переместить объект с использованием ввода с помощью рук в HoloLens 2 (ближнее), телекинеза (дальнее), сигнала контроллера движения (дальнее), курсора взгляда HoloLens, а также касания (дальнее).</span><span class="sxs-lookup"><span data-stu-id="b9963-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="b9963-133">Как изменить размер объекта?</span><span class="sxs-lookup"><span data-stu-id="b9963-133">How to resize an object?</span></span>
<span data-ttu-id="b9963-134">**ObjectManipulator.cs** поддерживает масштабирование и вращение двумя руками.</span><span class="sxs-lookup"><span data-stu-id="b9963-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="b9963-135">Этот скрипт работает с разными типами ввода, например с вводом с помощью рук на HoloLens 2, вводом с помощью взгляда и жестов на HoloLens 1 или контроллера движений иммерсивной гарнитуры в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b9963-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="b9963-136">Дополнительные сведения о компоненте Object Manipulator см. в документации по MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9963-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="b9963-137">Как аккуратно переместить или повернуть объект?</span><span class="sxs-lookup"><span data-stu-id="b9963-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="b9963-138">Назначьте **BoundsControl.cs** объекту для использования ограничивающего прямоугольника, который представляет собой интерфейс для масштабирования и вращения объекта.</span><span class="sxs-lookup"><span data-stu-id="b9963-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="b9963-139">По умолчанию в нем отображаются синие маркеры и границы, как в HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="b9963-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="b9963-140">Чтобы использовать анимированные маркеры с учетом расстояния до объекта в стиле HoloLens 2, необходимо назначить заготовки и материалы.</span><span class="sxs-lookup"><span data-stu-id="b9963-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="b9963-141">Дополнительные сведения о компоненте Bounds Control см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="b9963-142">Как сделать, чтобы объект реагировал на входные события?</span><span class="sxs-lookup"><span data-stu-id="b9963-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="b9963-143">Назначьте **PointerHandler.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="b9963-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="b9963-144">В инспекторе вы можете применять события OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Чтобы использовать эти события в скрипте, реализуйте **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="b9963-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="b9963-145">Дополнительные сведения о системе ввода см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="b9963-146">Как добавить визуальный отклик?</span><span class="sxs-lookup"><span data-stu-id="b9963-146">How to add visual feedback?</span></span>
<span data-ttu-id="b9963-147">Назначьте **Interactable.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="b9963-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="b9963-148">В инспекторе добавьте целевой объект и создайте тему.</span><span class="sxs-lookup"><span data-stu-id="b9963-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="b9963-149">С помощью интерактивных профилей темы вы сможете легко добавить визуальный отклик для всех доступных состояний взаимодействий ввода.</span><span class="sxs-lookup"><span data-stu-id="b9963-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="b9963-150">Интерактивный объект предоставляет несколько типов тем, в том числе тему shader, которая позволяет управлять параметрами текстуры для каждого состояния взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b9963-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="b9963-151">Дополнительные сведения об интерактивном объекте см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="b9963-152">Еще один важный строительный блок для создания визуального отклика — **стандартный шейдер MRTK**.</span><span class="sxs-lookup"><span data-stu-id="b9963-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="b9963-153">С помощью шейдера MRTK Standard можно легко добавлять визуальные эффекты для отклика, например эффект указателя и подсветки при приближении.</span><span class="sxs-lookup"><span data-stu-id="b9963-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="b9963-154">Стандартный шейдер MRTK выполняет меньше вычислений, чем стандартный шейдер Unity, поэтому позволяет создать высокопроизводительную среду взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b9963-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="b9963-155">Создайте новый материал и выберите шейдер Mixed Reality Toolkit > Standard (Набор средств для смешанной реальности > Стандартный).</span><span class="sxs-lookup"><span data-stu-id="b9963-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="b9963-156">Вы также можете выбрать любой из существующих материалов, для которых настроен стандартный шейдер MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9963-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="b9963-157">Дополнительные сведения о стандартном шейдере MRTK см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="b9963-158">Как добавить звуковой отклик?</span><span class="sxs-lookup"><span data-stu-id="b9963-158">How to add audio feedback?</span></span>
<span data-ttu-id="b9963-159">Поместите **AudioSource** в объект.</span><span class="sxs-lookup"><span data-stu-id="b9963-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="b9963-160">Затем в скриптах, которые предоставляют нужные события ввода (например, Interactable.cs или PointerHandler.cs), назначьте объекту с AudioSource событие и выберите **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="b9963-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="b9963-161">Вы можете использовать собственные звуковые клипы или выбрать подходящий из числа звуковых активов MRTK.</span><span class="sxs-lookup"><span data-stu-id="b9963-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="b9963-162">Как использовать заготовки кнопок в стиле HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="b9963-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="b9963-163">MRTK предоставляет различные типы кнопок в стиле оболочки (ОС) HoloLens 2, в том числе с визуальной обратной связью, такие как подсветка при приближении, прямоугольник сжатия и эффект ряби на поверхности кнопки, которые упрощают взаимодействие для пользователя.</span><span class="sxs-lookup"><span data-stu-id="b9963-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="b9963-164">Перетащите любую из **заготовок нажимаемых кнопок в стиле HoloLens 2** в сцену.</span><span class="sxs-lookup"><span data-stu-id="b9963-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="b9963-165">В заготовках используется описанный выше скрипт Interactable.cs.</span><span class="sxs-lookup"><span data-stu-id="b9963-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="b9963-166">Вы можете предоставлять в интерактивном объекте события для запуска действий, например OnClick().</span><span class="sxs-lookup"><span data-stu-id="b9963-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="b9963-167">Дополнительные сведения о заготовках кнопок см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="b9963-168">Как сделать, чтобы объект следовал за вами?</span><span class="sxs-lookup"><span data-stu-id="b9963-168">How to make an object follow you?</span></span>
<span data-ttu-id="b9963-169">Назначьте скрипт **RadialView.cs** или **Follow.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="b9963-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="b9963-170">Это часть целой серии по работе со скриптом средства решения, которые позволяют реализовать разные типы размещения объектов в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="b9963-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="b9963-171">**SolverHandler.cs** будет добавлен автоматически.</span><span class="sxs-lookup"><span data-stu-id="b9963-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="b9963-172">Ниже вы видите пример конфигурации RadialView, которая позволяет добиться поведения "ленивое следование", например начальное меню в оболочке HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b9963-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="b9963-173">Вы можете указать минимальную и максимальную дистанцию, а также минимальный и максимальный угол обзора.</span><span class="sxs-lookup"><span data-stu-id="b9963-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="b9963-174">В следующем примере представлен объект на расстоянии от 0,4 до 8,8 м в угле зрения 15°.</span><span class="sxs-lookup"><span data-stu-id="b9963-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="b9963-175">Измените значение параметра Lerp Time (Время линейной интерполяции), чтобы изменение положения выполнялось быстрее или медленнее.</span><span class="sxs-lookup"><span data-stu-id="b9963-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="b9963-176">Дополнительные сведения о инструменте решения см. в документации по МRТК.</span><span class="sxs-lookup"><span data-stu-id="b9963-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="b9963-177">Как сделать, чтобы объект поворачивался к вам?</span><span class="sxs-lookup"><span data-stu-id="b9963-177">How to make an object face you?</span></span>
<span data-ttu-id="b9963-178">Назначьте скрипт **Billboard.cs** объекту.</span><span class="sxs-lookup"><span data-stu-id="b9963-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="b9963-179">Теперь этот объект всегда будет развернут к вам, независимо от вашего положения.</span><span class="sxs-lookup"><span data-stu-id="b9963-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="b9963-180">Вы можете указать расположение оси вращения.</span><span class="sxs-lookup"><span data-stu-id="b9963-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="b9963-181">Вы готовы создать великолепные взаимодействия для смешанной реальности?</span><span class="sxs-lookup"><span data-stu-id="b9963-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="b9963-182">Изучите предложенные ниже страницы, чтобы получить дополнительные сведения об MRTK и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b9963-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b9963-183">Об авторе</span><span class="sxs-lookup"><span data-stu-id="b9963-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b9963-184"><b>Дон Юн Парк</b> (Dong Yoon Park)</span><span class="sxs-lookup"><span data-stu-id="b9963-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b9963-185">Разработчик средств взаимодействия с пользователем @Microsoft</span><span class="sxs-lookup"><span data-stu-id="b9963-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="b9963-186">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b9963-186">See also</span></span>
* [<span data-ttu-id="b9963-187">Руководство по установке MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b9963-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* <span data-ttu-id="b9963-188">[Набор средств для смешанной реальности (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="b9963-188">[Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span>
* [<span data-ttu-id="b9963-189">Портал документации по MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b9963-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b9963-190">Рекомендации по переносу кода с HoloToolKit на MRTK</span><span class="sxs-lookup"><span data-stu-id="b9963-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
