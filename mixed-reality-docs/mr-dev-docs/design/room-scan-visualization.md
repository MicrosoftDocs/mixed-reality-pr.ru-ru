---
title: Визуализация при сканировании комнаты
description: Приложения, требующие пространственного сопоставления, используют устройство для получения данных со временем и между сеансами.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, шаблоны приложений, проектирование, HoloLens, Просмотр комнаты, пространственное сопоставление, сетка, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143617"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="bddb0-104">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="bddb0-104">Room scan visualization</span></span>

<span data-ttu-id="bddb0-105">Приложения, требующие пространственного сопоставления, используют устройство для получения данных со временем и между сеансами.</span><span class="sxs-lookup"><span data-stu-id="bddb0-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="bddb0-106">Полнота и качество данных сопоставления зависит от многих факторов, в том числе от количества выполнений пользователя, времени, прошедших с момента исследования, а также от того, были ли перемещены объекты, такие как мебель и двери, с тех пор, пока устройство проверило область.</span><span class="sxs-lookup"><span data-stu-id="bddb0-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="bddb0-107">Чтобы обеспечить полезные данные пространственного сопоставления, разработчики приложений имеют несколько вариантов:</span><span class="sxs-lookup"><span data-stu-id="bddb0-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="bddb0-108">Полагаться на то, что уже было собрано.</span><span class="sxs-lookup"><span data-stu-id="bddb0-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="bddb0-109">Изначально эти данные могут быть неполными.</span><span class="sxs-lookup"><span data-stu-id="bddb0-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="bddb0-110">Попросите пользователя использовать жест раскрытия для перехода на домашнюю страницу Windows Mixed Reality, а затем изучите область, которую хотите использовать для работы.</span><span class="sxs-lookup"><span data-stu-id="bddb0-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="bddb0-111">Они могут использовать воздушное касание для подтверждения того, что все необходимые области известны устройству.</span><span class="sxs-lookup"><span data-stu-id="bddb0-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="bddb0-112">Создание пользовательского интерфейса для просмотра в собственном приложении.</span><span class="sxs-lookup"><span data-stu-id="bddb0-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="bddb0-113">Во всех этих случаях фактические данные, собранные во время исследования, хранятся в системе, и приложению не нужно делать это.</span><span class="sxs-lookup"><span data-stu-id="bddb0-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="bddb0-114">Если вы хотите просмотреть представление "Просмотр комнаты" в действии, ознакомьтесь с нашими [голограммами по проектированию —]() демонстрационный видеоролик о поддержке пространственных данных ниже:</span><span class="sxs-lookup"><span data-stu-id="bddb0-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="bddb0-115">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="bddb0-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bddb0-116"><strong>Компонент</strong></span><span class="sxs-lookup"><span data-stu-id="bddb0-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="bddb0-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bddb0-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bddb0-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="bddb0-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bddb0-119">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="bddb0-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="bddb0-120">✔️</span><span class="sxs-lookup"><span data-stu-id="bddb0-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="bddb0-121">Создание пользовательского интерфейса сканирования</span><span class="sxs-lookup"><span data-stu-id="bddb0-121">Building a custom scanning experience</span></span>

<span data-ttu-id="bddb0-122">Приложения могут проанализировать данные пространственного сопоставления в начале работы, чтобы определить, требуется ли пользователю выполнять дополнительные действия для улучшения его полноты и качества.</span><span class="sxs-lookup"><span data-stu-id="bddb0-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="bddb0-123">Если анализ означает, что качество следует улучшить, разработчики должны предоставить визуализацию для наложения на мир, чтобы указать:</span><span class="sxs-lookup"><span data-stu-id="bddb0-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="bddb0-124">Какая часть общего объема в области пользователей должна быть частью работы</span><span class="sxs-lookup"><span data-stu-id="bddb0-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="bddb0-125">Где пользователь должен переходить к улучшению данных</span><span class="sxs-lookup"><span data-stu-id="bddb0-125">Where the user should go to improve data</span></span>

