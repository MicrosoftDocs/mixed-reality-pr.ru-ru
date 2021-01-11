---
title: Руководства по MRTK — 2 Инициализация проекта и развертывание первого приложения
description: Из этого курса вы узнаете, как настроить проект Unity для работы с Mixed Reality Toolkit (MRTK) и как развернуть его на HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859533"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Инициализация проекта и развертывание первого приложения

## <a name="overview"></a>Обзор

Из этого учебника вы узнаете, как создать проект Unity, настроить его для разработки <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">набора средств для смешанной реальности (MRTK)</a> и импортировать MRTK. Вы также узнаете, как настроить, создать и развернуть базовую сцену Unity из Visual Studio на HoloLens 2. Развернув ее на HoloLens 2, вы увидите, как виртуальная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения.

## <a name="objectives"></a>Задачи

* Узнайте, как настроить Unity для разработки HoloLens.
* Узнайте, как создать и развернуть приложение в HoloLens.
* Изучите возможности сетки пространственного сканирования, виртуальных рук и счетчика частоты кадров на устройстве HoloLens 2.

## <a name="creating-the-unity-project"></a>Создание проекта Unity

1. Запустите **Unity Hub**, откройте вкладку **Projects** (Проекты), а затем щелкните **стрелку вниз** рядом с кнопкой **New** (Создать):

![Unity Hub с выделенной стрелкой вниз для кнопки "Создать"](images/mr-learning-base/base-02-section1-step1-1.png)

2. В раскрывающемся списке выберите версию Unity, указанную в разделе с [предварительными требованиями](mr-learning-base-01.md#prerequisites).

![Выбор версии Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Если конкретная версия Unity недоступна в Unity Hub, можно запустить установку из <a href="https://unity3d.com/get-unity/download/archive" target="_blank">архива загрузок</a> Unity.

3. В окне **Create a new project** (Создание нового проекта) сделайте следующее:

    * Убедитесь, что для параметра **Templates** (Шаблоны) задано значение **3D**.
    * В поле **Project Name** (Имя проекта) введите подходящее имя для проекта (например, "MRTK Tutorials").
    * Нажмите кнопку с тремя точками рядом с элементом **Location** (Расположение), а затем перейдите к папке, в которой нужно сохранить проект.

> [!CAUTION]
> В Windows для переменной MAX_PATH есть ограничение в 255 символов. Поэтому проект Unity желательно сохранять ближе к корневому каталогу диска.

    * Нажмите кнопку **Создать** . Будет создан и запущен новый проект Unity.

![Unity Hub с указанными значениями в окне "Create a new project" (Создание нового проекта)](images/mr-learning-base/base-02-section1-step1-3.png)

Строка состояния позволяет отслеживать ход выполнения.

![Индикатор выполнения Unity постоянно информирует вас о состоянии процесса создания проекта](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Переключение платформы сборки

1. В строке меню выберите **File** > **Build Settings...** (Файл > Параметры сборки...).

![Выбор параметров сборки Unity в меню](images/mr-learning-base/base-02-section2-step1-1.png)

2. В окне **Build Settings** (Параметры сборки) щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу).

![Окно параметров сборки в Unity с выбранной платформой UWP](images/mr-learning-base/base-02-section2-step1-2.png)

3. Дождитесь, пока Unity завершит переключение платформы, а затем закройте окно **Build Settings** (Параметры сборки).

## <a name="importing-the-textmeshpro-essential-resources"></a>Импорт требуемых ресурсов TextMeshPro

Ресурсы TextMeshPro требуются для элементов пользовательского интерфейса MRTK. Этот шаг можно пропустить, если вы не намерены использовать элементы пользовательского интерфейса MRTK в проекте.

1. На панели меню щелкните **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Окно > TextMeshPro > Импорт требуемых ресурсов TMP):

![Выбор Import TMP Essential Resources (Импорт требуемых ресурсов TMP) в меню](images/mr-learning-base/base-02-section3-step1-1.png)

2. В окне **Import Unity Package** (Импорт пакета Unity) нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их:

![Окно импорта требуемых ресурсов TMP в Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Импорт набора средств для смешанной реальности (MRTK)

1. Скачайте пользовательский пакет Unity:

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. В строке меню щелкните **Assets** > **Import Package** > **Custom Package...** (Активы > Импортировать пакеты > Пользовательский пакет...).
3. В диалоговом окне **Import package...** (Импорт пакета...) перейдите к расположению только что скачанного пакета, выберите его и нажмите кнопку **Open** (Открыть).
4. В окне **Import Unity Package** (Импорт пакета Unity) нажмите кнопку **All** (Все), чтобы выбрать все ресурсы, а затем нажмите кнопку **Import** (Импорт), чтобы импортировать их.

## <a name="selecting-mrtk-and-project-settings"></a>Выбор MRTK и параметров проекта

Когда Unity завершит импорт пакета из предыдущего раздела, должно отобразиться окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). В противном случае откройте это окно вручную, щелкнув **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств для Смешанной реальности > Служебные программы > Настроить проект Unity).

