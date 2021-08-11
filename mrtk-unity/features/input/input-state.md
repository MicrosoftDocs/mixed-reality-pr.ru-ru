---
title: Состояние входных данных
description: Документация по входным состояниям в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, инпутстате,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228364"
---
# <a name="accessing-input-state-in-mrtk"></a>Доступ к входному состоянию в МРТК

Можно напрямую запрашивать состояние всех входных данных в МРТК путем прохода по контроллерам, подключенным к источникам входных данных. МРТК также предоставляет удобные методы для доступа к положению и повороту глаз, руки, головной панели и контроллера движения.

Пример запроса входных данных с помощью итерации контроллеров и класса см. в сцене Инпутдатаексампле [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Пример: доступ к положению, поворот головного, руки, глаза в МРТК

Класс МРТК [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) предоставляет удобные методы для доступа к рукой, а также к элементу управления "рука", "головной луч", "глаз глаза" и к лучау контроллера движения

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Пример: расположение доступа, поворот всех контроллеров 6DOF, активных в сцене

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>См. также раздел

- [InputEvents](input-events.md)
- [Указатели](pointers.md)
- [хандтраккинг](hand-tracking.md)
