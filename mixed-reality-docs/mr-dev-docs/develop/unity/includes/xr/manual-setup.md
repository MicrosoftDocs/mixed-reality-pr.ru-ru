---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603733"
---
# <a name="openxr"></a>[<span data-ttu-id="3a222-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3a222-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="3a222-102">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="3a222-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="3a222-103">Следуйте [инструкциям по установке и использованию](../../welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории **Поддержка платформы** :</span><span class="sxs-lookup"><span data-stu-id="3a222-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="3a222-105">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="3a222-105">Setting your build target</span></span>

<span data-ttu-id="3a222-106">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="3a222-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным компьютером, & автономной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="3a222-108">если вы нацеливание на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="3a222-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="3a222-109">выберите **файл > сборка Параметры...**</span><span class="sxs-lookup"><span data-stu-id="3a222-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="3a222-110">выберите **универсальная платформа Windows** в списке платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="3a222-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="3a222-111">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="3a222-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="3a222-112">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="3a222-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="3a222-113">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="3a222-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="3a222-114">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="3a222-114">Set **Target SDK Version** to **Latest installed**</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="3a222-116">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="3a222-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="3a222-117">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="3a222-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="3a222-118">в редакторе Unity перейдите к **изменению > Project Параметры**</span><span class="sxs-lookup"><span data-stu-id="3a222-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="3a222-119">в списке Параметры выберите **управление подключаемым модулем XR** (должно быть уже установлено, если установлен подключаемый модуль опенкср смешанной реальности с помощью мрфт).</span><span class="sxs-lookup"><span data-stu-id="3a222-119">In the list of Settings, select **XR Plugin Management** (should already be installed if you installed the Mixed Reality OpenXR plugin using MRFT)</span></span>
3. <span data-ttu-id="3a222-120">Установите флажок **инициализировать XR при запуске** .</span><span class="sxs-lookup"><span data-stu-id="3a222-120">Check the **Initialize XR on Startup** box</span></span>
4. <span data-ttu-id="3a222-121">если нацеливание на Desktop VR, оставайтесь на автономной вкладке пк (мониторе) и установите флажки для **опенкср** и **Windows Mixed Reality набора функций** .</span><span class="sxs-lookup"><span data-stu-id="3a222-121">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
5. <span data-ttu-id="3a222-122">если нацеливание на HoloLens 2, перейдите на вкладку универсальная платформа Windows (логотип Windows) и установите флажки для **набора функций** **опенкср** и Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3a222-122">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="3a222-124">Если рядом с **подключаемым модулем опенкср** отображается желтый значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="3a222-124">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="3a222-125">Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="3a222-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="3a222-127">Optimization</span><span class="sxs-lookup"><span data-stu-id="3a222-127">Optimization</span></span>

<span data-ttu-id="3a222-128">если вы разрабатываете для HoloLens 2, выберите **> смешанная реальность Project > применить рекомендуемые параметры проекта для HoloLens 2** пункта меню, чтобы повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="3a222-128">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](../../images/openxr-img-08.png)

