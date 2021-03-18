---
title: Сборка и развертывание
description: Документация по сборке и развертыванию приложений на разных устройствах.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: f86e70fb80e854111c62391d706a8d33fcd67c90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101775067"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="d7eb3-104">Сборка и развертывание MRTK</span><span class="sxs-lookup"><span data-stu-id="d7eb3-104">Building and deploying MRTK</span></span>

<span data-ttu-id="d7eb3-105">Чтобы запустить приложение на устройстве (HoloLens, Android, iOS и т. д.) как автономное приложение, необходимо выполнить в проекте Unity шаг сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="d7eb3-106">Сборка и развертывание приложения, в котором используется MRTK, ничем не отличается от сборки и развертывания любого другого приложения Unity.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="d7eb3-107">Специальные инструкции для MRTK отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="d7eb3-108">Ниже приведены подробные инструкции по сборке и развертыванию приложения Unity для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="d7eb3-109">Сведения о сборке для других платформ см. [здесь](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="d7eb3-110">Сборка и развертывание MRTK на HoloLens 1 и HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="d7eb3-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="d7eb3-111">Инструкции по сборке и развертыванию для HoloLens 1 и HoloLens 2 (UWP) можно найти в статье [о сборке приложения на устройстве](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="d7eb3-112">**Совет.** При сборке для платформы WMR, HoloLens 1 или HoloLens 2 мы рекомендуем использовать следующие параметры сборки для целевой версии пакета SDK и минимальной версии платформы:</span><span class="sxs-lookup"><span data-stu-id="d7eb3-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Окно сборки](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="d7eb3-114">Другие параметры могут отличаться (например, конфигурация сборки, архитектура или тип сборки), а некоторые из них вы всегда можете изменить в решении Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="d7eb3-115">Убедитесь, что раскрывающийся список "Target SDK Version" (Целевая версия пакета SDK) содержит вариант "10.0.18362.0". Если он отсутствует, необходимо установить [последнюю версию Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="d7eb3-116">Unity 2019.3 и HoloLens</span><span class="sxs-lookup"><span data-stu-id="d7eb3-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="d7eb3-117">Если приложение HoloLens отображается на устройстве в формате двухмерной панели, перед развертыванием приложения UWP убедитесь, что в Unity 2019.3. x были настроены следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="d7eb3-118">При использовании старой версии XR выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d7eb3-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="d7eb3-119">Последовательно выберите Edit > Project Settings, Player (Правка — Параметры проекта — Средство воспроизведения).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="d7eb3-120">В разделе **XR Settings** (Параметры смешанной реальности) на вкладке UWP убедитесь, что включен параметр **Virtual Reality Supported** (Поддержка виртуальной реальности), а в список пакетов SDK добавлен SDK **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="d7eb3-121">Выполните сборку и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="d7eb3-122">При использовании подключаемого модуля смешанной реальности выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d7eb3-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="d7eb3-123">Выполните шаги, описанные в статье [Начало работы с XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-123">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="d7eb3-124">Убедитесь, что **DefaultXRSDKConfigurationProfile** выбран в качестве профиля конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="d7eb3-125">Последовательно выберите **Edit > Project Settings, XR-Plugin Management** (Правка — Параметры проекта — Управление подключаемым модулем смешанной реальности) и убедитесь, что включен параметр **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="d7eb3-126">Выполните сборку и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d7eb3-127">При использовании Unity 2019.3.x в качестве архитектуры сборки в Visual Studio выберите **ARM64**, а не **ARM**.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d7eb3-128">При стандартных параметрах Unity для версии Unity 2019.3.x из-за ошибки Unity приложение Unity не сможет развернуться на HoloLens, если выбрана архитектура ARM.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="d7eb3-129">Подробнее об этой проблеме см. в [системе контроля проблем Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="d7eb3-130">Если архитектура ARM является обязательной, выберите **Edit > Project Settings, Player** (Правка — Параметры проекта — Средство воспроизведения), а затем в меню **Other Settings** (Другие настройки) отключите параметр **Graphics Jobs** (Графические задания).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="d7eb3-131">Отключение параметра **Graphics Jobs** (Графические задания) позволит развернуть приложение с архитектурой сборки ARM в Unity 2019.3.x, но мы рекомендуем использовать ARM64.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="d7eb3-132">Сборка и развертывание MRTK на гарнитуре Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d7eb3-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="d7eb3-133">Гарнитура Windows Mixed Reality может использоваться для сборки под универсальную платформу Windows (UWP) или для автономной сборки.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="d7eb3-134">Автономная сборка для гарнитуры Windows Mixed Reality требует несколько дополнительных действий:</span><span class="sxs-lookup"><span data-stu-id="d7eb3-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="d7eb3-135">Пакет SDK XR для Unity также имеет встроенную поддержку Windows Mixed Reality в автономных сборках, но не требует наличия подключаемого модуля SteamVR или Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="d7eb3-136">Описанные здесь действия обязательны для выполнения в устаревшей версии XR в Unity.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="d7eb3-137">Установите [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="d7eb3-138">Установите [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="d7eb3-139">Установите [подключаемый модуль Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="d7eb3-140">Использование подключаемого модуля Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d7eb3-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="d7eb3-141">Откройте Steam и найдите подключаемый модуль Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="d7eb3-142">Перед запуском подключаемого модуля Windows Mixed Reality обязательно закройте SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="d7eb3-143">Запуск подключаемого модуля Windows Mixed Reality автоматически запускает SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="d7eb3-144">Убедитесь, что подключена гарнитура Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-144">Make sure the WMR headset is plugged in.</span></span>

    ![Поиск подключаемого модуля Windows Mixed Reality](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="d7eb3-146">Выберите **Launch** (Запустить) для подключаемого модуля Windows Mixed Reality для SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Подключаемый модуль Windows Mixed Reality](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="d7eb3-148">Будут запущены SteamVR и подключаемый модуль Windows Mixed Reality, а также откроется новое окно отслеживания состояния для гарнитуры Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="d7eb3-149">Дополнительные сведения см. в [документации по использованию Steam с Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Подключаемый модуль Windows Mixed Reality запущен](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="d7eb3-151">В Unity при открытой сцене MRTK выберите **File > Build Settings** (Файл — Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="d7eb3-152">Выполните сборку сцены:</span><span class="sxs-lookup"><span data-stu-id="d7eb3-152">Build the scene</span></span>
    - <span data-ttu-id="d7eb3-153">Щелкните **Add Open Scene** (Добавить открытую сцену).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="d7eb3-154">Убедитесь, что для параметра Platform (Платформа) выбран вариант **Standalone** (Автономная).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="d7eb3-155">Щелкните **Build** (Выполнить сборку).</span><span class="sxs-lookup"><span data-stu-id="d7eb3-155">Select **Build**</span></span>
    - <span data-ttu-id="d7eb3-156">Выберите расположение для новой сборки в проводнике.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-156">Choose the location for the new build in File Explorer</span></span>

    ![Параметры для автономной сборки](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="d7eb3-158">Будет создан новый исполняемый файл Unity, который нужно выбрать в проводнике, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="d7eb3-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity в проводнике](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="d7eb3-160">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d7eb3-160">See also</span></span>

- [<span data-ttu-id="d7eb3-161">Поддержка Android и iOS</span><span class="sxs-lookup"><span data-stu-id="d7eb3-161">Android and iOS Support</span></span>](../features/cross-platform/using-ar-foundation.md)
- [<span data-ttu-id="d7eb3-162">Поддержка Leap Motion</span><span class="sxs-lookup"><span data-stu-id="d7eb3-162">Leap Motion Support</span></span>](../features/cross-platform/leap-motion-mrtk.md)
- [<span data-ttu-id="d7eb3-163">Обнаружение возможностей платформы</span><span class="sxs-lookup"><span data-stu-id="d7eb3-163">Detecting Platform Capabilities</span></span>](../features/cross-platform/detecting-platform-capabilities.md)
