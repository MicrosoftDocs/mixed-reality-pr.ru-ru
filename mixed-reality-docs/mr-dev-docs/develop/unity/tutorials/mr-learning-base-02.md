---
title: Руководства по началу работы Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 62f79e1a50f8a2f0d2c8829b968e2c3bf5ee7403
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679383"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Инициализация проекта и развертывание первого приложения

## <a name="overview"></a>Обзор

Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK. Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2. Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.

## <a name="objectives"></a>Задачи

* Узнайте, как настроить Unity для разработки HoloLens.
* Узнайте, как создать и развернуть приложение в HoloLens.
* Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.

## <a name="creating-the-unity-project"></a>Создание проекта Unity

Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):

![Unity Hub с выделенной кнопкой создания](images/mr-learning-base/base-02-section1-step1-1.png)

В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).

![Unity Hub с раскрывающимся селектором версии NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.

В окне Create a new project (Создание нового проекта) сделайте следующее:

* Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.
* Укажите понятное **имя проекта**, например _MRTK Tutorials_.
* Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.
* Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.

![Unity Hub с окном создания проекта с внесенными данными](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> В Windows для переменной MAX_PATH есть ограничение в 255 символов. Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.

Подождите, пока Unity создаст проект:

![Unity выполняет создание проекта](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Переключение платформы сборки

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):

![Окно параметров сборки в Unity с выбранной платформой UWP](images/mr-learning-base/base-02-section2-step1-2.png)

Подождите, пока Unity переключит платформу:

![Unity выполняет переключение платформы](images/mr-learning-base/base-02-section2-step1-3.png)

Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:

![Окно сборки Unity с выделенным значком закрытия](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Импорт требуемых ресурсов TextMeshPro

В меню Unity выберите **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP), чтобы открыть окно Import Unity Package (Импорт пакета Unity):

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK. Этот шаг можно пропустить, если вы не планируете использовать элементы пользовательского интерфейса MRTK в проекте.

## <a name="importing-the-mixed-reality-toolkit"></a>Импорт набора средств для смешанной реальности (MRTK)

Скачайте пользовательский пакет Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

В меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:

![Выбор импорта пользовательского пакета в меню Unity](images/mr-learning-base/base-02-section4-step1-1.png)

В окне импорта пакетов выберите скачанный пакет **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** и щелкните кнопку **Open** (Открыть):

![Окно с запросом открытия пользовательского пакета при импорте в Unity](images/mr-learning-base/base-02-section4-step1-2.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![Окно импорта MRTK Foundation в Unity](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Настройка проекта Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Применение параметров конфигуратора проекта MRTK

Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

В окне конфигуратора проектов MRTK разверните раздел **Modify Configurations** (Изменение конфигураций), убедитесь, что все флажки включены, и нажмите кнопку **Apply**(Применить), чтобы применить эти параметры:

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!NOTE]
> Вы используете встроенные устаревшие возможности смешанной реальности в Unity, а не новую систему подключаемого модуля смешанной реальности, так как новая система не обеспечивает полную совместимость с [рекомендуемыми версиями Unity и MRTK](mr-learning-base-01.md#prerequisites), которые используются при работе с этой серией руководств. Поэтому вы можете игнорировать любую информацию или предупреждения о том, что встроенные возможности смешанной реальности не рекомендуются к использованию.

> [!TIP]
> Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:
>
> * Enable legacy XR (Включить традиционные возможности смешанной реальности): позволяет включить возможности виртуальной реальности для этого проекта.
> * Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки. Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).
> * Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения. Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).

### <a name="2-configure-additional-project-settings"></a>2. Настройка дополнительных параметров проекта

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проекта:

![Выбор в меню параметров проекта Unity](images/mr-learning-base/base-02-section5-step2-1.png)

В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), щелкните значок **+** и выберите Windows Mixed Reality, чтобы добавить пакет SDK для Windows Mixed Reality:

![Параметры смешанной реальности Unity с выбранным меню для добавления пакета SDK Windows Mixed Reality](images/mr-learning-base/base-02-section5-step2-2.png)

Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно конфигуратора проекта MRTK. Если этого не произошло, откройте его в меню Unity.

В окне конфигуратора проектов MRTK откройте раскрывающийся список **Audio spatializer** (Аудио спатиалайзер), чтобы выбрать **MS HRTF Spatializer** (Спатиалайзер MS HRTF), а затем нажмите кнопку **Apply** (Применить), чтобы применить параметр:

![Конфигуратор проекта MRTK в Unity с выбранным спатиалайзером MS HRTF](images/mr-learning-base/base-02-section5-step2-3.png)

> [!TIP]
> Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в [руководствах по пространственному звуку](unity-spatial-audio-ch1.md).

В окне Project Settings (Параметры проекта) выберите **Player** > **XR Settings** (Проигрыватель > Параметры XR), а затем в раскрывающемся списке **Depth Format** (Формат глубины) выберите **16-bit depth** (16-разрядная глубина):

![Параметры смешанной реальности в Unity с выбранной 16-битной глубиной](images/mr-learning-base/base-02-section5-step2-4.png)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) (Совместное использование буфера глубины в HoloLens) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).

