---
title: Пространственные привязки Azure для Android и iOS
description: Пройдите этот курс и узнайте, как развернуть проект Unity с использованием Mixed Reality Toolkit (MRTK) и Пространственных привязок Azure для Android и iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, Android, iOS, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 699c7689fcd23543f4d4b0e86f64cdbf98debc1f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590716"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="76a5b-104">5. Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="76a5b-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="76a5b-105">В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="76a5b-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="76a5b-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="76a5b-106">Objectives</span></span>

* <span data-ttu-id="76a5b-107">Узнайте, как выполнить сборку проекта на своем устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="76a5b-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="76a5b-108">Узнайте, как выполнить сборку проекта на своем устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="76a5b-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="76a5b-109">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="76a5b-109">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="76a5b-110">В этом разделе будут обновлены и установлены следующие встроенные пакеты:</span><span class="sxs-lookup"><span data-stu-id="76a5b-110">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="76a5b-111">AR Foundation 3.1.3;</span><span class="sxs-lookup"><span data-stu-id="76a5b-111">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="76a5b-112">XR Legacy Input Helpers 2.1.6</span><span class="sxs-lookup"><span data-stu-id="76a5b-112">XR Legacy Input Helpers 2.1.6</span></span>
* <span data-ttu-id="76a5b-113">пакет поддержки ARCore XR Plugin 3.1.3 для Android;</span><span class="sxs-lookup"><span data-stu-id="76a5b-113">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="76a5b-114">пакет поддержки ARKit XR plugin 3.1.3 для iOS.</span><span class="sxs-lookup"><span data-stu-id="76a5b-114">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="76a5b-115">Не все версии совместимы с MRTK. С набором будет работать только определенная версия, поэтому убедитесь, что установлены в точности те версии, которые перечислены выше.</span><span class="sxs-lookup"><span data-stu-id="76a5b-115">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="76a5b-116">В меню Unity выберите **Window (Окно)**  > **Package Manager (Диспетчер пакетов)** , чтобы открыть окно диспетчера пакетов. Затем выберите **AR Foundation** > **3.1.3** и нажмите кнопку **Update to 3.1.3** (Обновить до 3.1.3), чтобы обновить пакет.</span><span class="sxs-lookup"><span data-stu-id="76a5b-116">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![Диспетчер пакетов Unity с выбранным пакетом AR Foundation](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="76a5b-118">С помощью той же процедуры вы можете по мере необходимости импортировать остальные пакеты.</span><span class="sxs-lookup"><span data-stu-id="76a5b-118">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="76a5b-119">Если вы разрабатываете проект для Android, устанавливать пакет ARKit XR Plugin не нужно.</span><span class="sxs-lookup"><span data-stu-id="76a5b-119">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="76a5b-120">Если вы разрабатываете проект для iOS, устанавливать пакет ARCore XR Plugin также не нужно.</span><span class="sxs-lookup"><span data-stu-id="76a5b-120">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="76a5b-121">Настройка MRTK для камеры AR Foundation</span><span class="sxs-lookup"><span data-stu-id="76a5b-121">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="76a5b-122">Из этого раздела вы узнаете, как настроить MRTK для развертывания на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="76a5b-122">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="76a5b-123">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="76a5b-123">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="76a5b-124">Затем в окне Inspector (Инспектор) перейдите на вкладку **Camera** (Камера), клонируйте профиль камеры и присвойте ему понятное имя, например **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="76a5b-124">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity с выбранным созданным профилем ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="76a5b-126">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="76a5b-126">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="76a5b-127">Оставив выбранной вкладку **Camera** (Камера) в окне Inspector (Инспектор), разверните раздел **Camera Setting Providers** (Поставщики параметров камеры) и нажмите кнопку **+ Add Camera Setting Provider** (+ Добавить поставщик параметров), а затем разверните появившийся раздел **New data provider 1** (Новый поставщик данных 1).</span><span class="sxs-lookup"><span data-stu-id="76a5b-127">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![Профиль ARCameraProfile в Unity с добавленным поставщиком данных](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="76a5b-129">В раскрывающемся списке **Type** (Тип) измените тип на **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="76a5b-129">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![Выбор типа поставщика данных для профиля ARCameraProfile в Unity](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="76a5b-131">Оставив выбранным объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), нажмите кнопку **Add Component** (Добавить компонент) в окне Inspector (Инспектор), чтобы добавить следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="76a5b-131">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="76a5b-132">диспетчер привязок AR (скрипт);</span><span class="sxs-lookup"><span data-stu-id="76a5b-132">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="76a5b-133">DisableDiagnosticsSystem (скрипт).</span><span class="sxs-lookup"><span data-stu-id="76a5b-133">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="76a5b-134">Объект MixedRealityToolkit в Unity с добавленными компонентами AR Anchor Manager и DisableDiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="76a5b-134">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="76a5b-135">При добавлении компонента диспетчера опорных точек AR (скрипт) автоматически добавляется компонент источника сеанса AR (скрипт), так как он необходим компоненту диспетчера опорных точек AR (скрипт).</span><span class="sxs-lookup"><span data-stu-id="76a5b-135">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>



<span data-ttu-id="76a5b-136">Выполните обновление описаний скриптов UnityAR в MRTK, вызвав элемент меню: **Mixed Reality Toolkit** > **Utilities (Служебные программы)**  > **UnityAR** > Update Scripting Defines (Обновить описания скриптов)</span><span class="sxs-lookup"><span data-stu-id="76a5b-136">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="76a5b-137">Создание приложения для устройства Android</span><span class="sxs-lookup"><span data-stu-id="76a5b-137">Building your application to your Android device</span></span>

<span data-ttu-id="76a5b-138">Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве Android.</span><span class="sxs-lookup"><span data-stu-id="76a5b-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="76a5b-139">В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на Android.</span><span class="sxs-lookup"><span data-stu-id="76a5b-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Окно параметров сборки Unity с выбранной платформой Android](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="76a5b-141">Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="76a5b-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="76a5b-142">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="76a5b-142">Close the Build Settings window.</span></span>

<span data-ttu-id="76a5b-143">В меню Unity выберите **Mixed Reality Toolkit (Набор средств для смешанной реальности)**  > **Utilities (Служебные программы)**  > **Configure Unity Project (Настройка проекта Unity)** ,чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="76a5b-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Окно конфигуратора проектов MRTK в Unity для Android](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="76a5b-145">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Выберите элемент **Vulkan** и удалите его, щелкнув символ **-** .</span><span class="sxs-lookup"><span data-stu-id="76a5b-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Другие параметры Unity с выбранным API Vulcan](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="76a5b-147">В меню Unity выберите **Edit (Правка)**  > **Project Settings (Параметры проекта)**  >**Player (Проигрыватель)** > **XR Setting (Параметры смешанной реальности)** , убедитесь, что вы используете платформу **Android** и установите флажок **Virtual Reality Supported** (С поддержкой виртуальной реальности), затем щелкните значок "+" и выберите None (Нет):</span><span class="sxs-lookup"><span data-stu-id="76a5b-147">In the Unity menu, select **Edit** > **Project Settings...** >**Player**> **XR Setting**, make sure you are in **Android** platform and check the **Virtual Reality Supported** checkbox then click the + icon, and select None:</span></span>

![Окно конфигуратора проектов MRTK в Unity для Android](images/mr-learning-asa/asa-05-section3-step1-2-1.png)

<span data-ttu-id="76a5b-149">Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="76a5b-149">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="76a5b-150">В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="76a5b-150">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="76a5b-151">Затем с помощью USB-кабеля подключите к компьютеру устройство Android и выберите его в раскрывающемся списке **Run Device** (Запустить устройство).</span><span class="sxs-lookup"><span data-stu-id="76a5b-151">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Окно параметров сборки в Unity с добавленной сценой и выбранным устройством выполнения](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="76a5b-153">Если устройство не отображается в раскрывающемся списке Run Device (Запустить устройство), возможно, потребуется нажать кнопку Refresh (Обновить) рядом с раскрывающимся списком.</span><span class="sxs-lookup"><span data-stu-id="76a5b-153">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="76a5b-154">В окне Build Settings (Параметры сборки) нажмите кнопку **Build And Run** (Сборка и запуск), чтобы открыть окно сборка Android.</span><span class="sxs-lookup"><span data-stu-id="76a5b-154">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="76a5b-155">Выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_. Присвойте сборке APK понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Save** (Сохранить), чтобы запустить процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="76a5b-155">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном сохранения для Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="76a5b-157">Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK и JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="76a5b-157">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="76a5b-158">По завершении сборки приложения должны автоматически загрузиться на устройство Android.</span><span class="sxs-lookup"><span data-stu-id="76a5b-158">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="76a5b-159">Создание приложения для устройства iOS</span><span class="sxs-lookup"><span data-stu-id="76a5b-159">Building your application to your iOS device</span></span>

<span data-ttu-id="76a5b-160">Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве iOS.</span><span class="sxs-lookup"><span data-stu-id="76a5b-160">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="76a5b-161">В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на iOS.</span><span class="sxs-lookup"><span data-stu-id="76a5b-161">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Окно параметров сборки Unity с выбранным вариантом iOS](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="76a5b-163">Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="76a5b-163">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="76a5b-164">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="76a5b-164">Close the Build Settings window.</span></span>

<span data-ttu-id="76a5b-165">В меню Unity выберите **Mixed Reality Toolkit (Набор средств для смешанной реальности)**  > **Utilities (Служебные программы)**  > **Configure Unity Project (Настройка проекта Unity)** ,чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="76a5b-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Окно конфигурации проекта MRTK в Unity для iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="76a5b-167">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Снимите флажок **Strip Engine Code** (Удалить код обработчика), чтобы отключить его.</span><span class="sxs-lookup"><span data-stu-id="76a5b-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Другие параметры Unity с отключенным параметром Strip Engine Code (Удалить код обработчика)](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="76a5b-169">Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="76a5b-169">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="76a5b-170">В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="76a5b-170">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Окно параметров сборки Unity с добавленной сценой](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="76a5b-172">В окне Build Settings (Параметры сборки) нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки iOS.</span><span class="sxs-lookup"><span data-stu-id="76a5b-172">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="76a5b-173">Выберите подходящее расположение для хранения проекта Xcode, например _D:\MixedRealityLearning\Builds_. Создайте папку и присвойте ей понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы начать сборку.</span><span class="sxs-lookup"><span data-stu-id="76a5b-173">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном сохранения для iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="76a5b-175">После сборки выполните инструкции из раздела [Экспорт проект Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы научиться развертывать проекты Xcode на устройствах iOS.</span><span class="sxs-lookup"><span data-stu-id="76a5b-175">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="76a5b-176">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="76a5b-176">Congratulations</span></span>

<span data-ttu-id="76a5b-177">Из этого руководства вы узнали, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="76a5b-177">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>