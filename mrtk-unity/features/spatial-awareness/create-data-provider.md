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
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="9381f-104">Создание системного поставщика данных для пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="9381f-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="9381f-105">Система пространственной осведомленности — это расширяемая система для предоставления приложениям данных о реальных средах.</span><span class="sxs-lookup"><span data-stu-id="9381f-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="9381f-106">Чтобы добавить поддержку для новой аппаратной платформы или новой формы данных пространственной осведомленности, может потребоваться пользовательский поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="9381f-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="9381f-107">В этой статье описывается создание [пользовательских поставщиков данных](../../architecture/systems-extensions-providers.md), также называемых пространственными наблюдателями, для системы поддержки пространственной информации.</span><span class="sxs-lookup"><span data-stu-id="9381f-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="9381f-108">Приведенный ниже пример кода относится к [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) реализации класса, которая [полезна при загрузке трехмерных данных сетки в редакторе](spatial-object-mesh-observer.md).</span><span class="sxs-lookup"><span data-stu-id="9381f-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9381f-109">Полный исходный код, используемый в этом примере, можно найти в `Assets/MRTK/Providers/ObjectMeshObserver` папке.</span><span class="sxs-lookup"><span data-stu-id="9381f-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="9381f-110">Пространство имен и структура папок</span><span class="sxs-lookup"><span data-stu-id="9381f-110">Namespace and folder structure</span></span>

<span data-ttu-id="9381f-111">Поставщики данных могут распространяться одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="9381f-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="9381f-112">Сторонние надстройки</span><span class="sxs-lookup"><span data-stu-id="9381f-112">Third party add-ons</span></span>
1. <span data-ttu-id="9381f-113">Часть набора средств Microsoft Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9381f-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="9381f-114">Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения.</span><span class="sxs-lookup"><span data-stu-id="9381f-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="9381f-115">Предложения можно отправлять, создавая новый [тип *запроса функции*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="9381f-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="9381f-116">Надстройка сторонних разработчиков</span><span class="sxs-lookup"><span data-stu-id="9381f-116">Third party add-on</span></span>

<span data-ttu-id="9381f-117">**Пространство имен**</span><span class="sxs-lookup"><span data-stu-id="9381f-117">**Namespace**</span></span>

<span data-ttu-id="9381f-118">Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен.</span><span class="sxs-lookup"><span data-stu-id="9381f-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="9381f-119">Рекомендуется, чтобы пространство имен включало следующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="9381f-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="9381f-120">Название компании, создающее надстройку</span><span class="sxs-lookup"><span data-stu-id="9381f-120">Company name producing the add-on</span></span>
- <span data-ttu-id="9381f-121">Область применения компонента</span><span class="sxs-lookup"><span data-stu-id="9381f-121">Feature area</span></span>

<span data-ttu-id="9381f-122">Например, поставщик данных пространственной осведомленности, созданный и поставляемый компанией Contoso, может иметь значение *contoso. микседреалити. Toolkit. спатиалаваренесс*.</span><span class="sxs-lookup"><span data-stu-id="9381f-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="9381f-123">**Структура папок**</span><span class="sxs-lookup"><span data-stu-id="9381f-123">**Folder structure**</span></span>

<span data-ttu-id="9381f-124">Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="9381f-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Пример структуры папок](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="9381f-126">Где папка *контососпатиалаваренесс* содержит реализацию поставщика данных, папка *редактора* содержит инспектор (и любой другой код, относящийся к редактору Unity), а папка *Profiles* содержит один или несколько предварительно подготовленных объектов Profile.</span><span class="sxs-lookup"><span data-stu-id="9381f-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="9381f-127">Отправка МРТК</span><span class="sxs-lookup"><span data-stu-id="9381f-127">MRTK submission</span></span>

<span data-ttu-id="9381f-128">**Пространство имен**</span><span class="sxs-lookup"><span data-stu-id="9381f-128">**Namespace**</span></span>

