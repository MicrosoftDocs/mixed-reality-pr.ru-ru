---
title: Окно миграции
description: Документация по переходу на обновление в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 8e03848097c313a518f638de591f692ab71f0985
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143870"
---
# <a name="migration-window"></a><span data-ttu-id="92f5c-104">Окно миграции</span><span class="sxs-lookup"><span data-stu-id="92f5c-104">Migration window</span></span>

<span data-ttu-id="92f5c-105">По мере изменения МРТК некоторые компоненты могут стать нерекомендуемыми, и замены будут введены.</span><span class="sxs-lookup"><span data-stu-id="92f5c-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="92f5c-106">Окно миграции — это средство, которое помогает пользователям автоматически переносить подмножество устаревших компонентов в новые замены.</span><span class="sxs-lookup"><span data-stu-id="92f5c-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Окно миграции](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="92f5c-108">Использование</span><span class="sxs-lookup"><span data-stu-id="92f5c-108">Usage</span></span>

<span data-ttu-id="92f5c-109">Чтобы открыть это окно, выберите средство  >  *переноса служебных программ* для набора средств для смешанной реальности  >  .</span><span class="sxs-lookup"><span data-stu-id="92f5c-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="92f5c-110">После открытия окна миграции можно включить вкладки навигации режима выбора, выбрав конкретную реализацию обработчика миграции для компонента.</span><span class="sxs-lookup"><span data-stu-id="92f5c-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Режимы выбора миграции](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="92f5c-112">Режим объекта</span><span class="sxs-lookup"><span data-stu-id="92f5c-112">Object mode</span></span>

<span data-ttu-id="92f5c-113">Выбор вкладки объекты позволяет полю объекта, где пользователь может перетаскивать любые игровые объекты из открытой сцены, или Prefabs из папки проекта для переноса.</span><span class="sxs-lookup"><span data-stu-id="92f5c-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="92f5c-114">При нажатии кнопки удалить *(-)* , отображаемой справа от указанного объекта, объект удаляется из списка выбора.</span><span class="sxs-lookup"><span data-stu-id="92f5c-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="92f5c-115">После того как все нужные объекты будут включены в список, нажатие кнопки *Миграция* применит изменения, необходимые выбранной реализации обработчика миграции, ко всем компонентам в выделенном фрагменте, которые соответствуют реализации.</span><span class="sxs-lookup"><span data-stu-id="92f5c-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Перенос выбора](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="92f5c-117">Режим сцены</span><span class="sxs-lookup"><span data-stu-id="92f5c-117">Scene mode</span></span>

<span data-ttu-id="92f5c-118">Позволяет пользователю перетаскивать ресурсы сцены, содержащие переносимые объекты.</span><span class="sxs-lookup"><span data-stu-id="92f5c-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Выбор сцен для миграции](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="92f5c-120">Режим проекта</span><span class="sxs-lookup"><span data-stu-id="92f5c-120">Project mode</span></span>

<span data-ttu-id="92f5c-121">Нажатие кнопки " *Миграция* " приведет к обновлению компонента, предназначенного для реализации обработчика миграции, для всех Prefabs и сцен в проекте.</span><span class="sxs-lookup"><span data-stu-id="92f5c-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Перенос завершенного проекта](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="92f5c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="92f5c-123">See also</span></span>

- [<span data-ttu-id="92f5c-124">Обновление с предыдущих версий</span><span class="sxs-lookup"><span data-stu-id="92f5c-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="92f5c-125">Выпуски Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="92f5c-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="92f5c-126">Стратегия МРТК</span><span class="sxs-lookup"><span data-stu-id="92f5c-126">MRTK roadmap</span></span>](../../roadmap.md)
