---
title: Создание первого приложения для HoloLens в Unreal
description: Сведения о том, как правильно настроить проект Unreal с объектами сцены и взаимодействиями ввода для разработки в среде смешанной реальности для HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, редактор Unreal, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, перенос, обновление
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421433"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="0884c-104">Создание первого приложения для HoloLens в Unreal</span><span class="sxs-lookup"><span data-stu-id="0884c-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="0884c-105">С помощью этого руководства вы создадите и запустите свое первое приложение смешанной реальности для HoloLens в Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="0884c-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="0884c-106">Как это заведено, вы создадите простое приложение Hello World, а именно такое, которое отображает куб на экране.</span><span class="sxs-lookup"><span data-stu-id="0884c-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="0884c-107">Чтобы сделать его более наглядным, вы также создадите первый жест для поворота куба и выхода из приложения.</span><span class="sxs-lookup"><span data-stu-id="0884c-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="0884c-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="0884c-108">Objectives</span></span>

* <span data-ttu-id="0884c-109">Создание проекта HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0884c-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="0884c-110">Активация нужных подключаемых модулей.</span><span class="sxs-lookup"><span data-stu-id="0884c-110">Enable the correct plugins</span></span>
* <span data-ttu-id="0884c-111">Создание актива данных ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="0884c-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="0884c-112">Настройка возможностей ввода с помощью жестов.</span><span class="sxs-lookup"><span data-stu-id="0884c-112">Set up gesture inputs</span></span>
* <span data-ttu-id="0884c-113">Создание базового уровня.</span><span class="sxs-lookup"><span data-stu-id="0884c-113">Build a basic level</span></span>
* <span data-ttu-id="0884c-114">Реализация жеста сжатия.</span><span class="sxs-lookup"><span data-stu-id="0884c-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="0884c-115">Создание нового проекта</span><span class="sxs-lookup"><span data-stu-id="0884c-115">Creating a new project</span></span>

