---
title: Рекомендации по использованию материалов в Unreal
description: Обзор материалов в нереальном подсистеме.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Нереал, Нереал. 4, UE4, HoloLens, HoloLens 2, разработка, материалы, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609575"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="fc0a6-104">Рекомендации по использованию материалов в Unreal</span><span class="sxs-lookup"><span data-stu-id="fc0a6-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="fc0a6-105">Используемые вами материалы могут напрямую влиять на то, насколько хорошо ваши проекты работают в нереальной подсистеме.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-105">The materials you use can directly affect how well your projects run in Unreal Engine.</span></span> <span data-ttu-id="fc0a6-106">Эта страница служит для быстрого запуска основных параметров, которые следует использовать для достижения максимальной производительности приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-106">This page acts as a quick-start for the basic settings you should be using to get the best performance out of your mixed reality applications.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="fc0a6-107">Использование Кустомизедувс</span><span class="sxs-lookup"><span data-stu-id="fc0a6-107">Using CustomizedUVs</span></span>

<span data-ttu-id="fc0a6-108">Если необходимо предоставить UV мозаику на своем материале, используйте Кустомизедувс, а не изменяйте UV узла текстуры напрямую.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-108">If you need to provide UV tiling on your material, use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="fc0a6-109">Кустомизедувс позволяют управлять UVs в шейдерах вершин, а не в шейдере пикселей.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-109">CustomizedUVs let you manipulate UVs in the Vertex shaders rather than the Pixel shader.</span></span>

![Параметры материала в нереальном режиме](images/unreal-materials-img-01c.png)

<span data-ttu-id="fc0a6-111">Сведения о материалах см. в [документации по нереальному подсистеме](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) и рекомендуемым примерам на снимках экрана ниже.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-111">You can find material details in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="fc0a6-112">[ ![ Рекомендуемые параметры материалов в нереальных ](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox) 
 *рекомендуемых настройках материалов*</span><span class="sxs-lookup"><span data-stu-id="fc0a6-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="fc0a6-113">[ ![ Нерекомендуемые параметры материалов в нереальной ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *нерекомендуемой настройке материалов*</span><span class="sxs-lookup"><span data-stu-id="fc0a6-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="fc0a6-114">Изменение режима смешения</span><span class="sxs-lookup"><span data-stu-id="fc0a6-114">Changing Blend Mode</span></span>

