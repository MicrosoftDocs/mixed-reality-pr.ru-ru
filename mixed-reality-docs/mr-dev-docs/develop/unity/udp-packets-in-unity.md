---
title: Пакеты UDP в приложениях UWP для Unity
description: Узнайте, как настроить приложение Unity UWP для отправки и получения UDP-пакетов по защищенной сети.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, пакеты UDP, сокет, клиентский сервер, конечная точка, сеть, удаленный компьютер, датаграмсоккет, пример, .NET
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566985"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="08d6c-104">Пакеты UDP в приложениях UWP для Unity</span><span class="sxs-lookup"><span data-stu-id="08d6c-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="08d6c-105">Вы можете настроить приложения Unity универсальная платформа Windows (UWP) для получения UDP-пакетов с помощью клиента сокета UDP и сервера.</span><span class="sxs-lookup"><span data-stu-id="08d6c-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="08d6c-106">Сокеты UDP не поддерживают подключение на обеих конечных точках, поэтому они являются быстрым и простым решением для работы в сети между удаленными компьютерами.</span><span class="sxs-lookup"><span data-stu-id="08d6c-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="08d6c-107">Однако вы несете ответственность за проверку того, что пакеты передаются в назначение, так как сокеты UDP не делают это автоматически.</span><span class="sxs-lookup"><span data-stu-id="08d6c-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="08d6c-108">Настройка</span><span class="sxs-lookup"><span data-stu-id="08d6c-108">Setup</span></span>

<span data-ttu-id="08d6c-109">Откройте проект HoloLens manifest.jsв файле и убедитесь, что вы включили:</span><span class="sxs-lookup"><span data-stu-id="08d6c-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="08d6c-110">**Интернет (клиент & сервер)**</span><span class="sxs-lookup"><span data-stu-id="08d6c-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="08d6c-111">**Частные сети (клиент & Server)**.</span><span class="sxs-lookup"><span data-stu-id="08d6c-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="08d6c-112">Создание клиента и сервера сокета</span><span class="sxs-lookup"><span data-stu-id="08d6c-112">Build your socket client and server</span></span> 

<span data-ttu-id="08d6c-113">Следуйте инструкциям по [созданию базового клиента и сервера сокета UDP](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="08d6c-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="08d6c-114">Вы будете использовать класс [датаграмсоккет](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) для отправки и получения данных по протоколу UDP и формирования эхо-клиента и сервера.</span><span class="sxs-lookup"><span data-stu-id="08d6c-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="08d6c-115">Мы также рекомендуем ознакомиться с другими разделами, посвященными этой статье, так как они применяются к более специализированным и сложным вариантам использования.</span><span class="sxs-lookup"><span data-stu-id="08d6c-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="08d6c-116">Если при отправке UDP-пакетов с компьютера на компьютер возникают проблемы, убедитесь, что в сети разрешены эти операции.</span><span class="sxs-lookup"><span data-stu-id="08d6c-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="08d6c-117">Если сеть блокирует пакеты UDP каким-либо образом, устройство HoloLens не сможет прослушивать их.</span><span class="sxs-lookup"><span data-stu-id="08d6c-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="08d6c-118">Полный пример приложения Датаграмсоккет UDP можно скачать по ссылке ниже:</span><span class="sxs-lookup"><span data-stu-id="08d6c-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="08d6c-119">Установка средств</span><span class="sxs-lookup"><span data-stu-id="08d6c-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="08d6c-120">См. также статью</span><span class="sxs-lookup"><span data-stu-id="08d6c-120">See also</span></span> 
* [<span data-ttu-id="08d6c-121">Эксперименты с общими голограммами, многоадресность хранилища BLOB-объектов Azure и UDP</span><span class="sxs-lookup"><span data-stu-id="08d6c-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)