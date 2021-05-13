---
title: детектингплатформкапабилитиес
description: Сведения о различных возможностях, поддерживаемых МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, возможности,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852440"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="ceea2-104">Обнаружение возможностей платформы</span><span class="sxs-lookup"><span data-stu-id="ceea2-104">Detecting platform capabilities</span></span>

<span data-ttu-id="ceea2-105">Распространенный вопрос о МРТКе заключается в том, что необходимо знать, какое конкретное устройство (например, Microsoft HoloLens 2) используется для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="ceea2-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="ceea2-106">Определение точного оборудования может быть трудной задачей на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="ceea2-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="ceea2-107">Вместо этого МРТК предоставляет способ для обнаружения конкретных возможностей во время выполнения (например, если текущая конечная точка устройства поддерживает четкое обучение).</span><span class="sxs-lookup"><span data-stu-id="ceea2-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="ceea2-108">Характеристики</span><span class="sxs-lookup"><span data-stu-id="ceea2-108">Capabilities</span></span>

<span data-ttu-id="ceea2-109">Набор средств Mixed Reality предоставляет [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) перечисление, которое определяет набор возможностей, которые приложение может запрашивать во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ceea2-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="ceea2-110">Возможности входной системы</span><span class="sxs-lookup"><span data-stu-id="ceea2-110">Input system capabilities</span></span>

<span data-ttu-id="ceea2-111">Входная система МРТК по умолчанию поддерживает запросы к следующим возможностям:</span><span class="sxs-lookup"><span data-stu-id="ceea2-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="ceea2-112">Возможности</span><span class="sxs-lookup"><span data-stu-id="ceea2-112">Capability</span></span> | <span data-ttu-id="ceea2-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ceea2-113">Description</span></span> |
|---|---|
| <span data-ttu-id="ceea2-114">артикулатедханд</span><span class="sxs-lookup"><span data-stu-id="ceea2-114">ArticulatedHand</span></span> | <span data-ttu-id="ceea2-115">Ввод с формулировкой</span><span class="sxs-lookup"><span data-stu-id="ceea2-115">Articulated hand input</span></span> |
| <span data-ttu-id="ceea2-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="ceea2-116">EyeTracking</span></span> | <span data-ttu-id="ceea2-117">Целевой объект взгляда на глаз</span><span class="sxs-lookup"><span data-stu-id="ceea2-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="ceea2-118">ггвханд</span><span class="sxs-lookup"><span data-stu-id="ceea2-118">GGVHand</span></span> | <span data-ttu-id="ceea2-119">Взгляд-жест — ввод голоса</span><span class="sxs-lookup"><span data-stu-id="ceea2-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="ceea2-120">мотионконтроллер</span><span class="sxs-lookup"><span data-stu-id="ceea2-120">MotionController</span></span> | <span data-ttu-id="ceea2-121">Входные данные контроллера движения</span><span class="sxs-lookup"><span data-stu-id="ceea2-121">Motion controller input</span></span> |
| <span data-ttu-id="ceea2-122">воицекомманд</span><span class="sxs-lookup"><span data-stu-id="ceea2-122">VoiceCommand</span></span> | <span data-ttu-id="ceea2-123">Голосовые команды с использованием определенных приложением ключевых слов</span><span class="sxs-lookup"><span data-stu-id="ceea2-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="ceea2-124">воицедиктатион</span><span class="sxs-lookup"><span data-stu-id="ceea2-124">VoiceDictation</span></span> | <span data-ttu-id="ceea2-125">Диктовка голоса по тексту</span><span class="sxs-lookup"><span data-stu-id="ceea2-125">Voice to text dictation</span></span> |

<span data-ttu-id="ceea2-126">Приведенный ниже пример кода проверяет, загрузил ли входную систему поставщик данных с поддержкой четко сформулированных стрелок.</span><span class="sxs-lookup"><span data-stu-id="ceea2-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="ceea2-127">Возможности пространственной осведомленности</span><span class="sxs-lookup"><span data-stu-id="ceea2-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="ceea2-128">Система поддержки пространственного МРТК по умолчанию поддерживает запросы к следующим возможностям:</span><span class="sxs-lookup"><span data-stu-id="ceea2-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="ceea2-129">Возможности</span><span class="sxs-lookup"><span data-stu-id="ceea2-129">Capability</span></span> | <span data-ttu-id="ceea2-130">Описание</span><span class="sxs-lookup"><span data-stu-id="ceea2-130">Description</span></span> |
|---|---|
| <span data-ttu-id="ceea2-131">спатиалаваренессмеш</span><span class="sxs-lookup"><span data-stu-id="ceea2-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="ceea2-132">Пространственные сетки</span><span class="sxs-lookup"><span data-stu-id="ceea2-132">Spatial meshes</span></span> |
| <span data-ttu-id="ceea2-133">спатиалаваренессплане</span><span class="sxs-lookup"><span data-stu-id="ceea2-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="ceea2-134">Пространственные плоскости</span><span class="sxs-lookup"><span data-stu-id="ceea2-134">Spatial planes</span></span> |
| <span data-ttu-id="ceea2-135">спатиалаваренесспоинт</span><span class="sxs-lookup"><span data-stu-id="ceea2-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="ceea2-136">Пространственные точки</span><span class="sxs-lookup"><span data-stu-id="ceea2-136">Spatial points</span></span> |

<span data-ttu-id="ceea2-137">В этом примере проверяется, загружен ли в системе пространственной информации поставщик данных с поддержкой пространственных сеток.</span><span class="sxs-lookup"><span data-stu-id="ceea2-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="ceea2-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ceea2-138">See also</span></span>

- [<span data-ttu-id="ceea2-139">Документация по API Имикседреалитикапабилитичекк</span><span class="sxs-lookup"><span data-stu-id="ceea2-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="ceea2-140">Документация по перечислению Микседреалитикапабилити</span><span class="sxs-lookup"><span data-stu-id="ceea2-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
