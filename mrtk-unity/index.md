---
title: Документация по MRTK в Unity для разработчиков
description: Сведения о Mixed Reality Toolkit для Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 85a203f22c62871265f7775c364f5388194b53a1
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550974"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="3289f-104">Что такое Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="3289f-104">What is the Mixed Reality Toolkit</span></span>

![Набор средств для смешанной реальности](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="3289f-106">MRTK-Unity — это проект, управляемый Майкрософт, который предоставляет набор компонентов и функций для ускорения кроссплатформенной разработки приложений смешанной реальности в Unity.</span><span class="sxs-lookup"><span data-stu-id="3289f-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="3289f-107">Ниже приведены некоторые его функции.</span><span class="sxs-lookup"><span data-stu-id="3289f-107">Here are some of its functions:</span></span>

* <span data-ttu-id="3289f-108">Предоставляет **кросс-платформенную систему ввода и стандартные блоки для пространственных взаимодействий и пользовательского интерфейса**.</span><span class="sxs-lookup"><span data-stu-id="3289f-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="3289f-109">Поддерживает **быстрое создание прототипов** с помощью имитации в редакторе, позволяющей сразу просматривать изменения.</span><span class="sxs-lookup"><span data-stu-id="3289f-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="3289f-110">Работает как **расширяемая платформа**, предоставляющая разработчикам возможность менять основные компоненты.</span><span class="sxs-lookup"><span data-stu-id="3289f-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="3289f-111">**Поддерживает широкий ряд платформ**, в том числе следующие:</span><span class="sxs-lookup"><span data-stu-id="3289f-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="3289f-112">OpenXR (Unity 2020.2 или более поздней версии):</span><span class="sxs-lookup"><span data-stu-id="3289f-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="3289f-113">Microsoft HoloLens 2;</span><span class="sxs-lookup"><span data-stu-id="3289f-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="3289f-114">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="3289f-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="3289f-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3289f-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="3289f-116">Microsoft HoloLens;</span><span class="sxs-lookup"><span data-stu-id="3289f-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="3289f-117">Microsoft HoloLens 2;</span><span class="sxs-lookup"><span data-stu-id="3289f-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="3289f-118">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="3289f-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="3289f-119">Oculus (Unity 2019.3 или более поздней версии):</span><span class="sxs-lookup"><span data-stu-id="3289f-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="3289f-120">Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="3289f-120">Oculus Quest</span></span>
  * <span data-ttu-id="3289f-121">OpenVR:</span><span class="sxs-lookup"><span data-stu-id="3289f-121">OpenVR</span></span>
    * <span data-ttu-id="3289f-122">гарнитуры смешанной реальности Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="3289f-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="3289f-123">HTC Vive;</span><span class="sxs-lookup"><span data-stu-id="3289f-123">HTC Vive</span></span>
    * <span data-ttu-id="3289f-124">Oculus Rift;</span><span class="sxs-lookup"><span data-stu-id="3289f-124">Oculus Rift</span></span>
  * <span data-ttu-id="3289f-125">отслеживание рук Ultraleap.</span><span class="sxs-lookup"><span data-stu-id="3289f-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="3289f-126">Мобильные устройства, например iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="3289f-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="3289f-127">Начало работы с MRTK</span><span class="sxs-lookup"><span data-stu-id="3289f-127">Getting started with MRTK</span></span>

<span data-ttu-id="3289f-128">Если вы не знакомы с MRTK или разработкой для смешанной реальности в Unity, рекомендуем установить необходимые инструменты и пройти серию учебников по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3289f-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3289f-129">Установка средств</span><span class="sxs-lookup"><span data-stu-id="3289f-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="3289f-130">Серия учебников по HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3289f-130">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="3289f-131">Хотите узнать, как это работает?</span><span class="sxs-lookup"><span data-stu-id="3289f-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3289f-132">Подробнее об MRTK на GitHub</span><span class="sxs-lookup"><span data-stu-id="3289f-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="3289f-133">Документация</span><span class="sxs-lookup"><span data-stu-id="3289f-133">Documentation</span></span>

| <span data-ttu-id="3289f-134">[![Заметки о выпуске](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="3289f-135">Заметки о выпуске</span><span class="sxs-lookup"><span data-stu-id="3289f-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="3289f-136">[![Обзор MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="3289f-137">Обзор MRTK</span><span class="sxs-lookup"><span data-stu-id="3289f-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="3289f-138">[![Справочник по API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="3289f-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="3289f-139">Справочник по интерфейсам API</span><span class="sxs-lookup"><span data-stu-id="3289f-139">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="3289f-140">Состояние сборки</span><span class="sxs-lookup"><span data-stu-id="3289f-140">Build status</span></span>

| <span data-ttu-id="3289f-141">Ветвь</span><span class="sxs-lookup"><span data-stu-id="3289f-141">Branch</span></span> | <span data-ttu-id="3289f-142">Состояние CI</span><span class="sxs-lookup"><span data-stu-id="3289f-142">CI Status</span></span> | <span data-ttu-id="3289f-143">Состояние документации</span><span class="sxs-lookup"><span data-stu-id="3289f-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="3289f-144">[![Состояние CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="3289f-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="3289f-145">[![Состояние документации](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="3289f-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="3289f-146">Функциональные области</span><span class="sxs-lookup"><span data-stu-id="3289f-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3289f-147">[![Система ввода](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="3289f-148">**[Система ввода](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-149">[![Отслеживание рук (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="3289f-150">**[Отслеживание рук <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-151">[![Отслеживание взгляда (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="3289f-152">**[Отслеживание взгляда <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-153">[![Профили](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="3289f-154">**[Профили](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-155">[![Отслеживание рук (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="3289f-156">**[Отслеживание рук <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-157">[![Элементы управления пользовательским интерфейсом](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="3289f-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="3289f-158">**[Элементы управления пользовательским интерфейсом](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="3289f-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-159">[![Решатели](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="3289f-160">**[Решатели](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-161">[![Диспетчер нескольких сцен](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-162">**[Диспетчер <br/>нескольких сцен](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-163">[![Отслеживание пространственного положения](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-164">**[Отслеживание <br/> пространственного положения](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-165">[![Средство диагностики](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-166">**[Средство <br/> диагностики](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-167">[![Отображение работы стандартного шейдера MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="3289f-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="3289f-168">**[Отображение примера работы стандартного шейдера MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="3289f-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-169">[![Речь и диктовка](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-170">**[Речь](features/input/speech.md)<br/> & [Диктовка](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-171">[![Система границ](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-172">**[Система<br/> границ](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-173">[![Имитация в редакторе](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="3289f-174">**[Имитация <br/> в редакторе](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-175">[![Экспериментальные возможности](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="3289f-176">**[Экспериментальные <br/> функции](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="3289f-177">Стандартные блоки пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="3289f-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3289f-178">[![Кнопка](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Кнопка](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="3289f-179">Элемент управления типа "кнопка", поддерживающий различные методы ввода, в том числе свободный ввод с отслеживаем рук в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3289f-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-180">[![Элемент управления границами](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Элемент управления границами](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="3289f-181">Стандартный пользовательский интерфейс для манипулирования объектами в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="3289f-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-182">[![Манипулятор объектов](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Манипулятор объектов](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="3289f-183">Скрипт для манипулирования объектами одной или двумя руками.</span><span class="sxs-lookup"><span data-stu-id="3289f-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-184">[![Грифель](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Грифель](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="3289f-185">Плоскость в двухмерном стиле, поддерживающая прокрутку с помощью свободного ввода рукой.</span><span class="sxs-lookup"><span data-stu-id="3289f-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-186">[![Системная клавиатура](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Системная клавиатура](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="3289f-187">Пример скрипта для использования системной клавиатуры в Unity.</span><span class="sxs-lookup"><span data-stu-id="3289f-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-188">[![Интерактивный объект](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Интерактивный объект](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="3289f-189">Скрипт, обеспечивающий взаимодействие с объектами, с поддержкой визуальных состояний и тем.</span><span class="sxs-lookup"><span data-stu-id="3289f-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-190">[![Решатель](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Решатель](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="3289f-191">Различные модели поведения для позиционирования объектов, такие как следование (tag-along), прикрепление к пользователю (body-lock), зафиксированный размер просмотра (constant view size) и поверхностный магнетизм (surface magnetism).</span><span class="sxs-lookup"><span data-stu-id="3289f-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-192">[![Коллекция объектов](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Коллекция объектов](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="3289f-193">Скрипт для размещения массива объектов в трехмерной фигуре.</span><span class="sxs-lookup"><span data-stu-id="3289f-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-194">[![Подсказка](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Подсказка](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="3289f-195">Пользовательский интерфейс заметок с гибкой системой привязки и поворота, который можно использовать, чтобы помечать контроллеры движений и объекты.</span><span class="sxs-lookup"><span data-stu-id="3289f-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-196">[![Ползунок](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Ползунок](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="3289f-197">Пользовательский интерфейс ползунков для изменения значений, поддерживающих взаимодействие с прямым отслеживанием рук.</span><span class="sxs-lookup"><span data-stu-id="3289f-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-198">[![Стандартный шейдер MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Стандартный шейдер MRTK](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="3289f-199">Стандартный шейдер MRTK поддерживает различные элементы интерфейса Fluent с достаточной производительностью.</span><span class="sxs-lookup"><span data-stu-id="3289f-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-200">[![Меню руки](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Меню руки](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="3289f-201">Привязанный к руке пользовательский интерфейс, обеспечивающий быстрый доступ и использующий решатель ограничения руки.</span><span class="sxs-lookup"><span data-stu-id="3289f-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-202">[![Панель приложения](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Панель приложения](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="3289f-203">Пользовательский интерфейс для активации элемента управления границами вручную.</span><span class="sxs-lookup"><span data-stu-id="3289f-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-204">[![Указатели](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Указатели](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="3289f-205">Сведения о различных типах указателей.</span><span class="sxs-lookup"><span data-stu-id="3289f-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-206">[![Визуализация с использованием кончика пальца](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Визуализация с использованием кончика пальца](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="3289f-207">Визуальный маркер на кончике пальца, повышающий уверенность в прямом взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="3289f-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-208">[![Быстрое меню](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Быстрое меню](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="3289f-209">Пользовательский интерфейс подвешенного меню для быстрых взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="3289f-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-210">[![Начало работы с отслеживанием пространственного положения](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Представление для отслеживания пространственного положения](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="3289f-211">Обеспечьте взаимодействие голографических объектов с физическими средами.</span><span class="sxs-lookup"><span data-stu-id="3289f-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-212">[![Голосовая команда](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Голосовая команда](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="3289f-213">Скрипты и примеры для интеграции голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="3289f-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-214">[![Индикатор хода выполнения](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Индикатор хода выполнения](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="3289f-215">Визуальный индикатор, сообщающий о ходе процесса или операции.</span><span class="sxs-lookup"><span data-stu-id="3289f-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-216">[![Диалоговое окно](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Диалоговое окно](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="3289f-217">Элемент пользовательского интерфейса для получения подтверждения пользователя.</span><span class="sxs-lookup"><span data-stu-id="3289f-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-218">[![Обучающая рука](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Обучающая рука](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="3289f-219">Компонент, помогающий направлять пользователя, если жест еще не выучен.</span><span class="sxs-lookup"><span data-stu-id="3289f-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-220">[![Служба физического взаимодействия с помощью рук](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Служба физического взаимодействия с помощью рук [экспериментальная]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="3289f-221">Служба физического взаимодействия с помощью рук поддерживает события столкновения с твердым телом и взаимодействия с помощью свободного ввода руками.</span><span class="sxs-lookup"><span data-stu-id="3289f-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-222">[![Коллекция прокрутки](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Коллекция прокрутки](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="3289f-223">Коллекция объектов со встроенной поддержкой прокрутки трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="3289f-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-224">[![Док-панель](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Док-панель [экспериментальная]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="3289f-225">Док-панель позволяет перемещать объекты между заранее определенными позициями.</span><span class="sxs-lookup"><span data-stu-id="3289f-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="3289f-226">[![Отслеживание взгляда: выбор цели](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Отслеживание взгляда: выбор цели](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="3289f-227">Объедините ввод с помощью взгляда, голоса и рук для быстрого и простого выбора голограмм в сцене.</span><span class="sxs-lookup"><span data-stu-id="3289f-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-228">[![Отслеживание взгляда: навигация](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Отслеживание взгляда: навигация](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="3289f-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="3289f-229">Узнайте, как автоматически прокручивать текст или быстро увеличить масштаб выбранного содержимого с учетом того, на что направлен ваш взгляд.</span><span class="sxs-lookup"><span data-stu-id="3289f-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3289f-230">[![Отслеживание взгляда: тепловая карта](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Отслеживание взгляда: тепловая карта](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="3289f-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="3289f-231">Примеры ведения журналов, загрузки и визуализации того, на что смотрят пользователи в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="3289f-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="3289f-232">Инструменты</span><span class="sxs-lookup"><span data-stu-id="3289f-232">Tools</span></span>

|  <span data-ttu-id="3289f-233">[![Окно оптимизации](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Окно оптимизации](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="3289f-234">[![Окно зависимости](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Окно зависимости](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![Окно сборки](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="3289f-236">Окно сборки</span><span class="sxs-lookup"><span data-stu-id="3289f-236">Build Window</span></span> | <span data-ttu-id="3289f-237">[![Запись ввода](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Запись ввода](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="3289f-238">Автоматизируйте настройку проектов смешанной реальности, чтобы оптимизировать производительность.</span><span class="sxs-lookup"><span data-stu-id="3289f-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="3289f-239">Анализируйте зависимости между активами и выявляйте неиспользуемые активы.</span><span class="sxs-lookup"><span data-stu-id="3289f-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="3289f-240">Настройте и выполните комплексный процесс сборки для приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3289f-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="3289f-241">Записывайте и воспроизводите данные о перемещении головы и отслеживания рук в редакторе.</span><span class="sxs-lookup"><span data-stu-id="3289f-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="3289f-242">Примеры сцен</span><span class="sxs-lookup"><span data-stu-id="3289f-242">Example scenes</span></span>

<span data-ttu-id="3289f-243">Узнайте о различных типах взаимодействий и элементов управления пользовательского интерфейса MRTK с помощью [этого примера сцены](features/example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="3289f-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="3289f-244">[![Пример сцены 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="3289f-245">Центр примеров MRTK</span><span class="sxs-lookup"><span data-stu-id="3289f-245">MRTK examples hub</span></span>

<span data-ttu-id="3289f-246">Центр примеров MRTK позволяет вам опробовать различные примеры сцен в MRTK.</span><span class="sxs-lookup"><span data-stu-id="3289f-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="3289f-247">Вы можете скачать готовые пакеты приложений для HoloLens (x86), HoloLens 2 (ARM) и иммерсивных гарнитур Windows Mixed Reality (x64), выбрав пакет Mixed Reality Toolkit Examples в средстве [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="3289f-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="3289f-248">Обязательно [используйте портал устройств Windows для установки приложений в HoloLens (1-го поколения)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span><span class="sxs-lookup"><span data-stu-id="3289f-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="3289f-249">Для HoloLens 2 можно скачать и установить [Центр примеров MRTK с помощью приложения Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span><span class="sxs-lookup"><span data-stu-id="3289f-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="3289f-250">Дополнительные сведения о создании центра со сценами с помощью системы сцен и службы перехода между сценами MRTK см. на [странице сведений Центра примеров](features/example-scenes/example-hub.md).</span><span class="sxs-lookup"><span data-stu-id="3289f-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="3289f-251">[![Центр примеров сцен](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="3289f-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="3289f-252">Примеры приложений, созданных с помощью MRTK</span><span class="sxs-lookup"><span data-stu-id="3289f-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="3289f-253">[![Периодическая таблица элементов](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="3289f-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="3289f-254">[![Исследование галактики](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="3289f-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="3289f-255">[![Пример приложения Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="3289f-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="3289f-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) — это пример приложения с открытым кодом, которое демонстрирует, как использовать систему ввода и стандартные блоки MRTK для создания интерфейса приложения для HoloLens и иммерсивных гарнитур.</span><span class="sxs-lookup"><span data-stu-id="3289f-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="3289f-257">Прочитайте историю о [портировании приложения Periodic Table of the Elements на HoloLens 2 с помощью MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158).</span><span class="sxs-lookup"><span data-stu-id="3289f-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="3289f-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) — пример приложения с открытым кодом, которое изначально было разработано для HoloLens в марте 2016 г. в рамках кампании Share Your Idea.</span><span class="sxs-lookup"><span data-stu-id="3289f-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="3289f-259">В Galaxy Explorer добавлены новые возможности для HoloLens 2 с помощью MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="3289f-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="3289f-260">Прочитайте историю о [создании Galaxy Explorer для HoloLens 2](/windows/mixed-reality/galaxy-explorer-update).</span><span class="sxs-lookup"><span data-stu-id="3289f-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="3289f-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) — это пример приложения с открытым кодом для HoloLens 2, которое демонстрирует, как мы можем вызвать тактильные ощущения с помощью визуализации, звуков и отслеживания свободных движений рук.</span><span class="sxs-lookup"><span data-stu-id="3289f-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="3289f-262">Ознакомьтесь с докладом Microsoft MR Dev Days по [наработкам при разработке и использовании приложения Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App), чтобы узнать больше о проектировании и разработке.</span><span class="sxs-lookup"><span data-stu-id="3289f-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="3289f-263">Видео докладов с Mixed Reality Dev Days 2020</span><span class="sxs-lookup"><span data-stu-id="3289f-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="3289f-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="3289f-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="3289f-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="3289f-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="3289f-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="3289f-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="3289f-267">Учебник по созданию простого приложения MRTK с нуля.</span><span class="sxs-lookup"><span data-stu-id="3289f-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="3289f-268">Узнайте больше о понятиях взаимодействия и мультиплатформенных возможностях MRTK.</span><span class="sxs-lookup"><span data-stu-id="3289f-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="3289f-269">Изучите стандартные блоки взаимодействий в MRTK, которые помогут вам создать великолепные среды смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="3289f-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="3289f-270">Вводная информация о встроенных и внешних средствах оценки производительности для MRTK, а также стандартного шейдера MRTK.</span><span class="sxs-lookup"><span data-stu-id="3289f-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="3289f-271">Другие видео с докладами см. на странице [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions).</span><span class="sxs-lookup"><span data-stu-id="3289f-271">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="3289f-272">Присоединяйтесь к сообществу</span><span class="sxs-lookup"><span data-stu-id="3289f-272">Engage with the community</span></span>

* <span data-ttu-id="3289f-273">Присоединяйтесь к обсуждению MRTK на сайте [Slack](https://holodevelopers.slack.com/).</span><span class="sxs-lookup"><span data-stu-id="3289f-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="3289f-274">Вступить в сообщество Slack можно с помощью [автоматической рассылки приглашений](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="3289f-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="3289f-275">Задать вопросы об MRTK можно на сайте [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) (используйте тег **MRTK**).</span><span class="sxs-lookup"><span data-stu-id="3289f-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="3289f-276">Если вы нашли ошибки в коде MRTK, вы можете выполнить поиск по [известным проблемам](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) или сообщить о [новой проблеме](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="3289f-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="3289f-277">Вопросы об участии в разработке MRTK можно задать на канале [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) в сообществе Slack.</span><span class="sxs-lookup"><span data-stu-id="3289f-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="3289f-278">В рамках этого проекта действуют [правила поведения в отношении продуктов с открытым исходным кодом Майкрософт](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="3289f-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="3289f-279">Дополнительные сведения см. в статье [Вопросы и ответы, связанные с правилами поведения](https://opensource.microsoft.com/codeofconduct/faq/). Чтобы задать вопрос или получить комментарии, обратитесь по адресу [opencode@microsoft.com](mailto:opencode@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="3289f-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="3289f-280">Полезные ресурсы в Центре разработки для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3289f-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="3289f-281">![Знания](features/images/mrdevcenter/icon-discover.png) [Знания](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="3289f-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="3289f-282">![Проектирование](features/images/mrdevcenter/icon-design.png) [Проектирование](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="3289f-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="3289f-283">![Разработка](features/images/mrdevcenter/icon-develop.png) [Разработка](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="3289f-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="3289f-284">![Дистрибуция](features/images/mrdevcenter/icon-distribute.png) [Дистрибуция](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="3289f-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="3289f-285">Узнайте, как создавать взаимодействия смешанной реальности для HoloLens и иммерсивных гарнитур (виртуальная реальность).</span><span class="sxs-lookup"><span data-stu-id="3289f-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="3289f-286">Получите руководства по проектированию.</span><span class="sxs-lookup"><span data-stu-id="3289f-286">Get design guides.</span></span> <span data-ttu-id="3289f-287">Создайте пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="3289f-287">Build user interface.</span></span> <span data-ttu-id="3289f-288">Узнайте о взаимодействиях и способах ввода.</span><span class="sxs-lookup"><span data-stu-id="3289f-288">Learn interactions and input.</span></span>     | <span data-ttu-id="3289f-289">Получите руководства по разработке.</span><span class="sxs-lookup"><span data-stu-id="3289f-289">Get development guides.</span></span> <span data-ttu-id="3289f-290">Узнайте о технологиях.</span><span class="sxs-lookup"><span data-stu-id="3289f-290">Learn the technology.</span></span> <span data-ttu-id="3289f-291">Изучите их научную основу.</span><span class="sxs-lookup"><span data-stu-id="3289f-291">Understand the science.</span></span>       | <span data-ttu-id="3289f-292">Подготовка приложения для других пользователей и создание средства для запуска трехмерных приложений.</span><span class="sxs-lookup"><span data-stu-id="3289f-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="3289f-293">Полезные ресурсы в Azure</span><span class="sxs-lookup"><span data-stu-id="3289f-293">Useful resources on Azure</span></span>

| <span data-ttu-id="3289f-294">![Пространственные привязки](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="3289f-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="3289f-295">Пространственные привязки</span><span class="sxs-lookup"><span data-stu-id="3289f-295">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="3289f-296">![Службы распознавания речи](features/images/mrdevcenter/icon-azurespeechservices.png) [Службы распознавания речи](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="3289f-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="3289f-297">![Службы компьютерного зрения](features/images/mrdevcenter/icon-azurevisionservices.png) [Службы компьютерного зрения](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="3289f-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="3289f-298">Пространственные привязки — это кросс-платформенная служба, которая позволяет создавать взаимодействия смешанной реальности с использованием объектов, сохраняющих свое расположение на различных устройствах с течением времени.</span><span class="sxs-lookup"><span data-stu-id="3289f-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="3289f-299">Откройте для себя и интегрируйте в свое приложение возможности обработки речи на платформе Azure, такие как преобразование речи в текст, распознавание говорящего или перевод речи.</span><span class="sxs-lookup"><span data-stu-id="3289f-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="3289f-300">Идентифицируйте изображения или видео с помощью служб визуального распознавания с такими возможностями, как компьютерное зрение, определение лиц, распознавание эмоций или индексация видео.</span><span class="sxs-lookup"><span data-stu-id="3289f-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="3289f-301">Как стать соавтором</span><span class="sxs-lookup"><span data-stu-id="3289f-301">How to contribute</span></span>

<span data-ttu-id="3289f-302">Узнайте, как [принять участие в разработке MRTK](contributing/contributing.md).</span><span class="sxs-lookup"><span data-stu-id="3289f-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="3289f-303">Получение справки</span><span class="sxs-lookup"><span data-stu-id="3289f-303">Getting help</span></span>

<span data-ttu-id="3289f-304">Если при использовании MRTK у вас возникли проблемы или появились вопросы, вам помогут следующие ресурсы:</span><span class="sxs-lookup"><span data-stu-id="3289f-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="3289f-305">Чтобы сообщить об ошибке, [создайте запрос](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) в репозитории GitHub.</span><span class="sxs-lookup"><span data-stu-id="3289f-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="3289f-306">Свой вопрос вы можете задать на сайте [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) или на [канале mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) в сообществе Slack.</span><span class="sxs-lookup"><span data-stu-id="3289f-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="3289f-307">Вступить в сообщество Slack можно с помощью [автоматической рассылки приглашений](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="3289f-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>