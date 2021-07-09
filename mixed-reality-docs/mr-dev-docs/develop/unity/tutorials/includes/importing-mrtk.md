---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175736"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8f8f8-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8f8f8-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="8f8f8-102">После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="8f8f8-103">Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="8f8f8-104">После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="8f8f8-105">Затем щелкните **Discover Features** (Обнаружение компонентов).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="8f8f8-106">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="8f8f8-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="8f8f8-107">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="8f8f8-108">Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="8f8f8-109">Папка должна содержать папки ресурсов, пакетов и параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="8f8f8-110">Функции группируются по категориям. чтобы упростить поиск. Щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с набором средств смешанной реальности, и щелкните раскрывающийся список **Platform Support** (Поддержка платформ), чтобы найти пакеты, относящиеся к различным платформам.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="8f8f8-111">Установите флажок **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK 2.7.2**, также укажите **Mixed Reality OpenXR Plugin 1.0.0** и щелкните раскрывающийся список, чтобы выбрать последнюю версию, а затем нажмите кнопку **Get features** (Получить компоненты), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="8f8f8-112">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="8f8f8-113">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="8f8f8-114">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8f8f8-114">Configuring the Unity project</span></span>

<span data-ttu-id="8f8f8-115">После того, как Unity завершит импорт пакета из предыдущего раздела, появится предупреждающее сообщение о перезапуске редактора Unity. Это нужно, чтобы подключить новую систему модулей. Нажмите кнопку **Yes**.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="8f8f8-116">После перезапуска Unity должно появиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="8f8f8-117">В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Открытие окна конфигуратора проекта MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="8f8f8-119">Щелкните **Unity OpenXR Plugin**, чтобы включить управление подключаемым модулем XR и добавить необходимые пакеты в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="8f8f8-120">Добавление подключаемого модуля Unity OpenXR</span><span class="sxs-lookup"><span data-stu-id="8f8f8-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="8f8f8-121">Нажмите кнопку **Show XR Plug-In Management Settings** (Показывать параметры управления подключаемым модулем XR) в конфигураторе проектов MRTK, чтобы импортировать необходимые пакеты Unity для управления модулем XR.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="8f8f8-122">Отображение параметров управления подключаемым модулем XR</span><span class="sxs-lookup"><span data-stu-id="8f8f8-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="8f8f8-123">Откроется **окно параметров проекта**.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="8f8f8-124">В окне параметров проект в разделе **XR Plug-in Management** (Управление подключаемым модулем XR) проверьте, что вы используете параметры универсальной платформы Windows (вкладка с логотипом Windows).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="8f8f8-125">Кроме того, проверьте, что установлен флажок **Initialize XR on Startup** (Инициализировать XR при запуске), а затем установите флажки **OpenXR** и **Microsoft HoloLens feature set** (Набор функций Microsoft HoloLens), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Включение Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="8f8f8-127">После установки флажка OpenXR в окне конфигуратора проекта MRTK будет отображаться обновленное сообщение с кнопкой **Apply Settings** (Приметь параметры).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="8f8f8-128">Нажмите кнопку **Apply Settings** (Приметь параметры).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-128">Click **Apply Settings** button.</span></span> 

