---
title: Критерии качества приложения
description: В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: критерии качества приложения, Смешанная реальность, приложение смешанной реальности, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 788a2e8ac1a364f8c33e3895992fd99fa220a26a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530290"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="63dde-104">Критерии качества приложения</span><span class="sxs-lookup"><span data-stu-id="63dde-104">App quality criteria</span></span>

<span data-ttu-id="63dde-105">В этом документе описываются лучшие факторы, влияющие на качество приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="63dde-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="63dde-106">Для каждого фактора предоставляются следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="63dde-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="63dde-107">Обзор — краткое описание фактора качества и его важность.</span><span class="sxs-lookup"><span data-stu-id="63dde-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="63dde-108">Воздействие на устройства. тип устройства Windows Mixed Reality, на который влияет действие.</span><span class="sxs-lookup"><span data-stu-id="63dde-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="63dde-109">Критерии качества — оценка коэффициента качества.</span><span class="sxs-lookup"><span data-stu-id="63dde-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="63dde-110">Способ измерения — методы для измерения (или взаимодействия) проблемы.</span><span class="sxs-lookup"><span data-stu-id="63dde-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="63dde-111">Рекомендации — общие сведения о подходах, обеспечивающих лучшую работу пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="63dde-112">Ресурсы — соответствующие ресурсы для разработчиков и проектирования, которые полезны для создания лучших возможностей приложений.</span><span class="sxs-lookup"><span data-stu-id="63dde-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="63dde-113">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="63dde-113">Frame rate</span></span>

<span data-ttu-id="63dde-114">Частота кадров — первый основополагающий уровень стабильности и комфорт пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="63dde-115">Частота кадров ниже рекомендуемых целевых объектов может привести к неблагоприятному снижению голограмм, негативно сказывается на белиевабилити опыта и потенциально выносливости глаз.</span><span class="sxs-lookup"><span data-stu-id="63dde-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="63dde-116">В зависимости от того, какие компьютеры, совместимые с Windows Mixed Reality, поддерживаются, частота целевых кадров в интерфейсе для захватывающих головных телефонов Windows Mixed Reality составляет 60 Гц или 90 Гц.</span><span class="sxs-lookup"><span data-stu-id="63dde-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="63dde-117">Для HoloLens скорость целевого кадра составляет 60 Гц.</span><span class="sxs-lookup"><span data-stu-id="63dde-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-118">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-121">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-121">✔️</span></span></td>
        <td><span data-ttu-id="63dde-122">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-123">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-123">Quality criteria</span></span>

|  <span data-ttu-id="63dde-124">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-124">Best</span></span>  |  <span data-ttu-id="63dde-125">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-125">Meets</span></span> |  <span data-ttu-id="63dde-126">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="63dde-127">Приложение согласованно соответствует цели кадров в секунду (кадров/с) для целевого устройства: 60/с в HoloLens; 90 кадров/с на Ultra ПК; и 60 кадров на самых распространенных ПК.</span><span class="sxs-lookup"><span data-stu-id="63dde-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="63dde-128">Приложение имеет периодические падения кадров, не мешающие основному интерфейсу, или число кадров в кадре постоянно меньше, чем нужная цель, но не помешать работе приложения.</span><span class="sxs-lookup"><span data-stu-id="63dde-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="63dde-129">В среднем каждые 10 секунд в приложении происходит частота кадров.</span><span class="sxs-lookup"><span data-stu-id="63dde-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="63dde-130">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-130">How to measure</span></span>

