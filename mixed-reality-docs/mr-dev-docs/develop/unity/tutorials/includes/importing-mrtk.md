---
ms.openlocfilehash: 7c86356a960929839f36cf326c5dd1a1005e64d2
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984298"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="373c9-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="373c9-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="373c9-102">После открытия **MixedRealityFeatureTool** щелкните кнопку запуска, чтобы начать работу с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="373c9-102">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![Окно Mixed RealityFeatureTool для подключаемого модуля Windows XR](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="373c9-104">Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="373c9-104">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Окно MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="373c9-106">Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать последнюю версию MRTK. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="373c9-106">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Выбор Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)


<span data-ttu-id="373c9-108">Вам также нужно указать расположение целевого проекта Unity, чтобы указать **путь к проекту**. Щелкните **три точки** рядом с полем Project path (Путь к проекту) и перейдите в обозревателе к папке проекта, например _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="373c9-108">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="373c9-109">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="373c9-109">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="373c9-110">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="373c9-110">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="373c9-111">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="373c9-111">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Проверка Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="373c9-113">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="373c9-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Утверждение Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="373c9-115">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="373c9-115">Unity 2020 + OpenXR</span></span>](#tab/openxr)
<span data-ttu-id="373c9-116">Слева в нижнем углу окна щелкните символ шестеренки, чтобы открыть меню параметров.</span><span class="sxs-lookup"><span data-stu-id="373c9-116">In the bottom left hand of the window, click on the gear symbol to open the settings menu.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="373c9-118">В разделе **Feature Settings** (Параметры функций) установите флажок **Include preview releases** (Включить выпуски предварительных версий) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="373c9-118">Under **Feature Settings**, check the **Include preview releases** box and then click the **OK** button.</span></span>

![Окно параметров MixedRealityFeatureTool](../images/mrft-settings.png)

> [!NOTE]
><span data-ttu-id="373c9-120">Если параметр включения выпусков предварительных версий не отображается, убедитесь, что вы используете последнюю версию MR Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="373c9-120">If you do not see an option to include preview releases, make sure you're using the latest version of the MR Feature Tool.</span></span>

<span data-ttu-id="373c9-121">Теперь, когда параметры настроены, щелкните **Start** (Запуск), чтобы приступить к работе с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="373c9-121">Now that your settings are configured, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![Экран запуска Mixed Reality Feature Tool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="373c9-123">Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="373c9-123">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>
<span data-ttu-id="373c9-124">Установите флажок **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать необходимую версию MRTK. Для этой серии руководств выберите последнюю **предварительную версию пакета 2.7**.</span><span class="sxs-lookup"><span data-stu-id="373c9-124">Check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select the latest **2.7 preview package**.</span></span>

![Окно Mixed RealityFeatureTool для Unity 2020 и OpenXR](../images/mrft-mrtk.png)

<span data-ttu-id="373c9-126">В раскрывающемся списке **Platform Support** (Поддержка платформ) выберите **Mixed Reality OpenXR Plugin** (Подключаемый модуль Mixed Reality OpenXR).</span><span class="sxs-lookup"><span data-stu-id="373c9-126">Under the **Platform Support** dropdown, select **Mixed Reality OpenXR Plugin**.</span></span> <span data-ttu-id="373c9-127">Обязательно выберите в раскрывающемся списке последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="373c9-127">Make sure the latest version is selected in the dropdown.</span></span>
<span data-ttu-id="373c9-128">![Выбор подключаемого модуля Смешанной реальности OpenXR](../images/mrft-openxr.png)</span><span class="sxs-lookup"><span data-stu-id="373c9-128">![Selecting Mixed Reality OpenXR Plugin](../images/mrft-openxr.png)</span></span>

<span data-ttu-id="373c9-129">Нажмите кнопку **Get features** (Получить компоненты), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="373c9-129">Click on the **Get features** button to download the selected packages.</span></span>

<span data-ttu-id="373c9-130">Вам также нужно указать расположение целевого проекта Unity, чтобы указать **путь к проекту**. Щелкните **три точки** рядом с полем Project path (Путь к проекту) и перейдите в обозревателе к папке проекта, например _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="373c9-130">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="373c9-131">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="373c9-131">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="373c9-132">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="373c9-132">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="373c9-133">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="373c9-133">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Проверка Mixed Reality Foundation](../images/mrft-openxr-validate2.png)

<span data-ttu-id="373c9-135">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="373c9-135">Click on the **Approve** button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Утверждение Mixed Reality Foundation](../images/mrft-openxr-import.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="373c9-137">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="373c9-137">Legacy WSA</span></span>](#tab/wsa)
<span data-ttu-id="373c9-138">После открытия **MixedRealityFeatureTool** щелкните кнопку запуска, чтобы начать работу с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="373c9-138">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool для устаревшей версии WSA](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="373c9-140">Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="373c9-140">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Окно MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="373c9-142">Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать последнюю версию MRTK. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="373c9-142">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Выбор Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="373c9-144">Вам также нужно указать расположение целевого проекта Unity, чтобы указать **путь к проекту**. Щелкните **три точки** рядом с полем Project path (Путь к проекту) и перейдите в обозревателе к папке проекта, например _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="373c9-144">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="373c9-145">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="373c9-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="373c9-146">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="373c9-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="373c9-147">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="373c9-147">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Проверка Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="373c9-149">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="373c9-149">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Утверждение Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

