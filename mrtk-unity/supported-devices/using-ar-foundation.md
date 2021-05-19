---
title: Использование AR Foundation
description: Документация по использованию Арфаундатион в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, AR Core, AR Kit
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143942"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Настройка МРТК для iOS и Android [экспериментальная версия]

## <a name="install-required-packages"></a>Установка необходимых пакетов

1. Скачайте и импортируйте пакет **Microsoft. микседреалити. Toolkit. Unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) или [диспетчера пакетов Unity](../configuration/usingupm.md) .

1. В диспетчере пакетов Unity (УПМ) установите следующие пакеты:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Примечания |
    | --- | --- | --- |
    | AR Foundation  <br/> Версия: 1.5.0-Preview 6 | AR Foundation  <br/> Версия: 1.5.0-Preview 6 | Для Unity 2018,4 этот пакет включен в качестве предварительной версии. Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Подключаемый модуль Аркоре XR <br/> Версия: 2.1.2 | Подключаемый модуль ARKit XR <br/> Версия: 2.1.2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Версия: 2.1.8 |  AR Foundation  <br/> Версия: 2.1.8 |
    | Подключаемый модуль Аркоре XR <br/> Версия: 2.1.11 | Подключаемый модуль ARKit XR <br/> Версия: 2.1.9 |

    **Unity 2020.1. x (в настоящее время не формально поддерживается), включается только в информационных целях.**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Версия: 3.1.3 |  AR Foundation  <br/> Версия: 3.1.3 |
    | Подключаемый модуль Аркоре XR <br/> Версия: 3.1.4 | Подключаемый модуль ARKit XR <br/> Версия: 3.1.3 |

1. Обновите скрипты МРТК Унитяр, вызвав пункт меню: **Mixed Reality Toolkit > служебные программы > унитяр > определения сценариев обновления**

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

    При переключении платформы вы увидите окно конфигуратора проектов МРТК с параметрами для выбранной платформы.  Нажмите кнопку Применить, чтобы включить параметры, зависящие от платформы.

    Параметры конфигуратора проектов iOS

    ![Конфигуратор проектов iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. После переключения платформы для Android дополнительные действия не выполняются.

1. Если платформа является iOS, измените параметры > проекта > проигрыватель > другие параметры в заголовке оптимизации, **снимите флажок** код обработчика полосковых систем.

    ![Параметры iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > Непроверяемый код механизма полоскового ядра — это краткосрочное решение ошибки в Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).  Мы работаем над долгосрочным решением.

1. Сборка и запуск сцены

## <a name="see-also"></a>См. также

- [Параметры камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md)
