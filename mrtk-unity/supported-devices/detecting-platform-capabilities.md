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
# <a name="detecting-platform-capabilities"></a>Обнаружение возможностей платформы

Распространенный вопрос о МРТКе заключается в том, что необходимо знать, какое конкретное устройство (например, Microsoft HoloLens 2) используется для запуска приложения. Определение точного оборудования может быть трудной задачей на разных платформах. Вместо этого МРТК предоставляет способ для обнаружения конкретных возможностей во время выполнения (например, если текущая конечная точка устройства поддерживает четкое обучение).

## <a name="capabilities"></a>Характеристики

Набор средств Mixed Reality предоставляет [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) перечисление, которое определяет набор возможностей, которые приложение может запрашивать во время выполнения.

### <a name="input-system-capabilities"></a>Возможности входной системы

Входная система МРТК по умолчанию поддерживает запросы к следующим возможностям:

| Возможности | Описание |
|---|---|
| артикулатедханд | Ввод с формулировкой |
| EyeTracking | Целевой объект взгляда на глаз |
| ггвханд | Взгляд-жест — ввод голоса |
| мотионконтроллер | Входные данные контроллера движения |
| воицекомманд | Голосовые команды с использованием определенных приложением ключевых слов |
| воицедиктатион | Диктовка голоса по тексту |

Приведенный ниже пример кода проверяет, загрузил ли входную систему поставщик данных с поддержкой четко сформулированных стрелок.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Возможности пространственной осведомленности

Система поддержки пространственного МРТК по умолчанию поддерживает запросы к следующим возможностям:

| Возможности | Описание |
|---|---|
| спатиалаваренессмеш | Пространственные сетки |
| спатиалаваренессплане | Пространственные плоскости |
| спатиалаваренесспоинт | Пространственные точки |

В этом примере проверяется, загружен ли в системе пространственной информации поставщик данных с поддержкой пространственных сеток.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>См. также раздел

- [Документация по API Имикседреалитикапабилитичекк](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Документация по перечислению Микседреалитикапабилити](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
