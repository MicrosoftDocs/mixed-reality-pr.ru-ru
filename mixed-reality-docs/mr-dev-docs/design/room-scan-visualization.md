---
title: Визуализация при сканировании комнаты
description: Приложения, требующие пространственного сопоставления, используют устройство для получения данных со временем и между сеансами.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, шаблоны приложений, проектирование, HoloLens, Просмотр комнаты, пространственное сопоставление, сетка, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196409"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f494a-104">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="f494a-104">Room scan visualization</span></span>

<span data-ttu-id="f494a-105">Приложения, требующие пространственного сопоставления, используют устройство для получения данных со временем и между сеансами.</span><span class="sxs-lookup"><span data-stu-id="f494a-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="f494a-106">Полнота и качество данных сопоставления зависит от многих факторов, в том числе от количества выполнений пользователя, времени, прошедших с момента исследования, а также от того, были ли перемещены объекты, такие как мебель и двери, с тех пор, пока устройство проверило область.</span><span class="sxs-lookup"><span data-stu-id="f494a-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f494a-107">Чтобы обеспечить полезные данные пространственного сопоставления, разработчики приложений имеют несколько вариантов:</span><span class="sxs-lookup"><span data-stu-id="f494a-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f494a-108">Полагаться на то, что уже было собрано.</span><span class="sxs-lookup"><span data-stu-id="f494a-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f494a-109">Изначально эти данные могут быть неполными.</span><span class="sxs-lookup"><span data-stu-id="f494a-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f494a-110">Попросите пользователя использовать жест раскрытия для перехода на домашнюю страницу Windows Mixed Reality, а затем изучите область, которую хотите использовать для работы.</span><span class="sxs-lookup"><span data-stu-id="f494a-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f494a-111">Они могут использовать воздушное касание для подтверждения того, что все необходимые области известны устройству.</span><span class="sxs-lookup"><span data-stu-id="f494a-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f494a-112">Создание пользовательского интерфейса для просмотра в собственном приложении.</span><span class="sxs-lookup"><span data-stu-id="f494a-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f494a-113">Во всех этих случаях фактические данные, собранные во время исследования, хранятся в системе, и приложению не нужно делать это.</span><span class="sxs-lookup"><span data-stu-id="f494a-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="f494a-114">Если вы хотите просмотреть представление "Просмотр комнаты" в действии, ознакомьтесь с нашими **голограммами по проектированию —** демонстрационный видеоролик о поддержке пространственных данных ниже:</span><span class="sxs-lookup"><span data-stu-id="f494a-114">If you'd like to see room scan visualization in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="f494a-115">*Это видео было взято из приложения HoloLens "Проектирование голограмм". Загрузите [и воспользуйтесь всеми возможностями.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="f494a-115">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="device-support"></a><span data-ttu-id="f494a-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="f494a-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f494a-117"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="f494a-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f494a-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f494a-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f494a-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="f494a-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f494a-120">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="f494a-120">Room scan visualization</span></span></td>
        <td><span data-ttu-id="f494a-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f494a-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f494a-122">Создание пользовательского интерфейса сканирования</span><span class="sxs-lookup"><span data-stu-id="f494a-122">Building a custom scanning experience</span></span>

<span data-ttu-id="f494a-123">Приложения могут проанализировать данные пространственного сопоставления в начале работы, чтобы определить, требуется ли пользователю выполнять дополнительные действия для улучшения его полноты и качества.</span><span class="sxs-lookup"><span data-stu-id="f494a-123">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="f494a-124">Если анализ означает, что качество следует улучшить, разработчики должны предоставить визуализацию для наложения на мир, чтобы указать:</span><span class="sxs-lookup"><span data-stu-id="f494a-124">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f494a-125">Какая часть общего объема в области пользователей должна быть частью работы</span><span class="sxs-lookup"><span data-stu-id="f494a-125">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f494a-126">Где пользователь должен переходить к улучшению данных</span><span class="sxs-lookup"><span data-stu-id="f494a-126">Where the user should go to improve data</span></span>

