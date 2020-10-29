---
title: Представления приложения
description: Два вида представлений в приложениях Windows Mixed Reality — это иммерсивное представление и 2D-представления.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: иммерсивное представление, 2D-представление, планшет, приложение
ms.openlocfilehash: e625eca3adb7cd4a9dcd1f971917f008d5daa7d2
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692145"
---
# <a name="app-views"></a><span data-ttu-id="c8af1-104">Представления приложения</span><span class="sxs-lookup"><span data-stu-id="c8af1-104">App views</span></span>

<span data-ttu-id="c8af1-105">Приложения Windows могут содержать два вида представлений: **иммерсивного** представления и **двумерные представления** .</span><span class="sxs-lookup"><span data-stu-id="c8af1-105">Windows apps can contain two kinds of views, **immersive views** and **2D views** .</span></span> <span data-ttu-id="c8af1-106">Приложения могут переключаться между различными иммерсивного представлениями и 2D-представлениями, отображая их 2D-представления на мониторе как окно или на гарнитуре в качестве планшета.</span><span class="sxs-lookup"><span data-stu-id="c8af1-106">Apps can switch between their various immersive views and 2D views, showing their 2D views either on a monitor as a window or in a headset as a slate.</span></span> <span data-ttu-id="c8af1-107">Приложения, имеющие по крайней мере одно иммерсивное представление, классифицируются как **приложения смешанной реальности** .</span><span class="sxs-lookup"><span data-stu-id="c8af1-107">Apps that have at least one immersive view are categorized as **mixed reality apps** .</span></span> <span data-ttu-id="c8af1-108">Приложения, для которых никогда не используется иммерсивное представление, являются **2D-приложениями** .</span><span class="sxs-lookup"><span data-stu-id="c8af1-108">Apps that never have a immersive view are **2D apps** .</span></span>

## <a name="immersive-views"></a><span data-ttu-id="c8af1-109">Иммерсивное представление</span><span class="sxs-lookup"><span data-stu-id="c8af1-109">Immersive views</span></span>

<span data-ttu-id="c8af1-110">Иммерсивный режим дает приложению возможность создавать голограммы по всему миру или погрузить пользователя в виртуальное окружение.</span><span class="sxs-lookup"><span data-stu-id="c8af1-110">An immersive view gives your app the ability to create holograms in the world around you or immerse the user in a virtual environment.</span></span> <span data-ttu-id="c8af1-111">Когда приложение рисуется в режиме погружения, другие приложения не рисуются одновременно &mdash; с несколькими приложениями, но не объединяются вместе.</span><span class="sxs-lookup"><span data-stu-id="c8af1-111">When an app is drawing in the immersive view, no other app is drawing at the same time&mdash;holograms from multiple apps are not composited together.</span></span> <span data-ttu-id="c8af1-112">Непрерывно изменяя перспективу, из которой [приложение визуализирует](../develop/platform-capabilities-and-apis/rendering.md) свою сцену в соответствии с переносом головного пользователя, приложение может [Отображать голограммы](coordinate-systems.md) , которые остаются в фиксированной точке реального мира, или визуализировать виртуальный мир, который удерживает свое местоположение по мере того, как пользователь перемещается внутри него.</span><span class="sxs-lookup"><span data-stu-id="c8af1-112">By continually adjusting the perspective from which your [app renders](../develop/platform-capabilities-and-apis/rendering.md) its scene to match the user's head movements, your app can render [world-locked](coordinate-systems.md) holograms that remain at a fixed point in the real world, or it can render a virtual world that holds its position as a user moves within it.</span></span>

