---
title: Заметки о выпуске МРТК 2,6
description: Заметки о выпуске для МРТК версии 2,6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК,
ms.openlocfilehash: c172e5d071bba22626e9c35b2b4318f1ff779335
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562514"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a><span data-ttu-id="b9139-104">Заметки о выпуске Microsoft Mixed Reality Toolkit 2,6</span><span class="sxs-lookup"><span data-stu-id="b9139-104">Microsoft Mixed Reality Toolkit 2.6 Release Notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9139-105">Существует известная ошибка компилятора, влияющая на приложения, созданные для Microsoft HoloLens 2 с помощью ARM64.</span><span class="sxs-lookup"><span data-stu-id="b9139-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="b9139-106">Эта проблема устранена путем обновления Visual Studio 2019 до версии 16,8 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="b9139-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="b9139-107">Если не удается обновить Visual Studio, импортируйте `com.microsoft.mixedreality.toolkit.tools` пакет, чтобы применить обходной путь.</span><span class="sxs-lookup"><span data-stu-id="b9139-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-262"></a><span data-ttu-id="b9139-108">Новые возможности в 2.6.2</span><span class="sxs-lookup"><span data-stu-id="b9139-108">What's new in 2.6.2</span></span>

### <a name="corrects-parenting-of-the-spatial-mesh"></a><span data-ttu-id="b9139-109">Исправление родительского объекта пространственной сетки</span><span class="sxs-lookup"><span data-stu-id="b9139-109">Corrects parenting of the spatial mesh</span></span>

<span data-ttu-id="b9139-110">Устраняет [проблему](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) , при которой пространственные сети не были должным образом размещены после перемещения объекта плайспаце смешанной реальности (например, через телепортируйтесь).</span><span class="sxs-lookup"><span data-stu-id="b9139-110">Fixes the [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) where spatial meshes were not being properly located after the Mixed Reality Playspace object was moved (ex: via a teleport).</span></span>

## <a name="whats-new-in-261"></a><span data-ttu-id="b9139-111">Новые возможности в 2.6.1</span><span class="sxs-lookup"><span data-stu-id="b9139-111">What's new in 2.6.1</span></span>

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a><span data-ttu-id="b9139-112">Исправления Опенкср не выполняются в HoloLens 2/UWP</span><span class="sxs-lookup"><span data-stu-id="b9139-112">Fixes OpenXR not running on HoloLens 2 / UWP</span></span>

<span data-ttu-id="b9139-113">Устраняется регрессия, препятствующая выполнению поддержки Опенкср МРТК в UWP.</span><span class="sxs-lookup"><span data-stu-id="b9139-113">Fixes a regression that prevented MRTK's OpenXR support from running on UWP.</span></span>

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a><span data-ttu-id="b9139-114">Исправления Обжектманипулатор, не вращающие LEAP</span><span class="sxs-lookup"><span data-stu-id="b9139-114">Fixes Leap Motion ObjectManipulator not rotating</span></span>

<span data-ttu-id="b9139-115">Устраняет регрессию, в которой поворот движения от руки не учитывается сценарием Обжектманипулатор.</span><span class="sxs-lookup"><span data-stu-id="b9139-115">Fixes a regression where a Leap Motion hand's rotation was not taken into account by the ObjectManipulator script.</span></span>

### <a name="sample-scene-updates"></a><span data-ttu-id="b9139-116">Обновления образца сцены</span><span class="sxs-lookup"><span data-stu-id="b9139-116">Sample scene updates</span></span>

