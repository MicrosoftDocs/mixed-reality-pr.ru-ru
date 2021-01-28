---
title: Настройка профилей MRTK
description: Из этого курса вы узнаете, как настроить профили Mixed Reality Toolkit (MRTK) для приложений смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание пространственного положения
ms.localizationpriority: high
ms.openlocfilehash: 9b0c914bd1f518d53abdd681b3a5f6959c9a6211
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579355"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="f333c-104">3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="f333c-104">3. Configuring the MRTK profiles</span></span>

<span data-ttu-id="f333c-105">Из этого руководства вы узнаете, как настраивать профили МRТК.</span><span class="sxs-lookup"><span data-stu-id="f333c-105">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="f333c-106"><a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">Профили MRTK</a> — это дерево вложенных профилей, которые включают сведения конфигурации для инициализации систем и функций MRTK.</span><span class="sxs-lookup"><span data-stu-id="f333c-106">The <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="f333c-107">Профиль верхнего уровня (профиль конфигурации) содержит вложенные профили для всех основных базовых систем.</span><span class="sxs-lookup"><span data-stu-id="f333c-107">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="f333c-108">Каждый вложенный профиль отвечает за настройку поведения соответствующей системы.</span><span class="sxs-lookup"><span data-stu-id="f333c-108">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="f333c-109">В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки.</span><span class="sxs-lookup"><span data-stu-id="f333c-109">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="f333c-110">Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.</span><span class="sxs-lookup"><span data-stu-id="f333c-110">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="f333c-111">Как вы узнали при развертывании своего проекта на HoloLens 2 при работе с [предыдущим руководством](mr-learning-base-02.md#congratulations), сетка <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">отслеживания пространственного положения</a> — это набор сеток, представляющих геометрию среды.</span><span class="sxs-lookup"><span data-stu-id="f333c-111">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="f333c-112">На начальных этапах разработки она помогает в работе, но обычно ее визуализацию отключают, чтобы она не отвлекала внимание и не снижала производительность.</span><span class="sxs-lookup"><span data-stu-id="f333c-112">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="f333c-113">Задачи</span><span class="sxs-lookup"><span data-stu-id="f333c-113">Objectives</span></span>

* <span data-ttu-id="f333c-114">Узнать,как настраивать профили MRTK.</span><span class="sxs-lookup"><span data-stu-id="f333c-114">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="f333c-115">Скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="f333c-115">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="f333c-116">Изменить параметр отображения отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="f333c-116">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="f333c-117">Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="f333c-117">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="f333c-118">Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="f333c-118">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="f333c-119">Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-119">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="f333c-120">Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-120">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="f333c-121">Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-121">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="f333c-122">Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-122">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="f333c-123">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="f333c-123">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="f333c-124">Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="f333c-124">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="f333c-125">Существует несколько вложенных уровней профилей.</span><span class="sxs-lookup"><span data-stu-id="f333c-125">There are several nested layers of profiles.</span></span> <span data-ttu-id="f333c-126">Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="f333c-126">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="f333c-127">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="f333c-127">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="f333c-128">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="f333c-128">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="f333c-129">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f333c-129">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="f333c-130">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и убедитесь, что для профиля конфигурации **MixedRealityToolkit** задано значение **DefaultXRSDKConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="f333c-130">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="f333c-132">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="f333c-132">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="f333c-134">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="f333c-134">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="f333c-136">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="f333c-136">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="f333c-138">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="f333c-138">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="f333c-139">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="f333c-139">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="f333c-140">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-140">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="f333c-141">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="f333c-141">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="f333c-143">Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="f333c-143">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="f333c-144">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="f333c-145">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="f333c-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="f333c-147">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="f333c-147">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="f333c-149">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="f333c-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="f333c-151">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="f333c-152">На вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель пространственной сетки Windows Mixed Reality для пакета SDK смешанной реальности), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="f333c-152">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="f333c-154">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="f333c-154">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="f333c-156">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="f333c-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="f333c-158">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="f333c-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="f333c-159">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="f333c-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="f333c-161">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="f333c-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="f333c-162">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="f333c-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="f333c-163">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="f333c-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="f333c-164">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f333c-164">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="f333c-165">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f333c-165">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="f333c-166">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="f333c-166">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="f333c-167">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="f333c-167">Congratulations</span></span>

<span data-ttu-id="f333c-168">В этом руководстве показано, как клонировать и настраивать профили MRTK и их параметры.</span><span class="sxs-lookup"><span data-stu-id="f333c-168">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f333c-169">Следующее руководство: 4. Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="f333c-169">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
