---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103909"
---
# <a name="openxr"></a>[<span data-ttu-id="16f1e-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="16f1e-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="16f1e-102">Подключаемый модуль Опенкср для смешанной реальности является **рекомендацией Майкрософт** для Unity 2020 LTS или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="16f1e-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="16f1e-103">По мере разработки новых функций в будущем они будут включены только в подключаемый модуль Mixed Reality Опенкср.</span><span class="sxs-lookup"><span data-stu-id="16f1e-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="16f1e-104">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="16f1e-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="16f1e-105">Это позволяет написать райкастингный код, который затем охватывает телефоны и Аркореы HoloLens 2 и ARKit.</span><span class="sxs-lookup"><span data-stu-id="16f1e-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="16f1e-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="16f1e-106">Prerequisites</span></span> 

* <span data-ttu-id="16f1e-107">Новейшие [средства для разработки HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="16f1e-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="16f1e-108">Новейшая версия Unity 2020,3 LTS (рекомендуется 2020.3.8 F1 или выше).</span><span class="sxs-lookup"><span data-stu-id="16f1e-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="16f1e-109">Минимальные версии</span><span class="sxs-lookup"><span data-stu-id="16f1e-109">Minimum versions</span></span>

<span data-ttu-id="16f1e-110">В инструкциях на этой странице будет настроены новейшие и максимальные требования Unity и Опенкср, перечисленные ниже.</span><span class="sxs-lookup"><span data-stu-id="16f1e-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="16f1e-111">Последний подключаемый модуль Unity Опенкср (рекомендуется 1,2 или более поздней версии)</span><span class="sxs-lookup"><span data-stu-id="16f1e-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="16f1e-112">Последняя версия подключаемого модуля Опенкср смешанной реальности (рекомендуется использовать версию 1.0.0 или более позднюю)</span><span class="sxs-lookup"><span data-stu-id="16f1e-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="16f1e-113">Если в проекте используется МРТК, рекомендуется использовать версию 2.7.2 или более позднюю.</span><span class="sxs-lookup"><span data-stu-id="16f1e-113">If your project uses MRTK, we recommend version 2.7.2 or later</span></span>
* <span data-ttu-id="16f1e-114">Если в проекте используется пакет универсального конвейера отрисовки (URP), рекомендуется использовать версию 10.5.1 или более позднюю.</span><span class="sxs-lookup"><span data-stu-id="16f1e-114">If your project uses Universal Render Pipeline (URP) package, we recommend version 10.5.1 or later</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="16f1e-115">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="16f1e-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="16f1e-116">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="16f1e-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="16f1e-117">XR Windows</span><span class="sxs-lookup"><span data-stu-id="16f1e-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="16f1e-118">Корпорация Майкрософт не рекомендует использовать подключаемый модуль Windows XR для новых проектов в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="16f1e-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="16f1e-119">Однако, если вы используете Unity 2019 и вам требуется AR Foundation 2,0 для совместимости с устройствами Аркоре/ARKit, этот подключаемый модуль обеспечивает такую поддержку.</span><span class="sxs-lookup"><span data-stu-id="16f1e-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16f1e-120">Использование этого подключаемого модуля в Unity 2019 не поддерживает пространственные привязки Azure.</span><span class="sxs-lookup"><span data-stu-id="16f1e-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="16f1e-121">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="16f1e-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="16f1e-122">Если вы по-прежнему используете Unity 2019 или более раннюю версию, корпорация Майкрософт рекомендует использовать встроенную поддержку XR.</span><span class="sxs-lookup"><span data-stu-id="16f1e-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="16f1e-123">Хотя подключаемый модуль Windows XR работает на Unity 2019, не рекомендуется, так как пространственные привязки Azure не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="16f1e-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>