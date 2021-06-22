---
title: Создание и развертывание в Android и iOS с помощью AR Foundation
description: Документация по настройке МРТК для Android и iOS (Арфаундатион) в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449743"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a>Создание и развертывание в Android и iOS с помощью AR Foundation [экспериментальная версия]

## <a name="install-required-packages"></a>Установка необходимых пакетов

1. Скачайте и импортируйте пакет **Microsoft. микседреалити. Toolkit. Unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) или [диспетчера пакетов Unity](../configuration/usingupm.md) .

1. В диспетчере пакетов Unity (УПМ) установите следующие пакеты:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Комментарии |
    | --- | --- | --- |
    | AR Foundation  <br/> Версия: 1.5.0-Preview 6 | AR Foundation  <br/> Версия: 1.5.0-Preview 6 | Для Unity 2018,4 этот пакет включен в качестве предварительной версии. Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Подключаемый модуль Аркоре XR <br/> Версия: 2.1.2 | Подключаемый модуль ARKit XR <br/> Версия: 2.1.2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Версия: 2.1.8 |  AR Foundation  <br/> Версия: 2.1.8 |
    | Подключаемый модуль Аркоре XR <br/> Версия: 2.1.11 | Подключаемый модуль ARKit XR <br/> Версия: 2.1.9 |

    **Unity 2020.3. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Версия: 3.1.3 |  AR Foundation  <br/> Версия: 4.0.12 |
    | Подключаемый модуль Аркоре XR <br/> Версия: 3.1.4 | Подключаемый модуль ARKit XR <br/> Версия: 4.1.7 |

1. Обновление скриптов МРТК Унитяр определяется путем вызова пункта меню: " **Смешанная реальность > набор средств > служебные программы > унитяр > обновление сценариев** "

    ![Обновление определений скриптов](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Включение поставщика параметров для камеры Unity AR

В следующих шагах предполагается использование объекта Микседреалититулкит. Действия, необходимые для других регистраторов служб, могут отличаться.

1. Выберите объект Микседреалититулкит в иерархии сцены.

    ![МРТК настроенная иерархия сцены](../features/images/MRTK_ConfiguredHierarchy.png)

1. Выберите **Копировать и настроить** , чтобы КЛОНИРОВАТЬ профиль мртк, чтобы включить настраиваемую конфигурацию.

    ![Клонировать профиль МРТК](../features/images/camera-system/CloneProfileARFoundation.png)

1. Выберите **клонировать** рядом с профилем камеры.

    ![Клонировать профиль камеры МРТК](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .

    ![Разверните узел Параметры поставщики.](../features/images/camera-system/ExpandProviders.png)

1. Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .

    ![Развернуть поставщик новых параметров](../features/images/camera-system/ExpandNewProvider.png)

1. Выбор поставщика параметров для камеры Unity AR

    ![Выбор поставщика параметров Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    Дополнительные сведения о настройке поставщика параметров Unity AR для камеры см. в статье [поставщик параметров камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Эта установка проверяет (при запуске приложения), если компоненты AR Foundation находятся в сцене. В противном случае они добавляются автоматически, чтобы обеспечить работу с Аркоре и ARKit.
> Если необходимо задать конкретное поведение, необходимо добавить необходимые компоненты.
> Дополнительные сведения о компонентах и установке AR Foundation см. в этой [документации](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Создание сцены для устройств Android и iOS

1. Убедитесь, что в сцену добавлен поставщик параметров камеры Унитяр.

1. Переключение платформы на Android или iOS в параметрах сборки Unity

1. Убедитесь, что связанный поставщик управления подключаемым модулем XR включен.

    Управление подключаемыми модулями iOS XR:  ![ Управление подключаемыми модулями XR iOS](../features/images/XRManagementiOS.png)

1. Сборка и запуск сцены

## <a name="see-also"></a>См. также

- [Параметры камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md)
