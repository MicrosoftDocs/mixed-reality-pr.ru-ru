---
title: Модульная МРТК
description: Описывает компоненты в МРТК.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177012"
---
# <a name="mrtk-modularization"></a><span data-ttu-id="d75ee-104">Модульная МРТК</span><span class="sxs-lookup"><span data-stu-id="d75ee-104">MRTK modularization</span></span>

<span data-ttu-id="d75ee-105">одной из замечательных новых функций смешанной реальности набор средств v2 является улучшение компонентов.</span><span class="sxs-lookup"><span data-stu-id="d75ee-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="d75ee-106">Везде, где это возможно, отдельные компоненты изолированы от всех основных уровней фундамента.</span><span class="sxs-lookup"><span data-stu-id="d75ee-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="d75ee-107">Минимальные зависимости</span><span class="sxs-lookup"><span data-stu-id="d75ee-107">Minimized dependencies</span></span>

<span data-ttu-id="d75ee-108">МРТК v2 была специально разработана для того, чтобы быть модульными и минимальными зависимостями между системными службами (например, сведения о пространственной поддержке).</span><span class="sxs-lookup"><span data-stu-id="d75ee-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="d75ee-109">Из-за особенностей некоторых системных служб (например, входных и телепортов) существует небольшое количество зависимостей.</span><span class="sxs-lookup"><span data-stu-id="d75ee-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="d75ee-110">Хотя предполагается, что службам потребуется один или несколько компонентов поставщика данных, между ними нет прямых связей.</span><span class="sxs-lookup"><span data-stu-id="d75ee-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="d75ee-111">Это справедливо и для функций пакета SDK (например, компонентов пользовательского интерфейса).</span><span class="sxs-lookup"><span data-stu-id="d75ee-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="d75ee-112">Взаимодействие компонентов</span><span class="sxs-lookup"><span data-stu-id="d75ee-112">Component communication</span></span>

