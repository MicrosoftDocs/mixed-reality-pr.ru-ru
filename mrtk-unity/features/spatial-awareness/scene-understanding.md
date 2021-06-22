---
title: Основные сведения о сцене
description: Описание принципов работы с сценами в МРТК
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, основные сведения о сцене
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449753"
---
# <a name="scene-understanding"></a><span data-ttu-id="b3fa4-104">Основные сведения о сцене</span><span class="sxs-lookup"><span data-stu-id="b3fa4-104">Scene Understanding</span></span>

<span data-ttu-id="b3fa4-105">[Понятие "сцена](/windows/mixed-reality/scene-understanding) " возвращает семантическое представление сущностей сцены, а также их геометрические формы в __HoloLens 2__ (не поддерживается Hololens 1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="b3fa4-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="b3fa4-106">Ниже перечислены некоторые ожидаемые варианты использования этой технологии.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="b3fa4-107">Размещение объектов на ближайшей поверхности определенного вида (например, стены и этажа)</span><span class="sxs-lookup"><span data-stu-id="b3fa4-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="b3fa4-108">Создание панели навигации — сетки для игр в стиле платформы</span><span class="sxs-lookup"><span data-stu-id="b3fa4-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="b3fa4-109">Предоставление понятных геометрических объектов с четырьмя подсистемами</span><span class="sxs-lookup"><span data-stu-id="b3fa4-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="b3fa4-110">Ускорение разработки за счет предотвращения необходимости написания аналогичных алгоритмов</span><span class="sxs-lookup"><span data-stu-id="b3fa4-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="b3fa4-111">Основные сведения о сцене представлены в виде __экспериментальной__ функции в мртк 2,6.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="b3fa4-112">Он интегрируется в МРТК как [пространственный наблюдатель](spatial-awareness-getting-started.md#register-observers) с именем [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="b3fa4-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="b3fa4-113">Понятие "сцены" работает как с устаревшим конвейером XR, так и с конвейером пакета SDK XR (Опенкср (начиная с МРТК 2,7) и подключаемым модулем Windows XR).</span><span class="sxs-lookup"><span data-stu-id="b3fa4-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="b3fa4-114">В обоих случаях `WindowsSceneUnderstandingObserver` используется.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="b3fa4-115">Использование сцены в удаленном взаимодействии не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="b3fa4-116">Общие сведения об наблюдателе</span><span class="sxs-lookup"><span data-stu-id="b3fa4-116">Observer overview</span></span>

<span data-ttu-id="b3fa4-117">При запросе [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) будет возвращено [спатиалаваренесссценеобжект](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) с атрибутами, полезными для приложения, чтобы понять его окружение.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="b3fa4-118">Частота наблюдения, возвращаемый тип объекта (например, стена, Floor) и другие поведения наблюдателя, зависит от конфигурации наблюдателя с помощью профиля.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="b3fa4-119">Например, если требуется маска перекрытия, наблюдатель должен быть настроен для формирования четырех чисел.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="b3fa4-120">Наблюдаемая сцена может быть сохранена в виде сериализованного файла, который впоследствии можно загрузить, чтобы воссоздать сцену в редакторе в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="b3fa4-121">Настройка</span><span class="sxs-lookup"><span data-stu-id="b3fa4-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3fa4-122">Понимание сцены поддерживается только в HoloLens 2 и Unity 2019,4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="b3fa4-123">Убедитесь, что платформа имеет значение UWP в параметрах сборки.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="b3fa4-124">Получите представление о пакете с помощью [средства "функция смешанной реальности](https://aka.ms/MRFeatureTool)".</span><span class="sxs-lookup"><span data-stu-id="b3fa4-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="b3fa4-125">Основные сведения об использовании сцены</span><span class="sxs-lookup"><span data-stu-id="b3fa4-125">Using Scene Understanding</span></span>

<span data-ttu-id="b3fa4-126">Самый быстрый способ приступить к пониманию сцены — извлечь пример сцены.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="b3fa4-127">Пример сцены "сцена"</span><span class="sxs-lookup"><span data-stu-id="b3fa4-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="b3fa4-128">В Unity используйте обозреватель проектов, чтобы открыть файл сцены в `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` , и нажмите кнопку Воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="b3fa4-129">Применяется только к МРТК 2.6.0 — при использовании средства "функция Mixed Reality" или при импорте через УПМ. Импортируйте пример "демонстрационные версии-Спатиалаваренесс" перед импортом примера "экспериментальный-Сценеундерстандинг" из-за проблемы с зависимостью.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="b3fa4-130">Дополнительные сведения см. в [этой ошибке GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .</span><span class="sxs-lookup"><span data-stu-id="b3fa4-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="b3fa4-131">Сцена демонстрирует следующее:</span><span class="sxs-lookup"><span data-stu-id="b3fa4-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="b3fa4-132">Визуализация наблюдаемых объектов сцены в пользовательском интерфейсе приложения для настройки наблюдателя</span><span class="sxs-lookup"><span data-stu-id="b3fa4-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="b3fa4-133">Пример `DemoSceneUnderstandingController` скрипта, демонстрирующий изменение параметров наблюдателя и прослушивание соответствующих событий</span><span class="sxs-lookup"><span data-stu-id="b3fa4-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="b3fa4-134">Сохранение данных сцены на устройстве для автономной разработки</span><span class="sxs-lookup"><span data-stu-id="b3fa4-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="b3fa4-135">Загрузка ранее сохраненных данных сцены (байт-файлов) для поддержки рабочего процесса разработки в редакторе</span><span class="sxs-lookup"><span data-stu-id="b3fa4-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3fa4-136">По умолчанию `ShouldLoadFromFile` свойство наблюдателя имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="b3fa4-137">Чтобы увидеть визуализацию сериализованного примера комнаты, ознакомьтесь с разделом [Настройка службы наблюдателя](#configuring-the-observer-service) ниже и задайте для свойства значение true в редакторе.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="b3fa4-138">Пример сцены основан на устаревшем конвейере XR.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="b3fa4-139">При использовании конвейера пакета SDK для XR необходимо соответствующим образом изменить профили.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="b3fa4-140">Указанная сцена, посвященная системному профилю пространственной информации ( `DemoSceneUnderstandingSystemProfile` ) и сцене, посвященной профилям наблюдателя ( `DefaultSceneUnderstandingObserverProfile` и `DemoSceneUnderstandingObserverProfile` ), работает для обоих конвейеров.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="b3fa4-141">Пример сцены регистрирует `There is no active AsyncCoroutineRunner when an action is posted.` предупреждение при определенных обстоятельствах из-за инициализации или порядка выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="b3fa4-142">Если вы можете подтвердить, что `AsyncCoroutineRunner` компонент подключен к "демонстрационному контроллеру" GameObject, а компонент или GameObject остается включенным/активным в сцене (вариант по умолчанию), это предупреждение можно спокойно проигнорировать.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="b3fa4-143">**Однако при создании сцены с пониманием сцены необходимо создать пустую GameObject в корне и присоединить `AsyncCoroutineRunner` к ней скрипт, иначе понимание сцены может работать неправильно.**</span><span class="sxs-lookup"><span data-stu-id="b3fa4-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="b3fa4-144">Настройка службы наблюдателя</span><span class="sxs-lookup"><span data-stu-id="b3fa4-144">Configuring the observer service</span></span>

<span data-ttu-id="b3fa4-145">Выберите объект игры "Микседреалититулкит" и проверьте инспектор.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![Сцена, в которой понимается расположение в иерархии](../images/spatial-awareness/MRTKHierarchy.png)

![Расположение МРТК в инспекторе](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="b3fa4-148">Эти параметры позволяют настроить `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="b3fa4-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="b3fa4-149">Пример сценария</span><span class="sxs-lookup"><span data-stu-id="b3fa4-149">Example script</span></span>

<span data-ttu-id="b3fa4-150">В примере сценария _демосценеундерстандингконтроллер. CS_ демонстрируются основные понятия, связанные с работой со службой "сцена".</span><span class="sxs-lookup"><span data-stu-id="b3fa4-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="b3fa4-151">Подписка на сцену основные сведения о событиях</span><span class="sxs-lookup"><span data-stu-id="b3fa4-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="b3fa4-152">Обработка событий сцены</span><span class="sxs-lookup"><span data-stu-id="b3fa4-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="b3fa4-153">Настройка `WindowsSceneUnderstandingObserver` среды выполнения</span><span class="sxs-lookup"><span data-stu-id="b3fa4-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="b3fa4-154">Переключатели на панели сцены изменяют поведение сцены в представлении "наблюдатель", вызывая открытые функции этого примера скрипта.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="b3fa4-155">При включении *создания экземпляра Prefabs* будет продемонстрировано создание объектов, размер которых должен соответствовать всем [спатиалаваренесссценеобжект](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), собираются в соответствии с родительским объектом.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![Параметры демонстрационного контроллера](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="b3fa4-157">Заметки о построении приложения</span><span class="sxs-lookup"><span data-stu-id="b3fa4-157">Built app notes</span></span>

<span data-ttu-id="b3fa4-158">Создавайте и развертывайте в HoloLens стандартным способом.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="b3fa4-159">После запуска для воспроизведения этих функций должно отобразиться несколько кнопок.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="b3fa4-160">Обратите внимание, что некоторые отчасти отправляют запросы наблюдателю.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="b3fa4-161">Неверная настройка результата запроса выборки в полезных данных события, не содержащих ожидаемые данные.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="b3fa4-162">Например, если один из них не запрашивает четыре числа, текстуры маски перекрытия не будут отображаться.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="b3fa4-163">Как и в разумных случаях, универсальные сети не отображаются, если наблюдатель не настроен на запрос сеток.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="b3fa4-164">Сценарий позаботится `DemoSceneUnderstandingController` о некоторых из этих зависимостей, но не на всех.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="b3fa4-165">Доступ к сохраненным файлам сцены можно получить на [портале устройств](/windows/mixed-reality/using-the-windows-device-portal) по адресу `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="b3fa4-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="b3fa4-166">Эти файлы сцены можно использовать в редакторе, указывая их в профиле наблюдателя, который находится в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="b3fa4-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Расположение файла (байт) на портале устройства](../images/spatial-awareness/BytesInDevicePortal.png)

![Байты сериализованной сцены в наблюдателе](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="b3fa4-169">См. также</span><span class="sxs-lookup"><span data-stu-id="b3fa4-169">See Also</span></span>

* [<span data-ttu-id="b3fa4-170">Общие сведения о сцене</span><span class="sxs-lookup"><span data-stu-id="b3fa4-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="b3fa4-171">Общие сведения о пакете SDK для сцены</span><span class="sxs-lookup"><span data-stu-id="b3fa4-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)