---
title: Отрисовка в DirectX
description: Описание более holographic для Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, отрисовка, трехмерная графика, Холографикфраме, цикл отрисовки, цикл обновления, пошаговое руководство, пример кода, Direct3D
ms.openlocfilehash: 4c1e6207dd7e858a323ea5234f2849e6a3bdfab3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691469"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="9952f-104">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="9952f-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="9952f-105">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="9952f-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="9952f-106">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)** .</span><span class="sxs-lookup"><span data-stu-id="9952f-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)** .</span></span>

<span data-ttu-id="9952f-107">Windows Mixed Reality построена на основе DirectX для создания полнофункциональных трехмерных графических интерфейсов для пользователей.</span><span class="sxs-lookup"><span data-stu-id="9952f-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="9952f-108">Абстракция отрисовки располагается непосредственно над DirectX и позволяет приложению определить положение и ориентацию одного или нескольких наблюдателей holographic-сцены, прогнозируемой системой.</span><span class="sxs-lookup"><span data-stu-id="9952f-108">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="9952f-109">После этого разработчик может размещать свои голограммы относительно каждой камеры, позволяя приложению визуализировать эти голограммы в различных пространственных системах координат по мере перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="9952f-109">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="9952f-110">Примечание. в этом пошаговом руководстве описывается обработка в Direct3D 11 более Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="9952f-111">Шаблон приложения Windows Mixed Reality с Direct3D 12 также предоставляется с расширением шаблонов приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9952f-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="9952f-112">Обновление текущего кадра</span><span class="sxs-lookup"><span data-stu-id="9952f-112">Update for the current frame</span></span>

<span data-ttu-id="9952f-113">Чтобы обновить состояние приложения для голограмм, один раз для каждого кадра приложение будет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9952f-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="9952f-114">Получение <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> из системы управления отображением.</span><span class="sxs-lookup"><span data-stu-id="9952f-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="9952f-115">Обновите сцену, используя текущий прогноз, где будет отображаться представление камеры после завершения подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="9952f-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="9952f-116">Обратите внимание, что для «holographic» сцены может существовать более одной камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="9952f-117">Для отображения в представлениях с Камером holographic, один раз для каждого кадра, приложение будет выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9952f-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="9952f-118">Для каждой камеры Визуализируйте сцену для текущего кадра, используя матрицы представления камеры и проекции из системы.</span><span class="sxs-lookup"><span data-stu-id="9952f-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="9952f-119">Создание нового пакета holographic и получение его прогноза</span><span class="sxs-lookup"><span data-stu-id="9952f-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="9952f-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Холографикфраме</a> содержит сведения, необходимые приложению для обновления и отрисовки текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="9952f-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="9952f-121">Приложение начинает каждый новый кадр, вызывая метод **креатенекстфраме** .</span><span class="sxs-lookup"><span data-stu-id="9952f-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="9952f-122">При вызове этого метода прогнозы выполняются с использованием последних доступных данных датчика и инкапсулированы в объект **куррентпредиктион** .</span><span class="sxs-lookup"><span data-stu-id="9952f-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="9952f-123">Для каждого отображаемого кадра должен использоваться новый объект Frame, так как он действителен только для мгновенного выполнения.</span><span class="sxs-lookup"><span data-stu-id="9952f-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="9952f-124">Свойство **куррентпредиктион** содержит такие сведения, как расположение камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="9952f-125">Данные выделяются на конкретный момент времени, когда фрейм должен быть видимым для пользователя.</span><span class="sxs-lookup"><span data-stu-id="9952f-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="9952f-126">Следующий код взят из **аппмаин:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-126">The following code is excerpted from **AppMain::Update** :</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="9952f-127">Обработка обновлений камеры</span><span class="sxs-lookup"><span data-stu-id="9952f-127">Process camera updates</span></span>

