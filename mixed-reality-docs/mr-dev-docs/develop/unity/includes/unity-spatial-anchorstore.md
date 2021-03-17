---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603396"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ac41e-101">Unity 2020 + Опенкср</span><span class="sxs-lookup"><span data-stu-id="ac41e-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="ac41e-102">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="ac41e-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="ac41e-103">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="ac41e-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="ac41e-104">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:</span><span class="sxs-lookup"><span data-stu-id="ac41e-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="ac41e-105">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ac41e-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="ac41e-106">Полный пример сохранения и несохраненных привязок см. в разделе привязки-> примеры привязок в образце [сцены подключаемого модуля Mixed Reality опенкср](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="ac41e-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](../images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="ac41e-109">Подключаемый модуль XR для Unity 2019/2020 + Windows</span><span class="sxs-lookup"><span data-stu-id="ac41e-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="ac41e-110">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="ac41e-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="ac41e-111">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="ac41e-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="ac41e-112">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксрреференцепоинтсубсистем (Unity 2019) или Ксранчорсубсистем (Unity 2020), подсистему Арреференцепоинтманажер/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="ac41e-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="ac41e-113">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом для Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="ac41e-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="ac41e-114">или для Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="ac41e-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="ac41e-115">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="ac41e-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="ac41e-116">**Пространство имен:** *UnityEngine. XR. WSA. сохраняемость*</span><span class="sxs-lookup"><span data-stu-id="ac41e-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="ac41e-117">**Класс:** *ворлданчорсторе*</span><span class="sxs-lookup"><span data-stu-id="ac41e-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="ac41e-118">Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах.</span><span class="sxs-lookup"><span data-stu-id="ac41e-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="ac41e-119">Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие конкретную привязку.</span><span class="sxs-lookup"><span data-stu-id="ac41e-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="ac41e-120">Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.</span><span class="sxs-lookup"><span data-stu-id="ac41e-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="ac41e-121">Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="ac41e-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="ac41e-122">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="ac41e-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac41e-123">Загрузка данных приложения, относящихся к универсальной привязке, которая предоставляет идентификатор универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="ac41e-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="ac41e-124">Загрузка универсальной привязки из идентификатора</span><span class="sxs-lookup"><span data-stu-id="ac41e-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="ac41e-125">Чтобы сохранить голограммы для будущих сеансов:</span><span class="sxs-lookup"><span data-stu-id="ac41e-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="ac41e-126">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="ac41e-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac41e-127">Сохранение универсальной привязки с указанием идентификатора</span><span class="sxs-lookup"><span data-stu-id="ac41e-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="ac41e-128">Сохранение данных приложения, связанных с привязкой мира, вместе с ИДЕНТИФИКАТОРом</span><span class="sxs-lookup"><span data-stu-id="ac41e-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="ac41e-129">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="ac41e-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="ac41e-130">Вы захотите обеспечить ссылку на Ворлданчорсторе, чтобы вы узнали, когда она готова к выполнению операции.</span><span class="sxs-lookup"><span data-stu-id="ac41e-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="ac41e-131">Так как это асинхронный вызов, потенциально как только запускается, вы хотите вызвать:</span><span class="sxs-lookup"><span data-stu-id="ac41e-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="ac41e-132">Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:</span><span class="sxs-lookup"><span data-stu-id="ac41e-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="ac41e-133">Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.</span><span class="sxs-lookup"><span data-stu-id="ac41e-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="ac41e-134">Сохранение Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="ac41e-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="ac41e-135">Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить.</span><span class="sxs-lookup"><span data-stu-id="ac41e-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="ac41e-136">Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false.</span><span class="sxs-lookup"><span data-stu-id="ac41e-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="ac41e-137">Удалите предыдущее сохранение, прежде чем сохранить новый:</span><span class="sxs-lookup"><span data-stu-id="ac41e-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="ac41e-138">Загрузка Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="ac41e-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="ac41e-139">И для загрузки:</span><span class="sxs-lookup"><span data-stu-id="ac41e-139">And to load:</span></span>

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

<span data-ttu-id="ac41e-140">Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.</span><span class="sxs-lookup"><span data-stu-id="ac41e-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="ac41e-141">Перечисление существующих привязок</span><span class="sxs-lookup"><span data-stu-id="ac41e-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="ac41e-142">Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.</span><span class="sxs-lookup"><span data-stu-id="ac41e-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="ac41e-143">Создание возможностей для мирового масштабирования</span><span class="sxs-lookup"><span data-stu-id="ac41e-143">Building a world-scale experience</span></span>

<span data-ttu-id="ac41e-144">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="ac41e-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ac41e-145">**Тип:** *ворлданчор*</span><span class="sxs-lookup"><span data-stu-id="ac41e-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="ac41e-146">Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты.</span><span class="sxs-lookup"><span data-stu-id="ac41e-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="ac41e-147">Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](../../../design/coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="ac41e-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="ac41e-148">В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.</span><span class="sxs-lookup"><span data-stu-id="ac41e-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="ac41e-149">Добавление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="ac41e-149">Adding a World Anchor</span></span>

<span data-ttu-id="ac41e-150">Чтобы добавить привязку по всему миру, вызовите `AddComponent<WorldAnchor>()` объект Game с преобразованием, которое необходимо привязать в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="ac41e-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="ac41e-151">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="ac41e-151">That's it!</span></span> <span data-ttu-id="ac41e-152">Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="ac41e-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="ac41e-153">Сведения о том, как закрепить это закрепленное расположение в следующем сеансе приложения, см. в статье [Загрузка универсальной привязки](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="ac41e-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="ac41e-154">Удаление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="ac41e-154">Removing a World Anchor</span></span>

<span data-ttu-id="ac41e-155">Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».</span><span class="sxs-lookup"><span data-stu-id="ac41e-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="ac41e-156">Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.</span><span class="sxs-lookup"><span data-stu-id="ac41e-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="ac41e-157">Перемещение привязанного GameObject по всему миру</span><span class="sxs-lookup"><span data-stu-id="ac41e-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="ac41e-158">GameObject нельзя переместить, пока на нем есть универсальная привязка.</span><span class="sxs-lookup"><span data-stu-id="ac41e-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="ac41e-159">Если вам нужно переместить GameObject этот кадр, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ac41e-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="ac41e-160">Дестройиммедиате компонент «мировая привязка»</span><span class="sxs-lookup"><span data-stu-id="ac41e-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="ac41e-161">Перемещение GameObject</span><span class="sxs-lookup"><span data-stu-id="ac41e-161">Move the GameObject</span></span>
3. <span data-ttu-id="ac41e-162">Добавьте новый компонент универсальной привязки к GameObject.</span><span class="sxs-lookup"><span data-stu-id="ac41e-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="ac41e-163">Обработка изменений Локатабилити</span><span class="sxs-lookup"><span data-stu-id="ac41e-163">Handling Locatability Changes</span></span>

<span data-ttu-id="ac41e-164">Ворлданчор не может быть размещаемые в физическом мире на момент времени.</span><span class="sxs-lookup"><span data-stu-id="ac41e-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="ac41e-165">В таком случае Unity не будет обновлять преобразование привязанного объекта.</span><span class="sxs-lookup"><span data-stu-id="ac41e-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="ac41e-166">Это также можно изменить во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="ac41e-166">This also can change while an app is running.</span></span> <span data-ttu-id="ac41e-167">Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.</span><span class="sxs-lookup"><span data-stu-id="ac41e-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="ac41e-168">Чтобы получать уведомления об изменениях локатабилити:</span><span class="sxs-lookup"><span data-stu-id="ac41e-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="ac41e-169">Подпишитесь на событие Онтраккингчанжед</span><span class="sxs-lookup"><span data-stu-id="ac41e-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="ac41e-170">Обработайте событие</span><span class="sxs-lookup"><span data-stu-id="ac41e-170">Handle the event</span></span>

<span data-ttu-id="ac41e-171">Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.</span><span class="sxs-lookup"><span data-stu-id="ac41e-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="ac41e-172">Затем обработайте событие:</span><span class="sxs-lookup"><span data-stu-id="ac41e-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="ac41e-173">Иногда привязки размещаются немедленно.</span><span class="sxs-lookup"><span data-stu-id="ac41e-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="ac41e-174">В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent <WorldAnchor> () возвращает.</span><span class="sxs-lookup"><span data-stu-id="ac41e-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="ac41e-175">В результате событие Онтраккингчанжед не будет запущено.</span><span class="sxs-lookup"><span data-stu-id="ac41e-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="ac41e-176">Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.</span><span class="sxs-lookup"><span data-stu-id="ac41e-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="ac41e-177">Сохранение голограмм для нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="ac41e-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="ac41e-178"><a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.</span><span class="sxs-lookup"><span data-stu-id="ac41e-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="ac41e-179">Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="ac41e-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="ac41e-180">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="ac41e-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ac41e-181">После завершения работы с пространственными привязками Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ac41e-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
