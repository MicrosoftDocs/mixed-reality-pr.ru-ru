---
title: Пример использования. расширение возможностей пространственных сопоставлений HoloLens
description: При создании наших первых приложений для Microsoft HoloLens мы затронули, насколько проводилась бы возможность отправки на устройстве границ пространственного сопоставления.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, пространственное сопоставление
ms.openlocfilehash: b6546c5c14c5a16f5218721d007bc83798bacfad
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91693300"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="17fbe-104">Пример использования. расширение возможностей пространственных сопоставлений HoloLens</span><span class="sxs-lookup"><span data-stu-id="17fbe-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="17fbe-105">При создании наших первых приложений для Microsoft HoloLens мы затронули, насколько проводилась бы возможность отправки на устройстве границ пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="17fbe-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="17fbe-106">Джефф Евертт, инженер по программному обеспечению в Microsoft Studios, объясняет, как была разработана новая технология, которая не требует большего контроля над тем, как голограммы помещаются в реальную среду пользователя.</span><span class="sxs-lookup"><span data-stu-id="17fbe-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="17fbe-107">В HoloLens 2 реализована новая сцена, посвященная [среде выполнения](../design/scene-understanding.md), которая предоставляет разработчикам смешанной реальности доступ к структурированному, высокоуровневой представлению среды, предназначенному для упрощения разработки приложений, поддерживающих среду.</span><span class="sxs-lookup"><span data-stu-id="17fbe-107">HoloLens 2 implements a new [Scene Understanding Runtime](../design/scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="17fbe-108">Просмотреть видео</span><span class="sxs-lookup"><span data-stu-id="17fbe-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="17fbe-109">За пределами пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="17fbe-109">Beyond spatial mapping</span></span>

<span data-ttu-id="17fbe-110">Несмотря на то, что мы работаем над [фрагментами](https://www.microsoft.com/p/fragments/9nblggh5ggm8) и [конкерами](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), два из первых игр для HoloLens, мы обнаружили, что при выполнении процедурного размещения голограмм в физическом мире нам требовалось более высокий уровень понимания среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="17fbe-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="17fbe-111">Каждая игра имеет свои собственные требования к размещению: в фрагментах, например, мы хотели иметь возможность отличать различные поверхности, например этаж или таблицу, чтобы разместить подсказки в соответствующих расположениях.</span><span class="sxs-lookup"><span data-stu-id="17fbe-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="17fbe-112">Нам также хотелось бы иметь возможность определять поверхности, на которых может находился жизненный размер, например диван или кресло.</span><span class="sxs-lookup"><span data-stu-id="17fbe-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="17fbe-113">В Титов Конкер мы хотели, чтобы Конкер и его соперники могли использовать порожденные поверхности в комнате проигрывателя как платформы.</span><span class="sxs-lookup"><span data-stu-id="17fbe-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="17fbe-114">[Асобо Studios](https://www.asobostudio.com/index.html), наш партнер по разработке для этих игр, столкнулся с этой проблемой и создал технологию, расширяющую возможности пространственных сопоставлений HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17fbe-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="17fbe-115">С помощью этого можно анализировать комнату игрока и выявление таких поверхностей, как стены, таблицы, стулья и пол.</span><span class="sxs-lookup"><span data-stu-id="17fbe-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="17fbe-116">Это также дает нам возможность оптимизироваться по набору ограничений, чтобы определить наилучшее размещение для holographic объектов.</span><span class="sxs-lookup"><span data-stu-id="17fbe-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="17fbe-117">Код пространственного понимания</span><span class="sxs-lookup"><span data-stu-id="17fbe-117">The spatial understanding code</span></span>

<span data-ttu-id="17fbe-118">Мы заняли исходный код асобо и создали библиотеку, которая инкапсулирует эту технологию.</span><span class="sxs-lookup"><span data-stu-id="17fbe-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="17fbe-119">Microsoft и асобо теперь имеют открытый исходный код и делают его доступным в [микседреалититулкит](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) для использования в собственных проектах.</span><span class="sxs-lookup"><span data-stu-id="17fbe-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="17fbe-120">Включается весь исходный код, позволяющий настроить его в своих целях и поделиться изменениями с сообществом.</span><span class="sxs-lookup"><span data-stu-id="17fbe-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="17fbe-121">Код для поиска решения C++ был заключен в библиотеку DLL UWP и предоставлен в Unity с помощью prefab, [содержащегося в микседреалититулкит](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="17fbe-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="17fbe-122">В примере Unity есть много полезных запросов, которые позволяют находить пустые пробелы в стенах, размещать объекты в самом потолке или в больших пространствах на этаже, обнаруживать места для символов и множество других пространственных сведений о запросах.</span><span class="sxs-lookup"><span data-stu-id="17fbe-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="17fbe-123">Хотя решение для пространственного сопоставления, предоставляемое HoloLens, достаточно универсально для удовлетворения потребностей всего спектра проблемных пространств, модуль пространственного понимания был разработан для поддержки потребностей двух конкретных игр.</span><span class="sxs-lookup"><span data-stu-id="17fbe-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="17fbe-124">Таким образом, его решение структурировано вокруг определенного процесса и набора допущений:</span><span class="sxs-lookup"><span data-stu-id="17fbe-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="17fbe-125">**Фиксированный размер плайспаце** : пользователь задает максимальный размер плайспаце в вызове init.</span><span class="sxs-lookup"><span data-stu-id="17fbe-125">**Fixed size playspace** : The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="17fbe-126">**Процесс однократного сканирования** . процесс требует наличия дискретного этапа сканирования, по истечении которого пользователь определяет плайспаце.</span><span class="sxs-lookup"><span data-stu-id="17fbe-126">**One-time scan process** : The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="17fbe-127">Функции запросов не будут работать до завершения проверки.</span><span class="sxs-lookup"><span data-stu-id="17fbe-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="17fbe-128">**Управляемая пользователем плайспаце "Рисование"** : на этапе сканирования пользователь перемещается и просматривает плайспаце, эффективно рисуя области, которые должны быть добавлены.</span><span class="sxs-lookup"><span data-stu-id="17fbe-128">**User driven playspace “painting”** : During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="17fbe-129">Созданная сетка важна для предоставления отзывов пользователей на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="17fbe-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="17fbe-130">**Домашняя страница и программа установки Office** . функции запросов разрабатываются вокруг плоских поверхностей и стен в правой части.</span><span class="sxs-lookup"><span data-stu-id="17fbe-130">**Indoors home or office setup** : The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="17fbe-131">Это мягкое ограничение.</span><span class="sxs-lookup"><span data-stu-id="17fbe-131">This is a soft limitation.</span></span> <span data-ttu-id="17fbe-132">Однако на этапе сканирования выполняется анализ основной оси для оптимизации тесселяции сетки вдоль основной и вспомогательной осей.</span><span class="sxs-lookup"><span data-stu-id="17fbe-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="17fbe-133">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="17fbe-133">Room Scanning Process</span></span>

<span data-ttu-id="17fbe-134">Когда вы загружаете модуль пространственного понимания, первое, что вы будете делать, — это сканирование пространства, поэтому все доступные поверхности, такие как пол, потолк и стены, определяются и помечаются меткой.</span><span class="sxs-lookup"><span data-stu-id="17fbe-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="17fbe-135">В процессе сканирования вы просматриваете комнату и зарисуете области, которые должны быть добавлены в сканирование.</span><span class="sxs-lookup"><span data-stu-id="17fbe-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="17fbe-136">Сетка, видимая на этом этапе, является важной частью визуальной обратной связи, которая позволяет пользователям узнать, какие части комнаты сканируются.</span><span class="sxs-lookup"><span data-stu-id="17fbe-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="17fbe-137">Библиотека DLL для модуля пространственного понимания внутренне сохраняет плайспаце в виде сетки 8cm Воксел Cubes.</span><span class="sxs-lookup"><span data-stu-id="17fbe-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="17fbe-138">Во время первой части сканирования выполняется анализ основных компонентов, чтобы определить оси комнаты.</span><span class="sxs-lookup"><span data-stu-id="17fbe-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="17fbe-139">На внутреннем уровне он хранит свое Воксел пространство, выравниваемая по этим осям.</span><span class="sxs-lookup"><span data-stu-id="17fbe-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="17fbe-140">Сетка создается приблизительно каждую секунду путем извлечения isosurface из тома Воксел.</span><span class="sxs-lookup"><span data-stu-id="17fbe-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Сетка пространственных сопоставлений в белом и знакомство с плайспаце сеткой зеленым цветом](images/spatial-mapping-500px.png)

<span data-ttu-id="17fbe-142">Сетка пространственных сопоставлений в белом и знакомство с плайспаце сеткой зеленым цветом</span><span class="sxs-lookup"><span data-stu-id="17fbe-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="17fbe-143">Прилагаемый файл SpatialUnderstanding.cs управляет процессом этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="17fbe-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="17fbe-144">Он вызывает следующие функции:</span><span class="sxs-lookup"><span data-stu-id="17fbe-144">It calls the following functions:</span></span>
* <span data-ttu-id="17fbe-145">**SpatialUnderstanding_Init** : вызывается один раз в начале.</span><span class="sxs-lookup"><span data-stu-id="17fbe-145">**SpatialUnderstanding_Init** : Called once at the start.</span></span>
* <span data-ttu-id="17fbe-146">**GeneratePlayspace_InitScan** : указывает, что должна начаться фаза сканирования.</span><span class="sxs-lookup"><span data-stu-id="17fbe-146">**GeneratePlayspace_InitScan** : Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="17fbe-147">**GeneratePlayspace_UpdateScan_DynamicScan** : вызывается каждый кадр для обновления процесса сканирования.</span><span class="sxs-lookup"><span data-stu-id="17fbe-147">**GeneratePlayspace_UpdateScan_DynamicScan** : Called each frame to update the scanning process.</span></span> <span data-ttu-id="17fbe-148">Положение и ориентация камеры передаются в и используются для процесса рисования плайспаце, описанного выше.</span><span class="sxs-lookup"><span data-stu-id="17fbe-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="17fbe-149">**GeneratePlayspace_RequestFinish** : вызывается для завершения плайспаце.</span><span class="sxs-lookup"><span data-stu-id="17fbe-149">**GeneratePlayspace_RequestFinish** : Called to finalize the playspace.</span></span> <span data-ttu-id="17fbe-150">При этом для определения и блокировки плайспаце будут использоваться области "нарисованные" на этапе сканирования.</span><span class="sxs-lookup"><span data-stu-id="17fbe-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="17fbe-151">Приложение может запрашивать статистику на этапе сканирования, а также запрашивать пользовательскую сетку для предоставления отзывов пользователей.</span><span class="sxs-lookup"><span data-stu-id="17fbe-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="17fbe-152">**Import_UnderstandingMesh** . во время сканирования поведение **спатиалундерстандингкустоммеш** , предоставляемое модулем и размещенное в понимании prefab, будет периодически запрашивать пользовательскую сетку, созданную процессом.</span><span class="sxs-lookup"><span data-stu-id="17fbe-152">**Import_UnderstandingMesh** : During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="17fbe-153">Кроме того, это делается после завершения проверки.</span><span class="sxs-lookup"><span data-stu-id="17fbe-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="17fbe-154">Поток сканирования, управляемый поведением **спатиалундерстандинг** , вызывает **инитскан** , а затем **упдатескан** каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="17fbe-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan** , then **UpdateScan** each frame.</span></span> <span data-ttu-id="17fbe-155">Когда статистический запрос сообщает о разумном покрытии, пользователь может аиртап вызвать **рекуестфиниш** , чтобы обозначить окончание этапа сканирования.</span><span class="sxs-lookup"><span data-stu-id="17fbe-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="17fbe-156">**Упдатескан** будет вызываться до тех пор, пока не будет возвращено значение, указывающее, что библиотека DLL завершила обработку.</span><span class="sxs-lookup"><span data-stu-id="17fbe-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="17fbe-157">Запросы</span><span class="sxs-lookup"><span data-stu-id="17fbe-157">The queries</span></span>

<span data-ttu-id="17fbe-158">После завершения проверки вы сможете получить доступ к трем различным типам запросов в интерфейсе:</span><span class="sxs-lookup"><span data-stu-id="17fbe-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="17fbe-159">**Запросы топологии** . это быстрые запросы, основанные на топологии сканируемой комнаты.</span><span class="sxs-lookup"><span data-stu-id="17fbe-159">**Topology queries** : These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="17fbe-160">**Запросы Shape** . они используют результаты запросов топологии для поиска горизонтальных поверхностей, которые хорошо соответствуют определенным пользовательским фигурам.</span><span class="sxs-lookup"><span data-stu-id="17fbe-160">**Shape queries** : These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="17fbe-161">**Запросы размещения объектов** . это более сложные запросы, которые находят оптимальное расположение на основе набора правил и ограничений для объекта.</span><span class="sxs-lookup"><span data-stu-id="17fbe-161">**Object placement queries** : These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="17fbe-162">В дополнение к трем основным запросам имеется интерфейс райкастинг, который можно использовать для извлечения типов областей с тегами, а также для копирования настраиваемой сетки комнаты ватертигхт.</span><span class="sxs-lookup"><span data-stu-id="17fbe-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="17fbe-163">Запросы топологии</span><span class="sxs-lookup"><span data-stu-id="17fbe-163">Topology queries</span></span>

<span data-ttu-id="17fbe-164">В библиотеке DLL диспетчер топологии обрабатывает метки среды.</span><span class="sxs-lookup"><span data-stu-id="17fbe-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="17fbe-165">Как упоминалось выше, большая часть данных хранится в сурфелс, которые содержатся в томе Воксел.</span><span class="sxs-lookup"><span data-stu-id="17fbe-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="17fbe-166">Кроме того, структура **плайспацеинфос** используется для хранения сведений о плайспаце, включая выравнивание по всему миру (Подробнее об этом ниже), этаж и высоту потолка.</span><span class="sxs-lookup"><span data-stu-id="17fbe-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="17fbe-167">Эвристические методы используются для определения этажей, потолков и стен.</span><span class="sxs-lookup"><span data-stu-id="17fbe-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="17fbe-168">Например, крупнейшим является самая крупная и меньшая горизонтальная поверхность с более чем одной контактной областью m2.</span><span class="sxs-lookup"><span data-stu-id="17fbe-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="17fbe-169">Обратите внимание, что в процессе сканирования также используется путь к камере.</span><span class="sxs-lookup"><span data-stu-id="17fbe-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="17fbe-170">Подмножество запросов, предоставляемых диспетчером топологии, предоставляется через библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="17fbe-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="17fbe-171">Доступны следующие запросы топологии.</span><span class="sxs-lookup"><span data-stu-id="17fbe-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="17fbe-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="17fbe-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="17fbe-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="17fbe-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="17fbe-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="17fbe-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="17fbe-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="17fbe-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="17fbe-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="17fbe-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="17fbe-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="17fbe-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="17fbe-178">Каждый запрос имеет набор параметров, относящихся к типу запроса.</span><span class="sxs-lookup"><span data-stu-id="17fbe-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="17fbe-179">В следующем примере пользователь указывает минимальную высоту, & ширину требуемого тома, минимальную высоту размещения выше пола и минимальный размер зазора перед томом.</span><span class="sxs-lookup"><span data-stu-id="17fbe-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="17fbe-180">Все измерения задаются в метрах.</span><span class="sxs-lookup"><span data-stu-id="17fbe-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="17fbe-181">Каждый из этих запросов принимает предварительно выделенный массив структур **топологиресулт** .</span><span class="sxs-lookup"><span data-stu-id="17fbe-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="17fbe-182">Параметр **локатионкаунт** задает длину переданного массива.</span><span class="sxs-lookup"><span data-stu-id="17fbe-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="17fbe-183">Возвращаемое значение сообщает о количестве возвращенных расположений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="17fbe-184">Это число никогда не превышает переданный параметр **локатионкаунт** .</span><span class="sxs-lookup"><span data-stu-id="17fbe-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="17fbe-185">**Топологиресулт** содержит центральную точку возвращенного тома, направление (то есть нормальное) и размеры найденного пространства.</span><span class="sxs-lookup"><span data-stu-id="17fbe-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="17fbe-186">Обратите внимание, что в примере Unity каждый из этих запросов связан с кнопкой на панели виртуального интерфейса.</span><span class="sxs-lookup"><span data-stu-id="17fbe-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="17fbe-187">Пример жестко кодирует параметры для каждого из этих запросов в разумные значения.</span><span class="sxs-lookup"><span data-stu-id="17fbe-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="17fbe-188">Дополнительные примеры см. в разделе *SpaceVisualizer.CS* в примере кода.</span><span class="sxs-lookup"><span data-stu-id="17fbe-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="17fbe-189">Запросы фигур</span><span class="sxs-lookup"><span data-stu-id="17fbe-189">Shape queries</span></span>

<span data-ttu-id="17fbe-190">В библиотеке DLL анализатор форм ( **ShapeAnalyzer_W** ) использует анализатор топологии для сопоставления с пользовательскими фигурами, определенными пользователем.</span><span class="sxs-lookup"><span data-stu-id="17fbe-190">Inside of the DLL, the shape analyzer ( **ShapeAnalyzer_W** ) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="17fbe-191">Образец Unity имеет предварительно определенный набор фигур, которые отображаются в меню "запрос" на вкладке "Фигура".</span><span class="sxs-lookup"><span data-stu-id="17fbe-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="17fbe-192">Обратите внимание, что анализ фигур работает только на горизонтальных поверхностях.</span><span class="sxs-lookup"><span data-stu-id="17fbe-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="17fbe-193">Например, диван определяется поверхностью плоского места и плоской вершиной на диване.</span><span class="sxs-lookup"><span data-stu-id="17fbe-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="17fbe-194">Запрос Shape выполняет поиск двух поверхностей определенного размера, высоты и пропорций, при этом две поверхности Выровняйте и соединены.</span><span class="sxs-lookup"><span data-stu-id="17fbe-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="17fbe-195">Используя терминологию API, место дивана и вершина задней части дивана являются компонентами фигур, а требования к выравниванию — ограничения компонента.</span><span class="sxs-lookup"><span data-stu-id="17fbe-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="17fbe-196">Пример запроса, определенный в примере Unity ( **ShapeDefinition.CS** ) для объектов "ситтабле", выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="17fbe-196">An example query defined in the Unity sample ( **ShapeDefinition.cs** ), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="17fbe-197">Каждый запрос Shape определяется набором компонентов Shape, каждый из которых имеет набор ограничений компонента и набор ограничений фигур, в котором перечисляются зависимости между компонентами.</span><span class="sxs-lookup"><span data-stu-id="17fbe-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="17fbe-198">Этот пример включает три ограничения в определении одного компонента и не имеет ограничений фигур между компонентами (так как существует только один компонент).</span><span class="sxs-lookup"><span data-stu-id="17fbe-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="17fbe-199">Напротив, фигура дивана имеет два компонента фигур и четыре ограничения фигуры.</span><span class="sxs-lookup"><span data-stu-id="17fbe-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="17fbe-200">Обратите внимание, что компоненты определяются по индексу в списке компонентов пользователя (в этом примере 0 и 1).</span><span class="sxs-lookup"><span data-stu-id="17fbe-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="17fbe-201">Функции-оболочки предоставляются в модуле Unity для простого создания пользовательских определений фигур.</span><span class="sxs-lookup"><span data-stu-id="17fbe-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="17fbe-202">Полный список ограничений для компонентов и фигур можно найти в **SpatialUnderstandingDll.CS** в структурах **шапекомпонентконстраинт** и **шапеконстраинт** .</span><span class="sxs-lookup"><span data-stu-id="17fbe-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Синий прямоугольник выделяет результаты запроса формы кресло.](images/chair-shape-query-500px.png)

<span data-ttu-id="17fbe-204">Синий прямоугольник выделяет результаты запроса формы кресло.</span><span class="sxs-lookup"><span data-stu-id="17fbe-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="17fbe-205">Поиск решения о размещении объектов</span><span class="sxs-lookup"><span data-stu-id="17fbe-205">Object placement solver</span></span>

<span data-ttu-id="17fbe-206">Запросы на размещение объектов можно использовать для обнаружения идеального расположения в физической комнате для размещения объектов.</span><span class="sxs-lookup"><span data-stu-id="17fbe-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="17fbe-207">Поиск решения позволяет найти оптимальное расположение с учетом правил и ограничений объекта.</span><span class="sxs-lookup"><span data-stu-id="17fbe-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="17fbe-208">Кроме того, запросы объектов сохраняются до тех пор, пока объект не будет удален с помощью **Solver_RemoveObject** или **Solver_RemoveAllObjects** вызовов, что позволяет ограничить размещение нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="17fbe-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="17fbe-209">Запросы размещения объектов состоят из трех частей: тип размещения с параметрами, список правил и список ограничений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="17fbe-210">Чтобы выполнить запрос, используйте следующий API:</span><span class="sxs-lookup"><span data-stu-id="17fbe-210">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="17fbe-211">Эта функция принимает имя объекта, определение размещения и список правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="17fbe-212">Оболочки C# предоставляют вспомогательные функции конструирования для упрощения создания правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="17fbe-213">Определение размещения содержит тип запроса, то есть один из следующих:</span><span class="sxs-lookup"><span data-stu-id="17fbe-213">The placement definition contains the query type — that is, one of the following:</span></span>




```
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

<span data-ttu-id="17fbe-214">Каждый из типов размещения имеет набор параметров, уникальных для данного типа.</span><span class="sxs-lookup"><span data-stu-id="17fbe-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="17fbe-215">Структура **обжектплацементдефинитион** содержит набор статических вспомогательных функций для создания этих определений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="17fbe-216">Например, чтобы найти место для размещения объекта в этаже, можно использовать следующую функцию:</span><span class="sxs-lookup"><span data-stu-id="17fbe-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="17fbe-217">В дополнение к типу размещения можно предоставить набор правил и ограничений.</span><span class="sxs-lookup"><span data-stu-id="17fbe-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="17fbe-218">Правила не могут быть нарушены.</span><span class="sxs-lookup"><span data-stu-id="17fbe-218">Rules cannot be violated.</span></span> <span data-ttu-id="17fbe-219">Возможные расположения размещения, которые соответствуют типу и правилам, оптимизируются по набору ограничений, чтобы выбрать оптимальное расположение размещения.</span><span class="sxs-lookup"><span data-stu-id="17fbe-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="17fbe-220">Каждое из правил и ограничений можно создать с помощью предоставленных статических функций создания.</span><span class="sxs-lookup"><span data-stu-id="17fbe-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="17fbe-221">Ниже приведен пример функции конструирования правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="17fbe-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="17fbe-222">Приведенный ниже запрос размещения объекта ищет место для размещения полугодового Куба на границе поверхности, от других ранее размещенных объектов и вблизи центра комнаты.</span><span class="sxs-lookup"><span data-stu-id="17fbe-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
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

<span data-ttu-id="17fbe-223">В случае успешного выполнения возвращается структура **обжектплацементресулт** , содержащая положение размещения, размеры и ориентацию.</span><span class="sxs-lookup"><span data-stu-id="17fbe-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="17fbe-224">Кроме того, размещение добавляется в внутренний список размещенных объектов библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="17fbe-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="17fbe-225">При последующих запросах на размещение этот объект учитывается.</span><span class="sxs-lookup"><span data-stu-id="17fbe-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="17fbe-226">Файл **LevelSolver.CS** в образце Unity содержит дополнительные примеры запросов.</span><span class="sxs-lookup"><span data-stu-id="17fbe-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Синие поля показывают результат из трех мест в запросах этаже с правилами "от позиции камеры".](images/away-from-camera-position-500px.png)

<span data-ttu-id="17fbe-228">Синие поля показывают результат из трех мест в запросах этаже с правилами "от позиции камеры".</span><span class="sxs-lookup"><span data-stu-id="17fbe-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="17fbe-229">**Советы**</span><span class="sxs-lookup"><span data-stu-id="17fbe-229">**Tips:**</span></span>
* <span data-ttu-id="17fbe-230">При решении для размещения нескольких объектов, необходимых для сценария уровня или приложения, сначала решите ненужные и крупные объекты, чтобы максимально увеличить вероятность того, что место может быть найдено.</span><span class="sxs-lookup"><span data-stu-id="17fbe-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="17fbe-231">Порядок размещения важен.</span><span class="sxs-lookup"><span data-stu-id="17fbe-231">Placement order is important.</span></span> <span data-ttu-id="17fbe-232">Если размещение объектов не найдено, попробуйте уменьшить количество ограниченных конфигураций.</span><span class="sxs-lookup"><span data-stu-id="17fbe-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="17fbe-233">Наличие набора резервных конфигураций крайне важно для поддержки функциональных возможностей во многих конфигурациях комнаты.</span><span class="sxs-lookup"><span data-stu-id="17fbe-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="17fbe-234">Приведение лучей</span><span class="sxs-lookup"><span data-stu-id="17fbe-234">Ray casting</span></span>

<span data-ttu-id="17fbe-235">В дополнение к трем основным запросам можно использовать интерфейс приведения лучей, чтобы извлечь типы областей с тегами, а пользовательскую сетку ватертигхт плайспаце можно скопировать после того, как комната будет проверена и завершена, метки будут внутренне созданы для таких поверхностей, как этаж, потолк и стенки.</span><span class="sxs-lookup"><span data-stu-id="17fbe-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="17fbe-236">Функция **плайспацерайкаст** принимает луч и возвращает, если луч конфликтует с известной поверхностью и, если да, сведения об этой поверхности в форме **райкастресулт** .</span><span class="sxs-lookup"><span data-stu-id="17fbe-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult** .</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="17fbe-237">На внутреннем уровне райкаст вычисляются на основе вычисленного 8cm Куба Воксел представления плайспаце.</span><span class="sxs-lookup"><span data-stu-id="17fbe-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="17fbe-238">Каждый Воксел содержит набор элементов Surface с обработанными данными топологии (также известный как сурфелс).</span><span class="sxs-lookup"><span data-stu-id="17fbe-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="17fbe-239">Сурфелс, содержащиеся в пересеченной ячейке Воксел, сравниваются с наиболее подходящим соответствием, используемым для поиска сведений о топологии.</span><span class="sxs-lookup"><span data-stu-id="17fbe-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="17fbe-240">Данные топологии содержат метки, возвращаемые в форме перечисления **сурфацетипес** , а также контактную зону пересекающейся поверхности.</span><span class="sxs-lookup"><span data-stu-id="17fbe-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="17fbe-241">В примере Unity курсор приводится к каждому кадру.</span><span class="sxs-lookup"><span data-stu-id="17fbe-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="17fbe-242">Во – первых, от своих противоречией Unity; Во вторых, для представления о мировом представлении модуля; и, наконец, для элементов пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="17fbe-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="17fbe-243">В этом приложении пользовательский интерфейс получает приоритет, а затем понимает результат и, наконец, с помощью противоречащих Unity.</span><span class="sxs-lookup"><span data-stu-id="17fbe-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="17fbe-244">**Сурфацетипе** сообщается в виде текста рядом с курсором.</span><span class="sxs-lookup"><span data-stu-id="17fbe-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Пересечение отчетов результатов райкаст с этажом.](images/raycast-result-500px.jpg)

<span data-ttu-id="17fbe-246">Пересечение отчетов результатов райкаст с этажом.</span><span class="sxs-lookup"><span data-stu-id="17fbe-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="17fbe-247">Получите код</span><span class="sxs-lookup"><span data-stu-id="17fbe-247">Get the code</span></span>

<span data-ttu-id="17fbe-248">Код с открытым кодом доступен в [микседреалититулкит](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="17fbe-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="17fbe-249">Если вы используете код в проекте, сообщите нам об этом на [форумах разработчиков HoloLens](https://forums.hololens.com/) .</span><span class="sxs-lookup"><span data-stu-id="17fbe-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="17fbe-250">Мы не можем увидеть, что вы сделаете!</span><span class="sxs-lookup"><span data-stu-id="17fbe-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="17fbe-251">Об авторе</span><span class="sxs-lookup"><span data-stu-id="17fbe-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="17fbe-252"><b>Джефф евертт</b> — это ведущий специалист по разработке программного обеспечения, который работал над HoloLens, начиная с первых дней, от руковожу группой создания до опыта разработки.</span><span class="sxs-lookup"><span data-stu-id="17fbe-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="17fbe-253">До HoloLens он работал на Kinect Xbox и в отрасли игр на самых разных платформах и играх.</span><span class="sxs-lookup"><span data-stu-id="17fbe-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="17fbe-254">Джефф имеет дело с автоматизированными, графическими объектами и объектами, с которыми поступают звуковые индикаторы.</span><span class="sxs-lookup"><span data-stu-id="17fbe-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="17fbe-255">Он изучает новые вещи и работу с программным обеспечением, оборудованием и особенно в пространстве, где два пересекаются.</span><span class="sxs-lookup"><span data-stu-id="17fbe-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="17fbe-256">См. также статью</span><span class="sxs-lookup"><span data-stu-id="17fbe-256">See also</span></span>
* [<span data-ttu-id="17fbe-257">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="17fbe-257">Spatial mapping</span></span>](../design/spatial-mapping.md)
* [<span data-ttu-id="17fbe-258">Интерпретация сцены</span><span class="sxs-lookup"><span data-stu-id="17fbe-258">Scene understanding</span></span>](../design/scene-understanding.md)
* [<span data-ttu-id="17fbe-259">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="17fbe-259">Room scan visualization</span></span>](../design/room-scan-visualization.md)
* [<span data-ttu-id="17fbe-260">Микседреалититулкит-Unity</span><span class="sxs-lookup"><span data-stu-id="17fbe-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="17fbe-261">Асобо Studio: уроки оказался разработки HoloLens</span><span class="sxs-lookup"><span data-stu-id="17fbe-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
