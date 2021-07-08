---
title: Создание и развертывание в Android и iOS с помощью AR Foundation
description: Документация по настройке МРТК для Android и iOS (Арфаундатион) в Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449743"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a><span data-ttu-id="65caa-104">Создание и развертывание в Android и iOS с помощью AR Foundation [экспериментальная версия]</span><span class="sxs-lookup"><span data-stu-id="65caa-104">Building and Deploying to Android and iOS via AR Foundation [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="65caa-105">Установка необходимых пакетов</span><span class="sxs-lookup"><span data-stu-id="65caa-105">Install required packages</span></span>

1. <span data-ttu-id="65caa-106">Скачайте и импортируйте пакет **Microsoft. микседреалити. Toolkit. Unity. Foundation** из [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) или [диспетчера пакетов Unity](../configuration/usingupm.md) .</span><span class="sxs-lookup"><span data-stu-id="65caa-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="65caa-107">В диспетчере пакетов Unity (УПМ) установите следующие пакеты:</span><span class="sxs-lookup"><span data-stu-id="65caa-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="65caa-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="65caa-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="65caa-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="65caa-109">**Android**</span></span> | <span data-ttu-id="65caa-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="65caa-110">**iOS**</span></span> | <span data-ttu-id="65caa-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="65caa-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="65caa-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-112">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-113">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="65caa-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="65caa-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-114">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-115">Версия: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="65caa-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="65caa-116">Для Unity 2018,4 этот пакет включен в качестве предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="65caa-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="65caa-117">Чтобы просмотреть пакет, выполните следующие действия. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="65caa-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="65caa-118">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="65caa-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="65caa-119">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="65caa-119">Version: 2.1.2</span></span> | <span data-ttu-id="65caa-120">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="65caa-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="65caa-121">Версия: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="65caa-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="65caa-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="65caa-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="65caa-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="65caa-123">**Android**</span></span> | <span data-ttu-id="65caa-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="65caa-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="65caa-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-125">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-126">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="65caa-126">Version: 2.1.8</span></span> |  <span data-ttu-id="65caa-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-127">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-128">Версия: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="65caa-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="65caa-129">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="65caa-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="65caa-130">Версия: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="65caa-130">Version: 2.1.11</span></span> | <span data-ttu-id="65caa-131">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="65caa-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="65caa-132">Версия: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="65caa-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="65caa-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="65caa-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="65caa-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="65caa-134">**Android**</span></span> | <span data-ttu-id="65caa-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="65caa-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="65caa-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-136">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-137">Версия: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="65caa-137">Version: 3.1.3</span></span> |  <span data-ttu-id="65caa-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="65caa-138">AR Foundation</span></span>  <br/> <span data-ttu-id="65caa-139">Версия: 4.0.12</span><span class="sxs-lookup"><span data-stu-id="65caa-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="65caa-140">Подключаемый модуль Аркоре XR</span><span class="sxs-lookup"><span data-stu-id="65caa-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="65caa-141">Версия: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="65caa-141">Version: 3.1.4</span></span> | <span data-ttu-id="65caa-142">Подключаемый модуль ARKit XR</span><span class="sxs-lookup"><span data-stu-id="65caa-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="65caa-143">Версия: 4.1.7</span><span class="sxs-lookup"><span data-stu-id="65caa-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="65caa-144">Обновление скриптов МРТК Унитяр определяется путем вызова пункта меню: " **Смешанная реальность > набор средств > служебные программы > унитяр > обновление сценариев** "</span><span class="sxs-lookup"><span data-stu-id="65caa-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Обновление определений скриптов](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="65caa-146">Включение поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="65caa-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="65caa-147">В следующих шагах предполагается использование объекта Микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="65caa-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="65caa-148">Действия, необходимые для других регистраторов служб, могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="65caa-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="65caa-149">Выберите объект Микседреалититулкит в иерархии сцены.</span><span class="sxs-lookup"><span data-stu-id="65caa-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![МРТК настроенная иерархия сцены](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="65caa-151">Выберите **Копировать и настроить** , чтобы КЛОНИРОВАТЬ профиль мртк, чтобы включить настраиваемую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="65caa-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Клонировать профиль МРТК](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="65caa-153">Выберите **клонировать** рядом с профилем камеры.</span><span class="sxs-lookup"><span data-stu-id="65caa-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Клонировать профиль камеры МРТК](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="65caa-155">Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="65caa-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Разверните узел Параметры поставщики.](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="65caa-157">Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .</span><span class="sxs-lookup"><span data-stu-id="65caa-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Развернуть поставщик новых параметров](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="65caa-159">Выбор поставщика параметров для камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="65caa-159">Select the Unity AR Camera Settings provider</span></span>

    ![Выбор поставщика параметров Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="65caa-161">Дополнительные сведения о настройке поставщика параметров Unity AR для камеры см. в статье [поставщик параметров камеры Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="65caa-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="65caa-162">Эта установка проверяет (при запуске приложения), если компоненты AR Foundation находятся в сцене.</span><span class="sxs-lookup"><span data-stu-id="65caa-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="65caa-163">В противном случае они добавляются автоматически, чтобы обеспечить работу с Аркоре и ARKit.</span><span class="sxs-lookup"><span data-stu-id="65caa-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="65caa-164">Если необходимо задать конкретное поведение, необходимо добавить необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="65caa-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="65caa-165">Дополнительные сведения о компонентах и установке AR Foundation см. в этой [документации](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="65caa-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="65caa-166">Создание сцены для устройств Android и iOS</span><span class="sxs-lookup"><span data-stu-id="65caa-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="65caa-167">Убедитесь, что в сцену добавлен поставщик параметров камеры Унитяр.</span><span class="sxs-lookup"><span data-stu-id="65caa-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="65caa-168">Переключение платформы на Android или iOS в параметрах сборки Unity</span><span class="sxs-lookup"><span data-stu-id="65caa-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="65caa-169">Убедитесь, что связанный поставщик управления подключаемым модулем XR включен.</span><span class="sxs-lookup"><span data-stu-id="65caa-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="65caa-170">Управление подключаемыми модулями iOS XR:  ![ Управление подключаемыми модулями XR iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="65caa-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="65caa-171">Сборка и запуск сцены</span><span class="sxs-lookup"><span data-stu-id="65caa-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="65caa-172">См. также</span><span class="sxs-lookup"><span data-stu-id="65caa-172">See also</span></span>

- [<span data-ttu-id="65caa-173">Параметры камеры Unity AR</span><span class="sxs-lookup"><span data-stu-id="65caa-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)