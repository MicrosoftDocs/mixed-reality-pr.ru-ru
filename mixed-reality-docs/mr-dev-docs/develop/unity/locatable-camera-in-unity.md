---
title: Камера с определяемым местоположением в Unity
description: Узнайте, как записать фотографию в файл или Texture2D, как записать фотографию и взаимодействовать с необработанными байтами, а также как записать видео.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Фото, видео, hololens, Камера, Unity, размещаемые, PVC, видеокамера, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, веб-камера, запись фотографий, видеозапись
ms.openlocfilehash: 8916b332774185e4453b514ca7b6916947bdcd81
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226423"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="9f8a8-104">Камера с определяемым местоположением в Unity</span><span class="sxs-lookup"><span data-stu-id="9f8a8-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="9f8a8-105">Включение возможности для видеокамеры</span><span class="sxs-lookup"><span data-stu-id="9f8a8-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="9f8a8-106">Для использования [камеры](../platform-capabilities-and-apis/locatable-camera.md)приложение должно быть объявлено как "веб-камера".</span><span class="sxs-lookup"><span data-stu-id="9f8a8-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="9f8a8-107">В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "изменение > параметров проекта > Player".</span><span class="sxs-lookup"><span data-stu-id="9f8a8-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="9f8a8-108">Выберите вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="9f8a8-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="9f8a8-109">В разделе "Параметры публикации > возможности" Проверьте возможности веб- **камеры** и **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="9f8a8-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="9f8a8-110">Только одна операция может выполняться с камерой за раз.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="9f8a8-111">Вы можете проверить режим с помощью камеры в настоящее время с помощью UnityEngine. XR. WSA. Camera. Mode.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-111">You can check with mode the camera is currently in with UnityEngine.XR.WSA.WebCam.Mode.</span></span> <span data-ttu-id="9f8a8-112">Доступные режимы: Фото, видео или нет.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="9f8a8-113">Запись фотографий</span><span class="sxs-lookup"><span data-stu-id="9f8a8-113">Photo Capture</span></span>

<span data-ttu-id="9f8a8-114">**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-114">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="9f8a8-115">**Тип:** *фотозапись*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-115">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="9f8a8-116">Тип *фотосъемки* позволяет вам по-прежнему иметь фотографии фотокамеры.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-116">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="9f8a8-117">Общий шаблон использования *фотосъемки* для получения фотографий выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9f8a8-117">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="9f8a8-118">Создание объекта *Фотозаписи*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-118">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="9f8a8-119">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="9f8a8-119">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="9f8a8-120">Запуск фоторежима через *стартфотомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-120">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="9f8a8-121">Сделайте нужную фотографию</span><span class="sxs-lookup"><span data-stu-id="9f8a8-121">Take the photo you want</span></span>
    * <span data-ttu-id="9f8a8-122">используемых Взаимодействие с этим изображением</span><span class="sxs-lookup"><span data-stu-id="9f8a8-122">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="9f8a8-123">Отключение режима фото и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="9f8a8-123">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="9f8a8-124">Стандартная настройка для фотозахвата</span><span class="sxs-lookup"><span data-stu-id="9f8a8-124">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="9f8a8-125">Для всех трех вариантов использования Начните с тех же первых трех описанных выше действий.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-125">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="9f8a8-126">Начните с создания объекта *фотосъемки*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-126">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="9f8a8-127">Затем сохраните объект, задайте параметры и запустите режим фото.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-127">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
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

<span data-ttu-id="9f8a8-128">В итоге вы также будете использовать тот же код очистки, представленный здесь.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-128">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="9f8a8-129">После выполнения этих действий можно выбрать тип фотографии для записи.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-129">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="9f8a8-130">Запись фотографии в файл</span><span class="sxs-lookup"><span data-stu-id="9f8a8-130">Capture a Photo to a File</span></span>

<span data-ttu-id="9f8a8-131">Самой простой операцией является запись фотографии непосредственно в файл.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-131">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="9f8a8-132">Фотографию можно сохранить в формате JPG или PNG.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-132">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="9f8a8-133">Если вы успешно начали фото-режим, возьмите фотографию и сохраните ее на диске.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-133">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="9f8a8-134">После записи фотографии на диск выйдите из режима Photo, а затем очистите объекты</span><span class="sxs-lookup"><span data-stu-id="9f8a8-134">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="9f8a8-135">Запись фотографии в Texture2D</span><span class="sxs-lookup"><span data-stu-id="9f8a8-135">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="9f8a8-136">При записи данных в Texture2D процесс аналогичен записи на диск.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-136">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="9f8a8-137">Выполните описанный выше процесс установки.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-137">Follow the setup process above.</span></span>

