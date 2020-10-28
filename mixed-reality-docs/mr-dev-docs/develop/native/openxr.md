---
title: OpenXR
description: Создайте подсистему с помощью переносимого стандарта API Опенкср и разверните его на гарнитурах Windows Mixed Reality и HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя
ms.openlocfilehash: 519d363c49f86a47eeaa5872c6f7911e12276c99
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903103"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

Опенкср — это открытый стандарт API из <a href="https://www.khronos.org/" target="_blank">кхронос</a> , который предоставляет механизмам собственный доступ к широкому спектру устройств от многих поставщиков, охватывающих спектр различных [типов](../../discover/mixed-reality.md).

Вы можете разрабатывать приложения, используя OpenXR с HoloLens 2 или иммерсивную гарнитуру Windows Mixed Reality с компьютером.  Если у вас нет доступа к гарнитуре, можно использовать эмулятор HoloLens 2 или симулятор Windows Mixed Reality.

## <a name="why-openxr"></a>Зачем Опенкср?

С помощью Опенкср вы можете создавать модули, предназначенные для более чем holographic устройств (например, HoloLens 2), которые размещают цифровое содержимое в реальной жизни, как если бы оно было на самом деле, а также впечатляющие устройства (например, гарнитуры Windows Mixed Reality для настольных ПК), которые скрывают физический мир и заменяют его цифровой опыт.  Опенкср позволяет написать код, который затем будет переносимым на широком диапазоне аппаратных платформ.

API Опенкср использует загрузчик, который подключает ваше приложение непосредственно к поддержке собственной платформы вашей гарнитуры.  Это обеспечивает максимальную производительность и минимальную задержку конечных пользователей независимо от того, используете ли они гарнитуру Windows Mixed Reality или любую другую гарнитуру.

## <a name="what-is-openxr"></a>Что такое OpenXR?

API Опенкср предоставляет основные функции прогнозирования, работы с рамками и использования пространственных входных данных. вам потребуется создать подсистему, предназначенную для таких устройств, как HoloLens 2 и иммерсивное устройство, например гарнитуры Windows Mixed Reality.

Чтобы узнать об API Опенкср, ознакомьтесь со <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификацией</a>опенкср 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">справочником по API</a> и <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">кратким справочником</a>.  Дополнительные сведения см. на <a href="https://www.khronos.org/openxr/" target="_blank">странице Кхронос опенкср</a>.

