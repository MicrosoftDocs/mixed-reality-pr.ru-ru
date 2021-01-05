---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 9e7f59c57d409d61df73e6d07659bf6c7242202c
ms.sourcegitcommit: 5784336a780486d05db6a627839efe47f08fac36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97880607"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="bacb4-104">Использование подключаемого модуля Опенкср в смешанной реальности для Unity</span><span class="sxs-lookup"><span data-stu-id="bacb4-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="bacb4-105">Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).</span><span class="sxs-lookup"><span data-stu-id="bacb4-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bacb4-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="bacb4-106">Prerequisites</span></span>

* <span data-ttu-id="bacb4-107">Unity 2020,2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="bacb4-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="bacb4-108">Подключаемый модуль Unity Опенкср 0.1.1 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="bacb4-108">Unity OpenXR plugin 0.1.1 or later</span></span>
* <span data-ttu-id="bacb4-109">Visual Studio 2019 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="bacb4-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="bacb4-110">Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bacb4-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="bacb4-111">Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется.</span><span class="sxs-lookup"><span data-stu-id="bacb4-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="bacb4-112">Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.</span><span class="sxs-lookup"><span data-stu-id="bacb4-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="bacb4-113">Установка подключаемого модуля Опенкср Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bacb4-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="bacb4-114">Перед использованием подключаемого модуля Опенкср Mixed Reality в проекте необходимо установить **подключаемый модуль опенкср** и пакеты **управления подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="bacb4-115">Если вы уже установили их, отлично!</span><span class="sxs-lookup"><span data-stu-id="bacb4-115">If you've already installed them, great!</span></span> <span data-ttu-id="bacb4-116">В противном случае Установка подключаемого модуля Опенкср для смешанной реальности автоматически установит их как зависимости:</span><span class="sxs-lookup"><span data-stu-id="bacb4-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="bacb4-117">В редакторе Unity выберите **правка > параметры проекта > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="bacb4-118">Разверните раздел **реестра с областью действия** , введите следующие сведения и выберите **сохранить**:</span><span class="sxs-lookup"><span data-stu-id="bacb4-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="bacb4-119">Присвоить **имя** **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="bacb4-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="bacb4-120">Задать **URL-адрес\*\*\*\*https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="bacb4-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="bacb4-121">Задайте для **областей** значение **com. Microsoft. микседреалити**</span><span class="sxs-lookup"><span data-stu-id="bacb4-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="bacb4-122">В разделе **Дополнительные параметры** выберите **включить предварительные версии пакетов** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Снимок экрана: окно диспетчера пакетов Unity, открываемое в параметрах проекта](images/openxr-img-01.png)

