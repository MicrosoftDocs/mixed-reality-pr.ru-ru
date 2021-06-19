---
title: Выбор конвейера разработчика
description: Оставайтесь в курсе последних рекомендаций по конвейерам разработки Unity для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394558"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="6b304-104">Выбор конвейера разработчика</span><span class="sxs-lookup"><span data-stu-id="6b304-104">Choosing your developer pipeline</span></span>

![Баннер с логотипом Unity](../images/unity_logo_banner.png)<br>

<span data-ttu-id="6b304-106">В настоящее время мы **рекомендуем установить Unity 2019,4 LTS и использовать устаревшие встроенные XR** для разработки смешанной реальности. Кроме того, вы можете создавать приложения с другими конфигурациями Unity.</span><span class="sxs-lookup"><span data-stu-id="6b304-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="6b304-107">Набор средств для смешанной реальности (рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="6b304-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="6b304-108">Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 — это набор средств Mixed Reality...</span><span class="sxs-lookup"><span data-stu-id="6b304-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="6b304-109">Установка средства "функция смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="6b304-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="6b304-110">Средство [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) предоставляет новый способ для обнаружения и добавления пакетов функций смешанной реальности в проекты Unity.</span><span class="sxs-lookup"><span data-stu-id="6b304-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="6b304-111">Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.</span><span class="sxs-lookup"><span data-stu-id="6b304-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="6b304-112">Когда вы подтвердите список нужных пакетов, средство Mixed Reality Feature Tool скачает их в выбранный вами проект.</span><span class="sxs-lookup"><span data-stu-id="6b304-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6b304-113">Импорт набора средств Mixed Reality для Unity</span><span class="sxs-lookup"><span data-stu-id="6b304-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="6b304-115">[Набор средств для смешанной реальности](mrtk-getting-started.md) (MRTK) — это кросс-платформенный пакет разработки с открытым кодом для приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="6b304-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="6b304-116">Установите пакет Mixed Reality Toolkit, следуя [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md#system-requirements), и выберите пакет **Mixed Reality Toolkit Foundation**.</span><span class="sxs-lookup"><span data-stu-id="6b304-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="6b304-117">Мы рекомендуем изучить раздел по началу работы, следуя нашим курируемым этапам разработки для[HoloLens](unity-development-overview.md#1-getting-started) или [виртуальной реальности](unity-development-wmr-overview.md#1-getting-started).</span><span class="sxs-lookup"><span data-stu-id="6b304-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="6b304-118">Если вы уже работаете с этими этапами, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](tutorials/mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="6b304-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b304-119">Обратите внимание, что инструкции по установке приведены для последнего стабильного сочетания выпусков MRTK и Unity — **MRTK 2.6.1** и **Unity 2019.4 LTS**.</span><span class="sxs-lookup"><span data-stu-id="6b304-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="6b304-120">Если вы не хотите использовать MRTK для Unity, вам придется [самостоятельно написать скрипты для всех взаимодействий и моделей поведения](configure-unity-project.md).</span><span class="sxs-lookup"><span data-stu-id="6b304-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6b304-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Баннер Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="6b304-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="6b304-122">**Набор средств для смешанной реальности — Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="6b304-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="6b304-123">Вручную</span><span class="sxs-lookup"><span data-stu-id="6b304-123">Manual</span></span> 

<span data-ttu-id="6b304-124">Подлежит уточнению...</span><span class="sxs-lookup"><span data-stu-id="6b304-124">TBD...</span></span>