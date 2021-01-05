---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717780"
---
# <a name="426"></a>[<span data-ttu-id="5db6b-101">4.26</span><span class="sxs-lookup"><span data-stu-id="5db6b-101">4.26</span></span>](#tab/426)

<span data-ttu-id="5db6b-102">Чтобы получить данные для луча, следует использовать функцию получения данных контроллера движения из предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="5db6b-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="5db6b-103">Возвращаемая структура содержит два параметра, которые можно использовать для создания руки луча — **нацеленности** и **ротации**.</span><span class="sxs-lookup"><span data-stu-id="5db6b-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="5db6b-104">Эти параметры формируют луч, направленный уступом.</span><span class="sxs-lookup"><span data-stu-id="5db6b-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="5db6b-105">Вы должны взять их и найти голограмму, на которую указывает.</span><span class="sxs-lookup"><span data-stu-id="5db6b-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="5db6b-106">Ниже приведен пример того, как определить, попадает ли рука-Ray в мини-приложение, и задать пользовательский результат попадания:</span><span class="sxs-lookup"><span data-stu-id="5db6b-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Схема функции получения данных контроллера движения](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="5db6b-108">4.25</span><span class="sxs-lookup"><span data-stu-id="5db6b-108">4.25</span></span>](#tab/425)

<span data-ttu-id="5db6b-109">Чтобы использовать лучи в схемах, выполните поиск любых действий в **Windows Mixed Reality ХМД**:</span><span class="sxs-lookup"><span data-stu-id="5db6b-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="5db6b-111">Чтобы получить доступ к ним в C++, включите `WindowsMixedRealityFunctionLibrary.h` в начало файла вызывающего кода.</span><span class="sxs-lookup"><span data-stu-id="5db6b-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="5db6b-112">Перечисление</span><span class="sxs-lookup"><span data-stu-id="5db6b-112">Enum</span></span>

<span data-ttu-id="5db6b-113">Кроме того, у вас есть доступ к входным вариантам в **ехмдинпутконтроллербуттонс**, которые можно использовать в схемах:</span><span class="sxs-lookup"><span data-stu-id="5db6b-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Кнопки контроллера ввода](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="5db6b-115">Для доступа в C++ используйте `EHMDInputControllerButtons` Класс Enum:</span><span class="sxs-lookup"><span data-stu-id="5db6b-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="5db6b-116">Ниже приведена разбивка двух применимых вариантов перечисления.</span><span class="sxs-lookup"><span data-stu-id="5db6b-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="5db6b-117">**SELECT** — пользователь активировал событие SELECT.</span><span class="sxs-lookup"><span data-stu-id="5db6b-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="5db6b-118">Активируется в HoloLens 2, выполняя касание, взгляните и зафиксировать, или выполнив команду "Select" с включенным [голосовым входом](../unreal-voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="5db6b-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="5db6b-119">Пользовательское событие **, активируемое с** учетом продачи.</span><span class="sxs-lookup"><span data-stu-id="5db6b-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="5db6b-120">Активируется в HoloLens 2, закрывая пальцы пользователя на голограмме.</span><span class="sxs-lookup"><span data-stu-id="5db6b-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="5db6b-121">Вы можете получить доступ к состоянию отслеживания сетки руки в C++ с помощью `EHMDTrackingStatus` перечисления, показанного ниже:</span><span class="sxs-lookup"><span data-stu-id="5db6b-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="5db6b-122">Ниже приведена разбивка двух применимых вариантов перечисления.</span><span class="sxs-lookup"><span data-stu-id="5db6b-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="5db6b-123">**Ноттраккед** — рука не отображается</span><span class="sxs-lookup"><span data-stu-id="5db6b-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="5db6b-124">С **отслеживанием** — рука полностью отслеживание</span><span class="sxs-lookup"><span data-stu-id="5db6b-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="5db6b-125">Структура</span><span class="sxs-lookup"><span data-stu-id="5db6b-125">Struct</span></span>

<span data-ttu-id="5db6b-126">Структура Поинтерпосеинфо может предоставить сведения о следующих данных:</span><span class="sxs-lookup"><span data-stu-id="5db6b-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="5db6b-127">**Источник** — источник руки</span><span class="sxs-lookup"><span data-stu-id="5db6b-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="5db6b-128">**Направление** — направление руки</span><span class="sxs-lookup"><span data-stu-id="5db6b-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="5db6b-129">**Вверх** — вверх в виде вектора руки</span><span class="sxs-lookup"><span data-stu-id="5db6b-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="5db6b-130">**Orientation** — ориентация кватерниона</span><span class="sxs-lookup"><span data-stu-id="5db6b-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="5db6b-131">**Состояние отслеживания** — текущее состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="5db6b-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="5db6b-132">Доступ к структуре Поинтерпосеинфо можно получить с помощью схем, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="5db6b-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![BP, сведения о указателе](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="5db6b-134">Или с + +:</span><span class="sxs-lookup"><span data-stu-id="5db6b-134">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="5db6b-135">Функции</span><span class="sxs-lookup"><span data-stu-id="5db6b-135">Functions</span></span>

<span data-ttu-id="5db6b-136">Все перечисленные ниже функции можно вызывать для каждого кадра, что позволяет выполнять непрерывный мониторинг.</span><span class="sxs-lookup"><span data-stu-id="5db6b-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="5db6b-137">**Получить сведения о выведении указателя** возвращает полные сведения о направлении ладони в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="5db6b-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="5db6b-138">Схем</span><span class="sxs-lookup"><span data-stu-id="5db6b-138">Blueprint:</span></span>

![Получить сведения о указателе](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="5db6b-140">C++:</span><span class="sxs-lookup"><span data-stu-id="5db6b-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="5db6b-141">Если рука проблюдается в текущем кадре, **будет** возвращено значение true.</span><span class="sxs-lookup"><span data-stu-id="5db6b-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="5db6b-142">Схем</span><span class="sxs-lookup"><span data-stu-id="5db6b-142">Blueprint:</span></span>

![Есть BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="5db6b-144">C++:</span><span class="sxs-lookup"><span data-stu-id="5db6b-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="5db6b-145">При **нажатии кнопки выбрать** возвращается значение true, если пользователь активировал выбор в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="5db6b-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="5db6b-146">Схем</span><span class="sxs-lookup"><span data-stu-id="5db6b-146">Blueprint:</span></span>

![Выбрана нажатая нажимаемая BP](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="5db6b-148">C++:</span><span class="sxs-lookup"><span data-stu-id="5db6b-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="5db6b-149">Нажата **кнопка "** возвращает значение true", если событие или кнопка активированы в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="5db6b-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="5db6b-150">Схем</span><span class="sxs-lookup"><span data-stu-id="5db6b-150">Blueprint:</span></span>

![Нажата кнопка BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="5db6b-152">C++:</span><span class="sxs-lookup"><span data-stu-id="5db6b-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="5db6b-153">**Получение состояния отслеживания контроллера** возвращает состояние отслеживания в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="5db6b-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="5db6b-154">Схем</span><span class="sxs-lookup"><span data-stu-id="5db6b-154">Blueprint:</span></span>

![Получить состояние отслежения контроллера](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="5db6b-156">C++:</span><span class="sxs-lookup"><span data-stu-id="5db6b-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```