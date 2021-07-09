---
title: Настройка проекта Unreal
description: Узнайте, как настроить проект с использованием последней версии Unreal Engine и средства Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, смешанная реальность, разработка, функции, новый проект, эмулятор, документация, руководства, голограммы, разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394616"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="ec95c-104">Настройка проекта Unreal</span><span class="sxs-lookup"><span data-stu-id="ec95c-104">Setting up your Unreal project</span></span>

<span data-ttu-id="ec95c-105">Мы рекомендуем установить [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) или более поздней версии, чтобы воспользоваться всеми преимуществами встроенной поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ec95c-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="ec95c-106">Перейдите на вкладку **Library** (Библиотека) в Epic Games Launcher. Щелкните стрелку раскрывающегося списка рядом с полем **Launch** (Запуск) и выберите **Options** (Параметры).</span><span class="sxs-lookup"><span data-stu-id="ec95c-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="ec95c-107">В разделе **Target Platforms** (Целевые платформы) выберите элемент **HoloLens 2** и щелкните команду **Apply** (Применить).</span><span class="sxs-lookup"><span data-stu-id="ec95c-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="ec95c-108">![Параметр установки Unreal для HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="ec95c-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="ec95c-109">Импорт набора средств для смешанной реальности для Unreal</span><span class="sxs-lookup"><span data-stu-id="ec95c-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="ec95c-111">Набор средств для смешанной реальности (MRTK) — это кроссплатформенный пакет SDK с открытым кодом для приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="ec95c-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="ec95c-112">MRTK предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="ec95c-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ec95c-113">Набор используется для ускорения разработки приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ec95c-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="ec95c-114">Для выполнения установки мы рекомендуем изучить [раздел по началу работы](unreal-development-overview.md#1-getting-started) нашего [обзора разработки для Unreal](unreal-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec95c-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="ec95c-115">Если вы уже работаете с этим обзором, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](tutorials/unreal-uxt-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="ec95c-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="ec95c-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Изображение с логотипом Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="ec95c-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="ec95c-117">**Набор средств для смешанной реальности — Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="ec95c-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="ec95c-118">Если вы не хотите использовать MRTK для Unreal, вам придется самостоятельно написать скрипты для всех взаимодействий и моделей поведения.</span><span class="sxs-lookup"><span data-stu-id="ec95c-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>