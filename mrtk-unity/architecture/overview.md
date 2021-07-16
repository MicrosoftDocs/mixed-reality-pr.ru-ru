---
title: Обзор архитектуры
description: Обзор архитектуры МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, архитектура мртк,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281916"
---
# <a name="architecture-overview"></a><span data-ttu-id="006b0-104">Обзор архитектуры</span><span class="sxs-lookup"><span data-stu-id="006b0-104">Architecture overview</span></span>

<span data-ttu-id="006b0-105">Общие сведения о содержимом МРТК см. в статье об архитектуре, приведенной в этом документе, которые помогут вам понять следующее:</span><span class="sxs-lookup"><span data-stu-id="006b0-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="006b0-106">Большие фрагменты МРТК и их подключение</span><span class="sxs-lookup"><span data-stu-id="006b0-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="006b0-107">Основные понятия МРТК, которые могут отсутствовать в обычный Unity</span><span class="sxs-lookup"><span data-stu-id="006b0-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="006b0-108">Работа некоторых более крупных систем (например, входных данных)</span><span class="sxs-lookup"><span data-stu-id="006b0-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="006b0-109">Этот раздел не предназначен для изучения задач, а именно для структурирования таких задач и их причин.</span><span class="sxs-lookup"><span data-stu-id="006b0-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="006b0-110">Множество аудиторий, один набор инструментов</span><span class="sxs-lookup"><span data-stu-id="006b0-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="006b0-111">МРТК не имеет единой унифицированной аудитории.</span><span class="sxs-lookup"><span data-stu-id="006b0-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="006b0-112">Она написана для поддержки вариантов использования, начиная от первого интенсивной, до тех, кто создает сложные общие возможности для предприятия.</span><span class="sxs-lookup"><span data-stu-id="006b0-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="006b0-113">Некоторые код и API могут быть написаны, оптимизированные для более чем другого (т. е. Некоторые части МРТК кажутся более оптимизированными для «одной щелчка»), но важно отметить, что некоторые из них более важны для целей истории и перебора.</span><span class="sxs-lookup"><span data-stu-id="006b0-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="006b0-114">По мере развития МРТК создаваемые функции должны быть спроектированы для поддержки различных вариантов использования.</span><span class="sxs-lookup"><span data-stu-id="006b0-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="006b0-115">МРТК также имеет требования к корректному масштабированию в пределах VR и AR.</span><span class="sxs-lookup"><span data-stu-id="006b0-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="006b0-116">создавать приложения, которые корректно отменяют работу при развертывании на HoloLens 2 или HoloLens 1, должны быть простыми и создавать приложения, предназначенные для опенвр и вмр (и других платформ).</span><span class="sxs-lookup"><span data-stu-id="006b0-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="006b0-117">Хотя в то время как группа может сосредоточиться на определенной итерации на определенной системе или платформе, долгосрочная цель состоит в том, чтобы создать широкий спектр возможностей, когда люди создают смешанную реальность.</span><span class="sxs-lookup"><span data-stu-id="006b0-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="006b0-118">Детализация высокого уровня</span><span class="sxs-lookup"><span data-stu-id="006b0-118">High level breakdown</span></span>

<span data-ttu-id="006b0-119">МРТК — это как набор средств для быстрого выполнения смешанной реальности (MR), так и платформа приложений с мнениями о собственной среде исполнения, то, как она должна быть расширена и как она должна быть настроена.</span><span class="sxs-lookup"><span data-stu-id="006b0-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="006b0-120">На высоком уровне МРТК можно разделить следующими способами:</span><span class="sxs-lookup"><span data-stu-id="006b0-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Схема обзора архитектуры](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="006b0-122">МРТК также содержит еще один набор служебных программ-контейнеров, которые не зависят от остальной части МРТК (Вот некоторые из них: средства сборки, поиск решения, звуковые факторы, сглаживание, служебные программы и модуль подготовки графики).</span><span class="sxs-lookup"><span data-stu-id="006b0-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="006b0-123">Оставшаяся часть документации по архитектуре будет создаваться постепенно, начиная от платформы и среды выполнения и до более интересных и сложных систем, таких как входные данные.</span><span class="sxs-lookup"><span data-stu-id="006b0-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="006b0-124">Чтобы продолжить обзор архитектуры, см. содержание оглавления.</span><span class="sxs-lookup"><span data-stu-id="006b0-124">Please see the table of contents to continue with the architectural overview.</span></span>
