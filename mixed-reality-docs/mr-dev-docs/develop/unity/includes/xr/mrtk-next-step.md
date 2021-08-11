---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202802"
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