---
title: Указатели
description: Документация по указателям в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, указатели,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191019"
---
# <a name="pointers"></a>Указатели

![Указатель](../images/pointers/MRTK_Pointer_Main.png)

В этой статье объясняется, как настроить и реагировать на ввод указателя на практике по сравнению с [архитектурой указателя](../../architecture/controllers-pointers-and-focus.md) .

Экземпляры указателей устанавливаются автоматически во время выполнения при обнаружении нового контроллера. К контроллеру можно подключить более одного указателя. например, при использовании профиля указателя по умолчанию Windows Mixed Reality контроллеры получают как линию, так и указатель параболическим для нормального выбора и телетранспорта соответственно.

## <a name="pointer-configuration"></a>Конфигурация указателя

Указатели настраиваются как часть входной системы в МРТК через [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Этот тип профиля назначается [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) в инспекторе конфигурации мртк. Профиль указателя определяет курсор, типы указателей, доступные во время выполнения, и то, как эти указатели обмениваются данными друг с другом, чтобы решить, какая из них активна.

- *Указывающее экстент* — определяет максимальное расстояние, для которого указатель может взаимодействовать с GameObject.

- *Указание Райкаст слоя-масок* — это упорядоченный массив лайермаскс, позволяющий определить, какие возможные объекты gameobject могут взаимодействовать с любым заданным указателем, а также порядок попыток взаимодействия. Это может быть полезно для обеспечения взаимодействия указателей с элементами пользовательского интерфейса перед другими объектами сцены.
![Пример профиля указателя](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Настройка параметров указателя

Конфигурация профиля указателя МРТК по умолчанию включает следующие классы указателей и связанные Prefabs. Список указателей, доступных системе во время выполнения, определяется в разделе *Параметры указателя* в профиле указателя. Разработчики могут использовать этот список для перенастройки существующих указателей, добавления новых указателей или удаления их.

![Пример профиля параметров указателя](../images/input/pointers/PointerOptionsProfile.PNG)

Каждая запись указателя определяется следующим набором данных:

- *Тип контроллера* — набор контроллеров, для которых допустимы указатели.
  - Например, *покепоинтер* отвечает за объекты "Знакомство" с помощью пальца. по умолчанию он помечен как поддерживающий только тип контроллера с установленным именем. Экземпляры указателей создаются только в том случае, если контроллер станет доступным, а в частности *тип контроллера* определяет, с какими контроллерами может быть создан этот указатель prefab.

- *Правой или левой* — позволяет создать указатель на экземпляр только для конкретной руки (слева направо).

> [!NOTE]
> Если задать для свойства *правой или левой* записи указателя значение *None* , это позволит эффективно отключить его от системы в качестве альтернативы удалению этого указателя из списка.

- *Pointer prefab* — этот ресурс prefab будет создан при отслеживании контроллера, соответствующего указанному типу контроллера и правой или левой.

С контроллером можно связать несколько указателей. Например, в `DefaultHoloLens2InputSystemProfile` (Assets/мртк/SDK/Profiles/HoloLens2/) контроллер с управляемым кодом связан с *покепоинтер*, *грабпоинтер* и *дефаултконтроллерпоинтер* (т. е. лучи с рукой).

> [!NOTE]
> МРТК предоставляет набор Prefabs указателя в *Assets/мртк/SDK/Features/UX/Prefabs/указатели*. Новый пользовательский prefab можно построить, если он содержит один из сценариев указателя в *Assets/мртк/SDK/Features/UX/Scripts* /Pointers или любом другом скрипте, реализующем [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Классы указателей по умолчанию

Следующие классы — это стандартные указатели МРТК, доступные и определенные в *профиле указателя мртк* по умолчанию, описанном выше. Каждый prefab указателя, указанный в разделе *Assets/мртк/SDK/Features/UX/Prefabs/* Pointers, содержит один из прикрепленных компонентов указателя.

![МРТК указатели по умолчанию](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Дальнее указатели

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *Линепоинтер*, базовый класс указателя, рисует линию из источника входных данных (т. е. контроллера) в направлении указателя и поддерживает один объект CAST в этом направлении. Как правило, такие дочерние классы, как [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) и указатели телепортируйтесь, являются экземплярами и используются (которые также рисуют линии, чтобы указать, где будет расположиться в конечном итоге) вместо этого класса, который в основном предоставляет общие функциональные возможности.

для контроллеров движения, таких как в окулус, naopak и Windows Mixed Reality, поворот будет соответствовать повороту контроллера. для других контроллеров, таких как HoloLens 2 накладываемые руки, поворот соответствует предоставленной системой, указывающей на свою руку.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*Курвепоинтер* расширяет класс *линепоинтер* , позволяя выполнять многошаговые приведения вдоль кривой. Базовый класс указателя полезен для таких искривленных экземпляров, как указатели на перемещение, когда линия постоянно изогнута в парабола.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

Реализация *шеллхандрайпоинтер*, которая расширяется из [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) , используется в качестве значения по умолчанию для *профиля указателя мртк*. *Дефаултконтроллерпоинтер* prefab реализует [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) класс.

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

кроме того, он называется указателем « *взгляд/жест/Voice» (ггв)* , ггвпоинтер выключает HoloLens вид и касание в стиле 1, в первую очередь с помощью сенсорного экрана и касания, а также сенсорного выбора. Позиции и направления указателя ГГВ определяются положением и поворотом головного элемента.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*Таучпоинтер* отвечает за работу с сенсорным входом Unity (т. е. сенсорного экрана). Это «дальнее взаимодействие», так как касание экрана приводит к преобразованию луча из камеры в потенциально далекое место в сцене.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer* выводит экран в мир райкаст для дальнего взаимодействия, но для мыши вместо касания.

![Указатель мыши](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> По умолчанию в МРТК поддержка мыши недоступна, но ее можно включить, добавив новый *поставщик входных данных* типа [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) в профиль ввода мртк и назначив его [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) поставщику данных.

#### <a name="near-pointers"></a>Близкие указатели

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[Покепоинтер](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* используется для взаимодействия с игровыми объектами, которые поддерживают "приближается к сенсорному взаимодействию". которые являются объекты gameobject, которые имеют присоединенный [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) скрипт. В случае с Унитюи этот указатель выполняет поиск Неаринтерактионтаучаблеунитюис.  Покепоинтер использует Сферекаст для определения ближайшего сенсорного элемента и используется для управления такими элементами, как нажатые кнопки.

 При настройке GameObject с помощью [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) компонента обязательно настройте параметр *локалфорвард* , чтобы он указывал на начало кнопки или другого объекта, который необходимо сделать сенсорным. Также убедитесь, что *границы* сенсорного ввода соответствуют границам сенсорного объекта.

Полезные свойства указателя для последующих действий:

- *Таучабледистанце*: максимальное расстояние, в котором можно взаимодействовать с сенсорной поверхностью
- *Визуальные элементы*: объект Game, используемый для визуализации визуального кончика пальца (по умолчанию кольцо на пальце).
- *Line*: необязательная линия для отображения активной поверхности ввода.
- *Вставка масок слоев* — упорядоченный массив лайермаскс для определения возможных объекты gameobject, с которыми может взаимодействовать указатель, а также порядок попыток взаимодействия. Обратите внимание, что GameObject также должен иметь `NearInteractionTouchable` компонент для взаимодействия с указателем на Вставка.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[Сферепоинтер](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* использует [UnityEngine. физик. оверлапсфере](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) для указания ближайшего [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) объекта для взаимодействия, что полезно для «захвата» входных данных, таких как `ManipulationHandler` . Как и [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) функциональная пара, для взаимодействия с указателем сферы, объект игры должен содержать компонент, который является [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) сценарием.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Свойства указателя на полезные сферы:

- *Радиус приведения сферы*: Радиус сферы, используемый для запроса объектов, которые могут быть извлечены.
- *Приближается к полю объекта*: расстояние на вершине радиуса приведения сферы к запросу для определения, находится ли объект рядом с указателем. Всего для обнаружения близких объектов RADIUS — это поле радиуса приведение типа сферы
- *Угол Ближнего сектора объекта*: угол вокруг прямой оси указателя для запроса ближайших объектов. Делает `IsNearObject` функцию запроса, подобную конусной. По умолчанию задано значение 66 градусов, совпадающее с поведением Hololens 2

![Указатель сферы изменен на запрос только объектов в прямом направлении](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Фактор сглаживания близких объектов*: Коэффициент сглаживания для обнаружения близкого объекта. Если объект обнаружен в радиусе вблизи объекта, запрашиваемый радиус становится ближайшим объектом RADIUS * (1 + Коэффициент сглаживания близких объектов) для уменьшения чувствительности и усложняет объект для выхода из диапазона обнаружения.
- *Маски слоя захвата* — приоритетный массив лайермаскс для определения возможных объекты gameobject, с которыми может взаимодействовать указатель, а также порядок попыток взаимодействия. Обратите внимание, что GameObject должен также иметь `NearInteractionGrabbable` для взаимодействия с сферепоинтер.
    > [!NOTE]
    > Уровень пространственной осведомленности отключен в Грабпоинтер prefab по умолчанию, предоставленном МРТК. Это делается для уменьшения влияния запроса на перекрытие сфер с пространственной сеткой. Это можно сделать, изменив prefab Грабпоинтер.
- *Игнорировать конфликты, отсутствующие в фов* , — следует ли игнорировать конфликты, которые могут находиться ближе к указателю, но не в самом деле в Visual фов.
Это может препятствовать случайному захвату и позволит включить отправку при приближении к захватау, но не может его увидеть. *Визуальный фов* определяется с помощью конуса вместо типичного фрустум по соображениям производительности. Этот конус выравнивается по центру и ориентирован так же, как и фрустум камеры с радиусом, равным половине отображаемой высоты (или вертикальной фов).

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Указатели телепортируйтесь

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) порождает запрос телепортируйтесь при выполнении действия (например, нажата кнопка телепортируйтесь, чтобы переместить пользователя.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) порождает запрос телепортируйтесь при выполнении действия (например, нажата кнопка телепортируйтесь) с параболическим строкой райкаст для перемещения пользователя.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Поддержка указателей для платформ смешанной реальности

В следующей таблице описаны типы указателей, которые обычно используются для общих платформ в МРТК. Примечание. для этих платформ можно добавить различные типы указателей. Например, можно добавить указатель или указатель-сферу в VR. Кроме того, устройства VR с игровой планшетом могут использовать указатель ГГВ.

|       Указатель              | OpenVR:  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| шеллхандрайпоинтер | Допустимо   | Допустимо                 |            | Допустимо      |
| телепортпоинтер     | Допустимо   | Допустимо                 |            |            |
| ггвпоинтер          |         |                       | Допустимо      |            |
| сферепоинтер       |         |                       |            | Допустимо      |
| покепоинтер         |         |                       |            | Допустимо      |

## <a name="pointer-interactions-via-code"></a>Взаимодействие указателей через код

### <a name="pointer-event-interfaces"></a>Интерфейсы событий указателя

Одностраничные, реализующие один или несколько из следующих интерфейсов и назначенные GameObject с помощью, получат `Collider` события взаимодействия указателя в соответствии с определением связанного интерфейса.

| Событие | Описание | Обработчик |
| --- | --- | --- |
| До изменения фокуса или изменения фокуса | Порождается как в игровом объекте, так и при каждом изменении фокуса. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Фокус на ввод/выход | Порождается на игровом объекте, чтобы получить фокус при нажатии первого указателя мыши и при потере фокуса, когда последний указатель покидает его. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Указатель "вниз"/"перемещено/вверх" | Вызывается для нажатия указателя на отчет, перетаскивания и освобождения. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Касание запущено, Обновлено/завершено | Порождается указателями, поддерживающими касание, например, [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) для создания отчетов. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) и [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) должны обрабатываться в объектах, на которых они создаются. События фокуса можно получать глобально, но, в отличие от других входных событий, глобальный обработчик событий не блокирует получение событий на основе фокуса (событие будет получено как глобальным обработчиком, так и соответствующим объектом в фокусе).

#### <a name="pointer-input-events-in-action"></a>События ввода указателя в действии

Входные события указателя распознаются и обрабатываются системой ввода МРТК так же, как [обычные события ввода](input-events.md#input-events-in-action). Разница заключается в том, что события ввода указателя обрабатываются только GameObject в фокусе указателем, который активировал событие ввода, а также любыми глобальными обработчиками ввода. Обычные события ввода обрабатываются объекты gameobject в фокусе для всех активных указателей.

1. Входная система МРТК распознает событие ввода.
1. Входная система МРТК запускает соответствующую функцию интерфейса для входного события во все зарегистрированные глобальные обработчики ввода.
1. Входная система определяет, в какой GameObject фокус находится указатель, который активировал событие.
    1. Входная система использует [систему событий Unity](https://docs.unity3d.com/Manual/EventSystem.html) для запуска соответствующей функции интерфейса для всех совпадающих компонентов в фокусе GameObject
    1. Если в любой момент входное событие было [помечено как используемое](input-events.md#how-to-stop-input-events), процесс завершится, а последующие объекты gameobject не получат обратные вызовы.
        - Пример: компоненты, реализующие интерфейс, [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) будут искать GameObject или теряет фокус
        - Примечание. Система событий Unity будет выполнять поиск в родительском GameObject, если ни один из компонентов, соответствующих требуемому интерфейсу, не найден в текущем GameObject.
1. Если не зарегистрированы глобальные входные обработчики и не найден GameObject с соответствующим компонентом или интерфейсом, то входная система будет вызывать каждый из зарегистрированных входных обработчиков.

#### <a name="example"></a>Пример

Ниже приведен пример скрипта, который изменяет цвет присоединенного модуля подготовки отчетов, когда указатель принимает или оставляет фокус или когда указатель выбирает объект.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Указатели запросов

Можно собрать все активные указатели, которые в настоящее время находятся в цикле, через доступные источники входных данных (например, доступны контроллеры и входные данные), чтобы определить, к каким из них прикреплены указатели.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Основной указатель

Разработчики могут подписываться на событие Фокуспровидерс Примарипоинтерчанжед, чтобы получать уведомления при изменении основного указателя в фокусе. Это может быть очень полезно для того, чтобы выяснить, взаимодействует ли пользователь с сценами с помощью взгляда или руки или другого источника входных данных.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

`PrimaryPointerExample`Сцена (Assets/мртк/examples/демонстрация/вход/сцена/примарипоинтер) показывает, как использовать [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) события for для реагирования на новый первичный указатель.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Результат указателя

Свойство указателя [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) содержит текущий результат для запроса сцены, используемого для определения объекта с фокусом. Для райкаст указателя, например созданных по умолчанию для контроллеров движения, Взгляните на входной и правый лучи, он будет содержать расположение и нормаль райкастного попадания.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

В `PointerResultExample` сцене (Assets/мртк/examples/демонстрация/input/сцены/поинтерресулт/поинтерресултексампле. Unity) показано, как использовать указатель [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) для порождения объекта в месте попадания.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Отключить указатели

Чтобы включить и отключить указатели (например, для отключения руки), задайте [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) для данного типа указателя через [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Дополнительные примеры см. в разделе и.

## <a name="pointer-interactions-via-editor"></a>Взаимодействие указателей через редактор

Для событий указателя, обрабатываемых [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) , мртк предоставляет дополнительное удобство в форме [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) компонента, что позволяет обрабатывать события указателей непосредственно через события Unity.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Область указателя

У дальнего указателя есть параметры, которые ограничивают, насколько они будут райкаст и взаимодействовать с другими объектами сцены.
По умолчанию это значение равно 10 метрах. это значение было выбрано для поддержания соответствия с поведением оболочки HoloLens.

Это можно изменить, обновив `DefaultControllerPointer` [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) поля компонента Prefab:

*Область указателя* — определяет максимальное расстояние, с которым будут взаимодействовать указатели.

*Область указателя по умолчанию* — определяет длину указателя луча/линии, которая будет отображаться, когда указатель не взаимодействует ни с чем.

## <a name="see-also"></a>См. также раздел

- [Архитектура указателя](../../architecture/controllers-pointers-and-focus.md)
- [Входные события](input-events.md)
