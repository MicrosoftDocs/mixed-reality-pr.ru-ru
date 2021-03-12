---
title: Взгляд на руки и отслеживание глаз в Unity
description: Узнайте о двух основных способах выполнения действий с взглядом в Unity, а также жестами и контроллерами движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, вход, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств для смешанной реальности
ms.openlocfilehash: ac122a0353bc5a35202c9aeba0d27c489b72fd68
ms.sourcegitcommit: 6ae047bf0d78819ee68681f7d9450961efbc8595
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103022876"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Взгляд на руки и отслеживание глаз в Unity

В HoloLens 2 появились новые и интересные возможности, такие как отслеживание с учетом особенностей и глаз.

Самый простой способ использовать новую возможность в Unity — МРТК. Также есть несколько примеров сцен, которые помогут вам приступить к работе.

* [Приступая к работе с формулировкой руки в МРТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/hand-tracking.md)
* [Начало работы с отслеживанием взгляда в МРТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Стандартные блоки, поддерживающие руки, глаза и др. в МРТК 

МРТК v2 предоставляет набор элементов управления пользовательского интерфейса и стандартных блоков, помогающих ускорить разработку.

|  [Кнопка](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) [ ![ кнопки](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) | [Ограничивающий](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) [ ![ ограничивающий](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) прямоугольник | [Обработчик манипуляций](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) обработчика [ ![ манипуляций](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| Элемент управления "Кнопка", поддерживающий различные методы ввода, включая HoloLens2's с определенными руками | Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве | Скрипт для манипулирования объектами с одной или двумя руки |
|  [Содержание](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) [ ![ планшета](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) | Системная [Клавиатура системной](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) [ ![ клавиатуры](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) | [ ![ Взаимодействие с](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) взаимодействием [](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) |
| Двухмерная плоскость, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки | Пример сценария использования системной клавиатуры в Unity  | Скрипт, обеспечивающий взаимодействие объектов с визуальными состояниями и поддержкой тем |
|  [ ![ Поиск решения](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) [](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) | [Коллекция объектов](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) [ ![ коллекции объектов](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) | [Подсказка](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) [ ![ подсказки](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) |
| Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей | Скрипт для размещения массива объектов в трехмерной фигуре | Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для пометки контроллеров движения и объекта. |
|  [Панель приложения](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) [ ![ панели приложений](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) | [Указатели](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) [ ![ указателей](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) | [ ![ ](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) Высокоудобное [Графическое](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) представление |
| Пользовательский интерфейс для активации ограничивающего прямоугольника вручную | Дополнительные сведения о различных типах указателей | Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии |
|  [ ![ Отслеживание глаз: отслеживание выбора целевого объекта](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) [: Выбор целевого объекта](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) | [ ![ Отслеживание взгляда:](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) [Отслеживание взгляда](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) на навигацию: Навигация | [ ![ Отслеживание глаз: отслеживание глаз на тепловой карте](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [: тепловая схема](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене. | Узнайте, как выполнять автоматическую прокрутку текста или увеличить содержимое с учетом того, что вы ищете| Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении |

## <a name="example-scenes"></a>Примеры сцен

Изучите различные типы взаимодействий и элементов управления пользовательского интерфейса МРТК в [этом примере сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Другие примеры сцен можно найти в разделе **Assets/микседреалититулкит. examples/демонстрационные материалы** в [GitHub с набором средств для смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Пример сцены](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples.md)

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
