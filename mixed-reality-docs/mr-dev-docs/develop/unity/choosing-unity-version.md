---
title: Выбор версии Unity и подключаемого модуля XR
description: оставайтесь в курсе последних рекомендаций по работе с модулями Unity и XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603685"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="fd9ea-104">Выбор версии Unity и подключаемого модуля XR</span><span class="sxs-lookup"><span data-stu-id="fd9ea-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="fd9ea-105">Хотя сейчас мы **рекомендуем установить Unity 2020,3 LTS с последним подключаемым модулем Опенкср смешанной реальности** для разработки смешанной реальности, вы также можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="fd9ea-106">Unity 2020,3 LTS (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="fd9ea-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="fd9ea-107">текущая рекомендуемая конфигурация Unity майкрософт для разработки HoloLens 2 и Windows Mixed Reality — **Unity 2020,3 LTS с последним подключаемым модулем опенкср смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="fd9ea-108">Чтобы избежать известных проблем с производительностью более ранних сборок 2020,3, **необходимо** использовать 2020.3.8 F1 или более позднюю версию для установки исправлений Unity.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd9ea-109">Unity 2020 не поддерживает нацеливание на HoloLens (1-й общий).</span><span class="sxs-lookup"><span data-stu-id="fd9ea-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="fd9ea-110">Эти гарнитуры поддерживаются в **[unity 2019 LTS](#unity-20194-lts)** с устаревшим встроенным XR для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="fd9ea-111">Лучший способ установки и управления Unity — через **центр Unity**:</span><span class="sxs-lookup"><span data-stu-id="fd9ea-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="fd9ea-112">Установите <a href="https://unity3d.com/get-unity/download" target="_blank">**центр Unity**</a>.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="fd9ea-113">Перейдите на вкладку **установки** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="fd9ea-114">Выберите **Unity 2020,3 LTS** и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Установка новой версии концентратора Unity](images/unity-hub-img-01.png)

4. <span data-ttu-id="fd9ea-116">Проверьте следующие компоненты в разделе **"платформы"**:</span><span class="sxs-lookup"><span data-stu-id="fd9ea-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="fd9ea-117">**поддержка сборки для универсальной платформы Windows**;</span><span class="sxs-lookup"><span data-stu-id="fd9ea-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="fd9ea-118">**поддержка сборки для Windows (IL2CPP)** .</span><span class="sxs-lookup"><span data-stu-id="fd9ea-118">**Windows Build Support (IL2CPP)**</span></span>

![Параметр Unity Universal Windows Platform Build Support (Поддержка сборки для универсальной платформы Windows)](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="fd9ea-120">Если вы ранее установили Unity без этих параметров, вы можете добавить их с помощью меню **"добавить модули"** в центре Unity:</span><span class="sxs-lookup"><span data-stu-id="fd9ea-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Параметр Unity Windows Build Support (Поддержка сборки для Windows)](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="fd9ea-122">После установки Unity 2020,3 приступайте к созданию проекта или обновлению существующего проекта с помощью подключаемого модуля Mixed Reality Опенкср:</span><span class="sxs-lookup"><span data-stu-id="fd9ea-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd9ea-123">Настройка проекта с помощью подключаемого модуля Опенкср</span><span class="sxs-lookup"><span data-stu-id="fd9ea-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="fd9ea-124">хотя мы рекомендуем использовать опенкср для всех новых проектов, Unity 2020,3 LTS также поддерживает [подключаемый модуль Windows XR](xr-project-setup.md?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="fd9ea-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="fd9ea-125">Этот подключаемый модуль полностью поддерживается, хотя он не будет принимать новые функции, такие как поддержка AR Foundation 4,0.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="fd9ea-126">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="fd9ea-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="fd9ea-127">Если необходимо использовать Unity 2019, можно использовать **unity 2019 LTS с устаревшими встроенными XR**.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="fd9ea-128">Чтобы приступить к работе с устаревшими встроенными XR в Unity 2019,4 LTS, щелкните здесь:</span><span class="sxs-lookup"><span data-stu-id="fd9ea-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd9ea-129">Настройка проекта с использованием устаревших встроенных XR</span><span class="sxs-lookup"><span data-stu-id="fd9ea-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="fd9ea-130">В Unity устарела устаревшая встроенная поддержка XR по отношению к Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="fd9ea-131">Хотя Unity 2019 предлагает новую инфраструктуру подключаемого модуля XR, корпорация Майкрософт сейчас не рекомендует этот путь в Unity 2019 из-за несовместимости пространственных привязок Azure с AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="fd9ea-132">В Unity 2020 поддержка пространственных привязок Azure поддерживается в инфраструктуре подключаемого модуля XR.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="fd9ea-133">если вы разрабатываете приложения для HoloLens (первое поколение), эти гарнитуры поддерживаются в Unity 2019 LTS с устаревшим встроенным XR для полного жизненного цикла Unity 2019 LTS через середину 2022.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="fd9ea-134">Unity 2021,2</span><span class="sxs-lookup"><span data-stu-id="fd9ea-134">Unity 2021.2</span></span>

<span data-ttu-id="fd9ea-135">Если вы пытаетесь выполнить ранние сборки **Unity 2021,2** , начните работу с [**подключаемым модулем Mixed Reality опенкср**](xr-project-setup.md?tabs=openxr).</span><span class="sxs-lookup"><span data-stu-id="fd9ea-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="fd9ea-136">подключаемый модуль опенкср является единственным путем для разработки смешанной реальности в Unity 2021,2 и более поздних версиях, так как окончательная версия Unity для поддержки подключаемого модуля Windows XR была Unity 2021,1.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="fd9ea-137">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="fd9ea-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="fd9ea-138">Unity 2018,4 LTS достиг конца окна поддержки годового Long-Term Unity и больше не получает обновления из Unity, хотя проекты будут по-прежнему выполняться.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="fd9ea-139">Если у вас есть проект Unity 2018, следует подумать о планировании миграции до Unity 2020,3 LTS и подключаемого модуля Опенкср Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>