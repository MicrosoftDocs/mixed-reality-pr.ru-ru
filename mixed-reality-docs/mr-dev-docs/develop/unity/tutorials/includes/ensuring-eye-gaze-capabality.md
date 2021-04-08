---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097741"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="9c0ee-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="9c0ee-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="9c0ee-102">Включение поддержки ввода данных с помощью взгляда и добавление соответствующего поставщика данных</span><span class="sxs-lookup"><span data-stu-id="9c0ee-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="9c0ee-103">В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Окно конфигурации проекта MRTK в Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9c0ee-105">Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), при настройке проекта Unity в начале работы с этой серией руководств.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="9c0ee-106">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="9c0ee-107">В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):</span><span class="sxs-lookup"><span data-stu-id="9c0ee-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="9c0ee-108">Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Добавление поставщика данных 1 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="9c0ee-110">Укажите **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** в поле **Type** (Тип) нового поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Добавление поставщика данных 2 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="9c0ee-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="9c0ee-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="9c0ee-113">Включение поддержки ввода данных с помощью взгляда и добавление соответствующего поставщика данных</span><span class="sxs-lookup"><span data-stu-id="9c0ee-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="9c0ee-114">В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):</span><span class="sxs-lookup"><span data-stu-id="9c0ee-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="9c0ee-115">Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Добавление поставщика данных 1 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="9c0ee-117">Укажите **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** в поле **Type** (Тип) нового поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Добавление поставщика данных 2 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="9c0ee-119">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="9c0ee-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="9c0ee-120">Проверка того, включена ли функция ввода с использованием взгляда</span><span class="sxs-lookup"><span data-stu-id="9c0ee-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="9c0ee-121">В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Окно конфигурации проекта MRTK в Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9c0ee-123">Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), при настройке проекта Unity в начале работы с этой серией руководств.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="9c0ee-124">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="9c0ee-124">However, if it is not enabled, make sure you enable it now.</span></span>
