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
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583196"
---
# <a name="samples-and-feature-apps"></a>Примеры приложений и возможностей

![Изображение пользователя в HoloLens, который манипулирует голограммой с помощью движений рук](unreal/images/unreal-developer.jpg)

Каждый проект разработки начинается с обзора того, что уже сделали другие разработчики. Смешанная реальность не исключение. Сейчас все наши руководства и примеры приложений встроены в Unity или Unreal. По мере разработки содержимого для других движков и платформ вы сможете находить соответствующие руководства по заголовку в содержании.

## <a name="sample-apps"></a>Примеры приложений

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Примеры возможностей

Приведенные ниже примеры возможностей соответствуют определенным реализациям, которые описаны в нашей документации. Они поддерживают разные платформы разработки и аппаратные устройства.

### <a name="research-mode"></a>Режим исследования

Режим исследования реализован в первом поколении HoloLens для обеспечения доступа к ключевым датчикам на устройстве специально для исследовательских приложений, которые не предназначены для развертывания. Примеры приложений, приведенные ниже, демонстрируют возможности получения доступа к потокам в режиме исследования и их записи, а также использования [встроенных и внешних объектов](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Справочная статья | Пример приложения |
| --- | --- |
| [Режим исследования](platform-capabilities-and-apis/research-mode.md) | [HoloLens (1-го поколения)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Режим исследования](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR-коды

HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода.

<br>

| Справочная статья | Образец |
| --- | --- |
| [QR-коды](platform-capabilities-and-apis/qr-code-tracking.md) | [Отслеживание QR-кодов в Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a>WebRTC

Проект MixedReality-WebRTC — это набор компонентов, которые помогают разработчикам приложений смешанной реальности интегрировать возможности обмена аудио, видео и данными в реальном времени в свои приложения. Компоненты WebRTC основаны на протоколе WebRTC для RTC, поддерживаемом большинством современных веб-браузеров.

<br>

| Справочная статья | Образец |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [Примеры приложений WebRTC](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Запись голограмм с помощью приложения "Съемка смешанной реальности"

Приложение "Съемка смешанной реальности" позволяет в реальном времени записывать процесс взаимодействия пользователя с реальностью, объединяющей реальный и цифровой миры, в формате фото и видео, а также в реальном времени обмениваться этими данными с другими пользователями.

<br>

| Справочная статья | Образец |
| --- | --- |
| [Съемка смешанной реальности](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Примеры для приложения "Съемка смешанной реальности"](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Голографическое удаленное взаимодействие

Holographic Remoting Player — это дополнительное приложение, которое подключается к приложениям и играм для ПК с поддержкой голографического удаленного взаимодействия. Голографическое удаленное взаимодействие в реальном времени отправляет поток голографического содержимого с ПК в Microsoft HoloLens по Wi-Fi. Оно поддерживается в HoloLens (1-го поколения) и HoloLens 2.

<br>

| Справочная статья | Образец |
| --- | --- |
| [Голографическое удаленное взаимодействие](platform-capabilities-and-apis/holographic-remoting-player.md) | [Примеры голографического удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |