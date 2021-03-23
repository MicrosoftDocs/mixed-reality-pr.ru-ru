---
title: 2. Инициализация проекта и первое приложение
description: Часть 2 (из 6) серии руководств по созданию приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля Mixed Reality UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, UX Tools, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583902"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="b12d0-104">2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="b12d0-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="b12d0-105">С помощью инструкций из первого руководства вы создадите проект Unreal, включите подключаемый модуль HoloLens, создадите уровень, зададите для него освещение и добавите шахматные фигуры.</span><span class="sxs-lookup"><span data-stu-id="b12d0-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="b12d0-106">Для этого мы воспользуемся готовыми ресурсами для трехмерных объектов и материалов. Создавать модели с нуля не придется.</span><span class="sxs-lookup"><span data-stu-id="b12d0-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="b12d0-107">Когда вы выполните все описанное в руководстве, у вас будет шаблон для работы со смешанной реальностью.</span><span class="sxs-lookup"><span data-stu-id="b12d0-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b12d0-108">Убедитесь, что у вас есть все необходимое из списка на странице [Начало работы](/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="b12d0-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="b12d0-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="b12d0-109">Objectives</span></span>

* <span data-ttu-id="b12d0-110">Настройка проекта Unreal с целью разработки для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b12d0-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="b12d0-111">Импорт ресурсов и настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="b12d0-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="b12d0-112">Создание субъектов и событий уровня скрипта.</span><span class="sxs-lookup"><span data-stu-id="b12d0-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="b12d0-113">Создание проекта Unreal.</span><span class="sxs-lookup"><span data-stu-id="b12d0-113">Creating a new Unreal project</span></span>

<span data-ttu-id="b12d0-114">Первое, что вам понадобится для работы — это проект.</span><span class="sxs-lookup"><span data-stu-id="b12d0-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="b12d0-115">Если вы только начинаете разработку на Unreal, [скачайте вспомогательные файлы](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) из Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="b12d0-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="b12d0-116">Запуск Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="b12d0-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="b12d0-117">В разделе **New Project Categories** (Категории для нового проекта) выберите **Games** (Игры) и щелкните **Next** (Далее).</span><span class="sxs-lookup"><span data-stu-id="b12d0-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Выбор шаблона проекта Games (Игры)](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="b12d0-119">Выберите пустой (**Blank**) шаблон и нажмите кнопку **Next** (Далее).</span><span class="sxs-lookup"><span data-stu-id="b12d0-119">Select the **Blank** Template and click **Next**.</span></span> 

![Выбор пустого шаблона](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="b12d0-121">Выберите **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Масштабируемый трехмерный или двухмерный, мобильное устройство или планшет) и **No Starter Content** (Без начального содержимого) в разделе **Project Settings** (Параметры проекта), а затем выберите расположение сохранения и нажмите **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="b12d0-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="b12d0-122">Выберите проект C++, а не проект шаблона, чтобы создать подключаемый модуль средств UX, который вы настроите позже (в разделе 4).</span><span class="sxs-lookup"><span data-stu-id="b12d0-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Начальные параметры проекта](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="b12d0-124">Проект должен автоматически открыться в редакторе Unreal, и тогда можно перейти к следующему этапу.</span><span class="sxs-lookup"><span data-stu-id="b12d0-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="b12d0-125">Включение необходимых подключаемых модулей</span><span class="sxs-lookup"><span data-stu-id="b12d0-125">Enabling required plugins</span></span>

<span data-ttu-id="b12d0-126">Вам потребуется активировать два подключаемых модуля, прежде чем вы сможете добавлять объекты в сцену.</span><span class="sxs-lookup"><span data-stu-id="b12d0-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="b12d0-127">Выберите **Edit > Plugins** (Правка > Подключаемые модули) и выберите вариант **Augmented Reality** (Дополненная реальность) в списке встроенных категорий.</span><span class="sxs-lookup"><span data-stu-id="b12d0-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="b12d0-128">Прокрутите список до пункта **HoloLens** и установите флажок **Enabled** (Включено).</span><span class="sxs-lookup"><span data-stu-id="b12d0-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Включение подключаемых модулей HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="b12d0-130">Выберите вариант **Virtual Reality** (Виртуальная реальность) в списке встроенных категорий.</span><span class="sxs-lookup"><span data-stu-id="b12d0-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="b12d0-131">Прокрутите список до пункта **Microsoft Windows Mixed Reality**, установите для него флажок **Enabled** (Включено) и перезапустите редактор.</span><span class="sxs-lookup"><span data-stu-id="b12d0-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Включение подключаемого модуля Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="b12d0-133">Оба подключаемых модуля обязательны при разработке для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b12d0-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="b12d0-134">Теперь, после включения подключаемых модулей, у вас есть пустой уровень, который можно чем-нибудь заполнить.</span><span class="sxs-lookup"><span data-stu-id="b12d0-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="b12d0-135">Создание уровня</span><span class="sxs-lookup"><span data-stu-id="b12d0-135">Creating a level</span></span>
<span data-ttu-id="b12d0-136">Следующая задача — создать игровую обстановку с начальной точкой и кубом, задающим начало отсчета и масштаб.</span><span class="sxs-lookup"><span data-stu-id="b12d0-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="b12d0-137">Выберите **File > New Level** (Файл > Создать уровень), а затем **Empty Level** (Пустой уровень).</span><span class="sxs-lookup"><span data-stu-id="b12d0-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="b12d0-138">В окне просмотра должна отображаться пустая сцена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b12d0-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="b12d0-139">На вкладке **Modes** (Режимы) выберите **Basic** (Основные) и перетащите в сцену элемент **PlayerStart**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="b12d0-140">Установите для параметра **Location** (Расположение) значения **X = 0**, **Y = 0** и **Z = 0** на вкладке **Details** (Сведения), чтобы расположить пользователя в центре сцены при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="b12d0-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Окно просмотра с элементом PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="b12d0-142">Перетащите в сцену элемент **Cube** (Куб) с вкладки **Basic** (Основные).</span><span class="sxs-lookup"><span data-stu-id="b12d0-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="b12d0-143">Установите для параметра **Location** (Расположение) значения **X = 50**, **Y = 0** и **Z = 0**,</span><span class="sxs-lookup"><span data-stu-id="b12d0-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="b12d0-144">чтобы в начале игры куб располагался в 50 см от игрока.</span><span class="sxs-lookup"><span data-stu-id="b12d0-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="b12d0-145">Установите для параметра **Scale** (Масштаб) значения **X = 0,2**, **Y = 0,2** и **Z = 0,2**, чтобы уменьшить размеры куба.</span><span class="sxs-lookup"><span data-stu-id="b12d0-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="b12d0-146">Куб не будет виден, пока в сцену не добавлен источник света. Это и будет нашей последней задачей перед тем, как протестировать сцену.</span><span class="sxs-lookup"><span data-stu-id="b12d0-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="b12d0-147">Перейдите на вкладку **Lights** (Свет) на панели **Modes** (Режимы) и перетащите в сцену элемент **Directional Light** (Направленный свет),</span><span class="sxs-lookup"><span data-stu-id="b12d0-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="b12d0-148">разместив его над элементом **PlayerStart**, чтобы он был виден.</span><span class="sxs-lookup"><span data-stu-id="b12d0-148">Position the light above **PlayerStart** so you can see it.</span></span>

![Окно просмотра после добавления света](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="b12d0-150">Выберите элементы **File > Save Current** (Файл > Сохранить текущий), присвойте уровню имя **Main** (Главный) и нажмите кнопку **Save** (Сохранить).</span><span class="sxs-lookup"><span data-stu-id="b12d0-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="b12d0-151">Сцена готова. Чтобы увидеть куб в действии, нажмите кнопку **Play** (Воспроизвести) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="b12d0-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="b12d0-152">Когда будете готовы действовать дальше, нажмите клавишу **ESC**, чтобы остановить приложение.</span><span class="sxs-lookup"><span data-stu-id="b12d0-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Куб в окне просмотра](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="b12d0-154">Теперь в настроенную сцену можно добавить шахматную доску и фигуру, чтобы получить готовую пространственную среду приложения.</span><span class="sxs-lookup"><span data-stu-id="b12d0-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="b12d0-155">Импорт ресурсов</span><span class="sxs-lookup"><span data-stu-id="b12d0-155">Importing assets</span></span>
<span data-ttu-id="b12d0-156">Пустая сцена выглядит скучновато, но мы сейчас это исправим, импортировав в проект готовые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="b12d0-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="b12d0-157">Скачайте файл с папкой активов с сайта [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) и распакуйте его с помощью [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="b12d0-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="b12d0-158">В обозревателе содержимого (**Content Browser**) выберите элементы **Add New > New Folder** (Добавить > Папка) и присвойте новой папке имя **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="b12d0-159">Дважды щелкните только что созданную папку. В нее мы будем импортировать трехмерные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="b12d0-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![Отображение и скрытие панели источников](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="b12d0-161">В обозревателе содержимого (**Content Browser**) нажмите кнопку **Import** (Импорт), выберите все элементы из папки с распакованными ресурсами и нажмите кнопку **Open** (Открыть).</span><span class="sxs-lookup"><span data-stu-id="b12d0-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="b12d0-162">Ресурсы содержат сетки трехмерных объектов для шахматной доски и фигур в формате FBX, а также файлы текстурных карт в формате TGA, на основе которых мы создадим материалы для доски и фигур.</span><span class="sxs-lookup"><span data-stu-id="b12d0-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="b12d0-163">Когда откроется всплывающее окно FBX Import Options (Параметры импорта FBX-файлов), разверните раздел **Material** (Материал) и смените значение параметра **Material Import Method** (Метод импорта материала) на **Do Not Create Material** (Не создавать материал).</span><span class="sxs-lookup"><span data-stu-id="b12d0-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="b12d0-164">Нажмите кнопку **Import All** (Импортировать все).</span><span class="sxs-lookup"><span data-stu-id="b12d0-164">Select **Import All**.</span></span>

![Параметры импорта FBX-файлов](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="b12d0-166">Это все, что нужно для импорта ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b12d0-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="b12d0-167">Следующая группа задач — создать элементарные блоки, из которых будет строиться приложение, с использованием схем.</span><span class="sxs-lookup"><span data-stu-id="b12d0-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="b12d0-168">Добавление схем</span><span class="sxs-lookup"><span data-stu-id="b12d0-168">Adding blueprints</span></span>

1. <span data-ttu-id="b12d0-169">В обозревателе содержимого (**Content Browser**) выберите элементы **Add New > New Folder** (Добавить > Папка) и присвойте новой папке имя **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="b12d0-170">[Схемы](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) — это специальные ресурсы, позволяющие создавать новые типы субъектов и события уровня скрипта с помощью интерфейса на основе узлов.</span><span class="sxs-lookup"><span data-stu-id="b12d0-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="b12d0-171">Дважды щелкните папку **Blueprints**, затем щелкните правой кнопкой мыши и выберите **Blueprint Class** (Класс схемы).</span><span class="sxs-lookup"><span data-stu-id="b12d0-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="b12d0-172">Выберите **Actor** (Субъект) и присвойте новой схеме имя **Board**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![Выбор родительского класса для новой схемы](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="b12d0-174">Новая схема **Board** появится в папке **Blueprints**, как можно видеть на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="b12d0-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Новая схема для шахматной доски](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="b12d0-176">Теперь можно добавлять материалы к созданным объектам.</span><span class="sxs-lookup"><span data-stu-id="b12d0-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="b12d0-177">Работа с материалами</span><span class="sxs-lookup"><span data-stu-id="b12d0-177">Working with materials</span></span>
<span data-ttu-id="b12d0-178">По умолчанию созданные объекты имеют серый цвет, а хотелось бы чего-то повеселее.</span><span class="sxs-lookup"><span data-stu-id="b12d0-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="b12d0-179">Последняя группа задач в этом руководстве — добавление материалов и сеток к объектам.</span><span class="sxs-lookup"><span data-stu-id="b12d0-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="b12d0-180">Дважды щелкните схему **Board**, чтобы открыть редактор схем.</span><span class="sxs-lookup"><span data-stu-id="b12d0-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="b12d0-181">На панели **Components** (Компоненты) выберите элементы **Add Component > Scene** (Добавить компонент > Сцена) и присвойте новой сцене имя **Root**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="b12d0-182">Обратите внимание, что **Root** отобразится как дочерний объект элемента **DefaultSceneRoot** (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="b12d0-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Замена корня в схеме](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="b12d0-184">Перетащите элемент **Root** на **DefaultSceneRoot**, чтобы заменить последний и избавиться от шара в окне просмотра.</span><span class="sxs-lookup"><span data-stu-id="b12d0-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Замена главного элемента](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="b12d0-186">На панели **Components** (Компоненты) выберите элементы **Add Component > Static Mesh** (Добавить компонент > Статическая сетка) и присвойте новой сетке имя **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="b12d0-187">Она отобразится как дочерний объект элемента **Root**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-187">It will appear as a child object under **Root**.</span></span>

![Добавление статической сетки](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="b12d0-189">Выберите элемент **SM_Board**, прокрутите панель **Details** (Сведения) до раздела **Static Mesh** (Статическая сетка) и выберите в раскрывающемся списке вариант **ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Сетка шахматной доски в окне просмотра](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="b12d0-191">На той же панели **Details** (Сведения) разверните раздел **Materials** (Материалы) и выберите в раскрывающемся списке элементы **Create New Asset > Material** (Создать ресурс > Материал).</span><span class="sxs-lookup"><span data-stu-id="b12d0-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="b12d0-192">Присвойте новому материалу имя **M_ChessBoard** и сохраните его в папке **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Создание нового материала](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="b12d0-194">Дважды щелкните материал **M_ChessBoard**, чтобы открыть редактор материалов.</span><span class="sxs-lookup"><span data-stu-id="b12d0-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Открытие редактора материалов](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="b12d0-196">В окне Material Editor (Редактор материалов) щелкните правой кнопкой мыши и найдите узел **Texture Sample** (Пример текстуры).</span><span class="sxs-lookup"><span data-stu-id="b12d0-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="b12d0-197">На панели **Details** (Сведения) разверните раздел **Material Expression Texture Base** (Основа текстуры для выражения материала) и установите для параметра **Texture** (Текстура) значение **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="b12d0-198">Перетащите маркер вывода **RGB** на маркер Base Color (Основной цвет) элемента **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Установка основного цвета](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="b12d0-200">Повторите предыдущий шаг еще четыре раза и создайте четыре новых узла **Texture Sample** (Пример текстуры), настроив их следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b12d0-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="b12d0-201">Установите для параметра **Texture** (Текстура) значение **ChessBoard_AO** и свяжите закрепление **RGB** с закреплением **Ambient Occlusion** (Рассеянное затенение).</span><span class="sxs-lookup"><span data-stu-id="b12d0-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="b12d0-202">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Metal** и свяжите закрепление **RGB** с закреплением **Metallic** (Металлик).</span><span class="sxs-lookup"><span data-stu-id="b12d0-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="b12d0-203">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Normal** и свяжите закрепление **RGB** с закреплением **Normal** (Обычный).</span><span class="sxs-lookup"><span data-stu-id="b12d0-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="b12d0-204">Установите для параметра **Texture** (Текстура) значение **ChessBoard_Rough** и свяжите закрепление **RGB** с закреплением **Roughness** (Шероховатость).</span><span class="sxs-lookup"><span data-stu-id="b12d0-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="b12d0-205">Нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-205">Click **Save**.</span></span> 

![Подключение оставшихся текстур](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="b12d0-207">Прежде чем продолжать, убедитесь, что материал настроен так, как показано на снимке экрана выше.</span><span class="sxs-lookup"><span data-stu-id="b12d0-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="b12d0-208">Заполнение сцены</span><span class="sxs-lookup"><span data-stu-id="b12d0-208">Populating the scene</span></span>
<span data-ttu-id="b12d0-209">Если вы вернетесь к схеме **Board**, то увидите, что к ней уже применен созданный только что материал.</span><span class="sxs-lookup"><span data-stu-id="b12d0-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="b12d0-210">Осталось только настроить сцену.</span><span class="sxs-lookup"><span data-stu-id="b12d0-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="b12d0-211">Сначала изменим свойства, как описано ниже, чтобы придать доске разумные размеры и расположить ее под правильным углом в сцене:</span><span class="sxs-lookup"><span data-stu-id="b12d0-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="b12d0-212">Установите для параметра **Scale** (Масштаб) значение **(0,05, 0,05, 0,05)** , а для параметра **Z Rotation** (Поворот по оси Z) — значение **90**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="b12d0-213">Нажмите кнопку **Compile** (Компилировать) в верхней панели инструментов, а затем кнопку **Save** (Сохранить), после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="b12d0-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Шахматная доска после применения материалов](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="b12d0-215">Щелкните правой кнопкой мыши **Cube > Edit > Delete** (Куб > Изменить > Удалить) и перетащите элемент **Board** из обозревателя контента (**Content Browser**) в окно просмотра.</span><span class="sxs-lookup"><span data-stu-id="b12d0-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="b12d0-216">Установите для параметра **Location** (Расположение) значения **X = 80**, **Y = 0** и **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="b12d0-217">Нажмите кнопку **Play** (Воспроизвести), чтобы просмотреть созданную доску на уровне.</span><span class="sxs-lookup"><span data-stu-id="b12d0-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="b12d0-218">Нажмите клавишу **ESC**, чтобы вернуться в редактор.</span><span class="sxs-lookup"><span data-stu-id="b12d0-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="b12d0-219">Теперь по тому же алгоритму, что и с доской, создадим шахматную фигуру:</span><span class="sxs-lookup"><span data-stu-id="b12d0-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="b12d0-220">Дважды щелкните папку **Blueprints**, щелкните правой кнопкой мыши и выберите элемент **Blueprint Class** (Класс схемы), а затем — элемент **Actor** (Субъект).</span><span class="sxs-lookup"><span data-stu-id="b12d0-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="b12d0-221">Присвойте субъекту имя **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="b12d0-222">Дважды щелкните элемент **WhiteKing**, чтобы открыть его в редакторе схем, выберите элементы **Add Component > Scene** (Добавить компонент > Сцена) и присвойте сцене имя **Root**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="b12d0-223">Замените элемент **DefaultSceneRoot**, перетащив на него элемент **Root**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="b12d0-224">Выберите **Add Component > Static Mesh** (Добавить компонент > Статическая сетка) и присвойте компоненту имя **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="b12d0-225">На панели Details (Сведения) установите для параметра **Static Mesh** (Статическая сетка) значение **Chess_King**, а для параметра **Material** (Материал) — значение **M_ChessWhite**, соответствующее новому материалу.</span><span class="sxs-lookup"><span data-stu-id="b12d0-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="b12d0-226">Откройте материал **M_ChessWhite** в редакторе материалов и подключите узлы **Texture Sample** (Пример текстуры) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b12d0-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="b12d0-227">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Albedo** и свяжите закрепление **RGB** с закреплением **Base Color** (Основной цвет).</span><span class="sxs-lookup"><span data-stu-id="b12d0-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="b12d0-228">Установите для параметра **Texture** (Текстура) значение **ChessWhite_AO** и свяжите закрепление **RGB** с закреплением **Ambient Occlusion** (Рассеянное затенение).</span><span class="sxs-lookup"><span data-stu-id="b12d0-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="b12d0-229">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Metal** и свяжите закрепление **RGB** с закреплением **Metallic** (Металлик).</span><span class="sxs-lookup"><span data-stu-id="b12d0-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="b12d0-230">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Normal** и свяжите закрепление **RGB** с закреплением **Normal** (Обычный).</span><span class="sxs-lookup"><span data-stu-id="b12d0-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="b12d0-231">Установите для параметра **Texture** (Текстура) значение **ChessWhite_Rough** и свяжите закрепление **RGB** с закреплением **Roughness** (Шероховатость).</span><span class="sxs-lookup"><span data-stu-id="b12d0-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="b12d0-232">Нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-232">Click **Save**.</span></span> 

<span data-ttu-id="b12d0-233">Прежде чем продолжать, убедитесь, что материал **M_ChessKing** настроен, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="b12d0-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Создание материала для шахматного короля](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="b12d0-235">Все почти готово, осталось лишь добавить новую шахматную фигуру в сцену:</span><span class="sxs-lookup"><span data-stu-id="b12d0-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="b12d0-236">Откройте схему **WhiteKing** и установите для параметра **Scale** (Масштаб) значение **(0,05, 0,05, 0,05)** , а для параметра **Z Rotation** (Поворот по оси Z) — значение **90**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="b12d0-237">Скомпилируйте схему и сохраните ее, а затем вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="b12d0-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="b12d0-238">Перетащите элемент **WhiteKing** в окно просмотра, переключитесь на панель **World Outliner** (Структура мира) и перетащите элемент **WhiteKing** на элемент **Board** в качестве дочернего объекта.</span><span class="sxs-lookup"><span data-stu-id="b12d0-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Структура мира](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="b12d0-240">На панели **Details** (Сведения) в разделе **Transform** (Преобразование) установите для параметра **Location** (Расположение) элемента **WhiteKing** значения **X = -26**, **Y = 4** и **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="b12d0-241">Готово!</span><span class="sxs-lookup"><span data-stu-id="b12d0-241">That's a wrap!</span></span> <span data-ttu-id="b12d0-242">Нажмите кнопку **Play** (Воспроизвести), чтобы увидеть уровень с объектами в действии, а когда захотите выполнить выход, нажмите клавишу **ESC**.</span><span class="sxs-lookup"><span data-stu-id="b12d0-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="b12d0-243">Вы ознакомились со множеством возможностей при создании простого проекта. Теперь вы можете перейти к следующей части серии — настройке проекта для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b12d0-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="b12d0-244">Следующий раздел: 3. Настройка проекта для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b12d0-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)