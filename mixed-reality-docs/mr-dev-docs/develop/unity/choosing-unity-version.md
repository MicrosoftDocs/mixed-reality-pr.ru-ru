---
title: Выбор версии Unity и подключаемого модуля XR
description: Оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906859"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="051b8-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="051b8-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="051b8-105">В настоящее время мы **рекомендуем установить Unity 2019,4 LTS и использовать устаревшие встроенные XR** для разработки смешанной реальности. Кроме того, вы можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="051b8-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="051b8-106">Unity 2019,4 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="051b8-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="051b8-107">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 и Windows Mixed Reality — **Unity 2019,4 LTS с использованием устаревшей встроенной поддержки XR** .</span><span class="sxs-lookup"><span data-stu-id="051b8-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="051b8-108">Лучший способ установки и управления Unity — через <a href="https://unity3d.com/get-unity/download" target="_blank">[концентратор Unity]</a>.</span><span class="sxs-lookup"><span data-stu-id="051b8-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="051b8-109">После установки откройте центр Unity:</span><span class="sxs-lookup"><span data-stu-id="051b8-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="051b8-110">Выберите вкладку **установки** и нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="051b8-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="051b8-111">Выберите Unity 2019,4 LTS и нажмите кнопку **Далее** .</span><span class="sxs-lookup"><span data-stu-id="051b8-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Установить новую версию центра Unity](images/unity-hub-img-2019.png)

3. <span data-ttu-id="051b8-113">Проверьте следующие компоненты в разделе **"платформы"**</span><span class="sxs-lookup"><span data-stu-id="051b8-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="051b8-114">**поддержка сборки для универсальной платформы Windows**;</span><span class="sxs-lookup"><span data-stu-id="051b8-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="051b8-115">**поддержка сборки для Windows (IL2CPP)** .</span><span class="sxs-lookup"><span data-stu-id="051b8-115">**Windows Build Support (IL2CPP)**</span></span>

![Параметр Unity Universal Windows Platform Build Support (Поддержка сборки для универсальной платформы Windows)](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="051b8-117">Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="051b8-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр Unity Windows Build Support (Поддержка сборки для Windows)](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="051b8-119">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="051b8-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="051b8-120">Настройка устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="051b8-120">Set up Legacy Built-in XR</span></span>](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="051b8-121">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="051b8-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="051b8-122">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="051b8-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="051b8-123">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="051b8-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="051b8-124">Если вы разрабатываете приложения для HoloLens (1-го поколения), эти гарнитуры остаются поддерживаемыми в Unity 2019 LTS с устаревшим встроенным XRом для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="051b8-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="051b8-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="051b8-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="051b8-126">Если вы используете **Unity 2020,3 LTS**, то текущая рекомендация корпорации Майкрософт является последним **подключаемым модулем Опенкср смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="051b8-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="051b8-127">Чтобы избежать известных проблем с производительностью более ранних сборок 2020,3, необходимо использовать 2020.3.8 F1 или более позднюю версию для установки исправлений Unity.</span><span class="sxs-lookup"><span data-stu-id="051b8-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="051b8-128">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="051b8-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="051b8-129">Это позволяет писать код проверки попадания один раз, который затем охватывает телефоны и Аркореы и ARKit телефонов и планшеты.</span><span class="sxs-lookup"><span data-stu-id="051b8-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="051b8-130">Однако существуют известные проблемы, которые влияют на проекты Unity 2020 LTS:</span><span class="sxs-lookup"><span data-stu-id="051b8-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="051b8-131">В 10.5.0 или более старой версии конвейера отрисовки (URP) на устройствах HoloLens 2 имеются штрафы в производительности.</span><span class="sxs-lookup"><span data-stu-id="051b8-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="051b8-132">Если вы решили запустить новый проект в Unity 2020 уже сегодня, перед отправкой приложения убедитесь, что в ближайшие недели для обновленных сборок Unity и пакетов URP.</span><span class="sxs-lookup"><span data-stu-id="051b8-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="051b8-133">Это обеспечит надлежащую стабильность работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="051b8-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="051b8-134">Использование подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="051b8-134">Using the OpenXR plugin</span></span>](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="051b8-135">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="051b8-135">Unity 2021.1</span></span>

<span data-ttu-id="051b8-136">Если вы пытаетесь выполнить ранние сборки **Unity 2021,1** , следует перейти к **подключаемому модулю опенкср**, так как подключаемый модуль XR для Windows устарел.</span><span class="sxs-lookup"><span data-stu-id="051b8-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="051b8-137">Начиная с Unity 2021,2, подключаемый модуль Опенкср будет единственным путем для разработки смешанной реальности, так как подключаемый модуль XR для Windows больше не будет поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="051b8-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="051b8-138">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="051b8-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="051b8-139">Если у вас уже есть проект, использующий Unity 2018,4 LTS, модуль Unity по-своему будет поддерживаться в течение 2 лет после его выпуска.</span><span class="sxs-lookup"><span data-stu-id="051b8-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="051b8-140">Unity 2018 LTS будет обращаться к концу службы в пружине 2021.</span><span class="sxs-lookup"><span data-stu-id="051b8-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>