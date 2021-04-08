---
title: Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088667"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Инициализация проекта и развертывание первого приложения

Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK. Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2. Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

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

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>Импорт требуемых ресурсов TextMeshPro

В меню Unity выберите **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP), чтобы открыть окно Import Unity Package (Импорт пакета Unity):

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

В окне импорта пакета Unity нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK. Этот шаг можно пропустить, если вы не планируете использовать элементы пользовательского интерфейса MRTK в проекте.

## <a name="importing-the-mixed-reality-toolkit"></a>Импорт набора средств для смешанной реальности (MRTK)

Чтобы импортировать Mixed Reality Toolkit в проект Unity, необходимо использовать [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), которое позволяет разработчикам обнаруживать, обновлять и добавлять пакеты компонентов Смешанной реальности в проекты Unity. Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.

Скачайте последнюю версию средства Mixed Reality Feature Tool из [Центра загрузки Майкрософт](https://aka.ms/MRFeatureTool). По завершении скачивания разархивируйте файл и сохраните его на своем компьютере.

> [!NOTE]
> Перед запуском средства Mixed Reality Feature Tool установите [среду выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0).

> [!NOTE]
> Mixed Reality Feature Tool сейчас работает только в Windows. Для MacOS выполните [эту процедуру](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages), чтобы скачать и импортировать Mixed Reality Toolkit в проект Unity.

Откройте исполняемый файл **MixedRealityFeatureTool** из скачанной папки, чтобы запустить Mixed Reality Feature Tool.  

![Открытие MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>Настройка проекта Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Применение параметров конфигуратора проекта MRTK

Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

В окне конфигуратора проектов MRTK разверните раздел **Modify Configurations** (Изменение конфигураций), убедитесь, что все флажки включены, и нажмите кнопку **Apply**(Применить), чтобы применить эти параметры:

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:

> * Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки. Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) в документации по [производительности MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения. Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).

### <a name="2-configure-additional-project-settings"></a>2. Настройка дополнительных параметров проекта

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Создание сцены и настройка MRTK

Чтобы создать сцену, в меню Unity выберите **File** > **New Scene** (Файл > Новая сцена):

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

В меню Unity щелкните **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> Снижать разрядность глубины до 16 бит необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Совместное использование буфера глубины в HoloLens) в документации по <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">производительности MRTK</a>.

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте следующий пользовательский пакет Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage).

Чтобы импортировать пользовательский пакет Unity, в меню Unity щелкните **Assets** > **Import Package** > **Custom Package** (Ресурсы > Импорт пакетов > Пользовательский пакет), чтобы открыть окно импорта пакетов:

![Импорт настраиваемого пакета](images/mr-learning-base/base-02-section7-step1-1.png)

В окне Import package (Импорт пакета) выберите скачанный файл **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** и нажмите кнопку Open (Открыть):

![Выбор пакета ресурсов](images/mr-learning-base/base-02-section7-step1-2.png)

В окне импорта пакета Unity нажмите кнопку All (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку Import (Импорт), чтобы импортировать их.

![Выбор всех ресурсов для импорта](images/mr-learning-base/base-02-section7-step1-3.png)

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![Окно проекта Unity после импорта ресурсов](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>Настройка сцены

В окне Project (Проект) перейдите к папке Assets (Ресурсы ) > MRTK.Tutorials.GettingStarted > Prefabs (Заготовки):

В окне Project (Проект) щелкните и перетащите заготовку **Cube** в окно Hierarchy (Иерархия). Затем в окне Inspector (Инспектор) настройте ее компонент **Transform** (Трансформация) следующим образом:

* **Position** (Положение): X = 0, Y = 0, Z = 0,5.
* **Rotation** (Поворот): X = 0, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 1, Y = 1, Z = 1.

![Добавление объекта Cube в сцену](images/mr-learning-base/base-02-section8-step1-1.png)

Чтобы перенести фокус на объекты сцены, дважды щелкните объект **Cube**, а затем снова немного увеличьте масштаб представления:

Чтобы вы могли взаимодействовать с объектом и захватывать его с поддержкой отслеживания рук, в объекте должен быть компонент Collider (Коллайдер), например **Box Collider** (Прямоугольный коллайдер), компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт) и компонент **Near Interaction Grabbable (Script)** (Возможность захвата при близком взаимодействии — скрипт).

Оставив выбранным объект **Cube** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор). Затем найдите и выберите скрипт **Object Manipulator** (Манипулятор объектами), чтобы добавить его в объект Cube.

