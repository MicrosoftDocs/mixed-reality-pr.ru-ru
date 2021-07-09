---
title: Примеры приложений и возможностей
description: Узнавайте первыми обо всех доступных примерах Майкрософт и приложениях-функциях смешанной реальности для HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: смешанная реальность, unity, руководство, hololens, обучение, примеры, mrtk, режим исследований, hololens 2, qr-коды, webrtc, запись смешанной реальности, удаленное взаимодействие, средства пользовательского интерфейса
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906900"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="2e02f-104">Примеры приложений и возможностей</span><span class="sxs-lookup"><span data-stu-id="2e02f-104">Samples and feature apps</span></span>

![Изображение пользователя в HoloLens, который манипулирует голограммой с помощью движений рук](unreal/images/unreal-developer.jpg)

<span data-ttu-id="2e02f-106">Каждый проект разработки начинается с обзора того, что уже сделали другие разработчики. Смешанная реальность не исключение.</span><span class="sxs-lookup"><span data-stu-id="2e02f-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="2e02f-107">Сейчас все наши руководства и примеры приложений встроены в Unity или Unreal.</span><span class="sxs-lookup"><span data-stu-id="2e02f-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="2e02f-108">По мере разработки содержимого для других движков и платформ вы сможете находить соответствующие руководства по заголовку в содержании.</span><span class="sxs-lookup"><span data-stu-id="2e02f-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="2e02f-109">Примеры приложений</span><span class="sxs-lookup"><span data-stu-id="2e02f-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="2e02f-110">Примеры возможностей</span><span class="sxs-lookup"><span data-stu-id="2e02f-110">Feature samples</span></span>

<span data-ttu-id="2e02f-111">Приведенные ниже примеры возможностей соответствуют определенным реализациям, которые описаны в нашей документации. Они поддерживают разные платформы разработки и аппаратные устройства.</span><span class="sxs-lookup"><span data-stu-id="2e02f-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="2e02f-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="2e02f-112">OpenXR</span></span>

