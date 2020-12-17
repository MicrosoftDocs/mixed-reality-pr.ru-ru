---
title: Системы координат в DirectX
description: Сведения о системах координат в DirectX и смешанной реальности с пространственными локаторами, ссылочными кадрами и пространственными привязками. Используйте Спатиалстаже и обрабатывайте отслеживание потерь, сохранение и загрузка привязок, а также Image стабилизации.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Смешанная реальность, пространственный локатор, фрейм пространственной ссылки, система пространственных координат, пространственный этап, пример кода, стабилизации изображения, пространственный якорь, хранилище пространственных привязок, отслеживание потерь, пошаговое руководство, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, головной телефон
ms.openlocfilehash: 7bf2309f3fb6264d6b1a5232f7ead78b771c1649
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613118"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="df8f5-105">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="df8f5-105">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="df8f5-106">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="df8f5-106">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="df8f5-107">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="df8f5-107">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="df8f5-108">[Системы координат](../../design/coordinate-systems.md) формируют базу для пространственного понимания, предлагаемого интерфейсами API Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="df8f5-108">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="df8f5-109">Современные устройства VR или с одним помещением в рабочее место устанавливают одну основную систему координат для их прослеживания.</span><span class="sxs-lookup"><span data-stu-id="df8f5-109">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="df8f5-110">Устройства смешанной реальности, такие как HoloLens, предназначены для крупных неопределенных сред, при этом устройства обнаруживаются и изучены окружающую среду по мере пошагового изучения пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-110">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="df8f5-111">Устройство адаптируется к постоянному улучшению знаний о комнатах пользователей, но приводит к системам координат, которые меняют их связь друг с другом по времени существования приложений.</span><span class="sxs-lookup"><span data-stu-id="df8f5-111">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="df8f5-112">Windows Mixed Reality поддерживает широкий спектр устройств, начиная от променяющихся впечатляющих головок с помощью связанных с миром кадров ссылок.</span><span class="sxs-lookup"><span data-stu-id="df8f5-112">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="df8f5-113">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="df8f5-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="df8f5-114">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="df8f5-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="df8f5-115">Пространственные системы координат в Windows</span><span class="sxs-lookup"><span data-stu-id="df8f5-115">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="df8f5-116">Основной тип, используемый в качестве основания для реальных систем координат в Windows, — это <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-116">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="df8f5-117">Экземпляр этого типа представляет произвольную систему координат, предоставляя метод для получения данных матрицы преобразования, которые можно использовать для преобразования между двумя системами координат, не зная сведений о них.</span><span class="sxs-lookup"><span data-stu-id="df8f5-117">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="df8f5-118">Методы, возвращающие пространственные данные, принимают параметр Спатиалкурдинатесистем, чтобы вы могли выбрать систему координат, в которой она наиболее полезна для возвращения этих координат.</span><span class="sxs-lookup"><span data-stu-id="df8f5-118">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="df8f5-119">Пространственные данные представлены в виде точек, лучей или томов в окружающей области пользователя, а единицы для этих координат всегда будут в метрах.</span><span class="sxs-lookup"><span data-stu-id="df8f5-119">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="df8f5-120">Спатиалкурдинатесистем имеет динамическую связь с другими системами координат, включая те, которые представляют положение устройства.</span><span class="sxs-lookup"><span data-stu-id="df8f5-120">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="df8f5-121">На любом этапе устройство может размещать некоторые системы координат, а не другие.</span><span class="sxs-lookup"><span data-stu-id="df8f5-121">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="df8f5-122">Для большинства систем координат приложение должно быть готово к обработке периодов времени, в течение которых они не могут быть найдены.</span><span class="sxs-lookup"><span data-stu-id="df8f5-122">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="df8f5-123">Приложение не должно напрямую создавать Спатиалкурдинатесистемс, а должно использоваться через API-интерфейсы восприятия.</span><span class="sxs-lookup"><span data-stu-id="df8f5-123">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="df8f5-124">В API-интерфейсах восприятия есть три основных источника систем координат, каждая из которых соответствует концепции, описанной на странице [системы координат](../../design/coordinate-systems.md) .</span><span class="sxs-lookup"><span data-stu-id="df8f5-124">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="df8f5-125">Чтобы получить стационарный кадр Reference, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">спатиалстатионарифрамеофреференце</a> или получите его из текущего <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">спатиалстажефрамеофреференце</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-125">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="df8f5-126">Чтобы получить пространственное привязку, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">спатиаланчор</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-126">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="df8f5-127">Чтобы получить присоединенную рамку ссылки, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">спатиаллокатораттачедфрамеофреференце</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-127">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="df8f5-128">Все системы координат, возвращенные этими объектами, находятся справа, с + y вверх, + x справа и + z в обратном направлении.</span><span class="sxs-lookup"><span data-stu-id="df8f5-128">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="df8f5-129">Вы можете вспомнить направление положительных точек по оси z, нажимая пальцы в левой или правой руки в положительном направлении x и заметив их положительным направлением по оси y.</span><span class="sxs-lookup"><span data-stu-id="df8f5-129">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="df8f5-130">Направление, в котором указывают ваши пальцы (к вам или от вас), — это направление, в котором указывает положительная ось z в этой системе координат.</span><span class="sxs-lookup"><span data-stu-id="df8f5-130">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="df8f5-131">На следующем рисунке показаны эти две системы координат.</span><span class="sxs-lookup"><span data-stu-id="df8f5-131">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="df8f5-132">![Руки и правая система координат](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="df8f5-132">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="df8f5-133">*Руки и правая система координат*</span><span class="sxs-lookup"><span data-stu-id="df8f5-133">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="df8f5-134">Используйте класс <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a> , чтобы создать присоединенный или стационарный кадр ссылки для начальной загрузки в спатиалкурдинатесистем на основе расположения HoloLens.</span><span class="sxs-lookup"><span data-stu-id="df8f5-134">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="df8f5-135">Перейдите к следующему разделу, чтобы узнать больше об этом процессе.</span><span class="sxs-lookup"><span data-stu-id="df8f5-135">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="df8f5-136">Размещение голограмм в мире с помощью пространственного этапа</span><span class="sxs-lookup"><span data-stu-id="df8f5-136">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="df8f5-137">Доступ к системе координат для непрозрачных впечатляющих головных телефонов Windows Mixed Reality осуществляется с помощью статического свойства <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">спатиалстажефрамеофреференце:: Current</a> .</span><span class="sxs-lookup"><span data-stu-id="df8f5-137">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="df8f5-138">Этот API предоставляет следующие функции:</span><span class="sxs-lookup"><span data-stu-id="df8f5-138">This API provides:</span></span>

* <span data-ttu-id="df8f5-139">Система координат</span><span class="sxs-lookup"><span data-stu-id="df8f5-139">A coordinate system</span></span>
* <span data-ttu-id="df8f5-140">Сведения о том, установлен ли проигрыватель в рабочее состояние или мобильное устройство</span><span class="sxs-lookup"><span data-stu-id="df8f5-140">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="df8f5-141">Граница надежной области для обхода, если проигрыватель является мобильным</span><span class="sxs-lookup"><span data-stu-id="df8f5-141">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="df8f5-142">Указывает, является ли гарнитура направленной.</span><span class="sxs-lookup"><span data-stu-id="df8f5-142">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="df8f5-143">Обработчик событий для обновлений на пространственном этапе.</span><span class="sxs-lookup"><span data-stu-id="df8f5-143">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="df8f5-144">Во первых, мы получаем пространственный этап и подписались на его обновления:</span><span class="sxs-lookup"><span data-stu-id="df8f5-144">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="df8f5-145">Код для **инициализации пространственного этапа**</span><span class="sxs-lookup"><span data-stu-id="df8f5-145">Code for **Spatial stage initialization**</span></span>

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

<span data-ttu-id="df8f5-146">В методе Онкуррентчанжед приложение должно проверить пространственный этап и обновить интерфейс проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-146">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="df8f5-147">В этом примере мы предоставляем визуализацию границы этапа и начальную точку, заданную пользователем, а также диапазон представлений и диапазон свойств перемещения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-147">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="df8f5-148">Мы также вернемся к нашей стационарной системе координат, когда невозможно предоставить этап.</span><span class="sxs-lookup"><span data-stu-id="df8f5-148">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="df8f5-149">Код для **обновления пространственного этапа**</span><span class="sxs-lookup"><span data-stu-id="df8f5-149">Code for **Spatial stage update**</span></span>

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

<span data-ttu-id="df8f5-150">Набор вершин, определяющих границу этапа, указывается в порядке по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="df8f5-150">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="df8f5-151">Оболочка Windows Mixed Reality выводит ограждение на границе, когда пользователь его приближает, но вы можете захотеть триангуларизе область неанализируемой для собственных целей.</span><span class="sxs-lookup"><span data-stu-id="df8f5-151">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="df8f5-152">Для триангуларизе этапа можно использовать следующий алгоритм.</span><span class="sxs-lookup"><span data-stu-id="df8f5-152">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="df8f5-153">Код для **треугольия пространственного этапа**</span><span class="sxs-lookup"><span data-stu-id="df8f5-153">Code for **Spatial stage triangularization**</span></span>

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="df8f5-154">Поместите голограммы в мир с помощью стационарной рамки ссылки</span><span class="sxs-lookup"><span data-stu-id="df8f5-154">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="df8f5-155">Класс [спатиалстатионарифрамеофреференце](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) представляет кадр ссылки, который [остается стационарным](../../design/coordinate-systems.md#stationary-frame-of-reference) по отношению к окружающей области пользователя при движении пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-155">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="df8f5-156">Этот кадр ссылок указывает на то, что координаты на устройстве постоянно стабильны.</span><span class="sxs-lookup"><span data-stu-id="df8f5-156">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="df8f5-157">Одним из ключевых способов использования Спатиалстатионарифрамеофреференце является система координат в основном мире в механизме визуализации при отрисовке голограмм.</span><span class="sxs-lookup"><span data-stu-id="df8f5-157">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="df8f5-158">Чтобы получить Спатиалстатионарифрамеофреференце, используйте класс [спатиаллокатор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) и вызовите [креатестатионарифрамеофреференцеаткуррентлокатион](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="df8f5-158">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="df8f5-159">Из кода шаблона приложения Windows holographic:</span><span class="sxs-lookup"><span data-stu-id="df8f5-159">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="df8f5-160">Стационарные опорные кадры предназначены для обеспечения наилучшего позиционирования относительно общего пространства.</span><span class="sxs-lookup"><span data-stu-id="df8f5-160">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="df8f5-161">Отдельные положения в рамках рамки ссылки могут немного отменяться.</span><span class="sxs-lookup"><span data-stu-id="df8f5-161">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="df8f5-162">Это нормально, так как устройство более подробно рассказывает о среде.</span><span class="sxs-lookup"><span data-stu-id="df8f5-162">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="df8f5-163">Если требуется точное размещение отдельных голограмм, следует использовать Спатиаланчор, чтобы закрепить отдельную голограмму до положения в реальной жизни, например, для того, чтобы пользователь указывал на специальный интерес.</span><span class="sxs-lookup"><span data-stu-id="df8f5-163">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="df8f5-164">Позиции привязки не имеют смещения, но могут быть исправлены; привязка будет использовать исправленную точку, начиная со следующего кадра после исправления.</span><span class="sxs-lookup"><span data-stu-id="df8f5-164">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="df8f5-165">Размещайте голограммы в мире с помощью пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="df8f5-165">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="df8f5-166">[Пространственные привязки](../../design/coordinate-systems.md#spatial-anchors) — это отличный способ размещения голограмм в определенном месте в реальном мире, где система гарантирует, что привязка остается на месте с течением времени.</span><span class="sxs-lookup"><span data-stu-id="df8f5-166">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="df8f5-167">В этом разделе объясняется, как создать и использовать привязку, а также как работать с данными привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-167">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="df8f5-168">Вы можете создать Спатиаланчор в любой позиции и ориентации в пределах Спатиалкурдинатесистем выбора.</span><span class="sxs-lookup"><span data-stu-id="df8f5-168">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="df8f5-169">Устройство должно иметь возможность нахождение этой системы координат в данный момент, и система не должна достигнуть предельного числа пространственных привязок.</span><span class="sxs-lookup"><span data-stu-id="df8f5-169">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="df8f5-170">После определения система координат Спатиаланчор настраивается непрерывно, чтобы обеспечить точную позицию и ориентацию исходного расположения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-170">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="df8f5-171">Затем эту Спатиаланчор можно использовать для визуализации голограмм, которые будут отображаться в пользовательской области в определенном месте.</span><span class="sxs-lookup"><span data-stu-id="df8f5-171">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="df8f5-172">Влияние корректировок, которые сохраняют привязку на месте, увеличивается по мере увеличения расстояния от точки привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-172">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="df8f5-173">Следует избегать отрисовки содержимого относительно привязки, которая больше 3 метров от источника этой привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-173">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="df8f5-174">Свойство [курдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) получает систему координат, которая позволяет разместить содержимое относительно привязки с применением замедления, когда устройство корректирует точное расположение привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-174">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="df8f5-175">Для самостоятельного управления настройкой используйте свойство [равкурдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) и соответствующее событие [равкурдинатесистемаджустед](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) .</span><span class="sxs-lookup"><span data-stu-id="df8f5-175">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="df8f5-176">Сохранение и совместное использование пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="df8f5-176">Persist and share spatial anchors</span></span>

<span data-ttu-id="df8f5-177">Вы можете сохранить Спатиаланчор локально с помощью класса [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) , а затем вернуть его в будущем сеансе приложения на том же устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="df8f5-177">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="df8f5-178">С помощью <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">пространственных привязок Azure</a>можно создать устойчивую облачную привязку на основе локальной спатиаланчор, которую приложение может затем разместить на нескольких устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="df8f5-178">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="df8f5-179">При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="df8f5-179">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="df8f5-180">Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> для асинхронного сохранения голограмм на устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="df8f5-180">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="df8f5-181">При совместном использовании пространственной геодоступной облачной привязки несколько устройств могут отслеживать одну и ту же голограмму с течением времени, даже если эти устройства не присутствуют одновременно.</span><span class="sxs-lookup"><span data-stu-id="df8f5-181">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="df8f5-182">Чтобы приступить к созданию общих интерфейсов в приложении HoloLens, ознакомьтесь с кратким руководством по HoloLens в течение 5 минут для <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">пространственных привязок Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-182">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="df8f5-183">После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создавать и размещать привязки на HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="df8f5-183">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="df8f5-184">Также доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> , что позволяет использовать одни и те же привязки на всех устройствах.</span><span class="sxs-lookup"><span data-stu-id="df8f5-184">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="df8f5-185">Создание Спатиаланчорс для holographic содержимого</span><span class="sxs-lookup"><span data-stu-id="df8f5-185">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="df8f5-186">В этом примере кода мы изменили шаблон приложения Windows holographic для создания привязок при обнаружении **нажатого** жеста.</span><span class="sxs-lookup"><span data-stu-id="df8f5-186">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="df8f5-187">Затем куб помещается на привязку во время передачи прорисовки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-187">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="df8f5-188">Так как вспомогательный класс поддерживает несколько привязок, можно разместить столько кубов, сколько нужно для использования этого примера кода!</span><span class="sxs-lookup"><span data-stu-id="df8f5-188">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="df8f5-189">Идентификаторы для привязок — это то, что вы управляете в приложении.</span><span class="sxs-lookup"><span data-stu-id="df8f5-189">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="df8f5-190">В этом примере мы создали схему именования, которая будет последовательной в зависимости от количества привязок, которые в настоящее время хранятся в коллекции привязок приложения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-190">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="df8f5-191">Асинхронная загрузка и кэширование, Спатиаланчорсторе</span><span class="sxs-lookup"><span data-stu-id="df8f5-191">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="df8f5-192">Давайте посмотрим, как написать класс Самплеспатиаланчорхелпер, который помогает справиться с этим сохраняемостью, в том числе:</span><span class="sxs-lookup"><span data-stu-id="df8f5-192">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="df8f5-193">Хранение коллекции привязок в памяти, индексируемых ключом Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="df8f5-193">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="df8f5-194">Загрузка привязок из Спатиаланчорсторе системы, которая хранится отдельно от локальной коллекции в памяти.</span><span class="sxs-lookup"><span data-stu-id="df8f5-194">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="df8f5-195">Сохранение локальной коллекции привязок в памяти в Спатиаланчорсторе при выборе приложения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-195">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="df8f5-196">Ниже показано, как сохранить объекты [спатиаланчор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) в [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="df8f5-196">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="df8f5-197">При запуске класса мы запрашиваете Спатиаланчорсторе асинхронно.</span><span class="sxs-lookup"><span data-stu-id="df8f5-197">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="df8f5-198">Это подразумевает системный ввод-вывод, так как API загружает хранилище привязки, и этот API становится асинхронным, чтобы операции ввода-вывода не блокировались.</span><span class="sxs-lookup"><span data-stu-id="df8f5-198">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

<span data-ttu-id="df8f5-199">Вам будет предоставлен Спатиаланчорсторе, который можно использовать для сохранения привязок.</span><span class="sxs-lookup"><span data-stu-id="df8f5-199">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="df8f5-200">Это IMapView, связывающая значения ключей, которые являются строками, со значениями данных, которые являются Спатиаланчорс.</span><span class="sxs-lookup"><span data-stu-id="df8f5-200">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="df8f5-201">В нашем примере кода мы сохраняем это в переменной-члене закрытого класса, доступной через открытую функцию нашего вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="df8f5-201">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="df8f5-202">Не забудьте подключить события приостановки и возобновления для сохранения и загрузки хранилища привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-202">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="df8f5-203">Сохранение содержимого в хранилище привязки</span><span class="sxs-lookup"><span data-stu-id="df8f5-203">Save content to the anchor store</span></span>

<span data-ttu-id="df8f5-204">Когда система приостанавливает работу приложения, необходимо сохранить пространственные привязки в хранилище привязки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-204">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="df8f5-205">Вы также можете сохранить привязки в хранилище привязки в другое время, так как вы увидите, что это необходимо для реализации приложения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-205">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="df8f5-206">Когда вы будете готовы сохранить привязки в памяти для Спатиаланчорсторе, вы можете перебрать коллекцию и попытаться сохранить каждую из них.</span><span class="sxs-lookup"><span data-stu-id="df8f5-206">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="df8f5-207">Загружать содержимое из хранилища привязки при возобновлении работы приложения</span><span class="sxs-lookup"><span data-stu-id="df8f5-207">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="df8f5-208">Вы можете восстановить сохраненные привязки в Анчорсторе, передавая их из IMapView хранилища привязки в собственную базу данных в памяти Спатиаланчорс, когда приложение возобновляется или в любое время.</span><span class="sxs-lookup"><span data-stu-id="df8f5-208">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="df8f5-209">Чтобы восстановить привязки из Спатиаланчорсторе, восстановите каждый из них, который вас интересует, в собственную коллекцию в памяти.</span><span class="sxs-lookup"><span data-stu-id="df8f5-209">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="df8f5-210">Вам потребуется собственная база данных в памяти Спатиаланчорс, чтобы связать строки с создаваемым Спатиаланчорс.</span><span class="sxs-lookup"><span data-stu-id="df8f5-210">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="df8f5-211">В нашем примере кода мы решили использовать Windows:: Foundation:: Collections:: IMap для хранения привязок, что позволяет легко использовать тот же ключ и значение данных для Спатиаланчорсторе.</span><span class="sxs-lookup"><span data-stu-id="df8f5-211">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="df8f5-212">Восстанавливаемая привязка может не размещаемые сразу.</span><span class="sxs-lookup"><span data-stu-id="df8f5-212">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="df8f5-213">Например, это может быть привязка в отдельной комнате или в другом здании.</span><span class="sxs-lookup"><span data-stu-id="df8f5-213">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="df8f5-214">Привязки, извлеченные из Анчорсторе, должны быть протестированы для локатабилити перед их использованием.</span><span class="sxs-lookup"><span data-stu-id="df8f5-214">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="df8f5-215">В этом примере кода мы получаем все привязки из Анчорсторе.</span><span class="sxs-lookup"><span data-stu-id="df8f5-215">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="df8f5-216">Это не обязательно; приложение может точно выбрать и выбрать определенное подмножество привязок, используя значения ключа строки, которые являются значимыми для вашей реализации.</span><span class="sxs-lookup"><span data-stu-id="df8f5-216">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="df8f5-217">Очищать хранилище привязки при необходимости</span><span class="sxs-lookup"><span data-stu-id="df8f5-217">Clear the anchor store, when needed</span></span>

<span data-ttu-id="df8f5-218">Иногда необходимо очистить состояние приложения и записать новые данные.</span><span class="sxs-lookup"><span data-stu-id="df8f5-218">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="df8f5-219">Вот как это делается с помощью [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="df8f5-219">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="df8f5-220">С помощью нашего вспомогательного класса практически не нужно обернуть функцию Clear.</span><span class="sxs-lookup"><span data-stu-id="df8f5-220">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="df8f5-221">Мы решили сделать это в нашем примере реализации, так как наш вспомогательный класс получает ответственность за владельца экземпляра Спатиаланчорсторе.</span><span class="sxs-lookup"><span data-stu-id="df8f5-221">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="df8f5-222">Пример. Связывание систем координат привязки с стационарными системными координатами опорных кадров</span><span class="sxs-lookup"><span data-stu-id="df8f5-222">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="df8f5-223">Предположим, у вас есть привязка и вы хотите связать что-то в системе координат привязки с Спатиалстатионариреференцефраме, который вы уже используете для вашего другого содержимого.</span><span class="sxs-lookup"><span data-stu-id="df8f5-223">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="df8f5-224">Вы можете использовать [трижеттрансформто](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) , чтобы получить преобразование из системы координат привязки к элементу стационарного ссылочного фрейма:</span><span class="sxs-lookup"><span data-stu-id="df8f5-224">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

<span data-ttu-id="df8f5-225">Этот процесс полезен в двух случаях:</span><span class="sxs-lookup"><span data-stu-id="df8f5-225">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="df8f5-226">Он указывает, что два эталонных кадра могут быть понятны относительно друг друга, и;</span><span class="sxs-lookup"><span data-stu-id="df8f5-226">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="df8f5-227">Если это так, он предоставляет преобразование для непосредственного перехода от одной системы координат к другой.</span><span class="sxs-lookup"><span data-stu-id="df8f5-227">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="df8f5-228">С помощью этих сведений вы получите представление о пространственной связи между объектами между двумя эталонными кадрами.</span><span class="sxs-lookup"><span data-stu-id="df8f5-228">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="df8f5-229">Для подготовки к просмотру часто можно получить лучшие результаты, группируя объекты в соответствии с их исходным эталонным фреймом или привязкой.</span><span class="sxs-lookup"><span data-stu-id="df8f5-229">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="df8f5-230">Выполните отдельный этап отрисовки для каждой группы.</span><span class="sxs-lookup"><span data-stu-id="df8f5-230">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="df8f5-231">Матрицы представления более точны для объектов с преобразованиями модели, которые изначально создаются с использованием одной и той же системы координат.</span><span class="sxs-lookup"><span data-stu-id="df8f5-231">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="df8f5-232">Создание голограмм с помощью привязанного к устройству фрейма ссылки</span><span class="sxs-lookup"><span data-stu-id="df8f5-232">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="df8f5-233">Иногда требуется отобразить голограмму, которая [остается прикрепленной](../../design/coordinate-systems.md#attached-frame-of-reference) к расположению устройства, например панель с отладочной информацией или информационное сообщение, если устройство может определить его ориентацию, а не его положение в пространстве.</span><span class="sxs-lookup"><span data-stu-id="df8f5-233">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="df8f5-234">Для этого мы используем присоединенный фрейм ссылки.</span><span class="sxs-lookup"><span data-stu-id="df8f5-234">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="df8f5-235">Класс Спатиаллокатораттачедфрамеофреференце определяет системы координат, которые являются относительными для устройства, а не для реального мира.</span><span class="sxs-lookup"><span data-stu-id="df8f5-235">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="df8f5-236">Этот кадр имеет фиксированный заголовок относительно окружающей среды пользователя, указывающий в направлении, в котором пользователь был направлен при создании эталонного фрейма.</span><span class="sxs-lookup"><span data-stu-id="df8f5-236">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="df8f5-237">После этого все ориентации в этой рамке ссылки зависят от этого фиксированного заголовка, даже при вращении устройства пользователем.</span><span class="sxs-lookup"><span data-stu-id="df8f5-237">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="df8f5-238">Для HoloLens происхождение системы координат этого фрейма находится в центре вращения заголовка пользователя, чтобы его положение не влияло на поворот головного элемента.</span><span class="sxs-lookup"><span data-stu-id="df8f5-238">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="df8f5-239">Приложение может указать смещение относительно этой точки, чтобы разместить голограммы перед пользователем.</span><span class="sxs-lookup"><span data-stu-id="df8f5-239">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="df8f5-240">Чтобы получить Спатиаллокатораттачедфрамеофреференце, используйте класс Спатиаллокатор и вызовите Креатеаттачедфрамеофреференцеаткурренсеадинг.</span><span class="sxs-lookup"><span data-stu-id="df8f5-240">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="df8f5-241">Это относится ко всему диапазону устройств Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="df8f5-241">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="df8f5-242">Использование ссылочного фрейма, присоединенного к устройству</span><span class="sxs-lookup"><span data-stu-id="df8f5-242">Use a reference frame attached to the device</span></span>

<span data-ttu-id="df8f5-243">В этих разделах мы поговорим о том, что мы изменили в шаблоне приложения Windows holographic, чтобы включить связанный с устройством фрейм ссылки с помощью этого API.</span><span class="sxs-lookup"><span data-stu-id="df8f5-243">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="df8f5-244">Эта «присоединенная» голограмма будет работать наряду с стационарными или прикрепленными голограммами, а также может использоваться, когда устройство временно не может найти свое местоположение в мире.</span><span class="sxs-lookup"><span data-stu-id="df8f5-244">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="df8f5-245">Сначала мы изменили шаблон, чтобы сохранить Спатиаллокатораттачедфрамеофреференце вместо Спатиалстатионарифрамеофреференце:</span><span class="sxs-lookup"><span data-stu-id="df8f5-245">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="df8f5-246">Из **холографиктагалонгсамплемаин. h**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-246">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="df8f5-247">Из **холографиктагалонгсамплемаин. cpp**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-247">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="df8f5-248">В ходе обновления теперь мы получаем систему координат в отметке времени, полученной с помощью прогнозирования кадров.</span><span class="sxs-lookup"><span data-stu-id="df8f5-248">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="df8f5-249">Получение пространственного указателя a и отслеживание пользователя</span><span class="sxs-lookup"><span data-stu-id="df8f5-249">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="df8f5-250">Мы хотим, чтобы наш пример голограммы проследовала [взгляд](../../design/gaze-and-commit.md)пользователя, аналогично тому, как с помощью оболочки holographic можно следовать взгляду пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-250">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="df8f5-251">Для этого нам нужно получить Спатиалпоинтерпосе из той же метки времени.</span><span class="sxs-lookup"><span data-stu-id="df8f5-251">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="df8f5-252">Этот Спатиалпоинтерпосе содержит сведения, необходимые для размещения голограммы в соответствии с [текущим заголовком пользователя](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="df8f5-252">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="df8f5-253">Для удобства пользователя мы используем линейную интерполяцию ("лерп"), чтобы сгладить изменение в положении в течение определенного периода времени.</span><span class="sxs-lookup"><span data-stu-id="df8f5-253">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="df8f5-254">Это более удобно для пользователя, чем блокировка голограммы до их взгляда.</span><span class="sxs-lookup"><span data-stu-id="df8f5-254">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="df8f5-255">Лерпингая с тегом голограмма также позволяет нам стабилизировать голограмму путем ослабления движения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-255">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="df8f5-256">Если это ослабление не было сделано, пользователь увидит неограниченную голограмму из-за того, что обычно считается незаметной передвижением заголовка пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-256">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="df8f5-257">Из **статионарикуадрендерер::P оситионхолограм**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-257">From **StationaryQuadRenderer::PositionHologram**:</span></span>

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
><span data-ttu-id="df8f5-258">В случае панели отладки можно изменить положение голограммы на сторону немного, чтобы она не переходила на ваше представление.</span><span class="sxs-lookup"><span data-stu-id="df8f5-258">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="df8f5-259">Ниже приведен пример того, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="df8f5-259">Here's an example of how you might do that.</span></span>

<span data-ttu-id="df8f5-260">Для **статионарикуадрендерер::P оситионхолограм**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-260">For **StationaryQuadRenderer::PositionHologram**:</span></span>

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="df8f5-261">Поворот голограммы на камеру</span><span class="sxs-lookup"><span data-stu-id="df8f5-261">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="df8f5-262">Не хватает для размещения голограммы, которая в данном случае является четырехъядерной; также необходимо повернуть объект, чтобы он был лицом к пользователю.</span><span class="sxs-lookup"><span data-stu-id="df8f5-262">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="df8f5-263">Этот поворот происходит в мировом пространстве, поскольку этот тип рекламы позволяет оставить голограмму частью среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-263">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="df8f5-264">Переход на пробелы в представлении не так удобен, так как голограмма становится заблокированной для ориентации экрана; в этом случае необходимо также выполнить интерполяцию между левым и правым матрицами представлений, чтобы получить преобразование стенда представления, которое не нарушает стерео отрисовку.</span><span class="sxs-lookup"><span data-stu-id="df8f5-264">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="df8f5-265">Здесь мы поворотим на оси X и Z пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-265">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="df8f5-266">Из **статионарикуадрендерер:: Update**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-266">From **StationaryQuadRenderer::Update**:</span></span>

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a><span data-ttu-id="df8f5-267">Подготовка присоединенной голограммы</span><span class="sxs-lookup"><span data-stu-id="df8f5-267">Render the attached hologram</span></span>

<span data-ttu-id="df8f5-268">В этом примере мы также решили визуализировать голограмму в системе координат Спатиаллокатораттачедреференцефраме, где мы разберем голограмму.</span><span class="sxs-lookup"><span data-stu-id="df8f5-268">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="df8f5-269">(Если бы мы решили подготовиться к просмотру с помощью другой системы координат, нам пришлось бы получить преобразование из системы координат связанного с устройством ссылочного фрейма в эту систему координат.)</span><span class="sxs-lookup"><span data-stu-id="df8f5-269">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="df8f5-270">Из **холографиктагалонгсамплемаин:: Render**:</span><span class="sxs-lookup"><span data-stu-id="df8f5-270">From **HolographicTagAlongSampleMain::Render**:</span></span>

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

<span data-ttu-id="df8f5-271">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="df8f5-271">That's it!</span></span> <span data-ttu-id="df8f5-272">Голограмма теперь будет «проследить» расположение, равное 2 метрах, перед направлением взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="df8f5-272">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="df8f5-273">В этом примере также загружается дополнительное содержимое — см. Статионарикуадрендерер. cpp.</span><span class="sxs-lookup"><span data-stu-id="df8f5-273">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="df8f5-274">Обработка потерь отслеживания</span><span class="sxs-lookup"><span data-stu-id="df8f5-274">Handling tracking loss</span></span>

<span data-ttu-id="df8f5-275">Если устройство не может располагаться в мире, в приложении происходит «отслеживание потерь».</span><span class="sxs-lookup"><span data-stu-id="df8f5-275">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="df8f5-276">Приложения Windows Mixed Reality должны иметь возможность обрабатывать такие нарушения в системе нацеленного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="df8f5-276">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="df8f5-277">Эти нарушения можно наблюдать и создавать ответы с помощью события Локатабилитичанжед по умолчанию Спатиаллокатор.</span><span class="sxs-lookup"><span data-stu-id="df8f5-277">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="df8f5-278">Из **аппмаин:: сесолографикспаце:**</span><span class="sxs-lookup"><span data-stu-id="df8f5-278">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="df8f5-279">Когда приложение получает событие Локатабилитичанжед, оно может изменить поведение по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="df8f5-279">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="df8f5-280">Например, в состоянии Поситионалтраккингинхибитед приложение может приостановить нормальную работу и вывести на экран [голограмму с пометкой](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , которая отображает предупреждающее сообщение.</span><span class="sxs-lookup"><span data-stu-id="df8f5-280">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="df8f5-281">Шаблон приложения Windows holographic поставляется с уже созданным обработчиком Локатабилитичанжед.</span><span class="sxs-lookup"><span data-stu-id="df8f5-281">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="df8f5-282">По умолчанию в консоли отладки отображается предупреждение, если позиционированное отслеживание недоступно.</span><span class="sxs-lookup"><span data-stu-id="df8f5-282">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="df8f5-283">Вы можете добавить код в этот обработчик, чтобы предоставить ответ по мере необходимости из приложения.</span><span class="sxs-lookup"><span data-stu-id="df8f5-283">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="df8f5-284">Из **аппмаин. cpp:**</span><span class="sxs-lookup"><span data-stu-id="df8f5-284">From **AppMain.cpp:**</span></span>

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a><span data-ttu-id="df8f5-285">пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="df8f5-285">Spatial mapping</span></span>

<span data-ttu-id="df8f5-286">API-интерфейсы [пространственного сопоставления](spatial-mapping-in-directx.md) используют системы координат для получения преобразований модели для сеток поверхности.</span><span class="sxs-lookup"><span data-stu-id="df8f5-286">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="df8f5-287">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="df8f5-287">See also</span></span>
* [<span data-ttu-id="df8f5-288">Системы координат</span><span class="sxs-lookup"><span data-stu-id="df8f5-288">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="df8f5-289">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="df8f5-289">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="df8f5-290"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a></span><span class="sxs-lookup"><span data-stu-id="df8f5-290"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="df8f5-291">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="df8f5-291">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="df8f5-292">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="df8f5-292">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="df8f5-293">Пространственное сопоставление в DirectX</span><span class="sxs-lookup"><span data-stu-id="df8f5-293">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
