---
title: Развертывание на HoloLens и гарнитурах смешанной реальности Windows
description: Документация по сборке и развертыванию приложений на разных устройствах.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209481"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Развертывание на HoloLens и гарнитурах смешанной реальности Windows

существует два способа развертывания приложений, созданных с помощью мртк, на устройстве windows, на платформе универсальной Windows platform (UWP) и на автономной платформе. приложения, созданные для HoloLens 1 или HoloLens 2, должны быть нацелены на uwp, тогда как приложения, созданные для гарнитур вмр, могут ориентироваться на uwp или Standalone.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>создание и развертывание мртк для HoloLens 1, HoloLens 2 и вмрных гарнитур (UWP)

инструкции по созданию и развертыванию для **HoloLens 1** и **HoloLens 2** (UWP) можно найти в статье [создание приложения на устройстве](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Эти шаги также позволяют развертывать на **ВМР гарнитурах**.

> [!NOTE]
> при развертывании приложения на устройстве в Visual Studio необходимо настроить Visual Studio несколько по-разному в зависимости от устройства. Используются следующие конфигурации
>
>| Платформа | Конфигурация | Архитектура | Целевой объект |
|---|---|---|---|
| HoloLens 2 | Выпуск или образец | ARM64 | Устройство |
| HoloLens 1 | Выпуск или образец | x86. | Устройство |
| ВМР гарнитуры | Выпуск или образец | X64 | Локальный компьютер |

**Совет.** при создании HoloLens 1, HoloLens 2 или вмр рекомендуется, чтобы параметры сборки "целевая версия пакета SDK" и "минимальная версия платформы" были показаны на рисунке ниже:

![Окно сборки](../features/images/getting-started/BuildWindow.png)

Другие параметры могут отличаться (например, конфигурация сборки, архитектура или тип сборки), а некоторые из них вы всегда можете изменить в решении Visual Studio.

Убедитесь, что раскрывающийся список "Target SDK Version" (Целевая версия пакета SDK) содержит вариант "10.0.18362.0". Если он отсутствует, необходимо установить [последнюю версию Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 и HoloLens

если HoloLens приложение отображается в виде двухмерной панели на устройстве, перед развертыванием приложения UWP убедитесь, что в Unity были настроены следующие параметры.

При использовании встроенной поддержки XR (только для Unity 2019):

1. Последовательно выберите Edit > Project Settings, Player (Правка — Параметры проекта — Средство воспроизведения).
1. В разделе **XR Settings** (Параметры смешанной реальности) на вкладке UWP убедитесь, что включен параметр **Virtual Reality Supported** (Поддержка виртуальной реальности), а в список пакетов SDK добавлен SDK **Windows Mixed Reality**.
1. Выполните сборку и развертывание в Visual Studio.

при использовании подключаемых модулей опенкср или Windows XR:

1. Выполните шаги, описанные в статье [Начало работы с XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).
1. Убедитесь, что **DefaultXRSDKConfigurationProfile** выбран в качестве профиля конфигурации.
1. Последовательно выберите **Edit > Project Settings, XR-Plugin Management** (Правка — Параметры проекта — Управление подключаемым модулем смешанной реальности) и убедитесь, что включен параметр **Windows Mixed Reality**.
1. Выполните сборку и развертывание в Visual Studio.

>[!IMPORTANT]
> При использовании Unity 2019.3.x в качестве архитектуры сборки в Visual Studio выберите **ARM64**, а не **ARM**. При стандартных параметрах Unity для версии Unity 2019.3.x из-за ошибки Unity приложение Unity не сможет развернуться на HoloLens, если выбрана архитектура ARM.
>
> Если архитектура ARM является обязательной, выберите **Edit > Project Settings, Player** (Правка — Параметры проекта — Средство воспроизведения), а затем в меню **Other Settings** (Другие настройки) отключите параметр **Graphics Jobs** (Графические задания). Отключение параметра **Graphics Jobs** (Графические задания) позволит развернуть приложение с архитектурой сборки ARM в Unity 2019.3.x, но мы рекомендуем использовать ARM64.
>
> Эта проблема была исправлена в Unity 2019,4 и Unity 2020,3.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Создание и развертывание МРТК на ВМРные гарнитуры (изолированные)

Автономные сборки МРТК можно использовать на гарнитурах ВМР. Автономная сборка для гарнитуры Windows Mixed Reality требует несколько дополнительных действий:

> [!NOTE]
> Пакет SDK XR для Unity также имеет встроенную поддержку Windows Mixed Reality в автономных сборках, но не требует наличия подключаемого модуля SteamVR или Windows Mixed Reality. Описанные здесь действия обязательны для выполнения в устаревшей версии XR в Unity.

1. Установите [Steam](https://store.steampowered.com/about/).
1. Установите [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).
1. Установите [подключаемый модуль Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

### <a name="how-to-use-wmr-plugin"></a>Использование подключаемого модуля Windows Mixed Reality

1. Откройте Steam и найдите подключаемый модуль Windows Mixed Reality.
    - Перед запуском подключаемого модуля Windows Mixed Reality обязательно закройте SteamVR. Запуск подключаемого модуля Windows Mixed Reality автоматически запускает SteamVR.
    - Убедитесь, что подключена гарнитура Windows Mixed Reality.

    ![Поиск подключаемого модуля Windows Mixed Reality](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Выберите **Launch** (Запустить) для подключаемого модуля Windows Mixed Reality для SteamVR.

    ![Подключаемый модуль Windows Mixed Reality](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Будут запущены SteamVR и подключаемый модуль Windows Mixed Reality, а также откроется новое окно отслеживания состояния для гарнитуры Windows Mixed Reality.
    - Дополнительные сведения см. в [документации по использованию Steam с Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).

        ![Подключаемый модуль Windows Mixed Reality запущен](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. В Unity при открытой сцене MRTK выберите **File > Build Settings** (Файл — Параметры сборки).

1. Выполните сборку сцены:
    - Щелкните **Add Open Scene** (Добавить открытую сцену).
    - Убедитесь, что для параметра Platform (Платформа) выбран вариант **Standalone** (Автономная).
    - Щелкните **Build** (Выполнить сборку).
    - Выберите расположение для новой сборки в проводнике.

    ![Параметры для автономной сборки](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Будет создан новый исполняемый файл Unity, который нужно выбрать в проводнике, чтобы запустить приложение.

    ![Unity в проводнике](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>См. также раздел

- [Поддержка Android и iOS](using-ar-foundation.md)
- [Поддержка Leap Motion](leap-motion-mrtk.md)
- [Обнаружение возможностей платформы](detecting-platform-capabilities.md)