<span data-ttu-id="9381f-129">Если в [репозиторий для смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity)отправляется поставщик системных данных пространственной информации, пространство имен **должно** начинаться с Microsoft. микседреалити. Toolkit (например, *Microsoft. микседреалити. Toolkit. спатиалобжектмешобсервер*).</span><span class="sxs-lookup"><span data-stu-id="9381f-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="9381f-130">код должен находиться в папке под МРТК или поставщиками (например, *мртк/providers/обжектмешобсервер*).</span><span class="sxs-lookup"><span data-stu-id="9381f-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="9381f-131">**Структура папок**</span><span class="sxs-lookup"><span data-stu-id="9381f-131">**Folder structure**</span></span>

<span data-ttu-id="9381f-132">Весь код должен находиться в папке под МРТК или поставщиками (например: МРТК/providers/Обжектмешобсервер).</span><span class="sxs-lookup"><span data-stu-id="9381f-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="9381f-133">Определение объекта пространственных данных</span><span class="sxs-lookup"><span data-stu-id="9381f-133">Define the spatial data object</span></span>

<span data-ttu-id="9381f-134">Первым шагом при создании поставщика данных для пространственного отслеживания является определение типа данных (например, сеток или плоскостей), которые будут предоставляться приложениям.</span><span class="sxs-lookup"><span data-stu-id="9381f-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="9381f-135">Все объекты пространственных данных должны реализовывать [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9381f-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="9381f-136">Набор средств Mixed Reality Toolkit предоставляет следующие пространственные объекты, которые можно использовать и расширять в новых поставщиках данных.</span><span class="sxs-lookup"><span data-stu-id="9381f-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="9381f-137">Реализация поставщика данных</span><span class="sxs-lookup"><span data-stu-id="9381f-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="9381f-138">Укажите наследование интерфейса и/или базового класса</span><span class="sxs-lookup"><span data-stu-id="9381f-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="9381f-139">Все поставщики данных пространственных сведений должны реализовывать [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) интерфейс, который указывает минимальные функциональные возможности, необходимые для системы поддержки пространственной информации.</span><span class="sxs-lookup"><span data-stu-id="9381f-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="9381f-140">МРТК Foundation включает класс, [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) который предоставляет реализацию по умолчанию для необходимых функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="9381f-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="9381f-141">Этот [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) интерфейс используется [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) классом, чтобы указать, что он обеспечивает поддержку возможности спатиалаваренессмеш.</span><span class="sxs-lookup"><span data-stu-id="9381f-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="9381f-142">Применение атрибута Микседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="9381f-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="9381f-143">Ключевым шагом при создании поставщика данных пространственного отслеживания является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу.</span><span class="sxs-lookup"><span data-stu-id="9381f-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="9381f-144">Этот шаг позволяет задать профиль и платформы по умолчанию для поставщика данных, если он выбран в профиле сведений о пространственном распознавании, а также имя, путь к папке и многое другое.</span><span class="sxs-lookup"><span data-stu-id="9381f-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="9381f-145">Реализация методов Имикседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="9381f-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="9381f-146">После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9381f-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="9381f-147">[`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)Класс через [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) класс предоставляет только пустые реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) методов.</span><span class="sxs-lookup"><span data-stu-id="9381f-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="9381f-148">Сведения об этих методах обычно относятся к конкретному поставщику данных.</span><span class="sxs-lookup"><span data-stu-id="9381f-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="9381f-149">Поставщик данных должен реализовать следующие методы:</span><span class="sxs-lookup"><span data-stu-id="9381f-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="9381f-150">Реализация логики поставщика данных</span><span class="sxs-lookup"><span data-stu-id="9381f-150">Implement the data provider logic</span></span>

