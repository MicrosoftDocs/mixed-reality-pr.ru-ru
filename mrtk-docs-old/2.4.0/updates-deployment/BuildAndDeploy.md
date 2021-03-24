---
title: Сборка и развертывание
description: Документация по сборке и развертыванию приложений на разных устройствах.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: 4acabe36f1b5cd9c06ee5ff5d4f3cb2681ec8fee
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687744"
---
# <a name="building-and-deploying-mrtk"></a>Сборка и развертывание MRTK

Чтобы запустить приложение на устройстве (HoloLens, Android, iOS и т. д.) как автономное приложение, необходимо выполнить в проекте Unity шаг сборки и развертывания. Сборка и развертывание приложения, в котором используется MRTK, ничем не отличается от сборки и развертывания любого другого приложения Unity. Специальные инструкции для MRTK отсутствуют. Ниже приведены подробные инструкции по сборке и развертыванию приложения Unity для HoloLens.  Сведения о сборке для других платформ см. [здесь](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>Сборка и развертывание MRTK на HoloLens 1 и HoloLens 2 (UWP)

Инструкции по сборке и развертыванию для HoloLens 1 и HoloLens 2 (UWP) можно найти в статье [о сборке приложения на устройстве](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).

**Совет.** При сборке для платформы WMR, HoloLens 1 или HoloLens 2 мы рекомендуем использовать следующие параметры сборки для целевой версии пакета SDK и минимальной версии платформы:

![Окно сборки](../features/Images/getting_started/BuildWindow.png)

Другие параметры могут отличаться (например, конфигурация сборки, архитектура или тип сборки), а некоторые из них вы всегда можете изменить в решении Visual Studio.

Убедитесь, что раскрывающийся список "Target SDK Version" (Целевая версия пакета SDK) содержит вариант "10.0.18362.0". Если он отсутствует, необходимо установить [последнюю версию Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 и HoloLens

Если приложение HoloLens отображается на устройстве в формате двухмерной панели, перед развертыванием приложения UWP убедитесь, что в Unity 2019.3. x были настроены следующие параметры.

При использовании старой версии XR выполните следующие действия:

1. Последовательно выберите Edit > Project Settings, Player (Правка — Параметры проекта — Средство воспроизведения).
1. В разделе **XR Settings** (Параметры смешанной реальности) на вкладке UWP убедитесь, что включен параметр **Virtual Reality Supported** (Поддержка виртуальной реальности), а в список пакетов SDK добавлен SDK **Windows Mixed Reality**.
1. Выполните сборку и развертывание в Visual Studio.

При использовании подключаемого модуля смешанной реальности выполните следующие действия:

1. Выполните шаги, описанные в статье [Начало работы с XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md).
1. Убедитесь, что **DefaultXRSDKConfigurationProfile** выбран в качестве профиля конфигурации.
1. Последовательно выберите **Edit > Project Settings, XR-Plugin Management** (Правка — Параметры проекта — Управление подключаемым модулем смешанной реальности) и убедитесь, что включен параметр **Windows Mixed Reality**.
1. Выполните сборку и развертывание в Visual Studio.

>[!IMPORTANT]
> При использовании Unity 2019.3.x в качестве архитектуры сборки в Visual Studio выберите **ARM64**, а не **ARM**. При стандартных параметрах Unity для версии Unity 2019.3.x из-за ошибки Unity приложение Unity не сможет развернуться на HoloLens, если выбрана архитектура ARM. Подробнее об этой проблеме см. в [системе контроля проблем Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).
>
> Если архитектура ARM является обязательной, выберите **Edit > Project Settings, Player** (Правка — Параметры проекта — Средство воспроизведения), а затем в меню **Other Settings** (Другие настройки) отключите параметр **Graphics Jobs** (Графические задания). Отключение параметра **Graphics Jobs** (Графические задания) позволит развернуть приложение с архитектурой сборки ARM в Unity 2019.3.x, но мы рекомендуем использовать ARM64.

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>Сборка и развертывание MRTK на гарнитуре Windows Mixed Reality

Гарнитура Windows Mixed Reality может использоваться для сборки под универсальную платформу Windows (UWP) или для автономной сборки.  Автономная сборка для гарнитуры Windows Mixed Reality требует несколько дополнительных действий:

> [!NOTE]
> Пакет SDK XR для Unity также имеет встроенную поддержку Windows Mixed Reality в автономных сборках, но не требует наличия подключаемого модуля SteamVR или Windows Mixed Reality. Описанные здесь действия обязательны для выполнения в устаревшей версии XR в Unity.

1. Установите [Steam](https://store.steampowered.com/about/).
1. Установите [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).
1. Установите [подключаемый модуль Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

### <a name="how-to-use-wmr-plugin"></a>Использование подключаемого модуля Windows Mixed Reality

1. Откройте Steam и найдите подключаемый модуль Windows Mixed Reality.
    - Перед запуском подключаемого модуля Windows Mixed Reality обязательно закройте SteamVR. Запуск подключаемого модуля Windows Mixed Reality автоматически запускает SteamVR.
    - Убедитесь, что подключена гарнитура Windows Mixed Reality.

    ![Поиск подключаемого модуля Windows Mixed Reality](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. Выберите **Launch** (Запустить) для подключаемого модуля Windows Mixed Reality для SteamVR.

    ![Подключаемый модуль Windows Mixed Reality](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - Будут запущены SteamVR и подключаемый модуль Windows Mixed Reality, а также откроется новое окно отслеживания состояния для гарнитуры Windows Mixed Reality.
    - Дополнительные сведения см. в [документации по использованию Steam с Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).

        ![Подключаемый модуль Windows Mixed Reality запущен](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. В Unity при открытой сцене MRTK выберите **File > Build Settings** (Файл — Параметры сборки).

1. Выполните сборку сцены:
    - Щелкните **Add Open Scene** (Добавить открытую сцену).
    - Убедитесь, что для параметра Platform (Платформа) выбран вариант **Standalone** (Автономная).
    - Щелкните **Build** (Выполнить сборку).
    - Выберите расположение для новой сборки в проводнике.

    ![Параметры для автономной сборки](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. Будет создан новый исполняемый файл Unity, который нужно выбрать в проводнике, чтобы запустить приложение.

    ![Unity в проводнике](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>См. также раздел

- [Поддержка Android и iOS](../features/CrossPlatform/UsingARFoundation.md)
- [Поддержка Leap Motion](../features/CrossPlatform/LeapMotionMRTK.md)
- [Обнаружение возможностей платформы](../features/DetectingPlatformCapabilities.md)