<span data-ttu-id="bddb0-126">Пользователи не узнают, что делает «хорошее» сканирование.</span><span class="sxs-lookup"><span data-stu-id="bddb0-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="bddb0-127">Они должны отображаться или знать, что следует искать, если у них есть запрос на оценку сканирования — плоскости, расстояния от фактических стен и т. д.</span><span class="sxs-lookup"><span data-stu-id="bddb0-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="bddb0-128">Разработчик должен реализовать цикл обратной связи, включающий обновление данных пространственного сопоставления на этапе сканирования или исследования.</span><span class="sxs-lookup"><span data-stu-id="bddb0-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="bddb0-129">Во многих случаях лучше сообщить пользователю, что нужно сделать, чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="bddb0-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="bddb0-130">Например, Взгляните на потолк, Взгляните на мебель и т. д.</span><span class="sxs-lookup"><span data-stu-id="bddb0-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="bddb0-131">Кэшированное и непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="bddb0-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="bddb0-132">Данные пространственного сопоставления — это наиболее интенсивно используемые приложения с данными о геовесовых источниках данных.</span><span class="sxs-lookup"><span data-stu-id="bddb0-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="bddb0-133">Чтобы избежать проблем с производительностью, таких как пропущенные кадры или "дергания", следует тщательно проделать эти данные.</span><span class="sxs-lookup"><span data-stu-id="bddb0-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="bddb0-134">Активное сканирование во время работы может быть как полезным, так и негативным, поэтому необходимо решить, какой метод использовать в зависимости от опыта работы.</span><span class="sxs-lookup"><span data-stu-id="bddb0-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="bddb0-135">Кэшированное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="bddb0-135">Cached spatial mapping</span></span>

<span data-ttu-id="bddb0-136">При наличии кэшированных данных пространственного сопоставления приложение обычно создает моментальный снимок данных пространственного сопоставления и использует этот моментальный снимок во время работы.</span><span class="sxs-lookup"><span data-stu-id="bddb0-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="bddb0-137">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="bddb0-137">**Benefits**</span></span>
* <span data-ttu-id="bddb0-138">Снижение затрат на систему в ходе работы, что повышает производительность, охлаждение и повышение производительности ЦП.</span><span class="sxs-lookup"><span data-stu-id="bddb0-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="bddb0-139">Более простая реализация основного интерфейса, так как она не прерывается изменениями в пространственных данных.</span><span class="sxs-lookup"><span data-stu-id="bddb0-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="bddb0-140">Однократная стоимость любой последующей обработки пространственных данных для физических, графических и других целей.</span><span class="sxs-lookup"><span data-stu-id="bddb0-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="bddb0-141">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="bddb0-141">**Drawbacks**</span></span>
* <span data-ttu-id="bddb0-142">Перемещение реальных объектов или людей не отражается в кэшированных данных.</span><span class="sxs-lookup"><span data-stu-id="bddb0-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="bddb0-143">Например, приложение может считать дверцу открытой, когда она будет закрыта.</span><span class="sxs-lookup"><span data-stu-id="bddb0-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="bddb0-144">Потенциально больше памяти приложения для поддержания кэшированной версии данных.</span><span class="sxs-lookup"><span data-stu-id="bddb0-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="bddb0-145">Хорошим вариантом для этого метода является управляемая среда или верхняя игра в виде таблицы.</span><span class="sxs-lookup"><span data-stu-id="bddb0-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="bddb0-146">Непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="bddb0-146">Continuous spatial mapping</span></span>

<span data-ttu-id="bddb0-147">Для обновления данных пространственного сопоставления некоторые приложения могут использовать для продолжения сканирования.</span><span class="sxs-lookup"><span data-stu-id="bddb0-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="bddb0-148">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="bddb0-148">**Benefits**</span></span>
* <span data-ttu-id="bddb0-149">В приложении не требуется выполнять сборку в отдельном сканировании или исследовании.</span><span class="sxs-lookup"><span data-stu-id="bddb0-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="bddb0-150">Движение реальных объектов в реальном мире может быть отражено в игре, хотя и с некоторой задержкой.</span><span class="sxs-lookup"><span data-stu-id="bddb0-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="bddb0-151">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="bddb0-151">**Drawbacks**</span></span>
* <span data-ttu-id="bddb0-152">Более высокая сложность реализации основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="bddb0-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="bddb0-153">Потенциальные издержки от дополнительной обработки графики и физикы, так как изменения должны потребовать постепенного принятия этих систем.</span><span class="sxs-lookup"><span data-stu-id="bddb0-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="bddb0-154">Более высокая мощность, тепловая нагрузка и производительность ЦП.</span><span class="sxs-lookup"><span data-stu-id="bddb0-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="bddb0-155">Хорошим вариантом для этого метода является ситуация, когда самые голограммы взаимодействуют с перемещением объектов, например с holographic автомобильом, на котором диски в этаже могут быть подняты в дверце в зависимости от того, открыт или закрыт.</span><span class="sxs-lookup"><span data-stu-id="bddb0-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="bddb0-156">См. также статью</span><span class="sxs-lookup"><span data-stu-id="bddb0-156">See also</span></span>

* [<span data-ttu-id="bddb0-157">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="bddb0-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="bddb0-158">Системы координат</span><span class="sxs-lookup"><span data-stu-id="bddb0-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="bddb0-159">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="bddb0-159">Spatial sound design</span></span>](spatial-sound-design.md)