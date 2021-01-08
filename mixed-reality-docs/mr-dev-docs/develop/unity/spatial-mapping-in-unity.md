---
title: Пространственное сопоставление в Unity
description: Узнайте, как использовать и управлять отрисовкой и конфликтом с реальной геометрией в приложениях Unity Mixed Reality.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, пространственное сопоставление, модуль подготовки отчетов, средство визуализации, сетка, сканирование, компонент, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств для смешанной реальности
ms.openlocfilehash: b4c45ba91a3e864c8cd29f3ebc3396d0250948f4
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009294"
---
# <a name="spatial-mapping-in-unity"></a>Пространственное сопоставление в Unity

[пространственное сопоставление](../../design/spatial-mapping.md) позволяет извлекать сетчатые треугольники, представляющие поверхности мира на устройстве HoloLens. Вы можете использовать данные Surface для размещения, перекрытия и анализа помещений, чтобы придать проектам Unity дополнительный четкое.

Unity включает полную поддержку пространственного сопоставления, которое предоставляется разработчикам следующими способами:
1. Компоненты пространственного сопоставления, доступные в Микседреалититулкит, которые предоставляют удобный и быстрый путь для начала работы с пространственным сопоставлением.
2. API-интерфейсы пространственного сопоставления нижнего уровня, обеспечивающие полный контроль и обеспечивающие более сложную настройку для конкретного приложения.

Чтобы использовать пространственное сопоставление в приложении, в AppxManifest необходимо задать возможность Спатиалперцептион.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Возможность</strong></td>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (первый общий)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>пространственное сопоставление</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a>Настройка возможности Спатиалперцептион

Чтобы приложение использовало данные пространственного сопоставления, необходимо включить возможность Спатиалперцептион.

Как включить функцию Спатиалперцептион:
1. В редакторе Unity откройте панель **"Параметры проигрывателя"** (измените > параметры проекта > Player).
2. Выберите на вкладке **"Магазин Windows"**
3. Разверните узел **"Параметры публикации"** и проверьте возможность **"спатиалперцептион** " в списке **"возможности"** .

