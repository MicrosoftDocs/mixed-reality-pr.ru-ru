---
title: Начало работы с Пространственными привязками Azure
description: Пройдите этот курс и узнайте, как использовать Пространственные привязки Azure для привязки объектов в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: ab216fc89c7161e4b3e7ee6fd9bcf9022b83c7fa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "103574960"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Начало работы с Пространственными привязками Azure

В этом руководстве показано, как запускать и завершать сеанс Пространственных привязок Azure, а также как создавать, отправлять и скачивать Пространственные привязки Azure на одном устройстве.

## <a name="objectives"></a>Задачи

* Изучите основы разработки Пространственных привязок Azure для HoloLens 2
* Узнайте, как создавать пространственные привязки и получать их из Azure.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md) (исключая раздел [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2)), в том числе следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.
2. [Переключение платформы сборки.](mr-learning-base-02.md#switching-the-build-platform)
3. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Импорт набора средств для Смешанной реальности (MRTK).](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Настройка проекта Unity.](mr-learning-base-02.md#configuring-the-unity-project)
6. [Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвоение ей понятного имени, например *AzureSpatialAnchors.*

Затем выполните инструкции из раздела [Изменение параметра отображения отслеживания пространственного положения](mr-learning-base-03.md#changing-the-spatial-awareness-display-option):

1. Измените **профиль конфигурации MRTK** на **DefaultHoloLens2ConfigurationProfile**.
1. Измените **параметры отображения сетки отслеживания пространственного положения** на **Occlusion** (Загораживание).

## <a name="installing-inbuilt-unity-packages"></a>Установка встроенных пакетов Unity

В меню Unity выберите **Window** > **Package Manager** (Окно > Диспетчер пакетов), чтобы открыть окно диспетчера пакетов, а затем щелкните **AR Foundation** и нажмите кнопку **Install** (Установить) для установки пакета.

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Пакет AR Foundation необходимо установить, так как он требуется для пакета SDK Пространственных привязок Azure, который вы будете импортировать при работе со следующим разделом.

## <a name="importing-the-tutorial-assets"></a>Импорт активов для руководства

Добавьте пакет SDK AzurespatialAnchors 2.7.1 в свой проект Unity с помощью этого [учебника](https://docs.microsoft.com/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).

Скачайте и **импортируйте** следующие пользовательские пакеты Unity **в указанном здесь порядке**:


* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage);
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage)

Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> Если вы видите предупреждение CS0618 о том, что параметр WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) устарел, его можно игнорировать.

> [!TIP]
> Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно иерархии, чтобы добавить их в сцену:

* **ButtonParent;**
* **DebugWindow;**
* **Instructions;**
* **ParentAnchor.**

![Unity с выбранными добавленными заготовками](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Если вы считаете, что большие значки в сцене (например, большие значки "Т" в рамках в нашем примере) отвлекают внимание, их можно спрятать. Для этого <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">переведите манипуляторы</a> в отключенное положение, как показано на рисунке выше.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Настройка кнопок для управления сценой

В этом разделе показано, как добавить в сцену скрипты, чтобы создать серию событий кнопок для демонстрации базовых приемов работы, а также поведения локальных привязок и Пространственных привязок Azure в приложении.

В окне иерархии разверните объект **ButtonParent** и выберите первый дочерний объект с именем **StartAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StartAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.

![Unity с настроенным событием OnClick для кнопки StartAzureSession](images/mr-learning-asa/asa-02-section5-step1-1.png)

В окне иерархии выберите следующую кнопку с именем **StopAzureSession**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **StopAzureSession ()** , чтобы задать эту функцию как действие, выполняемое при активации события.

![Unity с настроенным событием OnClick для кнопки StopAzureSession](images/mr-learning-asa/asa-02-section5-step1-2.png)

В окне иерархии выберите следующую кнопку с именем **CreateAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **CreateAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.
* В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции CreateAzureAnchor ().

![Unity с настроенным событием OnClick для кнопки CreateAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-3.png)

В окне иерархии выберите следующую кнопку с именем **RemoveLocalAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **RemoveLocalAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.
* В поле **None (Game Object)** (Отсутствует (игровой объект)) укажите объект **ParentAnchor**, чтобы сделать его аргументом функции RemoveLocalAnchor ().

![Unity с настроенным событием OnClick для кнопки RemoveLocalAnchor](images/mr-learning-asa/asa-02-section5-step1-4.png)

В окне иерархии выберите следующую кнопку с именем **FindAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **FindAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.

![Unity с настроенным событием OnClick для кнопки FindAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-5.png)

В окне иерархии выберите следующую кнопку с именем **DeleteAzureAnchor**. Затем в окне инспектора настройте событие **On Click ()** компонента **Button Config Helper (Script)** (Вспомогательная конфигурация кнопки — скрипт) следующим образом.

* В поле **None (Object)** (Отсутствует (объект)) укажите объект **ParentAnchor**.
* В раскрывающемся списке **No Function** (Функция отсутствует) выберите **AnchorModuleScript** > **DeleteAzureAnchor ()** , чтобы задать эту функцию как действие, выполняемое при активации события.

![Unity с настроенным событием OnClick для кнопки DeleteAzureAnchor](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Подключение сцены к ресурсу Azure

В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора найдите компонент **Spatial Anchor Manager (Script)** (Диспетчер пространственных привязок — скрипт). Укажите в разделе **Credentials** (Учетные данные) данные учетной записи Пространственных привязок Azure, созданной при работе с разделом [предварительных требований](mr-learning-asa-01.md#prerequisites) для этой серии руководств.

* В поле **Spatial Anchors Account ID** (Идентификатор учетной записи пространственных привязок) вставьте **идентификатор учетной записи** Пространственных привязок Azure.
* В поле **Spatial Anchors Account Key** (Ключ учетной записи пространственных привязок) вставьте первичный или вторичный **ключ доступа** учетной записи Пространственных привязок Azure.
* В поле **Spatial Anchors Account Domain** (Домен учетной записи пространственных привязок) укажите **домен учетной записи** Пространственных привязок Azure.

![Unity с настроенным диспетчером пространственных привязок](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Изучение базового поведения Пространственных привязок Azure

Пространственные привязки Azure не могут работать в Unity. Поэтому для проверки функциональных возможностей этой службы вам нужно создать проект и развернуть приложение на устройстве.

> [!TIP]
> Сведения о том, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Запустив приложение на устройстве, выполните инструкции, отображаемые на панели с инструкциями из руководства по Пространственным привязкам Azure.

1. Переместите куб в другое расположение.
1. Запустите сеанс Azure.
1. Создайте привязку Azure (она создается в расположении, где находится куб).
1. Завершите сеанс Azure.
1. Удалите локальную привязку (позволяет пользователю перемещать куб).
1. Переместите куб в другое место.
1. Запустите сеанс Azure.
1. Выполните поиск привязки Azure (размещение куба в расположении, которое мы настроили на шаге 3).
1. Удалите привязку Azure.
1. Завершите сеанс Azure.

![Unity с выбранным объектом Instructions](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Пространственные привязки Azure используют Интернет для сохранения и загрузки данных привязки. Поэтому обеспечьте подключение устройства к Интернету.

## <a name="anchoring-an-experience"></a>Привязка к взаимодействию

В предыдущих разделах вы изучили базовые принципы Пространственных привязок Azure. С помощью куба мы представили и визуализировали родительский объект игры с прикрепленной привязкой. Из этого раздела вы узнаете, как привязать взаимодействие целиком, разместив его в дочернем элементе объекта ParentAnchor.

В окне иерархии выберите объект **ParentAnchor**. Затем в окне инспектора настройте компонент **Transform** (Преобразование).

* Измените значение **Scale X** (Масштаб Х) на 1.1.
* Измените значение **Scale Z** (Масштаб Z) на 1.1.

![Unity с выбранным объектом ParentAnchor, для которого выполнено позиционирование и масштабирование](images/mr-learning-asa/asa-02-section8-step1-1.png)

В окне проекта перейдите к папке **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Активы > MRTK.Tutorials.GettingStarted > Заготовки > Rover), а затем щелкните и перетащите заготовку **RoverExplorer_Complete** в окно иерархии, чтобы добавить ее в сцену.

![Unity с выбранной добавленной заготовкой RoverExplorer_Complete](images/mr-learning-asa/asa-02-section8-step1-2.png)

Выбрав добавленный объект RoverModule_Complete в окне иерархии, перетащите его в объект **ParentAnchor**, чтобы сделать его дочерним объектом объекта ParentAnchor.

![Unity с объектом RoverExplorer_Complete, настроенным как дочерний объект ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

Если сейчас вы перестроите проект и развернете приложение на устройстве, вы сможете перемещать все средства взаимодействия с Rover Explorer, передвигая куб измененного размера.

> [!TIP]
> Есть разные виды взаимодействия с пользователем для изменения положения, в том числе: перемещение объекта (например, куба в этом учебнике), включение ограничивающего элемента вокруг средств взаимодействия нажатием кнопки, применение манипуляторов положения и вращения и другие.

## <a name="congratulations"></a>Поздравляем!

В рамках этого руководства вы изучили базовые принципы Пространственных привязок Azure. В этом руководстве показано, как использовать разные кнопки для запуска и завершения сеанса Пространственных привязок Azure, а также создания, отправки и скачивания Пространственных привязок Azure на одном устройстве.

В следующем руководстве показано, как сохранить идентификаторы привязок Azure на устройстве HoloLens 2, чтобы их можно было извлечь даже после перезапуска приложения, и как передавать идентификаторы привязок между несколькими устройствами для пространственного выравнивания.

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Сохранение, получение и совместное использование пространственных привязок Azure](mr-learning-asa-03.md)
