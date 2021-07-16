---
title: Создание поставщика параметров камеры
description: Поставщик данных для параметров камеры в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 2151887a6162239e993634d5d346065362f1c428
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282034"
---
# <a name="creating-a-camera-settings-provider"></a>Создание поставщика параметров камеры

Система камеры является расширяемой системой для обеспечения поддержки конфигураций камер, зависящих от платформы. Чтобы добавить поддержку новой конфигурации камеры, может потребоваться поставщик настраиваемых параметров.

> [!NOTE]
> Полный исходный код, используемый в этом примере, можно найти в папке **мртк/providers/унитяр** .

## <a name="namespace-and-folder-structure"></a>Пространство имен и структура папок

Поставщики данных могут распространяться одним из двух способов:

1. Сторонние надстройки
1. в составе Microsoft Mixed Reality набор средств

Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения. Предложения можно отправлять, создавая новый [тип *запроса функции*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Сторонние надстройки

**Пространство имен**

Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен. Рекомендуется, чтобы пространство имен включало следующие компоненты.

- Название компании, создающее надстройку
- Область применения компонента

например, поставщик параметров камеры, созданный и поставляемый компанией contoso, может иметь значение *Contoso. микседреалити. набор средств. Camera»*.

**Структура папок**

Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.

![Пример структуры папок](../images/camera-system/ExampleProviderFolderStructure.png)

Где папка *контосокамера* содержит реализацию поставщика данных, папка *редактора* содержит инспектор (и любой другой код, относящийся к редактору Unity), а папка *Profiles* содержит один или несколько предварительно подготовленных объектов Profile.

### <a name="mrtk-submission"></a>Отправка МРТК

**Пространство имен**

если поставщик параметров камеры отправляется в [репозиторий "смешанная реальность" набор средств](https://github.com/Microsoft/MixedRealityToolkit-Unity), пространство имен **должно** начинаться с Microsoft. микседреалити. набор средств (например: *Microsoft. микседреалити. набор средств. Камерасистем*).

**Структура папок**

Весь код должен находиться в папке под МРТК или поставщиками (например: МРТК/providers/Унитяр).

## <a name="define-the-camera-settings-object"></a>Определение объекта параметров камеры

Первым шагом в создании поставщика параметров камеры является определение типа данных (например, сеток или плоскостей), которые будут предоставляться приложениям.

Все объекты пространственных данных должны реализовывать [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) интерфейс.

## <a name="implement-the-settings-provider"></a>Реализация поставщика параметров

### <a name="specify-interface-andor-base-class-inheritance"></a>Укажите наследование интерфейса и/или базового класса

Все поставщики параметров камеры должны реализовывать [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) интерфейс, который указывает минимальную функциональность, требуемую для системы камеры. МРТК Foundation включает класс, [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) который предоставляет реализацию требуемой функциональности по умолчанию.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Применение атрибута Микседреалитидатапровидер

Ключевым шагом при создании поставщика параметров камеры является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу. Этот шаг позволяет задать профиль и платформы по умолчанию для поставщика данных, если он выбран в профиле системы камеры, а также имя, путь к папке и т. д.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Реализация методов Имикседреалитидатапровидер

После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.

> [!NOTE]
> [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)Класс через [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) класс предоставляет пустые реализации для [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) методов. Сведения об этих методах обычно относятся к конкретному поставщику данных.

Поставщик данных должен реализовать следующие методы:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Не все поставщики параметров потребует реализации всех этих методов. Настоятельно рекомендуется `Destroy()` и `Initialize()` реализовывать как минимум.

### <a name="implement-the-data-provider-logic"></a>Реализация логики поставщика данных

Следующим шагом является добавление логики поставщика параметров путем реализации [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Эта часть поставщика данных, как правило, зависит от конфигурации камеры.

## <a name="create-the-profile-and-inspector"></a>Создание профиля и инспектора

в набор средств смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).

### <a name="define-the-profile"></a>Определение профиля

Содержимое профиля должно отражать параметры конфигурации, выбираемые разработчиком. Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, также должны содержаться в профиле.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

`CreateAssetMenu`атрибут можно применить к классу profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню " **создание**  >  **ресурсов**" в набор средств "профили"  >  **смешанной реальности**  >   .

### <a name="implement-the-inspector"></a>Реализация инспектора

Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля. Каждый инспектор профилей должен расширять [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) класс.

`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Создание определений сборок

набор средств смешанной реальности использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.

Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.

Используя [структуру папок](#namespace-and-folder-structure) в предыдущем примере, для поставщика данных контосокамера требуется два асмдеф файла.

Первое определение сборки предназначено для поставщика данных. В этом примере он будет называться Контосокамера и будет находиться в папке *контосокамера* в примере. Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. набор средств и другие сборки, от которых он зависит.

В определении сборки Контосокамераедитор будет указан инспектор профилей и код конкретного редактора. Этот файл должен находиться в корневой папке кода редактора. В этом примере файл будет находиться в папке *контосокамера\едитор* Это определение сборки будет содержать ссылку на сборку Контосокамера, а также:

- Microsoft. Микседреалити. набор средств
- Microsoft. Микседреалити. набор средств. Редактор. Инспекторы
- Microsoft. Микседреалити. набор средств. Редактор. Utilities

## <a name="register-the-data-provider"></a>Регистрация поставщика данных

После создания поставщик данных можно зарегистрировать в системе камеры для использования в приложении.

![Выбор поставщика параметров камеры](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Упаковка и распространение

Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика. Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.

если поставщик данных отправлен и принят как часть пакета microsoft Mixed Reality набор средств, группа microsoft мртк будет упаковывать и распространять ее в рамках предложений мртк.

## <a name="see-also"></a>См. также

- [Обзор системы камеры](camera-system-overview.md)
- [Класс `BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` взаимодействия](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` взаимодействия](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
