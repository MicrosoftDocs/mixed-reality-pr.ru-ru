---
title: Жесты и контроллеры движения в Unity
description: Узнайте, как выполнять действия с взглядом в Unity с помощью жестов и контроллеров движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, вход, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств для смешанной реальности
ms.openlocfilehash: e1a2ae10638bb8dbd35eed7e9a0a1d2a05181f0c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678653"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Жесты и контроллеры движения в Unity

Существует два основных способа выполнения действий с вашим [взглядом в Unity](gaze-in-unity.md), [жестами](../../design/gaze-and-commit.md#composite-gestures) и [контроллерами движения](../../design/motion-controllers.md) в HoloLens и иммерсивное ХМД. Доступ к данным для обоих источников пространственных данных осуществляется через одни и те же API в Unity.

Unity предоставляет два основных способа доступа к пространственным входным данным для Windows Mixed Reality, общих *входных и входных API-интерфейсов input.* XR, работающих в нескольких пакетах SDK для Unity, и API *интерактионманажер/GestureRecognizer* , относящийся к Windows Mixed Reality, который предоставляет полный набор пространственных входных данных.

## <a name="unity-buttonaxis-mapping-table"></a>Таблица сопоставления кнопок и осей Unity

Идентификаторы кнопок и осей, приведенные в таблице ниже, поддерживаются диспетчером ввода Unity для контроллеров движения Windows Mixed Reality с помощью *входных API-интерфейсов input. OnButton и AXIS* , а столбец "Windows MR" относится к свойствам, доступным для типа *интерактионсаурцестате* . Каждый из этих API подробно описан в следующих разделах.

Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality обычно соответствует идентификаторам кнопок и осей Окулус.

Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality отличается от сопоставлений Опенвр двумя способами:
1. Сопоставление использует идентификаторы сенсорной панели, отличающиеся от аналоговый, для поддержки контроллеров с сумбстиккс и сенсорными устройствами.
2. Сопоставление позволяет избежать перегрузки идентификаторов кнопок A и X для кнопок меню, чтобы оставить их доступными для физических кнопок АБКСИ.

<table>
<tr>
<th rowspan="2">Входные данные </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Распространенные API Unity</a><br />(Входные данные. Кнопка/ось) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Входной API Windows MR</a><br />XR. Головк. Входной</th>
</tr><tr>
<th> Левая рука </th><th> Правая рука</th>
</tr><tr>
<td> Выбрать триггер нажат </td><td> Ось 9 = 1,0 </td><td> Ось 10 = 1,0 </td><td> селектпрессед</td>
</tr><tr>
<td> Выбор триггера аналогового значения </td><td> Ось 9 </td><td> Ось 10 </td><td> селектпресседамаунт</td>
</tr><tr>
<td> Выделение триггера частично нажато </td><td> Кнопка 14 <i>(совместимость с игровым планшетом)</i> </td><td> Кнопка 15 <i>(совместимость с игровым планшетом)</i> </td><td> Селектпресседамаунт &gt; 0,0</td>
</tr><tr>
<td> Нажата кнопка меню </td><td> Кнопка 6 * </td><td> Кнопка 7 * </td><td> менупрессед</td>
</tr><tr>
<td> Нажата кнопка захвата </td><td> Ось 11 = 1,0 (нет аналоговых значений)<br />Кнопка 4 <i>(совместимость с игровым планшетом)</i> </td><td> Ось 12 = 1,0 (нет аналоговых значений)<br />Кнопка 5 <i>(совместимость с игровым планшетом)</i> </td><td> Новы</td>
</tr><tr>
<td> Аналоговый стик X <i>(слева:-1,0, справа: 1,0)</i> </td><td> Ось 1 </td><td> Ось 4 </td><td> Сумбстиккпоситион. x</td>
</tr><tr>
<td> Аналоговый стик <i>по оси Y (Top:-1,0, Нижняя: 1,0)</i> </td><td> Ось 2 </td><td> Ось 5 </td><td> Сумбстиккпоситион. y</td>
</tr><tr>
<td> Нажатый аналоговый стик </td><td> Кнопка 8 </td><td> Кнопка 9 </td><td> сумбстиккпрессед</td>
</tr><tr>
<td> Сенсорная панель X <i>(слева:-1,0, справа: 1,0)</i> </td><td> Ось 17 * </td><td> Ось 19 * </td><td> Таучпадпоситион. x</td>
</tr><tr>
<td> Сенсорная панель Y <i>(верхняя:-1,0, Нижняя: 1,0)</i> </td><td> Ось 18 * </td><td> Ось 20 * </td><td> Таучпадпоситион. y</td>
</tr><tr>
<td> Сенсорная панель затронута </td><td> Кнопка 18 * </td><td> Кнопка 19 * </td><td> таучпадтаучед</td>
</tr><tr>
<td> Сенсорная панель нажата </td><td> Кнопка 16 * </td><td> Кнопка 17 * </td><td> таучпадпрессед</td>
</tr><tr>
<td> 6DoF захват захвата или указатель </td><td colspan="2"> Только <i>захват</i> : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Инпуттраккинг. Жетлокалпоситион</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Инпуттраккинг. Жетлокалротатион</a></td><td> Передается <i>захват</i> или <i>указатель</i> в качестве аргумента: Саурцестате. саурцепосе. трижетпоситион<br />Саурцестате. Саурцепосе. Трижетротатион<br /></td>
</tr><tr>
<td> Состояние отслеживания </td><td colspan="2"> <i>Точность расположения и потери исходного кода доступны только через API-интерфейс MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">Саурцестате. Саурцепосе. Поситионаккураци</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">Саурцестате. Properties. Саурцелоссриск</a></td>
</tr>
</table>

>[!NOTE]
>Эти идентификаторы кнопок и осей отличаются от идентификаторов, используемых Unity для Опенвр из-за конфликтов в сопоставлениях, используемых в игровых элементах управления, Окулус Touch и Опенвр.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a>Захват захвата и указание объекта a

Windows Mixed Reality поддерживает контроллеры Motion в различных конструктивных факторах, при этом структура каждого контроллера различается в связи между положением пользователя и естественным направлением "вперед", которое приложения должны использовать для указания при подготовке к просмотру контроллера.

Для лучшего представления этих контроллеров существует два вида экземпляров, которые можно исследовать для каждого источника взаимодействия, **захвата** и **указателя**. Координаты захвата и указателя "указатель" выражаются всеми API Unity в глобальных координатах мира Unity.

### <a name="grip-pose"></a>Подзахват

Подсистема **захвата** представляет собой расположение кармана от руки, обнаруженного HoloLens, или карманного компьютера, удерживающий контроллер движения.

На современных головных телефонах подзахваты лучше использовать для отрисовки **руки пользователя** или объекта, **хранящегося в руки пользователя**, например технологий или обоймы. Элемент захвата также используется при визуализации контроллера движения, так как **модель подготовки к просмотру** , предоставляемая Windows для контроллера движения, использует захват в качестве источника и центра вращения.

Захват захвата определяется в частности следующим образом:
* **Позиция захвата**: Карманный центроид при удержании контроллера естественным образом настраивается влево или вправо для центрирования места внутри захвата. В контроллере движения Windows Mixed Reality эта отправка обычно соответствует кнопке "расположить".
* **Правая ось ориентации захвата**: когда вы полностью открываете руку для формирования плоской задачи с 5-пальцем, луч, обычный для вашего кармана (вперед от левого кармана, назад от правого Palm)
* **Прямая ось ориентации захвата**: когда вы частично закрываете руку (как при удержании контроллера), луч, который указывает на "Forward" через лампу, сформированную небегункными пальцами.
* **Ось Up (вверх) для ориентации захвата**: ось Up, подразумеваемая правым и прямым определением.

Доступ к захвату можно получить через API-интерфейс ввода кросс-поставщика Unity (*[XR). Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Жетлокалпоситион/вращение*) или через API-интерфейс Windows MR (*Саурцестате. Саурцепосе. Трижетпоситион/вращение*, запрашивающий данные для узла **захвата** ).

### <a name="pointer-pose"></a>Указатель a

**Указатель** a представляет кончик контроллера, указывающий на пересылку.

Предоставляемый системой указатель, который лучше использовать для райкаст при **отрисовке самой модели контроллера**. При визуализации какого-либо другого виртуального объекта вместо контроллера, например виртуального, следует указывать на луч, который наиболее естественным для этого виртуального объекта, например луч, который перемещается на объект модели обойм, определяемой приложением. Так как пользователи могут видеть виртуальный объект, а не физический контроллер, указание виртуального объекта, скорее всего, будет более естественным для тех, кто использует ваше приложение.

В настоящее время указатель a доступен в Unity только через API-интерфейс Windows MR, *саурцестате. саурцепосе. трижетпоситион/вращение*, передавая *интерактионсаурценоде. Pointer* в качестве аргумента.

## <a name="controller-tracking-state"></a>Состояние отслеживания контроллера

Как и гарнитуры, для контроллера движения Windows Mixed Reality не требуется настраивать внешние датчики отслеживания. Вместо этого контроллеры прописываются датчиками в самой гарнитуре.

Если пользователь перемещает контроллеры из поля зрения гарнитуры, в большинстве случаев Windows будет по прежнему вычислять позиции контроллера и предоставлять их приложению. Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.

На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации. Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать при приближенной точности, не закрывая пользователю.

Лучший способ сделать это — попробовать. Просмотрите это видео с примерами впечатляющих материалов, которые работают с контроллерами движения в различных состояниях отслеживания:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Явное объяснение состояния отслеживания

Приложения, которые хотят обрабатывать позиции по-разному в зависимости от состояния отслеживания, могут дополнительно проанализировать свойства в состоянии контроллера, такие как *саурцелоссриск* и *поситионаккураци*:

<table>
<tr>
<th> Состояние отслеживания </th><th> саурцелоссриск </th><th> поситионаккураци </th><th> трижетпоситион</th>
</tr><tr>
<td> <b>Высокая точность</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Высокий </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Высокая точность (при потере риска)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Высокий </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Приблизительная точность</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Приблизительна </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Без расположения</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Приблизительна </td><td style="background-color: orange"> false</td>
</tr>
</table>

Эти состояния отслеживания контроллера движения определяются следующим образом.
* **Высокая точность:** Хотя контроллер движения находится внутри поля зрения гарнитуры, он обычно предоставляет высокую точность на основе визуального отслеживания. Обратите внимание, что перемещаемый контроллер, проходящий через некоторое время, выходит за пределы поля зрения, или мгновенно закрывается от датчиков гарнитуры (например, с другой стороны пользователя), будет по-прежнему возвращать большую точность в течение короткого времени, исходя из инерции отслеживания самого контроллера.
* **Высокая точность (при потере риска):** Когда пользователь перемещает контроллер движения за пределы поля "гарнитура", головной телефон вскоре не сможет визуально отвести мониторинг позиции контроллера. Приложение знает, когда контроллер достиг этой фов границы, просматривая **саурцелоссриск** REACH 1,0. На этом этапе приложение может приостановить жесты контроллера, для которых требуется устойчивый поток с очень высоким качеством.
* **Приблизительная точность:** Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности. На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации. Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать в режиме обычной точности, не закрывая пользователю. Приложения с более **высокими** требованиями к входным данным могут отказаться от высокой точности для **приблизительной** точности, проверив свойство **поситионаккураци** , например, чтобы предоставить пользователю более масштабная хитбокс на экранных целевых объектах в течение этого времени.
* **Без расположения:** Несмотря на то, что контроллер может нормально обрабатываться в течение длительного времени, иногда система знает, что даже в данный момент не имеет смысла в положении блокировки текста. Например, контроллер, который был только что включен, может никогда не наблюдать визуально, или же пользователь может установить контроллер, который затем забирается другим пользователем. В это время система не будет предоставлять никакой позиции приложению, а *трижетпоситион* вернет значение false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Общие API-интерфейсы Unity (входные или кнопки и ось)

**Пространство имен:** *UnityEngine*, *UnityEngine. XR*<br>
**Types**: *input*, *XR. Инпуттраккинг*

В настоящее время Unity использует общие *входные API-интерфейсы input. Окулус и input. Axis* для предоставления входных данных для [пакета SDK для](https://docs.unity3d.com/Manual/OculusControllers.html), [пакета SDK опенвр](https://docs.unity3d.com/Manual/OpenVRControllers.html) и Windows Mixed Reality, включая руки и контроллеры движения. Если приложение использует эти API для ввода данных, оно может легко поддерживать контроллеры движения в нескольких пакетах SDK XR, включая Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Получение состояния нажатия логической кнопки

Чтобы использовать общие интерфейсы API ввода Unity, обычно начнем с привязки кнопок и осей к логическим именам в [диспетчере ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязывая идентификаторы кнопок или осей к каждому имени. Затем можно написать код, ссылающийся на эту логическую кнопку или имя оси.

Например, чтобы связать кнопку триггера левого контроллера движения с действием Отправить, перейдите в меню **правка > параметры проекта > входные данные** в Unity и разверните свойства раздела отправить в разделе оси. Измените **положительную кнопку** или свойство **положительной кнопки Alt** , чтобы прочесть **игровую кнопку 14**, например:

![InputManager Unity](images/unity-input-manager.png)<br>
*InputManager Unity*

Затем скрипт может проверить действие отправки с помощью *input. OnButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Можно добавить дополнительные логические кнопки, изменив свойство **size** в разделе **оси**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Непосредственное получение состояния нажатия физической кнопки

Можно также получить доступ к кнопкам вручную по полному имени с помощью *input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Получение объекта руки или контроллера движения

Вы можете получить доступ к положению и повороту контроллера с помощью *XR. Инпуттраккинг*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Обратите внимание, что это представляет собой захват контроллера (где пользователь удерживает контроллер), который полезен для отрисовки технологий или оружия в руки пользователя или модели самого контроллера.

Обратите внимание, что связь между этим захватом и указателем (где накладывается кончик контроллера) может отличаться в разных контроллерах. На данный момент доступ к элементу указателя контроллера может осуществляться только через API ввода, характерный для MR, описанный в следующих разделах.

## <a name="windows-specific-apis-xrwsainput"></a>Интерфейсы API для Windows (XR. Головк. Входной

**Пространство имен:** *UnityEngine. XR. WSA. Input*<br>
**Типы**: *интерактионманажер*, *интерактионсаурцестате*, *интерактионсаурце*, *интерактионсаурцепропертиес*, *InteractionSourceKind*, *InteractionSourceLocation*

Чтобы получить более подробные сведения о вводе-выделе Windows Mixed Reality (для HoloLens) и контроллеров движения, можно выбрать использование пространственных входных API Windows в пространстве имен *UnityEngine. XR. WSA. Input* . Это позволяет получить доступ к дополнительным сведениям, таким как точность расположения или тип источника, что позволяет сообщать о руки и контроллерах.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Опрос состояния движений и контроллеров движения

Вы можете опросить состояние этого кадра для каждого источника взаимодействия (вручную или контроллера движения) с помощью метода *жеткуррентреадинг* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Каждый *интерактионсаурцестате* , который вы получаете назад, представляет источник взаимодействия на текущий момент времени. *Интерактионсаурцестате* предоставляет такие сведения:
* Какие [виды нажатия](../../design/motion-controllers.md) происходят (выбор/меню, распечатка, Сенсорная панель или аналоговый стик)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Другие данные, относящиеся к контроллерам движения, таким как координаты и/или ТОЧЕЧный стик, а также затронутое состояние

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* Интерактионсаурцекинд, чтобы выяснить, является ли источник рукой или контроллером движения

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Опрос для перенаправляемых прогнозов отрисовки

* При опросе данных об источнике взаимодействия от рук и контроллеров, получаемые вами данные будут перенаправлены на момент времени, когда фотоны этого кадра будет достигнуть глаз пользователя.  Эти перенаправленные объекты лучше использовать для **подготовки к просмотру** контроллера или удерживаемого объекта в каждом кадре.  Если вы нажимаете на контроллере любую нажатие или выпуск, это будет наиболее точным, если вы используете API событий предыстории, описанные ниже.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Вы также можете получить в этом текущем фрейме объект с прямым прогнозированием.  Как и в случае с исходной версией, это полезно для **отрисовки** курсора, хотя нацеливание на заданную клавишу или выпуск будет наиболее точным, если вы используете интерфейсы API событий с предысторией, описанные ниже.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Обработка событий источника взаимодействия

Чтобы обрабатывались входные события, происходящие с точными данными предыстории, вместо опроса можно использовать события источника взаимодействий.

Для управления событиями источника взаимодействия:
* Регистрация для события ввода *интерактионманажер* . Для каждого интересующего вас типа события взаимодействия необходимо подписываться на него.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Обработайте событие. После подписки на событие взаимодействия вы получите обратный вызов при необходимости. В примере *саурцепрессед* это произойдет после обнаружения источника и до его освобождения или потери.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Как прерывать обработку события

Если вы больше не заинтересованы в событии или удаляете объект, подписанный на событие, необходимо отменить обработку события. Чтобы прерывать обработку события, отказаться от подписки на событие.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Список событий источника взаимодействия

Доступные события источника взаимодействия:
* *Интерактионсаурцедетектед* (источник стал активным)
* *Интерактионсаурцелост* (неактивен)
* *Интерактионсаурцепрессед* (TAP, нажатие кнопки или "Select" распространенная)
* *Интерактионсаурцерелеасед* (окончание касания, кнопка отжата или конец "Select" распространенная)
* *Интерактионсаурцеупдатед* (перемещение или иным образом изменяет некоторое состояние)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>События для исторических целей, которые наиболее точно соответствуют нажатию или выпуску

API-интерфейсы опроса, описанные выше, предоставляют приложению перенаправление прогнозов.  Хотя эти прогнозируемые объекты лучше всего подходят для подготовки к просмотру контроллера или виртуального карманного объекта, будущие элементы не оптимальны для нацеливания, по двум основным причинам:
* Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс задержки беспроводной сети через Bluetooth, прежде чем система получит нажатие.
* Затем, если вы используете прямую прогнозную единицу, будет использоваться еще 10-20 мс прямого прогноза, который будет применяться к моменту, когда фотоны текущего кадра достигнет глаза пользователя.

Это означает, что опрос дает вам исходную позицию или головной элемент, который составляет 30 – 40ms вперед от того места, где головка пользователя и руки в действительности были возвращены при нажатии или выпуске.  Для входных данных HoloLens, в то время как нет задержки беспроводной передачи, существует аналогичная задержка обработки для обнаружения нажатия.

Чтобы правильно ориентироваться в зависимости от первоначальной цели пользователя или нажатия контроллера, следует использовать источник с предысторией или головной элемент из этого события ввода *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* .

Вы можете выбрать пресс или Release с предысторией данных из заголовка пользователя или контроллера:
* В момент, когда произошло нажатие жеста или контроллера, эта головная программа может быть **использована для определения** того, что именно [облаками](../../design/gaze-and-commit.md) пользователь:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* Исходная ошибка в момент, когда произошло нажатие кнопки контроллера движения, которое можно использовать для определения **нацеливания** пользователя на контроллер.  Это будет состояние контроллера, на котором нажимается клавиша.  Если вы создаете сам контроллер, то можете запросить объект a, а не захват, чтобы прокрутить целевой луч от того, что пользователь будет рассматривать как естественный Совет этого отображаемого контроллера:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Пример обработчиков событий

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Интерфейсы API составных жестов высокого уровня (GestureRecognizer)

**Пространство имен:** *UnityEngine. XR. WSA. Input*<br>
**Типы**: *GestureRecognizer*, *жестуресеттингс*, *интерактионсаурцекинд*

Приложение может также распознать составные жесты более высокого уровня для пространственных источников входных данных, коснуться, удерживать, манипуляции и жесты навигации. Эти составные жесты можно распознавать как в движении, [так и в](../../design/gaze-and-commit.md#composite-gestures) [контроллерах движения](../../design/motion-controllers.md) с помощью GestureRecognizer.

Каждое событие жеста в GestureRecognizer предоставляет Саурцекинд для входных данных, а также целевой заголовочный элемент на момент события. Некоторые события предоставляют дополнительные сведения, относящиеся к контексту.

Для записи жестов с помощью распознавателя жестов требуется всего несколько действий:
1. Создание нового распознавателя жестов
2. Укажите, какие жесты следует отслеживать
3. Подписываться на события для этих жестов
4. Начать запись жестов

### <a name="create-a-new-gesture-recognizer"></a>Создание нового распознавателя жестов

Чтобы использовать *GestureRecognizer*, необходимо создать *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Укажите, какие жесты следует отслеживать

Укажите, какие жесты вы хотите использовать с помощью *сетрекогнизаблежестурес ()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Подписываться на события для этих жестов

Подпишитесь на события для интересующих вас жестов.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Жесты навигации и манипуляции являются взаимоисключающими в экземпляре *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Начать запись жестов

По умолчанию *GestureRecognizer* не отслеживает входные данные до тех пор, пока не будет вызван *старткаптурингжестурес ()* . Возможно, что событие жеста может быть создано после вызова *стопкаптурингжестурес ()* , если входные данные были выполнены до того, как был обработан *стопкаптурингжестурес ()* . *GestureRecognizer* будет запоминать, была ли она включена или отключена во время предыдущего кадра, в котором он действительно выполнялся, и таким образом, чтобы обеспечить возможность запуска и остановки мониторинга жестов на основе целевых объектов взгляда.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Завершение записи жестов

Чтобы отключить распознавание жестов, сделайте следующее:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Удаление распознавателя жестов

Не забудьте отказаться от подписки на подписанные события перед уничтожением объекта *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Подготовка модели контроллера движения к просмотру в Unity

![Модель контроллера движения и телеперенос](images/motioncontrollertest-teleport-1000px.png)<br>
*Модель контроллера движения и телеперенос*

Для подготовки к просмотру в приложении контроллеров движения, соответствующих физическим контроллерам, которые хранятся и обрабатываются при нажатии различных кнопок, можно использовать **prefab мотионконтроллер** в [наборе средств Mixed Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Этот prefab динамически загружает правильную модель Глтф во время выполнения из установленного в системе драйвера контроллера движения.  Важно динамически загружать эти модели, а не импортировать их вручную в редакторе, чтобы приложение показывало физически точную трехмерную модель для всех существующих и будущих контроллеров, которые могут иметь пользователи.

1. Следуйте инструкциям по [Начало работы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) , чтобы скачать набор средств для смешанной реальности и добавить его в проект Unity.
2. Если вы заменили камеру на *микседреалитикамерапарент* prefab в рамках начало работы действий, то можете продолжить!  Этот prefab включает визуализацию контроллера движения.  В противном случае добавьте *Assets/холотулкит/input/Prefabs/мотионконтроллерс. prefab* в сцену из области проекта.  Вам потребуется добавить prefab в качестве дочернего объекта для того, чтобы перемещать камеру, когда у пользователя есть телепередачи в пределах сцены, чтобы контроллеры поступали вместе с пользователем.  Если ваше приложение не предусматривает телеперенос, просто добавьте prefab в корень сцены.

## <a name="throwing-objects"></a>Создание вызывающих объектов

Создание объектов в Virtual Reality усложняется, и это может показаться на первый взгляд. Как и в случае с наиболее частыми взаимодействиями, когда вызов в игре происходит непредвиденным образом, он немедленно становится очевидным и нарушается. Мы тратили некоторое время на обдумывание того, как представить физически правильное поведение при вызове и получили несколько рекомендаций, включенных через обновления нашей платформы, которые мы хотели бы поделиться с вами.

Вы можете найти пример того, как мы рекомендуем реализовать [это](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)создание. Этот пример соответствует следующим четырем рекомендациям:
* **Используйте *скорость* контроллера вместо расположения**. В ноябре-обновлении Windows мы предоставили изменение в поведении, когда в [позиционированном состоянии отслеживания "приближено](../../design/motion-controllers.md#controller-tracking-state)". В этом состоянии информация о скорости контроллера будет по-прежнему отображаться до тех пор, пока мы считаем, что он имеет высокую точность, что часто бывает дольше, чем в положении.
* **Внедрение *угловой скорости* контроллера**. Эта логика хранится в `throwing.cs` файле в `GetThrownObjectVelAngVel` статическом методе в связанном выше пакете.
   1. По мере того, как угловая скорость сохраняется, создаваемый объект должен поддерживать ту же угловую скорость, что и в момент создания: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Поскольку центр массы создаваемого объекта, скорее всего, не находится на происхождении захвата, он, вероятно, имеет другую скорость, а контроллер в кадре ссылки пользователя. Часть скорости объекта, созданная таким образом, является мгновенно отношения скоростью центра массы создаваемого объекта по отношению к источнику контроллера. Отношения скорость — это перекрестное произведение угловой скорости контроллера с вектором, представляющим расстояние между источником контроллера и центром массы создаваемого объекта.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. Общая скорость создаваемого объекта, таким образом, является суммой скорости контроллера и этой отношения скорости: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Обратите особое внимание на *время* , когда мы применяем скорость**. При нажатии кнопки может потребоваться до 20 мс для этого события, чтобы это событие было переработано с помощью Bluetooth к операционной системе. Это означает, что если вы опрашиваете изменение состояния контроллера с нажатия на не нажато или наоборот, сведения об этом контроллере, которые вы получаете вместе с ним, на самом деле будут находиться впереди этого изменения в состоянии. Кроме того, контроллер, представленный нашим API-интерфейсом опроса, передается в прогноз, чтобы отразить, что в момент отображения кадра может быть больше 20 мс в будущем. Это хорошо подходит для *визуализации* удерживаемых объектов, но создает *задачу по времени для объекта* , так как мы вычисляем траекторию на момент, когда пользователь выпустил свое исключение. К счастью, при обновлении за Ноябрьское событие при отправке события Unity, такого как *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* , состояние включает данные предыстории с обратной стороны, когда кнопка была на самом деле нажата или освобождена.  Чтобы получить наиболее точную визуализацию контроллера и нацеливание контроллера во время возникновения исключения, необходимо правильно использовать опрос и события, если это уместно:
   * Для **отрисовки** каждого кадра на контроллере приложение должно располагать *GameObject* контроллера на переphotonном контроллере в течение текущего кадра.  Эти данные можно получить из API опроса Unity, например *[XR. Инпуттраккинг. Жетлокалпоситион](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или *[XR. Головк. Входные данные. Интерактионманажер. Жеткуррентреадинг](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Для **нацеливания контроллера** на нажатие или выпуск ваше приложение должно райкаст и вычислять траекторий на основе данных о том, что такое событие выпусков.  Эти данные можно получить из API-интерфейсов Unity, таких как *[интерактионманажер. интерактионсаурцепрессед](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Использование захвата**. Угловая скорость и скорость отмечаются относительно захвата, а не указателя.

Порождение продолжит совершенствоваться с будущими обновлениями Windows, и вы сможете найти дополнительные сведения здесь.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Жесты и контроллеры движения в МРТК v2

Вы можете получить доступ к жестам и контроллеру движения из диспетчера ввода.
* [Жест в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Контроллер движения в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Обучение по руководствам

Пошаговые учебники с более подробными примерами настройки доступны в Academyе Mixed Reality:

- [211. Ввод в смешанной реальности: жест](tutorials/holograms-211.md)
- [213. Ввод в смешанной реальности: контроллеры движения](../../deprecated/mixed-reality-213.md)

[![MR-вход 213 — контроллер движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR-вход 213 — контроллер движения*

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK. Отсюда вы можете перейти к следующему стандартному блоку:

> [!div class="nextstepaction"]
> [Отслеживание рук и взгляда](hand-eye-in-unit.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также статью

* [Направление головы и фиксация](../../design/gaze-and-commit.md)
* [Контроллеры движения](../../design/motion-controllers.md)
