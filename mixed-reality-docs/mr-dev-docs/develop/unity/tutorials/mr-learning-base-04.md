---
title: Учебники по MRTK — 4. Размещение объектов в сцене
description: Из этого курса вы узнаете, как размещать объекты в сцене и как использовать Mixed Reality Toolkit (MRTK) для упорядочивания объектов в сетке.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, решатели, коллекция объектов сетки
ms.localizationpriority: high
ms.openlocfilehash: e09047e4f75697722f76301630c275f126b3cbda
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613258"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="f3287-105">4. Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="f3287-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="f3287-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="f3287-106">Overview</span></span>

<span data-ttu-id="f3287-107">В этом руководстве показано, как импортировать предоставляемые активы и размещать указанные объекты в сцене.</span><span class="sxs-lookup"><span data-stu-id="f3287-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="f3287-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="f3287-108">Objectives</span></span>

* <span data-ttu-id="f3287-109">Научиться размещать объекты в сцене.</span><span class="sxs-lookup"><span data-stu-id="f3287-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="f3287-110">Научиться использовать функцию коллекции объектов сетки в MRTK.</span><span class="sxs-lookup"><span data-stu-id="f3287-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f3287-111">Импорт активов для руководства</span><span class="sxs-lookup"><span data-stu-id="f3287-111">Importing the tutorial assets</span></span>

<span data-ttu-id="f3287-112">Скачайте и импортируйте следующий пользовательский пакет Unity:</span><span class="sxs-lookup"><span data-stu-id="f3287-112">Download and import the following Unity custom package:</span></span>

* <span data-ttu-id="f3287-113">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="f3287-113">[MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)</span></span>

