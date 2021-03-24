---
title: Серия руководств по началу работы, часть 3 Настройка профилей MRTK
description: Из этого курса вы узнаете, как настроить профили Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание пространственного положения
ms.localizationpriority: high
ms.openlocfilehash: 0a8beb647516ebcb5bc07cb58d0193e8fe71e9fc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "101760020"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="01c79-105">3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="01c79-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="01c79-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="01c79-106">Overview</span></span>

<span data-ttu-id="01c79-107">Из этого руководства вы узнаете, как настраивать профили МRТК.</span><span class="sxs-lookup"><span data-stu-id="01c79-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="01c79-108"><a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">Профили MRTK</a> — это дерево вложенных профилей, которые включают сведения конфигурации для инициализации систем и функций MRTK.</span><span class="sxs-lookup"><span data-stu-id="01c79-108">The <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="01c79-109">Профиль верхнего уровня (профиль конфигурации) содержит вложенные профили для всех основных базовых систем.</span><span class="sxs-lookup"><span data-stu-id="01c79-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="01c79-110">Каждый вложенный профиль отвечает за настройку поведения соответствующей системы.</span><span class="sxs-lookup"><span data-stu-id="01c79-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="01c79-111">В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки.</span><span class="sxs-lookup"><span data-stu-id="01c79-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="01c79-112">Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.</span><span class="sxs-lookup"><span data-stu-id="01c79-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="01c79-113">Как вы узнали при развертывании своего проекта на HoloLens 2 при работе с [предыдущим руководством](mr-learning-base-02.md#congratulations), сетка <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">отслеживания пространственного положения</a> — это набор сеток, представляющих геометрию среды.</span><span class="sxs-lookup"><span data-stu-id="01c79-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="01c79-114">На начальных этапах разработки она помогает в работе, но обычно ее визуализацию отключают, чтобы она не отвлекала внимание и не снижала производительность.</span><span class="sxs-lookup"><span data-stu-id="01c79-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="01c79-115">Задачи</span><span class="sxs-lookup"><span data-stu-id="01c79-115">Objectives</span></span>

* <span data-ttu-id="01c79-116">Узнать,как настраивать профили MRTK.</span><span class="sxs-lookup"><span data-stu-id="01c79-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="01c79-117">Скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="01c79-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="01c79-118">Изменить параметр отображения отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="01c79-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="01c79-119">Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="01c79-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="01c79-120">Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="01c79-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="01c79-121">Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="01c79-122">Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="01c79-123">Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="01c79-124">Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="01c79-125">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="01c79-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="01c79-126">Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="01c79-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="01c79-127">Существует несколько вложенных уровней профилей.</span><span class="sxs-lookup"><span data-stu-id="01c79-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="01c79-128">Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="01c79-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="01c79-129">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="01c79-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="01c79-130">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="01c79-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="01c79-131">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="01c79-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="01c79-132">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и измените профиль конфигурации **MixedRealityToolkit** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="01c79-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранным профилем DefaultHoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="01c79-134">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="01c79-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с кнопкой копирования и настройки](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="01c79-136">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_HoloLens2ConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultHololens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="01c79-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля конфигурации](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="01c79-138">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="01c79-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем HoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="01c79-140">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="01c79-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="01c79-141">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="01c79-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="01c79-142">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="01c79-143">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="01c79-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Компонент MixedRealityToolkit в Unity с добавленной системой отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="01c79-145">Если вашим приложениям не нужно будет реагировать на среду или взаимодействовать с ней, для оптимальной производительности рекомендуется не включать отслеживание пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="01c79-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="01c79-146">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="01c79-147">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="01c79-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с выбранной вкладкой Spatial Awareness (Отслеживание пространственного положения)](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="01c79-149">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessSystemProfile**.</span><span class="sxs-lookup"><span data-stu-id="01c79-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования системного профиля отслеживания пространственного положения](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="01c79-151">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="01c79-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным новым пользовательским профилем MixedRealitySpatialAwarenessSystemProfile](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="01c79-153">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="01c79-154">Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="01c79-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Компонент MixedRealityToolkit в Unity с развернутым разделом наблюдателя виртуальной сетки Windows Mixed Reality](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="01c79-156">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="01c79-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Компонент MixedRealityToolkit в Unity со всплывающим окном клонирования профиля наблюдателя виртуальной сетки](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="01c79-158">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="01c79-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Компонент MixedRealityToolkit в Unity с примененным созданным пользовательским профилем MixedRealitySpatialAwarenessMeshObserverProfile](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="01c79-160">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="01c79-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="01c79-161">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="01c79-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Компонент MixedRealityToolkit в Unity с параметром отображения наблюдателя виртуальной сетки, для которого задано значение Occlusion (Загораживание)](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="01c79-163">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="01c79-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="01c79-164">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="01c79-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="01c79-165">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="01c79-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="01c79-166">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="01c79-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="01c79-167">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="01c79-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="01c79-168">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) на [портале документации по МRТК](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span><span class="sxs-lookup"><span data-stu-id="01c79-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

## <a name="congratulations"></a><span data-ttu-id="01c79-169">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="01c79-169">Congratulations</span></span>

<span data-ttu-id="01c79-170">В этом руководстве показано, как клонировать и настраивать профили MRTK и их параметры.</span><span class="sxs-lookup"><span data-stu-id="01c79-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01c79-171">Следующее руководство: 4. Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="01c79-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
