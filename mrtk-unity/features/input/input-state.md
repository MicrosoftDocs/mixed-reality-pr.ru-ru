---
title: Состояние входных данных
description: Документация по входным состояниям в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Инпутстате,
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145251"
---
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="119a8-104">Доступ к входному состоянию в МРТК</span><span class="sxs-lookup"><span data-stu-id="119a8-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="119a8-105">Можно напрямую запрашивать состояние всех входных данных в МРТК путем прохода по контроллерам, подключенным к источникам входных данных.</span><span class="sxs-lookup"><span data-stu-id="119a8-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="119a8-106">МРТК также предоставляет удобные методы для доступа к положению и повороту глаз, руки, головной панели и контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="119a8-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="119a8-107">Пример запроса входных данных с помощью итерации контроллеров и класса см. в сцене Инпутдатаексампле [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) .</span><span class="sxs-lookup"><span data-stu-id="119a8-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="119a8-108">Пример: доступ к положению, поворот головного, руки, глаза в МРТК</span><span class="sxs-lookup"><span data-stu-id="119a8-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="119a8-109">Класс МРТК [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) предоставляет удобные методы для доступа к рукой, а также к элементу управления "рука", "головной луч", "глаз глаза" и к лучау контроллера движения</span><span class="sxs-lookup"><span data-stu-id="119a8-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="119a8-110">Пример: расположение доступа, поворот всех контроллеров 6DOF, активных в сцене</span><span class="sxs-lookup"><span data-stu-id="119a8-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

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

## <a name="see-also"></a><span data-ttu-id="119a8-111">См. также</span><span class="sxs-lookup"><span data-stu-id="119a8-111">See also</span></span>

- [<span data-ttu-id="119a8-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="119a8-112">InputEvents</span></span>](input-events.md)
- [<span data-ttu-id="119a8-113">Указатели</span><span class="sxs-lookup"><span data-stu-id="119a8-113">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="119a8-114">хандтраккинг</span><span class="sxs-lookup"><span data-stu-id="119a8-114">HandTracking</span></span>](hand-tracking.md)
