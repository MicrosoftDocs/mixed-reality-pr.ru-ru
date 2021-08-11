---
title: Обзор решателя
description: Обзор решателей в MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK, решатели Solver,
ms.openlocfilehash: 28e961aa20fb15b533f369ed436e2d8178d682801f6f6ce6a703e53a0c26ac01
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206915"
---
# <a name="solver-overview"></a>Обзор решателя

![Решатель — главная](../../images/solver/MRTK_Solver_Main.png)

Решатели — это компоненты, которые упрощают вычисление положения и ориентации объекта в соответствии с предопределенным алгоритмом. Примером использования может быть расположение предмета на поверхности, на которую устремлен взгляд пользователя в конкретный момент.

Кроме того, система поиска решений детерминированно определяет порядок операций для этих вычислений преобразования, так как другого надежного способа указать для Unity порядок обновления компонентов как не существует.

Решатели предлагают ряд вариантов поведения для присоединения объектов к другим объектам или системам. Еще один пример — закрепленный объект, который парит перед пользователем (на основе положения камеры). Решатель можно также подключить к контроллеру и объекту, чтобы закрепить объект у контроллера. Все решатели можно безопасно собрать вместе, например, закрепление + поверхностный магнетизм + импульс.

## <a name="how-to-use-a-solver"></a>Использование решателей

Система решателей состоит из трех категорий сценариев:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): базовый абстрактный класс, от которого наследуются все решатели. Он обеспечивает отслеживание состояния, параметры сглаживания и их реализацию, автоматическую интеграцию системы решателей и порядок обновления.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): задает опорный объект для отслеживания (например: трансформация основной камеры, телекинез и т. д.), обеспечивает сбор компонентов решателя и выполняет их обновление в нужном порядке.

Третья категория — это сам решатель. Стандартные блоки для основного поведения предоставляют следующие решатели:

