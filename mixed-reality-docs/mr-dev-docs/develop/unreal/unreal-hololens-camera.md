---
title: Фото- и видеокамера HoloLens в Unreal
description: Руководство по работе с фото- и видеокамерой HoloLens в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера, PV-камера, MRC
ms.openlocfilehash: e66583d46d64361621303e36a5fbcc209300f5d8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699269"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="72a24-104">Фото- и видеокамера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="72a24-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="72a24-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="72a24-105">Overview</span></span>

<span data-ttu-id="72a24-106">Устройство HoloLens оснащено фото- и видеокамерой, которая используется для съемки смешанной реальности (MRC) и может также использоваться приложением для доступа к визуальным элементам реального мира.</span><span class="sxs-lookup"><span data-stu-id="72a24-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="72a24-107">Отрисовка с фото- и видеокамеры для MRC</span><span class="sxs-lookup"><span data-stu-id="72a24-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="72a24-108">Для этого требуется **Unreal Engine версии 4.25** и выше.</span><span class="sxs-lookup"><span data-stu-id="72a24-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="72a24-109">Системные и пользовательские средства MRC производят съемку смешанной реальности, совмещая изображение с фото- и видеокамеры и голограммы, которые отрисовываются иммерсивным приложением.</span><span class="sxs-lookup"><span data-stu-id="72a24-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="72a24-110">По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза.</span><span class="sxs-lookup"><span data-stu-id="72a24-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="72a24-111">В иммерсивном приложении можно вместо этого выбрать [отрисовку с фото- и видеокамеры](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in).</span><span class="sxs-lookup"><span data-stu-id="72a24-111">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="72a24-112">Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC.</span><span class="sxs-lookup"><span data-stu-id="72a24-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="72a24-113">Чтобы включить отрисовку с фото- и видеокамеры (по умолчанию она выключена):</span><span class="sxs-lookup"><span data-stu-id="72a24-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="72a24-114">Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera** .</span><span class="sxs-lookup"><span data-stu-id="72a24-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="72a24-115">Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).</span><span class="sxs-lookup"><span data-stu-id="72a24-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Третья камера](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="72a24-117">После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.</span><span class="sxs-lookup"><span data-stu-id="72a24-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="72a24-118">Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](../../mixed-reality-capture.md).</span><span class="sxs-lookup"><span data-stu-id="72a24-118">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="72a24-119">Использование фото- и видеокамеры</span><span class="sxs-lookup"><span data-stu-id="72a24-119">Using the PV Camera</span></span>

<span data-ttu-id="72a24-120">Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:</span><span class="sxs-lookup"><span data-stu-id="72a24-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings** :</span></span>
1. <span data-ttu-id="72a24-121">Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="72a24-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam** .</span></span>
    * <span data-ttu-id="72a24-122">Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture** , а чтобы остановить запись, вызовите функцию **StopCameraCapture** .</span><span class="sxs-lookup"><span data-stu-id="72a24-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="72a24-124">Отрисовка изображения</span><span class="sxs-lookup"><span data-stu-id="72a24-124">Rendering an image</span></span>
<span data-ttu-id="72a24-125">Для отрисовки изображения с камеры:</span><span class="sxs-lookup"><span data-stu-id="72a24-125">To render the camera image:</span></span>
1. <span data-ttu-id="72a24-126">Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="72a24-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="72a24-127">Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="72a24-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="72a24-128">Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="72a24-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="72a24-129">Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.</span><span class="sxs-lookup"><span data-stu-id="72a24-129">Start a timer that will be used to bind the camera image to the material.</span></span>

![Отрисовка камеры](images/unreal-camera-render.PNG)

4. <span data-ttu-id="72a24-131">Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer** ) и вызовите функцию **GetARCameraImage** , чтобы получить текстуру с веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="72a24-131">Create a new function for this timer, in this case **MaterialTimer** , and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="72a24-132">Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="72a24-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="72a24-133">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="72a24-133">Otherwise, start the material timer again.</span></span>

![Текстура камеры с веб-камеры](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="72a24-135">У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue** , привязанное к записи о цвете.</span><span class="sxs-lookup"><span data-stu-id="72a24-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="72a24-136">Без этого изображение с камеры не может быть правильно отображено.</span><span class="sxs-lookup"><span data-stu-id="72a24-136">Without this, the camera image can't be properly displayed.</span></span>

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="72a24-138">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="72a24-138">Next Development Checkpoint</span></span>

<span data-ttu-id="72a24-139">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="72a24-139">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="72a24-140">Отсюда вы можете перейти к следующей теме:</span><span class="sxs-lookup"><span data-stu-id="72a24-140">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72a24-141">QR-коды</span><span class="sxs-lookup"><span data-stu-id="72a24-141">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="72a24-142">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="72a24-142">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72a24-143">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="72a24-143">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="72a24-144">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="72a24-144">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="72a24-145">См. также статью</span><span class="sxs-lookup"><span data-stu-id="72a24-145">See also</span></span>
* [<span data-ttu-id="72a24-146">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="72a24-146">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="72a24-147">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="72a24-147">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
