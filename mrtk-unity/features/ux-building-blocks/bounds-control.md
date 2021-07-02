---
title: Элемент управления Bounds
description: Общие сведения об элементе управления Bounds в МРТК
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, управление границами,
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176461"
---
# <a name="bounds-control"></a><span data-ttu-id="866a6-104">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="866a6-104">Bounds control</span></span>

![Элемент управления Bounds](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="866a6-106">*Баундсконтрол* — это новый компонент для поведения манипуляции, ранее обнаруженный в *BoundingBox*.</span><span class="sxs-lookup"><span data-stu-id="866a6-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="866a6-107">Элемент управления "границы" делает ряд улучшений и упрощений в программе установки и добавляет новые функции.</span><span class="sxs-lookup"><span data-stu-id="866a6-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="866a6-108">Этот компонент является заменой для ограничивающего прямоугольника, который будет устаревшим.</span><span class="sxs-lookup"><span data-stu-id="866a6-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="866a6-109">[`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl)Скрипт предоставляет базовые функциональные возможности для преобразования объектов в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="866a6-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="866a6-110">Элемент управления "границы" покажет рамку вокруг голограммы, чтобы указать, что она может взаимодействовать с.</span><span class="sxs-lookup"><span data-stu-id="866a6-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="866a6-111">Маркеры на углах и краях бокса позволяют масштабировать, поворачивать или переводить объект.</span><span class="sxs-lookup"><span data-stu-id="866a6-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="866a6-112">Элемент управления "границы" также реагирует на вводимые пользователем данные.</span><span class="sxs-lookup"><span data-stu-id="866a6-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="866a6-113">в HoloLens 2, например, элемент управления "границы" реагирует на близость пальца, предоставляя визуальную обратную связь для получения расстояния от объекта.</span><span class="sxs-lookup"><span data-stu-id="866a6-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="866a6-114">Все взаимодействия и визуальные элементы можно легко настроить.</span><span class="sxs-lookup"><span data-stu-id="866a6-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="866a6-115">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="866a6-115">Example scene</span></span>

<span data-ttu-id="866a6-116">Примеры конфигураций элементов управления границами можно найти в `BoundsControlExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="866a6-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="866a6-117">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="866a6-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="866a6-118">Целевой объект</span><span class="sxs-lookup"><span data-stu-id="866a6-118">Target object</span></span>

<span data-ttu-id="866a6-119">Это свойство указывает, какой объект будет преобразован с помощью операций управления границами.</span><span class="sxs-lookup"><span data-stu-id="866a6-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="866a6-120">Если объект не задан, по умолчанию используется объект Owner.</span><span class="sxs-lookup"><span data-stu-id="866a6-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="866a6-121">Поведение при активации</span><span class="sxs-lookup"><span data-stu-id="866a6-121">Activation behavior</span></span>

<span data-ttu-id="866a6-122">Существует несколько вариантов активации интерфейса управления границами.</span><span class="sxs-lookup"><span data-stu-id="866a6-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="866a6-123">*Активировать при запуске*: элемент управления "границы" становится видимым после запуска сцены.</span><span class="sxs-lookup"><span data-stu-id="866a6-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="866a6-124">*Активировать по сходству*: элемент управления "границы" становится видимым, когда накрывающаяся рука близко к объекту.</span><span class="sxs-lookup"><span data-stu-id="866a6-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="866a6-125">*Активировать по указателю*: элемент управления "границы" становится видимым, если он предназначен для указателя "рука-Ray".</span><span class="sxs-lookup"><span data-stu-id="866a6-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="866a6-126">*Активировать по сходству и указателю*: элемент управления "границы" становится видимым, если он предназначен для указателя типа "рука-Ray" или "руки" близко к объекту.</span><span class="sxs-lookup"><span data-stu-id="866a6-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="866a6-127">*Активировать вручную*: элемент управления "границы" не становится видимым автоматически.</span><span class="sxs-lookup"><span data-stu-id="866a6-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="866a6-128">Вы можете активировать его вручную с помощью скрипта, обратившись к свойству Баундсконтрол. Active.</span><span class="sxs-lookup"><span data-stu-id="866a6-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="866a6-129">Переопределение границ</span><span class="sxs-lookup"><span data-stu-id="866a6-129">Bounds override</span></span>

<span data-ttu-id="866a6-130">Устанавливает блочный объект для вычисления границ объекта.</span><span class="sxs-lookup"><span data-stu-id="866a6-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="866a6-131">Заполнение Box</span><span class="sxs-lookup"><span data-stu-id="866a6-131">Box padding</span></span>

<span data-ttu-id="866a6-132">Добавляет заполнение к границам, используемым для вычисления экстентов элемента управления.</span><span class="sxs-lookup"><span data-stu-id="866a6-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="866a6-133">Это влияет не только на взаимодействие, но и на визуальные элементы.</span><span class="sxs-lookup"><span data-stu-id="866a6-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="866a6-134">Плоская ось</span><span class="sxs-lookup"><span data-stu-id="866a6-134">Flatten axis</span></span>

<span data-ttu-id="866a6-135">Указывает, выровнен ли элемент управления по одной из осей, что делает его 2-мерный и запрещая манипуляцию вдоль этой оси.</span><span class="sxs-lookup"><span data-stu-id="866a6-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="866a6-136">Эта функция может использоваться для тонких объектов, таких как планшеты.</span><span class="sxs-lookup"><span data-stu-id="866a6-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="866a6-137">Если для оси выравнивания задано значение *автоматическое сведение* , скрипт автоматически выбирает ось с наименьшим экстентом в виде плоской оси.</span><span class="sxs-lookup"><span data-stu-id="866a6-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="866a6-138">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="866a6-138">Smoothing</span></span>

<span data-ttu-id="866a6-139">Раздел сглаживания позволяет настроить режим сглаживания для масштабирования и поворота элемента управления.</span><span class="sxs-lookup"><span data-stu-id="866a6-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="866a6-140">Визуальные элементы</span><span class="sxs-lookup"><span data-stu-id="866a6-140">Visuals</span></span>

<span data-ttu-id="866a6-141">Внешний вид элемента управления Bounds можно настроить, изменив одну из соответствующих конфигураций визуальных элементов.</span><span class="sxs-lookup"><span data-stu-id="866a6-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="866a6-142">Визуальные конфигурации являются связанными или встроенными объектами, поддерживающими сценарии, и более подробно описаны в [разделе объект конфигурации](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="866a6-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="866a6-143">Объекты конфигурации</span><span class="sxs-lookup"><span data-stu-id="866a6-143">Configuration Objects</span></span>

<span data-ttu-id="866a6-144">Элемент управления поставляется с набором объектов конфигурации, которые могут храниться в виде объектов, поддерживающих скрипты, и совместно использоваться разными экземплярами или Prefabs.</span><span class="sxs-lookup"><span data-stu-id="866a6-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="866a6-145">Конфигурации можно совместно использовать и связывать как отдельные файлы ресурсов с скриптами или вложенные сценарии в Prefabs.</span><span class="sxs-lookup"><span data-stu-id="866a6-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="866a6-146">Дополнительные конфигурации также можно определить непосредственно в экземпляре, не связываясь с внешним или вложенным сценарным ресурсом.</span><span class="sxs-lookup"><span data-stu-id="866a6-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="866a6-147">Инспектор элементов управления "границы" будет указывать, является ли конфигурация общей или встроенной в текущий экземпляр, отображая сообщение в инспекторе свойств.</span><span class="sxs-lookup"><span data-stu-id="866a6-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="866a6-148">Кроме того, общие экземпляры не могут быть изменены непосредственно в самом окне свойств элемента управления Bounds, но ресурс, к которому он привязан, должен быть напрямую изменили, чтобы избежать случайных изменений в общих конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="866a6-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="866a6-149">В настоящее время элемент управления "границы" предлагает параметры объектов конфигурации для следующих функций:</span><span class="sxs-lookup"><span data-stu-id="866a6-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="866a6-150">Маркеры</span><span class="sxs-lookup"><span data-stu-id="866a6-150">Handles</span></span>
  * [<span data-ttu-id="866a6-151">Маркеры масштабирования</span><span class="sxs-lookup"><span data-stu-id="866a6-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="866a6-152">Маркеры вращения</span><span class="sxs-lookup"><span data-stu-id="866a6-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="866a6-153">Маркеры перевода</span><span class="sxs-lookup"><span data-stu-id="866a6-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="866a6-154">Ссылки/каркасная схема</span><span class="sxs-lookup"><span data-stu-id="866a6-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="866a6-155">Отображение Box</span><span class="sxs-lookup"><span data-stu-id="866a6-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="866a6-156">Воздействие на близость</span><span class="sxs-lookup"><span data-stu-id="866a6-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="866a6-157">Конфигурация Box</span><span class="sxs-lookup"><span data-stu-id="866a6-157">Box configuration</span></span>

<span data-ttu-id="866a6-158">Конфигурация Box отвечает за визуализацию сплошного прямоугольника с границами, определенными через размер и заполнение поля.</span><span class="sxs-lookup"><span data-stu-id="866a6-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="866a6-159">Можно настроить следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="866a6-159">The following properties can be set up:</span></span>

* <span data-ttu-id="866a6-160">**Материал Box**: определяет материал, применяемый к отображаемому полю, когда взаимодействие не происходит.</span><span class="sxs-lookup"><span data-stu-id="866a6-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="866a6-161">Поле отображается только в том случае, если этот материал задан.</span><span class="sxs-lookup"><span data-stu-id="866a6-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="866a6-162">**Блочный материал**: материал для поля, когда пользователь взаимодействует с элементом управления, переключаясь по ближайшему или дальнему взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="866a6-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="866a6-163">**Горизонтальное отображение оси**: шкала, применяемая к полю, отображается, если одна из осей [плоская](#flatten-axis).</span><span class="sxs-lookup"><span data-stu-id="866a6-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="866a6-164">Конфигурация дескрипторов масштабирования</span><span class="sxs-lookup"><span data-stu-id="866a6-164">Scale handles configuration</span></span>

<span data-ttu-id="866a6-165">Этот ящик свойств позволяет изменять поведение и визуализацию дескрипторов масштабирования элемента управления "границы".</span><span class="sxs-lookup"><span data-stu-id="866a6-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="866a6-166">**Обработка материала**: материал, примененный к маркерам.</span><span class="sxs-lookup"><span data-stu-id="866a6-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="866a6-167">**Обрабатывающий извлеченный материал**: материал, примененный к извлеченному маркеру.</span><span class="sxs-lookup"><span data-stu-id="866a6-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="866a6-168">**Handle prefab**: необязательный prefab для маркера масштабирования.</span><span class="sxs-lookup"><span data-stu-id="866a6-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="866a6-169">Если параметр не задан, МРТК будет использовать куб по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="866a6-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="866a6-170">**Размер маркера**: размер маркера масштабирования.</span><span class="sxs-lookup"><span data-stu-id="866a6-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="866a6-171">**Дополнение к конфликту**: заполнение, добавляемое в обработчик конфликта.</span><span class="sxs-lookup"><span data-stu-id="866a6-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="866a6-172">**Рисовать модем при манипуляции**: когда активно выводит линию модема с точки зрения начала взаимодействия с текущей рукой или положением указателя.</span><span class="sxs-lookup"><span data-stu-id="866a6-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="866a6-173">**Дескрипторы игнорирования игнорируемых** файлов: Если конфликт связан здесь, дескрипторы будут игнорировать любые конфликты с этим.</span><span class="sxs-lookup"><span data-stu-id="866a6-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="866a6-174">**Обработка планшета prefab**: prefab, используемый для обработки, когда элемент управления плоский.</span><span class="sxs-lookup"><span data-stu-id="866a6-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="866a6-175">**Показывать маркеры масштабирования**: управляет видимостью дескриптора.</span><span class="sxs-lookup"><span data-stu-id="866a6-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="866a6-176">**Поведение масштабирования**: можно задать равномерное или неоднородное масштабирование.</span><span class="sxs-lookup"><span data-stu-id="866a6-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="866a6-177">Конфигурация дескрипторов вращения</span><span class="sxs-lookup"><span data-stu-id="866a6-177">Rotation handles configuration</span></span>

<span data-ttu-id="866a6-178">Эта конфигурация определяет поведение маркера поворота.</span><span class="sxs-lookup"><span data-stu-id="866a6-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="866a6-179">**Обработка материала**: материал, примененный к маркерам.</span><span class="sxs-lookup"><span data-stu-id="866a6-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="866a6-180">**Обрабатывающий извлеченный материал**: материал, примененный к извлеченному маркеру.</span><span class="sxs-lookup"><span data-stu-id="866a6-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="866a6-181">**Handle prefab**: необязательный prefab для этого маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="866a6-182">Если значение не задано, МРТК будет использовать сферу по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="866a6-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="866a6-183">**Размер маркера**: размер маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="866a6-184">**Дополнение к конфликту**: заполнение, добавляемое в обработчик конфликта.</span><span class="sxs-lookup"><span data-stu-id="866a6-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="866a6-185">**Рисовать модем при манипуляции**: когда активно выводит линию модема с точки зрения начала взаимодействия с текущей рукой или положением указателя.</span><span class="sxs-lookup"><span data-stu-id="866a6-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="866a6-186">**Дескрипторы игнорирования игнорируемых** файлов: Если конфликт связан здесь, дескрипторы будут игнорировать любые конфликты с этим.</span><span class="sxs-lookup"><span data-stu-id="866a6-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="866a6-187">**Handle prefab Type**: тип "не используется" для созданного маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="866a6-188">**Отображать маркер для x**: управляет видимостью маркера для оси x.</span><span class="sxs-lookup"><span data-stu-id="866a6-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="866a6-189">**Отобразить маркер для y**: управляет видимостью маркера для оси y.</span><span class="sxs-lookup"><span data-stu-id="866a6-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="866a6-190">**Отображать маркер для z**: управляет видимостью маркера для оси z.</span><span class="sxs-lookup"><span data-stu-id="866a6-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="866a6-191">Конфигурация дескрипторов перевода</span><span class="sxs-lookup"><span data-stu-id="866a6-191">Translation handles configuration</span></span>

<span data-ttu-id="866a6-192">Позволяет включать и настраивать дескрипторы перевода для элемента управления "границы".</span><span class="sxs-lookup"><span data-stu-id="866a6-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="866a6-193">Обратите внимание, что маркеры перевода отключены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="866a6-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="866a6-194">**Обработка материала**: материал, примененный к маркерам.</span><span class="sxs-lookup"><span data-stu-id="866a6-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="866a6-195">**Обрабатывающий извлеченный материал**: материал, примененный к извлеченному маркеру.</span><span class="sxs-lookup"><span data-stu-id="866a6-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="866a6-196">**Handle prefab**: необязательный prefab для этого маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="866a6-197">Если значение не задано, МРТК будет использовать сферу по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="866a6-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="866a6-198">**Размер маркера**: размер маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="866a6-199">**Дополнение к конфликту**: заполнение, добавляемое в обработчик конфликта.</span><span class="sxs-lookup"><span data-stu-id="866a6-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="866a6-200">**Рисовать модем при манипуляции**: когда активно выводит линию модема с точки зрения начала взаимодействия с текущей рукой или положением указателя.</span><span class="sxs-lookup"><span data-stu-id="866a6-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="866a6-201">**Дескрипторы игнорирования игнорируемых** файлов: Если конфликт связан здесь, дескрипторы будут игнорировать любые конфликты с этим.</span><span class="sxs-lookup"><span data-stu-id="866a6-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="866a6-202">**Handle prefab Type**: тип "не используется" для созданного маркера.</span><span class="sxs-lookup"><span data-stu-id="866a6-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="866a6-203">**Отображать маркер для x**: управляет видимостью маркера для оси x.</span><span class="sxs-lookup"><span data-stu-id="866a6-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="866a6-204">**Отобразить маркер для y**: управляет видимостью маркера для оси y.</span><span class="sxs-lookup"><span data-stu-id="866a6-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="866a6-205">**Отображать маркер для z**: управляет видимостью маркера для оси z.</span><span class="sxs-lookup"><span data-stu-id="866a6-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="866a6-206">Конфигурация ссылок (каркасная схема)</span><span class="sxs-lookup"><span data-stu-id="866a6-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="866a6-207">Конфигурация ссылок включает функцию каркаса элемента управления "границы".</span><span class="sxs-lookup"><span data-stu-id="866a6-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="866a6-208">Можно настроить следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="866a6-208">The following properties can be configured:</span></span>

* <span data-ttu-id="866a6-209">**Каркасный материал**: материал, примененный к сетке каркаса.</span><span class="sxs-lookup"><span data-stu-id="866a6-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="866a6-210">**Пограничные радиусы каркаса**: Толщина каркаса.</span><span class="sxs-lookup"><span data-stu-id="866a6-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="866a6-211">**Каркасная фигура**: фигура каркаса может быть либо кубической, либо цилиндрической.</span><span class="sxs-lookup"><span data-stu-id="866a6-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="866a6-212">**Показывать каркас**: управляет видимостью каркаса.</span><span class="sxs-lookup"><span data-stu-id="866a6-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="866a6-213">Конфигурация эффектов с учетом расположения</span><span class="sxs-lookup"><span data-stu-id="866a6-213">Proximity effect configuration</span></span>

<span data-ttu-id="866a6-214">Отображение и скрытие маркеров с анимацией на основе расстояния от руки.</span><span class="sxs-lookup"><span data-stu-id="866a6-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="866a6-215">Он имеет двустороннюю анимацию масштабирования.</span><span class="sxs-lookup"><span data-stu-id="866a6-215">It has two-step scaling animation.</span></span> <span data-ttu-id="866a6-216">по умолчанию задано поведение стиля HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="866a6-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="866a6-217">**Активно воздействие на близкое** использование: Включение активации с помощью маркеров с учетом расположения</span><span class="sxs-lookup"><span data-stu-id="866a6-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="866a6-218">**Средний уровень сходства объектов**: расстояние для первого шага масштабирования</span><span class="sxs-lookup"><span data-stu-id="866a6-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="866a6-219">Близкое к близкому **объекту**: расстояние для второго шага масштабирования</span><span class="sxs-lookup"><span data-stu-id="866a6-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="866a6-220">**Далеко масштаб**: значение масштаба по умолчанию для ресурса-маркера, если руки выходят за пределы диапазона взаимодействия элемента управления границ (расстояние, определенное выше с помощью "маркер среднего сходства").</span><span class="sxs-lookup"><span data-stu-id="866a6-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="866a6-221">Использовать 0 для скрытия обработчика по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="866a6-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="866a6-222">**Средняя шкала**: значение масштаба ресурса маркера, когда руки находятся в диапазоне взаимодействия элемента управления границ (расстояние, определенное выше с помощью маркера близкого сходства).</span><span class="sxs-lookup"><span data-stu-id="866a6-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="866a6-223">Чтобы отобразить нормальный размер, используйте значение 1.</span><span class="sxs-lookup"><span data-stu-id="866a6-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="866a6-224">**Закрытие шкалы**: масштабирование значения ресурса-маркера, когда руки находятся в диапазоне взаимодействия (расстояние, определенное выше с помощью маркера близкого сходства).</span><span class="sxs-lookup"><span data-stu-id="866a6-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="866a6-225">Используйте 1. x, чтобы отобразить больший размер)</span><span class="sxs-lookup"><span data-stu-id="866a6-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="866a6-226">**Существенное увеличение скорости**: оцените масштабированный объект с учетом масштаба, когда руки переходят с среднего на расстояние.</span><span class="sxs-lookup"><span data-stu-id="866a6-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="866a6-227">**Средний коэффициент роста**: оцените масштабированный масштабируемый объект, когда движение руки перемещается с среднего на близкое.</span><span class="sxs-lookup"><span data-stu-id="866a6-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="866a6-228">**Закрыть скорость роста**: оцените масштабированный масштабируемый объект, когда руки переходят от близкого к центру объектов.</span><span class="sxs-lookup"><span data-stu-id="866a6-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="866a6-229">Система ограничений</span><span class="sxs-lookup"><span data-stu-id="866a6-229">Constraint System</span></span>

<span data-ttu-id="866a6-230">Элемент управления Bounds поддерживает использование [диспетчера ограничений](constraint-manager.md) для ограничения или изменения преобразования, вращения или масштабирования при использовании дескрипторов управления границами.</span><span class="sxs-lookup"><span data-stu-id="866a6-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="866a6-231">Инспектор свойств покажет все доступные диспетчеры ограничений, присоединенные к тому же игровому объекту в раскрывающемся списке с возможностью прокрутки и выделения выбранного диспетчера ограничений.</span><span class="sxs-lookup"><span data-stu-id="866a6-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="866a6-232">События</span><span class="sxs-lookup"><span data-stu-id="866a6-232">Events</span></span>

<span data-ttu-id="866a6-233">Элемент управления Bounds предоставляет следующие события.</span><span class="sxs-lookup"><span data-stu-id="866a6-233">Bounds control provides the following events.</span></span> <span data-ttu-id="866a6-234">В этом примере эти события используются для воспроизведения звуковых отзывов.</span><span class="sxs-lookup"><span data-stu-id="866a6-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="866a6-235">**Начало** вращения: срабатывает при начале вращения.</span><span class="sxs-lookup"><span data-stu-id="866a6-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="866a6-236">**Поворот остановлен**: срабатывает при остановке вращения.</span><span class="sxs-lookup"><span data-stu-id="866a6-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="866a6-237">**Масштабирование начато**: активируется при запуске масштабирования.</span><span class="sxs-lookup"><span data-stu-id="866a6-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="866a6-238">**Масштабирование остановлено**: срабатывает при остановке масштабирования.</span><span class="sxs-lookup"><span data-stu-id="866a6-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="866a6-239">**Миграция начата**: активируется при начале перевода.</span><span class="sxs-lookup"><span data-stu-id="866a6-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="866a6-240">**Перевод остановлен**: срабатывает при остановке перевода.</span><span class="sxs-lookup"><span data-stu-id="866a6-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="866a6-241">Эластичные (экспериментальные)</span><span class="sxs-lookup"><span data-stu-id="866a6-241">Elastics (Experimental)</span></span>

<span data-ttu-id="866a6-242">Эластичные объекты можно использовать при манипуляции с объектами через элемент управления "границы".</span><span class="sxs-lookup"><span data-stu-id="866a6-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="866a6-243">Обратите внимание, что [система эластичных](../experimental/elastic-system.md) баз данных по-прежнему находится в экспериментальном состоянии.</span><span class="sxs-lookup"><span data-stu-id="866a6-243">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="866a6-244">Для включения эластичных баз данных необходимо связать существующий компонент диспетчера эластичных баз данных или создать и связать новый диспетчер эластичных баз данных с помощью `Add Elastics Manager` кнопки.</span><span class="sxs-lookup"><span data-stu-id="866a6-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="866a6-245">Стили обработчиков</span><span class="sxs-lookup"><span data-stu-id="866a6-245">Handle styles</span></span>

<span data-ttu-id="866a6-246">по умолчанию при простом назначении [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) сценария будет показан дескриптор HoloLens 1-го стиля.</span><span class="sxs-lookup"><span data-stu-id="866a6-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="866a6-247">чтобы использовать HoloLens 2 дескрипторы стилей, необходимо назначить соответствующие дескрипторы prefabs и материалы.</span><span class="sxs-lookup"><span data-stu-id="866a6-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Стили маркера управления границами 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="866a6-249">ниже приведены prefabs, материалы и значения масштабирования для маркеров управления HoloLens 2 стиля.</span><span class="sxs-lookup"><span data-stu-id="866a6-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="866a6-250">Этот пример можно найти в `BoundsControlExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="866a6-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="866a6-251">дескрипторы (программа установки для стиля HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="866a6-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="866a6-252">**Обрабатывающий материал**: баундингбоксхандлевхите.</span><span class="sxs-lookup"><span data-stu-id="866a6-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="866a6-253">**Обработано извлеченный материал**: баундингбоксхандлеблуеграббед.</span><span class="sxs-lookup"><span data-stu-id="866a6-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="866a6-254">**Маркер масштабирования prefab**: MRTK_BoundingBox_ScaleHandle. prefab</span><span class="sxs-lookup"><span data-stu-id="866a6-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="866a6-255">MRTK_BoundingBox_ScaleHandle_Slate prefab. prefab на **планшетном маркере масштабирования**.</span><span class="sxs-lookup"><span data-stu-id="866a6-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="866a6-256">**Размер маркера масштабирования**: 0,016 (1.6 cm)</span><span class="sxs-lookup"><span data-stu-id="866a6-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="866a6-257">**Коэффициент масштабирования**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)</span><span class="sxs-lookup"><span data-stu-id="866a6-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="866a6-258">**Маркер вращения prefab**: MRTK_BoundingBox_RotateHandle. prefab</span><span class="sxs-lookup"><span data-stu-id="866a6-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="866a6-259">**Размер маркера вращения**: 0,016</span><span class="sxs-lookup"><span data-stu-id="866a6-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="866a6-260">**Маркер поворота**: 0,016 (делает переданный объект, который немного превышает обработку визуального элемента)</span><span class="sxs-lookup"><span data-stu-id="866a6-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="866a6-261">Изменения преобразования с манипулятором объекта</span><span class="sxs-lookup"><span data-stu-id="866a6-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="866a6-262">Элемент управления "границы" можно использовать в сочетании с [`ObjectManipulator.cs`](object-manipulator.md) , чтобы разрешить определенные типы манипуляции (например,</span><span class="sxs-lookup"><span data-stu-id="866a6-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="866a6-263">Перемещение объекта) без использования дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="866a6-263">moving the object) without using handles.</span></span> <span data-ttu-id="866a6-264">Обработчик манипуляции поддерживает как одно, так и два действия.</span><span class="sxs-lookup"><span data-stu-id="866a6-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="866a6-265">[Отслеживание вручную](../input/hand-tracking.md) можно использовать для взаимодействия с объектом по закрытию.</span><span class="sxs-lookup"><span data-stu-id="866a6-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="866a6-266">Чтобы границы элемента управления применялись к тому же принципу, что и при их перемещении с помощью [`ObjectManipulator`](object-manipulator.md) дальнего взаимодействия, рекомендуется соединить свои события для *манипуляции, начатой* для  /  *манипуляции, которые заканчиваются* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` соответственно, как показано на снимке экрана выше.</span><span class="sxs-lookup"><span data-stu-id="866a6-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="866a6-267">Добавление и настройка элемента управления "границы" с помощью инспектора Unity</span><span class="sxs-lookup"><span data-stu-id="866a6-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="866a6-268">Добавить в объект конфликт Box</span><span class="sxs-lookup"><span data-stu-id="866a6-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="866a6-269">Назначение `BoundsControl` скрипта объекту</span><span class="sxs-lookup"><span data-stu-id="866a6-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="866a6-270">Настройка параметров, таких как методы активации (см. раздел [Свойства инспектора](#inspector-properties) ниже).</span><span class="sxs-lookup"><span data-stu-id="866a6-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="866a6-271">Используемых назначение prefabs и материалов для элемента управления "границы стиля HoloLens 2" (см. раздел [стили маркеров](#handle-styles) ниже)</span><span class="sxs-lookup"><span data-stu-id="866a6-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="866a6-272">Используйте поле *Переопределение* *целевого объекта* и границ в инспекторе, чтобы назначить определенный объект и конфликтующее значение в объекте с несколькими дочерними компонентами.</span><span class="sxs-lookup"><span data-stu-id="866a6-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Элемент управления границами](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="866a6-274">Добавление и настройка элемента управления "границы" в коде</span><span class="sxs-lookup"><span data-stu-id="866a6-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="866a6-275">Создание экземпляра куба GameObject</span><span class="sxs-lookup"><span data-stu-id="866a6-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="866a6-276">Назначение `BoundsControl` скрипта объекту с помощью функции AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="866a6-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="866a6-277">Настройка параметров либо непосредственно в элементе управления, либо с помощью одной из сценариев конфигурации (см. раздел свойства и [конфигурации](#configuration-objects) [инспектора](#inspector-properties) ниже).</span><span class="sxs-lookup"><span data-stu-id="866a6-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="866a6-278">Используемых назначьте prefabs и материалы для элемента управления с границами стиля HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="866a6-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="866a6-279">Это по-прежнему требует назначений через инспектор, так как материалы и Prefabs должны загружаться динамически.</span><span class="sxs-lookup"><span data-stu-id="866a6-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="866a6-280">Использование папки "Resources" или [шейдера Unity.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) не рекомендуется искать динамически загружаемые шейдеры, так как в среде выполнения могут отсутствовать перестановки шейдеров.</span><span class="sxs-lookup"><span data-stu-id="866a6-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="866a6-281">Пример: Установка минимума с максимальным числом ограничивающих элементов с помощью Минмаксскалеконстраинт</span><span class="sxs-lookup"><span data-stu-id="866a6-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="866a6-282">Чтобы задать минимальный и максимальный масштаб, присоедините [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) к элементу управления.</span><span class="sxs-lookup"><span data-stu-id="866a6-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="866a6-283">Поскольку элемент управления "границы" автоматически присоединяет и активирует диспетчер ограничений, Минмаксскалеконстраинт будет автоматически применен к изменениям преобразования после его присоединения и настройки.</span><span class="sxs-lookup"><span data-stu-id="866a6-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="866a6-284">Минмаксскалеконстраинт также можно использовать для установки минимального и максимального масштаба для [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="866a6-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="866a6-285">Пример: Добавление управления границами вокруг игрового объекта</span><span class="sxs-lookup"><span data-stu-id="866a6-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="866a6-286">Чтобы добавить элемент управления "границы" вокруг объекта, просто добавьте `BoundsControl` в него компонент:</span><span class="sxs-lookup"><span data-stu-id="866a6-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="866a6-287">Переход с ограничивающего прямоугольника</span><span class="sxs-lookup"><span data-stu-id="866a6-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="866a6-288">Существующие Prefabs и экземпляры, использующие [ограничивающий прямоугольник](bounding-box.md) , можно обновить до нового элемента управления "границы" через [окно миграции](../tools/migration-window.md) , которое является частью пакета средств мртк.</span><span class="sxs-lookup"><span data-stu-id="866a6-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="866a6-289">Для обновления отдельных экземпляров ограничивающего прямоугольника также существует параметр миграции в инспекторе свойств компонента.</span><span class="sxs-lookup"><span data-stu-id="866a6-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="866a6-290">См. также:</span><span class="sxs-lookup"><span data-stu-id="866a6-290">See also</span></span>

* [<span data-ttu-id="866a6-291">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="866a6-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="866a6-292">Диспетчер ограничений</span><span class="sxs-lookup"><span data-stu-id="866a6-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="866a6-293">Окно миграции</span><span class="sxs-lookup"><span data-stu-id="866a6-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="866a6-294">Система эластичных БД (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="866a6-294">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
