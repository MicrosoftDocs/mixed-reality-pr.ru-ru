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
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="5cb51-104">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="5cb51-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="5cb51-105">[пространственное сопоставление](../../design/spatial-mapping.md) позволяет извлекать сетчатые треугольники, представляющие поверхности мира на устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5cb51-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="5cb51-106">Вы можете использовать данные Surface для размещения, перекрытия и анализа помещений, чтобы придать проектам Unity дополнительный четкое.</span><span class="sxs-lookup"><span data-stu-id="5cb51-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="5cb51-107">Unity включает полную поддержку пространственного сопоставления, которое предоставляется разработчикам следующими способами:</span><span class="sxs-lookup"><span data-stu-id="5cb51-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="5cb51-108">Компоненты пространственного сопоставления, доступные в Микседреалититулкит, которые предоставляют удобный и быстрый путь для начала работы с пространственным сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="5cb51-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="5cb51-109">API-интерфейсы пространственного сопоставления нижнего уровня, обеспечивающие полный контроль и обеспечивающие более сложную настройку для конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="5cb51-110">Чтобы использовать пространственное сопоставление в приложении, в AppxManifest необходимо задать возможность Спатиалперцептион.</span><span class="sxs-lookup"><span data-stu-id="5cb51-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="5cb51-111">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="5cb51-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5cb51-112"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="5cb51-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5cb51-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (первый общий)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cb51-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5cb51-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5cb51-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="5cb51-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cb51-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5cb51-116">пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="5cb51-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="5cb51-117">✔️</span><span class="sxs-lookup"><span data-stu-id="5cb51-117">✔️</span></span></td>
        <td><span data-ttu-id="5cb51-118">✔️</span><span class="sxs-lookup"><span data-stu-id="5cb51-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="5cb51-119">Настройка возможности Спатиалперцептион</span><span class="sxs-lookup"><span data-stu-id="5cb51-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="5cb51-120">Чтобы приложение использовало данные пространственного сопоставления, необходимо включить возможность Спатиалперцептион.</span><span class="sxs-lookup"><span data-stu-id="5cb51-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="5cb51-121">Как включить функцию Спатиалперцептион:</span><span class="sxs-lookup"><span data-stu-id="5cb51-121">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="5cb51-122">В редакторе Unity откройте панель **"Параметры проигрывателя"** (измените > параметры проекта > Player).</span><span class="sxs-lookup"><span data-stu-id="5cb51-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="5cb51-123">Выберите на вкладке **"Магазин Windows"**</span><span class="sxs-lookup"><span data-stu-id="5cb51-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="5cb51-124">Разверните узел **"Параметры публикации"** и проверьте возможность **"спатиалперцептион** " в списке **"возможности"** .</span><span class="sxs-lookup"><span data-stu-id="5cb51-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="5cb51-125">Если вы уже экспортировали проект Unity в решение Visual Studio, необходимо либо экспортировать в новую папку, либо вручную [установить эту возможность в appxmanifest в Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="5cb51-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="5cb51-126">Для пространственного сопоставления также требуется Maxversiontested укажите установленную по меньшей мере 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="5cb51-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="5cb51-127">В Visual Studio щелкните правой кнопкой мыши **Package. appxmanifest** в Обозреватель решений и выберите **Просмотреть код** .</span><span class="sxs-lookup"><span data-stu-id="5cb51-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="5cb51-128">Найдите строку с указанием **TargetDeviceFamily** и измените **maxversiontested укажите установленную = "10.0.10240.0"** на **maxversiontested укажите установленную = "10.0.10586.0"** .</span><span class="sxs-lookup"><span data-stu-id="5cb51-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="5cb51-129">**Сохраните** пакет. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="5cb51-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="5cb51-130">Начало работы с встроенными компонентами пространственного сопоставления Unity</span><span class="sxs-lookup"><span data-stu-id="5cb51-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="5cb51-131">Unity предлагает два компонента для простого добавления пространственного сопоставления в приложение, модуль **подготовки** к пространственному сопоставлению и средство **сопоставления пространственных сопоставлений**.</span><span class="sxs-lookup"><span data-stu-id="5cb51-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="5cb51-132">Модуль подготовки пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="5cb51-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="5cb51-133">Модуль подготовки пространственных сопоставлений позволяет визуализировать сетку пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Модуль подготовки пространственных сопоставлений в Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="5cb51-135">Конфликт пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="5cb51-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="5cb51-136">Механизм обработки пространственных сопоставлений позволяет взаимодействовать с данными (или символами), например физикой, с сеткой пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Конфликт пространственного сопоставления в Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="5cb51-138">Использование встроенных компонентов пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="5cb51-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="5cb51-139">Вы можете добавить оба компонента в приложение, если вы хотите визуализировать и взаимодействовать с физическими областями.</span><span class="sxs-lookup"><span data-stu-id="5cb51-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="5cb51-140">Чтобы использовать эти два компонента в приложении Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5cb51-140">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="5cb51-141">Выберите GameObject в центре области, в которой вы хотите определить сетки пространственных поверхностей.</span><span class="sxs-lookup"><span data-stu-id="5cb51-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="5cb51-142">В окне инспектора **добавьте компонент**  >  **XR**  >  **пространственное сопоставление пространственного сопоставления** или модуль **подготовки пространственных сопоставлений**.</span><span class="sxs-lookup"><span data-stu-id="5cb51-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="5cb51-143">Дополнительные сведения об использовании этих компонентов можно найти на <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">сайте документации по Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="5cb51-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="5cb51-144">Переход за пределы встроенных компонентов пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="5cb51-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="5cb51-145">Эти компоненты упрощают перетаскивание, чтобы начать работу с пространственным сопоставлением.</span><span class="sxs-lookup"><span data-stu-id="5cb51-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="5cb51-146">Если вы хотите продолжить, необходимо изучить два основных пути:</span><span class="sxs-lookup"><span data-stu-id="5cb51-146">When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="5cb51-147">Чтобы выполнить собственную обработку сетки более низкого уровня, см. раздел, посвященный API сценария низкоуровневого пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="5cb51-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="5cb51-148">Сведения об анализе сетки более высокого уровня см. в разделе, посвященном библиотеке Спатиалундерстандинг в <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">микседреалититулкит</a>.</span><span class="sxs-lookup"><span data-stu-id="5cb51-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="5cb51-149">Использование API пространственного сопоставления Unity с низким уровнем</span><span class="sxs-lookup"><span data-stu-id="5cb51-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="5cb51-150">Если вам требуется больший контроль, чем средства визуализации пространственных сопоставлений и средства для работы с пространственными сопоставлениями, используйте низкоуровневые API пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="5cb51-151">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="5cb51-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="5cb51-152">**Типы**: *сурфацеобсервер*, *сурфацечанже*, *сурфацедата*, *сурфацеид*</span><span class="sxs-lookup"><span data-stu-id="5cb51-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="5cb51-153">Мы выделили предлагаемый поток для приложения, которое использует API-интерфейсы пространственного сопоставления в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="5cb51-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="5cb51-154">Настройка Сурфацеобсервер (s)</span><span class="sxs-lookup"><span data-stu-id="5cb51-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="5cb51-155">Создайте экземпляр одного объекта Сурфацеобсервер для каждой определенной приложением области пространства, для которой требуются данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="5cb51-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="5cb51-156">Укажите регион пространства, в котором каждый объект Сурфацеобсервер будет предоставлять данные, вызвав либо Сетволумеассфере, Сетволумеасаксисалигнедбокс, Сетволумеасориентедбокс, либо SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="5cb51-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="5cb51-157">Можно переопределить область пространства в будущем, просто вызвав один из этих методов снова.</span><span class="sxs-lookup"><span data-stu-id="5cb51-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="5cb51-158">При вызове Сурфацеобсервер. Update () необходимо предоставить обработчик для каждой пространственной поверхности в регионе Сурфацеобсервер, для которого в системе пространственных сопоставлений есть новая информация.</span><span class="sxs-lookup"><span data-stu-id="5cb51-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="5cb51-159">Обработчик получает для одной пространственной поверхности:</span><span class="sxs-lookup"><span data-stu-id="5cb51-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="5cb51-160">Обработка изменений поверхности</span><span class="sxs-lookup"><span data-stu-id="5cb51-160">Handling Surface Changes</span></span>

<span data-ttu-id="5cb51-161">Существует несколько основных вариантов для добавления и обновления, которые могут использовать один и тот же путь к коду и удалены.</span><span class="sxs-lookup"><span data-stu-id="5cb51-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>
* <span data-ttu-id="5cb51-162">В добавленных и обновленных случаях мы добавляем или получаем GameObject, представляющий эту сетку, из словаря, создаем структуру Сурфацедата с необходимыми компонентами, а затем вызываем Рекуестмешдатаасинк для заполнения GameObject данными сетки и положением в сцене.</span><span class="sxs-lookup"><span data-stu-id="5cb51-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="5cb51-163">В удаленном варианте мы удаляем GameObject, представляющий эту сетку, из словаря и удалим ее.</span><span class="sxs-lookup"><span data-stu-id="5cb51-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="5cb51-164">Обработка данных готова</span><span class="sxs-lookup"><span data-stu-id="5cb51-164">Handling Data Ready</span></span>

<span data-ttu-id="5cb51-165">Обработчик Ондатареади получает объект Сурфацедата.</span><span class="sxs-lookup"><span data-stu-id="5cb51-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="5cb51-166">Ворлданчор, Мешфилтер и (необязательно) Мешколлидер объекты, которые он содержит, отражает Последнее состояние связанной пространственной поверхности.</span><span class="sxs-lookup"><span data-stu-id="5cb51-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="5cb51-167">При необходимости анализируйте и (или) [обработайте](../../design/spatial-mapping.md#mesh-processing) данные сетки, обращаясь к элементу сетки объекта мешфилтер.</span><span class="sxs-lookup"><span data-stu-id="5cb51-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="5cb51-168">Отрисовка пространственной поверхности с помощью последней сети и (необязательно) используйте ее для физических конфликтов и райкастс.</span><span class="sxs-lookup"><span data-stu-id="5cb51-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="5cb51-169">Важно убедиться, что содержимое Сурфацедата не равно null.</span><span class="sxs-lookup"><span data-stu-id="5cb51-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="5cb51-170">Начать обработку обновлений</span><span class="sxs-lookup"><span data-stu-id="5cb51-170">Start processing on updates</span></span>

<span data-ttu-id="5cb51-171">Сурфацеобсервер. Update () следует вызывать при задержке, а не во всех кадрах.</span><span class="sxs-lookup"><span data-stu-id="5cb51-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="5cb51-172">Анализ сетки более высокого уровня: Спатиалундерстандинг</span><span class="sxs-lookup"><span data-stu-id="5cb51-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="5cb51-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Микседреалититулкит</a> — это набор служебного кода для holographic-интерфейсов, созданных на основе более holographic-API Unity.</span><span class="sxs-lookup"><span data-stu-id="5cb51-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="5cb51-174">Пространственное понимание</span><span class="sxs-lookup"><span data-stu-id="5cb51-174">Spatial Understanding</span></span>

<span data-ttu-id="5cb51-175">При помещении голограмм в физический мир часто желательно выйти за пределы сетки и поверхностей пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="5cb51-175">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="5cb51-176">Когда размещение выполняется процедурно, желательно более высокий уровень понимания окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="5cb51-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="5cb51-177">Обычно это требует принятия решений о том, что такое этаж, потолк и стенки.</span><span class="sxs-lookup"><span data-stu-id="5cb51-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="5cb51-178">Кроме того, у вас есть возможность оптимизировать с учетом набора ограничений на размещение, чтобы определить наиболее подходящие физические расположения для holographic объектов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-178">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="5cb51-179">Во время разработки Конкер и фрагментов асобо Studios столкнулись с этой проблемой, разрабатывая Поиск решения для комнаты.</span><span class="sxs-lookup"><span data-stu-id="5cb51-179">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="5cb51-180">Каждая из этих игр имела потребность в конкретных играх, но они являются общими ключевыми технологиями для пространственного понимания.</span><span class="sxs-lookup"><span data-stu-id="5cb51-180">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="5cb51-181">Библиотека Холотулкит. Спатиалундерстандинг инкапсулирует эту технологию, позволяя быстро находить пустые пробелы в стенах, размещать объекты в самом потолке, указывать место для размещения символа и множество других пространственных запросов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="5cb51-182">Весь исходный код включен, что позволяет настроить его в своих целях и поделиться изменениями с сообществом.</span><span class="sxs-lookup"><span data-stu-id="5cb51-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="5cb51-183">Код для поиска решения C++ был заключен в библиотеку DLL UWP и предоставлен в Unity с помощью Drop в prefab, который содержится в Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="5cb51-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="5cb51-184">Основные сведения о модулях</span><span class="sxs-lookup"><span data-stu-id="5cb51-184">Understanding Modules</span></span>

<span data-ttu-id="5cb51-185">Существует три основных интерфейса, предоставляемых модулем: топология простых и пространственных запросов, форма для обнаружения объектов и поисковый запрос на размещение объектов для размещения наборов объектов на основе ограничений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="5cb51-186">Каждый из этих способов описан ниже.</span><span class="sxs-lookup"><span data-stu-id="5cb51-186">Each of these is described below.</span></span> <span data-ttu-id="5cb51-187">В дополнение к трем интерфейсам основного модуля можно использовать интерфейс приведения лучей, чтобы извлечь типы областей с тегами, а также можно скопировать пользовательскую сетку ватертигхт плайспаце.</span><span class="sxs-lookup"><span data-stu-id="5cb51-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="5cb51-188">Приведение лучей</span><span class="sxs-lookup"><span data-stu-id="5cb51-188">Ray Casting</span></span>

<span data-ttu-id="5cb51-189">После завершения просмотра комнаты Метки создаются на внутреннем уровне для таких поверхностей, как этаж, потолк и стенки.</span><span class="sxs-lookup"><span data-stu-id="5cb51-189">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="5cb51-190">Функция "Плайспацерайкаст" принимает луч и возвращает, если луч конфликтует с известной поверхностью и, если да, сведения об этой поверхности в виде "Райкастресулт".</span><span class="sxs-lookup"><span data-stu-id="5cb51-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="5cb51-191">На внутреннем уровне райкаст выдается по сравнению с вычисленным Воксел представлением плайспаце в Кубе 8 – cm.</span><span class="sxs-lookup"><span data-stu-id="5cb51-191">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="5cb51-192">Каждый Воксел содержит набор элементов Surface с обработанными данными топологии (то есть сурфелс).</span><span class="sxs-lookup"><span data-stu-id="5cb51-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="5cb51-193">Сурфелс, содержащийся в пересеченной ячейке Воксел, сравнивается с лучшим соответствием, используемым для поиска сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="5cb51-193">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="5cb51-194">Данные топологии содержат метки, возвращаемые в форме перечисления "Сурфацетипес", а также контактную зону для пересекающейся поверхности.</span><span class="sxs-lookup"><span data-stu-id="5cb51-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="5cb51-195">В примере Unity курсор приводится к каждому кадру.</span><span class="sxs-lookup"><span data-stu-id="5cb51-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="5cb51-196">Во – первых, от своих противоречией Unity.</span><span class="sxs-lookup"><span data-stu-id="5cb51-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="5cb51-197">Во вторых, для представления о мировом представлении модуля.</span><span class="sxs-lookup"><span data-stu-id="5cb51-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="5cb51-198">И наконец, еще раз элементы пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5cb51-198">And finally, again UI elements.</span></span> <span data-ttu-id="5cb51-199">В этом приложении пользовательский интерфейс получает приоритет, далее понимание результата и, наконец, конфликтующие элементы Unity.</span><span class="sxs-lookup"><span data-stu-id="5cb51-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="5cb51-200">Сурфацетипе сообщается в виде текста рядом с курсором.</span><span class="sxs-lookup"><span data-stu-id="5cb51-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="5cb51-201">![Тип поверхности помечен рядом с курсором](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cb51-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="5cb51-202">*Тип поверхности помечен рядом с курсором*</span><span class="sxs-lookup"><span data-stu-id="5cb51-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="5cb51-203">Запросы топологии</span><span class="sxs-lookup"><span data-stu-id="5cb51-203">Topology Queries</span></span>

<span data-ttu-id="5cb51-204">В библиотеке DLL диспетчер топологии обрабатывает метки среды.</span><span class="sxs-lookup"><span data-stu-id="5cb51-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="5cb51-205">Как упоминалось выше, большая часть данных хранится в сурфелс, содержащейся в томе Воксел.</span><span class="sxs-lookup"><span data-stu-id="5cb51-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="5cb51-206">Кроме того, структура "Плайспацеинфос" используется для хранения сведений о плайспаце, включая выравнивание по всему миру (Дополнительные сведения см. ниже), этаж и высоту потолка.</span><span class="sxs-lookup"><span data-stu-id="5cb51-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="5cb51-207">Эвристические методы используются для определения этажей, потолков и стен.</span><span class="sxs-lookup"><span data-stu-id="5cb51-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="5cb51-208">Например, крупнейшим является самая крупная и наименьшая горизонтальная поверхность с более чем 1-m2 контактной областью.</span><span class="sxs-lookup"><span data-stu-id="5cb51-208">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span> 

> [!NOTE]
> <span data-ttu-id="5cb51-209">В этом процессе также используется путь камеры в процессе сканирования.</span><span class="sxs-lookup"><span data-stu-id="5cb51-209">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="5cb51-210">Подмножество запросов, предоставляемых диспетчером топологии, предоставляется через библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="5cb51-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="5cb51-211">Доступны следующие запросы топологии.</span><span class="sxs-lookup"><span data-stu-id="5cb51-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="5cb51-212">Каждый запрос имеет набор параметров, относящихся к типу запроса.</span><span class="sxs-lookup"><span data-stu-id="5cb51-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="5cb51-213">В следующем примере пользователь указывает минимальную высоту, & ширину требуемого тома, минимальную высоту размещения выше пола и минимальный размер зазора перед томом.</span><span class="sxs-lookup"><span data-stu-id="5cb51-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="5cb51-214">Все измерения задаются в метрах.</span><span class="sxs-lookup"><span data-stu-id="5cb51-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="5cb51-215">Каждый из этих запросов принимает предварительно выделенный массив структур "Топологиресулт".</span><span class="sxs-lookup"><span data-stu-id="5cb51-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="5cb51-216">Параметр "Локатионкаунт" задает длину переданного массива.</span><span class="sxs-lookup"><span data-stu-id="5cb51-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="5cb51-217">Возвращаемое значение сообщает о количестве возвращенных расположений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="5cb51-218">Это число никогда не превышает значение, переданное параметром "Локатионкаунт".</span><span class="sxs-lookup"><span data-stu-id="5cb51-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="5cb51-219">"Топологиресулт" содержит центральную точку возвращенного тома, направление (то есть нормальное) и размеры найденного пространства.</span><span class="sxs-lookup"><span data-stu-id="5cb51-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

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
> <span data-ttu-id="5cb51-220">В примере Unity каждый из этих запросов связан с кнопкой на панели виртуального интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5cb51-220">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="5cb51-221">Пример жестко кодирует параметры для каждого из этих запросов в разумные значения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="5cb51-222">Дополнительные примеры см. в разделе SpaceVisualizer.cs в примере кода.</span><span class="sxs-lookup"><span data-stu-id="5cb51-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="5cb51-223">Запросы фигур</span><span class="sxs-lookup"><span data-stu-id="5cb51-223">Shape Queries</span></span>

<span data-ttu-id="5cb51-224">В библиотеке DLL анализатор форм ("ShapeAnalyzer_W") использует анализатор топологии для сопоставления с пользовательскими фигурами, определенными пользователем.</span><span class="sxs-lookup"><span data-stu-id="5cb51-224">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="5cb51-225">Образец Unity определяет набор фигур и предоставляет результаты из меню запросов в приложении на вкладке Shape. Цель состоит в том, что пользователь может определить собственные запросы фигур объектов и использовать их в соответствии с потребностями приложения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="5cb51-226">Анализ фигур работает только на горизонтальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="5cb51-226">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="5cb51-227">Например, диван определяется поверхностью плоского места и плоской вершиной на диване.</span><span class="sxs-lookup"><span data-stu-id="5cb51-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="5cb51-228">Запрос Shape выполняет поиск двух поверхностей определенного размера, высоты и пропорций, при этом две поверхности Выровняйте и соединены.</span><span class="sxs-lookup"><span data-stu-id="5cb51-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="5cb51-229">Используя терминологию API, место в диване и задняя часть являются компонентами фигур, а требования к выравниванию — к ограничениям компонентов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="5cb51-230">Пример запроса, определенный в примере Unity (ShapeDefinition.cs) для объектов "ситтабле", выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="5cb51-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="5cb51-231">Каждый запрос Shape определяется набором компонентов Shape, каждый из которых имеет набор ограничений компонента и набор ограничений фигуры, в котором перечисляются зависимости между компонентами.</span><span class="sxs-lookup"><span data-stu-id="5cb51-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="5cb51-232">Этот пример включает три ограничения в определении одного компонента и не имеет ограничений фигур между компонентами (как и один компонент).</span><span class="sxs-lookup"><span data-stu-id="5cb51-232">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="5cb51-233">Напротив, фигура дивана имеет два компонента фигур и четыре ограничения фигуры.</span><span class="sxs-lookup"><span data-stu-id="5cb51-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="5cb51-234">Компоненты определяются по индексу в списке компонентов пользователя (в этом примере 0 и 1).</span><span class="sxs-lookup"><span data-stu-id="5cb51-234">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="5cb51-235">Функции-оболочки предоставляются в модуле Unity для простого создания пользовательских определений фигур.</span><span class="sxs-lookup"><span data-stu-id="5cb51-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="5cb51-236">Полный список ограничений для компонентов и фигур можно найти в "SpatialUnderstandingDll.cs" в структурах "Шапекомпонентконстраинт" и "Шапеконстраинт".</span><span class="sxs-lookup"><span data-stu-id="5cb51-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="5cb51-237">![Фигура прямоугольника находится на этой поверхности](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cb51-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="5cb51-238">*Фигура прямоугольника находится на этой поверхности*</span><span class="sxs-lookup"><span data-stu-id="5cb51-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="5cb51-239">Поиск решения о размещении объектов</span><span class="sxs-lookup"><span data-stu-id="5cb51-239">Object Placement Solver</span></span>

<span data-ttu-id="5cb51-240">Поиск по месту размещения объектов можно использовать для обнаружения идеального расположения в физической комнате для размещения объектов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="5cb51-241">Поиск решения позволяет найти оптимальное расположение с учетом правил и ограничений объекта.</span><span class="sxs-lookup"><span data-stu-id="5cb51-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="5cb51-242">Кроме того, запросы объектов сохраняются до тех пор, пока объект не будет удален с помощью вызовов "Solver_RemoveObject" или "Solver_RemoveAllObjects", что позволяет ограничить размещение нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="5cb51-243">Запросы размещения объектов состоят из трех частей: тип размещения с параметрами, список правил и список ограничений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="5cb51-244">Чтобы выполнить запрос, используйте следующий API.</span><span class="sxs-lookup"><span data-stu-id="5cb51-244">To run a query, use the following API.</span></span>

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

<span data-ttu-id="5cb51-245">Эта функция принимает имя объекта, определение размещения и список правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="5cb51-246">Оболочки C# предоставляют вспомогательные функции конструирования для упрощения создания правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="5cb51-247">Определение размещения содержит тип запроса, то есть один из следующих элементов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-247">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="5cb51-248">Каждый из типов размещения имеет набор параметров, уникальных для данного типа.</span><span class="sxs-lookup"><span data-stu-id="5cb51-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="5cb51-249">Структура "Обжектплацементдефинитион" содержит набор статических вспомогательных функций для создания этих определений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="5cb51-250">Например, чтобы найти место для размещения объекта в этаже, можно использовать следующую функцию.</span><span class="sxs-lookup"><span data-stu-id="5cb51-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="5cb51-251">общедоступная статическая Обжектплацементдефинитион Create_OnFloor (Vector3 Халфдимс) в дополнение к типу размещения можно предоставить набор правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="5cb51-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="5cb51-252">Правила не могут быть нарушены.</span><span class="sxs-lookup"><span data-stu-id="5cb51-252">Rules cannot be violated.</span></span> <span data-ttu-id="5cb51-253">Возможные расположения размещения, которые соответствуют типу и правилам, оптимизируются по набору ограничений, чтобы выбрать оптимальное расположение размещения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="5cb51-254">Каждое из правил и ограничений можно создать с помощью предоставленных статических функций создания.</span><span class="sxs-lookup"><span data-stu-id="5cb51-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="5cb51-255">Ниже приведен пример функции конструирования правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="5cb51-256">Приведенный ниже запрос на размещение объекта ищет место для размещения полугодового Куба на границе поверхности, от других ранее размещенных объектов и вблизи центра комнаты.</span><span class="sxs-lookup"><span data-stu-id="5cb51-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="5cb51-257">В случае успешного выполнения возвращается структура "Обжектплацементресулт", содержащая положение, размеры и ориентацию размещения.</span><span class="sxs-lookup"><span data-stu-id="5cb51-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="5cb51-258">Кроме того, размещение добавляется в внутренний список размещенных объектов библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="5cb51-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="5cb51-259">При последующих запросах на размещение этот объект учитывается.</span><span class="sxs-lookup"><span data-stu-id="5cb51-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="5cb51-260">Файл "LevelSolver.cs" в образце Unity содержит дополнительные примеры запросов.</span><span class="sxs-lookup"><span data-stu-id="5cb51-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="5cb51-261">![Результаты размещения объектов](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cb51-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="5cb51-262">*Рис. 3. синий прямоугольник, посвященный результату из трех мест в запросах к этаже от правил размещения камеры*</span><span class="sxs-lookup"><span data-stu-id="5cb51-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="5cb51-263">При решении для размещения нескольких объектов, необходимых для сценария уровня или приложения, сначала решите ненужные и крупные объекты, чтобы максимально эффективно обнаружить место.</span><span class="sxs-lookup"><span data-stu-id="5cb51-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="5cb51-264">Порядок размещения важен.</span><span class="sxs-lookup"><span data-stu-id="5cb51-264">Placement order is important.</span></span> <span data-ttu-id="5cb51-265">Если размещение объектов не найдено, попробуйте уменьшить количество ограниченных конфигураций.</span><span class="sxs-lookup"><span data-stu-id="5cb51-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="5cb51-266">Наличие набора резервных конфигураций крайне важно для поддержки функциональных возможностей во многих конфигурациях комнаты.</span><span class="sxs-lookup"><span data-stu-id="5cb51-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="5cb51-267">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="5cb51-267">Room Scanning Process</span></span>

<span data-ttu-id="5cb51-268">Хотя решение для пространственного сопоставления, предоставляемое HoloLens, достаточно универсально для удовлетворения потребностей всего спектра проблемных пространств, модуль пространственного понимания был разработан для поддержки потребностей двух конкретных игр.</span><span class="sxs-lookup"><span data-stu-id="5cb51-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="5cb51-269">Его решение структурировано на основе определенного процесса и набора допущений, приведенных ниже.</span><span class="sxs-lookup"><span data-stu-id="5cb51-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="5cb51-270">Пользователь, плайспаце "Рисование" — на этапе сканирования пользователь перемещает и просматривает темпы воспроизведения, эффективно рисуя области, которые должны быть добавлены.</span><span class="sxs-lookup"><span data-stu-id="5cb51-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="5cb51-271">Созданная сетка важна для предоставления отзывов пользователей на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="5cb51-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="5cb51-272">Настройка домашних и офисных задвижок — функции запросов разрабатываются вокруг плоских поверхностей и стен в правой части.</span><span class="sxs-lookup"><span data-stu-id="5cb51-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="5cb51-273">Это мягкое ограничение.</span><span class="sxs-lookup"><span data-stu-id="5cb51-273">This is a soft limitation.</span></span> <span data-ttu-id="5cb51-274">Однако на этапе сканирования выполняется анализ основной оси для оптимизации тесселяции сетки вдоль основной и вспомогательной осей.</span><span class="sxs-lookup"><span data-stu-id="5cb51-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="5cb51-275">Прилагаемый файл SpatialUnderstanding.cs управляет процессом этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="5cb51-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="5cb51-276">Он вызывает следующие функции.</span><span class="sxs-lookup"><span data-stu-id="5cb51-276">It calls the following functions.</span></span>

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

<span data-ttu-id="5cb51-277">Поток сканирования, управляемый поведением "Спатиалундерстандинг", вызывает Инитскан, а затем Упдатескан каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="5cb51-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="5cb51-278">Когда статистический запрос сообщает о разумном покрытии, пользователю разрешается аиртап вызывать Рекуестфиниш, чтобы обозначить окончание этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="5cb51-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="5cb51-279">Упдатескан будет вызываться до тех пор, пока его возвращаемое значение не обозначает, что библиотека DLL завершила обработку.</span><span class="sxs-lookup"><span data-stu-id="5cb51-279">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="5cb51-280">Общие сведения о сетке</span><span class="sxs-lookup"><span data-stu-id="5cb51-280">Understanding Mesh</span></span>

<span data-ttu-id="5cb51-281">Внутренняя библиотека DLL сохраняет плайспаце в виде сетки с 8 вокселными кубами cm.</span><span class="sxs-lookup"><span data-stu-id="5cb51-281">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="5cb51-282">Во время первой части сканирования выполняется анализ основных компонентов, чтобы определить оси комнаты.</span><span class="sxs-lookup"><span data-stu-id="5cb51-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="5cb51-283">На внутреннем уровне он хранит свое Воксел пространство, выравниваемая по этим осям.</span><span class="sxs-lookup"><span data-stu-id="5cb51-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="5cb51-284">Сетка создается приблизительно каждую секунду путем извлечения isosurface из тома Воксел.</span><span class="sxs-lookup"><span data-stu-id="5cb51-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="5cb51-285">![Созданная Сетка создана на основе тома Воксел](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cb51-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="5cb51-286">*Созданная Сетка создана на основе тома Воксел*</span><span class="sxs-lookup"><span data-stu-id="5cb51-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5cb51-287">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="5cb51-287">Troubleshooting</span></span>
* <span data-ttu-id="5cb51-288">Убедитесь, что вы установили функцию [спатиалперцептион](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="5cb51-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="5cb51-289">При потере отслеживания следующее событие Онсурфацечанжед удалит все сетки.</span><span class="sxs-lookup"><span data-stu-id="5cb51-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="5cb51-290">Пространственное сопоставление в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5cb51-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="5cb51-291">Дополнительные сведения об использовании пространственного сопоставления с Mixed Reality Toolkit v2 см. в <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">разделе о поддержке пространственных</a> данных в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="5cb51-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5cb51-292">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="5cb51-292">Next Development Checkpoint</span></span>

<span data-ttu-id="5cb51-293">Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core.</span><span class="sxs-lookup"><span data-stu-id="5cb51-293">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="5cb51-294">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="5cb51-294">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cb51-295">Текстовые</span><span class="sxs-lookup"><span data-stu-id="5cb51-295">Text</span></span>](text-in-unity.md)

<span data-ttu-id="5cb51-296">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="5cb51-296">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="5cb51-297">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="5cb51-297">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="5cb51-298">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="5cb51-298">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cb51-299">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5cb51-299">See also</span></span>
* [<span data-ttu-id="5cb51-300">Системы координат</span><span class="sxs-lookup"><span data-stu-id="5cb51-300">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="5cb51-301">Системы координат в Unity</span><span class="sxs-lookup"><span data-stu-id="5cb51-301">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="5cb51-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit;</a></span><span class="sxs-lookup"><span data-stu-id="5cb51-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="5cb51-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. Мешфилтер</a></span><span class="sxs-lookup"><span data-stu-id="5cb51-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="5cb51-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. Мешколлидер</a></span><span class="sxs-lookup"><span data-stu-id="5cb51-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="5cb51-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="5cb51-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
