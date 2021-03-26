---
title: Пакеты UDP в приложениях UWP для Unity
description: Узнайте, как настроить приложение Unity UWP для отправки и получения UDP-пакетов по защищенной сети.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, пакеты UDP, сокет, клиентский сервер, конечная точка, сеть, удаленный компьютер, датаграмсоккет, пример, .NET
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550524"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Пакеты UDP в приложениях UWP для Unity

Вы можете настроить приложения Unity универсальная платформа Windows (UWP) для получения UDP-пакетов с помощью клиента сокета UDP и сервера. Сокеты UDP не поддерживают подключение на обеих конечных точках, поэтому они являются быстрым и простым решением для работы в сети между удаленными компьютерами. Однако вы несете ответственность за проверку того, что пакеты передаются в назначение, так как сокеты UDP не делают это автоматически.

## <a name="setup"></a>Настройка

Откройте проект HoloLens manifest.jsв файле и убедитесь, что вы включили:
* **Интернет (клиент & сервер)** 
* **Частные сети (клиент & Server)**.

## <a name="build-your-socket-client-and-server"></a>Создание клиента и сервера сокета 

Следуйте инструкциям по [созданию базового клиента и сервера сокета UDP](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Вы будете использовать класс [датаграмсоккет](/uwp/api/Windows.Networking.Sockets.DatagramSocket) для отправки и получения данных по протоколу UDP и формирования эхо-клиента и сервера. Мы также рекомендуем ознакомиться с другими разделами, посвященными этой статье, так как они применяются к более специализированным и сложным вариантам использования. 

> [!IMPORTANT]
> Если при отправке UDP-пакетов с компьютера на компьютер возникают проблемы, убедитесь, что в сети разрешены эти операции. Если сеть блокирует пакеты UDP каким-либо образом, устройство HoloLens не сможет прослушивать их.

Полный пример приложения Датаграмсоккет UDP можно скачать по ссылке ниже:

> [!div class="nextstepaction"]
> [Установка средств](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>См. также статью 
* [Эксперименты с общими голограммами, многоадресность хранилища BLOB-объектов Azure и UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)