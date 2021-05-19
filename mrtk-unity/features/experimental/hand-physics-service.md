---
title: Служба расширения Физикы вручную
description: Описание. службы расширения Физикы.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143437"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="6c2d7-104">Службы расширения физикы вручную</span><span class="sxs-lookup"><span data-stu-id="6c2d7-104">Hand physics extension services</span></span>

<span data-ttu-id="6c2d7-105">Служба «рука» (физика) позволяет реализовать события конфликтов с жестким текстом и взаимодействия с сформулированными руки.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="6c2d7-106">Приступая к работе со службой расширения физикы нал.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="6c2d7-107">Добавьте службу вручную в список служб расширений и используйте профиль по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="6c2d7-108">После включения для получения событий конфликта от всех 10 цифр используйте свойство Палмс любого из них.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6c2d7-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6c2d7-109">Prerequisites</span></span>

- <span data-ttu-id="6c2d7-110">Включена служба расширений</span><span class="sxs-lookup"><span data-stu-id="6c2d7-110">Enabled the extension service</span></span>
- <span data-ttu-id="6c2d7-111">Назначьте соответствующую prefabу для соединения пальца/Palm.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="6c2d7-112">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="6c2d7-112">Recommendations</span></span>

<span data-ttu-id="6c2d7-113">Хотя служба по умолчанию имеет уровень "по умолчанию", рекомендуется использовать отдельный слой для объектов Хандфисикс.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="6c2d7-114">В противном случае могут возникнуть нежелательные конфликты и/или неточные райкастс.</span><span class="sxs-lookup"><span data-stu-id="6c2d7-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
