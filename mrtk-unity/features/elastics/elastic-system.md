---
title: Эластичная система
description: Документация, связанная с моделированием эластичных баз данных в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Еластикссистем,
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145188"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="a7358-104">Эластичная система (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="a7358-104">Elastic system (experimental)</span></span>

![Эластичная система](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="a7358-106">МРТК поставляется с системой эластичного моделирования, которая включает широкий спектр расширяемых и гибких подклассов, предлагая привязки для 4-мерных пружины, трехмерных и простых линейных систем.</span><span class="sxs-lookup"><span data-stu-id="a7358-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="a7358-107">В настоящее время следующие компоненты МРТК, поддерживающие [Диспетчер эластичных](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) баз данных, могут использовать функциональные возможности эластичных БД:</span><span class="sxs-lookup"><span data-stu-id="a7358-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="a7358-108">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="a7358-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="a7358-109">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="a7358-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="a7358-110">Диспетчер эластичных баз данных</span><span class="sxs-lookup"><span data-stu-id="a7358-110">Elastics manager</span></span>

![Эластичные System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="a7358-112">Диспетчер эластичных баз данных обрабатывает переданные преобразования и передает их в систему эластичных БД.</span><span class="sxs-lookup"><span data-stu-id="a7358-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="a7358-113">Включение эластичных баз данных для пользовательских компонентов можно выполнить двумя шагами:</span><span class="sxs-lookup"><span data-stu-id="a7358-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="a7358-114">Вызов метода Initialize в начале манипуляции, обновление системы с текущим преобразованием узла.</span><span class="sxs-lookup"><span data-stu-id="a7358-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="a7358-115">Запрос Апплихосттрансформ при каждом выполнении вычисления эластичных баз данных в обновленном целевом преобразовании.</span><span class="sxs-lookup"><span data-stu-id="a7358-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="a7358-116">Обратите внимание, что эластичные операции продолжат моделирование по окончании манипуляции (через цикл обновления диспетчера эластичных баз данных).</span><span class="sxs-lookup"><span data-stu-id="a7358-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="a7358-117">Чтобы заблокировать поведение, для параметра Автоматическое обновление эластичных баз данных [енаблиластиксупдате](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) можно задать значение false.</span><span class="sxs-lookup"><span data-stu-id="a7358-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="a7358-118">По умолчанию компонент диспетчера эластичных баз данных, добавляемый к игровому объекту, не будет включать эластичные объекты для любого типа преобразований.</span><span class="sxs-lookup"><span data-stu-id="a7358-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="a7358-119">Поле `Manipulation types using elastic feedback` должно быть включено для конкретных типов преобразования, чтобы создать конфигурацию эластичных баз данных и экстенты для выбранного типа.</span><span class="sxs-lookup"><span data-stu-id="a7358-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="a7358-120">Конфигурации эластичных БД</span><span class="sxs-lookup"><span data-stu-id="a7358-120">Elastics configurations</span></span>

<span data-ttu-id="a7358-121">Как и в случае с [конфигурациями элементов управления "границы](../ux-building-blocks/bounds-control.md#configuration-objects)", диспетчер эластичных баз данных поставляется с набором объектов конфигурации, которые могут храниться в виде объектов с поддержкой скриптов и совместно использоваться разными экземплярами или Prefabs.</span><span class="sxs-lookup"><span data-stu-id="a7358-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="a7358-122">Конфигурации можно совместно использовать и связывать как отдельные файлы ресурсов с скриптами или вложенные сценарии в Prefabs.</span><span class="sxs-lookup"><span data-stu-id="a7358-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="a7358-123">Дополнительные конфигурации также можно определить непосредственно в экземпляре, не связываясь с внешним или вложенным сценарным ресурсом.</span><span class="sxs-lookup"><span data-stu-id="a7358-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="a7358-124">Инспектор диспетчера эластичных баз данных будет указывать, является ли конфигурация общей или встроенной в текущий экземпляр, отображая сообщение в инспекторе свойств.</span><span class="sxs-lookup"><span data-stu-id="a7358-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="a7358-125">Кроме того, общие экземпляры не будут доступны для изменения непосредственно в окне свойств диспетчера эластичных баз данных, но ресурс, на который он связан, должен быть напрямую изменили, чтобы избежать случайных изменений в общих конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="a7358-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="a7358-126">Диспетчер эластичных баз данных предлагает параметры объектов конфигурации для следующих типов преобразования, каждый из которых представлен [объектом эластичной конфигурации](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="a7358-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="a7358-127">Эластичное преобразование</span><span class="sxs-lookup"><span data-stu-id="a7358-127">Translation Elastic</span></span>
- <span data-ttu-id="a7358-128">Эластичное вращение</span><span class="sxs-lookup"><span data-stu-id="a7358-128">Rotation Elastic</span></span>
- <span data-ttu-id="a7358-129">Эластичное масштабирование</span><span class="sxs-lookup"><span data-stu-id="a7358-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="a7358-130">Объект эластичной конфигурации</span><span class="sxs-lookup"><span data-stu-id="a7358-130">Elastic configuration object</span></span>

<span data-ttu-id="a7358-131">Конфигурация эластичных БД определяет свойства для системы дифференциальной гармонической осциллятори.</span><span class="sxs-lookup"><span data-stu-id="a7358-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="a7358-132">Следующие свойства можно изменить, но уже поставляются с набором значений по умолчанию в МРТК:</span><span class="sxs-lookup"><span data-stu-id="a7358-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="a7358-133">**Масса**: масса смоделированного элемента осциллятор.</span><span class="sxs-lookup"><span data-stu-id="a7358-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="a7358-134">**Хандк**: постоянная пружина.</span><span class="sxs-lookup"><span data-stu-id="a7358-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="a7358-135">**Ендк**: пружинная константа конца крепления.</span><span class="sxs-lookup"><span data-stu-id="a7358-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="a7358-136">**Снапк**: пружинная константа точки привязки.</span><span class="sxs-lookup"><span data-stu-id="a7358-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="a7358-137">**Перетащите**: коэффициент перетаскивания или затухания, пропорциональный скорости.</span><span class="sxs-lookup"><span data-stu-id="a7358-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="a7358-138">Экстенты эластичных баз данных</span><span class="sxs-lookup"><span data-stu-id="a7358-138">Elastics extents</span></span>

<span data-ttu-id="a7358-139">Параметры экстентов эластичных БД зависят от типа манипуляции.</span><span class="sxs-lookup"><span data-stu-id="a7358-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="a7358-140">Перевод и масштабирование представлены [экстентами эластичных БД](#volume-elastic-extent) и вращения, которые представлены [экстентом эластичных](#quaternion-elastic-extent)баз данных кватернион.</span><span class="sxs-lookup"><span data-stu-id="a7358-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="a7358-141">Экстент эластичных БД</span><span class="sxs-lookup"><span data-stu-id="a7358-141">Volume elastic extent</span></span>

<span data-ttu-id="a7358-142">Экстенты тома определяют трехмерное пространство, в котором можно перемещать гармонические осцилляторы.</span><span class="sxs-lookup"><span data-stu-id="a7358-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Границы растяжения эластичных томов](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="a7358-144">**Стретчбаундс**: представляет нижние границы эластичного пространства.</span><span class="sxs-lookup"><span data-stu-id="a7358-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="a7358-145">**Усебаундс**: следует ли учитывать границы растяжения системой.</span><span class="sxs-lookup"><span data-stu-id="a7358-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="a7358-146">Если значение равно true, то если текущая итерация целевой точки находится вне границ растяжения, будет применена конечная сила.</span><span class="sxs-lookup"><span data-stu-id="a7358-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="a7358-147">**Точек прикрепления**: указывает внутри пространства, к которому будет привязана система.</span><span class="sxs-lookup"><span data-stu-id="a7358-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="a7358-148">**Репеатснаппоинтс**: повторяет точки привязки до бесконечности.</span><span class="sxs-lookup"><span data-stu-id="a7358-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="a7358-149">Существующие точки привязки будут выступать в качестве модуля, в котором фактические точки привязки сопоставляются с ближайшим целым числом, кратным каждой точке привязки.</span><span class="sxs-lookup"><span data-stu-id="a7358-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="a7358-150">**Снапрадиус**: расстояние, с которого точки привязки начинают вынуждены заставлять пружину.</span><span class="sxs-lookup"><span data-stu-id="a7358-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Сетка оснастки эластичных томов](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="a7358-152">Экстент эластичных баз данных кватернион</span><span class="sxs-lookup"><span data-stu-id="a7358-152">Quaternion elastic extent</span></span>

<span data-ttu-id="a7358-153">Экстенты кватернион определяют четыре пространства вращения, в которых прокрутка гармонических осциллятор может быть свободна.</span><span class="sxs-lookup"><span data-stu-id="a7358-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Пример эластичного вращения](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="a7358-155">**Точек прикрепления**: Эйлера углы, к которым будет привязана система.</span><span class="sxs-lookup"><span data-stu-id="a7358-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="a7358-156">**Репеатснаппоинтс**: повторяет точки привязки.</span><span class="sxs-lookup"><span data-stu-id="a7358-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="a7358-157">Существующие точки привязки будут выступать в качестве модуля, в котором фактические точки привязки сопоставляются с ближайшим целым числом, кратным каждой точке привязки.</span><span class="sxs-lookup"><span data-stu-id="a7358-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="a7358-158">**Снапрадиус**: дуга — угол, с которой точки привязки начинают заставлять пружину в Эйлера градусах.</span><span class="sxs-lookup"><span data-stu-id="a7358-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="a7358-159">Пример сцены эластичных баз данных</span><span class="sxs-lookup"><span data-stu-id="a7358-159">Elastics example scene</span></span>

<span data-ttu-id="a7358-160">Примеры конфигураций эластичных баз данных можно найти в `ElasticSystemExample` сцене.</span><span class="sxs-lookup"><span data-stu-id="a7358-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Пример сцены эластичных баз данных](../images/elastics/Elastics_Example_Scene.png)
