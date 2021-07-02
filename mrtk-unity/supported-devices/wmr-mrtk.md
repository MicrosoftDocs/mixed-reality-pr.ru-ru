---
title: развертывание на гарнитурах HoloLens и вмр
description: Документация по сборке и развертыванию приложений на разных устройствах.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176370"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="c404b-104">развертывание на гарнитурах HoloLens и вмр</span><span class="sxs-lookup"><span data-stu-id="c404b-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="c404b-105">существует два способа развертывания приложений, созданных с помощью мртк, на устройстве windows, на платформе универсальной Windows platform (UWP) и на автономной платформе.</span><span class="sxs-lookup"><span data-stu-id="c404b-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="c404b-106">приложения, созданные для HoloLens 1 или HoloLens 2, должны быть нацелены на uwp, тогда как приложения, созданные для гарнитур вмр, могут ориентироваться на uwp или Standalone.</span><span class="sxs-lookup"><span data-stu-id="c404b-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="c404b-107">создание и развертывание мртк для HoloLens 1, HoloLens 2 и вмрных гарнитур (UWP)</span><span class="sxs-lookup"><span data-stu-id="c404b-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="c404b-108">инструкции по созданию и развертыванию для **HoloLens 1** и **HoloLens 2** (UWP) можно найти в статье [создание приложения на устройстве](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="c404b-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="c404b-109">Эти шаги также позволяют развертывать на **ВМР гарнитурах**.</span><span class="sxs-lookup"><span data-stu-id="c404b-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="c404b-110">при развертывании приложения на устройстве в Visual Studio необходимо настроить Visual Studio несколько по-разному в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="c404b-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="c404b-111">Используются следующие конфигурации</span><span class="sxs-lookup"><span data-stu-id="c404b-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="c404b-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="c404b-112">Platform</span></span> | <span data-ttu-id="c404b-113">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="c404b-113">Configuration</span></span> | <span data-ttu-id="c404b-114">Архитектура</span><span class="sxs-lookup"><span data-stu-id="c404b-114">Architecture</span></span> | <span data-ttu-id="c404b-115">Целевой объект</span><span class="sxs-lookup"><span data-stu-id="c404b-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="c404b-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c404b-116">HoloLens 2</span></span> | <span data-ttu-id="c404b-117">Выпуск или образец</span><span class="sxs-lookup"><span data-stu-id="c404b-117">Release or Master</span></span> | <span data-ttu-id="c404b-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="c404b-118">ARM64</span></span> | <span data-ttu-id="c404b-119">Устройство</span><span class="sxs-lookup"><span data-stu-id="c404b-119">Device</span></span> |
| <span data-ttu-id="c404b-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="c404b-120">HoloLens 1</span></span> | <span data-ttu-id="c404b-121">Выпуск или образец</span><span class="sxs-lookup"><span data-stu-id="c404b-121">Release or Master</span></span> | <span data-ttu-id="c404b-122">x86</span><span class="sxs-lookup"><span data-stu-id="c404b-122">x86</span></span> | <span data-ttu-id="c404b-123">Устройство</span><span class="sxs-lookup"><span data-stu-id="c404b-123">Device</span></span> |
| <span data-ttu-id="c404b-124">ВМР гарнитуры</span><span class="sxs-lookup"><span data-stu-id="c404b-124">WMR Headsets</span></span> | <span data-ttu-id="c404b-125">Выпуск или образец</span><span class="sxs-lookup"><span data-stu-id="c404b-125">Release or Master</span></span> | <span data-ttu-id="c404b-126">X64</span><span class="sxs-lookup"><span data-stu-id="c404b-126">x64</span></span> | <span data-ttu-id="c404b-127">Локальный компьютер</span><span class="sxs-lookup"><span data-stu-id="c404b-127">Local Machine</span></span> |

