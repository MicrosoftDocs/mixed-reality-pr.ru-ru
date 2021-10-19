---
title: Отслеживание QR-кода
description: Узнайте, как обнаруживать QR-коды, добавлять возможности веб-камеры и управлять системами координат в приложениях Unity Mixed Reality на HoloLens 2.
author: dorreneb
ms.author: v-vtieto
ms.date: 09/28/2021
ms.topic: article
keywords: VR, лбе, развлечения на основе расположения, VR Аркадные, Аркадные, иммерсивное, QR-, QR-код, hololens2, отслеживание
ms.openlocfilehash: 41088e70e53c0519facc7073880a3e1df8ce7402
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130157761"
---
# <a name="qr-code-tracking"></a>Отслеживание QR-кода

Перед началом работы мы рекомендуем ознакомиться со статьей [Обзор отслеживания QR-кода](../advanced-concepts/qr-code-tracking-overview.md) , содержащей общие сведения, таблицу поддержки устройств и рекомендации.

### <a name="detecting-qr-codes"></a>Обнаружение QR-кодов

### <a name="adding-the-webcam-capability"></a>Добавление возможности веб-камеры

Чтобы обнаружить QR-коды, необходимо добавить в `webcam` Манифест возможность. Эта возможность необходима, так как данные в обнаруженных кодах в пользовательской среде могут содержать конфиденциальные сведения.

Разрешение можно запросить, вызвав `QRCodeWatcher.RequestAccessAsync()` :

_См_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

Разрешение должно быть запрошено до создания объекта Кркодеватчер.

Хотя для обнаружения QR-кодов требуется `webcam` возможность, обнаружение осуществляется с помощью камер отслеживания устройства. Это обеспечивает более широкое ФОВное обнаружение и повышает время работы аккумулятора по сравнению с обнаружением с помощью камеры устройства и видео (ПС).

API обнаружения QR-кода можно использовать в Unity без импорта мртк, установив пакет NuGet с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity). Если вы хотите узнать, как это работает, скачайте [пример приложения Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). Пример приложения содержит примеры для отображения с holographic-го квадрата по QR кодам и связанным данным, таким как GUID, физический размер, метка времени и декодированные данные.

## <a name="using-openxr"></a>Использование Опенкср

При использовании подключаемого модуля Опенкср Извлеките [ `SpatialGraphNodeId` из QR-интерфейса API](../native/qr-code-tracking-cs-cpp.md#qr-code-tracking-api-reference) и используйте `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API для нахождение QR-кода.

для справки существует [пример проекта отслеживания QR на GitHub](https://github.com/yl-msft/QRTracking) с более подробным описанием использования [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Получение системы координат для QR-кода

Каждый обнаруженный QR-код предоставляет [пространственное координатную систему](../../design/coordinate-systems.md) , согласованную с QR-кодом в левом верхнем углу квадрата быстрого обнаружения в верхней левой части:  

![Система координат QR-кода](images/Qr-coordinatesystem.png) 

При преобразовании в координаты Unity указывает, что ось Z находится за пределами бумаги и является левой.

## <a name="see-also"></a>См. также раздел
* [Обзор отслеживания QR-кода](../advanced-concepts/qr-code-tracking-overview.md)
* [Отслеживание QR-кода с помощью машинных примеров C++ и C# #](../native/qr-code-tracking-cs-cpp.md)
* [Справочник по API отслеживания QR-кода](../native/qr-code-tracking-cs-cpp.md)
* [Системы координат](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure.</a>