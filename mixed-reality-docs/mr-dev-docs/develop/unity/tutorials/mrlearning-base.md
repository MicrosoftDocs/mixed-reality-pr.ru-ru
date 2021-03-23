---
title: Обзор и цели учебника
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98581166"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="d75e1-104">1. Общие сведения и цели</span><span class="sxs-lookup"><span data-stu-id="d75e1-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="d75e1-105">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="d75e1-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d75e1-106"><strong>Курс</strong></span><span class="sxs-lookup"><span data-stu-id="d75e1-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="d75e1-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d75e1-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d75e1-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="d75e1-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="d75e1-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="d75e1-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="d75e1-110">✔️</span><span class="sxs-lookup"><span data-stu-id="d75e1-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d75e1-111">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="d75e1-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d75e1-112">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="d75e1-112">Prerequisites</span></span>

* <span data-ttu-id="d75e1-113">Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d75e1-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="d75e1-114">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="d75e1-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d75e1-115">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="d75e1-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="d75e1-116">Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d75e1-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d75e1-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="d75e1-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d75e1-118">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="d75e1-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="d75e1-119">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="d75e1-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="d75e1-120">Следующий урок. 2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="d75e1-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)