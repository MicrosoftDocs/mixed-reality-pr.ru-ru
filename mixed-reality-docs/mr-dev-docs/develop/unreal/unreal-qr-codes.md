---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 72f08c22b8dcab5e13de2baae817b3496ada1a60
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926075"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="f0d3d-104">QR-коды в Unreal</span><span class="sxs-lookup"><span data-stu-id="f0d3d-104">QR codes in Unreal</span></span>

<span data-ttu-id="f0d3d-105">Устройство HoloLens 2 способно видеть QR-коды в мировом пространстве с помощью веб-камеры, отрисовывая их в виде голограмм в месте расположения каждого QR-кода в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="f0d3d-106">Кроме того, HoloLens 2 может также отрисовывать голограммы в одном и том же месте на нескольких устройствах для общего взаимодействия с несколькими пользователями.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="f0d3d-107">Соблюдайте рекомендации по добавлению QR-кодов в приложения:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="f0d3d-108">Тихие зоны</span><span class="sxs-lookup"><span data-stu-id="f0d3d-108">Quiet zones</span></span>
- <span data-ttu-id="f0d3d-109">Освещение и фон</span><span class="sxs-lookup"><span data-stu-id="f0d3d-109">Lighting and backdrop</span></span>
- <span data-ttu-id="f0d3d-110">Размер, расстояние и угловое положение</span><span class="sxs-lookup"><span data-stu-id="f0d3d-110">Size, distance, and angular position</span></span>

<span data-ttu-id="f0d3d-111">Размещая QR-коды в приложении, следует уделять особое внимание [особенностям пространственной среды](../../environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="f0d3d-112">Более подробные сведения по каждой из этих тем, а также инструкции по скачиванию соответствующего пакета NuGet см. в главном документе "[Отслеживание QR-кодов](../platform-capabilities-and-apis/qr-code-tracking.md)".</span><span class="sxs-lookup"><span data-stu-id="f0d3d-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="f0d3d-113">QR-коды — это единственный тип изображений, отслеживаемый HoloLens без дополнительной настройки. Модуль Unreal **UARTrackedImage** не поддерживается в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="f0d3d-114">Если вам требуется отслеживать собственные изображения, вы можете получать данные с [веб-камеры](unreal-hololens-camera.md) устройства и обрабатывать кадры с нее с помощью сторонней библиотеки распознавания изображений.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="f0d3d-115">Включение обнаружения QR-кодов</span><span class="sxs-lookup"><span data-stu-id="f0d3d-115">Enabling QR detection</span></span>
<span data-ttu-id="f0d3d-116">Поскольку для обнаружения QR-кодов устройству HoloLens 2 нужно задействовать веб-камеру, необходимо включить эту функцию в параметрах проекта:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="f0d3d-117">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите элемент **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="f0d3d-118">Разверните раздел **Capabilities** (Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="f0d3d-119">Необходимо также включить отслеживание QR-кодов, [добавив ресурс ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) (по умолчанию оно выключено).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="f0d3d-120">Настройка отслеживаемого QR-кода</span><span class="sxs-lookup"><span data-stu-id="f0d3d-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="f0d3d-121">QR-коды выводятся в виде отслеживаемого изображения через систему отслеживания геометрии в дополненной реальности Unreal.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="f0d3d-122">Чтобы обеспечить работу этого механизма:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="f0d3d-123">Создайте схему субъекта и добавьте в нее компонент **ARTrackableNotify**:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="f0d3d-125">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События):</span><span class="sxs-lookup"><span data-stu-id="f0d3d-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="f0d3d-127">Нажмите кнопку **+** напротив события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), чтобы добавить соответствующий узел в граф событий.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="f0d3d-128">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Добавление узла в событие On Add Tracked Geometry (При добавлении отслеживаемой геометрии)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="f0d3d-130">Использование отслеживаемого QR-кода</span><span class="sxs-lookup"><span data-stu-id="f0d3d-130">Using a tracked QR code</span></span>
<span data-ttu-id="f0d3d-131">В графе событий, показанном на следующей иллюстрации, событие **OnUpdateTrackedImage** используется для отрисовки точки в центре QR-кода и печати его данных.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="f0d3d-132">Что происходит:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-132">Here's what's going on:</span></span>
1. <span data-ttu-id="f0d3d-133">Сначала отслеживаемое изображение приводится к типу **ARTrackedQRCode** и проверяется, что текущее обновленное изображение содержит QR-код.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="f0d3d-134">Закодированные данные извлекаются из переменной **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="f0d3d-135">Координаты левого верхнего угла QR-кода можно получить из расположения, возвращаемого функцией **GetLocalToWorldTransform**, а размеры кода — с помощью функции **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="f0d3d-136">Можно также [получить систему координат для QR-кода](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) в программном коде.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="f0d3d-137">Поиск уникального идентификатора</span><span class="sxs-lookup"><span data-stu-id="f0d3d-137">Finding the unique ID</span></span>
<span data-ttu-id="f0d3d-138">Каждый QR-код имеет уникальный идентификатор (GUID), найти который можно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="f0d3d-139">Перетащите закрепление **As ARTracked QRCode** (Как отслеживаемый QR-код дополненной реальности) и найдите узел **Get Unique ID** (Получить уникальный идентификатор).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID для QR-кода](images/unreal-qr-guid.PNG)

<span data-ttu-id="f0d3d-141">При работе с QR-кодами многое происходит за кадром, поэтому приведенные здесь сведения не исчерпывающие.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="f0d3d-142">Ознакомьтесь с материалами по приведенным ниже ссылкам, чтобы узнать подробнее, как все организовано на более низком уровне.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f0d3d-143">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="f0d3d-143">Next Development Checkpoint</span></span>

<span data-ttu-id="f0d3d-144">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f0d3d-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="f0d3d-145">Отсюда вы можете перейти к следующей теме:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0d3d-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="f0d3d-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="f0d3d-147">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="f0d3d-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0d3d-148">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="f0d3d-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="f0d3d-149">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="f0d3d-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d3d-150">См. также статью</span><span class="sxs-lookup"><span data-stu-id="f0d3d-150">See also</span></span>
* [<span data-ttu-id="f0d3d-151">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f0d3d-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="f0d3d-152">Голограммы</span><span class="sxs-lookup"><span data-stu-id="f0d3d-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="f0d3d-153">Системы координат</span><span class="sxs-lookup"><span data-stu-id="f0d3d-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)
