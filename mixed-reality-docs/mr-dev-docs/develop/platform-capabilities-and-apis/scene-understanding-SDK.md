---
title: Пакет SDK для понимания сцены
description: Узнайте, как установить и использовать пакет SDK для сцены, включая компоненты, сетки и объекты в приложениях смешанной реальности.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Основные сведения о сцене, пространственное сопоставление, Windows Mixed Reality, Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009384"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="2df72-104">Общие сведения о пакете SDK для сцены</span><span class="sxs-lookup"><span data-stu-id="2df72-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="2df72-105">Понятие "сцена" преобразует неструктурированные данные датчика среды, записанные устройством смешанной реальности, и преобразует их в эффективное абстрактное представление.</span><span class="sxs-lookup"><span data-stu-id="2df72-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="2df72-106">Пакет SDK выступает в качестве коммуникационного уровня между приложением и сцены среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2df72-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="2df72-107">Он предназначен для имитации существующих стандартных конструкций, таких как графики трехмерных сцен для трехмерных представлений, и двумерных прямоугольников и панелей для двумерных приложений.</span><span class="sxs-lookup"><span data-stu-id="2df72-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="2df72-108">Хотя сцены конструкций понимают, что имитирует сопоставление с конкретными платформами, в целом Сценеундерстандинг является независимым от платформы и обеспечивает взаимодействие между различными средами, которые взаимодействуют с ним.</span><span class="sxs-lookup"><span data-stu-id="2df72-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="2df72-109">По мере того, как в сцене понимается развитие роли пакета SDK, мы видим, что новые представления и возможности по-прежнему будут доступны в единой инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="2df72-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="2df72-110">В этом документе мы сначала предложим основные понятия, которые помогут вам ознакомиться с средой разработки и использованием, а затем предоставить более подробную документацию по конкретным классам и конструкциям.</span><span class="sxs-lookup"><span data-stu-id="2df72-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="2df72-111">Где получить пакет SDK?</span><span class="sxs-lookup"><span data-stu-id="2df72-111">Where do I get the SDK?</span></span>

<span data-ttu-id="2df72-112">Пакет SDK для Сценеундерстандинг загружается через NuGet.</span><span class="sxs-lookup"><span data-stu-id="2df72-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="2df72-113">Пакет SDK для Сценеундерстандинг</span><span class="sxs-lookup"><span data-stu-id="2df72-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="2df72-114">**Примечание.** последний выпуск зависит от предварительных версий пакетов, и для его просмотра необходимо включить пакеты предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="2df72-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="2df72-115">Для версии 0.5.2022-RC и более поздних версий сцены понимает поддержку языковых проекций для C# и C++, позволяя приложениям разрабатывать приложения для платформ Win32 или UWP.</span><span class="sxs-lookup"><span data-stu-id="2df72-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="2df72-116">Начиная с этой версии, Сценеундерстандинг поддерживает поддержку Unity в редакторе, позволяя отменять Сценеобсервер, который используется исключительно для взаимодействия с HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="2df72-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="2df72-117">Для Сценеундерстандинг требуется Windows SDK версии 18362 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="2df72-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="2df72-118">Если вы используете пакет SDK в проекте Unity, используйте [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity) , чтобы установить пакет в проект.</span><span class="sxs-lookup"><span data-stu-id="2df72-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="2df72-119">Общие сведения об основных понятиях</span><span class="sxs-lookup"><span data-stu-id="2df72-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="2df72-120">Сцена</span><span class="sxs-lookup"><span data-stu-id="2df72-120">The Scene</span></span>