<span data-ttu-id="9952f-128">Задние буферы могут меняться от кадра к кадру.</span><span class="sxs-lookup"><span data-stu-id="9952f-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="9952f-129">Приложению необходимо проверить задний буфер для каждой камеры, а также освободить и повторно создать представления ресурсов и буферы глубины по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="9952f-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="9952f-130">Обратите внимание, что набор элементов прогноза является полномочным списком камер, используемых в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="9952f-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="9952f-131">Обычно этот список используется для итерации по набору камер.</span><span class="sxs-lookup"><span data-stu-id="9952f-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="9952f-132">Из **аппмаин:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-132">From **AppMain::Update** :</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="9952f-133">Из **DeviceResources:: енсурекамераресаурцес** :</span><span class="sxs-lookup"><span data-stu-id="9952f-133">From **DeviceResources::EnsureCameraResources** :</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="9952f-134">Получение системы координат для использования в качестве основания для подготовки к просмотру</span><span class="sxs-lookup"><span data-stu-id="9952f-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="9952f-135">Windows Mixed Reality позволяет вашему приложению создавать различные [системы координат](coordinate-systems-in-directx.md) по мере необходимости, например присоединенный фрейм ссылки и стационарный опорный фрейм, которые отслеживанием расположения в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="9952f-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="9952f-136">Приложение может использовать эти системы координат в качестве причины, по которой следует визуализировать голограммы каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="9952f-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="9952f-137">При запросе координат из API вы всегда будете передавать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a> , внутри которых должны выражаться эти координаты.</span><span class="sxs-lookup"><span data-stu-id="9952f-137">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="9952f-138">Из **аппмаин:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-138">From **AppMain::Update** :</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="9952f-139">Эти системы координат можно затем использовать для создания матрицы стерео View при отрисовке содержимого в сцене.</span><span class="sxs-lookup"><span data-stu-id="9952f-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="9952f-140">Из **камераресаурцес:: упдатевиевпрожектионбуффер** :</span><span class="sxs-lookup"><span data-stu-id="9952f-140">From **CameraResources::UpdateViewProjectionBuffer** :</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="9952f-141">Обработка взгляда и ввод с жестом</span><span class="sxs-lookup"><span data-stu-id="9952f-141">Process gaze and gesture input</span></span>

<span data-ttu-id="9952f-142">Ввод с помощью [взгляда](gaze-in-directx.md) и [руки](hands-and-motion-controllers-in-directx.md) не основан на времени, поэтому их не нужно обновлять в функции **стептимер** .</span><span class="sxs-lookup"><span data-stu-id="9952f-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="9952f-143">Однако эти входные данные — это то, что приложению нужно взглянуть на каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="9952f-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="9952f-144">Обработка обновлений на основе времени</span><span class="sxs-lookup"><span data-stu-id="9952f-144">Process time-based updates</span></span>

<span data-ttu-id="9952f-145">Любому приложению отрисовки в режиме реального времени потребуется какой-то способ обработки обновлений на основе времени; Мы предоставляем способ сделать это в шаблоне приложения Windows holographic с помощью реализации **стептимер** .</span><span class="sxs-lookup"><span data-stu-id="9952f-145">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="9952f-146">Это похоже на Стептимер, предоставляемый в шаблоне приложения UWP DirectX 11, поэтому, если вы уже рассматривали этот шаблон, вы должны быть знакомы со знакомым заземлением.</span><span class="sxs-lookup"><span data-stu-id="9952f-146">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="9952f-147">Этот пример вспомогательного класса Стептимер способен предоставлять фиксированные обновления времени, а также выполнять изменения в переменных времени, а режим по умолчанию — с переменным шагом.</span><span class="sxs-lookup"><span data-stu-id="9952f-147">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="9952f-148">В случае с holographic, мы выбрали не слишком много времени на функцию таймера.</span><span class="sxs-lookup"><span data-stu-id="9952f-148">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="9952f-149">Это связано с тем, что вы можете настроить его как фиксированный шаг времени. в этом случае он может вызываться более одного раза для каждого кадра, а не вообще — для некоторых кадров, а наши обновления данных — по одному на кадр.</span><span class="sxs-lookup"><span data-stu-id="9952f-149">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="9952f-150">Из **аппмаин:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-150">From **AppMain::Update** :</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="9952f-151">Размещение и поворот голограмм в системе координат</span><span class="sxs-lookup"><span data-stu-id="9952f-151">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="9952f-152">Если вы работаете в одной системе координат, так как шаблон работает с **спатиалстатионариреференцефраме** , этот процесс не отличается от того, что используется в трехмерной графике.</span><span class="sxs-lookup"><span data-stu-id="9952f-152">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame** , this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="9952f-153">Здесь мы вращающим куб и устанавливаем матрицу модели относительно положения в стационарной системе координат.</span><span class="sxs-lookup"><span data-stu-id="9952f-153">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="9952f-154">Из **спиннингкуберендерер:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-154">From **SpinningCubeRenderer::Update** :</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="9952f-155">**Примечание о расширенных сценариях:** Вращающийся куб — это очень простой пример того, как разместить голограмму в пределах одного опорного кадра.</span><span class="sxs-lookup"><span data-stu-id="9952f-155">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="9952f-156">Кроме того, можно одновременно [использовать несколько спатиалкурдинатесистемс](coordinate-systems-in-directx.md) в одном и том же подготовленном фрейме.</span><span class="sxs-lookup"><span data-stu-id="9952f-156">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="9952f-157">Обновление данных буфера констант</span><span class="sxs-lookup"><span data-stu-id="9952f-157">Update constant buffer data</span></span>

