---
title: Фото- и видеокамера HoloLens в Unreal
description: Руководство по работе с фото- и видеокамерой HoloLens в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, камера, фото-/видеокамера, MRC, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 975853a7b39c4d8790adb1f48160d7e4fdf6c19a
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679043"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="9850f-104">Фото- и видеокамера HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="9850f-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="9850f-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="9850f-105">Overview</span></span>

<span data-ttu-id="9850f-106">Устройство HoloLens оснащено фото- и видеокамерой, которая используется для съемки смешанной реальности (MRC) и может также использоваться приложением для доступа к визуальным элементам реального мира.</span><span class="sxs-lookup"><span data-stu-id="9850f-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9850f-107">Фото-/видеокамера не поддерживается в голографическом удаленном взаимодействии, но вы можете использовать веб-камеру, подключенную к компьютеру, для имитации функциональности фото-/видеокамеры в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9850f-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="9850f-108">Отрисовка с фото- и видеокамеры для MRC</span><span class="sxs-lookup"><span data-stu-id="9850f-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="9850f-109">Для этого требуется **Unreal Engine версии 4.25** и выше.</span><span class="sxs-lookup"><span data-stu-id="9850f-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="9850f-110">Системные и пользовательские средства MRC производят съемку смешанной реальности, совмещая изображение с фото- и видеокамеры и голограммы, которые отрисовываются иммерсивным приложением.</span><span class="sxs-lookup"><span data-stu-id="9850f-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="9850f-111">По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза.</span><span class="sxs-lookup"><span data-stu-id="9850f-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="9850f-112">В иммерсивном приложении можно вместо этого выбрать [отрисовку с фото- и видеокамеры](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in).</span><span class="sxs-lookup"><span data-stu-id="9850f-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="9850f-113">Это улучшает соответствие между реальным миром и голограммами в видеороликах MRC.</span><span class="sxs-lookup"><span data-stu-id="9850f-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="9850f-114">Чтобы включить отрисовку с фото- и видеокамеры (по умолчанию она выключена):</span><span class="sxs-lookup"><span data-stu-id="9850f-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="9850f-115">Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="9850f-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="9850f-116">Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).</span><span class="sxs-lookup"><span data-stu-id="9850f-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Третья камера](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="9850f-118">После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.</span><span class="sxs-lookup"><span data-stu-id="9850f-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="9850f-119">Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](../../mixed-reality-capture.md).</span><span class="sxs-lookup"><span data-stu-id="9850f-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="9850f-120">Использование фото- и видеокамеры</span><span class="sxs-lookup"><span data-stu-id="9850f-120">Using the PV Camera</span></span>

<span data-ttu-id="9850f-121">Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:</span><span class="sxs-lookup"><span data-stu-id="9850f-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="9850f-122">Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="9850f-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="9850f-123">Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture**, а чтобы остановить запись, вызовите функцию **StopCameraCapture**.</span><span class="sxs-lookup"><span data-stu-id="9850f-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Запуск и остановка камеры](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="9850f-125">Отрисовка изображения</span><span class="sxs-lookup"><span data-stu-id="9850f-125">Rendering an image</span></span>
<span data-ttu-id="9850f-126">Для отрисовки изображения с камеры:</span><span class="sxs-lookup"><span data-stu-id="9850f-126">To render the camera image:</span></span>
1. <span data-ttu-id="9850f-127">Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="9850f-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="9850f-128">Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="9850f-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="9850f-129">Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="9850f-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="9850f-130">Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.</span><span class="sxs-lookup"><span data-stu-id="9850f-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![Отрисовка камеры](images/unreal-camera-render.PNG)

4. <span data-ttu-id="9850f-132">Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer**) и вызовите функцию **GetARCameraImage**, чтобы получить текстуру с веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="9850f-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="9850f-133">Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="9850f-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="9850f-134">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="9850f-134">Otherwise, start the material timer again.</span></span>

![Текстура камеры с веб-камеры](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="9850f-136">У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue**, привязанное к записи о цвете.</span><span class="sxs-lookup"><span data-stu-id="9850f-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="9850f-137">Без этого изображение с камеры не может быть правильно отображено.</span><span class="sxs-lookup"><span data-stu-id="9850f-137">Without this, the camera image can't be properly displayed.</span></span>

![Текстура от камеры](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="9850f-139">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="9850f-139">Next Development Checkpoint</span></span>

<span data-ttu-id="9850f-140">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="9850f-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="9850f-141">Отсюда вы можете перейти к следующей теме:</span><span class="sxs-lookup"><span data-stu-id="9850f-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9850f-142">QR-коды</span><span class="sxs-lookup"><span data-stu-id="9850f-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="9850f-143">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="9850f-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9850f-144">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="9850f-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="9850f-145">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="9850f-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9850f-146">См. также статью</span><span class="sxs-lookup"><span data-stu-id="9850f-146">See also</span></span>
* [<span data-ttu-id="9850f-147">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="9850f-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="9850f-148">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="9850f-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
