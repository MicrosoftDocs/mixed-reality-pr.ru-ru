---
title: Знакомство с MRTK для Unreal
description: Сведения, позволяющие новым разработчикам решений смешанной реальности начать работу с набором Mixed Reality Toolkit для Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, тестирование, Mixed Reality Toolkit, MRTK версии 2, MRTK, инструменты, пакет SDK, HoloLens, HoloLens 2, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, кросс-платформенность
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584833"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="64a90-104">Знакомство с MRTK для Unreal</span><span class="sxs-lookup"><span data-stu-id="64a90-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="64a90-106">Что такое набор средств для смешанной реальности (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="64a90-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="64a90-107">MRTK — это превосходный набор инструментов с открытым кодом, ведущий свою историю еще с момента выпуска HoloLens.</span><span class="sxs-lookup"><span data-stu-id="64a90-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="64a90-108">Своей широкой функциональностью он обязан упорной работе сообщества разработчиков.</span><span class="sxs-lookup"><span data-stu-id="64a90-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="64a90-109">Mixed Reality Toolkit для Unreal (MRTK-Unreal) представляет собой набор таких компонентов, как подключаемые модули, примеры и документы, созданных для помощи в разработке приложений смешанной реальности с использованием Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="64a90-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="64a90-110">В настоящее время этот набор средств включает следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="64a90-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="64a90-111">[UX Tools для Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) — предоставляет код, схемы и примеры для реализации функций взаимодействия с пользователем в приложениях Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="64a90-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="64a90-112">[Graphics Tools для Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal) — помогают улучшить графику для приложений смешанной реальности с минимальным влиянием на производительность.</span><span class="sxs-lookup"><span data-stu-id="64a90-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="64a90-113">Изучите [документацию по MRTK на GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) и воспользуйтесь руководствами по установке для [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) и [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="64a90-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="64a90-114">Модульность</span><span class="sxs-lookup"><span data-stu-id="64a90-114">Modular</span></span>

<span data-ttu-id="64a90-115">MRTK для Unreal является модульным, поэтому нет необходимости добавлять его в проект целиком.</span><span class="sxs-lookup"><span data-stu-id="64a90-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="64a90-116">Вы можете выбрать и установить только необходимые подключаемые модули, а позднее добавлять или удалять их по мере надобности.</span><span class="sxs-lookup"><span data-stu-id="64a90-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="64a90-117">Такой подход помогает поддерживать небольшой объем проекта и упрощает управление им.</span><span class="sxs-lookup"><span data-stu-id="64a90-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="64a90-118">Высокая производительность</span><span class="sxs-lookup"><span data-stu-id="64a90-118">Performant</span></span>

<span data-ttu-id="64a90-119">Помня об ограничениях мобильных платформ, при создании MRTK Unreal мы ориентировались на производительность.</span><span class="sxs-lookup"><span data-stu-id="64a90-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="64a90-120">Это очень важный фактор, и мы стремились сделать инструменты максимально полезными.</span><span class="sxs-lookup"><span data-stu-id="64a90-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="64a90-121">См. также статью</span><span class="sxs-lookup"><span data-stu-id="64a90-121">See also</span></span>

* [<span data-ttu-id="64a90-122">Установка средств</span><span class="sxs-lookup"><span data-stu-id="64a90-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="64a90-123">Разработка с помощью MRTK для Unreal</span><span class="sxs-lookup"><span data-stu-id="64a90-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="64a90-124">Руководство по установке UX Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="64a90-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="64a90-125">Домашняя страница документации по UX Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="64a90-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="64a90-126">Руководство по установке Graphics Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="64a90-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="64a90-127">Домашняя страница документации по Graphics Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="64a90-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)