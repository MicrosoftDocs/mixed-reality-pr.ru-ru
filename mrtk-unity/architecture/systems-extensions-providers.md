---
title: Поставщик системных расширений
description: Расширения МРТК и поставщики данных
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, расширения системы,
ms.openlocfilehash: 358294702971b7d9e8de1b842d3bc1844e5dc9bf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121472"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="4e3f9-104">Системы, службы расширений и поставщики данных</span><span class="sxs-lookup"><span data-stu-id="4e3f9-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="4e3f9-105">В наборе средств Mixed Reality многие функции предоставляются в виде служб.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="4e3f9-106">Службы группируются по трем основным категориям: системам, службам расширений и поставщикам данных.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="4e3f9-107">системы</span><span class="sxs-lookup"><span data-stu-id="4e3f9-107">Systems</span></span>

<span data-ttu-id="4e3f9-108">Системы — это службы, которые предоставляют основные функциональные возможности набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4e3f9-109">Все системы являются реализациями [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="4e3f9-110">баундарисистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="4e3f9-111">камерасистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="4e3f9-112">диагностикссистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="4e3f9-113">инпутсистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="4e3f9-114">сценесистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="4e3f9-115">спатиалаваренесссистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="4e3f9-116">телепортсистем</span><span class="sxs-lookup"><span data-stu-id="4e3f9-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="4e3f9-117">Каждая из перечисленных систем отображается в [профиле](../features/profiles/profiles.md)конфигурации компонента микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="4e3f9-118">Расширения</span><span class="sxs-lookup"><span data-stu-id="4e3f9-118">Extensions</span></span>

<span data-ttu-id="4e3f9-119">Службы расширения — это компоненты, расширяющие функциональные возможности набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4e3f9-120">Все службы расширений должны указывать, что они реализуют [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="4e3f9-121">Сведения о создании служб расширения см. в статье [службы расширений](../features/extensions/extension-services.md) .</span><span class="sxs-lookup"><span data-stu-id="4e3f9-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="4e3f9-122">Для доступа к МРТК службы расширения регистрируются и настраиваются с помощью раздела Extensions в профиле конфигурации компонента Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Настройка службы расширений](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="4e3f9-124">Поставщики данных</span><span class="sxs-lookup"><span data-stu-id="4e3f9-124">Data providers</span></span>

<span data-ttu-id="4e3f9-125">Поставщики данных — это компоненты, которые по имени предоставляют данные для службы набора средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="4e3f9-126">Все поставщики данных должны указывать, что они реализуют [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="4e3f9-127">Не все службы потребует поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-127">Not all services will require data providers.</span></span> <span data-ttu-id="4e3f9-128">Систем, появляющихся системами набора средств смешанной реальности, являются единственной службой для использования поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="4e3f9-129">Для доступа к конкретной службе МРТК поставщики данных регистрируются в профиле конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="4e3f9-130">Код приложения обращается к поставщикам данных через [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="4e3f9-131">Для упрощения доступа поставщики данных также можно получить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="4e3f9-132">Несмотря на то `IMixedRealityDataProvider` , что наследует от `IMixedRealityService` , поставщики данных не регистрируются в `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="4e3f9-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="4e3f9-133">Для доступа к поставщикам данных код приложения должен запросить экземпляр службы, для которого они были зарегистрированы (например, система ввода).</span><span class="sxs-lookup"><span data-stu-id="4e3f9-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="4e3f9-134">Входные данные</span><span class="sxs-lookup"><span data-stu-id="4e3f9-134">Input</span></span>

<span data-ttu-id="4e3f9-135">Система ввода МРТК использует только поставщики данных, реализующие [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="4e3f9-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Поставщики входных системных данных](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="4e3f9-137">В следующем примере демонстрируется доступ к поставщику имитации ввода и переключается свойство Смусэйетраккинг.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="4e3f9-138">Доступ к поставщику данных для основной входной системы также можно упростить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="4e3f9-139">Входная система возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="4e3f9-140">Сведения о создании поставщика данных для входной системы МРТК см. в разделе [Создание входного системного поставщика данных](../features/input/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4e3f9-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="4e3f9-141">Поддержка пространственных сведений</span><span class="sxs-lookup"><span data-stu-id="4e3f9-141">Spatial awareness</span></span>

<span data-ttu-id="4e3f9-142">Система пространственной осведомленности МРТК использует только поставщики данных, реализующие [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Поставщики системных данных для пространственного отслеживания](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="4e3f9-144">В следующем примере демонстрируется доступ к зарегистрированным поставщикам данных пространственной сетки и изменение видимости сеток.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="4e3f9-145">Доступ к поставщику данных для основной системы пространственной информации также можно упростить с помощью `CoreServices` вспомогательного класса.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="4e3f9-146">Система пространственной информации возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="4e3f9-147">Сведения о написании поставщика данных для системы поддержки пространственной информации МРТК см. в разделе [Создание системного поставщика данных с](../features/spatial-awareness/create-data-provider.md)поддержкой пространственного доступа.</span><span class="sxs-lookup"><span data-stu-id="4e3f9-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e3f9-148">См. также</span><span class="sxs-lookup"><span data-stu-id="4e3f9-148">See also</span></span>

- [<span data-ttu-id="4e3f9-149">Службы расширений</span><span class="sxs-lookup"><span data-stu-id="4e3f9-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="4e3f9-150">Создание поставщика входных системных данных</span><span class="sxs-lookup"><span data-stu-id="4e3f9-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="4e3f9-151">Создание поставщика системных системных данных для пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="4e3f9-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="4e3f9-152">Интерфейс Имикседреалитисервице</span><span class="sxs-lookup"><span data-stu-id="4e3f9-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="4e3f9-153">Интерфейс Имикседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="4e3f9-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="4e3f9-154">Интерфейс Имикседреалитекстенсионсервице</span><span class="sxs-lookup"><span data-stu-id="4e3f9-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
