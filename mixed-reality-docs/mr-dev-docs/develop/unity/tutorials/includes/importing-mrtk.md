---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175736"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool. Затем щелкните **Discover Features** (Обнаружение компонентов).

> [!NOTE]
> При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_". Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.

> [!Important]
> Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity. Папка должна содержать папки ресурсов, пакетов и параметров проекта.

Функции группируются по категориям. чтобы упростить поиск. Щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с набором средств смешанной реальности, и щелкните раскрывающийся список **Platform Support** (Поддержка платформ), чтобы найти пакеты, относящиеся к различным платформам.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Установите флажок **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK 2.7.2**, также укажите **Mixed Reality OpenXR Plugin 1.0.0** и щелкните раскрывающийся список, чтобы выбрать последнюю версию, а затем нажмите кнопку **Get features** (Получить компоненты), чтобы скачать выбранные пакеты.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Настройка проекта Unity

После того, как Unity завершит импорт пакета из предыдущего раздела, появится предупреждающее сообщение о перезапуске редактора Unity. Это нужно, чтобы подключить новую систему модулей. Нажмите кнопку **Yes**.

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

После перезапуска Unity должно появиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).

![Открытие окна конфигуратора проекта MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Щелкните **Unity OpenXR Plugin**, чтобы включить управление подключаемым модулем XR и добавить необходимые пакеты в проект.

![Добавление подключаемого модуля Unity OpenXR ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Нажмите кнопку **Show XR Plug-In Management Settings** (Показывать параметры управления подключаемым модулем XR) в конфигураторе проектов MRTK, чтобы импортировать необходимые пакеты Unity для управления модулем XR.

![Отображение параметров управления подключаемым модулем XR ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Откроется **окно параметров проекта**. В окне параметров проект в разделе **XR Plug-in Management** (Управление подключаемым модулем XR) проверьте, что вы используете параметры универсальной платформы Windows (вкладка с логотипом Windows). Кроме того, проверьте, что установлен флажок **Initialize XR on Startup** (Инициализировать XR при запуске), а затем установите флажки **OpenXR** и **Microsoft HoloLens feature set** (Набор функций Microsoft HoloLens), чтобы включить их.

![Включение Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

После установки флажка OpenXR в окне конфигуратора проекта MRTK будет отображаться обновленное сообщение с кнопкой **Apply Settings** (Приметь параметры). Нажмите кнопку **Apply Settings** (Приметь параметры). 

![Окно параметров проекта 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

При нажатии кнопки Apply Settings (Применить параметры) это сообщение об ошибке может появиться в консоли. Если это единственная ошибка или ошибки нет, можно продолжать работу.

![Сообщение об ошибке удаленного взаимодействия OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Чтобы проверить конфигурацию OpenXR, щелкните **OpenXR** в разделе **XR Plug-in Management** (Управление подключаемыми модулями XR) и проверьте следующие элементы:
* Режим глубины при отправке: **16-битная глубина**
* Профили взаимодействия: **Microsoft Hand Interaction Profile** (профиль взаимодействия с помощью рук)

![Окно параметров проекта 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> Уменьшать разрядность глубины до 16 битов необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.


В окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) нажмите кнопку **Next** (Далее), а затем кнопку **Apply**, чтобы применить параметры. Если вы закрыли окно, откройте его вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).

![Окно параметров проекта 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Окно параметров проекта 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

После нажатия кнопки Apply (Применить) Unity попытается перезапуститься, чтобы применить параметры входной системы. Нажмите кнопку **Apply** (Применить), чтобы перезапустить редактор Unity.

### <a name="configure-additional-project-settings"></a>Настройка дополнительных параметров проекта

В меню Unity выберите **Edit** > **Project Settings...** (Правка > Параметры проекта…), чтобы открыть окно параметров проекта.

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Раздел параметров публикации Unity. Задано имя пакета](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.

# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool. Затем щелкните **Discover Features** (Обнаружение компонентов).

> [!NOTE]
> При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_". Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.

> [!Important]
> Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity. Папка должна содержать папки ресурсов, пакетов и параметров проекта.

Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK версии 2.7.0**. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Настройка проекта Unity

Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).

![Открытие средства конфигуратора MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Щелкните **Built-in Unity Plugin(non-OpenXR)** (Встроенные модуль Unity — не OpenXR), чтобы включить управление подключаемым модулем XR и добавить необходимые пакеты в проект.

![ Средство конфигуратора MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> Приведенный выше снимок экрана относится к Unity 2020, если вы используете Unity 2019, выберите **XR SDK/XR Management** (Пакет SDK XR или управление XR).

Нажмите кнопку **Show Settings** (Показать параметры) в конфигураторе проектов MRTK, чтобы импортировать необходимые пакеты Unity для управления модулем XR.

![Окно параметров воспроизведения](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Откроется **окно параметров проекта**. В окне параметров проекта в разделе **XR Plug-in Management** (Управление подключаемыми модулями XR). Перейдите в параметры универсальной платформы Windows и проверьте, что установлен флажок **Initialize XR on Startup** (Инициализировать XR при запуске), и установите флажок **Windows Mixed Reality**.

![Окно параметров воспроизведения — включение смешанной реальности — xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK. Если этого не произошло, откройте его в меню Unity.

В окне конфигуратора проектов MRTK щелкните **Next** (Далее) откройте раскрывающийся список Audio spatializer, выберите в нем **MS HRTF Spatializer**, а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Конфигуратор проекта MRTK — xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:

> * Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки. Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения. Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).

> [!TIP]
> Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.

Чтобы завершить настройку проекта Unity для XRSDK, нажмите кнопку **Next** (Далее), а затем щелкните **Done** (Готово) в окне конфигуратора проекта MRTK.

### <a name="configure-additional-project-settings"></a>Настройка дополнительных параметров проекта

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

В окне Project Settings (Параметры проекта), выберите **XR Plug-in Management (Управление подключаемым модулем XR)**  > **Windows Mixed Reality** > **Runtime Settings (Параметры среды выполнения)** . Затем в раскрывающемся списке **Depth Buffer Format** (Формат буфера глубины) выберите **16-bit depth** (16-битная глубина):

![Включение 16-разрядной глубины в Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Раздел параметров публикации Unity. Задано имя пакета](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

После открытия **MixedRealityFeatureTool** щелкните кнопку **Start** (Запуск), чтобы начать работу с Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Сначала необходимо указать для Mixed Reality Feature Tool **Project path** (Путь к проекту) с помощью кнопки **с многоточием**. Нажмите кнопку с тремя точками рядом с путем к проекту и перейдите к папке проекта в проводнике, например в _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

После того как вы нашли папку проекта, нажмите кнопку Open (Открыть), чтобы вернуться к средству Mixed Reality Feature Tool. Затем щелкните **Discover Features** (Обнаружение компонентов).

> [!NOTE]
> При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_". Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.

> [!Important]
> Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity. Папка должна содержать папки ресурсов, пакетов и параметров проекта.

Функции группируются по категориям. Чтобы упростить поиск, щелкните раскрывающийся список **Mixed Reality Toolkit**, чтобы найти пакеты, связанные с Набором средств для Смешанной реальности.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Установите флажок напротив **Mixed Reality Toolkit Foundation** и щелкните раскрывающийся список рядом с ним, чтобы выбрать **MRTK версии 2.7.0**. Затем нажмите кнопку **Get features** (Получить функции), чтобы скачать выбранные пакеты.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Затем нажмите кнопку **Validate** (Проверить), чтобы проверить выбранный пакет. Отобразится всплывающее окно с сообщением **No validation issues were detected** (Проблемы с проверкой не обнаружены). Щелкните **ОК**, чтобы закрыть окно, и нажмите кнопку **Import** (Импорт).

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Нажмите кнопку **Approve** (Утвердить), чтобы добавить **Mixed Reality Toolkit** в проект.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Настройка проекта Unity

Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную, щелкнув **Mixed Reality** > **Toolkit** >  **Utilities** > **Configure Project for MRTK** (Смешанная реальность > Набор средств > Служебные программы > Настроить проект для MRTK).

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Щелкните **Legacy XR**, чтобы включить устаревшие XR и добавить необходимые пакеты в проект.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Нажмите кнопку Next (Далее), чтобы включить параметры конвейера XR для устаревших XR.

![Окно настройки MRTK Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

В окне конфигуратора проектов MRTK установите флажки для всех параметров, откройте раскрывающийся список **Audio spatializer**, выберите в нем **MS HRTF Spatializer**, а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Окна настройки MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:

> * Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки. Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения. Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).

> [!TIP]
> Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">учебниках по пространственному звуку</a>.

Чтобы завершить настройку проекта Unity для Legacy XR, нажмите кнопку **Next** (Далее), а затем щелкните **Done** (Готово) в окне конфигуратора проекта MRTK.

### <a name="configure-additional-project-settings"></a>Настройка дополнительных параметров проекта

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):

![Включение 16-разрядной глубины в Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по производительности MRTK.

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Раздел параметров публикации Unity. Задано имя пакета](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.
