---
title: Начало работы с MRTK и SDK смешанной реальности
description: Целевая страница для МРТК с пакетом SDK для XR
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, ксрсдк, XR SDK
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603695"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="77b20-104">Начало работы с MRTK и SDK смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="77b20-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="77b20-105">Пакет SDK для XR — это [Новый конвейер XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="77b20-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="77b20-106">В Unity 2019 он предоставляет альтернативу существующему конвейеру XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="77b20-107">В Unity 2020 это единственный конвейер XR в Unity.</span><span class="sxs-lookup"><span data-stu-id="77b20-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="77b20-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="77b20-108">Prerequisites</span></span>

<span data-ttu-id="77b20-109">чтобы начать работу с набор средств смешанной реальности, выполните указанные [шаги](../install-the-tools.md#importing-the-mixed-reality-toolkit) , чтобы добавить мртк в проект.</span><span class="sxs-lookup"><span data-stu-id="77b20-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="77b20-110">Настройка Unity для конвейера SDK XR</span><span class="sxs-lookup"><span data-stu-id="77b20-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="77b20-111">в настоящее время конвейер XR SDK поддерживает 3 платформы: Windows Mixed Reality, окулус и опенкср.</span><span class="sxs-lookup"><span data-stu-id="77b20-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="77b20-112">В следующих разделах описываются шаги, необходимые для настройки пакета SDK для XR для каждой платформы.</span><span class="sxs-lookup"><span data-stu-id="77b20-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="77b20-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="77b20-113">Windows Mixed Reality</span></span>

<span data-ttu-id="77b20-114">перейдите в **диспетчер пакетов Unity** и установите пакет подключаемого модуля Windows XR, который добавляет поддержку Windows Mixed Reality в пакете SDK для XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="77b20-115">При этом будут также извлекаться несколько пакетов зависимостей.</span><span class="sxs-lookup"><span data-stu-id="77b20-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="77b20-116">Убедитесь, что следующие компоненты успешно установлены:</span><span class="sxs-lookup"><span data-stu-id="77b20-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="77b20-117">Управление подключаемым модулем XR</span><span class="sxs-lookup"><span data-stu-id="77b20-117">XR Plugin Management</span></span>
   * <span data-ttu-id="77b20-118">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="77b20-119">Устаревшие вспомогательные функции ввода XR</span><span class="sxs-lookup"><span data-stu-id="77b20-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="77b20-120">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="77b20-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="77b20-121">в окне Project Параметры щелкните вкладку управление подключаемыми модулями XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="77b20-122">перейдите к параметрам универсальная платформа Windows и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей.</span><span class="sxs-lookup"><span data-stu-id="77b20-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="77b20-123">Убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="77b20-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="77b20-124">(**_требуется для удаленного взаимодействия в редакторе HoloLens, в противном случае необязательно_**) перейдите к автономным параметрам и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей.</span><span class="sxs-lookup"><span data-stu-id="77b20-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="77b20-125">Также убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="77b20-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![Управление подключаемым модулем XR с выбранным изолированной вкладкой](images/xr-management-img-02.png)

7. <span data-ttu-id="77b20-127">(**_Необязательно_**) щелкните вкладку Windows Mixed Reality в разделе управление подключаемыми модулями XR и создайте профиль настраиваемых параметров, чтобы изменить значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77b20-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="77b20-128">Если список параметров уже существует, профиль создавать не нужно.</span><span class="sxs-lookup"><span data-stu-id="77b20-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![управление подключаемым модулем XR с выбранной вкладкой Windows](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="77b20-130">окулус</span><span class="sxs-lookup"><span data-stu-id="77b20-130">Oculus</span></span>

1. <span data-ttu-id="77b20-131">Выполните [инструкции по настройке Окулус Quest в мртк с помощью руководства по конвейеру XR SDK](../supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="77b20-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="77b20-132">В руководстве описаны действия, необходимые для настройки Unity и МРТК для использования конвейера XR SDK для Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="77b20-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr"></a><span data-ttu-id="77b20-133">OpenXR</span><span class="sxs-lookup"><span data-stu-id="77b20-133">OpenXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77b20-134">Опенкср в Unity поддерживается только в Unity 2020,2 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="77b20-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="77b20-135">Он также поддерживает только сборки x64, ARM и ARM64.</span><span class="sxs-lookup"><span data-stu-id="77b20-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="77b20-136">Следуйте указаниям в руководстве по [использованию подключаемого модуля Mixed Reality опенкср для Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , включая шаги по настройке управления подключаемым модулем XR и оптимизации для установки подключаемого модуля опенкср в проект.</span><span class="sxs-lookup"><span data-stu-id="77b20-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="77b20-137">Убедитесь, что следующие компоненты успешно установлены:</span><span class="sxs-lookup"><span data-stu-id="77b20-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="77b20-138">Управление подключаемым модулем XR</span><span class="sxs-lookup"><span data-stu-id="77b20-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="77b20-139">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="77b20-140">Подключаемый модуль Опенкср в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="77b20-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="77b20-141">перейдите в раздел Edit > Project Параметры.</span><span class="sxs-lookup"><span data-stu-id="77b20-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="77b20-142">в окне Project Параметры щелкните вкладку управление подключаемыми модулями XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="77b20-143">Убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="77b20-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="77b20-144">(**_Необязательно_**) если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP и выберите Microsoft HoloLens наборе функций.</span><span class="sxs-lookup"><span data-stu-id="77b20-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Опенкср управления подключаемым модулем](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="77b20-146">Если у вас уже есть проект, использующий МРТК из УПМ, убедитесь, что следующая строка находится в файле **link.xml** , расположенном в папке Микседреалититулкит. Generated.</span><span class="sxs-lookup"><span data-stu-id="77b20-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="77b20-147">в первоначальном выпуске мртк и опенкср поддерживаются только HoloLens 2 наWindows Mixed Realityные контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="77b20-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="77b20-148">В будущих выпусках будет добавлена поддержка дополнительного оборудования.</span><span class="sxs-lookup"><span data-stu-id="77b20-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="77b20-149">Настройка МРТК для конвейера XR SDK</span><span class="sxs-lookup"><span data-stu-id="77b20-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-150">Используйте любой из профилей МРТК по умолчанию, которые настроены для всех конвейеров XR Unity.</span><span class="sxs-lookup"><span data-stu-id="77b20-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="77b20-151">Предыдущие "Дефаултопенксрконфигуратионпрофиле" и "Дефаултксрсдкконфигуратионпрофиле" теперь помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="77b20-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="77b20-152">При использовании Опенкср выберите "Дефаултопенксрконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.</span><span class="sxs-lookup"><span data-stu-id="77b20-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="77b20-153">при использовании других сред выполнения XR в конфигурации управления подключаемыми модулями XR, например Windows Mixed Reality или окулус, выберите "дефаултксрсдкконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.</span><span class="sxs-lookup"><span data-stu-id="77b20-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="77b20-154">При необходимости эти профили устанавливаются с правильными системами и поставщиками.</span><span class="sxs-lookup"><span data-stu-id="77b20-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="77b20-155">Дополнительные сведения о профилировании и примерах поддержки с помощью пакета SDK для XR см. [в](../features/profiles/profiles.md#xr-sdk) документации по профилям.</span><span class="sxs-lookup"><span data-stu-id="77b20-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="77b20-156">Чтобы перенести существующий профиль в пакет SDK для XR, необходимо обновить следующие службы и поставщики данных.</span><span class="sxs-lookup"><span data-stu-id="77b20-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-157">Вы сможете увидеть новые поставщики данных на вкладке XR SDK в Unity 2019 или в основном представлении/только в Unity 2020 +, где не существует устаревшей версии XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![Вкладка XR SDK](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="77b20-159">Камера</span><span class="sxs-lookup"><span data-stu-id="77b20-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-160">Добавление следующих поставщиков данных</span><span class="sxs-lookup"><span data-stu-id="77b20-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="77b20-161">От [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="77b20-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Параметры старой камеры](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="77b20-163">значение</span><span class="sxs-lookup"><span data-stu-id="77b20-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="77b20-164">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-164">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-165">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="77b20-166">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-166">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-167">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Параметры камеры пакета SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="77b20-169">Входные данные</span><span class="sxs-lookup"><span data-stu-id="77b20-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-170">Добавление следующих поставщиков данных</span><span class="sxs-lookup"><span data-stu-id="77b20-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="77b20-171">От [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="77b20-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Устаревшие параметры ввода](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="77b20-173">значение</span><span class="sxs-lookup"><span data-stu-id="77b20-173">to</span></span>
::: moniker-end

| <span data-ttu-id="77b20-174">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-174">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-175">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="77b20-176">__Опенкср__:</span><span class="sxs-lookup"><span data-stu-id="77b20-176">__OpenXR__:</span></span>

![Параметры ввода Опенкср](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="77b20-178">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="77b20-178">__Windows Mixed Reality__:</span></span>

![Входные параметры пакета SDK для XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="77b20-180">Граница</span><span class="sxs-lookup"><span data-stu-id="77b20-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-181">Добавление следующих поставщиков данных</span><span class="sxs-lookup"><span data-stu-id="77b20-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="77b20-182">От [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="77b20-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Устаревшие параметры границ](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="77b20-184">значение</span><span class="sxs-lookup"><span data-stu-id="77b20-184">to</span></span>
::: moniker-end

| <span data-ttu-id="77b20-185">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-185">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-186">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Параметры границ пакета SDK для XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="77b20-188">Отслеживание пространственного положения</span><span class="sxs-lookup"><span data-stu-id="77b20-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="77b20-189">Добавление следующих поставщиков данных</span><span class="sxs-lookup"><span data-stu-id="77b20-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="77b20-190">От [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="77b20-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Устаревшие параметры пространственной информации о поддержке](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="77b20-192">значение</span><span class="sxs-lookup"><span data-stu-id="77b20-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="77b20-193">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-193">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-194">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="77b20-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (для UWP)</span><span class="sxs-lookup"><span data-stu-id="77b20-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="77b20-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (для UWP)</span><span class="sxs-lookup"><span data-stu-id="77b20-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="77b20-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (для не-UWP)</span><span class="sxs-lookup"><span data-stu-id="77b20-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="77b20-198">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="77b20-198">OpenXR Plugin</span></span> | <span data-ttu-id="77b20-199">Windows Подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="77b20-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Параметры пространственной осведомленности пакета SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="77b20-201">Сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="77b20-201">Controller mappings</span></span>

<span data-ttu-id="77b20-202">если вы используете настраиваемые профили сопоставления контроллеров, откройте один из них и запустите команду меню "служебные программы набор средств-> Utilities-> обновления->", чтобы убедиться, что определены новые типы контроллеров SDK XR.</span><span class="sxs-lookup"><span data-stu-id="77b20-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="77b20-203">См. также</span><span class="sxs-lookup"><span data-stu-id="77b20-203">See also</span></span>

* [<span data-ttu-id="77b20-204">Начало работы с AR Development в Unity</span><span class="sxs-lookup"><span data-stu-id="77b20-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="77b20-205">Начало работы с разработкой VR в Unity</span><span class="sxs-lookup"><span data-stu-id="77b20-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
