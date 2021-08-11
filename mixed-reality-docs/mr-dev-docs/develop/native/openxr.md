---
title: OpenXR
description: создайте подсистему с помощью переносимого стандарта API опенкср и разверните его, чтобы Windows Mixed Reality и HoloLens 2 гарнитуры.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Опенкср, Путеводитель, расширения, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое подсистема, по промежуточного слоя
ms.openlocfilehash: 66ef972e09617e596a7d1d097073183943037e29b462ed3070d4defac91ca6b6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193755"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

Опенкср — это общедоступный Стандарт API из <a href="https://www.khronos.org/" target="_blank">кхронос</a>, предоставляющий модули с собственным доступом к диапазону устройств в разных [спектрах смешанной реальности](../../discover/mixed-reality.md).

вы можете разрабатывать с помощью опенкср HoloLens 2 или Windows Mixed Reality на рабочем столе головной телефон VR.  если у вас нет доступа к гарнитуре, вы можете использовать HoloLens 2 Emulator или симулятор Windows Mixed Reality.

## <a name="why-openxr"></a>Зачем Опенкср?

с помощью опенкср можно создавать модули, предназначенные для таких устройств, как HoloLens 2 и впечатляющие устройства VR, такие как Windows Mixed Reality гарнитуры для настольных пк. Опенкср позволяет написать код, который затем будет переносимым на широком диапазоне аппаратных платформ.

API Опенкср использует загрузчик для подключения приложения непосредственно к собственной поддержке платформы вашей гарнитуры. конечные пользователи получают максимальную производительность и минимальную задержку независимо от того, используете ли они Windows Mixed Reality или другие гарнитуры.

## <a name="what-is-openxr"></a>Что такое OpenXR?

API Опенкср предоставляет основные функции прогнозирования, работы с кадрами и пространственного ввода. вам потребуется создать подсистему, которая может ориентироваться на как holographic, так и впечатляющие устройства.

Чтобы узнать об API Опенкср, ознакомьтесь со <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификацией</a>опенкср 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">справочником по API</a>и <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">кратким справочником</a>.  Дополнительные сведения см. на <a href="https://www.khronos.org/openxr/" target="_blank">странице Кхронос опенкср</a>.