Чтобы ориентироваться на полный набор функций HoloLens 2, вы также будете использовать расширения Опенкср, относящиеся к поставщику и поставщику, которые предоставляют дополнительные функции за пределами ядра Опенкср 1,0, такие как отслеживание, отслеживание глаз, пространственное сопоставление и пространственные привязки.  Дополнительные сведения о расширениях, которые появятся позже в этом году, см. в [разделе о планах](#roadmap) .

Обратите внимание, что Опенкср не является механизмом смешанной реальности.  Вместо этого Опенкср позволяет использовать такие модули, как Unity и Нереал, для написания переносимого кода, который затем может получить доступ к функциям собственной платформы в holographic или иммерсивное устройство пользователя независимо от того, какой поставщик создал эту платформу.

## <a name="roadmap"></a>Схема действий

Спецификация Опенкср определяет механизм расширения, позволяющий разработчикам среды выполнения предоставлять дополнительные функциональные возможности за пределами [основных функций](#what-is-openxr) , определенных в <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">базовой спецификации опенкср 1,0</a>.

Существует три вида расширений Опенкср:
* **Расширения поставщика (например, `MSFT` ):** включает инновации для каждого поставщика в аппаратных или программных функциях.  Любой поставщик среды выполнения может в любое время внедрить и поставлять расширение поставщика.
  * **Экспериментальные расширения поставщиков (например, `MSFT_preview` ):** экспериментальные расширения поставщиков, которые можно просмотреть для сбора отзывов.  `MSFT_preview` расширения предназначены только для устройств разработчика и будут удалены при поставке настоящего расширения.  Чтобы поэкспериментировать с ними, можно [включить расширения предварительного просмотра на устройстве разработчика](openxr-getting-started.md#using-preview-extensions).
* **Расширения кросс-поставщика `EXT` :** расширения кросс-поставщика, которые определяются и реализуются несколькими компаниями.  Группы заинтересованных компаний могут в любое время внедрять расширения EXT.
* **Официальные `KHR` расширения:** официальные расширения кхронос ратифицирован в рамках основной версии спецификации.  Расширения КХР охватываются той же лицензией, что и Основная спецификация.

По состоянию на июль 2020 среда выполнения Windows Mixed Reality поддерживает набор `MSFT` `EXT` расширений и, которые переносят полный набор функций HoloLens 2 в приложения опенкср:

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
| [Пространственные привязки](../../design/spatial-anchors.md) | **`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Взаимодействие <br /> с рукой (захват/AIM, воздушный нажим, посвятка)](../../design/hands-and-tools.md)<p>*Только HoloLens 2*</p> | **`MSFT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Сетка руки артикулатион +](../../design/hands-and-tools.md)<p>*Только HoloLens 2*</p> | <p>**`EXT` расширение, выпущенное в среде выполнения 102:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` расширение, выпущенное в среде выполнения 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Отслеживание глаз](../../design/eye-tracking.md)<p>*Только HoloLens 2*</p> | **`EXT` выпущенное расширение:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Взаимодействие с другими пакетами SDK для HoloLens<br />(например, [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*Только HoloLens 2*</p> | <p>**`MSFT` расширение, выпущенное в среде выполнения 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` расширение в [среде выполнения предварительной версии 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [Запись смешанной реальности <br /> (третья Визуализация с камеры PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Только HoloLens 2*</p> | **`MSFT` расширения, выпущенные в среде выполнения 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Взаимодействие с API CoreWindow UWP<br />(например, для клавиатуры или мыши) | **`MSFT` расширение, выпущенное в среде выполнения 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Профили взаимодействия контроллера движения (Samsung Одиссэй и HP REVERB G2) | **`MSFT` расширения, выпущенные в среде выполнения 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Модели отрисовки контроллера движения](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` расширение в [среде выполнения предварительной версии 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Основные сведения о сцене (плоскости, сетки)](../../design/scene-understanding.md)<p>*Только HoloLens 2*</p> | <p>**В [среде выполнения предварительной версии 102 или более поздней версии](openxr-getting-started.md#using-preview-extensions):**<br />Использование <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> с [сцену общие сведения о пакете SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT_preview` расширение в будущей среде выполнения предварительной версии** *(запланированное)*</p> |
| Другие расширения кросс-поставщика | <p>**`KHR`Выпущены официальные расширения:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` выпущенные расширения:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Хотя некоторые из этих расширений могут запускаться как расширения, зависящие от поставщика `MSFT` , корпорация Майкрософт и другие поставщики среды выполнения опенкср работают вместе для проектирования кросс-поставщиков `EXT` или `KHR` расширений для многих из этих функциональных областей.  Это обеспечит переносимость кода, который вы пишете для этих функций, между поставщиками среды выполнения, как и в случае с основной спецификацией.

## <a name="get-started-with-openxr"></a>Начало работы с OpenXR

Вы можете разрабатывать приложения, используя OpenXR с HoloLens 2 или иммерсивную гарнитуру Windows Mixed Reality с компьютером.  Если у вас нет доступа к гарнитуре, можно использовать эмулятор HoloLens 2 или симулятор Windows Mixed Reality.

Чтобы приступить к разработке приложений Опенкср для HoloLens 2 или впечатляющих головных телефонов Windows Mixed Reality, см. статью как приступить к разработке [опенкср](openxr-getting-started.md).

Для ознакомления со всеми основными компонентами API Опенкср и примерами реальных приложений, использующих Опенкср сегодня, ознакомьтесь с этим видео в 60-минутном пошаговом руководстве:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>См. также

* <a href="https://www.khronos.org/openxr/" target="_blank">Дополнительные сведения о Опенкср</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Спецификация Опенкср 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Справочник по API Опенкср 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Краткое справочное руководство по Опенкср 1,0</a>
