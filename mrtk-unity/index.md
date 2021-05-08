---
title: Документация по MRTK в Unity для разработчиков
description: Сведения о Mixed Reality Toolkit для Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: cb8b95cf9e563e8a277fa0d4b253639a763f5ad5
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489304"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Что такое Mixed Reality Toolkit

![Набор средств для смешанной реальности](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

MRTK-Unity — это проект, управляемый Майкрософт, который предоставляет набор компонентов и функций для ускорения кроссплатформенной разработки приложений смешанной реальности в Unity. Ниже приведены некоторые его функции.

* Предоставляет **кросс-платформенную систему ввода и стандартные блоки для пространственных взаимодействий и пользовательского интерфейса**.
* Поддерживает **быстрое создание прототипов** с помощью имитации в редакторе, позволяющей сразу просматривать изменения.
* Работает как **расширяемая платформа**, предоставляющая разработчикам возможность менять основные компоненты.
* **Поддерживает широкий ряд платформ**:

| Платформа | Поддерживаемые устройства |
|---|---|
| OpenXR (Unity 2020.2 или более поздней версии): | Microsoft HoloLens 2; <br> гарнитуры смешанной реальности Windows Mixed Reality; |
| Windows Mixed Reality | Microsoft HoloLens; <br> Microsoft HoloLens 2; <br> гарнитуры смешанной реальности Windows Mixed Reality;  |
| Oculus (Unity 2019.3 или более поздней версии): | Oculus Quest. |
| OpenVR: |  гарнитуры смешанной реальности Windows Mixed Reality; <br> HTC Vive; <br> Oculus Rift; |
| отслеживание рук Ultraleap. | Leap Motion Controller (Ultraleap) |
| Мобильные службы | iOS и Android |

## <a name="getting-started-with-mrtk"></a>Начало работы с MRTK

Если вы не знакомы с MRTK или разработкой для Смешанной реальности в Unity, мы рекомендуем установить и изучить пример приложения из центра примеров MRTK на устройстве или в эмуляторе. 

> [!div class="nextstepaction"]
> [Скачайте приложение в центре примеров MRTK](running-examples-hub.md)

Ознакомившись с MRTK и Смешанной реальностью, установите необходимые средства и следуйте инструкциям из серии руководств по HoloLens 2 для начинающих.

> [!div class="nextstepaction"]
> [Установка средств](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [Серия учебников по HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Хотите узнать, как это работает?
> [!div class="nextstepaction"]
> [Подробнее об MRTK на GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Документация

| [![Заметки о выпуске](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[Заметки о выпуске](release-notes/mrtk-26-release-notes.md)| [![Обзор MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Обзор MRTK](architecture/overview.md)|[![Справочник по API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[Справочник по интерфейсам API](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>Состояние сборки

| Ветвь | Состояние CI | Состояние документации |
|---|---|---|
| `main` |[![Состояние CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Состояние документации](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Функциональные области

:::row:::
    :::column:::
       [![Система ввода](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[Система ввода](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Отслеживание рук (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Отслеживание рук <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Отслеживание взгляда (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[Отслеживание взгляда <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Профили](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Профили](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Отслеживание рук (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)<br>
        **[Отслеживание рук <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![Элементы управления пользовательским интерфейсом](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[Элементы управления пользовательским интерфейсом](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Решатели](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[Решатели](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Диспетчер нескольких сцен](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Диспетчер <br/>нескольких сцен](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Отслеживание пространственного положения](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[Отслеживание <br/> пространственного положения](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Средство диагностики](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Средство <br/> диагностики](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Отображение работы стандартного шейдера MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[Отображение примера работы стандартного шейдера MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Речь и диктовка](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Речь](features/input/speech.md)<br/> & [Диктовка](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Система границ](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[Система<br/> границ](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Имитация в редакторе](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Имитация <br/> в редакторе](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Экспериментальные возможности](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[Экспериментальные <br/> функции](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>Стандартные блоки пользовательского интерфейса

:::row:::
    :::column:::
       [![Кнопка](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Кнопка](features/ux-building-blocks/button.md)**<br>
        Элемент управления типа "кнопка", поддерживающий различные методы ввода, в том числе свободный ввод с отслеживаем рук в HoloLens 2.
    :::column-end:::
    :::column:::
        [![Элемент управления границами](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Элемент управления границами](features/ux-building-blocks/bounds-control.md)**<br>
        Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве.
    :::column-end:::
    :::column:::
        [![Манипулятор объектов](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Манипулятор объектов](features/ux-building-blocks/object-manipulator.md)**<br>
        Скрипт для манипулирования объектами одной или двумя руками.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Грифель](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Грифель](features/ux-building-blocks/slate.md)**<br>
        Плоскость в двухмерном стиле, поддерживающая прокрутку с помощью свободного ввода рукой.
    :::column-end:::
    :::column:::
        [![Системная клавиатура](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Системная клавиатура](features/ux-building-blocks/system-keyboard.md)**<br>
        Пример скрипта для использования системной клавиатуры в Unity.
    :::column-end:::
    :::column:::
        [![Интерактивный объект](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Интерактивный объект](features/ux-building-blocks/interactable.md)**<br>
        Скрипт, обеспечивающий взаимодействие с объектами, с поддержкой визуальных состояний и тем.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Решатель](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Решатель](features/ux-building-blocks/solvers/solver.md)**<br>
        Различные модели поведения для позиционирования объектов, такие как следование (tag-along), прикрепление к пользователю (body-lock), зафиксированный размер просмотра (constant view size) и поверхностный магнетизм (surface magnetism).
    :::column-end:::
    :::column:::
        [![Коллекция объектов](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Коллекция объектов](features/ux-building-blocks/object-collection.md)**<br>
        Скрипт для размещения массива объектов в трехмерной фигуре.
    :::column-end:::
    :::column:::
        [![Подсказка](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Подсказка](features/ux-building-blocks/tooltip.md)**<br>
        Пользовательский интерфейс заметок с гибкой системой привязки и поворота, который можно использовать, чтобы помечать контроллеры движений и объекты.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Ползунок](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Ползунок](features/ux-building-blocks/sliders.md)**<br>
        Пользовательский интерфейс ползунков для изменения значений, поддерживающих взаимодействие с прямым отслеживанием рук.
    :::column-end:::
    :::column:::
        [![Стандартный шейдер MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Стандартный шейдер MRTK](features/rendering/mrtk-standard-shader.md)**<br>
        Стандартный шейдер MRTK поддерживает различные элементы интерфейса Fluent с достаточной производительностью.
    :::column-end:::
    :::column:::
        [![Меню руки](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Меню руки](features/ux-building-blocks/hand-menu.md)**<br>
        Привязанный к руке пользовательский интерфейс, обеспечивающий быстрый доступ и использующий решатель ограничения руки.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Панель приложения](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Панель приложения](features/ux-building-blocks/app-bar.md)**<br>
        Пользовательский интерфейс для активации элемента управления границами вручную.
    :::column-end:::
    :::column:::
        [![Указатели](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Указатели](features/input/pointers.md)**<br>
        Сведения о различных типах указателей.
    :::column-end:::
    :::column:::
        [![Визуализация с использованием кончика пальца](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Визуализация с использованием кончика пальца](features/ux-building-blocks/fingertip-visualization.md)**<br>
        Визуальный маркер на кончике пальца, повышающий уверенность в прямом взаимодействии.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Быстрое меню](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Быстрое меню](features/ux-building-blocks/near-menu.md)**<br>
        Пользовательский интерфейс подвешенного меню для быстрых взаимодействий.
    :::column-end:::
    :::column:::
        [![Начало работы с отслеживанием пространственного положения](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Представление для отслеживания пространственного положения](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Обеспечьте взаимодействие голографических объектов с физическими средами.
    :::column-end:::
    :::column:::
        [![Голосовая команда](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Голосовая команда](features/input/speech.md)**<br>
        Скрипты и примеры для интеграции голосового ввода.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Индикатор хода выполнения](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Индикатор хода выполнения](features/ux-building-blocks/progress-indicator.md)**<br>
        Визуальный индикатор, сообщающий о ходе процесса или операции.
    :::column-end:::
    :::column:::
        [![Диалоговое окно](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Диалоговое окно](features/ux-building-blocks/dialog.md)**<br>
        Элемент пользовательского интерфейса для получения подтверждения пользователя.
    :::column-end:::
    :::column:::
        [![Обучающая рука](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Обучающая рука](features/ux-building-blocks/hand-coach.md)**<br>
        Компонент, помогающий направлять пользователя, если жест еще не выучен.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Служба физического взаимодействия с помощью рук](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Служба физического взаимодействия с помощью рук [экспериментальная]](features/experimental/hand-physics-service.md)**<br>
        Служба физического взаимодействия с помощью рук поддерживает события столкновения с твердым телом и взаимодействия с помощью свободного ввода руками.
    :::column-end:::
    :::column:::
        [![Коллекция прокрутки](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Коллекция прокрутки](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Коллекция объектов со встроенной поддержкой прокрутки трехмерных объектов.
    :::column-end:::
    :::column:::
        [![Док-панель](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Док-панель [экспериментальная]](features/experimental/dock.md)**<br>
        Док-панель позволяет перемещать объекты между заранее определенными позициями.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Отслеживание взгляда: выбор цели](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Отслеживание взгляда: выбор цели](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Объедините ввод с помощью взгляда, голоса и рук для быстрого и простого выбора голограмм в сцене.
    :::column-end:::
    :::column:::
        [![Отслеживание взгляда: навигация](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Отслеживание взгляда: навигация](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Узнайте, как автоматически прокручивать текст или быстро увеличить масштаб выбранного содержимого с учетом того, на что направлен ваш взгляд.
    :::column-end:::
    :::column:::
        [![Отслеживание взгляда: тепловая карта](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Отслеживание взгляда: тепловая карта](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Примеры ведения журналов, загрузки и визуализации того, на что смотрят пользователи в вашем приложении.
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Инструменты

|  [![Окно оптимизации](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Окно оптимизации](features/tools/optimize-window.md) | [![Окно зависимости](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Окно зависимости](features/tools/dependency-window.md) | ![Окно сборки](features/images/MRTK_Icon_BuildWindow.png) Окно сборки | [![Запись ввода](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Запись ввода](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Автоматизируйте настройку проектов смешанной реальности, чтобы оптимизировать производительность. | Анализируйте зависимости между активами и выявляйте неиспользуемые активы. |  Настройте и выполните комплексный процесс сборки для приложений смешанной реальности. | Записывайте и воспроизводите данные о перемещении головы и отслеживания рук в редакторе. |

## <a name="example-scenes"></a>Примеры сцен

Узнайте о различных типах взаимодействий и элементов управления пользовательского интерфейса MRTK с помощью [этого примера сцены](features/example-scenes/hand-interaction-examples.md).

[![Пример сцены 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Центр примеров MRTK

Центр примеров MRTK позволяет вам опробовать различные примеры сцен в MRTK.
Вы можете скачать готовые пакеты приложений для HoloLens (x86), HoloLens 2 (ARM) и иммерсивных гарнитур Windows Mixed Reality (x64), выбрав пакет Mixed Reality Toolkit Examples в средстве [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Обязательно [используйте портал устройств Windows для установки приложений в HoloLens (1-го поколения)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). Для HoloLens 2 можно скачать и установить [Центр примеров MRTK с помощью приложения Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Дополнительные сведения о создании центра со сценами с помощью системы сцен и службы перехода между сценами MRTK см. на [странице сведений Центра примеров](features/example-scenes/example-hub.md).

[![Центр примеров сцен](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>Примеры приложений, созданных с помощью MRTK

| [![Периодическая таблица элементов](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Исследование галактики](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![Пример приложения Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) — это пример приложения с открытым кодом, которое демонстрирует, как использовать систему ввода и стандартные блоки MRTK для создания интерфейса приложения для HoloLens и иммерсивных гарнитур. Прочитайте историю о [портировании приложения Periodic Table of the Elements на HoloLens 2 с помощью MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158). |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) — пример приложения с открытым кодом, которое изначально было разработано для HoloLens в марте 2016 г. в рамках кампании Share Your Idea. В Galaxy Explorer добавлены новые возможности для HoloLens 2 с помощью MRTK v2. Прочитайте историю о [создании Galaxy Explorer для HoloLens 2](/windows/mixed-reality/galaxy-explorer-update). |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) — это пример приложения с открытым кодом для HoloLens 2, которое демонстрирует, как мы можем вызвать тактильные ощущения с помощью визуализации, звуков и отслеживания свободных движений рук. Ознакомьтесь с докладом Microsoft MR Dev Days по [наработкам при разработке и использовании приложения Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App), чтобы узнать больше о проектировании и разработке. |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Видео докладов с Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Учебник по созданию простого приложения MRTK с нуля. Узнайте больше о понятиях взаимодействия и мультиплатформенных возможностях MRTK. | Изучите стандартные блоки взаимодействий в MRTK, которые помогут вам создать великолепные среды смешанной реальности. | Вводная информация о встроенных и внешних средствах оценки производительности для MRTK, а также стандартного шейдера MRTK. |

Другие видео с докладами см. на странице [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions).

## <a name="engage-with-the-community"></a>Присоединяйтесь к сообществу

* Присоединяйтесь к обсуждению MRTK на сайте [Slack](https://holodevelopers.slack.com/). Вступить в сообщество Slack можно с помощью [автоматической рассылки приглашений](https://holodevelopersslack.azurewebsites.net/).

* Задать вопросы об MRTK можно на сайте [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) (используйте тег **MRTK**).

* Если вы нашли ошибки в коде MRTK, вы можете выполнить поиск по [известным проблемам](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) или сообщить о [новой проблеме](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues).

* Вопросы об участии в разработке MRTK можно задать на канале [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) в сообществе Slack.

В рамках этого проекта действуют [правила поведения в отношении продуктов с открытым исходным кодом Майкрософт](https://opensource.microsoft.com/codeofconduct/).
Дополнительные сведения см. в статье [Вопросы и ответы, связанные с правилами поведения](https://opensource.microsoft.com/codeofconduct/faq/). Чтобы задать вопрос или получить комментарии, обратитесь по адресу [opencode@microsoft.com](mailto:opencode@microsoft.com).

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Полезные ресурсы в Центре разработки для смешанной реальности

| ![Знания](features/images/mrdevcenter/icon-discover.png) [Знания](/windows/mixed-reality/)| ![Проектирование](features/images/mrdevcenter/icon-design.png) [Проектирование](/windows/mixed-reality/design)| ![Разработка](features/images/mrdevcenter/icon-develop.png) [Разработка](/windows/mixed-reality/development)| ![Дистрибуция](features/images/mrdevcenter/icon-distribute.png) [Дистрибуция](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Узнайте, как создавать взаимодействия смешанной реальности для HoloLens и иммерсивных гарнитур (виртуальная реальность).          | Получите руководства по проектированию. Создайте пользовательский интерфейс. Узнайте о взаимодействиях и способах ввода.     | Получите руководства по разработке. Узнайте о технологиях. Изучите их научную основу.       | Подготовка приложения для других пользователей и создание средства для запуска трехмерных приложений. |

## <a name="useful-resources-on-azure"></a>Полезные ресурсы в Azure

| ![Пространственные привязки](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Пространственные привязки](/azure/spatial-anchors/)| ![Службы распознавания речи](features/images/mrdevcenter/icon-azurespeechservices.png) [Службы распознавания речи](/azure/cognitive-services/speech-service/)| ![Службы компьютерного зрения](features/images/mrdevcenter/icon-azurevisionservices.png) [Службы компьютерного зрения](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Пространственные привязки — это кросс-платформенная служба, которая позволяет создавать взаимодействия смешанной реальности с использованием объектов, сохраняющих свое расположение на различных устройствах с течением времени.| Откройте для себя и интегрируйте в свое приложение возможности обработки речи на платформе Azure, такие как преобразование речи в текст, распознавание говорящего или перевод речи.| Идентифицируйте изображения или видео с помощью служб визуального распознавания с такими возможностями, как компьютерное зрение, определение лиц, распознавание эмоций или индексация видео. |

## <a name="how-to-contribute"></a>Как стать соавтором

Узнайте, как [принять участие в разработке MRTK](contributing/contributing.md).

## <a name="getting-help"></a>Получение справки

Если при использовании MRTK у вас возникли проблемы или появились вопросы, вам помогут следующие ресурсы:

* Чтобы сообщить об ошибке, [создайте запрос](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) в репозитории GitHub.
* Свой вопрос вы можете задать на сайте [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) или на [канале mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) в сообществе Slack. Вступить в сообщество Slack можно с помощью [автоматической рассылки приглашений](https://holodevelopersslack.azurewebsites.net/).