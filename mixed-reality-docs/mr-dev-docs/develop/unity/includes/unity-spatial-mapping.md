---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905711"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>Система отслеживания пространственного положения.

В МРТК ознакомьтесь с руководством по [началу работы с пространственными](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) сведениями о настройке различных наблюдателей пространственной сетки.

Сведения об наблюдателях, посвященных устройствам, см. в разделе [Настройка наблюдателей сетки для устройства](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) .

Сведения об аспектах, посвященных наблюдателям, см. в разделе [понятие сцены наблюдателя](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) .

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)

## <a name="armeshmanager"></a>армешманажер

Арфаундатион Unity предоставляет компонент Армешманажер для встроенной визуализации пространственных сеток. Дополнительные сведения об использовании см. в [документации Unity](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) .

## <a name="xrmeshsubsystem"></a>ксрмешсубсистем

Если вы предпочитаете работать с [Ксрмешсубсистем](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) Unity напрямую, см. Дополнительные сведения об использовании в [документации Unity](https://docs.unity3d.com/Manual/xrsdk-meshing.html) .

## <a name="windows-xr-plugin"></a>Windows Подключаемый модуль XR

Windows Подключаемый модуль XR предоставляет некоторые дополнительные методы расширения для настройки Ксрмешсубсистем, такие как установка ограничивающей сферы или доступ к представлению сетки базовой платформы. Все эти расширения можно найти [в документации Unity](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html).

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Начало работы с встроенными компонентами пространственного сопоставления Unity

Unity предлагает два компонента для простого добавления пространственного сопоставления в приложение, модуль **подготовки** к пространственному сопоставлению и средство **сопоставления пространственных сопоставлений**.

### <a name="spatial-mapping-renderer"></a>Модуль подготовки пространственных сопоставлений

Модуль подготовки пространственных сопоставлений позволяет визуализировать сетку пространственных сопоставлений.

![Модуль подготовки пространственных сопоставлений в Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Конфликт пространственного сопоставления

Механизм обработки пространственных сопоставлений позволяет взаимодействовать с данными (или символами), например физикой, с сеткой пространственных сопоставлений.

![Конфликт пространственного сопоставления в Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Использование встроенных компонентов пространственного сопоставления

Вы можете добавить оба компонента в приложение, если вы хотите визуализировать и взаимодействовать с физическими областями.

Чтобы использовать эти два компонента в приложении Unity, сделайте следующее:

1. Выберите GameObject в центре области, в которой вы хотите определить сетки пространственных поверхностей.
2. В окне инспектора **добавьте компонент**  >  **XR**  >  **пространственное сопоставление пространственного сопоставления**   или модуль **подготовки пространственных сопоставлений**.

Дополнительные сведения об использовании этих компонентов можно найти на <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">сайте документации по Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Переход за пределы встроенных компонентов пространственного сопоставления

Эти компоненты упрощают перетаскивание, чтобы начать работу с пространственным сопоставлением. Если вы хотите продолжить, необходимо изучить два основных пути:

* Чтобы выполнить собственную обработку сетки более низкого уровня, см. раздел, посвященный API сценария низкоуровневого пространственного сопоставления.
* Сведения об анализе сетки более высокого уровня см. в разделе, посвященном библиотеке Спатиалундерстандинг в [микседреалититулкит](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding).

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Использование API пространственного сопоставления Unity с низким уровнем

Если вам требуется больший контроль, чем средства визуализации пространственных сопоставлений и средства для работы с пространственными сопоставлениями, используйте низкоуровневые API пространственных сопоставлений.

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Типы**: *сурфацеобсервер*, *сурфацечанже*, *сурфацедата*, *сурфацеид*

Мы выделили предлагаемый поток для приложения, которое использует API-интерфейсы пространственного сопоставления в следующих разделах.

### <a name="set-up-the-surfaceobservers"></a>Настройка Сурфацеобсервер (s)

Создайте экземпляр одного объекта Сурфацеобсервер для каждой определенной приложением области пространства, для которой требуются данные пространственного сопоставления.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Укажите регион пространства, в котором каждый объект Сурфацеобсервер предоставляет данные, вызвав Сетволумеассфере, Сетволумеасаксисалигнедбокс, Сетволумеасориентедбокс или SetVolumeAsFrustum. Можно переопределить область пространства в будущем, вызвав один из этих методов еще раз.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

При вызове Сурфацеобсервер. Update () необходимо предоставить обработчик для каждой пространственной поверхности в регионе Сурфацеобсервер, для которого в системе пространственных сопоставлений есть новая информация. Обработчик получает для одной пространственной поверхности:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Обработка изменений поверхности

Существует несколько основных вариантов для работы: добавлены и обновлены, которые могут использовать один и тот же путь к коду и удалены.

* В добавленных и обновленных случаях мы добавим или получаем GameObject, представляющий эту сетку, из словаря. Мы создаем структуру Сурфацедата с необходимыми компонентами, затем вызываем Рекуестмешдатаасинк для заполнения GameObject данными сетки, а затем разместите ее в сцене.
* В удаленном варианте мы удаляем GameObject, представляющий эту сетку, из словаря и удалим ее.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Обработка данных готова

Обработчик Ондатареади получает объект Сурфацедата. Ворлданчор, Мешфилтер и (необязательно) Мешколлидер объекты, которые он содержит, отражает Последнее состояние связанной пространственной поверхности. При необходимости анализируйте и (или) [обработайте](../../../design/spatial-mapping.md#mesh-processing) данные сетки, обращаясь к элементу сетки объекта мешфилтер. Отрисовка пространственной поверхности с помощью последней сети и (необязательно) используйте ее для физических конфликтов и райкастс. Важно убедиться, что содержимое Сурфацедата не равно null.

### <a name="start-processing-on-updates"></a>Начать обработку обновлений

Сурфацеобсервер. Update () следует вызывать при задержке, а не во всех кадрах.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
