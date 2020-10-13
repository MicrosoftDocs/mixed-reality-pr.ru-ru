---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды
ms.openlocfilehash: 0f0507e2f726830cef27c190083363b3607379ee
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957824"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="050a0-104">QR-коды в Unreal</span><span class="sxs-lookup"><span data-stu-id="050a0-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="050a0-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="050a0-105">Overview</span></span>

<span data-ttu-id="050a0-106">Устройство HoloLens 2 способно видеть QR-коды в мировом пространстве с помощью веб-камеры, отрисовывая их в виде голограмм с использованием системы координат в месте расположения каждого QR-кода в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="050a0-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="050a0-107">Помимо одиночных QR-кодов, HoloLens 2 может также отрисовывать голограммы в одном и том же месте на нескольких устройствах для общего взаимодействия с несколькими пользователями.</span><span class="sxs-lookup"><span data-stu-id="050a0-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="050a0-108">Соблюдайте рекомендации по добавлению QR-кодов в приложения:</span><span class="sxs-lookup"><span data-stu-id="050a0-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="050a0-109">Тихие зоны</span><span class="sxs-lookup"><span data-stu-id="050a0-109">Quiet zones</span></span>
- <span data-ttu-id="050a0-110">Освещение и фон</span><span class="sxs-lookup"><span data-stu-id="050a0-110">Lighting and backdrop</span></span>
- <span data-ttu-id="050a0-111">Размер, расстояние и угловое положение</span><span class="sxs-lookup"><span data-stu-id="050a0-111">Size, distance, and angular position</span></span>

<span data-ttu-id="050a0-112">Размещая QR-коды в приложении, следует уделять особое внимание [особенностям пространственной среды](../../environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="050a0-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="050a0-113">Более подробные сведения по каждой из этих тем, а также инструкции по скачиванию соответствующего пакета NuGet см. в главном документе "[Отслеживание QR-кодов](../platform-capabilities-and-apis/qr-code-tracking.md)".</span><span class="sxs-lookup"><span data-stu-id="050a0-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="050a0-114">Включение обнаружения QR-кодов</span><span class="sxs-lookup"><span data-stu-id="050a0-114">Enabling QR detection</span></span>
<span data-ttu-id="050a0-115">Поскольку для обнаружения QR-кодов устройству HoloLens 2 нужно задействовать веб-камеру, необходимо включить эту функцию в параметрах проекта:</span><span class="sxs-lookup"><span data-stu-id="050a0-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="050a0-116">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="050a0-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="050a0-117">Разверните раздел **Capabilities** (Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="050a0-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="050a0-118">Необходимо также включить отслеживание QR-кодов, [добавив ресурс ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) (по умолчанию оно выключено).</span><span class="sxs-lookup"><span data-stu-id="050a0-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="050a0-119">Непосредственно перед использованием вручную включите отслеживание, вызвав функцию `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span><span class="sxs-lookup"><span data-stu-id="050a0-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="050a0-120">Завершив отслеживание кода QR, отключите его, вызвав функцию `UHoloLensARFunctionLibrary::StopCameraCapture()`, чтобы уменьшить нагрузку на ресурсы устройства.</span><span class="sxs-lookup"><span data-stu-id="050a0-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="050a0-121">Настройка отслеживаемого изображения</span><span class="sxs-lookup"><span data-stu-id="050a0-121">Setting up a tracked image</span></span>

<span data-ttu-id="050a0-122">QR-коды выводятся в виде отслеживаемого изображения через систему отслеживания геометрии в дополненной реальности Unreal.</span><span class="sxs-lookup"><span data-stu-id="050a0-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="050a0-123">Чтобы обеспечить работу этого механизма:</span><span class="sxs-lookup"><span data-stu-id="050a0-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="050a0-124">Создайте схему Blueprint и добавьте в нее компонент **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="050a0-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="050a0-126">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="050a0-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="050a0-128">Нажмите кнопку **+** напротив события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), чтобы добавить соответствующий узел в граф событий.</span><span class="sxs-lookup"><span data-stu-id="050a0-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="050a0-129">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="050a0-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Добавление узла в событие On Add Tracked Geometry (При добавлении отслеживаемой геометрии)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="050a0-131">Использование отслеживаемого изображения</span><span class="sxs-lookup"><span data-stu-id="050a0-131">Using a tracked image</span></span>
<span data-ttu-id="050a0-132">В графе событий, показанном на следующей иллюстрации, событие **OnUpdateTrackedImage** используется для отрисовки точки в центре QR-кода и печати его данных.</span><span class="sxs-lookup"><span data-stu-id="050a0-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![Пример отрисовки QR-кода](images/unreal-qr-render.PNG)

<span data-ttu-id="050a0-134">Что происходит:</span><span class="sxs-lookup"><span data-stu-id="050a0-134">Here's what's going on:</span></span>
1. <span data-ttu-id="050a0-135">Сначала отслеживаемое изображение приводится к типу **ARTrackedQRCode** и проверяется, что текущее обновленное изображение содержит QR-код.</span><span class="sxs-lookup"><span data-stu-id="050a0-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="050a0-136">Закодированные данные извлекаются из переменной **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="050a0-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="050a0-137">Координаты левого верхнего угла QR-кода можно получить из расположения, возвращаемого функцией **GetLocalToWorldTransform**, а размеры кода — с помощью функции **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="050a0-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="050a0-138">Можно также [получить систему координат для QR-кода](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) в программном коде.</span><span class="sxs-lookup"><span data-stu-id="050a0-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="050a0-139">Поиск уникального идентификатора</span><span class="sxs-lookup"><span data-stu-id="050a0-139">Finding the unique ID</span></span>
<span data-ttu-id="050a0-140">Каждый QR-код имеет уникальный идентификатор (GUID), найти который можно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="050a0-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="050a0-141">Перетащите закрепление **As ARTracked QRCode** (Как отслеживаемый QR-код дополненной реальности) и найдите узел **Get Unique ID** (Получить уникальный идентификатор).</span><span class="sxs-lookup"><span data-stu-id="050a0-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID для QR-кода](images/unreal-qr-guid.PNG)

<span data-ttu-id="050a0-143">При работе с QR-кодами многое происходит за кадром, поэтому приведенные здесь сведения не исчерпывающие.</span><span class="sxs-lookup"><span data-stu-id="050a0-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="050a0-144">Ознакомьтесь с материалами по приведенным ниже ссылкам, чтобы узнать подробнее, как все организовано на более низком уровне.</span><span class="sxs-lookup"><span data-stu-id="050a0-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="050a0-145">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="050a0-145">Next Development Checkpoint</span></span>

<span data-ttu-id="050a0-146">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="050a0-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="050a0-147">Отсюда вы можете перейти к следующей теме:</span><span class="sxs-lookup"><span data-stu-id="050a0-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="050a0-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="050a0-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="050a0-149">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="050a0-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="050a0-150">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="050a0-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="050a0-151">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="050a0-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="050a0-152">См. также статью</span><span class="sxs-lookup"><span data-stu-id="050a0-152">See also</span></span>
* [<span data-ttu-id="050a0-153">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="050a0-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="050a0-154">Голограммы</span><span class="sxs-lookup"><span data-stu-id="050a0-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="050a0-155">Системы координат</span><span class="sxs-lookup"><span data-stu-id="050a0-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