<span data-ttu-id="b9139-117">Обновляет образец сцены "сцена", чтобы правильно отразить состояние доставки подключаемого модуля Unity.</span><span class="sxs-lookup"><span data-stu-id="b9139-117">Updates the scene understanding sample scene to correctly reflect the shipped state of the Unity plugin.</span></span> <span data-ttu-id="b9139-118">Также обновляет пример, чтобы он больше не имел зависимости от импортируемого примера демонстрационной информации о поддержке пространственных объектов.</span><span class="sxs-lookup"><span data-stu-id="b9139-118">Also updates the sample to no longer have a dependency on the spatial awareness sample scene being imported.</span></span> <span data-ttu-id="b9139-119">Перед обновлением до 2.6.1 следует удалить импортированные и пространственные примеры, если они есть в проекте, чтобы избежать возможных конфликтов.</span><span class="sxs-lookup"><span data-stu-id="b9139-119">Before updating to 2.6.1 you should delete the imported scene understanding and spatial awareness samples if they are present in your project to avoid possible conflicts.</span></span> <span data-ttu-id="b9139-120">Если вы не удалили эти образцы и увидите конфликты, связанные с ними в консоли, удалите оба образца (или `Assets/Samples/Mixed Reality Toolkit Examples` папку) и повторите попытку импорта.</span><span class="sxs-lookup"><span data-stu-id="b9139-120">If you did not remove those samples and do see conflicts related to those in the console, please remove both samples (or the `Assets/Samples/Mixed Reality Toolkit Examples` folder) and then try importing again.</span></span>

<span data-ttu-id="b9139-121">Обновляет сцену примера диалогового окна, чтобы правильно описать текущие сценарии диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="b9139-121">Updates the dialog example scene to correctly describe the current dialog scenarios.</span></span>

## <a name="whats-new-in-260"></a><span data-ttu-id="b9139-122">Новые возможности в 2.6.0</span><span class="sxs-lookup"><span data-stu-id="b9139-122">What's new in 2.6.0</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a><span data-ttu-id="b9139-123">Добавление поддержки для Опенкср</span><span class="sxs-lookup"><span data-stu-id="b9139-123">Add support for OpenXR</span></span>

<span data-ttu-id="b9139-124">Добавлена первоначальная поддержка пакета предварительной версии Опенкср Unity и пакета Опенкср для смешанной реальности Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9139-124">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="b9139-125">Дополнительные сведения см. [на странице Приступая к работе с мртк/ксрсдк](../configuration/getting-started-with-mrtk-and-xrsdk.md), на [форуме Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)или в [документации Майкрософт](/windows/mixed-reality/develop/unity/openxr-getting-started) .</span><span class="sxs-lookup"><span data-stu-id="b9139-125">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9139-126">Опенкср в Unity поддерживается только в Unity 2020,2 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="b9139-126">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="b9139-127">В настоящее время он также поддерживает только сборки x64 и ARM64.</span><span class="sxs-lookup"><span data-stu-id="b9139-127">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="asset-swap-utility"></a><span data-ttu-id="b9139-128">Служебная программа переключения ресурсов</span><span class="sxs-lookup"><span data-stu-id="b9139-128">Asset swap utility</span></span>

<span data-ttu-id="b9139-129">Переключение нескольких ресурсов в сцене Unity с помощью новой [служебной программы переключения ресурсов](../features/tools/asset-swap-utility.md).</span><span class="sxs-lookup"><span data-stu-id="b9139-129">Swap multiple assets in a Unity scene with the new [Asset Swap utility](../features/tools/asset-swap-utility.md).</span></span>

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a><span data-ttu-id="b9139-130">Контроллеры Motion HP теперь поддерживаются с МРТК</span><span class="sxs-lookup"><span data-stu-id="b9139-130">HP Motion Controllers now supported with MRTK</span></span>

<span data-ttu-id="b9139-131">Контроллеры для переглагола HP теперь работают изначально с МРТК.</span><span class="sxs-lookup"><span data-stu-id="b9139-131">Controllers for the HP Reverb G2 now work natively with MRTK.</span></span>

### <a name="experimental-interactive-element--state-visualizer"></a><span data-ttu-id="b9139-132">Экспериментальный интерактивный элемент + визуализатор состояния</span><span class="sxs-lookup"><span data-stu-id="b9139-132">Experimental Interactive Element + State Visualizer</span></span>

<span data-ttu-id="b9139-133">Интерактивный элемент — это упрощенная централизованная точка входа в систему ввода МРТК.</span><span class="sxs-lookup"><span data-stu-id="b9139-133">Interactive Element is a simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="b9139-134">Он содержит методы управления состоянием, управление событиями и логику настройки состояния для основных состояний взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b9139-134">It contains state management methods, event management and the state setting logic for Core Interaction States.</span></span> <span data-ttu-id="b9139-135">Дополнительные сведения см. в [документации по интерактивному элементу](../features/experimental/interactive-element.md).</span><span class="sxs-lookup"><span data-stu-id="b9139-135">For more information see [Interactive Element Documentation](../features/experimental/interactive-element.md).</span></span>

