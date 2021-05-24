---
title: Выбор версии Unity и подключаемого модуля XR
description: Оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333386"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="e99f6-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="e99f6-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="e99f6-105">В настоящее время мы **рекомендуем установить Unity 2019,4 LTS и использовать устаревшие встроенные XR** для разработки смешанной реальности. Кроме того, вы можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="e99f6-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="e99f6-106">Unity 2019,4 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="e99f6-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="e99f6-107">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 и Windows Mixed Reality — **Unity 2019,4 LTS с использованием устаревшей встроенной поддержки XR** .</span><span class="sxs-lookup"><span data-stu-id="e99f6-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="e99f6-108">Лучший способ установки и управления Unity — через <a href="https://unity3d.com/get-unity/download" target="_blank">[концентратор Unity]</a>.</span><span class="sxs-lookup"><span data-stu-id="e99f6-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="e99f6-109">После установки откройте центр Unity:</span><span class="sxs-lookup"><span data-stu-id="e99f6-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="e99f6-110">Выберите вкладку **установки** и нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="e99f6-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="e99f6-111">Выберите Unity 2019,4 LTS и нажмите кнопку **Далее** .</span><span class="sxs-lookup"><span data-stu-id="e99f6-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Установить новую версию центра Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="e99f6-113">Проверьте следующие компоненты в разделе **"платформы"**</span><span class="sxs-lookup"><span data-stu-id="e99f6-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="e99f6-114">**поддержка сборки для универсальной платформы Windows**;</span><span class="sxs-lookup"><span data-stu-id="e99f6-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="e99f6-115">**поддержка сборки для Windows (IL2CPP)** .</span><span class="sxs-lookup"><span data-stu-id="e99f6-115">**Windows Build Support (IL2CPP)**</span></span>

![Параметр Unity Universal Windows Platform Build Support (Поддержка сборки для универсальной платформы Windows)](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="e99f6-117">Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="e99f6-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр Unity Windows Build Support (Поддержка сборки для Windows)](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="e99f6-119">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="e99f6-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e99f6-120">Настройка устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="e99f6-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="e99f6-121">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="e99f6-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="e99f6-122">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="e99f6-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="e99f6-123">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="e99f6-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="e99f6-124">Если вы разрабатываете приложения для HoloLens (1-го поколения), эти гарнитуры остаются поддерживаемыми в Unity 2019 LTS с устаревшим встроенным XRом для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="e99f6-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="e99f6-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="e99f6-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="e99f6-126">Если вы используете **Unity 2020,3 LTS**, можно использовать **подключаемый модуль XR Windows** для разработки приложений HoloLens 2 и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e99f6-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="e99f6-127">Однако существуют известные проблемы, влияющие на стабильность и другие функции в HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="e99f6-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="e99f6-128">Приложения с удаленным взаимодействием holographic, использующие целевой объект сборки универсальная платформа Windows, не работают.</span><span class="sxs-lookup"><span data-stu-id="e99f6-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="e99f6-129">Система заданий графики Unity по умолчанию включена, несмотря на то, что она несовместима с проектами HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e99f6-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="e99f6-130">Если вы решили использовать Unity 2020, не забудьте выполнить обновление до Unity 2020.3.6 F1 или более поздней версии, чтобы обеспечить надлежащую стабильность работы пользователя.</span><span class="sxs-lookup"><span data-stu-id="e99f6-130">If you choose to use Unity 2020, be sure to upgrade to Unity 2020.3.6f1 or later versions to ensure your user experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e99f6-131">Использование подключаемого модуля Windows XR</span><span class="sxs-lookup"><span data-stu-id="e99f6-131">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="e99f6-132">Использование Опенкср</span><span class="sxs-lookup"><span data-stu-id="e99f6-132">Using OpenXR</span></span>

<span data-ttu-id="e99f6-133">Unity 2020,3 LTS также поддерживает общедоступную предварительную версию подключаемого модуля **Опенкср смешанной реальности** .</span><span class="sxs-lookup"><span data-stu-id="e99f6-133">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="e99f6-134">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="e99f6-134">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="e99f6-135">Это позволяет писать код проверки попадания один раз, который затем охватывает телефоны и Аркореы и ARKit телефонов и планшеты.</span><span class="sxs-lookup"><span data-stu-id="e99f6-135">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="e99f6-136">В дальнейшем в этом году **unity 2020,3 LTS с подключаемым модулем опенкср** станет рекомендуемой конфигурацией Unity, а будущие функции HoloLens 2 в Unity будут предоставляться только через этот подключаемый модуль.</span><span class="sxs-lookup"><span data-stu-id="e99f6-136">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e99f6-137">Использование подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="e99f6-137">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="e99f6-138">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="e99f6-138">Unity 2021.1</span></span>

<span data-ttu-id="e99f6-139">Если вы пытаетесь выполнить ранние сборки **Unity 2021,1** , следует перейти к **подключаемому модулю опенкср**, так как подключаемый модуль XR для Windows устарел.</span><span class="sxs-lookup"><span data-stu-id="e99f6-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="e99f6-140">Начиная с Unity 2021,2, подключаемый модуль Опенкср будет единственным путем для разработки смешанной реальности, так как подключаемый модуль XR для Windows больше не будет поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="e99f6-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="e99f6-141">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="e99f6-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="e99f6-142">Если у вас уже есть проект, использующий Unity 2018,4 LTS, модуль Unity по-своему будет поддерживаться в течение 2 лет после его выпуска.</span><span class="sxs-lookup"><span data-stu-id="e99f6-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="e99f6-143">Unity 2018 LTS будет обращаться к концу службы в пружине 2021.</span><span class="sxs-lookup"><span data-stu-id="e99f6-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
