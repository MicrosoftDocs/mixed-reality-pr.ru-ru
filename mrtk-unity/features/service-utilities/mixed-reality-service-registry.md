---
title: Реестр службы Mixed Reality и Имикседреалитисервицерегистрар
description: Документация по Микседреалитисервицерегистри и Имикседреалитисервицерегистрар
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145230"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="f7a47-104">Что такое Микседреалитисервицерегистри и Имикседреалитисервицерегистрар?</span><span class="sxs-lookup"><span data-stu-id="f7a47-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="f7a47-105">В наборе средств Mixed Reality есть два очень схожих именованных компонента, выполняющих связанные задачи: Микседреалитисервицерегистри и Имикседреалитисервицерегистрар.</span><span class="sxs-lookup"><span data-stu-id="f7a47-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="f7a47-106">микседреалитисервицерегистри</span><span class="sxs-lookup"><span data-stu-id="f7a47-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="f7a47-107">[Микседреалитисервицерегистри](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) — это компонент, который содержит экземпляры каждой зарегистрированной службы (основные системы и службы расширений).</span><span class="sxs-lookup"><span data-stu-id="f7a47-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="f7a47-108">Микседреалитисервицерегистри содержит экземпляры объектов, реализующих интерфейс [имикседреалитисервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , включая [имикседреалитекстенсионсервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span><span class="sxs-lookup"><span data-stu-id="f7a47-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="f7a47-109">Объекты, реализующие [имикседреалитидатапровидер](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (подкласс имикседреалитисервице), явно не зарегистрированы в микседреалитисервицерегистри.</span><span class="sxs-lookup"><span data-stu-id="f7a47-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="f7a47-110">Эти объекты управляются отдельными службами (например, пространственной осведомленностью).</span><span class="sxs-lookup"><span data-stu-id="f7a47-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="f7a47-111">Микседреалитисервицерегистри реализуется как статический класс C# и является рекомендуемым шаблоном, используемым для получения экземпляров службы в коде приложения.</span><span class="sxs-lookup"><span data-stu-id="f7a47-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="f7a47-112">В следующем фрагменте кода демонстрируется получение экземпляра Имикседреалитинпутсистем.</span><span class="sxs-lookup"><span data-stu-id="f7a47-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="f7a47-113">имикседреалитисервицерегистрар</span><span class="sxs-lookup"><span data-stu-id="f7a47-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="f7a47-114">[Имикседреалитисервицерегистрар](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) — это интерфейс, который определяет функциональные возможности, реализуемые компонентами, которые управляют регистрацией одной или нескольких служб.</span><span class="sxs-lookup"><span data-stu-id="f7a47-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="f7a47-115">Компоненты, реализующие Имикседреалитисервицерегистрар, отвечают за добавление и удаление данных в Микседреалитисервицерегистри.</span><span class="sxs-lookup"><span data-stu-id="f7a47-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="f7a47-116">Объект [микседреалититулкит](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) является одним из таких компонентов.</span><span class="sxs-lookup"><span data-stu-id="f7a47-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="f7a47-117">Другие регистраторы можно найти в папке МРТК/SDK/эксперименталь/Features.</span><span class="sxs-lookup"><span data-stu-id="f7a47-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="f7a47-118">Эти компоненты можно использовать для добавления в приложение поддержки отдельной службы (например, пространственной осведомленности).</span><span class="sxs-lookup"><span data-stu-id="f7a47-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="f7a47-119">Эти одиночные Диспетчеры служб перечислены ниже.</span><span class="sxs-lookup"><span data-stu-id="f7a47-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="f7a47-120">баундарисистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="f7a47-121">камерасистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="f7a47-122">диагностикссистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="f7a47-123">инпутсистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="f7a47-124">спатиалаваренесссистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="f7a47-125">телепортсистемманажер</span><span class="sxs-lookup"><span data-stu-id="f7a47-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="f7a47-126">Каждый из перечисленных выше компонентов, за исключением Инпутсистемманажер, отвечает за Управление регистрацией и состоянием одного типа службы.</span><span class="sxs-lookup"><span data-stu-id="f7a47-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="f7a47-127">Для Инпутсистем требуются некоторые дополнительные службы поддержки (например, Фокуспровидер), которые также управляются Инпутсистемманажер.</span><span class="sxs-lookup"><span data-stu-id="f7a47-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="f7a47-128">Как правило, методы, определенные Имикседреалитисервицерегистрар, вызываются внутренне компонентами управления службами или вызываются службами, требующими правильной работы дополнительных компонентов службы.</span><span class="sxs-lookup"><span data-stu-id="f7a47-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="f7a47-129">Код приложения, как правило, не вызывает эти методы, так как это может привести к непредсказуемому поведению приложения (например, кэшированный экземпляр службы может стать недопустимым).</span><span class="sxs-lookup"><span data-stu-id="f7a47-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a47-130">См. также</span><span class="sxs-lookup"><span data-stu-id="f7a47-130">See also</span></span>

- [<span data-ttu-id="f7a47-131">Документация по API Имикседреалитисервицерегистрар</span><span class="sxs-lookup"><span data-stu-id="f7a47-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="f7a47-132">Документация по API Микседреалитисервицерегистри</span><span class="sxs-lookup"><span data-stu-id="f7a47-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