чтобы воспользоваться полным набором функций HoloLens 2, вы также будете использовать расширения опенкср, относящиеся к поставщику и поставщику, которые предоставляют дополнительные возможности за пределами ядра опенкср 1,0, такие как отслеживание, отслеживание глаз, пространственное сопоставление и пространственные привязки. Дополнительные сведения см. в [разделе "планы](#roadmap) " ниже на расширениях, которые появятся позже в этом году.

Опенкср не является механизмом смешанной реальности.  Вместо этого Опенкср позволяет использовать такие модули, как Unity и Нереал, для написания переносимого кода, который затем может получить доступ к функциям собственной платформы в holographic или иммерсивное устройство пользователя, независимо от поставщика, созданного этой платформой.

## <a name="roadmap"></a>Стратегия

Спецификация Опенкср определяет механизм расширения, позволяющий разработчикам среды выполнения предоставлять дополнительные функциональные возможности за пределами [основных функций](#what-is-openxr) , определенных в <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">базовой спецификации опенкср 1,0</a>.

Существует три вида расширений Опенкср:
* **Расширения поставщика (например, `MSFT` ):** включает инновации для каждого поставщика в аппаратных или программных функциях.  Любой поставщик среды выполнения может в любое время внедрить и поставлять расширение поставщика.
  * **Экспериментальные расширения поставщиков (например, `MSFT_preview` ):** экспериментальные расширения поставщиков, которые можно просмотреть для сбора отзывов.  `MSFT_preview` расширения предназначены только для устройств разработчика и будут удалены при поставке настоящего расширения.  Чтобы поэкспериментировать с ними, можно [включить расширения предварительного просмотра на устройстве разработчика](openxr-getting-started.md#using-preview-extensions).
* **Расширения кросс-поставщика `EXT` :** расширения кросс-поставщика, которые определяются и реализуются несколькими компаниями.  Группы заинтересованных компаний могут в любое время внедрять расширения EXT.
* **Официальные `KHR` расширения:** официальные расширения кхронос ратифицирован в рамках основной версии спецификации.  Расширения КХР охватываются той же лицензией, что и Основная спецификация.

Windows Mixed Reality среда выполнения опенкср поддерживает набор `MSFT` `EXT` расширений и, который предоставляет полный набор функций HoloLens 2 приложениям опенкср:

| Область применения компонента | Доступность расширения |
|--------------|------------------------|
| Системы + сеансы | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Справочные пространства (Просмотр, локальный, этап)](../../design/coordinate-systems.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Просмотр конфигураций (моно, стерео) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Цепочек переключений](../platform-capabilities-and-apis/rendering.md)  +  [время кадров](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Слои композиции<br />(проекция, четыре) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Входные и хаптикс](../../design/interaction-fundamentals.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Интеграция Direct3D 11 | **`KHR`Выпущено официальное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Интеграция Direct3D 12 | **`KHR`Выпущено официальное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Несвязанное пространство ссылок <br /> (возможности мирового масштаба)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Пространственные привязки](../../design/spatial-anchors.md) | <p>**`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview` расширение в [среде выполнения предварительной версии 107](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [Взаимодействие <br /> с рукой (захват/AIM, воздушный нажим, посвятка)](../../design/hands-and-tools.md)<p>*только HoloLens 2*</p> | **`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Сетка руки артикулатион +](../../design/hands-and-tools.md)<p>*только HoloLens 2*</p> | <p>**`EXT` выпущенное расширение:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Отслеживание глаз](../../design/eye-tracking.md)<p>*только HoloLens 2*</p> | **`EXT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [Запись смешанной реальности <br /> (третья Визуализация с камеры PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*только HoloLens 2*</p> | **`MSFT` выпущенные расширения:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Взаимодействие с другими пакетами SDK смешанной реальности<br />(например, [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) | <p>**`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` расширение, выпущенное в среде выполнения 105:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| Взаимодействие с API CoreWindow UWP<br />(например, для клавиатуры или мыши) | **`MSFT` расширение, выпущенное в среде выполнения 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Профили взаимодействия контроллера движения<br />(Samsung Одиссэй и HP, команда G2) | **`MSFT` расширения, выпущенные в среде выполнения 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Модели отрисовки контроллера движения](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` расширение, выпущенное в среде выполнения 104:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Основные сведения о сцене (плоскости, сетки)](../../design/scene-understanding.md)<p>*только HoloLens 2*</p> | <p>**`MSFT` расширение, выпущенное в среде выполнения 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [Режимы РЕПРОЕКЦИИ слоя композиции <br /> (автоматическое плоское или перестроение только ориентации)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` расширение, выпущенное в среде выполнения 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| Другие расширения кросс-поставщика | <p>**`KHR`Выпущены официальные расширения:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` выпущенные расширения:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

Хотя некоторые из этих расширений могут запускаться как расширения, зависящие от поставщика `MSFT` , корпорация Майкрософт и другие поставщики среды выполнения опенкср работают вместе для проектирования кросс-поставщиков `EXT` или `KHR` расширений для многих из этих функциональных областей. Расширения для разных поставщиков заставляют код, который вы пишете для этих функций, переносимыми между поставщиками среды выполнения, как и Основная спецификация.

## <a name="getting-started-with-openxr"></a>Начало работы с OpenXR

![снимок экрана Minecraft, воспроизводимого пользователем, людьми гарнитуру смешанной реальности](images/openxr-minecraft.jpg)

*новая подсистема рендердрагон Minecraft создала свою настольную службу поддержки версий VR с помощью опенкср!*

корпорация майкрософт приработала к играм Unity и в рабочей ситуации, чтобы убедиться в том, что будущее смешанной реальности открыта, а не только для HoloLens 2, но в полном объеме для пк, включая [новую переглаголную гарнитуру G2](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).  опенкср включает поддержку стабилизатора напряжения для основных наименований на сегодняшний день, например Minecraft и имитатора рейсов майкрософт!  дополнительные сведения о разработке для HoloLens (1-го поколения) см. в [заметках о выпуске](/hololens/hololens1-release-notes).

Чтобы узнать, как можно приступить к работе с Опенкср в Unity, нереальном модулем или собственной подсистемой, читайте здесь!

### <a name="openxr-in-unity"></a>Опенкср в Unity

текущая рекомендуемая конфигурация Unity майкрософт для разработки HoloLens 2 и Windows Mixed Reality — **Unity 2020,3 LTS** с последним подключаемым модулем опенкср смешанной реальности.  этот подключаемый модуль включает поддержку расширений опенкср, которые включают [все возможности HoloLens 2 и Windows Mixed Reality гарнитуры](#roadmap), в том числе отслеживание типа «рука/глаз», пространственные привязки и контроллеры HP reverbы G2.  MRTK-Unity поддерживает Опенкср в [мртк 2,7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project).  Дополнительные сведения о начале работы с Unity 2020 и Опенкср см. [в разделе Выбор версии Unity](../unity/choosing-unity-version.md).

при разработке для HoloLens (1-го поколения) необходимо продолжить использовать **Unity 2019,4 LTS** с устаревшей серверной частью API WinRT.  Если вы используете новый контроллер HP REVERB G2 в приложении Unity 2019, см. статью [входные документы с помощью команды HP](../unity/unity-reverb-g2-controllers.md).

начиная с **Unity 2021,2**, опенкср будет единственной поддерживаемой внутренней частью unity для нацеливания на HoloLens 2 и Windows Mixed Reality гарнитуры.

### <a name="openxr-in-unreal-engine"></a>Опенкср в нереальном ядре

Нереальный механизм 4,23 был первым основным выпуском игр для отправки поддержки предварительной версии Опенкср 1,0!  теперь в **нереальном подсистеме 4,26** поддержка HoloLens 2, Windows Mixed Reality и других головных телефонов настольных систем доступна через встроенную поддержку опенкср.  нереалный механизм 4,26 также поддерживает [подключаемый модуль расширения опенкср корпорации майкрософт](https://github.com/microsoft/Microsoft-OpenXR-Unreal), обеспечивая взаимодействие с рукой и поддержку контроллеров HP reverbов G2, [выполняя весь набор функций HoloLens 2 и Windows Mixed Reality гарнитуры](#roadmap).  В настоящее время в средстве [запуска игр](https://www.unrealengine.com/download/creators)для моделирования выпущена неreal-подсистема 4,26 с MRTK-Unreal 0,12, поддерживающими проекты опенкср.

### <a name="openxr-for-native-development"></a>Опенкср для разработки машинного кода

вы можете разрабатывать с помощью опенкср HoloLens 2 или Windows Mixed Reality на рабочем столе головной телефон VR.  если у вас нет доступа к гарнитуре, вы можете использовать HoloLens 2 Emulator или симулятор Windows Mixed Reality.

чтобы приступить к разработке опенкср приложений для HoloLens 2 или Windows Mixed Realityных гарнитур VR, см. статью как приступить к [разработке опенкср](openxr-getting-started.md).

Для ознакомления со всеми основными компонентами API Опенкср и примерами реальных приложений, использующих Опенкср сегодня, ознакомьтесь с этим видео в 60-минутном пошаговом руководстве:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>См. также раздел

* <a href="https://www.khronos.org/openxr/" target="_blank">Дополнительные сведения о Опенкср</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Спецификация Опенкср 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Справочник по API Опенкср 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Краткое справочное руководство по Опенкср 1,0</a>