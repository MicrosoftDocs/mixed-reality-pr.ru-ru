---
title: Контроллеры движения в Unity
description: Узнайте, как принять меры для вашего взгляда в Unity с входными данными контроллера движения с помощью XR и общих API кнопок и осей.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: контроллеры движения, Unity, ввод, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: bf9aad0ee67a406280cefedec8b55fb1de130b8b
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192976"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="a1a3e-104">Контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="a1a3e-104">Motion controllers in Unity</span></span>

<span data-ttu-id="a1a3e-105">Существует два основных способа выполнения действий с вашим [взглядом в Unity](gaze-in-unity.md), [жестами](../../design/gaze-and-commit.md#composite-gestures) и [контроллерами движения](../../design/motion-controllers.md) в HoloLens и иммерсивное ХМД.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="a1a3e-106">Доступ к данным для обоих источников пространственных данных осуществляется через одни и те же API в Unity.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="a1a3e-107">Unity предоставляет два основных способа доступа к данным пространственного ввода для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="a1a3e-108">Общие *входные API-интерфейсы input. "input. Axis"* работают в нескольких пакетах SDK для Unity XR, а API *интерактионманажер/GestureRecognizer* , относящийся к Windows Mixed Reality, предоставляет полный набор пространственных входных данных.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="a1a3e-109">Входные API-интерфейсы Unity XR</span><span class="sxs-lookup"><span data-stu-id="a1a3e-109">Unity XR input APIs</span></span>

<span data-ttu-id="a1a3e-110">Для новых проектов рекомендуется использовать новые интерфейсы API ввода XR с самого начала.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="a1a3e-111">Дополнительные сведения об [API XR](https://docs.unity3d.com/Manual/xr_input.html)можно найти здесь.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="a1a3e-112">Таблица сопоставления кнопок и осей Unity</span><span class="sxs-lookup"><span data-stu-id="a1a3e-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="a1a3e-113">Диспетчер ввода Unity для контроллеров движения Windows Mixed Reality поддерживает указанные ниже идентификаторы кнопок и осей с помощью API-интерфейсов *input. OnButton и AXIS* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="a1a3e-114">В столбце "Windows MR" содержатся ссылки на свойства, доступные для типа *интерактионсаурцестате* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="a1a3e-115">Каждый из этих API подробно описывается в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="a1a3e-116">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality обычно соответствует идентификаторам кнопок и осей Окулус.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="a1a3e-117">Сопоставление ИДЕНТИФИКАТОРов кнопок и осей для Windows Mixed Reality отличается от сопоставлений Опенвр двумя способами:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="a1a3e-118">Сопоставление использует идентификаторы сенсорной панели, отличающиеся от аналоговый, для поддержки контроллеров с сумбстиккс и сенсорными устройствами.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="a1a3e-119">Сопоставление позволяет избежать перегрузки идентификаторов кнопок A и X для кнопок меню, чтобы оставить их доступными для физических кнопок АБКСИ.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="a1a3e-120">Входные данные</span><span class="sxs-lookup"><span data-stu-id="a1a3e-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="a1a3e-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Распространенные API Unity</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="a1a3e-122">(Входные данные. Кнопка/ось)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="a1a3e-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Входной API Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="a1a3e-124">XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="a1a3e-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="a1a3e-125">Левая рука</span><span class="sxs-lookup"><span data-stu-id="a1a3e-125">Left hand</span></span> </th><th> <span data-ttu-id="a1a3e-126">Правая рука</span><span class="sxs-lookup"><span data-stu-id="a1a3e-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a1a3e-127">Выбрать триггер нажат</span><span class="sxs-lookup"><span data-stu-id="a1a3e-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="a1a3e-128">Ось 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="a1a3e-129">Ось 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="a1a3e-130">селектпрессед</span><span class="sxs-lookup"><span data-stu-id="a1a3e-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-131">Выбор триггера аналогового значения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="a1a3e-132">Ось 9</span><span class="sxs-lookup"><span data-stu-id="a1a3e-132">Axis 9</span></span> </td><td> <span data-ttu-id="a1a3e-133">Ось 10</span><span class="sxs-lookup"><span data-stu-id="a1a3e-133">Axis 10</span></span> </td><td> <span data-ttu-id="a1a3e-134">селектпресседамаунт</span><span class="sxs-lookup"><span data-stu-id="a1a3e-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-135">Выделение триггера частично нажато</span><span class="sxs-lookup"><span data-stu-id="a1a3e-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="a1a3e-136">Кнопка 14 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a1a3e-137">Кнопка 15 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a1a3e-138">Селектпресседамаунт &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-139">Нажата кнопка меню</span><span class="sxs-lookup"><span data-stu-id="a1a3e-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="a1a3e-140">Кнопка 6 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-140">Button 6\*</span></span> </td><td> <span data-ttu-id="a1a3e-141">Кнопка 7 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-141">Button 7\*</span></span> </td><td> <span data-ttu-id="a1a3e-142">менупрессед</span><span class="sxs-lookup"><span data-stu-id="a1a3e-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-143">Нажата кнопка захвата</span><span class="sxs-lookup"><span data-stu-id="a1a3e-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="a1a3e-144">Ось 11 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a1a3e-145">Кнопка 4 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a1a3e-146">Ось 12 = 1,0 (нет аналоговых значений)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a1a3e-147">Кнопка 5 <i>(совместимость с игровым планшетом)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a1a3e-148">Новы</span><span class="sxs-lookup"><span data-stu-id="a1a3e-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-149">Аналоговый стик X <i>(слева:-1,0, справа: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a1a3e-150">Ось 1</span><span class="sxs-lookup"><span data-stu-id="a1a3e-150">Axis 1</span></span> </td><td> <span data-ttu-id="a1a3e-151">Ось 4</span><span class="sxs-lookup"><span data-stu-id="a1a3e-151">Axis 4</span></span> </td><td> <span data-ttu-id="a1a3e-152">Сумбстиккпоситион. x</span><span class="sxs-lookup"><span data-stu-id="a1a3e-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-153">Аналоговый стик <i>по оси Y (Top:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a1a3e-154">Ось 2</span><span class="sxs-lookup"><span data-stu-id="a1a3e-154">Axis 2</span></span> </td><td> <span data-ttu-id="a1a3e-155">Ось 5</span><span class="sxs-lookup"><span data-stu-id="a1a3e-155">Axis 5</span></span> </td><td> <span data-ttu-id="a1a3e-156">Сумбстиккпоситион. y</span><span class="sxs-lookup"><span data-stu-id="a1a3e-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-157">Нажатый аналоговый стик</span><span class="sxs-lookup"><span data-stu-id="a1a3e-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="a1a3e-158">Кнопка 8</span><span class="sxs-lookup"><span data-stu-id="a1a3e-158">Button 8</span></span> </td><td> <span data-ttu-id="a1a3e-159">Кнопка 9</span><span class="sxs-lookup"><span data-stu-id="a1a3e-159">Button 9</span></span> </td><td> <span data-ttu-id="a1a3e-160">сумбстиккпрессед</span><span class="sxs-lookup"><span data-stu-id="a1a3e-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-161">Сенсорная панель X <i>(слева:-1,0, справа: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a1a3e-162">Ось 17 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="a1a3e-163">Ось 19 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="a1a3e-164">Таучпадпоситион. x</span><span class="sxs-lookup"><span data-stu-id="a1a3e-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-165">Сенсорная панель Y <i>(верхняя:-1,0, Нижняя: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a1a3e-166">Ось 18 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="a1a3e-167">Ось 20 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="a1a3e-168">Таучпадпоситион. y</span><span class="sxs-lookup"><span data-stu-id="a1a3e-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-169">Сенсорная панель затронута</span><span class="sxs-lookup"><span data-stu-id="a1a3e-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="a1a3e-170">Кнопка 18 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-170">Button 18\*</span></span> </td><td> <span data-ttu-id="a1a3e-171">Кнопка 19 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-171">Button 19\*</span></span> </td><td> <span data-ttu-id="a1a3e-172">таучпадтаучед</span><span class="sxs-lookup"><span data-stu-id="a1a3e-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-173">Сенсорная панель нажата</span><span class="sxs-lookup"><span data-stu-id="a1a3e-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="a1a3e-174">Кнопка 16 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-174">Button 16\*</span></span> </td><td> <span data-ttu-id="a1a3e-175">Кнопка 17 \*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-175">Button 17\*</span></span> </td><td> <span data-ttu-id="a1a3e-176">таучпадпрессед</span><span class="sxs-lookup"><span data-stu-id="a1a3e-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-177">6DoF захват захвата или указатель</span><span class="sxs-lookup"><span data-stu-id="a1a3e-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="a1a3e-178">Только <i>захват</i> : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Инпуттраккинг. Жетлокалпоситион</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="a1a3e-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Инпуттраккинг. Жетлокалротатион</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="a1a3e-180">Передается <i>захват</i> или <i>указатель</i> в качестве аргумента: Саурцестате. саурцепосе. трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="a1a3e-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="a1a3e-181">Саурцестате. Саурцепосе. Трижетротатион</span><span class="sxs-lookup"><span data-stu-id="a1a3e-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-182">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="a1a3e-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="a1a3e-183"><i>Точность расположения и потери исходного кода доступны только через API-интерфейс MR</i> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="a1a3e-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">Саурцестате. Саурцепосе. Поситионаккураци</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="a1a3e-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">Саурцестате. Properties. Саурцелоссриск</a></span><span class="sxs-lookup"><span data-stu-id="a1a3e-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="a1a3e-186">Эти идентификаторы кнопок и осей отличаются от идентификаторов, используемых Unity для Опенвр из-за конфликтов в сопоставлениях, используемых в игровых элементах управления, Окулус Touch и Опенвр.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="a1a3e-187">Захват захвата и указание объекта a</span><span class="sxs-lookup"><span data-stu-id="a1a3e-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="a1a3e-188">Windows Mixed Reality поддерживает контроллеры движения различными конструктивными факторами.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="a1a3e-189">Структура каждого контроллера различает свое отношение между положением пользователя и естественным направлением "вперед", которое приложения должны использовать для указания при подготовке к просмотру контроллера.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="a1a3e-190">Для лучшего представления этих контроллеров существует два вида экземпляров, которые можно исследовать для каждого источника взаимодействия, **захвата** и **указателя**.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="a1a3e-191">Координаты захвата и указателя "указатель" выражаются всеми API Unity в глобальных координатах мира Unity.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="a1a3e-192">Подзахват</span><span class="sxs-lookup"><span data-stu-id="a1a3e-192">Grip pose</span></span>

<span data-ttu-id="a1a3e-193">**Захват** — это расположение карманных пользователей, обнаруженное HoloLens или удерживающий контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="a1a3e-194">На современных головных телефонах подзахваты лучше использовать для визуализации **руки пользователя** или **объекта, хранящегося в руки пользователя**.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="a1a3e-195">Элемент захвата также используется при визуализации контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="a1a3e-196">**Модель подготовки к просмотру** , предоставляемая Windows для контроллера движения, использует захват в качестве источника и центра вращения.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="a1a3e-197">Захват захвата определяется в частности следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="a1a3e-198">**Позиция захвата**: Карманный центроид при удержании контроллера естественным образом настраивается влево или вправо для центрирования места внутри захвата.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="a1a3e-199">В контроллере движения Windows Mixed Reality эта отправка обычно соответствует кнопке "расположить".</span><span class="sxs-lookup"><span data-stu-id="a1a3e-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="a1a3e-200">**Правая ось ориентации захвата**: когда вы полностью открываете руку для формирования плоской задачи с 5-пальцем, луч, обычный для вашего кармана (вперед от левого кармана, назад от правого Palm)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="a1a3e-201">**Прямая ось ориентации захвата**: когда вы частично закрываете руку (как при удержании контроллера), луч, который указывает на "Forward" через лампу, сформированную небегункными пальцами.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="a1a3e-202">**Ось Up (вверх) для ориентации захвата**: ось Up, подразумеваемая правым и прямым определением.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="a1a3e-203">Доступ к захвату можно получить через API-интерфейс ввода кросс-поставщика Unity (*[XR). Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Жетлокалпоситион/вращение*) или через API-интерфейс Windows MR (*Саурцестате. Саурцепосе. Трижетпоситион/вращение*, запрашивающий данные для узла **захвата** ).</span><span class="sxs-lookup"><span data-stu-id="a1a3e-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="a1a3e-204">Указатель a</span><span class="sxs-lookup"><span data-stu-id="a1a3e-204">Pointer pose</span></span>

<span data-ttu-id="a1a3e-205">**Указатель** a представляет кончик контроллера, указывающий на пересылку.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="a1a3e-206">Предоставляемый системой указатель, который лучше использовать для райкаст при **отрисовке самой модели контроллера**.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="a1a3e-207">При визуализации какого-либо другого виртуального объекта вместо контроллера, такого как виртуальный обойм, следует указывать на луч, который наиболее естественным для этого виртуального объекта, например луч, передаваемый на объект модели оружия, определяемой приложением.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="a1a3e-208">Так как пользователи могут видеть виртуальный объект, а не физический контроллер, указание виртуального объекта, скорее всего, будет более естественным для тех, кто использует ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="a1a3e-209">В настоящее время указатель a доступен в Unity только через API-интерфейс Windows MR, *саурцестате. саурцепосе. трижетпоситион/вращение*, передавая *интерактионсаурценоде. Pointer* в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="a1a3e-210">Состояние отслеживания контроллера</span><span class="sxs-lookup"><span data-stu-id="a1a3e-210">Controller tracking state</span></span>

<span data-ttu-id="a1a3e-211">Как и гарнитуры, для контроллера движения Windows Mixed Reality не требуется настраивать внешние датчики отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="a1a3e-212">Вместо этого контроллеры прописываются датчиками в самой гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="a1a3e-213">Если пользователь переместит контроллеры из поля "гарнитура", Windows по большей части будет вычислять положение контроллера в большинстве случаев.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="a1a3e-214">Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="a1a3e-215">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a1a3e-216">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать при приближенной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="a1a3e-217">Лучший способ сделать это — попробовать.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="a1a3e-218">Просмотрите это видео с примерами впечатляющих материалов, которые работают с контроллерами движения в различных состояниях отслеживания:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="a1a3e-219">Явное объяснение состояния отслеживания</span><span class="sxs-lookup"><span data-stu-id="a1a3e-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="a1a3e-220">Приложения, которые хотят обрабатывать позиции по-разному в зависимости от состояния отслеживания, могут дополнительно проанализировать свойства в состоянии контроллера, такие как *саурцелоссриск* и *поситионаккураци*:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="a1a3e-221">Состояние отслеживания</span><span class="sxs-lookup"><span data-stu-id="a1a3e-221">Tracking state</span></span> </th><th> <span data-ttu-id="a1a3e-222">саурцелоссриск</span><span class="sxs-lookup"><span data-stu-id="a1a3e-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="a1a3e-223">поситионаккураци</span><span class="sxs-lookup"><span data-stu-id="a1a3e-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="a1a3e-224">трижетпоситион</span><span class="sxs-lookup"><span data-stu-id="a1a3e-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a1a3e-225"><b>Высокая точность</b> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-226">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-227">Высокий</span><span class="sxs-lookup"><span data-stu-id="a1a3e-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-228">Да</span><span class="sxs-lookup"><span data-stu-id="a1a3e-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-229"><b>Высокая точность (при потере риска)</b> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a1a3e-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-231">Высокий</span><span class="sxs-lookup"><span data-stu-id="a1a3e-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-232">Да</span><span class="sxs-lookup"><span data-stu-id="a1a3e-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-233"><b>Приблизительная точность</b> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a1a3e-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a1a3e-235">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="a1a3e-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a1a3e-236">Да</span><span class="sxs-lookup"><span data-stu-id="a1a3e-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a1a3e-237"><b>Без расположения</b> </span><span class="sxs-lookup"><span data-stu-id="a1a3e-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a1a3e-238">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a1a3e-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a1a3e-239">Приблизительна</span><span class="sxs-lookup"><span data-stu-id="a1a3e-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a1a3e-240">false</span><span class="sxs-lookup"><span data-stu-id="a1a3e-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="a1a3e-241">Эти состояния отслеживания контроллера движения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="a1a3e-242">**Высокая точность:** Хотя контроллер движения находится внутри поля зрения гарнитуры, он обычно предоставляет высокую точность на основе визуального отслеживания.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="a1a3e-243">Перемещаемый контроллер, проходящий через некоторое время, покидает поле зрения или незаметно от него (например, с другой стороны пользователя) будет продолжать возвращать высокую точность в течение короткого времени, исходя из инерции отслеживания самого контроллера.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="a1a3e-244">**Высокая точность (при потере риска):** Когда пользователь перемещает контроллер движения за пределы поля "гарнитура", головной телефон вскоре не сможет визуально отвести мониторинг позиции контроллера.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="a1a3e-245">Приложение знает, когда контроллер достиг этой фов границы, просматривая **саурцелоссриск** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="a1a3e-246">На этом этапе приложение может приостановить жесты контроллера, для которых требуется постоянный поток с высоким качеством.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="a1a3e-247">**Приблизительная точность:** Когда контроллер потеряет Визуальное отслеживание на достаточно длинном уровне, позиции контроллера будут отбрасываться на позиции приблизительной точности.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="a1a3e-248">На этом этапе система будет блокировать контроллер для пользователя, отслеживая положение пользователя по мере его перемещения, сохраняя при этом ориентацию на уровне true, используя внутренние датчики ориентации.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a1a3e-249">Многие приложения, использующие контроллеры для указания и активации элементов пользовательского интерфейса, могут нормально работать в режиме обычной точности, не закрывая пользователю.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="a1a3e-250">Приложения с более **высокими** требованиями к входным данным могут отказаться от высокой точности для **приблизительной** точности, проверив свойство **поситионаккураци** , например, чтобы предоставить пользователю более масштабная хитбокс на экранных целевых объектах в течение этого времени.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="a1a3e-251">**Без расположения:** Несмотря на то, что контроллер может нормально обрабатываться в течение длительного времени, иногда система знает, что даже в данный момент не имеет смысла в том случае, если на самом деле есть неосмысленная Блокировка текста.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="a1a3e-252">Например, контроллер, который был включен, может никогда не наблюдаться в визуальном состоянии, или же пользователь может установить контроллер, который затем заберет другой.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="a1a3e-253">В это время система не предоставит какое бы то ни было приложение, а *трижетпоситион* вернет значение false.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="a1a3e-254">Общие API-интерфейсы Unity (входные или кнопки и ось)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="a1a3e-255">**Пространство имен:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="a1a3e-256">**Types**: *input*, *XR. Инпуттраккинг*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="a1a3e-257">В настоящее время Unity использует общие *входные API-интерфейсы input. Окулус и input. Axis* для предоставления входных данных для [пакета SDK для](https://docs.unity3d.com/Manual/OculusControllers.html), [пакета SDK опенвр](https://docs.unity3d.com/Manual/OpenVRControllers.html) и Windows Mixed Reality, включая руки и контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="a1a3e-258">Если приложение использует эти API для ввода данных, оно может легко поддерживать контроллеры движения в нескольких пакетах SDK XR, включая Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="a1a3e-259">Получение состояния нажатия логической кнопки</span><span class="sxs-lookup"><span data-stu-id="a1a3e-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="a1a3e-260">Чтобы использовать общие интерфейсы API ввода Unity, обычно начнем с привязки кнопок и осей к логическим именам в [диспетчере ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязывая идентификаторы кнопок или осей к каждому имени.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="a1a3e-261">Затем можно написать код, ссылающийся на эту логическую кнопку или имя оси.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="a1a3e-262">Например, чтобы связать кнопку триггера левого контроллера движения с действием Отправить, перейдите в меню **правка > параметры проекта > входные данные** в Unity и разверните свойства раздела отправить в разделе оси.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="a1a3e-263">Измените **положительную кнопку** или свойство **положительной кнопки Alt** , чтобы прочесть **игровую кнопку 14**, например:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="a1a3e-264">![InputManager Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="a1a3e-265">*InputManager Unity*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-265">*Unity InputManager*</span></span>

<span data-ttu-id="a1a3e-266">Затем скрипт может проверить действие отправки с помощью *input. OnButton*:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="a1a3e-267">Можно добавить дополнительные логические кнопки, изменив свойство **size** в разделе **оси**.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="a1a3e-268">Непосредственное получение состояния нажатия физической кнопки</span><span class="sxs-lookup"><span data-stu-id="a1a3e-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="a1a3e-269">Можно также получить доступ к кнопкам вручную по полному имени с помощью *input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="a1a3e-270">Получение объекта руки или контроллера движения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="a1a3e-271">Вы можете получить доступ к положению и повороту контроллера с помощью *XR. Инпуттраккинг*:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="a1a3e-272">Приведенный выше код представляет собой захват контроллера (где пользователь владеет контроллером), который полезен для отрисовки технологий или оружия в руки пользователя или модели самого контроллера.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="a1a3e-273">Связь между этим захватом и указателем (где накладывается кончик контроллера) может отличаться в разных контроллерах.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="a1a3e-274">На данный момент доступ к элементу указателя контроллера может осуществляться только через API ввода, характерный для MR, описанный в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="a1a3e-275">Интерфейсы API для Windows (XR. Головк. Входной</span><span class="sxs-lookup"><span data-stu-id="a1a3e-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="a1a3e-276">Если в проекте используются какие-либо из XR. Поэтапные API-интерфейсы см. в них используется пакет SDK XR в будущих выпусках Unity.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="a1a3e-277">Для новых проектов мы рекомендуем использовать пакет SDK для XR с самого начала.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="a1a3e-278">Дополнительные сведения о [системе ввода и интерфейсах API XR](https://docs.unity3d.com/Manual/xr_input.html)можно найти здесь.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="a1a3e-279">**Пространство имен:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a1a3e-280">**Типы**: *интерактионманажер*, *интерактионсаурцестате*, *интерактионсаурце*, *интерактионсаурцепропертиес*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="a1a3e-281">Чтобы получить более подробные сведения о вводе-выделе Windows Mixed Reality (для HoloLens) и контроллеров движения, можно выбрать использование пространственных входных API Windows в пространстве имен *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="a1a3e-282">Это позволяет получить доступ к дополнительным сведениям, таким как точность расположения или тип источника, что позволяет сообщать о руки и контроллерах.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="a1a3e-283">Опрос состояния движений и контроллеров движения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="a1a3e-284">Вы можете опросить состояние этого кадра для каждого источника взаимодействия (вручную или контроллера движения) с помощью метода *жеткуррентреадинг* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="a1a3e-285">Каждый *интерактионсаурцестате* , который вы получаете назад, представляет источник взаимодействия на текущий момент времени.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="a1a3e-286">*Интерактионсаурцестате* предоставляет такие сведения:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="a1a3e-287">Какие [виды нажатия](../../design/motion-controllers.md) происходят (выбор/меню, распечатка, Сенсорная панель или аналоговый стик)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="a1a3e-288">Другие данные, относящиеся к контроллерам движения, таким как координаты и/или ТОЧЕЧный стик, а также затронутое состояние</span><span class="sxs-lookup"><span data-stu-id="a1a3e-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="a1a3e-289">Интерактионсаурцекинд, чтобы выяснить, является ли источник рукой или контроллером движения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="a1a3e-290">Опрос для перенаправляемых прогнозов отрисовки</span><span class="sxs-lookup"><span data-stu-id="a1a3e-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="a1a3e-291">При опросе данных об источнике взаимодействия от рук и контроллеров, получаемые вами данные будут перенаправлены на момент времени, когда фотоны этого кадра будет достигнуть глаз пользователя.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="a1a3e-292">Для **подготовки к просмотру** контроллера или удерживаемого объекта в каждом кадре лучше использовать перенаправляемые объекты.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="a1a3e-293">Если вы нажимаете на контроллере любую нажатие или выпуск, это будет наиболее точным, если вы используете API событий предыстории, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="a1a3e-294">Вы также можете получить в этом текущем фрейме объект с прямым прогнозированием.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="a1a3e-295">Как и в случае с исходной версией, это полезно для **отрисовки** курсора, хотя нацеливание на заданную клавишу или выпуск будет наиболее точным, если вы используете интерфейсы API событий с предысторией, описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="a1a3e-296">Обработка событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a1a3e-296">Handling interaction source events</span></span>

<span data-ttu-id="a1a3e-297">Чтобы обрабатывались входные события, происходящие с точными данными предыстории, вместо опроса можно использовать события источника взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="a1a3e-298">Для управления событиями источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-298">To handle interaction source events:</span></span>
* <span data-ttu-id="a1a3e-299">Регистрация для события ввода *интерактионманажер* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="a1a3e-300">Для каждого интересующего вас типа события взаимодействия необходимо подписываться на него.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="a1a3e-301">Обработайте событие.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-301">Handle the event.</span></span> <span data-ttu-id="a1a3e-302">После подписки на событие взаимодействия вы получите обратный вызов при необходимости.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="a1a3e-303">В примере *саурцепрессед* это произойдет после обнаружения источника и до его освобождения или потери.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="a1a3e-304">Как прерывать обработку события</span><span class="sxs-lookup"><span data-stu-id="a1a3e-304">How to stop handling an event</span></span>

<span data-ttu-id="a1a3e-305">Если вы больше не заинтересованы в событии или удаляете объект, подписанный на событие, необходимо отменить обработку события.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="a1a3e-306">Чтобы прерывать обработку события, отказаться от подписки на событие.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="a1a3e-307">Список событий источника взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a1a3e-307">List of interaction source events</span></span>

<span data-ttu-id="a1a3e-308">Доступные события источника взаимодействия:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-308">The available interaction source events are:</span></span>
* <span data-ttu-id="a1a3e-309">*Интерактионсаурцедетектед* (источник стал активным)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="a1a3e-310">*Интерактионсаурцелост* (неактивен)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="a1a3e-311">*Интерактионсаурцепрессед* (TAP, нажатие кнопки или "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="a1a3e-312">*Интерактионсаурцерелеасед* (окончание касания, кнопка отжата или конец "Select" распространенная)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="a1a3e-313">*Интерактионсаурцеупдатед* (перемещение или иным образом изменяет некоторое состояние)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="a1a3e-314">События для исторических целей, которые наиболее точно соответствуют нажатию или выпуску</span><span class="sxs-lookup"><span data-stu-id="a1a3e-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="a1a3e-315">API-интерфейсы опроса, описанные выше, предоставляют приложению перенаправление прогнозов.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="a1a3e-316">Хотя эти прогнозируемые объекты лучше всего подходят для подготовки к просмотру контроллера или виртуального карманного объекта, будущие элементы не оптимальны для нацеливания, по двум основным причинам:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="a1a3e-317">Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс беспроводной задержки по Bluetooth, прежде чем система получит нажатие.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="a1a3e-318">Затем, если вы используете перенаправленный прогноз, в качестве целевого времени будет использоваться еще 10-20 мс прямого прогнозирования, когда фотоны текущего кадра достигнет глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="a1a3e-319">Это означает, что опрос дает вам исходную позицию или головной элемент, который находится в 30-40 мс вперед от того места, где заголовком пользователя и фактически была обратна в момент возникновения нажатия или выпуска.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="a1a3e-320">Для входных данных HoloLens, в то время как нет задержки беспроводной передачи, существует аналогичная задержка обработки для обнаружения нажатия.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="a1a3e-321">Чтобы правильно ориентироваться в зависимости от первоначальной цели пользователя или нажатия контроллера, следует использовать источник с предысторией или головной элемент из этого события ввода *интерактионсаурцепрессед* или *интерактионсаурцерелеасед* .</span><span class="sxs-lookup"><span data-stu-id="a1a3e-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="a1a3e-322">Вы можете выбрать пресс или Release с предысторией данных из заголовка пользователя или контроллера:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="a1a3e-323">В момент, когда произошло нажатие жеста или контроллера, эта головная программа может быть **использована для определения** того, что именно [облаками](../../design/gaze-and-commit.md) пользователь:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="a1a3e-324">Исходная ошибка в момент, когда произошло нажатие кнопки контроллера движения, которое можно использовать для определения **нацеливания** пользователя на контроллер.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="a1a3e-325">Это будет состояние контроллера, на котором нажимается клавиша.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="a1a3e-326">Если вы создаете сам контроллер, то можете запросить объект a, а не захват, чтобы прокрутить целевой луч от того, что пользователь будет рассматривать как естественный Совет этого отображаемого контроллера:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="a1a3e-327">Пример обработчиков событий</span><span class="sxs-lookup"><span data-stu-id="a1a3e-327">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk-v2"></a><span data-ttu-id="a1a3e-328">Контроллеры движения в МРТК v2</span><span class="sxs-lookup"><span data-stu-id="a1a3e-328">Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="a1a3e-329">Вы можете получить доступ к [жестам и контроллеру движения](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) из диспетчера ввода.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-329">You can access [gesture and motion controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="a1a3e-330">Обучение по руководствам</span><span class="sxs-lookup"><span data-stu-id="a1a3e-330">Follow along with tutorials</span></span>

<span data-ttu-id="a1a3e-331">Пошаговые учебники с более подробными примерами настройки доступны в Academyе Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="a1a3e-332">211. Ввод в смешанной реальности: жест</span><span class="sxs-lookup"><span data-stu-id="a1a3e-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="a1a3e-333">213. Ввод в смешанной реальности: контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="a1a3e-334">[![MR-вход 213 — контроллер движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="a1a3e-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="a1a3e-335">*MR-вход 213 — контроллер движения*</span><span class="sxs-lookup"><span data-stu-id="a1a3e-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a1a3e-336">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="a1a3e-336">Next Development Checkpoint</span></span>

<span data-ttu-id="a1a3e-337">Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core.</span><span class="sxs-lookup"><span data-stu-id="a1a3e-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="a1a3e-338">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1a3e-339">Отслеживание рук и взгляда</span><span class="sxs-lookup"><span data-stu-id="a1a3e-339">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="a1a3e-340">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="a1a3e-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="a1a3e-341">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="a1a3e-341">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="a1a3e-342">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="a1a3e-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a3e-343">См. также статью</span><span class="sxs-lookup"><span data-stu-id="a1a3e-343">See also</span></span>

* [<span data-ttu-id="a1a3e-344">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="a1a3e-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="a1a3e-345">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="a1a3e-345">Motion controllers</span></span>](../../design/motion-controllers.md)