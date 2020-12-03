---
title: Пространственное сопоставление в Unreal
description: Руководство по применению пространственного сопоставления в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственное сопоставление, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354388"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="269ec-104">Пространственное сопоставление в Unreal</span><span class="sxs-lookup"><span data-stu-id="269ec-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="269ec-105">Пространственное сопоставление позволяет помещать объекты на поверхности в физическом мире, показывая мир вокруг устройства HoloLens. За счет этого голограммы кажутся пользователю более реалистичными.</span><span class="sxs-lookup"><span data-stu-id="269ec-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="269ec-106">Кроме того, пространственное сопоставление обеспечивает привязку объектов в мире пользователя, пользуясь признаками глубины из реального мира. Это помогает создать у пользователя впечатление, что голограммы физически находятся в одном с ним пространстве. Если голограммы будут висеть в воздухе или перемещаться, ощущения пользователя будут не столь реалистичными.</span><span class="sxs-lookup"><span data-stu-id="269ec-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="269ec-107">При размещении объектов в пространстве нужно по возможности ориентироваться на комфорт.</span><span class="sxs-lookup"><span data-stu-id="269ec-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="269ec-108">Дополнительные сведения о качестве пространственного сопоставления, размещении объектов, загораживании, отрисовке и других аспектах см. в разделе справки "[Пространственное сопоставление](../../design/spatial-mapping.md)".</span><span class="sxs-lookup"><span data-stu-id="269ec-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="269ec-109">Включение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="269ec-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="269ec-110">Чтобы включить пространственное сопоставление для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="269ec-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="269ec-111">Выберите **Edit > Project Settings** (Правка > Параметры проекта) и прокрутите вниз до раздела **Platforms** (Платформы).</span><span class="sxs-lookup"><span data-stu-id="269ec-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="269ec-112">Выберите **HoloLens** и установите флажок **Spatial Perception** (Пространственное восприятие).</span><span class="sxs-lookup"><span data-stu-id="269ec-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Снимок экрана: параметры проекта HoloLens с выделенным параметром пространственного восприятия](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="269ec-114">Чтобы включить пространственное сопоставление (по умолчанию оно выключено) и отладить сетку **MRMesh** в игре для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="269ec-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="269ec-115">Откройте компонент **ARSessionConfig** и разверните раздел **ARSettings > World Mapping** (Параметры дополненной реальности > Сопоставление мира).</span><span class="sxs-lookup"><span data-stu-id="269ec-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="269ec-116">Установите флажок **Generate Mesh Data from Tracked Geometry** (Генерировать данные сетки по отслеживаемой геометрии), который предписывает подключаемому модулю HoloLens начать асинхронную регистрацию данных пространственного сопоставления с выводом в Unreal посредством сетки **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="269ec-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="269ec-117">Установите флажок **Render Mesh Data in Wireframe** (Отрисовывать данные сетки в виде каркасной модели), чтобы контур каждого треугольника сетки **MRMesh** показывался белым цветом.</span><span class="sxs-lookup"><span data-stu-id="269ec-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Хранилище пространственных привязок готово](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="269ec-119">Пространственное сопоставление во время выполнения</span><span class="sxs-lookup"><span data-stu-id="269ec-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="269ec-120">Изменить логику пространственного сопоставления во время выполнения можно путем настройки следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="269ec-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="269ec-121">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens > Spatial Mapping** (HoloLens > Пространственное сопоставление):</span><span class="sxs-lookup"><span data-stu-id="269ec-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Параметры пространственных привязок для проекта](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="269ec-123">Параметр **Max Triangles Per Cubic Meter** (Максимальное число треугольников на кубический метр) задает плотность треугольников в сетке пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="269ec-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="269ec-124">Параметр **Spatial Meshing Volume Size** (Размер объема для пространственных сеток) задает размер куба вокруг игрока, в пределах которого будут отрисовываться и обновляться данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="269ec-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="269ec-125">Если предполагается, что приложение будет выполняться в обширном пространстве, следует указать в этом поле достаточно большое значение, чтобы оно лучше соответствовало пространству реального мира.</span><span class="sxs-lookup"><span data-stu-id="269ec-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="269ec-126">Если же приложению нужны голограммы только на поверхностях рядом с пользователем, значение в этом поле может быть небольшим.</span><span class="sxs-lookup"><span data-stu-id="269ec-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="269ec-127">По мере перемещения пользователя по игровому миру вместе с ним перемещается и пространство для пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="269ec-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="269ec-128">Работа с сеткой MRMesh</span><span class="sxs-lookup"><span data-stu-id="269ec-128">Working with MRMesh</span></span>

<span data-ttu-id="269ec-129">Сначала вам нужно запустить пространственное сопоставление:</span><span class="sxs-lookup"><span data-stu-id="269ec-129">First, you need to start Spatial Mapping:</span></span>

![Схема функции ToggleARCapture с выделенным типом захвата Spatial Mapping (пространственное сопоставление)](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="269ec-131">После захвата пространственного сопоставления для пространства мы рекомендуем отключить его.</span><span class="sxs-lookup"><span data-stu-id="269ec-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="269ec-132">Пространственное сопоставление может быть выполнено после определенного периода времени или после того, как лучи, выпущенные во всех направлениях, возвратят столкновения с MRMesh.</span><span class="sxs-lookup"><span data-stu-id="269ec-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="269ec-133">Чтобы получить доступ к сетке **MRMesh** во время выполнения:</span><span class="sxs-lookup"><span data-stu-id="269ec-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="269ec-134">Добавьте к субъекту Blueprint компонент **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="269ec-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![AR Trackable Notify для пространственных привязок](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="269ec-136">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="269ec-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="269ec-137">Нажмите кнопку **+** на событиях, мониторинг которых требуется вести.</span><span class="sxs-lookup"><span data-stu-id="269ec-137">Click the **+** button on the events you want to monitor.</span></span> 

![События пространственных привязок](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="269ec-139">В данном случае ведется мониторинг события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), которое ведет поиск действительных мировых сеток, соответствующих данным пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="269ec-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="269ec-140">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="269ec-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="269ec-141">Изменить материал сетки можно в графе событий схемы или в коде на C++.</span><span class="sxs-lookup"><span data-stu-id="269ec-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="269ec-142">На приведенном ниже снимке экрана показан вариант действий с графом событий схемы.</span><span class="sxs-lookup"><span data-stu-id="269ec-142">The screenshot below shows the Blueprint route:</span></span> 

![Пример пространственных привязок](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="269ec-144">Пространственное сопоставление в C++</span><span class="sxs-lookup"><span data-stu-id="269ec-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="269ec-145">В файле build.cs игры добавьте **AugmentedReality** и **MRMesh** в список PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="269ec-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="269ec-146">Чтобы получать доступ к MRMesh, подпишитесь на делегатов **OnTrackableAdded**:</span><span class="sxs-lookup"><span data-stu-id="269ec-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="269ec-147">Также существуют аналогичные делегаты для обновленных и удаленных событий: **AddOnTrackableUpdatedDelegate_Handle** и **AddOnTrackableRemovedDelegate_Handle** соответственно.</span><span class="sxs-lookup"><span data-stu-id="269ec-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="269ec-148">Полный список событий можно найти в API объекта [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="269ec-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="269ec-149">См. также статью</span><span class="sxs-lookup"><span data-stu-id="269ec-149">See also</span></span>
* [<span data-ttu-id="269ec-150">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="269ec-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