<span data-ttu-id="9952f-158">Преобразования модели для содержимого обновляются обычным образом.</span><span class="sxs-lookup"><span data-stu-id="9952f-158">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="9952f-159">К этому моменту вы получите вычисленные Допустимые преобразования для системы координат, в которой будет выполняться отрисовка.</span><span class="sxs-lookup"><span data-stu-id="9952f-159">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="9952f-160">Из **спиннингкуберендерер:: Update** :</span><span class="sxs-lookup"><span data-stu-id="9952f-160">From **SpinningCubeRenderer::Update** :</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="9952f-161">Как насчет преобразований представлений и проекций?</span><span class="sxs-lookup"><span data-stu-id="9952f-161">What about view and projection transforms?</span></span> <span data-ttu-id="9952f-162">Для достижения лучших результатов мы хотим подождать, пока мы почти готовы к вызовам Draw, прежде чем они будут получены.</span><span class="sxs-lookup"><span data-stu-id="9952f-162">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="9952f-163">Отобразить текущий кадр</span><span class="sxs-lookup"><span data-stu-id="9952f-163">Render the current frame</span></span>

<span data-ttu-id="9952f-164">Отрисовка в Windows Mixed Reality не намного отличается от отрисовки на 2D Mono, но есть некоторые различия, которые необходимо учитывать:</span><span class="sxs-lookup"><span data-stu-id="9952f-164">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="9952f-165">Важны прогнозы с Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-165">Holographic frame predictions are important.</span></span> <span data-ttu-id="9952f-166">Чем ближе прогноз к представлению вашей рамки, тем лучше будет выглядеть голограмма.</span><span class="sxs-lookup"><span data-stu-id="9952f-166">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="9952f-167">Windows Mixed Reality управляет представлениями камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-167">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="9952f-168">Необходимо выполнить рендеринг для каждого из них, так как в holographic кадр будет демонстрироваться позже.</span><span class="sxs-lookup"><span data-stu-id="9952f-168">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="9952f-169">Рекомендуется выполнить отрисовку стерео с помощью экземпляра Drawing в массиве целевых объектов прорисовки.</span><span class="sxs-lookup"><span data-stu-id="9952f-169">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="9952f-170">Шаблон holographic App использует Рекомендуемый подход экземпляра Drawing к целевому массиву прорисовки, который использует представление целевого объекта отрисовки в **Texture2DArray** .</span><span class="sxs-lookup"><span data-stu-id="9952f-170">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray** .</span></span>
* <span data-ttu-id="9952f-171">Если вы хотите подготовиться к просмотру без использования стереосистемы, необходимо создать два Рендертаржетвиевс, не являющихся массивами (один для каждого взгляда), каждый из которых ссылается на один из двух срезов в **Texture2DArray** , предоставленных приложению из системы.</span><span class="sxs-lookup"><span data-stu-id="9952f-171">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="9952f-172">Это не рекомендуется, так как обычно значительно медленнее, чем использование создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="9952f-172">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="9952f-173">Получение обновленного прогноза Холографикфраме</span><span class="sxs-lookup"><span data-stu-id="9952f-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="9952f-174">Обновление прогноза кадров повышает эффективность стабилизации изображений и обеспечивает более точное позиционирование голограмм из-за более короткого промежутка времени между прогнозом и отображением кадра для пользователя.</span><span class="sxs-lookup"><span data-stu-id="9952f-174">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="9952f-175">В идеале перед отрисовкой обновите прогнозирование кадров.</span><span class="sxs-lookup"><span data-stu-id="9952f-175">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="9952f-176">Подготовка к просмотру на каждой камере</span><span class="sxs-lookup"><span data-stu-id="9952f-176">Render to each camera</span></span>

