---
ms.openlocfilehash: ad45cf8df4e51d17533c8e57b9ffe67738676d2af5398dd320cc86be469d5803
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208890"
---
# <a name="world-locking-tools-recommended"></a>[Средства блокировки по всему миру (рекомендуется)](#tab/wlt)

По умолчанию средства блокировки мира восстанавливают систему координат Unity относительно физического мира во всех сеансах. Это означает, что голограмма будет выглядеть так же, как в физическом мире после выхода и повторного запуска приложения, а голограмма должна снова иметь ту же самую копию.

![Компонент контекста блокировки в мире в инспекторе Unity](../../images/world-locking-tools-img-02.png)

Если приложению требуется более детальное управление, **Автоматическое сохранение** и **Автоматическая загрузка** могут быть отключены в инспекторе, а управление сохраняемостью выполняется из скрипта, как описано в [разделе Сохраняемость документации](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

# <a name="aranchormanager"></a>[аранчорманажер](#tab/anchorstore)

Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами. Ксранчорсторе — это представление сохраненных привязок на устройстве. Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.

> [!NOTE]
> Эти привязки должны быть сохранены и загружены на одном устройстве. Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.

### <a name="namespaces"></a>Пространства имен

Для **Unity 2020 и опенкср**: 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

или **подключаемый модуль XR для Unity 2019/2020 + Windows**: 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Открытые методы

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

### <a name="getting-an-anchor-store-reference"></a>Получение ссылки на хранилище привязки 

Чтобы загрузить Ксранчорсторе с **Unity 2020 и опенкср**, используйте метод расширения в ксранчорсубсистем, подсистему аранчорманажер:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

чтобы загрузить ксранчорсторе с **Unity 2019/2020 и подключаемым модулем Windows XR**, используйте метод расширения в ксрреференцепоинтсубсистем (unity 2019) или ксранчорсубсистем (unity 2020), подсистему арреференцепоинтманажер/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Загрузка хранилища привязки

Чтобы загрузить хранилище привязки в **Unity 2020 и опенкср**, выполните доступ к нему из подсистемы аранчорманажер следующим образом:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

или с **Unity 2019/2020 и Windows подключаемым модулем XR**:

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Полный пример сохранения и несохраненных привязок см. в примере привязок-> привязок образец GameObject и скрипт Анчорссампле. cs в [примере сцены подключаемого модуля Mixed Reality опенкср](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2):

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](../../images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[ворлданчор](#tab/worldanchor)

**Ворлданчорсторе** — это ключ к созданию более реалистичных возможностей, в которых голограммы остаются в конкретных реальных местах для экземпляров приложения. Пользователи могут затем закреплять отдельные голограммы в любом месте, где бы они ни находились, и найти их позже в одном и том же месте во многих случаях использования приложения.

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

## <a name="persisting-holograms-for-multiple-devices"></a>Сохранение голограмм для нескольких устройств

<a href="/azure/spatial-anchors/overview" target="_blank">пространственные привязки Azure</a> можно использовать для создания надежной облачной привязки на основе локальной ворлданчор, которая может быть размещена на нескольких устройствах HoloLens, iOS и Android, даже если эти устройства не находятся одновременно.  Так как облачные привязки являются постоянными, несколько устройств с течением времени могут видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.