---
title: Настройка диагностики
description: Документация по настройке диагностики в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121802"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="1d27c-104">Настройка системы диагностики</span><span class="sxs-lookup"><span data-stu-id="1d27c-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="1d27c-105">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="1d27c-105">General settings</span></span>

![Общие параметры диагностики](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="1d27c-107">Включить подробное ведение журнала</span><span class="sxs-lookup"><span data-stu-id="1d27c-107">Enable verbose logging</span></span>

<span data-ttu-id="1d27c-108">Указывает, будет ли включено подробное ведение журнала МРТК.</span><span class="sxs-lookup"><span data-stu-id="1d27c-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="1d27c-109">По умолчанию используется значение false, но его можно включить для получения подробных трассировок, позволяющих команде МРТК выполнять отладку и детализацию проблем.</span><span class="sxs-lookup"><span data-stu-id="1d27c-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="1d27c-110">Например, при возникновении проблемы подключение журналов проигрывателя Unity (из редактора или из проигрывателя) может помочь уменьшить источник ошибок и проблем.</span><span class="sxs-lookup"><span data-stu-id="1d27c-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="1d27c-111">Обратите внимание, что этот параметр не зависит от того, включена ли система диагностики. это отображается в системе диагностики, так как это параметр ведения журнала, но в конечном итоге работает на более высоком уровне, так как он влияет на ведение журнала всей базы кода МРТК.</span><span class="sxs-lookup"><span data-stu-id="1d27c-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="1d27c-112">Показать диагностику</span><span class="sxs-lookup"><span data-stu-id="1d27c-112">Show diagnostics</span></span>

<span data-ttu-id="1d27c-113">Указывает, должна ли система диагностики отображать настроенные параметры диагностики.</span><span class="sxs-lookup"><span data-stu-id="1d27c-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="1d27c-114">Если этот параметр отключен, все настроенные параметры диагностики будут скрыты.</span><span class="sxs-lookup"><span data-stu-id="1d27c-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="1d27c-115">Параметры профилировщика</span><span class="sxs-lookup"><span data-stu-id="1d27c-115">Profiler settings</span></span>

![Параметры профилировщика диагностики](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="1d27c-117">Отобразить профилировщик</span><span class="sxs-lookup"><span data-stu-id="1d27c-117">Show profiler</span></span>

<span data-ttu-id="1d27c-118">Указывает, следует ли отображать Визуальный профилировщик.</span><span class="sxs-lookup"><span data-stu-id="1d27c-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="1d27c-119">Частота выборки кадров</span><span class="sxs-lookup"><span data-stu-id="1d27c-119">Frame sample rate</span></span>

<span data-ttu-id="1d27c-120">Время в секундах, необходимое для получения кадров для вычисления частоты кадров.</span><span class="sxs-lookup"><span data-stu-id="1d27c-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="1d27c-121">Диапазон — от 0 до 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="1d27c-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="1d27c-122">Привязка окна</span><span class="sxs-lookup"><span data-stu-id="1d27c-122">Window anchor</span></span>

<span data-ttu-id="1d27c-123">К какой части порта представления следует привязать окно профилировщика.</span><span class="sxs-lookup"><span data-stu-id="1d27c-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="1d27c-124">Значение по умолчанию — ниже Center.</span><span class="sxs-lookup"><span data-stu-id="1d27c-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="1d27c-125">Смещение окна</span><span class="sxs-lookup"><span data-stu-id="1d27c-125">Window offset</span></span>

<span data-ttu-id="1d27c-126">Смещение от центра порта представления для размещения визуального профилировщика.</span><span class="sxs-lookup"><span data-stu-id="1d27c-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="1d27c-127">Смещение будет находиться в направлении свойства *привязки окна* .</span><span class="sxs-lookup"><span data-stu-id="1d27c-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="1d27c-128">Масштаб окна</span><span class="sxs-lookup"><span data-stu-id="1d27c-128">Window scale</span></span>

<span data-ttu-id="1d27c-129">Множитель размера, применяемый к окну профилировщика.</span><span class="sxs-lookup"><span data-stu-id="1d27c-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="1d27c-130">Например, установка значения 2 приведет к удвоению размера окна.</span><span class="sxs-lookup"><span data-stu-id="1d27c-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="1d27c-131">Скорость выполнения окна</span><span class="sxs-lookup"><span data-stu-id="1d27c-131">Window follow speed</span></span>

<span data-ttu-id="1d27c-132">Скорость перемещения окна профилировщика для поддержания видимости в пределах порта представления.</span><span class="sxs-lookup"><span data-stu-id="1d27c-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="1d27c-133">Программное управление системой диагностики</span><span class="sxs-lookup"><span data-stu-id="1d27c-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="1d27c-134">Также можно переключить видимость системы диагностики и профилировщика во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1d27c-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="1d27c-135">Например, приведенный ниже код будет скрывать систему диагностики и профилировщик.</span><span class="sxs-lookup"><span data-stu-id="1d27c-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="1d27c-136">См. также</span><span class="sxs-lookup"><span data-stu-id="1d27c-136">See also</span></span>

- [<span data-ttu-id="1d27c-137">Система диагностики</span><span class="sxs-lookup"><span data-stu-id="1d27c-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="1d27c-138">Использование Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="1d27c-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