<span data-ttu-id="9952f-177">Цикл по набору камер в прогнозе и отрисовка на каждой камере в этом наборе.</span><span class="sxs-lookup"><span data-stu-id="9952f-177">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="9952f-178">**Настройка этапа подготовки к просмотру**</span><span class="sxs-lookup"><span data-stu-id="9952f-178">**Set up your rendering pass**</span></span>

<span data-ttu-id="9952f-179">Windows Mixed Reality использует стереоскопикную визуализацию для улучшения иллюзии глубины и визуализации стереоскопикалли, поэтому активно и правое отображение активны.</span><span class="sxs-lookup"><span data-stu-id="9952f-179">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="9952f-180">При отрисовке стереоскопик между двумя дисплеями имеется смещение, которое мозг может согласовать как фактическую глубину.</span><span class="sxs-lookup"><span data-stu-id="9952f-180">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="9952f-181">В этом разделе описывается визуализация стереоскопик с помощью создания экземпляров с помощью кода из шаблона приложения Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-181">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="9952f-182">У каждой камеры есть собственный целевой буфер рендеринга (заднего буфера), а также матрицы просмотра и проекции в Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-182">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="9952f-183">Приложению потребуется создать любые другие ресурсы на основе камеры, такие как буфер глубины, для каждой камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-183">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="9952f-184">В шаблоне приложения Windows holographic мы предоставляем вспомогательный класс для объединения этих ресурсов в DX:: Камераресаурцес.</span><span class="sxs-lookup"><span data-stu-id="9952f-184">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="9952f-185">Начните с настройки представлений целевого объекта прорисовки:</span><span class="sxs-lookup"><span data-stu-id="9952f-185">Start by setting up the render target views:</span></span>

<span data-ttu-id="9952f-186">Из **аппмаин:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-186">From **AppMain::Render** :</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="9952f-187">**Использование прогноза для получения матриц представления и проекции для камеры**</span><span class="sxs-lookup"><span data-stu-id="9952f-187">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="9952f-188">Матрицы представления и проекции для каждой из этих камер Изменятся с каждым кадром.</span><span class="sxs-lookup"><span data-stu-id="9952f-188">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="9952f-189">Обновите данные в буфере констант для каждой камеры Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-189">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="9952f-190">Сделайте это после обновления прогноза и перед выполнением вызовов рисования для этой камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-190">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="9952f-191">Из **аппмаин:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-191">From **AppMain::Render** :</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="9952f-192">Здесь мы покажем, как можно получить матрицы от самой камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-192">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="9952f-193">В ходе этого процесса мы также получаем текущее окно просмотра для камеры.</span><span class="sxs-lookup"><span data-stu-id="9952f-193">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="9952f-194">Обратите внимание на то, как мы предоставляем систему координат: это та же система координат, которая использовалась для понимания взгляда, и это то же самое, что мы использовали для размещения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="9952f-194">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="9952f-195">Из **камераресаурцес:: упдатевиевпрожектионбуффер** :</span><span class="sxs-lookup"><span data-stu-id="9952f-195">From **CameraResources::UpdateViewProjectionBuffer** :</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="9952f-196">Окно просмотра должно быть задано для каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="9952f-196">The viewport should be set each frame.</span></span> <span data-ttu-id="9952f-197">Как правило, шейдеру вершин (по крайней мере) необходим доступ к данным представления или проекции.</span><span class="sxs-lookup"><span data-stu-id="9952f-197">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="9952f-198">Из **камераресаурцес:: аттачвиевпрожектионбуффер** :</span><span class="sxs-lookup"><span data-stu-id="9952f-198">From **CameraResources::AttachViewProjectionBuffer** :</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="9952f-199">**Подготавливается к просмотру в фоновом буфере камеры и зафиксируйте буфер глубины** :</span><span class="sxs-lookup"><span data-stu-id="9952f-199">**Render to the camera back buffer and commit the depth buffer** :</span></span>

