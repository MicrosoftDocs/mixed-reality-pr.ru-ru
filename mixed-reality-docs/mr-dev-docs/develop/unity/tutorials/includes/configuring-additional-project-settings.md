---
ms.openlocfilehash: 2b0dc328a1a47d9a0bd385cac6a88563dcc3938d
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107327723"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

![Выбор в меню параметров проекта Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

В окне Project Settings (Параметры проекта) выберите **XR Plug-in Management (Управление подключаемым модулем смешанной реальности)**  > **Install XR Plug-in Management (Установить пакет для управления подключаемым модулем смешанной реальности)** :

![Параметры XR Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

После установки пакета для управления подключаемым модулем смешанной реальности в Unity сделайте следующее. Убедитесь, что вы выбрали параметр Universal Windows Platform (Универсальная платформа Windows). Установите флажки **Initialize XR on Startup** (Инициализировать смешанную реальность при запуске) и **Windows Mixed Reality**.

![Раздел параметров XR Unity с меню для добавления пакета SDK Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK. Если этого не произошло, откройте его в меню Unity.

В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Раздел параметров XR Unity с выбранным меню пакета SDK Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.

В окне Project Settings (Параметры проекта), выберите **XR Plug-in Management (Управление подключаемым модулем XR)**  > **Windows Mixed Reality** > **Runtime Settings (Параметры среды выполнения)** . Затем в раскрывающемся списке **Depth Buffer Format** (Формат буфера глубины) выберите **16-bit depth** (16-битная глубина):

![Раздел параметров публикации Unity с выделенным именем пакета](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">производительности MRTK</a>.

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Раздел параметров публикации Unity с именем пакета](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

![Выбор в меню параметров проекта Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

В окне Project Settings (Параметры проекта) выберите **XR Plug-in Management (Управление подключаемым модулем смешанной реальности)**  > **Install XR Plug-in Management (Установить пакет для управления подключаемым модулем смешанной реальности)** :

![Раздел параметров XR Unity с выбранным параметром Install XR plug-in management (Установка средства управления подключаемым модулем XR)](../images/mr-learning-base/base-02-section5-step2-2.png)

После установки пакета для управления подключаемым модулем смешанной реальности в Unity сделайте следующее. Убедитесь, что вы выбрали параметр Universal Windows Platform (Универсальная платформа Windows). Установите флажки **Initialize XR on Startup** (Инициализировать смешанную реальность при запуске), **OpenXR** и **Microsoft HoloLens feature set** (Набор функций Microsoft HoloLens).

![Раздел параметров XR Unity с выбранными параметрами OpenXR и Microsoft HoloLens feature set (Набор функций Microsoft HoloLens).](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

В строке меню в верхней части экрана перейдите в раздел **Mixed Reality (Смешанная реальность) > OpenXR > Apply recommended project settings for HoloLens 2 (Применить рекомендуемые параметры проекта для HoloLens 2)** , чтобы повысить производительность приложения.

![Меню смешанной реальности с выбранными параметрами OpenXR и Apply recommended project settings for HoloLens 2 (Применить рекомендуемые параметры проекта для HoloLens 2)](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
>Если рядом с параметром подключаемого модуля OpenXR (предварительная версия) отображается красный предупреждающий значок, щелкните его и выберите Fix all (Исправить все), прежде чем продолжать работу. Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.
>![Меню проверки проекта OpenXR со всеми проблемами, выбранными для исправления.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Когда Unity завершит импорт необходимых файлов, должно снова отобразиться окно MRTK Project Configurator (Конфигуратор проекта MRTK). Если этого не произошло, откройте его в меню Unity.

В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Окно конфигуратора МРТК с выбранными параметрами по умолчанию](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.


В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Unity с открытыми параметрами публикации](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), установите флажок **Virual Reality Supported** (Поддержка виртуальной реальности), щелкните значок **+** и выберите Windows Mixed Reality, чтобы добавить пакет SDK Windows Mixed Reality:

![Раздел параметров смешанной реальности Unity, выбрано меню для добавления пакета SDK Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-4.png)

Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную из меню Unity, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для смешанной реальности > Служебные программы > Настроить проект Unity).

В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Окна настройки MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.

В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):

![Включение 16-разрядной глубины в Unity](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Раздел параметров публикации Unity. Задано имя пакета](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.