![Выбор пункта Configure Unity Project (Настройка проекта Unity) в меню Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. Если потребуется, в окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) разверните раздел **Modify Configurations** (Изменение конфигураций) и убедитесь, что выбраны все параметры.

![Окно конфигуратора проекта MRTK, где отображается раздел Modify Configurations (Изменение конфигураций)](images/mr-learning-base/base-02-section5-step1-2.png)

2. Чтобы применить параметры, нажмите кнопку **Apply** (Применить).

![Кнопка Apply (Применить) в MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> Вы используете встроенные устаревшие возможности смешанной реальности в Unity, а не новую систему подключаемого модуля смешанной реальности, так как новая система не обеспечивает полную совместимость с [рекомендуемыми версиями Unity и MRTK](mr-learning-base-01.md#prerequisites), которые используются при работе с этой серией руководств. Если поступят предупреждения об устаревании встроенных средств XR, их можно игнорировать.

> [!TIP]
> Применять параметры MRTK по умолчанию необязательно, но настоятельно рекомендуется, так как это поможет настроить некоторые рекомендуемые параметры Unity:
>
> * Enable legacy XR (Включить традиционные возможности смешанной реальности): позволяет включить возможности виртуальной реальности для этого проекта.
> * Set Single Pass Instanced rendering path (Задать путь однопроходной отрисовки экземпляра.): повышает производительность графики благодаря выполнению конвейера отрисовки для обоих глаз в одном вызове отрисовки. Дополнительные сведения см. в разделе [Однопроходная отрисовка экземпляра](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).
> * Set default Spatial Awareness layer (Задать слой отслеживания пространственного положения по умолчанию): создает слой Unity с именем Spatial Awareness и настраивает MRTK для использования этого слоя для сетки отслеживания пространственного положения. Дополнительные сведения о слоях Unity см. в документации Unity <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Настройка рабочего пространства).

3. В строке меню выберите **Edit** > **Project Settings...** (Правка > Параметры проекта...).

4. В окне **Project Settings** (Параметры проекта) выберите элемент **Player** (Воспроизведение), затем откройте раскрывающийся список **XR Settings** (Параметры XR) и установите флажок рядом с параметром **Virtual Reality Supported** (Поддержка виртуальной реальности):

![Параметры XR в Unity, где отображается флажок Virtual Reality Supported (Поддержка виртуальной реальности)](images/mr-learning-base/base-02-section5-step2-2.png)

Это действие позволяет импортировать пакет SDK для Windows Mixed Reality:

![Параметры XR в Unity, где отображаются пакеты SDK для виртуальной реальности](images/mr-learning-base/mixed-reality-sdk.png)

Когда Unity завершит импорт пакета SDK для Windows Mixed Reality, должно снова отобразиться окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Если окно не отображается, откройте его вручную. Для этого выберите элементы **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Набор средств смешанной реальности > Средства > Настройка проекта Unity).

5. В окне **MRTK Project Configurator** (Конфигуратор проекта MRTK) щелкните раскрывающийся список **Audio spatializer** (Аудиоспатиалайзер) и выберите вариант **MS HRTF Spatializer** (Спатиалайзер MS HRTF).

![Параметры проекта, где отображаются варианты аудиоспатиалайзера](images/mr-learning-base/base-02-section5-step2-3.png)

