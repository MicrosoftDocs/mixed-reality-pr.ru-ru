---
title: Использование подключаемого модуля Смешанной реальности OpenXR
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547051"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="ce87d-104">Использование подключаемого модуля Смешанной реальности OpenXR</span><span class="sxs-lookup"><span data-stu-id="ce87d-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="ce87d-105">Для разработчиков, нацеленных на Unity 2020 для создания приложений HoloLens 2 или Mixed Reality, можно использовать подключаемый модуль Опенкср вместо подключаемого модуля Виндовскср для повышения совместимости между платформами.</span><span class="sxs-lookup"><span data-stu-id="ce87d-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="ce87d-106">Подключаемый модуль Опенкср для смешанной реальности хорошо работает с последним [набором средств для управления смешанной реальности 2,7](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="ce87d-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce87d-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="ce87d-107">Prerequisites</span></span>

* <span data-ttu-id="ce87d-108">Новейшая версия Unity 2020,3 LTS (рекомендуется 2020.3.8 F1 или выше).</span><span class="sxs-lookup"><span data-stu-id="ce87d-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="ce87d-109">Последний подключаемый модуль Unity Опенкср (рекомендуется 1,2 или более поздней версии)</span><span class="sxs-lookup"><span data-stu-id="ce87d-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="ce87d-110">Новейшие [средства для разработки HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="ce87d-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ce87d-111">Последняя МРТК (необязательно) (рекомендуется версия 2,7 или более поздняя).</span><span class="sxs-lookup"><span data-stu-id="ce87d-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="ce87d-112">Последний подключаемый модуль Опенкср в смешанной реальности (рекомендуется использовать версию 1.0.0-Preview. 1 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="ce87d-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![Снимок экрана открытого примера XR Unity Basic, работающего на HoloLens](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="ce87d-114">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="ce87d-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ce87d-115">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="ce87d-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="ce87d-116">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="ce87d-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="ce87d-117">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="ce87d-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ce87d-118">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ce87d-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="ce87d-119">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="ce87d-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce87d-120">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="ce87d-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="ce87d-121">Дополнительные сведения о функциях см. в [документации по MRTK ](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="ce87d-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="ce87d-122">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="ce87d-122">Manual setup without MRTK</span></span>

<span data-ttu-id="ce87d-123">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="ce87d-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="ce87d-124">Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":</span><span class="sxs-lookup"><span data-stu-id="ce87d-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="ce87d-126">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="ce87d-126">Setting your build target</span></span>

<span data-ttu-id="ce87d-127">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="ce87d-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="ce87d-129">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="ce87d-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="ce87d-130">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="ce87d-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="ce87d-131">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="ce87d-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="ce87d-132">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="ce87d-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="ce87d-133">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ce87d-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="ce87d-134">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="ce87d-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="ce87d-135">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="ce87d-135">Set **UWP SDK** to **Latest installed**</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ce87d-137">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="ce87d-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ce87d-138">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ce87d-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ce87d-139">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="ce87d-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ce87d-140">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="ce87d-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ce87d-141">Установите флажки **инициализировать XR при запуске** и **опенкср**</span><span class="sxs-lookup"><span data-stu-id="ce87d-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="ce87d-142">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="ce87d-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="ce87d-144">Optimization</span><span class="sxs-lookup"><span data-stu-id="ce87d-144">Optimization</span></span>

<span data-ttu-id="ce87d-145">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="ce87d-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="ce87d-147">Если рядом с **подключаемым модулем опенкср** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** , прежде чем продолжить.</span><span class="sxs-lookup"><span data-stu-id="ce87d-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ce87d-148">Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="ce87d-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="ce87d-150">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="ce87d-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ce87d-151">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="ce87d-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="ce87d-152">Примеры проектов Unity для Опенкср и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ce87d-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="ce87d-153">Ознакомьтесь с [репозиторием примеров Опенкср Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) для примера проектов Unity, демонстрирующих создание приложений Unity для головных телефонов HoloLens 2 или Mixed Reality с помощью подключаемого модуля Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="ce87d-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ce87d-154">Использование МРТК с поддержкой Опенкср</span><span class="sxs-lookup"><span data-stu-id="ce87d-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ce87d-155">МРТК для Unity версии 2,7 теперь официально поддерживает подключаемый модуль Mixed Reality Опенкср.</span><span class="sxs-lookup"><span data-stu-id="ce87d-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="ce87d-156">Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали.</span><span class="sxs-lookup"><span data-stu-id="ce87d-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="ce87d-157">Поддержка Опенкср находится в пакете **Foundation** .</span><span class="sxs-lookup"><span data-stu-id="ce87d-157">OpenXR support is in the **Foundation** package.</span></span>

![Окно компонентов функции смешанной реальности с выделенными стандартными активами](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="ce87d-159">При обновлении предыдущей версии МРТК убедитесь, что в файле **Assets/микседреалититулкит. Generated/link.xml** указана следующая строка:</span><span class="sxs-lookup"><span data-stu-id="ce87d-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ce87d-160">Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ce87d-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce87d-161">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ce87d-161">Next steps</span></span>

<span data-ttu-id="ce87d-162">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="ce87d-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ce87d-163">Хотите оставить отзыв?</span><span class="sxs-lookup"><span data-stu-id="ce87d-163">Have Feedback?</span></span>

<span data-ttu-id="ce87d-164">Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его.</span><span class="sxs-lookup"><span data-stu-id="ce87d-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ce87d-165">Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="ce87d-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce87d-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ce87d-166">See also</span></span>

* [<span data-ttu-id="ce87d-167">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="ce87d-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ce87d-168">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="ce87d-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ce87d-169">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="ce87d-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
