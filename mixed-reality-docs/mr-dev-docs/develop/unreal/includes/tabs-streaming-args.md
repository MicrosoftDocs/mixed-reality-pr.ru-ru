---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855889"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Параметр | Описание |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Принимает IP-адрес (и необязательный порт) для подключения к устройству HoloLens 2. Если порт не указан, используется значение по умолчанию 8265. |
| `-RemotingBitrate=<bitrate>` | (Необязательно) Значение по умолчанию: 8000. Максимальная скорость передачи данных по сети (КБ/с). |
| `-HoloLensRemotingListen` | (Необязательно) Запуск сервера прослушивания. |
| `-HoloLensRemotingListenPort=<port>` | (Необязательно) Принимает порт для прослушивания. Используется для подключения к компьютеру или виртуальной машины с устройства HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (Не рекомендуется с версии 4.26) Принимает IP-адрес для подключения к устройству HoloLens 1. |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Параметр | Описание |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Принимает IP-адрес (и необязательный порт, 8265 по умолчанию) для подключения к устройству HoloLens 2 или порт, на котором приложение будет прослушивать подключения. |
| `-EnableAudio` | (Необязательно) Использовать аудио с компьютера при удаленном подключении.  |
| `-Listen` | (Необязательно) Запуск сервера прослушивания. |
| `-RemotingBitrate=<bitrate>` | (Необязательно) Значение по умолчанию: 8000. Максимальная скорость передачи данных по сети (КБ/с). |
| `-RemotingCodec=<codec>` | (Необязательно) Кодек подключения.  |