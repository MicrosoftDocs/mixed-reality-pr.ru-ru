---
ms.openlocfilehash: 2a2dcb6ec9133eb5efa0dc04e4d757cabd48461a
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107327144"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="db1bb-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="db1bb-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="db1bb-102">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="db1bb-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="db1bb-104">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="db1bb-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="db1bb-106">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="db1bb-106">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="db1bb-108">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="db1bb-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="db1bb-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="db1bb-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="db1bb-111">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="db1bb-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="db1bb-113">В окне параметров сборки щелкните элемент **Universal Windows Platform** (Универсальная платформа Windows). Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="db1bb-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="db1bb-114">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="db1bb-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="db1bb-115">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="db1bb-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="db1bb-116">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="db1bb-116">Set **Build Type** to **D3D**</span></span>
4.  <span data-ttu-id="db1bb-117">Задайте для параметра **Minimum Platform Version** (Минимальная версия платформы) значение **10.0.18362**.</span><span class="sxs-lookup"><span data-stu-id="db1bb-117">Set **Minimum Platform Version** to **10.0.18362**</span></span>
5.  <span data-ttu-id="db1bb-118">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="db1bb-118">Set **UWP SDK** to **Latest installed**</span></span>
6.  <span data-ttu-id="db1bb-119">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="db1bb-119">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
7.  <span data-ttu-id="db1bb-120">Нажмите кнопку Switch Platform (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="db1bb-120">Click the Switch Platform button</span></span>


![Окно параметров сборки Unity с заданным параметром Universal Windows Platform (Универсальная платформа Windows)](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="db1bb-122">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="db1bb-122">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="db1bb-123">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="db1bb-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="db1bb-124">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="db1bb-124">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="db1bb-126">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="db1bb-126">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="db1bb-128">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="db1bb-128">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="db1bb-130">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="db1bb-130">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)