<span data-ttu-id="2df72-121">Устройство Mixed Reality постоянно интегрирует информацию о том, что она видит в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="2df72-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="2df72-122">При понимании сцены создаются все эти источники данных и создается одна единая абстракция.</span><span class="sxs-lookup"><span data-stu-id="2df72-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="2df72-123">Понятие сцены создает сцены, представляющие собой композицию [сценеобжектс](scene-understanding-SDK.md#sceneobjects) , которая представляет экземпляр одной вещи (например, стены, потолка или этажа). Сами объекты сцены представляют собой композицию [Сценекомпонентс, представляющую более детализированные элементы, составляющие этот Сценеобжект.</span><span class="sxs-lookup"><span data-stu-id="2df72-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="2df72-124">Примерами компонентов являются четыре и сетчатые сети, но в будущем они могут представлять ограничивающие рамки, конфликты сеток, метаданные и т. д.</span><span class="sxs-lookup"><span data-stu-id="2df72-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="2df72-125">Процесс преобразования необработанных данных датчика в сцену является потенциально дорогостоящей операцией, которая может занять секунды для средних пробелов (~ 10x10m) в минутах для больших пробелов (~ 50x50m) и, следовательно, не будет вычисляться устройством без запроса приложения.</span><span class="sxs-lookup"><span data-stu-id="2df72-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="2df72-126">Вместо этого создание сцены активируется вашим приложением по запросу.</span><span class="sxs-lookup"><span data-stu-id="2df72-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="2df72-127">Класс Сценеобсервер содержит статические методы, которые могут вычислять или десериализовать сцену, которые затем можно перечислить или взаимодействовать с.</span><span class="sxs-lookup"><span data-stu-id="2df72-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="2df72-128">Действие "вычисление" выполняется по требованию и выполняется в ЦП, но в отдельном процессе (драйвер Mixed Reality).</span><span class="sxs-lookup"><span data-stu-id="2df72-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="2df72-129">Однако, пока мы выполняем вычисление в другом процессе, полученные данные сцены сохраняются и обслуживаются в приложении в объекте сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="2df72-130">Ниже приведена схема, на которой показан этот поток процесса, и приведены примеры двух приложений, взаимодействующих с сценой выполнения.</span><span class="sxs-lookup"><span data-stu-id="2df72-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Схема процесса](images/SU-ProcessFlow.png)

<span data-ttu-id="2df72-132">В левой части находится схема среды выполнения Mixed Reality, которая всегда включена и выполняется в собственном процессе.</span><span class="sxs-lookup"><span data-stu-id="2df72-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="2df72-133">Эта среда выполнения отвечает за выполнение отслеживания устройств, пространственное сопоставление и другие операции, которые используются в сцене для понимания и причины вокруг всего мира.</span><span class="sxs-lookup"><span data-stu-id="2df72-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="2df72-134">В правой части схемы показаны два теоретических приложения, которые используют понимание сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="2df72-135">Первое приложение взаимодействует с МРТК, которое использует для внутренних целей пакет SDK, второе приложение выполняет вычисление и использует два отдельных экземпляра сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="2df72-136">Все три сцены на этой схеме создают отдельные экземпляры сцен, драйвер не отслеживает глобальное состояние, которое совместно используется приложениями, а объекты сцены в одной сцене не находятся в другой.</span><span class="sxs-lookup"><span data-stu-id="2df72-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="2df72-137">Понятие "сцена" обеспечивает механизм для мониторинга со временем, но это делается с помощью пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="2df72-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="2df72-138">Код отслеживания уже выполняется в пакете SDK в процессе приложения.</span><span class="sxs-lookup"><span data-stu-id="2df72-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="2df72-139">Поскольку каждый монтажный кадр хранит данные в памяти приложения, можно предположить, что все функции объекта сцены или внутренние данные всегда выполняются в процессе приложения.</span><span class="sxs-lookup"><span data-stu-id="2df72-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="2df72-140">Layout</span><span class="sxs-lookup"><span data-stu-id="2df72-140">Layout</span></span>

<span data-ttu-id="2df72-141">Для работы с представлением сцены может быть полезно знать и понять, как среда выполнения представляет компоненты логически и физически.</span><span class="sxs-lookup"><span data-stu-id="2df72-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="2df72-142">Сцена представляет данные с определенным макетом, который был выбран для простоты при сохранении базовой структуры, плиабле в соответствии с будущими требованиями, не требуя значительных изменений.</span><span class="sxs-lookup"><span data-stu-id="2df72-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="2df72-143">Сцена делает это, сохраняя все компоненты (стандартные блоки для всех объектов сцены) в плоском списке и определяя иерархию и композицию с помощью ссылок, где определенные компоненты ссылаются на другие.</span><span class="sxs-lookup"><span data-stu-id="2df72-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="2df72-144">Ниже представлен пример структуры как в плоской, так и в логической форме.</span><span class="sxs-lookup"><span data-stu-id="2df72-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="2df72-145">Логический макет</span><span class="sxs-lookup"><span data-stu-id="2df72-145">Logical Layout</span></span></th><th><span data-ttu-id="2df72-146">Физический макет</span><span class="sxs-lookup"><span data-stu-id="2df72-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="2df72-147">Сцена</span><span class="sxs-lookup"><span data-stu-id="2df72-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="2df72-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2df72-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="2df72-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="2df72-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="2df72-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2df72-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="2df72-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="2df72-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="2df72-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2df72-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="2df72-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2df72-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="2df72-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="2df72-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="2df72-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2df72-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="2df72-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="2df72-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="2df72-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2df72-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="2df72-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2df72-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="2df72-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2df72-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="2df72-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2df72-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="2df72-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="2df72-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="2df72-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="2df72-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="2df72-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="2df72-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="2df72-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="2df72-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="2df72-165">На этом рисунке показана разница между физическим и логическим макетом сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="2df72-166">Слева мы видим иерархический макет данных, отображаемых приложением при перечислении сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="2df72-167">Справа видно, что сцена состоит из 12 отдельных компонентов, доступных по отдельности.</span><span class="sxs-lookup"><span data-stu-id="2df72-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="2df72-168">При обработке новой сцены мы предполагаем, что приложения будут логически проходить эту иерархию, однако при отслеживании обновлений сцены некоторые приложения могут заинтересовать только те компоненты, которые являются общими для двух сцен.</span><span class="sxs-lookup"><span data-stu-id="2df72-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="2df72-169">Обзор API</span><span class="sxs-lookup"><span data-stu-id="2df72-169">API overview</span></span>

<span data-ttu-id="2df72-170">В следующем разделе представлен общий обзор конструкций в представлении сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="2df72-171">В этом разделе вы узнаете, как представлено представление сцены, а также о том, для чего используются различные компоненты.</span><span class="sxs-lookup"><span data-stu-id="2df72-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="2df72-172">В следующем разделе приводятся конкретные примеры кода и дополнительные сведения, которые будут включены в этот обзор.</span><span class="sxs-lookup"><span data-stu-id="2df72-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="2df72-173">Все приведенные ниже типы находятся в `Microsoft.MixedReality.SceneUnderstanding` пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="2df72-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="2df72-174">сценекомпонентс</span><span class="sxs-lookup"><span data-stu-id="2df72-174">SceneComponents</span></span>

<span data-ttu-id="2df72-175">Теперь, когда вы понимаете логическую структуру сцен, теперь можно представить концепцию Сценекомпонентс и то, как они используются для создания иерархии.</span><span class="sxs-lookup"><span data-stu-id="2df72-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="2df72-176">Сценекомпонентс — это наиболее детализированные декомпозиции в Сценеундерстандинг, представляющие одну основную вещь, например сетку или четырехъядерный прямоугольник.</span><span class="sxs-lookup"><span data-stu-id="2df72-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="2df72-177">Сценекомпонентс — это вещи, которые могут обновляться независимо друг от друга и на которые могут ссылаться другие Сценекомпонентс, поэтому у них есть одно глобальное свойство с уникальным ИДЕНТИФИКАТОРом, разрешающее этот тип механизма отслеживания и создания ссылок.</span><span class="sxs-lookup"><span data-stu-id="2df72-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="2df72-178">Идентификаторы используются для логической композиции иерархии сцены, а также для сохранения объектов (действия по обновлению одной сцены относительно другой).</span><span class="sxs-lookup"><span data-stu-id="2df72-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="2df72-179">Если вы обрабатываете все недавно вычисленные сцены как отличающиеся и просто перечисляете все данные внутри него, идентификаторы в значительной степени прозрачны.</span><span class="sxs-lookup"><span data-stu-id="2df72-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="2df72-180">Однако если вы планируете отслеживание компонентов по нескольким обновлениям, вы будете использовать идентификаторы для индексирования и поиска Сценекомпонентс между объектами сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="2df72-181">сценеобжектс</span><span class="sxs-lookup"><span data-stu-id="2df72-181">SceneObjects</span></span>

<span data-ttu-id="2df72-182">Сценеобжект — это Сценекомпонент, представляющий экземпляр "вещи", например стены, этаж, потолк и т. д. выражается по свойству Kind.</span><span class="sxs-lookup"><span data-stu-id="2df72-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="2df72-183">Сценеобжектс являются геометрическими и, следовательно, имеют функции и свойства, представляющие их расположение в пространстве, однако они не содержат геометрическую или логическую структуру.</span><span class="sxs-lookup"><span data-stu-id="2df72-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="2df72-184">Вместо этого Сценеобжектс ссылаться на другие Сценекомпонентс, в частности Сценекуадс и Сценемешес, которые предоставляют различные представления, поддерживаемые системой.</span><span class="sxs-lookup"><span data-stu-id="2df72-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="2df72-185">При вычислении новой сцены приложение, скорее всего, будет перечислять Сценеобжектс сцены, чтобы обработать его интерес.</span><span class="sxs-lookup"><span data-stu-id="2df72-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="2df72-186">Сценеобжектс может иметь одно из следующих:</span><span class="sxs-lookup"><span data-stu-id="2df72-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="2df72-187">сценеобжекткинд</span><span class="sxs-lookup"><span data-stu-id="2df72-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="2df72-188">Описание</span><span class="sxs-lookup"><span data-stu-id="2df72-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="2df72-189">Историческая справка</span><span class="sxs-lookup"><span data-stu-id="2df72-189">Background</span></span></td><td><span data-ttu-id="2df72-190">Известно, что Сценеобжект <b>не</b> является одним из других распознаваемых видов объекта сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="2df72-191">Этот класс не следует путать с неизвестным, где фон может не быть стенным, этажным, вытолоком и т. д. Хотя неизвестно, еще не классифицировано.</span><span class="sxs-lookup"><span data-stu-id="2df72-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="2df72-192">Брандмауэр</span><span class="sxs-lookup"><span data-stu-id="2df72-192">Wall</span></span></td><td><span data-ttu-id="2df72-193">Физическая стенка.</span><span class="sxs-lookup"><span data-stu-id="2df72-193">A physical wall.</span></span> <span data-ttu-id="2df72-194">Предполагается, что стены являются неперемещаемыми структурами окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="2df72-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="2df72-195">Этаж</span><span class="sxs-lookup"><span data-stu-id="2df72-195">Floor</span></span></td><td><span data-ttu-id="2df72-196">Полs — это любые поверхности, на которых может пройти один проход.</span><span class="sxs-lookup"><span data-stu-id="2df72-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="2df72-197">Примечание. лестница не является пол.</span><span class="sxs-lookup"><span data-stu-id="2df72-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="2df72-198">Кроме того, обратите внимание, что в этом этаже предполагается любая неанализируемойная поверхность и, следовательно, нет явного предположений о единственном этаже.</span><span class="sxs-lookup"><span data-stu-id="2df72-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="2df72-199">Многоуровневые структуры, пандуси и т. д. Все категории должны классифицироваться как пол.</span><span class="sxs-lookup"><span data-stu-id="2df72-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="2df72-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="2df72-200">Ceiling</span></span></td><td><span data-ttu-id="2df72-201">Верхняя поверхность комнаты.</span><span class="sxs-lookup"><span data-stu-id="2df72-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="2df72-202">Платформа</span><span class="sxs-lookup"><span data-stu-id="2df72-202">Platform</span></span></td><td><span data-ttu-id="2df72-203">Крупная плоская поверхность, на которую можно поместить голограммы.</span><span class="sxs-lookup"><span data-stu-id="2df72-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="2df72-204">Они обычно представляют таблицы, каунтертопс и другие крупные горизонтальные поверхности.</span><span class="sxs-lookup"><span data-stu-id="2df72-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="2df72-205">World</span><span class="sxs-lookup"><span data-stu-id="2df72-205">World</span></span></td><td><span data-ttu-id="2df72-206">Зарезервированная метка для геометрических данных, не зависящая от меток.</span><span class="sxs-lookup"><span data-stu-id="2df72-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="2df72-207">Сетка, созданная путем установки флага обновления Енаблеворлдмеш, будет классифицироваться как мир.</span><span class="sxs-lookup"><span data-stu-id="2df72-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="2df72-208">Неизвестно</span><span class="sxs-lookup"><span data-stu-id="2df72-208">Unknown</span></span></td><td><span data-ttu-id="2df72-209">Этот объект сцены еще не классифицирован и ему назначен тип.</span><span class="sxs-lookup"><span data-stu-id="2df72-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="2df72-210">Это не следует путать с фоном, так как этот объект может быть любым, система просто не поступила с достаточной классификацией.</span><span class="sxs-lookup"><span data-stu-id="2df72-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="2df72-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="2df72-211">SceneMesh</span></span>

<span data-ttu-id="2df72-212">Сценемеш — это Сценекомпонент, который приблизительно отражает геометрию произвольных геометрических объектов с помощью списка треугольников.</span><span class="sxs-lookup"><span data-stu-id="2df72-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="2df72-213">Сценемешес используются в нескольких разных контекстах, они могут представлять компоненты структуры ячеек ватертигхт или Ворлдмеш, представляющие неограниченную сетку пространственных сопоставлений, связанную с сценой.</span><span class="sxs-lookup"><span data-stu-id="2df72-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="2df72-214">Данные индекса и вершины, предоставляемые в каждой сетке, используют тот же привычный макет, что [и буферы вершин и индексов](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , которые используются для отрисовки сеток треугольников во всех современных API-интерфейсах отрисовки.</span><span class="sxs-lookup"><span data-stu-id="2df72-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2df72-215">В понимании сцены сетки используют 32-разрядные индексы и могут быть разбиты на фрагменты для определенных механизмов визуализации.</span><span class="sxs-lookup"><span data-stu-id="2df72-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="2df72-216">Порядок поворота и системы координат</span><span class="sxs-lookup"><span data-stu-id="2df72-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="2df72-217">Все сетки, созданные при понимании сцены, должны возвращать сетки в Right-Handedной системе координат, используя порядок поворота по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="2df72-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="2df72-218">Примечание. сборки ОС, выпущенные до. 191105, могут иметь известную ошибку, когда "мировые" сетки возвращались в Counter-Clockwise порядке обмотки, которая впоследствии была исправлена.</span><span class="sxs-lookup"><span data-stu-id="2df72-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="2df72-219">сценекуад</span><span class="sxs-lookup"><span data-stu-id="2df72-219">SceneQuad</span></span>

<span data-ttu-id="2df72-220">Сценекуад — это Сценекомпонент, представляющий двумерные поверхности, занимающие трехмерный мир.</span><span class="sxs-lookup"><span data-stu-id="2df72-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="2df72-221">Сценекуадс можно использовать аналогично ARKit Арпланеанчор или Аркоре плоскости, но они предлагают более высокоуровневые функции в виде двумерных холстов для использования в неструктурированных приложениях или дополненного UX.</span><span class="sxs-lookup"><span data-stu-id="2df72-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="2df72-222">для четырех массивов предусмотрены двумерные API, которые делают размещение и разметку простыми в использовании, а разработка (за исключением отрисовки) с четырьмя областями должна быть более похожей на работу с плоскими холстами, чем с трехмерными сетками.</span><span class="sxs-lookup"><span data-stu-id="2df72-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="2df72-223">Сценекуад, фигура</span><span class="sxs-lookup"><span data-stu-id="2df72-223">SceneQuad shape</span></span>

<span data-ttu-id="2df72-224">Сценекуадс определить ограниченную прямоугольную поверхность в 2D.</span><span class="sxs-lookup"><span data-stu-id="2df72-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="2df72-225">Однако Сценекуадс представляют поверхности с произвольными и потенциально сложными фигурами (например, с помощью кольцевой таблицы). Чтобы представить сложную форму, вы можете использовать API Жетсурфацемаск, чтобы отобразить форму поверхности в буфере изображения, который вы задаете.</span><span class="sxs-lookup"><span data-stu-id="2df72-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="2df72-226">Если Сценеобжект, у которых имеется четырехъядерный объект, также есть сетка, то треугольники сетки должны быть эквивалентны этому визуализированному изображению. они представляют реальную геометрию поверхности в виде 2D-или трехмерных координат.</span><span class="sxs-lookup"><span data-stu-id="2df72-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="2df72-227">Сцены сведения о пакете SDK и справочнике</span><span class="sxs-lookup"><span data-stu-id="2df72-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="2df72-228">Следующий раздел поможет вам ознакомиться с основами Сценеундерстандинг.</span><span class="sxs-lookup"><span data-stu-id="2df72-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="2df72-229">В этом разделе приводятся основные сведения, в которых вы должны получить достаточно контекста для просмотра примеров приложений, чтобы увидеть, как Сценеундерстандинг используется глобально.</span><span class="sxs-lookup"><span data-stu-id="2df72-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="2df72-230">Инициализация</span><span class="sxs-lookup"><span data-stu-id="2df72-230">Initialization</span></span>

<span data-ttu-id="2df72-231">Первым шагом для работы с Сценеундерстандинг является получение ссылки на объект сцены в приложении.</span><span class="sxs-lookup"><span data-stu-id="2df72-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="2df72-232">Это можно сделать одним из двух способов: сцена может вычисляться драйвером, или существующая сцена, которая была вычислена в прошлом, может быть десериализована.</span><span class="sxs-lookup"><span data-stu-id="2df72-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="2df72-233">Последнее полезно для работы с Сценеундерстандинг во время разработки, где приложения и опыт можно быстро создавать с помощью прототипа без устройства смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2df72-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="2df72-234">Сцены вычисляются с помощью Сценеобсервер.</span><span class="sxs-lookup"><span data-stu-id="2df72-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="2df72-235">Перед созданием сцены приложение должно запросить устройство, чтобы убедиться, что оно поддерживает Сценеундерстандинг, а также запросить доступ пользователей для получения информации, которая необходима Сценеундерстандинг.</span><span class="sxs-lookup"><span data-stu-id="2df72-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="2df72-236">Если не вызывается Рекуестакцессасинк (), то Вычисление новой сцены завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="2df72-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="2df72-237">Далее мы вычислим новую сцену, которая находится в корне вокруг гарнитуры смешанной реальности и имеет 10-измерительный радиус.</span><span class="sxs-lookup"><span data-stu-id="2df72-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="2df72-238">Инициализация из данных (также известных как.</span><span class="sxs-lookup"><span data-stu-id="2df72-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="2df72-239">Путь к компьютеру)</span><span class="sxs-lookup"><span data-stu-id="2df72-239">the PC Path)</span></span>

<span data-ttu-id="2df72-240">В то время как сцены можно вычислять для прямого потребления, их также можно вычислить в сериализованной форме для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="2df72-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="2df72-241">Это было признано полезным для разработки, так как оно позволяет разработчикам работать и тестировать сцены без необходимости использования устройства.</span><span class="sxs-lookup"><span data-stu-id="2df72-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="2df72-242">Процесс сериализации сцены практически идентичен его вычислению, поэтому данные возвращаются в приложение, а не десериализуется локально с помощью пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="2df72-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="2df72-243">Вы можете выполнить десериализацию самостоятельно или сохранить его для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="2df72-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="2df72-244">Перечисление Сценеобжект</span><span class="sxs-lookup"><span data-stu-id="2df72-244">SceneObject Enumeration</span></span>

<span data-ttu-id="2df72-245">Теперь, когда приложение содержит сцену, приложение будет искать и взаимодействовать с Сценеобжектс.</span><span class="sxs-lookup"><span data-stu-id="2df72-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="2df72-246">Это делается путем обращения к свойству **сценеобжектс** :</span><span class="sxs-lookup"><span data-stu-id="2df72-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="2df72-247">Обновление компонентов и их поиск</span><span class="sxs-lookup"><span data-stu-id="2df72-247">Component update and refinding components</span></span>

<span data-ttu-id="2df72-248">Существует другая функция, которая извлекает компоненты в сцене с именем \**_финдкомпонент_* _.</span><span class="sxs-lookup"><span data-stu-id="2df72-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="2df72-249">Эта функция полезна при обновлении объектов отслеживания и их поиске в последующих сценах.</span><span class="sxs-lookup"><span data-stu-id="2df72-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="2df72-250">Следующий код вычислит новую сцену относительно предыдущей сцены, а затем найдет этаж в новой сцене.</span><span class="sxs-lookup"><span data-stu-id="2df72-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="2df72-251">Доступ к сеткам и четырем из объектов сцены</span><span class="sxs-lookup"><span data-stu-id="2df72-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="2df72-252">После обнаружения Сценеобжектс приложение, скорее всего, захочет получить доступ к данным, содержащимся в потерях или в Объединенных в них сетках.</span><span class="sxs-lookup"><span data-stu-id="2df72-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="2df72-253">Доступ к этим данным осуществляется с помощью свойств « _\*_четыре_\*_ » и « _\*_сетки_\*_ ».</span><span class="sxs-lookup"><span data-stu-id="2df72-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="2df72-254">Следующий код будет перечислять все четыре и сетки нашего объекта Floor.</span><span class="sxs-lookup"><span data-stu-id="2df72-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="2df72-255">Обратите внимание, что это Сценеобжект, который имеет преобразование относительно начала сцены.</span><span class="sxs-lookup"><span data-stu-id="2df72-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="2df72-256">Это обусловлено тем, что Сценеобжект представляет экземпляр "вещь" и размещаемые в пространстве, четыре части и сетки представляют геометрию, которая преобразуется относительно родительской.</span><span class="sxs-lookup"><span data-stu-id="2df72-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="2df72-257">Можно использовать отдельный Сценеобжектс для ссылки на один и тот же Сценемеш или Сценекуад Сценекомпонентс, и возможно, что у Сценеобжект есть более одного Сценемеш/Сценекуад.</span><span class="sxs-lookup"><span data-stu-id="2df72-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="2df72-258">Работа с преобразованиями</span><span class="sxs-lookup"><span data-stu-id="2df72-258">Dealing with Transforms</span></span>

<span data-ttu-id="2df72-259">Понимание сцены предоставило намеренную попытку выполнить согласование с традиционными представлениями трехмерной сцены при работе с преобразованиями.</span><span class="sxs-lookup"><span data-stu-id="2df72-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="2df72-260">Таким образом, каждая сцена ограничена одной системой координат, похожей на наиболее распространенные трехмерные представления среды.</span><span class="sxs-lookup"><span data-stu-id="2df72-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="2df72-261">Сценеобжектс каждый из них предоставляет свое расположение относительно этой системы координат.</span><span class="sxs-lookup"><span data-stu-id="2df72-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="2df72-262">Если ваше приложение работает с сценами, которые дотягивают ограничение на один источник, можно привязать Сценеобжектс к Спатиаланчорс или создать несколько сцен и объединить их вместе, но для простоты предполагается, что ватертигхт сцены существуют в собственном источнике, локализованном одним NodeId, определенным в сцене. Оригинспатиалграфнодеид.</span><span class="sxs-lookup"><span data-stu-id="2df72-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="2df72-263">В следующем коде Unity, например, показано, как использовать восприятие Windows и API Unity для совмещения систем координат.</span><span class="sxs-lookup"><span data-stu-id="2df72-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="2df72-264">Дополнительные сведения о получении Спатиалкурдинатесистем, которые соответствуют источнику мира Unity, см. в статьях [спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) и [спатиалграфинтероппревиев](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) . подробные сведения о API восприятия Windows и [собственные объекты смешанной реальности в Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) .</span><span class="sxs-lookup"><span data-stu-id="2df72-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="2df72-265">Каждый `SceneObject` из них имеет преобразование, которое затем применяется к этому объекту.</span><span class="sxs-lookup"><span data-stu-id="2df72-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="2df72-266">В Unity преобразуются в правильные координаты и назначаются локальные преобразования следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2df72-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="2df72-267">Четырехъядерный</span><span class="sxs-lookup"><span data-stu-id="2df72-267">Quad</span></span>

<span data-ttu-id="2df72-268">Четыре из них были разработаны для упрощения сценариев размещения и должны рассматриваться как расширения для элементов UX в двумерных холстах.</span><span class="sxs-lookup"><span data-stu-id="2df72-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="2df72-269">Хотя четыре компонента являются компонентами Сценеобжектс и могут быть визуализированы в трехмерном виде, четыре интерфейса API предполагают, что четыре структуры являются 2D-структурами.</span><span class="sxs-lookup"><span data-stu-id="2df72-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="2df72-270">Они предлагают такие сведения, как экстент, форма и предоставление API для размещения.</span><span class="sxs-lookup"><span data-stu-id="2df72-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="2df72-271">Четыре имеют прямоугольные экстенты, но они представляют собой произвольные геоповерхности.</span><span class="sxs-lookup"><span data-stu-id="2df72-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="2df72-272">Чтобы включить размещение на этих 2D-поверхностях, взаимодействующих с четырьмя трехмерными средами, можно использовать служебные программы для обеспечения этого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2df72-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="2df72-273">В настоящее время понятие сцены предоставляет две такие функции: _ *финдцентермостплацемент*\* и **жетсурфацемаск**.</span><span class="sxs-lookup"><span data-stu-id="2df72-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="2df72-274">Финдцентермостплацемент — это высокоуровневый API-интерфейс, который определяет положение, в котором можно поместить объект, и пытается найти лучшее место для объекта, гарантируя, что ограничивающий прямоугольник будет оставаться на базовой поверхности.</span><span class="sxs-lookup"><span data-stu-id="2df72-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="2df72-275">Координаты выходных данных задаются относительно четырех в ««Quad» места с верхним левым углом (x = 0, y = 0), точно так же, как и с другими типами Rect Windows.</span><span class="sxs-lookup"><span data-stu-id="2df72-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="2df72-276">Не забудьте принять это в учетную запись при работе с источниками собственных объектов.</span><span class="sxs-lookup"><span data-stu-id="2df72-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="2df72-277">В следующем примере показано, как найти центермост место и привязать голограмму к четырем.</span><span class="sxs-lookup"><span data-stu-id="2df72-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="2df72-278">Шаги 1-4 сильно зависят от конкретной платформы или реализации, но темы должны быть похожи.</span><span class="sxs-lookup"><span data-stu-id="2df72-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="2df72-279">Важно отметить, что четыре просто представляют ограниченную двухмерную плоскость, локализованную в пространстве.</span><span class="sxs-lookup"><span data-stu-id="2df72-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="2df72-280">Если ваш модуль или платформа знает, где четыре – и в корне объекты находятся относительно четырех, то голограммы будут правильно располагаться в соответствии с реальным миром.</span><span class="sxs-lookup"><span data-stu-id="2df72-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="2df72-281">Сетка</span><span class="sxs-lookup"><span data-stu-id="2df72-281">Mesh</span></span>

<span data-ttu-id="2df72-282">Сетки представляют геометрические представления объектов или сред.</span><span class="sxs-lookup"><span data-stu-id="2df72-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="2df72-283">Подобно [пространственному сопоставлению](../../design/spatial-mapping.md), индекс сетки и данные вершин, предоставляемые каждой сетке пространственных областей, используют тот же привычный макет, что и буферы вершин и индексов, которые используются для отрисовки сеток треугольников во всех современных API-интерфейсах отрисовки.</span><span class="sxs-lookup"><span data-stu-id="2df72-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2df72-284">Позиции вершин предоставляются в системе координат `Scene` .</span><span class="sxs-lookup"><span data-stu-id="2df72-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="2df72-285">Ниже перечислены конкретные API-интерфейсы, используемые для ссылки на эти данные.</span><span class="sxs-lookup"><span data-stu-id="2df72-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="2df72-286">В следующем коде приведен пример создания списка треугольников из структуры сетки.</span><span class="sxs-lookup"><span data-stu-id="2df72-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="2df72-287">Буферы индексов и вершин должны быть >= число индексов или вершин, но в противном случае можно произвольно изменять размер, допуская эффективное повторное использование памяти.</span><span class="sxs-lookup"><span data-stu-id="2df72-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="2df72-288">коллидермеш</span><span class="sxs-lookup"><span data-stu-id="2df72-288">ColliderMesh</span></span>

<span data-ttu-id="2df72-289">Объекты сцены обеспечивают доступ к сетке и данным в виде сетки через сетки и свойства Коллидермешес.</span><span class="sxs-lookup"><span data-stu-id="2df72-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="2df72-290">Эти сетки всегда будут соответствовать друг другу, то есть индекс и'с свойства "сетки" представляет ту же геометрию, что и индекс и'с свойства Коллидермешес.</span><span class="sxs-lookup"><span data-stu-id="2df72-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="2df72-291">Если среда выполнения или объект поддерживает сетчатые конфликты, гарантированно получается наименьший многоугольник, приближение с наибольшим порядковым номером, и рекомендуется использовать Коллидермешес везде, где приложение будет использовать конфликты.</span><span class="sxs-lookup"><span data-stu-id="2df72-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="2df72-292">Если система не поддерживает конфликты, объект сетки, возвращаемый в Коллидермешес, будет таким же, как и сетка, уменьшающая ограничения памяти.</span><span class="sxs-lookup"><span data-stu-id="2df72-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="2df72-293">Общие сведения о разработке с использованием сцены</span><span class="sxs-lookup"><span data-stu-id="2df72-293">Developing with scene understanding</span></span>

<span data-ttu-id="2df72-294">На этом этапе вы должны понимать основные строительные блоки сцены, посвященные среде выполнения и пакету SDK.</span><span class="sxs-lookup"><span data-stu-id="2df72-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="2df72-295">Многие возможности и сложность основаны на шаблонах доступа, взаимодействии с трехмерными платформами и средствах, которые могут быть написаны поверх этих API для выполнения более сложных задач, таких как пространственное планирование, анализ комнаты, навигация, физика и т. д.</span><span class="sxs-lookup"><span data-stu-id="2df72-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="2df72-296">Мы надеемся, что они записываются в примеры, которые будут надеяться вам в правильном направлении.</span><span class="sxs-lookup"><span data-stu-id="2df72-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="2df72-297">Если есть примеры или сценарии, которые мы не будем адресовать, сообщите нам, и мы попытаемся попытаться документировать или обменять нужные объекты.</span><span class="sxs-lookup"><span data-stu-id="2df72-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="2df72-298">Где можно получить пример кода?</span><span class="sxs-lookup"><span data-stu-id="2df72-298">Where can I get sample code?</span></span>

<span data-ttu-id="2df72-299">Пример кода для Unity, посвященный примеру, можно найти на странице [образца страницы Unity](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="2df72-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="2df72-300">Это приложение позволит вам взаимодействовать с устройством и визуализировать различные объекты сцены, или же оно позволит загрузить сериализованный монтажный кадр на ПК и позволит вам работать с сценами без устройства.</span><span class="sxs-lookup"><span data-stu-id="2df72-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="2df72-301">Где можно получить образцы сцен?</span><span class="sxs-lookup"><span data-stu-id="2df72-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="2df72-302">Если у вас есть HoloLens2, можно сохранить любую сцену, которая была захвачена, сохранив выходные данные Компутесериализедасинк в файл и десериализовать ее в удобном для вас виде.</span><span class="sxs-lookup"><span data-stu-id="2df72-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="2df72-303">Если у вас нет устройства HoloLens2, но вы хотите играть со сведениями о сцене, вам потребуется скачать предварительно сохраненную сцену.</span><span class="sxs-lookup"><span data-stu-id="2df72-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="2df72-304">В настоящее время пример использования сцены поставляются с серийными монтажными кадрами, которые можно скачать и использовать для удобства.</span><span class="sxs-lookup"><span data-stu-id="2df72-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="2df72-305">Их можно найти здесь:</span><span class="sxs-lookup"><span data-stu-id="2df72-305">You can find them here:</span></span>

[<span data-ttu-id="2df72-306">Пример сцен для понимания сцены</span><span class="sxs-lookup"><span data-stu-id="2df72-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="2df72-307">См. также статью</span><span class="sxs-lookup"><span data-stu-id="2df72-307">See also</span></span>

* [<span data-ttu-id="2df72-308">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="2df72-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="2df72-309">Интерпретация сцены</span><span class="sxs-lookup"><span data-stu-id="2df72-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="2df72-310">Пример Unity</span><span class="sxs-lookup"><span data-stu-id="2df72-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
