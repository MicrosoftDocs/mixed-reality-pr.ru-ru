---
title: Общие сведения об MRTK. Как с помощью Mixed Reality Toolkit для Unity выполнять стандартные пространственные взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Как с помощью Набора средств Unity для смешанной реальности выполнять базовые операции взаимодействия (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, проектирование, пример приложения, средства управления, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677534"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>Общие сведения об MRTK. Как использовать Mixed Reality Toolkit в Unity для реализации стандартных пространственных взаимодействий
![MRTK](images/MRTK101/MRTK101Cover.png)

Сведения о том, как использовать МRТК для достижения некоторых распространенных моделей взаимодействия в смешанной реальности.

- Как имитировать входные взаимодействия в редакторе Unity?
- Как взять и переместить объект?
- Как изменить размер объекта?
- Как аккуратно переместить или повернуть объект?
- Как сделать, чтобы объект реагировал на входные события?
- Как добавить визуальный отклик?
- Как добавить звуковой отклик?
- Как использовать заготовки кнопок в стиле HoloLens 2?
- Как сделать, чтобы объект следовал за вами?
- Как сделать, чтобы объект поворачивался к вам?

> [!NOTE]
> Эта статья была обновлена с учетом изменений в [выпуске MRTK версии 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).

Все содержимое на этой странице можно протестировать в редакторе Unity с имитацией ввода MRTK. Если вы еще не сделали этого, выполните инструкции из [руководства по установке MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), чтобы установить последнюю версию MRTK.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>Как имитировать входные взаимодействия в редакторе Unity?
МRТК поддерживает имитацию входных данных в редакторе. Просто запустите сцену, нажав кнопку воспроизведения в Unity. Следующие клавиши позволяют имитировать входные данные.
Чтобы переместить камеру, нажимайте клавиши W, A, S, D.
Чтобы посмотреть по сторонам, перемещайте мышь при нажатой правой кнопке мыши.
Чтобы имитировать поднятие рук вверх, нажмите клавишу пробела (для правой руки) или левую клавишу SHIFT (для левой руки). Чтобы имитировать удержание рук в зоне видимости, нажмите клавишу "T" или "Y", а чтобы имитировать поворот рук, нажимайте клавиши "Q" и "E" (горизонтально) или "R" и "F" (вертикально).

- [Дополнительные сведения об имитации входных данных см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a>Как взять и переместить объект?
Чтобы объект поддерживал захват и перемещение, назначьте ему следующие два скрипта: **ObjectManipulator.cs** и **NearInteractionGrabbable.cs** (для прямого захвата при отслеживании ввода с помощью рук). ObjectManipulator поддерживает как близкие, так и дальние взаимодействия. Вы можете захватить и переместить объект с использованием ввода с помощью рук в HoloLens 2 (ближнее), телекинеза (дальнее), сигнала контроллера движения (дальнее), курсора взгляда HoloLens, а также касания (дальнее).

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>Как изменить размер объекта?
**ObjectManipulator.cs** поддерживает масштабирование и вращение двумя руками. Это работает с разными типами входных данных, например ввод с помощью рук в HoloLens 2, ввод с помощью взгляда и жестов в HoloLens 1 или контроллера движений иммерсивной гарнитуры в Windows Mixed Reality.

- [Дополнительные сведения о компоненте Object Manipulator см. в документации по MRTK.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Как аккуратно переместить или повернуть объект?
Назначьте **BoundsControl.cs** объекту для использования ограничивающего прямоугольника, который представляет собой интерфейс для масштабирования и вращения объекта. По умолчанию в нем отображаются синие маркеры и границы, как в HoloLens 1. Чтобы использовать анимированные маркеры с учетом расстояния до объекта в стиле HoloLens 2, необходимо назначить заготовки и материалы. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [Дополнительные сведения о компоненте Bounds Control см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>Как сделать, чтобы объект реагировал на входные события?
Назначьте **PointerHandler.cs** объекту. В инспекторе вы сможете применить события OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Чтобы использовать эти события в скрипте, реализуйте **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Дополнительные сведения о системе ввода см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Как добавить визуальный отклик?
Назначьте **Interactable.cs** объекту. В инспекторе добавьте целевой объект и создайте тему. С помощью интерактивных профилей темы вы сможете легко добавить визуальный отклик для всех доступных состояний взаимодействий ввода.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Интерактивный объект предоставляет несколько типов тем, в том числе тему shader, которая позволяет управлять параметрами текстуры для каждого состояния взаимодействия.

- [Дополнительные сведения об интерактивном объекте см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Еще один важный строительный блок для создания визуального отклика — **стандартный шейдер MRTK**. С помощью шейдера MRTK Standard можно легко добавлять визуальные эффекты для отклика, например эффект указателя и подсветки при приближении. Стандартный шейдер MRTK выполняет намного меньше вычислений, чем стандартный шейдер Unity, поэтому позволяет создать высокопроизводительную среду взаимодействия.

Создайте новый материал и выберите шейдер Mixed Reality Toolkit > Standard (Набор средств для смешанной реальности > Стандартный). Вы также можете выбрать любой из существующих материалов, для которых настроен стандартный шейдер MRTK.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Дополнительные сведения о стандартном шейдере MRTK см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Как добавить звуковой отклик?
Поместите **AudioSource** в объект. Затем в скриптах, которые предоставляют нужные события ввода (например, Interactable.cs или PointerHandler.cs), назначьте объекту с AudioSource событие и выберите **AudioSource.PlayOneShot()** . Вы можете использовать собственные звуковые клипы или выбрать подходящий из числа звуковых активов MRTK.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>Как использовать заготовки кнопок в стиле HoloLens 2?
MRTK предоставляет несколько типов кнопок в стиле оболочки (ОС) HoloLens 2. Они поддерживают сложные типы визуального отклика, например подсветка при приближении, прямоугольник сжатия и эффект ряби на поверхности кнопки, которые упрощают взаимодействие для пользователя.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

Вам нужно лишь перетащить любую из **заготовок нажимаемых кнопок в стиле HoloLens 2** в сцену. В заготовках используется описанный выше Interactable.cs. Вы можете предоставлять в интерактивном объекте события для запуска действий, например OnClick().

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Дополнительные сведения о заготовках кнопок см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>Как сделать, чтобы объект следовал за вами?
Назначьте скрипт **RadialView.cs** или **Follow.cs** объекту. Это часть целой серии скриптов Solver, которые позволяют использовать разные типы размещения объектов в трехмерном пространстве. **SolverHandler.cs** будет добавлен автоматически.
Ниже вы видите пример конфигурации RadialView, которая позволяет добиться поведения "ленивое следование", например начальное меню в оболочке HoloLens. Вы можете указать минимальную и максимальную дистанцию, а также минимальный и максимальный угол обзора. В следующем примере представлен объект с расстоянием от 0,4 до 0,8 м и диапазоном углов 15°. Измените значение параметра Lerp Time (Время линейной интерполяции), чтобы изменение положения выполнялось быстрее или медленнее.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Дополнительные сведения о инструменте решения см. в документации по МRТК.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>Как сделать, чтобы объект поворачивался к вам?
Назначьте скрипт **Billboard.cs** объекту. Теперь этот объект всегда будет развернут к вам, независимо от вашего положения. Вы можете указать расположение оси вращения.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Вы готовы создать великолепные взаимодействия для смешанной реальности? Изучите предложенные ниже страницы, чтобы получить дополнительные сведения об MRTK и смешанной реальности.

## <a name="about-the-author"></a>Об авторе

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Дон Юн Парк</b> (Dong Yoon Park)<br>Разработчик средств взаимодействия с пользователем @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK. Отсюда вы можете перейти к следующему стандартному блоку: 

> [!div class="nextstepaction"]
> [Камера](camera-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также раздел
* [Руководство по установке MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Набор средств для смешанной реальности (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub
* [Портал документации по MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Рекомендации по переносу кода с HoloToolKit на MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
