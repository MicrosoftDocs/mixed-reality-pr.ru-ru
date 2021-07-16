---
title: Обновление с Холотулкит
description: миграция с HoloLens набор средств (хтк) на смешанную реальность набор средств (мртк).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, хтк,
ms.openlocfilehash: b54445dc5ca7a6c01c968929e243a1fc4ca2d107
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281755"
---
# <a name="upgrading-from-holotoolkit"></a>Обновление с Холотулкит

рекомендации по миграции с HoloLens набор средств (хтк) на смешанную реальность набор средств (мртк).

## <a name="controller-and-hand-input"></a>Контроллер и ввод вручную

### <a name="setup-and-configuration"></a>Установка и настройка

|         Методы                  | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Тип                      | Конкретные события для кнопок со сведениями о типе входных данных, если они актуальны. | Ввод на основе действия или жеста, передаваемый через события. |
| Настройка                     | Поместите InputManager в сцену. | Включите входную систему в [профиле конфигурации](../configuration/mixed-reality-configuration-guide.md) и укажите конкретный тип входной системы. |
| Параметр Configuration             | Настроено в инспекторе для каждого отдельного скрипта в сцене. | Настраивается с помощью входного системного профиля и связанного с ним профиля, приведенного ниже. |

Связанные профили:

* Профиль сопоставления контроллера смешанной реальности
* Профиль визуализации контроллера смешанной реальности
* Профиль жестов смешанной реальности
* Профиль входных действий смешанной реальности
* Профиль правил для входных действий смешанной реальности
* Профиль указателя смешанной реальности

Параметры [поставщика](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) будут изменены на объекте основной камеры в сцене.

компоненты поддержки платформы (например, Windows Mixed Reality диспетчер устройств) должны быть добавлены в соответствующие поставщики данных соответствующей службы.

### <a name="interface-and-event-mappings"></a>Сопоставления интерфейсов и событий

Некоторые события больше не имеют уникальных событий и теперь содержат [микседреалитинпутактион](../features/input/input-actions.md). Эти действия указываются в профиле входных действий и сопоставляются с определенными контроллерами и платформами в профиле сопоставления контроллеров. Теперь события `OnInputDown` должны проверять тип микседреалитинпутактион.

Связанные входные системы:

* [Общие сведения о входных данных](../features/input/overview.md)
* [Входные события](../features/input/input-events.md)
* [Входные указатели](../features/input/pointers.md)