<span data-ttu-id="c8af1-113">![В режиме погружения можно помещать голограммы в мир по всему миру.](images/designoverview-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c8af1-113">![When in an immersive view, holograms can be placed in the world around you.](images/designoverview-940px.jpg)</span></span><br>
<span data-ttu-id="c8af1-114">*В режиме погружения можно поместить голограммы в мир*</span><span class="sxs-lookup"><span data-stu-id="c8af1-114">*When in an immersive view, holograms can be placed in the world around you*</span></span>

<span data-ttu-id="c8af1-115">В [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware)приложение визуализирует свои голограммы на основе реальной окружающей среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8af1-115">On [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware), your app renders its holograms on top of the user's real-world surroundings.</span></span> <span data-ttu-id="c8af1-116">На [иммерсивное головной гарнитуре Windows Mixed Reality](../discover/immersive-headset-hardware-details.md)пользователь не может видеть реальный мир, поэтому приложение должно визуализировать все, что будет видеть пользователь.</span><span class="sxs-lookup"><span data-stu-id="c8af1-116">On a [Windows Mixed Reality immersive headset](../discover/immersive-headset-hardware-details.md), the user cannot see the real world, and so your app must render everything the user will see.</span></span>

<span data-ttu-id="c8af1-117">[Главная страница Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (включая меню «Пуск» и голограммы, помещенные в среду) не отображается в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="c8af1-117">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (including the Start menu and holograms you've placed around the environment) does not render while in an immersive view either.</span></span> <span data-ttu-id="c8af1-118">В HoloLens все системные уведомления, происходящие при отображении иммерсивного представления, будут ревоспроизвести Кортане, и пользователь может ответить на ввод голоса.</span><span class="sxs-lookup"><span data-stu-id="c8af1-118">On HoloLens, any system notifications that occur while an immersive view is showing will be relayed audibly by Cortana, and the user can respond with voice input.</span></span>

<span data-ttu-id="c8af1-119">В режиме погружения приложение также отвечает за обработку всех входных данных.</span><span class="sxs-lookup"><span data-stu-id="c8af1-119">While in an immersive view, your app is also responsible for handling all input.</span></span> <span data-ttu-id="c8af1-120">Входные данные в Windows Mixed Reality состоят из [взгляда](gaze-and-commit.md), [жеста](gaze-and-commit.md#composite-gestures) (только HoloLens), [голоса](voice-input.md) и [контроллеров движения](motion-controllers.md) (только для иммерсивного гарнитуры).</span><span class="sxs-lookup"><span data-stu-id="c8af1-120">Input in Windows Mixed Reality is made up of [gaze](gaze-and-commit.md), [gesture](gaze-and-commit.md#composite-gestures) (HoloLens only), [voice](voice-input.md) and [motion controllers](motion-controllers.md) (immersive headsets only).</span></span>

## <a name="2d-views"></a><span data-ttu-id="c8af1-121">Двумерные представления</span><span class="sxs-lookup"><span data-stu-id="c8af1-121">2D views</span></span>

<span data-ttu-id="c8af1-122">![Несколько 2D-представлений, размещенных вокруг домашней страницы Windows Mixed Reality](images/teleportation-940px.png)</span><span class="sxs-lookup"><span data-stu-id="c8af1-122">![Multiple 2D views laid out around the Windows Mixed Reality home](images/teleportation-940px.png)</span></span><br>
<span data-ttu-id="c8af1-123">*Несколько приложений с плоским представлением, размещенным вокруг домашней страницы Windows Mixed Reality*</span><span class="sxs-lookup"><span data-stu-id="c8af1-123">*Multiple apps with a 2D view placed around the Windows Mixed Reality home*</span></span>

<span data-ttu-id="c8af1-124">Приложение с плоским представлением отображается в [главной панели Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (иногда называется "оболочкой") как виртуальное веб-приложение, которое отображается вместе с запусками приложений и другими голограммами, которые пользователь поместил в свой мир.</span><span class="sxs-lookup"><span data-stu-id="c8af1-124">An app with a 2D view appears in the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (sometimes called the "shell") as a virtual slate, rendered alongside the app launchers and other holograms the user has placed in their world.</span></span> <span data-ttu-id="c8af1-125">Пользователь может настроить перемещение и масштабирование этого материала, хотя он остается в фиксированном разрешении, независимо от его размера.</span><span class="sxs-lookup"><span data-stu-id="c8af1-125">The user can adjust this slate to move and scale it, though it remains at a fixed resolution regardless of its size.</span></span> <span data-ttu-id="c8af1-126">Если первое представление приложения является 2D-представлением, то оно будет заполнено тем же материалом, который использовался для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="c8af1-126">If your app's first view is a 2D view, your 2D content will fill the same slate used to launch the app.</span></span>

<span data-ttu-id="c8af1-127">В гарнитуре настольного компьютера можно запускать любые приложения универсальная платформа Windows (UWP), которые выполняются на рабочем столе сейчас.</span><span class="sxs-lookup"><span data-stu-id="c8af1-127">In a desktop headset, you can run any Universal Windows Platform (UWP) apps that run on your desktop monitor today.</span></span> <span data-ttu-id="c8af1-128">В настоящее время эти приложения уже отображают 2D-представления, и их содержимое будет автоматически отображаться на планшете в мире пользователя при запуске.</span><span class="sxs-lookup"><span data-stu-id="c8af1-128">These apps are already rendering 2D views today, and their content will automatically appear on a slate in the user's world when launched.</span></span> <span data-ttu-id="c8af1-129">Двумерные приложения UWP могут ориентироваться на семейство устройств **Windows. Universal** для запуска как в гарнитурах настольных ПК, так и на HoloLens в качестве планшетов.</span><span class="sxs-lookup"><span data-stu-id="c8af1-129">2D UWP apps can target the **Windows.Universal** device family to run on both desktop headsets and on HoloLens as slates.</span></span>

<span data-ttu-id="c8af1-130">Одним из основных представлений является отображение формы ввода текста, которая может использовать системную клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="c8af1-130">One key use of 2D views is to show a text entry form that can make use of the system keyboard.</span></span> <span data-ttu-id="c8af1-131">Так как оболочка не может быть отображена поверх иммерсивного представления, приложение должно переключиться на плоское представление для отображения системной клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="c8af1-131">Because the shell cannot render on top of an immersive view, the app must switch to a 2D view to show the system keyboard.</span></span> <span data-ttu-id="c8af1-132">Приложения, которые хотят принимать текстовые данные, могут переключаться в двухмерную представление с помощью текстового поля.</span><span class="sxs-lookup"><span data-stu-id="c8af1-132">Apps that want to accept text input can switch to a 2D view with a text box.</span></span> <span data-ttu-id="c8af1-133">Пока это текстовое поле находится в фокусе, система выводит системную клавиатуру, позволяя пользователю вводить текст.</span><span class="sxs-lookup"><span data-stu-id="c8af1-133">While that text box has focus, the system will show the system keyboard, allowing the user to enter text.</span></span>

<span data-ttu-id="c8af1-134">Обратите внимание, что на настольном компьютере приложение может иметь 2D-представления как на настольном мониторе, так и на присоединенной гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="c8af1-134">Note that on a desktop PC, an app can have 2D views on both the desktop monitor and in an attached headset.</span></span> <span data-ttu-id="c8af1-135">Например, вы можете просмотреть ребро на настольном мониторе, используя его основное плоское представление, чтобы найти видео 360-градуса.</span><span class="sxs-lookup"><span data-stu-id="c8af1-135">For example, you can browse Edge on your desktop monitor using its main 2D view to find a 360-degree video.</span></span> <span data-ttu-id="c8af1-136">При воспроизведении этого видео ребро запустит дополнительное иммерсивное представление внутри гарнитуры, чтобы отобразить иммерсивное видео.</span><span class="sxs-lookup"><span data-stu-id="c8af1-136">When you play that video, Edge will launch a secondary immersive view inside the headset to display the immersive video content.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8af1-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c8af1-137">See also</span></span>

* [<span data-ttu-id="c8af1-138">Модель приложений</span><span class="sxs-lookup"><span data-stu-id="c8af1-138">App model</span></span>](app-model.md)
* [<span data-ttu-id="c8af1-139">Обновление двухмерных приложений UWP для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c8af1-139">Updating 2D UWP apps for mixed reality</span></span>](../develop/porting-apps/building-2d-apps.md)
* [<span data-ttu-id="c8af1-140">Получение HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="c8af1-140">Getting a HolographicSpace</span></span>](../develop/native/getting-a-holographicspace.md)
* [<span data-ttu-id="c8af1-141">Навигация по дому с технологией Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c8af1-141">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="c8af1-142">Типы приложений смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="c8af1-142">Types of mixed reality apps</span></span>](types-of-mixed-reality-apps.md)