<span data-ttu-id="9381f-151">Следующим шагом является добавление логики поставщика данных путем реализации конкретного интерфейса поставщика данных, например [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="9381f-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="9381f-152">Эта часть поставщика данных обычно зависит от платформы.</span><span class="sxs-lookup"><span data-stu-id="9381f-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="9381f-153">Уведомления об изменениях наблюдения</span><span class="sxs-lookup"><span data-stu-id="9381f-153">Observation change notifications</span></span>

<span data-ttu-id="9381f-154">Чтобы позволить приложениям реагировать на изменения в понимании среды на устройстве, поставщик данных создает события уведомления, как определено в [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="9381f-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="9381f-155">В следующем коде из [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) примеров демонстрируется вызов и событие при добавлении данных сетки.</span><span class="sxs-lookup"><span data-stu-id="9381f-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

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
> <span data-ttu-id="9381f-156">[`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver)Класс не создает события, `OnObservationUpdated` так как трехмерная модель загружается только один раз.</span><span class="sxs-lookup"><span data-stu-id="9381f-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="9381f-157">Реализация в [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) классе предоставляет пример вызова `OnObservationUpdated` события для наблюдаемой сетки.</span><span class="sxs-lookup"><span data-stu-id="9381f-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="9381f-158">Добавить инструментирование профилировщика Unity</span><span class="sxs-lookup"><span data-stu-id="9381f-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="9381f-159">В приложениях смешанной реальности важна производительность.</span><span class="sxs-lookup"><span data-stu-id="9381f-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="9381f-160">Каждый компонент добавляет некоторый объем издержек, при которых должны быть учетные записи приложений.</span><span class="sxs-lookup"><span data-stu-id="9381f-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="9381f-161">Для этого важно, чтобы все поставщики данных пространственных сведений содержат инструментирование профилировщика Unity во внутреннем цикле и часто используемые пути кода.</span><span class="sxs-lookup"><span data-stu-id="9381f-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="9381f-162">Рекомендуется реализовать шаблон, используемый МРТК при инструментировании настраиваемых поставщиков.</span><span class="sxs-lookup"><span data-stu-id="9381f-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

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
> <span data-ttu-id="9381f-163">Имя, используемое для распознавания маркера профилировщика, является произвольным.</span><span class="sxs-lookup"><span data-stu-id="9381f-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="9381f-164">МРТК использует следующий шаблон.</span><span class="sxs-lookup"><span data-stu-id="9381f-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="9381f-165">"[Product] className. methodName-необязательное примечание"</span><span class="sxs-lookup"><span data-stu-id="9381f-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="9381f-166">Для упрощения идентификации конкретных компонентов и методов при анализе трассировок рекомендуется использовать пользовательские поставщики данных с похожим шаблоном.</span><span class="sxs-lookup"><span data-stu-id="9381f-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="9381f-167">Создание профиля и инспектора</span><span class="sxs-lookup"><span data-stu-id="9381f-167">Create the profile and inspector</span></span>

<span data-ttu-id="9381f-168">В наборе средств для смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9381f-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="9381f-169">Определение профиля</span><span class="sxs-lookup"><span data-stu-id="9381f-169">Define the profile</span></span>

<span data-ttu-id="9381f-170">Содержимое профиля должно отражать доступные свойства поставщика данных (например, интервал обновления).</span><span class="sxs-lookup"><span data-stu-id="9381f-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="9381f-171">Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, должны содержаться в профиле.</span><span class="sxs-lookup"><span data-stu-id="9381f-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="9381f-172">Базовые классы рекомендуется, если новый поставщик данных расширяет существующий поставщик.</span><span class="sxs-lookup"><span data-stu-id="9381f-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="9381f-173">Например, [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) расширяет класс, позволяя [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) клиентам предоставлять трехмерную модель для использования в качестве данных среды.</span><span class="sxs-lookup"><span data-stu-id="9381f-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

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

<span data-ttu-id="9381f-174">`CreateAssetMenu`Атрибут можно применить к классу Profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню **Создание**  >    >  **профилей набора средств Mixed Reality**  >   .</span><span class="sxs-lookup"><span data-stu-id="9381f-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="9381f-175">Реализация инспектора</span><span class="sxs-lookup"><span data-stu-id="9381f-175">Implement the inspector</span></span>

<span data-ttu-id="9381f-176">Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля.</span><span class="sxs-lookup"><span data-stu-id="9381f-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="9381f-177">Каждый инспектор профилей должен расширять [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) класс.</span><span class="sxs-lookup"><span data-stu-id="9381f-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="9381f-178">`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.</span><span class="sxs-lookup"><span data-stu-id="9381f-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="9381f-179">Создание определений сборок</span><span class="sxs-lookup"><span data-stu-id="9381f-179">Create assembly definition(s)</span></span>

<span data-ttu-id="9381f-180">Набор средств Mixed Reality использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="9381f-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="9381f-181">Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.</span><span class="sxs-lookup"><span data-stu-id="9381f-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="9381f-182">Используя [структуру папок](#namespace-and-folder-structure) в предыдущем примере, для поставщика данных контососпатиалаваренесс требуется два асмдеф файла.</span><span class="sxs-lookup"><span data-stu-id="9381f-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="9381f-183">Первое определение сборки предназначено для поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="9381f-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="9381f-184">В этом примере он будет называться Контососпатиалаваренесс и будет находиться в папке *контососпатиалаваренесс* в примере.</span><span class="sxs-lookup"><span data-stu-id="9381f-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="9381f-185">Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. Toolkit и других сборок, от которых он зависит.</span><span class="sxs-lookup"><span data-stu-id="9381f-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="9381f-186">В определении сборки Контосоинпутедитор будет указан инспектор профилей и код конкретного редактора.</span><span class="sxs-lookup"><span data-stu-id="9381f-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="9381f-187">Этот файл должен находиться в корневой папке кода редактора.</span><span class="sxs-lookup"><span data-stu-id="9381f-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="9381f-188">В этом примере файл будет находиться в папке *контососпатиалаваренесс\едитор*</span><span class="sxs-lookup"><span data-stu-id="9381f-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="9381f-189">Это определение сборки будет содержать ссылку на сборку Контососпатиалаваренесс, а также:</span><span class="sxs-lookup"><span data-stu-id="9381f-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="9381f-190">Microsoft. Микседреалити. Toolkit</span><span class="sxs-lookup"><span data-stu-id="9381f-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="9381f-191">Microsoft. Микседреалити. Toolkit. Editor. Инспекторы</span><span class="sxs-lookup"><span data-stu-id="9381f-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="9381f-192">Microsoft. Микседреалити. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="9381f-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="9381f-193">Регистрация поставщика данных</span><span class="sxs-lookup"><span data-stu-id="9381f-193">Register the data provider</span></span>

<span data-ttu-id="9381f-194">После создания поставщик данных может быть зарегистрирован в системе пространственной осведомленности, которая будет использоваться в приложении.</span><span class="sxs-lookup"><span data-stu-id="9381f-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Выбор наблюдателя для сетки пространственных объектов](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="9381f-196">Упаковка и распространение</span><span class="sxs-lookup"><span data-stu-id="9381f-196">Packaging and distribution</span></span>

<span data-ttu-id="9381f-197">Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика.</span><span class="sxs-lookup"><span data-stu-id="9381f-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="9381f-198">Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.</span><span class="sxs-lookup"><span data-stu-id="9381f-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="9381f-199">Если поставщик данных отправлен и принят как часть пакета Microsoft Mixed Reality Toolkit, группа Microsoft МРТК будет упаковывать и распространять ее в рамках предложений МРТК.</span><span class="sxs-lookup"><span data-stu-id="9381f-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="9381f-200">См. также</span><span class="sxs-lookup"><span data-stu-id="9381f-200">See also</span></span>

- [<span data-ttu-id="9381f-201">Система отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9381f-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="9381f-202">`IMixedRealitySpatialAwarenessObject` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9381f-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="9381f-203">Класс `BaseSpatialAwarenessObject`</span><span class="sxs-lookup"><span data-stu-id="9381f-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="9381f-204">Класс `SpatialAwarenessMeshObject`</span><span class="sxs-lookup"><span data-stu-id="9381f-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="9381f-205">Класс `SpatialAwarenessPlanarObject`</span><span class="sxs-lookup"><span data-stu-id="9381f-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="9381f-206">`IMixedRealitySpatialAwarenessObserver` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9381f-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="9381f-207">Класс `BaseSpatialObserver`</span><span class="sxs-lookup"><span data-stu-id="9381f-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="9381f-208">`IMixedRealitySpatialAwarenessMeshObserver` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9381f-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="9381f-209">`IMixedRealityDataProvider` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9381f-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="9381f-210">`IMixedRealityCapabilityCheck` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9381f-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
