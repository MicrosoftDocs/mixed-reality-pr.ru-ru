---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: Добавьте подключаемый модуль Microsoft Спатиализер в проект Unity, чтобы получить доступ к аппаратной разгрузке HoloLens 2 ХРТФ.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук
ms.openlocfilehash: 9ddfd1644a20ac063551b8140f9f8950ae172196
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91694492"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="51196-105">Добавление пространственного звука в проект Unity</span><span class="sxs-lookup"><span data-stu-id="51196-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="51196-106">Добро пожаловать в учебник по пространственному аудио для Unity в HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="51196-106">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="51196-107">В этой последовательности учебников показано следующее:</span><span class="sxs-lookup"><span data-stu-id="51196-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="51196-108">Как использовать функцию перегрузки, связанную с HEAD (ХРТФ), в HoloLens 2 в Unity</span><span class="sxs-lookup"><span data-stu-id="51196-108">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="51196-109">Включение переглагола при использовании разгрузки ХРТФ</span><span class="sxs-lookup"><span data-stu-id="51196-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="51196-110">В [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.</span><span class="sxs-lookup"><span data-stu-id="51196-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="51196-111">Сведения о том, что означает спатиализеие звуков с помощью технологий пространственности на основе ХРТФ и рекомендации по их полезности, см. в статье о [проектировании пространственных звуков](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="51196-111">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="51196-112">Что такое разгрузка ХРТФ?</span><span class="sxs-lookup"><span data-stu-id="51196-112">What is HRTF offload?</span></span>
<span data-ttu-id="51196-113">Для обработки звука с использованием алгоритмов на основе ХРТФ требуется большой объем специализированных вычислений.</span><span class="sxs-lookup"><span data-stu-id="51196-113">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="51196-114">HoloLens 2 включает выделенное оборудование, которое можно использовать, чтобы избежать перегрузки процессора приложений, таким путем «разложить» обработку алгоритмов на основе ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="51196-114">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="51196-115">Подключаемый модуль Microsoft спатиализер предоставляет приложению простой способ воспользоваться преимуществами выделенного оборудования ХРТФ, чтобы приложение могла использовать больше процессоров приложений для операций, отличных от пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="51196-115">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="51196-116">Цели</span><span class="sxs-lookup"><span data-stu-id="51196-116">Objectives</span></span>
<span data-ttu-id="51196-117">В этой первой главе вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="51196-117">In this first chapter, you'll:</span></span>
* <span data-ttu-id="51196-118">Создание проекта Unity и импорт МРТК</span><span class="sxs-lookup"><span data-stu-id="51196-118">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="51196-119">Импорт подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="51196-119">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="51196-120">Включение подключаемого модуля Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="51196-120">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="51196-121">Включение пространственного звука на рабочей станции разработчика</span><span class="sxs-lookup"><span data-stu-id="51196-121">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="51196-122">Создание проекта и добавление NuGet для Unity</span><span class="sxs-lookup"><span data-stu-id="51196-122">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="51196-123">Начните с пустого проекта Unity, а затем добавьте и настройте NuGet для Unity:</span><span class="sxs-lookup"><span data-stu-id="51196-123">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="51196-124">Скачайте последнюю версию [нужетфорунити. пакет unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="51196-124">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="51196-125">В строке меню Unity щелкните **активы-> импортировать пакет-> пользовательский пакет...** и установите пакет нужетфорунити:</span><span class="sxs-lookup"><span data-stu-id="51196-125">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Импорт пользовательского пакета](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="51196-127">Добавление пакета Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="51196-127">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="51196-128">Поддержка Windows Mixed Reality в Unity 2019 и более поздних версиях содержится в необязательном пакете.</span><span class="sxs-lookup"><span data-stu-id="51196-128">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="51196-129">Чтобы добавить его в проект, откройте **окно Диспетчер пакетов >** в строке меню Unity:</span><span class="sxs-lookup"><span data-stu-id="51196-129">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Меню диспетчера пакетов](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="51196-131">Затем найдите и установите пакет **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="51196-131">Then find and install the **Windows Mixed Reality** package:</span></span>

![Окно диспетчера пакетов](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="51196-133">Установка МРТК и Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="51196-133">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="51196-134">Используя NuGet для Unity, установите подключаемые модули МРТК и Microsoft Спатиализер.</span><span class="sxs-lookup"><span data-stu-id="51196-134">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="51196-135">В строке меню Unity щелкните **NuGet-> Управление пакетами NuGet** .</span><span class="sxs-lookup"><span data-stu-id="51196-135">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages** .</span></span>

![Управление пакетами NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="51196-137">В поле **поиска** введите "Microsoft. Микседреалити. Toolkit" и установите пакет мртк Core: **Microsoft. микседреалити. Toolkit. Foundation** .</span><span class="sxs-lookup"><span data-stu-id="51196-137">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Пакет NuGet МРТК](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="51196-139">[Пакет NuGet мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) имеет дополнительный контекст и сведения.</span><span class="sxs-lookup"><span data-stu-id="51196-139">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="51196-140">В поле **поиска** введите "Microsoft. спатиалаудио" и установите пакет Microsoft Спатиализер: **Microsoft. спатиалаудио. спатиализер. Unity.**</span><span class="sxs-lookup"><span data-stu-id="51196-140">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![NuGet подключаемого модуля спатиализер](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="51196-142">Настройка МРТК в проекте</span><span class="sxs-lookup"><span data-stu-id="51196-142">Set up MRTK in your project</span></span>

1. <span data-ttu-id="51196-143">Откройте окно параметры сборки, выбрав **файл-> параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="51196-143">Open the Build Settings window by going to **File -> Build Settings** .</span></span>

2. <span data-ttu-id="51196-144">Выберите _универсальная платформа Windows_ и нажмите кнопку **Переключить платформу** .</span><span class="sxs-lookup"><span data-stu-id="51196-144">Select the _Universal Windows Platform_ and click **Switch Platform** .</span></span>

3. <span data-ttu-id="51196-145">Щелкните **Параметры проигрывателя** в **окне сборка** , чтобы открыть свойства **параметров проигрывателя** на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="51196-145">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="51196-146">В разделе **Параметры XR** установите флажок **Поддерживаемые виртуальные реальность** .</span><span class="sxs-lookup"><span data-stu-id="51196-146">Under **XR Settings** , check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="51196-147">В разделе **Параметры XR** измените **режим отображения стерео** на **один экземпляр однопроходного экземпляра** .</span><span class="sxs-lookup"><span data-stu-id="51196-147">Under **XR Settings** , change the **Stereo Rendering Mode** to **Single Pass Instanced** .</span></span>
    * <span data-ttu-id="51196-148">В разделе **Параметры публикации** установите флажок **пространственное восприятие** в разделе **возможности** .</span><span class="sxs-lookup"><span data-stu-id="51196-148">Under **Publishing Settings** , check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="51196-149">В строке меню щелкните **набор средств для смешанной реальности — > добавить в сцену и настроить..**</span><span class="sxs-lookup"><span data-stu-id="51196-149">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="51196-150">чтобы добавить МРТК в сцену.</span><span class="sxs-lookup"><span data-stu-id="51196-150">to add MRTK to your scene.</span></span>

<span data-ttu-id="51196-151">Дополнительные рекомендации, включая создание приложения и развертывание в HoloLens 2, см. в [главе 1 базового модуля MR Learning](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="51196-151">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="51196-152">Включение подключаемого модуля Microsoft Спатиализер</span><span class="sxs-lookup"><span data-stu-id="51196-152">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="51196-153">Включите подключаемый модуль **Microsoft спатиализер** .</span><span class="sxs-lookup"><span data-stu-id="51196-153">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="51196-154">Откройте **> параметры проекта-> аудио** и измените **подключаемый модуль Спатиализер** на "Microsoft спатиализер".</span><span class="sxs-lookup"><span data-stu-id="51196-154">Open **Edit -> Project Settings -> Audio** , and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="51196-155">Теперь раздел **аудио** в **параметрах проекта** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="51196-155">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Параметры проекта, отображающие подключаемый модуль спатиализер](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="51196-157">Включение пространственного звука на рабочей станции</span><span class="sxs-lookup"><span data-stu-id="51196-157">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="51196-158">В настольных версиях Windows Пространственный звук по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="51196-158">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="51196-159">Включите его, щелкнув значок тома правой кнопкой мыши на панели задач.</span><span class="sxs-lookup"><span data-stu-id="51196-159">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="51196-160">Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Пространственный звук — > Windows Sonic для наушников** .</span><span class="sxs-lookup"><span data-stu-id="51196-160">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones** .</span></span>

![Параметры пространственного звука рабочего стола](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="51196-162">Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="51196-162">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51196-163">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="51196-163">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51196-164">Пространственный звуковой раздел Unity 2</span><span class="sxs-lookup"><span data-stu-id="51196-164">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

