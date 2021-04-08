---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097825"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Клонирование профиля конфигурация по умолчанию

> [!NOTE]
> Профиль конфигурации является профилем верхнего уровня. Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и убедитесь, что для профиля конфигурации **MixedRealityToolkit** задано значение **DefaultXRSDKConfigurationProfile**.

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKConfigurationProfile**:

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.

> [!TIP]
> Не забывайте сохранять работу при работе с руководством.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Включение системы отслеживания пространственного положения

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель пространственной сетки Windows Mixed Reality для пакета SDK смешанной реальности), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Изменение видимости сетки отслеживания пространственного положения

В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать. Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.

Вы только что узнали, как изменить параметр в профиле MRTK. Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию. Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию. Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Клонирование профиля конфигурация по умолчанию

> [!NOTE]
> Профиль конфигурации является профилем верхнего уровня. Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и убедитесь, что для профиля конфигурации **MixedRealityToolkit** задано значение **DefaultOpenXRConfigurationProfile**:

![Компонент Unity MixedRealityToolkit с выбранным профилем OpenXR по умолчанию](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки для профиля OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_OpenXRConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultOpenXRConfigurationProfile**:

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем OpenXR](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.

> [!TIP]
> Не забывайте сохранять работу при работе с руководством.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Включение системы отслеживания пространственного положения

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например GettingStarted_OpenXRSpatialAwarenessSystemProfile, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель пространственной сетки Windows Mixed Reality для пакета SDK смешанной реальности), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Изменение видимости сетки отслеживания пространственного положения

В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать. Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.

Вы только что узнали, как изменить параметр в профиле MRTK. Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию. Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию. Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).


# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1. Клонирование профиля конфигурация по умолчанию

> [!NOTE]
> Профиль конфигурации является профилем верхнего уровня. Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и измените профиль конфигурации **MixedRealityToolkit** на **DefaultHoloLens2ConfigurationProfile**.

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1.png)

Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](../images/mr-learning-base/base-03-section1-step1-2.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_HoloLens2ConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultHololens2ConfigurationProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](../images/mr-learning-base/base-03-section1-step1-3.png)

Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4.png)

В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.

> [!TIP]
> Не забывайте сохранять работу при работе с руководством.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Включение системы отслеживания пространственного положения

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения

На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessSystemProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2.png)

Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения

Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1.png)

В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2.png)

Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Изменение видимости сетки отслеживания пространственного положения

В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать. Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.

Вы только что узнали, как изменить параметр в профиле MRTK. Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию. Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию. Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).
