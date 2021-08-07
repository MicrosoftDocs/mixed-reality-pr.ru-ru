---
title: Как добавить ближнее взаимодействие
description: Документация по ближайшему взаимодействию в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, близкое взаимодействие,
ms.openlocfilehash: 174623ebf340e800848c15e22dc2299aaf997b484a1329d67c28540acd79515a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212600"
---
# <a name="how-to-add-near-interactivity"></a>Как добавить ближнее взаимодействие

Близкие взаимодействия приходят в виде касаний и захватов. События касания и захвата создаются как события указателя [покепоинтер](pointers.md#pokepointer) и [сферепоинтер](pointers.md#spherepointer)соответственно.

Для прослушивания сенсорного ввода и/или получения входных событий в определенном GameObject требуется три ключевых шага.

1. Убедитесь, что соответствующий указатель зарегистрирован в основном [профиле конфигурации мртк](../../configuration/mixed-reality-configuration-guide.md).
1. Убедитесь, что нужный GameObject имеет соответствующий компонент скрипта [захвата](#add-grab-interactions) или [сенсорного ввода](#add-touch-interactions) и [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Реализуйте интерфейс обработчика входных данных для присоединенного скрипта к желаемому GameObject для прослушивания событий [захвата](#grab-code-example) или [касания](#touch-code-example) .

## <a name="add-grab-interactions"></a>Добавление взаимодействий захвата

1. Убедитесь, что [сферепоинтер](pointers.md#spherepointer) зарегистрирован в *профиле указателя мртк*.

    профиль мртк по умолчанию и профиль HoloLens 2 по умолчанию уже содержат *сферепоинтер*. Можно подтвердить, что сферепоинтер будет создан, выбрав профиль конфигурации мртк и перейдя к   >    >  **параметрам указателя** входных указателей. По умолчанию для `GrabPointer` prefab (Assets/мртк/SDK/Features/UX/Prefabs/указатели) должен быть указан *тип контроллера* с установленной *рукой*. Пользовательское prefab можно использовать при условии, что он реализует [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) класс.

    ![Пример профиля курсора захвата](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Указатель захвата по умолчанию запрашивает соседние объекты в конусе вокруг точки захвата в соответствии с интерфейсом Hololens 2 по умолчанию.

    ![Закрестный указатель для захвата](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. В GameObject, которые должны быть захвачены, добавьте [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , а также в виде конфликтующего.

    Убедитесь, что слой GameObject находится на захваченном слое. По умолчанию все слои, кроме *пространственной осведомленности* и *Ignore райкастс* , могут быть извлечены. Чтобы узнать, какие слои могут быть извлечены, проверьте *маски слоя захвата* в *грабпоинтер* prefab.

1. В GameObject или одном из его предков добавьте компонент скрипта, реализующий [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) интерфейс. Любой предок объекта с объектом [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) будет иметь возможность получать события указателя.

### <a name="grab-code-example"></a>Пример кода захвата

Ниже приведен скрипт, который будет печатать, если событие является касанием или захватом. В соответствующей функции интерфейса *имикседреалитипоинтерхандлер* можно просмотреть тип указателя, который активирует это событие через [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Если указатель является *сферепоинтер*, то взаимодействие является захватом.

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

## <a name="add-touch-interactions"></a>Добавление сенсорных взаимодействий

Процесс добавления сенсорного взаимодействия в элементах Унитюи отличается от процесса обычный 3D объекты gameobject. Чтобы включить компоненты пользовательского интерфейса Unity, можно перейти к следующему разделу *Unity UI*.

Однако для **обоих** типов элементов UX убедитесь, что [покепоинтер](pointers.md#pokepointer) зарегистрирован в *профиле указателя мртк*.

профиль мртк по умолчанию и профиль HoloLens 2 по умолчанию уже содержат *покепоинтер*. Можно подтвердить, что покепоинтер будет создан, выбрав профиль конфигурации мртк и перейдя к   >    >  **параметрам указателя** входных указателей. По умолчанию `PokePointer` (Assets/мртк/SDK/Features/UX/Prefabs/указатели) prefab должен быть указан *тип контроллера* с установленной *рукой*. Пользовательское prefab можно использовать при условии, что он реализует [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) класс.

![Пример профиля указателя для примера](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>Трехмерная объекты gameobject

Существует два разных способа добавления сенсорных взаимодействий в трехмерные объекты gameobjectы в зависимости от того, будет ли трехмерный объект иметь только одну сенсорную плоскость, или, если она должна быть сенсорной в зависимости от его полного конфликта.
Первый способ обычно применяется к объектам с Боксколлидерс, где требуется только один человек, реагирующий на события касания. Другой — для объектов, которые должны быть сенсорными в любом направлении в зависимости от их конфликтующего объекта.

### <a name="single-face-touch"></a>Касание одним лицом

Это полезно для случаев, когда только один человек должен быть сенсорным. Этот параметр предполагает, что у игрового объекта есть Боксколлидер. его можно использовать с объектами, не являющимися Боксколлидер. в этом случае свойства "Bounds" и "Local Center" настраиваются вручную для настройки сенсорной плоскости (т. е. для границ следует задать ненулевое нулевое значение).

1. в GameObject, который должен быть сенсорным, добавьте боксколлидер и [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. набор средств. Input. Неаринтерактионтаучабле).

    1. задайте **события для получения** *касания* при использовании [ `IMixedRealityTouchHandler` ] (xref: Microsoft. микседреалити. набор средств. Input. Имикседреалититаучхандлер) в скрипте компонента ниже.

    1. Щелкните **исправить границы** и **центр исправлений** .

    ![Установка Неаринтерактионтаучабле](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . любой предок объекта с [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. набор средств. Input. Неаринтерактионтаучабле) также смогут получать события указателя.

> [!NOTE]
> В представлении сцены редактора с выбранным *неаринтерактионтаучабле* GameObject Обратите внимание на белый квадрат и стрелку. Стрелка указывает на "лицевой" сенсорной панели. Конфликтующие будет осуществляться только из этого направления. Дополнительные сведения о том, как сделать набор для противоречию от всех направлений, см. в разделе о [произвольном касании](#arbitrary-collider-touch).
> ![Неаринтерактионтаучабле приспособлений ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Произвольный сенсорный экран

Это полезно для случаев, когда объект игры должен быть сенсорным для всего себя. Например, это можно использовать для включения взаимодействия касания для объекта с Сфереколлидер, где весь конфликт должен быть сенсорным.

1. в GameObject, который должен быть сенсорным, добавьте объект "" и [ `NearInteractionTouchableVolume` ] (xref: Microsoft. микседреалити. набор средств. Input. Неаринтерактионтаучаблеволуме).

    1. задайте **события для получения** *касания* при использовании [ `IMixedRealityTouchHandler` ] (xref: Microsoft. микседреалити. набор средств. Input. Имикседреалититаучхандлер) в скрипте компонента ниже.

1. Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . любой предок объекта с [ `NearInteractionTouchable` ] (xref: Microsoft. микседреалити. набор средств. Input. Неаринтерактионтаучабле) также смогут получать события указателя.

### <a name="unity-ui"></a>ИНТЕРФЕЙС Unity

1. Добавьте или убедитесь, что в сцене есть [унитюи холст](https://docs.unity3d.com/Manual/UICanvas.html) .

1. В GameObject, который должен быть сенсорным, добавьте [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) компонент.  

    1. Задайте **события, которые следует принимать** в *сенсорный ввод* при использовании [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейса в скрипте компонента ниже.

1. Для этого объекта или одного из его предков добавьте компонент скрипта, реализующий [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейс. Все предки объекта с помощью смогут [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) также получать события указателя.

> [!IMPORTANT]
> Объекты могут работать не так, как ожидалось, если они расположены на перекрывающихся объектах Canvas. Чтобы обеспечить единообразие поведения, никогда не пересекать объекты Canvas в сцене.

> [!IMPORTANT]
> В `NearInteractionTouchable` компоненте скрипта для событий свойств *можно получить* два варианта: *указатель* и *сенсорный ввод*. Задайте *события для получения* *указателя* , если используется [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) интерфейс, и задайте для параметра значение *Touch* , если используется [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) интерфейс в скрипте компонента, который отвечает и обрабатывает входные события.

#### <a name="touch-code-example"></a>Пример кода Touch

В приведенном ниже коде показано неизменное поведение, которое можно присоединить к GameObject с [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) вариантным компонентом и реагировать на события сенсорного ввода.

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

## <a name="near-interaction-script-examples"></a>Примеры сценариев взаимодействия ближнего действия

### <a name="touch-events"></a>События касания

Этот пример создает куб, делает его сенсорным и изменяет цвет при касании.

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

### <a name="grab-events"></a>События захвата

В приведенном ниже примере показано, как сделать GameObject перетаскиванием. Предполагает, что на нем есть объект Game.

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

## <a name="useful-apis"></a>Полезные интерфейсы API

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>См. также раздел

* [Общие сведения о входных данных](overview.md)
* [Указатели](pointers.md)
* [Входные события](input-events.md)