![интерактивилементаддкорестате](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

<span data-ttu-id="b9139-137">Визуализатор состояния — это компонент анимации, который зависит от интерактивного элемента.</span><span class="sxs-lookup"><span data-stu-id="b9139-137">The State Visualizer is an animation component that depends on Interactive Element.</span></span> <span data-ttu-id="b9139-138">Этот компонент создает анимированные фрагменты, устанавливает опорные кадры и создает конечный автомат аниматор.</span><span class="sxs-lookup"><span data-stu-id="b9139-138">This component creates Animation Clips, sets keyframes and generates an Animator State Machine.</span></span> <span data-ttu-id="b9139-139">Дополнительные сведения см. в [документации по визуализатору состояния](../features/experimental/interactive-element.md#state-visualizer-experimental) .</span><span class="sxs-lookup"><span data-stu-id="b9139-139">For more information see [State Visualizer Documentation](../features/experimental/interactive-element.md#state-visualizer-experimental)</span></span>

![статевисуализерколорчанжеонфокус](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a><span data-ttu-id="b9139-141">Телепортироваться с помощью жеста телепортируйтесь, который теперь поддерживается на всех платформах</span><span class="sxs-lookup"><span data-stu-id="b9139-141">Teleportation with the teleport gesture now supported on all platforms</span></span>

<span data-ttu-id="b9139-142">Теперь пользователи могут использовать жест телепортируйтесь, чтобы перемещаться вокруг пространства воспроизведения на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="b9139-142">Users can now use the teleport gesture to move around their play space across all platforms.</span></span> <span data-ttu-id="b9139-143">Чтобы телепортируйтесь с контроллером на устройствах MR с конфигурациями по умолчанию, используйте аналоговый стик.</span><span class="sxs-lookup"><span data-stu-id="b9139-143">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="b9139-144">Чтобы телепортируйтесь с поднятыми руки, нарисуйте жест с помощью своего карманного ПК с помощью индекса и пальца, чтобы выполнить телепортироваться через фигуру указателя.</span><span class="sxs-lookup"><span data-stu-id="b9139-144">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="b9139-145">Чтобы телепортируйтесь с моделированием ввода, ознакомьтесь с нашей обновленной [документацией по службе моделирования ввода](../features/input-simulation/input-simulation-service.md).</span><span class="sxs-lookup"><span data-stu-id="b9139-145">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../features/input-simulation/input-simulation-service.md).</span></span>

![Жест телепортируйтесь](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a><span data-ttu-id="b9139-147">Основные сведения о сцене теперь доступны в МРТК как экспериментальный наблюдатель пространственной информации</span><span class="sxs-lookup"><span data-stu-id="b9139-147">Scene Understanding now available in MRTK as an experimental spatial awareness observer</span></span>

<span data-ttu-id="b9139-148">Экспериментальная поддержка [понимания сцены](/windows/mixed-reality/scene-understanding) представлена в мртк 2,6.</span><span class="sxs-lookup"><span data-stu-id="b9139-148">Experimental support of [Scene Understanding](/windows/mixed-reality/scene-understanding) is introduced in MRTK 2.6.</span></span> <span data-ttu-id="b9139-149">Пользователи могут внедрить сцену, чтобы понять возможности HoloLens 2 в проектах на основе МРТК.</span><span class="sxs-lookup"><span data-stu-id="b9139-149">Users can incorporate the scene understanding capabilities of HoloLens 2 as a spatial awareness observer in MRTK based projects.</span></span> <span data-ttu-id="b9139-150">Дополнительные сведения см. в [документации по монтажному кадру](../features/spatial-awareness/scene-understanding.md) .</span><span class="sxs-lookup"><span data-stu-id="b9139-150">Please read the [Scene Understanding documentation](../features/spatial-awareness/scene-understanding.md) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9139-151">Понимание сцены поддерживается только в HoloLens 2 и Unity 2019,4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="b9139-151">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>
>
> <span data-ttu-id="b9139-152">Для этой функции требуется представление "пакет" для сцены, которое теперь доступно через [инструмент "функция" смешанной реальности](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="b9139-152">This feature requires the Scene Understanding package, which is now available via the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>
> <span data-ttu-id="b9139-153">При использовании средства «функция Mixed Reality» или при импорте с помощью УПМ импортируйте пример демонстрационной версии Спатиалаваренесс перед импортом примера экспериментального Сценеундерстандинг из-за проблемы с зависимостью.</span><span class="sxs-lookup"><span data-stu-id="b9139-153">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="b9139-154">Дополнительные сведения см. в [этой ошибке GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .</span><span class="sxs-lookup"><span data-stu-id="b9139-154">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

![Основные сведения о сцене](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a><span data-ttu-id="b9139-156">Поддержка переключения профилей среды выполнения</span><span class="sxs-lookup"><span data-stu-id="b9139-156">Runtime profile switching support</span></span>

<span data-ttu-id="b9139-157">МРТК теперь поддерживает переключение профилей перед инициализацией экземпляра МРТК (т. е. параметр профиля инициализации pre МРТК) и после того, как профиль был активен в активном режиме (т. е. в активном параметре профиля).</span><span class="sxs-lookup"><span data-stu-id="b9139-157">MRTK now allows profile switching both before the initialization of the MRTK instance (i.e. Pre MRTK initialization profile switch) and after a profile has been in active use (i.e. Active profile switch).</span></span> <span data-ttu-id="b9139-158">Бывший параметр можно использовать для включения выбора компонентов на основе возможностей оборудования, а второй — для изменения интерфейса при входе пользователя в часть приложения.</span><span class="sxs-lookup"><span data-stu-id="b9139-158">The former switch can be used to enable select components based on capabilities of the hardware, while the latter can be used to modify experience as the user enters a subpart of the application.</span></span> <span data-ttu-id="b9139-159">Дополнительные сведения и примеры кода см. в [документации по переключению профилей](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) .</span><span class="sxs-lookup"><span data-stu-id="b9139-159">Please read the [documentation on profile switching](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) for more information and code samples.</span></span>

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a><span data-ttu-id="b9139-160">Индикатор направления и дальнейшие действия для поиска решения в экспериментальном режиме</span><span class="sxs-lookup"><span data-stu-id="b9139-160">Directional indicator and follow solvers graduated from experimental</span></span>

<span data-ttu-id="b9139-161">Два новых решения для работы с магистральными МРТКми готовы.</span><span class="sxs-lookup"><span data-stu-id="b9139-161">Two new solvers are ready for use with mainline MRTK.</span></span>

![Поиск решения для индикатора направления](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a><span data-ttu-id="b9139-163">Обучение от экспериментального учебного заведения</span><span class="sxs-lookup"><span data-stu-id="b9139-163">Hand Coach graduated from experimental</span></span>

<span data-ttu-id="b9139-164">Теперь функция подготовки к работе уже готова к использованию в магистральной МРТК.</span><span class="sxs-lookup"><span data-stu-id="b9139-164">The Hand Coach feature is now ready for use with mainline MRTK.</span></span>

![Пример подготовки к рукой](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a><span data-ttu-id="b9139-166">Элементы управления диалогового окна, постепенные от экспериментальных</span><span class="sxs-lookup"><span data-stu-id="b9139-166">Dialog controls graduated from experimental</span></span>

<span data-ttu-id="b9139-167">Элементы управления диалогового окна теперь готовы к использованию в магистральной МРТК.</span><span class="sxs-lookup"><span data-stu-id="b9139-167">Dialog controls are now ready for use with mainline MRTK.</span></span>

![Элементы управления диалогового окна](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a><span data-ttu-id="b9139-169">Постепенной шейдер с экспериментальным выпуском</span><span class="sxs-lookup"><span data-stu-id="b9139-169">Pulse shader graduated from experimental</span></span>

<span data-ttu-id="b9139-170">Повышено экспериментальные сценарии шейдера пульса.</span><span class="sxs-lookup"><span data-stu-id="b9139-170">The Pulse shader scripts have graduated from experimental.</span></span> <span data-ttu-id="b9139-171">Дополнительные сведения см. в разделе [Документация по импульсному шейдеру](../features/rendering/pulse-shader.md)</span><span class="sxs-lookup"><span data-stu-id="b9139-171">For more information see: [Pulse Shader Documentation](../features/rendering/pulse-shader.md)</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a><span data-ttu-id="b9139-173">Усовершенствования службы записи ввода</span><span class="sxs-lookup"><span data-stu-id="b9139-173">Input Recording Service improvements</span></span>

<span data-ttu-id="b9139-174">`InputRecordingService` и `InputPlaybackService` теперь могут записывать и воспроизводить входные данные взгляда.</span><span class="sxs-lookup"><span data-stu-id="b9139-174">`InputRecordingService` and `InputPlaybackService` can now record and play back eye gaze input.</span></span> <span data-ttu-id="b9139-175">Запись оптимизирована для обеспечения согласованной частоты кадров в течение периода записи, а время записи размера файла и экономии времени сокращается примерно на 50%.</span><span class="sxs-lookup"><span data-stu-id="b9139-175">Recording has been optimized to ensure a consistent framerate throughout the recording period while recording file size and save time are also reduced by about 50%.</span></span> <span data-ttu-id="b9139-176">Сохранение и загрузка файлов записи теперь можно выполнять асинхронно.</span><span class="sxs-lookup"><span data-stu-id="b9139-176">Saving and loading of recording files can now be performed asynchronously.</span></span> <span data-ttu-id="b9139-177">Обратите внимание, что формат файла записи изменился в этой версии МРТК. Дополнительные сведения о новых спецификациях версии 1,1 см. [здесь](../features/input-simulation/input-animation-file-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b9139-177">Note the file format of the recording has changed in this MRTK version, please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="reading-mode"></a><span data-ttu-id="b9139-178">Режим чтения</span><span class="sxs-lookup"><span data-stu-id="b9139-178">Reading mode</span></span>

<span data-ttu-id="b9139-179">Добавлена поддержка [режима чтения](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b9139-179">Added support for [reading mode](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) on HoloLens 2.</span></span> <span data-ttu-id="b9139-180">Режим чтения уменьшает поле представления системы, но устраняет масштабирование выходных данных Unity.</span><span class="sxs-lookup"><span data-stu-id="b9139-180">Reading mode reduces the system's field of view but eliminates a scaling of Unity's output.</span></span> <span data-ttu-id="b9139-181">Пиксель, отображаемый Unity, будет соответствовать прогнозируемому пикселю в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b9139-181">A pixel rendered by Unity will correspond to a projected pixel on HoloLens 2.</span></span> <span data-ttu-id="b9139-182">Авторы приложений должны выполнять тесты с несколькими пользователями, чтобы убедиться в том, что это будет компромисс в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="b9139-182">Application authors should do tests with multiple individuals to be sure this is a tradeoff they want in their app.</span></span>

![Режим чтения Windows Mixed Reality](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a><span data-ttu-id="b9139-184">Поддержка запуска трехмерных приложений в UWP</span><span class="sxs-lookup"><span data-stu-id="b9139-184">Support for 3D app launchers on UWP</span></span>

<span data-ttu-id="b9139-185">Добавляет возможность настройки средства [запуска 3D-приложений](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) для UWP.</span><span class="sxs-lookup"><span data-stu-id="b9139-185">Adds the ability to set a [3D app launcher](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for UWP.</span></span> <span data-ttu-id="b9139-186">Этот параметр доступен как в окне сборка МРТК, так и в параметрах проекта МРТК в разделе параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="b9139-186">This setting is exposed both in the MRTK Build Window and the MRTK Project Settings, under Build Settings.</span></span> <span data-ttu-id="b9139-187">Он автоматически записывается в проект во время сборки в Unity.</span><span class="sxs-lookup"><span data-stu-id="b9139-187">It's automatically written into the project during the build in Unity.</span></span>

![Параметры сборки](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a><span data-ttu-id="b9139-189">Критические изменения</span><span class="sxs-lookup"><span data-stu-id="b9139-189">Breaking changes</span></span>

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a><span data-ttu-id="b9139-190">Некоторые поля импортированных объектов ГЛТФ теперь заглавные буквы</span><span class="sxs-lookup"><span data-stu-id="b9139-190">Certain fields of imported GLTF objects are now capitalized</span></span>

<span data-ttu-id="b9139-191">Из-за проблем, связанных с десериализациям, некоторые поля импортированных объектов ГЛТФ теперь начинаются с прописных букв.</span><span class="sxs-lookup"><span data-stu-id="b9139-191">Due to deserialization related issues some fields of imported GLTF objects are now starting with capital letters.</span></span> <span data-ttu-id="b9139-192">Затронутые поля (в их новых именах): `ComponentType` , `Path` , `Interpolation` , `Target` , `Type` , `Mode` , `MagFilter` , `MinFilter` , `WrapS` , `WrapT` .</span><span class="sxs-lookup"><span data-stu-id="b9139-192">The affected fields are (in their new names): `ComponentType`, `Path`, `Interpolation`, `Target`, `Type`, `Mode`, `MagFilter`, `MinFilter`, `WrapS`, `WrapT`.</span></span>

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a><span data-ttu-id="b9139-193">Двоичный файл входной анимации имеет обновленный формат версии 1,1</span><span class="sxs-lookup"><span data-stu-id="b9139-193">Input animation binary file has an updated version 1.1 format</span></span>

<span data-ttu-id="b9139-194">Двоичный файл анимации ввода, используемый `InputRecordingService` и `InputPlaybackService` , теперь имеет обновленный формат файла для включения оптимизации для этих двух служб.</span><span class="sxs-lookup"><span data-stu-id="b9139-194">Input animation binary file, used by `InputRecordingService` and `InputPlaybackService`, now has an updated file format to enable the optimizations made to those two services.</span></span> <span data-ttu-id="b9139-195">Дополнительные сведения о новых спецификациях версии 1,1 см. [здесь](../features/input-simulation/input-animation-file-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b9139-195">Please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="b9139-196">Поддержка MSBuild для поддержки Unity</span><span class="sxs-lookup"><span data-stu-id="b9139-196">MSBuild for Unity support</span></span>

<span data-ttu-id="b9139-197">Поддержка MSBuild для Unity была удалена в 2.5.2 выпуске для согласования с [новым руководством по пакетам Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span><span class="sxs-lookup"><span data-stu-id="b9139-197">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="b9139-198">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="b9139-198">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="b9139-199">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b9139-199">OpenXR</span></span>

<span data-ttu-id="b9139-200">В настоящее время существует известная ситуация с holographic удаленным взаимодействием и Опенкср, в которой соединения не являются постоянно доступными.</span><span class="sxs-lookup"><span data-stu-id="b9139-200">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="b9139-201">Кроме того, в настоящее время _не_ поддерживается отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="b9139-201">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking _does_ work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="b9139-202">Для некоторых функций шейдера "Стандартный" набора средств смешанной реальности требуется пакет Foundation</span><span class="sxs-lookup"><span data-stu-id="b9139-202">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="b9139-203">При импорте с помощью диспетчера пакетов Unity скрипты служебных программ для стандартных шейдеров МРТК (например, Ховерлигхт. cs) не располагаются совместно с шейдером в пакете стандартных активов.</span><span class="sxs-lookup"><span data-stu-id="b9139-203">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="b9139-204">Для доступа к этой функции приложениям потребуется импортировать пакет Foundation.</span><span class="sxs-lookup"><span data-stu-id="b9139-204">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="b9139-205">Камеракаче может создать новую камеру при завершении работы</span><span class="sxs-lookup"><span data-stu-id="b9139-205">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="b9139-206">В некоторых ситуациях (например, при использовании поставщика Леапмотион в редакторе Unity) Камеракаче может повторно создать Маинкамера при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="b9139-206">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="b9139-207">Дополнительные сведения см. в [этой статье](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .</span><span class="sxs-lookup"><span data-stu-id="b9139-207">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="b9139-208">FileNotFoundException при импорте примеров с помощью диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="b9139-208">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="b9139-209">В зависимости от длины пути проекта Импорт примеров через диспетчер пакетов Unity может создавать сообщения FileNotFoundException в консоли Unity.</span><span class="sxs-lookup"><span data-stu-id="b9139-209">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="b9139-210">Причина в том, что путь к файлу "Missing" превышает MAX_PATH (256 символов).</span><span class="sxs-lookup"><span data-stu-id="b9139-210">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="b9139-211">Чтобы устранить проблему, Сократите длину пути к проекту.</span><span class="sxs-lookup"><span data-stu-id="b9139-211">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="b9139-212">Спатиализер не указан.</span><span class="sxs-lookup"><span data-stu-id="b9139-212">No spatializer was specified.</span></span> <span data-ttu-id="b9139-213">Приложение не будет поддерживать Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="b9139-213">The application will not support Spatial Sound</span></span>

<span data-ttu-id="b9139-214">Предупреждение "не указано спатиализер" отображается, если не настроено звуковое спатиализер.</span><span class="sxs-lookup"><span data-stu-id="b9139-214">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="b9139-215">Это может произойти, если пакет XR не установлен, так как Unity включает спатиализерс в эти пакеты.</span><span class="sxs-lookup"><span data-stu-id="b9139-215">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="b9139-216">Чтобы устранить эту проблему, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="b9139-216">To resolve, please ensure that:</span></span>

- <span data-ttu-id="b9139-217">**Окно**  >  В **диспетчере пакетов** установлен один или несколько пакетов XR</span><span class="sxs-lookup"><span data-stu-id="b9139-217">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="b9139-218">**Набор средств**  >  для смешанной реальности **Служебные программы**  >  **Настройка проекта Unity** и выбор для **спатиализер звука**</span><span class="sxs-lookup"><span data-stu-id="b9139-218">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Выберите Audio Спатиализер](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="b9139-220">NullReferenceException: ссылка на объект не задает экземпляр объекта (SceneTransitionService.Iniтиализе)</span><span class="sxs-lookup"><span data-stu-id="b9139-220">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="b9139-221">В некоторых ситуациях открытие `EyeTrackingDemo-00-RootScene` может вызвать NullReferenceException в методе Initialize класса сценетранситионсервице.</span><span class="sxs-lookup"><span data-stu-id="b9139-221">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="b9139-222">Эта ошибка возникает из-за того, что профиль конфигурации службы смены сцены не установлен.</span><span class="sxs-lookup"><span data-stu-id="b9139-222">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="b9139-223">Чтобы устранить эту проблему, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b9139-223">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="b9139-224">Переход к `MixedRealityToolkit` объекту в иерархии</span><span class="sxs-lookup"><span data-stu-id="b9139-224">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="b9139-225">В окне инспектора выберите `Extensions`</span><span class="sxs-lookup"><span data-stu-id="b9139-225">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="b9139-226">Если не развернуто, разверните узел `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="b9139-226">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="b9139-227">Присвойте параметру `Configuration Profile` значение **мрткексамплешубсценетранситионсервицепрофиле** .</span><span class="sxs-lookup"><span data-stu-id="b9139-227">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![Исправить профиль перехода сцены](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="b9139-229">Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b9139-229">Oculus Quest</span></span>

<span data-ttu-id="b9139-230">В настоящее время существует известная ошибка при использовании [подключаемого модуля Окулус XR с целью использования изолированных платформ](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="b9139-230">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="b9139-231">Ознакомьтесь с разметкой об ошибках Окулус, а также с заметками о выпуске для обновлений.</span><span class="sxs-lookup"><span data-stu-id="b9139-231">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="b9139-232">Ошибка указывает на этот набор из трех ошибок:</span><span class="sxs-lookup"><span data-stu-id="b9139-232">The bug is signified with this set of 3 errors:</span></span>

![Ошибка подключаемого модуля XR Окулус](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="b9139-234">Унитюи и Текстмешпро</span><span class="sxs-lookup"><span data-stu-id="b9139-234">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="b9139-235">Существует известная ошибка для новых версий Текстмешпро (1.5.0 + или более поздней версии), где размер шрифта по умолчанию для раскрывающихся списков и интервалы между символами шрифта были изменены.</span><span class="sxs-lookup"><span data-stu-id="b9139-235">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Образ TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="b9139-237">Это можно обойти, понизить до более ранней версии Текстмешпро.</span><span class="sxs-lookup"><span data-stu-id="b9139-237">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="b9139-238">Дополнительные сведения см. в разделе о [выпуске #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .</span><span class="sxs-lookup"><span data-stu-id="b9139-238">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
