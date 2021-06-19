---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394588"
---
# <a name="openxr"></a>[<span data-ttu-id="1fb03-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="1fb03-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="1fb03-102">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="1fb03-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="1fb03-103">Следуйте [инструкциям по установке и использованию](../../welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":</span><span class="sxs-lookup"><span data-stu-id="1fb03-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="1fb03-105">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="1fb03-105">Setting your build target</span></span>

<span data-ttu-id="1fb03-106">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="1fb03-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="1fb03-108">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="1fb03-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="1fb03-109">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="1fb03-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="1fb03-110">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="1fb03-111">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="1fb03-112">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="1fb03-113">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="1fb03-114">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="1fb03-114">Set **UWP SDK** to **Latest installed**</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="1fb03-116">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="1fb03-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="1fb03-117">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="1fb03-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="1fb03-118">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="1fb03-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="1fb03-119">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="1fb03-120">Установите флажки **инициализировать XR при запуске** и **опенкср**</span><span class="sxs-lookup"><span data-stu-id="1fb03-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="1fb03-121">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="1fb03-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="1fb03-123">Optimization</span></span>

<span data-ttu-id="1fb03-124">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="1fb03-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="1fb03-126">Если рядом с **подключаемым модулем опенкср** отображается желтый значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="1fb03-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="1fb03-127">Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="1fb03-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](../../images/openxr-img-06.png)

<span data-ttu-id="1fb03-129">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="1fb03-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="1fb03-130">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="1fb03-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="1fb03-131">Примеры проектов Unity для Опенкср и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1fb03-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="1fb03-132">Ознакомьтесь с [репозиторием примеров Опенкср Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) для примера проектов Unity, демонстрирующих создание приложений Unity для головных телефонов HoloLens 2 или Mixed Reality с помощью подключаемого модуля Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="1fb03-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="1fb03-133">XR Windows</span><span class="sxs-lookup"><span data-stu-id="1fb03-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="1fb03-134">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="1fb03-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="1fb03-136">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="1fb03-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="1fb03-137">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="1fb03-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="1fb03-138">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="1fb03-139">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="1fb03-140">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="1fb03-141">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="1fb03-142">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="1fb03-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="1fb03-143">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="1fb03-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="1fb03-145">После настройки платформы необходимо предоставить Unity знать, чтобы при экспорте создать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления:</span><span class="sxs-lookup"><span data-stu-id="1fb03-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="1fb03-146">В редакторе Unity перейдите к разделу **правка > параметры проекта** и выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="1fb03-147">Выберите **установить управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-147">Select **Install XR Plugin Management**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="1fb03-149">Выберите **инициализировать XR при запуске** и **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="1fb03-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="1fb03-151">Разверните раздел **Управление подключаемым модулем XR** и выберите **универсальной на вкладке параметры платформы Windows** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="1fb03-152">Если вы используете Unity 2020 или более поздней версии, вы увидите параметры для проверки **опенкср** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="1fb03-153">Можно выбрать любую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="1fb03-153">You can choose either runtime.</span></span>  <span data-ttu-id="1fb03-154">Если вы специально разрабатываете для HoloLens 2 или HP reverbа G2 и решите опробовать **опенкср**, выберите поле опенкср и ознакомьтесь с нашим руководством по [использованию подключаемого модуля опенкср Mixed Reality для Unity](../../openxr-getting-started.md) , чтобы обеспечить правильную настройку этих устройств перед возвратом в этом учебнике.</span><span class="sxs-lookup"><span data-stu-id="1fb03-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="1fb03-155">Начиная с Unity 2020 LTS, корпорация Майкрософт применяет разработку с Опенкср.</span><span class="sxs-lookup"><span data-stu-id="1fb03-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="1fb03-156">По мере перехода по этому пути в Unity 2021,1 подключаемый модуль XR Windows будет устаревшим и удален в 2021,2, Опенкср только поддерживаемый путь.</span><span class="sxs-lookup"><span data-stu-id="1fb03-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="1fb03-157">Дополнительные сведения см. в [подокне использование подключаемого модуля Mixed Reality опенкср](../../openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="1fb03-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="1fb03-158">Если вы решили выбрать подключаемый модуль **Windows Mixed Reality** , установите флажок все флажки и задайте для параметра **режим отправки глубины** значение **глубиной 16 бит** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом Windows Mixed Reality](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="1fb03-160">Устаревшая смешанная реальность</span><span class="sxs-lookup"><span data-stu-id="1fb03-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="1fb03-161">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="1fb03-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](../../images/wmr-config-img-3.png)

<span data-ttu-id="1fb03-163">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="1fb03-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="1fb03-164">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="1fb03-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="1fb03-165">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="1fb03-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="1fb03-166">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="1fb03-167">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="1fb03-168">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1fb03-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="1fb03-169">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="1fb03-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="1fb03-170">Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.</span><span class="sxs-lookup"><span data-stu-id="1fb03-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](../../images/wmr-config-img-4.png)

<span data-ttu-id="1fb03-172">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="1fb03-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="1fb03-173">Устаревший XR является устаревшим в Unity 2019 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="1fb03-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="1fb03-174">Открыть **Параметры проигрывателя...** из **параметров сборки... и разверните** группу **параметров XR**</span><span class="sxs-lookup"><span data-stu-id="1fb03-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="1fb03-175">В разделе **Параметры XR** выберите **Виртуальная реальность поддержка** , чтобы добавить список устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="1fb03-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="1fb03-176">Установка **16-разрядного** **формата глубины** и включение **общего доступа к буферу глубины**</span><span class="sxs-lookup"><span data-stu-id="1fb03-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="1fb03-177">Задать **режим отображения стерео** для **одного экземпляра Pass**</span><span class="sxs-lookup"><span data-stu-id="1fb03-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="1fb03-178">Выберите **WSA holographic Remoting поддерживается** , если вы хотите использовать удаленное взаимодействие с holographic</span><span class="sxs-lookup"><span data-stu-id="1fb03-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом параметров проигрывателя](../../images/wmr-config-img-9.png)