---
title: Обзор разработки для собственной платформы
description: Создайте модуль смешанной реальности на основе DirectX, используя интерфейсы API Windows Mixed Reality напрямую.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic-визуализация, собственное, собственное приложение, WinRT, приложение WinRT, API платформы, настраиваемое ядро, промежуточное по, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 493715660ff8df79df25e09c82fe48b863053ed3
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613078"
---
# <a name="native-development-overview"></a><span data-ttu-id="a0f88-104">Обзор разработки для собственной платформы</span><span class="sxs-lookup"><span data-stu-id="a0f88-104">Native development overview</span></span>

![Эмблема собственного баннера](../images/native_logo_banner.png)

<span data-ttu-id="a0f88-106">Трехмерные модули, такие как [Unity](../unity/unity-development-overview.md) или [Real](../unreal/unreal-development-overview.md) , не являются открытыми для вас путями к разработке смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a0f88-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="a0f88-107">Вы также можете создавать приложения смешанной реальности с помощью интерфейсов API Windows Mixed Reality с DirectX 11 или DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="a0f88-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="a0f88-108">Перейдя к источнику платформы, вы сами создаете собственное по промежуточного слоя или платформу.</span><span class="sxs-lookup"><span data-stu-id="a0f88-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="a0f88-109">Если у вас есть проект WinRT, который вы хотите поддерживать, перейдите к нашей основной [документации по WinRT](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a0f88-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="a0f88-110">Этапы разработки</span><span class="sxs-lookup"><span data-stu-id="a0f88-110">Development checkpoints</span></span>

<span data-ttu-id="a0f88-111">Используйте следующие контрольные точки, чтобы реализовать свои игры и приложения Unity в мире смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a0f88-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="a0f88-112">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="a0f88-112">1. Getting started</span></span>

<span data-ttu-id="a0f88-113">Windows Mixed Reality поддерживает [два типа приложений](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="a0f88-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="a0f88-114">Приложения UWP или Win32 **Mixed Reality** , использующие [API Холографикспаце](getting-a-holographicspace.md) или [API опенкср](openxr.md) для визуализации [иммерсивного представления](../../design/app-views.md) , которое заполняет отображение гарнитуры</span><span class="sxs-lookup"><span data-stu-id="a0f88-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="a0f88-115">**2D-приложения** (UWP), использующие DirectX, XAML или другую платформу для отрисовки [2D-представлений](../../design/app-views.md#2d-views) на планшетах в домашней среде Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a0f88-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="a0f88-116">Различия между разработкой DirectX для [2D-представлений и иммерсивное представление](../../design/app-views.md) в основном связаны с более holographic и пространственными входными данными.</span><span class="sxs-lookup"><span data-stu-id="a0f88-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="a0f88-117">[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) приложения UWP или HWND приложения Win32 являются обязательными и остаются в основном одинаковыми.</span><span class="sxs-lookup"><span data-stu-id="a0f88-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="a0f88-118">Это справедливо и для API-интерфейсов WinRT, доступных для приложения.</span><span class="sxs-lookup"><span data-stu-id="a0f88-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="a0f88-119">Однако для использования преимуществ holographic необходимо использовать другое подмножество этих API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a0f88-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="a0f88-120">Например, система для holographic приложений управляет имеющуюся цепочку буферов и Frame on для реализации циклического цикла кадров.</span><span class="sxs-lookup"><span data-stu-id="a0f88-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="a0f88-121">2. Основные компоненты</span><span class="sxs-lookup"><span data-stu-id="a0f88-121">2. Core building blocks</span></span>

<span data-ttu-id="a0f88-122">Приложения Windows Mixed Reality используют следующие API для создания [смешанных](../../discover/mixed-reality.md) возможностей для HoloLens и других впечатляющих головных телефонов:</span><span class="sxs-lookup"><span data-stu-id="a0f88-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="a0f88-123">Компонент</span><span class="sxs-lookup"><span data-stu-id="a0f88-123">Feature</span></span>  |  <span data-ttu-id="a0f88-124">Возможностями.</span><span class="sxs-lookup"><span data-stu-id="a0f88-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="a0f88-125">Взгляд</span><span class="sxs-lookup"><span data-stu-id="a0f88-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="a0f88-126">Предоставление пользователям возможности выбирать голограммы взглядом</span><span class="sxs-lookup"><span data-stu-id="a0f88-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="a0f88-127">жесты</span><span class="sxs-lookup"><span data-stu-id="a0f88-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="a0f88-128">Добавление пространственных действий в приложения</span><span class="sxs-lookup"><span data-stu-id="a0f88-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="a0f88-129">Голографическая отрисовка</span><span class="sxs-lookup"><span data-stu-id="a0f88-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="a0f88-130">Нарисуйте голограмму в точном месте вокруг пользователей</span><span class="sxs-lookup"><span data-stu-id="a0f88-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="a0f88-131">Контроллер движения</span><span class="sxs-lookup"><span data-stu-id="a0f88-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="a0f88-132">Разрешить пользователям предпринимать действия в средах смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="a0f88-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="a0f88-133">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="a0f88-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="a0f88-134">Сопоставление физического пространства с наложением виртуальной сетки для определения границ среды</span><span class="sxs-lookup"><span data-stu-id="a0f88-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="a0f88-135">Голосовая связь</span><span class="sxs-lookup"><span data-stu-id="a0f88-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="a0f88-136">Захват произнесенных слов, фраз и диктовка со стороны пользователей</span><span class="sxs-lookup"><span data-stu-id="a0f88-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="a0f88-137">В документации по Опенкср [Путеводитель](openxr.md#roadmap) можно найти предстоящие и встроенные основные функции.</span><span class="sxs-lookup"><span data-stu-id="a0f88-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="a0f88-138">3. Развертывание и тестирование</span><span class="sxs-lookup"><span data-stu-id="a0f88-138">3. Deploying and testing</span></span>

<span data-ttu-id="a0f88-139">Вы можете разрабатывать приложения на настольном компьютере, используя Опенкср на виртуальной гарнитуре HoloLens 2 или Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a0f88-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="a0f88-140">Если у вас нет доступа к гарнитуре, можно использовать [эмулятор HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) или [симулятор Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .</span><span class="sxs-lookup"><span data-stu-id="a0f88-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="a0f88-141">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="a0f88-141">What's next?</span></span>

<span data-ttu-id="a0f88-142">Разработчику всегда будет чем заняться, особенно при изучении нового инструмента или пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="a0f88-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="a0f88-143">В следующих разделах вы можете перейти к областям, которые выходят за пределы уже выполненных материалов.</span><span class="sxs-lookup"><span data-stu-id="a0f88-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="a0f88-144">Эти разделы и ресурсы не располагаются в последовательном порядке, поэтому вы можете разоойтись и изучить!</span><span class="sxs-lookup"><span data-stu-id="a0f88-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a0f88-145">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="a0f88-145">Additional resources</span></span>

<span data-ttu-id="a0f88-146">Если вы хотите выровнять игру Опенкср, ознакомьтесь с приведенными ниже ссылками.</span><span class="sxs-lookup"><span data-stu-id="a0f88-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="a0f88-147">Рекомендации по работе с OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0f88-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="a0f88-148">Производительность OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0f88-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="a0f88-149">Устранение неполадок с OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0f88-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="a0f88-150">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a0f88-150">See also</span></span>
* [<span data-ttu-id="a0f88-151">Модель приложений</span><span class="sxs-lookup"><span data-stu-id="a0f88-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="a0f88-152">Представления приложений</span><span class="sxs-lookup"><span data-stu-id="a0f88-152">App views</span></span>](../../design/app-views.md)
