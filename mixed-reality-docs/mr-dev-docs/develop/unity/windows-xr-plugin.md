---
title: Использование подключаемого модуля XR для Windows
description: Узнайте, как настроить проекты Unity с помощью и без МРТК, используя поддержку Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, разработка, начало работы, новый проект, Windows Mixed Reality, UWP, XR, производительность, устаревший, мртк, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938124"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="b59be-104">Использование подключаемого модуля XR Windows</span><span class="sxs-lookup"><span data-stu-id="b59be-104">Using Windows XR plugin</span></span>

<span data-ttu-id="b59be-105">Для разработчиков, предназначенных для Unity 2020, подключаемый модуль Windows XR обеспечивает доступ к функциям смешанной реальности на гарнитурах HoloLens 2 и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b59be-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="b59be-106">Этот подключаемый модуль также поддерживается в Unity 2019, хотя при использовании этого подключаемого модуля в этой версии существуют некоторые известные проблемы с несовместимостью с пространственными привязками Azure.</span><span class="sxs-lookup"><span data-stu-id="b59be-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="b59be-107">Хотя корпорация Майкрософт и сообщество создали средства конвертер, такие как набор средств для [смешанной реальности (мртк)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , который автоматически настраивает среду ВМР, многие разработчики хотят создавать свои впечатления с нуля.</span><span class="sxs-lookup"><span data-stu-id="b59be-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="b59be-108">В следующей документации показано, как правильно настроить проект для разработки смешанной реальности независимо от того, используется ли МРТК.</span><span class="sxs-lookup"><span data-stu-id="b59be-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="b59be-109">Параметры, которые необходимо изменить, разбиваются на две категории: параметры для каждого проекта и параметры на сцене.</span><span class="sxs-lookup"><span data-stu-id="b59be-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="b59be-110">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="b59be-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="b59be-111">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="b59be-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="b59be-112">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="b59be-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="b59be-113">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="b59be-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b59be-114">Ознакомьтесь с нашими руководствами по МРТК</span><span class="sxs-lookup"><span data-stu-id="b59be-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="b59be-115">Дополнительные сведения о функциях см. в [документации по мртк](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="b59be-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="b59be-116">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="b59be-116">Manual setup without MRTK</span></span>

<span data-ttu-id="b59be-117">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="b59be-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="b59be-119">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="b59be-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="b59be-120">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="b59be-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="b59be-121">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="b59be-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="b59be-122">Установка **архитектуры** **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="b59be-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="b59be-123">Задать **целевое устройство** в **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b59be-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="b59be-124">Задать для **типа сборки** **D3D**</span><span class="sxs-lookup"><span data-stu-id="b59be-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="b59be-125">Установить **последнюю версию** **пакета SDK для UWP**</span><span class="sxs-lookup"><span data-stu-id="b59be-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="b59be-126">Задать для **конфигурации сборки** значение **Release** , так как имеются известные проблемы с производительностью при отладке</span><span class="sxs-lookup"><span data-stu-id="b59be-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

<span data-ttu-id="b59be-128">После настройки платформы необходимо предоставить Unity знать, чтобы при экспорте создать [иммерсивное представление](../../design/app-views.md) вместо 2D-представления:</span><span class="sxs-lookup"><span data-stu-id="b59be-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="b59be-129">В редакторе Unity перейдите к разделу **правка > параметры проекта** и выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="b59be-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="b59be-130">Выберите **установить управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="b59be-130">Select **Install XR Plugin Management**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](images/wmr-config-img-5.png)

3. <span data-ttu-id="b59be-132">Выберите **инициализировать XR при запуске** и **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="b59be-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным управлением подключаемым модулем XR](images/wmr-config-img-7.png)

4. <span data-ttu-id="b59be-134">Разверните раздел **Управление подключаемым модулем XR** и выберите **универсальной на вкладке параметры платформы Windows** .</span><span class="sxs-lookup"><span data-stu-id="b59be-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="b59be-135">Если вы используете Unity 2020 или более поздней версии, вы увидите параметры для проверки **опенкср** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="b59be-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="b59be-136">Можно выбрать любую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="b59be-136">You can choose either runtime.</span></span>  <span data-ttu-id="b59be-137">Если вы специально разрабатываете для HoloLens 2 или HP reverbа G2 и решите опробовать **опенкср**, выберите поле опенкср и ознакомьтесь с нашим руководством по [использованию подключаемого модуля опенкср Mixed Reality для Unity](openxr-getting-started.md) , чтобы обеспечить правильную настройку этих устройств перед возвратом в этом учебнике.</span><span class="sxs-lookup"><span data-stu-id="b59be-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="b59be-138">Начиная с Unity 2020 LTS, корпорация Майкрософт применяет разработку с Опенкср.</span><span class="sxs-lookup"><span data-stu-id="b59be-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="b59be-139">По мере перехода по этому пути в Unity 2021,1 подключаемый модуль XR Windows будет устаревшим и удален в 2021,2, Опенкср только поддерживаемый путь.</span><span class="sxs-lookup"><span data-stu-id="b59be-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="b59be-140">Дополнительные сведения см. в [подокне использование подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="b59be-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="b59be-141">Если вы решили выбрать подключаемый модуль **Windows Mixed Reality** , установите флажок все флажки и задайте для параметра **режим отправки глубины** значение **глубиной 16 бит** .</span><span class="sxs-lookup"><span data-stu-id="b59be-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом Windows Mixed Reality](images/wmr-config-img-8.png)
