---
title: Использование AR Foundation
description: Документация по использованию Арфаундатион в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, AR Core, AR Kit
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143942"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="376bb-104">Настройка МРТК для iOS и Android [экспериментальная версия]</span><span class="sxs-lookup"><span data-stu-id="376bb-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="376bb-105">Установка необходимых пакетов</span><span class="sxs-lookup"><span data-stu-id="376bb-105">Install required packages</span></span>

1. <span data-ttu-id="376bb-106">Скачайте и импортируйте пакет **Microsoft. микседреалити. Toolkit. Unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) или [диспетчера пакетов Unity](../configuration/usingupm.md) .</span><span class="sxs-lookup"><span data-stu-id="376bb-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="376bb-107">В диспетчере пакетов Unity (УПМ) установите следующие пакеты:</span><span class="sxs-lookup"><span data-stu-id="376bb-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="376bb-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="376bb-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="376bb-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="376bb-109">**Android**</span></span> | <span data-ttu-id="376bb-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="376bb-110">**iOS**</span></span> | <span data-ttu-id="376bb-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="376bb-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="376bb-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-112">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-113">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="376bb-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="376bb-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-114">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-115">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="376bb-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="376bb-116">Для Unity 2018,4 этот пакет включен в качестве предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="376bb-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="376bb-117">Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="376bb-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="376bb-118">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="376bb-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="376bb-119">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="376bb-119">Version: 2.1.2</span></span> | <span data-ttu-id="376bb-120">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="376bb-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="376bb-121">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="376bb-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="376bb-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="376bb-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="376bb-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="376bb-123">**Android**</span></span> | <span data-ttu-id="376bb-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="376bb-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="376bb-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-125">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-126">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="376bb-126">Version: 2.1.8</span></span> |  <span data-ttu-id="376bb-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-127">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-128">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="376bb-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="376bb-129">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="376bb-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="376bb-130">Версия: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="376bb-130">Version: 2.1.11</span></span> | <span data-ttu-id="376bb-131">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="376bb-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="376bb-132">Версия: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="376bb-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="376bb-133">**Unity 2020.1. x (в настоящее время не формально поддерживается), включается только в информационных целях.**</span><span class="sxs-lookup"><span data-stu-id="376bb-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="376bb-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="376bb-134">**Android**</span></span> | <span data-ttu-id="376bb-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="376bb-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="376bb-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-136">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-137">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="376bb-137">Version: 3.1.3</span></span> |  <span data-ttu-id="376bb-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="376bb-138">AR Foundation</span></span>  <br/> <span data-ttu-id="376bb-139">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="376bb-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="376bb-140">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="376bb-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="376bb-141">Версия: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="376bb-141">Version: 3.1.4</span></span> | <span data-ttu-id="376bb-142">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="376bb-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="376bb-143">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="376bb-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="376bb-144">Обновите скрипты МРТК Унитяр, вызвав пункт меню: **Mixed Reality Toolkit > служебные программы > унитяр > определения сценариев обновления**</span><span class="sxs-lookup"><span data-stu-id="376bb-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="376bb-145">Включение поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="376bb-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="376bb-146">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="376bb-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="376bb-147">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="376bb-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="376bb-148">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="376bb-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="376bb-150">Выберите **Копировать и настроить** , чтобы КЛОНИРОВАТЬ профиль мртк, чтобы включить настраиваемую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="376bb-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Клонировать профиль МРТК](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="376bb-152">Выберите **клонировать** рядом с профилем камеры.</span><span class="sxs-lookup"><span data-stu-id="376bb-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Клонировать профиль камеры МРТК](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="376bb-154">Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="376bb-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Разверните узел Параметры поставщики.](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="376bb-156">Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="376bb-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Развернуть поставщик новых параметров](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="376bb-158">Выбор поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="376bb-158">Select the Unity AR Camera Settings provider</span></span>

    ![Выбор поставщика параметров Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="376bb-160">Дополнительные сведения о настройке поставщика параметров Unity AR для камеры см. в статье [поставщик параметров камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="376bb-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="376bb-161">Эта установка проверяет (при запуске приложения), если компоненты AR Foundation находятся в сцене.</span><span class="sxs-lookup"><span data-stu-id="376bb-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="376bb-162">В противном случае они добавляются автоматически, чтобы обеспечить работу с Аркоре и ARKit.</span><span class="sxs-lookup"><span data-stu-id="376bb-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="376bb-163">Если необходимо задать конкретное поведение, необходимо добавить необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="376bb-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="376bb-164">Дополнительные сведения о компонентах и установке AR Foundation см. в этой [документации](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="376bb-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="376bb-165">Создание сцены для устройств Android и iOS</span><span class="sxs-lookup"><span data-stu-id="376bb-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="376bb-166">Убедитесь, что в сцену добавлен поставщик параметров камеры Унитяр.</span><span class="sxs-lookup"><span data-stu-id="376bb-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="376bb-167">Переключение платформы на Android или iOS в параметрах сборки Unity</span><span class="sxs-lookup"><span data-stu-id="376bb-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="376bb-168">При переключении платформы вы увидите окно конфигуратора проектов МРТК с параметрами для выбранной платформы.</span><span class="sxs-lookup"><span data-stu-id="376bb-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="376bb-169">Нажмите кнопку Применить, чтобы включить параметры, зависящие от платформы.</span><span class="sxs-lookup"><span data-stu-id="376bb-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="376bb-170">Параметры конфигуратора проектов iOS</span><span class="sxs-lookup"><span data-stu-id="376bb-170">iOS Project Configurator Settings</span></span>

    ![Конфигуратор проектов iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="376bb-172">После переключения платформы для Android дополнительные действия не выполняются.</span><span class="sxs-lookup"><span data-stu-id="376bb-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="376bb-173">Если платформа является iOS, измените параметры > проекта > проигрыватель > другие параметры в заголовке оптимизации, **снимите флажок** код обработчика полосковых систем.</span><span class="sxs-lookup"><span data-stu-id="376bb-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Параметры iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="376bb-175">Непроверяемый код механизма полоскового ядра — это краткосрочное решение ошибки в Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="376bb-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="376bb-176">Мы работаем над долгосрочным решением.</span><span class="sxs-lookup"><span data-stu-id="376bb-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="376bb-177">Сборка и запуск сцены</span><span class="sxs-lookup"><span data-stu-id="376bb-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="376bb-178">См. также</span><span class="sxs-lookup"><span data-stu-id="376bb-178">See also</span></span>

- [<span data-ttu-id="376bb-179">Параметры камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="376bb-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
