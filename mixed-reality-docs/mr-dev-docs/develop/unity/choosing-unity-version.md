---
title: Выбор версии Unity и подключаемого модуля XR
description: Оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080701"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="c5ba2-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="c5ba2-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="c5ba2-105">Хотя сейчас мы **рекомендуем установить Unity 2020,3 LTS с последним подключаемым модулем Опенкср смешанной реальности** для разработки смешанной реальности, вы также можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="c5ba2-106">Unity 2020,3 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="c5ba2-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="c5ba2-107">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 и Windows Mixed Reality — **Unity 2020,3 LTS с последним подключаемым модулем Опенкср смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="c5ba2-108">Чтобы избежать известных проблем с производительностью более ранних сборок 2020,3, необходимо использовать 2020.3.8 F1 или более позднюю версию для установки исправлений Unity.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5ba2-109">Unity 2020 не поддерживает нацеливание на HoloLens (1-й общий).</span><span class="sxs-lookup"><span data-stu-id="c5ba2-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="c5ba2-110">Эти гарнитуры поддерживаются в **[unity 2019 LTS](#unity-20194-lts)** с устаревшим встроенным XR для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="c5ba2-111">Удаленная визуализация Azure еще не отгрузила обновленный выпуск, поддерживающий Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-111">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="c5ba2-112">Если проект Unity использует удаленную визуализацию Azure, мы рекомендуем отключить обновление проекта до Unity 2020, пока не будет доступен обновленный пакет.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-112">If your Unity project uses Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until an updated package is available.</span></span>

<span data-ttu-id="c5ba2-113">Лучший способ установки и администрирования Unity — с помощью <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-113">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="c5ba2-114">После установки откройте центр Unity:</span><span class="sxs-lookup"><span data-stu-id="c5ba2-114">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="c5ba2-115">Выберите вкладку **установки** и нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="c5ba2-115">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="c5ba2-116">Выберите Unity 2020,3 LTS и нажмите кнопку **Далее** .</span><span class="sxs-lookup"><span data-stu-id="c5ba2-116">Select Unity 2020.3 LTS and click **Next**</span></span>

![Установить новую версию центра Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="c5ba2-118">Проверьте следующие компоненты в разделе **"платформы"**</span><span class="sxs-lookup"><span data-stu-id="c5ba2-118">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="c5ba2-119">**поддержка сборки для универсальной платформы Windows**;</span><span class="sxs-lookup"><span data-stu-id="c5ba2-119">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="c5ba2-120">**поддержка сборки для Windows (IL2CPP)** .</span><span class="sxs-lookup"><span data-stu-id="c5ba2-120">**Windows Build Support (IL2CPP)**</span></span>

![Параметр Unity Universal Windows Platform Build Support (Поддержка сборки для универсальной платформы Windows)](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="c5ba2-122">Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="c5ba2-122">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр Unity Windows Build Support (Поддержка сборки для Windows)](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c5ba2-124">Использование подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="c5ba2-124">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="c5ba2-125">Хотя мы рекомендуем использовать Опенкср для всех новых проектов, Unity 2020,3 LTS также поддерживает [подключаемый модуль Windows XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="c5ba2-125">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="c5ba2-126">Этот подключаемый модуль полностью поддерживается, хотя он не будет принимать новые функции, такие как поддержка AR Foundation 4,0.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-126">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="c5ba2-127">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="c5ba2-127">Unity 2019.4 LTS</span></span>

<span data-ttu-id="c5ba2-128">Если необходимо использовать Unity 2019, можно использовать **unity 2019 LTS с устаревшими встроенными XR**.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-128">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="c5ba2-129">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="c5ba2-129">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c5ba2-130">Настройка устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="c5ba2-130">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="c5ba2-131">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-131">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="c5ba2-132">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-132">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="c5ba2-133">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-133">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="c5ba2-134">Если вы разрабатываете приложения для HoloLens (1-го поколения), эти гарнитуры остаются поддерживаемыми в Unity 2019 LTS с устаревшим встроенным XRом для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-134">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="c5ba2-135">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="c5ba2-135">Unity 2021.1</span></span>

<span data-ttu-id="c5ba2-136">Если вы пытаетесь выполнить ранние сборки **Unity 2021,1** , следует перейти к **подключаемому модулю опенкср**, так как подключаемый модуль XR для Windows устарел.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="c5ba2-137">Начиная с Unity 2021,2, подключаемый модуль Опенкср будет единственным путем для разработки смешанной реальности, так как подключаемый модуль XR для Windows больше не будет поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="c5ba2-138">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="c5ba2-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="c5ba2-139">Если у вас уже есть проект, использующий Unity 2018,4 LTS, модуль Unity по-своему будет поддерживаться в течение 2 лет после его выпуска.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="c5ba2-140">Unity 2018 LTS будет обращаться к концу службы в пружине 2021.</span><span class="sxs-lookup"><span data-stu-id="c5ba2-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
