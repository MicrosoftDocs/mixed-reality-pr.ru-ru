---
title: Пользовательские каналы данных с holographic удаленное взаимодействие и API Опенкср
description: На этой странице объясняется, как можно использовать пользовательские каналы данных с API Опенкср для отправки пользовательских данных через уже установленное удаленное подключение Holographic.
author: vimusc
ms.author: vimusch
ms.date: 09/07/2021
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, гарнитура смешанной реальности, гарнитура windows mixed, гарнитура виртуальной реальности, каналы данных
ms.openlocfilehash: a342f344dcad840a01acb9ca04c6cce2ef467aa1
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158423"
---
# <a name="custom-data-channels-with-holographic-remoting-and-the-openxr-api"></a>Пользовательские каналы данных с holographic удаленное взаимодействие и API Опенкср

> [!NOTE]
> это руководство относится к удаленному взаимодействию с HoloLens 2 и Windows пк под управлением [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

Используйте пользовательские каналы данных для отправки пользовательских данных через установленное удаленное соединение.

> [!IMPORTANT]
> Для пользовательских каналов данных требуется пользовательское удаленное приложение и пользовательское приложение проигрывателя. Это позволяет обмениваться данными между двумя пользовательскими приложениями.

> [!TIP]
> Простой пример для проверки связи можно найти в примерах для удаленного доступа и проигрывателя в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
>Раскомментируйте в ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` файлах опенксрпрограмм. cpp и самплеплайермаин. h, чтобы включить пример кода.

> [!IMPORTANT]
> Подробную [спецификацию](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html) можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).


## <a name="create-a-custom-data-channel"></a>Создание пользовательского канала данных

После успешной установки соединения новые каналы данных можно создать с помощью ```xrCreateRemotingDataChannelMSFT``` функции.
Пользовательские каналы данных можно создавать из проигрывателя и из удаленного приложения, даже если среды выполнения различаются.
Если канал данных создается на стороне проигрывателя, то удаленная сторона получает уведомления о ```XrEventDataRemotingDataChannelCreatedMSFT``` структуре событий.

Начальное ```XrRemotingDataChannelStatusMSFT``` состояние после вызова ```xrCreateRemotingDataChannelMSFT``` — ```XR_REMOTING_DATA_CHANNEL_STATUS_OPEN_PENDING_MSFT``` .
После полной установки канала данных состояние канала переключается на ```XR_REMOTING_DATA_CHANNEL_STATUS_OPENED_MSFT``` .
```XrEventDataRemotingDataChannelOpenedMSFT```Структура событий помещается в очередь событий, когда состояние ранее созданного канала данных переключается с ```XR_REMOTING_DATA_CHANNEL_STATUS_OPEN_PENDING_MSFT``` на ```XR_REMOTING_DATA_CHANNEL_STATUS_OPENED_MSFT``` .

## <a name="send-data"></a>Отправка данных

```xrSendRemotingDataMSFT```Функция используется для отправки данных на сторону проигрывателя.

## <a name="retrieve-data"></a>Получение данных

Каждый раз, когда данные поступают через канал данных, ```XrEventDataRemotingDataChannelDataReceivedMSFT``` Структура событий помещается в очередь событий.
Полученные пакеты можно получить с помощью ```xrRetrieveRemotingDataMSFT``` функции.

## <a name="get-the-channel-state"></a>Получение состояния канала

```xrGetRemotingDataChannelStateMSFT```Функцию можно использовать для запроса состояния канала данных.

## <a name="destroy-a-data-channel"></a>Уничтожение канала данных

Канал данных можно уничтожить с помощью ```xrDestroyRemotingDataChannelMSFT``` .
```XrRemotingDataChannelMSFT```Маркер является недопустимым после ```xrDestroyRemotingDataChannelMSFT``` вызова, и обработчик канала данных не должен использоваться впоследствии.

Объект ```XrEventDataRemotingDataChannelClosedMSFT``` будет помещен в очередь событий в том случае, если сторона проигрывателя закроет или удалит канал данных.
Состояние канала данных переключается в ```XR_REMOTING_DATA_CHANNEL_STATUS_CLOSED_MSFT``` .
Для закрытого канала данных ```XrRemotingDataChannelMSFT``` маркер остается действительным.

## <a name="see-also"></a>См. также:
* [Обзор удаленного голографического взаимодействия](holographic-remoting-overview.md)
* [Создание удаленного приложения holographic с удаленным взаимодействием с помощью API-интерфейсов Опенкср](../native/holographic-remoting-create-remote-openxr.md)
