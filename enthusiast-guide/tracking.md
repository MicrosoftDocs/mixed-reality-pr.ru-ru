---
title: Отслеживание часто задаваемых вопросов
description: Отслеживание устранения неполадок Windows Mixed Reality, которые выходят за рамки стандартной документации по поддержке пользователей.
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, устранение неполадок, ошибки, Справка, поддержка, отслеживание
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725835"
---
# <a name="tracking-faqs"></a><span data-ttu-id="331b3-104">Отслеживание часто задаваемых вопросов</span><span class="sxs-lookup"><span data-stu-id="331b3-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="331b3-105">Моя гарнитура прекратила отслеживание</span><span class="sxs-lookup"><span data-stu-id="331b3-105">My headset has stopped tracking</span></span>

<span data-ttu-id="331b3-106">Убедитесь, что индикаторы включены и что в передней части гарнитуры нет каких-либо посторонних камер отслеживания.</span><span class="sxs-lookup"><span data-stu-id="331b3-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="331b3-107">Если отслеживание потеряно, возобновление может занять несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="331b3-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="331b3-108">Перезапуск на портале Windows Mixed Reality отслеживание не перезапускается.</span><span class="sxs-lookup"><span data-stu-id="331b3-108">Restart the Windows Mixed Reality Portal is tracking doesn't restart.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="331b3-109">Я могу взглянуть, но я не могу пересмотреть (я застрял в 3DOF)</span><span class="sxs-lookup"><span data-stu-id="331b3-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="331b3-110">Это означает, что система отслеживания не может создать объект, или приложение было остановлено с помощью данных нового объекта для подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="331b3-110">This means that the tracking system can't generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="331b3-111">Чтобы исправить проблему</span><span class="sxs-lookup"><span data-stu-id="331b3-111">To fix the issue:</span></span>

* <span data-ttu-id="331b3-112">Убедитесь, что в комнате достаточно освещения.</span><span class="sxs-lookup"><span data-stu-id="331b3-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="331b3-113">Убедитесь, что комната имеет достаточно сведений для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="331b3-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="331b3-114">Отключите устройство, закройте Windows Mixed Reality и снова подключите устройство.</span><span class="sxs-lookup"><span data-stu-id="331b3-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="331b3-115">Если сообщение повторяется, обратитесь в [службу поддержки пользователей](https://support.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="331b3-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-frozen"></a><span data-ttu-id="331b3-116">Представление в ХМД заморожено</span><span class="sxs-lookup"><span data-stu-id="331b3-116">The view in the HMD is frozen</span></span>

<span data-ttu-id="331b3-117">Обычно это означает, что приложение или компонент уровня системы завершились с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="331b3-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="331b3-118">Попробуйте:</span><span class="sxs-lookup"><span data-stu-id="331b3-118">Try to:</span></span>

1. <span data-ttu-id="331b3-119">Нажмите кнопку "домой", чтобы выйти из приложения.</span><span class="sxs-lookup"><span data-stu-id="331b3-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="331b3-120">Отключите устройство, закройте MRP и снова подключите устройство.</span><span class="sxs-lookup"><span data-stu-id="331b3-120">Unplug the device, close MRP, and plug the device back in.</span></span>
3. <span data-ttu-id="331b3-121">Перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="331b3-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="331b3-122">Мир ненадолго фрозеся и наклонен или зеркально переворачивается перед возвратом в нормальный режим</span><span class="sxs-lookup"><span data-stu-id="331b3-122">The world briefly froze and tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="331b3-123">Это может быть вызвано тем, что приложение или компонент уровня системы приводят к неустранимой ошибке или временному нехватке памяти или ресурсов ЦП.</span><span class="sxs-lookup"><span data-stu-id="331b3-123">This could be caused by an application or system level component hitting a fatal error or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="331b3-124">Для проверки:</span><span class="sxs-lookup"><span data-stu-id="331b3-124">To check:</span></span>

1. <span data-ttu-id="331b3-125">Откройте диспетчер задач и убедитесь, что по крайней мере 20% ресурсов ЦП свободна, доступно 400 МБ памяти, а дисковые операции ввода-вывода должны быть ниже 80%.</span><span class="sxs-lookup"><span data-stu-id="331b3-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400 MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="331b3-126">Перейдите в раздел **Просмотр событий > Windows журналы > приложение** , чтобы найти ошибки с момента заморозки.</span><span class="sxs-lookup"><span data-stu-id="331b3-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="331b3-127">Ищите все, что относится к датчикам HoloLens, смешанной реальности или приложению, которое было запущено в течение этого времени.</span><span class="sxs-lookup"><span data-stu-id="331b3-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="331b3-128">Эти журналы могут объяснить причину сбоя.</span><span class="sxs-lookup"><span data-stu-id="331b3-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="331b3-129">Если проблема не исчезнет, перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="331b3-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="331b3-130">По всему миру Перевернутый объект переворачивается вниз и возвращается в нормальный режим</span><span class="sxs-lookup"><span data-stu-id="331b3-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="331b3-131">Обычно это вызвано ошибками при получении данных датчика от гарнитуры для информирования алгоритмов отслеживания.</span><span class="sxs-lookup"><span data-stu-id="331b3-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="331b3-132">Если это происходит часто:</span><span class="sxs-lookup"><span data-stu-id="331b3-132">If this happens frequently:</span></span>

1. <span data-ttu-id="331b3-133">Подключите гарнитуру к другому порту USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="331b3-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="331b3-134">Подключите гарнитуру непосредственно к компьютеру, а не к концентратору USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="331b3-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="331b3-135">Если проблема не исчезнет, обратитесь в [службу поддержки пользователей](https://support.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="331b3-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="331b3-136">Мир имеет наклон, но я могу перемещаться и обходить в Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="331b3-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="331b3-137">Если ошибки в данных датчика записаны в данные среды на компьютере, это может привести к тому, что Windows Mixed Reality будет отображаться наклонным, а иногда навсегда.</span><span class="sxs-lookup"><span data-stu-id="331b3-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="331b3-138">Чтобы устранить эту проблему, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="331b3-138">To fix this:</span></span>

1. <span data-ttu-id="331b3-139">Отсоедините гарнитуру, закройте Windows Mixed Reality и снова подключите гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="331b3-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="331b3-140">Перезагрузите компьютер.</span><span class="sxs-lookup"><span data-stu-id="331b3-140">Restart the PC.</span></span>
3. <span data-ttu-id="331b3-141">Очистите данные среды.</span><span class="sxs-lookup"><span data-stu-id="331b3-141">Clear your environment data.</span></span>