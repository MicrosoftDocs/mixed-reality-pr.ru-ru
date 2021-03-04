---
title: Отслеживание рук в Unreal
description: Узнайте, как использовать входные данные отслеживания, а именно сетки и анимацию Live Link в нереальных приложениях смешанной реальности.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, отслеживание, неreal, нереалное ядро 4, UE4, HoloLens, HoloLens 2, Смешанная реальность, разработка, функции, документация, руководства, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: ea4ba3ad5905e899eae474e4d571585fef77c0c2
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117658"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="c8498-104">Отслеживание рук в Unreal</span><span class="sxs-lookup"><span data-stu-id="c8498-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="c8498-105">Система отслеживания руки в качестве входных данных использует Палмс и пальцы человека.</span><span class="sxs-lookup"><span data-stu-id="c8498-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="c8498-106">Данные по положению и повороту каждого пальца доступны все жесты Palm и руки.</span><span class="sxs-lookup"><span data-stu-id="c8498-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="c8498-107">Начиная с нереального 4,26, отслеживание выполняется на основе нереального подключаемого модуля Хеадмаунтеддисплай и использует общий API на всех платформах и устройствах XR.</span><span class="sxs-lookup"><span data-stu-id="c8498-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="c8498-108">Функции одинаковы для систем Windows Mixed Reality и Опенкср.</span><span class="sxs-lookup"><span data-stu-id="c8498-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="c8498-109">Рука</span><span class="sxs-lookup"><span data-stu-id="c8498-109">Hand pose</span></span>

