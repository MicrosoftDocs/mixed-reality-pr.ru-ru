---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719819"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="39e8b-101">Unity 2020 + Опенкср</span><span class="sxs-lookup"><span data-stu-id="39e8b-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="39e8b-102">Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами.</span><span class="sxs-lookup"><span data-stu-id="39e8b-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="39e8b-103">Ксранчорсторе — это представление сохраненных привязок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="39e8b-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="39e8b-104">Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.</span><span class="sxs-lookup"><span data-stu-id="39e8b-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="39e8b-105">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="39e8b-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="39e8b-106">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="39e8b-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="39e8b-107">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:</span><span class="sxs-lookup"><span data-stu-id="39e8b-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="39e8b-108">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="39e8b-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="39e8b-109">Полный пример сохранения и несохраненных привязок см. в примере привязок-> привязок образец GameObject и скрипт Анчорссампле. cs в [примере сцены подключаемого модуля Mixed Reality опенкср](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="39e8b-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](../images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="39e8b-112">Подключаемый модуль XR для Unity 2019/2020 + Windows</span><span class="sxs-lookup"><span data-stu-id="39e8b-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="39e8b-113">API, именуемый **ксранчорсторе** , позволяет сохранять привязки между сеансами.</span><span class="sxs-lookup"><span data-stu-id="39e8b-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="39e8b-114">Ксранчорсторе — это представление сохраненных привязок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="39e8b-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="39e8b-115">Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.</span><span class="sxs-lookup"><span data-stu-id="39e8b-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="39e8b-116">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="39e8b-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="39e8b-117">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="39e8b-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="39e8b-118">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксрреференцепоинтсубсистем (Unity 2019) или Ксранчорсубсистем (Unity 2020), подсистему Арреференцепоинтманажер/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="39e8b-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="39e8b-119">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом для Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="39e8b-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="39e8b-120">или для Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="39e8b-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="39e8b-121">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="39e8b-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="39e8b-122">**Ворлданчорсторе** — это ключ к созданию более реалистичных возможностей, в которых голограммы остаются в конкретных реальных местах для экземпляров приложения.</span><span class="sxs-lookup"><span data-stu-id="39e8b-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="39e8b-123">Пользователи могут затем закреплять отдельные голограммы в любом месте, где бы они ни находились, и найти их позже в одном и том же месте во многих случаях использования приложения.</span><span class="sxs-lookup"><span data-stu-id="39e8b-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="39e8b-124">**Пространство имен:** *UnityEngine. XR. WSA. сохраняемость*</span><span class="sxs-lookup"><span data-stu-id="39e8b-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="39e8b-125">**Класс:** *ворлданчорсторе*</span><span class="sxs-lookup"><span data-stu-id="39e8b-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="39e8b-126">Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах.</span><span class="sxs-lookup"><span data-stu-id="39e8b-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="39e8b-127">Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие конкретную привязку.</span><span class="sxs-lookup"><span data-stu-id="39e8b-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="39e8b-128">Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.</span><span class="sxs-lookup"><span data-stu-id="39e8b-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="39e8b-129">Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="39e8b-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="39e8b-130">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="39e8b-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="39e8b-131">Загрузка данных приложения, относящихся к универсальной привязке, которая предоставляет идентификатор универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="39e8b-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="39e8b-132">Загрузка универсальной привязки из идентификатора</span><span class="sxs-lookup"><span data-stu-id="39e8b-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="39e8b-133">Чтобы сохранить голограммы для будущих сеансов:</span><span class="sxs-lookup"><span data-stu-id="39e8b-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="39e8b-134">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="39e8b-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="39e8b-135">Сохранение универсальной привязки с указанием идентификатора</span><span class="sxs-lookup"><span data-stu-id="39e8b-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="39e8b-136">Сохранение данных приложения, связанных с привязкой мира, вместе с ИДЕНТИФИКАТОРом</span><span class="sxs-lookup"><span data-stu-id="39e8b-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="39e8b-137">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="39e8b-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="39e8b-138">Вы захотите обеспечить ссылку на Ворлданчорсторе, чтобы вы узнали, когда она готова к выполнению операции.</span><span class="sxs-lookup"><span data-stu-id="39e8b-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="39e8b-139">Так как это асинхронный вызов, потенциально как только запускается, вы хотите вызвать:</span><span class="sxs-lookup"><span data-stu-id="39e8b-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="39e8b-140">Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:</span><span class="sxs-lookup"><span data-stu-id="39e8b-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="39e8b-141">Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.</span><span class="sxs-lookup"><span data-stu-id="39e8b-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="39e8b-142">Сохранение Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="39e8b-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="39e8b-143">Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить.</span><span class="sxs-lookup"><span data-stu-id="39e8b-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="39e8b-144">Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false.</span><span class="sxs-lookup"><span data-stu-id="39e8b-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="39e8b-145">Удалите предыдущее сохранение, прежде чем сохранить новый:</span><span class="sxs-lookup"><span data-stu-id="39e8b-145">Delete the previous save before saving the new one:</span></span>

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="39e8b-146">Загрузка Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="39e8b-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="39e8b-147">И для загрузки:</span><span class="sxs-lookup"><span data-stu-id="39e8b-147">And to load:</span></span>

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

<span data-ttu-id="39e8b-148">Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.</span><span class="sxs-lookup"><span data-stu-id="39e8b-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="39e8b-149">Перечисление существующих привязок</span><span class="sxs-lookup"><span data-stu-id="39e8b-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="39e8b-150">Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.</span><span class="sxs-lookup"><span data-stu-id="39e8b-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="39e8b-151">Сохранение голограмм для нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="39e8b-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="39e8b-152"><a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.</span><span class="sxs-lookup"><span data-stu-id="39e8b-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="39e8b-153">Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="39e8b-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="39e8b-154">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="39e8b-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="39e8b-155">После завершения работы с пространственными привязками Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="39e8b-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