![Окно параметров проекта 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="8f8f8-130">При нажатии кнопки Apply Settings (Применить параметры) это сообщение об ошибке может появиться в консоли.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="8f8f8-131">Если это единственная ошибка или ошибки нет, можно продолжать работу.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-131">You can proceed if this is the only error or there is no error.</span></span>

![Сообщение об ошибке удаленного взаимодействия OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="8f8f8-133">Чтобы проверить конфигурацию OpenXR, щелкните **OpenXR** в разделе **XR Plug-in Management** (Управление подключаемыми модулями XR) и проверьте следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="8f8f8-134">Режим глубины при отправке: **16-битная глубина**</span><span class="sxs-lookup"><span data-stu-id="8f8f8-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="8f8f8-135">Профили взаимодействия: **Microsoft Hand Interaction Profile** (профиль взаимодействия с помощью рук)</span><span class="sxs-lookup"><span data-stu-id="8f8f8-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Окно параметров проекта 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="8f8f8-137">Уменьшать разрядность глубины до 16 битов необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="8f8f8-138">Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="8f8f8-139">В окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) нажмите кнопку **Next** (Далее), а затем кнопку **Apply**, чтобы применить параметры.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="8f8f8-140">Если вы закрыли окно, откройте его вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Окно параметров проекта 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Окно параметров проекта 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="8f8f8-143">После нажатия кнопки Apply (Применить) Unity попытается перезапуститься, чтобы применить параметры входной системы. Нажмите кнопку **Apply** (Применить), чтобы перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="8f8f8-144">Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="8f8f8-144">Configure additional project settings</span></span>

<span data-ttu-id="8f8f8-145">В меню Unity выберите **Edit** > **Project Settings...** (Правка > Параметры проекта…), чтобы открыть окно параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="8f8f8-146">В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Раздел параметров публикации Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="8f8f8-149">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="8f8f8-150">Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="8f8f8-151">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="8f8f8-152">Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8f8f8-153">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="8f8f8-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="8f8f8-154">После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="8f8f8-155">Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="8f8f8-156">После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="8f8f8-157">Затем щелкните **Discover Features** (Обнаружение компонентов).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="8f8f8-158">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="8f8f8-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="8f8f8-159">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="8f8f8-160">Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="8f8f8-161">Папка должна содержать папки ресурсов, пакетов и параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="8f8f8-162">Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="8f8f8-163">Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK версии 2.7.0**. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="8f8f8-164">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="8f8f8-165">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="8f8f8-166">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8f8f8-166">Configuring the Unity project</span></span>

<span data-ttu-id="8f8f8-167">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="8f8f8-168">В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Открытие средства конфигуратора MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="8f8f8-170">Щелкните **Built-in Unity Plugin(non-OpenXR)** (Встроенные модуль Unity — не OpenXR), чтобы включить управление подключаемым модулем XR и добавить необходимые пакеты в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="8f8f8-171">Средство конфигуратора MRTK</span><span class="sxs-lookup"><span data-stu-id="8f8f8-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="8f8f8-172">Приведенный выше снимок экрана относится к Unity 2020, если вы используете Unity 2019, выберите **XR SDK/XR Management** (Пакет SDK XR или управление XR).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="8f8f8-173">Нажмите кнопку **Show Settings** (Показать параметры) в конфигураторе проектов MRTK, чтобы импортировать необходимые пакеты Unity для управления модулем XR.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Окно параметров воспроизведения](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="8f8f8-175">Откроется **окно параметров проекта**. В окне параметров проекта в разделе **XR Plug-in Management** (Управление подключаемыми модулями XR). Перейдите в параметры универсальной платформы Windows и проверьте, что установлен флажок **Initialize XR on Startup** (Инициализировать XR при запуске), и установите флажок **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Окно параметров воспроизведения — включение смешанной реальности — xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="8f8f8-177">Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="8f8f8-178">Если этого не произошло, откройте его в меню Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="8f8f8-179">В окне конфигуратора проектов MRTK щелкните **Next** (Далее) откройте раскрывающийся список Audio spatializer, выберите в нем **MS HRTF Spatializer**, а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Конфигуратор проекта MRTK — xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="8f8f8-181">Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="8f8f8-182">Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="8f8f8-183">Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="8f8f8-184">Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="8f8f8-185">Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="8f8f8-186">Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="8f8f8-187">Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="8f8f8-188">Дополнительные сведения см. в <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="8f8f8-189">Чтобы завершить настройку проекта Unity для XRSDK, нажмите кнопку **Next** (Далее), а затем щелкните **Done** (Готово) в окне конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="8f8f8-190">Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="8f8f8-190">Configure additional project settings</span></span>

<span data-ttu-id="8f8f8-191">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="8f8f8-192">В окне Project Settings (Параметры проекта), выберите **XR Plug-in Management (Управление подключаемым модулем XR)**  > **Windows Mixed Reality** > **Runtime Settings (Параметры среды выполнения)** . Затем в раскрывающемся списке **Depth Buffer Format** (Формат буфера глубины) выберите **16-bit depth** (16-битная глубина):</span><span class="sxs-lookup"><span data-stu-id="8f8f8-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Включение 16-разрядной глубины в Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="8f8f8-194">Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="8f8f8-195">Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="8f8f8-196">В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Раздел параметров публикации Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="8f8f8-199">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="8f8f8-200">Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="8f8f8-201">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="8f8f8-202">Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="8f8f8-203">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="8f8f8-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="8f8f8-204">После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="8f8f8-205">Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="8f8f8-206">После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="8f8f8-207">Затем щелкните **Discover Features** (Обнаружение компонентов).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="8f8f8-208">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="8f8f8-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="8f8f8-209">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="8f8f8-210">Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="8f8f8-211">Папка должна содержать папки ресурсов, пакетов и параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="8f8f8-212">Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="8f8f8-213">Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK версии 2.7.0**. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="8f8f8-214">Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="8f8f8-215">Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="8f8f8-216">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8f8f8-216">Configuring the Unity project</span></span>

<span data-ttu-id="8f8f8-217">Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="8f8f8-218">В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="8f8f8-220">Щелкните **Legacy XR**, чтобы включить устаревшие XR и добавить необходимые пакеты в проект.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="8f8f8-222">Нажмите кнопку Next (Далее), чтобы включить параметры конвейера XR для устаревших XR.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Окно настройки MRTK Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="8f8f8-224">В окне конфигуратора проектов MRTK установите флажки для всех параметров, откройте раскрывающийся список **Audio spatializer**, выберите в нем **MS HRTF Spatializer**, а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Окна настройки MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="8f8f8-226">Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="8f8f8-227">Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="8f8f8-228">Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="8f8f8-229">Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="8f8f8-230">Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).</span><span class="sxs-lookup"><span data-stu-id="8f8f8-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="8f8f8-231">Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="8f8f8-232">Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="8f8f8-233">Дополнительные сведения см. в <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="8f8f8-234">Чтобы завершить настройку проекта Unity для Legacy XR, нажмите кнопку **Next** (Далее), а затем щелкните **Done** (Готово) в окне конфигуратора проекта MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="8f8f8-235">Настройка дополнительных параметров проекта</span><span class="sxs-lookup"><span data-stu-id="8f8f8-235">Configure additional project settings</span></span>

<span data-ttu-id="8f8f8-236">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="8f8f8-237">В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):</span><span class="sxs-lookup"><span data-stu-id="8f8f8-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Включение 16-разрядной глубины в Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="8f8f8-239">Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="8f8f8-240">Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="8f8f8-241">В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="8f8f8-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Раздел параметров публикации Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="8f8f8-244">Package name (Имя пакета) — это уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="8f8f8-245">Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="8f8f8-246">Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="8f8f8-247">Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.</span><span class="sxs-lookup"><span data-stu-id="8f8f8-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
