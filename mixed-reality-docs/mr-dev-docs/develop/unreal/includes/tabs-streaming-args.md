---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855889"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="a0c3e-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a0c3e-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="a0c3e-102">Параметр</span><span class="sxs-lookup"><span data-stu-id="a0c3e-102">Option</span></span> | <span data-ttu-id="a0c3e-103">Описание</span><span class="sxs-lookup"><span data-stu-id="a0c3e-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="a0c3e-104">Принимает IP-адрес (и необязательный порт) для подключения к устройству HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="a0c3e-105">Если порт не указан, используется значение по умолчанию 8265.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="a0c3e-106">(Необязательно) Значение по умолчанию: 8000.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-106">(optional) Default 8000.</span></span> <span data-ttu-id="a0c3e-107">Максимальная скорость передачи данных по сети (КБ/с).</span><span class="sxs-lookup"><span data-stu-id="a0c3e-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="a0c3e-108">(Необязательно) Запуск сервера прослушивания.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="a0c3e-109">(Необязательно) Принимает порт для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="a0c3e-110">Используется для подключения к компьютеру или виртуальной машины с устройства HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="a0c3e-111">(Не рекомендуется с версии 4.26) Принимает IP-адрес для подключения к устройству HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="a0c3e-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0c3e-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="a0c3e-113">Параметр</span><span class="sxs-lookup"><span data-stu-id="a0c3e-113">Option</span></span> | <span data-ttu-id="a0c3e-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a0c3e-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="a0c3e-115">Принимает IP-адрес (и необязательный порт, 8265 по умолчанию) для подключения к устройству HoloLens 2 или порт, на котором приложение будет прослушивать подключения.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="a0c3e-116">(Необязательно) Использовать аудио с компьютера при удаленном подключении.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="a0c3e-117">(Необязательно) Запуск сервера прослушивания.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="a0c3e-118">(Необязательно) Значение по умолчанию: 8000.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-118">(optional) Default 8000.</span></span> <span data-ttu-id="a0c3e-119">Максимальная скорость передачи данных по сети (КБ/с).</span><span class="sxs-lookup"><span data-stu-id="a0c3e-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="a0c3e-120">(Необязательно) Кодек подключения.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-120">(optional) Connection codec</span></span>  |