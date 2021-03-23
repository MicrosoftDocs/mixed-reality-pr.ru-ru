---
title: Пространственное сопоставление в Unreal
description: Сведения о том, как использовать пространственное сопоставление и сетки в приложениях смешанной реальности Unreal для устройств HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, функции, документация, руководства, голограммы, пространственное сопоставление, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 3f07acc5bb4ad85084f6eb178fd1c33d94224408
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98009964"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="69cb5-104">Пространственное сопоставление в Unreal</span><span class="sxs-lookup"><span data-stu-id="69cb5-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="69cb5-105">Пространственное сопоставление позволяет размещать объекты на физических поверхностях в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="69cb5-105">Spatial mapping lets you place objects on physical surfaces in the real-world.</span></span> <span data-ttu-id="69cb5-106">Когда мир вокруг HoloLens сопоставляется, голограммы кажутся более реальными для пользователя.</span><span class="sxs-lookup"><span data-stu-id="69cb5-106">When the world around the HoloLens is mapped, holograms seem more real to the user.</span></span> <span data-ttu-id="69cb5-107">Пространственное сопоставление также обеспечивает привязку объектов в мире пользователя на основе признаков глубины. Это помогает убедить пользователя в том, что эти голограммы на самом деле находятся в его пространстве.</span><span class="sxs-lookup"><span data-stu-id="69cb5-107">Spatial mapping also anchors objects in the user's world by taking advantage of depth cues, helping convince them that these holograms are actually in their space.</span></span> <span data-ttu-id="69cb5-108">Голограммы, плавающие в пространстве или перемещающиеся вместе с пользователем не будут ощущаться как реальные, поэтому всегда следует помещать элементы в удобном расположении.</span><span class="sxs-lookup"><span data-stu-id="69cb5-108">Holograms floating in space or moving with the user won't feel as real, so you always want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="69cb5-109">Дополнительные сведения о качестве пространственного сопоставления, размещении объектов, загораживании, отрисовке и других аспектах см. в разделе справки "[Пространственное сопоставление](../../design/spatial-mapping.md)".</span><span class="sxs-lookup"><span data-stu-id="69cb5-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="69cb5-110">Включение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="69cb5-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="69cb5-111">Чтобы включить пространственное сопоставление для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="69cb5-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="69cb5-112">Выберите **Edit > Project Settings** (Правка > Параметры проекта) и прокрутите вниз до раздела **Platforms** (Платформы).</span><span class="sxs-lookup"><span data-stu-id="69cb5-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="69cb5-113">Выберите **HoloLens** и установите флажок **Spatial Perception** (Пространственное восприятие).</span><span class="sxs-lookup"><span data-stu-id="69cb5-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Снимок экрана: параметры проекта HoloLens с выделенным параметром пространственного восприятия](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="69cb5-115">Чтобы включить пространственное сопоставление (по умолчанию оно выключено) и отладить сетку **MRMesh** в игре для HoloLens:</span><span class="sxs-lookup"><span data-stu-id="69cb5-115">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="69cb5-116">Откройте компонент **ARSessionConfig** и разверните раздел **ARSettings > World Mapping** (Параметры дополненной реальности > Сопоставление мира).</span><span class="sxs-lookup"><span data-stu-id="69cb5-116">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="69cb5-117">Установите флажок **Generate Mesh Data from Tracked Geometry** (Генерировать данные сетки по отслеживаемой геометрии), который предписывает подключаемому модулю HoloLens начать асинхронную регистрацию данных пространственного сопоставления с выводом в Unreal посредством сетки **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="69cb5-117">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="69cb5-118">Установите флажок **Render Mesh Data in Wireframe** (Отрисовывать данные сетки в виде каркасной модели), чтобы контур каждого треугольника сетки **MRMesh** показывался белым цветом.</span><span class="sxs-lookup"><span data-stu-id="69cb5-118">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Хранилище пространственных привязок готово](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="69cb5-120">Пространственное сопоставление во время выполнения</span><span class="sxs-lookup"><span data-stu-id="69cb5-120">Spatial Mapping at runtime</span></span>
<span data-ttu-id="69cb5-121">Изменить логику пространственного сопоставления во время выполнения можно путем настройки следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="69cb5-121">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="69cb5-122">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens > Spatial Mapping** (HoloLens > Пространственное сопоставление):</span><span class="sxs-lookup"><span data-stu-id="69cb5-122">Open **Edit > Project Settings**, scroll down to the **Platforms** section, and select **HoloLens > Spatial Mapping**:</span></span> 

