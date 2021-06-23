---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535739"
---
# <a name="openxr"></a>[<span data-ttu-id="d0bcf-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="d0bcf-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d0bcf-102">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="d0bcf-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="d0bcf-103">Следуйте [инструкциям по установке и использованию](../../welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории **Поддержка платформы** :</span><span class="sxs-lookup"><span data-stu-id="d0bcf-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="d0bcf-105">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="d0bcf-105">Setting your build target</span></span>

<span data-ttu-id="d0bcf-106">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="d0bcf-108">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="d0bcf-109">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="d0bcf-110">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="d0bcf-111">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="d0bcf-112">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="d0bcf-113">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="d0bcf-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="d0bcf-114">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="d0bcf-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="d0bcf-116">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="d0bcf-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="d0bcf-117">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="d0bcf-118">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="d0bcf-119">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="d0bcf-120">Выберите **установить управление подключаемым модулем XR** , если оно отображается ![ на снимке экрана окна параметров проекта в редакторе Unity с выделенным элементом управления подключаемым модулем XR.](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="d0bcf-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="d0bcf-121">Установите флажок **инициализировать XR при запуске** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="d0bcf-122">Если нацеливание на Desktop VR, оставайтесь на автономной вкладке ПК (мониторе) и установите флажки в полях **опенкср** и **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="d0bcf-123">Если нацеливание на HoloLens 2, перейдите на вкладку универсальная платформа Windows (логотип Windows) и выберите поля **опенкср** и **Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="d0bcf-125">Если рядом с **подключаемым модулем опенкср** отображается желтый значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="d0bcf-126">Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="d0bcf-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="d0bcf-128">Optimization</span></span>

<span data-ttu-id="d0bcf-129">Если вы разрабатываете для HoloLens 2, выберите **проект > смешанной реальности > применить Рекомендуемые параметры проекта для пункта меню HoloLens 2** , чтобы повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](../../images/openxr-img-08.png)

<span data-ttu-id="d0bcf-131">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="d0bcf-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="d0bcf-132">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="d0bcf-133">Примеры проектов Unity для Опенкср и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d0bcf-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="d0bcf-134">Ознакомьтесь с [репозиторием примеров Опенкср Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) для примера проектов Unity, демонстрирующих создание приложений Unity для головных телефонов HoloLens 2 или Mixed Reality с помощью подключаемого модуля Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="d0bcf-135">Если вы готовы приступить к работе с пустым проектом, перейдите к статье [Настройка камеры](../../camera-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="d0bcf-136">XR Windows</span><span class="sxs-lookup"><span data-stu-id="d0bcf-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="d0bcf-137">Подключаемый модуль Windows XR является устаревшим в Unity 2021,1 и будет удален в Unity 2021,2.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="d0bcf-138">Для разработки Unity 2020 Корпорация Майкрософт рекомендует вместо этого использовать подключаемый модуль Опенкср.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="d0bcf-139">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="d0bcf-141">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="d0bcf-142">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="d0bcf-143">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="d0bcf-144">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="d0bcf-145">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="d0bcf-146">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="d0bcf-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="d0bcf-147">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="d0bcf-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="d0bcf-148">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="d0bcf-150">После настройки платформы необходимо предоставить Unity знать, чтобы при экспорте создать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="d0bcf-151">В редакторе Unity перейдите к разделу **правка > параметры проекта** и выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="d0bcf-152">Выберите **установить управление подключаемым модулем XR** , если оно отображается</span><span class="sxs-lookup"><span data-stu-id="d0bcf-152">Select **Install XR Plugin Management** if it appears</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="d0bcf-154">Выберите **инициализировать XR при запуске** и **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="d0bcf-156">Выберите подраздел **Управление подключаемым модулем XR**  >  **Windows Mixed Reality** , установите флажки для всех полей и задайте для параметра **Формат буфера глубины** значение **буфер глубины 16 бит** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом Windows Mixed Reality](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="d0bcf-158">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="d0bcf-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="d0bcf-159">Устаревший XR является устаревшим в Unity 2019 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="d0bcf-160">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="d0bcf-162">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="d0bcf-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="d0bcf-163">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="d0bcf-164">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="d0bcf-165">Для параметра **Архитектура** выберите **ARM64**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="d0bcf-166">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="d0bcf-167">Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).</span><span class="sxs-lookup"><span data-stu-id="d0bcf-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="d0bcf-168">Задать для **целевой версии пакета SDK** **последнюю установленную** версию</span><span class="sxs-lookup"><span data-stu-id="d0bcf-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="d0bcf-169">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="d0bcf-171">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="d0bcf-172">Открыть **Параметры проигрывателя...** из **параметров сборки... и разверните** группу **параметров XR**</span><span class="sxs-lookup"><span data-stu-id="d0bcf-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="d0bcf-173">В разделе **Параметры XR** выберите **Виртуальная реальность поддержка** , чтобы добавить список устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="d0bcf-174">Задайте для **формата глубины** глубину **16 бит** и установите флажок **включить общий доступ к буферу глубины** .</span><span class="sxs-lookup"><span data-stu-id="d0bcf-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="d0bcf-175">Задайте для параметра **Stereo Rendering Mode** (Режим стерео отрисовки) значение **Single Pass Instanced** (Однопроходный экземпляр).</span><span class="sxs-lookup"><span data-stu-id="d0bcf-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="d0bcf-176">Выберите **WSA holographic Remoting Supported** (удаленное взаимодействие), если хотите использовать режим удаленного взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="d0bcf-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом параметров проигрывателя](../../images/wmr-config-img-9.png)
