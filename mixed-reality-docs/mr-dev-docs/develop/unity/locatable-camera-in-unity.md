---
title: Фото- и видеокамера в Unity
description: Узнайте, как записать фотографию в файл или Texture2D, как записать фотографию и взаимодействовать с необработанными байтами, а также как записать видео.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: Фото, видео, hololens, Камера, Unity, размещаемые, PVC, видеокамера, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, веб-камера, запись фотографий, видеозапись
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193508"
---
# <a name="photo-video-camera-in-unity"></a>Фото- и видеокамера в Unity

## <a name="enabling-the-capability-for-camera-access"></a>Включение возможности доступа к камере

Для использования [камеры](../platform-capabilities-and-apis/locatable-camera.md)приложение должно быть объявлено как "веб-камера".

1. в редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "изменение > Project Параметры > player".
2. выберите вкладку "хранилище Windows".
3. в разделе "возможности публикации Параметры >" проверьте возможности веб- **камеры** и **микрофона** .

Только одна операция может выполняться с камерой за раз. В `UnityEngine.XR.WSA.WebCam.Mode` unity 2018 и более ранних версиях или `UnityEngine.Windows.WebCam.Mode` в Unity 2019 и более поздних версиях можно проверить, в каком режиме в настоящее время находится камера. Доступные режимы: Фото, видео или нет.

## <a name="photo-capture"></a>Запись фотографий

**Пространство имен (перед Unity 2019):** *UnityEngine. XR. WSA. веб-камера*<br>
**Namespace (Unity 2019 и более поздние версии):** *UnityEngine. Windows. Веб-камера*<br>
**Тип:** *фотозапись*

Тип *фотосъемки* позволяет вам по-прежнему иметь фотографии фотокамеры. Общий шаблон использования *фотосъемки* для получения фотографий выглядит следующим образом:

1. Создание объекта *Фотозаписи*
2. Создание объекта *камерапараметерс* с нужными параметрами
3. Запуск фоторежима через *стартфотомодеасинк*
4. Сделайте нужную фотографию
    * используемых Взаимодействие с этим изображением
5. Отключение режима фото и очистка ресурсов

### <a name="common-set-up-for-photocapture"></a>Общая Настройка для фотозаписи

Для всех трех вариантов использования Начните с тех же первых трех описанных выше действий.

Начните с создания объекта *фотосъемки*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Затем сохраните объект, задайте параметры и запустите режим фото.

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

В итоге вы также будете использовать тот же код очистки, представленный здесь.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

После выполнения этих действий можно выбрать тип фотографии для записи.

### <a name="capture-a-photo-to-a-file"></a>Фотозахват в файл

Самой простой операцией является запись фотографии непосредственно в файл. Фотографию можно сохранить в формате JPG или PNG.

Если вы успешно начали фото-режим, возьмите фотографию и сохраните ее на диске.

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

После записи фотографии на диск выйдите из режима Photo, а затем очистите объекты

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Запись фотографии в Texture2D с расположением

При записи данных в Texture2D процесс аналогичен записи на диск.

Выполните описанный выше процесс установки.

В *онфотомодестартед* запишите кадр в память.

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

Затем вы примените результат к текстуре и используйте общий приведенный выше код очистки.

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

#### <a name="locatable-camera"></a>Камера с определяемым местоположением

Чтобы поместить эту текстуру в сцену и отобразить ее с помощью матриц размещаемые Camera, добавьте следующий код в *онкаптуредфототомемори* в `result.success` проверке:

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

В [Unity предоставлен пример кода](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) для применения матрицы проекции к конкретному шейдеру на форумах.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Запись фотографии и взаимодействие с необработанными байтами

Чтобы взаимодействовать с необработанными байтами в кадре памяти, выполните те же действия по настройке, что и в предыдущем разделе, и *онфотомодестартед* , как при записи фотографии в Texture2D. Разница заключается в *онкаптуредфототомемори* , где можно получить необработанные байты и взаимодействовать с ними.

В этом примере вы создадите *список <Color>* , который будет обрабатываться или применен к текстуре с помощью *сетпикселс ()* .

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

## <a name="video-capture"></a>Видеозахват

**Пространство имен (перед Unity 2019):** *UnityEngine. XR. WSA. веб-камера*<br>
**Namespace (Unity 2019 и более поздние версии):** *UnityEngine. Windows. Веб-камера*<br>
**Тип:** *видеокаптуре*

Функции *видеокаптуре* аналогичны функциям *фотозахвата*. Единственное отличие заключается в том, что необходимо указать значение кадров в секунду, которое можно сохранить непосредственно на диск как файл .mp4. Ниже приведены действия по использованию *видеокаптуре* .

1. Создание объекта *видеокаптуре*
2. Создание объекта *камерапараметерс* с нужными параметрами
3. Запуск видеорежима через *стартвидеомодеасинк*
4. Начать запись видео
5. Закончить запись видео
6. Воспроизведение видеорежима и очистка ресурсов

Начните с создания нашего  объекта видеокаптуре *видеокаптуре m_VideoCapture = NULL;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Затем настройте параметры для записи и запуска.

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

После запуска Запустите запись.

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

После начала записи можно обновить пользовательский интерфейс или поведение, чтобы включить остановку. Здесь вы только зарегистрируетесь.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

На более позднем этапе вы захотите отключить запись с помощью таймера или ввода пользователя, например.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

После остановки записи остановите видеорежим и очистите ресурсы.

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

## <a name="troubleshooting"></a>Устранение неполадок

* Нет доступных разрешений
  * Убедитесь, что в проекте указана возможность использования **веб-камеры** .

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API. Вы можете перейти к следующей статье:

> [!div class="nextstepaction"]
> [точка фокусировки](focus-point-in-unity.md);

Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:

> [!div class="nextstepaction"]
> [развертывание в HoloLens или Windows Mixed Reality впечатляющих головных телефонов](../platform-capabilities-and-apis/using-visual-studio.md)

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-advanced-features).

## <a name="see-also"></a>См. также:

* [Камера с определяемым местоположением](../platform-capabilities-and-apis/locatable-camera.md)