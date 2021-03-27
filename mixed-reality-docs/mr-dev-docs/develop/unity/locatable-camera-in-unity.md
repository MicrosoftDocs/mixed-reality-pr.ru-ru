---
title: Фото видеокамера в Unity
description: Узнайте, как записать фотографию в файл или Texture2D, как записать фотографию и взаимодействовать с необработанными байтами, а также как записать видео.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: Фото, видео, hololens, Камера, Unity, размещаемые, PVC, видеокамера, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, веб-камера, запись фотографий, видеозапись
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636216"
---
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="77be7-104">Фото видеокамера в Unity</span><span class="sxs-lookup"><span data-stu-id="77be7-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="77be7-105">Включение возможности доступа к камере</span><span class="sxs-lookup"><span data-stu-id="77be7-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="77be7-106">Для использования [камеры](../platform-capabilities-and-apis/locatable-camera.md)приложение должно быть объявлено как "веб-камера".</span><span class="sxs-lookup"><span data-stu-id="77be7-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="77be7-107">В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "изменение > параметров проекта > Player".</span><span class="sxs-lookup"><span data-stu-id="77be7-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="77be7-108">Выберите вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="77be7-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="77be7-109">В разделе "Параметры публикации > возможности" Проверьте возможности веб- **камеры** и **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="77be7-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="77be7-110">Только одна операция может выполняться с камерой за раз.</span><span class="sxs-lookup"><span data-stu-id="77be7-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="77be7-111">В `UnityEngine.XR.WSA.WebCam.Mode` unity 2018 и более ранних версиях или `UnityEngine.Windows.WebCam.Mode` в Unity 2019 и более поздних версиях можно проверить, в каком режиме в настоящее время находится камера.</span><span class="sxs-lookup"><span data-stu-id="77be7-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="77be7-112">Доступные режимы: Фото, видео или нет.</span><span class="sxs-lookup"><span data-stu-id="77be7-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="77be7-113">Запись фотографий</span><span class="sxs-lookup"><span data-stu-id="77be7-113">Photo capture</span></span>

<span data-ttu-id="77be7-114">**Пространство имен (перед Unity 2019):** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="77be7-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="77be7-115">**Пространство имен (Unity 2019 и более поздние версии):** *UnityEngine. Windows. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="77be7-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="77be7-116">**Тип:** *фотозапись*</span><span class="sxs-lookup"><span data-stu-id="77be7-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="77be7-117">Тип *фотосъемки* позволяет вам по-прежнему иметь фотографии фотокамеры.</span><span class="sxs-lookup"><span data-stu-id="77be7-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="77be7-118">Общий шаблон использования *фотосъемки* для получения фотографий выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="77be7-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="77be7-119">Создание объекта *Фотозаписи*</span><span class="sxs-lookup"><span data-stu-id="77be7-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="77be7-120">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="77be7-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="77be7-121">Запуск фоторежима через *стартфотомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="77be7-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="77be7-122">Сделайте нужную фотографию</span><span class="sxs-lookup"><span data-stu-id="77be7-122">Take the photo you want</span></span>
    * <span data-ttu-id="77be7-123">используемых Взаимодействие с этим изображением</span><span class="sxs-lookup"><span data-stu-id="77be7-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="77be7-124">Отключение режима фото и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="77be7-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="77be7-125">Общая Настройка для фотозаписи</span><span class="sxs-lookup"><span data-stu-id="77be7-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="77be7-126">Для всех трех вариантов использования Начните с тех же первых трех описанных выше действий.</span><span class="sxs-lookup"><span data-stu-id="77be7-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="77be7-127">Начните с создания объекта *фотосъемки*</span><span class="sxs-lookup"><span data-stu-id="77be7-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="77be7-128">Затем сохраните объект, задайте параметры и запустите режим фото.</span><span class="sxs-lookup"><span data-stu-id="77be7-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

<span data-ttu-id="77be7-129">В итоге вы также будете использовать тот же код очистки, представленный здесь.</span><span class="sxs-lookup"><span data-stu-id="77be7-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="77be7-130">После выполнения этих действий можно выбрать тип фотографии для записи.</span><span class="sxs-lookup"><span data-stu-id="77be7-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="77be7-131">Фотозахват в файл</span><span class="sxs-lookup"><span data-stu-id="77be7-131">Capture a photo to a file</span></span>

<span data-ttu-id="77be7-132">Самой простой операцией является запись фотографии непосредственно в файл.</span><span class="sxs-lookup"><span data-stu-id="77be7-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="77be7-133">Фотографию можно сохранить в формате JPG или PNG.</span><span class="sxs-lookup"><span data-stu-id="77be7-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="77be7-134">Если вы успешно начали фото-режим, возьмите фотографию и сохраните ее на диске.</span><span class="sxs-lookup"><span data-stu-id="77be7-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="77be7-135">После записи фотографии на диск выйдите из режима Photo, а затем очистите объекты</span><span class="sxs-lookup"><span data-stu-id="77be7-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="77be7-136">Запись фотографии в Texture2D с расположением</span><span class="sxs-lookup"><span data-stu-id="77be7-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="77be7-137">При записи данных в Texture2D процесс аналогичен записи на диск.</span><span class="sxs-lookup"><span data-stu-id="77be7-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="77be7-138">Выполните описанный выше процесс установки.</span><span class="sxs-lookup"><span data-stu-id="77be7-138">Follow the setup process above.</span></span>

