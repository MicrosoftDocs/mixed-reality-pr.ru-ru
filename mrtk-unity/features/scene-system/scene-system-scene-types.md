---
title: Система сцен — типы сцен
description: Документация по различным типам сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144572"
---
# <a name="scene-types"></a><span data-ttu-id="ab821-104">Типы сцен</span><span class="sxs-lookup"><span data-stu-id="ab821-104">Scene types</span></span>

<span data-ttu-id="ab821-105">Сцены делятся на три типа, и у каждого типа есть другая функция.</span><span class="sxs-lookup"><span data-stu-id="ab821-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Система сцен в иерархии](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="ab821-107">Сцены содержимого</span><span class="sxs-lookup"><span data-stu-id="ab821-107">Content scenes</span></span>

<span data-ttu-id="ab821-108">Это сцены, с которыми вы работаете.</span><span class="sxs-lookup"><span data-stu-id="ab821-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="ab821-109">В них могут храниться любые виды содержимого, которые могут быть загружены или выгружены в любом сочетании.</span><span class="sxs-lookup"><span data-stu-id="ab821-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="ab821-110">Сцены содержимого включены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ab821-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="ab821-111">Все сцены, входящие в массив вашего профиля, `Content Scenes` могут быть загружены и выгружены службой.</span><span class="sxs-lookup"><span data-stu-id="ab821-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="ab821-112">Сцены диспетчера</span><span class="sxs-lookup"><span data-stu-id="ab821-112">Manager scenes</span></span>

<span data-ttu-id="ab821-113">Отдельная сцена с требуемым экземпляром Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="ab821-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="ab821-114">Эта сцена будет загружена первой при запуске и останется загруженной в течение времени существования приложения.</span><span class="sxs-lookup"><span data-stu-id="ab821-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="ab821-115">В сцене руководителя также могут размещаться другие объекты, которые никогда не должны уничтожаться.</span><span class="sxs-lookup"><span data-stu-id="ab821-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="ab821-116">Это предпочтительная альтернатива Донтдестройонлоад.</span><span class="sxs-lookup"><span data-stu-id="ab821-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="ab821-117">Чтобы включить эту функцию, проверьте `Use Manager Scene` профиль и перетащите объект сцены в `Manager Scene` поле.</span><span class="sxs-lookup"><span data-stu-id="ab821-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="ab821-118">Освещение сцен</span><span class="sxs-lookup"><span data-stu-id="ab821-118">Lighting scenes</span></span>

<span data-ttu-id="ab821-119">Набор сцен, в котором хранятся сведения о освещении и объекты освещения.</span><span class="sxs-lookup"><span data-stu-id="ab821-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="ab821-120">Одновременно можно загрузить только один из них, и их параметры можно смешивать во время загрузки для переходов плавного освещения.</span><span class="sxs-lookup"><span data-stu-id="ab821-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="ab821-121">Параметры освещения Unity — окружающий свет, скибоксес и т. д. могут быть непростыми в управлении при использовании аддитивной загрузки, поскольку они привязаны к отдельным сценам и переопределяют поведение не так просто.</span><span class="sxs-lookup"><span data-stu-id="ab821-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="ab821-122">На практике это может привести к путанице при создании ресурсов в условиях освещения, которые не получаются во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ab821-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Параметры освещения системы сцены](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="ab821-124">В системе сцены используются сцены освещения, чтобы обеспечить единообразие этих параметров независимо от того, какие сцены загружаются или активны, как в режиме редактирования, так и в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="ab821-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="ab821-125">Чтобы включить эту функцию, проверьте `Use Lighting Scene` профиль и заполните `Lighting Scenes` массив.</span><span class="sxs-lookup"><span data-stu-id="ab821-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="ab821-126">Параметры кэшированного освещения</span><span class="sxs-lookup"><span data-stu-id="ab821-126">Cached lighting settings</span></span>

<span data-ttu-id="ab821-127">В вашем профиле хранятся кэшированные копии параметров освещения, которые хранятся в фоновом освещении.</span><span class="sxs-lookup"><span data-stu-id="ab821-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="ab821-128">Если эти параметры изменяются в фоновом освещении, необходимо обновить кэш, чтобы обеспечить нормальную работу освещения в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="ab821-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="ab821-129">В профиле будет отображаться предупреждение о том, что параметры кэшированных параметров устарели.</span><span class="sxs-lookup"><span data-stu-id="ab821-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="ab821-130">При щелчке `Update Cached Lighting Settings` будет загружена каждая из сцен освещения, извлечены их параметры, а затем сохранены в своем профиле.</span><span class="sxs-lookup"><span data-stu-id="ab821-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Параметры кэшированного освещения в системе сцены](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="ab821-132">Реакция на событие редактора</span><span class="sxs-lookup"><span data-stu-id="ab821-132">Editor behavior</span></span>

<span data-ttu-id="ab821-133">Одним из преимуществ использования сцен освещения является знание того, что содержимое правильно освещено при редактировании.</span><span class="sxs-lookup"><span data-stu-id="ab821-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="ab821-134">Для этого служба сцены будет постоянно загружать сцены освещения, а параметры освещения сцены будут скопированы в текущую активную сцену.\*</span><span class="sxs-lookup"><span data-stu-id="ab821-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="ab821-135">Вы можете изменить, какая сцена освещения будет загружена, открыв [инспектор службы](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) в системе сцены.</span><span class="sxs-lookup"><span data-stu-id="ab821-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="ab821-136">В режиме редактирования можно мгновенно переходить между сценами освещения.</span><span class="sxs-lookup"><span data-stu-id="ab821-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="ab821-137">В режиме воспроизведения можно просматривать переходы.</span><span class="sxs-lookup"><span data-stu-id="ab821-137">In play mode, you can preview transitions.</span></span>

![Инспектор системы сцен](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="ab821-139">\**Примечание. обычно активная сцена определяет параметры освещения в редакторе. Однако мы решили не использовать эту функцию для применения параметров освещения, так как активная сцена также размещает вновь созданные объекты по умолчанию, а сцены освещения могут содержать только компоненты освещения. Вместо этого параметры сцены текущего освещения автоматически копируются в параметры активной сцены. Помните, что это приведет к тому, что параметры освещения сцены содержимого будут перезаписаны.*</span><span class="sxs-lookup"><span data-stu-id="ab821-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
