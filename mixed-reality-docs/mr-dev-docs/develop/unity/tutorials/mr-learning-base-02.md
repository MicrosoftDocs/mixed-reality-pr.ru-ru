---
title: Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: cab10789bc7ab86a4090a0db46e5445b728c7c8ad2dd904cba530e81f1bab18e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201439"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Инициализация проекта и развертывание первого приложения

Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки набора средств для смешанной реальности (MRTK) и импортировать MRTK. Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2. Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.

## <a name="objectives"></a>Задачи

* Узнайте, как настроить Unity для разработки HoloLens.
* Узнайте, как создать и развернуть приложение в HoloLens.
* Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.

### <a name="steps-overview"></a>Обзор шагов
:::row:::
    :::column:::
       ![Обзор шага 1 ](images/mr-learning-base/base-02-overview-step1.png) **1. Создание проекта Unity**
    :::column-end:::
    :::column:::
       ![Обзор шага 2](images/mr-learning-base/base-02-overview-step2.png) **2. Импорт MRTK в проект**
    :::column-end:::
    :::column:::
       ![Обзор шага 3](images/mr-learning-base/base-02-overview-step3.png) **3. Настройка новой сцены с помощью MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Обзор шага 4](images/mr-learning-base/base-02-overview-step4.png) **4. Сборка проекта Unity**
    :::column-end:::
    :::column:::
       ![Обзор шага 5](images/mr-learning-base/base-02-overview-step5.png) **5. Сборка проекта UWP**
    :::column-end:::
    :::column:::
       ![Обзор шага 6](images/mr-learning-base/base-02-overview-step6.png) **6. Запуск проекта на устройстве**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Создание проекта Unity

Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты) и щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

В раскрывающемся списке выберите **версию** Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.

В окне Create a new project (Создание нового проекта) сделайте следующее:

* Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.
* Укажите понятное **имя проекта**, например _MRTK Tutorials_.
* Выберите подходящее **расположение** для хранения проекта, например _D:\MixedRealityLearning_.
* Нажмите кнопку **Create** (Создать), чтобы создать и запустить новый проект Unity.

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> В Windows для переменной MAX_PATH есть ограничение в 255 символов. Поэтому следует сохранить проект Unity рядом с корневым каталогом диска.

Подождите, пока Unity создаст проект:

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Переключение платформы сборки

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

В окне параметров сборки щелкните элемент **Universal Windows Platform** (Универсальная платформа Windows). Затем сделайте следующее:

1. Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.
2. Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**. 
3. Для параметра **Build Type** (Тип сборки) выберите **D3D Project** (Проект D3D).
4. Задайте для параметра **Target SDK Version** (Целевая версия пакета SDK) значение **Latest Installed** (Последняя установленная версия).
5. Задайте для параметра **Minimum Platform Version** (Минимальная версия платформы) значение **10.0.1024.0**.
6. Задайте для параметра **Visual Studio Version** (Версия Visual Studio) значение **Latest Installed** (Последняя установленная версия).
7. Задайте для параметра **Build and Run on** (Устройство для сборки и выполнения) значение **USB Device** (USB-устройство).
8. Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.
9. Нажмите кнопку Switch Platform (Сменить платформу).

