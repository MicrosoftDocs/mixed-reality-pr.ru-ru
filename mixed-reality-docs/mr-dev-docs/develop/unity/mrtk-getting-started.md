---
title: Знакомство с MRTK для Unity
description: Начните работу с кросс-платформенными функциями Mixed Reality Toolkit для разработчиков смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, тестирование, Mixed Reality Toolkit, MRTK версии 2, MRTK, инструменты, пакет SDK, HoloLens, HoloLens 2, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, кросс-платформенность
ms.openlocfilehash: 69b7bbf073e278c17be42241e8c6e3a47be60ee9
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300449"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="232f3-104">Знакомство с MRTK для Unity</span><span class="sxs-lookup"><span data-stu-id="232f3-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="232f3-106">Что такое набор средств для смешанной реальности (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="232f3-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="232f3-107">MRTK — это превосходный набор инструментов с открытым кодом, ведущий свою историю еще с момента выпуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="232f3-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="232f3-108">Своей широкой функциональностью он обязан упорной работе сообщества разработчиков.</span><span class="sxs-lookup"><span data-stu-id="232f3-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="232f3-109">Последние 3 года мы собирали отзывы сообщества и создали MRTK версии 2, реализовав основные ваши пожелания.</span><span class="sxs-lookup"><span data-stu-id="232f3-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="232f3-110">MRTK для Unity — это кросс-платформенный пакет SDK с открытым кодом для приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="232f3-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="232f3-111">Самый простой способ установить набор средств — с помощью нашего нового приложения Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="232f3-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="232f3-112">Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **Mixed Reality Toolkit Foundation** в категории Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="232f3-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

<span data-ttu-id="232f3-113">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="232f3-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="232f3-114">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="232f3-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="232f3-115">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="232f3-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [<span data-ttu-id="232f3-116">Ознакомьтесь с нашими руководствами по МРТК</span><span class="sxs-lookup"><span data-stu-id="232f3-116">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="232f3-117">Дополнительные сведения о функциях см. в [документации по MRTK ](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="232f3-117">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="232f3-118">Новые возможности в MRTK версии 2</span><span class="sxs-lookup"><span data-stu-id="232f3-118">New with MRTK v2</span></span>

<span data-ttu-id="232f3-119">Мы хотим испытать свою приверженность к этим инструментам платформы.</span><span class="sxs-lookup"><span data-stu-id="232f3-119">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="232f3-120">Более того, мы использовали MRTK версии 2 для внутренней разработки, в том числе мастера настройки во время первого запуска (OOBE) и нашего приложения с советами по использованию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="232f3-120">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="232f3-121">Вы можете также увидеть новые возможности HoloLens 2, сначала предоставленные посредством MRTK, так как мы считаем, что это лучший способ разработки на нашей платформе.</span><span class="sxs-lookup"><span data-stu-id="232f3-121">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span>

### <a name="modular"></a><span data-ttu-id="232f3-122">Модульность</span><span class="sxs-lookup"><span data-stu-id="232f3-122">Modular</span></span>

<span data-ttu-id="232f3-123">Этот набор инструментов является модульным, поэтому нет необходимости добавлять его в свой проект целиком.</span><span class="sxs-lookup"><span data-stu-id="232f3-123">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="232f3-124">Это дает ряд преимуществ.</span><span class="sxs-lookup"><span data-stu-id="232f3-124">There are actually a few benefits to this.</span></span>  <span data-ttu-id="232f3-125">Проект будет меньшего размера и им будет проще управлять.</span><span class="sxs-lookup"><span data-stu-id="232f3-125">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="232f3-126">Кроме того, так как набор основан на поддерживающих сценарии объектах и управляется интерфейсом, можно также заменить его компоненты собственными, чтобы обеспечить поддержку других служб, систем и платформ.</span><span class="sxs-lookup"><span data-stu-id="232f3-126">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="232f3-127">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="232f3-127">Cross-platform</span></span>

<span data-ttu-id="232f3-128">Говоря о других платформах, этот набор является кросс-платформенным.</span><span class="sxs-lookup"><span data-stu-id="232f3-128">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="232f3-129">И хотя это и не означает, что поддерживается любая платформа, мы гарантируем, что код набора инструментов будет работать и дальше при изменении целевой платформы для сборки.</span><span class="sxs-lookup"><span data-stu-id="232f3-129">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="232f3-130">Надежность и расширяемость модульной структуры обеспечивает возможность поддержки приложениями нескольких платформ, таких как ARCore, ARKit и OpenVR.</span><span class="sxs-lookup"><span data-stu-id="232f3-130">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="232f3-131">Высокая производительность</span><span class="sxs-lookup"><span data-stu-id="232f3-131">Performant</span></span>

<span data-ttu-id="232f3-132">Добавляя возможности для мобильных платформ, мы помнили о производительности.</span><span class="sxs-lookup"><span data-stu-id="232f3-132">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="232f3-133">Это очень важно, и мы хотели убедиться, что инструменты будут работать надежно.</span><span class="sxs-lookup"><span data-stu-id="232f3-133">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="232f3-134">См. также статью</span><span class="sxs-lookup"><span data-stu-id="232f3-134">See also</span></span>

* [<span data-ttu-id="232f3-135">Установка средств</span><span class="sxs-lookup"><span data-stu-id="232f3-135">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="232f3-136">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="232f3-136">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="232f3-137">Разработка с помощью MRTK для Unity</span><span class="sxs-lookup"><span data-stu-id="232f3-137">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="232f3-138">MRTK: домашняя страница документации</span><span class="sxs-lookup"><span data-stu-id="232f3-138">MRTK - Documentation home</span></span>](/windows/mixed-reality/mrtk-unity/)
* [<span data-ttu-id="232f3-139">Перенос из HoloToolkit/MRTK в MRTK версии 2</span><span class="sxs-lookup"><span data-stu-id="232f3-139">Porting from HoloToolkit/MRTK to MRTK version 2</span></span>](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
