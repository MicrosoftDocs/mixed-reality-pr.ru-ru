---
title: Камера с определяемым местоположением
description: примеры кода, которые направлены на HoloLens переднюю камеру, как она работает, а также профили и разрешения, доступные для разработчиков.
author: cdedmonds
ms.author: v-vtieto
ms.date: 09/28/2021
ms.topic: article
keywords: Камера, hololens, цветовая камера, лицевая сторона, hololens 2, ОПС, компьютерное зрение, фидуЦиал, маркеры, QR-код, QR-, Фото, видео, размещаемые
ms.openlocfilehash: 815db661be66071c59a3a3470ed4acc55d2de812
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158505"
---
# <a name="locatable-camera"></a>Камера с определяемым местоположением

перед началом работы мы рекомендуем ознакомиться со статьей [о размещаемыеной камере](../advanced-concepts/locatable-camera-overview.md) , содержащей обзорную информацию и таблицу со сведениями о камере HoloLens 1 и 2.

### <a name="using-mediaframereference"></a>Использование Медиафрамереференце

Эти инструкции применяются, если вы используете класс [медиафрамереференце](/uwp/api/windows.media.capture.frames.mediaframereference) для чтения кадров изображения с камеры.

Каждый кадр изображения (фото или видео) включает в себя [спатиалкурдинатесистем](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) с корнем на камере во время записи, доступ к которому можно получить с помощью свойства [курдинатесистем](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) [медиафрамереференце](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Каждый кадр содержит описание модели линзы, которое можно найти в свойстве [камераинтринсикс](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Вместе эти преобразования определяются для каждого пикселя в трехмерном пространстве, представляющем путь, взятый фотоны, который создал пиксель. Эти лучи могут быть связаны с другим содержимым в приложении путем получения преобразования из системы координат кадра в другую систему координат (например, из [стационарной рамки ссылки](../../design/coordinate-systems.md#stationary-frame-of-reference)). 

Каждый кадр изображения предоставляет следующие сведения:
* Пиксельные данные (в формате RGB/NV12/JPEG/т. д.)
* [Спатиалкурдинатесистем](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) из расположения записи
* Класс [камераинтринсикс](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) , содержащий режим линзы камеры

[Образец холографикфацетраккинг](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) показывает довольно простой способ запроса преобразования между системой координат камеры и собственными системами координат приложения.

### <a name="using-media-foundation"></a>Использование Media Foundation

Если вы используете Media Foundation непосредственно для чтения кадров изображения с камеры, можно использовать [атрибуты MFSampleExtension_CameraExtrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) и [MFSampleExtension_PinholeCameraIntrinsics](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) для каждого кадра, чтобы нахождение кадров камеры относительно других систем координат вашего приложения, как показано в следующем примере кода:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```
## <a name="locatable-camera-usage-scenarios"></a>Сценарии использования камеры размещаемые

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Показывать фотографию или видео в мире, где они были собраны

Кадры камеры устройства поставляются с преобразованием «Камера — мир», которое можно использовать для отображения точного расположения устройства при создании образа. Например, можно разместить небольшой holographic-значок в этом месте (Камератоворлд. Мултиплипоинт (Vector3. Zero)) и даже нарисовать маленькую стрелку в направлении, в котором была направлена камера (Камератоворлд. Мултипливектор (Vector3. Forward)).

### <a name="frame-rate"></a>Частота кадров

Поддержание интерактивной частоты кадров приложений очень важна, особенно при работе с долгосрочными алгоритмами распознавания изображений. По этой причине мы обычно используем следующий шаблон:
1. Основной поток: управляет объектом Camera
2. Основной поток: запрашивает новые кадры (асинхронно)
3. Основной поток: передача новых кадров в отслеживаемый поток
4. Поток отслеживания: обрабатывает изображение для сбора ключевых точек
5. Основной поток: перемещение виртуальной модели в соответствие найденных ключевых точек
6. Основной поток: повторение из шага 2

Некоторые системы меток изображений обеспечивают только одно место в пикселях (другие предоставляют полное преобразование, в котором этот раздел не будет нужен), что соответствует лучау из возможных расположений. Чтобы перейти к одному третьему расположению, можно использовать несколько лучи и найти окончательный результат по их приблизительному пересечением. Вот как это сделать.
1. Получение цикла, который собирает несколько изображений с камеры
2. Найдите связанные точки компонентов и их лучи мира
3. Если у вас есть словарь функций, каждый из которых имеет несколько мировых индексов, можно использовать следующий код для решения пересечения этих лучей:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```
### <a name="positioning-a-modeled-scene"></a>Размещение смоделированной сцены

Учитывая два или более расположений отслеживаний тегов, можно разместить смоделированную сцену в соответствии с текущим сценарием пользователя. Если вы не можете предположить сила притяжения, вам потребуется три расположения тегов. Во многих случаях мы используем цветовую схему, где белый шарик представляет расположение тегов, отслеживающихся в реальном времени, а синий шарик — расположения смоделированных тегов. Это позволяет пользователю визуально оценить качество выравнивания. Мы предполагаем, что во всех наших приложениях выполняется следующая настройка:
* Два или более расположения смоделированных тегов
* Одна область калибровки, которая в сцене является родителем тегов
* Идентификатор компонента камеры
* Поведение, которое перемещает пространство калибровки для согласования модели тегов с тегами в реальном времени (мы внимательнее перемещать родительское пространство, а не сами маркеры, так как другие соединения являются позициями, связанными с ними).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Отслеживать или выявлять стационарные или переносить реальные объекты и лица с помощью индикаторов или других библиотек распознавателей;

Примеры:
* Промышленные роботы с индикаторами (или QR-коды для более медленных движущихся объектов)
* Определение и распознавание объектов в комнате
* Определение и распознавание людей в комнате, например размещение карточек контактных лиц с помощью лиц

## <a name="see-also"></a>См. также раздел
* [Пример камеры размещаемые](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Обзор камеры размещаемые](../advanced-concepts/locatable-camera-overview.md)
* [Камера с определяемым местоположением в Unity](../unity/locatable-camera-in-unity.md)
* [Смешанный захват реальности](/hololens/holographic-photos-and-videos)
* [Съемка смешанной реальности для разработчиков](../advanced-concepts/mixed-reality-capture-overview.md)
* [Введение в запись носителя](/windows/uwp/audio-video-camera/)
* [Пример отслеживания с "holographic лиц"](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)