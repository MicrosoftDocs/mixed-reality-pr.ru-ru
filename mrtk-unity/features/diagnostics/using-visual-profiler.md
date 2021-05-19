---
title: Использование Visual Profiler
description: Документация по использованию Visual Profiler в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143715"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="7f0e0-104">Использование Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="7f0e0-104">Using the visual profiler</span></span>

<span data-ttu-id="7f0e0-105">Висуалпрофилер предоставляет простое в использовании представление производительности приложения смешанной реальности в приложении.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="7f0e0-106">Профилировщик поддерживается на всех платформах набора средств смешанной реальности, включая:</span><span class="sxs-lookup"><span data-stu-id="7f0e0-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="7f0e0-107">Microsoft HoloLens (1-й общий)</span><span class="sxs-lookup"><span data-stu-id="7f0e0-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="7f0e0-108">Microsoft HoloLens 2;</span><span class="sxs-lookup"><span data-stu-id="7f0e0-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="7f0e0-109">Иммерсивные гарнитуры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7f0e0-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="7f0e0-110">OpenVR:</span><span class="sxs-lookup"><span data-stu-id="7f0e0-110">OpenVR</span></span>

<span data-ttu-id="7f0e0-111">При разработке приложения Сосредоточьтесь на нескольких частях сцены, так как Визуальный профилировщик отображает данные относительно текущего представления.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f0e0-112">Сосредоточьте внимание на частях сцены, используя сложные объекты, эффекты примитивов или действия.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="7f0e0-113">Эти и другие факторы часто способствуют снижению производительности приложения и менее оптимальному интерфейсу пользователя.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="7f0e0-114">Интерфейс Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="7f0e0-114">Visual profiler interface</span></span>

![Интерфейс Visual Profiler](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="7f0e0-116">В интерфейс Visual Profiler входят следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="7f0e0-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="7f0e0-117">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="7f0e0-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="7f0e0-118">Время кадра</span><span class="sxs-lookup"><span data-stu-id="7f0e0-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="7f0e0-119">Граф кадров</span><span class="sxs-lookup"><span data-stu-id="7f0e0-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="7f0e0-120">Использование памяти</span><span class="sxs-lookup"><span data-stu-id="7f0e0-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="7f0e0-121">Частота кадров</span><span class="sxs-lookup"><span data-stu-id="7f0e0-121">Frame rate</span></span>

<span data-ttu-id="7f0e0-122">В левом верхнем углу интерфейса находится частота кадров, измеряемая в кадрах в секунду.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="7f0e0-123">Для лучшего удобства работы пользователей это значение должно быть максимально высоким.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="7f0e0-124">Определенная платформа и конфигурация оборудования играют важную роль в максимальной достижимой частоте кадров.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="7f0e0-125">Ниже приведены некоторые общие целевые значения.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-125">Some common target values include:</span></span>

- <span data-ttu-id="7f0e0-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="7f0e0-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="7f0e0-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="7f0e0-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="7f0e0-128">Из-за [регулирования частоты кадров в HoloLens при активном ограничении по умолчанию](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)Визуальный профилировщик скрывает себя во время записи видео и фотографий.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="7f0e0-129">Этот параметр можно переопределить в системном профиле диагностики.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="7f0e0-130">Время кадра</span><span class="sxs-lookup"><span data-stu-id="7f0e0-130">Frame time</span></span>

<span data-ttu-id="7f0e0-131">Справа от частоты кадров — это время в миллисекундах, затраченное на загрузку ЦП.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="7f0e0-132">Чтобы достичь целевой частоты кадров, упомянутой ранее, приложение может потратить следующее количество времени на кадр:</span><span class="sxs-lookup"><span data-stu-id="7f0e0-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="7f0e0-133">60 кадров/с: 16,6 мс</span><span class="sxs-lookup"><span data-stu-id="7f0e0-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="7f0e0-134">90 кадров/с: 11,1 мс</span><span class="sxs-lookup"><span data-stu-id="7f0e0-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="7f0e0-135">Время GPU планируется добавить в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="7f0e0-136">Граф кадров</span><span class="sxs-lookup"><span data-stu-id="7f0e0-136">Frame graph</span></span>

<span data-ttu-id="7f0e0-137">Граф кадров обеспечивает графическое отображение журнала частоты кадров приложения.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![График пропущенного фрейма Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="7f0e0-139">При использовании приложения найдите пропущенные кадры, указывающие на то, что приложение не достигает его целевой частоты кадров и может потребовать оптимизации.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="7f0e0-140">Использование памяти</span><span class="sxs-lookup"><span data-stu-id="7f0e0-140">Memory utilization</span></span>

<span data-ttu-id="7f0e0-141">Отображение использования памяти позволяет легко понять, как текущее представление влияет на потребление памяти приложением.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Граф памяти Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="7f0e0-143">При использовании приложения найдите общий объем используемой памяти.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="7f0e0-144">Ключевые индикаторы включают в себя приближается к пределу памяти и быстрое изменение в использовании.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="7f0e0-145">Настройка визуального профилировщика</span><span class="sxs-lookup"><span data-stu-id="7f0e0-145">Customizing the visual profiler</span></span>

<span data-ttu-id="7f0e0-146">Внешний вид и поведение визуального профилировщика можно настраивать с помощью системного профиля диагностики.</span><span class="sxs-lookup"><span data-stu-id="7f0e0-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="7f0e0-147">Дополнительные сведения см. [в разделе Настройка системы диагностики](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="7f0e0-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f0e0-148">См. также</span><span class="sxs-lookup"><span data-stu-id="7f0e0-148">See also</span></span>

- [<span data-ttu-id="7f0e0-149">Система диагностики</span><span class="sxs-lookup"><span data-stu-id="7f0e0-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="7f0e0-150">Настройка системы диагностики</span><span class="sxs-lookup"><span data-stu-id="7f0e0-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)