6. Нажмите кнопку **Применить**. Окно **MRTK Project Configurator** (Конфигурация проекта MRTK) будет закрыто.

    > [!TIP]
    > Настраивать свойство аудиоспатиалайзера необязательно, но это может упростить работу со звуком в проекте. Если задать для свойства значение MS HRTF Spatializer (Спатиалайзер MS HRTF), этот подключаемый модуль спатиалайзера будет использоваться при включенном свойстве AudioSource.spatialize в Unity. Дополнительные сведения см. в руководствах по пространственному звуку.

7. В окне **Project Settings** (Параметры проекта) щелкните раскрывающийся список **Depth Format** (Формат глубины) и выберите вариант **16-bit depth** (16-битная глубина).

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Параметры XR в Unity с выбранной 16-битной глубиной.":::

    > [!TIP]
    > Уменьшать разрядность глубины до 16 битов необязательно, но это может улучшить производительность графики в проекте. Дополнительные сведения см. в разделе [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) (Совместное использование буфера глубины в HoloLens) в документации по [производительности MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).

8. Щелкните раскрывающийся список **Publishing Settings** (Параметры публикации), а затем в поле **Package name** (Имя пакета) введите подходящее имя (например, "MRTK-Tutorials-Getting-Started").

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Параметры публикации Unity с настроенным именем пакета":::

    **Имя пакета и название продукта**

    - Package name (Имя пакета) — это уникальный идентификатор приложения. Создайте этот идентификатор перед развертыванием приложения, чтобы избежать перезаписи установленных ранее приложений.
    - Product Name (Название продукта) — это имя, отображаемое в меню запуска HoloLens. Чтобы упростить размещение приложения во время разработки, можно добавить перед именем символ подчеркивания, чтобы при сортировке это имя оказывалось вверху.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Параметры проекта Unity с настроенным именем продукта.":::

9. Закройте окно **Project Settings** (Параметры проекта).

## <a name="creating-and-configuring-the-scene"></a>Создание и настройка сцены

1. В строке меню выберите элементы **File** > **New Scene** (Файл > Новая сцена).
2. Чтобы добавить MRTK в текущую сцену, в строке меню щелкните элемент **Mixed Reality Toolkit** > **Add to Scene and Configure** (Набор средств для смешанной реальности >Добавить в сцену и настроить).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Путь в меню Unity &quot;Add to Scene and Configure...&quot; (Добавить в сцену и настроить)":::

3. Убедитесь, что в окне **Hierarchy** (Иерархия) выбран элемент **MixedRealityToolkit**.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Убедитесь, что выбран элемент MixedRealityTookit.":::

4. В окне **Inspector** (Инспектор), в разделе **MixedRealityToolkit** проверьте, установлен ли профиль конфигурации **DefaultMixedRealityToolkitConfigurationProfile**.

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultMixedRealityTookitConfigurationProfile":::

    > [!IMPORTANT]
    > Как правило, при разработке для HoloLens используется DefaultHoloLens2ConfigurationProfile. Но для работы с этим руководством вы будете использовать DefaultMixedRealityToolkitConfigurationProfile. В следующем руководстве [Настройка профилей MRTK](mr-learning-base-03.md) вы измените это значение на DefaultHoloLens2ConfigurationProfile.

5. В строке меню выберите **File** > **Save As...** (Файл > Сохранить как).
6. В диалоговом окне **Save Scene** (Сохранение сцены) перейдите к папке проекта **Scenes**. В поле **File name** (Имя файла) укажите подходящее имя сцены (например, \_GettingStarted\_) и нажмите кнопку **Save** (Сохранить).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Окно Unity с запросом на сохранение сцены":::.

## <a name="building-and-deploying-to-your-hololens-2"></a>Сборка и развертывание для HoloLens 2

> Перед сборкой для устройства убедитесь, что выполняются следующие условия:
- Устройство находится в режиме разработчика.
- Устройство связано с компьютером разработки. Если это не так, в процессе сборки в Visual Studio отобразится следующее диалоговое окно:

![Ввод ПИН-кода для связывания устройств](images/mr-learning-base/pin-request.png)

 Дополнительные сведения об этих действиях см. в статье [Развертывание и отладка с помощью Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).

1. В строке меню выберите **File** > **Build Settings...** (Файл > Параметры сборки...).
2. В окне **Build Settings** (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).

