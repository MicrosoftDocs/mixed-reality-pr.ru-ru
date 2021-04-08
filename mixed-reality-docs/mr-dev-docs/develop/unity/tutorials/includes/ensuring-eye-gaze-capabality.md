---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097741"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Включение поддержки ввода данных с помощью взгляда и добавление соответствующего поставщика данных

В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.

![Окно конфигурации проекта MRTK в Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), при настройке проекта Unity в начале работы с этой серией руководств. Если функция отключена, включите ее сейчас.

В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):

* Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.

![Добавление поставщика данных 1 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-2.png)

Укажите **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** в поле **Type** (Тип) нового поставщика данных.

![Добавление поставщика данных 2 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Включение поддержки ввода данных с помощью взгляда и добавление соответствующего поставщика данных

В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):

* Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.

![Добавление поставщика данных 1 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Укажите **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** в поле **Type** (Тип) нового поставщика данных.

![Добавление поставщика данных 2 для ввода с помощью глаз](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Проверка того, включена ли функция ввода с использованием взгляда

В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.

![Окно конфигурации проекта MRTK в Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), при настройке проекта Unity в начале работы с этой серией руководств. Если функция отключена, включите ее сейчас.
