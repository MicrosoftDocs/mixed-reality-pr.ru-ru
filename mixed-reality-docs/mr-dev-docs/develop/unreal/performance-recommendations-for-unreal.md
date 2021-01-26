---
title: Рекомендации по производительности для Unreal
description: Сведения о том, как обеспечить оптимальную производительность приложений смешанной реальности с помощью рекомендуемых параметров проекта Unreal.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583065"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="724bc-104">Рекомендации по производительности для Unreal</span><span class="sxs-lookup"><span data-stu-id="724bc-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="724bc-105">В Unreal Engine есть несколько функций, которые могут [повысить производительность приложений](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="724bc-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="724bc-106">Прежде чем продолжать, рекомендуется прочесть о факторах, ограничивающих производительность приложения, анализе и профилировании приложений смешанной реальности, а также общих настройках, повышающих производительность.</span><span class="sxs-lookup"><span data-stu-id="724bc-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="724bc-107">Рекомендуемые параметры для проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="724bc-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="724bc-108">Каждый из параметров, о которых идет речь ниже, можно найти в разделе **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="724bc-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="724bc-109">При использовании мобильного отрисовщика виртуальной реальности:</span><span class="sxs-lookup"><span data-stu-id="724bc-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="724bc-110">Прокрутите до раздела **Project** (Проект), выберите **Target Hardware** (Целевое оборудование) и выберите целевую платформу **Mobile/Tablet** (Мобильное устройство или планшет).</span><span class="sxs-lookup"><span data-stu-id="724bc-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Выбор мобильного устройства в качестве целевого](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="724bc-112">При использовании стандартного отрисовщика (forward renderer):</span><span class="sxs-lookup"><span data-stu-id="724bc-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="724bc-113">Стандартный отрисовщик гораздо лучше подходит для смешанной реальности, чем конвейер отложенной отрисовки по умолчанию, благодаря тому, что ряд функций можно отключить по отдельности.</span><span class="sxs-lookup"><span data-stu-id="724bc-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="724bc-114">Дополнительные сведения см. в [документации по Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="724bc-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Стандартная отрисовка (forward rendering)](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="724bc-116">Использование нескольких представлений для мобильных устройств:</span><span class="sxs-lookup"><span data-stu-id="724bc-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="724bc-117">Прокрутите до раздела **Engine** (Подсистема), выберите пункт **Rendering** (Отрисовка), разверните раздел **VR** (Виртуальная реальность) и установите флажки **Instanced Stereo** (Параллельное стерео) и **Mobile Multi-View** (Мобильная мультиотрисовка).</span><span class="sxs-lookup"><span data-stu-id="724bc-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="724bc-118">Необходимо снять флажок Mobile HDR (HDR для мобильных устройств).</span><span class="sxs-lookup"><span data-stu-id="724bc-118">Mobile HDR should be unchecked.</span></span>

![Параметры отрисовки виртуальной реальности](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="724bc-120">**[Только для OpenXR]** Убедитесь, что выбрано значение **Default** (По умолчанию) или **D3D12** для параметра **Default RHI** (RHI по умолчанию):</span><span class="sxs-lookup"><span data-stu-id="724bc-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="724bc-121">Вариант **D3D11** приведет к ухудшению производительности, так как платформе придется выполнять дополнительный проход отрисовки.</span><span class="sxs-lookup"><span data-stu-id="724bc-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="724bc-122">**D3D12** улучшает производительность отрисовки (и не требует дополнительного прохода).</span><span class="sxs-lookup"><span data-stu-id="724bc-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI по умолчанию](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="724bc-124">Отключение затуманивания вершин (vertex fogging):</span><span class="sxs-lookup"><span data-stu-id="724bc-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="724bc-125">Затуманивание вершин применяет расчеты тумана к каждой вершине в многоугольнике, а затем интерполирует результаты на поверхность многоугольника.</span><span class="sxs-lookup"><span data-stu-id="724bc-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="724bc-126">Если в игре не используется туман, рекомендуется отключить затуманивание вершин, чтобы повысить производительность шейдеров.</span><span class="sxs-lookup"><span data-stu-id="724bc-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Параметры затуманивания вершин](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="724bc-128">Отключение отбрасывания загораживаемых объектов:</span><span class="sxs-lookup"><span data-stu-id="724bc-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="724bc-129">Прокрутите до раздела **Engine** (Подсистема), выберите **Rendering** (Отрисовка), разверните раздел **Culling** (Отбрасывание объектов) и снимите флажок **Occlusion Culling** (Отбрасывание загораживаемых объектов).</span><span class="sxs-lookup"><span data-stu-id="724bc-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="724bc-130">Если вам требуется удаление скрытых объектов для подробной отрисовки сцены, рекомендуется установить флажок **Support Software Occlusion Culling** (Поддержка программного удаления скрытых объектов) в разделе **Engine > Rendering** (Движок > Отрисовка).</span><span class="sxs-lookup"><span data-stu-id="724bc-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="724bc-131">Это позволит Unreal выполнять соответствующую обработку на центральном процессоре, избегая отправки соответствующих запросов к GPU, которые выполняются неэффективно на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="724bc-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="724bc-132">GPU мобильных устройств медленно выполняют отбрасывание загораживаемых объектов.</span><span class="sxs-lookup"><span data-stu-id="724bc-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="724bc-133">Как правило, в основном GPU должен выполнять отрисовку.</span><span class="sxs-lookup"><span data-stu-id="724bc-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="724bc-134">Если вы считаете, что такое отбрасывание увеличит производительность, попробуйте включить программное отбрасывание.</span><span class="sxs-lookup"><span data-stu-id="724bc-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="724bc-135">Включение программного удаления скрытых объектов может ухудшить производительность, если ЦП уже обрабатывает большое количество вызовов отрисовки.</span><span class="sxs-lookup"><span data-stu-id="724bc-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Отключение отбрасывания загораживаемых объектов](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="724bc-137">Отключение настраиваемого прохода трафарета глубины:</span><span class="sxs-lookup"><span data-stu-id="724bc-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="724bc-138">Отключение этой функции требует дополнительного прохода, то есть оно выполняется медленно.</span><span class="sxs-lookup"><span data-stu-id="724bc-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="724bc-139">Применение прозрачности также выполняется медленно в Unreal.</span><span class="sxs-lookup"><span data-stu-id="724bc-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="724bc-140">Дополнительные сведения см. в [документации по Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="724bc-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Трафарет глубины](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="724bc-142">Сокращение числа каскадных карт теней:</span><span class="sxs-lookup"><span data-stu-id="724bc-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="724bc-143">Сокращение числа карт теней улучшит производительность.</span><span class="sxs-lookup"><span data-stu-id="724bc-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="724bc-144">Как правило, для этого свойства нужно задать значение 1 (если это не приводит к заметному ухудшению качества).</span><span class="sxs-lookup"><span data-stu-id="724bc-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Каскадные карты теней](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="724bc-146">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="724bc-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="724bc-147">Следующие параметры могут улучшить производительность, но за счет отключения некоторых функций.</span><span class="sxs-lookup"><span data-stu-id="724bc-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="724bc-148">Используйте их, только если вы уверены, что эти функции вам не потребуются.</span><span class="sxs-lookup"><span data-stu-id="724bc-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="724bc-149">Сокращение числа преобразований шейдеров на мобильных устройствах</span><span class="sxs-lookup"><span data-stu-id="724bc-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="724bc-150">Если ваши источники света не двигаются независимо от камеры, вы можете задать для этого свойства значение 0.</span><span class="sxs-lookup"><span data-stu-id="724bc-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="724bc-151">Его основное преимущество — он позволяет Unreal не выполнять некоторые преобразования шейдеров и ускорить их компиляцию.</span><span class="sxs-lookup"><span data-stu-id="724bc-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Сокращение числа преобразований шейдеров на мобильных устройствах](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="724bc-153">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="724bc-153">See also</span></span>

* [<span data-ttu-id="724bc-154">Рекомендации по повышению производительности для Unreal Engine на мобильных устройствах</span><span class="sxs-lookup"><span data-stu-id="724bc-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)