![Добавление скрипта Object Manipulator (Манипулятор объектами) в объект Cube](images/mr-learning-base/base-02-section8-step1-2.png)

Повторите те же действия, чтобы добавить в объект Cube скрипт **Near Interaction Grabbable** (Возможность захвата при близком взаимодействии).

![Добавление скрипта Near Interaction Grabbable (Возможность захвата при близком взаимодействии) в объект Cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> В нашем примере, когда добавляется компонент Object Manipulator (Script), автоматически добавляется и компонент Constraint Manager (Script), от которого тот зависит.

> [!NOTE]
> Для выполнения задач этого руководства в объект Cube уже добавлены коллайдеры. Чтобы получить дополнительные сведения о коллайдерах, воспользуйтесь <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">этим разделом</a> из документации по Unity.

Чтобы проверить это в редакторе Unity, можно перейти в режим воспроизведения и удерживать клавишу **SHIFT** слева или **ПРОБЕЛ** для включения контроллера. Контроллер можно перемещать, передвигая мышь, а приближать его к камере или удалять от нее вы можете с помощью колесика мыши. Наведите указатель на объект Cube, а затем нажмите и удерживайте **правую кнопку мыши**, чтобы переместить объект Cube.

![Режим игры](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a>Создание приложения в HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Создание проекта Unity

В меню Unity щелкните **File** > **Build Settings** (Файл > Параметры сборки), чтобы открыть окно параметров сборки.

В окне параметров сборки нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке), а затем нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки универсальной платформы Windows:

![Окно параметров сборки Unity с выбранным вариантом UWP](images/mr-learning-base/base-02-section9-step1-1.png)

В окне сборки универсальной платформы Windows выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_, создайте папку и присвойте ей понятное имя, например _GettingStarted_, а затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки:

![Окно параметров сборки Unity с окном выбора папки](images/mr-learning-base/base-02-section9-step1-2.png)

Подождите, пока Unity завершит сборку:

![Unity выполняет сборку](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Сборка и развертывание приложения

По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой. Перейдите в папку и дважды щелкните файл решения, чтобы открыть его в Visual Studio:

![Проводник Windows с выбранным созданным решением Visual Studio](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .

Настройте Visual Studio для устройства HoloLens, выбрав конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство):

![Среда Visual Studio, настроенная для развертывания в HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.

> [!NOTE]
> В HoloLens обычно выполняется сборка для архитектуры ARM. Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio. Рекомендуемое решение — выполните сборку для ARM64. Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.

> [!NOTE]
> Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP. Для этого в обозревателе решений щелкните правой кнопкой мыши имя_проекта (Universal Windows) и выберите **Set as StartUp Project** (Назначить запускаемым проектом).

Подключите HoloLens к компьютеру, а затем выберите **Debug** > **Start Without Debugging** (Отладка >Запуск без отладки), чтобы выполнить сборку и развертывание на устройстве:

![Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Перед выполнением сборки устройство нужно перевести в режим разработчика и связать с компьютером разработки. Оба эти действия можно выполнить, следуя [этим инструкциям](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.

Использование параметра запуска без отладки автоматически запускает приложение на устройстве без присоединения отладчика Visual Studio.

Выберите **Build > Deploy Solution** (Сборка > Развернуть решение), чтобы развернуть решение на устройстве без автоматического запуска приложения.

> [!NOTE]
>В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику). В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность. Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Поздравляем!

Вы развернули свое первое приложение HoloLens. Когда приложение откроется, перед вами должен отобразиться объект Cube. С ним можно взаимодействовать, перемещая его. Кроме того, когда вы будете передвигаться, должна отображаться сетка пространственного сопоставления, которая покрывает поверхности, воспринимаемые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения. Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK. В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Настройка профилей MRTK](mr-learning-base-03.md)