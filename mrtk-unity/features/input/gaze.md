---
title: Взгляд
description: Докумментатион для типов взгляда на МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, взгляд,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176909"
---
# <a name="gaze"></a><span data-ttu-id="0c90b-104">Взгляд</span><span class="sxs-lookup"><span data-stu-id="0c90b-104">Gaze</span></span>

<span data-ttu-id="0c90b-105">[Взгляд](/windows/mixed-reality/gaze) — это форма входных данных, которая взаимодействует с миром в зависимости от того, где находится пользователь.</span><span class="sxs-lookup"><span data-stu-id="0c90b-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="0c90b-106">Взгляд существует в двух разных разновидностях</span><span class="sxs-lookup"><span data-stu-id="0c90b-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="0c90b-107">Отслеживание направления головы</span><span class="sxs-lookup"><span data-stu-id="0c90b-107">Head gaze</span></span>

<span data-ttu-id="0c90b-108">Этот тип взгляда основан на направлении, в котором просматривается головной или камера.</span><span class="sxs-lookup"><span data-stu-id="0c90b-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="0c90b-109">Головной взгляд активен на системах, не поддерживающих глаз, или в случаях, когда оборудование может поддерживать глазный взгляд, но правильный набор [разрешений и настройки](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) не выполнялся.</span><span class="sxs-lookup"><span data-stu-id="0c90b-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="0c90b-110">головной взгляд, как правило, связан с взаимодействием в стиле HoloLens 1, включающим поиск объекта, поместив его в центре holographic-кадра, а затем выполняя жест касания воздуха.</span><span class="sxs-lookup"><span data-stu-id="0c90b-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="0c90b-111">Отслеживание глаз</span><span class="sxs-lookup"><span data-stu-id="0c90b-111">Eye gaze</span></span>

<span data-ttu-id="0c90b-112">Этот тип взгляда зависит от того, где ищутся глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="0c90b-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="0c90b-113">Взгляд на глаза имеется только в системах, поддерживающих отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="0c90b-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="0c90b-114">Дополнительные сведения об использовании глаз см. в [документации по отслеживанию взглядов](eye-tracking/eye-tracking-main.md) .</span><span class="sxs-lookup"><span data-stu-id="0c90b-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="0c90b-115">газепровидер</span><span class="sxs-lookup"><span data-stu-id="0c90b-115">GazeProvider</span></span>

<span data-ttu-id="0c90b-116">Функция взгляда («руководитель» и «глаз») предоставляется [газепровидер](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span><span class="sxs-lookup"><span data-stu-id="0c90b-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="0c90b-117">Этот поставщик можно настроить в разделе *указателя* входного системного профиля:</span><span class="sxs-lookup"><span data-stu-id="0c90b-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Взгляните на точку входа конфигурации](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="0c90b-119">Как и другие источники входных данных, поставщик взгляда взаимодействует с объектами в сцене с помощью указателя [(Дополнительные сведения об указателях см. в этом документе)](../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="0c90b-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="0c90b-120">В случае с поставщиком взгляд его указатель реализуется через `InternalGazePointer` и не настраивается с помощью профиля.</span><span class="sxs-lookup"><span data-stu-id="0c90b-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="0c90b-121">Можно заменить акцию Газепровидер другой реализацией, изменив *тип поставщика взгляда* на другой класс, реализующий [имикседреалитигазепровидер](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) и [имикседреалитеегазепровидер](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span><span class="sxs-lookup"><span data-stu-id="0c90b-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="0c90b-122">Обычно рекомендуется использовать Газепровидер на бирже (и при обнаружении ошибок), так как повторное внедрение Газепровидер не является тривиальной задачей.</span><span class="sxs-lookup"><span data-stu-id="0c90b-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="0c90b-123">Альтернативные предоставляемые платформой взгляды</span><span class="sxs-lookup"><span data-stu-id="0c90b-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="0c90b-124">По умолчанию МРТК Газепровидер использует центр кадра камеры в качестве источника взгляда.</span><span class="sxs-lookup"><span data-stu-id="0c90b-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="0c90b-125">некоторые платформы, например Windows Mixed Reality на HoloLens 2, предоставляют в качестве альтернативы определенный объект «взгляд».</span><span class="sxs-lookup"><span data-stu-id="0c90b-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="0c90b-126">Это осуществляется с помощью `Use Head Gaze Override` параметра в параметрах взгляда.</span><span class="sxs-lookup"><span data-stu-id="0c90b-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="0c90b-127">Если этот параметр включен, будет использоваться альтернативное переопределение взгляда.</span><span class="sxs-lookup"><span data-stu-id="0c90b-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="0c90b-128">Если этот параметр отключен, будет использоваться источник по умолчанию для центра кадров.</span><span class="sxs-lookup"><span data-stu-id="0c90b-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="0c90b-129">в частности, для HoloLens 2 угол взгляда будет выдаваться в несколько градусов, что позволит пользователю прилагаться к использованию их головного расположения.</span><span class="sxs-lookup"><span data-stu-id="0c90b-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="0c90b-130">Использование</span><span class="sxs-lookup"><span data-stu-id="0c90b-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="0c90b-131">Получение текущего целевого объекта взгляда</span><span class="sxs-lookup"><span data-stu-id="0c90b-131">How get the current gaze target</span></span>

<span data-ttu-id="0c90b-132">В этом примере показано, как получить текущий объект Game, который является целевым для пользователя.</span><span class="sxs-lookup"><span data-stu-id="0c90b-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="0c90b-133">Как получить текущее направление и источник взгляда</span><span class="sxs-lookup"><span data-stu-id="0c90b-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="0c90b-134">В этом примере показано, как получить Vector3, представляющую направление пользователя и источник (точку, из которой переходит направление).</span><span class="sxs-lookup"><span data-stu-id="0c90b-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
