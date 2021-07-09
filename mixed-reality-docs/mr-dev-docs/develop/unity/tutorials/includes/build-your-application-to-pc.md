---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392658"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8d22c-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8d22c-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="8d22c-102">1. Переключение платформы сборки</span><span class="sxs-lookup"><span data-stu-id="8d22c-102">1. Switching Build Platform</span></span>

<span data-ttu-id="8d22c-103">В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="8d22c-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8d22c-104">В окне параметров сборки выберите платформу **PC, Mac & Linux Standalone** и нажмите кнопку **Switch Platform** (Переключить платформу), чтобы изменить платформу сборки.</span><span class="sxs-lookup"><span data-stu-id="8d22c-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Переключение платформы сборки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="8d22c-106">Когда Unity переключит платформу, щелкните значок крестика, чтобы закрыть окно параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="8d22c-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="8d22c-107">2. Настройка параметров проекта</span><span class="sxs-lookup"><span data-stu-id="8d22c-107">2. Set the project settings</span></span>

<span data-ttu-id="8d22c-108">В меню Unity выберите пункт **Edit** (Изменить)  >  **Project Settings** (Параметры проекта)  >  **XR Plug-in Management** (Управление подключаемыми модулями XR), убедитесь, что вы на вкладке Windows Standalone, и установите флажок **OpenXR** и **Windows Mixed Reality feature set** (Набор функций Windows Mixed Reality).</span><span class="sxs-lookup"><span data-stu-id="8d22c-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Включение OpenXR и набора функций Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="8d22c-110">В окне Project Settings (Параметры проекта) выберите **OpenXR**, убедитесь, что вы на вкладке Windows Standalone, и измените значение параметра **Depth submission mode** (Режим глубины при отправке) с None на **Depth 16 Bit** (16-битная глубина).</span><span class="sxs-lookup"><span data-stu-id="8d22c-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="8d22c-111">На вкладке профилей взаимодействия добавьте **Eye Gaze Interaction Profile** (Профиль взаимодействия взгляда) и **Microsoft Hand Interaction Profile** (Профиль взаимодействия рук Microsoft), щелкнув значок "+".</span><span class="sxs-lookup"><span data-stu-id="8d22c-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Добавление профиля взаимодействия с помощью взгляда и профиля взаимодействия с помощью рук (Майкрософт)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="8d22c-113">В разделе **Open XR feature groups** (Открыть группы функций XR)  >  **All features** (Все функции) установите флажок **Holographic App Remoting** (Голографическое удаленное взаимодействие через приложение).</span><span class="sxs-lookup"><span data-stu-id="8d22c-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Включение голографического удаленного взаимодействия через приложение](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="8d22c-115">Далее установите флажок **Windows Mixed Reality** и в разделе группы Windows Mixed Reality установите флажок **Holographic App Remoting** (Голографическое удаленное взаимодействие с приложением).</span><span class="sxs-lookup"><span data-stu-id="8d22c-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Включение голографического удаленного взаимодействия с приложением Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="8d22c-117">3. Сборка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8d22c-117">3. Build the Unity Project</span></span>

<span data-ttu-id="8d22c-118">В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="8d22c-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8d22c-119">В окне Build Settings (Параметры сборки) нажмите кнопку \***Add Open Scenes** _ (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены).</span><span class="sxs-lookup"><span data-stu-id="8d22c-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="8d22c-120">В списке Build (Сборка) нажмите кнопку _ \*Build\*\*:</span><span class="sxs-lookup"><span data-stu-id="8d22c-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Окно параметров сборки Unity с добавленной сценой](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="8d22c-122">Выберите подходящее расположение для хранения сборки, например Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="8d22c-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="8d22c-123">Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="8d22c-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="8d22c-124">Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="8d22c-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="8d22c-126">Подождите, пока Unity завершит сборку.</span><span class="sxs-lookup"><span data-stu-id="8d22c-126">Wait for Unity to finish the build process.</span></span>

![Unity выполняет сборку](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="8d22c-128">Дважды щелкните исполняемый файл, чтобы открыть на компьютере приложение голографического удаленного взаимодействия Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="8d22c-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="8d22c-129">Из-за некоторых известных проблем в приложении Holographic Remoting для ПК, созданного как UWP, мы создаем приложение для ПК как Windows Standalone для OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8d22c-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="8d22c-130">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="8d22c-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="8d22c-131">1. Настройка параметров проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="8d22c-131">1. Set the player settings</span></span>

<span data-ttu-id="8d22c-132">В разделе **XR Settings** (Параметры XR) установите флажок **WSA Holographic Remoting Supported** (Поддержка голографического удаленного взаимодействия WSA) и включите функцию голографического удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="8d22c-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Окно параметров смешанной реальности Unity с включенной поддержкой удаленного голографического взаимодействия WSA](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="8d22c-134">2. Создание проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="8d22c-134">2. Build the Unity Project</span></span>

<span data-ttu-id="8d22c-135">В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:</span><span class="sxs-lookup"><span data-stu-id="8d22c-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8d22c-136">В окне Build Settings (Параметры сборки) нажмите кнопку \***Add Open Scenes** _ (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены).</span><span class="sxs-lookup"><span data-stu-id="8d22c-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="8d22c-137">В списке Build (Сборка) нажмите кнопку _ *_Build_*\* (Сборка), чтобы открыть окно Build Universal Windows Platform (Создание приложений универсальной платформы Windows):</span><span class="sxs-lookup"><span data-stu-id="8d22c-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Окно параметров сборки Unity с добавленной сценой](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="8d22c-139">В окне Build Universal Windows Platform (Создание приложений универсальной платформы Windows) выберите подходящее расположение для хранения своей сборки, например Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="8d22c-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="8d22c-140">Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="8d22c-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="8d22c-141">Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:</span><span class="sxs-lookup"><span data-stu-id="8d22c-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном выбора папки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="8d22c-143">Подождите, пока Unity завершит сборку.</span><span class="sxs-lookup"><span data-stu-id="8d22c-143">Wait for Unity to finish the build process.</span></span>

![Unity выполняет сборку](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="8d22c-145">3. Сборка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="8d22c-145">3. Build and deploy the application</span></span>

<span data-ttu-id="8d22c-146">По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой.</span><span class="sxs-lookup"><span data-stu-id="8d22c-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="8d22c-147">Перейдите к папке и дважды щелкните файл SLN, чтобы открыть его в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="8d22c-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Проводник Windows с выбранным созданным решением Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="8d22c-149">Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по установке средств.</span><span class="sxs-lookup"><span data-stu-id="8d22c-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="8d22c-150">Настройте Visual Studio для компьютера, выбрав конфигурацию "Выпуск" архитектуру x64 и целевой объект "Локальный компьютер":</span><span class="sxs-lookup"><span data-stu-id="8d22c-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Среда Visual Studio, настроенная для локального компьютера](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="8d22c-152">Нажмите кнопку ***Локальный компьютер***.</span><span class="sxs-lookup"><span data-stu-id="8d22c-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="8d22c-153">Запустится сборка и развертывание приложения на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="8d22c-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="8d22c-154">Приложение будет установлено на ваш компьютер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8d22c-154">The application will be installed in your PC by default.</span></span>
