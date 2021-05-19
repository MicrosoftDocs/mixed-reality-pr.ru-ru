---
title: Основные сведения о сцене
description: Описание принципов работы с сценами в МРТК
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, основные сведения о сцене
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143888"
---
# <a name="scene-understanding"></a><span data-ttu-id="4cfbe-104">Основные сведения о сцене</span><span class="sxs-lookup"><span data-stu-id="4cfbe-104">Scene Understanding</span></span>

<span data-ttu-id="4cfbe-105">[Понятие "сцена](/windows/mixed-reality/scene-understanding) " возвращает семантическое представление сущностей сцены, а также их геометрические формы в __HoloLens 2__ (не поддерживается Hololens 1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="4cfbe-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="4cfbe-106">Ниже перечислены некоторые ожидаемые варианты использования этой технологии.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="4cfbe-107">Размещение объектов на ближайшей поверхности определенного вида (например, стены и этажа)</span><span class="sxs-lookup"><span data-stu-id="4cfbe-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="4cfbe-108">Создание панели навигации — сетки для игр в стиле платформы</span><span class="sxs-lookup"><span data-stu-id="4cfbe-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="4cfbe-109">Предоставление понятных геометрических объектов с четырьмя подсистемами</span><span class="sxs-lookup"><span data-stu-id="4cfbe-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="4cfbe-110">Ускорение разработки за счет предотвращения необходимости написания аналогичных алгоритмов</span><span class="sxs-lookup"><span data-stu-id="4cfbe-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="4cfbe-111">Основные сведения о сцене доступны в качестве __экспериментальной__ функции, начиная с мртк 2,6.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="4cfbe-112">Он интегрируется в МРТК как [пространственный наблюдатель](spatial-awareness-getting-started.md#register-observers) с именем [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="4cfbe-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="4cfbe-113">Понятие "сцены" работает как с устаревшим конвейером XR, так и с конвейером пакета SDK XR.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="4cfbe-114">В обоих случаях `WindowsSceneUnderstandingObserver` используется.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="4cfbe-115">Общие сведения об наблюдателе</span><span class="sxs-lookup"><span data-stu-id="4cfbe-115">Observer overview</span></span>

<span data-ttu-id="4cfbe-116">При запросе [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) будет возвращено [спатиалаваренесссценеобжект](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) с атрибутами, полезными для приложения, чтобы понять его окружение.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="4cfbe-117">Частота наблюдения, возвращаемый тип объекта (например, стена, Floor) и другие поведения наблюдателя, зависит от конфигурации наблюдателя с помощью профиля.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="4cfbe-118">Например, если требуется маска перекрытия, наблюдатель должен быть настроен для формирования четырех чисел.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="4cfbe-119">Наблюдаемая сцена может быть сохранена в виде сериализованного файла, который впоследствии можно загрузить, чтобы воссоздать сцену в редакторе в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="4cfbe-120">Настройка</span><span class="sxs-lookup"><span data-stu-id="4cfbe-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cfbe-121">Понимание сцены поддерживается только в HoloLens 2 и Unity 2019,4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="4cfbe-122">Убедитесь, что платформа имеет значение UWP в параметрах сборки.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="4cfbe-123">Получите представление о пакете с помощью [средства "функция смешанной реальности](https://aka.ms/MRFeatureTool)".</span><span class="sxs-lookup"><span data-stu-id="4cfbe-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="4cfbe-124">Основные сведения об использовании сцены</span><span class="sxs-lookup"><span data-stu-id="4cfbe-124">Using Scene Understanding</span></span>

<span data-ttu-id="4cfbe-125">Самый быстрый способ приступить к пониманию сцены — извлечь пример сцены.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="4cfbe-126">Пример сцены "сцена"</span><span class="sxs-lookup"><span data-stu-id="4cfbe-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="4cfbe-127">В Unity используйте обозреватель проектов, чтобы открыть файл сцены в `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` , и нажмите кнопку Воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cfbe-128">При использовании средства «функция Mixed Reality» или при импорте с помощью УПМ импортируйте пример демонстрационной версии Спатиалаваренесс перед импортом примера экспериментального Сценеундерстандинг из-за проблемы с зависимостью.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="4cfbe-129">Дополнительные сведения см. в [этой ошибке GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .</span><span class="sxs-lookup"><span data-stu-id="4cfbe-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="4cfbe-130">Сцена демонстрирует следующее:</span><span class="sxs-lookup"><span data-stu-id="4cfbe-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="4cfbe-131">Визуализация наблюдаемых объектов сцены в пользовательском интерфейсе приложения для настройки наблюдателя</span><span class="sxs-lookup"><span data-stu-id="4cfbe-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="4cfbe-132">Пример `DemoSceneUnderstandingController` скрипта, демонстрирующий изменение параметров наблюдателя и прослушивание соответствующих событий</span><span class="sxs-lookup"><span data-stu-id="4cfbe-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="4cfbe-133">Сохранение данных сцены на устройстве для автономной разработки</span><span class="sxs-lookup"><span data-stu-id="4cfbe-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="4cfbe-134">Загрузка ранее сохраненных данных сцены (байт-файлов) для поддержки рабочего процесса разработки в редакторе</span><span class="sxs-lookup"><span data-stu-id="4cfbe-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="4cfbe-135">Пример сцены основан на устаревшем конвейере XR.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="4cfbe-136">При использовании конвейера пакета SDK для XR необходимо соответствующим образом изменить профили.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="4cfbe-137">Указанная сцена, посвященная системному профилю пространственной информации ( `DemoSceneUnderstandingSystemProfile` ) и сцене, посвященной профилям наблюдателя ( `DefaultSceneUnderstandingObserverProfile` и `DemoSceneUnderstandingObserverProfile` ), работает для обоих конвейеров.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="4cfbe-138">Настройка службы наблюдателя</span><span class="sxs-lookup"><span data-stu-id="4cfbe-138">Configuring the observer service</span></span>

<span data-ttu-id="4cfbe-139">Выберите объект игры "Микседреалититулкит" и проверьте инспектор.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![Сцена, в которой понимается расположение в иерархии](../images/spatial-awareness/MRTKHierarchy.png)

![Расположение МРТК в инспекторе](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="4cfbe-142">Эти параметры позволяют настроить `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="4cfbe-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="4cfbe-143">Пример сценария</span><span class="sxs-lookup"><span data-stu-id="4cfbe-143">Example script</span></span>

<span data-ttu-id="4cfbe-144">В примере сценария _демосценеундерстандингконтроллер. CS_ демонстрируются основные понятия, связанные с работой со службой "сцена".</span><span class="sxs-lookup"><span data-stu-id="4cfbe-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="4cfbe-145">Подписка на сцену основные сведения о событиях</span><span class="sxs-lookup"><span data-stu-id="4cfbe-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="4cfbe-146">Обработка событий сцены</span><span class="sxs-lookup"><span data-stu-id="4cfbe-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="4cfbe-147">Настройка `WindowsSceneUnderstandingObserver` среды выполнения</span><span class="sxs-lookup"><span data-stu-id="4cfbe-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="4cfbe-148">Переключатели на панели сцены изменяют поведение сцены в представлении "наблюдатель", вызывая открытые функции этого примера скрипта.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="4cfbe-149">При включении *создания экземпляра Prefabs* будет продемонстрировано создание объектов, размер которых должен соответствовать всем [спатиалаваренесссценеобжект](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), собираются в соответствии с родительским объектом.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![Параметры демонстрационного контроллера](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="4cfbe-151">Заметки о построении приложения</span><span class="sxs-lookup"><span data-stu-id="4cfbe-151">Built app notes</span></span>

<span data-ttu-id="4cfbe-152">Создавайте и развертывайте в HoloLens стандартным способом.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="4cfbe-153">После запуска для воспроизведения этих функций должно отобразиться несколько кнопок.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="4cfbe-154">Обратите внимание, что некоторые отчасти отправляют запросы наблюдателю.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="4cfbe-155">Неверная настройка результата запроса выборки в полезных данных события, не содержащих ожидаемые данные.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="4cfbe-156">Например, если один из них не запрашивает четыре числа, текстуры маски перекрытия не будут отображаться.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="4cfbe-157">Как и в разумных случаях, универсальные сети не отображаются, если наблюдатель не настроен на запрос сеток.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="4cfbe-158">Сценарий позаботится `DemoSceneUnderstandingController` о некоторых из этих зависимостей, но не на всех.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="4cfbe-159">Доступ к сохраненным файлам сцены можно получить на [портале устройств](/windows/mixed-reality/using-the-windows-device-portal) по адресу `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="4cfbe-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="4cfbe-160">Эти файлы сцены можно использовать в редакторе, указывая их в профиле наблюдателя, который находится в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="4cfbe-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Расположение файла (байт) на портале устройства](../images/spatial-awareness/BytesInDevicePortal.png)

![Байты сериализованной сцены в наблюдателе](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="4cfbe-163">См. также:</span><span class="sxs-lookup"><span data-stu-id="4cfbe-163">See Also</span></span>

* [<span data-ttu-id="4cfbe-164">Общие сведения о пространственном сопоставлении ВМР</span><span class="sxs-lookup"><span data-stu-id="4cfbe-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="4cfbe-165">Общие сведения о пространственном сопоставлении ВМР</span><span class="sxs-lookup"><span data-stu-id="4cfbe-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)