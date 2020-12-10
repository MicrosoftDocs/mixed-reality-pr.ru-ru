---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002705"
---
# <a name="425"></a>[<span data-ttu-id="a03f1-101">4.25</span><span class="sxs-lookup"><span data-stu-id="a03f1-101">4.25</span></span>](#tab/425)

<span data-ttu-id="a03f1-102">Функцию схемы можно найти в разделе **пространственный ввод Windows Mixed Reality**, а функция C++ — путем добавления `WindowsMixedRealitySpatialInputFunctionLibrary.h` в файл вызывающего кода.</span><span class="sxs-lookup"><span data-stu-id="a03f1-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Жесты записи](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="a03f1-104">Перечисление</span><span class="sxs-lookup"><span data-stu-id="a03f1-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="a03f1-105">Схем</span><span class="sxs-lookup"><span data-stu-id="a03f1-105">Blueprint:</span></span>

![Тип жеста](../images/unreal/gesture-type.png)

<span data-ttu-id="a03f1-107">C++:</span><span class="sxs-lookup"><span data-stu-id="a03f1-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="a03f1-108">Функция</span><span class="sxs-lookup"><span data-stu-id="a03f1-108">Function</span></span>
<span data-ttu-id="a03f1-109">Включить и отключить захват жестов можно с помощью `CaptureGestures` функции.</span><span class="sxs-lookup"><span data-stu-id="a03f1-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="a03f1-110">Когда включенный жест запускает входные события, функция возвращает значение, `true` Если захват жеста завершается удачно, и `false` при наличии ошибки.</span><span class="sxs-lookup"><span data-stu-id="a03f1-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="a03f1-111">Схем</span><span class="sxs-lookup"><span data-stu-id="a03f1-111">Blueprint:</span></span>

![Точка применения жестов захвата](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="a03f1-113">C++:</span><span class="sxs-lookup"><span data-stu-id="a03f1-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="a03f1-114">Ниже приведены ключевые события, которые можно найти в чертежах и C++: ключевые события. ![](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="a03f1-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![Ключевые события 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

# <a name="426"></a>[<span data-ttu-id="a03f1-116">4.26</span><span class="sxs-lookup"><span data-stu-id="a03f1-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="a03f1-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a03f1-117">Windows Mixed Reality</span></span>

![План начала воспроизведения, подключенный к функции настройки жестов](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="a03f1-119">Затем следует добавить код для подписки на следующие события:</span><span class="sxs-lookup"><span data-stu-id="a03f1-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="a03f1-120">![Снимок экрана с графическими жестами для сохранения данных на пространственном входе ](../images/unreal/key-events.png)
 ![ в Windows](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="a03f1-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="a03f1-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a03f1-121">OpenXR</span></span>

<span data-ttu-id="a03f1-122">В Опенкср события жестов отправляются через входной конвейер.</span><span class="sxs-lookup"><span data-stu-id="a03f1-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="a03f1-123">Используя взаимодействие с руки, устройство может автоматически распознать жесты касания и удерживания, но не другие.</span><span class="sxs-lookup"><span data-stu-id="a03f1-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="a03f1-124">Они именуются в виде Опенксрмсфсандинтерактион выбора и сопоставлений с захватом.</span><span class="sxs-lookup"><span data-stu-id="a03f1-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="a03f1-125">Вам не нужно включать подписку, вы должны объявить события в параметрах проекта/подсистеме/входе, как в следующем:</span><span class="sxs-lookup"><span data-stu-id="a03f1-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Снимок экрана с сопоставлениями действий Опенкср](../images/unreal-hand-tracking-img-12.png)
