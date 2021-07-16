---
title: Развертывание в Android и iOS (AR Foundation) [экспериментальная версия]
description: Документация по настройке МРТК для Android и iOS (Арфаундатион) в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, ar Core, ar Kit, ios, ios, Android, ar Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281948"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a><span data-ttu-id="f6ced-104">Развертывание в Android и iOS (AR Foundation) [экспериментальная версия]</span><span class="sxs-lookup"><span data-stu-id="f6ced-104">Deploying to Android and iOS (AR Foundation) [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="f6ced-105">Установка необходимых пакетов</span><span class="sxs-lookup"><span data-stu-id="f6ced-105">Install required packages</span></span>

1. <span data-ttu-id="f6ced-106">скачайте и импортируйте файл **Microsoft. микседреалити. набор средств. пакет unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) или [Unity диспетчер пакетов](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="f6ced-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="f6ced-107">в диспетчер пакетов Unity (упм) установите следующие пакеты:</span><span class="sxs-lookup"><span data-stu-id="f6ced-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="f6ced-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="f6ced-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="f6ced-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="f6ced-109">**Android**</span></span> | <span data-ttu-id="f6ced-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f6ced-110">**iOS**</span></span> | <span data-ttu-id="f6ced-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="f6ced-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="f6ced-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-112">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-113">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="f6ced-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="f6ced-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-114">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-115">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="f6ced-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="f6ced-116">Для Unity 2018,4 этот пакет включен в качестве предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="f6ced-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="f6ced-117">Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="f6ced-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="f6ced-118">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-119">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="f6ced-119">Version: 2.1.2</span></span> | <span data-ttu-id="f6ced-120">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-121">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="f6ced-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="f6ced-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="f6ced-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="f6ced-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="f6ced-123">**Android**</span></span> | <span data-ttu-id="f6ced-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f6ced-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="f6ced-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-125">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-126">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="f6ced-126">Version: 2.1.8</span></span> |  <span data-ttu-id="f6ced-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-127">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-128">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="f6ced-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="f6ced-129">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-130">Версия: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="f6ced-130">Version: 2.1.11</span></span> | <span data-ttu-id="f6ced-131">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-132">Версия: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="f6ced-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="f6ced-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="f6ced-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="f6ced-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="f6ced-134">**Android**</span></span> | <span data-ttu-id="f6ced-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="f6ced-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="f6ced-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-136">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-137">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="f6ced-137">Version: 3.1.3</span></span> |  <span data-ttu-id="f6ced-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="f6ced-138">AR Foundation</span></span>  <br/> <span data-ttu-id="f6ced-139">Версия: 4.0.12</span><span class="sxs-lookup"><span data-stu-id="f6ced-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="f6ced-140">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-141">Версия: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="f6ced-141">Version: 3.1.4</span></span> | <span data-ttu-id="f6ced-142">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="f6ced-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="f6ced-143">Версия: 4.1.7</span><span class="sxs-lookup"><span data-stu-id="f6ced-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="f6ced-144">обновление скриптов мртк унитяр определяется путем вызова пункта меню: **Mixed Reality > набор средств > служебные программы > унитяр > определения сценариев обновления**</span><span class="sxs-lookup"><span data-stu-id="f6ced-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Обновление определений скриптов](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="f6ced-146">Включение поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="f6ced-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="f6ced-147">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="f6ced-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="f6ced-148">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="f6ced-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="f6ced-149">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="f6ced-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="f6ced-151">Выберите **Копировать и настроить** , чтобы КЛОНИРОВАТЬ профиль мртк, чтобы включить настраиваемую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="f6ced-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Клонировать профиль МРТК](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="f6ced-153">Выберите **клонировать** рядом с профилем камеры.</span><span class="sxs-lookup"><span data-stu-id="f6ced-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Клонировать профиль камеры МРТК](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="f6ced-155">перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики Параметры камеры** .</span><span class="sxs-lookup"><span data-stu-id="f6ced-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Разверните узел Параметры поставщики.](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="f6ced-157">щелкните **добавить камера Параметры поставщик** и разверните добавленную **новую запись параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="f6ced-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Развернуть поставщик новых параметров](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="f6ced-159">выбор поставщика Параметры Unity AR Camera</span><span class="sxs-lookup"><span data-stu-id="f6ced-159">Select the Unity AR Camera Settings provider</span></span>

    ![Выбор поставщика параметров Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="f6ced-161">Дополнительные сведения о настройке поставщика параметров Unity AR для камеры см. в статье [поставщик параметров камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f6ced-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f6ced-162">Эта установка проверяет (при запуске приложения), если компоненты AR Foundation находятся в сцене.</span><span class="sxs-lookup"><span data-stu-id="f6ced-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="f6ced-163">В противном случае они добавляются автоматически, чтобы обеспечить работу с Аркоре и ARKit.</span><span class="sxs-lookup"><span data-stu-id="f6ced-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="f6ced-164">Если необходимо задать конкретное поведение, необходимо добавить необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="f6ced-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="f6ced-165">Дополнительные сведения о компонентах и установке AR Foundation см. в этой [документации](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="f6ced-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="f6ced-166">Создание сцены для устройств Android и iOS</span><span class="sxs-lookup"><span data-stu-id="f6ced-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="f6ced-167">убедитесь, что в сцену добавлен поставщик Параметры камеры унитяр.</span><span class="sxs-lookup"><span data-stu-id="f6ced-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="f6ced-168">переключение платформы на Android или iOS в сборке Unity Параметры</span><span class="sxs-lookup"><span data-stu-id="f6ced-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="f6ced-169">Убедитесь, что связанный поставщик управления подключаемым модулем XR включен.</span><span class="sxs-lookup"><span data-stu-id="f6ced-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="f6ced-170">Управление подключаемыми модулями iOS XR:  ![ Управление подключаемыми модулями XR iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="f6ced-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="f6ced-171">Сборка и запуск сцены</span><span class="sxs-lookup"><span data-stu-id="f6ced-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="f6ced-172">См. также</span><span class="sxs-lookup"><span data-stu-id="f6ced-172">See also</span></span>

- [<span data-ttu-id="f6ced-173">Параметры камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="f6ced-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
