---
title: Начало работы с MRTK и SDK смешанной реальности
description: Целевая страница для МРТК с пакетом SDK для XR
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, ксрсдк, XR SDK
ms.openlocfilehash: 681352ff854598ab34bd9521b46ae9f4e6f42f02
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905756"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Начало работы с MRTK и SDK смешанной реальности

Пакет SDK для XR — это [Новый конвейер XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). В Unity 2019 он предоставляет альтернативу существующему конвейеру XR. В Unity 2020 это единственный конвейер XR в Unity.

## <a name="prerequisites"></a>Необходимые компоненты

чтобы начать работу с набор средств смешанной реальности, выполните указанные [шаги](/windows/mixed-reality/develop/install-the-tools#importing-the-mixed-reality-toolkit) , чтобы добавить мртк в проект.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Настройка Unity для конвейера SDK XR

в настоящее время конвейер XR SDK поддерживает 3 платформы: Windows Mixed Reality, окулус и опенкср. В следующих разделах описываются шаги, необходимые для настройки пакета SDK для XR для каждой платформы.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

перейдите в **диспетчер пакетов Unity** и установите пакет подключаемого модуля Windows XR, который добавляет поддержку Windows Mixed Reality в пакете SDK для XR. При этом будут также извлекаться несколько пакетов зависимостей.

1. Убедитесь, что следующие компоненты успешно установлены:
   * Управление подключаемым модулем XR
   * Windows Подключаемый модуль XR
   * Устаревшие вспомогательные функции ввода XR

2. Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).
3. в окне Project Параметры щелкните вкладку управление подключаемыми модулями XR.
4. перейдите к параметрам универсальная платформа Windows и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей.
5. Убедитесь, что установлен флажок инициализировать XR при запуске.
6. (**_требуется для удаленного взаимодействия в редакторе HoloLens, в противном случае необязательно_**) перейдите к автономным параметрам и убедитесь, что Windows Mixed Reality проверяется в разделе поставщики подключаемых модулей. Также убедитесь, что установлен флажок инициализировать XR при запуске.

    ![Управление подключаемым модулем XR с выбранным изолированной вкладкой](images/xr-management-img-02.png)

7. (**_Необязательно_**) щелкните вкладку Windows Mixed Reality в разделе управление подключаемыми модулями XR и создайте профиль настраиваемых параметров, чтобы изменить значения по умолчанию. Если список параметров уже существует, профиль создавать не нужно.

    ![управление подключаемым модулем XR с выбранной вкладкой Windows](images/xr-management-img-01.png)

### <a name="oculus"></a>окулус

1. Выполните [инструкции по настройке Окулус Quest в мртк с помощью руководства по конвейеру XR SDK](../supported-devices/oculus-quest-mrtk.md) . В руководстве описаны действия, необходимые для настройки Unity и МРТК для использования конвейера XR SDK для Окулус Quest.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> Опенкср в Unity поддерживается только в Unity 2020,2 и более поздних версиях.
> Он также поддерживает только сборки x64, ARM и ARM64.

1. Следуйте указаниям в руководстве по [использованию подключаемого модуля Mixed Reality опенкср для Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , включая шаги по настройке управления подключаемым модулем XR и оптимизации для установки подключаемого модуля опенкср в проект. Убедитесь, что следующие компоненты успешно установлены:
   1. Управление подключаемым модулем XR
   1. Подключаемый модуль Опенкср
   1. Подключаемый модуль Опенкср в смешанной реальности
1. перейдите в раздел Edit > Project Параметры.
1. в окне Project Параметры щелкните вкладку управление подключаемыми модулями XR.
1. Убедитесь, что установлен флажок инициализировать XR при запуске.
1. (**_Необязательно_**) если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP и выберите Microsoft HoloLens наборе функций.

![Опенкср управления подключаемым модулем](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Если у вас уже есть проект, использующий МРТК из УПМ, убедитесь, что следующая строка находится в файле **link.xml** , расположенном в папке Микседреалититулкит. Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> в первоначальном выпуске мртк и опенкср поддерживаются только HoloLens 2 наWindows Mixed Realityные контроллеры движения. В будущих выпусках будет добавлена поддержка дополнительного оборудования.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Настройка МРТК для конвейера XR SDK

::: moniker range=">= mrtkunity-2021-05"
Используйте любой из профилей МРТК по умолчанию, которые настроены для всех конвейеров XR Unity. Предыдущие "Дефаултопенксрконфигуратионпрофиле" и "Дефаултксрсдкконфигуратионпрофиле" теперь помечены как устаревшие.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
При использовании Опенкср выберите "Дефаултопенксрконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.

при использовании других сред выполнения XR в конфигурации управления подключаемыми модулями XR, например Windows Mixed Reality или окулус, выберите "дефаултксрсдкконфигуратионпрофиле" в качестве активного профиля или клонировать его для внесения настроек.

При необходимости эти профили устанавливаются с правильными системами и поставщиками. Дополнительные сведения о профилировании и примерах поддержки с помощью пакета SDK для XR см. [в](../features/profiles/profiles.md#xr-sdk) документации по профилям.
::: moniker-end

Чтобы перенести существующий профиль в пакет SDK для XR, необходимо обновить следующие службы и поставщики данных.
::: moniker range=">= mrtkunity-2021-05"
Вы сможете увидеть новые поставщики данных на вкладке XR SDK в Unity 2019 или в основном представлении/только в Unity 2020 +, где не существует устаревшей версии XR.

![Вкладка XR SDK](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Камера

::: moniker range=">= mrtkunity-2021-05"
Добавление следующих поставщиков данных
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
От [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Параметры старой камеры](../features/images/xrsdk/CameraSystemLegacy.png)

значение
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Параметры камеры пакета SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Входные данные

::: moniker range=">= mrtkunity-2021-05"
Добавление следующих поставщиков данных
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
От [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Устаревшие параметры ввода](../features/images/xrsdk/InputSystemWMRLegacy.png)

значение
::: moniker-end

| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__Опенкср__:

![Параметры ввода Опенкср](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Входные параметры пакета SDK для XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Граница

::: moniker range=">= mrtkunity-2021-05"
Добавление следующих поставщиков данных
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
От [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Устаревшие параметры границ](../features/images/xrsdk/BoundarySystemLegacy.png)

значение
::: moniker-end

| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Параметры границ пакета SDK для XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Отслеживание пространственного положения

::: moniker range=">= mrtkunity-2021-05"
Добавление следующих поставщиков данных
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
От [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Устаревшие параметры пространственной информации о поддержке](../features/images/xrsdk/SpatialAwarenessLegacy.png)

значение
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (для UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (для UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (для не-UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Подключаемый модуль Опенкср | Windows Подключаемый модуль XR |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Параметры пространственной осведомленности пакета SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Сопоставления контроллеров

если вы используете настраиваемые профили сопоставления контроллеров, откройте один из них и запустите команду меню "служебные программы набор средств-> Utilities-> обновления->", чтобы убедиться, что определены новые типы контроллеров SDK XR.

## <a name="see-also"></a>См. также

* [Начало работы с AR Development в Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Начало работы с разработкой VR в Unity](https://docs.unity3d.com/Manual/VROverview.html)