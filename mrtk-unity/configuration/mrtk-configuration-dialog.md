---
title: Диалоговое окно настройки МРТК
description: Настройка МРТК в проекте Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345097"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="77148-104">Диалоговое окно настройки проекта МРТК</span><span class="sxs-lookup"><span data-stu-id="77148-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="77148-105">Диалоговое окно настройки МРТК отображается, когда Unity загружает проект и определяет, что один или несколько параметров конфигурации требуют внимания разработчика.</span><span class="sxs-lookup"><span data-stu-id="77148-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Применить позже](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="77148-107">Чтобы применить изменения, нажмите кнопку " **Применить** ".</span><span class="sxs-lookup"><span data-stu-id="77148-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="77148-108">**Затем** кнопка будет откладывать изменения до тех пор, пока проект не будет перезагружен в будущем.</span><span class="sxs-lookup"><span data-stu-id="77148-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="77148-109">Диалоговое окно настройки появится снова, если не установлен один или несколько рекомендуемых параметров.</span><span class="sxs-lookup"><span data-stu-id="77148-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="77148-110">Чтобы предотвратить это, примените нужные параметры, а затем перезапустите диалоговое окно с помощью служебной программы **набора средств для смешанной реальности**  >    >  **Настройка проекта Unity** и нажмите кнопку **пропустить**.</span><span class="sxs-lookup"><span data-stu-id="77148-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="77148-111">Это предотвратит автоматическое появление диалогового окна настройки.</span><span class="sxs-lookup"><span data-stu-id="77148-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="77148-112">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="77148-112">Common settings</span></span>

<span data-ttu-id="77148-113">Все целевые объекты сборки совместно используют коллекцию общих параметров.</span><span class="sxs-lookup"><span data-stu-id="77148-113">All build targets share a collection of common options.</span></span>