<span data-ttu-id="fc0a6-115">Рекомендуется устанавливать режим смешения в непрозрачное состояние, если в противном случае нет серьезной причины.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-115">We recommend setting the blend mode to opaque unless there's a strong reason to do otherwise.</span></span> <span data-ttu-id="fc0a6-116">Маскированные и полупрозрачные материалы работают очень долго.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="fc0a6-117">Дополнительные сведения о материалах см. в [документации по нереальному подсистеме](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="fc0a6-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Изменение режима смешения](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="fc0a6-119">Обновление освещения для мобильных устройств</span><span class="sxs-lookup"><span data-stu-id="fc0a6-119">Updating lighting for mobile</span></span>

<span data-ttu-id="fc0a6-120">Полная точность должна быть отключена.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-120">Full precision should be turned off.</span></span> <span data-ttu-id="fc0a6-121">Лигхтмап освещение можно набирать вниз, отключив сведения о направлении.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="fc0a6-122">При отключении освещение от лигхтмапс будет плоским, но дешевле.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Параметры мобильного материала в нереальном режиме](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="fc0a6-124">Настройка перемотки заливки вперед</span><span class="sxs-lookup"><span data-stu-id="fc0a6-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="fc0a6-125">Эти параметры улучшают качество визуализации за счет производительности.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="fc0a6-126">Они должны быть отключены для максимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-126">They should be turned off for maximum performance.</span></span>

![Пересылка параметров материала заливки в нереальном режиме](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="fc0a6-128">Настройка материала полупрозрачность</span><span class="sxs-lookup"><span data-stu-id="fc0a6-128">Setting material translucency</span></span>

<span data-ttu-id="fc0a6-129">Указывает, что на полупрозрачные материалы не должны влиять раскрытия или ДОФ.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="fc0a6-130">Так как оба этих эффекта в MR редки, этот параметр должен быть включен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Отдельный параметр полупрозрачность в нереальном режиме для мобильных устройств](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="fc0a6-132">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="fc0a6-132">Optional settings</span></span>

<span data-ttu-id="fc0a6-133">Следующие параметры могут повысить производительность, но обратите внимание, что они отключают определенные функции.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="fc0a6-134">Используйте их, только если вы уверены, что эти функции вам не потребуются.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-134">Only use these settings if you're sure you don't need the features in question.</span></span>

![Необязательные параметры материалов в нереальном режиме](images/unreal-materials-img-06.jpg)

<span data-ttu-id="fc0a6-136">Если для вашего материала не требуются отражения или «блики», то установка этого параметра может обеспечить значительное повышение производительности.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="fc0a6-137">Во внутреннем тестировании это так же быстро, как "унлит", при предоставлении сведений о освещении.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-137">In internal testing, it's as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fc0a6-138">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="fc0a6-138">Best practices</span></span>

<span data-ttu-id="fc0a6-139">Следующие параметры не являются "параметрами", так как они являются рекомендациями, относящимися к материалам.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-139">The following aren't "settings" as much as they're best practices related to Materials.</span></span>

<span data-ttu-id="fc0a6-140">При создании параметров предпочтительнее использовать "статические параметры" везде, где это возможно.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="fc0a6-141">Статические коммутаторы можно использовать для удаления целой ветви материала без затрат времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="fc0a6-142">Экземпляры могут иметь разные значения, что позволяет настроить шаблон шейдера без потери производительности.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-142">Instances can have different values, making it possible to have a templated shader set up with no performance loss.</span></span> <span data-ttu-id="fc0a6-143">Недостаток заключается в том, что создается несколько перестановок, что приведет к перекомпиляции шейдера.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-143">The downside, is that several permutations are created that will cause shader recompilation.</span></span> <span data-ttu-id="fc0a6-144">Попробуйте максимально ограничить количество статических параметров в материале и число перестановок используемых статических параметров.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are used.</span></span> <span data-ttu-id="fc0a6-145">Дополнительные сведения о подготовке к просмотру параметров материалов см. в [документации по нереальному подсистеме](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="fc0a6-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Рекомендации по настройке материалов](images/unreal-materials-img-07.jpg)

<span data-ttu-id="fc0a6-147">При создании экземпляров материалов предпочтение необходимо предоставить **константе экземпляра материала** для экземпляра материала Dynamic.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="fc0a6-148">**Константа экземпляра материала** — это экземпляр материала, который вычисляется только один раз до времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-148">**Material Instance Constant** is an instanced Material that calculates only once before runtime.</span></span>

<span data-ttu-id="fc0a6-149">Экземпляр материала, созданный с помощью браузера содержимого (**щелкните правой кнопкой мыши > создать экземпляр материала**) — это константа экземпляра материала.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="fc0a6-150">Экземпляр материала Dynamic создается с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="fc0a6-151">Дополнительные сведения об экземплярах материалов см. в [документации по нереальному подсистеме](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="fc0a6-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Создание экземпляров материалов в нереальном режиме](images/unreal-materials-img-08.png)

<span data-ttu-id="fc0a6-153">Следите за сложными материалами и шейдерами.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="fc0a6-154">Вы можете просмотреть стоимость вашего материала на различных платформах, щелкнув значок статистика платформы.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="fc0a6-155">Дополнительные сведения о материалах см. в документации по [нереальному подсистеме](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="fc0a6-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Создание динамических параметров экземпляра материала в нереальном режиме](images/unreal-materials-img-09.png)

<span data-ttu-id="fc0a6-157">Вы можете быстро понять относительную сложность шейдера через [режим](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)сложности шейдера.</span><span class="sxs-lookup"><span data-stu-id="fc0a6-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="fc0a6-158">Сочетание клавиш в режиме просмотра: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="fc0a6-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="fc0a6-159">Команда консоли: ViewMode шадеркомплексити</span><span class="sxs-lookup"><span data-stu-id="fc0a6-159">Console command: viewmode shadercomplexity</span></span>

![Сложность материала в нереальном режиме](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="fc0a6-161">См. также</span><span class="sxs-lookup"><span data-stu-id="fc0a6-161">See also</span></span>
* [<span data-ttu-id="fc0a6-162">Мобильные материалы</span><span class="sxs-lookup"><span data-stu-id="fc0a6-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="fc0a6-163">Режимы представления</span><span class="sxs-lookup"><span data-stu-id="fc0a6-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="fc0a6-164">Экземпляры материалов</span><span class="sxs-lookup"><span data-stu-id="fc0a6-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
