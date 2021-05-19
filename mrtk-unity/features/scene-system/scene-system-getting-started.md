---
title: Система сцен — начало работы
description: Целевая страница для системы сцен с МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144305"
---
# <a name="scene-system-overview"></a><span data-ttu-id="c1b77-104">Обзор системы сцены</span><span class="sxs-lookup"><span data-stu-id="c1b77-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="c1b77-105">Когда следует использовать систему сцен</span><span class="sxs-lookup"><span data-stu-id="c1b77-105">When to use the scene system</span></span>

<span data-ttu-id="c1b77-106">Если проект состоит из одной сцены, то, скорее всего, такая система не нужна.</span><span class="sxs-lookup"><span data-stu-id="c1b77-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="c1b77-107">Это наиболее полезно, когда выполняется одно или несколько из следующих условий.</span><span class="sxs-lookup"><span data-stu-id="c1b77-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="c1b77-108">Проект имеет несколько сцен.</span><span class="sxs-lookup"><span data-stu-id="c1b77-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="c1b77-109">Вы используете загрузку одного сцены, но вам не нравится, как она уничтожает экземпляр Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="c1b77-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="c1b77-110">Вам нужен простой способ одновременной загрузки нескольких сцен для создания интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c1b77-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="c1b77-111">Вам нужен простой способ отслеживания выполняемых операций загрузки или простой способ управления активацией сцены для нескольких сцен, загружаемых одновременно.</span><span class="sxs-lookup"><span data-stu-id="c1b77-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="c1b77-112">Вы хотите, чтобы согласованность освещения и прогнозируемость выполнялись во всех сценах.</span><span class="sxs-lookup"><span data-stu-id="c1b77-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="c1b77-113">Ресурсы системы сцены</span><span class="sxs-lookup"><span data-stu-id="c1b77-113">Scene System Resources</span></span>