<span data-ttu-id="bacb4-124">Диспетчер пакетов Unity использует файл манифеста с именем *manifest.js* для определения устанавливаемых пакетов и реестров, из которых они могут быть установлены.</span><span class="sxs-lookup"><span data-stu-id="bacb4-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bacb4-125">Опенкср по-прежнему является экспериментальным в Unity, и этот процесс может измениться со временем, так как мы работаем над оптимизацией процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="bacb4-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="bacb4-126">Регистрация зависимости Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bacb4-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="bacb4-127">После добавления реестра с областью действия Microsoft Mixed Reality в манифест можно указать пакет Опенкср.</span><span class="sxs-lookup"><span data-stu-id="bacb4-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="bacb4-128">Чтобы добавить пакет Опенкср, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="bacb4-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="bacb4-129">Откройте **[прожектрут]/паккажес/manifest.js** в текстовом редакторе, например Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bacb4-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="bacb4-130">Чтобы получить его, щелкните правой кнопкой мыши **пакеты** на левой панели окна проекта.</span><span class="sxs-lookup"><span data-stu-id="bacb4-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="bacb4-131">Затем нажмите кнопку " **отобразить в проводнике**".</span><span class="sxs-lookup"><span data-stu-id="bacb4-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="bacb4-132">![Снимок экрана: список пакетов в окне проекта](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="bacb4-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="bacb4-133">Измените раздел "зависимости" в файле *packages/manifest.jsдля* файла следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bacb4-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bacb4-134">В файле манифеста может быть больше зависимостей, чем показано здесь.</span><span class="sxs-lookup"><span data-stu-id="bacb4-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="bacb4-135">Не удаляйте ни один из них. просто добавьте в список зависимость Опенкср.</span><span class="sxs-lookup"><span data-stu-id="bacb4-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. <span data-ttu-id="bacb4-136">Сохраните файл, вернитесь в редактор Unity и откройте **Диспетчер пакетов** , чтобы убедиться, что подключаемый модуль установлен:</span><span class="sxs-lookup"><span data-stu-id="bacb4-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным подключаемым модулем Mixed Reality Опенкср](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="bacb4-138">Если пакет Опенкср удаляется с помощью диспетчера пакетов Unity, его необходимо добавить повторно с помощью описанных выше действий.</span><span class="sxs-lookup"><span data-stu-id="bacb4-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="bacb4-139">Настройка управления подключаемым модулем XR для Опенкср</span><span class="sxs-lookup"><span data-stu-id="bacb4-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="bacb4-140">Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="bacb4-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="bacb4-141">В редакторе Unity перейдите к **изменению > параметры проекта**</span><span class="sxs-lookup"><span data-stu-id="bacb4-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="bacb4-142">В списке параметров выберите **Управление подключаемым модулем XR** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="bacb4-143">Установите флажки **инициализировать XR при запуске** и **опенкср (Предварительная версия)** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="bacb4-144">Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="bacb4-146">Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением.</span><span class="sxs-lookup"><span data-stu-id="bacb4-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="bacb4-147">Для вступления изменений в силу может потребоваться перезапустить редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="bacb4-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

<span data-ttu-id="bacb4-149">Теперь вы готовы начать разработку с помощью Опенкср в Unity!</span><span class="sxs-lookup"><span data-stu-id="bacb4-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="bacb4-150">Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.</span><span class="sxs-lookup"><span data-stu-id="bacb4-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="bacb4-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="bacb4-151">Optimization</span></span>

<span data-ttu-id="bacb4-152">Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="bacb4-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="bacb4-154">Испытайте примеры сцен для Unity</span><span class="sxs-lookup"><span data-stu-id="bacb4-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="bacb4-155">Чтобы использовать один или несколько примеров, установите [арфаундатион 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) из **диспетчера пакетов**:</span><span class="sxs-lookup"><span data-stu-id="bacb4-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным элементом управления AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="bacb4-157">Примеры HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bacb4-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="bacb4-158">В редакторе Unity перейдите к **окну > диспетчер пакетов** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="bacb4-159">В списке пакетов выберите **подключаемый модуль Опенкср Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="bacb4-160">Выберите пример в списке **образцы** и нажмите кнопку **Импорт** .</span><span class="sxs-lookup"><span data-stu-id="bacb4-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выбранным подключаемым модулем смешанной реальности Опенкср и кнопка импорта выборки](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="bacb4-162">При обновлении пакета Unity предоставляет возможность обновления импортированных образцов.</span><span class="sxs-lookup"><span data-stu-id="bacb4-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="bacb4-163">При обновлении импортированного образца будут перезаписаны все изменения, внесенные в образец и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="bacb4-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bacb4-164">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="bacb4-164">Next steps</span></span>

<span data-ttu-id="bacb4-165">Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.</span><span class="sxs-lookup"><span data-stu-id="bacb4-165">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="bacb4-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bacb4-166">See also</span></span>

* [<span data-ttu-id="bacb4-167">Настройка проекта без МРТК</span><span class="sxs-lookup"><span data-stu-id="bacb4-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="bacb4-168">Рекомендуемые параметры для Unity</span><span class="sxs-lookup"><span data-stu-id="bacb4-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="bacb4-169">Рекомендации по производительности для Unity</span><span class="sxs-lookup"><span data-stu-id="bacb4-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
