---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 1adfb979cfc22be5da18ed990c9db55e6bad97f3
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238136"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="35bad-104">Использование подключаемого модуля Опенкср в смешанной реальности для Unity</span><span class="sxs-lookup"><span data-stu-id="35bad-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="35bad-105">Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).</span><span class="sxs-lookup"><span data-stu-id="35bad-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="35bad-106">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="35bad-106">Prerequisites</span></span>

* <span data-ttu-id="35bad-107">Unity 2020,2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="35bad-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="35bad-108">Подключаемый модуль Unity Опенкср 0.1.2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="35bad-108">Unity OpenXR plugin 0.1.2 or later</span></span>
* <span data-ttu-id="35bad-109">Visual Studio 2019 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="35bad-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="35bad-110">Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="35bad-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="35bad-111">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="35bad-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="35bad-112">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="35bad-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="35bad-113">Установка Опенкср с помощью средства "функция смешанной реальности"</span><span class="sxs-lookup"><span data-stu-id="35bad-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="35bad-114">Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности".</span><span class="sxs-lookup"><span data-stu-id="35bad-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="35bad-115">Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":</span><span class="sxs-lookup"><span data-stu-id="35bad-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="35bad-117">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="35bad-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="35bad-118">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="35bad-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="35bad-119">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="35bad-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="35bad-120">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="35bad-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="35bad-121">Установите флажки **инициализировать XR при запуске** и **опенкср (Предварительная версия)** .</span><span class="sxs-lookup"><span data-stu-id="35bad-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="35bad-122">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="35bad-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="35bad-124">Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="35bad-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="35bad-125">Для вступления изменений в силу может потребоваться перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="35bad-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="35bad-127">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="35bad-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="35bad-128">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="35bad-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="35bad-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="35bad-129">Optimization</span></span>

<span data-ttu-id="35bad-130">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="35bad-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="35bad-132">Испытайте примеры сцен для Unity</span><span class="sxs-lookup"><span data-stu-id="35bad-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="35bad-133">Чтобы использовать один или несколько примеров, установите [арфаундатион 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) из **диспетчера пакетов**:</span><span class="sxs-lookup"><span data-stu-id="35bad-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным элементом управления AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="35bad-135">Примеры HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="35bad-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="35bad-136">В редакторе Unity перейдите к **окну > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="35bad-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="35bad-137">В списке пакетов выберите **подключаемый модуль Опенкср Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="35bad-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="35bad-138">Выберите пример в списке **образцы** и нажмите кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="35bad-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выбранным подключаемым модулем смешанной реальности Опенкср и кнопка импорта выборки](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="35bad-140">При обновлении пакета Unity предоставляет возможность обновления импортированных образцов.</span><span class="sxs-lookup"><span data-stu-id="35bad-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="35bad-141">При обновлении импортированного образца будут перезаписаны все изменения, внесенные в образец и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="35bad-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="35bad-142">Использование МРТК с поддержкой Опенкср</span><span class="sxs-lookup"><span data-stu-id="35bad-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="35bad-143">МРТК Unity поддерживает подключаемый модуль Mixed Reality Опенкср, начиная с выпуска 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="35bad-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="35bad-144">Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) " и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории поддержка платформы.</span><span class="sxs-lookup"><span data-stu-id="35bad-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>

<!-- MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin). You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Add following packages in your **[projectRoot]/Packages/manifest.json** file:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
``` -->

2. <span data-ttu-id="35bad-145">Перейдите к скрипту компонента набора средств Микседреалити Toolkit в инспекторе и переключитесь в профиль **дефаултопенксрконфигуратионпрофиле** :</span><span class="sxs-lookup"><span data-stu-id="35bad-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![Снимок экрана: переключение конфигурации МРТК в компоненте набора средств Mixed Reality в инспекторе](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="35bad-147">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="35bad-147">Known issues</span></span> 

<span data-ttu-id="35bad-148">При использовании функции отслеживания вручную добавьте следующую строку в файл **Assets/микседреалититулкит. Generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="35bad-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="35bad-149">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="35bad-149">Next steps</span></span>

<span data-ttu-id="35bad-150">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="35bad-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="35bad-151">Хотите оставить отзыв?</span><span class="sxs-lookup"><span data-stu-id="35bad-151">Have Feedback?</span></span>

<span data-ttu-id="35bad-152">Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его.</span><span class="sxs-lookup"><span data-stu-id="35bad-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="35bad-153">Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="35bad-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="35bad-154">См. также</span><span class="sxs-lookup"><span data-stu-id="35bad-154">See also</span></span>

* [<span data-ttu-id="35bad-155">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="35bad-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="35bad-156">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="35bad-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="35bad-157">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="35bad-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