![Окно параметров сборки Unity с заданным параметром Universal Windows Platform (Универсальная платформа Windows)](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Подождите, пока Unity переключит платформу:

![Unity выполняет переключение платформы](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Когда Unity переключит платформу, щелкните значок **x**, чтобы закрыть окно параметров сборки.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity

Чтобы импортировать Mixed Reality Toolkit в проект Unity, необходимо использовать [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), которое позволяет разработчикам обнаруживать, обновлять и добавлять пакеты компонентов Смешанной реальности в проекты Unity. Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.

Скачайте последнюю версию средства Mixed Reality Feature Tool из [Центра загрузки Майкрософт](https://aka.ms/MRFeatureTool). По завершении скачивания разархивируйте файл и сохраните его на своем компьютере.

> [!NOTE]
> Перед запуском средства Mixed Reality Feature Tool установите [среду выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer).

Откройте исполняемый файл **MixedRealityFeatureTool** из скачанной папки, чтобы запустить Mixed Reality Feature Tool.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Создание сцены и настройка MRTK

В меню Unity выберите **File**  >  **New Scene** (Файл > Новая сцена):

![Выбор новой сцены в меню Unity](images/mr-learning-base/base-02-section6-step1-1.png)

В окне **New Scene** (Новая сцена) выберите **Basic (Built-in)** (Базовая — встроенная) и щелкните **Create**, чтобы создать сцену.

![Окно создания сцены Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> Приведенный выше снимок экрана относится к Unity версии 2020. Если вы используете Unity 2019, то при нажатии кнопки **Create** будет создана пустая сцена.

В меню Unity щелкните **Mixed Reality**  >  **Toolkit**  >  **Add to Scene and Configure...** (Смешанная реальность > Набор средств > Добавить в сцену и настроить), чтобы добавить MRTK в текущую сцену:

![Выбор добавления в сцену и настройки в меню Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), убедитесь, что профиль конфигурации **MixedRealityToolkit** имеет значение **DefaultMixedRealityToolkitConfigurationProfile** в окне Inspector (Инспектор):

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

В меню Unity щелкните **File** > **Save As...** (Файл > Сохранить как), чтобы открыть окно сохранения сцены:

![Выбор пользовательского сохранения в меню Unity](images/mr-learning-base/base-02-section6-step1-4.png)

Сохраните сцену в проекте в разделе **Asset** (Ресурсы)  >  **Scenes** (Сцены).

![Окно с запросом сохранения сцены в Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Добавление взаимодействия с рукой к объекту

В меню Unity выберите **GameObject**  >  **3D Object**  >  **Cube**, чтобы добавить объект куба в сцену.

![Добавление объекта Cube в сцену](images/mr-learning-base/base-02-section8-step1-1.png)

Щелкните объект **Cube** в окне Hierarchy (Иерархия), а затем в окне инспектора настройте его компонент **Transform** (Преобразование) следующим образом.

* **Position** (Положение): X = 0, Y = –0,1, Z = 0,5.
* **Rotation** (Поворот): X = 0, Y = 0, Z = 0.
* **Scale** (Масштаб): X = 0,1, Y = 0,1, Z = 0,1.

1 единица Unity — 1 метр. Размер куба обновлен до 10 x 10 x 10 см, помещен в 50 см от позиции гарнитуры (0; 0; 0). На 10 см ниже уровня взгляда для удобного взаимодействия. 

Если используется масштаб по умолчанию (1; 1; 1), куб будет слишком большим. Если используется положение по умолчанию (0; 0; 0), куб будет размещаться в той же позиции, что и гарнитура, и вы не сможете увидеть ее, пока не переместитесь назад.

![Настройка сведений о преобразовании](images/mr-learning-base/base-02-section8-step1-1b.png)

Чтобы перенести фокус на объекты сцены, дважды щелкните объект **Cube**, а затем снова немного увеличьте масштаб представления. Также можно использовать клавишу F для масштабирования и фокусировки на объекте.

Для взаимодействия и захвата объекта с помощью отслеживаемых рук объект должен иметь:
 * компонент коллайдера **Box Collider** (объект куба в Unity уже имеет компонент Box Collider по умолчанию);
 * компонент **Object Manipulator (Script)** (Манипулятор объектами — скрипт).
 * компонент **NearInteractionGrabbable(Script)** .

Сценарий MRTK **ObjectManipulator** делает объект перемещаемым, масштабируемым и вращаемым, используя одну или две руки. Этот сценарий поддерживает модель ввода прямого манипулирования, так как он позволяет пользователю касаться голограммы непосредственно руками.

Оставив выбранным объект **Cube** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор). Затем найдите и выберите скрипт **Object Manipulator** (Манипулятор объектами), чтобы добавить его в объект Cube.

![Добавление скрипта Object Manipulator (Манипулятор объектами) в объект Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

Повторите те же действия, чтобы добавить в объект Cube скрипт **Near Interaction Grabbable** (Возможность захвата при близком взаимодействии).

![Добавление скрипта Near Interaction Grabbable (Возможность захвата при близком взаимодействии) в объект Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> В нашем примере, когда добавляется компонент Object Manipulator (Script), автоматически добавляется и компонент Constraint Manager (Script), от которого тот зависит.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Тестирование приложения в редакторе Unity с имитацией ввода MRTK

С помощью имитации ввода MRTK можно тестировать различные типы взаимодействий в редакторе Unity, не создавая и не развертывая их на устройстве. Это позволяет быстро проверять свои идеи в процессе проектирования и разработки. Используйте сочетания клавиш и мыши для управления имитацией входных данных.

Нажмите кнопку воспроизведения и войдите в режим воспроизведения. Удерживайте левую клавишу **SHIFT** или **ПРОБЕЛ**, чтобы отобразить контроллер (имитация рук). Перемещение мыши переместит контроллер, а также его можно переместить ближе к камере или дальше от нее с помощью колесика мыши. Наведите указатель на объект Cube, а затем нажмите и удерживайте **левую кнопку мыши**, чтобы захватить объект Cube.

* Чтобы переместить камеру, нажимайте клавиши **W, A, S, D, Q, E**.
* Чтобы посмотреть по сторонам, перемещайте мышь при нажатой **правой кнопке мыши**.
* Нажмите клавишу **ПРОБЕЛ (правой рукой)** или клавишу **SHIFT (левой рукой)** , чтобы отобразить имитацию рук.
* Нажмите клавишу **T** или **Y**, чтобы удерживать имитацию рук в поле зрения.
* Чтобы повернуть смоделированные руки, нажмите и удерживайте клавишу **CTRL** и перемещайте указатель мыши.

![Режим игры](images/mr-learning-base/base-02-section8-step1-4.gif)


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