<span data-ttu-id="77be7-139">В *онфотомодестартед* запишите кадр в память.</span><span class="sxs-lookup"><span data-stu-id="77be7-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="77be7-140">Затем вы примените результат к текстуре и используйте общий приведенный выше код очистки.</span><span class="sxs-lookup"><span data-stu-id="77be7-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a><span data-ttu-id="77be7-141">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="77be7-141">Locatable camera</span></span>

<span data-ttu-id="77be7-142">Чтобы поместить эту текстуру в сцену и отобразить ее с помощью матриц размещаемые Camera, добавьте следующий код в *онкаптуредфототомемори* в `result.success` проверке:</span><span class="sxs-lookup"><span data-stu-id="77be7-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="77be7-143">В [Unity предоставлен пример кода](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) для применения матрицы проекции к конкретному шейдеру на форумах.</span><span class="sxs-lookup"><span data-stu-id="77be7-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="77be7-144">Запись фотографии и взаимодействие с необработанными байтами</span><span class="sxs-lookup"><span data-stu-id="77be7-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="77be7-145">Чтобы взаимодействовать с необработанными байтами в кадре памяти, выполните те же действия по настройке, что и в предыдущем разделе, и *онфотомодестартед* , как при записи фотографии в Texture2D.</span><span class="sxs-lookup"><span data-stu-id="77be7-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="77be7-146">Разница заключается в *онкаптуредфототомемори* , где можно получить необработанные байты и взаимодействовать с ними.</span><span class="sxs-lookup"><span data-stu-id="77be7-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="77be7-147">В этом примере вы создадите *список <Color>* , который будет обрабатываться или применен к текстуре с помощью *сетпикселс ()* .</span><span class="sxs-lookup"><span data-stu-id="77be7-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a><span data-ttu-id="77be7-148">Видеозахват</span><span class="sxs-lookup"><span data-stu-id="77be7-148">Video capture</span></span>

<span data-ttu-id="77be7-149">**Пространство имен (перед Unity 2019):** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="77be7-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="77be7-150">**Пространство имен (Unity 2019 и более поздние версии):** *UnityEngine. Windows. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="77be7-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="77be7-151">**Тип:** *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="77be7-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="77be7-152">Функции *видеокаптуре* аналогичны функциям *фотозахвата*.</span><span class="sxs-lookup"><span data-stu-id="77be7-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="77be7-153">Единственное отличие заключается в том, что необходимо указать значение кадров в секунду, которое можно сохранить непосредственно на диск в виде MP4-файла.</span><span class="sxs-lookup"><span data-stu-id="77be7-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="77be7-154">Ниже приведены действия по использованию *видеокаптуре* .</span><span class="sxs-lookup"><span data-stu-id="77be7-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="77be7-155">Создание объекта *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="77be7-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="77be7-156">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="77be7-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="77be7-157">Запуск видеорежима через *стартвидеомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="77be7-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="77be7-158">Начать запись видео</span><span class="sxs-lookup"><span data-stu-id="77be7-158">Start recording video</span></span>
5. <span data-ttu-id="77be7-159">Закончить запись видео</span><span class="sxs-lookup"><span data-stu-id="77be7-159">Stop recording video</span></span>
6. <span data-ttu-id="77be7-160">Воспроизведение видеорежима и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="77be7-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="77be7-161">Начните с создания нашего  объекта видеокаптуре *видеокаптуре m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="77be7-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="77be7-162">Затем настройте параметры для записи и запуска.</span><span class="sxs-lookup"><span data-stu-id="77be7-162">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

<span data-ttu-id="77be7-163">После запуска Запустите запись.</span><span class="sxs-lookup"><span data-stu-id="77be7-163">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

<span data-ttu-id="77be7-164">После начала записи можно обновить пользовательский интерфейс или поведение, чтобы включить остановку.</span><span class="sxs-lookup"><span data-stu-id="77be7-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="77be7-165">Здесь вы только зарегистрируетесь.</span><span class="sxs-lookup"><span data-stu-id="77be7-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="77be7-166">На более позднем этапе вы захотите отключить запись с помощью таймера или ввода пользователя, например.</span><span class="sxs-lookup"><span data-stu-id="77be7-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="77be7-167">После остановки записи остановите видеорежим и очистите ресурсы.</span><span class="sxs-lookup"><span data-stu-id="77be7-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a><span data-ttu-id="77be7-168">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="77be7-168">Troubleshooting</span></span>

* <span data-ttu-id="77be7-169">Нет доступных разрешений</span><span class="sxs-lookup"><span data-stu-id="77be7-169">No resolutions are available</span></span>
  * <span data-ttu-id="77be7-170">Убедитесь, что в проекте указана возможность использования **веб-камеры** .</span><span class="sxs-lookup"><span data-stu-id="77be7-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="77be7-171">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="77be7-171">Next Development Checkpoint</span></span>

<span data-ttu-id="77be7-172">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="77be7-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="77be7-173">Вы можете перейти к следующей статье:</span><span class="sxs-lookup"><span data-stu-id="77be7-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="77be7-174">[точка фокусировки](focus-point-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="77be7-174">[Focus point](focus-point-in-unity.md)</span></span>

<span data-ttu-id="77be7-175">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="77be7-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77be7-176">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="77be7-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="77be7-177">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-advanced-features).</span><span class="sxs-lookup"><span data-stu-id="77be7-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="77be7-178">См. также:</span><span class="sxs-lookup"><span data-stu-id="77be7-178">See Also</span></span>

* [<span data-ttu-id="77be7-179">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="77be7-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)