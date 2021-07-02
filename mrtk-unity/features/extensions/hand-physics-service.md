---
title: Служба вручную
description: Документация по использованию службы расширения физикы вручную в МРТК
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176250"
---
# <a name="hand-physics-service"></a><span data-ttu-id="9584f-104">Служба вручную</span><span class="sxs-lookup"><span data-stu-id="9584f-104">Hand physics service</span></span>

![Служба расширения Физикы вручную](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="9584f-106">Служба «рука» (физика) позволяет реализовать события конфликтов с жестким текстом и взаимодействия с сформулированными руки.</span><span class="sxs-lookup"><span data-stu-id="9584f-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="9584f-107">Включение расширения</span><span class="sxs-lookup"><span data-stu-id="9584f-107">Enabling the extension</span></span>

<span data-ttu-id="9584f-108">Чтобы включить расширение, откройте профиль Регистередсервицепровидер.</span><span class="sxs-lookup"><span data-stu-id="9584f-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="9584f-109">Нажмите `Register a new Service Provider` , чтобы добавить новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9584f-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="9584f-110">В поле Тип компонента выберите Хандфисикссервице.</span><span class="sxs-lookup"><span data-stu-id="9584f-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="9584f-111">В поле профиль конфигурации выберите профиль по умолчанию, который входит в состав расширения.</span><span class="sxs-lookup"><span data-stu-id="9584f-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="9584f-112">Параметры профиля</span><span class="sxs-lookup"><span data-stu-id="9584f-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="9584f-113">Слой физикы руки</span><span class="sxs-lookup"><span data-stu-id="9584f-113">Hand physics layer</span></span>

<span data-ttu-id="9584f-114">Управляет слоем, к которому будут обращаться экземпляры, созданные вручную.</span><span class="sxs-lookup"><span data-stu-id="9584f-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="9584f-115">Хотя служба по умолчанию имеет уровень "по умолчанию" (0), рекомендуется использовать отдельный слой для объектов вручную.</span><span class="sxs-lookup"><span data-stu-id="9584f-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="9584f-116">В противном случае могут возникнуть нежелательные конфликты и/или неточные райкастс.</span><span class="sxs-lookup"><span data-stu-id="9584f-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="9584f-117">Совет по отпечатку пальца prefab</span><span class="sxs-lookup"><span data-stu-id="9584f-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="9584f-118">Определяет, к какому экземпляру prefab создавать экземпляры.</span><span class="sxs-lookup"><span data-stu-id="9584f-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="9584f-119">Чтобы служба работала должным образом, для prefab требуется:</span><span class="sxs-lookup"><span data-stu-id="9584f-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="9584f-120">Компонент RigidBody с включенной поддержкой onкинематики</span><span class="sxs-lookup"><span data-stu-id="9584f-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="9584f-121">Конфликт</span><span class="sxs-lookup"><span data-stu-id="9584f-121">A collider</span></span>
- <span data-ttu-id="9584f-122">Компонент `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="9584f-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="9584f-123">Использовать текст для ручной кинематики</span><span class="sxs-lookup"><span data-stu-id="9584f-123">Use palm kinematic body</span></span>

<span data-ttu-id="9584f-124">Определяет, будет ли служба пытаться создать экземпляр prefab на совместных соединениях Palm.</span><span class="sxs-lookup"><span data-stu-id="9584f-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="9584f-125">Palm, prefab Body</span><span class="sxs-lookup"><span data-stu-id="9584f-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="9584f-126">Если `UsePalmKinematicBody` параметр включен, это prefab будет создавать экземпляр.</span><span class="sxs-lookup"><span data-stu-id="9584f-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="9584f-127">Как `FingerTipKinematicBodyPrefab` и для этого prefab, требуется:</span><span class="sxs-lookup"><span data-stu-id="9584f-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="9584f-128">Компонент RigidBody с включенной поддержкой onкинематики</span><span class="sxs-lookup"><span data-stu-id="9584f-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="9584f-129">Конфликт</span><span class="sxs-lookup"><span data-stu-id="9584f-129">A collider</span></span>
- <span data-ttu-id="9584f-130">Компонент `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="9584f-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="9584f-131">Использование службы</span><span class="sxs-lookup"><span data-stu-id="9584f-131">How to use the service</span></span>

<span data-ttu-id="9584f-132">После включения приложения используйте любое `IsTrigger` свойство, чтобы получить события конфликта от всех 10 цифр (и Палмс, если они включены).</span><span class="sxs-lookup"><span data-stu-id="9584f-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
