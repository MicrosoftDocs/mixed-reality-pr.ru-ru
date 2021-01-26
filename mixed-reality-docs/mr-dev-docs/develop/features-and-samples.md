---
title: Примеры приложений и возможностей
description: Узнавайте первыми обо всех доступных примерах Майкрософт и приложениях-функциях смешанной реальности для HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: смешанная реальность, unity, руководство, hololens, обучение, примеры, mrtk, режим исследований, hololens 2, qr-коды, webrtc, запись смешанной реальности, удаленное взаимодействие, средства пользовательского интерфейса
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583196"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="518f0-104">Примеры приложений и возможностей</span><span class="sxs-lookup"><span data-stu-id="518f0-104">Samples and feature apps</span></span>

![Изображение пользователя в HoloLens, который манипулирует голограммой с помощью движений рук](unreal/images/unreal-developer.jpg)

<span data-ttu-id="518f0-106">Каждый проект разработки начинается с обзора того, что уже сделали другие разработчики. Смешанная реальность не исключение.</span><span class="sxs-lookup"><span data-stu-id="518f0-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="518f0-107">Сейчас все наши руководства и примеры приложений встроены в Unity или Unreal.</span><span class="sxs-lookup"><span data-stu-id="518f0-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="518f0-108">По мере разработки содержимого для других движков и платформ вы сможете находить соответствующие руководства по заголовку в содержании.</span><span class="sxs-lookup"><span data-stu-id="518f0-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="518f0-109">Примеры приложений</span><span class="sxs-lookup"><span data-stu-id="518f0-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="518f0-110">Примеры возможностей</span><span class="sxs-lookup"><span data-stu-id="518f0-110">Feature samples</span></span>

<span data-ttu-id="518f0-111">Приведенные ниже примеры возможностей соответствуют определенным реализациям, которые описаны в нашей документации. Они поддерживают разные платформы разработки и аппаратные устройства.</span><span class="sxs-lookup"><span data-stu-id="518f0-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="518f0-112">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="518f0-112">Research Mode</span></span>

<span data-ttu-id="518f0-113">Режим исследования реализован в первом поколении HoloLens для обеспечения доступа к ключевым датчикам на устройстве специально для исследовательских приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="518f0-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="518f0-114">Примеры приложений, приведенные ниже, демонстрируют возможности получения доступа к потокам в режиме исследования и их записи, а также использования [встроенных и внешних объектов](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="518f0-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="518f0-115">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="518f0-115">Reference article</span></span> | <span data-ttu-id="518f0-116">Пример приложения</span><span class="sxs-lookup"><span data-stu-id="518f0-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="518f0-117">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="518f0-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="518f0-118">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="518f0-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="518f0-119">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="518f0-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="518f0-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="518f0-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="518f0-121">QR-коды</span><span class="sxs-lookup"><span data-stu-id="518f0-121">QR codes</span></span>

<span data-ttu-id="518f0-122">HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода.</span><span class="sxs-lookup"><span data-stu-id="518f0-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="518f0-123">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="518f0-123">Reference article</span></span> | <span data-ttu-id="518f0-124">Образец</span><span class="sxs-lookup"><span data-stu-id="518f0-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="518f0-125">QR-коды</span><span class="sxs-lookup"><span data-stu-id="518f0-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="518f0-126">Отслеживание QR-кодов в Unity</span><span class="sxs-lookup"><span data-stu-id="518f0-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="518f0-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="518f0-127">WebRTC</span></span>

<span data-ttu-id="518f0-128">Проект MixedReality-WebRTC — это набор компонентов, которые помогают разработчикам приложений смешанной реальности интегрировать возможности обмена аудио, видео и данными в реальном времени в свои приложения. Компоненты WebRTC основаны на протоколе WebRTC для RTC, поддерживаемом большинством современных веб-браузеров.</span><span class="sxs-lookup"><span data-stu-id="518f0-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="518f0-129">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="518f0-129">Reference article</span></span> | <span data-ttu-id="518f0-130">Образец</span><span class="sxs-lookup"><span data-stu-id="518f0-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="518f0-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="518f0-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="518f0-132">Примеры приложений WebRTC</span><span class="sxs-lookup"><span data-stu-id="518f0-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="518f0-133">Запись голограмм с помощью приложения "Съемка смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="518f0-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="518f0-134">Приложение "Съемка смешанной реальности" позволяет в реальном времени записывать процесс взаимодействия пользователя с реальностью, объединяющей реальный и цифровой миры, в формате фото и видео, а также в реальном времени обмениваться этими данными с другими пользователями.</span><span class="sxs-lookup"><span data-stu-id="518f0-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="518f0-135">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="518f0-135">Reference article</span></span> | <span data-ttu-id="518f0-136">Образец</span><span class="sxs-lookup"><span data-stu-id="518f0-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="518f0-137">Съемка смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="518f0-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="518f0-138">Примеры для приложения "Съемка смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="518f0-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="518f0-139">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="518f0-139">Holographic Remoting</span></span>

<span data-ttu-id="518f0-140">Holographic Remoting Player — это дополнительное приложение, которое подключается к приложениям и играм для ПК с поддержкой голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="518f0-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="518f0-141">Голографическое удаленное взаимодействие в реальном времени отправляет поток голографического содержимого с ПК в Microsoft HoloLens по Wi-Fi. Оно поддерживается в HoloLens (1-го поколения) и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="518f0-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="518f0-142">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="518f0-142">Reference article</span></span> | <span data-ttu-id="518f0-143">Образец</span><span class="sxs-lookup"><span data-stu-id="518f0-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="518f0-144">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="518f0-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="518f0-145">Примеры голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="518f0-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |