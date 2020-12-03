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
# <a name="spatial-mapping-in-unreal"></a>Пространственное сопоставление в Unreal

Пространственное сопоставление позволяет помещать объекты на поверхности в физическом мире, показывая мир вокруг устройства HoloLens. За счет этого голограммы кажутся пользователю более реалистичными. Кроме того, пространственное сопоставление обеспечивает привязку объектов в мире пользователя, пользуясь признаками глубины из реального мира. Это помогает создать у пользователя впечатление, что голограммы физически находятся в одном с ним пространстве. Если голограммы будут висеть в воздухе или перемещаться, ощущения пользователя будут не столь реалистичными. При размещении объектов в пространстве нужно по возможности ориентироваться на комфорт.

Дополнительные сведения о качестве пространственного сопоставления, размещении объектов, загораживании, отрисовке и других аспектах см. в разделе справки "[Пространственное сопоставление](../../design/spatial-mapping.md)".

## <a name="enabling-spatial-mapping"></a>Включение пространственного сопоставления

Чтобы включить пространственное сопоставление для HoloLens:
- Выберите **Edit > Project Settings** (Правка > Параметры проекта) и прокрутите вниз до раздела **Platforms** (Платформы).    
    + Выберите **HoloLens** и установите флажок **Spatial Perception** (Пространственное восприятие).

![Снимок экрана: параметры проекта HoloLens с выделенным параметром пространственного восприятия](images/unreal-spatial-mapping-img-01.png)

Чтобы включить пространственное сопоставление (по умолчанию оно выключено) и отладить сетку **MRMesh** в игре для HoloLens:
1. Откройте компонент **ARSessionConfig** и разверните раздел **ARSettings > World Mapping** (Параметры дополненной реальности > Сопоставление мира). 

2. Установите флажок **Generate Mesh Data from Tracked Geometry** (Генерировать данные сетки по отслеживаемой геометрии), который предписывает подключаемому модулю HoloLens начать асинхронную регистрацию данных пространственного сопоставления с выводом в Unreal посредством сетки **MRMesh**. 
3. Установите флажок **Render Mesh Data in Wireframe** (Отрисовывать данные сетки в виде каркасной модели), чтобы контур каждого треугольника сетки **MRMesh** показывался белым цветом. 

![Хранилище пространственных привязок готово](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Пространственное сопоставление во время выполнения
Изменить логику пространственного сопоставления во время выполнения можно путем настройки следующих параметров:

- Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите вниз до раздела **Platforms** (Платформы) и выберите **HoloLens > Spatial Mapping** (HoloLens > Пространственное сопоставление): 

![Параметры пространственных привязок для проекта](images/unreal-spatialmapping-projectsettings.PNG)

- Параметр **Max Triangles Per Cubic Meter** (Максимальное число треугольников на кубический метр) задает плотность треугольников в сетке пространственного сопоставления.  
- Параметр **Spatial Meshing Volume Size** (Размер объема для пространственных сеток) задает размер куба вокруг игрока, в пределах которого будут отрисовываться и обновляться данные пространственного сопоставления.  
    + Если предполагается, что приложение будет выполняться в обширном пространстве, следует указать в этом поле достаточно большое значение, чтобы оно лучше соответствовало пространству реального мира.  Если же приложению нужны голограммы только на поверхностях рядом с пользователем, значение в этом поле может быть небольшим. По мере перемещения пользователя по игровому миру вместе с ним перемещается и пространство для пространственных сопоставлений. 

## <a name="working-with-mrmesh"></a>Работа с сеткой MRMesh

Сначала вам нужно запустить пространственное сопоставление:

![Схема функции ToggleARCapture с выделенным типом захвата Spatial Mapping (пространственное сопоставление)](images/unreal-spatial-mapping-img-02.png)

После захвата пространственного сопоставления для пространства мы рекомендуем отключить его.  Пространственное сопоставление может быть выполнено после определенного периода времени или после того, как лучи, выпущенные во всех направлениях, возвратят столкновения с MRMesh.

Чтобы получить доступ к сетке **MRMesh** во время выполнения:
1. Добавьте к субъекту Blueprint компонент **ARTrackableNotify**. 

![AR Trackable Notify для пространственных привязок](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Выберите компонент **ARTrackableNotify** и в панели **Details** (Сведения) разверните раздел **Events** (События). 
    - Нажмите кнопку **+** на событиях, мониторинг которых требуется вести. 

![События пространственных привязок](images/unreal-spatialmapping-events.PNG)

В данном случае ведется мониторинг события **On Add Tracked Geometry** (При добавлении отслеживаемой геометрии), которое ведет поиск действительных мировых сеток, соответствующих данным пространственного сопоставления. Полный список событий можно найти в API объекта [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Изменить материал сетки можно в графе событий схемы или в коде на C++. На приведенном ниже снимке экрана показан вариант действий с графом событий схемы. 

![Пример пространственных привязок](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Пространственное сопоставление в C++

В файле build.cs игры добавьте **AugmentedReality** и **MRMesh** в список PublicDependencyModuleNames:

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

Чтобы получать доступ к MRMesh, подпишитесь на делегатов **OnTrackableAdded**:

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
> Также существуют аналогичные делегаты для обновленных и удаленных событий: **AddOnTrackableUpdatedDelegate_Handle** и **AddOnTrackableRemovedDelegate_Handle** соответственно.
>
> Полный список событий можно найти в API объекта [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>См. также статью
* [Пространственное сопоставление](../../design/spatial-mapping.md)
