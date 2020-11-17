---
title: Отслеживание рук в Unreal
description: Объясняется, как использовать отслеживание вручную в нереальных
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, отслеживание, неreal, нереалное ядро 4, UE4, HoloLens, HoloLens 2, Смешанная реальность, разработка, функции, документация, руководства, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 0a16a0291261277cb09e736e60b25f8ba71382e3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679213"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="8a138-104">Отслеживание рук в Unreal</span><span class="sxs-lookup"><span data-stu-id="8a138-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="8a138-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="8a138-105">Overview</span></span>

<span data-ttu-id="8a138-106">Система отслеживания руки в качестве входных данных использует Палмс и пальцы человека.</span><span class="sxs-lookup"><span data-stu-id="8a138-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="8a138-107">Вы можете получить расположение и поворот каждого пальца, всего карманного компьютера и даже руки, которые будут использоваться в коде.</span><span class="sxs-lookup"><span data-stu-id="8a138-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="8a138-108">Рука</span><span class="sxs-lookup"><span data-stu-id="8a138-108">Hand Pose</span></span>

<span data-ttu-id="8a138-109">Рука руки позволяет отслеживанию руки и пальцы активного пользователя и использовать его в качестве входных данных, доступ к которым можно получить с помощью схем и C++.</span><span class="sxs-lookup"><span data-stu-id="8a138-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="8a138-110">Дополнительные технические сведения можно найти в API [Windows. восприятие. People. хандпосе](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) .</span><span class="sxs-lookup"><span data-stu-id="8a138-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="8a138-111">Нереалный API отправляет данные в виде системы координат с тактами, синхронизированными с нереальным механизмом.</span><span class="sxs-lookup"><span data-stu-id="8a138-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="8a138-112">Основные сведения об иерархии костей</span><span class="sxs-lookup"><span data-stu-id="8a138-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="8a138-113">`EWMRHandKeypoint`Перечисление описывает иерархию костей руки.</span><span class="sxs-lookup"><span data-stu-id="8a138-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="8a138-114">Вы можете найти все руки кэйпоинт, перечисленные в ваших чертежах:</span><span class="sxs-lookup"><span data-stu-id="8a138-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![Кэйпоинт BP](images/hand-keypoint-bp.png)

