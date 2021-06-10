---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349894"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="0e420-101">Средства блокировки по всему миру (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="0e420-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="0e420-102">По умолчанию средства блокировки мира восстанавливают систему координат Unity относительно физического мира во всех сеансах.</span><span class="sxs-lookup"><span data-stu-id="0e420-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="0e420-103">Это означает, что голограмма будет выглядеть так же, как в физическом мире после выхода и повторного запуска приложения, а голограмма должна снова иметь ту же самую копию.</span><span class="sxs-lookup"><span data-stu-id="0e420-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Компонент контекста блокировки в мире в инспекторе Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="0e420-105">Если приложению требуется более детальное управление, **Автоматическое сохранение** и **Автоматическая загрузка** могут быть отключены в инспекторе, а управление сохраняемостью выполняется из скрипта, как описано в [разделе Сохраняемость документации](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="0e420-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="0e420-106">аранчорманажер</span><span class="sxs-lookup"><span data-stu-id="0e420-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="0e420-107">Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами.</span><span class="sxs-lookup"><span data-stu-id="0e420-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="0e420-108">Ксранчорсторе — это представление сохраненных привязок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="0e420-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="0e420-109">Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.</span><span class="sxs-lookup"><span data-stu-id="0e420-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="0e420-110">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="0e420-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="0e420-111">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="0e420-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="0e420-112">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="0e420-112">Namespaces</span></span>

<span data-ttu-id="0e420-113">Для **Unity 2020 и опенкср**:</span><span class="sxs-lookup"><span data-stu-id="0e420-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="0e420-114">или **Unity 2019/2020 + Windows XR подключаемый модуль**:</span><span class="sxs-lookup"><span data-stu-id="0e420-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="0e420-115">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="0e420-115">Public methods</span></span>

```cs 
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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="0e420-116">Получение ссылки на хранилище привязки</span><span class="sxs-lookup"><span data-stu-id="0e420-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="0e420-117">Чтобы загрузить Ксранчорсторе с **Unity 2020 и опенкср**, используйте метод расширения в ксранчорсубсистем, подсистему аранчорманажер:</span><span class="sxs-lookup"><span data-stu-id="0e420-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="0e420-118">Чтобы загрузить Ксранчорсторе с **Unity 2019/2020 и подключаемым модулем Windows XR**, используйте метод расширения в Ксрреференцепоинтсубсистем (Unity 2019) или Ксранчорсубсистем (Unity 2020), подсистему Арреференцепоинтманажер/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="0e420-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="0e420-119">Загрузка хранилища привязки</span><span class="sxs-lookup"><span data-stu-id="0e420-119">Loading an anchor store</span></span>

<span data-ttu-id="0e420-120">Чтобы загрузить хранилище привязки в **Unity 2020 и опенкср**, выполните доступ к нему из подсистемы аранчорманажер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0e420-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="0e420-121">или с **Unity 2019/2020 и подключаемым модулем Windows XR**:</span><span class="sxs-lookup"><span data-stu-id="0e420-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="0e420-122">Полный пример сохранения и несохраненных привязок см. в примере привязок-> привязок образец GameObject и скрипт Анчорссампле. cs в [примере сцены подключаемого модуля Mixed Reality опенкср](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2):</span><span class="sxs-lookup"><span data-stu-id="0e420-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2):</span></span>

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](../../images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="0e420-125">ворлданчор</span><span class="sxs-lookup"><span data-stu-id="0e420-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="0e420-126">**Ворлданчорсторе** — это ключ к созданию более реалистичных возможностей, в которых голограммы остаются в конкретных реальных местах для экземпляров приложения.</span><span class="sxs-lookup"><span data-stu-id="0e420-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="0e420-127">Пользователи могут затем закреплять отдельные голограммы в любом месте, где бы они ни находились, и найти их позже в одном и том же месте во многих случаях использования приложения.</span><span class="sxs-lookup"><span data-stu-id="0e420-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="0e420-128">**Пространство имен:** *UnityEngine. XR. WSA. сохраняемость*</span><span class="sxs-lookup"><span data-stu-id="0e420-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="0e420-129">**Класс:** *ворлданчорсторе*</span><span class="sxs-lookup"><span data-stu-id="0e420-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="0e420-130">Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах.</span><span class="sxs-lookup"><span data-stu-id="0e420-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="0e420-131">Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие конкретную привязку.</span><span class="sxs-lookup"><span data-stu-id="0e420-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="0e420-132">Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.</span><span class="sxs-lookup"><span data-stu-id="0e420-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="0e420-133">Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0e420-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="0e420-134">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="0e420-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0e420-135">Загрузка данных приложения, относящихся к универсальной привязке, которая предоставляет идентификатор универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="0e420-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="0e420-136">Загрузка универсальной привязки из идентификатора</span><span class="sxs-lookup"><span data-stu-id="0e420-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="0e420-137">Чтобы сохранить голограммы для будущих сеансов:</span><span class="sxs-lookup"><span data-stu-id="0e420-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="0e420-138">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="0e420-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0e420-139">Сохранение универсальной привязки с указанием идентификатора</span><span class="sxs-lookup"><span data-stu-id="0e420-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="0e420-140">Сохранение данных приложения, связанных с привязкой мира, вместе с ИДЕНТИФИКАТОРом</span><span class="sxs-lookup"><span data-stu-id="0e420-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="0e420-141">Получение Ворлданчорсторе</span><span class="sxs-lookup"><span data-stu-id="0e420-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="0e420-142">Вы захотите обеспечить ссылку на Ворлданчорсторе, чтобы вы узнали, когда она готова к выполнению операции.</span><span class="sxs-lookup"><span data-stu-id="0e420-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="0e420-143">Так как это асинхронный вызов, потенциально как только запускается, вы хотите вызвать:</span><span class="sxs-lookup"><span data-stu-id="0e420-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="0e420-144">Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:</span><span class="sxs-lookup"><span data-stu-id="0e420-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="0e420-145">Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.</span><span class="sxs-lookup"><span data-stu-id="0e420-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="0e420-146">Сохранение Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="0e420-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="0e420-147">Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить.</span><span class="sxs-lookup"><span data-stu-id="0e420-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="0e420-148">Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false.</span><span class="sxs-lookup"><span data-stu-id="0e420-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="0e420-149">Удалите предыдущее сохранение, прежде чем сохранить новый:</span><span class="sxs-lookup"><span data-stu-id="0e420-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="0e420-150">Загрузка Ворлданчор</span><span class="sxs-lookup"><span data-stu-id="0e420-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="0e420-151">И для загрузки:</span><span class="sxs-lookup"><span data-stu-id="0e420-151">And to load:</span></span>

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

<span data-ttu-id="0e420-152">Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.</span><span class="sxs-lookup"><span data-stu-id="0e420-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="0e420-153">Перечисление существующих привязок</span><span class="sxs-lookup"><span data-stu-id="0e420-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="0e420-154">Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.</span><span class="sxs-lookup"><span data-stu-id="0e420-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="0e420-155">Сохранение голограмм для нескольких устройств</span><span class="sxs-lookup"><span data-stu-id="0e420-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="0e420-156"><a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.</span><span class="sxs-lookup"><span data-stu-id="0e420-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="0e420-157">Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.</span><span class="sxs-lookup"><span data-stu-id="0e420-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="0e420-158">Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="0e420-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="0e420-159">После завершения работы с пространственными привязками Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="0e420-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