| ХТК 2017 |  МРТК v2  | Сопоставление действий |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Сопоставлено с сенсорной панелью или аналоговый стик |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Сопоставлено с сенсорной панелью |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Сопоставлено с удержанием в профиле жестов |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Сопоставлено с кнопками контроллера или вручную коснуться |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Сопоставлено с манипуляцией в профиле жестов |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Сопоставлено с навигацией в профиле жестов |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Сопоставлено с позицией триггера |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) или [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Сопоставлено с позицией указателя или позицией захвата |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) или [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Сопоставлено с позицией указателя или позицией захвата |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) и [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Сопоставлено с различными кнопками контроллера и сумбстиккс |

## <a name="camera"></a>Камера

|        Методы                    | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | удалите маинкамера, добавьте микседреалитикамерапарент/микседреалитикамера/хололенскамера prefab в сцену **или** используйте смешанную реальность набор средств > настроить > применить сцену смешанной реальности Параметры пункт меню. | маинкамера, родительская микседреалитиплайспаце с помощью смешанной реальности набор средств > добавить в сцену и настроить... |
| Параметр Configuration             | Настройка параметров камеры, выполненная в экземпляре prefab. | Параметры камеры, настроенные в [профиле камеры смешанной реальности](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Речь

### <a name="keyword-recognition"></a>Распознавание ключевых слов

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Добавьте Спичинпутсаурце в сцену. | служба ключевых слов (например, Windows диспетчер речевого ввода) должна быть добавлена в поставщики данных входной системы. |
| Параметр Configuration             | Распознанные ключевые слова настраиваются в инспекторе Спичинпутсаурце. | Ключевые слова настраиваются в [профиле голосовых команд смешанной реальности](../features/input/speech.md). |
| Обработчики событий            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Диктовка

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Добавьте Диктатионинпутманажер в сцену. | для поддержки диктовки требуется служба (например, Windows "диспетчер ввода диктофона"), добавляемая в поставщики данных входной системы. |
| Обработчики событий            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Поддержка пространственной информации и сопоставление

### <a name="mesh"></a>Сетка

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Добавьте prefab Спатиалмаппинг в сцену. | включите систему пространственной осведомленности в профиле конфигурации и добавьте пространственный наблюдатель (например, наблюдатель пространственной сетки Windows Mixed Reality) к поставщикам данных системы пространственной связи. |
| Параметр Configuration             | Настройте экземпляр сцены в инспекторе. | Настройте параметры для каждого профиля пространственного наблюдателя. |

### <a name="planes"></a>Плоскост

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Используйте `SurfaceMeshesToPlanes` скрипт. | Еще не реализовано. |

### <a name="spatial-understanding"></a>Пространственное понимание

|       Методы                      | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Добавьте prefab Спатиалундерстандинг в сцену. | Еще не реализовано. |
| Параметр Configuration             | Настройте экземпляр сцены в инспекторе. | Еще не реализовано. |

## <a name="boundary"></a>Граница

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Добавьте `BoundaryManager` скрипт в сцену. | Включите в профиле конфигурации систему границ. |
| Параметр Configuration             | Настройте экземпляр сцены в инспекторе. | Настройте параметры в профиле визуализации границ. |

## <a name="sharing"></a>Совместное использование

|             Методы               | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Настройка                     | Общий доступ к службе: Добавьте в сцену общий доступ prefab. Унет: Используйте пример Шарингвисунет. | ведутся работы |
| Параметр Configuration             | Настройте экземпляры сцены в инспекторе. | ведутся работы |

## <a name="ux"></a>Пользовательский интерфейс

|         Методы                   | ХТК 2017 |  МРТК v2  |
|---------------------------|----------|-----------|
| Кнопка                     | [Взаимодействующие объекты](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Кнопка](../features/ux-building-blocks/Button.md) |
| Интерактивный объект                     | [Взаимодействующие объекты](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Интерактивный объект](../features/ux-building-blocks/Interactable.md) |
| Ограничивающий прямоугольник             | [Ограничивающий прямоугольник](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Ограничивающий прямоугольник](../features/ux-building-blocks/bounding-box.md) |
| Панель приложения             | [Панель приложения](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Панель приложения](../features/ux-building-blocks/app-bar.md) |
| Обработка одной руки (ГРБ и Move)   | [ханддраггабле](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Обработчик манипуляции](../features/ux-building-blocks/manipulation-handler.md) |
| Две манипуляции (захват, перемещение, вращение и масштабирование)             | [твохандманипулатабле](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Обработчик манипуляции](../features/ux-building-blocks/manipulation-handler.md) |
| Клавиатура             | [Клавиатура prefab]() | [Системная клавиатура](../features/ux-building-blocks/system-keyboard.md) |
| Всплывающая подсказка             | [Подсказка](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Подсказка](../features/ux-building-blocks/tooltip.md) |
| Коллекция объектов             | [Коллекция объектов](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Коллекция объектов](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Служебные программы

Некоторые служебные программы были согласованы в системе поиска решений как дубликаты. Если какой бы то ни было из необходимых скриптов отсутствует, выдайте сообщение.

| ХТК 2017 |  МРТК v2  |
|----------|-----------|
| Печат | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| тагалонг | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) или [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Поиск решения](../features/ux-building-blocks/solvers/Solver.md) |
| фикседангуларсизе | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Поиск решения](../features/ux-building-blocks/solvers/solver.md) |
| фпсдисплай | [Система диагностики](../features/diagnostics/diagnostics-system-getting-started.md) (в профиле конфигурации) |
| неарфаде | встроенные в [смешанную реальность набор средств стандартный шейдер](../features/rendering/mrtk-standard-shader.md) |