> [!NOTE]
> Если вы уже экспортировали проект Unity в решение Visual Studio, необходимо либо экспортировать в новую папку, либо вручную [установить эту возможность в appxmanifest в Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Для пространственного сопоставления также требуется Maxversiontested укажите установленную по меньшей мере 10.0.10586.0:
1. В Visual Studio щелкните правой кнопкой мыши **Package. appxmanifest** в Обозреватель решений и выберите **Просмотреть код** .
2. Найдите строку с указанием **TargetDeviceFamily** и измените **maxversiontested укажите установленную = "10.0.10240.0"** на **maxversiontested укажите установленную = "10.0.10586.0"** .
3. **Сохраните** пакет. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Начало работы с встроенными компонентами пространственного сопоставления Unity

Unity предлагает два компонента для простого добавления пространственного сопоставления в приложение, модуль **подготовки** к пространственному сопоставлению и средство **сопоставления пространственных сопоставлений**.

### <a name="spatial-mapping-renderer"></a>Модуль подготовки пространственных сопоставлений

Модуль подготовки пространственных сопоставлений позволяет визуализировать сетку пространственных сопоставлений.

![Модуль подготовки пространственных сопоставлений в Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Конфликт пространственного сопоставления

Механизм обработки пространственных сопоставлений позволяет взаимодействовать с данными (или символами), например физикой, с сеткой пространственных сопоставлений.

![Конфликт пространственного сопоставления в Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Использование встроенных компонентов пространственного сопоставления

Вы можете добавить оба компонента в приложение, если вы хотите визуализировать и взаимодействовать с физическими областями.

Чтобы использовать эти два компонента в приложении Unity, сделайте следующее:
1. Выберите GameObject в центре области, в которой вы хотите определить сетки пространственных поверхностей.
2. В окне инспектора **добавьте компонент**  >  **XR**  >  **пространственное сопоставление пространственного сопоставления** или модуль **подготовки пространственных сопоставлений**.

Дополнительные сведения об использовании этих компонентов можно найти на <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">сайте документации по Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Переход за пределы встроенных компонентов пространственного сопоставления

Эти компоненты упрощают перетаскивание, чтобы начать работу с пространственным сопоставлением.  Если вы хотите продолжить, необходимо изучить два основных пути:
* Чтобы выполнить собственную обработку сетки более низкого уровня, см. раздел, посвященный API сценария низкоуровневого пространственного сопоставления.
* Сведения об анализе сетки более высокого уровня см. в разделе, посвященном библиотеке Спатиалундерстандинг в <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">микседреалититулкит</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Использование API пространственного сопоставления Unity с низким уровнем

Если вам требуется больший контроль, чем средства визуализации пространственных сопоставлений и средства для работы с пространственными сопоставлениями, используйте низкоуровневые API пространственных сопоставлений.

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Типы**: *сурфацеобсервер*, *сурфацечанже*, *сурфацедата*, *сурфацеид*

Мы выделили предлагаемый поток для приложения, которое использует API-интерфейсы пространственного сопоставления в следующих разделах.

### <a name="set-up-the-surfaceobservers"></a>Настройка Сурфацеобсервер (s)

Создайте экземпляр одного объекта Сурфацеобсервер для каждой определенной приложением области пространства, для которой требуются данные пространственного сопоставления.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Укажите регион пространства, в котором каждый объект Сурфацеобсервер будет предоставлять данные, вызвав либо Сетволумеассфере, Сетволумеасаксисалигнедбокс, Сетволумеасориентедбокс, либо SetVolumeAsFrustum. Можно переопределить область пространства в будущем, просто вызвав один из этих методов снова.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

При вызове Сурфацеобсервер. Update () необходимо предоставить обработчик для каждой пространственной поверхности в регионе Сурфацеобсервер, для которого в системе пространственных сопоставлений есть новая информация. Обработчик получает для одной пространственной поверхности:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Обработка изменений поверхности

Существует несколько основных вариантов для добавления и обновления, которые могут использовать один и тот же путь к коду и удалены.
* В добавленных и обновленных случаях мы добавляем или получаем GameObject, представляющий эту сетку, из словаря, создаем структуру Сурфацедата с необходимыми компонентами, а затем вызываем Рекуестмешдатаасинк для заполнения GameObject данными сетки и положением в сцене.
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
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
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

Обработчик Ондатареади получает объект Сурфацедата. Ворлданчор, Мешфилтер и (необязательно) Мешколлидер объекты, которые он содержит, отражает Последнее состояние связанной пространственной поверхности. При необходимости анализируйте и (или) [обработайте](../../design/spatial-mapping.md#mesh-processing) данные сетки, обращаясь к элементу сетки объекта мешфилтер. Отрисовка пространственной поверхности с помощью последней сети и (необязательно) используйте ее для физических конфликтов и райкастс. Важно убедиться, что содержимое Сурфацедата не равно null.

### <a name="start-processing-on-updates"></a>Начать обработку обновлений

Сурфацеобсервер. Update () следует вызывать при задержке, а не во всех кадрах.

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Анализ сетки более высокого уровня: Спатиалундерстандинг

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Микседреалититулкит</a> — это набор служебного кода для holographic-интерфейсов, созданных на основе более holographic-API Unity.

### <a name="spatial-understanding"></a>Пространственное понимание

При помещении голограмм в физический мир часто желательно выйти за пределы сетки и поверхностей пространственного сопоставления. Когда размещение выполняется процедурно, желательно более высокий уровень понимания окружающей среды. Обычно это требует принятия решений о том, что такое этаж, потолк и стенки. Кроме того, у вас есть возможность оптимизировать с учетом набора ограничений на размещение, чтобы определить наиболее подходящие физические расположения для holographic объектов.

Во время разработки Конкер и фрагментов асобо Studios столкнулись с этой проблемой, разрабатывая Поиск решения для комнаты. Каждая из этих игр имела потребность в конкретных играх, но они являются общими ключевыми технологиями для пространственного понимания. Библиотека Холотулкит. Спатиалундерстандинг инкапсулирует эту технологию, позволяя быстро находить пустые пробелы в стенах, размещать объекты в самом потолке, указывать место для размещения символа и множество других пространственных запросов.

Весь исходный код включен, что позволяет настроить его в своих целях и поделиться изменениями с сообществом. Код для поиска решения C++ был заключен в библиотеку DLL UWP и предоставлен в Unity с помощью Drop в prefab, который содержится в Микседреалититулкит.

### <a name="understanding-modules"></a>Основные сведения о модулях

Существует три основных интерфейса, предоставляемых модулем: топология простых и пространственных запросов, форма для обнаружения объектов и поисковый запрос на размещение объектов для размещения наборов объектов на основе ограничений. Каждый из этих способов описан ниже. В дополнение к трем интерфейсам основного модуля можно использовать интерфейс приведения лучей, чтобы извлечь типы областей с тегами, а также можно скопировать пользовательскую сетку ватертигхт плайспаце.

### <a name="ray-casting"></a>Приведение лучей

После завершения просмотра комнаты Метки создаются на внутреннем уровне для таких поверхностей, как этаж, потолк и стенки. Функция "Плайспацерайкаст" принимает луч и возвращает, если луч конфликтует с известной поверхностью и, если да, сведения об этой поверхности в виде "Райкастресулт".

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

На внутреннем уровне райкаст выдается по сравнению с вычисленным Воксел представлением плайспаце в Кубе 8 – cm. Каждый Воксел содержит набор элементов Surface с обработанными данными топологии (то есть сурфелс). Сурфелс, содержащийся в пересеченной ячейке Воксел, сравнивается с лучшим соответствием, используемым для поиска сведений о топологии. Данные топологии содержат метки, возвращаемые в форме перечисления "Сурфацетипес", а также контактную зону для пересекающейся поверхности.

В примере Unity курсор приводится к каждому кадру. Во – первых, от своих противоречией Unity. Во вторых, для представления о мировом представлении модуля. И наконец, еще раз элементы пользовательского интерфейса. В этом приложении пользовательский интерфейс получает приоритет, далее понимание результата и, наконец, конфликтующие элементы Unity. Сурфацетипе сообщается в виде текста рядом с курсором.

![Тип поверхности помечен рядом с курсором](images/su-raycastresults-300px.jpg)<br>
*Тип поверхности помечен рядом с курсором*

### <a name="topology-queries"></a>Запросы топологии

В библиотеке DLL диспетчер топологии обрабатывает метки среды. Как упоминалось выше, большая часть данных хранится в сурфелс, содержащейся в томе Воксел. Кроме того, структура "Плайспацеинфос" используется для хранения сведений о плайспаце, включая выравнивание по всему миру (Дополнительные сведения см. ниже), этаж и высоту потолка. Эвристические методы используются для определения этажей, потолков и стен. Например, крупнейшим является самая крупная и наименьшая горизонтальная поверхность с более чем 1-m2 контактной областью. 

> [!NOTE]
> В этом процессе также используется путь камеры в процессе сканирования.

Подмножество запросов, предоставляемых диспетчером топологии, предоставляется через библиотеку DLL. Доступны следующие запросы топологии.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Каждый запрос имеет набор параметров, относящихся к типу запроса. В следующем примере пользователь указывает минимальную высоту, & ширину требуемого тома, минимальную высоту размещения выше пола и минимальный размер зазора перед томом. Все измерения задаются в метрах.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Каждый из этих запросов принимает предварительно выделенный массив структур "Топологиресулт". Параметр "Локатионкаунт" задает длину переданного массива. Возвращаемое значение сообщает о количестве возвращенных расположений. Это число никогда не превышает значение, переданное параметром "Локатионкаунт".

"Топологиресулт" содержит центральную точку возвращенного тома, направление (то есть нормальное) и размеры найденного пространства.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

> [!NOTE]
> В примере Unity каждый из этих запросов связан с кнопкой на панели виртуального интерфейса. Пример жестко кодирует параметры для каждого из этих запросов в разумные значения. Дополнительные примеры см. в разделе SpaceVisualizer.cs в примере кода.

### <a name="shape-queries"></a>Запросы фигур

В библиотеке DLL анализатор форм ("ShapeAnalyzer_W") использует анализатор топологии для сопоставления с пользовательскими фигурами, определенными пользователем. Образец Unity определяет набор фигур и предоставляет результаты из меню запросов в приложении на вкладке Shape. Цель состоит в том, что пользователь может определить собственные запросы фигур объектов и использовать их в соответствии с потребностями приложения.

Анализ фигур работает только на горизонтальных поверхностях. Например, диван определяется поверхностью плоского места и плоской вершиной на диване. Запрос Shape выполняет поиск двух поверхностей определенного размера, высоты и пропорций, при этом две поверхности Выровняйте и соединены. Используя терминологию API, место в диване и задняя часть являются компонентами фигур, а требования к выравниванию — к ограничениям компонентов.

Пример запроса, определенный в примере Unity (ShapeDefinition.cs) для объектов "ситтабле", выглядит следующим образом.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Каждый запрос Shape определяется набором компонентов Shape, каждый из которых имеет набор ограничений компонента и набор ограничений фигуры, в котором перечисляются зависимости между компонентами. Этот пример включает три ограничения в определении одного компонента и не имеет ограничений фигур между компонентами (как и один компонент).

Напротив, фигура дивана имеет два компонента фигур и четыре ограничения фигуры. Компоненты определяются по индексу в списке компонентов пользователя (в этом примере 0 и 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Функции-оболочки предоставляются в модуле Unity для простого создания пользовательских определений фигур. Полный список ограничений для компонентов и фигур можно найти в "SpatialUnderstandingDll.cs" в структурах "Шапекомпонентконстраинт" и "Шапеконстраинт".

![Фигура прямоугольника находится на этой поверхности](images/su-shapequery-300px.jpg)<br>
*Фигура прямоугольника находится на этой поверхности*

### <a name="object-placement-solver"></a>Поиск решения о размещении объектов

Поиск по месту размещения объектов можно использовать для обнаружения идеального расположения в физической комнате для размещения объектов. Поиск решения позволяет найти оптимальное расположение с учетом правил и ограничений объекта. Кроме того, запросы объектов сохраняются до тех пор, пока объект не будет удален с помощью вызовов "Solver_RemoveObject" или "Solver_RemoveAllObjects", что позволяет ограничить размещение нескольких объектов. Запросы размещения объектов состоят из трех частей: тип размещения с параметрами, список правил и список ограничений. Чтобы выполнить запрос, используйте следующий API.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Эта функция принимает имя объекта, определение размещения и список правил и ограничений. Оболочки C# предоставляют вспомогательные функции конструирования для упрощения создания правил и ограничений. Определение размещения содержит тип запроса, то есть один из следующих элементов.

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

Каждый из типов размещения имеет набор параметров, уникальных для данного типа. Структура "Обжектплацементдефинитион" содержит набор статических вспомогательных функций для создания этих определений. Например, чтобы найти место для размещения объекта в этаже, можно использовать следующую функцию. общедоступная статическая Обжектплацементдефинитион Create_OnFloor (Vector3 Халфдимс) в дополнение к типу размещения можно предоставить набор правил и ограничений. Правила не могут быть нарушены. Возможные расположения размещения, которые соответствуют типу и правилам, оптимизируются по набору ограничений, чтобы выбрать оптимальное расположение размещения. Каждое из правил и ограничений можно создать с помощью предоставленных статических функций создания. Ниже приведен пример функции конструирования правила и ограничения.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Приведенный ниже запрос на размещение объекта ищет место для размещения полугодового Куба на границе поверхности, от других ранее размещенных объектов и вблизи центра комнаты.

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

В случае успешного выполнения возвращается структура "Обжектплацементресулт", содержащая положение, размеры и ориентацию размещения. Кроме того, размещение добавляется в внутренний список размещенных объектов библиотеки DLL. При последующих запросах на размещение этот объект учитывается. Файл "LevelSolver.cs" в образце Unity содержит дополнительные примеры запросов.

![Результаты размещения объектов](images/su-objectplacement-1000px.jpg)<br>
*Рис. 3. синий прямоугольник, посвященный результату из трех мест в запросах к этаже от правил размещения камеры*

При решении для размещения нескольких объектов, необходимых для сценария уровня или приложения, сначала решите ненужные и крупные объекты, чтобы максимально эффективно обнаружить место. Порядок размещения важен. Если размещение объектов не найдено, попробуйте уменьшить количество ограниченных конфигураций. Наличие набора резервных конфигураций крайне важно для поддержки функциональных возможностей во многих конфигурациях комнаты.

### <a name="room-scanning-process"></a>Процесс сканирования комнаты

Хотя решение для пространственного сопоставления, предоставляемое HoloLens, достаточно универсально для удовлетворения потребностей всего спектра проблемных пространств, модуль пространственного понимания был разработан для поддержки потребностей двух конкретных игр. Его решение структурировано на основе определенного процесса и набора допущений, приведенных ниже.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Пользователь, плайспаце "Рисование" — на этапе сканирования пользователь перемещает и просматривает темпы воспроизведения, эффективно рисуя области, которые должны быть добавлены. Созданная сетка важна для предоставления отзывов пользователей на этом этапе. Настройка домашних и офисных задвижок — функции запросов разрабатываются вокруг плоских поверхностей и стен в правой части. Это мягкое ограничение. Однако на этапе сканирования выполняется анализ основной оси для оптимизации тесселяции сетки вдоль основной и вспомогательной осей. Прилагаемый файл SpatialUnderstanding.cs управляет процессом этапа сканирования. Он вызывает следующие функции.

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

Поток сканирования, управляемый поведением "Спатиалундерстандинг", вызывает Инитскан, а затем Упдатескан каждый кадр. Когда статистический запрос сообщает о разумном покрытии, пользователю разрешается аиртап вызывать Рекуестфиниш, чтобы обозначить окончание этапа сканирования. Упдатескан будет вызываться до тех пор, пока его возвращаемое значение не обозначает, что библиотека DLL завершила обработку.

### <a name="understanding-mesh"></a>Общие сведения о сетке

Внутренняя библиотека DLL сохраняет плайспаце в виде сетки с 8 вокселными кубами cm. Во время первой части сканирования выполняется анализ основных компонентов, чтобы определить оси комнаты. На внутреннем уровне он хранит свое Воксел пространство, выравниваемая по этим осям. Сетка создается приблизительно каждую секунду путем извлечения isosurface из тома Воксел. 

![Созданная Сетка создана на основе тома Воксел](images/su-custommesh.jpg)<br>
*Созданная Сетка создана на основе тома Воксел*

## <a name="troubleshooting"></a>Устранение неполадок
* Убедитесь, что вы установили функцию [спатиалперцептион](#setting-the-spatialperception-capability)
* При потере отслеживания следующее событие Онсурфацечанжед удалит все сетки.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Пространственное сопоставление в наборе средств Mixed Reality
Дополнительные сведения об использовании пространственного сопоставления с Mixed Reality Toolkit v2 см. в <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">разделе о поддержке пространственных</a> данных в документации по мртк.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core. Отсюда вы можете перейти к следующему стандартному блоку: 

> [!div class="nextstepaction"]
> [Текстовые](text-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также раздел
* [Системы координат](../../design/coordinate-systems.md)
* [Системы координат в Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit;</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. Мешфилтер</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. Мешколлидер</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a>