<span data-ttu-id="c404b-128">**Совет.** при создании HoloLens 1, HoloLens 2 или вмр рекомендуется, чтобы параметры сборки "целевая версия пакета SDK" и "минимальная версия платформы" были показаны на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="c404b-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Окно сборки](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="c404b-130">Другие параметры могут отличаться (например, конфигурация сборки, архитектура или тип сборки), а некоторые из них вы всегда можете изменить в решении Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c404b-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="c404b-131">Убедитесь, что раскрывающийся список "Target SDK Version" (Целевая версия пакета SDK) содержит вариант "10.0.18362.0". Если он отсутствует, необходимо установить [последнюю версию Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="c404b-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="c404b-132">Unity 2019/2020 и HoloLens</span><span class="sxs-lookup"><span data-stu-id="c404b-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="c404b-133">если HoloLens приложение отображается в виде двухмерной панели на устройстве, перед развертыванием приложения UWP убедитесь, что в Unity были настроены следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="c404b-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="c404b-134">При использовании встроенной поддержки XR (только для Unity 2019):</span><span class="sxs-lookup"><span data-stu-id="c404b-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="c404b-135">Последовательно выберите Edit > Project Settings, Player (Правка — Параметры проекта — Средство воспроизведения).</span><span class="sxs-lookup"><span data-stu-id="c404b-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="c404b-136">В разделе **XR Settings** (Параметры смешанной реальности) на вкладке UWP убедитесь, что включен параметр **Virtual Reality Supported** (Поддержка виртуальной реальности), а в список пакетов SDK добавлен SDK **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="c404b-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="c404b-137">Выполните сборку и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c404b-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="c404b-138">при использовании подключаемых модулей опенкср или Windows XR:</span><span class="sxs-lookup"><span data-stu-id="c404b-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="c404b-139">Выполните шаги, описанные в статье [Начало работы с XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="c404b-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="c404b-140">Убедитесь, что **DefaultXRSDKConfigurationProfile** выбран в качестве профиля конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c404b-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="c404b-141">Последовательно выберите **Edit > Project Settings, XR-Plugin Management** (Правка — Параметры проекта — Управление подключаемым модулем смешанной реальности) и убедитесь, что включен параметр **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="c404b-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="c404b-142">Выполните сборку и развертывание в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c404b-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="c404b-143">При использовании Unity 2019.3.x в качестве архитектуры сборки в Visual Studio выберите **ARM64**, а не **ARM**.</span><span class="sxs-lookup"><span data-stu-id="c404b-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="c404b-144">При стандартных параметрах Unity для версии Unity 2019.3.x из-за ошибки Unity приложение Unity не сможет развернуться на HoloLens, если выбрана архитектура ARM.</span><span class="sxs-lookup"><span data-stu-id="c404b-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="c404b-145">Если архитектура ARM является обязательной, выберите **Edit > Project Settings, Player** (Правка — Параметры проекта — Средство воспроизведения), а затем в меню **Other Settings** (Другие настройки) отключите параметр **Graphics Jobs** (Графические задания).</span><span class="sxs-lookup"><span data-stu-id="c404b-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="c404b-146">Отключение параметра **Graphics Jobs** (Графические задания) позволит развернуть приложение с архитектурой сборки ARM в Unity 2019.3.x, но мы рекомендуем использовать ARM64.</span><span class="sxs-lookup"><span data-stu-id="c404b-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="c404b-147">Эта проблема была исправлена в Unity 2019,4 и Unity 2020,3.</span><span class="sxs-lookup"><span data-stu-id="c404b-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="c404b-148">Создание и развертывание МРТК на ВМРные гарнитуры (изолированные)</span><span class="sxs-lookup"><span data-stu-id="c404b-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="c404b-149">Автономные сборки МРТК можно использовать на гарнитурах ВМР.</span><span class="sxs-lookup"><span data-stu-id="c404b-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="c404b-150">Автономная сборка для гарнитуры Windows Mixed Reality требует несколько дополнительных действий:</span><span class="sxs-lookup"><span data-stu-id="c404b-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="c404b-151">Пакет SDK XR для Unity также имеет встроенную поддержку Windows Mixed Reality в автономных сборках, но не требует наличия подключаемого модуля SteamVR или Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c404b-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="c404b-152">Описанные здесь действия обязательны для выполнения в устаревшей версии XR в Unity.</span><span class="sxs-lookup"><span data-stu-id="c404b-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="c404b-153">Установите [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="c404b-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="c404b-154">Установите [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="c404b-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="c404b-155">Установите [подключаемый модуль Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="c404b-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="c404b-156">Использование подключаемого модуля Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c404b-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="c404b-157">Откройте Steam и найдите подключаемый модуль Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c404b-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="c404b-158">Перед запуском подключаемого модуля Windows Mixed Reality обязательно закройте SteamVR.</span><span class="sxs-lookup"><span data-stu-id="c404b-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="c404b-159">Запуск подключаемого модуля Windows Mixed Reality автоматически запускает SteamVR.</span><span class="sxs-lookup"><span data-stu-id="c404b-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="c404b-160">Убедитесь, что подключена гарнитура Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c404b-160">Make sure the WMR headset is plugged in.</span></span>

    ![Поиск подключаемого модуля Windows Mixed Reality](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="c404b-162">Выберите **Launch** (Запустить) для подключаемого модуля Windows Mixed Reality для SteamVR.</span><span class="sxs-lookup"><span data-stu-id="c404b-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Подключаемый модуль Windows Mixed Reality](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="c404b-164">Будут запущены SteamVR и подключаемый модуль Windows Mixed Reality, а также откроется новое окно отслеживания состояния для гарнитуры Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c404b-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="c404b-165">Дополнительные сведения см. в [документации по использованию Steam с Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="c404b-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Подключаемый модуль Windows Mixed Reality запущен](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="c404b-167">В Unity при открытой сцене MRTK выберите **File > Build Settings** (Файл — Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="c404b-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="c404b-168">Выполните сборку сцены:</span><span class="sxs-lookup"><span data-stu-id="c404b-168">Build the scene</span></span>
    - <span data-ttu-id="c404b-169">Щелкните **Add Open Scene** (Добавить открытую сцену).</span><span class="sxs-lookup"><span data-stu-id="c404b-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="c404b-170">Убедитесь, что для параметра Platform (Платформа) выбран вариант **Standalone** (Автономная).</span><span class="sxs-lookup"><span data-stu-id="c404b-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="c404b-171">Щелкните **Build** (Выполнить сборку).</span><span class="sxs-lookup"><span data-stu-id="c404b-171">Select **Build**</span></span>
    - <span data-ttu-id="c404b-172">Выберите расположение для новой сборки в проводнике.</span><span class="sxs-lookup"><span data-stu-id="c404b-172">Choose the location for the new build in File Explorer</span></span>

    ![Параметры для автономной сборки](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="c404b-174">Будет создан новый исполняемый файл Unity, который нужно выбрать в проводнике, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="c404b-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity в проводнике](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="c404b-176">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c404b-176">See also</span></span>

- [<span data-ttu-id="c404b-177">Поддержка Android и iOS</span><span class="sxs-lookup"><span data-stu-id="c404b-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="c404b-178">Поддержка Leap Motion</span><span class="sxs-lookup"><span data-stu-id="c404b-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="c404b-179">Обнаружение возможностей платформы</span><span class="sxs-lookup"><span data-stu-id="c404b-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)
