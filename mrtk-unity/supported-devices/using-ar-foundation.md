---
title: усингарфаундатион
description: Документация по использованию Арфаундатион в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, AR Core, AR Kit
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852432"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="9c7f8-104">Настройка МРТК для iOS и Android [экспериментальная версия]</span><span class="sxs-lookup"><span data-stu-id="9c7f8-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="9c7f8-105">Установка необходимых пакетов</span><span class="sxs-lookup"><span data-stu-id="9c7f8-105">Install required packages</span></span>

1. <span data-ttu-id="9c7f8-106">Скачайте и импортируйте пакет **Microsoft. микседреалити. Toolkit. Unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) или [диспетчера пакетов Unity](../configuration/usingupm.md) .</span><span class="sxs-lookup"><span data-stu-id="9c7f8-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="9c7f8-107">В диспетчере пакетов Unity (УПМ) установите следующие пакеты:</span><span class="sxs-lookup"><span data-stu-id="9c7f8-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="9c7f8-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="9c7f8-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-109">**Android**</span></span> | <span data-ttu-id="9c7f8-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-110">**iOS**</span></span> | <span data-ttu-id="9c7f8-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="9c7f8-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="9c7f8-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-112">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-113">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="9c7f8-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="9c7f8-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-114">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-115">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="9c7f8-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="9c7f8-116">Для Unity 2018,4 этот пакет включен в качестве предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="9c7f8-117">Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="9c7f8-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="9c7f8-118">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-119">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="9c7f8-119">Version: 2.1.2</span></span> | <span data-ttu-id="9c7f8-120">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-121">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="9c7f8-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="9c7f8-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="9c7f8-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-123">**Android**</span></span> | <span data-ttu-id="9c7f8-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="9c7f8-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-125">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-126">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="9c7f8-126">Version: 2.1.8</span></span> |  <span data-ttu-id="9c7f8-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-127">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-128">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="9c7f8-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="9c7f8-129">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-130">Версия: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="9c7f8-130">Version: 2.1.11</span></span> | <span data-ttu-id="9c7f8-131">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-132">Версия: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="9c7f8-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="9c7f8-133">**Unity 2020.1. x (в настоящее время не формально поддерживается), включается только в информационных целях.**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="9c7f8-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-134">**Android**</span></span> | <span data-ttu-id="9c7f8-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="9c7f8-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-136">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-137">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="9c7f8-137">Version: 3.1.3</span></span> |  <span data-ttu-id="9c7f8-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9c7f8-138">AR Foundation</span></span>  <br/> <span data-ttu-id="9c7f8-139">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="9c7f8-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="9c7f8-140">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-141">Версия: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="9c7f8-141">Version: 3.1.4</span></span> | <span data-ttu-id="9c7f8-142">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="9c7f8-143">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="9c7f8-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="9c7f8-144">Обновите скрипты МРТК Унитяр, вызвав пункт меню: **Mixed Reality Toolkit > служебные программы > унитяр > определения сценариев обновления**</span><span class="sxs-lookup"><span data-stu-id="9c7f8-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="9c7f8-145">Включение поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="9c7f8-146">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="9c7f8-147">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="9c7f8-148">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="9c7f8-150">Выберите **Копировать и настроить** , чтобы КЛОНИРОВАТЬ профиль мртк, чтобы включить настраиваемую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Клонировать профиль МРТК](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="9c7f8-152">Выберите **клонировать** рядом с профилем камеры.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Клонировать профиль камеры МРТК](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="9c7f8-154">Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="9c7f8-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Разверните узел Параметры поставщики.](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="9c7f8-156">Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="9c7f8-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Развернуть поставщик новых параметров](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="9c7f8-158">Выбор поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-158">Select the Unity AR Camera Settings provider</span></span>

    ![Выбор поставщика параметров Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="9c7f8-160">Дополнительные сведения о настройке поставщика параметров Unity AR для камеры см. в статье [поставщик параметров камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9c7f8-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9c7f8-161">Эта установка проверяет (при запуске приложения), если компоненты AR Foundation находятся в сцене.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="9c7f8-162">В противном случае они добавляются автоматически, чтобы обеспечить работу с Аркоре и ARKit.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="9c7f8-163">Если необходимо задать конкретное поведение, необходимо добавить необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="9c7f8-164">Дополнительные сведения о компонентах и установке AR Foundation см. в этой [документации](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="9c7f8-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="9c7f8-165">Создание сцены для устройств Android и iOS</span><span class="sxs-lookup"><span data-stu-id="9c7f8-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="9c7f8-166">Убедитесь, что в сцену добавлен поставщик параметров камеры Унитяр.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="9c7f8-167">Переключение платформы на Android или iOS в параметрах сборки Unity</span><span class="sxs-lookup"><span data-stu-id="9c7f8-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="9c7f8-168">При переключении платформы вы увидите окно конфигуратора проектов МРТК с параметрами для выбранной платформы.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="9c7f8-169">Нажмите кнопку Применить, чтобы включить параметры, зависящие от платформы.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="9c7f8-170">Параметры конфигуратора проектов iOS</span><span class="sxs-lookup"><span data-stu-id="9c7f8-170">iOS Project Configurator Settings</span></span>

    ![Конфигуратор проектов iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="9c7f8-172">После переключения платформы для Android дополнительные действия не выполняются.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="9c7f8-173">Если платформа является iOS, измените параметры > проекта > проигрыватель > другие параметры в заголовке оптимизации, **снимите флажок** код обработчика полосковых систем.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Параметры iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="9c7f8-175">Непроверяемый код механизма полоскового ядра — это краткосрочное решение ошибки в Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="9c7f8-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="9c7f8-176">Мы работаем над долгосрочным решением.</span><span class="sxs-lookup"><span data-stu-id="9c7f8-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="9c7f8-177">Сборка и запуск сцены</span><span class="sxs-lookup"><span data-stu-id="9c7f8-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="9c7f8-178">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9c7f8-178">See also</span></span>

- [<span data-ttu-id="9c7f8-179">Параметры камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="9c7f8-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