* [`Orbital`](#orbital): фиксирует определенную позицию и смещение относительно объекта, на который ссылается.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): масштабируется, чтобы поддерживать постоянный размер относительно вида с объекта, на который ссылается.
* [`RadialView`](#radialview): удерживает объект в конусе просмотра объекта, на который ссылается.
* [`Follow`](#follow): удерживает объект внутри границ, заданных пользователем, объекта, на который ссылается.
* [`InBetween`](#inbetween): удерживает объект между двумя отслеживаемыми объектами.
* [`SurfaceMagnetism`](#surfacemagnetism): направляет лучи на поверхности в мире и выравнивает объект по этой поверхности.
* [`DirectionalIndicator`](#directionalindicator): определяет положение и ориентацию объекта как индикатор направления. С исходной позиции отслеживаемой цели SolverHandler этот индикатор будет ориентироваться на указанное целевое направление DirectionalTarget.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): применяет ускорение, скорость или трение для моделирования импульса и упругости для объекта, перемещаемого другими решателями или компонентами.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): определяет, что объект должен следовать за руками в области, в которой GameObject и руки не пересекаются. Это может быть полезно для ограниченного интерактивного содержимого, такого как меню и т. д. Этот решатель предназначен для работы с контроллером [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand), но работает и с [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): является производным от HandConstraint, но включает логику для проверки того, находится ли ладонь напротив пользователя перед активацией. Этот решатель работает только с контроллерами [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand). С другими типами контроллеров этот решатель будет вести себя так же, как и его базовый класс.

Чтобы использовать систему решателей, просто добавьте один из перечисленных выше компонентов в GameObject. Так как для всех решателей требуется сценарий [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), он будет создан Unity автоматически.

> [!NOTE]
> Примеры использования системы решателей можно найти в файле **SolverExamples.scene**.

## <a name="how-to-change-tracking-reference"></a>Изменение ссылки на отслеживание

Свойство *Tracked Target Type* (Тип отслеживаемой цели) компонента [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) определяет позицию, которую будут использовать все решатели для вычисления своих алгоритмов. Например, тип значения [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) с простым компонентом [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) приведет к созданию луча от головы по направлению взгляда пользователя для решения задачи, на какую поверхность луч будет направлен. Возможные значения свойства `TrackedTargetType`:

* *Head*: исходная позиция — преобразование основной камеры.
* *ControllerRay*: исходной позицией является преобразование [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) на контроллере (т. е. источник указателя на контроллере движения или ладони), указывающее направление линии лучей.
  * Используйте свойство `TrackedHandedness` для выбора руки (т. е. левая, правая, обе).
* *HandJoint*: исходной позицией является преобразование определенного сустава руки.
  * Используйте свойство `TrackedHandedness` для выбора руки (т. е. левая, правая, обе).
  * Используйте свойство `TrackedHandJoint`, чтобы определить, какое преобразование сустава нужно использовать.
* *CustomOverride*: исходная позиция из назначенного свойства `TransformOverride`.

> [!NOTE]
> Для типов *ControllerRay* и *HandJoint* решатель сначала попытается обратиться к левому контроллеру или преобразованию руки, а затем к правому, если левая сторона недоступна или если в свойстве `TrackedHandedness` не указано иное.

![Объект, отслеживаемый решателем](../../images/solver/TrackedObjectType-Example.gif) 
*Пример различных свойств, связанных с каждым TrackedTargetType*

> [!IMPORTANT]
> Большинство решателей используют вектор, направленный вперед, для отслеживаемой цели преобразования, который предоставляется `SolverHandler`. При использовании типа отслеживаемой цели *Hand Joint* вектор суставов ладони может указывать на пальцы, а не сквозь ладонь. Это зависит от платформы, предоставляющей данные о суставах руки. Для симуляции входных данных и Windows Mixed Reality это *вектор вверх*, который указывает сквозь ладонь (т. е. зеленый вектор — вверх, синий вектор — вправо).
>
> ![Вектор вперед вверх](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Чтобы устранить это, обновите свойство *Additional Rotation* (Дополнительное вращение), указав значение `SolverHandler` **<90; 0; 0>** . Это обеспечит направление вектора, подаваемого решателям, вперед через ладонь и обратно от руки.
>
> ![Дополнительное вращение](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> Кроме того, можно использовать тип отслеживаемой цели *Controller Ray*, чтобы получить аналогичное поведение при указании направления с помощью рук.

## <a name="how-to-chain-solvers"></a>Создание цепочки решателей

Можно добавить несколько компонентов `Solver` в один и тот же GameObject, чтобы связать их алгоритмы. Компоненты `SolverHandler` обрабатывают обновление всех решателей в одном GameObject. По умолчанию `SolverHandler` вызывает `GetComponents<Solver>()` при запуске, что будет возвращать решатели в том порядке, в котором они отображаются в инспекторе.

Более того, значение True для свойства *Updated Linked Transform* позволит `Solver` сохранить вычисленное положение, ориентацию и масштаб в промежуточную переменную, доступную всем решателям (т. е. `GoalPosition`). Если значение равно False, `Solver` обновляет преобразование GameObject напрямую. При сохранении свойств преобразования в промежуточном расположении другие решатели могут выполнять вычисления, начиная с промежуточной переменной. Это обусловлено тем, что Unity не допускает обновления gameObject.Transform в стеке внутри одного кадра.

> [!NOTE]
> Разработчики могут изменить порядок выполнения решателей, задав свойство `SolverHandler.Solvers` напрямую.

## <a name="how-to-create-a-new-solver"></a>Создание решателя

Все решатели должны наследоваться от абстрактного базового класса [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver). Основные требования расширения решателей включают переопределение метода `SolverUpdate`. В этом методе разработчики должны обновить унаследованные свойства `GoalPosition`, `GoalRotation` и `GoalScale` до нужных значений. Более того, обычно полезно использовать `SolverHandler.TransformTarget` в качестве системы отсчета, необходимой клиенту.

Приведенный ниже код содержит пример нового компонента решателя `InFront`, который помещает присоединенный объект на 2 метра вперед от `SolverHandler.TransformTarget`. Если объект `SolverHandler.TrackedTargetType` задан клиентом как [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), тогда `SolverHandler.TransformTarget` будет преобразованием камеры, а этот решатель разместит присоединенный GameObject на расстоянии 2 м перед каждым кадром.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Руководства по реализации решателей

### <a name="common-solver-properties"></a>Общие свойства решателей

Каждый компонент решателя имеет основной набор идентичных свойств, управляющих основным поведением решателя.

Если включен параметр *Smoothing*, решатель постепенно обновит преобразование GameObject с учетом вычисленных значений. Скорость этого изменения определяется свойством *LerpTime* каждого компонента преобразования. Например, более высокое значение *MoveLerpTime* приведет к более медленному приращению движения между кадрами.

Если включен параметр *MaintainScale*, то решатель будет использовать локальный масштаб GameObject по умолчанию.

![Основные свойства решателей](../../images/solver/GeneralSolverProperties.png)  
*Общие свойства, унаследованные всеми компонентами решателей*

### <a name="orbital"></a>Orbital

Класс [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) является компонентом закрепления, который ведет себя как планеты в солнечной системе. Этот решатель обеспечит для присоединенных GameObject перемещение по орбите вокруг отслеживаемых преобразований. Таким образом, если для *типа отслеживаемой цели* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) задано значение [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), то GameObject будет перемещаться по орбите вокруг головы пользователя с фиксированным смещением.

Разработчики могут изменить это фиксированное смещение для сохранения меню и других компонентов сцены на уровне взгляда или пояса и т. д. вокруг пользователя. Это можно сделать, изменив свойства локального смещения *Local Offset* и смещения мира *World Offset*. Свойство типа ориентации *Orientation Type* определяет поворот, применяемый к объекту: должен ли всегда сохраняться начальный поворот, поворот в камеру либо поворот на любой объект, определяемый преобразованием.

![Пример Orbital](../../images/solver/OrbitalExample.png)  
*Пример Orbital*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) — это еще один компонент с закреплением, который хранит определенную часть GameObject в усеченном конусе обзора пользователя.

Свойства *Min & Max View Degrees* (минимальный и максимальный угол обзора) определяют, как большая часть GameObject всегда отображается в представлении.

Свойства *Min & Max Distance* (минимальное и максимальное расстояние) определяют, насколько далеко должен находиться объект GameObject от пользователя. Например, если подойти к объекту GameObject на расстояние *Min Distance* в 1 м, то GameObject будет отталкиваться от камеры, потому что он не должен приближаться к пользователю ближе, чем на 1 м.

Как правило, [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) используется в сочетании с *типом отслеживаемой цели* [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), чтобы компонент следовал за взглядом пользователя. Однако этот компонент может сохраняться в *представлении* любого *типа отслеживаемой цели*.

![Пример RadialView](../../images/solver/RadialViewExample.png)  
*Пример RadialView*

### <a name="follow"></a>Follow

Класс [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) размещает элемент перед отслеживаемой целью относительно ее локальной оси вперед. Элемент может быть слабо ограничен (то есть закреплен), чтобы он не следовал за целью, пока она не переместится за пределы, указанные пользователем.

Он работает аналогично решателю RadialView и обладает дополнительными элементами для управления *максимальным горизонтальным и вертикальным углом* и механизмами изменения *ориентации* объекта.

![Свойства следования](../../images/solver/FollowExample.png)  
*Свойства следования*

![Сцена с примером следования](../../images/solver/FollowExampleScene.gif)  
*Сцена с примером следования (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

Класс [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) удерживает присоединенный GameObject между двумя преобразованиями. Эти две конечные точки преобразования определяются *типом отслеживаемой цели* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) объекта GameObject и свойством *Second Tracked Target Type* (Тип второй отслеживаемой цели) компонента [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween). Как правило, оба типа будут иметь значение [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride), а результирующие значения `SolverHandler.TransformOverride` и `InBetween.SecondTransformOverride` задаются для двух отслеживаемых конечных точек.

Во время выполнения компонент [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) создаст другой компонент [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) на основе *Second Tracked Target Type* и свойства *Second Transform Override*.

`PartwayOffset` определяет, где на линии между двумя преобразованиями должен располагаться объект: 0,5 на половине пути, 1,0 на первом преобразовании и 0,0 на втором преобразовании.

![Пример InBetween](../../images/solver/InBetweenExample.png)  
*Пример использования решателя InBetween для сохранения объекта между двумя преобразованиями*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) работает путем создания луча на поверхностях, заданных LayerMask, и размещения GameObject в точке контакта.

*Surface Normal Offset* (Смещение нормали поверхности) помещает GameObject на заданное расстояние на расстоянии в метрах от поверхности в направлении нормали в точке попадания на поверхности.

И наоборот, *Surface Ray Offset* (Смещение луча поверхности) помещает GameObject на заданное расстояние в метрах от поверхности, но в противоположном направлении создания луча. Таким образом, если луч создается по взгляду пользователя, то GameObject будет передвигаться ближе к линии от точки попадания на поверхности в камеру.

*Orientation Mode* (Режим ориентации) определяет тип поворота, который необходимо применить к нормали на поверхности.

* *None* — поворот не применяется.
* *TrackedTarget* — объект будет обращен к отслеживаемому преобразованию, движущему луч.
* *SurfaceNormal* — объект будет выравниваться по нормали в точке попадания на поверхности.
* *Blended* — объект будет выравниваться на основе нормали в точке попадания на поверхности и на основе обращения к отслеживаемому преобразованию.

Чтобы заставить связанный объект GameObject оставаться в вертикальном положении в любом режиме, кроме *None*, включите параметр *Keep Orientation Vertical* (Сохранять вертикальную ориентацию).

> [!NOTE]
> Свойство *Orientation Blend* (Смешение ориентации) используется для управления балансом между факторами поворота, если *Orientation Mode* (Режим ориентации) установлен в значение *Blended* (Смешанная). При значении 0,0 ориентация будет полностью управляться режимом *TrackedTarget*, а при значении 1,0 — режимом *SurfaceNormal*.

![Пример SurfaceMagnetism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Определение достигаемых поверхностей

При добавлении компонента [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) в GameObject важно рассмотреть слой GameObject и его дочерних элементов, если они есть. Компонент работает, выполняя различные типы пускания лучей, чтобы определить, к какой поверхности они должны "примагнититься". Если решатель GameObject имеет конфликт на одном из слоев, перечисленных в свойстве `MagneticSurfaces` `SurfaceMagnetism`, то луч, скорее всего, будет направлен сам на себя, в результате чего GameObject присоединится к своей собственной точке. Такого поведения можно избежать, задав для основного GameObject и всех дочерних элементов слой *Ignore Raycast* (Игнорирование луча) или изменив массив `MagneticSurfaces` в LayerMask соответствующим образом.

И наоборот, [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject не будет конфликтовать с областями на слое, не перечисленными в свойстве `MagneticSurfaces`. Обычно рекомендуется размещать все нужные поверхности на выделенном слое (т. е. *Surfaces*) и присваивать свойству `MagneticSurfaces` значения только этого слоя.  Использование значений *default* (по умолчанию) или *everything* (все) может привести к тому, что компоненты пользовательского интерфейса или курсоры будут влиять на решатель.

Наконец, поверхности, расположенные дальше, чем указано в значении свойства `MaxRaycastDistance`, будут игнорироваться лучами `SurfaceMagnetism`.

### <a name="directionalindicator"></a>DirectionalIndicator

Класс [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) является компонентом закрепления, который ориентируется в направлении нужной точки в пространстве.

Он чаще всего используется, если для *типа отслеживаемой цели* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) задано значение [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head). Таким образом, компонент UX с решателем [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) будет направлять пользователя на нужную точку в пространстве.

Требуемая точка в пространстве определяется с помощью свойства *Directional Target* (Целевое направление).

Если целевое направление доступно для просмотра пользователю или в [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) установлен какой-либо кадр позиции, решатель отключит все компоненты [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) под ним. Если направление не отображается, на индикаторе будет включено все.

Чем ближе пользователь будет к появлению *точки целевого направления* в поле зрения, тем меньше будет индикатор.

* *Min Indicator Scale* — минимальный масштаб для объекта индикатора.
* *Max Indicator Scale* — максимальный масштаб для объекта индикатора.

* *Visibility Scale Factor* — множитель для увеличения или уменьшения поля зрения, который определяет, где становится доступна точка *целевого направления*.
* *View Offset* — с точки зрения кадра позиции (т. е. возможно, самой камеры) это свойство определяет, насколько далеко в направлении индикатора должен находиться объект из центра окна просмотра.

![Свойства индикатора направления](../../images/solver/DirectionalIndicatorExample.png)  
*Свойства индикатора направления*

![Сцена с примером индикатора направления](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Сцена с примером индикатора направления (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Меню руки с HandConstraint и HandConstraintPalmUp

![Пример интерфейса меню руки](../../images/solver/MRTK_UX_HandMenu.png)

[`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) предоставляет решатель, который ограничивает отслеживаемый объект областью, безопасной для содержимого, ограничиваемого руками (например, пользовательский интерфейс, меню и т. д.). Безопасными считаются области, которые не пересекаются с рукой. Производный класс [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint), вызываемый [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp), также включен для демонстрации общего поведения активации объекта, отслеживаемого решателем, когда ладонь обращена к пользователю.

[См. страницу меню руки Hand Menu](../hand-menu.md), на которой приведены примеры использования решателей для ограничения руки (Hand Constraint) для создания меню.

## <a name="see-also"></a>См. также

* [Отслеживание рук](../../input/hand-tracking.md)
* [Взгляд](../../input/gaze.md)
