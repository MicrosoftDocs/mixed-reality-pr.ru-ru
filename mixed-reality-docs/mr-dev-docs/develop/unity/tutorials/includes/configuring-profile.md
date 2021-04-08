---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097825"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8cddc-101">Подключаемый модуль Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="8cddc-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="8cddc-102">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8cddc-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="8cddc-103">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8cddc-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="8cddc-104">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8cddc-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="8cddc-105">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и убедитесь, что для профиля конфигурации **MixedRealityToolkit** задано значение **DefaultXRSDKConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="8cddc-107">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="8cddc-109">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="8cddc-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="8cddc-111">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="8cddc-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="8cddc-113">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="8cddc-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="8cddc-114">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="8cddc-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="8cddc-115">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="8cddc-116">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="8cddc-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="8cddc-118">Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="8cddc-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="8cddc-119">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="8cddc-120">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="8cddc-122">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="8cddc-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="8cddc-124">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8cddc-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="8cddc-126">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="8cddc-127">На вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель пространственной сетки Windows Mixed Reality для пакета SDK смешанной реальности), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="8cddc-129">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="8cddc-131">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="8cddc-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="8cddc-133">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="8cddc-134">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="8cddc-136">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="8cddc-137">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="8cddc-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="8cddc-138">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="8cddc-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="8cddc-139">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="8cddc-140">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="8cddc-141">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="8cddc-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8cddc-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8cddc-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="8cddc-143">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8cddc-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="8cddc-144">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8cddc-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="8cddc-145">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8cddc-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="8cddc-146">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и убедитесь, что для профиля конфигурации **MixedRealityToolkit** задано значение **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="8cddc-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Компонент Unity MixedRealityToolkit с выбранным профилем OpenXR по умолчанию](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="8cddc-148">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки для профиля OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="8cddc-150">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_OpenXRConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="8cddc-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="8cddc-152">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="8cddc-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем OpenXR](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="8cddc-154">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="8cddc-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="8cddc-155">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="8cddc-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="8cddc-156">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="8cddc-157">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="8cddc-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="8cddc-159">Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="8cddc-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="8cddc-160">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="8cddc-161">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="8cddc-163">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например GettingStarted_OpenXRSpatialAwarenessSystemProfile, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="8cddc-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="8cddc-165">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8cddc-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="8cddc-167">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="8cddc-168">На вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель пространственной сетки Windows Mixed Reality для пакета SDK смешанной реальности), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="8cddc-170">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="8cddc-172">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="8cddc-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="8cddc-174">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="8cddc-175">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="8cddc-177">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="8cddc-178">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="8cddc-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="8cddc-179">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="8cddc-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="8cddc-180">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="8cddc-181">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="8cddc-182">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="8cddc-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="8cddc-183">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="8cddc-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="8cddc-184">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8cddc-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="8cddc-185">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8cddc-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="8cddc-186">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8cddc-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="8cddc-187">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и измените профиль конфигурации **MixedRealityToolkit** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="8cddc-189">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="8cddc-191">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_HoloLens2ConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultHololens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="8cddc-193">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="8cddc-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="8cddc-195">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="8cddc-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="8cddc-196">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="8cddc-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="8cddc-197">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="8cddc-198">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="8cddc-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="8cddc-200">Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="8cddc-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="8cddc-201">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="8cddc-202">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="8cddc-204">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessSystemProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="8cddc-206">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="8cddc-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="8cddc-208">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="8cddc-209">Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="8cddc-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="8cddc-211">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="8cddc-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="8cddc-213">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="8cddc-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="8cddc-215">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="8cddc-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="8cddc-216">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="8cddc-218">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="8cddc-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="8cddc-219">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="8cddc-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="8cddc-220">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="8cddc-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="8cddc-221">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="8cddc-222">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8cddc-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="8cddc-223">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="8cddc-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
