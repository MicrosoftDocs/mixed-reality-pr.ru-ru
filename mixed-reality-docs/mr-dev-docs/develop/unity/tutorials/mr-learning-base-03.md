---
title: Серия руководств по началу работы, часть 3 Настройка профилей MRTK
description: Из этого курса вы узнаете, как настроить профили Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 15fa4285fd6dd60aac9ba3869430649db5b40f91
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353262"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Настройка профилей MRTK

## <a name="overview"></a>Обзор

Из этого руководства вы узнаете, как настраивать профили МRТК.

<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">Профили MRTK</a> — это дерево вложенных профилей, которые включают сведения конфигурации для инициализации систем и функций MRTK. Профиль верхнего уровня (профиль конфигурации) содержит вложенные профили для всех основных базовых систем. Каждый вложенный профиль отвечает за настройку поведения соответствующей системы.

В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки. Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.

Как вы узнали при развертывании своего проекта на HoloLens 2 при работе с [предыдущим руководством](mr-learning-base-02.md#congratulations), сетка <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">отслеживания пространственного положения</a> — это набор сеток, представляющих геометрию среды. На начальных этапах разработки она помогает в работе, но обычно ее визуализацию отключают, чтобы она не отвлекала внимание и не снижала производительность.

## <a name="objectives"></a>Задачи

* Узнать,как настраивать профили MRTK.
* Скрыть сетку отслеживания пространственного положения.

## <a name="changing-the-spatial-awareness-display-option"></a>Изменить параметр отображения отслеживания пространственного положения.

Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.

1. Клонирование профиля конфигурация по умолчанию
2. Включение системы отслеживания пространственного положения
3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения
4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения
5. Изменение видимости сетки отслеживания пространственного положения

> [!NOTE]
> По умолчанию профили MRTK недоступны для редактирования. Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать. Существует несколько вложенных уровней профилей. Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.

### <a name="1-clone-the-default-configuration-profile"></a>1. Клонирование профиля конфигурация по умолчанию

> [!NOTE]
> Профиль конфигурации является профилем верхнего уровня. Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit** , перейдите в окно Inspector (Инспектор) и измените профиль конфигурации **MixedRealityToolkit** на **DefaultHoloLens2ConfigurationProfile**.

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-1.png)

Сохраняя выделение объекта **MixedRealityToolkit** , в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](images/mr-learning-base/base-03-section1-step1-2.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля** , например _GettingStarted_HoloLens2ConfigurationProfile_ , а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultHololens2ConfigurationProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](images/mr-learning-base/base-03-section1-step1-3.png)

Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-4.png)

В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.

> [!TIP]
> Не забывайте сохранять работу при работе с руководством.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Включение системы отслеживания пространственного положения

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit** , перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](images/mr-learning-base/base-03-section1-step3-1.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля** , например _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ , а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessSystemProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step3-2.png)

Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения

Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](images/mr-learning-base/base-03-section1-step4-1.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля** , например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ , а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](images/mr-learning-base/base-03-section1-step4-2.png)

Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Изменение видимости сетки отслеживания пространственного положения

В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать. Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.

Вы только что узнали, как изменить параметр в профиле MRTK. Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию. Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию. Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Поздравляем!

В этом руководстве показано, как клонировать и настраивать профили MRTK и их параметры.

> [!div class="nextstepaction"]
> [Следующее руководство: 4. Размещение объектов в сцене](mr-learning-base-04.md)
