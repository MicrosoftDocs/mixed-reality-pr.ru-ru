---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603396"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + Опенкср](#tab/openxr)

> [!NOTE]
> Эти привязки должны быть сохранены и загружены на одном устройстве. Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.

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

Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Полный пример сохранения и несохраненных привязок см. в разделе привязки-> примеры привязок в образце [сцены подключаемого модуля Mixed Reality опенкср](../openxr-getting-started.md#hololens-2-samples):

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](../images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль XR для Unity 2019/2020 + Windows](#tab/winxr)

> [!NOTE]
> Эти привязки должны быть сохранены и загружены на одном устройстве. Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.

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

Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксрреференцепоинтсубсистем (Unity 2019) или Ксранчорсубсистем (Unity 2020), подсистему Арреференцепоинтманажер/ARAnchorManager:

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом для Unity 2019:

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

или для Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)

**Пространство имен:** *UnityEngine. XR. WSA. сохраняемость*<br>
**Класс:** *ворлданчорсторе*

Ворлданчорсторе позволит сохранить расположение Ворлданчор в сеансах. Чтобы фактически сохранить голограммы в сеансах, необходимо отдельно отследить объекты gameobject, использующие конкретную привязку. Часто имеет смысл создать корневой элемент GameObject с привязкой к международному сопоставлению и иметь в нем голограммы, прикрепленные с помощью смещения локальной позиции.

Чтобы загрузить голограммы из предыдущих сеансов, выполните следующие действия.

1. Получение Ворлданчорсторе
2. Загрузка данных приложения, относящихся к универсальной привязке, которая предоставляет идентификатор универсальной привязки
3. Загрузка универсальной привязки из идентификатора

Чтобы сохранить голограммы для будущих сеансов:

1. Получение Ворлданчорсторе
2. Сохранение универсальной привязки с указанием идентификатора
3. Сохранение данных приложения, связанных с привязкой мира, вместе с ИДЕНТИФИКАТОРом

### <a name="getting-the-worldanchorstore"></a>Получение Ворлданчорсторе

Вы захотите обеспечить ссылку на Ворлданчорсторе, чтобы вы узнали, когда она готова к выполнению операции. Так как это асинхронный вызов, потенциально как только запускается, вы хотите вызвать:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

Сторелоадед в этом случае — наш обработчик для момента завершения загрузки Ворлданчорсторе:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Теперь у нас есть ссылка на Ворлданчорсторе, которую мы будем использовать для сохранения и загрузки конкретных привязок мира.

### <a name="saving-a-worldanchor"></a>Сохранение Ворлданчор

Чтобы сохранить, нужно просто присвоить имя сохраненному и передать его в Ворлданчор, прежде чем мы хотим сохранить. Примечание. попытка сохранить две привязки в одной строке завершится ошибкой (хранилище. При сохранении будет возвращено значение false. Удалите предыдущее сохранение, прежде чем сохранить новый:

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

### <a name="loading-a-worldanchor"></a>Загрузка Ворлданчор

И для загрузки:

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

Кроме того, можно использовать Store. Удалите (), чтобы удалить привязку, сохраненную ранее, и сохранить ее. Clear () для удаления всех ранее сохраненных данных.

### <a name="enumerating-existing-anchors"></a>Перечисление существующих привязок

Чтобы обнаружить ранее сохраненные привязки, вызовите Жеталлидс.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a>Создание возможностей для мирового масштабирования

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип:** *ворлданчор*

Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты. Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](../../../design/coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](../../../design/coordinate-systems.md#spatial-anchor-persistence).

В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.

### <a name="adding-a-world-anchor"></a>Добавление универсальной привязки

Чтобы добавить привязку по всему миру, вызовите `AddComponent<WorldAnchor>()` объект Game с преобразованием, которое необходимо привязать в реальном мире.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Вот и все! Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание. Сведения о том, как закрепить это закрепленное расположение в следующем сеансе приложения, см. в статье [Загрузка универсальной привязки](#loading-a-worldanchor) .

### <a name="removing-a-world-anchor"></a>Удаление универсальной привязки

Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Перемещение привязанного GameObject по всему миру

GameObject нельзя переместить, пока на нем есть универсальная привязка. Если вам нужно переместить GameObject этот кадр, сделайте следующее:

1. Дестройиммедиате компонент «мировая привязка»
2. Перемещение GameObject
3. Добавьте новый компонент универсальной привязки к GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Обработка изменений Локатабилити

Ворлданчор не может быть размещаемые в физическом мире на момент времени. В таком случае Unity не будет обновлять преобразование привязанного объекта. Это также можно изменить во время работы приложения. Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.

Чтобы получать уведомления об изменениях локатабилити:

1. Подпишитесь на событие Онтраккингчанжед
2. Обработайте событие

Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Затем обработайте событие:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Иногда привязки размещаются немедленно. В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent <WorldAnchor> () возвращает. В результате событие Онтраккингчанжед не будет запущено. Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>Сохранение голограмм для нескольких устройств

<a href="/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.  Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.
