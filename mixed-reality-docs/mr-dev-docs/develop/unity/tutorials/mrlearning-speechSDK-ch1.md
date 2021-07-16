---
title: Руководства по использованию службы "Речь" в Azure, часть 1. Интеграция и использование средств распознавания и транскрибирования речи
description: В рамках этого курса вы узнаете, как реализовать пакет SDK службы "Речь" в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, распознавание речи, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656630"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Интеграция и использование средств распознавания и транскрибирования речи

## <a name="overview"></a>Обзор

В этой серии руководств вы создадите приложение смешанной реальности и на его примере изучите использование служб распознавания речи Azure с HoloLens 2. Изучив эту серию руководств, вы сможете применять микрофон устройства для транскрибирования речи в текст в режиме реального времени, переводить эту речь на другие языки и применять распознавание намерений для анализа голосовых команд с применением искусственного интеллекта.

## <a name="objectives"></a>Задачи

* Сведения об интеграции службы речи Azure с приложением HoloLens 2.
* Сведения об использовании функции распознавания речи для транскрибирования текста

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли руководства из серии, посвященной [началу работы](mr-learning-base-01.md), мы рекомендуем начать знакомство именно с этой серии.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020/2019 LTS и модулем поддержки сборки универсальной платформы Windows

> [!Important]
> В этой серии руководств учитывается поддержка Unity 2020 LTS (в настоящее время 2020.3.x), если вы используете Open XR или подключаемый модуль Windows XR, а также Unity 2019 LTS (в настоящее время 2019.4.x), если вы используете устаревшую версию WSA или подключаемый модуль Windows XR. Это заменяет все требования к версии Unity, указанные выше.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.
2. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)
3. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Импорт набора средств для смешанной реальности (MRTK) и настройка проекта Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и присвоение ей понятного имени, например *AzureSpeechServices*.

Затем следуйте инструкциям по [изменению параметра отображения для отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), чтобы указать профиль конфигурации MRTK **DefaultHoloLens2ConfigurationProfile** для сцены и значение **Occlusion** (Загораживание) для параметра отображения сетки отслеживания пространственного положения.

## <a name="configuring-the-speech-commands-start-behavior"></a>Настройка поведения для начала речевых команд

Поскольку для распознавания и транскрибирования речи вы будете применять пакет SDK "Речь", вам нужно настроить речевые команды MRTK так, чтобы они не мешали работе пакета SDK "Речь". Чтобы добиться этого, измените поведение начала речевых команд с Auto Start (Автозапуск) на Manual Start (Запуск вручную).

Выделив объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), выберите в окне Inspector (Инспектор) вкладку **Input** (Ввод), клонируйте профили **DefaultHoloLens2InputSystemProfile** и **DefaultMixedRealitySpeechCommandsProfile**, а затем измените для речевых команд параметр **Start Behavior** (Поведение начала) на **Manual Start** (Старт вручную):