<span data-ttu-id="d75ee-113">Чтобы обеспечить отсутствие прямых связей между компонентами, МРТК v2 использует интерфейсы для взаимодействия между службами, поставщиками данных и кодом приложения.</span><span class="sxs-lookup"><span data-stu-id="d75ee-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="d75ee-114">эти интерфейсы определяются в, и все коммуникации направляются через компонент набор средств ядра "смешанная реальность".</span><span class="sxs-lookup"><span data-stu-id="d75ee-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Использование системы пространственного отслеживания через интерфейсы](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="d75ee-116">Минимизация объема МРТК импорта</span><span class="sxs-lookup"><span data-stu-id="d75ee-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="d75ee-117">В данный момент МРТК импортируется как единый базовый пакет (без учета примеров пакета, который является полностью необязательным пакетом).</span><span class="sxs-lookup"><span data-stu-id="d75ee-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="d75ee-118">Вы можете уменьшить размер этого места, выполнив ручную отработку на импортированные файлы, хотя это очень просто процесс, который не имеет четко определенного руководства.</span><span class="sxs-lookup"><span data-stu-id="d75ee-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="d75ee-119">При импорте пакета Foundation можно снять флажки для произвольных элементов.</span><span class="sxs-lookup"><span data-stu-id="d75ee-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="d75ee-120">Однако не рекомендуется делать это на раннем этапе разработки, так как это может привести к нарушению функциональности.</span><span class="sxs-lookup"><span data-stu-id="d75ee-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="d75ee-121">После выяснения итогового набора функций приложения Удаление ненужных поставщиков и служб может выполняться в следующих папках:</span><span class="sxs-lookup"><span data-stu-id="d75ee-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="d75ee-122">МРТК и службы</span><span class="sxs-lookup"><span data-stu-id="d75ee-122">MRTK/Services</span></span>
- <span data-ttu-id="d75ee-123">МРТК и поставщики</span><span class="sxs-lookup"><span data-stu-id="d75ee-123">MRTK/Providers</span></span>
- <span data-ttu-id="d75ee-124">МРТК/SDK/компоненты</span><span class="sxs-lookup"><span data-stu-id="d75ee-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="d75ee-125">Для МРТК версии 2. x **_требуется_** содержимое папки Assets/Мртк/Core.</span><span class="sxs-lookup"><span data-stu-id="d75ee-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="d75ee-126">Предстоящие функции</span><span class="sxs-lookup"><span data-stu-id="d75ee-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="d75ee-127">Архитектура приложения</span><span class="sxs-lookup"><span data-stu-id="d75ee-127">Application architecture</span></span>

<span data-ttu-id="d75ee-128">МРТК будет поддерживать сборку приложений с использованием различных архитектур, в том числе:</span><span class="sxs-lookup"><span data-stu-id="d75ee-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="d75ee-129">Локатор службы Микседреалититулкит</span><span class="sxs-lookup"><span data-stu-id="d75ee-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="d75ee-130">Отдельные службы</span><span class="sxs-lookup"><span data-stu-id="d75ee-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="d75ee-131">Пользовательский указатель службы</span><span class="sxs-lookup"><span data-stu-id="d75ee-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="d75ee-132">Гибридная архитектура</span><span class="sxs-lookup"><span data-stu-id="d75ee-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="d75ee-133">При выборе архитектуры приложения важно учитывать гибкость проектирования и производительность приложений.</span><span class="sxs-lookup"><span data-stu-id="d75ee-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="d75ee-134">Описанные здесь архитектуры не должны подойти для каждого приложения.</span><span class="sxs-lookup"><span data-stu-id="d75ee-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="d75ee-135">Локатор службы Микседреалититулкит</span><span class="sxs-lookup"><span data-stu-id="d75ee-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="d75ee-136">МРТК включает (и автоматически настраивает) сцены приложений для использования [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) компонента локатора служб по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d75ee-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="d75ee-137">Этот компонент включает поддержку настройки систем и поставщиков данных МРТК через инспекторы конфигураций и управляет сроком существования компонентов и основными характеристиками (например, при обновлении).</span><span class="sxs-lookup"><span data-stu-id="d75ee-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="d75ee-138">Все системы представлены в основном инспекторе конфигураций, независимо от того, есть они или нет в проекте.</span><span class="sxs-lookup"><span data-stu-id="d75ee-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="d75ee-139">Дополнительные сведения см. в разделе с [руководством по настройке смешанной реальности](../configuration/mixed-reality-configuration-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="d75ee-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="d75ee-140">Отдельные компоненты службы</span><span class="sxs-lookup"><span data-stu-id="d75ee-140">Individual service components</span></span>

<span data-ttu-id="d75ee-141">Некоторые разработчики выражают желание включить отдельные компоненты службы в иерархию Application сцены.</span><span class="sxs-lookup"><span data-stu-id="d75ee-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="d75ee-142">Чтобы включить это использование, необходимо инкапсулировать службы в настраиваемом регистраторе или выполнить самостоятельную регистрацию или самостоятельное управление.</span><span class="sxs-lookup"><span data-stu-id="d75ee-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="d75ee-143">Самостоятельная служба реализует [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) и регистрирует саму себя, чтобы код приложения мог обнаружить экземпляр службы через реестр.</span><span class="sxs-lookup"><span data-stu-id="d75ee-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="d75ee-144">Самостоятельно управляемая служба может быть реализована как одноэлементный объект в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="d75ee-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="d75ee-145">Этот объект предоставляет и свойство экземпляра, которые код приложения может использовать для прямого доступа к функциональным возможностям службы.</span><span class="sxs-lookup"><span data-stu-id="d75ee-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="d75ee-146">Пользовательский указатель службы</span><span class="sxs-lookup"><span data-stu-id="d75ee-146">Custom service locator</span></span>

<span data-ttu-id="d75ee-147">Некоторые разработчики запросили возможность создания пользовательского компонента локатора служб.</span><span class="sxs-lookup"><span data-stu-id="d75ee-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="d75ee-148">Пользовательские указатели служб реализуют [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) интерфейс и управляют жизненным циклом и основными поведениями активных служб.</span><span class="sxs-lookup"><span data-stu-id="d75ee-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="d75ee-149">Гибридная архитектура</span><span class="sxs-lookup"><span data-stu-id="d75ee-149">Hybrid architecture</span></span>

<span data-ttu-id="d75ee-150">МРТК будет поддерживать гибридную архитектуру, в которой разработчики могут комбинировать предыдущие подходы по мере необходимости или нужным образом.</span><span class="sxs-lookup"><span data-stu-id="d75ee-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="d75ee-151">Например, разработчик может начать с [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) локатора службы и добавить собственную службу регистрации.</span><span class="sxs-lookup"><span data-stu-id="d75ee-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="d75ee-152">При продолжении использования гибридной архитектуры важно быть учитыватьм любого дублирования работы (например, получение данных контроллера из нескольких компонентов).</span><span class="sxs-lookup"><span data-stu-id="d75ee-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