В окне Project Settings (Параметры проекта) выберите **Player** > **Publishing Settings** (Проигрыватель >Параметры публикации), затем в поле **Package name** (Имя пакета) введите подходящее имя, например _MRTKTutorials-GettingStarted_:

![Параметры публикации Unity с настроенным именем пакета](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> Package name (Имя пакета) — это уникальный идентификатор приложения. Измените этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.

> [!TIP]
> Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, добавьте символ подчеркивания перед именем, чтобы при сортировке имя оказывалось вверху.

## <a name="creating-and-configuring-the-scene"></a>Создание и настройка сцены

Чтобы создать сцену, в меню Unity выберите **File** > **New Scene** (Файл > Новая сцена):

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), убедитесь, что профиль конфигурации **MixedRealityToolkit** имеет значение **DefaultMixedRealityToolkitConfigurationProfile** в окне Inspector (Инспектор):

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> Как правило, при разработке для HoloLens используется DefaultHoloLens2ConfigurationProfile. Но при работе с этим учебником вы будете использовать DefaultMixedRealityToolkitConfigurationProfile, а затем при работе со следующим учебником [по настройке профилей MRTK](mr-learning-base-03.md) — DefaultHoloLens2ConfigurationProfile.

В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

В окне сохранения сцены перейдите к папке **Scenes** проекта, присвойте сцене понятное имя, например _GettingStarted_, и нажмите кнопку **Save** (Сохранить), чтобы сохранить сцену:

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Создание приложения в HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Создание проекта Unity

В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.

В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:

![Окно параметров сборки Unity с выбранным вариантом UWP](images/mr-learning-base/base-02-section7-step1-1.png)

В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:

![Окно параметров сборки Unity с окном выбора папки](images/mr-learning-base/base-02-section7-step1-2.png)

Подождите, пока Unity завершит сборку:

![Unity выполняет сборку](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Сборка и развертывание приложения

По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой. Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:

![Проводник Windows с выбранным созданным решением Visual Studio](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .

Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):

![Среда Visual Studio, настроенная для развертывания в HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.

> [!NOTE]
> В HoloLens обычно выполняется сборка для архитектуры ARM. Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio. Рекомендуемое решение — выполните сборку для ARM64. Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.

> [!NOTE]
> Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP. Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).

Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:

![Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки. Оба эти действия можно выполнить, следуя [этим инструкциям](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.

Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.

Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.

> [!NOTE]
>В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику). В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность. Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Поздравляем!

Вы развернули свое первое приложение HoloLens. Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения. Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK. В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Настройка профилей MRTK](mr-learning-base-03.md)