![учебник по смешанной реальности — распознавание речи 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a>Настройка функциональных возможностей

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player** >  **Publishing Settings** (Проигрыватель > Параметры публикации).

![учебник по смешанной реальности — распознавание речи 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

В окне **Publishing Settings** (Параметры публикации) прокрутите содержимое вниз до раздела **Capabilities** (Возможности) и убедитесь, что здесь включены возможности **InternetClient** (Интернет-клиент), **Microphone** (Микрофон) и **SpatialPerception** (Пространственное восприятие), которые были включены при создании проекта в начале работы с этим учебником. Теперь включите возможности **InternetClientServer** (Сервер интернет-клиента) и **PrivateNetworkClientServer** (Сервер клиента частной сети):

![учебник по смешанной реальности — распознавание речи 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (последняя версия);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-04.md#importing-the-tutorial-assets).

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![учебник по смешанной реальности — распознавание речи 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

Необходимо настроить проект Unity для публикации подключаемых модулей обработки речи Azure для ARM64. Для этого в окне проекта перейдите в раздел **Assets** (Ресурсы)  >  **SpeechSDK**  >  **Plugins** (Подключаемые модули)  >  **WSA**  >  **ARM64** и выберите подключаемый модуль **Microsoft.CognitiveServices.Speech.core**.

![учебник по смешанной реальности — распознавание речи 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

С выбранным подключаемым модулем **Microsoft.CognitiveServices.Speech.core** в окне инспектора включите **WSA Player**, затем в разделе **Platform settings** (Параметры платформы) выберите **UWP** для SDK, **ARM64** для ЦП и нажмите кнопку Apply, чтобы применить эти параметры к подключаемому модулю.

![учебник по смешанной реальности — распознавание речи 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

Повторите эти действия для каждого из оставшихся подключаемых модулей:

* **Microsoft.CognitiveServices.Speech.extension.audio.sys**
* **Microsoft.CognitiveServices.Speech.extension.kws**
* **Microsoft.CognitiveServices.Speech.extension.lu**
* **Microsoft.CognitiveServices.Speech.extension.silk_codec**

## <a name="preparing-the-scene"></a>Подготовка сцены

В этом разделе вы подготовите сцену, добавив заготовку для руководства, и настроите компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) для управления сценой.

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** и перетащите заготовку **Lunarcom** в окно Hierarchy (Иерархия), чтобы добавить ее в сцену:

![учебник по смешанной реальности — распознавание речи 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

В окне Hierarchy (Иерархия) сохраните выделение объекта **Lunarcom**, а в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) к объекту Lunarcom.

![учебник по смешанной реальности — распознавание речи 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Компонент Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Сохраняя выделение объекта **Lunarcom**, разверните его для просмотра списка дочерних объектов, затем перетащите объект **Terminal** (Терминал) в поле **Terminal** (Терминал) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт):

![учебник по смешанной реальности — распознавание речи 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Сохраняя выделение объекта **Lunarcom**, разверните объект Terminal (Терминал) для просмотра списка его дочерних объектов, затем перетащите объект **ConnectionLight** (Индикатор подключения) в поле **ConnectionLight** (Индикатор подключения) объекта Lunarcom Controller (Script) (Контроллер Lunarcom — скрипт), а объект **OutputText** (Выходной текст) — в поле **Output Text** (Выходной текст):

![учебник по смешанной реальности — распознавание речи 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Сохраняя выделение объекта **Lunarcom**, разверните объект Buttons (Кнопки), чтобы открыть список его дочерних объектов, а затем в окне "Инспектор" разверните список **Buttons** (Кнопки), установите для его параметра **Size** (Размер) значение 3 и перетащите объекты **MicButton**, **SatelliteButton** и **RocketButton** в поля **Элемент** с номерами 0, 1 и 2, соответственно:

![учебник по смешанной реальности — распознавание речи 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Подключение проекта Unity к ресурсу Azure

Чтобы использовать службу речи Azure, потребуется создать ресурс Azure и получить ключ API для службы "Речь". Выполните инструкции [по применению бесплатной версии службы "Речь"](/azure/cognitive-services/speech-service/get-started) и выясните регион (расположение) вашей службы и значение ключа API (это может быть Key1 или Key2).

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) найдите в компоненте **Lunarcom Controller (Script)** (Контроллер Lunarcom — скрипт) раздел **Speech SDK Credentials** (Учетные данные пакета SDK) и настройте его, как описано ниже.

* В поле **Speech Service API Key** (Ключ API службы "Речь") введите значение ключа API (Key1 или Key2).
* В поле **Speech Service Region** (Регион службы "Речь") введите значение региона (расположения) службы, переведя все буквы в нижний регистр и удалив пробелы.

![учебник по смешанной реальности — распознавание речи 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Использование функции распознавания речи для транскрибирования речи

В окне Hierarchy (Иерархия) выберите объект **Lunarcom**, а затем в окне Inspector (Инспектор) с помощью кнопки **Add Component** (Добавить компонент) добавьте компонент **Lunarcom Speech Recognizer (Script)** (Распознаватель речи Lunarcom — скрипт) к объекту Lunarcom.

![учебник по смешанной реальности — распознавание речи 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Компонент Lunarcom Speech Recognizer (Script) (Распознаватель речи Lunarcom — скрипт) не входит в состав MRTK. Он был предоставлен с активами для этого руководства.

Войдя в игровой режим, вы сможете проверить распознавание речи. Для начала нажмите кнопку микрофона.

![учебник по смешанной реальности — распознавание речи 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Теперь, если на компьютере подключен микрофон, любой сказанный вами текст будет выводиться на панели терминала:

![учебник по смешанной реальности — распознавание речи 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> Этому приложению требуется подключение к Azure, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.

## <a name="congratulations"></a>Поздравляем!

Вы успешно реализовали функцию распознавания речи на платформе Azure. Запустите приложение на устройстве и убедитесь, что все работает правильно.

В следующем учебнике вы узнаете, как выполнять команды с помощью распознавания речи Azure.

> [!div class="nextstepaction"]
> [Следующий учебник: 2. Выполнение команд с помощью распознавания речи Azure](mrlearning-speechSDK-ch2.md)
