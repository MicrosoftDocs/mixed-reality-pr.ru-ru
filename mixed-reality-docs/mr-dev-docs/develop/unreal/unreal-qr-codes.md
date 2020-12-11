---
title: QR-коды в Unreal
description: Введение в использование QR-кодов в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, QR-коды, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 7e39e1d822f0aa623a83678beef24f2c98a18944
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609645"
---
# <a name="qr-codes-in-unreal"></a>QR-коды в Unreal

Устройство HoloLens 2 способно видеть QR-коды в мировом пространстве с помощью веб-камеры, отрисовывая их в виде голограмм в месте расположения каждого QR-кода в реальном мире. Кроме того, HoloLens 2 может также отрисовывать голограммы в одном и том же месте на нескольких устройствах для общего взаимодействия с несколькими пользователями. Соблюдайте рекомендации по добавлению QR-кодов в приложения:

- Тихие зоны
- Освещение и фон
- Размер, расстояние и угловое положение

Размещая QR-коды в приложении, следует уделять особое внимание [особенностям пространственной среды](../../environment-considerations-for-hololens.md). Более подробные сведения по каждой из этих тем, а также инструкции по скачиванию соответствующего пакета NuGet см. в главном документе "[Отслеживание QR-кодов](../platform-capabilities-and-apis/qr-code-tracking.md)".

> [!CAUTION]
> QR-коды — это единственный тип изображений, отслеживаемый HoloLens без дополнительной настройки. Модуль Unreal **UARTrackedImage** не поддерживается в HoloLens. Если вам требуется отслеживать собственные изображения, вы можете получать данные с [веб-камеры](unreal-hololens-camera.md) устройства и обрабатывать кадры с нее с помощью сторонней библиотеки распознавания изображений. 

## <a name="enabling-qr-detection"></a>Включение обнаружения QR-кодов
Поскольку для обнаружения QR-кодов устройству HoloLens 2 нужно задействовать веб-камеру, необходимо включить эту функцию в параметрах проекта:
- Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите элемент **HoloLens**.
    + Разверните раздел **Capabilities** (Возможности) и установите флажок **Webcam** (Веб-камера).  
- Необходимо также включить отслеживание QR-кодов, [добавив ресурс ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) (по умолчанию оно выключено).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Настройка отслеживаемого QR-кода

QR-коды выводятся в виде отслеживаемого изображения через систему отслеживания геометрии в дополненной реальности Unreal. Чтобы обеспечить работу этого механизма:
1. Создайте схему субъекта и добавьте в нее компонент **ARTrackableNotify**:

![AR Trackable Notify для QR-кодов](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События):

![События QR-кодов](images/unreal-spatialmapping-events.PNG)

3. Нажмите кнопку **+** напротив события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), чтобы добавить соответствующий узел в граф событий.
    - Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Добавление узла в событие On Add Tracked Geometry (При добавлении отслеживаемой геометрии)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Использование отслеживаемого QR-кода
В графе событий, показанном на следующей иллюстрации, событие **OnUpdateTrackedImage** используется для отрисовки точки в центре QR-кода и печати его данных.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Что происходит:
1. Сначала отслеживаемое изображение приводится к типу **ARTrackedQRCode** и проверяется, что текущее обновленное изображение содержит QR-код.  
2. Закодированные данные извлекаются из переменной **QRCode**. Координаты левого верхнего угла QR-кода можно получить из расположения, возвращаемого функцией **GetLocalToWorldTransform**, а размеры кода — с помощью функции **GetEstimateSize**.

Можно также [получить систему координат для QR-кода](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) в программном коде.

## <a name="finding-the-unique-id"></a>Поиск уникального идентификатора
Каждый QR-код имеет уникальный идентификатор (GUID), найти который можно следующим образом:
- Перетащите закрепление **As ARTracked QRCode** (Как отслеживаемый QR-код дополненной реальности) и найдите узел **Get Unique ID** (Получить уникальный идентификатор).

![GUID для QR-кода](images/unreal-qr-guid.PNG)

При работе с QR-кодами многое происходит за кадром, поэтому приведенные здесь сведения не исчерпывающие. Ознакомьтесь с материалами по приведенным ниже ссылкам, чтобы узнать подробнее, как все организовано на более низком уровне.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности. Отсюда вы можете перейти к следующей теме:

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:

> [!div class="nextstepaction"]
> [Развертывание на устройстве](unreal-deploying.md)

Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis).

## <a name="see-also"></a>См. также статью
* [Пространственное сопоставление](../../design/spatial-mapping.md)
* [Голограммы](../../discover/hologram.md)
* [Системы координат](../../design/coordinate-systems.md)
