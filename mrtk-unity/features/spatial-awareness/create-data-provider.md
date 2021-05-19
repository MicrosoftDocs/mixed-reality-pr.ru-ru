---
title: Создание поставщика данных пространственной осведомленности
description: Описывает создание пользовательских поставщиков данных в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145151"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Создание системного поставщика данных для пространственного отслеживания

Система пространственной осведомленности — это расширяемая система для предоставления приложениям данных о реальных средах. Чтобы добавить поддержку для новой аппаратной платформы или новой формы данных пространственной осведомленности, может потребоваться пользовательский поставщик данных.

В этой статье описывается создание [пользовательских поставщиков данных](../../architecture/systems-extensions-providers.md), также называемых пространственными наблюдателями, для системы поддержки пространственной информации. Приведенный ниже пример кода относится к [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) реализации класса, которая [полезна при загрузке трехмерных данных сетки в редакторе](spatial-object-mesh-observer.md).

> [!NOTE]
> Полный исходный код, используемый в этом примере, можно найти в `Assets/MRTK/Providers/ObjectMeshObserver` папке.

## <a name="namespace-and-folder-structure"></a>Пространство имен и структура папок

Поставщики данных могут распространяться одним из двух способов:

1. Сторонние надстройки
1. Часть набора средств Microsoft Mixed Reality

Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения. Предложения можно отправлять, создавая новый [тип *запроса функции*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Надстройка сторонних разработчиков

**Пространство имен**

Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен. Рекомендуется, чтобы пространство имен включало следующие компоненты.

- Название компании, создающее надстройку
- Область применения компонента

Например, поставщик данных пространственной осведомленности, созданный и поставляемый компанией Contoso, может иметь значение *contoso. микседреалити. Toolkit. спатиалаваренесс*.

**Структура папок**

Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.

![Пример структуры папок](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Где папка *контососпатиалаваренесс* содержит реализацию поставщика данных, папка *редактора* содержит инспектор (и любой другой код, относящийся к редактору Unity), а папка *Profiles* содержит один или несколько предварительно подготовленных объектов Profile.

### <a name="mrtk-submission"></a>Отправка МРТК

**Пространство имен**

Если в [репозиторий для смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity)отправляется поставщик системных данных пространственной информации, пространство имен **должно** начинаться с Microsoft. микседреалити. Toolkit (например, *Microsoft. микседреалити. Toolkit. спатиалобжектмешобсервер*).

 код должен находиться в папке под МРТК или поставщиками (например, *мртк/providers/обжектмешобсервер*).

**Структура папок**

Весь код должен находиться в папке под МРТК или поставщиками (например: МРТК/providers/Обжектмешобсервер).

## <a name="define-the-spatial-data-object"></a>Определение объекта пространственных данных

Первым шагом при создании поставщика данных для пространственного отслеживания является определение типа данных (например, сеток или плоскостей), которые будут предоставляться приложениям.

Все объекты пространственных данных должны реализовывать [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) интерфейс.

Набор средств Mixed Reality Toolkit предоставляет следующие пространственные объекты, которые можно использовать и расширять в новых поставщиках данных.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Реализация поставщика данных

### <a name="specify-interface-andor-base-class-inheritance"></a>Укажите наследование интерфейса и/или базового класса

Все поставщики данных пространственных сведений должны реализовывать [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) интерфейс, который указывает минимальные функциональные возможности, необходимые для системы поддержки пространственной информации. МРТК Foundation включает класс, [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) который предоставляет реализацию по умолчанию для необходимых функциональных возможностей.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> Этот [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) интерфейс используется [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) классом, чтобы указать, что он обеспечивает поддержку возможности спатиалаваренессмеш.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Применение атрибута Микседреалитидатапровидер

Ключевым шагом при создании поставщика данных пространственного отслеживания является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу. Этот шаг позволяет задать профиль и платформы по умолчанию для поставщика данных, если он выбран в профиле сведений о пространственном распознавании, а также имя, путь к папке и многое другое.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Реализация методов Имикседреалитидатапровидер

После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.

> [!NOTE]
> [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)Класс через [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) класс предоставляет только пустые реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) методов. Сведения об этих методах обычно относятся к конкретному поставщику данных.

Поставщик данных должен реализовать следующие методы:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Реализация логики поставщика данных

Следующим шагом является добавление логики поставщика данных путем реализации конкретного интерфейса поставщика данных, например [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Эта часть поставщика данных обычно зависит от платформы.

### <a name="observation-change-notifications"></a>Уведомления об изменениях наблюдения

Чтобы позволить приложениям реагировать на изменения в понимании среды на устройстве, поставщик данных создает события уведомления, как определено в [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) интерфейсе.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 В следующем коде из [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) примеров демонстрируется вызов и событие при добавлении данных сетки.

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver)Класс не создает события, `OnObservationUpdated` так как трехмерная модель загружается только один раз. Реализация в [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) классе предоставляет пример вызова `OnObservationUpdated` события для наблюдаемой сетки.

### <a name="add-unity-profiler-instrumentation"></a>Добавить инструментирование профилировщика Unity

В приложениях смешанной реальности важна производительность. Каждый компонент добавляет некоторый объем издержек, при которых должны быть учетные записи приложений. Для этого важно, чтобы все поставщики данных пространственных сведений содержат инструментирование профилировщика Unity во внутреннем цикле и часто используемые пути кода.

Рекомендуется реализовать шаблон, используемый МРТК при инструментировании настраиваемых поставщиков.

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> Имя, используемое для распознавания маркера профилировщика, является произвольным. МРТК использует следующий шаблон.
>
> "[Product] className. methodName-необязательное примечание"
>
> Для упрощения идентификации конкретных компонентов и методов при анализе трассировок рекомендуется использовать пользовательские поставщики данных с похожим шаблоном.

## <a name="create-the-profile-and-inspector"></a>Создание профиля и инспектора

В наборе средств для смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).

