---
title: Служба моделирования ввода
description: Документация по службе моделирования ввода в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176961"
---
# <a name="input-simulation-service"></a><span data-ttu-id="a6497-104">Служба моделирования ввода</span><span class="sxs-lookup"><span data-stu-id="a6497-104">Input simulation service</span></span>

![Имитация ввода МРТК](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="a6497-106">С помощью имитации ввода МРТК можно тестировать различные типы взаимодействий в редакторе Unity, не создавая и не развертывая их на устройстве.</span><span class="sxs-lookup"><span data-stu-id="a6497-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="a6497-107">Это позволяет быстро перебирать свои идеи в процессе разработки и разработки.</span><span class="sxs-lookup"><span data-stu-id="a6497-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="a6497-108">Использование сочетаний клавиш и мыши для управления имитацией входных данных.</span><span class="sxs-lookup"><span data-stu-id="a6497-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="a6497-109">Служба моделирования ввода эмулирует поведение устройств и платформ, которые могут быть недоступны в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="a6497-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="a6497-110">Примеры приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="a6497-110">Examples include:</span></span>

* <span data-ttu-id="a6497-111">отслеживание головного устройства HoloLens или VR</span><span class="sxs-lookup"><span data-stu-id="a6497-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="a6497-112">жесты HoloLens руки</span><span class="sxs-lookup"><span data-stu-id="a6497-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="a6497-113">отслеживание HoloLens 2 с неуправляемыми манипуляторами</span><span class="sxs-lookup"><span data-stu-id="a6497-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="a6497-114">отслеживание HoloLens 2 глаз</span><span class="sxs-lookup"><span data-stu-id="a6497-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="a6497-115">Контроллеры устройств VR</span><span class="sxs-lookup"><span data-stu-id="a6497-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="a6497-116">Это не работает при использовании одноXRной эмуляции Unity > режим эмуляции = "имитировать в редакторе".</span><span class="sxs-lookup"><span data-stu-id="a6497-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="a6497-117">Имитация в редакторе Unity будет управляться от имитации ввода МРТК.</span><span class="sxs-lookup"><span data-stu-id="a6497-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="a6497-118">Чтобы использовать службу имитации ввода МРТК, необходимо установить XR holographic Emulator в режим эмуляции = *"нет"*</span><span class="sxs-lookup"><span data-stu-id="a6497-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="a6497-119">Как использовать моделирование ввода МРТК</span><span class="sxs-lookup"><span data-stu-id="a6497-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="a6497-120">Имитация ввода включена по умолчанию в профилях, поставляемых с МРТК.</span><span class="sxs-lookup"><span data-stu-id="a6497-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="a6497-121">Можно просто нажать кнопку **воспроизвести** , чтобы запустить сцену с поддержкой имитации ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="a6497-122">Для перемещения камеры нажмите клавиши **W, A, S, D, Q, E** .</span><span class="sxs-lookup"><span data-stu-id="a6497-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="a6497-123">Удерживайте **правую кнопку мыши** и наведите указатель мыши на нужное место.</span><span class="sxs-lookup"><span data-stu-id="a6497-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="a6497-124">Чтобы открыть имитацию руки, нажмите клавишу **пробела (справа)** или **клавишу SHIFT слева (слева)** .</span><span class="sxs-lookup"><span data-stu-id="a6497-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="a6497-125">Чтобы имитировать имитацию действий в представлении, нажмите клавишу **T** или **Y** .</span><span class="sxs-lookup"><span data-stu-id="a6497-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="a6497-126">Чтобы повернуть смоделированные руки, нажмите и удерживайте клавишу **CTRL** и переместите указатель мыши</span><span class="sxs-lookup"><span data-stu-id="a6497-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="a6497-127">Лист Памятка по с имитацией входных данных редактора</span><span class="sxs-lookup"><span data-stu-id="a6497-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="a6497-128">Нажмите **левую клавишу CTRL + H** в сцене хандинтерактионексамплес, чтобы открыть лист Памятка по с элементами управления имитацией входных данных.</span><span class="sxs-lookup"><span data-stu-id="a6497-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![Лист Памятка по МРТК моделирования входных данных](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="a6497-130">Включение службы моделирования ввода</span><span class="sxs-lookup"><span data-stu-id="a6497-130">Enabling the input simulation service</span></span>

<span data-ttu-id="a6497-131">В конфигурации поставщика входных системных данных для службы моделирования ввода можно настроить следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="a6497-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="a6497-132">**тип** должен быть *Microsoft. микседреалити. набор средств. Входные > Инпутсимулатионсервице*.</span><span class="sxs-lookup"><span data-stu-id="a6497-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="a6497-133">**Поддерживаемые платформы (-ы)** по умолчанию включают все платформы *редактора* , так как служба использует ввод с клавиатуры и с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="a6497-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="a6497-134">Службу моделирования ввода можно использовать на других конечных точках платформы, например в автономном режиме, изменив свойство **Supported Platform (s)** , включив в него нужные целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="a6497-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="a6497-135">Элемент управления камерой</span><span class="sxs-lookup"><span data-stu-id="a6497-135">Camera control</span></span>

<span data-ttu-id="a6497-136">Головное перемещение может эмулироваться службой моделирования ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="a6497-137">Вращение камеры</span><span class="sxs-lookup"><span data-stu-id="a6497-137">Rotating the camera</span></span>

1. <span data-ttu-id="a6497-138">Наведите указатель мыши на окно редактора окна просмотра.</span><span class="sxs-lookup"><span data-stu-id="a6497-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="a6497-139">*Может потребоваться щелкнуть окно, чтобы задать фокус ввода, если нажатие кнопки не работают.*</span><span class="sxs-lookup"><span data-stu-id="a6497-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="a6497-140">Нажмите и удерживайте **кнопку мыши** (по умолчанию — правая кнопка мыши).</span><span class="sxs-lookup"><span data-stu-id="a6497-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="a6497-141">Переместите указатель мыши в окне просмотра, чтобы повернуть камеру.</span><span class="sxs-lookup"><span data-stu-id="a6497-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="a6497-142">Используйте колесо прокрутки для поворота камеры вокруг направления представления.</span><span class="sxs-lookup"><span data-stu-id="a6497-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="a6497-143">Скорость вращения камеры можно настроить, изменив параметр **скорость отображения мыши** в профиле эмуляции ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="a6497-144">Кроме того, можно использовать / **вертикальные** горизонтальные оси для поворота камеры (по умолчанию: игровое устройство — аналоговый стик).</span><span class="sxs-lookup"><span data-stu-id="a6497-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="a6497-145">Перемещение камеры</span><span class="sxs-lookup"><span data-stu-id="a6497-145">Moving the camera</span></span>

<span data-ttu-id="a6497-146">Используйте вертикальные оси перемещение по **горизонтали** /  для перемещения камеры (по умолчанию — трассе Keys или игровой контроллер — левый аналоговый стик).</span><span class="sxs-lookup"><span data-stu-id="a6497-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="a6497-147">Расположение и угол поворота камеры можно задать явным образом в окне "средства".</span><span class="sxs-lookup"><span data-stu-id="a6497-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="a6497-148">Камеру можно сбросить до ее значения по умолчанию с помощью кнопки **Сброс** .</span><span class="sxs-lookup"><span data-stu-id="a6497-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="a6497-149">Моделирование контроллера</span><span class="sxs-lookup"><span data-stu-id="a6497-149">Controller simulation</span></span>

<span data-ttu-id="a6497-150">Имитация ввода поддерживает эмулированные устройства контроллера (т. е. контроллеры движения и руки).</span><span class="sxs-lookup"><span data-stu-id="a6497-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="a6497-151">Эти виртуальные контроллеры могут взаимодействовать с любым объектом, поддерживающим обычные контроллеры, например кнопками или объектами, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="a6497-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="a6497-152">Режим моделирования контроллера</span><span class="sxs-lookup"><span data-stu-id="a6497-152">Controller simulation mode</span></span>

<span data-ttu-id="a6497-153">В [окне средства моделирования ввода](#input-simulation-tools-window) в **режиме моделирования контроллера по умолчанию** переключается между тремя различными входными моделями.</span><span class="sxs-lookup"><span data-stu-id="a6497-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="a6497-154">Этот режим по умолчанию также можно задать в профиле имитации ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="a6497-155">*Руки*: имитирует полностью обозначающий устройство с данными о размещении.</span><span class="sxs-lookup"><span data-stu-id="a6497-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="a6497-156">эмулирует модель взаимодействия HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6497-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="a6497-157">В этом режиме можно имитировать взаимодействия, основанные на точном положении руки или использовании касания.</span><span class="sxs-lookup"><span data-stu-id="a6497-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="a6497-158">*Жесты руки*: имитирует упрощенную модель с помощью воздушного касания и основных жестов.</span><span class="sxs-lookup"><span data-stu-id="a6497-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="a6497-159">эмулирует [модель взаимодействия HoloLens](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="a6497-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="a6497-160">Управление фокусом осуществляется с помощью указателя взгляните.</span><span class="sxs-lookup"><span data-stu-id="a6497-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="a6497-161">Жест *касания* используется для взаимодействия с кнопками.</span><span class="sxs-lookup"><span data-stu-id="a6497-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="a6497-162">*Контроллер движения*. имитирует контроллер движения, используемый с наушниками VR, которые работают аналогично дальнему взаимодействию с четко написанными руки.</span><span class="sxs-lookup"><span data-stu-id="a6497-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="a6497-163">Эмулирует гарнитуру VR с моделью взаимодействия контроллеров.</span><span class="sxs-lookup"><span data-stu-id="a6497-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="a6497-164">Клавиши триггера, захвата и меню моделируются с помощью ввода с клавиатуры и мыши.</span><span class="sxs-lookup"><span data-stu-id="a6497-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="a6497-165">Имитация перемещения контроллера</span><span class="sxs-lookup"><span data-stu-id="a6497-165">Simulating controller movement</span></span>

<span data-ttu-id="a6497-166">Нажмите и удерживайте клавишу **управления для левого и правого контроллера** (по умолчанию *сдвиг* для левого контроллера и *пространства* для правого контроллера), чтобы получить контроль над любым контроллером.</span><span class="sxs-lookup"><span data-stu-id="a6497-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="a6497-167">При нажатии клавиши манипуляции контроллер появится в окне просмотра.</span><span class="sxs-lookup"><span data-stu-id="a6497-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="a6497-168">После освобождения ключа манипуляции контроллеры исчезают после того, как короткий **контроллер не сможет скрыть время ожидания**.</span><span class="sxs-lookup"><span data-stu-id="a6497-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="a6497-169">Контроллеры можно переключать и закрепить относительно камеры во [входном окне средства моделирования](#input-simulation-tools-window) или путем нажатия клавиши "переключить **левый/правый контроллер** " (по умолчанию: *T* для Left и *Y* для прав).</span><span class="sxs-lookup"><span data-stu-id="a6497-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="a6497-170">Снова нажмите клавишу Toggle, чтобы снова скрыть контроллеры.</span><span class="sxs-lookup"><span data-stu-id="a6497-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="a6497-171">Для управления контроллерами необходимо удерживать **левый или правый ключ манипуляции с контроллером** .</span><span class="sxs-lookup"><span data-stu-id="a6497-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="a6497-172">Двойное касание **ключа манипуляции с левым или правым контроллером** также может включать и отключать контроллеры.</span><span class="sxs-lookup"><span data-stu-id="a6497-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="a6497-173">Перемещение мыши переместит контроллер на плоскости просмотра.</span><span class="sxs-lookup"><span data-stu-id="a6497-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="a6497-174">Контроллеры можно перемещать на камеру или ближе к камере с помощью **колесика мыши**.</span><span class="sxs-lookup"><span data-stu-id="a6497-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="a6497-175">Чтобы поворачивать контроллеры с помощью мыши, удерживайте нажатой **левый/правый ключ манипуляции** (*сдвиг влево* или *пробел*) *и* **кнопку вращения контроллера** (по умолчанию — кнопка с *левой* кнопкой мыши), а затем передвиньте мышь, чтобы повернуть контроллер.</span><span class="sxs-lookup"><span data-stu-id="a6497-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="a6497-176">Скорость смены контроллера можно настроить, изменив параметр **скорость вращения контроллера мыши** в профиле моделирования ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="a6497-177">Кроме того, размещение можно изменить в [окне средства моделирования ввода](#input-simulation-tools-window), включая сброс настроек по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a6497-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="a6497-178">Дополнительные параметры профиля</span><span class="sxs-lookup"><span data-stu-id="a6497-178">Additional profile settings</span></span>

* <span data-ttu-id="a6497-179">**Множитель глубины контроллера** управляет чувствительностью перемещения колесика мыши к прокрутке.</span><span class="sxs-lookup"><span data-stu-id="a6497-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="a6497-180">Чем больше значение, тем ускоряется увеличение масштаба контроллера.</span><span class="sxs-lookup"><span data-stu-id="a6497-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="a6497-181">**Расстояние по контроллеру по умолчанию** — это начальное расстояние контроллеров от камеры.</span><span class="sxs-lookup"><span data-stu-id="a6497-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="a6497-182">При нажатии кнопки **Сброс** контроллеры также будут размещаться контроллеры на этом расстоянии.</span><span class="sxs-lookup"><span data-stu-id="a6497-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="a6497-183">**Величина колебаний контроллера** добавляет случайное движение к контроллерам.</span><span class="sxs-lookup"><span data-stu-id="a6497-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="a6497-184">Эта функция может использоваться для имитации неточного отслеживания контроллеров на устройстве и обеспечения удобного взаимодействия с шумами ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="a6497-185">Жесты руками</span><span class="sxs-lookup"><span data-stu-id="a6497-185">Hand gestures</span></span>

<span data-ttu-id="a6497-186">Также можно имитировать жесты, такие как сжатие, броские, знакомство и т. д.</span><span class="sxs-lookup"><span data-stu-id="a6497-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="a6497-187">Включение элемента управления "рука" с помощью **ключа манипуляции с левым или правым контроллером** (*сдвиг влево* или *пробел*)</span><span class="sxs-lookup"><span data-stu-id="a6497-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="a6497-188">При манипуляции нажмите и удерживайте кнопку мыши, чтобы выполнить жест руки.</span><span class="sxs-lookup"><span data-stu-id="a6497-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="a6497-189">Каждая кнопка мыши может быть сопоставлена с преобразованием формы руки в другой жест, используя параметры *левого или среднего или правого жеста мыши* .</span><span class="sxs-lookup"><span data-stu-id="a6497-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="a6497-190">*По умолчанию используется жест* руки, если кнопка не нажата.</span><span class="sxs-lookup"><span data-stu-id="a6497-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="a6497-191">Жест *сжатия* — это единственный жест, выполняющий действие "Select" на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="a6497-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="a6497-192">Односторонняя манипуляция</span><span class="sxs-lookup"><span data-stu-id="a6497-192">One-hand manipulation</span></span>

1. <span data-ttu-id="a6497-193">Нажмите и удерживайте клавишу **управления "левый/правый" контроллер** (*сдвиг влево* или *пробел*)</span><span class="sxs-lookup"><span data-stu-id="a6497-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="a6497-194">Точка на объекте</span><span class="sxs-lookup"><span data-stu-id="a6497-194">Point at object</span></span>
3. <span data-ttu-id="a6497-195">Удерживайте кнопку мыши для сжатия</span><span class="sxs-lookup"><span data-stu-id="a6497-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="a6497-196">Перемещение объекта с помощью мыши</span><span class="sxs-lookup"><span data-stu-id="a6497-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="a6497-197">Отпустите кнопку мыши, чтобы прекратить взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a6497-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="a6497-198">Манипуляция с двумя рукой</span><span class="sxs-lookup"><span data-stu-id="a6497-198">Two-hand manipulation</span></span>

<span data-ttu-id="a6497-199">Для манипулирования объектами с двумя практическими операциями рекомендуется использовать режим постоянной обработки.</span><span class="sxs-lookup"><span data-stu-id="a6497-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="a6497-200">Переключитесь в обе руки, нажав клавиши переключения (*T/Y*).</span><span class="sxs-lookup"><span data-stu-id="a6497-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="a6497-201">Управлять одной рукой за раз:</span><span class="sxs-lookup"><span data-stu-id="a6497-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="a6497-202">Удержание **пространства** для управления правой рукой</span><span class="sxs-lookup"><span data-stu-id="a6497-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="a6497-203">Переместить руку в то место, куда нужно захватить объект</span><span class="sxs-lookup"><span data-stu-id="a6497-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="a6497-204">Нажмите **левую кнопку мыши** , чтобы активировать жест *сжатия* .</span><span class="sxs-lookup"><span data-stu-id="a6497-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="a6497-205">**Место** выпуска для отмены управления правой стороны.</span><span class="sxs-lookup"><span data-stu-id="a6497-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="a6497-206">Рука будет зафиксирована и заблокирована для жеста *сжатия* , так как он больше не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="a6497-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="a6497-207">Повторите процесс с другой стороны, извлеките один и тот же объект во вторую точку.</span><span class="sxs-lookup"><span data-stu-id="a6497-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="a6497-208">Теперь, когда обе руки изменяют один и тот же объект, можно переместить любой из них, чтобы выполнить двустороннюю манипуляцию.</span><span class="sxs-lookup"><span data-stu-id="a6497-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="a6497-209">Взаимодействие ГГВ (взгляд, жест и речь)</span><span class="sxs-lookup"><span data-stu-id="a6497-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="a6497-210">По умолчанию взаимодействие ГГВ включено в редакторе, в то время как в сцене отсутствуют четко сформулированные руки.</span><span class="sxs-lookup"><span data-stu-id="a6497-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="a6497-211">Повернуть камеру, чтобы она указывала курсор взгляда на взаимодействующий объект (правая кнопка мыши)</span><span class="sxs-lookup"><span data-stu-id="a6497-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="a6497-212">Нажмите и удерживайте **левую кнопку мыши** для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a6497-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="a6497-213">Снова поверните камеру для работы с объектом</span><span class="sxs-lookup"><span data-stu-id="a6497-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="a6497-214">Это можно отключить, включив параметр " *доступно без поддержки ввода* " в профиле эмуляции ввода.</span><span class="sxs-lookup"><span data-stu-id="a6497-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="a6497-215">Кроме того, можно использовать смоделированные руки для взаимодействия ГГВ.</span><span class="sxs-lookup"><span data-stu-id="a6497-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="a6497-216">Включение имитации ГГВ путем переключения **режима моделирования вручную** на *жесты* в [профиле моделирования ввода](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="a6497-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="a6497-217">Повернуть камеру, чтобы она указывала курсор взгляда на взаимодействующий объект (правая кнопка мыши)</span><span class="sxs-lookup"><span data-stu-id="a6497-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="a6497-218">Удержание **пространства** для управления правой рукой</span><span class="sxs-lookup"><span data-stu-id="a6497-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="a6497-219">Нажмите и удерживайте **левую кнопку мыши** для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a6497-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="a6497-220">Перемещение объекта с помощью мыши</span><span class="sxs-lookup"><span data-stu-id="a6497-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="a6497-221">Отпустите кнопку мыши, чтобы прекратить взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a6497-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="a6497-222">Создание событий телепортируйтесь</span><span class="sxs-lookup"><span data-stu-id="a6497-222">Raising Teleport Events</span></span>

<span data-ttu-id="a6497-223">чтобы вызвать событие телепортируйтесь во время моделирования ввода, настройте жест руки Параметры в профиле имитации ввода, чтобы он выполнял жест **запуска телепортируйтесь** , а другой выполняет жест **конца телепортируйтесь** .</span><span class="sxs-lookup"><span data-stu-id="a6497-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="a6497-224">Жест **запуска телепортируйтесь** выводит указатель телепортируйтесь, а **Окончание** жесуреа телепортируйтесь завершит действие телепортируйтесь и переместит пользователя.</span><span class="sxs-lookup"><span data-stu-id="a6497-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="a6497-225">Y-расположение полученного телепортировать зависит от смещения камеры вдоль оси y.</span><span class="sxs-lookup"><span data-stu-id="a6497-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="a6497-226">В редакторе по умолчанию это 0, поэтому используйте клавиши **Q** и **E** , чтобы изменить высоту.</span><span class="sxs-lookup"><span data-stu-id="a6497-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![моделирование входных данных телепортируйтесь Параметры](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="a6497-228">Взаимодействие с контроллером движения</span><span class="sxs-lookup"><span data-stu-id="a6497-228">Motion controller interaction</span></span>

<span data-ttu-id="a6497-229">Смоделированные контроллеры движения можно манипулировать так же, как и руки.</span><span class="sxs-lookup"><span data-stu-id="a6497-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="a6497-230">Модель взаимодействия схожа с назначением руки, когда ключи триггера, сочетания клавиш и меню сопоставлены с *левой кнопкой мыши*, *G* и *M* соответственно.</span><span class="sxs-lookup"><span data-stu-id="a6497-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="a6497-231">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="a6497-231">Eye tracking</span></span>

<span data-ttu-id="a6497-232">[Моделирование отслеживания глаз](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) можно включить, установив флажок **имитировать глаз** в [профиле имитации ввода](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="a6497-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="a6497-233">Его не следует использовать с ГГВ или взаимодействия с стилем контроллера движения (поэтому убедитесь, что для **режима имитации контроллера по умолчанию** задано значение " *руки*").</span><span class="sxs-lookup"><span data-stu-id="a6497-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="a6497-234">Окно средств моделирования ввода</span><span class="sxs-lookup"><span data-stu-id="a6497-234">Input simulation tools window</span></span>

<span data-ttu-id="a6497-235">включите окно средства моделирования входных данных из   >    >  меню "имитация" набор средств **служебных программ** смешанной реальности  >   .</span><span class="sxs-lookup"><span data-stu-id="a6497-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="a6497-236">Это окно предоставляет доступ к состоянию имитации ввода в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="a6497-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="a6497-237">Кнопки окна просмотра (необязательно)</span><span class="sxs-lookup"><span data-stu-id="a6497-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="a6497-238">Prefab для кнопок в редакторе, позволяющих управлять базовым размещением вручную, можно указать в профиле моделирования ввода в разделе **индикаторы prefab**.</span><span class="sxs-lookup"><span data-stu-id="a6497-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="a6497-239">Это необязательная служебная программа. к тем же функциям можно обращаться в [окне средства моделирования ввода](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="a6497-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="a6497-240">Индикаторы окна просмотра по умолчанию отключены, так как в настоящее время они могут мешать взаимодействию с ИП Unity.</span><span class="sxs-lookup"><span data-stu-id="a6497-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="a6497-241">См. раздел Issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span><span class="sxs-lookup"><span data-stu-id="a6497-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="a6497-242">Чтобы включить, добавьте Инпутсимулатиониндикаторс prefab в **индикаторы prefab**.</span><span class="sxs-lookup"><span data-stu-id="a6497-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="a6497-243">Значки руки показывают состояние имитации руки:</span><span class="sxs-lookup"><span data-stu-id="a6497-243">Hand icons show the state of the simulated hands:</span></span>

* ![Значок незаписанного руки](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="a6497-245&quot;>Рука не отслеживается.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a6497-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;a6497-246&quot;>Щелкните, чтобы включить руку.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a6497-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;a6497-247&quot;>![Значок с изображением руки](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Значок с изображением руки") Рука передается, но не контролируется пользователем.</span><span class="sxs-lookup"><span data-stu-id="a6497-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="a6497-248">Щелкните, чтобы скрыть руку.</span><span class="sxs-lookup"><span data-stu-id="a6497-248">Click to hide the hand.</span></span>
* <span data-ttu-id="a6497-249">![Управляемый значок руки](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Управляемый значок руки") Рука и контролируется пользователем.</span><span class="sxs-lookup"><span data-stu-id="a6497-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="a6497-250">Щелкните, чтобы скрыть руку.</span><span class="sxs-lookup"><span data-stu-id="a6497-250">Click to hide the hand.</span></span>
* <span data-ttu-id="a6497-251">![Значок сброса руки](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Значок сброса руки") Щелкните, чтобы сбросить руку на стандартное расположение.</span><span class="sxs-lookup"><span data-stu-id="a6497-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="a6497-252">См. также:</span><span class="sxs-lookup"><span data-stu-id="a6497-252">See also</span></span>

* <span data-ttu-id="a6497-253">[Входной системный профиль](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="a6497-253">[Input System profile](../input/input-providers.md).</span></span>