<span data-ttu-id="9952f-200">Прежде чем пытаться использовать данные представления или проекции, рекомендуется проверить, что **трижетвиевтрансформ** успешно выполнен, так как если система координат не размещаемыеа (например, отслеживание было прервано), приложение не сможет визуализировать его для этого кадра.</span><span class="sxs-lookup"><span data-stu-id="9952f-200">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="9952f-201">Шаблон вызывает **визуализацию** только для вращающегося куба, если класс **камераресаурцес** указывает на успешное обновление.</span><span class="sxs-lookup"><span data-stu-id="9952f-201">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="9952f-202">Для сохранения голограмм, в которых разработчик или пользователь помещает их в мир, Windows Mixed Reality включает функции для [стабилизации изображений](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="9952f-202">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md).</span></span> <span data-ttu-id="9952f-203">Образ стабилизации помогает скрыть задержку, присущую конвейеру отрисовки, чтобы обеспечить наилучший опыт для пользователей. можно указать точку фокусировки, чтобы улучшить стабилизации изображений, или можно предоставить буфер глубины для стабилизации оптимизированного изображения в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="9952f-203">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="9952f-204">Для получения лучших результатов приложение должно предоставить буфер глубины с помощью API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="9952f-204">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="9952f-205">Затем Windows Mixed Reality может использовать сведения об геометрии из буфера глубины для оптимизации стабилизации изображений в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="9952f-205">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="9952f-206">Шаблон приложения Windows holographic по умолчанию фиксирует буфер глубины приложения, помогая оптимизировать стабильность.</span><span class="sxs-lookup"><span data-stu-id="9952f-206">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="9952f-207">Из **аппмаин:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-207">From **AppMain::Render** :</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="9952f-208">Windows обработает текстуру глубины на GPU, поэтому в качестве ресурса шейдера необходимо использовать буфер глубины.</span><span class="sxs-lookup"><span data-stu-id="9952f-208">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="9952f-209">Создаваемый ID3D11Texture2D должен быть в формате без типа, и его следует привязать как представление ресурсов шейдера.</span><span class="sxs-lookup"><span data-stu-id="9952f-209">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="9952f-210">Ниже приведен пример создания текстуры глубины, которую можно зафиксировать для изображения стабилизации.</span><span class="sxs-lookup"><span data-stu-id="9952f-210">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="9952f-211">Код для **создания ресурсов буфера глубины для CommitDirect3D11DepthBuffer** :</span><span class="sxs-lookup"><span data-stu-id="9952f-211">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer** :</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="9952f-212">**Нарисуйте holographic, содержимое**</span><span class="sxs-lookup"><span data-stu-id="9952f-212">**Draw holographic content**</span></span>