<span data-ttu-id="0884c-116">Первое, что вам понадобится для работы — это проект.</span><span class="sxs-lookup"><span data-stu-id="0884c-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="0884c-117">Если вы только начинаете разработку на Unreal, [скачайте вспомогательные файлы](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) из Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="0884c-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="0884c-118">Запуск Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="0884c-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="0884c-119">В разделе **New Project Categories** (Категории для нового проекта) выберите **Games** (Игры) и щелкните **Next** (Далее):</span><span class="sxs-lookup"><span data-stu-id="0884c-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Открытое окно "Недавние проекты" с выделенным элементом "Games" (Игры)](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="0884c-121">Выберите шаблон **Blank** (Пустой) и щелкните **Next** (Далее):</span><span class="sxs-lookup"><span data-stu-id="0884c-121">Select the **Blank** template and click **Next**:</span></span>

![Окно обозревателя проектов Unreal с выделенным шаблоном Blank](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="0884c-123">В разделе **Project Settings** (Параметры проекта) установите значения **C++, Scalable 3D or 2D, Mobile/Tablet** (C++, масштабируемый трехмерный или двухмерный, мобильное устройство или планшет) и **No Starter Content** (Без начального содержимого), затем выберите расположение для сохранения и щелкните **Create Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="0884c-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="0884c-124">Вам нужно выбрать C++ вместо проекта схемы, чтобы позднее добавить подключаемый модуль OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0884c-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="0884c-125">В этом кратком руководстве используется подключаемый модуль OpenXR, по умолчанию входящий в состав Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="0884c-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="0884c-126">Но мы рекомендуем скачать и использовать официальный подключаемый модуль OpenXR корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="0884c-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="0884c-127">Для этого необходимо использовать проект C++.</span><span class="sxs-lookup"><span data-stu-id="0884c-127">That requires the project to be a C++ project.</span></span>

![Окно параметров проекта, где выделены поля для выбора проекта, производительности, целевой платформы и начального содержимого](images/unreal-quickstart-img-03.png)

<span data-ttu-id="0884c-129">Новый проект должен автоматически открыться в редакторе Unreal, и тогда можно перейти к следующему этапу.</span><span class="sxs-lookup"><span data-stu-id="0884c-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="0884c-130">Включение необходимых подключаемых модулей</span><span class="sxs-lookup"><span data-stu-id="0884c-130">Enabling required plugins</span></span>

<span data-ttu-id="0884c-131">Вам потребуется активировать два подключаемых модуля, прежде чем вы сможете добавлять объекты в сцену.</span><span class="sxs-lookup"><span data-stu-id="0884c-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="0884c-132">Выберите **Edit > Plugins** (Правка > Подключаемые модули) и выберите вариант **Augmented Reality** (Дополненная реальность) в списке встроенных категорий.</span><span class="sxs-lookup"><span data-stu-id="0884c-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="0884c-133">Прокрутите список до пункта **HoloLens** и установите флажок **Enabled** (Включено).</span><span class="sxs-lookup"><span data-stu-id="0884c-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Окно подключаемых модулей, где открыт раздел дополненной реальности и выделен элемент HoloLens](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="0884c-135">Введите **OpenXR** в поле поиска, расположенном в правом верхнем углу, затем включите подключаемые модули **OpenXR** и **OpenXRMsftHandInteraction**:</span><span class="sxs-lookup"><span data-stu-id="0884c-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Окно подключаемых модулей, где включен OpenXR](images/unreal-quickstart-img-05.jpg)

![Окно подключаемых модулей, где включено взаимодействие с руками Open XR Msft](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="0884c-138">Перезапустите редактор</span><span class="sxs-lookup"><span data-stu-id="0884c-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="0884c-139">В этом руководстве используется OpenXR, но два установленных ранее подключаемых модуля в настоящее время не предоставляют полный набор возможностей для разработки решений для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0884c-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="0884c-140">Подключаемый модуль HandInteraction обеспечит поддержку для жеста "сжатия", который вы примените далее, но для более сложного взаимодействия потребуется [скачать подключаемый модуль OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="0884c-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="0884c-141">Завершив настройку подключаемых модулей, переходите к созданию содержимого.</span><span class="sxs-lookup"><span data-stu-id="0884c-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="0884c-142">Создание уровня</span><span class="sxs-lookup"><span data-stu-id="0884c-142">Creating a level</span></span>

<span data-ttu-id="0884c-143">Следующая задача — создать игровую обстановку с начальной точкой и кубом, задающим начало отсчета и масштаб.</span><span class="sxs-lookup"><span data-stu-id="0884c-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="0884c-144">Выберите **File > New Level** (Файл > Создать уровень), а затем **Empty Level** (Пустой уровень).</span><span class="sxs-lookup"><span data-stu-id="0884c-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="0884c-145">В окне просмотра должна отображаться пустая сцена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0884c-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="0884c-146">На вкладке **Modes** (Режимы) выберите **Basic** (Основные) и перетащите в сцену элемент **PlayerStart**.</span><span class="sxs-lookup"><span data-stu-id="0884c-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="0884c-147">На вкладке **Details** (Сведения) установите для параметра **Location** (Расположение) значения **X = 0, Y = 0** и **Z = 0**, чтобы размещать пользователя в центре сцены при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="0884c-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Сцена редактора Unreal, где добавлены расположение и начальная позиция игрока](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="0884c-149">С вкладки **Basic** (Основные) перетащите в сцену элемент **Cube** (Куб).</span><span class="sxs-lookup"><span data-stu-id="0884c-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="0884c-150">Задайте для параметра **Location** (Расположение) этого куба значения **X = 50, Y = 0** и **Z = 0**, чтобы при запуске размещать куб на расстоянии 50 см от игрока.</span><span class="sxs-lookup"><span data-stu-id="0884c-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="0884c-151">Измените параметр **Scale** (Масштаб) для этого куба на значение **X = 0,2, Y = 0,2** и **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="0884c-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="0884c-152">Куб не будет виден, пока в сцену не добавлен источник света. Это и будет нашей последней задачей перед тем, как протестировать сцену.</span><span class="sxs-lookup"><span data-stu-id="0884c-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="0884c-153">На панели **Modes** (Режимы) перейдите на вкладку **Lights** (Освещение) и перетащите с нее в сцену элемент **Directional Light** (Направленное освещение),</span><span class="sxs-lookup"><span data-stu-id="0884c-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="0884c-154">разместив его над элементом **PlayerStart** так, чтобы он был виден.</span><span class="sxs-lookup"><span data-stu-id="0884c-154">Position the light above **PlayerStart** so you can see it</span></span>

![Сцена редактора Unreal, где добавлены куб и источник направленного освещения](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="0884c-156">Выберите элементы **File > Save Current** (Файл > Сохранить текущий), присвойте уровню имя **Main** (Главный) и щелкните **Save** (Сохранить).</span><span class="sxs-lookup"><span data-stu-id="0884c-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="0884c-157">Сцена готова. Чтобы увидеть куб в действии, нажмите кнопку **Play** (Воспроизвести) на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="0884c-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="0884c-158">Когда будете готовы действовать дальше, нажмите клавишу ESC, чтобы остановить приложение.</span><span class="sxs-lookup"><span data-stu-id="0884c-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Сцена в режиме воспроизведения, на которой в середине экрана размещен куб](images/unreal-quickstart-img-09.png)

<span data-ttu-id="0884c-160">Итак, настройка сцены завершена, и мы можем подготовить ее к простым взаимодействиям в режиме дополненной реальности (AR).</span><span class="sxs-lookup"><span data-stu-id="0884c-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="0884c-161">Сначала вам нужно создать сеанс AR и добавить схемы, чтобы обеспечить взаимодействие с руками.</span><span class="sxs-lookup"><span data-stu-id="0884c-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="0884c-162">Добавление актива для сеанса</span><span class="sxs-lookup"><span data-stu-id="0884c-162">Adding a session asset</span></span>

<span data-ttu-id="0884c-163">Сеансы дополненной реальности в Unreal не возникают сами по себе.</span><span class="sxs-lookup"><span data-stu-id="0884c-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="0884c-164">Для работы с сеансом требуется ресурс данных ARSessionConfig, который мы сейчас и добавим:</span><span class="sxs-lookup"><span data-stu-id="0884c-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="0884c-165">В **обозревателе содержимого** выберите **Add New > Miscellaneous > Data Asset** (Добавить > Прочее > Актив данных) и перейдите в корень папки Content.</span><span class="sxs-lookup"><span data-stu-id="0884c-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="0884c-166">Выберите **ARSessionConfig**, щелкните **Select** (Выбрать) и присвойте активу имя **ARSessionConfig**:</span><span class="sxs-lookup"><span data-stu-id="0884c-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Открытое окно выбора класса для актива данных, где выделен актив конфигурации сеанса дополненной реальности](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="0884c-168">Дважды щелкните **ARSessionConfig**, чтобы открыть этот актив, а затем **сохраните** его со значениями по умолчанию. Это действие вернет вас в основное окно:</span><span class="sxs-lookup"><span data-stu-id="0884c-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Окно сведений об активе конфигурации для сеанса дополненной реальности](images/unreal-quickstart-img-11.png)

<span data-ttu-id="0884c-170">Следующий шаг — настроить сеанс дополненной реальности таким образом, чтобы он запускался при загрузке уровня и останавливался при его завершении.</span><span class="sxs-lookup"><span data-stu-id="0884c-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="0884c-171">К счастью, для этого в Unreal есть специальная схема **Level Blueprint** (Схема уровня), которая работает как глобальный граф событий, относящихся к уровню.</span><span class="sxs-lookup"><span data-stu-id="0884c-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="0884c-172">Если подключить ресурс ARSessionConfig на схеме Level Blueprint (Схема уровня), сеанс дополненной реальности будет гарантированно стартовать в момент начала игры.</span><span class="sxs-lookup"><span data-stu-id="0884c-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="0884c-173">На панели инструментов редактора выберите **Blueprints > Open Level Blueprint** (Схемы > Открыть схему уровня):</span><span class="sxs-lookup"><span data-stu-id="0884c-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Открытое меню Blueprints (Схемы), где выделен параметр Open Level Blueprint (Открыть схему уровня)](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="0884c-175">Перетащите узел выполнения (значок с направленной вправо стрелкой) из узла **Event BeginPlay** и отпустите его.</span><span class="sxs-lookup"><span data-stu-id="0884c-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="0884c-176">Найдите узел **Start AR Session** (Запуск сеанса дополненной реальности) и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="0884c-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="0884c-177">В разделе **Session Config** (Параметры сеанса) щелкните стрелку раскрывающегося списка **Select Asset** (Выбор актива) и выберите актив **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="0884c-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Граф схемы, на котором начало воспроизведения события подключено к функции запуска сеанса дополненной реальности](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="0884c-179">Щелкните правой кнопкой мыши в EventGraph и создайте новый узел **Event EndPlay** (Завершение воспроизведения события).</span><span class="sxs-lookup"><span data-stu-id="0884c-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="0884c-180">Перетащите закрепление выполнения и отпустите его, а затем введите **Stop AR Session** (Завершить сеанс дополненной реальности) для поиска и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="0884c-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="0884c-181">Нажмите кнопку **Compile** (Компилировать), а затем **Save** (Сохранить). Это действие вернет вас в главное окно.</span><span class="sxs-lookup"><span data-stu-id="0884c-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0884c-182">Если сеанс дополненной реальности не останавливается по окончании уровня, некоторые функции могут не работать после перезапуска приложения при потоковой передаче данных на гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="0884c-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Конечный узел события, присоединенный к функции "stop ar session" (Прекратить выполнение сеанса)](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="0884c-184">Настройка входных данных</span><span class="sxs-lookup"><span data-stu-id="0884c-184">Setting up inputs</span></span>

1. <span data-ttu-id="0884c-185">Щелкните **Edit > Project Settings** (Правка > Параметры проекта) и найдите раздел **Engine > Input** (Движок > Вход).</span><span class="sxs-lookup"><span data-stu-id="0884c-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="0884c-186">Щелкните значок **+** рядом с элементом **Action Mappings** (Сопоставления действий) и создайте действия **RightPinch** и **LeftPinch**:</span><span class="sxs-lookup"><span data-stu-id="0884c-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Привязка входных параметров, где выделены сопоставления действий сжатия слева и справа](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="0884c-188">Сопоставьте действия **RightPinch** и **LeftPinch** с соответствующими действиями **взаимодействия с руками OpenXR Msft**:</span><span class="sxs-lookup"><span data-stu-id="0884c-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Область сопоставления действий, где выделены параметры взаимодействия с руками OpenXR Msft](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="0884c-190">Настройка жестов</span><span class="sxs-lookup"><span data-stu-id="0884c-190">Setting up gestures</span></span>

<span data-ttu-id="0884c-191">Теперь, когда мы настроили возможности ввода, мы можем приступить к интересной части. А именно, к добавлению жестов.</span><span class="sxs-lookup"><span data-stu-id="0884c-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="0884c-192">Мы настроим вращение куба при сжатии справа и выход из приложения при сжатии слева.</span><span class="sxs-lookup"><span data-stu-id="0884c-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="0884c-193">Откройте схему уровня (**Level Blueprint**) и добавьте действия **InputAction RightPinch** и **InputAction LeftPinch**.</span><span class="sxs-lookup"><span data-stu-id="0884c-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="0884c-194">Подключите действие сжатия справа к действию **AddActorLocalRotation**, у которого целевым объектом является созданный ранее **куб**, а параметр **Delta Rotation** имеет значения **X = 0, Y = 0** и **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="0884c-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="0884c-195">Теперь куб будет вращаться на 20 градусов при каждой активации сжатия</span><span class="sxs-lookup"><span data-stu-id="0884c-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="0884c-196">Подключите событие сжатия слева к действию **Quit Game** (Выход из игры).</span><span class="sxs-lookup"><span data-stu-id="0884c-196">Connect the left pinch event to **Quit Game**</span></span>

![Открытое окно схемы уровня, где настроены действия ввода для событий сжатия справа и слева](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="0884c-198">В параметрах **Transform** (Преобразование) для этого куба задайте параметру **Mobility** (Мобильность) значение **Movable** (Перемещаемый), чтобы объект мог динамически перемещаться:</span><span class="sxs-lookup"><span data-stu-id="0884c-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Параметры преобразования, где выделено свойство перемещаемости](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="0884c-200">Теперь вы готовы к развертыванию и тестированию приложения!</span><span class="sxs-lookup"><span data-stu-id="0884c-200">At this point, you're ready to deploy and test the application!</span></span>