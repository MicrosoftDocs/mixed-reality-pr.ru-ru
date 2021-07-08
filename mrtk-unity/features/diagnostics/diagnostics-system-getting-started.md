---
title: Обзор системы диагностики
description: Документация по включению и отключению диагностики в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177245"
---
# <a name="diagnostics-system-overview"></a><span data-ttu-id="4e66d-104">Обзор системы диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-104">Diagnostics system overview</span></span>

<span data-ttu-id="4e66d-105">система диагностики смешанной реальности набор средств предоставляет средства диагностики, которые выполняются в приложении, чтобы обеспечить анализ проблем приложений.</span><span class="sxs-lookup"><span data-stu-id="4e66d-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="4e66d-106">Первый выпуск системы диагностики содержит [Визуальный профилировщик](using-visual-profiler.md) , позволяющий анализировать проблемы производительности при использовании приложения.</span><span class="sxs-lookup"><span data-stu-id="4e66d-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="4e66d-107">Начало работы</span><span class="sxs-lookup"><span data-stu-id="4e66d-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e66d-108">**_Настоятельно_** рекомендуется включить систему диагностики во всем цикле разработки продукта и отключить ее в соответствии с последним изменением до создания и выпуска окончательной версии.</span><span class="sxs-lookup"><span data-stu-id="4e66d-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="4e66d-109">Для начала работы с системой диагностики необходимо выполнить два основных действия.</span><span class="sxs-lookup"><span data-stu-id="4e66d-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="4e66d-110">[Включение](#enable-diagnostics) диагностической системы</span><span class="sxs-lookup"><span data-stu-id="4e66d-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="4e66d-111">[Настройка](#configure-diagnostic-options) параметров диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="4e66d-112">Включение диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-112">Enable diagnostics</span></span>

<span data-ttu-id="4e66d-113">Система диагностики управляется объектом Микседреалититулкит (или другим компонентом [регистратора служб](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="4e66d-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="4e66d-114">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="4e66d-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="4e66d-115">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="4e66d-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="4e66d-116">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="4e66d-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="4e66d-118">Перейдите на панель инспектора к разделу системы диагностики и установите флажок Включить.</span><span class="sxs-lookup"><span data-stu-id="4e66d-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="4e66d-119">Выбор реализации системы диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-119">Select the Diagnostics System implementation</span></span>

    ![Выбор реализации системы диагностики](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="4e66d-121">Пользователи профиля по умолчанию `DefaultMixedRealityToolkitConfigurationProfile` (Assets/мртк/SDK/Profiles) будут иметь предварительно настроенную систему диагностики для использования [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) объекта.</span><span class="sxs-lookup"><span data-stu-id="4e66d-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="4e66d-122">Настройка параметров диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-122">Configure diagnostic options</span></span>

<span data-ttu-id="4e66d-123">Система диагностики использует профиль конфигурации для указания отображаемых компонентов и настройки их параметров.</span><span class="sxs-lookup"><span data-stu-id="4e66d-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="4e66d-124">Дополнительные сведения о доступных параметрах компонентов см. в разделе [Настройка системы диагностики](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="4e66d-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e66d-125">Хотя можно использовать режим воспроизведения Unity при разработке приложений без необходимости выполнять сборку и развертывание, важно оценить результаты системы диагностики с помощью скомпилированного приложения, работающего на целевом оборудовании и платформе.</span><span class="sxs-lookup"><span data-stu-id="4e66d-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="4e66d-126">Диагностика производительности, например, [Визуальный профилировщик](using-visual-profiler.md), может не точно отражать фактическую производительность приложения при запуске в редакторе.</span><span class="sxs-lookup"><span data-stu-id="4e66d-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e66d-127">См. также:</span><span class="sxs-lookup"><span data-stu-id="4e66d-127">See also</span></span>

- [<span data-ttu-id="4e66d-128">Документация по API диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="4e66d-129">Настройка системы диагностики</span><span class="sxs-lookup"><span data-stu-id="4e66d-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="4e66d-130">Использование Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="4e66d-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)