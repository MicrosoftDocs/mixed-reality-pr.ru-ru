---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603723"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:

> [!div class="nextstepaction"]
> [Настройка нового проекта Опенкср с помощью МРТК](../../tutorials/mr-learning-base-02.md?tabs=openxr)

При обновлении **существующего проекта мртк до опенкср** сначала необходимо обновить MRTK-Unity до последней версии (2.7.2 или более поздней версии), чтобы получить основные исправления для совместимости с подключаемым модулем Mixed Reality опенкср.  Используйте [средство "функция смешанной реальности](../../welcome-to-mr-feature-tool.md) " для обновления до последней версии мртк, а затем следуйте инструкциям по [настройке опенкср вручную ниже](#manual-setup-without-mrtk). [Более подробные сведения о переносе существующего проекта мртк в опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.

> [!NOTE]
> При обновлении предыдущей версии МРТК, более ранней, чем **2.5.3**, убедитесь, что в файле **Assets/микседреалититулкит. generated/link.xml** указана следующая строка:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:

> [!div class="nextstepaction"]
> [настройка нового проекта Windows XR с помощью мртк](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Устаревшая смешанная реальность](#tab/legacy)

Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:

> [!div class="nextstepaction"]
> [Настройка нового проекта XR прежних версий с помощью МРТК](../../tutorials/mr-learning-base-02.md?tabs=wsa)