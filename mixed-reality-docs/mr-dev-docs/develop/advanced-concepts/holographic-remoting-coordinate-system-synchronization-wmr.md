---
title: синхронизация системы координирования с помощью удаленного взаимодействия с holographic и Windows Mixed Reality API
description: на этой странице объясняется, как выполняется синхронизация системы с помощью удаленного взаимодействия с holographic и Windows Mixed Reality API.
author: vimusc
ms.author: vimusch
ms.date: 09/07/2021
ms.topic: article
keywords: HoloLens, HoloLens 2, mixed reality, мртк, смешанная реальность набор средств, дополненная реальность, виртуальная реальность, телефоны смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие
ms.openlocfilehash: a3f501464945bc4c625df96ea864bf2921ccf61e
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158236"
---
# <a name="coordinate-system-synchronization-with-holographic-remoting-and-the-windows-mixed-reality-api"></a>синхронизация системы координирования с помощью удаленного взаимодействия с holographic и Windows Mixed Reality API

при использовании Windows Mixed Reality API система координат пользователя упаковывается в [спатиалстатионарифрамеофреференце](/uwp/api/windows.perception.spatial.spatialstationaryframeofreference).

> [!TIP]
> Простой пример можно найти в примерах для удаленного доступа и проигрывателя в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
>Раскомментируйте в ```#define ENABLE_USER_COORDINATE_SYSTEM_SAMPLE``` файлах самплеремотеапп. h и самплеплайермаин. h, чтобы включить пример кода.

## <a name="set-and-update-the-user-coordinate-system-in-the-player-app"></a>Установка и обновление пользовательской системы координат в приложении проигрывателя

Чтобы установить и обновить систему координат пользователя, вызовите ```UpdateUserSpatialFrameOfReference``` в контексте игрока и передайте в него [спатиалкурдинатесистем](/uwp/api/windows.perception.spatial.spatialCoordinateSystem) .
[Спатиалкурдинатесистем](/uwp/api/windows.perception.spatial.spatialCoordinateSystem) может, например, быть [спатиалстатионарифрамеофреференце](/uwp/api/windows.perception.spatial.spatialstationaryframeofreference), [спатиаллокатораттачедфрамеофреференце](/uwp/api/windows.perception.spatial.SpatialLocatorAttachedFrameOfReference)или [SpatialAnchor](/uwp/api/windows.perception.spatial.SpatialAnchor).

> [!NOTE]
> При использовании примера [спатиалстатионарифрамеофреференце](/uwp/api/windows.perception.spatial.spatialstationaryframeofreference) ```UpdateUserSpatialFrameOfReference``` необходимо вызывать через обычный интервал, чтобы избежать смещения после потери отслеживания устройств, даже если система координат пользователя не изменилась.

## <a name="get-the-user-coordinate-system-in-the-remote-app"></a>Получение пользовательской системы координат в удаленном приложении

Чтобы получить доступ к пользовательской системе координат, вызовите в ```GetUserSpatialFrameOfReference``` удаленном контексте.
```GetUserSpatialFrameOfReference``` Возвращает [спатиалстатионарифрамеофреференце](/uwp/api/windows.perception.spatial.spatialstationaryframeofreference), представляющий систему координат пользователя.

## <a name="see-also"></a>См. также:
* [Общие сведения о синхронизации системы в holographic с помощью удаленного взаимодействия](holographic-remoting-coordinate-system-synchronization.md)
