---
title: начало работы с МРТК и КСРСДК
description: Целевая страница для МРТК с КСРСДК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, КСРСДК,
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143526"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="4683d-104">Приступая к работе с МРТК и XR SDK</span><span class="sxs-lookup"><span data-stu-id="4683d-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="4683d-105">Пакет SDK для XR — это [Новый конвейер XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="4683d-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="4683d-106">В Unity 2019 он предоставляет альтернативу существующему конвейеру XR.</span><span class="sxs-lookup"><span data-stu-id="4683d-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="4683d-107">В Unity 2020 он станет единственным конвейером XR в Unity.</span><span class="sxs-lookup"><span data-stu-id="4683d-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4683d-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4683d-108">Prerequisites</span></span>

<span data-ttu-id="4683d-109">Чтобы приступить к работе с набором средств Mixed Reality, выполните указанные [шаги](../install-the-tools.md#importing-the-mixed-reality-toolkit) , чтобы добавить мртк в проект.</span><span class="sxs-lookup"><span data-stu-id="4683d-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="4683d-110">Настройка Unity для конвейера SDK XR</span><span class="sxs-lookup"><span data-stu-id="4683d-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="4683d-111">В настоящее время конвейер XR SDK поддерживает 3 платформы: Windows Mixed Reality, Окулус и Опенкср.</span><span class="sxs-lookup"><span data-stu-id="4683d-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="4683d-112">В следующих разделах описываются шаги, необходимые для настройки пакета SDK для XR для каждой платформы.</span><span class="sxs-lookup"><span data-stu-id="4683d-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="4683d-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4683d-113">Windows Mixed Reality</span></span>

<span data-ttu-id="4683d-114">Перейдите в **Диспетчер пакетов Unity** и установите пакет подключаемого модуля Windows XR, который добавляет поддержку Windows Mixed Reality в пакете SDK для XR.</span><span class="sxs-lookup"><span data-stu-id="4683d-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="4683d-115">При этом будут также извлекаться несколько пакетов зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4683d-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="4683d-116">Убедитесь, что следующие компоненты успешно установлены:</span><span class="sxs-lookup"><span data-stu-id="4683d-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="4683d-117">Управление подключаемым модулем XR</span><span class="sxs-lookup"><span data-stu-id="4683d-117">XR Plugin Management</span></span>
   * <span data-ttu-id="4683d-118">Подключаемый модуль Windows XR</span><span class="sxs-lookup"><span data-stu-id="4683d-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="4683d-119">Устаревшие вспомогательные функции ввода XR</span><span class="sxs-lookup"><span data-stu-id="4683d-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="4683d-120">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="4683d-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="4683d-121">Откройте вкладку Управление подключаемым модулем XR в окне Параметры проекта.</span><span class="sxs-lookup"><span data-stu-id="4683d-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="4683d-122">Перейдите к параметрам универсальная платформа Windows и убедитесь, что в разделе поставщики подключаемых модулей установлен флажок Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4683d-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="4683d-123">Убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="4683d-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="4683d-124">(**_Требуется для удаленного взаимодействия в в редакторе HoloLens, в противном случае необязательно_**) Перейдите к автономным параметрам и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей.</span><span class="sxs-lookup"><span data-stu-id="4683d-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="4683d-125">Также убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="4683d-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Управление подключаемым модулем XR с выбранным изолированной вкладкой](images/xr-management-img-02.png)

7. <span data-ttu-id="4683d-127">(**_Необязательно_**) Щелкните вкладку Windows Mixed Reality в разделе Управление подключаемыми модулями XR и создайте профиль настраиваемых параметров, чтобы изменить значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4683d-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="4683d-128">Если список параметров уже существует, профиль создавать не нужно.</span><span class="sxs-lookup"><span data-stu-id="4683d-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Управление подключаемым модулем XR с выбранной вкладкой Windows](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="4683d-130">окулус</span><span class="sxs-lookup"><span data-stu-id="4683d-130">Oculus</span></span>

1. <span data-ttu-id="4683d-131">Выполните [инструкции по настройке Окулус Quest в мртк с помощью руководства по конвейеру XR SDK](../supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="4683d-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="4683d-132">В руководстве описаны действия, необходимые для настройки Unity и МРТК для использования конвейера XR SDK для Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="4683d-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="4683d-133">Опенкср (Предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="4683d-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4683d-134">Опенкср в Unity поддерживается только в Unity 2020,2 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="4683d-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="4683d-135">В настоящее время он также поддерживает только сборки x64 и ARM64.</span><span class="sxs-lookup"><span data-stu-id="4683d-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="4683d-136">Следуйте указаниям в руководстве по [использованию подключаемого модуля Mixed Reality опенкср для Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , включая шаги по настройке управления подключаемым модулем XR и оптимизации для установки подключаемого модуля опенкср в проект.</span><span class="sxs-lookup"><span data-stu-id="4683d-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="4683d-137">Убедитесь, что следующие компоненты успешно установлены:</span><span class="sxs-lookup"><span data-stu-id="4683d-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="4683d-138">Управление подключаемым модулем XR</span><span class="sxs-lookup"><span data-stu-id="4683d-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="4683d-139">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="4683d-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="4683d-140">Подключаемый модуль Опенкср в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="4683d-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="4683d-141">Перейдите к разделу Edit > Settings Project.</span><span class="sxs-lookup"><span data-stu-id="4683d-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="4683d-142">Откройте вкладку Управление подключаемым модулем XR в окне Параметры проекта.</span><span class="sxs-lookup"><span data-stu-id="4683d-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="4683d-143">Убедитесь, что установлен флажок инициализировать XR при запуске.</span><span class="sxs-lookup"><span data-stu-id="4683d-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="4683d-144">(**_Необязательно_**) Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите набор функций Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4683d-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Управление подключаемым модулем Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="4683d-146">Если у вас уже есть проект, использующий МРТК из УПМ, убедитесь, что следующая строка находится в файле **link.xml** , расположенном в папке Микседреалититулкит. Generated.</span><span class="sxs-lookup"><span data-stu-id="4683d-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="4683d-147">В первоначальном выпуске МРТК и Опенкср поддерживаются только контроллеры движения HoloLens 2 с четкой и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4683d-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="4683d-148">В будущих выпусках будет добавлена поддержка дополнительного оборудования.</span><span class="sxs-lookup"><span data-stu-id="4683d-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="4683d-149">Настройка МРТК для конвейера XR SDK</span><span class="sxs-lookup"><span data-stu-id="4683d-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="4683d-150">При использовании Опенкср выберите "Дефаултопенксрконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.</span><span class="sxs-lookup"><span data-stu-id="4683d-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="4683d-151">При использовании других сред выполнения XR в конфигурации управления подключаемыми модулями XR, например Windows Mixed Reality или Окулус, выберите "Дефаултксрсдкконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.</span><span class="sxs-lookup"><span data-stu-id="4683d-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="4683d-152">При необходимости эти профили устанавливаются с правильными системами и поставщиками.</span><span class="sxs-lookup"><span data-stu-id="4683d-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="4683d-153">Дополнительные сведения о профилировании и примерах поддержки с помощью пакета SDK для XR см. [в](../features/profiles/profiles.md#xr-sdk) документации по профилям.</span><span class="sxs-lookup"><span data-stu-id="4683d-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="4683d-154">Чтобы перенести существующий профиль в пакет SDK для XR, необходимо обновить следующие службы и поставщики данных:</span><span class="sxs-lookup"><span data-stu-id="4683d-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="4683d-155">Камера</span><span class="sxs-lookup"><span data-stu-id="4683d-155">Camera</span></span>

<span data-ttu-id="4683d-156">От [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="4683d-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Параметры старой камеры](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="4683d-158">значение</span><span class="sxs-lookup"><span data-stu-id="4683d-158">to</span></span>

| <span data-ttu-id="4683d-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4683d-159">OpenXR</span></span> | <span data-ttu-id="4683d-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4683d-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="4683d-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**и**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="4683d-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Параметры камеры пакета SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="4683d-163">Входные данные</span><span class="sxs-lookup"><span data-stu-id="4683d-163">Input</span></span>

<span data-ttu-id="4683d-164">От [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="4683d-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Устаревшие параметры ввода](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="4683d-166">значение</span><span class="sxs-lookup"><span data-stu-id="4683d-166">to</span></span>

| <span data-ttu-id="4683d-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4683d-167">OpenXR</span></span> | <span data-ttu-id="4683d-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4683d-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="4683d-169">__Опенкср__:</span><span class="sxs-lookup"><span data-stu-id="4683d-169">__OpenXR__:</span></span>

![Параметры ввода Опенкср](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="4683d-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="4683d-171">__Windows Mixed Reality__:</span></span>

![Входные параметры пакета SDK для XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="4683d-173">Граница</span><span class="sxs-lookup"><span data-stu-id="4683d-173">Boundary</span></span>

<span data-ttu-id="4683d-174">От [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="4683d-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Устаревшие параметры границ](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="4683d-176">значение</span><span class="sxs-lookup"><span data-stu-id="4683d-176">to</span></span>

| <span data-ttu-id="4683d-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4683d-177">OpenXR</span></span> | <span data-ttu-id="4683d-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4683d-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Параметры границ пакета SDK для XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="4683d-180">Поддержка пространственных сведений</span><span class="sxs-lookup"><span data-stu-id="4683d-180">Spatial awareness</span></span>

<span data-ttu-id="4683d-181">От [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="4683d-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Устаревшие параметры пространственной информации о поддержке](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="4683d-183">значение</span><span class="sxs-lookup"><span data-stu-id="4683d-183">to</span></span>

| <span data-ttu-id="4683d-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4683d-184">OpenXR</span></span> | <span data-ttu-id="4683d-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4683d-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="4683d-186">Выполняется</span><span class="sxs-lookup"><span data-stu-id="4683d-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Параметры пространственной осведомленности пакета SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="4683d-188">Сопоставления контроллеров</span><span class="sxs-lookup"><span data-stu-id="4683d-188">Controller mappings</span></span>

<span data-ttu-id="4683d-189">Если вы используете настраиваемые профили сопоставления контроллеров, откройте один из них и запустите команду меню "служебные программы" набора средств для управления смешанной реальности — > Utilities-> обновление->, чтобы убедиться, что определены новые типы контроллеров SDK для XR.</span><span class="sxs-lookup"><span data-stu-id="4683d-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="4683d-190">См. также</span><span class="sxs-lookup"><span data-stu-id="4683d-190">See also</span></span>

* [<span data-ttu-id="4683d-191">Начало работы с AR Development в Unity</span><span class="sxs-lookup"><span data-stu-id="4683d-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="4683d-192">Начало работы с разработкой VR в Unity</span><span class="sxs-lookup"><span data-stu-id="4683d-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)