### <a name="define-the-profile"></a>Определение профиля

Содержимое профиля должно отражать доступные свойства поставщика данных (например, интервал обновления). Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, должны содержаться в профиле.

Базовые классы рекомендуется, если новый поставщик данных расширяет существующий поставщик. Например, [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) расширяет класс, позволяя [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) клиентам предоставлять трехмерную модель для использования в качестве данных среды.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

`CreateAssetMenu`Атрибут можно применить к классу Profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню **Создание**  >    >  **профилей набора средств Mixed Reality**  >   .

### <a name="implement-the-inspector"></a>Реализация инспектора

Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля. Каждый инспектор профилей должен расширять [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) класс.

`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Создание определений сборок

Набор средств Mixed Reality использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.

Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.

Используя [структуру папок](#namespace-and-folder-structure) в предыдущем примере, для поставщика данных контососпатиалаваренесс требуется два асмдеф файла.

Первое определение сборки предназначено для поставщика данных. В этом примере он будет называться Контососпатиалаваренесс и будет находиться в папке *контососпатиалаваренесс* в примере. Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. Toolkit и других сборок, от которых он зависит.

В определении сборки Контосоинпутедитор будет указан инспектор профилей и код конкретного редактора. Этот файл должен находиться в корневой папке кода редактора. В этом примере файл будет находиться в папке *контососпатиалаваренесс\едитор* Это определение сборки будет содержать ссылку на сборку Контососпатиалаваренесс, а также:

- Microsoft. Микседреалити. Toolkit
- Microsoft. Микседреалити. Toolkit. Editor. Инспекторы
- Microsoft. Микседреалити. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Регистрация поставщика данных

После создания поставщик данных может быть зарегистрирован в системе пространственной осведомленности, которая будет использоваться в приложении.

![Выбор наблюдателя для сетки пространственных объектов](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Упаковка и распространение

Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика. Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.

Если поставщик данных отправлен и принят как часть пакета Microsoft Mixed Reality Toolkit, группа Microsoft МРТК будет упаковывать и распространять ее в рамках предложений МРТК.

## <a name="see-also"></a>См. также

- [Система отслеживания пространственного положения.](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` взаимодействия](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [Класс `BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [Класс `SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [Класс `SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` взаимодействия](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [Класс `BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` взаимодействия](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` взаимодействия](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` взаимодействия](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
