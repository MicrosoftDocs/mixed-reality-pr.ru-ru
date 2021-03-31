---
title: Выбор версии Unity и подключаемого модуля XR
description: Оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938143"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="84e25-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="84e25-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="84e25-105">В настоящее время мы **рекомендуем установить Unity 2019,4 LTS и использовать устаревшие встроенные XR** для разработки смешанной реальности. Кроме того, вы можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="84e25-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="84e25-106">Unity 2019,4 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="84e25-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="84e25-107">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 и Windows Mixed Reality — **Unity 2019,4 LTS с использованием устаревшей встроенной поддержки XR** .</span><span class="sxs-lookup"><span data-stu-id="84e25-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="84e25-108">Лучший способ установки и управления Unity — через <a href="https://unity3d.com/get-unity/download" target="_blank">[концентратор Unity]</a>.</span><span class="sxs-lookup"><span data-stu-id="84e25-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="84e25-109">После установки откройте центр Unity:</span><span class="sxs-lookup"><span data-stu-id="84e25-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="84e25-110">Выберите вкладку **установки** и нажмите кнопку **Добавить** .</span><span class="sxs-lookup"><span data-stu-id="84e25-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="84e25-111">Выберите Unity 2019,4 LTS и нажмите кнопку **Далее** .</span><span class="sxs-lookup"><span data-stu-id="84e25-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Установить новую версию центра Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="84e25-113">Проверьте следующие компоненты в разделе **"платформы"**</span><span class="sxs-lookup"><span data-stu-id="84e25-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="84e25-114">**Поддержка сборки универсальная платформа Windows**</span><span class="sxs-lookup"><span data-stu-id="84e25-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="84e25-115">**Поддержка сборки Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="84e25-115">**Windows Build Support (IL2CPP)**</span></span>

![Параметр поддержки сборки универсальная платформа Windows Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="84e25-117">Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="84e25-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр поддержки сборки Windows Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="84e25-119">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="84e25-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84e25-120">Настройка устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="84e25-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="84e25-121">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="84e25-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="84e25-122">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="84e25-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="84e25-123">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="84e25-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="84e25-124">Если вы разрабатываете приложения для HoloLens (1-го поколения), эти гарнитуры остаются поддерживаемыми в Unity 2019 LTS с устаревшим встроенным XRом для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="84e25-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="84e25-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="84e25-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="84e25-126">Если вы используете **Unity 2020,3 LTS**, можно использовать **подключаемый модуль XR Windows** для разработки приложений HoloLens 2 и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="84e25-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="84e25-127">Однако существуют известные проблемы, влияющие на стабильность и другие функции в HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="84e25-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="84e25-128">Передача буфера глубины в последние сборки Unity 2020 увеличилась, что приводит к нестабильной работе.</span><span class="sxs-lookup"><span data-stu-id="84e25-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="84e25-129">Приложения с удаленным взаимодействием holographic, использующие целевой объект сборки универсальная платформа Windows, не работают.</span><span class="sxs-lookup"><span data-stu-id="84e25-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="84e25-130">Система заданий графики Unity по умолчанию включена, несмотря на то, что она несовместима с проектами HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84e25-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="84e25-131">Если вы решили запустить новый проект в Unity 2020 уже сегодня, перед отправкой приложения убедитесь, что в ближайшие месяцы для обновленных сборок Unity и сборки подключаемых модулей Windows XR.</span><span class="sxs-lookup"><span data-stu-id="84e25-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="84e25-132">Это обеспечит надлежащую стабильность работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="84e25-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84e25-133">Использование подключаемого модуля XR для Windows</span><span class="sxs-lookup"><span data-stu-id="84e25-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="84e25-134">Использование Опенкср</span><span class="sxs-lookup"><span data-stu-id="84e25-134">Using OpenXR</span></span>

<span data-ttu-id="84e25-135">Unity 2020,3 LTS также поддерживает общедоступную предварительную версию подключаемого модуля **Опенкср смешанной реальности** .</span><span class="sxs-lookup"><span data-stu-id="84e25-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="84e25-136">Подключаемый модуль Mixed Reality Опенкср полностью поддерживает AR Foundation 4,0, предоставляя реализации Арпланеманажер и Аррайкастманажер.</span><span class="sxs-lookup"><span data-stu-id="84e25-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="84e25-137">Это позволяет писать код проверки попадания один раз, который затем охватывает телефоны и Аркореы и ARKit телефонов и планшеты.</span><span class="sxs-lookup"><span data-stu-id="84e25-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="84e25-138">В дальнейшем в этом году **unity 2020,3 LTS с подключаемым модулем опенкср** станет рекомендуемой конфигурацией Unity, а будущие функции HoloLens 2 в Unity будут предоставляться только через этот подключаемый модуль.</span><span class="sxs-lookup"><span data-stu-id="84e25-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="84e25-139">Вы можете запустить проект сейчас, если проект предназначен для HoloLens 2, в настоящее время будет вычислена стабильность Unity 2020 и другие проблемы, перечисленные выше.</span><span class="sxs-lookup"><span data-stu-id="84e25-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="84e25-140">Не забудьте вернуться в ближайшие месяцы для обновленных сборок Unity и сборок подключаемых модулей Опенкср перед доставкой приложения.</span><span class="sxs-lookup"><span data-stu-id="84e25-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="84e25-141">Это обеспечит надлежащую стабильность работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="84e25-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="84e25-142">Использование подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="84e25-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="84e25-143">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="84e25-143">Unity 2021.1</span></span>

<span data-ttu-id="84e25-144">Если вы пытаетесь выполнить ранние сборки **Unity 2021,1** , следует перейти к **подключаемому модулю опенкср**, так как подключаемый модуль XR для Windows устарел.</span><span class="sxs-lookup"><span data-stu-id="84e25-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="84e25-145">Начиная с Unity 2021,2, подключаемый модуль Опенкср будет единственным путем для разработки смешанной реальности, так как подключаемый модуль XR для Windows больше не будет поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="84e25-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="84e25-146">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="84e25-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="84e25-147">Если у вас уже есть проект, использующий Unity 2018,4 LTS, модуль Unity по-своему будет поддерживаться в течение 2 лет после его выпуска.</span><span class="sxs-lookup"><span data-stu-id="84e25-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="84e25-148">Unity 2018 LTS будет обращаться к концу службы в пружине 2021.</span><span class="sxs-lookup"><span data-stu-id="84e25-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
