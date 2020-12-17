---
title: Направление головы и взгляда в DirectX
description: Узнайте, как использовать головное взгляд и отслеживание взгляда в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: взгляд на глаза, головной взгляд, отслеживание головок, отслеживание глаз, DirectX, ввод, голограммы, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 4e8c638d91125a30cb4121b09a699f9ff6db5892
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613048"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="6a4ce-104">Ввод с взгляда на глаза в DirectX</span><span class="sxs-lookup"><span data-stu-id="6a4ce-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="6a4ce-105">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="6a4ce-106">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="6a4ce-107">В Windows Mixed Reality для определения того, что просматривает пользователь, используется ввод с глазом и взглядом на головной взгляд.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="6a4ce-108">Данные можно использовать для управления первичными входными моделями, такими как [head-взгляд и Commit](../../design/gaze-and-commit.md), и предоставления контекста для различных типов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-108">You can use the data to drive primary input models like [head-gaze and commit](../../design/gaze-and-commit.md), and provide context for different interaction types.</span></span> <span data-ttu-id="6a4ce-109">Есть два типа векторов взгляда, доступных через API: «Head-взгляд» и «глаз-взгляд».</span><span class="sxs-lookup"><span data-stu-id="6a4ce-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="6a4ce-110">Оба объекта предоставляются в виде трехмерного луча с исходным и направленным координатами.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-110">Both are provided as a three-dimensional ray with an origin and direction.</span></span> <span data-ttu-id="6a4ce-111">Приложения могут райкаст в фоновом режиме или в реальном мире, а также определить назначение пользователя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="6a4ce-112">**Заголовок-взгляд** представляет направление, на которое указывает заголовок пользователя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="6a4ce-113">Обдумайте голову как расположение и направление вперед самого устройства, в качестве центральной точки между двумя дисплеями.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-113">Think of head-gaze as the position and forward direction of the device itself, with the position as the center point between the two displays.</span></span> <span data-ttu-id="6a4ce-114">Головной взгляд доступен на всех устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="6a4ce-115">**Глаз** . Наблюдатель представляет направление, в котором просматриваются глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="6a4ce-116">Источник располагается между глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="6a4ce-117">Он доступен на устройствах смешанной реальности, включающих систему отслеживания глаз.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-117">It's available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="6a4ce-118">И те, и другие лучи доступны через API  [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="6a4ce-119">Вызовите метод [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе в указанной метке времени и [системе координат](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-119">Call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="6a4ce-120">Этот Спатиалпоинтерпосе содержит источник и направление головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="6a4ce-121">Он также содержит источник глаза и направление взгляда, если отслеживание взгляда доступно.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="6a4ce-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="6a4ce-122">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="6a4ce-123"><strong>Компонент</strong></span><span class="sxs-lookup"><span data-stu-id="6a4ce-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="6a4ce-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6a4ce-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="6a4ce-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6a4ce-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="6a4ce-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="6a4ce-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="6a4ce-127">Направление головы</span><span class="sxs-lookup"><span data-stu-id="6a4ce-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="6a4ce-128">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4ce-128">✔️</span></span></td>
     <td><span data-ttu-id="6a4ce-129">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4ce-129">✔️</span></span></td>
     <td><span data-ttu-id="6a4ce-130">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4ce-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="6a4ce-131">Взгляд — взгляд</span><span class="sxs-lookup"><span data-stu-id="6a4ce-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="6a4ce-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4ce-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="6a4ce-133">Использование Head-взгляда</span><span class="sxs-lookup"><span data-stu-id="6a4ce-133">Using head-gaze</span></span>