![Добавление текущей сцены в список Scenes In Build (Сцены в сборке)](images/mr-learning-base/base-02-section7-step1-1.png)

3. Нажмите кнопку **Сборка**.

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Нажмите кнопку Сборка.":::

4. В диалоговом окне **Build Universal Windows Platform** (Сборка для универсальной платформы Windows) выберите подходящее расположение для хранения сборки (например, создайте подпапку Builds в папке "MRTK Tutorials"). Создайте новую папку и присвойте ей подходящее имя (например, GettingStarted), выберите эту папку и нажмите кнопку **Select Folder** (Выбрать папку), чтобы запустить процесс сборки.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Окно сборки Unity, где отображается папка сборки.":::

    Появится строка состояния с постоянно обновляемой информацией о ходе выполнения сборки.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Отображение сведений о состоянии сборки в Unity":::

    > [!TIP]
    > Кроме того, можно выполнить развертывание в [эмуляторе HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) или создать [пакет приложения](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) для загрузки неопубликованных приложений.

5. Когда сборка завершится, в проводнике перейдите к расположению, где сохранена сборка, и двойным щелчком откройте файл решения в Visual Studio.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Проводник Windows с выбранным файлом решения Visual Studio":::

    > [!NOTE]
    > Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по **[установке средств](../../install-the-tools.md)** .

6. Настройте Visual Studio для устройства HoloLens. Для этого выберите конфигурацию **Master** (Ведущий) или **Release** (Выпуск), архитектуру **ARM64** и целевой объект **Device** (Устройство).

    > [!TIP]
    > Если выполняется развертывание в HoloLens (первое поколение), выберите архитектуру **x86**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Среда Visual Studio, настроенная для развертывания в HoloLens 2":::

    > [!NOTE]
    > В HoloLens обычно выполняется сборка для архитектуры ARM. Однако в Unity 2019.3 существует <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>известная проблема</strong></a>, которая вызывает ошибки при выборе ARM в качестве архитектуры сборки в Visual Studio. Рекомендуемое решение — выполните сборку для ARM64. Если такой вариант неприемлем, выберите **Edit > Project Settings > Player > Other Settings** (Изменить > Параметры проекта > Проигрыватель > Другие параметры) и отключите **графические задания**.

    > [!NOTE]
    > Если выбранное устройство не отображается как целевой объект, может потребоваться изменить загружаемый проект для решения Visual Studio из проекта IL2CPP на UWP. Для этого в обозревателе решений щелкните правой кнопкой мыши имя проекта (YourProjectName), в нашем примере это "Universal Windows", и выберите **Set as StartUp Project** (Назначить запускаемым проектом).

7. Подключите HoloLens к локальному компьютеру и выполните одно из следующих действий:
- Чтобы скомпилировать приложение, развернуть его в HoloLens и автоматически запустить без отладчика Visual Studio, выберите в строке меню **Debug** > **Start Without Debugging** (Отладка > Начать без отладки).

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Выбор варианта Start Without Debugging (Начать без отладки) в меню Visual Studio":::

- Чтобы выполнить сборку и развертывание приложения в HoloLens, не запуская его автоматически, выберите в строке меню **Build > Deploy Solution** (Сборка > Развернуть решение).

    > [!NOTE]
    >В приложении можно заметить профилировщик диагностики, который можно включать или выключать с помощью голосовой команды **Toggle Diagnostics** (Переключить диагностику). В процессе разработки рекомендуется отображать профилировщик основную часть времени. Это позволит определить, повлияют ли изменения приложения на производительность. Например, приложения HoloLens должны [непрерывно выполняться с частотой 60 кадров/с](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Поздравляем!

Вы развернули свое первое приложение HoloLens. Перемещаясь, вы увидите, как пространственная сетка сопоставления покрывает поверхности, воспринятые HoloLens. Кроме того, вы увидите на руках и пальцах индикаторы для отслеживания рук и счетчик частоты кадров для отслеживания производительности приложения. Эти функции — лишь немногие из новых базовых компонентов, входящих в состав MRTK. В следующих учебниках вы добавите содержимое в сцену, чтобы исследовать возможности HoloLens и MRTK.

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Настройка профилей MRTK](mr-learning-base-03.md)