<span data-ttu-id="2e02f-113">Для разработчиков, использующих Unity 2020 для создания приложений HoloLens 2 или смешанной реальности, можно использовать подключаемый модуль OpenXR вместо WindowsXR, чтобы улучшить совместимость между платформами.</span><span class="sxs-lookup"><span data-stu-id="2e02f-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="2e02f-114">Подключаемый модуль OpenXR для смешанной реальности хорошо работает с последним набором средств для смешанной реальности версии 2.7.</span><span class="sxs-lookup"><span data-stu-id="2e02f-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="2e02f-115">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-115">Reference article</span></span> | <span data-ttu-id="2e02f-116">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-117">Использование подключаемого модуля OpenXR</span><span class="sxs-lookup"><span data-stu-id="2e02f-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="2e02f-118">Смешанная реальность OpenXR с примерами Unity</span><span class="sxs-lookup"><span data-stu-id="2e02f-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="2e02f-119">Недоступно</span><span class="sxs-lookup"><span data-stu-id="2e02f-119">N/A</span></span> | [<span data-ttu-id="2e02f-120">Базовый проект Unity с MRTK OpenXR</span><span class="sxs-lookup"><span data-stu-id="2e02f-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="2e02f-121">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="2e02f-121">Research Mode</span></span>

<span data-ttu-id="2e02f-122">Режим исследования реализован в первом поколении HoloLens для обеспечения доступа к ключевым датчикам на устройстве специально для исследовательских приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="2e02f-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="2e02f-123">Примеры приложений, приведенные ниже, демонстрируют возможности получения доступа к потокам в режиме исследования и их записи, а также использования [встроенных и внешних объектов](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="2e02f-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="2e02f-124">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-124">Reference article</span></span> | <span data-ttu-id="2e02f-125">Пример приложения</span><span class="sxs-lookup"><span data-stu-id="2e02f-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-126">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="2e02f-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="2e02f-127">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="2e02f-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="2e02f-128">Режим исследования</span><span class="sxs-lookup"><span data-stu-id="2e02f-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="2e02f-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2e02f-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="2e02f-130">QR-коды</span><span class="sxs-lookup"><span data-stu-id="2e02f-130">QR codes</span></span>

<span data-ttu-id="2e02f-131">HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода.</span><span class="sxs-lookup"><span data-stu-id="2e02f-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="2e02f-132">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-132">Reference article</span></span> | <span data-ttu-id="2e02f-133">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-134">QR-коды</span><span class="sxs-lookup"><span data-stu-id="2e02f-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="2e02f-135">Отслеживание QR-кодов в Unity</span><span class="sxs-lookup"><span data-stu-id="2e02f-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="2e02f-136">Интерпретация сцены</span><span class="sxs-lookup"><span data-stu-id="2e02f-136">Scene understanding</span></span>

<span data-ttu-id="2e02f-137">Интерпретация сцены позволяет разработчикам смешанной реальности использовать структурированное высокоуровневое представление среды, чтобы сделать разработку приложений, учитывающих среду, интуитивно понятной.</span><span class="sxs-lookup"><span data-stu-id="2e02f-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="2e02f-138">При интерпретации сцены это достигается путем объединения возможностей существующих сред выполнения смешанной реальности, таких как высокоточное, но менее структурированное пространственное отображение, и новых исполнительных механизмов, управляемых искусственным интеллектом.</span><span class="sxs-lookup"><span data-stu-id="2e02f-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="2e02f-139">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-139">Reference article</span></span> | <span data-ttu-id="2e02f-140">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-141">Интерпретация сцены</span><span class="sxs-lookup"><span data-stu-id="2e02f-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="2e02f-142">Примеры интерпретации сцены смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="2e02f-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="2e02f-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="2e02f-143">WebRTC</span></span>

<span data-ttu-id="2e02f-144">Проект MixedReality-WebRTC — это набор компонентов, которые помогают разработчикам приложений смешанной реальности интегрировать возможности обмена аудио, видео и данными в реальном времени в свои приложения. Компоненты WebRTC основаны на протоколе WebRTC для RTC, поддерживаемом большинством современных веб-браузеров.</span><span class="sxs-lookup"><span data-stu-id="2e02f-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="2e02f-145">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-145">Reference article</span></span> | <span data-ttu-id="2e02f-146">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="2e02f-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="2e02f-148">Примеры приложений WebRTC</span><span class="sxs-lookup"><span data-stu-id="2e02f-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="2e02f-149">Запись голограмм с помощью приложения "Съемка смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="2e02f-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="2e02f-150">Приложение "Съемка смешанной реальности" позволяет в реальном времени записывать процесс взаимодействия пользователя с реальностью, объединяющей реальный и цифровой миры, в формате фото и видео, а также в реальном времени обмениваться этими данными с другими пользователями.</span><span class="sxs-lookup"><span data-stu-id="2e02f-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="2e02f-151">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-151">Reference article</span></span> | <span data-ttu-id="2e02f-152">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-153">Съемка смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="2e02f-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="2e02f-154">Примеры для приложения "Съемка смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="2e02f-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="2e02f-155">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2e02f-155">Holographic Remoting</span></span>

<span data-ttu-id="2e02f-156">Holographic Remoting Player — это дополнительное приложение, которое подключается к приложениям и играм для ПК с поддержкой голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2e02f-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="2e02f-157">Голографическое удаленное взаимодействие в реальном времени отправляет поток голографического содержимого с ПК в Microsoft HoloLens по Wi-Fi. Оно поддерживается в HoloLens (1-го поколения) и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2e02f-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="2e02f-158">Справочная статья</span><span class="sxs-lookup"><span data-stu-id="2e02f-158">Reference article</span></span> | <span data-ttu-id="2e02f-159">Образец</span><span class="sxs-lookup"><span data-stu-id="2e02f-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="2e02f-160">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2e02f-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="2e02f-161">Примеры голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="2e02f-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |