---
title: ховтоадднеаринтерактивити
description: Документация по ближайшему взаимодействию в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, близкое взаимодействие,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644850"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="de14e-104">Как добавить близкое взаимодействие в МРТК</span><span class="sxs-lookup"><span data-stu-id="de14e-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="de14e-105">Близкие взаимодействия приходят в виде касаний и захватов.</span><span class="sxs-lookup"><span data-stu-id="de14e-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="de14e-106">События касания и захвата создаются как события указателя [покепоинтер](pointers.md#pokepointer) и [сферепоинтер](pointers.md#spherepointer)соответственно.</span><span class="sxs-lookup"><span data-stu-id="de14e-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="de14e-107">Для прослушивания сенсорного ввода и/или получения входных событий в определенном GameObject требуется три ключевых шага.</span><span class="sxs-lookup"><span data-stu-id="de14e-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="de14e-108">Убедитесь, что соответствующий указатель зарегистрирован в основном [профиле конфигурации мртк](../../configuration/mixed-reality-configuration-guide.md).</span><span class="sxs-lookup"><span data-stu-id="de14e-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="de14e-109">Убедитесь, что нужный GameObject имеет соответствующий компонент скрипта [захвата](#add-grab-interactions) или [сенсорного ввода](#add-touch-interactions) и [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="de14e-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="de14e-110">Реализуйте интерфейс обработчика входных данных для присоединенного скрипта к желаемому GameObject для прослушивания событий [захвата](#grab-code-example) или [касания](#touch-code-example) .</span><span class="sxs-lookup"><span data-stu-id="de14e-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="de14e-111">Добавление взаимодействий захвата</span><span class="sxs-lookup"><span data-stu-id="de14e-111">Add grab interactions</span></span>

1. <span data-ttu-id="de14e-112">Убедитесь, что [сферепоинтер](pointers.md#spherepointer) зарегистрирован в *профиле указателя мртк*.</span><span class="sxs-lookup"><span data-stu-id="de14e-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="de14e-113">Профиль МРТК по умолчанию и профиль HoloLens 2 по умолчанию уже содержат *сферепоинтер*.</span><span class="sxs-lookup"><span data-stu-id="de14e-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="de14e-114">Можно подтвердить, что сферепоинтер будет создан, выбрав профиль конфигурации мртк и перейдя к   >    >  **параметрам указателя** входных указателей.</span><span class="sxs-lookup"><span data-stu-id="de14e-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="de14e-115">По умолчанию для `GrabPointer` prefab (Assets/мртк/SDK/Features/UX/Prefabs/указатели) должен быть указан *тип контроллера* с установленной *рукой*.</span><span class="sxs-lookup"><span data-stu-id="de14e-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="de14e-116">Пользовательское prefab можно использовать при условии, что он реализует [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) класс.</span><span class="sxs-lookup"><span data-stu-id="de14e-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Пример профиля курсора захвата](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="de14e-118">Указатель захвата по умолчанию запрашивает соседние объекты в конусе вокруг точки захвата в соответствии с интерфейсом Hololens 2 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="de14e-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Закрестный указатель для захвата](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="de14e-120">В GameObject, которые должны быть захвачены, добавьте [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , а также в виде конфликтующего.</span><span class="sxs-lookup"><span data-stu-id="de14e-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="de14e-121">Убедитесь, что слой GameObject находится на захваченном слое.</span><span class="sxs-lookup"><span data-stu-id="de14e-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="de14e-122">По умолчанию все слои, кроме *пространственной осведомленности* и *Ignore райкастс* , могут быть извлечены.</span><span class="sxs-lookup"><span data-stu-id="de14e-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="de14e-123">Чтобы узнать, какие слои могут быть извлечены, проверьте *маски слоя захвата* в *грабпоинтер* prefab.</span><span class="sxs-lookup"><span data-stu-id="de14e-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="de14e-124">В GameObject или одном из его предков добавьте компонент скрипта, реализующий [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="de14e-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="de14e-125">Любой предок объекта с объектом [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) будет иметь возможность получать события указателя.</span><span class="sxs-lookup"><span data-stu-id="de14e-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="de14e-126">Пример кода захвата</span><span class="sxs-lookup"><span data-stu-id="de14e-126">Grab code example</span></span>

<span data-ttu-id="de14e-127">Ниже приведен скрипт, который будет печатать, если событие является касанием или захватом.</span><span class="sxs-lookup"><span data-stu-id="de14e-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="de14e-128">В соответствующей функции интерфейса *имикседреалитипоинтерхандлер* можно просмотреть тип указателя, который активирует это событие через [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="de14e-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="de14e-129">Если указатель является *сферепоинтер*, то взаимодействие является захватом.</span><span class="sxs-lookup"><span data-stu-id="de14e-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a><span data-ttu-id="de14e-130">Добавление сенсорных взаимодействий</span><span class="sxs-lookup"><span data-stu-id="de14e-130">Add touch interactions</span></span>

<span data-ttu-id="de14e-131">Процесс добавления сенсорного взаимодействия в элементах Унитюи отличается от процесса обычный 3D объекты gameobject.</span><span class="sxs-lookup"><span data-stu-id="de14e-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="de14e-132">Чтобы включить компоненты пользовательского интерфейса Unity, можно перейти к следующему разделу *Unity UI*.</span><span class="sxs-lookup"><span data-stu-id="de14e-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="de14e-133">Однако для **обоих** типов элементов UX убедитесь, что [покепоинтер](pointers.md#pokepointer) зарегистрирован в *профиле указателя мртк*.</span><span class="sxs-lookup"><span data-stu-id="de14e-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="de14e-134">Профиль МРТК по умолчанию и профиль HoloLens 2 по умолчанию уже содержат *покепоинтер*.</span><span class="sxs-lookup"><span data-stu-id="de14e-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="de14e-135">Можно подтвердить, что покепоинтер будет создан, выбрав профиль конфигурации мртк и перейдя к   >    >  **параметрам указателя** входных указателей.</span><span class="sxs-lookup"><span data-stu-id="de14e-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="de14e-136">По умолчанию `PokePointer` (Assets/мртк/SDK/Features/UX/Prefabs/указатели) prefab должен быть указан *тип контроллера* с установленной *рукой*.</span><span class="sxs-lookup"><span data-stu-id="de14e-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="de14e-137">Пользовательское prefab можно использовать при условии, что он реализует [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) класс.</span><span class="sxs-lookup"><span data-stu-id="de14e-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Пример профиля указателя для примера](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="de14e-139">Трехмерная объекты gameobject</span><span class="sxs-lookup"><span data-stu-id="de14e-139">3D GameObjects</span></span>

<span data-ttu-id="de14e-140">Существует два разных способа добавления сенсорных взаимодействий в трехмерные объекты gameobjectы в зависимости от того, будет ли трехмерный объект иметь только одну сенсорную плоскость, или, если она должна быть сенсорной в зависимости от его полного конфликта.</span><span class="sxs-lookup"><span data-stu-id="de14e-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="de14e-141">Первый способ обычно применяется к объектам с Боксколлидерс, где требуется только один человек, реагирующий на события касания.</span><span class="sxs-lookup"><span data-stu-id="de14e-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="de14e-142">Другой — для объектов, которые должны быть сенсорными в любом направлении в зависимости от их конфликтующего объекта.</span><span class="sxs-lookup"><span data-stu-id="de14e-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="de14e-143">Касание одним лицом</span><span class="sxs-lookup"><span data-stu-id="de14e-143">Single face touch</span></span>

<span data-ttu-id="de14e-144">Это полезно для случаев, когда только один человек должен быть сенсорным.</span><span class="sxs-lookup"><span data-stu-id="de14e-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="de14e-145">Этот параметр предполагает, что у игрового объекта есть Боксколлидер.</span><span class="sxs-lookup"><span data-stu-id="de14e-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="de14e-146">его можно использовать с объектами, не являющимися Боксколлидер. в этом случае свойства "Bounds" и "Local Center" настраиваются вручную для настройки сенсорной плоскости (т. е. для границ следует задать ненулевое нулевое значение).</span><span class="sxs-lookup"><span data-stu-id="de14e-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="de14e-147">В GameObject, который должен быть сенсорным, добавьте компонент Боксколлидер и [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. Toolkit. input. неаринтерактионтаучабле).</span><span class="sxs-lookup"><span data-stu-id="de14e-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="de14e-148">Задайте **события, которые должны быть получены** *при использовании* `IMixedRealityTouchHandler` интерфейса [] (xref: Microsoft. микседреалити. Toolkit. input. имикседреалититаучхандлер) в скрипте компонента ниже.</span><span class="sxs-lookup"><span data-stu-id="de14e-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="de14e-149">Щелкните **исправить границы** и **центр исправлений** .</span><span class="sxs-lookup"><span data-stu-id="de14e-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Установка Неаринтерактионтаучабле](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="de14e-151">Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="de14e-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="de14e-152">.</span><span class="sxs-lookup"><span data-stu-id="de14e-152">interface.</span></span> <span data-ttu-id="de14e-153">Все предки объекта с [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. Toolkit. input. неаринтерактионтаучабле) смогут также получать события указателя.</span><span class="sxs-lookup"><span data-stu-id="de14e-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="de14e-154">В представлении сцены редактора с выбранным *неаринтерактионтаучабле* GameObject Обратите внимание на белый квадрат и стрелку.</span><span class="sxs-lookup"><span data-stu-id="de14e-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="de14e-155">Стрелка указывает на "лицевой" сенсорной панели.</span><span class="sxs-lookup"><span data-stu-id="de14e-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="de14e-156">Конфликтующие будет осуществляться только из этого направления.</span><span class="sxs-lookup"><span data-stu-id="de14e-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="de14e-157">Дополнительные сведения о том, как сделать набор для противоречию от всех направлений, см. в разделе о [произвольном касании](#arbitrary-collider-touch).</span><span class="sxs-lookup"><span data-stu-id="de14e-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="de14e-158">![Неаринтерактионтаучабле приспособлений ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="de14e-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="de14e-159">Произвольный сенсорный экран</span><span class="sxs-lookup"><span data-stu-id="de14e-159">Arbitrary collider touch</span></span>

<span data-ttu-id="de14e-160">Это полезно для случаев, когда объект игры должен быть сенсорным для всего себя.</span><span class="sxs-lookup"><span data-stu-id="de14e-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="de14e-161">Например, это можно использовать для включения взаимодействия касания для объекта с Сфереколлидер, где весь конфликт должен быть сенсорным.</span><span class="sxs-lookup"><span data-stu-id="de14e-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="de14e-162">В GameObject, который должен быть сенсорным, добавьте компонент и [ `NearInteractionTouchableVolume` ] (xref: Microsoft. микседреалити. Toolkit. input. неаринтерактионтаучаблеволуме).</span><span class="sxs-lookup"><span data-stu-id="de14e-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="de14e-163">Задайте **события, которые должны быть получены** *при использовании* `IMixedRealityTouchHandler` интерфейса [] (xref: Microsoft. микседреалити. Toolkit. input. имикседреалититаучхандлер) в скрипте компонента ниже.</span><span class="sxs-lookup"><span data-stu-id="de14e-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="de14e-164">Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="de14e-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="de14e-165">.</span><span class="sxs-lookup"><span data-stu-id="de14e-165">interface.</span></span> <span data-ttu-id="de14e-166">Все предки объекта с [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. Toolkit. input. неаринтерактионтаучабле) смогут также получать события указателя.</span><span class="sxs-lookup"><span data-stu-id="de14e-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="de14e-167">ИНТЕРФЕЙС Unity</span><span class="sxs-lookup"><span data-stu-id="de14e-167">Unity UI</span></span>

1. <span data-ttu-id="de14e-168">Добавьте или убедитесь, что в сцене есть [унитюи холст](https://docs.unity3d.com/Manual/UICanvas.html) .</span><span class="sxs-lookup"><span data-stu-id="de14e-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="de14e-169">В GameObject, который должен быть сенсорным, добавьте [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) компонент.</span><span class="sxs-lookup"><span data-stu-id="de14e-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="de14e-170">Задайте **события, которые следует принимать** в *сенсорный ввод* при использовании [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейса в скрипте компонента ниже.</span><span class="sxs-lookup"><span data-stu-id="de14e-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="de14e-171">Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="de14e-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="de14e-172">Все предки объекта с помощью смогут [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) также получать события указателя.</span><span class="sxs-lookup"><span data-stu-id="de14e-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de14e-173">Объекты могут работать не так, как ожидалось, если они расположены на перекрывающихся объектах Canvas.</span><span class="sxs-lookup"><span data-stu-id="de14e-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="de14e-174">Чтобы обеспечить единообразие поведения, никогда не пересекать объекты Canvas в сцене.</span><span class="sxs-lookup"><span data-stu-id="de14e-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de14e-175">В `NearInteractionTouchable` компоненте скрипта для событий свойств *можно получить* два варианта: *указатель* и *сенсорный ввод*.</span><span class="sxs-lookup"><span data-stu-id="de14e-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="de14e-176">Задайте *события для получения* *указателя* , если используется [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) интерфейс, и задайте для параметра значение *Touch* , если используется [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейс в скрипте компонента, который отвечает и обрабатывает входные события.</span><span class="sxs-lookup"><span data-stu-id="de14e-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="de14e-177">Пример кода Touch</span><span class="sxs-lookup"><span data-stu-id="de14e-177">Touch code example</span></span>

<span data-ttu-id="de14e-178">В приведенном ниже коде показано неизменное поведение, которое можно присоединить к GameObject с [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) вариантным компонентом и реагировать на события сенсорного ввода.</span><span class="sxs-lookup"><span data-stu-id="de14e-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a><span data-ttu-id="de14e-179">Примеры сценариев взаимодействия ближнего действия</span><span class="sxs-lookup"><span data-stu-id="de14e-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="de14e-180">События касания</span><span class="sxs-lookup"><span data-stu-id="de14e-180">Touch events</span></span>

<span data-ttu-id="de14e-181">Этот пример создает куб, делает его сенсорным и изменяет цвет при касании.</span><span class="sxs-lookup"><span data-stu-id="de14e-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a><span data-ttu-id="de14e-182">События захвата</span><span class="sxs-lookup"><span data-stu-id="de14e-182">Grab events</span></span>

<span data-ttu-id="de14e-183">В приведенном ниже примере показано, как сделать GameObject перетаскиванием.</span><span class="sxs-lookup"><span data-stu-id="de14e-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="de14e-184">Предполагает, что на нем есть объект Game.</span><span class="sxs-lookup"><span data-stu-id="de14e-184">Assumes that the game object has a collider on it.</span></span>

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a><span data-ttu-id="de14e-185">Полезные интерфейсы API</span><span class="sxs-lookup"><span data-stu-id="de14e-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="de14e-186">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="de14e-186">See also</span></span>

* [<span data-ttu-id="de14e-187">Общие сведения о входных данных</span><span class="sxs-lookup"><span data-stu-id="de14e-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="de14e-188">Указатели</span><span class="sxs-lookup"><span data-stu-id="de14e-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="de14e-189">Входные события</span><span class="sxs-lookup"><span data-stu-id="de14e-189">Input Events</span></span>](input-events.md)
