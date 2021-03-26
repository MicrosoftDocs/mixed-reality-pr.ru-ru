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
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="44428-104">Пакеты UDP в приложениях UWP для Unity</span><span class="sxs-lookup"><span data-stu-id="44428-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="44428-105">Вы можете настроить приложения Unity универсальная платформа Windows (UWP) для получения UDP-пакетов с помощью клиента сокета UDP и сервера.</span><span class="sxs-lookup"><span data-stu-id="44428-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="44428-106">Сокеты UDP не поддерживают подключение на обеих конечных точках, поэтому они являются быстрым и простым решением для работы в сети между удаленными компьютерами.</span><span class="sxs-lookup"><span data-stu-id="44428-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="44428-107">Однако вы несете ответственность за проверку того, что пакеты передаются в назначение, так как сокеты UDP не делают это автоматически.</span><span class="sxs-lookup"><span data-stu-id="44428-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="44428-108">Настройка</span><span class="sxs-lookup"><span data-stu-id="44428-108">Setup</span></span>

<span data-ttu-id="44428-109">Откройте проект HoloLens manifest.jsв файле и убедитесь, что вы включили:</span><span class="sxs-lookup"><span data-stu-id="44428-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="44428-110">**Интернет (клиент & сервер)**</span><span class="sxs-lookup"><span data-stu-id="44428-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="44428-111">**Частные сети (клиент & Server)**.</span><span class="sxs-lookup"><span data-stu-id="44428-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="44428-112">Создание клиента и сервера сокета</span><span class="sxs-lookup"><span data-stu-id="44428-112">Build your socket client and server</span></span> 

<span data-ttu-id="44428-113">Следуйте инструкциям по [созданию базового клиента и сервера сокета UDP](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="44428-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="44428-114">Вы будете использовать класс [датаграмсоккет](/uwp/api/Windows.Networking.Sockets.DatagramSocket) для отправки и получения данных по протоколу UDP и формирования эхо-клиента и сервера.</span><span class="sxs-lookup"><span data-stu-id="44428-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="44428-115">Мы также рекомендуем ознакомиться с другими разделами, посвященными этой статье, так как они применяются к более специализированным и сложным вариантам использования.</span><span class="sxs-lookup"><span data-stu-id="44428-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="44428-116">Если при отправке UDP-пакетов с компьютера на компьютер возникают проблемы, убедитесь, что в сети разрешены эти операции.</span><span class="sxs-lookup"><span data-stu-id="44428-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="44428-117">Если сеть блокирует пакеты UDP каким-либо образом, устройство HoloLens не сможет прослушивать их.</span><span class="sxs-lookup"><span data-stu-id="44428-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="44428-118">Полный пример приложения Датаграмсоккет UDP можно скачать по ссылке ниже:</span><span class="sxs-lookup"><span data-stu-id="44428-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="44428-119">Установка средств</span><span class="sxs-lookup"><span data-stu-id="44428-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="44428-120">См. также статью</span><span class="sxs-lookup"><span data-stu-id="44428-120">See also</span></span> 
* [<span data-ttu-id="44428-121">Эксперименты с общими голограммами, многоадресность хранилища BLOB-объектов Azure и UDP</span><span class="sxs-lookup"><span data-stu-id="44428-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)