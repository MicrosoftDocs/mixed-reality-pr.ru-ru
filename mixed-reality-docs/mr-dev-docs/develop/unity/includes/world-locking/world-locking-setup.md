---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528801"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="16043-101">Средства блокировки по всему миру (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="16043-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="16043-102">Мы рекомендуем установить средства блокировки мирового уровня с помощью нового средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="16043-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="16043-103">После скачивания средства "функция смешанной реальности" из приведенной ниже ссылки выберите последнюю версию **ВЛТ Core** в разделе **средства блокировки мира** :</span><span class="sxs-lookup"><span data-stu-id="16043-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Окно выбора компонентов средства смешанной реальности с выбранными инструментами блокировки мира](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="16043-105">Установка средств блокировки мира с помощью инструмента «MR»</span><span class="sxs-lookup"><span data-stu-id="16043-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="16043-106">Автоматическая установка</span><span class="sxs-lookup"><span data-stu-id="16043-106">Automated setup</span></span>

<span data-ttu-id="16043-107">Когда проект будет готов к работе, запустите программу настройки сцены из **набора средств смешанной реальности > служебные программы > средства блокировки мира**:</span><span class="sxs-lookup"><span data-stu-id="16043-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Редактор Unity с выбранным меню набора средств для смешанной реальности](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="16043-109">Программу настройки сцены можно повторно запустить в любое время.</span><span class="sxs-lookup"><span data-stu-id="16043-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="16043-110">Например, его следует перезапустить, если целевой объект AR был изменен с Legacy на XR SDK.</span><span class="sxs-lookup"><span data-stu-id="16043-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="16043-111">Если сцена уже настроена правильно, запуск программы не оказывает никакого влияния.</span><span class="sxs-lookup"><span data-stu-id="16043-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="16043-112">Визуализаторы</span><span class="sxs-lookup"><span data-stu-id="16043-112">Visualizers</span></span>

<span data-ttu-id="16043-113">Во время разработки на ранних этапах Добавление визуализаторов может быть полезным для того, чтобы ВЛТ был настроен и работал правильно.</span><span class="sxs-lookup"><span data-stu-id="16043-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="16043-114">Они могут быть удалены для повышения производительности, или если по какой бы то ни было причине больше не требуется, с помощью служебной программы Remove визуализаторы.</span><span class="sxs-lookup"><span data-stu-id="16043-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="16043-115">Дополнительные сведения о визуализаторах можно найти в [документации по средствам](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span><span class="sxs-lookup"><span data-stu-id="16043-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="16043-116">аранчорманажер</span><span class="sxs-lookup"><span data-stu-id="16043-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="16043-117">Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity.</span><span class="sxs-lookup"><span data-stu-id="16043-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="16043-118">Основные сведения о Аранчорс в Арфаундатион см. в руководстве по [арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="16043-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="16043-119">ворлданчор</span><span class="sxs-lookup"><span data-stu-id="16043-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="16043-120">Создание возможностей для мирового масштабирования</span><span class="sxs-lookup"><span data-stu-id="16043-120">Building a world-scale experience</span></span>

<span data-ttu-id="16043-121">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="16043-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="16043-122">**Тип:** *ворлданчор*</span><span class="sxs-lookup"><span data-stu-id="16043-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="16043-123">Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты.</span><span class="sxs-lookup"><span data-stu-id="16043-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="16043-124">Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](../../../../design/coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="16043-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="16043-125">В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.</span><span class="sxs-lookup"><span data-stu-id="16043-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="16043-126">Добавление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="16043-126">Adding a World Anchor</span></span>

<span data-ttu-id="16043-127">Чтобы добавить привязку по всему миру, вызовите `AddComponent<WorldAnchor>()` объект Game с преобразованием, которое необходимо привязать в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="16043-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="16043-128">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="16043-128">That's it!</span></span> <span data-ttu-id="16043-129">Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="16043-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="16043-130">Сведения о том, как закрепить это закрепленное расположение в следующем сеансе приложения, см. в статье [Загрузка универсальной привязки](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="16043-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="16043-131">Удаление универсальной привязки</span><span class="sxs-lookup"><span data-stu-id="16043-131">Removing a World Anchor</span></span>

<span data-ttu-id="16043-132">Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».</span><span class="sxs-lookup"><span data-stu-id="16043-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="16043-133">Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.</span><span class="sxs-lookup"><span data-stu-id="16043-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="16043-134">Перемещение привязанного GameObject по всему миру</span><span class="sxs-lookup"><span data-stu-id="16043-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="16043-135">GameObject нельзя переместить, пока на нем есть универсальная привязка.</span><span class="sxs-lookup"><span data-stu-id="16043-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="16043-136">Если вам нужно переместить GameObject этот кадр, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="16043-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="16043-137">Дестройиммедиате компонент «мировая привязка»</span><span class="sxs-lookup"><span data-stu-id="16043-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="16043-138">Перемещение GameObject</span><span class="sxs-lookup"><span data-stu-id="16043-138">Move the GameObject</span></span>
3. <span data-ttu-id="16043-139">Добавьте новый компонент универсальной привязки к GameObject.</span><span class="sxs-lookup"><span data-stu-id="16043-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="16043-140">Обработка изменений Локатабилити</span><span class="sxs-lookup"><span data-stu-id="16043-140">Handling Locatability Changes</span></span>

<span data-ttu-id="16043-141">Ворлданчор не может быть размещаемые в физическом мире на момент времени.</span><span class="sxs-lookup"><span data-stu-id="16043-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="16043-142">В таком случае Unity не будет обновлять преобразование привязанного объекта.</span><span class="sxs-lookup"><span data-stu-id="16043-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="16043-143">Это также можно изменить во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="16043-143">This also can change while an app is running.</span></span> <span data-ttu-id="16043-144">Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.</span><span class="sxs-lookup"><span data-stu-id="16043-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="16043-145">Чтобы получать уведомления об изменениях локатабилити:</span><span class="sxs-lookup"><span data-stu-id="16043-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="16043-146">Подпишитесь на событие Онтраккингчанжед</span><span class="sxs-lookup"><span data-stu-id="16043-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="16043-147">Обработайте событие</span><span class="sxs-lookup"><span data-stu-id="16043-147">Handle the event</span></span>

<span data-ttu-id="16043-148">Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.</span><span class="sxs-lookup"><span data-stu-id="16043-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="16043-149">Затем обработайте событие:</span><span class="sxs-lookup"><span data-stu-id="16043-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="16043-150">Иногда привязки размещаются немедленно.</span><span class="sxs-lookup"><span data-stu-id="16043-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="16043-151">В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent <WorldAnchor> () возвращает.</span><span class="sxs-lookup"><span data-stu-id="16043-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="16043-152">В результате событие Онтраккингчанжед не будет запущено.</span><span class="sxs-lookup"><span data-stu-id="16043-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="16043-153">Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.</span><span class="sxs-lookup"><span data-stu-id="16043-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```