<span data-ttu-id="f3287-114">Когда вы завершите импорт активов для руководства, окно проекта должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="f3287-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity с окнами Hierarchy (Иерархия), Scene (Сцена) и Project (Проект) после импорта ресурсов для руководства](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f3287-116">Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт набора средств для Смешанной реальности](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="f3287-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="f3287-117">Создание родительского объекта</span><span class="sxs-lookup"><span data-stu-id="f3287-117">Creating the parent object</span></span>

<span data-ttu-id="f3287-118">Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой), чтобы добавить в сцену пустой объект.</span><span class="sxs-lookup"><span data-stu-id="f3287-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Unity с пунктом Create Empty (Создать пустой) в контекстном меню](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f3287-120">Чтобы отобразить окна Scene (Сцена) и Game (Игра) рядом друг с другом, как на изображении ниже, перетащите окно Game (Игра) и поместите его справа от окна Scene (Сцена).</span><span class="sxs-lookup"><span data-stu-id="f3287-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="f3287-121">Дополнительные сведения см. на странице <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Настройка рабочего пространства</a> в документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="f3287-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="f3287-122">Щелкните правой кнопкой мыши созданный объект, выберите **Rename** (Переименовать) и измените имя на **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="f3287-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Unity с пунктом Rename (Переименовать) в контекстном меню](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="f3287-124">Выбрав объект RoverExplorer в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f3287-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f3287-125">**Position** (Положение): X = 0, Y = -0,6, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="f3287-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="f3287-126">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3287-127">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="f3287-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity с выбранным и размещенным объектом RoverExplorer](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="f3287-129">Камера представляет голову пользователя в исходном положении: X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="f3287-130">Обычно одна единица в Unity равна примерно одному метру в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="f3287-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="f3287-131">Но из этого правила могут быть исключения, например для дочерних объектов масштабированных объектов.</span><span class="sxs-lookup"><span data-stu-id="f3287-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="f3287-132">В приведенном выше сценарии для RoverExplorer задается положение на расстоянии 2 метра перед головой пользователя и 0,6 метра ниже нее.</span><span class="sxs-lookup"><span data-stu-id="f3287-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="f3287-133">Добавление заготовок для выполнения задач руководства</span><span class="sxs-lookup"><span data-stu-id="f3287-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="f3287-134">В окне Project (Проект) перейдите к папке **Assets (Активы)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Заготовки)** .</span><span class="sxs-lookup"><span data-stu-id="f3287-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Окно проекта Unity с выбранной папкой заготовок](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="f3287-136"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Заготовкой</a> называется предварительно настроенный игровой объект (GameObject), который хранится в качестве актива Unity и может повторно использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="f3287-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="f3287-137">В окне Project (Проект) щелкните и перетащите заготовку **Table** (Таблица) в объект **RoverExplorer**, чтобы сделать ее дочерним объектом RoverExplorer. Затем в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f3287-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f3287-138">**Position** (Положение): X = 0, Y = -0,005, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="f3287-139">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3287-140">**Scale** (Масштаб): X = 1,2, Y = 0,01, Z = 1,2.</span><span class="sxs-lookup"><span data-stu-id="f3287-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity с выбранной и размещенной добавленной заготовкой Table](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="f3287-142">Для отображения сцены, как на рисунке ниже, используйте <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Манипулятор сцены) справа в верхнем углу окна сцены, чтобы направить угол взгляда вдоль оси Z вперед. Затем дважды щелкните объект MixedRealityPlayspace, чтобы перевести на него фокус камеры, и при необходимости увеличьте масштаб.</span><span class="sxs-lookup"><span data-stu-id="f3287-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="f3287-143">В окне Project (Проект) щелкните и перетащите заготовку **RoverAssembly** в объект **RoverExplorer**, чтобы сделать ее дочерним объектом RoverExplorer. Затем в окне инспектора настройте компонент **Transform** (Преобразование) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f3287-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f3287-144">**Position** (Положение): X = -0,1, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3287-145">**Rotation** (Поворот): X = 0, Y = -135, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="f3287-146">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="f3287-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity с выбранной и размещенной добавленной заготовкой RoverAssembly](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="f3287-148">Упорядочение объектов в коллекции</span><span class="sxs-lookup"><span data-stu-id="f3287-148">Organizing objects in a collection</span></span>

<span data-ttu-id="f3287-149">В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **RoverExplorer** и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в качестве дочернего объекта RoverExplorer. Присвойте объекту имя **RoverParts** и настройте компонент **Transform** (Преобразование), следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f3287-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f3287-150">**Position** (Положение): X = 0, Y = 0,06, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="f3287-151">**Rotation** (Поворот): X = 0, Y = 90, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="f3287-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="f3287-152">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="f3287-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity выбранным и расположенным созданным объектом RoverParts](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="f3287-154">В окне Hierarchy (Иерархия) выберите все дочерние объекты RoverExplorer > RoverAssembly > RoverModel > **Parts** (Части). Щелкните их правой кнопкой мыши и выберите **Duplicate** (Дублировать), чтобы создать копию каждой части.</span><span class="sxs-lookup"><span data-stu-id="f3287-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity со всеми выбранными частями и пунктом Duplicate (Создать копию) в контекстном меню](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="f3287-156">Чтобы выбрать несколько смежных объектов, нажав и удерживая клавишу SHIFT, выберите первый и последний объект.</span><span class="sxs-lookup"><span data-stu-id="f3287-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="f3287-157">Оставив выбранными только что продублированные дочерние объекты Parts (Части), щелкните и перетащите их в объект **RoverParts**, чтобы сделать их дочерними объектами RoverParts.</span><span class="sxs-lookup"><span data-stu-id="f3287-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity с новыми копиями частей, являющихся дочерними объектами RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="f3287-159">Чтобы со сценой было проще работать, в окне Hierarchy (Иерархия) щелкните значок с изображением **глаза** слева от объекта. Для объекта **RoverAssembly** будет отключена **видимость сцены**.</span><span class="sxs-lookup"><span data-stu-id="f3287-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="f3287-160">Так вы скроете объект в окне сцены, не изменяя его внутриигровую видимость.</span><span class="sxs-lookup"><span data-stu-id="f3287-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity с отключенной видимостью сцены RoverAssembly](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="f3287-162">Дополнительные сведения об элементах управления видимостью и их применении для оптимизации представления сцены и рабочего процесса вы можете найти на странице <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Видимость сцены</a> в документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="f3287-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="f3287-163">В окне Hierarchy (Иерархия) очистите имена дочерних объектов RoverParts, изменив добавленную запись **(1)** на **_Part**:</span><span class="sxs-lookup"><span data-stu-id="f3287-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity с очищенным именем копий частей](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="f3287-165">В окне Hierarchy (Иерархия) выберите объект **RoverParts**. Затем в окне инспектора нажмите кнопку **Add Component** (Добавить компонент). Найдите и выберите компонент **GridObjectCollection**, чтобы добавить его в объект RoverParts:</span><span class="sxs-lookup"><span data-stu-id="f3287-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Unity с объектом RoverParts с поиском Grid Object Collection при добавлении компонента](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="f3287-167">Настройте значения компонента **GridObjectCollection** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f3287-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="f3287-168">**Sort Type** (Тип сортировки): Alphabetical (По алфавиту).</span><span class="sxs-lookup"><span data-stu-id="f3287-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="f3287-169">**Layout** (Макет): По горизонтали</span><span class="sxs-lookup"><span data-stu-id="f3287-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="f3287-170">**Cell Width** (Ширина ячейки): 0,25.</span><span class="sxs-lookup"><span data-stu-id="f3287-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="f3287-171">**Distance from parent** (Расстояние от родительского объекта): 0,38.</span><span class="sxs-lookup"><span data-stu-id="f3287-171">**Distance from parent**: 0.38</span></span>

![Unity с настроенным компонентом GridObjectCollection](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="f3287-173">Затем нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы обновить положение дочерних объектов RoverParts.</span><span class="sxs-lookup"><span data-stu-id="f3287-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity с примененным компонентом GridObjectCollection](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="f3287-175">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="f3287-175">Congratulations</span></span>

<span data-ttu-id="f3287-176">Из этого руководства вы узнали, как разместить объекты в сцене относительно пользователя и упорядочить объекты в коллекции с помощью функции коллекции объектов сетки MRTK.</span><span class="sxs-lookup"><span data-stu-id="f3287-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="f3287-177">Следующее руководство: 5. Создание динамического содержимого с помощью решателей</span><span class="sxs-lookup"><span data-stu-id="f3287-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)