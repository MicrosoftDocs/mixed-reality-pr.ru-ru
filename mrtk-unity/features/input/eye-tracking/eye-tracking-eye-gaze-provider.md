---
title: Отслеживание взгляда — поставщик данных о направлении взгляда
description: Документация для поставщика взгляда на глаза в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг, Эйегазе,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144025"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="c8c59-104">Доступ к данным отслеживания взгляда в скрипте Unity</span><span class="sxs-lookup"><span data-stu-id="c8c59-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="c8c59-105">В этой статье предполагается, что у одной из них есть основные сведения о настройке отслеживания взглядов в МРТК сцене (см. раздел [Базовая настройка мртк для использования отслеживания глаз](eye-tracking-basic-setup.md)).</span><span class="sxs-lookup"><span data-stu-id="c8c59-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="c8c59-106">Доступ к данным отслеживания взгляда в скрипте с несложным поведением очень прост!</span><span class="sxs-lookup"><span data-stu-id="c8c59-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="c8c59-107">Просто используйте *коресервицес. инпутсистем. эйегазепровидер*.</span><span class="sxs-lookup"><span data-stu-id="c8c59-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="c8c59-108">имикседреалитеегазепровидер</span><span class="sxs-lookup"><span data-stu-id="c8c59-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="c8c59-109">Конфигурация отслеживания взгляда в МРТК настраивается через [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c8c59-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="c8c59-110">Использование [коресервицес. инпутсистем. эйегазепровидер](eye-tracking-eye-gaze-provider.md) предоставляет реализацию поставщика взгляда по умолчанию, зарегистрированную в наборе средств во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c8c59-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="c8c59-111">Ниже приведено описание полезных свойств `EyeGazeProvider` .</span><span class="sxs-lookup"><span data-stu-id="c8c59-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="c8c59-112">**Исэйетраккинженаблед**: true, если пользователь выбрал отслеживание взгляда для взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="c8c59-113">**Исэйекалибратионвалид**: указывает, является ли калибровка отслеживания взгляда пользователя допустимой.</span><span class="sxs-lookup"><span data-stu-id="c8c59-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="c8c59-114">Он возвращает значение null, если данные еще не получены из системы отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="c8c59-115">Возможно, она недопустима, так как пользователь пропустил калибровку отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="c8c59-116">**Исэйетраккинженабледандвалид**: указывает, используются ли текущие данные отслеживания взгляда в настоящее время для взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="c8c59-117">**Исэйетраккингдатавалид**: true, если доступны данные отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="c8c59-118">Он может быть недоступен из-за превышения времени ожидания (должен быть надежным для пользователя, который мигает) или отсутствия оборудования или разрешений для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="c8c59-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="c8c59-119">Ознакомьтесь с [примером уведомления об](eye-tracking-is-user-calibrated.md) устранении незамеченных глаз, в котором объясняется, как определить, откалиброван ли пользователь, и отобразить соответствующее уведомление.</span><span class="sxs-lookup"><span data-stu-id="c8c59-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="c8c59-120">**Газеоригин**: источник взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="c8c59-121">Обратите внимание, что при значении "Исэйегазевалид *" в качестве* значения false будет возвращен начальный источник взгляда.</span><span class="sxs-lookup"><span data-stu-id="c8c59-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="c8c59-122">**Газедиректион**: направление луча.</span><span class="sxs-lookup"><span data-stu-id="c8c59-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="c8c59-123">Если значение "Исэйегазевалид" равно false, будет возвращено направление взгляда на *заголовок* .</span><span class="sxs-lookup"><span data-stu-id="c8c59-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="c8c59-124">**Хитинфо**, **хитпоситион**, **хитнормал** и т. д. — сведения о текущем газед в целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="c8c59-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="c8c59-125">Опять же, если `IsEyeGazeValid` имеет значение false, это будет основано на *голове* пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8c59-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="c8c59-126">Примеры использования Коресервицес. Инпутсистем. Эйегазепровидер</span><span class="sxs-lookup"><span data-stu-id="c8c59-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="c8c59-127">Ниже приведен пример из [фолловэйегазе. CS](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span><span class="sxs-lookup"><span data-stu-id="c8c59-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="c8c59-128">Получить точку голограммы, которую пользователь просматривает:</span><span class="sxs-lookup"><span data-stu-id="c8c59-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="c8c59-129">Отображение визуального ресурса с фиксированным расстоянием от места, где пользователь находится в данный момент:</span><span class="sxs-lookup"><span data-stu-id="c8c59-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="c8c59-130">См. также</span><span class="sxs-lookup"><span data-stu-id="c8c59-130">See also</span></span>

- [<span data-ttu-id="c8c59-131">Общие сведения об отслеживании МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="c8c59-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="c8c59-132">Настройка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="c8c59-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="c8c59-133">Калибровка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="c8c59-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="c8c59-134">Документация по отслеживания взгляда HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c8c59-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)