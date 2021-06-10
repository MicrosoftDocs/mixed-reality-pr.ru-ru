---
title: Выбор версии Unity и подключаемого модуля XR
description: Оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741926"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="ae8c7-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="ae8c7-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="ae8c7-105">Хотя сейчас мы **рекомендуем установить Unity 2020,3 LTS с последним подключаемым модулем Опенкср смешанной реальности** для разработки смешанной реальности, вы также можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="ae8c7-106">Unity 2020,3 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="ae8c7-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="ae8c7-107">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 и Windows Mixed Reality — **Unity 2020,3 LTS с последним подключаемым модулем Опенкср смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae8c7-108">Unity 2020 не поддерживает нацеливание на HoloLens (1-й общий).</span><span class="sxs-lookup"><span data-stu-id="ae8c7-108">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="ae8c7-109">Эти гарнитуры поддерживаются в **[unity 2019 LTS](#unity-20194-lts)** с устаревшим встроенным XR для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-109">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="ae8c7-110">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-110">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="ae8c7-111">Это позволяет писать код проверки попадания один раз, который затем охватывает телефоны и Аркореы и ARKit телефонов и планшеты.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-111">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="ae8c7-112">Лучший способ установки и администрирования Unity — с помощью <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-112">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="ae8c7-113">После установки откройте центр Unity:</span><span class="sxs-lookup"><span data-stu-id="ae8c7-113">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="ae8c7-114">Выберите вкладку **установки** и нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="ae8c7-114">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="ae8c7-115">Выберите Unity 2020,3 LTS и нажмите кнопку **Далее** .</span><span class="sxs-lookup"><span data-stu-id="ae8c7-115">Select Unity 2020.3 LTS and click **Next**</span></span>

![Установить новую версию центра Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="ae8c7-117">Проверьте следующие компоненты в разделе **"платформы"**</span><span class="sxs-lookup"><span data-stu-id="ae8c7-117">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="ae8c7-118">**поддержка сборки для универсальной платформы Windows**;</span><span class="sxs-lookup"><span data-stu-id="ae8c7-118">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="ae8c7-119">**поддержка сборки для Windows (IL2CPP)** .</span><span class="sxs-lookup"><span data-stu-id="ae8c7-119">**Windows Build Support (IL2CPP)**</span></span>

![Параметр Unity Universal Windows Platform Build Support (Поддержка сборки для универсальной платформы Windows)](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="ae8c7-121">Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="ae8c7-121">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр Unity Windows Build Support (Поддержка сборки для Windows)](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae8c7-123">Использование подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="ae8c7-123">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="ae8c7-124">Хотя мы рекомендуем использовать Опенкср для всех новых проектов, Unity 2020,3 LTS также поддерживает **[подключаемый модуль Windows XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the **[Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span></span> <span data-ttu-id="ae8c7-125">К известным проблемам, влияющим на стабильность и другие функции в HoloLens 2, относятся:</span><span class="sxs-lookup"><span data-stu-id="ae8c7-125">Known issues that affect hologram stability and other features on HoloLens 2 include:</span></span>
>
> * <span data-ttu-id="ae8c7-126">Приложения с удаленным взаимодействием holographic, использующие целевой объект сборки универсальная платформа Windows, не работают.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-126">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
> * <span data-ttu-id="ae8c7-127">Система заданий графики Unity по умолчанию включена, несмотря на то, что она несовместима с проектами HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-127">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="ae8c7-128">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="ae8c7-128">Unity 2019.4 LTS</span></span>

<span data-ttu-id="ae8c7-129">Если необходимо использовать Unity 2019, можно использовать **unity 2019 LTS с устаревшими встроенными XR**.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-129">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="ae8c7-130">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="ae8c7-130">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae8c7-131">Настройка устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="ae8c7-131">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="ae8c7-132">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-132">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="ae8c7-133">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-133">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="ae8c7-134">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-134">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="ae8c7-135">Если вы разрабатываете приложения для HoloLens (1-го поколения), эти гарнитуры остаются поддерживаемыми в Unity 2019 LTS с устаревшим встроенным XRом для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-135">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="ae8c7-136">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="ae8c7-136">Unity 2021.1</span></span>

<span data-ttu-id="ae8c7-137">Если вы пытаетесь выполнить ранние сборки **Unity 2021,1** , следует перейти к **подключаемому модулю опенкср**, так как подключаемый модуль XR для Windows устарел.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-137">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="ae8c7-138">Начиная с Unity 2021,2, подключаемый модуль Опенкср будет единственным путем для разработки смешанной реальности, так как подключаемый модуль XR для Windows больше не будет поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-138">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="ae8c7-139">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="ae8c7-139">Unity 2018.4 LTS</span></span>

<span data-ttu-id="ae8c7-140">Если у вас уже есть проект, использующий Unity 2018,4 LTS, модуль Unity по-своему будет поддерживаться в течение 2 лет после его выпуска.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-140">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="ae8c7-141">Unity 2018 LTS будет обращаться к концу службы в пружине 2021.</span><span class="sxs-lookup"><span data-stu-id="ae8c7-141">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
