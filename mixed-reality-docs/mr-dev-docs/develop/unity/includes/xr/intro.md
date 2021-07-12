---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603720"
---
# <a name="openxr"></a>[<span data-ttu-id="6cc06-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="6cc06-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6cc06-102">Подключаемый модуль Опенкср для смешанной реальности является **рекомендацией Майкрософт** для **Unity 2020 LTS** или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="6cc06-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="6cc06-103">По мере разработки новых функций в будущем они будут включены только в подключаемый модуль Mixed Reality Опенкср.</span><span class="sxs-lookup"><span data-stu-id="6cc06-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="6cc06-104">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="6cc06-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="6cc06-105">это позволяет написать код райкастинг, который затем охватывает HoloLens 2 и аркоре/ARKit phones and планшетные пк.</span><span class="sxs-lookup"><span data-stu-id="6cc06-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6cc06-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6cc06-106">Prerequisites</span></span> 

* <span data-ttu-id="6cc06-107">новейшие [средства для разработки HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="6cc06-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="6cc06-108">Последний Unity 2020,3 LTS: Version 2020.3.8 F1 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="6cc06-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="6cc06-109">Рекомендуемые версии пакета</span><span class="sxs-lookup"><span data-stu-id="6cc06-109">Recommended package versions</span></span>

<span data-ttu-id="6cc06-110">в инструкциях на этой странице будет настроены основные пакеты Unity опенкср, необходимые для развертывания HoloLens 2 или Windows Mixed Reality приложений.</span><span class="sxs-lookup"><span data-stu-id="6cc06-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="6cc06-111">Подключаемый модуль Unity Опенкср: версии 1,2 или более поздней</span><span class="sxs-lookup"><span data-stu-id="6cc06-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="6cc06-112">Подключаемый модуль Опенкср для смешанной реальности: версия 1.0.0 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="6cc06-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="6cc06-113">Если в проекте используются следующие пакеты, необходимо убедиться, что используются по крайней мере перечисленные ниже минимальные версии.</span><span class="sxs-lookup"><span data-stu-id="6cc06-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="6cc06-114">МРТК: версия 2.7.2 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="6cc06-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="6cc06-115">AR Foundation: версия 4.1.1 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="6cc06-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="6cc06-116">Универсальный конвейер отрисовки (URP): версия 10.5.1 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="6cc06-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="6cc06-117">Пространственные привязки Azure: версии 2,10 или более поздней</span><span class="sxs-lookup"><span data-stu-id="6cc06-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="6cc06-118">Удаленная визуализация Azure: версия 1.0.15 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="6cc06-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="6cc06-119">если вы создаете приложения VR на Windows компьютере, подключаемый модуль Mixed Reality опенкср не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="6cc06-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="6cc06-120">однако необходимо установить подключаемый модуль, если вы настраиваете входные привязки для контроллеров HP reverb G2 или создаете приложения, работающие на обеих гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="6cc06-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="6cc06-121">Windows XR</span><span class="sxs-lookup"><span data-stu-id="6cc06-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="6cc06-122">корпорация майкрософт не рекомендует использовать подключаемый модуль Windows XR для новых проектов в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="6cc06-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="6cc06-123">Вместо этого следует использовать подключаемый модуль Mixed Reality Опенкср.</span><span class="sxs-lookup"><span data-stu-id="6cc06-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="6cc06-124">Однако, если вы используете Unity 2019 и вам требуется AR Foundation 2,0 для совместимости с устройствами Аркоре/ARKit, этот подключаемый модуль обеспечивает такую поддержку.</span><span class="sxs-lookup"><span data-stu-id="6cc06-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc06-125">Использование этого подключаемого модуля в Unity 2019 несовместимо с пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="6cc06-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="6cc06-126">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="6cc06-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="6cc06-127">Если вы по-прежнему используете **Unity 2019** или более раннюю версию, корпорация Майкрософт рекомендует использовать **встроенную поддержку XR**.</span><span class="sxs-lookup"><span data-stu-id="6cc06-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="6cc06-128">хотя модуль Windows XR работает в unity 2019, не рекомендуется, так как этот подключаемый модуль несовместим с пространственными привязками Azure в unity 2019.</span><span class="sxs-lookup"><span data-stu-id="6cc06-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="6cc06-129">При запуске нового проекта рекомендуется [установить Unity 2020 вместо него](../../choosing-unity-version.md) и использовать подключаемый модуль Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="6cc06-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>