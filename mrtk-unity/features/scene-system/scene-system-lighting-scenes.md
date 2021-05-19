---
title: Система сцен — сцены освещения
description: Документация по освещению в сцене.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144410"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="3d86f-104">Операции освещения сцены</span><span class="sxs-lookup"><span data-stu-id="3d86f-104">Lighting scene operations</span></span>

<span data-ttu-id="3d86f-105">Сцена освещения по умолчанию, определенная в профиле, загружается при запуске.</span><span class="sxs-lookup"><span data-stu-id="3d86f-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="3d86f-106">Эта сцена освещения остается загруженной до `SetLightingScene` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="3d86f-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="3d86f-107">Переходы параметров освещения</span><span class="sxs-lookup"><span data-stu-id="3d86f-107">Lighting setting transitions</span></span>

<span data-ttu-id="3d86f-108">`transitionType` управляет стилем перехода к новой сцене освещения.</span><span class="sxs-lookup"><span data-stu-id="3d86f-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="3d86f-109">Доступны следующие стили:</span><span class="sxs-lookup"><span data-stu-id="3d86f-109">The available styles are:</span></span>

<span data-ttu-id="3d86f-110">Тип</span><span class="sxs-lookup"><span data-stu-id="3d86f-110">Type</span></span> | <span data-ttu-id="3d86f-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="3d86f-111">Description</span></span> | <span data-ttu-id="3d86f-112">Duration</span><span class="sxs-lookup"><span data-stu-id="3d86f-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="3d86f-113">None</span><span class="sxs-lookup"><span data-stu-id="3d86f-113">None</span></span> | <span data-ttu-id="3d86f-114">Предыдущая сцена освещения выгружена, будет загружена новая сцена освещения.</span><span class="sxs-lookup"><span data-stu-id="3d86f-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="3d86f-115">Нет перехода.</span><span class="sxs-lookup"><span data-stu-id="3d86f-115">No transition.</span></span> | <span data-ttu-id="3d86f-116">Не учитывается</span><span class="sxs-lookup"><span data-stu-id="3d86f-116">Ignored</span></span>
<span data-ttu-id="3d86f-117">фадетоблакк</span><span class="sxs-lookup"><span data-stu-id="3d86f-117">FadeToBlack</span></span> | <span data-ttu-id="3d86f-118">Предыдущая сцена освещения плавно уменьшается до черного цвета.</span><span class="sxs-lookup"><span data-stu-id="3d86f-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="3d86f-119">Загружается новая сцена освещения, затем она проявляется черным.</span><span class="sxs-lookup"><span data-stu-id="3d86f-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="3d86f-120">Полезно для плавного перехода между расположениями.</span><span class="sxs-lookup"><span data-stu-id="3d86f-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="3d86f-121">Используется</span><span class="sxs-lookup"><span data-stu-id="3d86f-121">Used</span></span>
<span data-ttu-id="3d86f-122">Плавное переход</span><span class="sxs-lookup"><span data-stu-id="3d86f-122">CrossFade</span></span> | <span data-ttu-id="3d86f-123">Предыдущая сцена освещения постепенно исчезает по мере появления новой сцены освещения.</span><span class="sxs-lookup"><span data-stu-id="3d86f-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="3d86f-124">Полезно для плавного перехода между настройками освещения в одном и том же расположении.</span><span class="sxs-lookup"><span data-stu-id="3d86f-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="3d86f-125">Используется</span><span class="sxs-lookup"><span data-stu-id="3d86f-125">Used</span></span>

<span data-ttu-id="3d86f-126">Обратите внимание, что некоторые параметры освещения не могут быть интерполяции во время переходов.</span><span class="sxs-lookup"><span data-stu-id="3d86f-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="3d86f-127">Если требуется плавное визуальное переход, эти параметры должны оставаться согласованными между сценой освещения.</span><span class="sxs-lookup"><span data-stu-id="3d86f-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="3d86f-128">Параметр</span><span class="sxs-lookup"><span data-stu-id="3d86f-128">Setting</span></span> | <span data-ttu-id="3d86f-129">Плавный переход Фадетоблакк</span><span class="sxs-lookup"><span data-stu-id="3d86f-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="3d86f-130">Плавный плавный переход</span><span class="sxs-lookup"><span data-stu-id="3d86f-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="3d86f-131">скибокс</span><span class="sxs-lookup"><span data-stu-id="3d86f-131">Skybox</span></span> | <span data-ttu-id="3d86f-132">нет</span><span class="sxs-lookup"><span data-stu-id="3d86f-132">No</span></span> | <span data-ttu-id="3d86f-133">нет</span><span class="sxs-lookup"><span data-stu-id="3d86f-133">No</span></span>
<span data-ttu-id="3d86f-134">Пользовательские отражения</span><span class="sxs-lookup"><span data-stu-id="3d86f-134">Custom Reflections</span></span> | <span data-ttu-id="3d86f-135">нет</span><span class="sxs-lookup"><span data-stu-id="3d86f-135">No</span></span> | <span data-ttu-id="3d86f-136">нет</span><span class="sxs-lookup"><span data-stu-id="3d86f-136">No</span></span>
<span data-ttu-id="3d86f-137">Тени в режиме реального времени Sun</span><span class="sxs-lookup"><span data-stu-id="3d86f-137">Sun light realtime shadows</span></span> | <span data-ttu-id="3d86f-138">Да</span><span class="sxs-lookup"><span data-stu-id="3d86f-138">Yes</span></span> | <span data-ttu-id="3d86f-139">нет</span><span class="sxs-lookup"><span data-stu-id="3d86f-139">No</span></span>