<span data-ttu-id="9952f-213">Шаблон приложения Windows holographic визуализирует содержимое на стереосистеме, используя рекомендуемый способ рисования экземпляра geometry в Texture2DArray размера 2.</span><span class="sxs-lookup"><span data-stu-id="9952f-213">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="9952f-214">Давайте рассмотрим эту часть и то, как она работает в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="9952f-214">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="9952f-215">Из **спиннингкуберендерер:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-215">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="9952f-216">Каждый экземпляр обращается к другой матрице представления или проекции из буфера констант.</span><span class="sxs-lookup"><span data-stu-id="9952f-216">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="9952f-217">Ниже приведена структура буфера констант, которая представляет собой просто массив из двух матриц.</span><span class="sxs-lookup"><span data-stu-id="9952f-217">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="9952f-218">Из **вертексшадершаред. HLSL** , входящего в **впртвертексшадер. HLSL** :</span><span class="sxs-lookup"><span data-stu-id="9952f-218">From **VertexShaderShared.hlsl** , included by **VPRTVertexShader.hlsl** :</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="9952f-219">Индекс целевого массива прорисовки должен быть задан для каждого пикселя.</span><span class="sxs-lookup"><span data-stu-id="9952f-219">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="9952f-220">В следующем фрагменте кода Output. viewId сопоставляется с семантикой **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="9952f-220">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="9952f-221">Обратите внимание, что для этого требуется поддержка необязательной функции Direct3D 11,3, которая позволяет задать семантику индекса целевого массива прорисовки на любом этапе шейдера.</span><span class="sxs-lookup"><span data-stu-id="9952f-221">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="9952f-222">Из **впртвертексшадер. HLSL** :</span><span class="sxs-lookup"><span data-stu-id="9952f-222">From **VPRTVertexShader.hlsl** :</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="9952f-223">Из **вертексшадершаред. HLSL** , входящего в **впртвертексшадер. HLSL** :</span><span class="sxs-lookup"><span data-stu-id="9952f-223">From **VertexShaderShared.hlsl** , included by **VPRTVertexShader.hlsl** :</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="9952f-224">Если вы хотите использовать существующие методы рисования экземпляров с помощью этого метода рисования в массиве нацеливания на стерео прорисовки, достаточно дважды нарисовать число экземпляров, которые у вас есть.</span><span class="sxs-lookup"><span data-stu-id="9952f-224">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="9952f-225">В шейдере разделите **input. куст Instid** на 2, чтобы получить идентификатор исходного экземпляра, который можно проиндексировать в (например,) буфер данных для каждого объекта: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="9952f-225">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="9952f-226">Важное примечание о визуализации стерео содержимого в HoloLens</span><span class="sxs-lookup"><span data-stu-id="9952f-226">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="9952f-227">Windows Mixed Reality поддерживает возможность установки индекса массива целевых объектов прорисовки с любого этапа шейдера. как правило, это задача, которая может быть выполнена только на этапе шейдера геометрии из-за способа определения семантики для Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="9952f-227">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="9952f-228">Здесь представлен полный пример настройки конвейера отрисовки с набором стадий вершин и шейдеров пикселей.</span><span class="sxs-lookup"><span data-stu-id="9952f-228">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="9952f-229">Код шейдера описан выше.</span><span class="sxs-lookup"><span data-stu-id="9952f-229">The shader code is as described above.</span></span>

