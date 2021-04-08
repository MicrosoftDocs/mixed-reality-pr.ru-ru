---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097071"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Включение поддержки микрофона и добавление поставщика данных для ввода речи

В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:

![Включение поддержки микрофона](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона. Если функция отключена, включите ее сейчас.

В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):

* Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.

![Поставщик данных для добавления новых голосовых команд](../images/mr-learning-base/base-09-section1-step1-2.png)

Укажите **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** в поле **Type** (Тип) нового поставщика данных.

![Параметры добавления новых речевых команд](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Включение поддержки микрофона и добавление поставщика данных для ввода речи

В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:

![Включение поддержки микрофона для OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#configuring-the-unity-project), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона. Если функция отключена, включите ее сейчас.

В окне Hierarchy (Иерархия) выберите объект MixedRealityToolkit, в окне инспектора откройте вкладку Input (Ввод):

* Разверните узел **Input Data Providers** (Поставщик входных данных) и нажмите кнопку **+ Add Data Provider** (+ Добавить поставщик данных), чтобы добавить новый поставщик данных.

![Добавление новых речевых команд для OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Укажите **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** в поле **Type** (Тип) нового поставщика данных.

![Параметры добавления новых речевых команд для OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Активация функции микрофона

В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:

![Включение поддержки микрофона](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона. Если функция отключена, включите ее сейчас.
