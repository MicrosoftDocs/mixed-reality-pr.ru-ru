---
title: Серия руководств по началу работы, часть 1 Общие сведения и цели
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 777203d0051c22b0f249db7d377ab08f92c089b7
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701591"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="e09f2-105">1. Общие сведения и цели</span><span class="sxs-lookup"><span data-stu-id="e09f2-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="e09f2-106">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="e09f2-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e09f2-107"><strong>Курс</strong></span><span class="sxs-lookup"><span data-stu-id="e09f2-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="e09f2-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e09f2-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e09f2-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e09f2-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="e09f2-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="e09f2-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="e09f2-111">✔️</span><span class="sxs-lookup"><span data-stu-id="e09f2-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e09f2-112">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="e09f2-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e09f2-113">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="e09f2-113">Prerequisites</span></span>

* <span data-ttu-id="e09f2-114">Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e09f2-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="e09f2-115">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="e09f2-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e09f2-116">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="e09f2-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="e09f2-117">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="e09f2-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e09f2-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="e09f2-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e09f2-119">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="e09f2-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="e09f2-120">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="e09f2-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="e09f2-121">Следующий урок. 2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="e09f2-121">Next lesson: 2. Initializing your project and first application</span></span>](../../../mrlearning-base-ch1.md)
