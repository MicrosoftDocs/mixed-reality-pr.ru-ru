---
title: Начало работы с пространственными сведениями
description: сведения о пространственной осведомленности в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176710"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="7abf3-104">Начало работы с пространственными сведениями</span><span class="sxs-lookup"><span data-stu-id="7abf3-104">Spatial awareness getting started</span></span>

![Отслеживание пространственного положения](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="7abf3-106">Система пространственной осведомленности обеспечивает реальную осведомленность окружающей среды в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7abf3-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="7abf3-107">при использовании в Microsoft HoloLens пространственной осведомленности предоставил коллекцию сеток, представляющую геометрию среды, которая допускает привлекательное взаимодействие между голограммами и реальными.</span><span class="sxs-lookup"><span data-stu-id="7abf3-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="7abf3-108">в настоящее время набор средств смешанной реальности не поставляются с пространственными знаниями о алгоритмах, изначально упакованных в холотулкит.</span><span class="sxs-lookup"><span data-stu-id="7abf3-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="7abf3-109">Пространственное понимание обычно включает преобразование данных пространственной сетки для создания упрощенных и/или сгруппированных данных сетки, таких как плоскости, стены, пол, цеилингс и т. д.</span><span class="sxs-lookup"><span data-stu-id="7abf3-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="7abf3-110">Начало работы</span><span class="sxs-lookup"><span data-stu-id="7abf3-110">Getting started</span></span>

<span data-ttu-id="7abf3-111">для добавления поддержки пространственной информации требуется два ключевых компонента смешанной набор средств реальности: система пространственной осведомленности и поддерживаемый поставщик платформы.</span><span class="sxs-lookup"><span data-stu-id="7abf3-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="7abf3-112">[Включение](#enable-the-spatial-awareness-system) системы распознавания пространственных</span><span class="sxs-lookup"><span data-stu-id="7abf3-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="7abf3-113">[Регистрация](#register-observers) и [Настройка](configuring-spatial-awareness-mesh-observer.md) одного или нескольких пространственных наблюдателей для предоставления данных сетки</span><span class="sxs-lookup"><span data-stu-id="7abf3-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="7abf3-114">[Сборка и развертывание](#build-and-deploy) на платформе, поддерживающей пространственное распознавание</span><span class="sxs-lookup"><span data-stu-id="7abf3-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="7abf3-115">Включение системы распознавания пространственных</span><span class="sxs-lookup"><span data-stu-id="7abf3-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="7abf3-116">Система пространственной осведомленности управляется объектом Микседреалититулкит (или другим компонентом [регистратора служб](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="7abf3-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="7abf3-117">Выполните следующие действия, чтобы включить или отключить *систему пространственного отслеживания* в профиле *микседреалититулкит* .</span><span class="sxs-lookup"><span data-stu-id="7abf3-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="7abf3-118">набор средств смешанной реальности поставляется с несколькими предварительно настроенными профилями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7abf3-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="7abf3-119">В некоторых из них по умолчанию включена или отключена система пространственной осведомленности.</span><span class="sxs-lookup"><span data-stu-id="7abf3-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="7abf3-120">Цель этой предварительной настройки, особенно для отключенной, заключается в предотвращении визуальных издержек при вычислении и визуализации сеток.</span><span class="sxs-lookup"><span data-stu-id="7abf3-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="7abf3-121">Профиль</span><span class="sxs-lookup"><span data-stu-id="7abf3-121">Profile</span></span> | <span data-ttu-id="7abf3-122">Система включена по умолчанию</span><span class="sxs-lookup"><span data-stu-id="7abf3-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="7abf3-123">`DefaultHoloLens1ConfigurationProfile` (Assets/МРТК/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="7abf3-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="7abf3-124">Неверно</span><span class="sxs-lookup"><span data-stu-id="7abf3-124">False</span></span> |
| <span data-ttu-id="7abf3-125">`DefaultHoloLens2ConfigurationProfile` (Assets/МРТК/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="7abf3-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="7abf3-126">Неверно</span><span class="sxs-lookup"><span data-stu-id="7abf3-126">False</span></span> |
| <span data-ttu-id="7abf3-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/МРТК/SDK/Profiles)</span><span class="sxs-lookup"><span data-stu-id="7abf3-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="7abf3-128">Верно</span><span class="sxs-lookup"><span data-stu-id="7abf3-128">True</span></span> |

1. <span data-ttu-id="7abf3-129">Выберите объект Микседреалититулкит в иерархии сцены, чтобы открыть его на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="7abf3-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="7abf3-131">Перейдите к разделу " *система пространственных* сведений" и установите флажок " *включить систему пространственного отслеживания* ".</span><span class="sxs-lookup"><span data-stu-id="7abf3-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Включить поддержку пространственного расположения](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="7abf3-133">Выберите нужный тип реализации системы пространственного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="7abf3-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="7abf3-134">По [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) умолчанию задано значение.</span><span class="sxs-lookup"><span data-stu-id="7abf3-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Выберите реализацию системы пространственного отслеживания](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="7abf3-136">Регистрация наблюдателей</span><span class="sxs-lookup"><span data-stu-id="7abf3-136">Register observers</span></span>

<span data-ttu-id="7abf3-137">службы в набор средств смешанной реальности могут иметь [службы поставщика данных](../../architecture/systems-extensions-providers.md) , которые дополняют основную службу данными и элементами управления реализацией, связанными с платформой.</span><span class="sxs-lookup"><span data-stu-id="7abf3-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="7abf3-138">Примером этого является система ввода смешанной реальности, которая имеет [несколько поставщиков данных](../input/input-providers.md) для получения контроллера и других связанных входных данных из различных интерфейсных API для конкретной платформы.</span><span class="sxs-lookup"><span data-stu-id="7abf3-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="7abf3-139">Система пространственной информации похожа на то, что поставщики данных предоставляют систему с данными сетки о реальном мире.</span><span class="sxs-lookup"><span data-stu-id="7abf3-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="7abf3-140">В профиле поддержки пространственных должно быть зарегистрировано по крайней мере один пространственный наблюдатель.</span><span class="sxs-lookup"><span data-stu-id="7abf3-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="7abf3-141">Пространственные наблюдатели обычно являются компонентами платформы, которые действуют как поставщик для отображая различных типов данных сетки из конечной точки конкретной платформы (т. е.</span><span class="sxs-lookup"><span data-stu-id="7abf3-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="7abf3-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="7abf3-142">HoloLens).</span></span>

1. <span data-ttu-id="7abf3-143">Открыть или развернуть *системный профиль пространственного отслеживания*</span><span class="sxs-lookup"><span data-stu-id="7abf3-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Системный профиль пространственного отслеживания](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="7abf3-145">Нажмите кнопку *"добавить пространственный наблюдатель"*</span><span class="sxs-lookup"><span data-stu-id="7abf3-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="7abf3-146">Выбор требуемого *типа реализации пространственного наблюдателя*</span><span class="sxs-lookup"><span data-stu-id="7abf3-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Выбор реализации пространственного наблюдателя](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="7abf3-148">[Изменение свойств конфигурации наблюдателя](configuring-spatial-awareness-mesh-observer.md) при необходимости</span><span class="sxs-lookup"><span data-stu-id="7abf3-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="7abf3-149">`DefaultMixedRealityToolkitConfigurationProfile`у пользователей (assets/мртк/SDK/profiles) будет предварительно настроена система пространственной осведомленности для платформы Windows Mixed Reality, которая использует [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) класс.</span><span class="sxs-lookup"><span data-stu-id="7abf3-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="7abf3-150">Сборка и развертывание</span><span class="sxs-lookup"><span data-stu-id="7abf3-150">Build and deploy</span></span>

<span data-ttu-id="7abf3-151">После настройки системы пространственной информации с нужными наблюдателями проект можно построить и развернуть на целевой платформе.</span><span class="sxs-lookup"><span data-stu-id="7abf3-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7abf3-152">если нацеливание на платформу Windows Mixed Reality (например, HoloLens), важно убедиться, что [функция пространственного восприятия](/windows/mixed-reality/spatial-mapping-in-unity) включена, чтобы использовать систему пространственной осведомленности на устройстве.</span><span class="sxs-lookup"><span data-stu-id="7abf3-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="7abf3-153">некоторые платформы, в том числе Microsoft HoloLens, обеспечивают поддержку удаленного выполнения из Unity.</span><span class="sxs-lookup"><span data-stu-id="7abf3-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="7abf3-154">Эта функция обеспечивает быструю разработку и тестирование без необходимости выполнять этап сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="7abf3-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="7abf3-155">Обязательно выполните окончательное приемочное тестирование с помощью созданной и развернутой версии приложения, работающей на целевом оборудовании и платформе.</span><span class="sxs-lookup"><span data-stu-id="7abf3-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7abf3-156">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="7abf3-156">Next steps</span></span>

<span data-ttu-id="7abf3-157">После выполнения описанных выше процедур для включения системы пространственной информации система может настраиваться и контролироваться более подробно.</span><span class="sxs-lookup"><span data-stu-id="7abf3-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="7abf3-158">Сведения о настройке наблюдателей в инспекторе:</span><span class="sxs-lookup"><span data-stu-id="7abf3-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="7abf3-159">Настройка наблюдателей для использования на устройствах</span><span class="sxs-lookup"><span data-stu-id="7abf3-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="7abf3-160">Настройка наблюдателей для использования в редакторе</span><span class="sxs-lookup"><span data-stu-id="7abf3-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="7abf3-161">Сведения для управления и расширения наблюдателей с помощью кода:</span><span class="sxs-lookup"><span data-stu-id="7abf3-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="7abf3-162">Настройка наблюдателей с помощью кода</span><span class="sxs-lookup"><span data-stu-id="7abf3-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="7abf3-163">Создание пользовательского наблюдателя</span><span class="sxs-lookup"><span data-stu-id="7abf3-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="7abf3-164">См. также:</span><span class="sxs-lookup"><span data-stu-id="7abf3-164">See also</span></span>

- [<span data-ttu-id="7abf3-165">Документация по API пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="7abf3-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="7abf3-166">Общие сведения о пространственном сопоставлении ВМР</span><span class="sxs-lookup"><span data-stu-id="7abf3-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="7abf3-167">Пространственное сопоставление в Unity ВМР</span><span class="sxs-lookup"><span data-stu-id="7abf3-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
