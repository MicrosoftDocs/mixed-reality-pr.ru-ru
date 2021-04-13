---
title: Серия руководств по началу работы, часть 3 Настройка профилей MRTK
description: Из этого курса вы узнаете, как настроить профили Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание пространственного положения
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300459"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="d2371-105">3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="d2371-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="d2371-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="d2371-106">Overview</span></span>

<span data-ttu-id="d2371-107">Из этого руководства вы узнаете, как настраивать профили МRТК.</span><span class="sxs-lookup"><span data-stu-id="d2371-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="d2371-108"><a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">Профили MRTK</a> — это дерево вложенных профилей, которые включают сведения конфигурации для инициализации систем и функций MRTK.</span><span class="sxs-lookup"><span data-stu-id="d2371-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="d2371-109">Профиль верхнего уровня (профиль конфигурации) содержит вложенные профили для всех основных базовых систем.</span><span class="sxs-lookup"><span data-stu-id="d2371-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="d2371-110">Каждый вложенный профиль отвечает за настройку поведения соответствующей системы.</span><span class="sxs-lookup"><span data-stu-id="d2371-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="d2371-111">В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки.</span><span class="sxs-lookup"><span data-stu-id="d2371-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="d2371-112">Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.</span><span class="sxs-lookup"><span data-stu-id="d2371-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="d2371-113">Как вы узнали при развертывании своего проекта на HoloLens 2 при работе с [предыдущим руководством](mr-learning-base-02.md#congratulations), сетка <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">отслеживания пространственного положения</a> — это набор сеток, представляющих геометрию среды.</span><span class="sxs-lookup"><span data-stu-id="d2371-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="d2371-114">На начальных этапах разработки она помогает в работе, но обычно ее визуализацию отключают, чтобы она не отвлекала внимание и не снижала производительность.</span><span class="sxs-lookup"><span data-stu-id="d2371-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="d2371-115">Задачи</span><span class="sxs-lookup"><span data-stu-id="d2371-115">Objectives</span></span>

* <span data-ttu-id="d2371-116">Узнать,как настраивать профили MRTK.</span><span class="sxs-lookup"><span data-stu-id="d2371-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="d2371-117">Скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="d2371-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="d2371-118">Изменить параметр отображения отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="d2371-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="d2371-119">Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="d2371-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="d2371-120">Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d2371-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="d2371-121">Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="d2371-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="d2371-122">Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="d2371-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="d2371-123">Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="d2371-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="d2371-124">Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="d2371-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="d2371-125">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="d2371-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="d2371-126">Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="d2371-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="d2371-127">Существует несколько вложенных уровней профилей.</span><span class="sxs-lookup"><span data-stu-id="d2371-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="d2371-128">Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="d2371-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="d2371-129">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d2371-129">Congratulations</span></span>

<span data-ttu-id="d2371-130">В этом руководстве показано, как клонировать и настраивать профили MRTK и их параметры.</span><span class="sxs-lookup"><span data-stu-id="d2371-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2371-131">Следующее руководство: 4. Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="d2371-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)