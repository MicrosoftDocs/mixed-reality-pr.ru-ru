---
title: експериенцесеттингс
description: Документация по различным параметрам интерфейса для МРТК
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647894"
---
# <a name="experience-settings"></a><span data-ttu-id="bde6c-104">Параметры работы</span><span class="sxs-lookup"><span data-stu-id="bde6c-104">Experience Settings</span></span>

<span data-ttu-id="bde6c-105">Одной из сложностей создания пользовательского интерфейса для смешанной реальности является согласованность по различным интерфейсам.</span><span class="sxs-lookup"><span data-stu-id="bde6c-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="bde6c-106">С помощью МРТК можно задать `Target Experience Scale` и `Content Offset` для сцены, настроить следующие данные для правильной работы в целевой шкале.</span><span class="sxs-lookup"><span data-stu-id="bde6c-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="bde6c-107">Содержимое сцены смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="bde6c-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="bde6c-108">Система границ</span><span class="sxs-lookup"><span data-stu-id="bde6c-108">Boundary System</span></span>

  ![Параметры интерфейса в профиле конфигурации МРТК](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="bde6c-110">Целевая шкала производительности</span><span class="sxs-lookup"><span data-stu-id="bde6c-110">Target Experience Scale</span></span>

<span data-ttu-id="bde6c-111">**Целевая шкала производительности** определяет среду, для которой предназначен интерфейс.</span><span class="sxs-lookup"><span data-stu-id="bde6c-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="bde6c-112">Он может принимать следующие значения.</span><span class="sxs-lookup"><span data-stu-id="bde6c-112">It can take on the following values.</span></span>

* <span data-ttu-id="bde6c-113">*Ориентатиононли* — это опыт, который использует только ориентацию гарнитуры и обеспечивает согласованность по тяжести.</span><span class="sxs-lookup"><span data-stu-id="bde6c-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="bde6c-114">Источник системы координат находится на головном уровне.</span><span class="sxs-lookup"><span data-stu-id="bde6c-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="bde6c-115">Опыт работы, предназначенный для использования в *рабочее место.*</span><span class="sxs-lookup"><span data-stu-id="bde6c-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="bde6c-116">Источник системы координат находится на уровне этажа.</span><span class="sxs-lookup"><span data-stu-id="bde6c-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="bde6c-117"> Работа, предназначенная для стационарного использования.</span><span class="sxs-lookup"><span data-stu-id="bde6c-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="bde6c-118">Источник системы координат находится на уровне этажа.</span><span class="sxs-lookup"><span data-stu-id="bde6c-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="bde6c-119">*Комната* — это опыт, предназначенный для поддержки перемещения во всей комнате.</span><span class="sxs-lookup"><span data-stu-id="bde6c-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="bde6c-120">Источник системы координат находится на уровне этажа.</span><span class="sxs-lookup"><span data-stu-id="bde6c-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="bde6c-121">*Мир* — это опыт, предназначенный для использования и перемещения по физическому миру.</span><span class="sxs-lookup"><span data-stu-id="bde6c-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="bde6c-122">Источник системы координат находится на головном уровне.</span><span class="sxs-lookup"><span data-stu-id="bde6c-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="bde6c-123">Смещение содержимого</span><span class="sxs-lookup"><span data-stu-id="bde6c-123">Content Offset</span></span>

<span data-ttu-id="bde6c-124">Этот параметр задает высоту, превышающую пол, для смещения [содержимого сцены смешанной реальности](scene-content.md) , если для **типа выравнивания** задано **выравнивание с использованием шкалы производительности** .</span><span class="sxs-lookup"><span data-stu-id="bde6c-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>