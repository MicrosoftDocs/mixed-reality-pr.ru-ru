---
title: Общие сведения о системе границ
description: Целевая страница для системы границ в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, система границ,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177084"
---
# <a name="boundary-system-overview"></a><span data-ttu-id="e75c9-104">Общие сведения о системе границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-104">Boundary system overview</span></span>

<span data-ttu-id="e75c9-105">Система границ обеспечивает поддержку визуализации компонентов границ виртуальной реальности в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e75c9-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="e75c9-106">Границы определяют область, в которой пользователи могут безопасно перемещаться, людьми гарнитуру VR.</span><span class="sxs-lookup"><span data-stu-id="e75c9-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="e75c9-107">Границы являются важным компонентом смешанной реальности, чтобы помочь пользователям избежать незамеченных препятствий при людьмие гарнитуры VR.</span><span class="sxs-lookup"><span data-stu-id="e75c9-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="e75c9-108">Многие платформы Virtual Reality предоставляют автоматическое отображение, например, белый контур, наложенный на виртуальный мир в качестве пользователя или контроллера вблизи границы.</span><span class="sxs-lookup"><span data-stu-id="e75c9-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="e75c9-109">система границ смешанной реальности набор средств расширяет эту функцию, позволяя отображать контур области, плоскости и другие функции, которые можно использовать для предоставления пользователям дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="e75c9-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="e75c9-110">Начало работы</span><span class="sxs-lookup"><span data-stu-id="e75c9-110">Getting started</span></span>

<span data-ttu-id="e75c9-111">для добавления поддержки границ требуются два ключевых компонента смешанной набор средств реальности: система границ и платформа Virtual Reality настроена с границей.</span><span class="sxs-lookup"><span data-stu-id="e75c9-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="e75c9-112">[Включение](#enable-boundary-system) системы границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="e75c9-113">[Настройка](#configure-boundary-visualization) визуализации границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="e75c9-114">[Сборка и развертывание](#build-and-deploy) на платформе VR с настроенной границей</span><span class="sxs-lookup"><span data-stu-id="e75c9-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="e75c9-115">Включить систему границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-115">Enable boundary system</span></span>

<span data-ttu-id="e75c9-116">Системой управления границей управляет объект Микседреалититулкит (или другой компонент [регистратора служб](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="e75c9-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="e75c9-117">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="e75c9-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e75c9-118">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="e75c9-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e75c9-119">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="e75c9-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="e75c9-121">Перейдите на панель инспектора к разделу система границ и установите флажок Включить.</span><span class="sxs-lookup"><span data-stu-id="e75c9-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Включение системы границ](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="e75c9-123">Выберите реализацию системы границ.</span><span class="sxs-lookup"><span data-stu-id="e75c9-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="e75c9-124">Реализацией класса по умолчанию, предоставляемой МРТК, является [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="e75c9-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Выбор реализации системы границ](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="e75c9-126">Вся реализация системы границ должна расширять [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="e75c9-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="e75c9-127">Настройка визуализации границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-127">Configure boundary visualization</span></span>

<span data-ttu-id="e75c9-128">[Система границ использует профиль конфигурации](configuring-boundary-visualization.md) , чтобы указать, какие компоненты границ должны быть отображены, и настроить их внешний вид.</span><span class="sxs-lookup"><span data-stu-id="e75c9-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Параметры визуализации границ](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="e75c9-130">У пользователей профиля по умолчанию `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/мртк/SDK/Profiles) будет предварительно настроена система границ для показа плоскости этажа, области воспроизведения и области с отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="e75c9-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="e75c9-131">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="e75c9-131">Build and deploy</span></span>

<span data-ttu-id="e75c9-132">После настройки системы границ с требуемыми параметрами визуализации проект можно построить на целевой платформе.</span><span class="sxs-lookup"><span data-stu-id="e75c9-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="e75c9-133">Режим воспроизведения Unity позволяет визуализировать настроенную границу в редакторе.</span><span class="sxs-lookup"><span data-stu-id="e75c9-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="e75c9-134">Эта функция обеспечивает быструю разработку и тестирование без необходимости выполнять этап сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="e75c9-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="e75c9-135">Обязательно выполните окончательное приемочное тестирование с помощью созданной и развернутой версии приложения, работающей на целевом оборудовании и платформе.</span><span class="sxs-lookup"><span data-stu-id="e75c9-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="e75c9-136">Доступ к граничной системе через код</span><span class="sxs-lookup"><span data-stu-id="e75c9-136">Accessing boundary system via code</span></span>

<span data-ttu-id="e75c9-137">Если параметр включен и настроен, доступ к системе границ можно получить с помощью статического вспомогательного класса Коресервицес.</span><span class="sxs-lookup"><span data-stu-id="e75c9-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="e75c9-138">Затем можно использовать ссылку для динамического изменения параметров границ и доступа к связанным объекты gameobject, управляемым системой.</span><span class="sxs-lookup"><span data-stu-id="e75c9-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="e75c9-139">См. также:</span><span class="sxs-lookup"><span data-stu-id="e75c9-139">See also</span></span>

- [<span data-ttu-id="e75c9-140">Документация по API границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="e75c9-141">Настройка визуализации границ</span><span class="sxs-lookup"><span data-stu-id="e75c9-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
