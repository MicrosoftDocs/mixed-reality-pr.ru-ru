---
title: Наблюдатель сетки пространственных объектов
description: Документация по наблюдателю пространственной сетки в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176696"
---
# <a name="spatial-object-mesh-observer"></a><span data-ttu-id="beeba-104">Наблюдатель сетки пространственных объектов</span><span class="sxs-lookup"><span data-stu-id="beeba-104">Spatial object mesh observer</span></span>

<span data-ttu-id="beeba-105">Удобный способ предоставления данных сетки среды в редакторе Unity — использование [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) класса.</span><span class="sxs-lookup"><span data-stu-id="beeba-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="beeba-106">*Наблюдатель сетки пространственных объектов* — это поставщик данных только для редактора для [системы пространственной](spatial-awareness-getting-started.md) информации, который позволяет импортировать данные трехмерной модели для представления пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="beeba-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="beeba-107">одним из распространенных способов использования *наблюдателя сетки пространственных объектов* является импорт данных, сканированных с помощью Microsoft HoloLens, чтобы проверить, как процесс адаптируется к различным средам в Unity.</span><span class="sxs-lookup"><span data-stu-id="beeba-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="beeba-108">Начало работы</span><span class="sxs-lookup"><span data-stu-id="beeba-108">Getting started</span></span>

