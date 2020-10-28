---
title: Взгляд на руки и отслеживание глаз в Unity
description: Существует два основных способа выполнения действий с вашим взглядом в Unity, жестами и контроллерами движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, входные данные
ms.openlocfilehash: b184cf1d9e6f35e3750015b51374058df79ed19d
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683240"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Взгляд на руки и отслеживание глаз в Unity

В HoloLens 2 появились новые и интересные возможности, такие как отслеживание с учетом особенностей и глаз.

Самый простой способ использовать новую возможность в Unity — МРТК v2. Также есть несколько примеров сцен, которые помогут вам приступить к работе.

* [Приступая к работе с наладонными руками в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Приступая к работе с отслеживанием взгляда в МРТК v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Стандартные блоки, поддерживающие руки, глаза и др. в МРТК v2

МРТК v2 предоставляет набор элементов управления пользовательского интерфейса и стандартных блоков, помогающих ускорить разработку.

|  [Кнопка](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [ ![ кнопки](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [Ограничивающий](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [ ![ ограничивающий](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) прямоугольник | [Обработчик манипуляций](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) обработчика [ ![ манипуляций](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Элемент управления "Кнопка", поддерживающий различные методы ввода, включая HoloLens2's с определенными руками | Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве | Скрипт для манипулирования объектами с одной или двумя руки |
|  [Содержание](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [ ![ планшета](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | Системная [Клавиатура системной](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [ ![ клавиатуры](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [ ![ Взаимодействие с](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) взаимодействием [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| плоскость двумерных стилей, которая поддерживает прокрутку с помощью клавиатуры с вытеканием руки | Пример сценария использования системной клавиатуры в Unity  | Скрипт, обеспечивающий взаимодействие объектов с визуальными состояниями и поддержкой тем |
|  [ ![ Поиск решения](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Коллекция объектов](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![ коллекции объектов](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Подсказка](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![ подсказки](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Различные поведения позиционирования объектов, такие как тег, блокировка тела, размер представления константы и магнит поверхностей поверхности | Скрипт для размещения массива объектов в трехмерной фигуре | Пользовательский интерфейс заметки с гибкой системой привязки и сведениями, который можно использовать для пометки контроллеров движения и объекта. |
|  [Панель приложения](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [ ![ панели приложений](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [Указатели](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [ ![ указателей](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [ ![ ](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) Высокоудобное [Графическое](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) представление |
| Пользовательский интерфейс для активации ограничивающего прямоугольника вручную | Дополнительные сведения о различных типах указателей | Визуальное взаимодействие с учетом того, что повышает уверенность в прямом взаимодействии |
|  [ ![ Отслеживание глаз: отслеживание выбора целевого объекта](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [: Выбор целевого объекта](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [ ![ Отслеживание взгляда:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) [Отслеживание взгляда](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) на навигацию: Навигация | [ ![ Отслеживание глаз: отслеживание глаз на тепловой карте](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [: тепловая схема](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Объедините глаза, голоса и руки, чтобы быстро и легко выбирать голограммы в сцене. | Узнайте, как выполнять автоматическую прокрутку текста или свободно изменять содержимое в зависимости от того, что вы ищете.| Примеры ведения журнала, загрузки и визуализации того, что пользователи просматривают в приложении |

## <a name="example-scenes"></a>Примеры сцен

Изучите различные типы взаимодействий и элементов управления пользовательского интерфейса МРТК в [этом примере сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Другие примеры сцен можно найти в разделе **Assets/микседреалититулкит. examples/демонстрационные материалы** в [GitHub с набором средств для смешанной реальности](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Пример сцены](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK. Отсюда вы можете перейти к следующему стандартному блоку:

> [!div class="nextstepaction"]
> [Пространственное сопоставление](spatial-mapping-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также статью

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
