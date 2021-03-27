---
title: Настройка камеры в Unity
description: Узнайте, как настроить и использовать основную камеру Unity для разработки Windows Mixed Reality для работы с Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, holographic, holographic, впечатляющий, захватывающий пункт, буфер глубины, только ориентация, Позиционированный, непрозрачный, прозрачный, зажим, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636307"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="aa116-104">Настройка камеры в Unity</span><span class="sxs-lookup"><span data-stu-id="aa116-104">Camera setup in Unity</span></span>

<span data-ttu-id="aa116-105">При износе гарнитуры смешанной реальности он станет центром в holographic-мире.</span><span class="sxs-lookup"><span data-stu-id="aa116-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="aa116-106">Компонент [камеры](https://docs.unity3d.com/Manual/class-Camera.html) Unity автоматически обрабатывает стереоскопикную визуализацию и поддерживайте свое головное перемещение и вращение.</span><span class="sxs-lookup"><span data-stu-id="aa116-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="aa116-107">Однако, чтобы полностью оптимизировать качество визуальных элементов и [стабильность](../platform-capabilities-and-apis/hologram-stability.md), необходимо задать параметры камеры, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="aa116-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="aa116-108">Наушники и иммерсивное виртуальная гарнитура HoloLens</span><span class="sxs-lookup"><span data-stu-id="aa116-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="aa116-109">Параметры по умолчанию для компонента камеры Unity предназначены для традиционных трехмерных приложений, которым требуется скибокс фон, так как у них нет реального мира.</span><span class="sxs-lookup"><span data-stu-id="aa116-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="aa116-110">При работе на **[иммерсивного гарнитуре](../../discover/immersive-headset-hardware-details.md)** вы получаете все, что видит пользователь, и поэтому вам, скорее всего, потребуется скибокс.</span><span class="sxs-lookup"><span data-stu-id="aa116-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="aa116-111">Однако при работе на **гарнитуре holographic** , такой как [HoloLens](/hololens/hololens2-hardware), реальный мир должен отображаться позади всей визуализации камеры.</span><span class="sxs-lookup"><span data-stu-id="aa116-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="aa116-112">Установите прозрачный фон камеры (в HoloLens, черный отображается как прозрачный) вместо текстуры Скибокс:</span><span class="sxs-lookup"><span data-stu-id="aa116-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="aa116-113">Выбор основной камеры на панели Иерархия</span><span class="sxs-lookup"><span data-stu-id="aa116-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="aa116-114">На панели инспектора найдите компонент Камера и измените раскрывающийся список нечетких флагов с Скибокс на сплошной цвет.</span><span class="sxs-lookup"><span data-stu-id="aa116-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="aa116-115">Выберите средство выбора цвета фона и измените значения RGBA на (0, 0, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="aa116-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="aa116-116">При задании этого значения из кода можно использовать [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="aa116-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="aa116-117">Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="aa116-117">Camera setup</span></span>

<span data-ttu-id="aa116-118">Какой бы опыт вы разрабатываете, основная камера всегда является основным компонентом для отображения стерео, подключенным к подключенному к головному дисплею устройства.</span><span class="sxs-lookup"><span data-stu-id="aa116-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="aa116-119">Если вы представиме начальную точку пользователя как (X: 0, Y: 0, Z: 0), будет проще размещать приложение.</span><span class="sxs-lookup"><span data-stu-id="aa116-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="aa116-120">Так как основная камера отслеживает перемещение заголовка пользователя, начальное расположение пользователя можно задать, установив начальную точку основной камеры.</span><span class="sxs-lookup"><span data-stu-id="aa116-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="aa116-121">Вам нужно выбрать вариант разработки для головных телефонов HoloLens или VR.</span><span class="sxs-lookup"><span data-stu-id="aa116-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="aa116-122">После этого перейдите в любой раздел установки.</span><span class="sxs-lookup"><span data-stu-id="aa116-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="aa116-123">Настройка камеры HoloLens</span><span class="sxs-lookup"><span data-stu-id="aa116-123">HoloLens camera setup</span></span>

<span data-ttu-id="aa116-124">Для приложений HoloLens необходимо использовать привязки для всех объектов, которые необходимо заблокировать в среде сцены.</span><span class="sxs-lookup"><span data-stu-id="aa116-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="aa116-125">Для повышения стабильности и создания привязок в нескольких комнатах рекомендуется использовать неограниченный объем памяти.</span><span class="sxs-lookup"><span data-stu-id="aa116-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="aa116-126">Настройка камеры VR</span><span class="sxs-lookup"><span data-stu-id="aa116-126">VR camera setup</span></span>

<span data-ttu-id="aa116-127">Windows Mixed Reality поддерживает приложения в различных [масштабах](../../design/coordinate-systems.md#mixed-reality-experience-scales), начиная с приложений с ориентацией на страницы и до крупномасштабных приложений.</span><span class="sxs-lookup"><span data-stu-id="aa116-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="aa116-128">В HoloLens вы можете создавать приложения для мирового уровня, которые позволяют пользователям проходить более чем за 5 метров, изучая целый ряд здания и выходят за рамки.</span><span class="sxs-lookup"><span data-stu-id="aa116-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="aa116-129">Первым шагом в создании смешанной реальности в Unity является определение того, для чего будет работать [масштабирование](../../design/coordinate-systems.md) приложения.</span><span class="sxs-lookup"><span data-stu-id="aa116-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="aa116-130">Ориентация или установленный масштаб</span><span class="sxs-lookup"><span data-stu-id="aa116-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="aa116-131">С фиксированным или комнатным масштабированием</span><span class="sxs-lookup"><span data-stu-id="aa116-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="aa116-132">Масштаб мира</span><span class="sxs-lookup"><span data-stu-id="aa116-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="aa116-133">Комната — масштабирование или фиксированное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="aa116-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="aa116-134">При создании для HL2 рекомендуется создать интерфейс на уровне глаз или рассмотреть возможность использования [сцены для понимания](../platform-capabilities-and-apis/scene-understanding-sdk.md) основания сцены.</span><span class="sxs-lookup"><span data-stu-id="aa116-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="aa116-135">Опыт работы в рабочее место</span><span class="sxs-lookup"><span data-stu-id="aa116-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="aa116-136">Настройка фона камеры</span><span class="sxs-lookup"><span data-stu-id="aa116-136">Setting up the camera background</span></span>

<span data-ttu-id="aa116-137">Если вы используете МРТК, фон камеры автоматически настраивается и управляется.</span><span class="sxs-lookup"><span data-stu-id="aa116-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="aa116-138">Для XR SDK или устаревших проектов WSA мы рекомендуем задать для фона камеры сплошной черный цвет в HoloLens и сохранить скибокс для VR.</span><span class="sxs-lookup"><span data-stu-id="aa116-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="aa116-139">Использование нескольких камер</span><span class="sxs-lookup"><span data-stu-id="aa116-139">Using multiple cameras</span></span>

<span data-ttu-id="aa116-140">Если в сцене имеется несколько компонентов камеры, Unity знает, какая камера будет использоваться для отрисовки стереоскопик на основе того, в какой GameObject есть тег Маинкамера.</span><span class="sxs-lookup"><span data-stu-id="aa116-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="aa116-141">В устаревшем XR он также использует этот тег для синхронизации головного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="aa116-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="aa116-142">В пакете SDK для XR отслеживание головного элемента осуществляется с помощью сценария Траккедпоседривер, подключенного к камере.</span><span class="sxs-lookup"><span data-stu-id="aa116-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="aa116-143">Совместное использование буферов глубины</span><span class="sxs-lookup"><span data-stu-id="aa116-143">Sharing depth buffers</span></span>

<span data-ttu-id="aa116-144">Предоставление общего доступа к буферу глубины приложения в Windows. Каждый кадр обеспечит ваше приложение одним из двух усовершенствований в голограммах, в зависимости от типа гарнитуры, для которой выполняется подготовка.</span><span class="sxs-lookup"><span data-stu-id="aa116-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="aa116-145">При постановке в буфер глубины иммерсивное виртуальная **гарнитура** может позаботиться о позиционированном перепроецировании, настраивая голограммы для неверного предсказания как на позиции, так и на ориентации.</span><span class="sxs-lookup"><span data-stu-id="aa116-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="aa116-146">**Гарнитуры HoloLens** имеют несколько различных методов.</span><span class="sxs-lookup"><span data-stu-id="aa116-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="aa116-147">HoloLens 1 автоматически выберет [точку фокусировки](focus-point-in-unity.md) при указании буфера глубины, оптимизируя голограмму на уровне, пересекающую наибольшее содержимое.</span><span class="sxs-lookup"><span data-stu-id="aa116-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="aa116-148">HoloLens 2 будет стабилизировать содержимое, используя [глубину ЛСР (см. примечания)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span><span class="sxs-lookup"><span data-stu-id="aa116-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="aa116-149">Использование отсечения плоскостей</span><span class="sxs-lookup"><span data-stu-id="aa116-149">Using clipping planes</span></span>

<span data-ttu-id="aa116-150">Визуализация содержимого слишком близко к пользователю может быть неудобно в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="aa116-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="aa116-151">В компоненте камеры можно настроить [близкие и более далекое плоскости](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) .</span><span class="sxs-lookup"><span data-stu-id="aa116-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="aa116-152">Выбор **основной камеры** на панели **Иерархия**</span><span class="sxs-lookup"><span data-stu-id="aa116-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="aa116-153">На панели **инспектора** найдите компонент **камеры** **обтравочные плоскости** и измените значение поля **NEAR** TextBox с **0,3** на **0,85**.</span><span class="sxs-lookup"><span data-stu-id="aa116-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="aa116-154">Содержимое, отображаемое еще ближе, может привести к дискомфорт пользователя, и его следует избегать в соответствии с [рекомендациями по расстоянию при визуализации](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span><span class="sxs-lookup"><span data-stu-id="aa116-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="aa116-155">Перецентрирование камеры</span><span class="sxs-lookup"><span data-stu-id="aa116-155">Recentering the camera</span></span>

<span data-ttu-id="aa116-156">Если вы создаете [опыт](../../design/coordinate-systems.md)в области, вы можете изменить центр по всему миру в текущей позиции головного пользователя, вызвав **[XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** в устаревшем XR или методе **[Ксринпутсубсистем. ТРИРЕЦЕНТЕР](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** в XR SDK.</span><span class="sxs-lookup"><span data-stu-id="aa116-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="aa116-157">Телепортация</span><span class="sxs-lookup"><span data-stu-id="aa116-157">Teleportation</span></span>

<span data-ttu-id="aa116-158">Эта функция обычно зарезервирована для среды VR:</span><span class="sxs-lookup"><span data-stu-id="aa116-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="aa116-159">Режимы РЕПРОЕКЦИИ</span><span class="sxs-lookup"><span data-stu-id="aa116-159">Reprojection modes</span></span>

<span data-ttu-id="aa116-160">Как HoloLens, так и иммерсивное гарнитуры будут перестраивать каждый кадр, отображаемый приложением, для коррекции неверного предсказания фактического расположения пользователя при выдаче фотоны.</span><span class="sxs-lookup"><span data-stu-id="aa116-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="aa116-161">По умолчанию:</span><span class="sxs-lookup"><span data-stu-id="aa116-161">By default:</span></span>

* <span data-ttu-id="aa116-162">Если приложение предоставляет буфер глубины для данного кадра **, то** позаботится о позиционированной РЕПРОЕКЦИИ.</span><span class="sxs-lookup"><span data-stu-id="aa116-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="aa116-163">Иммерсивное гарнитура также настраивают голограммы для неверного предсказания как в положении, так и на ориентации.</span><span class="sxs-lookup"><span data-stu-id="aa116-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="aa116-164">Если буфер глубины не указан, система будет исправлять только неправильные прогнозы по ориентации.</span><span class="sxs-lookup"><span data-stu-id="aa116-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="aa116-165">В случае с более **holographicми гарнитурами** , такими как HoloLens 2, позаботится о том, предоставляет ли приложение свой буфер глубины.</span><span class="sxs-lookup"><span data-stu-id="aa116-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="aa116-166">Позиционированное перестановка возможно без буферов глубины в HoloLens, так как отрисовка часто является разреженной с стабильным фоном, обеспечиваемым реальным миром.</span><span class="sxs-lookup"><span data-stu-id="aa116-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="aa116-167">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="aa116-167">Next Development Checkpoint</span></span>

<span data-ttu-id="aa116-168">Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core.</span><span class="sxs-lookup"><span data-stu-id="aa116-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="aa116-169">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="aa116-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa116-170">Взгляд</span><span class="sxs-lookup"><span data-stu-id="aa116-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="aa116-171">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="aa116-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="aa116-172">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="aa116-172">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="aa116-173">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="aa116-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa116-174">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="aa116-174">See also</span></span>

* [<span data-ttu-id="aa116-175">Стабильность голограммы</span><span class="sxs-lookup"><span data-stu-id="aa116-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="aa116-176">Масштабирование работы</span><span class="sxs-lookup"><span data-stu-id="aa116-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="aa116-177">Пространственный этап</span><span class="sxs-lookup"><span data-stu-id="aa116-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="aa116-178">Потеря слежения в Unity</span><span class="sxs-lookup"><span data-stu-id="aa116-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="aa116-179">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="aa116-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="aa116-180">Сохраняемость в Unity</span><span class="sxs-lookup"><span data-stu-id="aa116-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="aa116-181">Общий доступ в Unity</span><span class="sxs-lookup"><span data-stu-id="aa116-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="aa116-182">Пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="aa116-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="aa116-183">Пакет SDK для пространственных привязок Azure для Unity</span><span class="sxs-lookup"><span data-stu-id="aa116-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)