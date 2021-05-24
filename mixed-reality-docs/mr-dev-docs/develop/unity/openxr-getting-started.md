---
title: Использование подключаемого модуля Смешанной реальности OpenXR
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333446"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="e206f-104">Использование подключаемого модуля Смешанной реальности OpenXR</span><span class="sxs-lookup"><span data-stu-id="e206f-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="e206f-105">Для разработчиков, нацеленных на Unity 2020 для создания приложений HoloLens 2 или Mixed Reality, можно использовать подключаемый модуль Опенкср вместо подключаемого модуля Виндовскср для повышения совместимости между платформами.</span><span class="sxs-lookup"><span data-stu-id="e206f-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="e206f-106">Подключаемый модуль Опенкср для смешанной реальности хорошо работает с последним [компонентом функции смешанной реальности](welcome-to-mr-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e206f-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e206f-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="e206f-107">Prerequisites</span></span>

* <span data-ttu-id="e206f-108">Последняя версия Unity 2020,3 LTS, рекомендуется 2020.3.6 F1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="e206f-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="e206f-109">Последний подключаемый модуль Unity Опенкср, рекомендуемый 1,2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="e206f-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="e206f-110">Новейшие [средства для разработки HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="e206f-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="e206f-111">Последняя МРТК (необязательно), рекомендуемая версия 2,6 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="e206f-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="e206f-112">Последний подключаемый модуль Опенкср смешанной реальности, рекомендуемая версия 0.9.5 или более поздняя</span><span class="sxs-lookup"><span data-stu-id="e206f-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="e206f-113">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="e206f-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="e206f-114">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="e206f-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="e206f-115">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="e206f-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="e206f-116">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="e206f-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="e206f-117">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="e206f-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="e206f-118">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="e206f-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e206f-119">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="e206f-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="e206f-120">Дополнительные сведения о функциях см. в [документации по MRTK ](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="e206f-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="e206f-121">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="e206f-121">Manual setup without MRTK</span></span>

<span data-ttu-id="e206f-122">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="e206f-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="e206f-123">Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":</span><span class="sxs-lookup"><span data-stu-id="e206f-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="e206f-125">Настройка целевого объекта сборки</span><span class="sxs-lookup"><span data-stu-id="e206f-125">Setting your build target</span></span>

<span data-ttu-id="e206f-126">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="e206f-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="e206f-128">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="e206f-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="e206f-129">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="e206f-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="e206f-130">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="e206f-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="e206f-131">Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="e206f-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="e206f-132">Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e206f-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="e206f-133">Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="e206f-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="e206f-134">Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).</span><span class="sxs-lookup"><span data-stu-id="e206f-134">Set **UWP SDK** to **Latest installed**</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="e206f-136">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="e206f-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="e206f-137">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e206f-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="e206f-138">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="e206f-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="e206f-139">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="e206f-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="e206f-140">Установите флажки **инициализировать XR при запуске** и **опенкср**</span><span class="sxs-lookup"><span data-stu-id="e206f-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="e206f-141">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="e206f-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="e206f-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="e206f-143">Optimization</span></span>

<span data-ttu-id="e206f-144">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="e206f-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="e206f-146">Если рядом с **подключаемым модулем опенкср** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** , прежде чем продолжить.</span><span class="sxs-lookup"><span data-stu-id="e206f-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="e206f-147">Чтобы изменения вступили в силу, возможно, потребуется перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="e206f-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="e206f-149">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="e206f-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="e206f-150">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="e206f-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="e206f-151">Примеры проектов Unity для Опенкср и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e206f-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="e206f-152">Ознакомьтесь с [репозиторием примеров Опенкср Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) для примера проектов Unity, демонстрирующих создание приложений Unity для головных телефонов HoloLens 2 или Mixed Reality с помощью подключаемого модуля Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="e206f-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="e206f-153">Использование МРТК с поддержкой Опенкср</span><span class="sxs-lookup"><span data-stu-id="e206f-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="e206f-154">MRTK-Unity поддерживает подключаемый модуль Mixed Reality Опенкср, начиная с выпуска 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="e206f-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="e206f-155">Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали.</span><span class="sxs-lookup"><span data-stu-id="e206f-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="e206f-156">Поддержка Опенкср находится в пакете **Foundation** .</span><span class="sxs-lookup"><span data-stu-id="e206f-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="e206f-157">Перейдите к скрипту компонента набора средств Микседреалити Toolkit в инспекторе и переключитесь в профиль **дефаултопенксрконфигуратионпрофиле** :</span><span class="sxs-lookup"><span data-stu-id="e206f-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Снимок экрана: переключение конфигурации МРТК в компоненте набора средств Mixed Reality в инспекторе](images/openxr-img-11.png)

    1. <span data-ttu-id="e206f-159">[Более подробные сведения о переходе на опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="e206f-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="e206f-160">При обновлении предыдущей версии МРТК убедитесь, что в файле **Assets/микседреалититулкит. Generated/link.xml** указана следующая строка:</span><span class="sxs-lookup"><span data-stu-id="e206f-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="e206f-161">Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="e206f-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e206f-162">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="e206f-162">Next steps</span></span>

<span data-ttu-id="e206f-163">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="e206f-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="e206f-164">Хотите оставить отзыв?</span><span class="sxs-lookup"><span data-stu-id="e206f-164">Have Feedback?</span></span>

<span data-ttu-id="e206f-165">Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его.</span><span class="sxs-lookup"><span data-stu-id="e206f-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="e206f-166">Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="e206f-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e206f-167">См. также</span><span class="sxs-lookup"><span data-stu-id="e206f-167">See also</span></span>

* [<span data-ttu-id="e206f-168">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="e206f-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="e206f-169">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="e206f-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="e206f-170">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="e206f-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