<span data-ttu-id="9f8a8-138">В *онфотомодестартед* запишите кадр в память.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-138">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="9f8a8-139">Затем вы примените результат к текстуре и используйте общий приведенный выше код очистки.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-139">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="9f8a8-140">Запись фотографии и взаимодействие с необработанными байтами</span><span class="sxs-lookup"><span data-stu-id="9f8a8-140">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="9f8a8-141">Чтобы взаимодействовать с необработанными байтами в кадре памяти, выполните те же действия по настройке, что и в предыдущем разделе, и *онфотомодестартед* , как при записи фотографии в Texture2D.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-141">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="9f8a8-142">Разница заключается в *онкаптуредфототомемори* , где можно получить необработанные байты и взаимодействовать с ними.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-142">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="9f8a8-143">В этом примере вы создадите *список <Color>* , который будет обрабатываться или применен к текстуре с помощью *сетпикселс ()* .</span><span class="sxs-lookup"><span data-stu-id="9f8a8-143">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="9f8a8-144">Видеозапись</span><span class="sxs-lookup"><span data-stu-id="9f8a8-144">Video Capture</span></span>

<span data-ttu-id="9f8a8-145">**Пространство имен:** *UnityEngine. XR. WSA. веб-камера*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-145">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="9f8a8-146">**Тип:** *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-146">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="9f8a8-147">Функции *видеокаптуре* аналогичны функциям *фотозахвата*.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-147">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="9f8a8-148">Единственное отличие заключается в том, что необходимо указать значение кадров в секунду, которое можно сохранить непосредственно на диск в виде MP4-файла.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-148">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="9f8a8-149">Ниже приведены действия по использованию *видеокаптуре* .</span><span class="sxs-lookup"><span data-stu-id="9f8a8-149">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="9f8a8-150">Создание объекта *видеокаптуре*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-150">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="9f8a8-151">Создание объекта *камерапараметерс* с нужными параметрами</span><span class="sxs-lookup"><span data-stu-id="9f8a8-151">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="9f8a8-152">Запуск видеорежима через *стартвидеомодеасинк*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-152">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="9f8a8-153">Начать запись видео</span><span class="sxs-lookup"><span data-stu-id="9f8a8-153">Start recording video</span></span>
5. <span data-ttu-id="9f8a8-154">Закончить запись видео</span><span class="sxs-lookup"><span data-stu-id="9f8a8-154">Stop recording video</span></span>
6. <span data-ttu-id="9f8a8-155">Воспроизведение видеорежима и очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="9f8a8-155">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="9f8a8-156">Начните с создания нашего  объекта видеокаптуре *видеокаптуре m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="9f8a8-156">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="9f8a8-157">Затем настройте параметры для записи и запуска.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-157">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
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

<span data-ttu-id="9f8a8-158">После запуска Запустите запись.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-158">Once started, begin the recording</span></span>

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

<span data-ttu-id="9f8a8-159">После начала записи можно обновить пользовательский интерфейс или поведение, чтобы включить остановку.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-159">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="9f8a8-160">Здесь вы только зарегистрируетесь.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-160">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="9f8a8-161">На более позднем этапе вы захотите отключить запись с помощью таймера или ввода пользователя, например.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-161">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="9f8a8-162">После остановки записи остановите видеорежим и очистите ресурсы.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="9f8a8-163">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="9f8a8-163">Troubleshooting</span></span>
* <span data-ttu-id="9f8a8-164">Нет доступных разрешений</span><span class="sxs-lookup"><span data-stu-id="9f8a8-164">No resolutions are available</span></span>
    * <span data-ttu-id="9f8a8-165">Убедитесь, что в проекте указана возможность использования **веб-камеры** .</span><span class="sxs-lookup"><span data-stu-id="9f8a8-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9f8a8-166">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="9f8a8-166">Next Development Checkpoint</span></span>

<span data-ttu-id="9f8a8-167">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="9f8a8-167">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="9f8a8-168">Вы можете перейти к следующей статье:</span><span class="sxs-lookup"><span data-stu-id="9f8a8-168">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="9f8a8-169">[точка фокусировки](focus-point-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="9f8a8-169">[Focus point](focus-point-in-unity.md)</span></span>

<span data-ttu-id="9f8a8-170">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="9f8a8-170">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f8a8-171">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9f8a8-171">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="9f8a8-172">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-advanced-features).</span><span class="sxs-lookup"><span data-stu-id="9f8a8-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f8a8-173">См. также</span><span class="sxs-lookup"><span data-stu-id="9f8a8-173">See Also</span></span>
* [<span data-ttu-id="9f8a8-174">Камера с определяемым местоположением</span><span class="sxs-lookup"><span data-stu-id="9f8a8-174">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