<span data-ttu-id="9952f-230">Из **спиннингкуберендерер:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-230">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="9952f-231">Важное замечание о подготовке к просмотру на устройствах, не являющихся HoloLens</span><span class="sxs-lookup"><span data-stu-id="9952f-231">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="9952f-232">Для задания индекса массива целевых объектов прорисовки в шейдере вершин требуется, чтобы графический драйвер поддерживал дополнительную функцию Direct3D 11,3, которая поддерживает HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9952f-232">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="9952f-233">Приложение может безопасно реализовать только этот метод для подготовки к просмотру, и все требования будут выполнены для работы в Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9952f-233">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="9952f-234">Это может быть тот случай, когда вы хотите использовать эмулятор HoloLens, который может быть мощным средством разработки для holographic приложений, и поддерживать иммерсивное устройство в Windows Mixed Reality, подключенное к компьютерам под управлением Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9952f-234">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="9952f-235">Поддержка пути визуализации не в HoloLens, поэтому для всех Windows Mixed Reality также встроена в шаблон приложения Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-235">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="9952f-236">В коде шаблона вы найдете код, позволяющий запускать приложение holographic на GPU на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="9952f-236">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="9952f-237">Ниже показано, как класс **DeviceResources** проверяет наличие этой дополнительной поддержки компонентов.</span><span class="sxs-lookup"><span data-stu-id="9952f-237">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="9952f-238">Из **DeviceResources:: креатедевицересаурцес** :</span><span class="sxs-lookup"><span data-stu-id="9952f-238">From **DeviceResources::CreateDeviceResources** :</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="9952f-239">Для поддержки отрисовки без этой дополнительной функции приложение должно использовать шейдер Geometry для задания индекса целевого массива прорисовки.</span><span class="sxs-lookup"><span data-stu-id="9952f-239">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="9952f-240">Этот фрагмент кода будет добавлен *после* **вссетконстантбуфферс** и *перед* **PSSetShader** в примере, приведенном в предыдущем разделе, в котором объясняется, как визуализировать стерео в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9952f-240">This snippet would be added *after* **VSSetConstantBuffers** , and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="9952f-241">Из **спиннингкуберендерер:: Render** :</span><span class="sxs-lookup"><span data-stu-id="9952f-241">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="9952f-242">**HLSL Примечание** . в этом случае необходимо также загрузить немного измененный шейдер вершин, передающий индекс массива целевых объектов отрисовки шейдеру Geometry с помощью семантики шейдера, которая всегда разрешена, например TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="9952f-242">**HLSL NOTE** : In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="9952f-243">Шейдер геометрии не должен выполнять никаких действий. Шейдер геометрии шаблона проходит через все данные, за исключением индекса целевого массива прорисовки, который используется для задания семантической SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="9952f-243">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="9952f-244">Код шаблона приложения для **жеометришадер. HLSL** :</span><span class="sxs-lookup"><span data-stu-id="9952f-244">App template code for **GeometryShader.hlsl** :</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="9952f-245">Присутствует</span><span class="sxs-lookup"><span data-stu-id="9952f-245">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="9952f-246">Включение в holographic фрейма цепочки буферов</span><span class="sxs-lookup"><span data-stu-id="9952f-246">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="9952f-247">В Windows Mixed Reality система управляет цепочкой буферов обмена.</span><span class="sxs-lookup"><span data-stu-id="9952f-247">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="9952f-248">Затем система управляет показом кадров на каждой из holographic камер для обеспечения высокого качества взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="9952f-248">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="9952f-249">Он также предоставляет окно просмотра, которое обновляет каждый кадр для каждой камеры для оптимизации аспектов системы, таких как изображение стабилизации или запись смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9952f-249">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="9952f-250">Таким образом, holographic приложение, использующее DirectX, не вызывает **Present** в цепочке подкачки DXGI.</span><span class="sxs-lookup"><span data-stu-id="9952f-250">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="9952f-251">Вместо этого используйте класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> , чтобы показать все цепочек переключений для кадра после завершения его рисования.</span><span class="sxs-lookup"><span data-stu-id="9952f-251">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="9952f-252">Из **DeviceResources::P** повторной отправки:</span><span class="sxs-lookup"><span data-stu-id="9952f-252">From **DeviceResources::Present** :</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="9952f-253">По умолчанию этот API ожидает завершения кадра перед возвратом.</span><span class="sxs-lookup"><span data-stu-id="9952f-253">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="9952f-254">Перед началом работы над новым кадром holographic приложения должны ожидать завершения предыдущего кадра, так как это сокращает задержку и обеспечивает лучшие результаты прогнозов с помощью Holographic.</span><span class="sxs-lookup"><span data-stu-id="9952f-254">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="9952f-255">Это не жесткое правило, и если у вас есть кадры, которые занимают больше одного экрана для подготовки к просмотру, можно отключить это время, передав параметр Холографикфрамепресентваитбехавиор в <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">пресентусингкуррентпредиктион</a>.</span><span class="sxs-lookup"><span data-stu-id="9952f-255">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="9952f-256">В этом случае, скорее всего, будет использоваться поток асинхронной отрисовки для поддержания непрерывной нагрузки на GPU.</span><span class="sxs-lookup"><span data-stu-id="9952f-256">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="9952f-257">Обратите внимание, что частота обновления устройства HoloLens составляет 60 Гц, при этом размер одного кадра составляет примерно 16 мс.</span><span class="sxs-lookup"><span data-stu-id="9952f-257">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="9952f-258">Для иммерсивного устройства гарнитуры могут варьироваться от 60 Гц до 90hz; При обновлении экрана с частотой 90 Гц каждый кадр будет иметь длительность примерно 11 мс.</span><span class="sxs-lookup"><span data-stu-id="9952f-258">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="9952f-259">Обрабатывайте сценарии Девицелост в сотрудничество с Холографикфраме</span><span class="sxs-lookup"><span data-stu-id="9952f-259">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="9952f-260">Приложениям DirectX 11 обычно требуется проверить значение HRESULT, возвращаемое функцией **Present** цепочки ПОДкачки DXGI, чтобы определить, была ли ошибка **девицелост** .</span><span class="sxs-lookup"><span data-stu-id="9952f-260">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="9952f-261">Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> обрабатывает это за вас.</span><span class="sxs-lookup"><span data-stu-id="9952f-261">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="9952f-262">Изучите <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">холографикфрамепресентресулт</a> , которые он возвращает, чтобы узнать, нужно ли освободить и повторно создать ресурсы на основе Direct3D и устройств.</span><span class="sxs-lookup"><span data-stu-id="9952f-262">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="9952f-263">Обратите внимание, что если устройство Direct3D было потеряно и вы создали его повторно, вам нужно сообщить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> начать использовать новое устройство.</span><span class="sxs-lookup"><span data-stu-id="9952f-263">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="9952f-264">Для этого устройства будет создана цепочка буферов.</span><span class="sxs-lookup"><span data-stu-id="9952f-264">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="9952f-265">Из **DeviceResources:: инитиализеусингхолографикспаце** :</span><span class="sxs-lookup"><span data-stu-id="9952f-265">From **DeviceResources::InitializeUsingHolographicSpace** :</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="9952f-266">После представления кадра можно вернуться к главному циклу программы и разрешить переход к следующему кадру.</span><span class="sxs-lookup"><span data-stu-id="9952f-266">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="9952f-267">Гибридные графические компьютеры и приложения смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="9952f-267">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="9952f-268">В Windows 10 Creators Update PCS можно настроить **как** дискретные, так и интегрированные GPU.</span><span class="sxs-lookup"><span data-stu-id="9952f-268">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="9952f-269">С этими типами компьютеров Windows выберет адаптер, к которому подключена гарнитура.</span><span class="sxs-lookup"><span data-stu-id="9952f-269">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="9952f-270">Приложения должны гарантировать, что создаваемое устройство DirectX использует тот же адаптер.</span><span class="sxs-lookup"><span data-stu-id="9952f-270">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="9952f-271">В большинстве общих примеров кода Direct3D демонстрируется создание устройства DirectX с помощью аппаратного адаптера по умолчанию, который в гибридной системе может отличаться от используемого для гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="9952f-271">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="9952f-272">Чтобы обойти все проблемы, которые могут возникнуть, используйте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">холографикадаптерид</a> из <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a>. Примарядаптерид () или <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">холографикдисплай</a>. ИД адаптера ().</span><span class="sxs-lookup"><span data-stu-id="9952f-272">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="9952f-273">Этот ИД адаптера можно затем использовать для выбора правильного Дксгиадаптер с помощью IDXGIFactory4. Енумадаптербилуид.</span><span class="sxs-lookup"><span data-stu-id="9952f-273">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="9952f-274">Из **DeviceResources:: инитиализеусингхолографикспаце** :</span><span class="sxs-lookup"><span data-stu-id="9952f-274">From **DeviceResources::InitializeUsingHolographicSpace** :</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="9952f-275">Код для **обновления DeviceResources:: креатедевицересаурцес для использования идксгиадаптер**</span><span class="sxs-lookup"><span data-stu-id="9952f-275">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="9952f-276">**Гибридная графика и Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="9952f-276">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="9952f-277">Использование Media Foundation в гибридных системах может вызвать проблемы, когда видео не будет отображаться или текстура видео повреждена.</span><span class="sxs-lookup"><span data-stu-id="9952f-277">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="9952f-278">Это может произойти из-за того, что Media Foundation по умолчанию используется поведение системы, как упоминалось выше.</span><span class="sxs-lookup"><span data-stu-id="9952f-278">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="9952f-279">В некоторых сценариях для поддержки многопоточности и установки правильных флагов создания требуется создать отдельный ID3D11Device.</span><span class="sxs-lookup"><span data-stu-id="9952f-279">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="9952f-280">При инициализации ID3D11Device должен быть определен флаг D3D11_CREATE_DEVICE_VIDEO_SUPPORT в составе D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="9952f-280">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="9952f-281">После создания устройства и контекста вызовите <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">сетмултисреадпротектед</a> , чтобы включить многопоточность.</span><span class="sxs-lookup"><span data-stu-id="9952f-281">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="9952f-282">Чтобы связать устройство с <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">имфдксгидевицеманажер</a>, используйте функцию <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">Имфдксгидевицеманажер:: ресетдевице</a> .</span><span class="sxs-lookup"><span data-stu-id="9952f-282">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="9952f-283">Код для **связывания ID3D11Device с имфдксгидевицеманажер** :</span><span class="sxs-lookup"><span data-stu-id="9952f-283">Code to **associate a ID3D11Device with IMFDXGIDeviceManager** :</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="9952f-284">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9952f-284">See also</span></span>
* [<span data-ttu-id="9952f-285">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="9952f-285">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="9952f-286">Использование эмулятора HoloLens</span><span class="sxs-lookup"><span data-stu-id="9952f-286">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)