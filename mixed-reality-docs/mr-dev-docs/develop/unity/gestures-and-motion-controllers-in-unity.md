---
title: Жесты и контроллеры движения в Unity
description: Узнайте, как выполнять действия с взглядом в Unity с помощью жестов и контроллеров движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, Unity, взгляд, входные данные
ms.openlocfilehash: 6b132e56e5d60e59fda53b95328580ed861ce75c
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638561"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="83da5-104">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="83da5-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="83da5-105">Существует два основных способа выполнения действий с вашим [взглядом в Unity](gaze-in-unity.md), [жестами](../../design/gaze-and-commit.md#composite-gestures) и [контроллерами движения](../../design/motion-controllers.md) в HoloLens и иммерсивное ХМД.</span><span class="sxs-lookup"><span data-stu-id="83da5-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="83da5-106">Доступ к данным для обоих источников пространственных данных осуществляется через одни и те же API в Unity.</span><span class="sxs-lookup"><span data-stu-id="83da5-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="83da5-107">Unity предоставляет два основных способа доступа к пространственным входным данным для Windows Mixed Reality, общих *входных и входных API-интерфейсов input.* XR, работающих в нескольких пакетах SDK для Unity, и API *интерактионманажер/GestureRecognizer* , относящийся к Windows Mixed Reality, который предоставляет полный набор пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="83da5-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="83da5-108">Таблица сопоставления кнопок и осей Unity</span><span class="sxs-lookup"><span data-stu-id="83da5-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="83da5-109">Идентификаторы кнопок и осей, приведенные в таблице ниже, поддерживаются диспетчером ввода Unity для контроллеров движения Windows Mixed Reality с помощью *входных API-интерфейсов input. OnButton и AXIS* , а столбец "Windows MR" относится к свойствам, доступным для типа *интерактионсаурцестате* .</span><span class="sxs-lookup"><span data-stu-id="83da5-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="83da5-110">Каждый из этих API подробно описан в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="83da5-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="83da5-111">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality обычно соответствует идентификаторам кнопок и осей Окулус.</span><span class="sxs-lookup"><span data-stu-id="83da5-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="83da5-112">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality отличается от сопоставлений Опенвр двумя способами:</span><span class="sxs-lookup"><span data-stu-id="83da5-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="83da5-113">Сопоставление использует идентификаторы сенсорной панели, отличающиеся от аналоговый, для поддержки контроллеров с сумбстиккс и сенсорными устройствами.</span><span class="sxs-lookup"><span data-stu-id="83da5-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="83da5-114">Сопоставление позволяет избежать перегрузки идентификаторов кнопок A и X для кнопок меню, чтобы оставить их доступными для физических кнопок АБКСИ.</span><span class="sxs-lookup"><span data-stu-id="83da5-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="83da5-115">Входные данные</span><span class="sxs-lookup"><span data-stu-id="83da5-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="83da5-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Распространенные API Unity</a></span><span class="sxs-lookup"><span data-stu-id="83da5-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="83da5-117">(Входные данные. Кнопка/ось)</span><span class="sxs-lookup"><span data-stu-id="83da5-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="83da5-118"><a href="gestures-and-motion-controllers-in-unity.md#">Входной API Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="83da5-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="83da5-119">XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="83da5-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="83da5-120">Левая рука</span><span class="sxs-lookup"><span data-stu-id="83da5-120">Left hand</span></span> </th><th> <span data-ttu-id="83da5-121">Правая рука</span><span class="sxs-lookup"><span data-stu-id="83da5-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="83da5-122">Выбрать триггер нажат</span><span class="sxs-lookup"><span data-stu-id="83da5-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="83da5-123">Ось 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="83da5-124">Ось 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="83da5-125">селектпрессед</span><span class="sxs-lookup"><span data-stu-id="83da5-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-126">Выбор триггера аналогового значения</span><span class="sxs-lookup"><span data-stu-id="83da5-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="83da5-127">Ось 9</span><span class="sxs-lookup"><span data-stu-id="83da5-127">Axis 9</span></span> </td><td> <span data-ttu-id="83da5-128">Ось 10</span><span class="sxs-lookup"><span data-stu-id="83da5-128">Axis 10</span></span> </td><td> <span data-ttu-id="83da5-129">селектпресседамаунт</span><span class="sxs-lookup"><span data-stu-id="83da5-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-130">Выделение триггера частично нажато</span><span class="sxs-lookup"><span data-stu-id="83da5-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="83da5-131">Кнопка 14 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83da5-132">Кнопка 15 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83da5-133">Селектпресседамаунт &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="83da5-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-134">Нажата кнопка меню</span><span class="sxs-lookup"><span data-stu-id="83da5-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="83da5-135">Кнопка 6 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-135">Button 6\*</span></span> </td><td> <span data-ttu-id="83da5-136">Кнопка 7 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-136">Button 7\*</span></span> </td><td> <span data-ttu-id="83da5-137">менупрессед</span><span class="sxs-lookup"><span data-stu-id="83da5-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-138">Нажата кнопка захвата</span><span class="sxs-lookup"><span data-stu-id="83da5-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="83da5-139">Ось 11 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="83da5-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="83da5-140">Кнопка 4 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83da5-141">Ось 12 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="83da5-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="83da5-142">Кнопка 5 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83da5-143">Новы</span><span class="sxs-lookup"><span data-stu-id="83da5-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-144">Аналоговый стик X <i>(слева:-1,0, справа: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="83da5-145">Ось 1</span><span class="sxs-lookup"><span data-stu-id="83da5-145">Axis 1</span></span> </td><td> <span data-ttu-id="83da5-146">Ось 4</span><span class="sxs-lookup"><span data-stu-id="83da5-146">Axis 4</span></span> </td><td> <span data-ttu-id="83da5-147">Сумбстиккпоситион. x</span><span class="sxs-lookup"><span data-stu-id="83da5-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-148">Аналоговый стик <i>по оси Y (Top:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="83da5-149">Ось 2</span><span class="sxs-lookup"><span data-stu-id="83da5-149">Axis 2</span></span> </td><td> <span data-ttu-id="83da5-150">Ось 5</span><span class="sxs-lookup"><span data-stu-id="83da5-150">Axis 5</span></span> </td><td> <span data-ttu-id="83da5-151">Сумбстиккпоситион. y</span><span class="sxs-lookup"><span data-stu-id="83da5-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-152">Нажатый аналоговый стик</span><span class="sxs-lookup"><span data-stu-id="83da5-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="83da5-153">Кнопка 8</span><span class="sxs-lookup"><span data-stu-id="83da5-153">Button 8</span></span> </td><td> <span data-ttu-id="83da5-154">Кнопка 9</span><span class="sxs-lookup"><span data-stu-id="83da5-154">Button 9</span></span> </td><td> <span data-ttu-id="83da5-155">сумбстиккпрессед</span><span class="sxs-lookup"><span data-stu-id="83da5-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-156">Сенсорная панель X <i>(слева:-1,0, справа: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="83da5-157">Ось 17 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="83da5-158">Ось 19 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="83da5-159">Таучпадпоситион. x</span><span class="sxs-lookup"><span data-stu-id="83da5-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-160">Сенсорная панель Y <i>(верхняя:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="83da5-161">Ось 18 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="83da5-162">Ось 20 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="83da5-163">Таучпадпоситион. y</span><span class="sxs-lookup"><span data-stu-id="83da5-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-164">Сенсорная панель затронута</span><span class="sxs-lookup"><span data-stu-id="83da5-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="83da5-165">Кнопка 18 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-165">Button 18\*</span></span> </td><td> <span data-ttu-id="83da5-166">Кнопка 19 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-166">Button 19\*</span></span> </td><td> <span data-ttu-id="83da5-167">таучпадтаучед</span><span class="sxs-lookup"><span data-stu-id="83da5-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-168">Сенсорная панель нажата</span><span class="sxs-lookup"><span data-stu-id="83da5-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="83da5-169">Кнопка 16 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-169">Button 16\*</span></span> </td><td> <span data-ttu-id="83da5-170">Кнопка 17 \*</span><span class="sxs-lookup"><span data-stu-id="83da5-170">Button 17\*</span></span> </td><td> <span data-ttu-id="83da5-171">таучпадпрессед</span><span class="sxs-lookup"><span data-stu-id="83da5-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-172">6DoF захват захвата или указатель</span><span class="sxs-lookup"><span data-stu-id="83da5-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="83da5-173">Только <i>захват</i> : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Инпуттраккинг. Жетлокалпоситион</a></span><span class="sxs-lookup"><span data-stu-id="83da5-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="83da5-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Инпуттраккинг. Жетлокалротатион</a></span><span class="sxs-lookup"><span data-stu-id="83da5-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="83da5-175">Передается <i>захват</i> или <i>указатель</i> в качестве аргумента: Саурцестате. саурцепосе. трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="83da5-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="83da5-176">Саурцестате. Саурцепосе. Трижетротатион</span><span class="sxs-lookup"><span data-stu-id="83da5-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="83da5-177">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="83da5-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="83da5-178"><i>Точность расположения и потери исходного кода доступны только через API-интерфейс MR</i> </span><span class="sxs-lookup"><span data-stu-id="83da5-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="83da5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">Саурцестате. Саурцепосе. Поситионаккураци</a></span><span class="sxs-lookup"><span data-stu-id="83da5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="83da5-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">Саурцестате. Properties. Саурцелоссриск</a></span><span class="sxs-lookup"><span data-stu-id="83da5-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="83da5-181">Эти идентификаторы кнопок и осей отличаются от идентификаторов, используемых Unity для Опенвр из-за конфликтов в сопоставлениях, используемых в игровых элементах управления, Окулус Touch и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="83da5-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

### <a name="using-hp-reverb-g2-controllers"></a><span data-ttu-id="83da5-182">Использование HP reverbов G2 контроллеров</span><span class="sxs-lookup"><span data-stu-id="83da5-182">Using HP Reverb G2 controllers</span></span>

<span data-ttu-id="83da5-183">При использовании контроллеров HP REVERB G2 см. приведенную ниже таблицу с идентификаторами кнопок и осей.</span><span class="sxs-lookup"><span data-stu-id="83da5-183">If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="83da5-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Входные данные</span><span class="sxs-lookup"><span data-stu-id="83da5-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input</span></span> </th><span data-ttu-id="83da5-185"><th colspan="2">Общие интерфейсы API Unity</span><span class="sxs-lookup"><span data-stu-id="83da5-185"><th colspan="2">Common Unity APIs</span></span></a><br /><span data-ttu-id="83da5-186">(Входные данные. Кнопка/ось)</span><span class="sxs-lookup"><span data-stu-id="83da5-186">(Input.GetButton/GetAxis)</span></span> </th><span data-ttu-id="83da5-187"><th rowspan="2">HP-команда G2 input API</span><span class="sxs-lookup"><span data-stu-id="83da5-187"><th rowspan="2">HP Reverb G2 Input API</span></span></a></th>
</tr><tr>
<th> <span data-ttu-id="83da5-188">Левая рука</span><span class="sxs-lookup"><span data-stu-id="83da5-188">Left hand</span></span> </th><th> <span data-ttu-id="83da5-189">Правая рука</span><span class="sxs-lookup"><span data-stu-id="83da5-189">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="83da5-190">Primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="83da5-190">Primary2DAxis</span></span> </td><td> <span data-ttu-id="83da5-191">Ось 1 (X) или ось 2 (Y)</span><span class="sxs-lookup"><span data-stu-id="83da5-191">Axis 1 (X) / Axis 2 (Y)</span></span> </td><td> <span data-ttu-id="83da5-192">Ось 4 (X) или ось 5 (Y)</span><span class="sxs-lookup"><span data-stu-id="83da5-192">Axis 4 (X) / Axis 5(Y)</span></span> </td><td> <span data-ttu-id="83da5-193">Джойстик</span><span class="sxs-lookup"><span data-stu-id="83da5-193">Thumbstick</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-194">Триггер нажат</span><span class="sxs-lookup"><span data-stu-id="83da5-194">Trigger pressed</span></span> </td><td> <span data-ttu-id="83da5-195">Ось 9</span><span class="sxs-lookup"><span data-stu-id="83da5-195">Axis 9</span></span> </td><td> <span data-ttu-id="83da5-196">Ось 10</span><span class="sxs-lookup"><span data-stu-id="83da5-196">Axis 10</span></span> </td><td> <span data-ttu-id="83da5-197">Триггер индекса</span><span class="sxs-lookup"><span data-stu-id="83da5-197">Index trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-198">Регулировки</span><span class="sxs-lookup"><span data-stu-id="83da5-198">Grip</span></span> </td><td> <span data-ttu-id="83da5-199">11D оси</span><span class="sxs-lookup"><span data-stu-id="83da5-199">Axis 11d</span></span> </td><td> <span data-ttu-id="83da5-200">Ось 12</span><span class="sxs-lookup"><span data-stu-id="83da5-200">Axis 12</span></span> </td><td> <span data-ttu-id="83da5-201">Триггер захвата</span><span class="sxs-lookup"><span data-stu-id="83da5-201">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-202">Примарибуттон нажата</span><span class="sxs-lookup"><span data-stu-id="83da5-202">PrimaryButton pressed</span></span> </td><td> <span data-ttu-id="83da5-203">Кнопка 2</span><span class="sxs-lookup"><span data-stu-id="83da5-203">Button 2</span></span> </td><td> <span data-ttu-id="83da5-204">Кнопка 0</span><span class="sxs-lookup"><span data-stu-id="83da5-204">Button 0</span></span> </td><td> <span data-ttu-id="83da5-205">Нажата кнопка меню</span><span class="sxs-lookup"><span data-stu-id="83da5-205">Menu button pressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-206">Секондарибуттон нажата</span><span class="sxs-lookup"><span data-stu-id="83da5-206">SecondaryButton pressed</span></span> </td><td> <span data-ttu-id="83da5-207">Кнопка 3</span><span class="sxs-lookup"><span data-stu-id="83da5-207">Button 3</span></span> </td><td> <span data-ttu-id="83da5-208">Кнопка 1</span><span class="sxs-lookup"><span data-stu-id="83da5-208">Button 1</span></span> </td><td> <span data-ttu-id="83da5-209">Кнопка/X</span><span class="sxs-lookup"><span data-stu-id="83da5-209">A/X button</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-210">грипбуттон</span><span class="sxs-lookup"><span data-stu-id="83da5-210">GripButton</span></span> </td><td> <span data-ttu-id="83da5-211">Кнопка 4</span><span class="sxs-lookup"><span data-stu-id="83da5-211">Button 4</span></span> </td><td> <span data-ttu-id="83da5-212">Кнопка 5</span><span class="sxs-lookup"><span data-stu-id="83da5-212">Button 5</span></span> </td><td> <span data-ttu-id="83da5-213">Триггер захвата</span><span class="sxs-lookup"><span data-stu-id="83da5-213">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-214">тригжербуттон</span><span class="sxs-lookup"><span data-stu-id="83da5-214">TriggerButton</span></span> </td><td> <span data-ttu-id="83da5-215">Кнопка 14</span><span class="sxs-lookup"><span data-stu-id="83da5-215">Button 14</span></span> </td><td> <span data-ttu-id="83da5-216">Кнопка 15</span><span class="sxs-lookup"><span data-stu-id="83da5-216">Button 15</span></span> </td><td> <span data-ttu-id="83da5-217">Триггер индекса</span><span class="sxs-lookup"><span data-stu-id="83da5-217">Index trigger</span></span></td>
</tr><tr>
</tr>
</table>


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="83da5-218">Захват захвата и указание объекта a</span><span class="sxs-lookup"><span data-stu-id="83da5-218">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="83da5-219">Windows Mixed Reality поддерживает контроллеры Motion в различных конструктивных факторах, при этом структура каждого контроллера различается в связи между положением пользователя и естественным направлением "вперед", которое приложения должны использовать для указания при подготовке к просмотру контроллера.</span><span class="sxs-lookup"><span data-stu-id="83da5-219">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="83da5-220">Для лучшего представления этих контроллеров существует два вида экземпляров, которые можно исследовать для каждого источника взаимодействия, **захвата** и **указателя** .</span><span class="sxs-lookup"><span data-stu-id="83da5-220">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose** .</span></span> <span data-ttu-id="83da5-221">Координаты захвата и указателя "указатель" выражаются всеми API Unity в глобальных координатах мира Unity.</span><span class="sxs-lookup"><span data-stu-id="83da5-221">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="83da5-222">Подзахват</span><span class="sxs-lookup"><span data-stu-id="83da5-222">Grip pose</span></span>

<span data-ttu-id="83da5-223">Подсистема **захвата** представляет собой расположение кармана от руки, обнаруженного HoloLens, или карманного компьютера, удерживающий контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="83da5-223">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="83da5-224">На современных головных телефонах подзахваты лучше использовать для отрисовки **руки пользователя** или объекта, **хранящегося в руки пользователя** , например технологий или обоймы.</span><span class="sxs-lookup"><span data-stu-id="83da5-224">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand** , such as a sword or gun.</span></span> <span data-ttu-id="83da5-225">Элемент захвата также используется при визуализации контроллера движения, так как **модель подготовки к просмотру** , предоставляемая Windows для контроллера движения, использует захват в качестве источника и центра вращения.</span><span class="sxs-lookup"><span data-stu-id="83da5-225">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="83da5-226">Захват захвата определяется в частности следующим образом:</span><span class="sxs-lookup"><span data-stu-id="83da5-226">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="83da5-227">**Позиция захвата** : Карманный центроид при удержании контроллера естественным образом настраивается влево или вправо для центрирования места внутри захвата.</span><span class="sxs-lookup"><span data-stu-id="83da5-227">The **grip position** : The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="83da5-228">В контроллере движения Windows Mixed Reality эта отправка обычно соответствует кнопке "расположить".</span><span class="sxs-lookup"><span data-stu-id="83da5-228">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="83da5-229">**Правая ось ориентации захвата** : когда вы полностью открываете руку для формирования плоской задачи с 5-пальцем, луч, обычный для вашего кармана (вперед от левого кармана, назад от правого Palm)</span><span class="sxs-lookup"><span data-stu-id="83da5-229">The **grip orientation's Right axis** : When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="83da5-230">**Прямая ось ориентации захвата** : когда вы частично закрываете руку (как при удержании контроллера), луч, который указывает на "Forward" через лампу, сформированную небегункными пальцами.</span><span class="sxs-lookup"><span data-stu-id="83da5-230">The **grip orientation's Forward axis** : When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="83da5-231">**Ось Up (вверх) для ориентации захвата** : ось Up, подразумеваемая правым и прямым определением.</span><span class="sxs-lookup"><span data-stu-id="83da5-231">The **grip orientation's Up axis** : The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="83da5-232">Доступ к захвату можно получить через API-интерфейс ввода кросс-поставщика Unity ( *[XR). Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Жетлокалпоситион/вращение* ) или через API-интерфейс Windows MR ( *Саурцестате. Саурцепосе. Трижетпоситион/вращение* , запрашивающий данные для узла **захвата** ).</span><span class="sxs-lookup"><span data-stu-id="83da5-232">You can access the grip pose through either Unity's cross-vendor input API ( *[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation* ) or through the Windows MR-specific API ( *sourceState.sourcePose.TryGetPosition/Rotation* , requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="83da5-233">Указатель a</span><span class="sxs-lookup"><span data-stu-id="83da5-233">Pointer pose</span></span>

<span data-ttu-id="83da5-234">**Указатель** a представляет кончик контроллера, указывающий на пересылку.</span><span class="sxs-lookup"><span data-stu-id="83da5-234">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="83da5-235">Предоставляемый системой указатель, который лучше использовать для райкаст при **отрисовке самой модели контроллера** .</span><span class="sxs-lookup"><span data-stu-id="83da5-235">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself** .</span></span> <span data-ttu-id="83da5-236">При визуализации какого-либо другого виртуального объекта вместо контроллера, например виртуального, следует указывать на луч, который наиболее естественным для этого виртуального объекта, например луч, который перемещается на объект модели обойм, определяемой приложением.</span><span class="sxs-lookup"><span data-stu-id="83da5-236">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="83da5-237">Так как пользователи могут видеть виртуальный объект, а не физический контроллер, указание виртуального объекта, скорее всего, будет более естественным для тех, кто использует ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="83da5-237">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="83da5-238">В настоящее время указатель a доступен в Unity только через API-интерфейс Windows MR, *саурцестате. саурцепосе. трижетпоситион/вращение* , передавая *интерактионсаурценоде. Pointer* в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="83da5-238">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation* , passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="83da5-239">Состояние отслеживания контроллера</span><span class="sxs-lookup"><span data-stu-id="83da5-239">Controller tracking state</span></span>

<span data-ttu-id="83da5-240">Как и гарнитуры, для контроллера движения Windows Mixed Reality не требуется настраивать внешние датчики отслеживания.</span><span class="sxs-lookup"><span data-stu-id="83da5-240">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="83da5-241">Вместо этого контроллеры прописываются датчиками в самой гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="83da5-241">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="83da5-242">Если пользователь перемещает контроллеры из поля зрения гарнитуры, в большинстве случаев Windows будет по прежнему вычислять позиции контроллера и предоставлять их приложению.</span><span class="sxs-lookup"><span data-stu-id="83da5-242">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="83da5-243">Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="83da5-243">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="83da5-244">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="83da5-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="83da5-245">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать при приближенной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="83da5-245">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="83da5-246">Лучший способ сделать это — попробовать.</span><span class="sxs-lookup"><span data-stu-id="83da5-246">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="83da5-247">Просмотрите это видео с примерами впечатляющих материалов, которые работают с контроллерами движения в различных состояниях отслеживания:</span><span class="sxs-lookup"><span data-stu-id="83da5-247">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="83da5-248">Явное объяснение состояния отслеживания</span><span class="sxs-lookup"><span data-stu-id="83da5-248">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="83da5-249">Приложения, которые хотят обрабатывать позиции по-разному в зависимости от состояния отслеживания, могут дополнительно проанализировать свойства в состоянии контроллера, такие как *саурцелоссриск* и *поситионаккураци* :</span><span class="sxs-lookup"><span data-stu-id="83da5-249">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy* :</span></span>

<table>
<tr>
<th> <span data-ttu-id="83da5-250">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="83da5-250">Tracking state</span></span> </th><th> <span data-ttu-id="83da5-251">саурцелоссриск</span><span class="sxs-lookup"><span data-stu-id="83da5-251">SourceLossRisk</span></span> </th><th> <span data-ttu-id="83da5-252">поситионаккураци</span><span class="sxs-lookup"><span data-stu-id="83da5-252">PositionAccuracy</span></span> </th><th> <span data-ttu-id="83da5-253">трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="83da5-253">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="83da5-254"><b>Высокая точность</b> </span><span class="sxs-lookup"><span data-stu-id="83da5-254"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-255">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-255">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-256">Высокий</span><span class="sxs-lookup"><span data-stu-id="83da5-256">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-257">true</span><span class="sxs-lookup"><span data-stu-id="83da5-257">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-258"><b>Высокая точность (при потере риска)</b> </span><span class="sxs-lookup"><span data-stu-id="83da5-258"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83da5-259">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-259">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-260">Высокий</span><span class="sxs-lookup"><span data-stu-id="83da5-260">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-261">true</span><span class="sxs-lookup"><span data-stu-id="83da5-261">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-262"><b>Приблизительная точность</b> </span><span class="sxs-lookup"><span data-stu-id="83da5-262"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83da5-263">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-263">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83da5-264">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="83da5-264">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83da5-265">true</span><span class="sxs-lookup"><span data-stu-id="83da5-265">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83da5-266"><b>Без расположения</b> </span><span class="sxs-lookup"><span data-stu-id="83da5-266"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83da5-267">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83da5-267">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83da5-268">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="83da5-268">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83da5-269">false</span><span class="sxs-lookup"><span data-stu-id="83da5-269">false</span></span></td>
</tr>
</table>

<span data-ttu-id="83da5-270">Эти состояния отслеживания контроллера движения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="83da5-270">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="83da5-271">**Высокая точность:** Хотя контроллер движения находится внутри поля зрения гарнитуры, он обычно предоставляет высокую точность на основе визуального отслеживания.</span><span class="sxs-lookup"><span data-stu-id="83da5-271">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="83da5-272">Обратите внимание, что перемещаемый контроллер, проходящий через некоторое время, выходит за пределы поля зрения, или мгновенно закрывается от датчиков гарнитуры (например, с другой стороны пользователя), будет по-прежнему возвращать большую точность в течение короткого времени, исходя из инерции отслеживания самого контроллера.</span><span class="sxs-lookup"><span data-stu-id="83da5-272">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="83da5-273">**Высокая точность (при потере риска):** Когда пользователь перемещает контроллер движения за пределы поля "гарнитура", головной телефон вскоре не сможет визуально отвести мониторинг позиции контроллера.</span><span class="sxs-lookup"><span data-stu-id="83da5-273">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="83da5-274">Приложение знает, когда контроллер достиг этой фов границы, просматривая **саурцелоссриск** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="83da5-274">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="83da5-275">На этом этапе приложение может приостановить жесты контроллера, для которых требуется устойчивый поток с очень высоким качеством.</span><span class="sxs-lookup"><span data-stu-id="83da5-275">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="83da5-276">**Приблизительная точность:** Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="83da5-276">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="83da5-277">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="83da5-277">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="83da5-278">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать в режиме обычной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="83da5-278">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="83da5-279">Приложения с более **высокими** требованиями к входным данным могут отказаться от высокой точности для **приблизительной** точности, проверив свойство **поситионаккураци** , например, чтобы предоставить пользователю более масштабная хитбокс на экранных целевых объектах в течение этого времени.</span><span class="sxs-lookup"><span data-stu-id="83da5-279">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="83da5-280">**Без расположения:** Несмотря на то, что контроллер может нормально обрабатываться в течение длительного времени, иногда система знает, что даже в данный момент не имеет смысла в положении блокировки текста.</span><span class="sxs-lookup"><span data-stu-id="83da5-280">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="83da5-281">Например, контроллер, который был только что включен, может никогда не наблюдать визуально, или же пользователь может установить контроллер, который затем забирается другим пользователем.</span><span class="sxs-lookup"><span data-stu-id="83da5-281">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="83da5-282">В это время система не будет предоставлять никакой позиции приложению, а *трижетпоситион* вернет значение false.</span><span class="sxs-lookup"><span data-stu-id="83da5-282">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="83da5-283">Общие API-интерфейсы Unity (входные или кнопки и ось)</span><span class="sxs-lookup"><span data-stu-id="83da5-283">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="83da5-284">**Пространство имен:** *UnityEngine* , *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="83da5-284">**Namespace:** *UnityEngine* , *UnityEngine.XR*</span></span><br>
<span data-ttu-id="83da5-285">**Types** : *input* , *XR. Инпуттраккинг*</span><span class="sxs-lookup"><span data-stu-id="83da5-285">**Types** : *Input* , *XR.InputTracking*</span></span>

<span data-ttu-id="83da5-286">В настоящее время Unity использует общие *входные API-интерфейсы input. Окулус и input. Axis* для предоставления входных данных для [пакета SDK для](https://docs.unity3d.com/Manual/OculusControllers.html), [пакета SDK опенвр](https://docs.unity3d.com/Manual/OpenVRControllers.html) и Windows Mixed Reality, включая руки и контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="83da5-286">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="83da5-287">Если приложение использует эти API для ввода данных, оно может легко поддерживать контроллеры движения в нескольких пакетах SDK XR, включая Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="83da5-287">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="83da5-288">Получение состояния нажатия логической кнопки</span><span class="sxs-lookup"><span data-stu-id="83da5-288">Getting a logical button's pressed state</span></span>

<span data-ttu-id="83da5-289">Чтобы использовать общие интерфейсы API ввода Unity, обычно начнем с привязки кнопок и осей к логическим именам в [диспетчере ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязывая идентификаторы кнопок или осей к каждому имени.</span><span class="sxs-lookup"><span data-stu-id="83da5-289">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="83da5-290">Затем можно написать код, ссылающийся на эту логическую кнопку или имя оси.</span><span class="sxs-lookup"><span data-stu-id="83da5-290">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="83da5-291">Например, чтобы связать кнопку триггера левого контроллера движения с действием Отправить, перейдите в меню **правка > параметры проекта > входные данные** в Unity и разверните свойства раздела отправить в разделе оси.</span><span class="sxs-lookup"><span data-stu-id="83da5-291">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="83da5-292">Измените **положительную кнопку** или свойство **положительной кнопки Alt** , чтобы прочесть **игровую кнопку 14** , например:</span><span class="sxs-lookup"><span data-stu-id="83da5-292">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14** , like this:</span></span>

<span data-ttu-id="83da5-293">![InputManager Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="83da5-293">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="83da5-294">*InputManager Unity*</span><span class="sxs-lookup"><span data-stu-id="83da5-294">*Unity InputManager*</span></span>

<span data-ttu-id="83da5-295">Затем скрипт может проверить действие отправки с помощью *input. OnButton* :</span><span class="sxs-lookup"><span data-stu-id="83da5-295">Your script can then check for the Submit action using *Input.GetButton* :</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="83da5-296">Можно добавить дополнительные логические кнопки, изменив свойство **size** в разделе **оси** .</span><span class="sxs-lookup"><span data-stu-id="83da5-296">You can add more logical buttons by changing the **Size** property under **Axes** .</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="83da5-297">Непосредственное получение состояния нажатия физической кнопки</span><span class="sxs-lookup"><span data-stu-id="83da5-297">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="83da5-298">Можно также получить доступ к кнопкам вручную по полному имени с помощью *input. GetKey* :</span><span class="sxs-lookup"><span data-stu-id="83da5-298">You can also access buttons manually by their fully-qualified name, using *Input.GetKey* :</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="83da5-299">Получение объекта руки или контроллера движения</span><span class="sxs-lookup"><span data-stu-id="83da5-299">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="83da5-300">Вы можете получить доступ к положению и повороту контроллера с помощью *XR. Инпуттраккинг* :</span><span class="sxs-lookup"><span data-stu-id="83da5-300">You can access the position and rotation of the controller, using *XR.InputTracking* :</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="83da5-301">Обратите внимание, что это представляет собой захват контроллера (где пользователь удерживает контроллер), который полезен для отрисовки технологий или оружия в руки пользователя или модели самого контроллера.</span><span class="sxs-lookup"><span data-stu-id="83da5-301">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="83da5-302">Обратите внимание, что связь между этим захватом и указателем (где накладывается кончик контроллера) может отличаться в разных контроллерах.</span><span class="sxs-lookup"><span data-stu-id="83da5-302">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="83da5-303">На данный момент доступ к элементу указателя контроллера может осуществляться только через API ввода, характерный для MR, описанный в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="83da5-303">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="83da5-304">Интерфейсы API для Windows (XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="83da5-304">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="83da5-305">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="83da5-305">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="83da5-306">**Типы** : *интерактионманажер* , *интерактионсаурцестате* , *интерактионсаурце* , *интерактионсаурцепропертиес* , *InteractionSourceKind* , *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="83da5-306">**Types** : *InteractionManager* , *InteractionSourceState* , *InteractionSource* , *InteractionSourceProperties* , *InteractionSourceKind* , *InteractionSourceLocation*</span></span>

<span data-ttu-id="83da5-307">Чтобы получить более подробные сведения о вводе-выделе Windows Mixed Reality (для HoloLens) и контроллеров движения, можно выбрать использование пространственных входных API Windows в пространстве имен *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="83da5-307">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="83da5-308">Это позволяет получить доступ к дополнительным сведениям, таким как точность расположения или тип источника, что позволяет сообщать о руки и контроллерах.</span><span class="sxs-lookup"><span data-stu-id="83da5-308">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="83da5-309">Опрос состояния движений и контроллеров движения</span><span class="sxs-lookup"><span data-stu-id="83da5-309">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="83da5-310">Вы можете опросить состояние этого кадра для каждого источника взаимодействия (вручную или контроллера движения) с помощью метода *жеткуррентреадинг* .</span><span class="sxs-lookup"><span data-stu-id="83da5-310">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="83da5-311">Каждый *интерактионсаурцестате* , который вы получаете назад, представляет источник взаимодействия на текущий момент времени.</span><span class="sxs-lookup"><span data-stu-id="83da5-311">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="83da5-312">*Интерактионсаурцестате* предоставляет такие сведения:</span><span class="sxs-lookup"><span data-stu-id="83da5-312">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="83da5-313">Какие [виды нажатия](../../design/motion-controllers.md) происходят (выбор/меню, распечатка, Сенсорная панель или аналоговый стик)</span><span class="sxs-lookup"><span data-stu-id="83da5-313">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="83da5-314">Другие данные, относящиеся к контроллерам движения, таким как координаты и/или ТОЧЕЧный стик, а также затронутое состояние</span><span class="sxs-lookup"><span data-stu-id="83da5-314">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="83da5-315">Интерактионсаурцекинд, чтобы выяснить, является ли источник рукой или контроллером движения</span><span class="sxs-lookup"><span data-stu-id="83da5-315">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="83da5-316">Опрос для перенаправляемых прогнозов отрисовки</span><span class="sxs-lookup"><span data-stu-id="83da5-316">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="83da5-317">При опросе данных об источнике взаимодействия от рук и контроллеров, получаемые вами данные будут перенаправлены на момент времени, когда фотоны этого кадра будет достигнуть глаз пользователя.</span><span class="sxs-lookup"><span data-stu-id="83da5-317">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="83da5-318">Эти перенаправленные объекты лучше использовать для **подготовки к просмотру** контроллера или удерживаемого объекта в каждом кадре.</span><span class="sxs-lookup"><span data-stu-id="83da5-318">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="83da5-319">Если вы нажимаете на контроллере любую нажатие или выпуск, это будет наиболее точным, если вы используете API событий предыстории, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="83da5-319">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="83da5-320">Вы также можете получить в этом текущем фрейме объект с прямым прогнозированием.</span><span class="sxs-lookup"><span data-stu-id="83da5-320">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="83da5-321">Как и в случае с исходной версией, это полезно для **отрисовки** курсора, хотя нацеливание на заданную клавишу или выпуск будет наиболее точным, если вы используете интерфейсы API событий с предысторией, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="83da5-321">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="83da5-322">Обработка событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="83da5-322">Handling interaction source events</span></span>

<span data-ttu-id="83da5-323">Чтобы обрабатывались входные события, происходящие с точными данными предыстории, вместо опроса можно использовать события источника взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="83da5-323">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="83da5-324">Для управления событиями источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="83da5-324">To handle interaction source events:</span></span>
* <span data-ttu-id="83da5-325">Регистрация для события ввода *интерактионманажер* .</span><span class="sxs-lookup"><span data-stu-id="83da5-325">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="83da5-326">Для каждого интересующего вас типа события взаимодействия необходимо подписываться на него.</span><span class="sxs-lookup"><span data-stu-id="83da5-326">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="83da5-327">Обработайте событие.</span><span class="sxs-lookup"><span data-stu-id="83da5-327">Handle the event.</span></span> <span data-ttu-id="83da5-328">После подписки на событие взаимодействия вы получите обратный вызов при необходимости.</span><span class="sxs-lookup"><span data-stu-id="83da5-328">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="83da5-329">В примере *саурцепрессед* это произойдет после обнаружения источника и до его освобождения или потери.</span><span class="sxs-lookup"><span data-stu-id="83da5-329">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="83da5-330">Как прерывать обработку события</span><span class="sxs-lookup"><span data-stu-id="83da5-330">How to stop handling an event</span></span>

<span data-ttu-id="83da5-331">Если вы больше не заинтересованы в событии или удаляете объект, подписанный на событие, необходимо отменить обработку события.</span><span class="sxs-lookup"><span data-stu-id="83da5-331">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="83da5-332">Чтобы прерывать обработку события, отказаться от подписки на событие.</span><span class="sxs-lookup"><span data-stu-id="83da5-332">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="83da5-333">Список событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="83da5-333">List of interaction source events</span></span>

<span data-ttu-id="83da5-334">Доступные события источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="83da5-334">The available interaction source events are:</span></span>
* <span data-ttu-id="83da5-335">*Интерактионсаурцедетектед* (источник стал активным)</span><span class="sxs-lookup"><span data-stu-id="83da5-335">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="83da5-336">*Интерактионсаурцелост* (неактивен)</span><span class="sxs-lookup"><span data-stu-id="83da5-336">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="83da5-337">*Интерактионсаурцепрессед* (TAP, нажатие кнопки или "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="83da5-337">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="83da5-338">*Интерактионсаурцерелеасед* (окончание касания, кнопка отжата или конец "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="83da5-338">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="83da5-339">*Интерактионсаурцеупдатед* (перемещение или иным образом изменяет некоторое состояние)</span><span class="sxs-lookup"><span data-stu-id="83da5-339">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="83da5-340">События для исторических целей, которые наиболее точно соответствуют нажатию или выпуску</span><span class="sxs-lookup"><span data-stu-id="83da5-340">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="83da5-341">API-интерфейсы опроса, описанные выше, предоставляют приложению перенаправление прогнозов.</span><span class="sxs-lookup"><span data-stu-id="83da5-341">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="83da5-342">Хотя эти прогнозируемые объекты лучше всего подходят для подготовки к просмотру контроллера или виртуального карманного объекта, будущие элементы не оптимальны для нацеливания, по двум основным причинам:</span><span class="sxs-lookup"><span data-stu-id="83da5-342">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="83da5-343">Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс задержки беспроводной сети через Bluetooth, прежде чем система получит нажатие.</span><span class="sxs-lookup"><span data-stu-id="83da5-343">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="83da5-344">Затем, если вы используете прямую прогнозную единицу, будет использоваться еще 10-20 мс прямого прогноза, который будет применяться к моменту, когда фотоны текущего кадра достигнет глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="83da5-344">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="83da5-345">Это означает, что опрос дает вам исходную позицию или головной элемент, который составляет 30 – 40ms вперед от того места, где головка пользователя и руки в действительности были возвращены при нажатии или выпуске.</span><span class="sxs-lookup"><span data-stu-id="83da5-345">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="83da5-346">Для входных данных HoloLens, в то время как нет задержки беспроводной передачи, существует аналогичная задержка обработки для обнаружения нажатия.</span><span class="sxs-lookup"><span data-stu-id="83da5-346">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="83da5-347">Чтобы правильно ориентироваться в зависимости от первоначальной цели пользователя или нажатия контроллера, следует использовать источник с предысторией или головной элемент из этого события ввода *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* .</span><span class="sxs-lookup"><span data-stu-id="83da5-347">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="83da5-348">Вы можете выбрать пресс или Release с предысторией данных из заголовка пользователя или контроллера:</span><span class="sxs-lookup"><span data-stu-id="83da5-348">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="83da5-349">В момент, когда произошло нажатие жеста или контроллера, эта головная программа может быть **использована для определения** того, что именно [облаками](../../design/gaze-and-commit.md) пользователь:</span><span class="sxs-lookup"><span data-stu-id="83da5-349">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="83da5-350">Исходная ошибка в момент, когда произошло нажатие кнопки контроллера движения, которое можно использовать для определения **нацеливания** пользователя на контроллер.</span><span class="sxs-lookup"><span data-stu-id="83da5-350">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="83da5-351">Это будет состояние контроллера, на котором нажимается клавиша.</span><span class="sxs-lookup"><span data-stu-id="83da5-351">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="83da5-352">Если вы создаете сам контроллер, то можете запросить объект a, а не захват, чтобы прокрутить целевой луч от того, что пользователь будет рассматривать как естественный Совет этого отображаемого контроллера:</span><span class="sxs-lookup"><span data-stu-id="83da5-352">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="83da5-353">Пример обработчиков событий</span><span class="sxs-lookup"><span data-stu-id="83da5-353">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="83da5-354">Интерфейсы API составных жестов высокого уровня (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="83da5-354">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="83da5-355">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="83da5-355">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="83da5-356">**Типы** : *GestureRecognizer* , *жестуресеттингс* , *интерактионсаурцекинд*</span><span class="sxs-lookup"><span data-stu-id="83da5-356">**Types** : *GestureRecognizer* , *GestureSettings* , *InteractionSourceKind*</span></span>

<span data-ttu-id="83da5-357">Приложение может также распознать составные жесты более высокого уровня для пространственных источников входных данных, коснуться, удерживать, манипуляции и жесты навигации.</span><span class="sxs-lookup"><span data-stu-id="83da5-357">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="83da5-358">Эти составные жесты можно распознавать как в движении, [так и в](../../design/gaze-and-commit.md#composite-gestures) [контроллерах движения](../../design/motion-controllers.md) с помощью GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="83da5-358">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="83da5-359">Каждое событие жеста в GestureRecognizer предоставляет Саурцекинд для входных данных, а также целевой заголовочный элемент на момент события.</span><span class="sxs-lookup"><span data-stu-id="83da5-359">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="83da5-360">Некоторые события предоставляют дополнительные сведения, относящиеся к контексту.</span><span class="sxs-lookup"><span data-stu-id="83da5-360">Some events provide additional context specific information.</span></span>

<span data-ttu-id="83da5-361">Для записи жестов с помощью распознавателя жестов требуется всего несколько действий:</span><span class="sxs-lookup"><span data-stu-id="83da5-361">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="83da5-362">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-362">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="83da5-363">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="83da5-363">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="83da5-364">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-364">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="83da5-365">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-365">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="83da5-366">Создание нового распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-366">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="83da5-367">Чтобы использовать *GestureRecognizer* , необходимо создать *GestureRecognizer* :</span><span class="sxs-lookup"><span data-stu-id="83da5-367">To use the *GestureRecognizer* , you must have created a *GestureRecognizer* :</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="83da5-368">Укажите, какие жесты следует отслеживать</span><span class="sxs-lookup"><span data-stu-id="83da5-368">Specify which gestures to watch for</span></span>

<span data-ttu-id="83da5-369">Укажите, какие жесты вы хотите использовать с помощью *сетрекогнизаблежестурес ()* :</span><span class="sxs-lookup"><span data-stu-id="83da5-369">Specify which gestures you are interested in via *SetRecognizableGestures()* :</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="83da5-370">Подписываться на события для этих жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-370">Subscribe to events for those gestures</span></span>

<span data-ttu-id="83da5-371">Подпишитесь на события для интересующих вас жестов.</span><span class="sxs-lookup"><span data-stu-id="83da5-371">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="83da5-372">Жесты навигации и манипуляции являются взаимоисключающими в экземпляре *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="83da5-372">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer* .</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="83da5-373">Начать запись жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-373">Start capturing gestures</span></span>

<span data-ttu-id="83da5-374">По умолчанию *GestureRecognizer* не отслеживает входные данные до тех пор, пока не будет вызван *старткаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="83da5-374">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="83da5-375">Возможно, что событие жеста может быть создано после вызова *стопкаптурингжестурес ()* , если входные данные были выполнены до того, как был обработан *стопкаптурингжестурес ()* .</span><span class="sxs-lookup"><span data-stu-id="83da5-375">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="83da5-376">*GestureRecognizer* будет запоминать, была ли она включена или отключена во время предыдущего кадра, в котором он действительно выполнялся, и таким образом, чтобы обеспечить возможность запуска и остановки мониторинга жестов на основе целевых объектов взгляда.</span><span class="sxs-lookup"><span data-stu-id="83da5-376">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="83da5-377">Завершение записи жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-377">Stop capturing gestures</span></span>

<span data-ttu-id="83da5-378">Чтобы отключить распознавание жестов, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="83da5-378">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="83da5-379">Удаление распознавателя жестов</span><span class="sxs-lookup"><span data-stu-id="83da5-379">Removing a gesture recognizer</span></span>

<span data-ttu-id="83da5-380">Не забудьте отказаться от подписки на подписанные события перед уничтожением объекта *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="83da5-380">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="83da5-381">Подготовка модели контроллера движения к просмотру в Unity</span><span class="sxs-lookup"><span data-stu-id="83da5-381">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="83da5-382">![Модель контроллера движения и телеперенос](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="83da5-382">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="83da5-383">*Модель контроллера движения и телеперенос*</span><span class="sxs-lookup"><span data-stu-id="83da5-383">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="83da5-384">Для подготовки к просмотру в приложении контроллеров движения, соответствующих физическим контроллерам, которые хранятся и обрабатываются при нажатии различных кнопок, можно использовать **prefab мотионконтроллер** в [наборе средств Mixed Reality](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="83da5-384">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="83da5-385">Этот prefab динамически загружает правильную модель Глтф во время выполнения из установленного в системе драйвера контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="83da5-385">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="83da5-386">Важно динамически загружать эти модели, а не импортировать их вручную в редакторе, чтобы приложение показывало физически точную трехмерную модель для всех существующих и будущих контроллеров, которые могут иметь пользователи.</span><span class="sxs-lookup"><span data-stu-id="83da5-386">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="83da5-387">Следуйте инструкциям по [Начало работы](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) , чтобы скачать набор средств для смешанной реальности и добавить его в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="83da5-387">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="83da5-388">Если вы заменили камеру на *микседреалитикамерапарент* prefab в рамках начало работы действий, то можете продолжить!</span><span class="sxs-lookup"><span data-stu-id="83da5-388">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="83da5-389">Этот prefab включает визуализацию контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="83da5-389">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="83da5-390">В противном случае добавьте *Assets/холотулкит/input/Prefabs/мотионконтроллерс. prefab* в сцену из области проекта.</span><span class="sxs-lookup"><span data-stu-id="83da5-390">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="83da5-391">Вам потребуется добавить prefab в качестве дочернего объекта для того, чтобы перемещать камеру, когда у пользователя есть телепередачи в пределах сцены, чтобы контроллеры поступали вместе с пользователем.</span><span class="sxs-lookup"><span data-stu-id="83da5-391">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="83da5-392">Если ваше приложение не предусматривает телеперенос, просто добавьте prefab в корень сцены.</span><span class="sxs-lookup"><span data-stu-id="83da5-392">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="83da5-393">Создание вызывающих объектов</span><span class="sxs-lookup"><span data-stu-id="83da5-393">Throwing objects</span></span>

<span data-ttu-id="83da5-394">Создание объектов в Virtual Reality усложняется, и это может показаться на первый взгляд.</span><span class="sxs-lookup"><span data-stu-id="83da5-394">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="83da5-395">Как и в случае с наиболее частыми взаимодействиями, когда вызов в игре происходит непредвиденным образом, он немедленно становится очевидным и нарушается.</span><span class="sxs-lookup"><span data-stu-id="83da5-395">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="83da5-396">Мы тратили некоторое время на обдумывание того, как представить физически правильное поведение при вызове и получили несколько рекомендаций, включенных через обновления нашей платформы, которые мы хотели бы поделиться с вами.</span><span class="sxs-lookup"><span data-stu-id="83da5-396">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="83da5-397">Вы можете найти пример того, как мы рекомендуем реализовать [это](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)создание.</span><span class="sxs-lookup"><span data-stu-id="83da5-397">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="83da5-398">Этот пример соответствует следующим четырем рекомендациям:</span><span class="sxs-lookup"><span data-stu-id="83da5-398">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="83da5-399">**Используйте *скорость* контроллера вместо расположения** .</span><span class="sxs-lookup"><span data-stu-id="83da5-399">**Use the controller’s *velocity* instead of position** .</span></span> <span data-ttu-id="83da5-400">В ноябре-обновлении Windows мы предоставили изменение в поведении, когда в [позиционированном состоянии отслеживания "приближено](../../design/motion-controllers.md#controller-tracking-state)".</span><span class="sxs-lookup"><span data-stu-id="83da5-400">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="83da5-401">В этом состоянии информация о скорости контроллера будет по-прежнему отображаться до тех пор, пока мы считаем, что он имеет высокую точность, что часто бывает дольше, чем в положении.</span><span class="sxs-lookup"><span data-stu-id="83da5-401">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="83da5-402">**Внедрение *угловой скорости* контроллера** .</span><span class="sxs-lookup"><span data-stu-id="83da5-402">**Incorporate the *angular velocity* of the controller** .</span></span> <span data-ttu-id="83da5-403">Эта логика хранится в `throwing.cs` файле в `GetThrownObjectVelAngVel` статическом методе в связанном выше пакете.</span><span class="sxs-lookup"><span data-stu-id="83da5-403">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="83da5-404">По мере того, как угловая скорость сохраняется, создаваемый объект должен поддерживать ту же угловую скорость, что и в момент создания: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="83da5-404">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="83da5-405">Поскольку центр массы создаваемого объекта, скорее всего, не находится на происхождении захвата, он, вероятно, имеет другую скорость, а контроллер в кадре ссылки пользователя.</span><span class="sxs-lookup"><span data-stu-id="83da5-405">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="83da5-406">Часть скорости объекта, созданная таким образом, является мгновенно отношения скоростью центра массы создаваемого объекта по отношению к источнику контроллера.</span><span class="sxs-lookup"><span data-stu-id="83da5-406">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="83da5-407">Отношения скорость — это перекрестное произведение угловой скорости контроллера с вектором, представляющим расстояние между источником контроллера и центром массы создаваемого объекта.</span><span class="sxs-lookup"><span data-stu-id="83da5-407">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="83da5-408">Общая скорость создаваемого объекта, таким образом, является суммой скорости контроллера и этой отношения скорости: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="83da5-408">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="83da5-409">**Обратите особое внимание на *время* , когда мы применяем скорость** .</span><span class="sxs-lookup"><span data-stu-id="83da5-409">**Pay close attention to the *time* at which we apply the velocity** .</span></span> <span data-ttu-id="83da5-410">При нажатии кнопки может потребоваться до 20 мс для этого события, чтобы это событие было переработано с помощью Bluetooth к операционной системе.</span><span class="sxs-lookup"><span data-stu-id="83da5-410">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="83da5-411">Это означает, что если вы опрашиваете изменение состояния контроллера с нажатия на не нажато или наоборот, сведения об этом контроллере, которые вы получаете вместе с ним, на самом деле будут находиться впереди этого изменения в состоянии.</span><span class="sxs-lookup"><span data-stu-id="83da5-411">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="83da5-412">Кроме того, контроллер, представленный нашим API-интерфейсом опроса, передается в прогноз, чтобы отразить, что в момент отображения кадра может быть больше 20 мс в будущем.</span><span class="sxs-lookup"><span data-stu-id="83da5-412">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="83da5-413">Это хорошо подходит для *визуализации* удерживаемых объектов, но создает *задачу по времени для объекта* , так как мы вычисляем траекторию на момент, когда пользователь выпустил свое исключение.</span><span class="sxs-lookup"><span data-stu-id="83da5-413">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="83da5-414">К счастью, при обновлении за Ноябрьское событие при отправке события Unity, такого как *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* , состояние включает данные предыстории с обратной стороны, когда кнопка была на самом деле нажата или освобождена.</span><span class="sxs-lookup"><span data-stu-id="83da5-414">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="83da5-415">Чтобы получить наиболее точную визуализацию контроллера и нацеливание контроллера во время возникновения исключения, необходимо правильно использовать опрос и события, если это уместно:</span><span class="sxs-lookup"><span data-stu-id="83da5-415">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="83da5-416">Для **отрисовки** каждого кадра на контроллере приложение должно располагать *GameObject* контроллера на переphotonном контроллере в течение текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="83da5-416">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="83da5-417">Эти данные можно получить из API опроса Unity, например *[XR. Инпуттраккинг. Жетлокалпоситион](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или *[XR. Головк. Входные данные. Интерактионманажер. Жеткуррентреадинг](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="83da5-417">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span></span>
   * <span data-ttu-id="83da5-418">Для **нацеливания контроллера** на нажатие или выпуск ваше приложение должно райкаст и вычислять траекторий на основе данных о том, что такое событие выпусков.</span><span class="sxs-lookup"><span data-stu-id="83da5-418">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="83da5-419">Эти данные можно получить из API-интерфейсов Unity, таких как *[интерактионманажер. интерактионсаурцепрессед](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="83da5-419">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span></span>
* <span data-ttu-id="83da5-420">**Использование захвата** .</span><span class="sxs-lookup"><span data-stu-id="83da5-420">**Use the grip pose** .</span></span> <span data-ttu-id="83da5-421">Угловая скорость и скорость отмечаются относительно захвата, а не указателя.</span><span class="sxs-lookup"><span data-stu-id="83da5-421">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="83da5-422">Порождение продолжит совершенствоваться с будущими обновлениями Windows, и вы сможете найти дополнительные сведения здесь.</span><span class="sxs-lookup"><span data-stu-id="83da5-422">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="83da5-423">Жесты и контроллеры движения в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="83da5-423">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="83da5-424">Вы можете получить доступ к жестам и контроллеру движения из диспетчера ввода.</span><span class="sxs-lookup"><span data-stu-id="83da5-424">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="83da5-425">Жест в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="83da5-425">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="83da5-426">Контроллер движения в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="83da5-426">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="83da5-427">Обучение по руководствам</span><span class="sxs-lookup"><span data-stu-id="83da5-427">Follow along with tutorials</span></span>

<span data-ttu-id="83da5-428">Пошаговые учебники с более подробными примерами настройки доступны в Academyе Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="83da5-428">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="83da5-429">211. Ввод в смешанной реальности: жест</span><span class="sxs-lookup"><span data-stu-id="83da5-429">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="83da5-430">213. Ввод в смешанной реальности: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="83da5-430">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="83da5-431">[![MR-вход 213 — контроллер движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="83da5-431">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="83da5-432">*MR-вход 213 — контроллер движения*</span><span class="sxs-lookup"><span data-stu-id="83da5-432">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="83da5-433">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="83da5-433">Next Development Checkpoint</span></span>

<span data-ttu-id="83da5-434">Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="83da5-434">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="83da5-435">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="83da5-435">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83da5-436">Отслеживание рук и взгляда</span><span class="sxs-lookup"><span data-stu-id="83da5-436">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="83da5-437">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="83da5-437">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="83da5-438">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="83da5-438">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="83da5-439">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="83da5-439">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="83da5-440">См. также статью</span><span class="sxs-lookup"><span data-stu-id="83da5-440">See also</span></span>

* [<span data-ttu-id="83da5-441">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="83da5-441">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="83da5-442">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="83da5-442">Motion controllers</span></span>](../../design/motion-controllers.md)
