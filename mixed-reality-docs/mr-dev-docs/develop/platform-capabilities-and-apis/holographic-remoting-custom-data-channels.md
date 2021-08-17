---
title: Пользовательские каналы данных с голографическим удаленным взаимодействием
description: Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное подключение Holographic.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, гарнитура смешанной реальности, гарнитура windows mixed, гарнитура виртуальной реальности, каналы данных
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184715"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>Пользовательские каналы данных с удаленным взаимодействием holographic (C++)

>[!NOTE]
>Это руководство относится к удаленному взаимодействию с HoloLens 2.

Используйте пользовательские каналы данных для отправки пользовательских данных через установленное удаленное соединение.

>[!IMPORTANT]
>Для пользовательских каналов данных требуется пользовательское удаленное приложение и пользовательское приложение проигрывателя, так как оно обеспечивает взаимодействие между двумя пользовательскими приложениями.

>[!TIP]
>Простой пример для проверки связи можно найти в примерах для удаленного доступа и проигрывателя в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Раскомментируйте в ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` файлах самплеремотемаин. h/самплеплайермаин. h, чтобы включить пример кода.


## <a name="create-a-custom-data-channel"></a>Создание пользовательского канала данных


Для создания пользовательского канала данных требуются следующие поля:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

После успешной установки соединения можно создавать каналы данных на удаленной стороне, на стороне проигрывателя или в обоих случаях. Как Ремотеконтекст, так и Плайерконтекст предоставляют ```CreateDataChannel()``` метод для создания каналов данных. Первый параметр — это идентификатор канала, который используется для идентификации канала данных в последующих операциях. Вторым параметром является приоритет, указывающий приоритет, с которым данные этого канала передаются на другую сторону. Допустимые идентификаторы каналов на удаленной стороне: от 0 до 63, а 64 до и включительно, включая 127 для стороны проигрывателя. Допустимые приоритеты: ```Low``` , ```Medium``` или ```High``` (на обеих сторонах).

Чтобы начать создание канала данных на **удаленной** стороне, выполните следующие действия.
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Чтобы начать создание канала данных на стороне **проигрывателя** , выполните следующие действия.
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Чтобы создать новый пользовательский канал данных, необходимо вызвать метод только одной стороны (удаленно или с помощью проигрывателя) ```CreateDataChannel``` .

## <a name="handling-custom-data-channel-events"></a>Обработка пользовательских событий канала данных

Чтобы установить пользовательский канал данных, необходимо ```OnDataChannelCreated``` обработать событие (как на проигрывателе, так и на удаленной стороне). Он активируется, когда пользовательский канал данных создается с обеих сторон, и предоставляет ```IDataChannel``` объект, который можно использовать для отправки и получения данных по этому каналу.

Чтобы зарегистрировать прослушиватель для ```OnDataChannelCreated``` события, выполните следующие действия.
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Чтобы получать уведомления при получении данных, зарегистрируйтесь в ```OnDataReceived``` событии для объекта, ```IDataChannel``` предоставленного ```OnDataChannelCreated``` обработчиком. Зарегистрируйтесь в ```OnClosed``` событии, чтобы получать уведомления при закрытии канала данных.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Отправка данных

Чтобы отправить данные через пользовательский канал данных, используйте ```IDataChannel::SendData()``` метод. Первый параметр представляет собой ```winrt::array_view<const uint8_t>``` данные, которые должны быть отправлены. Второй параметр указывает, куда следует повторно отправить данные, пока другая сторона не подтвердит получение. 

>[!IMPORTANT]
>В случае неудачных условий сети один и тот же пакет данных может быть доставлен более одного раза. Получающий код должен иметь возможность справиться с этой ситуацией.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Закрытие пользовательского канала данных

Чтобы закрыть пользовательский канал данных, используйте ```IDataChannel::Close()``` метод. Обе стороны будут уведомлены ```OnClosed``` событием после закрытия пользовательского канала данных.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>См. также:
* [Обзор удаленного взаимодействия с holographic](holographic-remoting-overview.md)
* [создание удаленного приложения holographic с удаленным взаимодействием с помощью Windows Mixed Reality api](holographic-remoting-create-remote-wmr.md)
* [Создание удаленного приложения holographic с удаленным взаимодействием с помощью API-интерфейсов Опенкср](holographic-remoting-create-remote-openxr.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)