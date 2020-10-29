---
title: Рекомендации по производительности для Unreal
description: Рекомендации по оптимизации производительности для приложений смешанной реальности в Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699288"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="afacf-104">Рекомендации по производительности для Unreal</span><span class="sxs-lookup"><span data-stu-id="afacf-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="afacf-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="afacf-105">Overview</span></span>

<span data-ttu-id="afacf-106">Эта статья служит продолжением обсуждения, начатого в [рекомендациях по оптимизации производительности для смешанной реальности](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), но посвящена функциям, специфичным для Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="afacf-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="afacf-107">Прежде чем продолжать, рекомендуется прочесть о факторах, ограничивающих производительность приложения, анализе и профилировании приложений смешанной реальности, а также общих настройках, повышающих производительность.</span><span class="sxs-lookup"><span data-stu-id="afacf-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="afacf-108">Рекомендуемые параметры для проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="afacf-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="afacf-109">Каждый из параметров, о которых идет речь ниже, можно найти в разделе **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="afacf-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="afacf-110">При использовании мобильного отрисовщика виртуальной реальности:</span><span class="sxs-lookup"><span data-stu-id="afacf-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="afacf-111">Прокрутите до раздела **Project** (Проект), выберите **Target Hardware** (Целевое оборудование) и выберите целевую платформу **Mobile/Tablet** (Мобильное устройство или планшет).</span><span class="sxs-lookup"><span data-stu-id="afacf-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="afacf-113">При использовании стандартного отрисовщика (forward renderer):</span><span class="sxs-lookup"><span data-stu-id="afacf-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="afacf-114">Эта функция намного больше подходит для смешанной реальности, чем конвейер отложенной отрисовки (deferred rendering) по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="afacf-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="afacf-115">В основном это обусловлено тем, что некоторые функции можно по отдельности отключить.</span><span class="sxs-lookup"><span data-stu-id="afacf-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="afacf-116">Дополнительные сведения см. в [документации по Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="afacf-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Стандартная отрисовка (forward rendering)](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="afacf-118">Отключение затуманивания вершин (vertex fogging):</span><span class="sxs-lookup"><span data-stu-id="afacf-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="afacf-119">Затуманивание вершин применяет расчеты тумана к каждой вершине в многоугольнике, а затем интерполирует результаты на поверхность многоугольника.</span><span class="sxs-lookup"><span data-stu-id="afacf-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="afacf-120">Если в игре не используется туман, выберите этот параметр, чтобы отключить туман и повысить производительность шейдеров.</span><span class="sxs-lookup"><span data-stu-id="afacf-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Параметры затуманивания вершин](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="afacf-122">Отключение отбрасывания загораживаемых объектов:</span><span class="sxs-lookup"><span data-stu-id="afacf-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="afacf-123">Прокрутите до раздела **Engine** (Подсистема), выберите **Rendering** (Отрисовка), разверните раздел **Culling** (Отбрасывание объектов) и снимите флажок **Occlusion Culling** (Отбрасывание загораживаемых объектов).</span><span class="sxs-lookup"><span data-stu-id="afacf-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="afacf-124">Если вам требуется удаление скрытых объектов для подробной отрисовки сцены, рекомендуется установить флажок **Support Software Occlusion Culling** (Поддержка программного удаления скрытых объектов) в разделе **Engine > Rendering** (Движок > Отрисовка).</span><span class="sxs-lookup"><span data-stu-id="afacf-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="afacf-125">Это позволит Unreal выполнять соответствующую обработку на центральном процессоре, избегая запросов для этой цели к GPU, которые выполняются неэффективно на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="afacf-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="afacf-126">GPU мобильных устройств медленно выполняют отбрасывание загораживаемых объектов.</span><span class="sxs-lookup"><span data-stu-id="afacf-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="afacf-127">Как правило, в основном GPU должен выполнять отрисовку.</span><span class="sxs-lookup"><span data-stu-id="afacf-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="afacf-128">Если вы считаете, что такое отбрасывание увеличит производительность, попробуйте включить программное отбрасывание.</span><span class="sxs-lookup"><span data-stu-id="afacf-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="afacf-129">Обратите внимание, что включение программного отбрасывания может ухудшить производительность, если на ЦП уже выполняется большое число вызовов отрисовки.</span><span class="sxs-lookup"><span data-stu-id="afacf-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Отключение отбрасывания загораживаемых объектов](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="afacf-131">Отключение трафарета глубины:</span><span class="sxs-lookup"><span data-stu-id="afacf-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="afacf-132">Эта функция требует дополнительного прохода, то есть она выполняется медленно.</span><span class="sxs-lookup"><span data-stu-id="afacf-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="afacf-133">Применение прозрачности также выполняется медленно в Unreal.</span><span class="sxs-lookup"><span data-stu-id="afacf-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="afacf-134">Дополнительные сведения см. в [документации по Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="afacf-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Трафарет глубины](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="afacf-136">Использование нескольких представлений для мобильных устройств:</span><span class="sxs-lookup"><span data-stu-id="afacf-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="afacf-137">Прокрутите до раздела **Engine** (Подсистема), выберите пункт **Rendering** (Отрисовка), разверните раздел **VR** (Виртуальная реальность) и установите флажки **Instanced Stereo** (Параллельное стерео) и **Mobile Multi-View** (Мобильная мультиотрисовка).</span><span class="sxs-lookup"><span data-stu-id="afacf-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="afacf-138">Необходимо снять флажок Mobile HDR (HDR для мобильных устройств).</span><span class="sxs-lookup"><span data-stu-id="afacf-138">Mobile HDR should be unchecked.</span></span>

![Параметры отрисовки виртуальной реальности](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="afacf-140">Сокращение числа каскадных карт теней:</span><span class="sxs-lookup"><span data-stu-id="afacf-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="afacf-141">Сокращение числа карт теней улучшит производительность.</span><span class="sxs-lookup"><span data-stu-id="afacf-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="afacf-142">Как правило, для этого параметра нужно задать значение 1 (если это не приводит к заметному ухудшению качества).</span><span class="sxs-lookup"><span data-stu-id="afacf-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Каскадные карты теней](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="afacf-144">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="afacf-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="afacf-145">Следующие параметры могут улучшить производительность, но за счет отключения некоторых функций.</span><span class="sxs-lookup"><span data-stu-id="afacf-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="afacf-146">Используйте их, только если вы уверены, что эти функции вам не потребуются.</span><span class="sxs-lookup"><span data-stu-id="afacf-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="afacf-147">Сокращение числа преобразований шейдеров на мобильных устройствах</span><span class="sxs-lookup"><span data-stu-id="afacf-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="afacf-148">Если ваши источники света не двигаются независимо от камеры, вы можете задать для этого параметра значение 0.</span><span class="sxs-lookup"><span data-stu-id="afacf-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="afacf-149">Его основное преимущество — он позволяет Unreal не выполнять некоторые преобразования шейдеров и ускорить их компиляцию.</span><span class="sxs-lookup"><span data-stu-id="afacf-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Сокращение числа преобразований шейдеров на мобильных устройствах](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="afacf-151">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="afacf-151">See also</span></span>
* [<span data-ttu-id="afacf-152">Рекомендации по повышению производительности для Unreal Engine на мобильных устройствах</span><span class="sxs-lookup"><span data-stu-id="afacf-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)