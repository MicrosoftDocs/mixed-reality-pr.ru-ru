---
title: Пространственные привязки Azure для Android и iOS
description: Пройдите этот курс и узнайте, как развернуть проект Unity с использованием Mixed Reality Toolkit (MRTK) и Пространственных привязок Azure для Android и iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, Android, iOS, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403435"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="fdc5d-104">5. Пространственные привязки Azure для Android и iOS</span><span class="sxs-lookup"><span data-stu-id="fdc5d-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="fdc5d-105">В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="fdc5d-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="fdc5d-106">Objectives</span></span>

* <span data-ttu-id="fdc5d-107">Узнайте, как выполнить сборку проекта на своем устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="fdc5d-108">Узнайте, как выполнить сборку проекта на своем устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="fdc5d-109">Установка встроенных пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="fdc5d-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="fdc5d-110">Настройка MRTK для камеры AR Foundation</span><span class="sxs-lookup"><span data-stu-id="fdc5d-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="fdc5d-111">Из этого раздела вы узнаете, как настроить MRTK для развертывания на мобильном устройстве.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="fdc5d-112">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="fdc5d-113">Затем в окне Inspector (Инспектор) перейдите на вкладку **Camera** (Камера), клонируйте профиль камеры и присвойте ему понятное имя, например **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="fdc5d-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity с выбранным созданным профилем ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="fdc5d-115">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="fdc5d-116">Оставляя выбранной вкладку **Camera** (Камера) в окне инспектора, разверните раздел **Camera Setting Providers** (Поставщики параметров камеры) и щелкните "-", чтобы удалить **Windows Mixed Reality Camera Setting** (Параметры камеры Windows Mixed Reality) или **XR SDK Windows Mixed Reality Camera Setting** (Параметры камеры XR SDK Windows Mixed Reality):</span><span class="sxs-lookup"><span data-stu-id="fdc5d-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="fdc5d-117">Профиль ARCameraProfile в Unity с добавленным поставщиком данных</span><span class="sxs-lookup"><span data-stu-id="fdc5d-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="fdc5d-118">Затем нажмите кнопку **+ Add Camera Setting Provider** (Добавить поставщика параметров камеры), а затем разверните добавленный раздел **New data provider** (Новый поставщик данных):</span><span class="sxs-lookup"><span data-stu-id="fdc5d-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Добавлена камера AR для Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="fdc5d-120">В раскрывающемся списке **Type** (Тип) измените тип на **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="fdc5d-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![Выбор типа поставщика данных для профиля ARCameraProfile в Unity](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="fdc5d-122">Выполните обновление описаний скриптов UnityAR в MRTK, вызвав элемент меню: **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **UnityAR** > Update Scripting Defines (Обновить описания скриптов)</span><span class="sxs-lookup"><span data-stu-id="fdc5d-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="fdc5d-123">Создание приложения для устройства Android</span><span class="sxs-lookup"><span data-stu-id="fdc5d-123">Building your application to your Android device</span></span>

<span data-ttu-id="fdc5d-124">Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве Android.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="fdc5d-125">В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на Android.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Окно параметров сборки Unity с выбранной платформой Android](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="fdc5d-127">Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="fdc5d-128">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-128">Close the Build Settings window.</span></span>

<span data-ttu-id="fdc5d-129">В меню Unity выберите **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **Configure Project for MRTK** (Настройка проекта для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Конфигуратор проекта Unity MRTK 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="fdc5d-131">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Выберите элемент **Vulkan** и удалите его, щелкнув символ **-** .</span><span class="sxs-lookup"><span data-stu-id="fdc5d-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Другие параметры Unity с выбранным API Vulcan](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="fdc5d-133">В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="fdc5d-134">Затем с помощью USB-кабеля подключите к компьютеру устройство Android и выберите его в раскрывающемся списке **Run Device** (Запустить устройство).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Окно параметров сборки в Unity с добавленной сценой и выбранным устройством выполнения](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="fdc5d-136">Если устройство не отображается в раскрывающемся списке Run Device (Запустить устройство), возможно, потребуется нажать кнопку Refresh (Обновить) рядом с раскрывающимся списком.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="fdc5d-137">В окне Build Settings (Параметры сборки) нажмите кнопку **Build And Run** (Сборка и запуск), чтобы открыть окно сборка Android.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="fdc5d-138">Выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_. Присвойте сборке APK понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Save** (Сохранить), чтобы запустить процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном сохранения для Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="fdc5d-140">Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK и JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="fdc5d-141">По завершении сборки приложения должны автоматически загрузиться на устройство Android.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="fdc5d-142">Создание приложения для устройства iOS</span><span class="sxs-lookup"><span data-stu-id="fdc5d-142">Building your application to your iOS device</span></span>

<span data-ttu-id="fdc5d-143">Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве iOS.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="fdc5d-144">В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на iOS.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Окно параметров сборки Unity с выбранным вариантом iOS](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="fdc5d-146">Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="fdc5d-147">Закройте окно Build Settings (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-147">Close the Build Settings window.</span></span>

<span data-ttu-id="fdc5d-148">В меню Unity выберите **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **Configure Project for MRTK** (Настройка проекта для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Окно конфигурации проекта MRTK в Unity для iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="fdc5d-150">В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Снимите флажок **Strip Engine Code** (Удалить код обработчика), чтобы отключить его.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Другие параметры Unity с отключенным параметром Strip Engine Code (Удалить код обработчика)](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="fdc5d-152">Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно **Build Settings** (Параметры сборки).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="fdc5d-153">В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).</span><span class="sxs-lookup"><span data-stu-id="fdc5d-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Окно параметров сборки Unity с добавленной сценой](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="fdc5d-155">В окне Build Settings (Параметры сборки) нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки iOS.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="fdc5d-156">Выберите подходящее расположение для хранения проекта Xcode, например _D:\MixedRealityLearning\Builds_. Создайте папку и присвойте ей понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы начать сборку.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Окно параметров сборки Unity с окном сохранения для iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="fdc5d-158">После сборки выполните инструкции из раздела [Экспорт проект Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы научиться развертывать проекты Xcode на устройствах iOS.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fdc5d-159">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="fdc5d-159">Congratulations</span></span>

<span data-ttu-id="fdc5d-160">Из этого руководства вы узнали, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="fdc5d-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
