---
title: Режим воспроизведения в Unity
description: Узнайте, как использовать режим воспроизведения в редакторе Unity для предварительного просмотра изменений приложения на устройстве без развертывания приложения.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, удаленное взаимодействие, удаленное взаимодействие с holographic, holographic удаленное взаимодействие, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, режим воспроизведения Unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392299"
---
# <a name="unity-play-mode"></a>Режим воспроизведения в Unity

Быстрый способ работы с проектом Unity — использование режима воспроизведения, который локально запускает приложение в редакторе Unity на компьютере. Unity использует holographic удаленное взаимодействие, чтобы обеспечить быстрый способ предварительного просмотра содержимого на реальном устройстве HoloLens. Режим воспроизведения также можно использовать с головным телефоном Windows Mixed Reality, подключенным к компьютеру разработки.

## <a name="holographic-remoting-setup"></a>Настройка удаленного взаимодействия с holographic

1. Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store в HoloLens 2.
2. Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.
    * Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Режим воспроизведения Unity с holographic удаленное взаимодействие

С помощью удаленного взаимодействия с holographic вы можете столкнуться с приложением на HoloLens, когда оно выполняется в редакторе Unity на компьютере. Входные данные с помощью взгляда, жеста, голоса и пространственного сопоставления отправляются из HoloLens на компьютер. Затем отображаемые кадры отправляются обратно в HoloLens. Это отличный способ быстрой отладки приложения без создания и развертывания полного проекта.

[!INCLUDE[](includes/unity-play-mode.md)]

Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение. Дополнительные сведения можно найти в документации по [удаленному проигрывателю holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Для достижения лучших результатов убедитесь, что приложение правильно устанавливает [фокусную точку](focus-point-in-unity.md). Это помогает более удачному удаленному взаимодействию лучше адаптировать сцену к задержке беспроводного подключения.

## <a name="see-also"></a>См. также

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
