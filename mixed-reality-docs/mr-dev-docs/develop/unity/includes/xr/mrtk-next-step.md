---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603723"
---
# <a name="openxr"></a>[<span data-ttu-id="c4529-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c4529-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="c4529-102">Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:</span><span class="sxs-lookup"><span data-stu-id="c4529-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c4529-103">Настройка нового проекта Опенкср с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="c4529-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="c4529-104">При обновлении **существующего проекта мртк до опенкср** сначала необходимо обновить MRTK-Unity до последней версии (2.7.2 или более поздней версии), чтобы получить основные исправления для совместимости с подключаемым модулем Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="c4529-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="c4529-105">Используйте [средство "функция смешанной реальности](../../welcome-to-mr-feature-tool.md) " для обновления до последней версии мртк, а затем следуйте инструкциям по [настройке опенкср вручную ниже](#manual-setup-without-mrtk).</span><span class="sxs-lookup"><span data-stu-id="c4529-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="c4529-106">[Более подробные сведения о переносе существующего проекта мртк в опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="c4529-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="c4529-107">При обновлении предыдущей версии МРТК, более ранней, чем **2.5.3**, убедитесь, что в файле **Assets/микседреалититулкит. generated/link.xml** указана следующая строка:</span><span class="sxs-lookup"><span data-stu-id="c4529-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="c4529-108">Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="c4529-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="c4529-109">Windows XR</span><span class="sxs-lookup"><span data-stu-id="c4529-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="c4529-110">Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:</span><span class="sxs-lookup"><span data-stu-id="c4529-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c4529-111">настройка нового проекта Windows XR с помощью мртк</span><span class="sxs-lookup"><span data-stu-id="c4529-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="c4529-112">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="c4529-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="c4529-113">Чтобы приступить к работе с **новым проектом Unity** с помощью мртк, начните с шага 2 в руководстве по мртк:</span><span class="sxs-lookup"><span data-stu-id="c4529-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c4529-114">Настройка нового проекта XR прежних версий с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="c4529-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)