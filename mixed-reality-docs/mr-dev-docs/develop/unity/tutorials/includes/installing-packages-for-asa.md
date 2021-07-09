---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175559"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="d559a-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="d559a-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d559a-102">В меню Unity выберите пункт **Window** (Окно) > **Package Manager** (Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем убедитесь, что установлена версия **AR Foundation** > **4.1.7**.</span><span class="sxs-lookup"><span data-stu-id="d559a-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d559a-104">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="d559a-104">Importing the tutorial assets</span></span>

<span data-ttu-id="d559a-105">Добавьте пакет SDK AzurespatialAnchors версии 2.10 в свой проект с помощью этого [руководства](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="d559a-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="d559a-106">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="d559a-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="d559a-107">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="d559a-107">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* [<span data-ttu-id="d559a-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d559a-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="d559a-109">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d559a-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="d559a-111">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе  [Импорт ресурсов для руководства](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="d559a-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="d559a-112">Подключаемый модуль Unity 2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="d559a-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="d559a-113">В меню Unity щелкните **Window** (Окно) > **Package Manager** (Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем выберите версию **AR Foundation > 4.0.12** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="d559a-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d559a-115">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="d559a-115">Importing the tutorial assets</span></span>

<span data-ttu-id="d559a-116">Добавьте пакет SDK AzurespatialAnchors версии 2.10 в свой проект с помощью этого [руководства](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="d559a-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="d559a-117">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="d559a-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="d559a-118">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="d559a-118">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* [<span data-ttu-id="d559a-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d559a-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="d559a-120">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d559a-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="d559a-122">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе  [Импорт ресурсов для руководства](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="d559a-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d559a-123">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="d559a-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="d559a-124">В меню Unity щелкните **Window** (Окно) > **Package Manager** (Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем выберите версию **AR Foundation  > 3.1.3** и нажмите кнопку **Install** (Установить) для установки пакета.</span><span class="sxs-lookup"><span data-stu-id="d559a-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d559a-126">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="d559a-126">Importing the tutorial assets</span></span>

<span data-ttu-id="d559a-127">Добавьте пакет SDK AzurespatialAnchors версии 2.7.2 в свой проект с помощью этого [руководства](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="d559a-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="d559a-128">Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:</span><span class="sxs-lookup"><span data-stu-id="d559a-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="d559a-129">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);</span><span class="sxs-lookup"><span data-stu-id="d559a-129">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>
* [<span data-ttu-id="d559a-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackagee</span><span class="sxs-lookup"><span data-stu-id="d559a-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="d559a-131">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d559a-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="d559a-133">Если вы видите предупреждение CS0618 о том, что параметр WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) устарел, его можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="d559a-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="d559a-134">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе  [Импорт ресурсов для руководства](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="d559a-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
