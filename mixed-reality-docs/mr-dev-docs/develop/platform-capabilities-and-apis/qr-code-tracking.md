---
title: Отслеживание QR-кода
description: Узнайте, как обнаруживать QR-коды, добавлять возможности веб-камеры и управлять системами координат в приложениях смешанной реальности в HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR, QR-код, hololens2
ms.openlocfilehash: 2617d5f811b9d437ece0d5ba2e7dbc909eb16988
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103574950"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="6a2f3-104">Отслеживание QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-104">QR code tracking</span></span>

<span data-ttu-id="6a2f3-105">HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="6a2f3-106">После включения веб-камеры устройства вы сможете распознать QR-коды в последних версиях проектов Нереал или Unity.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="6a2f3-107">Прежде чем перейти в рабочую среду, рекомендуется выполнить [рекомендации,](#best-practices-for-qr-code-detection) описанные в конце статьи.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="6a2f3-108">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="6a2f3-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6a2f3-109">Признак</span><span class="sxs-lookup"><span data-stu-id="6a2f3-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="6a2f3-110"><a href="/hololens/hololens1-hardware">HoloLens (первый общий)</a></span><span class="sxs-lookup"><span data-stu-id="6a2f3-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="6a2f3-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6a2f3-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="6a2f3-112"><a href="../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="6a2f3-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="6a2f3-113">Обнаружение QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="6a2f3-114">️</span><span class="sxs-lookup"><span data-stu-id="6a2f3-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6a2f3-115">✔️</span><span class="sxs-lookup"><span data-stu-id="6a2f3-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="6a2f3-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6a2f3-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="6a2f3-117">Отслеживание QR-кодов с помощью впечатляющих головных телефонов Windows Mixed Reality на настольных компьютерах поддерживается в Windows 10 версии 2004 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="6a2f3-118">Используйте API Microsoft. Микседреалити. Кркодеватчер. support (), чтобы определить, поддерживается ли эта функция на текущем устройстве.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="6a2f3-119">Получение QR-пакета</span><span class="sxs-lookup"><span data-stu-id="6a2f3-119">Getting the QR package</span></span>

<span data-ttu-id="6a2f3-120">Пакет NuGet для обнаружения QR-кода можно скачать [здесь](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="6a2f3-121">Обнаружение QR-кодов</span><span class="sxs-lookup"><span data-stu-id="6a2f3-121">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="6a2f3-122">Добавление возможности веб-камеры</span><span class="sxs-lookup"><span data-stu-id="6a2f3-122">Adding the webcam capability</span></span>

<span data-ttu-id="6a2f3-123">Чтобы обнаружить QR-коды, необходимо добавить в `webcam` Манифест возможность.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-123">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="6a2f3-124">Эта возможность необходима, так как данные в обнаруженных кодах в пользовательской среде могут содержать конфиденциальные сведения.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-124">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="6a2f3-125">Разрешение можно запросить, вызвав `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="6a2f3-125">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="6a2f3-126">_См_</span><span class="sxs-lookup"><span data-stu-id="6a2f3-126">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="6a2f3-127">_C++_</span><span class="sxs-lookup"><span data-stu-id="6a2f3-127">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="6a2f3-128">Разрешение должно быть запрошено до создания объекта Кркодеватчер.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-128">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="6a2f3-129">Хотя для обнаружения QR-кодов требуется `webcam` возможность, обнаружение осуществляется с помощью камер отслеживания устройства.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-129">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="6a2f3-130">Это обеспечивает более широкое ФОВное обнаружение и повышает время работы аккумулятора по сравнению с обнаружением с помощью камеры устройства и видео (ПС).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-130">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="6a2f3-131">Обнаружение QR-кодов в Unity</span><span class="sxs-lookup"><span data-stu-id="6a2f3-131">Detecting QR codes in Unity</span></span>

<span data-ttu-id="6a2f3-132">API обнаружения QR-кода можно использовать в Unity без импорта МРТК, установив пакет NuGet с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-132">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="6a2f3-133">Если вы хотите узнать, как это работает, скачайте [пример приложения Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-133">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="6a2f3-134">Пример приложения содержит примеры для отображения с holographic-го квадрата по QR кодам и связанным данным, таким как GUID, физический размер, метка времени и декодированные данные.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-134">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="6a2f3-135">Обнаружение QR-кодов в C++</span><span class="sxs-lookup"><span data-stu-id="6a2f3-135">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="6a2f3-136">Получение системы координат для QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-136">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="6a2f3-137">Каждый обнаруженный QR-код предоставляет [пространственное координатную систему](../../design/coordinate-systems.md) , согласованную с QR-кодом в левом верхнем углу квадрата быстрого обнаружения в верхней левой части:</span><span class="sxs-lookup"><span data-stu-id="6a2f3-137">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

<span data-ttu-id="6a2f3-139">При непосредственном использовании QR-пакета SDK ось Z указывает на бумагу (не показано) — при преобразовании в координаты Unity точки оси Z находятся за пределами бумаги и остаются в левой части.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-139">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="6a2f3-140">Спатиалкурдинатесистем QR-кода выстраивается так, как показано.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-140">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="6a2f3-141">Вы можете получить систему координат из платформы, вызвав <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">спатиалграфинтероппревиев:: креатекурдинатесистемфорноде</a> и передав спатиалграфнодеид кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-141">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="6a2f3-142">В приведенном ниже коде C++ показано, как создать прямоугольник и разместить его с помощью системы координат QR-кода:</span><span class="sxs-lookup"><span data-stu-id="6a2f3-142">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="6a2f3-143">Для создания QR-прямоугольника можно использовать физический размер:</span><span class="sxs-lookup"><span data-stu-id="6a2f3-143">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="6a2f3-144">Систему координат можно использовать для рисования QR-кода или прикрепления голограмм к расположению:</span><span class="sxs-lookup"><span data-stu-id="6a2f3-144">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="6a2f3-145">В целом, ваш *кркодеаддедхандлер* может выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="6a2f3-145">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="6a2f3-146">Рекомендации по обнаружению QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-146">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="6a2f3-147">Зоны без кавычек вокруг QR-кодов</span><span class="sxs-lookup"><span data-stu-id="6a2f3-147">Quiet zones around QR Codes</span></span>

<span data-ttu-id="6a2f3-148">Для правильного чтения QR-коды занимают поля вокруг всех сторон кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-148">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="6a2f3-149">Это поле не должно содержать ни одного печатного содержимого и должно состоять из четырех модулей (один черный квадрат в коде).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-149">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="6a2f3-150">[QR-спецификация](https://www.qrcode.com/en/howto/code.html) содержит дополнительные сведения о зонах «тихий».</span><span class="sxs-lookup"><span data-stu-id="6a2f3-150">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="6a2f3-151">Освещение и фон</span><span class="sxs-lookup"><span data-stu-id="6a2f3-151">Lighting and backdrop</span></span>
<span data-ttu-id="6a2f3-152">Качество обнаружения QR-кодов является уязвимым для различных освещения и подложки.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-152">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="6a2f3-153">В сцене с ярким освещением распечатайте черный цвет на сером фоне.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-153">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="6a2f3-154">В противном случае распечатайте черный QR-код на белом фоне.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-154">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="6a2f3-155">Если фон кода является темным, попробуйте использовать черный цвет в сером коде, если частота обнаружения мала.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-155">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="6a2f3-156">Если подложка относительно легкая, то обычный код должен работать нормально.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-156">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="6a2f3-157">Размер QR-кодов</span><span class="sxs-lookup"><span data-stu-id="6a2f3-157">Size of QR codes</span></span>
<span data-ttu-id="6a2f3-158">Устройства Windows Mixed Reality не работают с QR-кодами с сторонами, меньшими 5 cm.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-158">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="6a2f3-159">Для QR-кодов, которые находятся в диапазоне от 5 до 10 cm, вы должны быть достаточно близки к обнаружению кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-159">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="6a2f3-160">Для обнаружения кодов с таким размером также потребуется больше времени.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-160">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="6a2f3-161">Точное время на обнаружение кодов зависит не только от размера QR-кодов, но от того, насколько далеко вы находитесь вне кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-161">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="6a2f3-162">Переход ближе к коду поможет в смещении проблем с размером.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-162">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="6a2f3-163">Расстояние и угловое расположение из QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-163">Distance and angular position from the QR code</span></span>
<span data-ttu-id="6a2f3-164">Отслеживающие камеры могут обнаруживать только определенный уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-164">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="6a2f3-165">Для небольших кодов — < 10 cm вдоль сторон, вы должны быть достаточно близки.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-165">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="6a2f3-166">Для QR-кода версии 1, отличающегося от 10 cm до 25 сантиметров, минимальное расстояние обнаружения составляет от 0,15 метров до 0,5 метров.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-166">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="6a2f3-167">Расстояние обнаружения размера увеличивается линейно, но также зависит от версии QR или размера модуля.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-167">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="6a2f3-168">Чем выше версия, тем меньше модулей, которые можно обнаружить только в более близком месте.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-168">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="6a2f3-169">Вы также можете попробовать использовать микроqr-коды, если хотите, чтобы расстояние обнаружения было больше.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-169">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="6a2f3-170">Обнаружение QR работает с диапазоном углов + = 45 град, чтобы обеспечить правильное разрешение для обнаружения кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-170">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a2f3-171">Всегда убедитесь, что у вас есть достаточно контрастная и соответствующая граница.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-171">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="6a2f3-172">QR-коды с логотипами</span><span class="sxs-lookup"><span data-stu-id="6a2f3-172">QR codes with logos</span></span>
<span data-ttu-id="6a2f3-173">QR-коды с логотипами не тестировались и в настоящее время не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-173">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="6a2f3-174">Управление данными QR-кода</span><span class="sxs-lookup"><span data-stu-id="6a2f3-174">Managing QR code data</span></span>
<span data-ttu-id="6a2f3-175">Устройства Windows Mixed Reality обнаруживают QR-коды на уровне системы в драйвере.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-175">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="6a2f3-176">При перезагрузке устройства обнаруженные QR-коды исчезают и будут повторно обнаружены как новые объекты в следующий раз.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-176">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="6a2f3-177">Мы рекомендуем настроить приложение так, чтобы оно игнорировало QR-коды старше определенной метки времени.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-177">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="6a2f3-178">В настоящее время API не поддерживает очистку журнала QR-кода.</span><span class="sxs-lookup"><span data-stu-id="6a2f3-178">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="6a2f3-179">Размещение QR-кода в пространстве</span><span class="sxs-lookup"><span data-stu-id="6a2f3-179">QR code placement in a space</span></span>
<span data-ttu-id="6a2f3-180">Рекомендации по месту и способу размещения QR-кодов см. в статье [рекомендации по окружению для HoloLens](/hololens/hololens-environment-considerations).</span><span class="sxs-lookup"><span data-stu-id="6a2f3-180">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="6a2f3-181">Справочник по QR-API</span><span class="sxs-lookup"><span data-stu-id="6a2f3-181">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6a2f3-182">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6a2f3-182">See also</span></span>
* [<span data-ttu-id="6a2f3-183">Системы координат</span><span class="sxs-lookup"><span data-stu-id="6a2f3-183">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="6a2f3-184"><a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure.</a></span><span class="sxs-lookup"><span data-stu-id="6a2f3-184"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>