![Общие параметры](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="77148-115">Принудительная Сериализация текстовых ресурсов и включение видимых мета файлов</span><span class="sxs-lookup"><span data-stu-id="77148-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="77148-116">Эти параметры помогают упростить работу с проектами Unity и системами управления версиями (например, Git).</span><span class="sxs-lookup"><span data-stu-id="77148-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="77148-117">Включить поддержку VR</span><span class="sxs-lookup"><span data-stu-id="77148-117">Enable VR supported</span></span>

<span data-ttu-id="77148-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="77148-118">**Unity 2018**</span></span>

<span data-ttu-id="77148-119">Настраивает параметры поддержки виртуальной реальности и пакета SDK виртуальной реальности в параметрах **проигрывателя** параметры  >  **XR**.</span><span class="sxs-lookup"><span data-stu-id="77148-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="77148-120">Задать путь отрисовки одиночного экземпляра с одним проходом</span><span class="sxs-lookup"><span data-stu-id="77148-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="77148-121">Настраивает для параметра **проигрывателя параметры**  >  **XR**  >  **режим рендеринга стерео** в **однопроходный экземпляр**.</span><span class="sxs-lookup"><span data-stu-id="77148-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="77148-122">Задать слой поддержки пространственных данных по умолчанию</span><span class="sxs-lookup"><span data-stu-id="77148-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="77148-123">Регистрирует пространственные сведения как слой 31, чтобы обеспечить простую и последовательную настройку параметров райкаст и физик.</span><span class="sxs-lookup"><span data-stu-id="77148-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="77148-124">Аудио спатиализер</span><span class="sxs-lookup"><span data-stu-id="77148-124">Audio spatializer</span></span>

<span data-ttu-id="77148-125">Звуковые спатиализерс — это компоненты, которые разкрывают возможности пространственного звукового и позиционированного звука, чтобы сделать работу смешанной реальности действительно увлекательной.</span><span class="sxs-lookup"><span data-stu-id="77148-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="77148-126">Если задать для параметра Audio спатиализер значение None, то функции позиционированного звука будут отключены.</span><span class="sxs-lookup"><span data-stu-id="77148-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="77148-127">Общие спатиализерс</span><span class="sxs-lookup"><span data-stu-id="77148-127">Common spatializers</span></span>

- <span data-ttu-id="77148-128">Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="77148-128">Microsoft Spatializer</span></span>

<span data-ttu-id="77148-129">Корпорация Майкрософт предоставила спатиализер, которая поддерживает использование аппаратного ускорения в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="77148-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="77148-130">Эта спатиализер доступна через [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) и [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="77148-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="77148-131">Дополнительные сведения о Microsoft Спатиализер см. в документации по [пространственной звукозаписи](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="77148-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="77148-132">Спатиализер MS ХРТФ</span><span class="sxs-lookup"><span data-stu-id="77148-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="77148-133">Microsoft Windows спатиализер, предоставляемая Unity в составе пакетов платформы Windows Mixed Reality и Windows XR.</span><span class="sxs-lookup"><span data-stu-id="77148-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="77148-134">Ресонанце аудио</span><span class="sxs-lookup"><span data-stu-id="77148-134">Resonance Audio</span></span>

<span data-ttu-id="77148-135">Кросс-платформенный спатиализер от Google, предоставляемый Unity.</span><span class="sxs-lookup"><span data-stu-id="77148-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="77148-136">Дополнительные сведения можно найти на сайте [Ресонанце Audio Documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .</span><span class="sxs-lookup"><span data-stu-id="77148-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="77148-137">Параметры универсальная платформа Windows</span><span class="sxs-lookup"><span data-stu-id="77148-137">Universal Windows Platform settings</span></span>

![Параметры UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="77148-139">Возможности UWP</span><span class="sxs-lookup"><span data-stu-id="77148-139">UWP Capabilities</span></span>

<span data-ttu-id="77148-140">Включает определенные возможности приложения для универсальная платформа Windows приложения.</span><span class="sxs-lookup"><span data-stu-id="77148-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="77148-141">Эти возможности позволяют платформе уведомлять и запрашивать разрешение на включение конкретных функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="77148-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="77148-142">Микрофон</span><span class="sxs-lookup"><span data-stu-id="77148-142">Microphone</span></span>

  <span data-ttu-id="77148-143">Включает запись звука с помощью микрофона.</span><span class="sxs-lookup"><span data-stu-id="77148-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="77148-144">Интернет клиента</span><span class="sxs-lookup"><span data-stu-id="77148-144">Internet Client</span></span>

  <span data-ttu-id="77148-145">Включает поддержку доступа к ресурсам через Интернет.</span><span class="sxs-lookup"><span data-stu-id="77148-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="77148-146">Пространственное восприятие</span><span class="sxs-lookup"><span data-stu-id="77148-146">Spatial Perception</span></span>

  <span data-ttu-id="77148-147">Обеспечивает поддержку использования реальной среды.</span><span class="sxs-lookup"><span data-stu-id="77148-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="77148-148">Взгляд глаз</span><span class="sxs-lookup"><span data-stu-id="77148-148">Eye Gaze</span></span>

  <span data-ttu-id="77148-149">**Unity 2019,3 и более поздние версии**</span><span class="sxs-lookup"><span data-stu-id="77148-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="77148-150">Включает поддержку отслеживания взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="77148-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="77148-151">Избегайте сбоя Unity "Плайерсеттингс. Графиксжоб"</span><span class="sxs-lookup"><span data-stu-id="77148-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="77148-152">**Unity 2019,3 и более поздние версии**</span><span class="sxs-lookup"><span data-stu-id="77148-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="77148-153">В последней версии Unity 2019 при включенном параметре "графические задания" приложение аварийно завершит работу при развертывании в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="77148-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="77148-154">Этот параметр включен по умолчанию в Unity. Хотя эта ошибка существует (см. статью [об ошибке Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), конфигуратор по умолчанию будет устанавливать для заданий графики значение "false" (таким образом, разрешив приложениям, развернутым в HoloLens 2, не удается завершить работу).</span><span class="sxs-lookup"><span data-stu-id="77148-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="77148-155">Параметры Android</span><span class="sxs-lookup"><span data-stu-id="77148-155">Android settings</span></span>

<span data-ttu-id="77148-156">Параметры конфигурации для поддержки приложений AR на устройствах под управлением Android.</span><span class="sxs-lookup"><span data-stu-id="77148-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Параметры Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="77148-158">Отключение многопоточной отрисовки</span><span class="sxs-lookup"><span data-stu-id="77148-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="77148-159">Отключает **Параметры проигрывателя**  >  **другие параметры**  >  **многопоточной отрисовки** в соответствии с требованиями поддержки AR в Android.</span><span class="sxs-lookup"><span data-stu-id="77148-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="77148-160">Задать минимальный уровень API</span><span class="sxs-lookup"><span data-stu-id="77148-160">Set Minimum API Level</span></span>

<span data-ttu-id="77148-161">Задает значение **параметров проигрывателя**  >  **другие параметры**  >  **минимальный уровень API** , чтобы обеспечить требования к операционной системе для приложений AR.</span><span class="sxs-lookup"><span data-stu-id="77148-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="77148-162">Параметры iOS</span><span class="sxs-lookup"><span data-stu-id="77148-162">iOS settings</span></span>

<span data-ttu-id="77148-163">Параметры конфигурации для поддержки приложений AR на устройствах под управлением iOS.</span><span class="sxs-lookup"><span data-stu-id="77148-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Параметры iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="77148-165">Задать требуемую версию ОС</span><span class="sxs-lookup"><span data-stu-id="77148-165">Set Required OS Version</span></span>

<span data-ttu-id="77148-166">Задает значение **параметров проигрывателя**  >  **другие параметры**  >  **Минимальная версия iOS** для соблюдения требований к операционной системе для приложений AR.</span><span class="sxs-lookup"><span data-stu-id="77148-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="77148-167">Задать требуемую архитектуру</span><span class="sxs-lookup"><span data-stu-id="77148-167">Set Required Architecture</span></span>

<span data-ttu-id="77148-168">Задает значение **параметров проигрывателя**  >  **другие параметры**  >  **архитектура** для обеспечения требований к платформе для приложений AR.</span><span class="sxs-lookup"><span data-stu-id="77148-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="77148-169">Задание описаний использования камеры</span><span class="sxs-lookup"><span data-stu-id="77148-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="77148-170">Задает значение **параметров проигрывателя**  >  **другие параметры**  >  **Описание использования камеры** , используемое для запроса разрешения на использование камеры устройства.</span><span class="sxs-lookup"><span data-stu-id="77148-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>