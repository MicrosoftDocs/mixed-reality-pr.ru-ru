---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718144"
---
# <a name="426"></a>[<span data-ttu-id="62ccd-101">4.26</span><span class="sxs-lookup"><span data-stu-id="62ccd-101">4.26</span></span>](#tab/426)

<span data-ttu-id="62ccd-102">Иерархия описана в разделе `EHandKeypoint` enum:</span><span class="sxs-lookup"><span data-stu-id="62ccd-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Изображение параметров руки кэйпоинт хранится](../images/hand-keypoint-bp.png)

<span data-ttu-id="62ccd-104">Все эти данные можно получить из руки пользователя с помощью функции **получения данных контроллера движения** .</span><span class="sxs-lookup"><span data-stu-id="62ccd-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="62ccd-105">Эта функция возвращает структуру **ксрмотионконтроллердата** .</span><span class="sxs-lookup"><span data-stu-id="62ccd-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="62ccd-106">Ниже приведен пример скрипта схемы, который анализирует структуру Ксрмотионконтроллердата для получения Объединенных расположений и рисует отладочную систему координат в каждом расположении соединения.</span><span class="sxs-lookup"><span data-stu-id="62ccd-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Схема функции получения данных с данными о получении, подключенной к трассировке строки по функциям канала](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="62ccd-108">Важно проверить, является ли структура допустимой, и что она является рукой.</span><span class="sxs-lookup"><span data-stu-id="62ccd-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="62ccd-109">В противном случае вы можете получить неопределенное поведение в доступе к позициям, поворотам и массивам радиусов.</span><span class="sxs-lookup"><span data-stu-id="62ccd-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="62ccd-110">4.25</span><span class="sxs-lookup"><span data-stu-id="62ccd-110">4.25</span></span>](#tab/425)

<span data-ttu-id="62ccd-111">`EWMRHandKeypoint`Перечисление описывает иерархию костей руки.</span><span class="sxs-lookup"><span data-stu-id="62ccd-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="62ccd-112">Вы можете найти все руки кэйпоинт, перечисленные в ваших чертежах:</span><span class="sxs-lookup"><span data-stu-id="62ccd-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![Кэйпоинт BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="62ccd-114">Полное перечисление C++ показано ниже.</span><span class="sxs-lookup"><span data-stu-id="62ccd-114">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="62ccd-115">Числовые значения для каждого варианта перечисления можно найти в таблице [Windows. восприятие. People. ханджоинткинд](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="62ccd-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="62ccd-116">Поддержка отслеживания</span><span class="sxs-lookup"><span data-stu-id="62ccd-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="62ccd-117">Вы можете использовать отслеживание вручную в схемах, добавив **поддержку отслеживания вручную** для **отслеживания > Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="62ccd-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![BP для отслеживания](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="62ccd-119">Эта функция возвращает значение `true` , если отслеживание поддерживается на устройстве, и `false` Если отслеживание недоступно.</span><span class="sxs-lookup"><span data-stu-id="62ccd-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Поддерживает отправную очередь для отслеживания](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="62ccd-121">C++:</span><span class="sxs-lookup"><span data-stu-id="62ccd-121">C++:</span></span>

<span data-ttu-id="62ccd-122">Добавьте `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="62ccd-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="62ccd-123">Отслеживание отслеживания</span><span class="sxs-lookup"><span data-stu-id="62ccd-123">Getting Hand Tracking</span></span>

<span data-ttu-id="62ccd-124">**Жесанджоинттрансформ** можно использовать для возврата пространственных данных из руки.</span><span class="sxs-lookup"><span data-stu-id="62ccd-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="62ccd-125">Данные обновляются каждым кадром, но если вы находитесь внутри фрейма, возвращаемые значения кэшируются.</span><span class="sxs-lookup"><span data-stu-id="62ccd-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="62ccd-126">В этой функции не рекомендуется использовать интенсивную логику для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="62ccd-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Преобразование «получение соединения с рукой»](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="62ccd-128">C++:</span><span class="sxs-lookup"><span data-stu-id="62ccd-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="62ccd-129">Ниже приведена декомпозиция параметров функции Жесанджоинттрансформ:</span><span class="sxs-lookup"><span data-stu-id="62ccd-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="62ccd-130">**Рука** — может быть пользователем слева или справа.</span><span class="sxs-lookup"><span data-stu-id="62ccd-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="62ccd-131">**Кэйпоинт** — кость руки.</span><span class="sxs-lookup"><span data-stu-id="62ccd-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="62ccd-132">**Transform** — координаты и ориентация базы данных-основания кости.</span><span class="sxs-lookup"><span data-stu-id="62ccd-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="62ccd-133">Можно запросить основу следующей кости, чтобы получить данные преобразования для конца кости.</span><span class="sxs-lookup"><span data-stu-id="62ccd-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="62ccd-134">Специальная кость TIP дает окончание дистал.</span><span class="sxs-lookup"><span data-stu-id="62ccd-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="62ccd-135">\* \* Радиус — радиус основы кости.</span><span class="sxs-lookup"><span data-stu-id="62ccd-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="62ccd-136">\* \* Возвращаемое значение — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="62ccd-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