<span data-ttu-id="6a4ce-134">Чтобы получить доступ к Head, начните с вызова  [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="6a4ce-135">Передайте следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-135">Pass the following parameters.</span></span>
 - <span data-ttu-id="6a4ce-136">Объект [спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , представляющий нужную систему координат для головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the coordinate system you want for the head-gaze.</span></span> <span data-ttu-id="6a4ce-137">Он представлен переменной *курдинатесистем* в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="6a4ce-138">Дополнительные сведения см. в нашем разделе, посвященном разработчику [систем координат](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="6a4ce-139">[Отметка времени](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , представляющая точное время запроса Head.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="6a4ce-140">Как правило, используется метка времени, соответствующая времени, когда будет отображаться текущий кадр.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-140">Typically, you'll use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="6a4ce-141">Эту прогнозируемую отметку экрана можно получить из объекта  [холографикфрамепредиктион](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , доступного через текущий [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="6a4ce-142">Этот объект Холографикфрамепредиктион представляется переменной *прогноза* в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="6a4ce-143">После получения допустимого Спатиалпоинтерпосе расположение головного и прямого направления можно получить в виде свойств.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="6a4ce-144">В следующем коде показано, как получить доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="6a4ce-145">Использование глаза-взгляд</span><span class="sxs-lookup"><span data-stu-id="6a4ce-145">Using eye-gaze</span></span>

<span data-ttu-id="6a4ce-146">Чтобы пользователи могли использовать ввод с глазным взглядом, каждый пользователь должен пройти по [калибровке пользователя с отслеживанием взгляда](../../calibration.md) при первом использовании устройства.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-146">For your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="6a4ce-147">API взгляда на глаза похож на «голова-взгляд».</span><span class="sxs-lookup"><span data-stu-id="6a4ce-147">The eye-gaze API is similar to head-gaze.</span></span>
<span data-ttu-id="6a4ce-148">Он использует тот же API [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , который предоставляет происхождение и направление луча, которые можно райкаст на сцене.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="6a4ce-149">Единственное отличие заключается в том, что необходимо явно включить отслеживание взгляда перед его использованием:</span><span class="sxs-lookup"><span data-stu-id="6a4ce-149">The only difference is that you need to explicitly enable eye tracking before using it:</span></span>
1. <span data-ttu-id="6a4ce-150">Запрос разрешения пользователя на использование отслеживания взгляда в приложении.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-150">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="6a4ce-151">Включите функцию "Ввод взгляда" в манифесте пакета.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-151">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="6a4ce-152">Запрос доступа к входным данным взгляда</span><span class="sxs-lookup"><span data-stu-id="6a4ce-152">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="6a4ce-153">При запуске приложения вызовите [эйеспосе:: рекуестакцессасинк](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) , чтобы запросить доступ к отслеживанию глаз.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-153">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="6a4ce-154">Система запросит пользователя при необходимости и возвратит [газеинпутакцессстатус:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) после предоставления доступа.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-154">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="6a4ce-155">Это асинхронный вызов, поэтому для него требуется некоторое дополнительное управление.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-155">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="6a4ce-156">В следующем примере показано, как отсоединить отсоединенный std:: Thread для ожидания результата, который он сохраняет в переменную-член с именем *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-156">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="6a4ce-157">Запуск отсоединенного потока — это только один вариант для обработки асинхронных вызовов.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-157">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="6a4ce-158">Можно также использовать новые функции [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) , поддерживаемые C++/винрт.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-158">You could also use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="6a4ce-159">Вот еще один пример для запроса разрешения пользователя:</span><span class="sxs-lookup"><span data-stu-id="6a4ce-159">Here's another example for asking for user permission:</span></span>
-   <span data-ttu-id="6a4ce-160">Эйеспосе:: An () позволяет приложению активировать диалоговое окно разрешения только при наличии средства записи глаз.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-160">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there's an eye tracker.</span></span>
-   <span data-ttu-id="6a4ce-161">Газеинпутакцессстатус m_gazeInputAccessStatus; Это позволяет предотвратить повторное извлечение запроса на разрешение.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-161">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="6a4ce-162">Объявление возможности ввода с помощью *взгляда*</span><span class="sxs-lookup"><span data-stu-id="6a4ce-162">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="6a4ce-163">Дважды щелкните файл AppxManifest в *Обозреватель решений*.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-163">Double-click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="6a4ce-164">Затем перейдите к разделу возможностей и проверьте возможность *ввода* с помощью *средства* выбора.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-164">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Возможность ввода с клавиатуры](images/gaze-input-capability.png)

<span data-ttu-id="6a4ce-166">В раздел *пакета* в файле appxmanifest добавляются следующие строки:</span><span class="sxs-lookup"><span data-stu-id="6a4ce-166">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="6a4ce-167">Получение луча с глазом взгляда</span><span class="sxs-lookup"><span data-stu-id="6a4ce-167">Getting the eye-gaze ray</span></span>
<span data-ttu-id="6a4ce-168">После получения доступа к ET вы можете бесплатно захватить каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-168">Once you have received access to ET, you're free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="6a4ce-169">Как и в случае с Head-взглядом, получите [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , вызвав [Спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с нужной меткой времени и системой координат.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-169">As with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="6a4ce-170">Спатиалпоинтерпосе содержит объект [эйеспосе](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) через свойство [глаза](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-170">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="6a4ce-171">Это значение не равно null, только если включено отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-171">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="6a4ce-172">После этого можно проверить, имеет ли пользователь устройства калибровку отслеживания взгляда, вызвав [эйеспосе:: искалибратионвалид](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-172">From there, you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="6a4ce-173">Затем [Используйте свойство "наблюдатель",](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) чтобы получить [спатиалрай](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) , содержащий расположение и направление взгляда.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-173">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="6a4ce-174">Свойство "взгляд" иногда может иметь значение null, поэтому обязательно проверьте это.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-174">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="6a4ce-175">Это может произойти, если калибровка пользователя временно закрывает свои глаза.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-175">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="6a4ce-176">В следующем коде показано, как получить доступ к лучау глаза.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-176">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a><span data-ttu-id="6a4ce-177">Откат, когда отслеживание глаз недоступно</span><span class="sxs-lookup"><span data-stu-id="6a4ce-177">Fallback when eye tracking isn't available</span></span>
<span data-ttu-id="6a4ce-178">Как упоминалось в [документах по проектированию отслеживания взгляда](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), проектировщики и разработчики должны знать экземпляры, в которых данные отслеживания взгляда могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-178">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers and developers should be aware of instances where eye tracking data may not be available.</span></span>

<span data-ttu-id="6a4ce-179">Существуют различные причины недоступности данных.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-179">There are various reasons for data being unavailable:</span></span>
* <span data-ttu-id="6a4ce-180">Пользователь не откалиброван</span><span class="sxs-lookup"><span data-stu-id="6a4ce-180">A user not being calibrated</span></span>
* <span data-ttu-id="6a4ce-181">Пользователь отклонил доступ к данным отслеживания взгляда на приложение.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-181">A user has denied the app access to his/her eye tracking data</span></span>
* <span data-ttu-id="6a4ce-182">Временные помехи, такие как Растушевка на делителях HoloLens или волосы, окклудинг глаз пользователя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-182">Temporary interferences, such as smudges on the HoloLens visor or hair occluding the user's eyes.</span></span> 

<span data-ttu-id="6a4ce-183">Хотя некоторые API-интерфейсы уже упоминались в этом документе, в следующей статье мы предоставляем сводку о том, как определить, что отслеживание взгляда доступно в качестве краткого справочника:</span><span class="sxs-lookup"><span data-stu-id="6a4ce-183">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="6a4ce-184">Убедитесь, что система поддерживает отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-184">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="6a4ce-185">Вызовите следующий *метод*: [Windows. восприятие. People. эйеспосе. Поддержка ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="6a4ce-185">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="6a4ce-186">Убедитесь, что пользователь откалиброван.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-186">Check that the user is calibrated.</span></span> <span data-ttu-id="6a4ce-187">Вызовите следующее *свойство*: [Windows. восприятие. People. эйеспосе. искалибратионвалид](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="6a4ce-187">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="6a4ce-188">Убедитесь, что пользователь предоставил приложению разрешение на использование данных отслеживания взгляда: получение текущего _"газеинпутакцессстатус"_.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-188">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="6a4ce-189">Пример того, как это сделать, объясняется в [запросе доступа к вводу с помощью взгляда](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-189">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="6a4ce-190">Кроме того, можно проверить, не устарели ли данные отслеживания взгляда, добавив время ожидания между полученными обновлениями данных отслеживания взгляда и иным образом выполнить откат до головного взгляда, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-190">You may also want to check that your eye tracking data isn't stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>   
<span data-ttu-id="6a4ce-191">Дополнительные сведения см. в разделе [рекомендации по проектированию резервного проектирования](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-191">Visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="6a4ce-192">Сопоставление взгляда с другими входными данными</span><span class="sxs-lookup"><span data-stu-id="6a4ce-192">Correlating gaze with other inputs</span></span>
<span data-ttu-id="6a4ce-193">Иногда может оказаться, что требуется [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) , соответствующий событию в прошлом.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-193">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="6a4ce-194">Например, если пользователь выполняет касание Air, ваше приложение может захотеть узнать, что именно оно искало.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-194">For example, if the user does an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="6a4ce-195">Для этой цели простое использование [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с прогнозируемым временем кадров будет неточным из-за задержки между системной обработкой входных данных и временем вывода.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-195">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="6a4ce-196">Кроме того, если для нацеливания используется глаз, наши глаза, как правило, переходят даже перед завершением действия фиксации.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-196">Also, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="6a4ce-197">Это не является проблемой для простого касания воздуха, но становится более важным при объединении длинных голосовых команд с помощью передвижений с быстрым глазом.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-197">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="6a4ce-198">Одним из способов решения этого сценария является создание дополнительного вызова  [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)с использованием метки времени с предысторией, соответствующей входному событию.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-198">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="6a4ce-199">Однако для входных данных, перенаправляющихся через Спатиалинтерактионманажер, существует более простой метод.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-199">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="6a4ce-200">[Спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) имеет собственную функцию [трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-200">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="6a4ce-201">Вызов, который предоставит вполне коррелированный [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) без предоставляя.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-201">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="6a4ce-202">Дополнительные сведения о работе с Спатиалинтерактионсаурцестатес см. в документации по [DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="6a4ce-202">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="6a4ce-203">Калибровка</span><span class="sxs-lookup"><span data-stu-id="6a4ce-203">Calibration</span></span>
<span data-ttu-id="6a4ce-204">Чтобы отслеживание отслеживания проработало правильно, каждый пользователь должен пройти по [калибровке пользователя с отслеживанием взгляда](../../calibration.md).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-204">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="6a4ce-205">Это позволяет устройству настроить систему для более удобного и качественного просмотра для пользователя, а также для обеспечения точного отслеживания в то же время.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-205">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="6a4ce-206">Разработчикам не нужно ничего делать на своих концах для управления калибровкой пользователей.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-206">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="6a4ce-207">Система обеспечит пользователю запрос на калибровку устройства в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="6a4ce-207">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="6a4ce-208">Пользователь использует устройство в первый раз</span><span class="sxs-lookup"><span data-stu-id="6a4ce-208">The user is using the device for the first time</span></span>
* <span data-ttu-id="6a4ce-209">Пользователь ранее отказался от процесса калибровки</span><span class="sxs-lookup"><span data-stu-id="6a4ce-209">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="6a4ce-210">Процесс калибровки не был выполнен в последний раз, когда пользователь использовал устройство.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-210">The calibration process didn't succeed the last time the user used the device</span></span>

<span data-ttu-id="6a4ce-211">Разработчикам следует обеспечить необходимую поддержку для пользователей, в которых данные отслеживания взгляда могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-211">Developers should make sure to provide adequate support for users where eye tracking data may not be available.</span></span> <span data-ttu-id="6a4ce-212">Дополнительные сведения см. в статье рекомендации по [отслеживанию решений на сайте HoloLens 2](../../design/eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-212">Learn more about considerations for fallback solutions at [Eye tracking on HoloLens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="6a4ce-213">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6a4ce-213">See also</span></span>
* [<span data-ttu-id="6a4ce-214">Калибровка</span><span class="sxs-lookup"><span data-stu-id="6a4ce-214">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="6a4ce-215">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="6a4ce-215">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="6a4ce-216">Глаз — Взгляните на HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6a4ce-216">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="6a4ce-217">Входная модель "взгляд" и "фиксация"</span><span class="sxs-lookup"><span data-stu-id="6a4ce-217">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="6a4ce-218">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="6a4ce-218">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="6a4ce-219">Ввод голоса в DirectX</span><span class="sxs-lookup"><span data-stu-id="6a4ce-219">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
