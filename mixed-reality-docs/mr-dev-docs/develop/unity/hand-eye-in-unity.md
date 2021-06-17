---
title: Взгляд на руки и отслеживание глаз в Unity
description: Узнайте о двух основных способах выполнения действий с взглядом в Unity, а также жестами и контроллерами движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, вход, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств для смешанной реальности
ms.openlocfilehash: 2daa02a0681fe4f3da24fa32379e10877750af7e
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110225"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Взгляд на руки и отслеживание глаз в Unity

В HoloLens 2 появились новые и интересные возможности, такие как отслеживание с учетом особенностей и глаз.

Самый простой способ использовать новую возможность в Unity — МРТК. Также есть несколько примеров сцен, которые помогут вам приступить к работе.

* [Приступая к работе с формулировкой руки в МРТК](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Начало работы с отслеживанием взгляда в МРТК](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Стандартные блоки, поддерживающие руки, глаза и др. в МРТК

МРТК v2 предоставляет набор элементов управления пользовательского интерфейса и стандартных блоков, помогающих ускорить разработку.

|  [![Кнопка](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Кнопка](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [Ограничивающий](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [ ![ ограничивающий](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) прямоугольник | [Обработчик манипуляций](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) обработчика [ ![ манипуляций](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Элемент управления "Кнопка", поддерживающий различные методы ввода, включая HoloLens2's с определенными руками | Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве. | Скрипт для манипулирования объектами одной или двумя руками. |
|  [![Грифель](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Грифель](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Системная клавиатура](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Системная клавиатура](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Интерактивный объект](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Интерактивный объект](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| Двухмерная плоскость, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки | Пример скрипта для использования системной клавиатуры в Unity.  | Скрипт, обеспечивающий взаимодействие с объектами, с поддержкой визуальных состояний и тем. |
|  [![Решатель](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Решатель](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Коллекция объектов](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Коллекция объектов](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![Подсказка](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [Подсказка](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей | Скрипт для размещения массива объектов в трехмерной фигуре | Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для пометки контроллеров движения и объекта. |
|  [![Панель приложения](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [Панель приложения](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![Указатели](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Указатели](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Визуализация с использованием кончика пальца](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Визуализация с использованием кончика пальца](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Пользовательский интерфейс для активации ограничивающего прямоугольника вручную | Сведения о различных типах указателей. | Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии |
|  [![Отслеживание взгляда: выбор цели](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Отслеживание взгляда: выбор цели](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Отслеживание взгляда: навигация](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Отслеживание взгляда: навигация](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене. | Узнайте, как выполнять автоматическую прокрутку текста или увеличить содержимое с учетом того, что вы ищете| Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении |

## <a name="example-scenes"></a>Примеры сцен

Узнайте о различных типах взаимодействий и элементов управления пользовательского интерфейса MRTK с помощью [этого примера сцены](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

Другие примеры сцен можно найти в разделе **Assets/микседреалититулкит. examples/демонстрационные материалы** в [GitHub с набором средств для смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Пример сцены](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core. Отсюда вы можете перейти к следующему стандартному блоку:

> [!div class="nextstepaction"]
> [Пространственное сопоставление](spatial-mapping-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также раздел

* [Взаимодействие на основе глаз](../../design/eye-gaze-interaction.md)
* [Отслеживание глаз в HoloLens 2](../../design/eye-tracking.md)
* [Взгляд и фиксация](../../design/gaze-and-commit.md)
* [Руки: непосредственное манипулирование](../../design/direct-manipulation.md)
* [Руки: жесты](../../design/gaze-and-commit.md#composite-gestures)
* [Руки: наведение и фиксация](../../design/point-and-commit.md)
* [Инстинктивное взаимодействие](../../design/interaction-fundamentals.md)
* [Контроллеры движения](../../design/motion-controllers.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)