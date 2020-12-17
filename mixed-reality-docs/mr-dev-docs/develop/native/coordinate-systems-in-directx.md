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
# <a name="coordinate-systems-in-directx"></a>Системы координат в DirectX

> [!NOTE]
> Эта статья связана с устаревшими собственными API-интерфейсами WinRT.  Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)**.

[Системы координат](../../design/coordinate-systems.md) формируют базу для пространственного понимания, предлагаемого интерфейсами API Windows Mixed Reality.

Современные устройства VR или с одним помещением в рабочее место устанавливают одну основную систему координат для их прослеживания. Устройства смешанной реальности, такие как HoloLens, предназначены для крупных неопределенных сред, при этом устройства обнаруживаются и изучены окружающую среду по мере пошагового изучения пользователя. Устройство адаптируется к постоянному улучшению знаний о комнатах пользователей, но приводит к системам координат, которые меняют их связь друг с другом по времени существования приложений. Windows Mixed Reality поддерживает широкий спектр устройств, начиная от променяющихся впечатляющих головок с помощью связанных с миром кадров ссылок.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="spatial-coordinate-systems-in-windows"></a>Пространственные системы координат в Windows

Основной тип, используемый в качестве основания для реальных систем координат в Windows, — это <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a>. Экземпляр этого типа представляет произвольную систему координат, предоставляя метод для получения данных матрицы преобразования, которые можно использовать для преобразования между двумя системами координат, не зная сведений о них.

Методы, возвращающие пространственные данные, принимают параметр Спатиалкурдинатесистем, чтобы вы могли выбрать систему координат, в которой она наиболее полезна для возвращения этих координат. Пространственные данные представлены в виде точек, лучей или томов в окружающей области пользователя, а единицы для этих координат всегда будут в метрах.

Спатиалкурдинатесистем имеет динамическую связь с другими системами координат, включая те, которые представляют положение устройства. На любом этапе устройство может размещать некоторые системы координат, а не другие. Для большинства систем координат приложение должно быть готово к обработке периодов времени, в течение которых они не могут быть найдены.

Приложение не должно напрямую создавать Спатиалкурдинатесистемс, а должно использоваться через API-интерфейсы восприятия. В API-интерфейсах восприятия есть три основных источника систем координат, каждая из которых соответствует концепции, описанной на странице [системы координат](../../design/coordinate-systems.md) .
* Чтобы получить стационарный кадр Reference, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">спатиалстатионарифрамеофреференце</a> или получите его из текущего <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">спатиалстажефрамеофреференце</a>.
* Чтобы получить пространственное привязку, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">спатиаланчор</a>.
* Чтобы получить присоединенную рамку ссылки, создайте <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">спатиаллокатораттачедфрамеофреференце</a>.

Все системы координат, возвращенные этими объектами, находятся справа, с + y вверх, + x справа и + z в обратном направлении. Вы можете вспомнить направление положительных точек по оси z, нажимая пальцы в левой или правой руки в положительном направлении x и заметив их положительным направлением по оси y. Направление, в котором указывают ваши пальцы (к вам или от вас), — это направление, в котором указывает положительная ось z в этой системе координат. На следующем рисунке показаны эти две системы координат.

![Руки и правая система координат](images/left-hand-right-hand.gif)<br>
*Руки и правая система координат*

Используйте класс <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a> , чтобы создать присоединенный или стационарный кадр ссылки для начальной загрузки в спатиалкурдинатесистем на основе расположения HoloLens. Перейдите к следующему разделу, чтобы узнать больше об этом процессе.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Размещение голограмм в мире с помощью пространственного этапа

Доступ к системе координат для непрозрачных впечатляющих головных телефонов Windows Mixed Reality осуществляется с помощью статического свойства <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">спатиалстажефрамеофреференце:: Current</a> . Этот API предоставляет следующие функции:

* Система координат
* Сведения о том, установлен ли проигрыватель в рабочее состояние или мобильное устройство
* Граница надежной области для обхода, если проигрыватель является мобильным
* Указывает, является ли гарнитура направленной. 
* Обработчик событий для обновлений на пространственном этапе.

