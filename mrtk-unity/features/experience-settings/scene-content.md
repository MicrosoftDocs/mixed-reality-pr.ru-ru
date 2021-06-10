---
title: сценеконтент
description: Документация по компоненту содержимого сцены смешанной реальности
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647916"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="a90e5-104">Содержимое сцены смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="a90e5-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="a90e5-105">При добавлении МРТК в сцену `MixedRealitySceneContent` создается gameobject.</span><span class="sxs-lookup"><span data-stu-id="a90e5-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="a90e5-106">Этот объект выступает в качестве выделенного места для размещения и создания экземпляра содержимого смешанной реальности, чтобы обеспечить его масштабирование в соответствии с множеством различных возможностей.</span><span class="sxs-lookup"><span data-stu-id="a90e5-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="a90e5-107">Gameobject имеет эквивалентное **микседреалитисценеконтентное** поведение, которое можно настроить с помощью параметра **типа выравнивания** .</span><span class="sxs-lookup"><span data-stu-id="a90e5-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="a90e5-108">Этот параметр может принимать следующие значения.</span><span class="sxs-lookup"><span data-stu-id="a90e5-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="a90e5-109">*Алигнвисекспериенцескале* — выровняйте содержимое по **целевому масштабу** и **смещению содержимого** , заданному в [параметрах интерфейса](experience-settings.md) профиля конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a90e5-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="a90e5-110">*Алигнвисхеадхеигхт* — выровняйте содержимое по оси y заголовка пользователя, который является расположением основной камеры.</span><span class="sxs-lookup"><span data-stu-id="a90e5-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Объект содержимого сцены смешанной реальности создан в редакторе](../images/experience-settings/MixedRealitySceneContent.png)