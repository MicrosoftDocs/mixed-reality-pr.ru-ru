---
title: Рекомендации по настройке смешанной реальности
description: Документация по настройке МРТК в Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК,
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588866"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Рекомендации по настройке профиля набора средств Mixed Reality

Набор средств для смешанной реальности централизует как можно больше конфигурации, необходимой для управления набором средств (за исключением истинной среды выполнения).

Это простое пошаговое руководство для каждого экрана профиля конфигурации, доступного для набора средств.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Основной профиль конфигурации набора средств для смешанной реальности

Главный профиль конфигурации, присоединенный к *микседреалититулкит* GameObject в сцене, предоставляет главную точку входа для набора инструментов в проекте.

> [!NOTE]
> Набор средств Mixed Reality "блокирует" экраны конфигурации по умолчанию, чтобы гарантировать, что у вас всегда есть общая начальная точка для проекта, и рекомендуется приступить к определению собственных параметров по мере развития проекта. Конфигурация МРТК не редактируется в режиме воспроизведения.

![Профиль конфигурации МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Все профили "по умолчанию" для набора средств Mixed Reality можно найти в проекте SDK в папке Assets/МРТК/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile оптимизирован для HoloLens 2. Дополнительные сведения см. в разделе [Профили](../features/profiles/profiles.md) .

При открытии главного профиля конфигурации набора средств для смешанной реальности в инспекторе отображается следующий экран:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Если вы выберете ресурс Микседреалититулкитконфигуратионпрофиле без Микседреалититулкит в сцене, то запросите, хотите ли вы, чтобы МРТК автоматически настроить сцену. Это необязательно, однако в сцене должен быть активный объект Микседреалититулкит для доступа ко всем экранам конфигурации.

Он содержит текущую активную конфигурацию среды выполнения для проекта.

Здесь можно переходить ко всем профилям конфигурации для МРТК, включая:

- [Рекомендации по настройке профиля набора средств Mixed Reality](#mixed-reality-toolkit-profile-configuration-guide)
  - [Основной профиль конфигурации набора средств для смешанной реальности](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Параметры работы](#experience-settings)
  - [Параметры камеры](#camera-settings)
  - [Параметры системы ввода](#input-system-settings)
  - [Параметры визуализации границ](#boundary-visualization-settings)
  - [Выбор системы для пропорций](#teleportation-system-selection)
  - [Параметры пространственной осведомленности](#spatial-awareness-settings)
  - [Параметры диагностики](#diagnostics-settings)
  - [Параметры системы сцены](#scene-system-settings)
  - [Дополнительные параметры служб](#additional-services-settings)
  - [Параметры входных действий](#input-actions-settings)
  - [Правила для входных действий](#input-actions-rules)
  - [Конфигурация указателя](#pointer-configuration)
  - [Настройка жестов](#gestures-configuration)
  - [Речевые команды](#speech-commands)
  - [Конфигурация сопоставления контроллеров](#controller-mapping-configuration)
  - [Параметры визуализации контроллера](#controller-visualization-settings)
  - [Служебные программы редактора](#editor-utilities)
    - [Инспекторы служб](#service-inspectors)
    - [Модуль подготовки буфера глубины](#depth-buffer-renderer)
  - [Изменение профилей во время выполнения](#changing-profiles-at-runtime)
    - [Параметр профиля инициализации pre МРТК](#pre-mrtk-initialization-profile-switch)
    - [Переключатель активного профиля](#active-profile-switch)
  - [См. также:](#see-also)

Эти профили конфигурации описаны ниже в соответствующих разделах.

---
<a name="experience"></a>

## <a name="experience-settings"></a>Параметры работы

Этот параметр, расположенный на главной странице конфигурации набора средств смешанной реальности, определяет операцию по умолчанию для [масштаба среды Mixed Reality](/windows/mixed-reality/coordinate-systems-in-unity) для проекта.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Параметры камеры

Параметры камеры определяют, как будет настроена камера для проекта смешанной реальности, определяя общие параметры обрезки, качества и прозрачности.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Параметры системы ввода

Проект Mixed Reality предоставляет надежную и хорошо обученную входную систему для маршрутизации всех событий ввода вокруг проекта, выбранного по умолчанию.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

За входной системой, предоставляемой МРТК, относятся несколько других систем, которые помогают управлять сложными взаимными настройками, необходимыми для абстракции сложностей многоплатформенных и смешанных сред.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Каждый из отдельных профилей описан ниже.

- Параметры фокуса
- [Параметры входных действий](#input-actions-settings)
- [Правила для входных действий](#input-actions-rules)
- [Конфигурация указателя](#pointer-configuration)
- [Настройка жестов](#gestures-configuration)
- [Речевые команды](#speech-commands)
- [Конфигурация сопоставления контроллеров](#controller-mapping-configuration)
- [Параметры визуализации контроллера](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Параметры визуализации границ

Система границ преобразует воспринимаемую границу, сообщаемую базовой системой границ и системы защиты платформ. Конфигурация визуализатора границы дает возможность автоматически отображать записанную границу в сцене относительно положения пользователя. Граница также будет реагировать на изменения и обновляться в зависимости от того, где находятся телепорты пользователя в сцене.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Выбор системы для пропорций

Проект Mixed Reality предоставляет полнофункциональную систему для управления событиями передачи в проекте, которая выбрана по умолчанию.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Параметры пространственной осведомленности

Проект Mixed Reality предоставляет перестроенную систему пространственной информации для работы с системами пространственного сканирования в проекте, выбранном по умолчанию.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

Конфигурация пространственной осведомленности в наборе средств Mixed Reality позволяет настраивать способ запуска системы, независимо от того, запускается ли она автоматически при запуске приложения или более поздней версии, а также при установке экстентов для поля представления.

Кроме того, она позволяет настроить параметры сетки и зоны, а также настраивать то, как проект понимает среду.

Это применимо только к устройствам, которые могут предоставлять сканированную среду.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Параметры диагностики

Необязательная, но очень полезная функция МРТК — это функция диагностики подключаемого модуля.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

Профиль диагностики предоставляет несколько простых систем для наблюдения за выполнением проекта, включая удобный переключатель вкл./выкл. для включения и отключения панели отображения в сцене.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Параметры системы сцены

МРТК предоставляет эту необязательную службу, которая помогает управлять сложной загрузкой и выгрузке сложных вспомогательных сцен. Чтобы решить, подходит ли система сцен для вашего проекта, ознакомьтесь с [руководством по начало работыию сцены.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Дополнительные параметры служб

Одной из более сложных областей набора средств Mixed Reality является реализация [шаблона локатора служб](https://en.wikipedia.org/wiki/Service_locator_pattern) , которая позволяет зарегистрировать любую "службу" в инфраструктуре. Это позволяет легко расширять платформу с помощью новых функций и систем, но также позволяет проектам использовать эти возможности для регистрации собственных компонентов среды выполнения.

Любая зарегистрированная служба по-прежнему получает все преимущества всех событий Unity без издержек и затрат на реализацию одноэлементных шаблонов неуклюжим. Это позволяет выполнять чисто компоненты C# без издержек на сцены для выполнения фоновых и задних процессов, например порождение систем, логика игры среды выполнения или практически любые другие.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Параметры входных действий

Входные действия предоставляют способ абстрактного взаимодействия с любыми физическими взаимодействиями и входными данными из проекта среды выполнения. Все физические входные данные (от контроллеров, руки и мыши/т. д.) преобразуются в логические действия ввода для использования в проекте среды выполнения. Это гарантирует неважность, откуда поступают входные данные. проект просто реализует эти действия в фоновом режиме в виде «вещей» или «взаимодействие с».

Чтобы создать новое действие ввода, просто нажмите кнопку "добавить новое действие" и введите понятное текстовое имя для того, что оно представляет. Затем нужно выбрать только ось (тип данных), которую должно передать действие, или, в случае физического контроллера, физический тип входных данных, к которому можно присоединиться, например:

| Ограничение оси | Тип данных | Описание | Пример использования |
| :--- | :--- | :--- | :--- |
| Нет | Нет данных | Используется для пустого действия или события | Триггер события |
| Необработанный (зарезервированный) | объект | Зарезервировано для использования в будущем. | Недоступно |
| Цифровой | bool | Логическое значение ON или Off типа Data | Кнопка контроллера |
| Одна ось | FLOAT | Одно значение данных точности | Входной диапазон, например триггер |
| Двойная ось | Vector2 | Тип данных Dual float для нескольких осей | Dpad или аналоговый стик |
| 3 ДОФ | Vector3 | Данные о позиционированном типе из с 3 осью с плавающей запятой | Контроллер только с трехмерным положением |
| Тройной поворот ДОФ | Quaternion | Только поворот входных данных с 4 осью с плавающей запятой | Контроллер в стиле с тремя степенями, например контроллер Окулус Go |
| Шесть ДОФ | "Смешанная реальность" (Vector3, кватернион) | Входные данные в стиле расположения и поворота с помощью компонентов Vector3 и кватернион | Контроллер или указатель движения |

События, использующие входные действия, не ограничиваются физическими контроллерами и могут по-прежнему использоваться в проекте для того, чтобы эффекты среды выполнения создавали новые действия.

> [!NOTE]
> Входные действия — это один из нескольких компонентов, которые нельзя изменять во время выполнения, они являются только конфигурацией времени разработки. Этот профиль не следует переключать в силу того, что проект работает из-за зависимости платформы (и ваших проектов) от идентификатора, созданного для каждого действия.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Правила для входных действий

Правила входных действий предоставляют способ автоматического преобразования события, вызванного одним входным действием, в различные действия на основе его значения данных. Они легко управляются в рамках платформы и не вызывают никаких затрат на производительность.

Например, преобразование одного входного события двойной оси из DPad в в 4 соответствующие действия «Dpad up»/«DPad Down»/«Dpad Left»/«Dpad Right» (как показано на рисунке ниже).

Это также можно сделать в собственном коде. Однако, так как это был очень распространенный шаблон, платформа предоставляет механизм для выполнения этой задачи «не из этого».

Правила входных действий можно настроить для любой доступной входной оси. Однако действия ввода из одного типа оси можно перевести в другое Входное действие того же типа оси. Действие двойной оси можно связать с другим действием двойной оси, но не с цифровым действием или без него.

![Профиль правил входных действий](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Конфигурация указателя

Указатели используются для взаимодействия в сцене на любом устройстве ввода, предоставляя направление и проверку нажатия для любого объекта в сцене (с присоединенным объектом или компонентом пользовательского интерфейса). Указатели по умолчанию автоматически настраиваются для контроллеров, гарнитур (взгляд/Focus) и ввод с клавиатуры и сенсорного ввода.

Указатели можно также выработать в активной сцене с помощью одного из многих компонентов строк, предоставляемых набором средств Mixed Reality, или любого собственного компонента, если они реализуют интерфейс МРТК Имикседреалитипоинтер.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Геообъектная область: определяет глобальную указывающую экстент для всех указателей, включая взгляд.
- Райкаст Layer Маскируетs: определяет, для каких слоев указатели будут райкаст.
- Отладка направленных вниз отрисованных лучей: вспомогательный модуль отладки для визуализации луча, используемых для райкастинг.
- Отладка рисуемых отлучающих лучей цветов: набор цветов, используемых для визуализации.
- Взгляните на курсор Prefab: позволяет легко указать глобальный курсор взгляда для любой сцены.

Есть дополнительная вспомогательная кнопка, позволяющая быстро перейти к поставщику взгляда, чтобы переопределить некоторые конкретные значения для взгляда при необходимости.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Настройка жестов

Жесты — это специальная реализация системы, позволяющая назначать входные действия различным входным методам "жеста", предоставляемым различными пакетами SDK (например, HoloLens).

> [!NOTE]
> Текущая реализация жестов предназначена только для HoloLens и будет улучшена для других систем, так как они будут добавлены в набор средств в будущем (пока нет дат).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Речевые команды

Как и жесты, некоторые платформы среды выполнения также предоставляют интеллектуальные функции "речь — текст" с возможностью создания команд, которые могут быть получены проектом Unity. Этот профиль конфигурации позволяет настроить следующие параметры:

1. Общие параметры. для параметра "поведение при запуске" задайте значение "автоматический запуск" или "запуск вручную". определяет, следует ли инициализировать Кэйвордрекогнизер при запуске системы ввода или разрешить проекту решать, когда инициализировать Кэйвордрекогнизер. "Уровень достоверности распознавания" используется для инициализации [API Кэйвордрекогнизер](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity.
2. Речевые команды — регистрируют слова и переводит их в для ввода действий, которые могут быть получены проектом. Они также могут быть присоединены к действиям клавиатуры, если это необходимо.

> [!IMPORTANT]
> В настоящее время система поддерживает только распознавание речи при работе на платформах Windows 10, например HoloLens и Windows 10 Desktop, и будет улучшена для других систем, так как они будут добавлены в МРТК в будущем (даты пока не указаны).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Конфигурация сопоставления контроллеров

Одним из основных экранов настройки набора средств Mixed Reality является возможность настраивать и сопоставлять различные типы контроллеров, которые могут использоваться в проекте.

На следующем экране настройки можно настроить любой контроллер, распознаваемый в настоящий момент набором.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

МРТК предоставляет конфигурацию по умолчанию для следующих контроллеров и систем:

- Мышь (включая поддержку трехмерной пространственной мыши)
- Сенсорный экран
- Контроллеры Xbox
- Контроллеры Windows Mixed Reality
- Жесты HoloLens
- Контроллеры HTC Naopak палочки
- Окулус Touch Controllers
- Удаленный контроллер Окулус
- Универсальные устройства Опенвр (только для опытных пользователей)

Если щелкнуть изображение для любой из предварительно созданных систем контроллеров, можно настроить одно входное действие для всех соответствующих входных данных, например, на экране Настройки сенсорного контроллера Окулус ниже:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

Также имеется расширенный экран для настройки других входных контроллеров Опенвр или Unity, которые не определены выше.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Параметры визуализации контроллера

Помимо сопоставления контроллеров, предоставляется отдельный профиль конфигурации для настройки способа представления контроллеров в фоновом режиме.

Это можно настроить в "глобальном" (все экземпляры контроллера для конкретной руки) или только для отдельного типа контроллера/вручную.

МРТК также поддерживает собственные модели контроллера SDK для Windows Mixed Reality и Опенвр. Они загружаются в виде объекты gameobject в сцене и размещаются с помощью отслеживания контроллера платформы.

Если представление контроллера в сцене должно быть смещено от позиции физического контроллера, то просто задайте это смещение относительно prefab модели контроллера (например, установив расположение преобразования контроллера prefab со смещением позиции).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Служебные программы редактора

Следующие служебные программы работают только в редакторе и полезны для повышения производительности разработки.

![Служебные программы настройки редактора МРТК](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Инспекторы служб

Инспекторы служб — это функция только редактора, которая создает объекты в сцене, представляющие активные службы. При выборе этих объектов отображаются инспекторы, предлагающие ссылки на документацию, управление визуализациями редактора и понимание состояния службы.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Инспекторы служб можно включить, установив флажок *использовать инспекторы служб* в разделе *Параметры редактора* в профиле конфигурации.

### <a name="depth-buffer-renderer"></a>Модуль подготовки буфера глубины

Совместное использование буфера глубины с некоторыми платформами смешанной реальности может повысить [голограмму стабилизации](../performance/hologram-stabilization.md). Например, платформа Windows Mixed Reality может изменить отображаемую сцену на пиксель, чтобы учитывать незначительные движения головного подразделения в течение времени, когда оно потребовалось для отрисовки кадра. Однако для этих методов требуются буферы глубины с точными данными, чтобы понять, где и насколько далеко от пользователя.

Чтобы обеспечить визуализацию сцены всех необходимых данных в буфер глубины, разработчики могут переключать функцию *буфера глубины рендеринга* в разделе *Параметры редактора* в профиле конфигурации. Это займет текущий буфер глубины и выводит его в виде цвета в представление сцены, применяя к основной камере результат последующей обработки [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) .

![Программа буфера глубины прорисовки ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>синий цилиндр в сцене содержит материал с зврите, поэтому данные глубины не записываются</sup> .

## <a name="changing-profiles-at-runtime"></a>Изменение профилей во время выполнения

Можно обновлять профили во время выполнения, и в большинстве случаев это полезно в двух разных сценариях.

1. **Параметр предварительной инициализации профиля мртк**: при запуске перед инициализацией мртк и переводом профиля в состояние "неиспользуемый" заменяется для включения и отключения различных функций в зависимости от возможностей устройства. Например, если опыт работает в VR без оборудования пространственного сопоставления, вероятно, не имеет смысла включать компонент пространственного сопоставления.
1. **Переключатель активного профиля**: после запуска, после инициализации мртк и активации профиля, переключать профиль, используемый в настоящий момент, для изменения способа работы определенных функций. Например, в приложении может быть определен конкретный вспомогательный интерфейс, который должен полностью удалить указатели.

### <a name="pre-mrtk-initialization-profile-switch"></a>Параметр профиля инициализации pre МРТК

Это можно сделать, присоединив незавершенное поведение (пример ниже), которое выполняется перед инициализацией МРТК (т. е. в спящем режиме ()). Обратите внимание, что сценарий (т. е. вызов `SetProfileBeforeInitialization` ) должен выполняться раньше `MixedRealityToolkit` , чем скрипт, который можно получить, установив [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html).

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

Вместо «Профилетаусе» можно иметь произвольный набор профилей, применяемых к определенным платформам (например, один для HoloLens 1, один для VR, один для HoloLens 2 и т. д.). Можно использовать различные другие индикаторы (например https://docs.unity3d.com/ScriptReference/SystemInfo.html , независимо от того, является ли камера непрозрачной или прозрачной), чтобы определить, какой профиль нужно загрузить.

### <a name="active-profile-switch"></a>Переключатель активного профиля

Это можно сделать, задав `MixedRealityToolkit.Instance.ActiveProfile` для свойства новый профиль, заменяющий активный профиль.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Обратите внимание `ActiveProfile` , что при настройке во время выполнения уничтожение выполняющихся служб будет происходить после последней латеупдате () всех служб, а создание и инициализацию служб, связанных с новым профилем, будет происходить до первого обновления () всех служб.

Во время этого процесса может возникнуть заметная колебание приложения. Кроме того, любой сценарий с более высоким приоритетом, чем `MixedRealityToolkit` скрипт, может ввести его обновление, прежде чем новый профиль будет правильно настроен. Дополнительные сведения о приоритете скрипта см. в разделе [Параметры порядка выполнения скрипта](https://docs.unity3d.com/Manual/class-MonoManager.html) .

В процессе переключения профиля существующая Камера интерфейса пользователя останется без изменений, гарантируя, что компоненты пользовательского интерфейса Unity, требующие Canvas, по-прежнему будут работать после параметра.

## <a name="see-also"></a>См. также

- [Стабилизация голограмм](../performance/hologram-stabilization.md)