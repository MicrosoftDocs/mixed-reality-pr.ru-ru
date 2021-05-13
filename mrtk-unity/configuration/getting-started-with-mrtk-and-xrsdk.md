---
title: жеттингстартедвисмрткандксрсдк
description: Целевая страница для МРТК с КСРСДК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, КСРСДК,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850430"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Приступая к работе с МРТК и XR SDK

Пакет SDK для XR — это [Новый конвейер XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). В Unity 2019 он предоставляет альтернативу существующему конвейеру XR. В Unity 2020 он станет единственным конвейером XR в Unity.

## <a name="prerequisites"></a>Предварительные требования

Чтобы приступить к работе с набором средств Mixed Reality, выполните указанные [шаги](../install-the-tools.md#importing-the-mixed-reality-toolkit) , чтобы добавить мртк в проект.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Настройка Unity для конвейера SDK XR

В настоящее время конвейер XR SDK поддерживает 3 платформы: Windows Mixed Reality, Окулус и Опенкср. В следующих разделах описываются шаги, необходимые для настройки пакета SDK для XR для каждой платформы.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Перейдите в **Диспетчер пакетов Unity** и установите пакет подключаемого модуля Windows XR, который добавляет поддержку Windows Mixed Reality в пакете SDK для XR. При этом будут также извлекаться несколько пакетов зависимостей. 

1. Убедитесь, что следующие компоненты успешно установлены:
   * Управление подключаемым модулем XR
   * Подключаемый модуль Windows XR
   * Устаревшие вспомогательные функции ввода XR

2. Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).
3. Откройте вкладку Управление подключаемым модулем XR в окне Параметры проекта.
4. Перейдите к параметрам универсальная платформа Windows и убедитесь, что в разделе поставщики подключаемых модулей установлен флажок Windows Mixed Reality.
5. Убедитесь, что установлен флажок инициализировать XR при запуске.
6. (**_Требуется для удаленного взаимодействия в в редакторе HoloLens, в противном случае необязательно_**) Перейдите к автономным параметрам и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей. Также убедитесь, что установлен флажок инициализировать XR при запуске.

![Управление подключаемым модулем XR с выбранным изолированной вкладкой](images/xr-management-img-02.png)

7. (**_Необязательно_**) Щелкните вкладку Windows Mixed Reality в разделе Управление подключаемыми модулями XR и создайте профиль настраиваемых параметров, чтобы изменить значения по умолчанию. Если список параметров уже существует, профиль создавать не нужно.

![Управление подключаемым модулем XR с выбранной вкладкой Windows](images/xr-management-img-01.png)

### <a name="oculus"></a>окулус

1. Выполните [инструкции по настройке Окулус Quest в мртк с помощью руководства по конвейеру XR SDK](../supported-devices/oculus-quest-mrtk.md) . В руководстве описаны действия, необходимые для настройки Unity и МРТК для использования конвейера XR SDK для Окулус Quest.

### <a name="openxr-preview"></a>Опенкср (Предварительная версия)

> [!IMPORTANT]
> Опенкср в Unity поддерживается только в Unity 2020,2 и более поздних версиях.
>
> В настоящее время он также поддерживает только сборки x64 и ARM64.

1. Следуйте указаниям в руководстве по [использованию подключаемого модуля Mixed Reality опенкср для Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , включая шаги по настройке управления подключаемым модулем XR и оптимизации для установки подключаемого модуля опенкср в проект. Убедитесь, что следующие компоненты успешно установлены:
   1. Управление подключаемым модулем XR
   1. Подключаемый модуль Опенкср
   1. Подключаемый модуль Опенкср в смешанной реальности
1. Перейдите к разделу Edit > Settings Project.
1. Откройте вкладку Управление подключаемым модулем XR в окне Параметры проекта.
1. Убедитесь, что установлен флажок инициализировать XR при запуске.
1. (**_Необязательно_**) Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите набор функций Microsoft HoloLens.

![Управление подключаемым модулем Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Если у вас уже есть проект, использующий МРТК из УПМ, убедитесь, что следующая строка находится в файле **link.xml** , расположенном в папке Микседреалититулкит. Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> В первоначальном выпуске МРТК и Опенкср поддерживаются только контроллеры движения HoloLens 2 с четкой и Windows Mixed Reality. В будущих выпусках будет добавлена поддержка дополнительного оборудования.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Настройка МРТК для конвейера XR SDK

При использовании Опенкср выберите "Дефаултопенксрконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.

При использовании других сред выполнения XR в конфигурации управления подключаемыми модулями XR, например Windows Mixed Reality или Окулус, выберите "Дефаултксрсдкконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.

При необходимости эти профили устанавливаются с правильными системами и поставщиками. Дополнительные сведения о профилировании и примерах поддержки с помощью пакета SDK для XR см. [в](../features/profiles/profiles.md#xr-sdk) документации по профилям.

Чтобы перенести существующий профиль в пакет SDK для XR, необходимо обновить следующие службы и поставщики данных:

### <a name="camera"></a>Камера

От [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Параметры старой камеры](../features/images/xrsdk/CameraSystemLegacy.png)

значение

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**и**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Параметры камеры пакета SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Входные данные

От [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Устаревшие параметры ввода](../features/images/xrsdk/InputSystemWMRLegacy.png)

значение

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__Опенкср__:

![Параметры ввода Опенкср](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Входные параметры пакета SDK для XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Граница

От [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Устаревшие параметры границ](../features/images/xrsdk/BoundarySystemLegacy.png)

значение

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Параметры границ пакета SDK для XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Поддержка пространственных сведений

От [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Устаревшие параметры пространственной информации о поддержке](../features/images/xrsdk/SpatialAwarenessLegacy.png)

значение

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| Выполняется | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Параметры пространственной осведомленности пакета SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Сопоставления контроллеров

Если вы используете настраиваемые профили сопоставления контроллеров, откройте один из них и запустите команду меню "служебные программы" набора средств для управления смешанной реальности — > Utilities-> обновление->, чтобы убедиться, что определены новые типы контроллеров SDK для XR.

## <a name="see-also"></a>См. также раздел

* [Начало работы с AR Development в Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Начало работы с разработкой VR в Unity](https://docs.unity3d.com/Manual/VROverview.html)