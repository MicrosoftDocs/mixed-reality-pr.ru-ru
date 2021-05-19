---
title: Поставщик системных расширений
description: Расширения МРТК и поставщики данных
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, расширения системы,
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143502"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="6cd6a-104">Системы, службы расширений и поставщики данных</span><span class="sxs-lookup"><span data-stu-id="6cd6a-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="6cd6a-105">В наборе средств Mixed Reality многие функции предоставляются в виде служб.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="6cd6a-106">Службы группируются по трем основным категориям: системам, службам расширений и поставщикам данных.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="6cd6a-107">системы</span><span class="sxs-lookup"><span data-stu-id="6cd6a-107">Systems</span></span>

<span data-ttu-id="6cd6a-108">Системы — это службы, которые предоставляют основные функциональные возможности набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6cd6a-109">Все системы являются реализациями [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="6cd6a-110">баундарисистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="6cd6a-111">камерасистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="6cd6a-112">диагностикссистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="6cd6a-113">инпутсистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="6cd6a-114">сценесистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="6cd6a-115">спатиалаваренесссистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="6cd6a-116">телепортсистем</span><span class="sxs-lookup"><span data-stu-id="6cd6a-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="6cd6a-117">Каждая из перечисленных систем отображается в [профиле](../features/profiles/profiles.md)конфигурации компонента микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="6cd6a-118">Модули</span><span class="sxs-lookup"><span data-stu-id="6cd6a-118">Extensions</span></span>

<span data-ttu-id="6cd6a-119">Службы расширения — это компоненты, расширяющие функциональные возможности набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6cd6a-120">Все службы расширений должны указывать, что они реализуют [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="6cd6a-121">Сведения о создании служб расширения см. в статье [службы расширений](../features/extensions/extension-services.md) .</span><span class="sxs-lookup"><span data-stu-id="6cd6a-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="6cd6a-122">Для доступа к МРТК службы расширения регистрируются и настраиваются с помощью раздела Extensions в профиле конфигурации компонента Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Настройка службы расширений](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="6cd6a-124">Поставщики данных</span><span class="sxs-lookup"><span data-stu-id="6cd6a-124">Data providers</span></span>

<span data-ttu-id="6cd6a-125">Поставщики данных — это компоненты, которые по имени предоставляют данные для службы набора средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="6cd6a-126">Все поставщики данных должны указывать, что они реализуют [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="6cd6a-127">Не все службы потребует поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-127">Not all services will require data providers.</span></span> <span data-ttu-id="6cd6a-128">Систем, появляющихся системами набора средств смешанной реальности, являются единственной службой для использования поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="6cd6a-129">Для доступа к конкретной службе МРТК поставщики данных регистрируются в профиле конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="6cd6a-130">Код приложения обращается к поставщикам данных через [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="6cd6a-131">Для упрощения доступа поставщики данных также можно получить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="6cd6a-132">Несмотря на то `IMixedRealityDataProvider` , что наследует от `IMixedRealityService` , поставщики данных не регистрируются в `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="6cd6a-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="6cd6a-133">Для доступа к поставщикам данных код приложения должен запросить экземпляр службы, для которого они были зарегистрированы (например, система ввода).</span><span class="sxs-lookup"><span data-stu-id="6cd6a-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="6cd6a-134">Входные данные</span><span class="sxs-lookup"><span data-stu-id="6cd6a-134">Input</span></span>

<span data-ttu-id="6cd6a-135">Система ввода МРТК использует только поставщики данных, реализующие [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="6cd6a-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Поставщики входных системных данных](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="6cd6a-137">В следующем примере демонстрируется доступ к поставщику имитации ввода и переключается свойство Смусэйетраккинг.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="6cd6a-138">Доступ к поставщику данных для основной входной системы также можно упростить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="6cd6a-139">Входная система возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="6cd6a-140">Сведения о создании поставщика данных для входной системы МРТК см. в разделе [Создание входного системного поставщика данных](../features/input/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6cd6a-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="6cd6a-141">Поддержка пространственных сведений</span><span class="sxs-lookup"><span data-stu-id="6cd6a-141">Spatial awareness</span></span>

<span data-ttu-id="6cd6a-142">Система пространственной осведомленности МРТК использует только поставщики данных, реализующие [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Поставщики системных данных для пространственного отслеживания](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="6cd6a-144">В следующем примере демонстрируется доступ к зарегистрированным поставщикам данных пространственной сетки и изменение видимости сеток.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="6cd6a-145">Доступ к поставщику данных для основной системы пространственной информации также можно упростить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="6cd6a-146">Система пространственной информации возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="6cd6a-147">Сведения о написании поставщика данных для системы поддержки пространственной информации МРТК см. в разделе [Создание системного поставщика данных с](../features/spatial-awareness/create-data-provider.md)поддержкой пространственного доступа.</span><span class="sxs-lookup"><span data-stu-id="6cd6a-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd6a-148">См. также</span><span class="sxs-lookup"><span data-stu-id="6cd6a-148">See also</span></span>

- [<span data-ttu-id="6cd6a-149">Службы расширений</span><span class="sxs-lookup"><span data-stu-id="6cd6a-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="6cd6a-150">Создание поставщика входных системных данных</span><span class="sxs-lookup"><span data-stu-id="6cd6a-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="6cd6a-151">Создание поставщика системных системных данных для пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="6cd6a-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="6cd6a-152">Интерфейс Имикседреалитисервице</span><span class="sxs-lookup"><span data-stu-id="6cd6a-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="6cd6a-153">Интерфейс Имикседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="6cd6a-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="6cd6a-154">Интерфейс Имикседреалитекстенсионсервице</span><span class="sxs-lookup"><span data-stu-id="6cd6a-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
