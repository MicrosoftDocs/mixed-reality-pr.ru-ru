---
title: Заметки о выпуске МРТК 2,5
description: Заметки о выпуске для МРТК версии 2,5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК,
ms.openlocfilehash: 536a37b56b4c7de9875ce1e1642922bd363fecb1
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562494"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a><span data-ttu-id="efd11-104">Заметки о выпуске Microsoft Mixed Reality Toolkit 2,5</span><span class="sxs-lookup"><span data-stu-id="efd11-104">Microsoft Mixed Reality Toolkit 2.5 release notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efd11-105">Существует известная ошибка компилятора, влияющая на приложения, созданные для Microsoft HoloLens 2 с помощью ARM64.</span><span class="sxs-lookup"><span data-stu-id="efd11-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="efd11-106">Эта проблема устранена путем обновления Visual Studio 2019 до версии 16,8 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="efd11-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="efd11-107">Если не удается обновить Visual Studio, импортируйте `com.microsoft.mixedreality.toolkit.tools` пакет, чтобы применить обходной путь.</span><span class="sxs-lookup"><span data-stu-id="efd11-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-254"></a><span data-ttu-id="efd11-108">Новые возможности в 2.5.4</span><span class="sxs-lookup"><span data-stu-id="efd11-108">What's new in 2.5.4</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="efd11-109">Устраняет ошибку с интеграцией Окулус при использовании УПМ</span><span class="sxs-lookup"><span data-stu-id="efd11-109">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="efd11-110">При использовании УПМ Окулусксрсдкдевицеманажерпрофиле всегда будет иметь [значение None во время запуска](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span><span class="sxs-lookup"><span data-stu-id="efd11-110">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="efd11-111">В этом выпуске настраивается диспетчер устройств, указывающий на рабочий набор Prefabs при запуске.</span><span class="sxs-lookup"><span data-stu-id="efd11-111">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="efd11-112">Устраняет проблему с Опенкср через УПМ</span><span class="sxs-lookup"><span data-stu-id="efd11-112">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="efd11-113">Устраняет проблему, из-за которой поставщики Опенкср не были добавлены в link.xml по умолчанию, что приводит к невозможности запуска новых проектов на устройстве при использовании Опенкср и МРТК с помощью диспетчера пакетов Unity.</span><span class="sxs-lookup"><span data-stu-id="efd11-113">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="efd11-114">Существующие проекты, которые были обновлены, по-прежнему потребуется добавить вручную.</span><span class="sxs-lookup"><span data-stu-id="efd11-114">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="whats-new-in-253"></a><span data-ttu-id="efd11-115">Новые возможности в 2.5.3</span><span class="sxs-lookup"><span data-stu-id="efd11-115">What's new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="efd11-116">Устраняет регрессию с помощью Окулус, появившихся в 2.5.2</span><span class="sxs-lookup"><span data-stu-id="efd11-116">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="efd11-117">в 2.5.2 появилась [ошибка сборки при интеграции пакета SDK для Окулус](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span><span class="sxs-lookup"><span data-stu-id="efd11-117">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="efd11-118">Этот выпуск возвращает эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="efd11-118">This release reverts that issue.</span></span>

## <a name="whats-new-in-252"></a><span data-ttu-id="efd11-119">Новые возможности в 2.5.2</span><span class="sxs-lookup"><span data-stu-id="efd11-119">What's new in 2.5.2</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="efd11-120">Добавление поддержки для Опенкср</span><span class="sxs-lookup"><span data-stu-id="efd11-120">Add support for OpenXR</span></span>

<span data-ttu-id="efd11-121">Добавлена первоначальная поддержка пакета предварительной версии Опенкср Unity и пакета Опенкср для смешанной реальности Microsoft.</span><span class="sxs-lookup"><span data-stu-id="efd11-121">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="efd11-122">Дополнительные сведения см. [на странице Приступая к работе с мртк/ксрсдк](../configuration/getting-started-with-mrtk-and-xrsdk.md), на [форуме Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)или в [документации Майкрософт](/windows/mixed-reality/develop/unity/openxr-getting-started) .</span><span class="sxs-lookup"><span data-stu-id="efd11-122">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efd11-123">Опенкср в Unity поддерживается только в Unity 2020,3 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="efd11-123">OpenXR in Unity is only supported on Unity 2020.3 and higher.</span></span>
> <span data-ttu-id="efd11-124">Он также поддерживает только сборки x64, ARM и ARM64.</span><span class="sxs-lookup"><span data-stu-id="efd11-124">It also only supports x64, ARM, and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="efd11-125">Исправлены ошибки визуализации границ</span><span class="sxs-lookup"><span data-stu-id="efd11-125">Boundary visualization errors fixed</span></span>

<span data-ttu-id="efd11-126">Теперь визуализации границ, такие как этаж или стенки, будут правильно настроены и видны во время выполнения в соответствии с профилем границы.</span><span class="sxs-lookup"><span data-stu-id="efd11-126">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="efd11-127">Поддержка MSBuild для поддержки Unity</span><span class="sxs-lookup"><span data-stu-id="efd11-127">MSBuild for Unity support</span></span>

<span data-ttu-id="efd11-128">Поддержка MSBuild для Unity была удалена в 2.5.2 выпуске для согласования с [новым руководством по пакетам Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span><span class="sxs-lookup"><span data-stu-id="efd11-128">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="whats-new-in-251"></a><span data-ttu-id="efd11-129">Новые возможности в 2.5.1</span><span class="sxs-lookup"><span data-stu-id="efd11-129">What's new in 2.5.1</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="efd11-130">Исправлены ошибки зависимостей пакета</span><span class="sxs-lookup"><span data-stu-id="efd11-130">Package dependency errors fixed</span></span>

<span data-ttu-id="efd11-131">В этом выпуске исправлена неправильная зависимость файлов между пакетами (например, файлы в стандартных ресурсах больше не являются неправильными ссылками на файлы в Foundation).</span><span class="sxs-lookup"><span data-stu-id="efd11-131">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="efd11-132">Кроме того, версия 2.5.1 добавляет явную зависимость от сетки текста Pro.</span><span class="sxs-lookup"><span data-stu-id="efd11-132">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="efd11-133">Текстуры пакетов стандартных активов, скопированные в активы/МРТК/шейдеры</span><span class="sxs-lookup"><span data-stu-id="efd11-133">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="efd11-134">Когда пакет стандартных активов устанавливается через УПМ, шейдеры копируются в папку Assets/МРТК/шейдеры, чтобы они больше не были неизменными.</span><span class="sxs-lookup"><span data-stu-id="efd11-134">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="efd11-135">Это позволяет устранить проблему, обновленную шейдером для универсального конвейера отрисовки (URP), отменяя прежнее поведение при следующем загрузке проекта.</span><span class="sxs-lookup"><span data-stu-id="efd11-135">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="efd11-136">Исправленный курсор телепортируйтесь, прикрепленный к руки</span><span class="sxs-lookup"><span data-stu-id="efd11-136">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="efd11-137">В этом выпуске Исправлена [проблема](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) , из которой курсор назначений телепортируйтесь может прикрепить к визуальным элементам.</span><span class="sxs-lookup"><span data-stu-id="efd11-137">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="whats-new-in-250"></a><span data-ttu-id="efd11-138">Новые возможности в 2.5.0</span><span class="sxs-lookup"><span data-stu-id="efd11-138">What's new in 2.5.0</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="efd11-139">Поддержка диспетчера пакетов Unity (УПМ)</span><span class="sxs-lookup"><span data-stu-id="efd11-139">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="efd11-140">Теперь набор средств Mixed Reality можно управлять с помощью диспетчера пакетов Unity.</span><span class="sxs-lookup"><span data-stu-id="efd11-140">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![Пакет УПМ МРТК Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="efd11-142">Для импорта пакетов УПМ МРТК необходимо выполнить некоторые действия вручную.</span><span class="sxs-lookup"><span data-stu-id="efd11-142">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="efd11-143">Дополнительные сведения см. в [наборе средств для смешанной реальности и диспетчере пакетов Unity](../configuration/usingupm.md) .</span><span class="sxs-lookup"><span data-stu-id="efd11-143">Please review [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xr-sdk-support"></a><span data-ttu-id="efd11-144">Поддержка пакета SDK для Окулус Quest XR</span><span class="sxs-lookup"><span data-stu-id="efd11-144">Oculus Quest XR SDK support</span></span>

<span data-ttu-id="efd11-145">МРТК теперь поддерживает запуск головных и видеоконтроллеров Окулус с помощью собственного конвейера пакета SDK XR.</span><span class="sxs-lookup"><span data-stu-id="efd11-145">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="efd11-146">Также поддерживается отслеживание вручную с [пакетом Unity для Окулус](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) [, спасибо](https://twitter.com/prvncher) за мртк-Quest!</span><span class="sxs-lookup"><span data-stu-id="efd11-146">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="efd11-147">Инструкции по развертыванию устройства в Окулус Quest с помощью нового конвейера см. в разделе Руководство по [установке Окулус Quest](../supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="efd11-147">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../supported-devices/oculus-quest-mrtk.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="efd11-148">Прокрутка коллекции объектов</span><span class="sxs-lookup"><span data-stu-id="efd11-148">Scrolling Object Collection</span></span>

<span data-ttu-id="efd11-149">Компонент UX МРТК был обновлен с экспериментальной функции и предоставляет больше возможностей для размещения трехмерного содержимого разного размера благодаря добавленной поддержке объектов, не подключенных к объектам.</span><span class="sxs-lookup"><span data-stu-id="efd11-149">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="efd11-150">Также добавлен новый параметр для отключения маскирования содержимого, что упрощает создание прототипов.</span><span class="sxs-lookup"><span data-stu-id="efd11-150">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="efd11-151">Дополнительные сведения см. в разделе [Коллекция объектов с прокруткой](../features/ux-building-blocks/scrolling-object-collection.md) .</span><span class="sxs-lookup"><span data-stu-id="efd11-151">See [Scrolling Object Collection](../features/ux-building-blocks/scrolling-object-collection.md) for more information.</span></span>

![Прокрутка коллекции объектов](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="efd11-153">Улучшение анимации, обработки и улучшения звука с указателями телепортируйтесь</span><span class="sxs-lookup"><span data-stu-id="efd11-153">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="efd11-154">Теперь у указателя телепортируйтесь появилась Улучшенная анимация и отзывы о звуках.</span><span class="sxs-lookup"><span data-stu-id="efd11-154">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="efd11-155">Мы также улучшили обработку указателя телепортируйтесь, чтобы он обрабатывался более гладко при переходе от ближайших поверхностей к поверхности.</span><span class="sxs-lookup"><span data-stu-id="efd11-155">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="efd11-156">Лист Памятка по моделирования входных данных</span><span class="sxs-lookup"><span data-stu-id="efd11-156">Input simulation cheat sheet</span></span>

<span data-ttu-id="efd11-157">Сцена Хандинтерактионексамплес теперь имеет настраиваемый ярлык для отображения страницы справки для имитации ввода</span><span class="sxs-lookup"><span data-stu-id="efd11-157">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![Лист Памятка по моделирования входных данных](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="efd11-159">Взгляд на имитацию ввода с помощью мыши</span><span class="sxs-lookup"><span data-stu-id="efd11-159">Input simulation eye gaze with mouse</span></span>

<span data-ttu-id="efd11-160">Теперь пользователи могут использовать мышь для имитации отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="efd11-160">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="efd11-161">Просмотрите `Eye Simulation Mode` поле в профиле моделирования ввода и установите его в качестве указателя мыши.</span><span class="sxs-lookup"><span data-stu-id="efd11-161">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="efd11-162">Это заменяет предыдущее `Simulate Eye Position` поле.</span><span class="sxs-lookup"><span data-stu-id="efd11-162">This replaces the previous `Simulate Eye Position` field.</span></span>

![Мышь взгляда на глаз](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="efd11-164">Контроллер движения для имитации входа в редакторе в режиме воспроизведения</span><span class="sxs-lookup"><span data-stu-id="efd11-164">Input simulation motion controller in editor Play Mode</span></span>

<span data-ttu-id="efd11-165">Теперь пользователи могут имитировать контроллер движения, как и в режиме воспроизведения редактора.</span><span class="sxs-lookup"><span data-stu-id="efd11-165">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="efd11-166">Кнопки триггера, захвата и меню в настоящее время поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="efd11-166">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="efd11-167">Закрестный указатель для захвата</span><span class="sxs-lookup"><span data-stu-id="efd11-167">Conical grab pointer</span></span>

<span data-ttu-id="efd11-168">Теперь указатели захвата можно настроить для запроса ближайших объектов с помощью конуса от точки захвата, а не сферы.</span><span class="sxs-lookup"><span data-stu-id="efd11-168">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="efd11-169">Это более точно напоминает поведение интерфейса HoloLens 2 по умолчанию, который запрашивает ближайшие объекты с помощью конуса.</span><span class="sxs-lookup"><span data-stu-id="efd11-169">This more closely resembles the behavior from the default HoloLens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="efd11-170">DefaultHoloLens2InputSystemProfile также был скорректирован для использования нового `ConicalGrabPointer` .</span><span class="sxs-lookup"><span data-stu-id="efd11-170">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![Закрестный указатель для захвата](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="efd11-172">Пакет Тестутилитиес</span><span class="sxs-lookup"><span data-stu-id="efd11-172">TestUtilities package</span></span>

<span data-ttu-id="efd11-173">Теперь существует пакет (Microsoft. Микседреалити. Toolkit. Unity. Тестутилитиес. 2.5.0. пакет unitypackage), содержащий инфраструктуру тестирования Плаймоде и Тестмоде, которую МРТК использует для создания сквозных тестов.</span><span class="sxs-lookup"><span data-stu-id="efd11-173">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="efd11-174">Эта инфраструктура чрезвычайно удобна для самой команды МРТК, и мы рады, что потребители используют его для добавления покрытия тестирования в собственные проекты.</span><span class="sxs-lookup"><span data-stu-id="efd11-174">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="efd11-175">В следующем коде показано, как создать тестовую часть, показать ее в определенном месте, переместить, а затем выполнить сжатие.</span><span class="sxs-lookup"><span data-stu-id="efd11-175">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="efd11-176">Инструкции по написанию теста с помощью этих Тестутилитиес см. в этом разделе, посвященном [написанию тестов](../contributing/unit-tests.md#writing-tests).</span><span class="sxs-lookup"><span data-stu-id="efd11-176">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../contributing/unit-tests.md#writing-tests).</span></span>

<span data-ttu-id="efd11-177">Примеры существующих тестов, использующих эту инфраструктуру, см. в разделе МРТК [плаймодетестс](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests).</span><span class="sxs-lookup"><span data-stu-id="efd11-177">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests).</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="efd11-178">Поддержка модулей Unity для LEAP Motion 4.5.1</span><span class="sxs-lookup"><span data-stu-id="efd11-178">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="efd11-179">Добавлена поддержка модулей Unity для управления LEAP версии 4.5.1, и поддержка ресурсов 4.4.0 была удалена.</span><span class="sxs-lookup"><span data-stu-id="efd11-179">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="efd11-180">Текущие поддерживаемые версии модулей Unity для платформы LEAP — 4.5.0 и 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="efd11-180">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="efd11-181">Кроме того, существует дополнительный шаг для начальной интеграции с LEAP. Дополнительные сведения см. в статье [Настройка отслеживания перемещения по LEAP в мртк](../supported-devices/leap-motion-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="efd11-181">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="efd11-182">Наблюдатель сетки с поддержкой пространственных данных лучше обрабатывает настройку материалов</span><span class="sxs-lookup"><span data-stu-id="efd11-182">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="efd11-183">В этом выпуске `Windows Mixed Reality Spatial Mesh Observer` компоненты и `Generic XR SDK Spatial Mesh Observer` имеют улучшенную обработку визуальных материалов.</span><span class="sxs-lookup"><span data-stu-id="efd11-183">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="efd11-184">Теперь материалы сохраняются при обновлении сетки наблюдателем, где ранее они были сброшены в Висиблематериал по умолчанию, как указано в профиле.</span><span class="sxs-lookup"><span data-stu-id="efd11-184">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="efd11-185">Это позволяет разработчикам изменять материалы сетки и не вносить непредвиденные изменения в журнал.</span><span class="sxs-lookup"><span data-stu-id="efd11-185">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="efd11-186">Link.xml, созданный в папке Микседреалититулкит. Generated</span><span class="sxs-lookup"><span data-stu-id="efd11-186">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="efd11-187">С введением диспетчера пакетов Unity МРТК, МРТК теперь записывает `link.xml` файл в `Assets/MixedRealityToolkit.Generated` папку, если он отсутствует.</span><span class="sxs-lookup"><span data-stu-id="efd11-187">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="efd11-188">Рекомендуется добавить этот файл (и `link.xml.meta` ) в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="efd11-188">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="efd11-189">Link.xml используется, чтобы повлиять на функции компоновщика Unity на [управляемом коде](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) .</span><span class="sxs-lookup"><span data-stu-id="efd11-189">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="efd11-190">Дополнительные сведения о файле link.xml МРТК можно найти в статье [мртк и управляемый код](../updates-deployment/mrtk-and-managed-code-stripping.md) .</span><span class="sxs-lookup"><span data-stu-id="efd11-190">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../updates-deployment/mrtk-and-managed-code-stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="efd11-191">Диалоговое окно настройки Unity 2019.3 +: МРТК больше не пытается включить поддержку устаревших XR</span><span class="sxs-lookup"><span data-stu-id="efd11-191">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="efd11-192">Чтобы избежать потенциальных конфликтов при использовании платформы XR Unity, параметр включения поддержки устаревших XR был удален из диалогового окна настройки МРТК.</span><span class="sxs-lookup"><span data-stu-id="efd11-192">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="efd11-193">При необходимости можно включить устаревшую поддержку XR в Unity 2019, используя параметр **изменить**  >  **проект параметры**  >
 **проигрывателя**  >  **XR параметры**  >  **Виртуальная реальность поддерживается**.</span><span class="sxs-lookup"><span data-stu-id="efd11-193">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="efd11-194">Сокращение расходов на Инитиализеонлоад</span><span class="sxs-lookup"><span data-stu-id="efd11-194">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="efd11-195">Мы сделали работу, чтобы сократить объем работы, выполняемый в обработчиках Инитиализеонлоад, что должно привести к улучшению скорости разработки внутреннего цикла.</span><span class="sxs-lookup"><span data-stu-id="efd11-195">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="efd11-196">Обработчики Инитиализеонлоад запускаются каждый раз при компиляции скрипта, перед входом в режим воспроизведения и при запуске редактора.</span><span class="sxs-lookup"><span data-stu-id="efd11-196">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="efd11-197">Эти обработчики теперь выполняются в гораздо меньшем количестве случаев, что приводит к увеличению скорости реагирования Unity.</span><span class="sxs-lookup"><span data-stu-id="efd11-197">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="efd11-198">В некоторых случаях было необходимо установить компромисс:</span><span class="sxs-lookup"><span data-stu-id="efd11-198">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="efd11-199">Дополнительные этапы интеграции см. в разделе [Настройка отслеживания движения](../supported-devices/leap-motion-mrtk.md) с помощью LEAP.</span><span class="sxs-lookup"><span data-stu-id="efd11-199">See [Leap Motion Hand Tracking Configuration](../supported-devices/leap-motion-mrtk.md) for the extra integration step.</span></span>
- <span data-ttu-id="efd11-200">Для тех, кто использует Арфаундатион, теперь можно выполнить дополнительные действия вручную в разделе «Начало работы».</span><span class="sxs-lookup"><span data-stu-id="efd11-200">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
  <span data-ttu-id="efd11-201">См. раздел [арфаундатион](../supported-devices/using-ar-foundation.md#install-required-packages) для выполнения новых шагов.</span><span class="sxs-lookup"><span data-stu-id="efd11-201">See [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="efd11-202">Для тех, кто будет использовать [holographic удаленное взаимодействие с устаревшим конвейером XR](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) в HoloLens 2, теперь можно выполнить [шаг, выполняемый вручную](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) .</span><span class="sxs-lookup"><span data-stu-id="efd11-202">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="efd11-203">Элемент управления границами с градиентом</span><span class="sxs-lookup"><span data-stu-id="efd11-203">Bounds control graduated</span></span>

![Элемент управления Bounds](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="efd11-205">[Управление границами](../features/ux-building-blocks/bounds-control.md) выходит за пределы экспериментального и включает целый ряд новых функций и тонн исправлений ошибок.</span><span class="sxs-lookup"><span data-stu-id="efd11-205">[Bounds control](../features/ux-building-blocks/bounds-control.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="efd11-206">Ниже приведен список основных особенностей этого обновления.</span><span class="sxs-lookup"><span data-stu-id="efd11-206">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="efd11-207">свойства разбиваются на конфигурации, что упрощает настройку элемента управления "границы"</span><span class="sxs-lookup"><span data-stu-id="efd11-207">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="efd11-208">конфигурации могут совместно использоваться объектами, поддерживающими сценарии</span><span class="sxs-lookup"><span data-stu-id="efd11-208">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="efd11-209">Каждое свойство или свойство, поддерживающее скрипт, можно настроить в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="efd11-209">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="efd11-210">Платформа управления границами больше не создается повторно при изменении свойства</span><span class="sxs-lookup"><span data-stu-id="efd11-210">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="efd11-211">поддержка дескрипторов перевода</span><span class="sxs-lookup"><span data-stu-id="efd11-211">translation handles support</span></span>
- <span data-ttu-id="efd11-212">Поддержка полного ограничения с помощью диспетчера ограничений</span><span class="sxs-lookup"><span data-stu-id="efd11-212">full constraint support through constraint manager</span></span>
- <span data-ttu-id="efd11-213">Интеграция системы эластичных баз данных (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="efd11-213">elastics system integration (experimental)</span></span>

<span data-ttu-id="efd11-214">Старый ограничивающий прямоугольник теперь устарел и существующие игровые объекты с помощью ограничивающего прямоугольника можно [обновить с помощью средства миграции](../features/tools/migration-window.md) или [инспектора ограничивающего прямоугольника](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span><span class="sxs-lookup"><span data-stu-id="efd11-214">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/tools/migration-window.md) or the [bounding box inspector](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="efd11-215">Компонент диспетчера ограничений</span><span class="sxs-lookup"><span data-stu-id="efd11-215">Constraint manager component</span></span>

<span data-ttu-id="efd11-216">Ограничения теперь могут использоваться как, элементом управления "границы", так и манипулятором объекта с помощью нового [компонента диспетчера ограничений](../features/ux-building-blocks/constraint-manager.md).</span><span class="sxs-lookup"><span data-stu-id="efd11-216">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/ux-building-blocks/constraint-manager.md).</span></span> <span data-ttu-id="efd11-217">Оба компонента создают диспетчер ограничений для каждого значения по умолчанию и автоматически обрабатывают все подключенные ограничения.</span><span class="sxs-lookup"><span data-stu-id="efd11-217">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="efd11-218">Кроме того, в Диспетчер ограничений автоматического поведения входит ручной режим, позволяющий пользователям решить, какое ограничение следует обработать.</span><span class="sxs-lookup"><span data-stu-id="efd11-218">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="efd11-219">По этой причине ограничения в инспекторе свойств отображаются немного.</span><span class="sxs-lookup"><span data-stu-id="efd11-219">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

<span data-ttu-id="efd11-220">Ограничения, применяемые к компоненту, теперь отображаются в виде списка в компоненте "Диспетчер ограничений", тогда как компонент, использующий диспетчер ограничений ( [элемент управления "границы](../features/ux-building-blocks/bounds-control.md#constraint-system) " или [манипулятор объекта](../features/ux-building-blocks/object-manipulator.md#constraint-manager)), теперь будет отображать выбранный диспетчер ограничений и режим (авто или вручную).</span><span class="sxs-lookup"><span data-stu-id="efd11-220">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/ux-building-blocks/bounds-control.md#constraint-system) or [object manipulator](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="efd11-221">Дополнительные сведения см. в разделе " [Менеджер по ограничениям](../features/ux-building-blocks/constraint-manager.md) " в наших документах.</span><span class="sxs-lookup"><span data-stu-id="efd11-221">For more information read the [constraint manager](../features/ux-building-blocks/constraint-manager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="efd11-222">Обновление материала кнопки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="efd11-222">HoloLens 2 button material update</span></span>

<span data-ttu-id="efd11-223">Обновленный материал передней части кнопки HoloLens 2 для удаления черного цвета в НОРМАТИВных планах.</span><span class="sxs-lookup"><span data-stu-id="efd11-223">Updated HoloLens 2 button's front cage material to remove black color in MRC.</span></span>

![Обновление материала кнопки HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="efd11-225">Обновление панели описания, перемещаемый пример сцены</span><span class="sxs-lookup"><span data-stu-id="efd11-225">Description panel update, movable example scene</span></span>

<span data-ttu-id="efd11-226">Обновленная панель описания.</span><span class="sxs-lookup"><span data-stu-id="efd11-226">Updated description panel.</span></span> <span data-ttu-id="efd11-227">(Сценедескриптионпанелрев. prefab) новая структура — это верхняя полоска, которая позволяет пользователю изменять или перемещать всю сцену.</span><span class="sxs-lookup"><span data-stu-id="efd11-227">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![Обновление панели описания](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="efd11-229">Визуализация пространственной сетки — импульс в Air — TAP</span><span class="sxs-lookup"><span data-stu-id="efd11-229">Spatial mesh visualization - pulse on air-tap</span></span>

<span data-ttu-id="efd11-230">В примере обновленного шейдера импульса для пространственной сети требуется сопоставление поведения оболочки HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="efd11-230">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![Импульс в Air — TAP](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a><span data-ttu-id="efd11-232">Эластичная система (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="efd11-232">Elastic system (experimental)</span></span>

![Эластичные System2](../features/images/elastics/Elastics_Main.gif)

<span data-ttu-id="efd11-234">МРТК теперь поставляется с [системой эластичного моделирования](../features/elastics/elastic-system.md) , которая включает в себя широкий спектр расширяемых и гибких подклассов, предлагая привязки для 4-мерных пружины, трехмерных и простых линейных систем.</span><span class="sxs-lookup"><span data-stu-id="efd11-234">MRTK now comes with an [elastic simulation system](../features/elastics/elastic-system.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="efd11-235">В настоящее время следующие компоненты МРТК, поддерживающие [Диспетчер эластичных](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) баз данных, могут использовать функциональные возможности эластичных БД:</span><span class="sxs-lookup"><span data-stu-id="efd11-235">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="efd11-236">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="efd11-236">Bounds control</span></span>](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [<span data-ttu-id="efd11-237">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="efd11-237">Object manipulator</span></span>](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a><span data-ttu-id="efd11-238">Джойстик (экспериментальный)</span><span class="sxs-lookup"><span data-stu-id="efd11-238">Joystick (experimental)</span></span>

<span data-ttu-id="efd11-239">Пример интерфейса джойстика, который может управлять большим целевым объектом.</span><span class="sxs-lookup"><span data-stu-id="efd11-239">An example of joystick interface that can control a large target object.</span></span>

![Джойстик](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="efd11-241">Палитра цветов (экспериментальная)</span><span class="sxs-lookup"><span data-stu-id="efd11-241">Color picker (experimental)</span></span>

<span data-ttu-id="efd11-242">Экспериментальный элемент управления, который позволяет легко изменять цвета материалов на любом объекте во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="efd11-242">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>

![Три разных метода элемента управления "Выбор цвета"](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Четыре разных метода элемента управления "Выбор цвета"](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a><span data-ttu-id="efd11-245">Критические изменения</span><span class="sxs-lookup"><span data-stu-id="efd11-245">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="efd11-246">Изменения файлов определения сборки</span><span class="sxs-lookup"><span data-stu-id="efd11-246">Assembly definition files changes</span></span>

<span data-ttu-id="efd11-247">Некоторые файлы асмдеф изменены, и теперь поддерживаются только Unity 2018.4.13 F1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="efd11-247">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="efd11-248">При обновлении до МРТК 2,5 в более ранних версиях Unity будут отображаться ошибки компиляции.</span><span class="sxs-lookup"><span data-stu-id="efd11-248">Compilation errors will show up when updating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="efd11-249">Это можно исправить, перейдя `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` в окно проекта и удалив недостающую ссылку в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="efd11-249">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="efd11-250">Повторите эти шаги с помощью `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` и `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` .</span><span class="sxs-lookup"><span data-stu-id="efd11-250">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="efd11-251">Обратите внимание, что изменения необходимо отменить, заменив эти три асмдеф-файла исходными (т. е. неизмененными) при обновлении до Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="efd11-251">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="efd11-252">имикседреалитипоинтермедиатор</span><span class="sxs-lookup"><span data-stu-id="efd11-252">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="efd11-253">Этот интерфейс был обновлен для создания функции:</span><span class="sxs-lookup"><span data-stu-id="efd11-253">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="efd11-254">Если у вас есть пользовательский указатель медиатора, который не является подкласс Дефаултпоинтермедиатор, необходимо реализовать эту новую функцию.</span><span class="sxs-lookup"><span data-stu-id="efd11-254">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="efd11-255">Дополнительные сведения о том, почему он был добавлен, см. в [этой статье](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) .</span><span class="sxs-lookup"><span data-stu-id="efd11-255">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="efd11-256">Это было добавлено, чтобы убедиться, что параметры указателя явно переданы в медиатора, вместо того, чтобы они были неявно выполнены на основе наличия конструктора, который принимал Ипоинтерпреференцес.</span><span class="sxs-lookup"><span data-stu-id="efd11-256">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="efd11-257">API-интерфейс для портала для RESTful и устройств</span><span class="sxs-lookup"><span data-stu-id="efd11-257">Rest / Device Portal API</span></span>

<span data-ttu-id="efd11-258">`UseSSL`Статическое свойство было перемещено из `Rest` в `DevicePortal` .</span><span class="sxs-lookup"><span data-stu-id="efd11-258">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="efd11-259">Если вы сделали это ранее...</span><span class="sxs-lookup"><span data-stu-id="efd11-259">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="efd11-260">Сделать это сейчас...</span><span class="sxs-lookup"><span data-stu-id="efd11-260">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="efd11-261">Link.xml</span><span class="sxs-lookup"><span data-stu-id="efd11-261">Link.xml</span></span>

<span data-ttu-id="efd11-262">Если приложение ранее использовало распределение NuGet МРТК, `link.xml` файл был удален из пакета Foundation.</span><span class="sxs-lookup"><span data-stu-id="efd11-262">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="efd11-263">Чтобы восстановить правила сохранения кода, при открытии проекта в Unity будет создан файл по умолчанию `link.xml` в `Assets/MixedRealityToolkit.Generated` .</span><span class="sxs-lookup"><span data-stu-id="efd11-263">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="efd11-264">Рекомендуется добавлять этот файл (и `link.xml.meta` ) в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="efd11-264">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="efd11-265">Изменение ограничений преобразования</span><span class="sxs-lookup"><span data-stu-id="efd11-265">Transform Constraint changes</span></span>

<span data-ttu-id="efd11-266">Свойство Таржеттрансформ помечено как устаревшее, так как оно не было использовано системой ограничений.</span><span class="sxs-lookup"><span data-stu-id="efd11-266">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="efd11-267">Логика ограничения основана на преобразовании, переданном в методы Initialize и Apply.</span><span class="sxs-lookup"><span data-stu-id="efd11-267">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="efd11-268">Пользовательские ограничения, зависящие от этого свойства, могут кэшировать Таржеттрансформ в своей реализации, сохраняя преобразование компонента ограничения для достижения того же поведения.</span><span class="sxs-lookup"><span data-stu-id="efd11-268">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="efd11-269">Сохраненный исходный `worldPoseOnManipulationStart` тип данных World изменился с микседреалитипосе на микседреалититрансформ, который включает значение локального масштаба для управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="efd11-269">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="efd11-270">При таком изменении нет необходимости в отдельном кэшировании начальных значений масштаба.</span><span class="sxs-lookup"><span data-stu-id="efd11-270">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="efd11-271">Новое свойство в Имикседреалитидиктатионсистем</span><span class="sxs-lookup"><span data-stu-id="efd11-271">New property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="efd11-272">В `AudioClip` интерфейс имикседреалитидиктатионсистем Добавлено новое свойство.</span><span class="sxs-lookup"><span data-stu-id="efd11-272">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="efd11-273">`AudioClip`Свойство обеспечивает доступ к аудиоклипу, связанному с текущим сеансом диктовки.</span><span class="sxs-lookup"><span data-stu-id="efd11-273">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="efd11-274">Пользователи должны реализовать свойство в своих скриптах, реализующих интерфейс.</span><span class="sxs-lookup"><span data-stu-id="efd11-274">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="efd11-275">Интерфейсов службы, отключение</span><span class="sxs-lookup"><span data-stu-id="efd11-275">Service facades turn down</span></span>

<span data-ttu-id="efd11-276">Интерфейсов служб выключаются в 2,5.</span><span class="sxs-lookup"><span data-stu-id="efd11-276">Services facades are being turned down in 2.5.</span></span> <span data-ttu-id="efd11-277">Эта функция была изначально добавлена для упрощения настройки профилей МРТК (путем создания имитации в сцене объекты gameobject, которая представляет каждую из служб МРТК).</span><span class="sxs-lookup"><span data-stu-id="efd11-277">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="efd11-278">В долгосрочной перспективе мы хотим избежать создания фиктивных объектов в игре и попытаться синхронизировать их (так как синхронизация данных и проблемы с источником истинно затрудняют масштабирование и получение прав).</span><span class="sxs-lookup"><span data-stu-id="efd11-278">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="efd11-279">В 2,5 обработчики фасаднойа службы, чтобы гарантировать, что обновление проекта выполняется без проблем. все интерфейсов, существующие в проекте, будут удалены обработчиком фасадной службы, чтобы обеспечить автоматическое исправление сцен, открытых в 2,5.</span><span class="sxs-lookup"><span data-stu-id="efd11-279">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="efd11-280">Оставшийся код, связанный с компонентом фасадной службы, будет удален в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="efd11-280">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="efd11-281">Добавление контроллера движения в службу моделирования ввода</span><span class="sxs-lookup"><span data-stu-id="efd11-281">Addition of motion controller to input simulation service</span></span>

<span data-ttu-id="efd11-282">Моделирование контроллера движения теперь предлагается в режиме воспроизведения редактора вместе с существующей имитацией руки.</span><span class="sxs-lookup"><span data-stu-id="efd11-282">Motion controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="efd11-283">Чтобы включить это изменение, многие текущие функции, поля и свойства теперь помечены как устаревшие, с `InputSimulationService.cs` `MixedRealityInputSimulationProfile.cs` получением наиболее значительных изменений.</span><span class="sxs-lookup"><span data-stu-id="efd11-283">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="efd11-284">Логика и поведение соответствующего кода во многом остаются неизменными, а большинство устаревших функций и т. д. связаны с заменой ссылки на "руки" на более универсальный термин "Controller" (например `DefaultHandSimulationMode` , from to `DefaultControllerSimulationMode` ).</span><span class="sxs-lookup"><span data-stu-id="efd11-284">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="efd11-285">Помимо получения новых имен, возвращаемый тип некоторых новых функций обновляется в соответствии с изменением имени или поведения (например, на `GetControllerDevice` основе первоначального возврата `GetHandDevice` `BaseController` вместо `SimulatedHand` ).</span><span class="sxs-lookup"><span data-stu-id="efd11-285">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="efd11-286">`IInputSimulationService` теперь имеет новые свойства `MotionControllerDataLeft` и `MotionControllerDataRight` .</span><span class="sxs-lookup"><span data-stu-id="efd11-286">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="efd11-287">`MixedRealityInputSimulationProfile` Теперь включает новые поля для назначения сочетаний клавиш определенными кнопками контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="efd11-287">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="efd11-288">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="efd11-288">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="efd11-289">Камеракаче может создать новую камеру при завершении работы</span><span class="sxs-lookup"><span data-stu-id="efd11-289">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="efd11-290">В некоторых ситуациях (например, при использовании поставщика Леапмотион в редакторе Unity) Камеракаче может повторно создать Маинкамера при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="efd11-290">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="efd11-291">Дополнительные сведения см. в [этой статье](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .</span><span class="sxs-lookup"><span data-stu-id="efd11-291">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="efd11-292">FileNotFoundException при импорте примеров с помощью диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="efd11-292">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="efd11-293">В зависимости от длины пути проекта Импорт примеров через диспетчер пакетов Unity может создавать сообщения FileNotFoundException в консоли Unity.</span><span class="sxs-lookup"><span data-stu-id="efd11-293">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="efd11-294">Причина в том, что путь к файлу "Missing" превышает MAX_PATH (256 символов).</span><span class="sxs-lookup"><span data-stu-id="efd11-294">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="efd11-295">Чтобы устранить проблему, Сократите длину пути к проекту.</span><span class="sxs-lookup"><span data-stu-id="efd11-295">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="efd11-296">Спатиализер не указан.</span><span class="sxs-lookup"><span data-stu-id="efd11-296">No spatializer was specified.</span></span> <span data-ttu-id="efd11-297">Приложение не будет поддерживать Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="efd11-297">The application will not support Spatial Sound</span></span>

<span data-ttu-id="efd11-298">Предупреждение "не указано спатиализер" отображается, если не настроено звуковое спатиализер.</span><span class="sxs-lookup"><span data-stu-id="efd11-298">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="efd11-299">Это может произойти, если пакет XR не установлен, так как Unity включает спатиализерс в эти пакеты.</span><span class="sxs-lookup"><span data-stu-id="efd11-299">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="efd11-300">Чтобы устранить эту проблему, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="efd11-300">To resolve, please ensure that:</span></span>

- <span data-ttu-id="efd11-301">**Окно**  >  В **диспетчере пакетов** установлен один или несколько пакетов XR</span><span class="sxs-lookup"><span data-stu-id="efd11-301">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="efd11-302">**Набор средств**  >  для смешанной реальности **Служебные программы**  >  **Настройка проекта Unity** и выбор для **спатиализер звука**</span><span class="sxs-lookup"><span data-stu-id="efd11-302">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Выберите Audio Спатиализер](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="efd11-304">NullReferenceException: ссылка на объект не задает экземпляр объекта (SceneTransitionService.Iniтиализе)</span><span class="sxs-lookup"><span data-stu-id="efd11-304">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="efd11-305">В некоторых ситуациях открытие `EyeTrackingDemo-00-RootScene` может вызвать NullReferenceException в методе Initialize класса сценетранситионсервице.</span><span class="sxs-lookup"><span data-stu-id="efd11-305">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="efd11-306">Эта ошибка возникает из-за того, что профиль конфигурации службы смены сцены не установлен.</span><span class="sxs-lookup"><span data-stu-id="efd11-306">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="efd11-307">Чтобы устранить эту проблему, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="efd11-307">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="efd11-308">Переход к `MixedRealityToolkit` объекту в иерархии</span><span class="sxs-lookup"><span data-stu-id="efd11-308">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="efd11-309">В окне инспектора выберите `Extensions`</span><span class="sxs-lookup"><span data-stu-id="efd11-309">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="efd11-310">Если не развернуто, разверните узел `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="efd11-310">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="efd11-311">Присвойте параметру `Configuration Profile` значение **мрткексамплешубсценетранситионсервицепрофиле** .</span><span class="sxs-lookup"><span data-stu-id="efd11-311">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![Исправить переход сцены](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="efd11-313">Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="efd11-313">Oculus Quest</span></span>

<span data-ttu-id="efd11-314">В настоящее время существует известная ошибка при использовании [подключаемого модуля Окулус XR с целью использования изолированных платформ](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="efd11-314">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="efd11-315">Ознакомьтесь с разметкой об ошибках Окулус, а также с заметками о выпуске для обновлений.</span><span class="sxs-lookup"><span data-stu-id="efd11-315">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="efd11-316">Ошибка указывает на этот набор из трех ошибок:</span><span class="sxs-lookup"><span data-stu-id="efd11-316">The bug is signified with this set of 3 errors:</span></span>

![Ошибка подключаемого модуля XR Окулус](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="efd11-318">Унитюи и Текстмешпро</span><span class="sxs-lookup"><span data-stu-id="efd11-318">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="efd11-319">Существует известная ошибка для новых версий Текстмешпро (1.5.0 + или более поздней версии), где размер шрифта по умолчанию для раскрывающихся списков и интервалы между символами шрифта были изменены.</span><span class="sxs-lookup"><span data-stu-id="efd11-319">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Образ TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="efd11-321">Это можно обойти, понизить до более ранней версии Текстмешпро.</span><span class="sxs-lookup"><span data-stu-id="efd11-321">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="efd11-322">Дополнительные сведения см. в разделе о [выпуске #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .</span><span class="sxs-lookup"><span data-stu-id="efd11-322">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