<span data-ttu-id="c1b77-114">По умолчанию в системе сцен используется пара объектов сцены (Дефаултманажерсцене и Дефаултлигхтинг сцены).</span><span class="sxs-lookup"><span data-stu-id="c1b77-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="c1b77-115">Если не удается найти ни один из этих сцен, в инспекторе системных профилей сцены появится сообщение.</span><span class="sxs-lookup"><span data-stu-id="c1b77-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Сообщение о ресурсах по умолчанию](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="c1b77-117">! Метим Если в проекте используются пользовательские сцены диспетчера и освещения, это сообщение можно спокойно проигнорировать.</span><span class="sxs-lookup"><span data-stu-id="c1b77-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="c1b77-118">В следующих разделах описано, как разрешить это сообщение, в зависимости от того, какой метод использовался для импорта набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c1b77-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="c1b77-119">Диспетчер пакетов Unity (УПМ)</span><span class="sxs-lookup"><span data-stu-id="c1b77-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="c1b77-120">В пакетах УПМ набора средств Mixed Reality в качестве примера упакованы системные ресурсы сцены.</span><span class="sxs-lookup"><span data-stu-id="c1b77-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="c1b77-121">Из-за неизменяемых пакетов УПМ Unity не может открыть необходимый файл сцены, если они не импортированы в проект явным образом.</span><span class="sxs-lookup"><span data-stu-id="c1b77-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="c1b77-122">Для импорта выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c1b77-122">To import use the following steps:</span></span>

- <span data-ttu-id="c1b77-123">Выбор   >  **диспетчера пакетов** окна</span><span class="sxs-lookup"><span data-stu-id="c1b77-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="c1b77-124">Выбор **набора средств для смешанной реальности Foundation**</span><span class="sxs-lookup"><span data-stu-id="c1b77-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="c1b77-125">Определение местоположения **системных ресурсов сцены** в разделе " **образцы** "</span><span class="sxs-lookup"><span data-stu-id="c1b77-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Импорт системных ресурсов сцены](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="c1b77-127">Выбор **импорта**</span><span class="sxs-lookup"><span data-stu-id="c1b77-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="c1b77-128">Файлы ресурсов (. пакет unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c1b77-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="c1b77-129">Если папка Сценесистемресаурцес была удалена или была отменена во время импорта, ее можно восстановить, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c1b77-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="c1b77-130">Выберите **активы**  >  **Импорт пакета**  >  **пользовательский пакет**</span><span class="sxs-lookup"><span data-stu-id="c1b77-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="c1b77-131">Откройте пакет **Microsoft. микседреалити. Toolkit. Foundation.**</span><span class="sxs-lookup"><span data-stu-id="c1b77-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="c1b77-132">Убедитесь, что выбраны **службы/сценесистем/сценесистемресаурцес** и все дочерние параметры.</span><span class="sxs-lookup"><span data-stu-id="c1b77-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Повторное импорт системных ресурсов сцены](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="c1b77-134">Выбор **импорта**</span><span class="sxs-lookup"><span data-stu-id="c1b77-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="c1b77-135">Использование системы сцен</span><span class="sxs-lookup"><span data-stu-id="c1b77-135">How to use the scene system</span></span>

- [<span data-ttu-id="c1b77-136">Типы сцен</span><span class="sxs-lookup"><span data-stu-id="c1b77-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="c1b77-137">Загрузка сцены содержимого</span><span class="sxs-lookup"><span data-stu-id="c1b77-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="c1b77-138">Мониторинг загрузки содержимого</span><span class="sxs-lookup"><span data-stu-id="c1b77-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="c1b77-139">Загрузка сцены освещения</span><span class="sxs-lookup"><span data-stu-id="c1b77-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="c1b77-140">Параметры редактора</span><span class="sxs-lookup"><span data-stu-id="c1b77-140">Editor settings</span></span>

<span data-ttu-id="c1b77-141">По умолчанию система сцен применяет несколько поведений в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="c1b77-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="c1b77-142">Если какое-либо из этих поведений найдется в рабочем состоянии, их можно отключить в разделе **Параметры редактора** в системном профиле сцены.</span><span class="sxs-lookup"><span data-stu-id="c1b77-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="c1b77-143">`Editor Manage Build Settings:` Если значение — true, служба автоматически обновит параметры сборки, гарантируя Добавление всех сцен диспетчера, освещения и содержимого.</span><span class="sxs-lookup"><span data-stu-id="c1b77-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="c1b77-144">Отключите этот параметр, если требуется полный контроль над параметрами сборки.</span><span class="sxs-lookup"><span data-stu-id="c1b77-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="c1b77-145">`Editor Enforce Scene Order:` Если значение — true, служба обеспечит сначала отображение сцены диспетчера в иерархии сцены, затем освещение, а затем содержимое.</span><span class="sxs-lookup"><span data-stu-id="c1b77-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="c1b77-146">Отключите этот параметр, если требуется полный контроль над иерархией сцены.</span><span class="sxs-lookup"><span data-stu-id="c1b77-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="c1b77-147">`Editor Manage Loaded Scenes:` Если значение — true, служба гарантирует, что диспетчер, содержимое и освещение будут загружаться всегда.</span><span class="sxs-lookup"><span data-stu-id="c1b77-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="c1b77-148">Отключите, если требуется полный контроль над тем, какие сцены загружаются в редакторе.</span><span class="sxs-lookup"><span data-stu-id="c1b77-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="c1b77-149">`Editor Enforce Lighting Scene Types:` Если задано значение true, служба гарантирует, что `PermittedLightingSceneComponentTypes` в сценах освещения будут разрешены только компоненты, связанные с освещением.</span><span class="sxs-lookup"><span data-stu-id="c1b77-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="c1b77-150">Отключите, если требуется полный контроль над содержимым сцен освещения.</span><span class="sxs-lookup"><span data-stu-id="c1b77-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Параметры редактора системных сцен](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
