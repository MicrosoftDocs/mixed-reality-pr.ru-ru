---
title: Синхронизация системы координирования с помощью удаленного взаимодействия и API Опенкср
description: На этой странице объясняется, как работает Синхронизация системы с помощью удаленного взаимодействия с holographic и API Опенкср.
author: vimusc
ms.author: vimusch
ms.date: 09/07/2021
ms.topic: article
keywords: HoloLens, HoloLens 2, mixed reality, мртк, смешанная реальность набор средств, дополненная реальность, виртуальная реальность, телефоны смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, опенкср
ms.openlocfilehash: 969548e269b77d4ed99fd5280c630c89cf808043
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158272"
---
# <a name="coordinate-system-synchronization-with-holographic-remoting-and-the-openxr-api"></a>Синхронизация системы координирования с помощью удаленного взаимодействия и API Опенкср

С помощью API Опенкср система координат пользователя упаковывается в пространство ссылок типа ```XR_REMOTING_REFERENCE_SPACE_TYPE_USER_MSFT``` .

>[!TIP]
>Простой пример можно найти в примерах для удаленного доступа и проигрывателя в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
>Раскомментируйте в ```#define ENABLE_USER_COORDINATE_SYSTEM_SAMPLE``` файлах опенксрпрограмм. cpp и самплеплайермаин. h, чтобы включить пример кода.

>[!IMPORTANT]
>Чтобы узнать об API расширения Опенкср для удаленного взаимодействия с holographic, ознакомьтесь со [спецификацией](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html) , которую можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="get-the-user-coordinate-system-in-the-remote-app"></a>Получение пользовательской системы координат в удаленном приложении

Создание пользовательской системы координат в удаленном вызове приложения ```xrCreateReferenceSpace``` с ```XR_REMOTING_REFERENCE_SPACE_TYPE_USER_MSFT``` аргументом.

## <a name="see-also"></a>См. также:
* [Общие сведения о синхронизации системы в holographic с помощью удаленного взаимодействия](holographic-remoting-coordinate-system-synchronization.md)