<span data-ttu-id="beeba-109">В этом руководстве рассматривается настройка *наблюдателя сетки пространственных объектов*.</span><span class="sxs-lookup"><span data-stu-id="beeba-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="beeba-110">Включить эту функцию можно тремя основными действиями.</span><span class="sxs-lookup"><span data-stu-id="beeba-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="beeba-111">Добавление *наблюдателя сетки пространственных объектов* в системный профиль пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="beeba-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="beeba-112">Задание объекта данных сетки среды</span><span class="sxs-lookup"><span data-stu-id="beeba-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="beeba-113">Настройка остальных свойств профиля наблюдателя сетки</span><span class="sxs-lookup"><span data-stu-id="beeba-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="beeba-114">Настройка профиля *наблюдателя для сетки пространственных объектов*</span><span class="sxs-lookup"><span data-stu-id="beeba-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="beeba-115">выберите нужный профиль конфигурации *набор средств смешанной реальности* или выберите объект *набор средств смешанной реальности* в сцене.</span><span class="sxs-lookup"><span data-stu-id="beeba-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="beeba-116">Открытие или развертывание вкладки *системы пространственной* информации</span><span class="sxs-lookup"><span data-stu-id="beeba-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="beeba-117">Нажмите кнопку *"добавить пространственный наблюдатель"*</span><span class="sxs-lookup"><span data-stu-id="beeba-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Добавить пространственный наблюдатель](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="beeba-119">Выберите тип *спатиалобжектмешобсервер*</span><span class="sxs-lookup"><span data-stu-id="beeba-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Выбор наблюдателя сетки пространственных объектов](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="beeba-121">Выберите нужный *объект пространственного сетки*.</span><span class="sxs-lookup"><span data-stu-id="beeba-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="beeba-122">По умолчанию наблюдатель настроен с использованием примера модели.</span><span class="sxs-lookup"><span data-stu-id="beeba-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="beeba-123">эта модель была создана с помощью Microsoft HoloLens но можно [создать новый объект "просмотр сетки](#acquiring-environment-scans)".</span><span class="sxs-lookup"><span data-stu-id="beeba-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="beeba-124">Настройка остальных свойств профиля наблюдателя сетки</span><span class="sxs-lookup"><span data-stu-id="beeba-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Выбор объекта сетки](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="beeba-126">Заметки профиля наблюдателя для сетки пространственных объектов</span><span class="sxs-lookup"><span data-stu-id="beeba-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="beeba-127">Поскольку *наблюдатель сетки пространственных объектов* загружает данные из трехмерной модели, он не учитывает некоторые стандартные параметры наблюдателя сетки, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="beeba-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="beeba-128">**Интервал обновления**</span><span class="sxs-lookup"><span data-stu-id="beeba-128">**Update Interval**</span></span>

<span data-ttu-id="beeba-129">*Наблюдатель сетки пространственных объектов* отправляет все сетки приложению при загрузке модели.</span><span class="sxs-lookup"><span data-stu-id="beeba-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="beeba-130">Он не моделирует разности времени между обновлениями.</span><span class="sxs-lookup"><span data-stu-id="beeba-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="beeba-131">Приложение может повторно получить события сетки путем вызова методов [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) и [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="beeba-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="beeba-132">**Является стационарным наблюдателем**</span><span class="sxs-lookup"><span data-stu-id="beeba-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="beeba-133">*Наблюдатель сетки пространственных объектов* считает, что все объекты трехмерной сетки являются стационарными и не считаются источниками.</span><span class="sxs-lookup"><span data-stu-id="beeba-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="beeba-134">**Фигура и экстенты наблюдателя**</span><span class="sxs-lookup"><span data-stu-id="beeba-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="beeba-135">*Наблюдатель сетки пространственных объектов* отправляет в приложение всю трехмерную сетку.</span><span class="sxs-lookup"><span data-stu-id="beeba-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="beeba-136">Формы и экстенты наблюдателя не рассматриваются.</span><span class="sxs-lookup"><span data-stu-id="beeba-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="beeba-137">**Уровень детализации и треугольников/кубических индикаторов**</span><span class="sxs-lookup"><span data-stu-id="beeba-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="beeba-138">Наблюдатель не пытается найти Лодс трехмерной модели при отправке сеток в приложение.</span><span class="sxs-lookup"><span data-stu-id="beeba-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="beeba-139">Получение просмотров среды</span><span class="sxs-lookup"><span data-stu-id="beeba-139">Acquiring environment scans</span></span>

<span data-ttu-id="beeba-140">В этом разделе описываются дополнительные сведения о создании и сборе файлов *объектов пространственного сетки* для использования с *наблюдателем сетки пространственных объектов*.</span><span class="sxs-lookup"><span data-stu-id="beeba-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="beeba-141">Портал устройств Windows</span><span class="sxs-lookup"><span data-stu-id="beeba-141">Windows Device Portal</span></span>

<span data-ttu-id="beeba-142">[портал Windows устройств](/windows/mixed-reality/using-the-windows-device-portal) можно использовать для загрузки пространственной сетки в виде obj-файла с устройства Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="beeba-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="beeba-143">Сканирование путем простого прохода и просмотра нужной среды с помощью HoloLens</span><span class="sxs-lookup"><span data-stu-id="beeba-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="beeba-144">Подключение HoloLens с помощью Windows портала устройств</span><span class="sxs-lookup"><span data-stu-id="beeba-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="beeba-145">Переход на страницу « *объемное представление* »</span><span class="sxs-lookup"><span data-stu-id="beeba-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="beeba-146">Нажмите кнопку *Обновить* в разделе *пространственное сопоставление* .</span><span class="sxs-lookup"><span data-stu-id="beeba-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="beeba-147">Нажмите кнопку *сохранить* в разделе *пространственное сопоставление* , чтобы сохранить файл obj на ПК.</span><span class="sxs-lookup"><span data-stu-id="beeba-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="beeba-148">**Файлы Холотулкит. Room**</span><span class="sxs-lookup"><span data-stu-id="beeba-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="beeba-149">Многие разработчики ранее использовали Холотулкит для сканирования сред и создания файлов комнаты.</span><span class="sxs-lookup"><span data-stu-id="beeba-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="beeba-150">смешанная реальность набор средств теперь поддерживает импорт этих файлов как объекты gameobject в Unity и их использование в качестве *объектов пространственных сеток* в наблюдателе.</span><span class="sxs-lookup"><span data-stu-id="beeba-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="beeba-151">См. также:</span><span class="sxs-lookup"><span data-stu-id="beeba-151">See also</span></span>

- [<span data-ttu-id="beeba-152">Профили</span><span class="sxs-lookup"><span data-stu-id="beeba-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="beeba-153">рекомендации по настройке профиля набор средств смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="beeba-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="beeba-154">Начало работы с пространственными сведениями</span><span class="sxs-lookup"><span data-stu-id="beeba-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="beeba-155">Настройка наблюдателей сетки на устройстве</span><span class="sxs-lookup"><span data-stu-id="beeba-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="beeba-156">Настройка наблюдателей сетки с помощью кода</span><span class="sxs-lookup"><span data-stu-id="beeba-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="beeba-157">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="beeba-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)