<span data-ttu-id="8a138-116">Полное перечисление C++ показано ниже.</span><span class="sxs-lookup"><span data-stu-id="8a138-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="8a138-117">Числовые значения для каждого варианта перечисления можно найти в таблице [Windows. восприятие. People. ханджоинткинд](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="8a138-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="8a138-118">На рисунке ниже показана вся схема оформления руки с соответствующими вариантами перечисления.</span><span class="sxs-lookup"><span data-stu-id="8a138-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Схема руки](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="8a138-120">Поддержка отслеживания</span><span class="sxs-lookup"><span data-stu-id="8a138-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="8a138-121">Вы можете использовать отслеживание вручную в схемах, добавив **поддержку отслеживания вручную** для **отслеживания > Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="8a138-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![BP для отслеживания](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="8a138-123">Эта функция возвращает значение `true` , если отслеживание поддерживается на устройстве и `false` Если отслеживание недоступно.</span><span class="sxs-lookup"><span data-stu-id="8a138-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![Поддерживает отправную очередь для отслеживания](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="8a138-125">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-125">C++:</span></span> 

<span data-ttu-id="8a138-126">Добавьте `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="8a138-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="8a138-127">Отслеживание отслеживания</span><span class="sxs-lookup"><span data-stu-id="8a138-127">Getting Hand Tracking</span></span>
<span data-ttu-id="8a138-128">**Жесанджоинттрансформ** можно использовать для возврата пространственных данных из руки.</span><span class="sxs-lookup"><span data-stu-id="8a138-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="8a138-129">Данные обновляются каждым кадром, но если вы находитесь внутри фрейма, возвращаемые значения кэшируются.</span><span class="sxs-lookup"><span data-stu-id="8a138-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="8a138-130">В этой функции не рекомендуется использовать интенсивную логику для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="8a138-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Преобразование «получение соединения с рукой»](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="8a138-132">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="8a138-133">Разбиение параметров функции:</span><span class="sxs-lookup"><span data-stu-id="8a138-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="8a138-134">**Рука** — левая или правая рука пользователя</span><span class="sxs-lookup"><span data-stu-id="8a138-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="8a138-135">**Кэйпоинт** — кость руки.</span><span class="sxs-lookup"><span data-stu-id="8a138-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="8a138-136">**Transform** — координаты и ориентация базы данных-основания кости.</span><span class="sxs-lookup"><span data-stu-id="8a138-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="8a138-137">Можно запросить основу следующей кости, чтобы получить данные преобразования для конца кости.</span><span class="sxs-lookup"><span data-stu-id="8a138-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="8a138-138">Специальная кость TIP дает окончание дистал.</span><span class="sxs-lookup"><span data-stu-id="8a138-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="8a138-139">**Радиус** — радиус базовой части кости.</span><span class="sxs-lookup"><span data-stu-id="8a138-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="8a138-140">**Возвращаемое значение** — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="8a138-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="8a138-141">Анимация прямой связи</span><span class="sxs-lookup"><span data-stu-id="8a138-141">Hand Live Link Animation</span></span>
<span data-ttu-id="8a138-142">Руки, доступные для анимации, используют [подключаемый модуль динамической компоновки](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="8a138-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="8a138-143">Если включены подключаемые модули Windows Mixed Reality и Live links:</span><span class="sxs-lookup"><span data-stu-id="8a138-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="8a138-144">Выберите **окно > активная ссылка** , чтобы открыть окно редактора динамической связи.</span><span class="sxs-lookup"><span data-stu-id="8a138-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="8a138-145">Щелкните **источник** и включите **источник отслеживания Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="8a138-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Источник прямой связи](images/unreal/live-link-source.png)
 
<span data-ttu-id="8a138-147">После включения источника и открытия ресурса анимации раскройте раздел " **анимация** " на вкладке " **Предварительный просмотр** ". Дополнительные параметры см. в документации по нереальному каналу. так как подключаемый модуль находится в бета-версии, этот процесс может измениться позже.</span><span class="sxs-lookup"><span data-stu-id="8a138-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![Динамическая анимация ссылки](images/unreal/live-link-animation.png)
 
<span data-ttu-id="8a138-149">Иерархия анимации руки такая же, как и в `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="8a138-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="8a138-150">Анимацию можно перенацелить с помощью **виндовсмикседреалитихандтраккингливелинкремапассет**:</span><span class="sxs-lookup"><span data-stu-id="8a138-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Анимация прямой связи 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="8a138-152">Он также может быть подклассом в редакторе:</span><span class="sxs-lookup"><span data-stu-id="8a138-152">It can also be subclassed in the editor:</span></span>

![Сопоставление активных ссылок](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="8a138-154">Доступ к данным сетки</span><span class="sxs-lookup"><span data-stu-id="8a138-154">Accessing Hand Mesh Data</span></span>

![Сетка руки](images/unreal/hand-mesh.png)

<span data-ttu-id="8a138-156">Прежде чем можно будет получить доступ к данным сетки данных, необходимо:</span><span class="sxs-lookup"><span data-stu-id="8a138-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="8a138-157">Выберите свой ресурс **арсессионконфиг** , разверните параметры **AR Settings-> мирового сопоставления** и установите флажок **создать данные сетки из отслеживающей геометрии**.</span><span class="sxs-lookup"><span data-stu-id="8a138-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="8a138-158">Ниже приведены параметры сетки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8a138-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="8a138-159">Использование данных сетки для перекрытия</span><span class="sxs-lookup"><span data-stu-id="8a138-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="8a138-160">Создать конфликт для данных сетки</span><span class="sxs-lookup"><span data-stu-id="8a138-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="8a138-161">Создать сетку навигации для данных сетки</span><span class="sxs-lookup"><span data-stu-id="8a138-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="8a138-162">Отображение данных сетки в каркасе — параметр отладки, показывающий созданную сетку</span><span class="sxs-lookup"><span data-stu-id="8a138-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="8a138-163">Эти значения параметров используются в качестве сетки пространственного сопоставления и по умолчанию для сетки.</span><span class="sxs-lookup"><span data-stu-id="8a138-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="8a138-164">Их можно изменить в любой момент в проекте или коде для любой сетки.</span><span class="sxs-lookup"><span data-stu-id="8a138-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="8a138-165">Справочник по API C++</span><span class="sxs-lookup"><span data-stu-id="8a138-165">C++ API Reference</span></span> 
<span data-ttu-id="8a138-166">Используется `EEARObjectClassification` для поиска значений сетки в объектах, доступных для наблюдения.</span><span class="sxs-lookup"><span data-stu-id="8a138-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="8a138-167">Следующие делегаты вызываются, когда система обнаруживает любой отслеживающий объект, включая сетку типа "рука".</span><span class="sxs-lookup"><span data-stu-id="8a138-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="8a138-168">Убедитесь, что обработчики делегатов следуют сигнатуре функции ниже:</span><span class="sxs-lookup"><span data-stu-id="8a138-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="8a138-169">Доступ к данным сетки можно получить с помощью  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="8a138-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="8a138-170">Справочник по API-интерфейсам схем</span><span class="sxs-lookup"><span data-stu-id="8a138-170">Blueprint API Reference</span></span>

<span data-ttu-id="8a138-171">Для работы с сетчатыми сетками в схемах:</span><span class="sxs-lookup"><span data-stu-id="8a138-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="8a138-172">Добавление компонента **артраккабленотифи** в проект схемы</span><span class="sxs-lookup"><span data-stu-id="8a138-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Уведомление Артраккабле](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="8a138-174">Перейдите на панель **сведений** и разверните раздел **события** .</span><span class="sxs-lookup"><span data-stu-id="8a138-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![Артраккабле уведомление 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="8a138-176">Перезаписать для добавления, обновления или удаления отслеживаний геометрии со следующими узлами в графе событий:</span><span class="sxs-lookup"><span data-stu-id="8a138-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Уведомление Артраккабле](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="8a138-178">Лучи с рукой</span><span class="sxs-lookup"><span data-stu-id="8a138-178">Hand Rays</span></span>

<span data-ttu-id="8a138-179">Можно использовать входной луч в качестве указывающего устройства как в C++, так и в чертежах, которые предоставляют API [Windows. UI. input. spatial. спатиалпоинтеринтерактионсаурцепосе](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .</span><span class="sxs-lookup"><span data-stu-id="8a138-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="8a138-180">Важно упомянуть, что поскольку результаты всех функций изменяют каждый кадр, все они становятся вызываемыми.</span><span class="sxs-lookup"><span data-stu-id="8a138-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="8a138-181">Дополнительные сведения о чистом и нечистом или вызываемых функциях см. в статье GUID пользователя в [функциях](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) .</span><span class="sxs-lookup"><span data-stu-id="8a138-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="8a138-182">Чтобы использовать лучи в схемах, выполните поиск любых действий в **Windows Mixed Reality ХМД**:</span><span class="sxs-lookup"><span data-stu-id="8a138-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="8a138-184">Чтобы получить доступ к ним в C++, включите `WindowsMixedRealityFunctionLibrary.h` в начало файла вызывающего кода.</span><span class="sxs-lookup"><span data-stu-id="8a138-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="8a138-185">Перечисление</span><span class="sxs-lookup"><span data-stu-id="8a138-185">Enum</span></span>
<span data-ttu-id="8a138-186">Кроме того, у вас есть доступ к входным вариантам в **ехмдинпутконтроллербуттонс**, которые можно использовать в схемах:</span><span class="sxs-lookup"><span data-stu-id="8a138-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Кнопки контроллера ввода](images/unreal/input-controller-buttons.png)

<span data-ttu-id="8a138-188">Для доступа в C++ используйте `EHMDInputControllerButtons` Класс Enum:</span><span class="sxs-lookup"><span data-stu-id="8a138-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="8a138-189">Ниже приведена разбивка двух применимых вариантов перечисления.</span><span class="sxs-lookup"><span data-stu-id="8a138-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="8a138-190">**SELECT** — пользователь активировал событие SELECT.</span><span class="sxs-lookup"><span data-stu-id="8a138-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="8a138-191">Событие можно активировать в HoloLens 2, выполнив касание, взгляните и зафиксировать, или выполнив команду "Select" с включенным [голосовым входом](unreal-voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="8a138-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="8a138-192">Пользовательское событие **, активируемое с** учетом продачи.</span><span class="sxs-lookup"><span data-stu-id="8a138-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="8a138-193">Это событие может быть активировано в HoloLens 2 путем закрытия пальцев пользователя на голограмме.</span><span class="sxs-lookup"><span data-stu-id="8a138-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="8a138-194">Вы можете получить доступ к состоянию отслеживания сетки руки в C++ с помощью `EHMDTrackingStatus` перечисления, показанного ниже:</span><span class="sxs-lookup"><span data-stu-id="8a138-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="8a138-195">Ниже приведена разбивка двух применимых вариантов перечисления.</span><span class="sxs-lookup"><span data-stu-id="8a138-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="8a138-196">**Ноттраккед** — рука не отображается</span><span class="sxs-lookup"><span data-stu-id="8a138-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="8a138-197">С **отслеживанием** — рука полностью отслеживание</span><span class="sxs-lookup"><span data-stu-id="8a138-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="8a138-198">Структура</span><span class="sxs-lookup"><span data-stu-id="8a138-198">Struct</span></span>
<span data-ttu-id="8a138-199">Структура Поинтерпосеинфо может предоставить сведения о следующих данных:</span><span class="sxs-lookup"><span data-stu-id="8a138-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="8a138-200">**Источник** — источник руки</span><span class="sxs-lookup"><span data-stu-id="8a138-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="8a138-201">**Направление** — направление руки</span><span class="sxs-lookup"><span data-stu-id="8a138-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="8a138-202">**Вверх** — вверх в виде вектора руки</span><span class="sxs-lookup"><span data-stu-id="8a138-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="8a138-203">**Orientation** — ориентация кватерниона</span><span class="sxs-lookup"><span data-stu-id="8a138-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="8a138-204">**Состояние отслеживания** — текущее состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="8a138-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="8a138-205">Доступ к нему можно получить с помощью схем, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="8a138-205">You can access this through Blueprints, as shown below:</span></span>

![BP, сведения о указателе](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="8a138-207">Или с + +:</span><span class="sxs-lookup"><span data-stu-id="8a138-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="8a138-208">Функции</span><span class="sxs-lookup"><span data-stu-id="8a138-208">Functions</span></span>

<span data-ttu-id="8a138-209">Все перечисленные ниже функции можно вызывать для каждого кадра, что позволяет выполнять непрерывный мониторинг.</span><span class="sxs-lookup"><span data-stu-id="8a138-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="8a138-210">**Получить сведения о выведении указателя** возвращает полные сведения о направлении ладони в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="8a138-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="8a138-211">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-211">Blueprint:</span></span>

![Получить сведения о указателе](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="8a138-213">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="8a138-214">Если рука проблюдается в текущем кадре, **будет** возвращено значение true.</span><span class="sxs-lookup"><span data-stu-id="8a138-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="8a138-215">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-215">Blueprint:</span></span>

![Есть BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="8a138-217">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="8a138-218">При **нажатии кнопки выбрать** возвращается значение true, если пользователь активировал выбор в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="8a138-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="8a138-219">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-219">Blueprint:</span></span>

![Выбрана нажатая нажимаемая BP](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="8a138-221">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="8a138-222">Нажата **кнопка "** возвращает значение true", если событие или кнопка активированы в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="8a138-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="8a138-223">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-223">Blueprint:</span></span>

![Нажата кнопка BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="8a138-225">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="8a138-226">**Получение состояния отслеживания контроллера** возвращает состояние отслеживания в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="8a138-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="8a138-227">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-227">Blueprint:</span></span>

![Получить состояние отслежения контроллера](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="8a138-229">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="8a138-230">Жесты</span><span class="sxs-lookup"><span data-stu-id="8a138-230">Gestures</span></span>

<span data-ttu-id="8a138-231">Hololens 2 может отслеживать пространственные жесты, что означает возможность захвата этих жестов в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="8a138-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="8a138-232">Дополнительные сведения о жестах можно найти в документе [об использовании HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="8a138-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="8a138-233">Функцию схемы можно найти в разделе **пространственный ввод Windows Mixed Reality**, а функция C++ — путем добавления `WindowsMixedRealitySpatialInputFunctionLibrary.h` в файл вызывающего кода.</span><span class="sxs-lookup"><span data-stu-id="8a138-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Жесты записи](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="8a138-235">Перечисление</span><span class="sxs-lookup"><span data-stu-id="8a138-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="8a138-236">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-236">Blueprint:</span></span> 

![Тип жеста](images/unreal/gesture-type.png)

<span data-ttu-id="8a138-238">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="8a138-239">Компонент</span><span class="sxs-lookup"><span data-stu-id="8a138-239">Function</span></span>
<span data-ttu-id="8a138-240">Включить и отключить захват жестов можно с помощью `CaptureGestures` функции.</span><span class="sxs-lookup"><span data-stu-id="8a138-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="8a138-241">Когда включенный жест запускает входные события, функция возвращает значение, `true` Если захват жеста завершается удачно, и `false` при наличии ошибки.</span><span class="sxs-lookup"><span data-stu-id="8a138-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="8a138-242">Схем</span><span class="sxs-lookup"><span data-stu-id="8a138-242">Blueprint:</span></span>

![Точка применения жестов захвата](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="8a138-244">C++:</span><span class="sxs-lookup"><span data-stu-id="8a138-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="8a138-245">Ниже приведены ключевые события, которые можно найти в чертежах и C++: ключевые события. ![](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="8a138-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Ключевые события 2](images/unreal/key-events2.png)
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

## <a name="next-development-checkpoint"></a><span data-ttu-id="8a138-247">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="8a138-247">Next Development Checkpoint</span></span>

<span data-ttu-id="8a138-248">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="8a138-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8a138-249">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="8a138-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="8a138-250">Локальные пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="8a138-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="8a138-251">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="8a138-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8a138-252">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="8a138-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="8a138-253">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="8a138-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>