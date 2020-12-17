---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: adb678d168d86dc2376ac46caa690e5db036099c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622983"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="52804-104">Использование подключаемого модуля Опенкср в смешанной реальности для Unity</span><span class="sxs-lookup"><span data-stu-id="52804-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="52804-105">Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).</span><span class="sxs-lookup"><span data-stu-id="52804-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52804-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="52804-106">Prerequisites</span></span>

*   <span data-ttu-id="52804-107">Unity 2020,2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="52804-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="52804-108">Подключаемый модуль Unity Опенкср 0.1.1 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="52804-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="52804-109">Visual Studio 2019 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="52804-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="52804-110">Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="52804-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="52804-111">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="52804-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="52804-112">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="52804-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="52804-113">Установка подключаемого модуля Опенкср Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="52804-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="52804-114">Перед использованием подключаемого модуля Опенкср для смешанной реальности необходимо установить **подключаемый модуль опенкср** для Unity и пакеты **управления подключаемым модулем XR** :</span><span class="sxs-lookup"><span data-stu-id="52804-114">Before using the Mixed Reality OpenXR Plugin, you need to install Unity’s **OpenXR Plugin** and **XR Plugin Management** packages:</span></span>

1. <span data-ttu-id="52804-115">В редакторе Unity выберите **правка > параметры проекта > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="52804-115">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="52804-116">Разверните раздел **реестра с областью действия** , введите следующие сведения и выберите **сохранить**:</span><span class="sxs-lookup"><span data-stu-id="52804-116">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="52804-117">Присвоить **имя** **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="52804-117">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="52804-118">Задать **URL-адрес\*\*\*\*https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="52804-118">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="52804-119">Задайте для **областей** значение **com. Microsoft. микседреалити**</span><span class="sxs-lookup"><span data-stu-id="52804-119">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="52804-120">В разделе **Дополнительные параметры** выберите **включить предварительные версии пакетов** .</span><span class="sxs-lookup"><span data-stu-id="52804-120">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Снимок экрана: окно диспетчера пакетов Unity, открываемое в параметрах проекта](images/openxr-img-01.png)

<span data-ttu-id="52804-122">Диспетчер пакетов Unity использует файл манифеста с именем *manifest.js* для определения устанавливаемых пакетов и реестров, из которых они могут быть установлены.</span><span class="sxs-lookup"><span data-stu-id="52804-122">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52804-123">Опенкср по-прежнему является экспериментальным в Unity, и этот процесс может измениться со временем, так как мы работаем над оптимизацией процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="52804-123">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="52804-124">Регистрация зависимости Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="52804-124">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="52804-125">После добавления реестра с областью действия Microsoft Mixed Reality в манифест можно указать пакет Опенкср.</span><span class="sxs-lookup"><span data-stu-id="52804-125">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="52804-126">Чтобы добавить пакет Опенкср, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="52804-126">To add the OpenXR package:</span></span>

1. <span data-ttu-id="52804-127">Откройте **<projectRoot> /паккажес/manifest.js** в текстовом редакторе, например Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="52804-127">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="52804-128">Измените раздел "зависимости" в файле *packages/manifest.jsдля* файла следующим образом:</span><span class="sxs-lookup"><span data-stu-id="52804-128">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52804-129">В файле манифеста может быть больше зависимостей, чем показано здесь.</span><span class="sxs-lookup"><span data-stu-id="52804-129">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="52804-130">Не удаляйте ни один из них. просто добавьте в список зависимость Опенкср.</span><span class="sxs-lookup"><span data-stu-id="52804-130">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="52804-131">Сохраните файл, вернитесь в редактор Unity и откройте **Диспетчер пакетов** , чтобы убедиться, что подключаемый модуль установлен:</span><span class="sxs-lookup"><span data-stu-id="52804-131">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным подключаемым модулем Mixed Reality Опенкср](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="52804-133">Если пакет Опенкср удаляется с помощью диспетчера пакетов Unity, его необходимо добавить повторно с помощью описанных выше действий.</span><span class="sxs-lookup"><span data-stu-id="52804-133">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="52804-134">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="52804-134">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="52804-135">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="52804-135">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="52804-136">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="52804-136">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="52804-137">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="52804-137">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="52804-138">Установите флажки **инициализировать XR при запуске** и **опенкср (Предварительная версия)** .</span><span class="sxs-lookup"><span data-stu-id="52804-138">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="52804-139">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="52804-139">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="52804-141">Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="52804-141">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="52804-142">Для вступления изменений в силу может потребоваться перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="52804-142">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="52804-144">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="52804-144">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="52804-145">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="52804-145">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="52804-146">Optimization</span><span class="sxs-lookup"><span data-stu-id="52804-146">Optimization</span></span>

<span data-ttu-id="52804-147">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="52804-147">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="52804-149">Испытайте примеры сцен для Unity</span><span class="sxs-lookup"><span data-stu-id="52804-149">Try out the Unity sample scenes</span></span>

<span data-ttu-id="52804-150">Чтобы использовать один или несколько примеров, установите [арфаундатион 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) из **пакакаже Manager**:</span><span class="sxs-lookup"><span data-stu-id="52804-150">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным элементом управления AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="52804-152">Примеры HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="52804-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="52804-153">В редакторе Unity перейдите к **окну > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="52804-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="52804-154">В списке пакетов выберите **подключаемый модуль Опенкср Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="52804-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="52804-155">Выберите пример в списке **образцы** и нажмите кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="52804-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выбранным подключаемым модулем смешанной реальности Опенкср и кнопка импорта выборки](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="52804-157">При обновлении пакета Unity предоставляет возможность обновления импортированных образцов.</span><span class="sxs-lookup"><span data-stu-id="52804-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="52804-158">При обновлении импортированного образца будут перезаписаны все изменения, внесенные в образец и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="52804-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="52804-159">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="52804-159">Next steps</span></span> 

<span data-ttu-id="52804-160">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="52804-160">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="52804-161">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="52804-161">See also</span></span>
* [<span data-ttu-id="52804-162">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="52804-162">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="52804-163">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="52804-163">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="52804-164">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="52804-164">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)