Во первых, мы получаем пространственный этап и подписались на его обновления: 

Код для **инициализации пространственного этапа**

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

В методе Онкуррентчанжед приложение должно проверить пространственный этап и обновить интерфейс проигрывателя. В этом примере мы предоставляем визуализацию границы этапа и начальную точку, заданную пользователем, а также диапазон представлений и диапазон свойств перемещения. Мы также вернемся к нашей стационарной системе координат, когда невозможно предоставить этап.


Код для **обновления пространственного этапа**

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

Набор вершин, определяющих границу этапа, указывается в порядке по часовой стрелке. Оболочка Windows Mixed Reality выводит ограждение на границе, когда пользователь его приближает, но вы можете захотеть триангуларизе область неанализируемой для собственных целей. Для триангуларизе этапа можно использовать следующий алгоритм.


Код для **треугольия пространственного этапа**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Поместите голограммы в мир с помощью стационарной рамки ссылки

Класс [спатиалстатионарифрамеофреференце](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) представляет кадр ссылки, который [остается стационарным](../../design/coordinate-systems.md#stationary-frame-of-reference) по отношению к окружающей области пользователя при движении пользователя. Этот кадр ссылок указывает на то, что координаты на устройстве постоянно стабильны. Одним из ключевых способов использования Спатиалстатионарифрамеофреференце является система координат в основном мире в механизме визуализации при отрисовке голограмм.

Чтобы получить Спатиалстатионарифрамеофреференце, используйте класс [спатиаллокатор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) и вызовите [креатестатионарифрамеофреференцеаткуррентлокатион](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

Из кода шаблона приложения Windows holographic:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Стационарные опорные кадры предназначены для обеспечения наилучшего позиционирования относительно общего пространства. Отдельные положения в рамках рамки ссылки могут немного отменяться. Это нормально, так как устройство более подробно рассказывает о среде.
* Если требуется точное размещение отдельных голограмм, следует использовать Спатиаланчор, чтобы закрепить отдельную голограмму до положения в реальной жизни, например, для того, чтобы пользователь указывал на специальный интерес. Позиции привязки не имеют смещения, но могут быть исправлены; привязка будет использовать исправленную точку, начиная со следующего кадра после исправления.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Размещайте голограммы в мире с помощью пространственных привязок

[Пространственные привязки](../../design/coordinate-systems.md#spatial-anchors) — это отличный способ размещения голограмм в определенном месте в реальном мире, где система гарантирует, что привязка остается на месте с течением времени. В этом разделе объясняется, как создать и использовать привязку, а также как работать с данными привязки.

Вы можете создать Спатиаланчор в любой позиции и ориентации в пределах Спатиалкурдинатесистем выбора. Устройство должно иметь возможность нахождение этой системы координат в данный момент, и система не должна достигнуть предельного числа пространственных привязок.

После определения система координат Спатиаланчор настраивается непрерывно, чтобы обеспечить точную позицию и ориентацию исходного расположения. Затем эту Спатиаланчор можно использовать для визуализации голограмм, которые будут отображаться в пользовательской области в определенном месте.

Влияние корректировок, которые сохраняют привязку на месте, увеличивается по мере увеличения расстояния от точки привязки. Следует избегать отрисовки содержимого относительно привязки, которая больше 3 метров от источника этой привязки.

Свойство [курдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) получает систему координат, которая позволяет разместить содержимое относительно привязки с применением замедления, когда устройство корректирует точное расположение привязки.

Для самостоятельного управления настройкой используйте свойство [равкурдинатесистем](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) и соответствующее событие [равкурдинатесистемаджустед](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) .

### <a name="persist-and-share-spatial-anchors"></a>Сохранение и совместное использование пространственных привязок

Вы можете сохранить Спатиаланчор локально с помощью класса [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) , а затем вернуть его в будущем сеансе приложения на том же устройстве HoloLens.

С помощью <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">пространственных привязок Azure</a>можно создать устойчивую облачную привязку на основе локальной спатиаланчор, которую приложение может затем разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении в режиме реального времени. 

Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> для асинхронного сохранения голограмм на устройствах HoloLens, iOS и Android.  При совместном использовании пространственной геодоступной облачной привязки несколько устройств могут отслеживать одну и ту же голограмму с течением времени, даже если эти устройства не присутствуют одновременно.

Чтобы приступить к созданию общих интерфейсов в приложении HoloLens, ознакомьтесь с кратким руководством по HoloLens в течение 5 минут для <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">пространственных привязок Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создавать и размещать привязки на HoloLens</a>.  Также доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> , что позволяет использовать одни и те же привязки на всех устройствах.

### <a name="create-spatialanchors-for-holographic-content"></a>Создание Спатиаланчорс для holographic содержимого

В этом примере кода мы изменили шаблон приложения Windows holographic для создания привязок при обнаружении **нажатого** жеста. Затем куб помещается на привязку во время передачи прорисовки.

Так как вспомогательный класс поддерживает несколько привязок, можно разместить столько кубов, сколько нужно для использования этого примера кода!

> [!NOTE]
> Идентификаторы для привязок — это то, что вы управляете в приложении. В этом примере мы создали схему именования, которая будет последовательной в зависимости от количества привязок, которые в настоящее время хранятся в коллекции привязок приложения.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Асинхронная загрузка и кэширование, Спатиаланчорсторе

Давайте посмотрим, как написать класс Самплеспатиаланчорхелпер, который помогает справиться с этим сохраняемостью, в том числе:
* Хранение коллекции привязок в памяти, индексируемых ключом Platform:: String.
* Загрузка привязок из Спатиаланчорсторе системы, которая хранится отдельно от локальной коллекции в памяти.
* Сохранение локальной коллекции привязок в памяти в Спатиаланчорсторе при выборе приложения.

Ниже показано, как сохранить объекты [спатиаланчор](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) в [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

При запуске класса мы запрашиваете Спатиаланчорсторе асинхронно. Это подразумевает системный ввод-вывод, так как API загружает хранилище привязки, и этот API становится асинхронным, чтобы операции ввода-вывода не блокировались.

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

Вам будет предоставлен Спатиаланчорсторе, который можно использовать для сохранения привязок. Это IMapView, связывающая значения ключей, которые являются строками, со значениями данных, которые являются Спатиаланчорс. В нашем примере кода мы сохраняем это в переменной-члене закрытого класса, доступной через открытую функцию нашего вспомогательного класса.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Не забудьте подключить события приостановки и возобновления для сохранения и загрузки хранилища привязки.

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

### <a name="save-content-to-the-anchor-store"></a>Сохранение содержимого в хранилище привязки

Когда система приостанавливает работу приложения, необходимо сохранить пространственные привязки в хранилище привязки. Вы также можете сохранить привязки в хранилище привязки в другое время, так как вы увидите, что это необходимо для реализации приложения.

Когда вы будете готовы сохранить привязки в памяти для Спатиаланчорсторе, вы можете перебрать коллекцию и попытаться сохранить каждую из них.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Загружать содержимое из хранилища привязки при возобновлении работы приложения

Вы можете восстановить сохраненные привязки в Анчорсторе, передавая их из IMapView хранилища привязки в собственную базу данных в памяти Спатиаланчорс, когда приложение возобновляется или в любое время.

Чтобы восстановить привязки из Спатиаланчорсторе, восстановите каждый из них, который вас интересует, в собственную коллекцию в памяти.

Вам потребуется собственная база данных в памяти Спатиаланчорс, чтобы связать строки с создаваемым Спатиаланчорс. В нашем примере кода мы решили использовать Windows:: Foundation:: Collections:: IMap для хранения привязок, что позволяет легко использовать тот же ключ и значение данных для Спатиаланчорсторе.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Восстанавливаемая привязка может не размещаемые сразу. Например, это может быть привязка в отдельной комнате или в другом здании. Привязки, извлеченные из Анчорсторе, должны быть протестированы для локатабилити перед их использованием.

<br>

>[!NOTE]
>В этом примере кода мы получаем все привязки из Анчорсторе. Это не обязательно; приложение может точно выбрать и выбрать определенное подмножество привязок, используя значения ключа строки, которые являются значимыми для вашей реализации.

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

### <a name="clear-the-anchor-store-when-needed"></a>Очищать хранилище привязки при необходимости

Иногда необходимо очистить состояние приложения и записать новые данные. Вот как это делается с помощью [спатиаланчорсторе](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

С помощью нашего вспомогательного класса практически не нужно обернуть функцию Clear. Мы решили сделать это в нашем примере реализации, так как наш вспомогательный класс получает ответственность за владельца экземпляра Спатиаланчорсторе.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Пример. Связывание систем координат привязки с стационарными системными координатами опорных кадров

Предположим, у вас есть привязка и вы хотите связать что-то в системе координат привязки с Спатиалстатионариреференцефраме, который вы уже используете для вашего другого содержимого. Вы можете использовать [трижеттрансформто](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) , чтобы получить преобразование из системы координат привязки к элементу стационарного ссылочного фрейма:

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

Этот процесс полезен в двух случаях:
1. Он указывает, что два эталонных кадра могут быть понятны относительно друг друга, и;
2. Если это так, он предоставляет преобразование для непосредственного перехода от одной системы координат к другой.

С помощью этих сведений вы получите представление о пространственной связи между объектами между двумя эталонными кадрами.

Для подготовки к просмотру часто можно получить лучшие результаты, группируя объекты в соответствии с их исходным эталонным фреймом или привязкой. Выполните отдельный этап отрисовки для каждой группы. Матрицы представления более точны для объектов с преобразованиями модели, которые изначально создаются с использованием одной и той же системы координат.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Создание голограмм с помощью привязанного к устройству фрейма ссылки

Иногда требуется отобразить голограмму, которая [остается прикрепленной](../../design/coordinate-systems.md#attached-frame-of-reference) к расположению устройства, например панель с отладочной информацией или информационное сообщение, если устройство может определить его ориентацию, а не его положение в пространстве. Для этого мы используем присоединенный фрейм ссылки.

Класс Спатиаллокатораттачедфрамеофреференце определяет системы координат, которые являются относительными для устройства, а не для реального мира. Этот кадр имеет фиксированный заголовок относительно окружающей среды пользователя, указывающий в направлении, в котором пользователь был направлен при создании эталонного фрейма. После этого все ориентации в этой рамке ссылки зависят от этого фиксированного заголовка, даже при вращении устройства пользователем.

Для HoloLens происхождение системы координат этого фрейма находится в центре вращения заголовка пользователя, чтобы его положение не влияло на поворот головного элемента. Приложение может указать смещение относительно этой точки, чтобы разместить голограммы перед пользователем.

Чтобы получить Спатиаллокатораттачедфрамеофреференце, используйте класс Спатиаллокатор и вызовите Креатеаттачедфрамеофреференцеаткурренсеадинг.

Это относится ко всему диапазону устройств Windows Mixed Reality.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Использование ссылочного фрейма, присоединенного к устройству

В этих разделах мы поговорим о том, что мы изменили в шаблоне приложения Windows holographic, чтобы включить связанный с устройством фрейм ссылки с помощью этого API. Эта «присоединенная» голограмма будет работать наряду с стационарными или прикрепленными голограммами, а также может использоваться, когда устройство временно не может найти свое местоположение в мире.

Сначала мы изменили шаблон, чтобы сохранить Спатиаллокатораттачедфрамеофреференце вместо Спатиалстатионарифрамеофреференце:

Из **холографиктагалонгсамплемаин. h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Из **холографиктагалонгсамплемаин. cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

В ходе обновления теперь мы получаем систему координат в отметке времени, полученной с помощью прогнозирования кадров.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Получение пространственного указателя a и отслеживание пользователя

Мы хотим, чтобы наш пример голограммы проследовала [взгляд](../../design/gaze-and-commit.md)пользователя, аналогично тому, как с помощью оболочки holographic можно следовать взгляду пользователя. Для этого нам нужно получить Спатиалпоинтерпосе из той же метки времени.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Этот Спатиалпоинтерпосе содержит сведения, необходимые для размещения голограммы в соответствии с [текущим заголовком пользователя](gaze-in-directx.md).

Для удобства пользователя мы используем линейную интерполяцию ("лерп"), чтобы сгладить изменение в положении в течение определенного периода времени. Это более удобно для пользователя, чем блокировка голограммы до их взгляда. Лерпингая с тегом голограмма также позволяет нам стабилизировать голограмму путем ослабления движения. Если это ослабление не было сделано, пользователь увидит неограниченную голограмму из-за того, что обычно считается незаметной передвижением заголовка пользователя.

Из **статионарикуадрендерер::P оситионхолограм**:

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
>В случае панели отладки можно изменить положение голограммы на сторону немного, чтобы она не переходила на ваше представление. Ниже приведен пример того, как это можно сделать.

Для **статионарикуадрендерер::P оситионхолограм**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>Поворот голограммы на камеру

Не хватает для размещения голограммы, которая в данном случае является четырехъядерной; также необходимо повернуть объект, чтобы он был лицом к пользователю. Этот поворот происходит в мировом пространстве, поскольку этот тип рекламы позволяет оставить голограмму частью среды пользователя. Переход на пробелы в представлении не так удобен, так как голограмма становится заблокированной для ориентации экрана; в этом случае необходимо также выполнить интерполяцию между левым и правым матрицами представлений, чтобы получить преобразование стенда представления, которое не нарушает стерео отрисовку. Здесь мы поворотим на оси X и Z пользователя.

Из **статионарикуадрендерер:: Update**:

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

### <a name="render-the-attached-hologram"></a>Подготовка присоединенной голограммы

В этом примере мы также решили визуализировать голограмму в системе координат Спатиаллокатораттачедреференцефраме, где мы разберем голограмму. (Если бы мы решили подготовиться к просмотру с помощью другой системы координат, нам пришлось бы получить преобразование из системы координат связанного с устройством ссылочного фрейма в эту систему координат.)

Из **холографиктагалонгсамплемаин:: Render**:

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

Вот и все! Голограмма теперь будет «проследить» расположение, равное 2 метрах, перед направлением взгляда пользователя.

>[!NOTE]
>В этом примере также загружается дополнительное содержимое — см. Статионарикуадрендерер. cpp.

## <a name="handling-tracking-loss"></a>Обработка потерь отслеживания

Если устройство не может располагаться в мире, в приложении происходит «отслеживание потерь». Приложения Windows Mixed Reality должны иметь возможность обрабатывать такие нарушения в системе нацеленного отслеживания. Эти нарушения можно наблюдать и создавать ответы с помощью события Локатабилитичанжед по умолчанию Спатиаллокатор.

Из **аппмаин:: сесолографикспаце:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Когда приложение получает событие Локатабилитичанжед, оно может изменить поведение по мере необходимости. Например, в состоянии Поситионалтраккингинхибитед приложение может приостановить нормальную работу и вывести на экран [голограмму с пометкой](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , которая отображает предупреждающее сообщение.

Шаблон приложения Windows holographic поставляется с уже созданным обработчиком Локатабилитичанжед. По умолчанию в консоли отладки отображается предупреждение, если позиционированное отслеживание недоступно. Вы можете добавить код в этот обработчик, чтобы предоставить ответ по мере необходимости из приложения.

Из **аппмаин. cpp:**

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

## <a name="spatial-mapping"></a>пространственное сопоставление

API-интерфейсы [пространственного сопоставления](spatial-mapping-in-directx.md) используют системы координат для получения преобразований модели для сеток поверхности.

## <a name="see-also"></a>См. также раздел
* [Системы координат](../../design/coordinate-systems.md)
* [Пространственные привязки](../../design/spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* [Направление головы и взгляда в DirectX](gaze-in-directx.md)
* [Контроллеры движения и жестов в DirectX](hands-and-motion-controllers-in-directx.md)
* [Пространственное сопоставление в DirectX](spatial-mapping-in-directx.md)
