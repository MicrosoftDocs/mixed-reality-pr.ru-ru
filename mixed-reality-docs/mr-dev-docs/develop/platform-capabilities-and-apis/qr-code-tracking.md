---
title: Отслеживание QR-кода
description: Узнайте, как обнаруживать QR-коды, добавлять возможности веб-камеры и управлять системами координат в приложениях смешанной реальности в HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код, hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394338"
---
# <a name="qr-code-tracking"></a>Отслеживание QR-кода

HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода. После включения веб-камеры устройства вы сможете распознать QR-коды в последних версиях проектов Нереал или Unity. Прежде чем перейти в рабочую среду, рекомендуется выполнить [рекомендации,](#best-practices-for-qr-code-detection) описанные в конце статьи.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Компонент</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (первый общий)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td> Обнаружение QR-кода</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>Отслеживание QR-кодов с помощью впечатляющих головных телефонов Windows Mixed Reality на настольных компьютерах поддерживается в Windows 10 версии 2004 и более поздних версиях. Используйте API Microsoft. Микседреалити. Кркодеватчер. support (), чтобы определить, поддерживается ли эта функция на текущем устройстве.

## <a name="getting-the-qr-package"></a>Получение QR-пакета

Пакет NuGet для обнаружения QR-кода можно скачать [здесь](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="using-openxr"></a>Использование Опенкср

При использовании подключаемого модуля Опенкср Извлеките [ `SpatialGraphNodeId` из QR-интерфейса API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) и используйте `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API для нахождение QR-кода.

Для справки у нас есть [Пример проекта отслеживания QR](https://github.com/yl-msft/QRTracking) -кодов на сайте GitHub с более подробным описанием использования [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="detecting-qr-codes"></a>Обнаружение QR-кодов

### <a name="adding-the-webcam-capability"></a>Добавление возможности веб-камеры

Чтобы обнаружить QR-коды, необходимо добавить в `webcam` Манифест возможность. Эта возможность необходима, так как данные в обнаруженных кодах в пользовательской среде могут содержать конфиденциальные сведения.

Разрешение можно запросить, вызвав `QRCodeWatcher.RequestAccessAsync()` :

_См_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Разрешение должно быть запрошено до создания объекта Кркодеватчер.

Хотя для обнаружения QR-кодов требуется `webcam` возможность, обнаружение осуществляется с помощью камер отслеживания устройства. Это обеспечивает более широкое ФОВное обнаружение и повышает время работы аккумулятора по сравнению с обнаружением с помощью камеры устройства и видео (ПС).

### <a name="detecting-qr-codes-in-unity"></a>Обнаружение QR-кодов в Unity

API обнаружения QR-кода можно использовать в Unity без импорта МРТК, установив пакет NuGet с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity). Если вы хотите узнать, как это работает, скачайте [пример приложения Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). Пример приложения содержит примеры для отображения с holographic-го квадрата по QR кодам и связанным данным, таким как GUID, физический размер, метка времени и декодированные данные.

### <a name="detecting-qr-codes-in-c"></a>Обнаружение QR-кодов в C++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Получение системы координат для QR-кода

Каждый обнаруженный QR-код предоставляет [пространственное координатную систему](../../design/coordinate-systems.md) , согласованную с QR-кодом в левом верхнем углу квадрата быстрого обнаружения в верхней левой части:  

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

При непосредственном использовании QR-пакета SDK ось Z указывает на бумагу (не показано) — при преобразовании в координаты Unity точки оси Z находятся за пределами бумаги и остаются в левой части.

Спатиалкурдинатесистем QR-кода выстраивается так, как показано. Вы можете получить систему координат из платформы, вызвав <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">спатиалграфинтероппревиев:: креатекурдинатесистемфорноде</a> и передав спатиалграфнодеид кода.

В приведенном ниже коде C++ показано, как создать прямоугольник и разместить его с помощью системы координат QR-кода:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Для создания QR-прямоугольника можно использовать физический размер:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

В целом, ваш *кркодеаддедхандлер* может выглядеть примерно так:

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Рекомендации по обнаружению QR-кода

### <a name="quiet-zones-around-qr-codes"></a>Зоны без кавычек вокруг QR-кодов

Для правильного чтения QR-коды занимают поля вокруг всех сторон кода. Это поле не должно содержать ни одного печатного содержимого и должно состоять из четырех модулей (один черный квадрат в коде). 

[QR-спецификация](https://www.qrcode.com/en/howto/code.html) содержит дополнительные сведения о зонах «тихий».

### <a name="lighting-and-backdrop"></a>Освещение и фон
Качество обнаружения QR-кодов является уязвимым для различных освещения и подложки. 

В сцене с ярким освещением распечатайте черный цвет на сером фоне. В противном случае распечатайте черный QR-код на белом фоне.

Если фон кода является темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала. Если подложка относительно легкая, то обычный код должен работать нормально.

### <a name="size-of-qr-codes"></a>Размер QR-кодов
Устройства Windows Mixed Reality не работают с QR-кодами с сторонами, меньшими 5 cm.

Для QR-кодов, которые находятся в диапазоне от 5 до 10 cm, вы должны быть достаточно близки к обнаружению кода. Для обнаружения кодов с таким размером также потребуется больше времени. 

Точное время на обнаружение кодов зависит не только от размера QR-кодов, но от того, насколько далеко вы находитесь вне кода. Переход ближе к коду поможет в смещении проблем с размером.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Расстояние и угловое расположение из QR-кода
Отслеживающие камеры могут обнаруживать только определенный уровень детализации. Для небольших кодов — < 10 cm вдоль сторон, вы должны быть достаточно близки. Для QR-кода версии 1, отличающегося от 10 cm до 25 сантиметров, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров. 

Расстояние обнаружения размера увеличивается линейно, но также зависит от версии QR или размера модуля. Чем выше версия, тем меньше модулей, которые можно обнаружить только в более близком месте. Вы также можете попробовать использовать микроqr-коды, если хотите, чтобы расстояние обнаружения было больше. Обнаружение QR работает с диапазоном углов + = 45 град, чтобы обеспечить правильное разрешение для обнаружения кода.

> [!IMPORTANT]
> Всегда убедитесь, что у вас есть достаточно контрастная и соответствующая граница.

### <a name="qr-codes-with-logos"></a>QR-коды с логотипами
QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.

### <a name="managing-qr-code-data"></a>Управление данными QR-кода
Устройства Windows Mixed Reality обнаруживают QR-коды на уровне системы в драйвере. При перезагрузке устройства обнаруженные QR-коды исчезают и будут повторно обнаружены как новые объекты в следующий раз.

Мы рекомендуем настроить приложение так, чтобы оно игнорировало QR-коды старше определенной метки времени. В настоящее время API не поддерживает очистку журнала QR-кода.

### <a name="qr-code-placement-in-a-space"></a>Размещение QR-кода в пространстве
Рекомендации по месту и способу размещения QR-кодов см. в статье [рекомендации по окружению для HoloLens](/hololens/hololens-environment-considerations).

## <a name="qr-api-reference"></a>Справочник по QR-API

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>См. также
* [Системы координат](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure.</a>