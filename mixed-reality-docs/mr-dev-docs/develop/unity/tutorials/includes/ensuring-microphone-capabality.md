---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097071"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="e8f84-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="e8f84-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="e8f84-102">Включение поддержки микрофона и добавление поставщика данных для ввода речи</span><span class="sxs-lookup"><span data-stu-id="e8f84-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="e8f84-103">В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:</span><span class="sxs-lookup"><span data-stu-id="e8f84-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Включение поддержки микрофона](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e8f84-105">Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона.</span><span class="sxs-lookup"><span data-stu-id="e8f84-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="e8f84-106">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="e8f84-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="e8f84-107">В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):</span><span class="sxs-lookup"><span data-stu-id="e8f84-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="e8f84-108">Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="e8f84-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Поставщик данных для добавления новых голосовых команд](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="e8f84-110">Укажите **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** в поле **Type** (Тип) нового поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="e8f84-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Параметры добавления новых речевых команд](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="e8f84-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="e8f84-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="e8f84-113">Включение поддержки микрофона и добавление поставщика данных для ввода речи</span><span class="sxs-lookup"><span data-stu-id="e8f84-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="e8f84-114">В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:</span><span class="sxs-lookup"><span data-stu-id="e8f84-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Включение поддержки микрофона для OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e8f84-116">Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона.</span><span class="sxs-lookup"><span data-stu-id="e8f84-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="e8f84-117">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="e8f84-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="e8f84-118">В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):</span><span class="sxs-lookup"><span data-stu-id="e8f84-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="e8f84-119">Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="e8f84-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Добавление новых речевых команд для OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="e8f84-121">Укажите **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** в поле **Type** (Тип) нового поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="e8f84-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Параметры добавления новых речевых команд для OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="e8f84-123">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="e8f84-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="e8f84-124">Активация функции микрофона</span><span class="sxs-lookup"><span data-stu-id="e8f84-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="e8f84-125">В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:</span><span class="sxs-lookup"><span data-stu-id="e8f84-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Включение поддержки микрофона](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e8f84-127">Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона.</span><span class="sxs-lookup"><span data-stu-id="e8f84-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="e8f84-128">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="e8f84-128">However, if it is not enabled, make sure you enable it now.</span></span>