<span data-ttu-id="3a222-130">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="3a222-130">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="3a222-131">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="3a222-131">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="3a222-132">Примеры проектов Unity для Опенкср и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3a222-132">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="3a222-133">ознакомьтесь с [репозиторием примеров опенкср смешанной реальности](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) для примера проектов unity, демонстрирующих создание приложений unity для HoloLens 2 или гарнитур смешанной реальности с помощью подключаемого модуля mixed reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="3a222-133">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="3a222-134">Если вы готовы приступить к работе с пустым проектом, перейдите к статье [Настройка камеры](../../camera-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="3a222-134">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="3a222-135">Windows XR</span><span class="sxs-lookup"><span data-stu-id="3a222-135">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="3a222-136">подключаемый модуль Windows XR является устаревшим в unity 2021,1 и будет удален в unity 2021,2.</span><span class="sxs-lookup"><span data-stu-id="3a222-136">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="3a222-137">Для разработки Unity 2020 Корпорация Майкрософт рекомендует вместо этого использовать подключаемый модуль Опенкср.</span><span class="sxs-lookup"><span data-stu-id="3a222-137">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="3a222-138">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="3a222-138">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным компьютером, & автономной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="3a222-140">если вы нацеливание на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="3a222-140">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="3a222-141">выберите **файл > сборка Параметры...**</span><span class="sxs-lookup"><span data-stu-id="3a222-141">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="3a222-142">выберите **универсальная платформа Windows** в списке платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="3a222-142">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="3a222-143">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="3a222-143">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="3a222-144">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="3a222-144">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="3a222-145">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="3a222-145">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="3a222-146">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="3a222-146">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="3a222-147">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="3a222-147">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="3a222-149">После настройки платформы необходимо предоставить Unity знать, чтобы при экспорте создать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления:</span><span class="sxs-lookup"><span data-stu-id="3a222-149">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="3a222-150">в редакторе Unity перейдите к разделу **изменение > параметры Project** и выберите **управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="3a222-150">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="3a222-151">Выберите **установить управление подключаемым модулем XR** , если оно отображается</span><span class="sxs-lookup"><span data-stu-id="3a222-151">Select **Install XR Plugin Management** if it appears</span></span>

![снимок экрана: окно Project Параметры открыть в редакторе unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="3a222-153">выберите **инициализировать XR при запуске** и **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="3a222-153">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![снимок экрана: окно "параметры Project" открыто в редакторе unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="3a222-155">выберите раздел **Windows Mixed Reality Management подключаемый модуль XR**  >   , установите флажки для всех полей и задайте для параметра **формат буфера глубины** значение **буфер глубины 16 бит** .</span><span class="sxs-lookup"><span data-stu-id="3a222-155">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![снимок экрана: окно "параметры Project" открыто в редакторе unity с выделенным Windows Mixed Realityным разделом](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="3a222-157">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="3a222-157">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="3a222-158">Устаревший XR является устаревшим в Unity 2019 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="3a222-158">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="3a222-159">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="3a222-159">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным компьютером, & автономной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="3a222-161">если вы нацеливание на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="3a222-161">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="3a222-162">выберите **файл > сборка Параметры...**</span><span class="sxs-lookup"><span data-stu-id="3a222-162">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="3a222-163">выберите **универсальная платформа Windows** в списке платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="3a222-163">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="3a222-164">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="3a222-164">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="3a222-165">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="3a222-165">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="3a222-166">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="3a222-166">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="3a222-167">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="3a222-167">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="3a222-168">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="3a222-168">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![снимок экрана: окно сборки Параметры открыть в редакторе unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="3a222-170">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="3a222-170">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="3a222-171">открыть **проигрыватель Параметры...** из **Параметры сборки... и разверните** группу **Параметры XR**</span><span class="sxs-lookup"><span data-stu-id="3a222-171">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="3a222-172">в разделе **Параметры XR** выберите **virtual reality supported (поддерживаемые** устройства), чтобы добавить список устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="3a222-172">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="3a222-173">Задайте для **формата глубины** глубину **16 бит** и установите флажок **включить общий доступ к буферу глубины** .</span><span class="sxs-lookup"><span data-stu-id="3a222-173">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="3a222-174">Задайте для параметра **Stereo Rendering Mode** (Режим стерео отрисовки) значение **Single Pass Instanced** (Однопроходный экземпляр).</span><span class="sxs-lookup"><span data-stu-id="3a222-174">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="3a222-175">Выберите **WSA holographic Remoting Supported** (удаленное взаимодействие), если хотите использовать режим удаленного взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="3a222-175">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![снимок экрана: окно "параметры Project" открыто в редакторе unity с выделенным разделом параметров проигрывателя](../../images/wmr-config-img-9.png)
