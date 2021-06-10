---
title: Хотская точка телепортируйтесь
description: Документация по компоненту HotSpot для телепортируйтесь в МРТК
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, система телепортируйтесь, хотная точка телепортируйтесь
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647043"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="58a62-104">Хотская точка телепортируйтесь</span><span class="sxs-lookup"><span data-stu-id="58a62-104">Teleport Hotspot</span></span>

<span data-ttu-id="58a62-105">Хот-спот телепортируйтесь — это компонент, который можно добавить в gameobject, чтобы обеспечить пользователю определенную позицию и ориентацию при телепортироваться к этому расположению.</span><span class="sxs-lookup"><span data-stu-id="58a62-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="58a62-106">Использование</span><span class="sxs-lookup"><span data-stu-id="58a62-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="58a62-107">Создание хот-спота телепортируйтесь</span><span class="sxs-lookup"><span data-stu-id="58a62-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="58a62-108">Чтобы создать хот-споту телепортируйтесь, добавьте компонент Телепорсотспот в объект, который также содержит компонент для создания и установки.</span><span class="sxs-lookup"><span data-stu-id="58a62-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Компонент "Хот Hotspot" телепортируйтесь](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="58a62-110">Теперь индикатор указателя телепортируйтесь изменит цвет при наведении на Телепорсотспот.</span><span class="sxs-lookup"><span data-stu-id="58a62-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="58a62-111">Когда действие телепортируйтесь будет выполнено над активной областью, пользователь будет телепортируйтесь в центр Телепорсотспот.</span><span class="sxs-lookup"><span data-stu-id="58a62-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="58a62-112">Если флаг переопределений ориентации установлен, ориентация пользователя будет совпадать с ориентацией на хот-споте телепортируйтесь.</span><span class="sxs-lookup"><span data-stu-id="58a62-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Пример хот HotSpot для телепортируйтесь](../images/teleport/TeleportHotspotExample.gif)
