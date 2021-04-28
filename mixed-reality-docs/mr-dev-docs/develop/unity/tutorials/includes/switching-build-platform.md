---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984407"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="26690-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="26690-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="26690-102">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="26690-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="26690-104">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="26690-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="26690-106">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="26690-106">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="26690-108">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="26690-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="26690-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="26690-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="26690-111">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="26690-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="26690-113">В окне параметров сборки щелкните элемент **Universal Windows Platform** (Универсальная платформа Windows). Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="26690-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="26690-114">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="26690-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="26690-115">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="26690-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="26690-116">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="26690-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="26690-117">Задайте для параметра **Target SDK Version** (Целевая версия пакета SDK) значение **Latest Installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="26690-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="26690-118">Задайте для параметра **Minimum Platform Version** (Минимальная версия платформы) значение **10.0.18362**.</span><span class="sxs-lookup"><span data-stu-id="26690-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="26690-119">Задайте для параметра **Visual Studio Version** (Версия Visual Studio) значение **Latest Installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="26690-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="26690-120">Задайте для параметра **Build and Run on** (Устройство для сборки и выполнения) значение **USB Device** (USB-устройство).</span><span class="sxs-lookup"><span data-stu-id="26690-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="26690-121">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="26690-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="26690-122">Нажмите кнопку Switch Platform (Сменить платформу).</span><span class="sxs-lookup"><span data-stu-id="26690-122">Click the Switch Platform button</span></span>


![Окно параметров сборки Unity с заданным параметром Universal Windows Platform (Универсальная платформа Windows)](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="26690-124">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="26690-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="26690-125">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="26690-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="26690-126">В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="26690-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="26690-128">В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):</span><span class="sxs-lookup"><span data-stu-id="26690-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="26690-130">Подождите, пока Unity переключит платформу:</span><span class="sxs-lookup"><span data-stu-id="26690-130">Wait for Unity to finish switching the platform:</span></span>

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="26690-132">Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="26690-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)