* <span data-ttu-id="63dde-131">Диаграмма частоты кадров в реальном времени предоставляется на [портале устройств Windows](using-the-windows-device-portal.md#system-performance) в разделе "производительность системы".</span><span class="sxs-lookup"><span data-stu-id="63dde-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="63dde-132">Для отладки разработки добавьте в приложение счетчик диагностики частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="63dde-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="63dde-133">Пример счетчика см. в разделе ресурсы.</span><span class="sxs-lookup"><span data-stu-id="63dde-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="63dde-134">При этом на устройстве могут возникать частоты кадров, пока приложение работает, перемещая головную часть в сторону.</span><span class="sxs-lookup"><span data-stu-id="63dde-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="63dde-135">Если в голограмме отображается непредвиденное движение с нарушением колебаний, то, скорее всего, причиной является низкая частота кадров или уровень стабильности.</span><span class="sxs-lookup"><span data-stu-id="63dde-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-136">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-136">Recommendations</span></span>

* <span data-ttu-id="63dde-137">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="63dde-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="63dde-138">Изменения, которые требуют сброса в частоте кадров, должны оцениваться и надлежащим образом разрешаться как ошибки производительности.</span><span class="sxs-lookup"><span data-stu-id="63dde-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-139">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-140">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-140">Documentation</span></span>

* [<span data-ttu-id="63dde-141">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="63dde-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="63dde-142">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="63dde-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="63dde-143">Бюджет производительности активов</span><span class="sxs-lookup"><span data-stu-id="63dde-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="63dde-144">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-145">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-145">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-146">Набор средств для смешанной реальности, отображение счетчика кадров/с</span><span class="sxs-lookup"><span data-stu-id="63dde-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="63dde-147">Набор средств для смешанной реальности, шейдеры</span><span class="sxs-lookup"><span data-stu-id="63dde-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="63dde-148">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="63dde-148">External references</span></span>

* [<span data-ttu-id="63dde-149">Unity, оптимизация мобильных приложений</span><span class="sxs-lookup"><span data-stu-id="63dde-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="63dde-150">Стабильность голограммы</span><span class="sxs-lookup"><span data-stu-id="63dde-150">Hologram stability</span></span>

<span data-ttu-id="63dde-151">Стабильные голограммы повышают удобство использования и белиевабилити приложения и создают более удобное для пользователя удобство просмотра.</span><span class="sxs-lookup"><span data-stu-id="63dde-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="63dde-152">Качество стабильной работы является результатом хорошей разработки приложений и способности устройства понять (отслеживанию) его среды.</span><span class="sxs-lookup"><span data-stu-id="63dde-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="63dde-153">Хотя Частота кадров — первый основополагающий уровень стабильности, другие факторы могут повлиять на стабильность, включая:</span><span class="sxs-lookup"><span data-stu-id="63dde-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="63dde-154">Использование плоскости стабилизации</span><span class="sxs-lookup"><span data-stu-id="63dde-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="63dde-155">Расстояние до пространственных привязок</span><span class="sxs-lookup"><span data-stu-id="63dde-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="63dde-156">Отслеживание</span><span class="sxs-lookup"><span data-stu-id="63dde-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-157">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-160">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-161">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-161">Quality criteria</span></span>

|  <span data-ttu-id="63dde-162">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-162">Best</span></span>  |  <span data-ttu-id="63dde-163">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-163">Meets</span></span> |  <span data-ttu-id="63dde-164">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-165">Голограммы согласованно выглядят стабильно.</span><span class="sxs-lookup"><span data-stu-id="63dde-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="63dde-166">В дополнительном содержимом показано непредвиденное перемещение; или непредвиденное перемещение не помешать работе приложения.</span><span class="sxs-lookup"><span data-stu-id="63dde-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="63dde-167">Основное содержимое в кадре показывает неожиданное перемещение.</span><span class="sxs-lookup"><span data-stu-id="63dde-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="63dde-168">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-168">How to measure</span></span>

<span data-ttu-id="63dde-169">Людьми устройство и просматривая его работу:</span><span class="sxs-lookup"><span data-stu-id="63dde-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="63dde-170">Переместите заголовок с боковой стороны на сторону.</span><span class="sxs-lookup"><span data-stu-id="63dde-170">Move your head from side to side.</span></span> <span data-ttu-id="63dde-171">Если на голограммах отображается непредвиденное перемещение, то вероятная причина может быть вызвана низкой частотой кадров или неправильным выравниванием плоскости стабильности.</span><span class="sxs-lookup"><span data-stu-id="63dde-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="63dde-172">Перемещайтесь по голограммам и окружениям, ищите такие варианты поведения, как дорожки и «переход».</span><span class="sxs-lookup"><span data-stu-id="63dde-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="63dde-173">Этот тип движения, скорее всего, вызван тем, что устройство не отслеживает среду или расстояние до пространственной привязки.</span><span class="sxs-lookup"><span data-stu-id="63dde-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="63dde-174">Если в кадре находятся большие или несколько голограмм, обратите внимание на поведение голограммы с различной глубиной при перемещении головной позиции с стороны в сторону, если шакинесс, вероятно, это вызвано плоскостью стабилизации.</span><span class="sxs-lookup"><span data-stu-id="63dde-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-175">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-175">Recommendations</span></span>

* <span data-ttu-id="63dde-176">Добавьте счетчик частоты кадров в начале работы по разработке.</span><span class="sxs-lookup"><span data-stu-id="63dde-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="63dde-177">Используйте плоскость стабилизации.</span><span class="sxs-lookup"><span data-stu-id="63dde-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="63dde-178">Всегда Визуализируйте закрепленные голограммы в пределах 3 метров их привязки.</span><span class="sxs-lookup"><span data-stu-id="63dde-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="63dde-179">Убедитесь, что ваша среда настроена для правильного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="63dde-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="63dde-180">Создайте свой опыт, чтобы избежать голограмм с различными уровнями фокусной глубины внутри рамки.</span><span class="sxs-lookup"><span data-stu-id="63dde-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-181">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-182">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-182">Documentation</span></span>

* [<span data-ttu-id="63dde-183">Голограмма, стабильность и частота кадров</span><span class="sxs-lookup"><span data-stu-id="63dde-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="63dde-184">Пример использования с плоскостью стабилизации</span><span class="sxs-lookup"><span data-stu-id="63dde-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="63dde-185">Основные сведения о производительности смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="63dde-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="63dde-186">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="63dde-187">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="63dde-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="63dde-188">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="63dde-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="63dde-189">Стационарная рамка ссылки</span><span class="sxs-lookup"><span data-stu-id="63dde-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-190">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-190">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-191">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="63dde-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="63dde-192">Расположение голограмм на реальных поверхностях</span><span class="sxs-lookup"><span data-stu-id="63dde-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="63dde-193">Неверное выравнивание голограмм с физическими объектами (если предполагается, что они помещаются в связи друг с другом) — это четкое указание на не объединение голограмм и реальных.</span><span class="sxs-lookup"><span data-stu-id="63dde-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="63dde-194">Точность размещения должна относиться к потребностям сценария. Например, при размещении в общей области можно использовать пространственное соответствие, но более точное размещение потребует использования маркеров и калибровки.</span><span class="sxs-lookup"><span data-stu-id="63dde-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-195">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-198">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-199">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-199">Quality criteria</span></span>

|  <span data-ttu-id="63dde-200">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-200">Best</span></span>  |  <span data-ttu-id="63dde-201">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-201">Meets</span></span> |  <span data-ttu-id="63dde-202">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="63dde-203">Голограммы выводятся на поверхность, как правило, в диапазоне от сантиметров до сантиметров.</span><span class="sxs-lookup"><span data-stu-id="63dde-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="63dde-204">Если вам требуется более высокая точность, приложение должно предоставить эффективные средства для совместной работы в спецификации приложения.</span><span class="sxs-lookup"><span data-stu-id="63dde-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="63dde-205">Н/Д</span><span class="sxs-lookup"><span data-stu-id="63dde-205">NA</span></span> | <span data-ttu-id="63dde-206">Голограммы выводятся без согласования с физическим целевым объектом путем его разрыва или появления в плавающей области.</span><span class="sxs-lookup"><span data-stu-id="63dde-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="63dde-207">Если требуется точность, голограммы должны соответствовать спецификации близости в сценарии.</span><span class="sxs-lookup"><span data-stu-id="63dde-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-208">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-208">How to measure</span></span>

* <span data-ttu-id="63dde-209">Голограммы, размещенные на пространственной карте, не должны отображаться, чтобы сильно переходилось выше или ниже поверхности.</span><span class="sxs-lookup"><span data-stu-id="63dde-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="63dde-210">Голограммы, для которых требуется точное размещение, должны иметь некоторую форму системы маркеров и калибровки, точную для требования сценария.</span><span class="sxs-lookup"><span data-stu-id="63dde-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-211">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-211">Recommendations</span></span>

* <span data-ttu-id="63dde-212">Пространственное соответствие удобно использовать для размещения объектов на поверхностях, когда точность не требуется.</span><span class="sxs-lookup"><span data-stu-id="63dde-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="63dde-213">Для наилучшей точности используйте маркеры или афиши, чтобы задать голограммы и контроллер Xbox (или какой-либо механизм выравнивания вручную) для окончательной калибровки.</span><span class="sxs-lookup"><span data-stu-id="63dde-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="63dde-214">Рассмотрите возможность разбиения очень больших голограмм на логические части и согласования каждой части с поверхностью.</span><span class="sxs-lookup"><span data-stu-id="63dde-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="63dde-215">Неправильное задание расстояния интерпупиллари (IPD) также может влиять на выравнивание голограмм.</span><span class="sxs-lookup"><span data-stu-id="63dde-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="63dde-216">Всегда настраивайте HoloLens для пользователя IPD.</span><span class="sxs-lookup"><span data-stu-id="63dde-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-217">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-218">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-218">Documentation</span></span>

* [<span data-ttu-id="63dde-219">Размещение пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="63dde-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="63dde-220">Процесс сканирования комнаты</span><span class="sxs-lookup"><span data-stu-id="63dde-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="63dde-221">Рекомендации по пространственной привязке</span><span class="sxs-lookup"><span data-stu-id="63dde-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="63dde-222">Обработка ошибок отслеживания</span><span class="sxs-lookup"><span data-stu-id="63dde-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="63dde-223">Пространственное сопоставление в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="63dde-224">Общие сведения о разработке вуфориа</span><span class="sxs-lookup"><span data-stu-id="63dde-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-225">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-225">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-226">MR Toolkit, библиотеки пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="63dde-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="63dde-227">Комплект поставки пакета MR, пример калибровки афиши</span><span class="sxs-lookup"><span data-stu-id="63dde-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="63dde-228">Пакет, сопровождающий MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="63dde-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="63dde-229">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="63dde-229">External references</span></span>

* [<span data-ttu-id="63dde-230">Ловес пример, выравнивание точности</span><span class="sxs-lookup"><span data-stu-id="63dde-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="63dde-231">Просмотр зоны отдыха</span><span class="sxs-lookup"><span data-stu-id="63dde-231">Viewing zone of comfort</span></span>

<span data-ttu-id="63dde-232">Разработчики приложений контролируют, где соходят глаза пользователей, размещая содержимое и голограммы с различной глубиной.</span><span class="sxs-lookup"><span data-stu-id="63dde-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="63dde-233">Пользователи людьми HoloLens всегда будут иметь доступ к 2,0 м для поддержания четкого образа, так как отображение HoloLens фиксировано на оптическом расстоянии примерно 2,0 м от пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="63dde-234">Неправильная глубина содержимого может привести к появлению Visual дискомфорт или выносливости.</span><span class="sxs-lookup"><span data-stu-id="63dde-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-235">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-238">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-239">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="63dde-240">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="63dde-241">Поместите содержимое в 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="63dde-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="63dde-242">Если не удается разместить голограммы на 2 м, а конфликты между конвергенцией и проживанием не могут быть устранены, оптимальная зона для размещения с голограммами составляет от 1,25 м до 5 м.</span><span class="sxs-lookup"><span data-stu-id="63dde-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="63dde-243">В каждом случае разработчики должны структурировать содержимое, чтобы рекомендовать пользователям взаимодействовать с 1 + m (например, настроить размер содержимого и параметры размещения по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="63dde-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="63dde-244">Если не требуется в сценарии, следует реализовать плоскость отсечения с эффектом затухания, начинающейся с 1 м.</span><span class="sxs-lookup"><span data-stu-id="63dde-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="63dde-245">В случаях, когда требуется более внимательное наблюдение за голограммой мотионлесс, содержимое не должно быть ближе к 50 cm.</span><span class="sxs-lookup"><span data-stu-id="63dde-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="63dde-246">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-246">Meets</span></span></td><td> <span data-ttu-id="63dde-247">Содержимое находится в рамках руководства по просмотру и перемещению, но неверно использует или не использует плоскость обрезки.</span><span class="sxs-lookup"><span data-stu-id="63dde-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="63dde-248">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-248">Fail</span></span> </td><td> <span data-ttu-id="63dde-249">Содержимое представлено слишком близко (обычно &lt; 1,25 м или &lt; 50 cm для стационарных голограмм, для которых необходимо более внимательное наблюдение).</span><span class="sxs-lookup"><span data-stu-id="63dde-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="63dde-250">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-250">How to measure</span></span>

* <span data-ttu-id="63dde-251">Обычно содержимое должно быть равно 2 m, но не выше 1,25 или более 5 м.</span><span class="sxs-lookup"><span data-stu-id="63dde-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="63dde-252">За некоторыми исключениями расстояние отсечения HoloLens должно быть установлено в 85CM с исчезновением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="63dde-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="63dde-253">Допишитесь на содержимое и обратите внимание на эффекты обтравочной плоскости.</span><span class="sxs-lookup"><span data-stu-id="63dde-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="63dde-254">Стационарное содержимое не должно быть ближе к 50 cm.</span><span class="sxs-lookup"><span data-stu-id="63dde-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-255">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-255">Recommendations</span></span>

* <span data-ttu-id="63dde-256">Создайте содержимое для оптимального расстояния при просмотре 2 МБ.</span><span class="sxs-lookup"><span data-stu-id="63dde-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="63dde-257">Установите расстояние прорисовки отсечения равным 85 cm с исчезновением содержимого, начиная с 1 МБ.</span><span class="sxs-lookup"><span data-stu-id="63dde-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="63dde-258">Для стационарных голограмм, для которых требуется более близкое к просмотру, плоскость обрезки должна быть не меньше 30 см, а эффект затухания должен начинаться не менее чем на 10 сантиметров с плоскости обрезки.</span><span class="sxs-lookup"><span data-stu-id="63dde-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-259">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-259">Resources</span></span>

* [<span data-ttu-id="63dde-260">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="63dde-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="63dde-261">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="63dde-262">Эксперименты с масштабом</span><span class="sxs-lookup"><span data-stu-id="63dde-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="63dde-263">Текст, рекомендуемый размер шрифта</span><span class="sxs-lookup"><span data-stu-id="63dde-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="63dde-264">Переключение глубины</span><span class="sxs-lookup"><span data-stu-id="63dde-264">Depth switching</span></span>

<span data-ttu-id="63dde-265">Независимо от способа просмотра зоны проблем, требования пользователя к частому или быстрому переключению между ближайшими и далекими объектами (включая голограммы и реальное содержимое) могут привести к окуломотор выносливости и общему дискомфорт.</span><span class="sxs-lookup"><span data-stu-id="63dde-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-266">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-269">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-269">✔️</span></span></td>
        <td><span data-ttu-id="63dde-270">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-271">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-271">Quality criteria</span></span>

|  <span data-ttu-id="63dde-272">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-272">Best</span></span>  |  <span data-ttu-id="63dde-273">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-273">Meets</span></span> |  <span data-ttu-id="63dde-274">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-275">Ограниченное или естественное изменение глубины, которое не приводит к неестественному переключению пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="63dde-276">Параметр с внезапной глубиной является базовым и разрабатывается в процессе работы приложения или с внезапной глубиной, вызванной непредвиденным реальным содержимым.</span><span class="sxs-lookup"><span data-stu-id="63dde-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="63dde-277">Постоянный переключатель глубины или внезапное переключение глубины, которое не требуется или является ядром для работы приложения.</span><span class="sxs-lookup"><span data-stu-id="63dde-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-278">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-278">How to measure</span></span>

* <span data-ttu-id="63dde-279">Если приложение требует, чтобы пользователь постоянно или резко изменил фокус глубины, существует проблема переключения глубины.</span><span class="sxs-lookup"><span data-stu-id="63dde-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-280">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-280">Recommendations</span></span>

* <span data-ttu-id="63dde-281">Сделайте основной контент на согласованной плоскости, убедитесь, что плоскость стабилизации соответствует фокальной плоскости.</span><span class="sxs-lookup"><span data-stu-id="63dde-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="63dde-282">Это позволит сократить окуломотор выносливости и неожиданное перемещение голограмм.</span><span class="sxs-lookup"><span data-stu-id="63dde-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-283">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-283">Resources</span></span>

* [<span data-ttu-id="63dde-284">Расстояние визуализации</span><span class="sxs-lookup"><span data-stu-id="63dde-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="63dde-285">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="63dde-286">Использование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="63dde-286">Use of spatial sound</span></span>

<span data-ttu-id="63dde-287">В Windows Mixed Reality подсистема аудио предоставляет компонент Аурал в режиме смешанной реальности, имитируя трехмерный звук с помощью направления, расстояния и моделирования окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="63dde-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="63dde-288">Использование пространственного звука в приложении позволяет разработчикам убедительно размещать звуки в трехмерном пространстве (Sphere) вокруг пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="63dde-289">Эти звуки будут выглядеть так, как будто они поступают от реальных физических объектов или голограмм в смешанной реальности в окружающей среде пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="63dde-290">Пространственный звук — это мощный инструмент для погружения, специальных возможностей и разработки UX в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="63dde-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-291">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-294">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-294">✔️</span></span></td>
        <td><span data-ttu-id="63dde-295">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-296">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-296">Quality criteria</span></span>

|  <span data-ttu-id="63dde-297">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-297">Best</span></span>  |  <span data-ttu-id="63dde-298">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-298">Meets</span></span> |  <span data-ttu-id="63dde-299">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-300">Звук логически пространственно, а UX соответствующим образом использует звук, чтобы помочь в обнаружении объектов и отзыве пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="63dde-301">Звук является естественным и относится к объектам и нормализуется в рамках сценария.</span><span class="sxs-lookup"><span data-stu-id="63dde-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="63dde-302">Пространственный звук используется соответствующим образом для белиевабилити, но отсутствует как средство для получения отзывов пользователей и возможности обнаружения.</span><span class="sxs-lookup"><span data-stu-id="63dde-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="63dde-303">Звук не пространственно, как ожидалось, и (или) недостаток звука, чтобы помочь пользователю в его интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="63dde-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="63dde-304">Или пространственный звук не рассматривался или не используется в проектировании сценария.</span><span class="sxs-lookup"><span data-stu-id="63dde-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-305">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-305">How to measure</span></span>

* <span data-ttu-id="63dde-306">Как правило, соответствующие звуки должны выдаваться из голограмм (например, лайного звука, поступающего от Holographic.)</span><span class="sxs-lookup"><span data-stu-id="63dde-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="63dde-307">Звуковые подсказки следует использовать по всему внешнему интерфейсу, чтобы помочь пользователю в отзыве или осведомлении о действиях, выходящих за рамки Holographic.</span><span class="sxs-lookup"><span data-stu-id="63dde-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-308">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-308">Recommendations</span></span>

* <span data-ttu-id="63dde-309">Используйте Пространственный звук для помощи с обнаружением объектов и пользовательскими интерфейсами.</span><span class="sxs-lookup"><span data-stu-id="63dde-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="63dde-310">Реальные звуки работают лучше, чем синтезированный или неестественный звук.</span><span class="sxs-lookup"><span data-stu-id="63dde-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="63dde-311">Большинство звуков должно быть пространственно.</span><span class="sxs-lookup"><span data-stu-id="63dde-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="63dde-312">Избегайте невидимых передатчиков.</span><span class="sxs-lookup"><span data-stu-id="63dde-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="63dde-313">Избегайте использования пространственных масок.</span><span class="sxs-lookup"><span data-stu-id="63dde-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="63dde-314">Нормализовать все звуки.</span><span class="sxs-lookup"><span data-stu-id="63dde-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-315">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-316">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-316">Documentation</span></span>

* [<span data-ttu-id="63dde-317">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="63dde-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="63dde-318">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="63dde-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="63dde-319">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="63dde-320">Пример использования: Пространственный звук для Холотаур</span><span class="sxs-lookup"><span data-stu-id="63dde-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="63dde-321">Пример использования пространственного звука в Робораид</span><span class="sxs-lookup"><span data-stu-id="63dde-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-322">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-322">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-323">Набор средств для смешанной реальности — Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="63dde-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="63dde-324">Фокус на границах в holographic кадрах (фов)</span><span class="sxs-lookup"><span data-stu-id="63dde-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="63dde-325">Хорошо спроектированное взаимодействие с пользователем может создать и поддерживать полезный контекст виртуальной среды, который будет расширяться вокруг пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="63dde-326">Устранение последствий границ фов заключается в продуманном проектировании масштабирования и контекста содержимого, использовании пространственных аудио, руководств и расположения пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="63dde-327">Если вы сделали это правильно, то у пользователя будет меньше ограничений, чем границы фов, и удобство работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="63dde-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-328">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-331">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-332">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-332">Quality criteria</span></span>

|  <span data-ttu-id="63dde-333">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-333">Best</span></span>  |  <span data-ttu-id="63dde-334">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-334">Meets</span></span> |  <span data-ttu-id="63dde-335">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-336">Пользователь никогда не теряет контекст и не может его просматривать.</span><span class="sxs-lookup"><span data-stu-id="63dde-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="63dde-337">Для больших объектов предоставляется помощь по контексту.</span><span class="sxs-lookup"><span data-stu-id="63dde-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="63dde-338">Для объектов за пределами фрейма предоставляется возможность обнаружения и просмотра.</span><span class="sxs-lookup"><span data-stu-id="63dde-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="63dde-339">Как правило, проектирование движения и масштабирование голограмм подходят для удобства просмотра.</span><span class="sxs-lookup"><span data-stu-id="63dde-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="63dde-340">Пользователь никогда не теряет контекст, но в ограниченных ситуациях может потребоваться дополнительный перенос горловины.</span><span class="sxs-lookup"><span data-stu-id="63dde-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="63dde-341">В ограниченных ситуациях масштаб приводит к тому, что голограммы нарушают вертикальную или горизонтальную рамку, что вызывает некоторое движение горловины для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="63dde-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="63dde-342">Пользователь, вероятно, потеряет контекст и (или) одинаковое движение горловины необходимо для просмотра голограмм.</span><span class="sxs-lookup"><span data-stu-id="63dde-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="63dde-343">Нет руководства по контексту для больших holographic объектов, перемещение объектов, которые легко потерять за пределами рамки без рекомендаций по обнаружению или высоких голограмм, требует регулярного движения горловины для просмотра.</span><span class="sxs-lookup"><span data-stu-id="63dde-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-344">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-344">How to measure</span></span>

* <span data-ttu-id="63dde-345">Контекст для (большой) голограммы потерян или не распознан из-за усечения в границах.</span><span class="sxs-lookup"><span data-stu-id="63dde-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="63dde-346">Расположение голограмм трудно найти в связи с отсутствием менеджеров по обучению или содержимым, которое быстро перемещается в holographic кадр и из него.</span><span class="sxs-lookup"><span data-stu-id="63dde-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="63dde-347">В сценарии требуется регулярное и повторяющееся движение головного движения, чтобы полностью увидеть голограмму, полученную в результате выносливости горловины.</span><span class="sxs-lookup"><span data-stu-id="63dde-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-348">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-348">Recommendations</span></span>

* <span data-ttu-id="63dde-349">Начните работу с небольшими объектами, которые соответствуют фов, а затем переходите с визуальными подсказками в более крупные версии.</span><span class="sxs-lookup"><span data-stu-id="63dde-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="63dde-350">Воспользуйтесь пространственными советами и директорами внимания, чтобы помочь пользователям найти содержимое, находящееся за пределами фов.</span><span class="sxs-lookup"><span data-stu-id="63dde-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="63dde-351">По возможности старайтесь не использовать голограммы, которые обфовся по вертикали.</span><span class="sxs-lookup"><span data-stu-id="63dde-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="63dde-352">Предоставьте пользователю рекомендации в приложении для наилучшего расположения для просмотра.</span><span class="sxs-lookup"><span data-stu-id="63dde-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-353">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-354">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-354">Documentation</span></span>

* [<span data-ttu-id="63dde-355">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="63dde-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="63dde-356">Пример внедрения, Холостудио пользовательского интерфейса и разработки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="63dde-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="63dde-357">Масштабирование объектов и сред</span><span class="sxs-lookup"><span data-stu-id="63dde-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="63dde-358">Курсоры, визуальные подсказки</span><span class="sxs-lookup"><span data-stu-id="63dde-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="63dde-359">Внешние ссылки</span><span class="sxs-lookup"><span data-stu-id="63dde-359">External references</span></span>

* [<span data-ttu-id="63dde-360">Множество ADO о фов</span><span class="sxs-lookup"><span data-stu-id="63dde-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="63dde-361">Содержимое реагирует на расположение пользователя</span><span class="sxs-lookup"><span data-stu-id="63dde-361">Content reacts to user position</span></span>

<span data-ttu-id="63dde-362">Голограммы должны реагировать на пользовательскую точку примерно так же, как и «реальные» объекты.</span><span class="sxs-lookup"><span data-stu-id="63dde-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="63dde-363">Важным аспектом разработки являются элементы пользовательского интерфейса, которые не обязательно предполагают, что положение пользователя является стационарным и адаптируется к перемещению пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="63dde-364">Проектирование приложения, которое правильно адаптируется к положению пользователей, приведет к более белиевабленому интерфейсу и упрощению его использования.</span><span class="sxs-lookup"><span data-stu-id="63dde-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-365">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-368">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-368">✔️</span></span></td>
        <td><span data-ttu-id="63dde-369">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-370">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="63dde-371">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-371">Best</span></span> </td><td> <span data-ttu-id="63dde-372">Содержимое и пользовательский интерфейс адаптируются к позициям пользователей, что позволяет пользователю естественным образом взаимодействовать с содержимым в области ожидаемого перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="63dde-373">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-373">Meets</span></span> </td><td> <span data-ttu-id="63dde-374">Пользовательский интерфейс адаптируется к положению пользователя, но может препятствовать просмотру содержимого ключа, в соответствии с которым пользователь должен изменить свое расположение.</span><span class="sxs-lookup"><span data-stu-id="63dde-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="63dde-375">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="63dde-376">Элементы пользовательского интерфейса теряются или блокируются во время перемещения, что приводит к неестественному возврату элементов управления (или поиска).</span><span class="sxs-lookup"><span data-stu-id="63dde-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="63dde-377">Элементы пользовательского интерфейса ограничивают представление основного содержимого.</span><span class="sxs-lookup"><span data-stu-id="63dde-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="63dde-378">Перемещение пользовательского интерфейса не оптимизировано для просмотра расстояния и длительности, особенно с элементами пользовательского интерфейса, <a href="../../design/billboarding-and-tag-along.md">основанными на тегах</a> .</span><span class="sxs-lookup"><span data-stu-id="63dde-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="63dde-379">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-379">How to measure</span></span>

* <span data-ttu-id="63dde-380">Все измерения должны выполняться в разумной области сценария.</span><span class="sxs-lookup"><span data-stu-id="63dde-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="63dde-381">В то время как перемещение пользователя будет разным, не пытайтесь заставить приложение использовать экстремальное перемещение пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="63dde-382">Для элементов пользовательского интерфейса соответствующие элементы управления должны быть доступны независимо от перемещения пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="63dde-383">Например, если пользователь просматривает трехмерную карту и обходит ее с помощью масштаба, элемент управления масштабом должен быть доступен пользователю независимо от расположения.</span><span class="sxs-lookup"><span data-stu-id="63dde-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-384">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-384">Recommendations</span></span>

* <span data-ttu-id="63dde-385">Пользователь является камерой и управляет движением.</span><span class="sxs-lookup"><span data-stu-id="63dde-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="63dde-386">Позвольте им управлять.</span><span class="sxs-lookup"><span data-stu-id="63dde-386">Let them drive.</span></span>
* <span data-ttu-id="63dde-387">Рассмотрите возможность объявления для систем с текстом и меню, которые в противном случае были бы заблокированы или скрыты, если бы пользователь мог переместиться по всему миру.</span><span class="sxs-lookup"><span data-stu-id="63dde-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="63dde-388">Используйте тег для содержимого, которое должно следовать за пользователем, не позволяя пользователю видеть, что находится перед ними.</span><span class="sxs-lookup"><span data-stu-id="63dde-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-389">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-390">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-390">Documentation</span></span>

* [<span data-ttu-id="63dde-391">Проектирование взаимодействия</span><span class="sxs-lookup"><span data-stu-id="63dde-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="63dde-392">Цвет, освещение и материал</span><span class="sxs-lookup"><span data-stu-id="63dde-392">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="63dde-393">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="63dde-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="63dde-394">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="63dde-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="63dde-395">Движение и перемещение</span><span class="sxs-lookup"><span data-stu-id="63dde-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="63dde-396">Ясность взаимодействия ввода</span><span class="sxs-lookup"><span data-stu-id="63dde-396">Input interaction clarity</span></span>

<span data-ttu-id="63dde-397">Точность входных данных очень важна для удобства использования приложения и включает согласованность входных данных, подход, возможность обнаружения методов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="63dde-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="63dde-398">Пользователь может использовать общие взаимодействия всей платформы без повторной информации.</span><span class="sxs-lookup"><span data-stu-id="63dde-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="63dde-399">Если приложение имеет пользовательский ввод, оно должно быть четко Отправлено и показано.</span><span class="sxs-lookup"><span data-stu-id="63dde-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-400">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-403">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-403">✔️</span></span></td>
        <td><span data-ttu-id="63dde-404">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-405">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-405">Quality criteria</span></span>

|  <span data-ttu-id="63dde-406">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-406">Best</span></span>  |  <span data-ttu-id="63dde-407">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-407">Meets</span></span> |  <span data-ttu-id="63dde-408">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-409">Методы взаимодействия ввода согласованы с предоставленными [рекомендациями](../../design/interaction-fundamentals.md)Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="63dde-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="63dde-410">Любые пользовательские входные данные не должны быть избыточными со стандартным входом (вместо использования стандартного взаимодействия) и должны быть четко переданы и продемонстрированы пользователю.</span><span class="sxs-lookup"><span data-stu-id="63dde-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="63dde-411">Похоже на лучшее, но пользовательские входные данные избыточны со стандартными методами ввода.</span><span class="sxs-lookup"><span data-stu-id="63dde-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="63dde-412">Пользователь по-прежнему может достигнуть цели и проделать ход работы с приложением.</span><span class="sxs-lookup"><span data-stu-id="63dde-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="63dde-413">Трудно понять сопоставление метода ввода или кнопки.</span><span class="sxs-lookup"><span data-stu-id="63dde-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="63dde-414">Входные данные сильно настроены, не поддерживают стандартные входные данные, нет инструкций или, вероятно, не вызывают выносливости и комфортные проблемы.</span><span class="sxs-lookup"><span data-stu-id="63dde-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-415">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-415">How to measure</span></span>

* <span data-ttu-id="63dde-416">Приложение использует последовательные [стандартные методы ввода.](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="63dde-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="63dde-417">Если приложение имеет пользовательский ввод, оно четко взаимодействует с помощью:</span><span class="sxs-lookup"><span data-stu-id="63dde-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="63dde-418">Интерфейс первого запуска</span><span class="sxs-lookup"><span data-stu-id="63dde-418">First-run experience</span></span>
* <span data-ttu-id="63dde-419">Начальные экраны</span><span class="sxs-lookup"><span data-stu-id="63dde-419">Introductory screens</span></span>
* <span data-ttu-id="63dde-420">Подсказки</span><span class="sxs-lookup"><span data-stu-id="63dde-420">Tooltips</span></span>
* <span data-ttu-id="63dde-421">Обучающая рука</span><span class="sxs-lookup"><span data-stu-id="63dde-421">Hand coach</span></span>
* <span data-ttu-id="63dde-422">Раздел справки</span><span class="sxs-lookup"><span data-stu-id="63dde-422">Help section</span></span>
* <span data-ttu-id="63dde-423">Голосовая связь через</span><span class="sxs-lookup"><span data-stu-id="63dde-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-424">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-424">Recommendations</span></span>

* <span data-ttu-id="63dde-425">По возможности используйте стандартные методы ввода.</span><span class="sxs-lookup"><span data-stu-id="63dde-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="63dde-426">Предоставление демонстраций, учебников и подсказок для нестандартных методов ввода.</span><span class="sxs-lookup"><span data-stu-id="63dde-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="63dde-427">Используйте согласованную модель взаимодействия во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="63dde-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-428">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-429">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-429">Documentation</span></span>

* [<span data-ttu-id="63dde-430">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="63dde-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="63dde-431">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="63dde-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="63dde-432">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="63dde-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="63dde-433">Курсоры</span><span class="sxs-lookup"><span data-stu-id="63dde-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="63dde-434">Комфорт и взгляните</span><span class="sxs-lookup"><span data-stu-id="63dde-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="63dde-435">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="63dde-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="63dde-436">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="63dde-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="63dde-437">Руководство по переносу логики ввода для Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="63dde-438">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="63dde-439">Взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="63dde-440">Жесты и контроллеры движения в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-440">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="63dde-441">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-441">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="63dde-442">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="63dde-442">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="63dde-443">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="63dde-443">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="63dde-444">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="63dde-444">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="63dde-445">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="63dde-445">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-446">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-446">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-447">Пример использования: преимущества дополнительных персональных компьютеров</span><span class="sxs-lookup"><span data-stu-id="63dde-447">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="63dde-448">Исследование приведения: Холостудио пользовательского интерфейса и разработки взаимодействия</span><span class="sxs-lookup"><span data-stu-id="63dde-448">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="63dde-449">Пример приложения: периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="63dde-449">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="63dde-450">Пример приложения: Лунный модуль</span><span class="sxs-lookup"><span data-stu-id="63dde-450">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="63dde-451">Взаимодействующие объекты</span><span class="sxs-lookup"><span data-stu-id="63dde-451">Interactable objects</span></span>

<span data-ttu-id="63dde-452">Кнопка длиннее метафоры, используемой для активации события в 2D-абстрактном мире.</span><span class="sxs-lookup"><span data-stu-id="63dde-452">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="63dde-453">В мире объемной смешанной реальности мы больше не должны беспокоиться об этом мире абстракции.</span><span class="sxs-lookup"><span data-stu-id="63dde-453">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="63dde-454">Любой может быть взаимодействующим объектом, запускающим событие.</span><span class="sxs-lookup"><span data-stu-id="63dde-454">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="63dde-455">Взаимодействующий объект может быть представлен любым из чашк кофе в таблице в виде всплывающей подсказки, плавающей в воздухе.</span><span class="sxs-lookup"><span data-stu-id="63dde-455">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="63dde-456">Независимо от формы, взаимодействующие объекты должны быть четко распознаны пользователем с помощью визуальных и звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="63dde-456">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-457">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-457">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-460">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-460">✔️</span></span></td>
        <td><span data-ttu-id="63dde-461">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-461">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-462">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-462">Quality criteria</span></span>

|  <span data-ttu-id="63dde-463">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-463">Best</span></span>  |  <span data-ttu-id="63dde-464">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-464">Meets</span></span> |  <span data-ttu-id="63dde-465">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-465">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-466">Независимо от формы, взаимодействующие объекты распознаются через визуальные и звуковые подсказки в трех состояниях: бездействие, Целевая и выбранная.</span><span class="sxs-lookup"><span data-stu-id="63dde-466">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="63dde-467">«Видите ИТ-подсистемы» — ясно и постоянно используется в ходе работы.</span><span class="sxs-lookup"><span data-stu-id="63dde-467">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="63dde-468">Объекты масштабируются и распределяются для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="63dde-468">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="63dde-469">Пользователь может распознать объект как взаимодействующий через аудио или визуальный отзыв, а также нацелить и активировать объект.</span><span class="sxs-lookup"><span data-stu-id="63dde-469">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="63dde-470">Не имея визуальных или звуковых подсказок, пользователь не сможет распознать взаимодействующий объект.</span><span class="sxs-lookup"><span data-stu-id="63dde-470">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="63dde-471">Взаимодействия могут быть подвержены ошибкам из-за масштабирования объекта или расстояния между объектами.</span><span class="sxs-lookup"><span data-stu-id="63dde-471">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-472">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-472">How to measure</span></span>

* <span data-ttu-id="63dde-473">Взаимодействующие объекты распознаются как "взаимодействующие"; включая кнопки, меню и содержимое для конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="63dde-473">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="63dde-474">Как правило, при нацеливании на взаимодействующие объекты должны быть визуальными и звуковыми подсказками.</span><span class="sxs-lookup"><span data-stu-id="63dde-474">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-475">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-475">Recommendations</span></span>

* <span data-ttu-id="63dde-476">Использование визуальных и звуковых отзывов для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="63dde-476">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="63dde-477">Визуальная обратная связь должна различаться для каждого входящего состояния (неактивно, назначено, выбрано).</span><span class="sxs-lookup"><span data-stu-id="63dde-477">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="63dde-478">Взаимодействующие объекты должны масштабироваться и размещаться для обеспечения бесплатной нацеливания на ошибки.</span><span class="sxs-lookup"><span data-stu-id="63dde-478">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="63dde-479">Сгруппированные взаимодействующие объекты (например, строка меню или список) должны иметь достаточное пространство для нацеливания.</span><span class="sxs-lookup"><span data-stu-id="63dde-479">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="63dde-480">Кнопки и меню, поддерживающие голосовую команду, должны предоставлять текстовые метки для ключевого слова Command (см. раздел, например, ")".</span><span class="sxs-lookup"><span data-stu-id="63dde-480">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-481">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-481">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-482">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-482">Documentation</span></span>

* [<span data-ttu-id="63dde-483">Активный объект</span><span class="sxs-lookup"><span data-stu-id="63dde-483">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="63dde-484">Текст в Unity</span><span class="sxs-lookup"><span data-stu-id="63dde-484">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="63dde-485">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="63dde-485">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="63dde-486">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="63dde-486">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-487">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-487">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-488">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="63dde-488">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="63dde-489">Сканирование комнаты</span><span class="sxs-lookup"><span data-stu-id="63dde-489">Room scanning</span></span>

<span data-ttu-id="63dde-490">Приложения, для которых требуются данные пространственного сопоставления, полагаются на устройство для автоматического получения этих данных с течением времени и между сеансами по мере того, как пользователь исследует среду с активным устройством.</span><span class="sxs-lookup"><span data-stu-id="63dde-490">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="63dde-491">Полнота и качество этих данных зависит от ряда факторов, в том числе от количества выполненных пользователем проверок, времени, прошедших с момента исследования и того, были ли объекты, такие как мебель и дверцы, перемещены, так как устройство проверило эту область.</span><span class="sxs-lookup"><span data-stu-id="63dde-491">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="63dde-492">Многие приложения анализируют данные пространственного сопоставления в начале работы, чтобы определить, следует ли пользователю выполнять дополнительные действия, чтобы улучшить полноту и качество пространственной карты.</span><span class="sxs-lookup"><span data-stu-id="63dde-492">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="63dde-493">Если пользователь должен проверить окружение, при сканировании необходимо указать четкие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="63dde-493">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-494">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-494">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-497">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-497">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-498">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-498">Quality criteria</span></span>

|  <span data-ttu-id="63dde-499">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-499">Best</span></span>  |  <span data-ttu-id="63dde-500">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-500">Meets</span></span> |  <span data-ttu-id="63dde-501">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-501">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-502">Визуализация пространственной сети указывает, что выполняется проверка пользователей.</span><span class="sxs-lookup"><span data-stu-id="63dde-502">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="63dde-503">Пользователь четко знает, что делать и когда сканирование запускается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="63dde-503">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="63dde-504">Обеспечивается визуализация пространственной сетки, но пользователь может не ясно понять, что делать, а сведения о ходе выполнения не предоставляются.</span><span class="sxs-lookup"><span data-stu-id="63dde-504">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="63dde-505">Отсутствует визуализация сетки.</span><span class="sxs-lookup"><span data-stu-id="63dde-505">No visualization of mesh.</span></span> <span data-ttu-id="63dde-506">Пользователю не предоставлены сведения о том, где искать или когда начинается или останавливается проверка.</span><span class="sxs-lookup"><span data-stu-id="63dde-506">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="63dde-507">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-507">How to measure</span></span>

* <span data-ttu-id="63dde-508">При проверке необходимой комнаты предоставляются визуальное и звуковое руководство, указывающее, где искать, а когда запускать и прекращать сканирование.</span><span class="sxs-lookup"><span data-stu-id="63dde-508">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-509">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-509">Recommendations</span></span>

* <span data-ttu-id="63dde-510">Укажите, какая часть общего объема в области пользователей должна быть частью работы.</span><span class="sxs-lookup"><span data-stu-id="63dde-510">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="63dde-511">Взаимодействие при запуске и остановке сканирования, например индикатор выполнения.</span><span class="sxs-lookup"><span data-stu-id="63dde-511">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="63dde-512">Используйте визуализацию сетки во время сканирования.</span><span class="sxs-lookup"><span data-stu-id="63dde-512">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="63dde-513">Предоставьте визуальные и звуковые подсказки, чтобы дать пользователю возможность просматривать и перемещаться по комнате.</span><span class="sxs-lookup"><span data-stu-id="63dde-513">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="63dde-514">Сообщите пользователю, где можно усовершенствовать данные.</span><span class="sxs-lookup"><span data-stu-id="63dde-514">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="63dde-515">Во многих случаях лучше сообщить пользователю, что нужно сделать (например, Взгляните на центр мебели), чтобы получить необходимое качество сканирования.</span><span class="sxs-lookup"><span data-stu-id="63dde-515">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-516">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-516">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="63dde-517">Документация</span><span class="sxs-lookup"><span data-stu-id="63dde-517">Documentation</span></span>

* [<span data-ttu-id="63dde-518">Визуализация при сканировании комнаты</span><span class="sxs-lookup"><span data-stu-id="63dde-518">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="63dde-519">Пример использования: расширение возможностей пространственных сопоставлений HoloLens</span><span class="sxs-lookup"><span data-stu-id="63dde-519">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="63dde-520">Пример использования: схема пространственного звука для Холотаур</span><span class="sxs-lookup"><span data-stu-id="63dde-520">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="63dde-521">Пример использования: Создание иммерсивного интерфейса в фрагментах</span><span class="sxs-lookup"><span data-stu-id="63dde-521">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="63dde-522">Средства и учебники</span><span class="sxs-lookup"><span data-stu-id="63dde-522">Tools and tutorials</span></span>

* [<span data-ttu-id="63dde-523">Набор средств для смешанной реальности — UX</span><span class="sxs-lookup"><span data-stu-id="63dde-523">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="63dde-524">Индикаторы направления</span><span class="sxs-lookup"><span data-stu-id="63dde-524">Directional indicators</span></span>

<span data-ttu-id="63dde-525">В приложении для смешанной реальности содержимое может находиться за пределами поля View или перекрыто по реальным объектам.</span><span class="sxs-lookup"><span data-stu-id="63dde-525">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="63dde-526">Хорошо спроектированное приложение упростит пользователю поиск невидимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="63dde-526">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="63dde-527">Направленные индикаторы предупреждают пользователя о важном содержимом и предоставляют рекомендации по содержимому относительно положения пользователя.</span><span class="sxs-lookup"><span data-stu-id="63dde-527">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="63dde-528">Руководство по невидимому содержимому может принимать форму звуковых датчиков, стрелок направления или прямых визуальных подсказок.</span><span class="sxs-lookup"><span data-stu-id="63dde-528">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-529">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-529">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-532">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-532">✔️</span></span></td>
        <td><span data-ttu-id="63dde-533">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-533">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-534">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-534">Quality criteria</span></span>

|  <span data-ttu-id="63dde-535">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-535">Best</span></span>  |  <span data-ttu-id="63dde-536">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-536">Meets</span></span> |  <span data-ttu-id="63dde-537">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-537">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-538">Визуальные и звуковые подсказки непосредственно позволяют пользователю подходящее содержимое за пределами поля представления.</span><span class="sxs-lookup"><span data-stu-id="63dde-538">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="63dde-539">Стрелка или индикатор, указывающий на пользователя в общем направлении содержимого.</span><span class="sxs-lookup"><span data-stu-id="63dde-539">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="63dde-540">Соответствующее содержимое находится за пределами поля представления, и для пользователя не предоставляется никаких инструкций по расположению.</span><span class="sxs-lookup"><span data-stu-id="63dde-540">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="63dde-541">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-541">How to measure</span></span>

* <span data-ttu-id="63dde-542">Содержимое, соответствующее содержимому за пределами поля "пользователь", может быть обнаружено с помощью визуальных и (или) звуковых подсказок.</span><span class="sxs-lookup"><span data-stu-id="63dde-542">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-543">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-543">Recommendations</span></span>

* <span data-ttu-id="63dde-544">Если соответствующее содержимое находится вне поля зрения пользователя, используйте индикаторы направления и звуковые подсказки для указания пользователю содержимого.</span><span class="sxs-lookup"><span data-stu-id="63dde-544">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="63dde-545">Во многих случаях непосредственное визуальное направляющее предпочтительнее стрелок направления.</span><span class="sxs-lookup"><span data-stu-id="63dde-545">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="63dde-546">Индикаторы направления не должны быть встроены в курсор.</span><span class="sxs-lookup"><span data-stu-id="63dde-546">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-547">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-547">Resources</span></span>

* [<span data-ttu-id="63dde-548">Голографический кадр</span><span class="sxs-lookup"><span data-stu-id="63dde-548">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="63dde-549">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="63dde-549">Data loading</span></span>

<span data-ttu-id="63dde-550">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="63dde-550">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="63dde-551">Это может означать, что пользователь не может взаимодействовать с приложением, когда индикатор хода выполнения является видимым, а также может указать, как долго должно быть установлено время ожидания.</span><span class="sxs-lookup"><span data-stu-id="63dde-551">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="63dde-552">Воздействие на устройства</span><span class="sxs-lookup"><span data-stu-id="63dde-552">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="63dde-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="63dde-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="63dde-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="63dde-555">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-555">✔️</span></span></td>
        <td><span data-ttu-id="63dde-556">✔️</span><span class="sxs-lookup"><span data-stu-id="63dde-556">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="63dde-557">Критерии качества</span><span class="sxs-lookup"><span data-stu-id="63dde-557">Quality criteria</span></span>

|  <span data-ttu-id="63dde-558">Лучшее</span><span class="sxs-lookup"><span data-stu-id="63dde-558">Best</span></span>  |  <span data-ttu-id="63dde-559">Соответствующ</span><span class="sxs-lookup"><span data-stu-id="63dde-559">Meets</span></span> |  <span data-ttu-id="63dde-560">Ошибка</span><span class="sxs-lookup"><span data-stu-id="63dde-560">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="63dde-561">Анимированный визуальный индикатор в виде индикатора выполнения или кольца, отображающий ход выполнения во время загрузки или обработки данных.</span><span class="sxs-lookup"><span data-stu-id="63dde-561">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="63dde-562">Визуальный индикатор предоставляет рекомендации по продолжительности ожидания.</span><span class="sxs-lookup"><span data-stu-id="63dde-562">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="63dde-563">Пользователь уведомляется о том, что выполняется загрузка данных, но нет никакой информации о том, как долго может быть ожидание.</span><span class="sxs-lookup"><span data-stu-id="63dde-563">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="63dde-564">Ни один индикатор загрузки данных или процесса для задачи не занимает более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="63dde-564">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="63dde-565">Как измерять</span><span class="sxs-lookup"><span data-stu-id="63dde-565">How to measure</span></span>

* <span data-ttu-id="63dde-566">Во время загрузки данных убедитесь в отсутствии пустого состояния более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="63dde-566">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="63dde-567">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="63dde-567">Recommendations</span></span>

* <span data-ttu-id="63dde-568">Предоставьте аниматор загрузки данных в любой ситуации, когда пользователь может раскрывать это приложение о зависании или сбое.</span><span class="sxs-lookup"><span data-stu-id="63dde-568">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="63dde-569">Разумное правило для параметра Thumb — это любое действие "Загрузка", которое может занять более 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="63dde-569">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="63dde-570">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="63dde-570">Resources</span></span>

* [<span data-ttu-id="63dde-571">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="63dde-571">Displaying progress</span></span>](../../design/progress.md)
