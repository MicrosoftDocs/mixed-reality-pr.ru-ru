---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 6e300c6117e04e2a49b060bcd7a6d268204f14da
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937479"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="ae9cb-104">Использование подключаемого модуля Опенкср в смешанной реальности для Unity</span><span class="sxs-lookup"><span data-stu-id="ae9cb-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="ae9cb-105">Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).</span><span class="sxs-lookup"><span data-stu-id="ae9cb-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae9cb-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="ae9cb-106">Prerequisites</span></span>

* <span data-ttu-id="ae9cb-107">Unity 2020,3 LTS или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="ae9cb-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="ae9cb-108">Подключаемый модуль Unity Опенкср 1.0.3 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="ae9cb-108">Unity OpenXR plugin 1.0.3 or later</span></span>
* <span data-ttu-id="ae9cb-109">Visual Studio 2019 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="ae9cb-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="ae9cb-110">Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ae9cb-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="ae9cb-111">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ae9cb-112">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

<!-- ## Setting up your project with MRTK

MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions. MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform. The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.

> [!div class="nextstepaction"]
> [Set up your project using MRTK](tutorials/mr-learning-base-01.md)

Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details. -->

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="ae9cb-113">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="ae9cb-113">Manual setup without MRTK</span></span>

<span data-ttu-id="ae9cb-114">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="ae9cb-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="ae9cb-115">Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":</span><span class="sxs-lookup"><span data-stu-id="ae9cb-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="ae9cb-117">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="ae9cb-117">Setting your build target</span></span>

<span data-ttu-id="ae9cb-118">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="ae9cb-118">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="ae9cb-120">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="ae9cb-120">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="ae9cb-121">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-121">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="ae9cb-122">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-122">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="ae9cb-123">Установка **архитектуры** **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-123">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="ae9cb-124">Задать **целевое устройство** в **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-124">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="ae9cb-125">Задать для **типа сборки** **D3D**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-125">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="ae9cb-126">Установить **последнюю версию** **пакета SDK для UWP**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-126">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="ae9cb-127">Задать для **конфигурации сборки** значение **Release** , так как имеются известные проблемы с производительностью при отладке</span><span class="sxs-lookup"><span data-stu-id="ae9cb-127">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

<span data-ttu-id="ae9cb-129">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-129">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ae9cb-130">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="ae9cb-130">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ae9cb-131">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ae9cb-131">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ae9cb-132">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-132">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ae9cb-133">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-133">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ae9cb-134">Установите флажки **инициализировать XR при запуске** и **опенкср**</span><span class="sxs-lookup"><span data-stu-id="ae9cb-134">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="ae9cb-135">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-135">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="ae9cb-137">Optimization</span><span class="sxs-lookup"><span data-stu-id="ae9cb-137">Optimization</span></span>

<span data-ttu-id="ae9cb-138">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-138">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="ae9cb-140">Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-140">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ae9cb-141">Для вступления изменений в силу может потребоваться перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-141">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="ae9cb-143">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="ae9cb-143">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ae9cb-144">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-144">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="ae9cb-145">Испытайте примеры сцен для Unity</span><span class="sxs-lookup"><span data-stu-id="ae9cb-145">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="ae9cb-146">Примеры HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ae9cb-146">HoloLens 2 samples</span></span>

1. <span data-ttu-id="ae9cb-147">В редакторе Unity перейдите к **окну > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-147">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="ae9cb-148">В списке пакетов выберите **подключаемый модуль Опенкср Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-148">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="ae9cb-149">Выберите пример в списке **образцы** и нажмите кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-149">Locate the sample in the **Samples** list and select **Import**</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выбранным подключаемым модулем смешанной реальности Опенкср и кнопка импорта выборки](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="ae9cb-151">При обновлении пакета Unity предоставляет возможность обновления импортированных образцов.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-151">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="ae9cb-152">При обновлении импортированного образца будут перезаписаны все изменения, внесенные в образец и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-152">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ae9cb-153">Использование МРТК с поддержкой Опенкср</span><span class="sxs-lookup"><span data-stu-id="ae9cb-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ae9cb-154">MRTK-Unity поддерживает подключаемый модуль Mixed Reality Опенкср, начиная с выпуска 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="ae9cb-155">Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="ae9cb-156">Поддержка Опенкср находится в пакете **Foundation** .</span><span class="sxs-lookup"><span data-stu-id="ae9cb-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="ae9cb-157">Перейдите к скрипту компонента набора средств Микседреалити Toolkit в инспекторе и переключитесь в профиль **дефаултопенксрконфигуратионпрофиле** :</span><span class="sxs-lookup"><span data-stu-id="ae9cb-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Снимок экрана: переключение конфигурации МРТК в компоненте набора средств Mixed Reality в инспекторе](images/openxr-img-11.png)

    1. <span data-ttu-id="ae9cb-159">[Более подробные сведения о переходе на опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ae9cb-160">При обновлении предыдущей версии МРТК убедитесь, что в файле **Assets/микседреалититулкит. Generated/link.xml** указана следующая строка:</span><span class="sxs-lookup"><span data-stu-id="ae9cb-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ae9cb-161">Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae9cb-162">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ae9cb-162">Next steps</span></span>

<span data-ttu-id="ae9cb-163">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ae9cb-164">Хотите оставить отзыв?</span><span class="sxs-lookup"><span data-stu-id="ae9cb-164">Have Feedback?</span></span>

<span data-ttu-id="ae9cb-165">Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ae9cb-166">Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="ae9cb-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9cb-167">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ae9cb-167">See also</span></span>

* [<span data-ttu-id="ae9cb-168">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="ae9cb-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ae9cb-169">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="ae9cb-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ae9cb-170">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="ae9cb-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