<span data-ttu-id="f494a-127">Пользователи не узнают, что делает «хорошее» сканирование.</span><span class="sxs-lookup"><span data-stu-id="f494a-127">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="f494a-128">Они должны отображаться или знать, что следует искать, если у них есть запрос на оценку сканирования — плоскости, расстояния от фактических стен и т. д.</span><span class="sxs-lookup"><span data-stu-id="f494a-128">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="f494a-129">Разработчик должен реализовать цикл обратной связи, включающий обновление данных пространственного сопоставления на этапе сканирования или исследования.</span><span class="sxs-lookup"><span data-stu-id="f494a-129">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f494a-130">Во многих случаях лучше сообщить пользователю, что нужно сделать, чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="f494a-130">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="f494a-131">Например, Взгляните на потолк, Взгляните на мебель и т. д.</span><span class="sxs-lookup"><span data-stu-id="f494a-131">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f494a-132">Кэшированное и непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f494a-132">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f494a-133">Данные пространственного сопоставления — это наиболее интенсивно используемые приложения с данными о геовесовых источниках данных.</span><span class="sxs-lookup"><span data-stu-id="f494a-133">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f494a-134">Чтобы избежать проблем с производительностью, таких как пропущенные кадры или "дергания", следует тщательно проделать эти данные.</span><span class="sxs-lookup"><span data-stu-id="f494a-134">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f494a-135">Активное сканирование во время работы может быть как полезным, так и негативным, поэтому необходимо решить, какой метод использовать в зависимости от опыта работы.</span><span class="sxs-lookup"><span data-stu-id="f494a-135">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f494a-136">Кэшированное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f494a-136">Cached spatial mapping</span></span>

<span data-ttu-id="f494a-137">При наличии кэшированных данных пространственного сопоставления приложение обычно создает моментальный снимок данных пространственного сопоставления и использует этот моментальный снимок во время работы.</span><span class="sxs-lookup"><span data-stu-id="f494a-137">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="f494a-138">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="f494a-138">**Benefits**</span></span>
* <span data-ttu-id="f494a-139">Снижение затрат на систему в ходе работы, что повышает производительность, охлаждение и повышение производительности ЦП.</span><span class="sxs-lookup"><span data-stu-id="f494a-139">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="f494a-140">Более простая реализация основного интерфейса, так как она не прерывается изменениями в пространственных данных.</span><span class="sxs-lookup"><span data-stu-id="f494a-140">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f494a-141">Однократная стоимость любой последующей обработки пространственных данных для физических, графических и других целей.</span><span class="sxs-lookup"><span data-stu-id="f494a-141">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="f494a-142">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="f494a-142">**Drawbacks**</span></span>
* <span data-ttu-id="f494a-143">Перемещение реальных объектов или людей не отражается в кэшированных данных.</span><span class="sxs-lookup"><span data-stu-id="f494a-143">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f494a-144">Например, приложение может считать дверцу открытой, когда она будет закрыта.</span><span class="sxs-lookup"><span data-stu-id="f494a-144">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="f494a-145">Потенциально больше памяти приложения для поддержания кэшированной версии данных.</span><span class="sxs-lookup"><span data-stu-id="f494a-145">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f494a-146">Хорошим вариантом для этого метода является управляемая среда или верхняя игра в виде таблицы.</span><span class="sxs-lookup"><span data-stu-id="f494a-146">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f494a-147">Непрерывное пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f494a-147">Continuous spatial mapping</span></span>

<span data-ttu-id="f494a-148">Для обновления данных пространственного сопоставления некоторые приложения могут использовать для продолжения сканирования.</span><span class="sxs-lookup"><span data-stu-id="f494a-148">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f494a-149">**Преимущества**</span><span class="sxs-lookup"><span data-stu-id="f494a-149">**Benefits**</span></span>
* <span data-ttu-id="f494a-150">В приложении не требуется выполнять сборку в отдельном сканировании или исследовании.</span><span class="sxs-lookup"><span data-stu-id="f494a-150">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f494a-151">Движение реальных объектов в реальном мире может быть отражено в игре, хотя и с некоторой задержкой.</span><span class="sxs-lookup"><span data-stu-id="f494a-151">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f494a-152">**Недостатки**</span><span class="sxs-lookup"><span data-stu-id="f494a-152">**Drawbacks**</span></span>
* <span data-ttu-id="f494a-153">Более высокая сложность реализации основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f494a-153">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f494a-154">Потенциальные издержки от дополнительной обработки графики и физикы, так как изменения должны потребовать постепенного принятия этих систем.</span><span class="sxs-lookup"><span data-stu-id="f494a-154">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f494a-155">Более высокая мощность, тепловая нагрузка и производительность ЦП.</span><span class="sxs-lookup"><span data-stu-id="f494a-155">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="f494a-156">Хорошим вариантом для этого метода является ситуация, когда самые голограммы взаимодействуют с перемещением объектов, например с holographic автомобильом, на котором диски в этаже могут быть подняты в дверце в зависимости от того, открыт или закрыт.</span><span class="sxs-lookup"><span data-stu-id="f494a-156">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f494a-157">См. также статью</span><span class="sxs-lookup"><span data-stu-id="f494a-157">See also</span></span>

* [<span data-ttu-id="f494a-158">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="f494a-158">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="f494a-159">Системы координат</span><span class="sxs-lookup"><span data-stu-id="f494a-159">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f494a-160">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="f494a-160">Spatial sound design</span></span>](spatial-sound-design.md)