---
title: Разработка в Unity для виртуальной реальности
description: Приступите к созданию приложений смешанной реальности в Unity для иммерсивных гарнитур виртуальной реальности и Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, смешанная реальность, разработка, начало работы, новый проект, перенос, возможность, камера, имитация, эмуляция, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, что такое виртуальная реальность, что такое дополненная реальность, MRTK, Mixed Reality Toolkit, голосовой ввод, камера с определяемым местоположением, эмулятор, Azure, руководства
ms.openlocfilehash: edd75def71ad31a1d29a480d0b2a7f7ffbd8c037
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226433"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="f153e-104">Разработка в Unity для виртуальной реальности и Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f153e-104">Unity development for VR and Windows Mixed Reality</span></span>

![Баннер с логотипом Unity](../images/unity_logo_banner.png)

<span data-ttu-id="f153e-106">Если вы еще не работали с Unity, мы рекомендуем вам предварительно изучить [руководства](https://unity3d.com/learn/tutorials) для начинающих на платформе Unity Learn.</span><span class="sxs-lookup"><span data-stu-id="f153e-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="f153e-107">Также посетите [форумы по смешанной реальности Unity](https://forum.unity3d.com/forums/hololens.102/), чтобы присоединиться к онлайн-сообществу, создающему приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="f153e-108">Никогда не угадаешь, какие великолепные ресурсы или решения можно найти в Интернете.</span><span class="sxs-lookup"><span data-stu-id="f153e-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="f153e-109">Когда вы будете готовы начать работу с MRTK, перейдите к этапам разработки ниже.</span><span class="sxs-lookup"><span data-stu-id="f153e-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f153e-110">Ознакомьтесь с нашими **[руководствами по переносу](../porting-apps/porting-overview.md)** , если вы хотите использовать существующий проект Unity с иммерсивной гарнитурой Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f153e-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="f153e-111">Этапы разработки</span><span class="sxs-lookup"><span data-stu-id="f153e-111">Development checkpoints</span></span>

<span data-ttu-id="f153e-112">Используйте следующие контрольные точки, чтобы реализовать свои игры и приложения Unity в мире смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="f153e-113">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="f153e-113">1. Getting started</span></span>

<span data-ttu-id="f153e-114">Вам потребуется вручную настроить небольшой набор параметров Unity для разработки для Windows Mixed Reality и виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="f153e-115">Они делятся на две категории: параметры проекта и параметры сцены.</span><span class="sxs-lookup"><span data-stu-id="f153e-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="f153e-116">К концу этого раздела вы узнаете об инструментах и параметрах проекта для создания собственных приложений.</span><span class="sxs-lookup"><span data-stu-id="f153e-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="f153e-117">Контрольная точка</span><span class="sxs-lookup"><span data-stu-id="f153e-117">Checkpoint</span></span>  |  <span data-ttu-id="f153e-118">Результат</span><span class="sxs-lookup"><span data-stu-id="f153e-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="f153e-119">Установка последних средств</span><span class="sxs-lookup"><span data-stu-id="f153e-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="f153e-120">Скачивание и установка последней версии пакета Unity и настройка проекта для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="f153e-121">Настройка проекта для WMR</span><span class="sxs-lookup"><span data-stu-id="f153e-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="f153e-122">Узнайте, как создавать приложения, которые отрисовывают цифровое содержимое на голографических устройствах и устройствах виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="f153e-123">2. Основные компоненты</span><span class="sxs-lookup"><span data-stu-id="f153e-123">2. Core building blocks</span></span>

<span data-ttu-id="f153e-124">После запуска нового иммерсивного проекта вам потребуется изучить некоторые базовые строительные блоки для разработки иммерсивных приложений.</span><span class="sxs-lookup"><span data-stu-id="f153e-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="f153e-125">Все основные стандартные блоки для приложений смешанной реальности предоставляются так же, как и другие интерфейсы API Unity.</span><span class="sxs-lookup"><span data-stu-id="f153e-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="f153e-126">Скорее всего, вам потребуются только некоторые из них, но мы все равно рекомендуем заранее ознакомиться с их возможностями.</span><span class="sxs-lookup"><span data-stu-id="f153e-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="f153e-127">Изучив стандартные блоки, приведенные ниже, вы сможете использовать набор функций, которые можно интегрировать в проект виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="f153e-128">3. Дополнительные функции</span><span class="sxs-lookup"><span data-stu-id="f153e-128">3. Advanced features</span></span>

<span data-ttu-id="f153e-129">Другие ключевые функции, которые играют важную роль в иммерсивных приложениях, доступны через API Unity, не требуя установки дополнительных пакетов или настройки.</span><span class="sxs-lookup"><span data-stu-id="f153e-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="f153e-130">Изучив расширенные функции, предлагаемые Unity, вы сможете создавать более сложные и интересные приложения виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="f153e-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="f153e-131">Функция</span><span class="sxs-lookup"><span data-stu-id="f153e-131">Feature</span></span>  |  <span data-ttu-id="f153e-132">Возможности</span><span class="sxs-lookup"><span data-stu-id="f153e-132">Capabilities</span></span>  |
| --- | --- |
| <span data-ttu-id="f153e-133">[потеря слежения](tracking-loss-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="f153e-133">[Tracking loss](tracking-loss-in-unity.md)</span></span> | <span data-ttu-id="f153e-134">Обработка сценариев, в которых ваше устройство не может определить свое расположение в мировом пространстве приложения.</span><span class="sxs-lookup"><span data-stu-id="f153e-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="f153e-135">Ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f153e-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="f153e-136">Получение ввода из реального мира и приложений смешанной реальности в приложении.</span><span class="sxs-lookup"><span data-stu-id="f153e-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="f153e-137">4. Развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="f153e-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="f153e-138">После подготовки голографического проекта Unity к тестированию следующим шагом является экспорт и сборка решения Unity в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f153e-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="f153e-139">С помощью этого решения Visual Studio вы можете запустить приложение, используя физическое или имитированное устройство.</span><span class="sxs-lookup"><span data-stu-id="f153e-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="f153e-140">Изучив этот раздел, вы сможете развернуть приложение на любом устройстве или эмуляторе, соответствующем вашим потребностями в разработке.</span><span class="sxs-lookup"><span data-stu-id="f153e-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="f153e-141">Иммерсивная гарнитура Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f153e-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="f153e-142">Симулятор иммерсивной гарнитуры Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f153e-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="f153e-143">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="f153e-143">What's next?</span></span>

<span data-ttu-id="f153e-144">Разработчику всегда будет чем заняться, особенно при изучении нового инструмента или пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="f153e-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="f153e-145">В приведенных ниже разделах вы найдете информацию для более опытных разработчиков, а также полезные ресурсы, которые помогут вам, если у вас возникнут трудности.</span><span class="sxs-lookup"><span data-stu-id="f153e-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="f153e-146">Учтите, что эти темы и ресурсы не имеют определенного порядка, поэтому вы можете изучать их в любой последовательности.</span><span class="sxs-lookup"><span data-stu-id="f153e-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="f153e-147">Перенос</span><span class="sxs-lookup"><span data-stu-id="f153e-147">Porting</span></span>

<span data-ttu-id="f153e-148">Если вы хотите перенести существующие приложения, вам помогут приведенные ниже статьи:</span><span class="sxs-lookup"><span data-stu-id="f153e-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="f153e-149">Перенос приложений VR в Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f153e-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="f153e-150">Обновление приложений SteamVR для Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f153e-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="f153e-151">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="f153e-151">Additional resources</span></span>

<span data-ttu-id="f153e-152">Прежде чем приступать к разработке приложений для смешанной реальности, изучите приведенную ниже документацию.</span><span class="sxs-lookup"><span data-stu-id="f153e-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="f153e-153">Руководство для энтузиастов виртуальной реальности</span><span class="sxs-lookup"><span data-stu-id="f153e-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="f153e-154">Магазин ресурсов Unity</span><span class="sxs-lookup"><span data-stu-id="f153e-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="f153e-155">См. также статью</span><span class="sxs-lookup"><span data-stu-id="f153e-155">See also</span></span> 

* [<span data-ttu-id="f153e-156">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="f153e-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="f153e-157">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="f153e-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="f153e-158">Экспорт и разработка решения Visual Studio для Unity</span><span class="sxs-lookup"><span data-stu-id="f153e-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="f153e-159">Рекомендации по работе с Unity и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f153e-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