![Параметры пространственных привязок для проекта](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="69cb5-124">Параметр **Max Triangles Per Cubic Meter** (Максимальное число треугольников на кубический метр) задает плотность треугольников в сетке пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="69cb5-124">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="69cb5-125">Параметр **Spatial Meshing Volume Size** (Размер объема для пространственных сеток) задает размер куба вокруг игрока, в пределах которого будут отрисовываться и обновляться данные пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="69cb5-125">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="69cb5-126">Если предполагается, что приложение будет выполняться в обширном пространстве, следует указать в этом поле достаточно большое значение, чтобы оно лучше соответствовало пространству реального мира.</span><span class="sxs-lookup"><span data-stu-id="69cb5-126">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span> <span data-ttu-id="69cb5-127">Если приложению нужны голограммы только на поверхностях рядом с пользователем, значение в этом поле может быть небольшим.</span><span class="sxs-lookup"><span data-stu-id="69cb5-127">The value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="69cb5-128">По мере перемещения пользователя по игровому миру вместе с ним перемещается и пространство для пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="69cb5-128">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="69cb5-129">Работа с сеткой MRMesh</span><span class="sxs-lookup"><span data-stu-id="69cb5-129">Working with MRMesh</span></span>

<span data-ttu-id="69cb5-130">Сначала вам нужно запустить пространственное сопоставление:</span><span class="sxs-lookup"><span data-stu-id="69cb5-130">First, you need to start Spatial Mapping:</span></span>

![Схема функции ToggleARCapture с выделенным типом захвата Spatial Mapping (пространственное сопоставление)](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="69cb5-132">После захвата пространственного сопоставления для пространства мы рекомендуем отключить его.</span><span class="sxs-lookup"><span data-stu-id="69cb5-132">Once spatial mapping has been captured for the space, we recommend toggling off spatial mapping.</span></span>  <span data-ttu-id="69cb5-133">Пространственное сопоставление может быть выполнено после определенного периода времени или после того, как лучи, выпущенные во всех направлениях, возвратят столкновения с MRMesh.</span><span class="sxs-lookup"><span data-stu-id="69cb5-133">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="69cb5-134">Чтобы получить доступ к сетке **MRMesh** во время выполнения:</span><span class="sxs-lookup"><span data-stu-id="69cb5-134">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="69cb5-135">Добавьте к субъекту Blueprint компонент **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="69cb5-135">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![AR Trackable Notify для пространственных привязок](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="69cb5-137">Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="69cb5-137">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="69cb5-138">Нажмите кнопку **+** на событиях, которые нужно отслеживать.</span><span class="sxs-lookup"><span data-stu-id="69cb5-138">Select the **+** button on the events you want to monitor.</span></span> 

![События пространственных привязок](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="69cb5-140">В данном случае ведется мониторинг события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), которое ведет поиск действительных мировых сеток, соответствующих данным пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="69cb5-140">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="69cb5-141">Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="69cb5-141">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="69cb5-142">Изменить материал сетки можно в графе событий схемы или в коде на C++.</span><span class="sxs-lookup"><span data-stu-id="69cb5-142">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="69cb5-143">На приведенном ниже снимке экрана показан вариант действий с графом событий схемы.</span><span class="sxs-lookup"><span data-stu-id="69cb5-143">The screenshot below shows the Blueprint route:</span></span> 

![Пример пространственных привязок](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="69cb5-145">Пространственное сопоставление в C++</span><span class="sxs-lookup"><span data-stu-id="69cb5-145">Spatial Mapping in C++</span></span>

<span data-ttu-id="69cb5-146">В файле build.cs игры добавьте **AugmentedReality** и **MRMesh** в список PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="69cb5-146">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

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

<span data-ttu-id="69cb5-147">Чтобы получать доступ к MRMesh, подпишитесь на делегатов **OnTrackableAdded**:</span><span class="sxs-lookup"><span data-stu-id="69cb5-147">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

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
> <span data-ttu-id="69cb5-148">Также существуют аналогичные делегаты для обновленных и удаленных событий: **AddOnTrackableUpdatedDelegate_Handle** и **AddOnTrackableRemovedDelegate_Handle** соответственно.</span><span class="sxs-lookup"><span data-stu-id="69cb5-148">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="69cb5-149">Полный список событий можно найти в API объекта [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="69cb5-149">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="69cb5-150">См. также статью</span><span class="sxs-lookup"><span data-stu-id="69cb5-150">See also</span></span>
* [<span data-ttu-id="69cb5-151">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="69cb5-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
