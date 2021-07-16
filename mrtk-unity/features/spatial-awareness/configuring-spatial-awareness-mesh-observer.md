---
title: Настройка наблюдателей сетки для устройства
description: Настройка наблюдателя для встроенной пространственной сетки в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281932"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="93135-104">Настройка наблюдателей сетки для устройства</span><span class="sxs-lookup"><span data-stu-id="93135-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="93135-105">в этом руководстве рассматривается настройка встроенного наблюдателя пространственной сетки в мртк, поддерживающего Windows Mixed Realityную платформу (например,</span><span class="sxs-lookup"><span data-stu-id="93135-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="93135-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="93135-106">HoloLens).</span></span> <span data-ttu-id="93135-107">реализацией по умолчанию, предоставляемой в набор средств смешанной реальности, является класс [виндовсмикседреалитиспатиалмешобсервер](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="93135-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="93135-108">Многие свойства в этой статье применимы для других [пользовательских реализаций наблюдателя](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="93135-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="93135-109">Параметры профиля</span><span class="sxs-lookup"><span data-stu-id="93135-109">Profile settings</span></span>

<span data-ttu-id="93135-110">Следующие два элемента должны быть определены первыми при настройке профиля наблюдателя пространственной сетки для [системы распознавания пространственных](spatial-awareness-getting-started.md)данных.</span><span class="sxs-lookup"><span data-stu-id="93135-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="93135-111">Реализация конкретного типа наблюдателя</span><span class="sxs-lookup"><span data-stu-id="93135-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="93135-112">Список поддерживаемых платформ для запуска этого наблюдателя</span><span class="sxs-lookup"><span data-stu-id="93135-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="93135-113">Все наблюдатели должны расширять интерфейс [имикседреалитиспатиалаваренессобсервер](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .</span><span class="sxs-lookup"><span data-stu-id="93135-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![общие типы Параметры платформы наблюдателя сети](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="93135-115">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="93135-115">General settings</span></span>

![общие параметры Параметры женрал для наблюдателя сетки](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="93135-117">**Поведение при запуске**</span><span class="sxs-lookup"><span data-stu-id="93135-117">**Startup Behavior**</span></span>

<span data-ttu-id="93135-118">Поведение при запуске указывает, будет ли наблюдатель запускаться при первом создании экземпляра.</span><span class="sxs-lookup"><span data-stu-id="93135-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="93135-119">Эти два варианта указаны ниже:</span><span class="sxs-lookup"><span data-stu-id="93135-119">The two options are:</span></span>

* <span data-ttu-id="93135-120">*Автоматический запуск* — значение по умолчанию, при котором наблюдатель начнет операцию после инициализации.</span><span class="sxs-lookup"><span data-stu-id="93135-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="93135-121">*Запуск вручную* — наблюдатель будет ждать запуска.</span><span class="sxs-lookup"><span data-stu-id="93135-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="93135-122">При *запуске вручную* необходимо [возобновить работу и приостановить их во время выполнения с помощью кода](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="93135-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="93135-123">**Интервал обновления**</span><span class="sxs-lookup"><span data-stu-id="93135-123">**Update Interval**</span></span>

<span data-ttu-id="93135-124">Время в секундах между запросами к платформе для обновления данных пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="93135-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="93135-125">Типичные значения лежат в диапазоне 0,1 и 5,0 секунд.</span><span class="sxs-lookup"><span data-stu-id="93135-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="93135-126">**Является стационарным наблюдателем**</span><span class="sxs-lookup"><span data-stu-id="93135-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="93135-127">Указывает, должен ли наблюдатель оставаться стационарным или перемещаться и обновляться с пользователем.</span><span class="sxs-lookup"><span data-stu-id="93135-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="93135-128">Если значение — true, *фигура наблюдателя* с томом, определенным *экстентом наблюдения* , останется в источнике при запуске.</span><span class="sxs-lookup"><span data-stu-id="93135-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="93135-129">Если значение равно false, пространство наблюдателя будет соответствовать заголовку пользователя в качестве источника фигуры.</span><span class="sxs-lookup"><span data-stu-id="93135-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="93135-130">Данные сетки не рассчитываются для физической области за пределами пространства наблюдателя, как определено в этих свойствах: *это стационарный наблюдатель*, \* форма наблюдателя \* \* и *экстенты наблюдения*.</span><span class="sxs-lookup"><span data-stu-id="93135-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="93135-131">**Фигура наблюдателя**</span><span class="sxs-lookup"><span data-stu-id="93135-131">**Observer Shape**</span></span>

<span data-ttu-id="93135-132">Фигура наблюдателя определяет тип тома, который будет использоваться наблюдателем сетки при наблюдении за сетями.</span><span class="sxs-lookup"><span data-stu-id="93135-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="93135-133">Поддерживаются следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="93135-133">The supported options are:</span></span>

* <span data-ttu-id="93135-134">Развернутая *по осям* прямоугольная фигура, которая остается согласованной с осями мировой системы координат, как определено при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="93135-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="93135-135">*Пользовательно* -прямоугольная фигура Куба, которая поворачивается в соответствие с локальной системой координат пользователя.</span><span class="sxs-lookup"><span data-stu-id="93135-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="93135-136">*Сфера* — это сферический том, который находится в центре в источнике мирового пространства.</span><span class="sxs-lookup"><span data-stu-id="93135-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="93135-137">Значение X для свойства *экстентов* будет использоваться в качестве радиуса сферы.</span><span class="sxs-lookup"><span data-stu-id="93135-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="93135-138">**Экстенты наблюдения**</span><span class="sxs-lookup"><span data-stu-id="93135-138">**Observation Extents**</span></span>

<span data-ttu-id="93135-139">Экстенты наблюдения определяют расстояние от точки наблюдения, в которой будут наблюдаться сети.</span><span class="sxs-lookup"><span data-stu-id="93135-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="93135-140">Параметры физикы</span><span class="sxs-lookup"><span data-stu-id="93135-140">Physics settings</span></span>

![физика Параметры наблюдателя сетки](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="93135-142">**Физический слой**</span><span class="sxs-lookup"><span data-stu-id="93135-142">**Physics Layer**</span></span>

<span data-ttu-id="93135-143">Уровень физических объектов, на котором будут размещаться объекты пространственной сетки, чтобы взаимодействовать с системами Unity физика и Райкаст.</span><span class="sxs-lookup"><span data-stu-id="93135-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="93135-144">смешанная реальность набор средств резервирует *уровень 31* по умолчанию для использования наблюдателями с поддержкой пространственного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="93135-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="93135-145">**Пересчитать нормали**</span><span class="sxs-lookup"><span data-stu-id="93135-145">**Recalculate Normals**</span></span>

<span data-ttu-id="93135-146">Указывает, будет ли наблюдатель сетки пересчитывать нормальы сети после наблюдения.</span><span class="sxs-lookup"><span data-stu-id="93135-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="93135-147">Этот параметр доступен, чтобы обеспечить получение приложениями сеток, содержащих допустимые данные нормалей, на платформах, которые не возвращают их в сети.</span><span class="sxs-lookup"><span data-stu-id="93135-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="93135-148">Уровень подробных параметров</span><span class="sxs-lookup"><span data-stu-id="93135-148">Level of detail settings</span></span>

![детализация уровня наблюдателя сети Параметры](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="93135-150">**Уровень детализации**</span><span class="sxs-lookup"><span data-stu-id="93135-150">**Level of Detail**</span></span>

<span data-ttu-id="93135-151">Задает уровень детализации данных пространственной сетки (Лод).</span><span class="sxs-lookup"><span data-stu-id="93135-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="93135-152">В настоящее время определены значения грубого, точного и пользовательского.</span><span class="sxs-lookup"><span data-stu-id="93135-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="93135-153">*Грубое* появление меньшего влияния на производительность приложения и является отличным выбором для навигации или плоскости поиска.</span><span class="sxs-lookup"><span data-stu-id="93135-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="93135-154">Параметр *средней* балансировки часто полезен для тех, кто постоянно сканирует среду как для крупных функций, этажей, так и для стен, так и для перекрытияных данных.</span><span class="sxs-lookup"><span data-stu-id="93135-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="93135-155">*Точнее* говоря, точное влияние на производительность приложения является отличным вариантом для сеток перекрытия.</span><span class="sxs-lookup"><span data-stu-id="93135-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="93135-156">*Настраиваемый* — требует, чтобы приложение затребовало свойство " *треугольники/кубический метр* " и позволяло приложениям настраивать точность и производительность наблюдателя пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="93135-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="93135-157">Не гарантируется, что все *треугольные и кубические значения счетчиков* будут учитываться всеми платформами.</span><span class="sxs-lookup"><span data-stu-id="93135-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="93135-158">При использовании пользовательского Лод настоятельно рекомендуется использовать эксперименты и профилирование.</span><span class="sxs-lookup"><span data-stu-id="93135-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="93135-159">**Число треугольников на кубический метр**</span><span class="sxs-lookup"><span data-stu-id="93135-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="93135-160">Действует при использовании *пользовательского* параметра **уровня детализации** и указывает плотность треугольника для пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="93135-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="93135-161">Параметры отображения</span><span class="sxs-lookup"><span data-stu-id="93135-161">Display settings</span></span>

![отображение Параметры наблюдателя сетки](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="93135-163">**Параметр "Показать"**</span><span class="sxs-lookup"><span data-stu-id="93135-163">**Display Option**</span></span>

<span data-ttu-id="93135-164">Указывает способ отображения пространственных сеток наблюдателем.</span><span class="sxs-lookup"><span data-stu-id="93135-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="93135-165">Поддерживаются значения:</span><span class="sxs-lookup"><span data-stu-id="93135-165">Supported values are:</span></span>

* <span data-ttu-id="93135-166">*None* — наблюдатель не будет визуализировать сетку</span><span class="sxs-lookup"><span data-stu-id="93135-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="93135-167">*Видимый* — данные сетки будут видны с помощью *видимого материала* .</span><span class="sxs-lookup"><span data-stu-id="93135-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="93135-168">*Перекрытия* — данные сетки будут окклуде элементами в сцене с помощью *материала перекрытия*</span><span class="sxs-lookup"><span data-stu-id="93135-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Выберите реализацию системы пространственного отслеживания](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="93135-170">Пространственные наблюдатели можно [возобновить или приостановить в среде выполнения с помощью кода.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="93135-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="93135-171">Установка *параметра вывода* в значение " *нет* " **не останавливает выполнение** наблюдателя.</span><span class="sxs-lookup"><span data-stu-id="93135-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="93135-172">Если вы хотите остановить всех наблюдателей, приложениям потребуется приостановить всех наблюдателей через [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="93135-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="93135-173">**Видимый материал**</span><span class="sxs-lookup"><span data-stu-id="93135-173">**Visible Material**</span></span>

<span data-ttu-id="93135-174">Указывает материал, используемый при визуализации пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="93135-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="93135-175">**Материал перекрытия**</span><span class="sxs-lookup"><span data-stu-id="93135-175">**Occlusion Material**</span></span>

<span data-ttu-id="93135-176">Указывает материал, который будет использоваться для окклуде голограмм.</span><span class="sxs-lookup"><span data-stu-id="93135-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="93135-177">См. также</span><span class="sxs-lookup"><span data-stu-id="93135-177">See also</span></span>

* [<span data-ttu-id="93135-178">Система пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="93135-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="93135-179">Настройка системы пространственной осведомленности с помощью кода</span><span class="sxs-lookup"><span data-stu-id="93135-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="93135-180">Документация по API Имикседреалитиспатиалаваренессобсервер</span><span class="sxs-lookup"><span data-stu-id="93135-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="93135-181">Документация по API Имикседреалитиспатиалаваренессмешобсервер</span><span class="sxs-lookup"><span data-stu-id="93135-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="93135-182">Документация по API Басеспатиалобсервер</span><span class="sxs-lookup"><span data-stu-id="93135-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
