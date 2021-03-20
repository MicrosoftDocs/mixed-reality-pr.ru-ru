---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719844"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="990ae-101">Unity 2020 + Опенкср</span><span class="sxs-lookup"><span data-stu-id="990ae-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="990ae-102">Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity.</span><span class="sxs-lookup"><span data-stu-id="990ae-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="990ae-103">Основные сведения о Аранчорс в Арфаундатион см. в руководстве по [арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="990ae-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="990ae-104">Подключаемый модуль XR для Unity 2019/2020 + Windows</span><span class="sxs-lookup"><span data-stu-id="990ae-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="990ae-105">Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity.</span><span class="sxs-lookup"><span data-stu-id="990ae-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="990ae-106">Основные сведения о Аранчорс в Арфаундатион см. в руководстве по [арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="990ae-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="990ae-107">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="990ae-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="990ae-108">Создание возможностей для мирового масштабирования</span><span class="sxs-lookup"><span data-stu-id="990ae-108">Building a world-scale experience</span></span>

<span data-ttu-id="990ae-109">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="990ae-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="990ae-110">**Тип:** *ворлданчор*</span><span class="sxs-lookup"><span data-stu-id="990ae-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="990ae-111">Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты.</span><span class="sxs-lookup"><span data-stu-id="990ae-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="990ae-112">Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](../../../design/coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="990ae-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="990ae-113">В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.</span><span class="sxs-lookup"><span data-stu-id="990ae-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="990ae-114">Добавление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="990ae-114">Adding a World Anchor</span></span>

<span data-ttu-id="990ae-115">Чтобы добавить привязку по всему миру, вызовите `AddComponent<WorldAnchor>()` объект Game с преобразованием, которое необходимо привязать в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="990ae-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="990ae-116">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="990ae-116">That's it!</span></span> <span data-ttu-id="990ae-117">Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="990ae-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="990ae-118">Сведения о том, как закрепить это закрепленное расположение в следующем сеансе приложения, см. в статье [Загрузка универсальной привязки](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="990ae-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="990ae-119">Удаление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="990ae-119">Removing a World Anchor</span></span>

<span data-ttu-id="990ae-120">Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».</span><span class="sxs-lookup"><span data-stu-id="990ae-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="990ae-121">Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.</span><span class="sxs-lookup"><span data-stu-id="990ae-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="990ae-122">Перемещение привязанного GameObject по всему миру</span><span class="sxs-lookup"><span data-stu-id="990ae-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="990ae-123">GameObject нельзя переместить, пока на нем есть универсальная привязка.</span><span class="sxs-lookup"><span data-stu-id="990ae-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="990ae-124">Если вам нужно переместить GameObject этот кадр, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="990ae-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="990ae-125">Дестройиммедиате компонент «мировая привязка»</span><span class="sxs-lookup"><span data-stu-id="990ae-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="990ae-126">Перемещение GameObject</span><span class="sxs-lookup"><span data-stu-id="990ae-126">Move the GameObject</span></span>
3. <span data-ttu-id="990ae-127">Добавьте новый компонент универсальной привязки к GameObject.</span><span class="sxs-lookup"><span data-stu-id="990ae-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="990ae-128">Обработка изменений Локатабилити</span><span class="sxs-lookup"><span data-stu-id="990ae-128">Handling Locatability Changes</span></span>

<span data-ttu-id="990ae-129">Ворлданчор не может быть размещаемые в физическом мире на момент времени.</span><span class="sxs-lookup"><span data-stu-id="990ae-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="990ae-130">В таком случае Unity не будет обновлять преобразование привязанного объекта.</span><span class="sxs-lookup"><span data-stu-id="990ae-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="990ae-131">Это также можно изменить во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="990ae-131">This also can change while an app is running.</span></span> <span data-ttu-id="990ae-132">Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.</span><span class="sxs-lookup"><span data-stu-id="990ae-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="990ae-133">Чтобы получать уведомления об изменениях локатабилити:</span><span class="sxs-lookup"><span data-stu-id="990ae-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="990ae-134">Подпишитесь на событие Онтраккингчанжед</span><span class="sxs-lookup"><span data-stu-id="990ae-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="990ae-135">Обработайте событие</span><span class="sxs-lookup"><span data-stu-id="990ae-135">Handle the event</span></span>

<span data-ttu-id="990ae-136">Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.</span><span class="sxs-lookup"><span data-stu-id="990ae-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="990ae-137">Затем обработайте событие:</span><span class="sxs-lookup"><span data-stu-id="990ae-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="990ae-138">Иногда привязки размещаются немедленно.</span><span class="sxs-lookup"><span data-stu-id="990ae-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="990ae-139">В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent <WorldAnchor> () возвращает.</span><span class="sxs-lookup"><span data-stu-id="990ae-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="990ae-140">В результате событие Онтраккингчанжед не будет запущено.</span><span class="sxs-lookup"><span data-stu-id="990ae-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="990ae-141">Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.</span><span class="sxs-lookup"><span data-stu-id="990ae-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```