<span data-ttu-id="c8498-110">Рука руки позволяет относить и использовать руки и пальцы пользователей в качестве входных данных, к которым можно получить доступ как в чертежах, так и в C++.</span><span class="sxs-lookup"><span data-stu-id="c8498-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="c8498-111">Нереалный API отправляет данные в виде системы координат с тактами, синхронизированными с нереальным механизмом.</span><span class="sxs-lookup"><span data-stu-id="c8498-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![Схема руки](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="c8498-113">Анимация прямой связи</span><span class="sxs-lookup"><span data-stu-id="c8498-113">Hand Live Link Animation</span></span>

<span data-ttu-id="c8498-114">Руки, доступные для анимации, используют [подключаемый модуль динамической компоновки](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="c8498-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="c8498-115">Если включены подключаемые модули Windows Mixed Reality и Live links:</span><span class="sxs-lookup"><span data-stu-id="c8498-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="c8498-116">Выберите **окно > активная ссылка** , чтобы открыть окно редактора динамической связи.</span><span class="sxs-lookup"><span data-stu-id="c8498-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="c8498-117">Выбор **источника** и включение **источника отслеживания Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="c8498-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Источник прямой связи](images/unreal/live-link-source.png)

<span data-ttu-id="c8498-119">После включения источника и открытия ресурса анимации раскройте раздел " **анимация** " на вкладке " **Предварительный просмотр** ". Дополнительные параметры см. здесь.</span><span class="sxs-lookup"><span data-stu-id="c8498-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Динамическая анимация ссылки](images/unreal/live-link-animation.png)

<span data-ttu-id="c8498-121">Иерархия анимации руки такая же, как и в `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="c8498-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="c8498-122">Анимацию можно перенацелить с помощью **виндовсмикседреалитихандтраккингливелинкремапассет**:</span><span class="sxs-lookup"><span data-stu-id="c8498-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Анимация прямой связи 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="c8498-124">Он также может быть подклассом в редакторе:</span><span class="sxs-lookup"><span data-stu-id="c8498-124">It can also be subclassed in the editor:</span></span>

![Сопоставление активных ссылок](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="c8498-126">Сетка руки</span><span class="sxs-lookup"><span data-stu-id="c8498-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="c8498-127">Сетка "рука" в виде отслеживающей геометрии</span><span class="sxs-lookup"><span data-stu-id="c8498-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8498-128">Для получения сеток в качестве отслеживаемой геометрии в Опенкср необходимо вызвать **set use сетчатая сетка** с **включенной геометрией отслеживания**.</span><span class="sxs-lookup"><span data-stu-id="c8498-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="c8498-129">Чтобы включить этот режим, следует вызвать **set use сетчатая сетка** с **включенной геометрией отслеживания**:</span><span class="sxs-lookup"><span data-stu-id="c8498-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Схема начала воспроизведения подключена к параметру использовать сетку данных с включенным режимом геометрического отслеживания](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="c8498-131">Одновременное включение обоих режимов невозможно.</span><span class="sxs-lookup"><span data-stu-id="c8498-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="c8498-132">Если включить один, то другой автоматически отключается.</span><span class="sxs-lookup"><span data-stu-id="c8498-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="c8498-133">Доступ к данным сетки</span><span class="sxs-lookup"><span data-stu-id="c8498-133">Accessing Hand Mesh Data</span></span>

![Сетка руки](images/unreal/hand-mesh.png)

<span data-ttu-id="c8498-135">Прежде чем можно будет получить доступ к данным сетки данных, необходимо:</span><span class="sxs-lookup"><span data-stu-id="c8498-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="c8498-136">Выберите свой ресурс **арсессионконфиг** , разверните параметры **AR Settings-> мирового сопоставления** и установите флажок **создать данные сетки из отслеживающей геометрии**.</span><span class="sxs-lookup"><span data-stu-id="c8498-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="c8498-137">Ниже приведены параметры сетки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c8498-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="c8498-138">Использование данных сетки для перекрытия</span><span class="sxs-lookup"><span data-stu-id="c8498-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="c8498-139">Создать конфликт для данных сетки</span><span class="sxs-lookup"><span data-stu-id="c8498-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="c8498-140">Создать сетку навигации для данных сетки</span><span class="sxs-lookup"><span data-stu-id="c8498-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="c8498-141">Отображение данных сетки в каркасе — параметр отладки, показывающий созданную сетку</span><span class="sxs-lookup"><span data-stu-id="c8498-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="c8498-142">Эти значения параметров используются в качестве сетки пространственного сопоставления и по умолчанию для сетки.</span><span class="sxs-lookup"><span data-stu-id="c8498-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="c8498-143">Их можно изменить в любой момент в проекте или коде для любой сетки.</span><span class="sxs-lookup"><span data-stu-id="c8498-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="c8498-144">Справочник по API C++</span><span class="sxs-lookup"><span data-stu-id="c8498-144">C++ API Reference</span></span>
<span data-ttu-id="c8498-145">Используется `EEARObjectClassification` для поиска значений сетки в объектах, доступных для наблюдения.</span><span class="sxs-lookup"><span data-stu-id="c8498-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="c8498-146">Следующие делегаты вызываются, когда система обнаруживает любой отслеживающий объект, включая сетку типа "рука".</span><span class="sxs-lookup"><span data-stu-id="c8498-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="c8498-147">Убедитесь, что обработчики делегатов следуют сигнатуре функции ниже:</span><span class="sxs-lookup"><span data-stu-id="c8498-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="c8498-148">Доступ к данным сетки можно получить с помощью  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="c8498-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="c8498-149">Справочник по API-интерфейсам схем</span><span class="sxs-lookup"><span data-stu-id="c8498-149">Blueprint API Reference</span></span>

<span data-ttu-id="c8498-150">Для работы с сетчатыми сетками в схемах:</span><span class="sxs-lookup"><span data-stu-id="c8498-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="c8498-151">Добавление компонента **артраккабленотифи** в проект схемы</span><span class="sxs-lookup"><span data-stu-id="c8498-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Уведомление Артраккабле](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="c8498-153">Перейдите на панель **сведений** и разверните раздел **события** .</span><span class="sxs-lookup"><span data-stu-id="c8498-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![Артраккабле уведомление 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="c8498-155">Перезаписать для добавления, обновления или удаления отслеживаний геометрии со следующими узлами в графе событий:</span><span class="sxs-lookup"><span data-stu-id="c8498-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Уведомление Артраккабле](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="c8498-157">Визуализация сетки руки в Опенкср</span><span class="sxs-lookup"><span data-stu-id="c8498-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="c8498-158">Чтобы визуализировать сетку, рекомендуется использовать подключаемый модуль Ксрвисуализатион в ситуации с [подключаемым модулем Microsoft опенкср](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="c8498-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="c8498-159">Затем в редакторе схем следует использовать функцию **set use сетчатой** функции из [подключаемого модуля Microsoft опенкср](https://github.com/microsoft/Microsoft-OpenXR-Unreal) с **включенной ксрвисуализатион** в качестве параметра:</span><span class="sxs-lookup"><span data-stu-id="c8498-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Схема начала воспроизведения подключена к параметру использовать сетку руки с включенным режимом ксрвисуализатион](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="c8498-161">Для управления процессом отрисовки следует использовать **контроллер движения Render** из ксрвисуализатион:</span><span class="sxs-lookup"><span data-stu-id="c8498-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Схема получения функции данных контроллера движения, подключенной к функции контроллера движения прорисовки](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="c8498-163">Получаются такие результаты:</span><span class="sxs-lookup"><span data-stu-id="c8498-163">The result:</span></span>

![Изображение цифрового руки, наложенное на реальную человеческий рукой](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="c8498-165">Если вам нужно нечто более сложное, например рисовать сетку руки с помощью пользовательского шейдера, необходимо получить сетки в виде отслеживающей геометрии.</span><span class="sxs-lookup"><span data-stu-id="c8498-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="c8498-166">Лучи рук</span><span class="sxs-lookup"><span data-stu-id="c8498-166">Hand rays</span></span>

<span data-ttu-id="c8498-167">Функция руки работает для замкнутых взаимодействий, таких как извлечение объектов или нажатие кнопок.</span><span class="sxs-lookup"><span data-stu-id="c8498-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="c8498-168">Однако иногда требуется работать с голограммами, которые находятся далеко от пользователей.</span><span class="sxs-lookup"><span data-stu-id="c8498-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="c8498-169">Это можно сделать с помощью луча, которые можно использовать в качестве указывающих устройств как в C++, так и в чертежах.</span><span class="sxs-lookup"><span data-stu-id="c8498-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="c8498-170">Вы можете нарисовать луч от руки до дальнего времени и с помощью некоторой помощи от нереальной трассировки лучей выбрать голограмму, которая в противном случае будет недоступна.</span><span class="sxs-lookup"><span data-stu-id="c8498-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c8498-171">Поскольку все результаты всех функций изменяются каждый кадр, все они становятся вызываемыми.</span><span class="sxs-lookup"><span data-stu-id="c8498-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="c8498-172">Дополнительные сведения о чистом и нечистом или вызываемых функциях см. в статье GUID пользователя в [функциях](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="c8498-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="c8498-173">Жесты</span><span class="sxs-lookup"><span data-stu-id="c8498-173">Gestures</span></span>

<span data-ttu-id="c8498-174">HoloLens 2 отслеживает пространственные жесты, что означает, что эти жесты можно записать в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="c8498-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="c8498-175">Отслеживание жестов основано на модели подписки.</span><span class="sxs-lookup"><span data-stu-id="c8498-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="c8498-176">Используйте функцию "Настройка жестов", чтобы сообщить устройству, какие жесты необходимо отслеживанию.  Дополнительные сведения о жестах можно найти в документе [об использовании HoloLens 2](/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="c8498-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="c8498-177">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="c8498-177">Next Development Checkpoint</span></span>

<span data-ttu-id="c8498-178">Если вы следуете изложенным нами инструкциям по разработке для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="c8498-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="c8498-179">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="c8498-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8498-180">Локальные пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="c8498-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="c8498-181">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="c8498-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8498-182">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8498-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="c8498-183">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="c8498-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>