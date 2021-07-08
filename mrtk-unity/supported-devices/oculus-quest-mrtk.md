---
title: Развертывание в Oculus Quest
description: Документация по настройке Окулус Quest в МРТК
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, окулус Quest
ms.openlocfilehash: d910f26374b21be26377bd40b9be0d45872e007a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177456"
---
# <a name="deploying-to-oculus-quest"></a><span data-ttu-id="c5481-104">Развертывание в Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="c5481-104">Deploying to Oculus Quest</span></span>

<span data-ttu-id="c5481-105">Требуется [окулусный Quest](https://www.oculus.com/quest/) .</span><span class="sxs-lookup"><span data-stu-id="c5481-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="c5481-106">Поддержка МРТК для Окулус Quest предоставляется через два разных источника: конвейер XR пакета SDK Unity и пакет Unity интеграции Окулус.</span><span class="sxs-lookup"><span data-stu-id="c5481-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="c5481-107">**Поставщик данных Окулус ксрсдк** позволяет использовать оба источника и должен использоваться для развертывания Мртк в Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="c5481-108">[Конвейер пакета SDK для Unity XR](https://docs.unity3d.com/Manual/XR.html) позволяет использовать сенсорные контроллеры Окулус и головное отслеживание с помощью Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="c5481-109">Этот конвейер является стандартом для разработки XR приложений в Unity 2019,3 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="c5481-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="c5481-110">Чтобы использовать этот конвейер, убедитесь, что используется **Unity 2019,3 или более поздней версии**.</span><span class="sxs-lookup"><span data-stu-id="c5481-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="c5481-111">**Это необходимо для развертывания** мртк приложений в Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="c5481-112">[Пакет Unity для интеграции Окулус](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) позволяет использовать **Отслеживание вручную** с помощью Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="c5481-113">Этот поставщик данных **не** использует **конвейер пакета SDK для XR** Unity или **устаревший конвейер XR**.</span><span class="sxs-lookup"><span data-stu-id="c5481-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="c5481-114">Настройка проекта для Окулус Quest</span><span class="sxs-lookup"><span data-stu-id="c5481-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="c5481-115">Выполните следующие [действия](https://developer.oculus.com/documentation/unity/book-unity-gsg/) , чтобы убедиться, что проект готов к развертыванию в Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="c5481-116">Убедитесь, что на устройстве включен [режим разработчика](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) .</span><span class="sxs-lookup"><span data-stu-id="c5481-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="c5481-117">Установка драйверов Окулус ADB является необязательной.</span><span class="sxs-lookup"><span data-stu-id="c5481-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="c5481-118">Настройка конвейера XR SDK для Окулус Quest</span><span class="sxs-lookup"><span data-stu-id="c5481-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="c5481-119">убедитесь, что **подключаемый модуль окулус XR** установлен в разделе **Window--> диспетчер пакетов**</span><span class="sxs-lookup"><span data-stu-id="c5481-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Пакет подключаемого модуля Окулус XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="c5481-121">убедитесь, что поставщик подключаемого модуля окулус включен в проект, выбрав " **изменить"--> Project Параметры--> "управление подключаемыми модулями XR"--> поставщиков подключаемых модулей**</span><span class="sxs-lookup"><span data-stu-id="c5481-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Поставщик подключаемого модуля Окулус](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="c5481-123">Настройка пакета Unity для интеграции Окулус для включения хандтраккинг</span><span class="sxs-lookup"><span data-stu-id="c5481-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="c5481-124">Скачайте и импортируйте [интеграцию Окулус](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) из магазина активов Unity.</span><span class="sxs-lookup"><span data-stu-id="c5481-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="c5481-125">Последняя версия, протестированная на работу, — это 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="c5481-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="c5481-126">Более старые версии можно найти в этом [архиве](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span><span class="sxs-lookup"><span data-stu-id="c5481-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="c5481-127">перейдите в раздел смешанная реальность набор средств > служебные программы > окулус > интеграция модулей Unity для интеграции окулус.</span><span class="sxs-lookup"><span data-stu-id="c5481-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="c5481-128">Это приведет к обновлению асмдефс с определениями и ссылками, необходимыми для работы соответствующего кода Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="c5481-129">Также будет обновлен файл CSC для фильтрации устаревших предупреждений, созданных ресурсами интеграции Окулус.</span><span class="sxs-lookup"><span data-stu-id="c5481-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="c5481-130">Репозиторий МРТК содержит файл CSC, который преобразует предупреждения в ошибки. это преобразование прерывает процесс настройки MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Асмдеф интеграция Окулус](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="c5481-132">В импортированной папке Окулус (она должна быть найдена в Assets/Окулус) имеется объект, поддерживающий скрипт, именуемый Окулуспрожектконфиг.</span><span class="sxs-lookup"><span data-stu-id="c5481-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="c5481-133">В этом файле конфигурации необходимо задать для Хандтраккингсуппорт значение "Controllers and руки".</span><span class="sxs-lookup"><span data-stu-id="c5481-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Контроллер интеграции Окулус и руки](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="c5481-135">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="c5481-135">Setting up the scene</span></span>

1. <span data-ttu-id="c5481-136">Создайте новую сцену или откройте уже существующую сцену, например Хандинтерактионексамплес.</span><span class="sxs-lookup"><span data-stu-id="c5481-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="c5481-137">добавьте мртк в сцену, перейдя к " **смешанная реальность" набор средств**  >  **добавить в сцену и настроить**.</span><span class="sxs-lookup"><span data-stu-id="c5481-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="c5481-138">Использование поставщика данных Окулус XR SDK</span><span class="sxs-lookup"><span data-stu-id="c5481-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="c5481-139">Настройка профиля для использования **поставщика данных Окулус XR SDK**</span><span class="sxs-lookup"><span data-stu-id="c5481-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="c5481-140">Если не планируется изменять профили конфигурации</span><span class="sxs-lookup"><span data-stu-id="c5481-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="c5481-141">Используйте любой из профилей МРТК по умолчанию, которые настроены для всех конвейеров XR Unity.</span><span class="sxs-lookup"><span data-stu-id="c5481-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="c5481-142">Предыдущая Дефаултксрсдкконфигуратионпрофиле теперь помечена как устаревшая.</span><span class="sxs-lookup"><span data-stu-id="c5481-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="c5481-143">Перейдите к разделу [Сборка и развертывание проекта в Окулус Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="c5481-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="c5481-144">В противном случае выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c5481-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="c5481-145">Выберите в иерархии объект Game Микседреалититулкит и выберите **Копировать и настроить** , чтобы клонировать профиль смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c5481-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Клонировать профиль](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="c5481-147">Выберите профиль **входной** конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c5481-147">Select the **Input** Configuration Profile.</span></span>

        ![Профиль входной конфигурации](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="c5481-149">Выберите **клон** во входном системном профиле, чтобы разрешить изменение.</span><span class="sxs-lookup"><span data-stu-id="c5481-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Клонировать входной системный профиль](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="c5481-151">Откройте раздел **поставщики входных данных** , выберите **Добавить поставщик данных** в верхней части, и новый поставщик данных будет добавлен в конец списка.</span><span class="sxs-lookup"><span data-stu-id="c5481-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="c5481-152">откройте новый поставщик данных и задайте для него **тип** **Microsoft. микседреалити. набор средств. КСРСДК. Окулус > Окулусксрсдкдевицеманажер**.</span><span class="sxs-lookup"><span data-stu-id="c5481-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Окулус добавить поставщик данных КСРСДК](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="c5481-154">Настройка профиля для использования **поставщика данных Окулус XR SDK**</span><span class="sxs-lookup"><span data-stu-id="c5481-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="c5481-155">Если не планируется изменять профили конфигурации</span><span class="sxs-lookup"><span data-stu-id="c5481-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="c5481-156">Измените профиль на Дефаултксрсдкконфигуратионпрофиле.</span><span class="sxs-lookup"><span data-stu-id="c5481-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="c5481-157">Перейдите к разделу [Сборка и развертывание проекта в Окулус Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="c5481-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="c5481-158">В противном случае выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c5481-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="c5481-159">Выберите в иерархии объект Game Микседреалититулкит и выберите **Копировать и настроить** , чтобы клонировать профиль смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c5481-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Клонировать профиль](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="c5481-161">Выберите профиль **входной** конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c5481-161">Select the **Input** Configuration Profile.</span></span>

        ![Профиль входной конфигурации](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="c5481-163">Выберите **клон** во входном системном профиле, чтобы разрешить изменение.</span><span class="sxs-lookup"><span data-stu-id="c5481-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Клонировать входной системный профиль](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="c5481-165">Откройте раздел **поставщики входных данных** , выберите **Добавить поставщик данных** в верхней части, и новый поставщик данных будет добавлен в конец списка.</span><span class="sxs-lookup"><span data-stu-id="c5481-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="c5481-166">откройте новый поставщик данных и задайте для него **тип** **Microsoft. микседреалити. набор средств. КСРСДК. Окулус > Окулусксрсдкдевицеманажер**.</span><span class="sxs-lookup"><span data-stu-id="c5481-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Окулус добавить поставщик данных КСРСДК](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="c5481-168">Поставщик данных Окулус XR SDK включает в себя ОВРную платформу камеры, prefab которая автоматически настраивает проект с помощью платформы ОВР Camera и ОВР для правильного направления входных данных.</span><span class="sxs-lookup"><span data-stu-id="c5481-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="c5481-169">Чтобы вручную добавить на сцену платформу камеры ОВР, потребуется настройка параметров и входных данных вручную.</span><span class="sxs-lookup"><span data-stu-id="c5481-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="c5481-170">Создание и развертывание проекта в Окулус Quest</span><span class="sxs-lookup"><span data-stu-id="c5481-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="c5481-171">Подключайте свой Окулусный Quest через 3,0 USB-> USB с кабелем</span><span class="sxs-lookup"><span data-stu-id="c5481-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="c5481-172">выберите **файл > сборка Параметры**</span><span class="sxs-lookup"><span data-stu-id="c5481-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="c5481-173">Изменение развертывания на **Android**</span><span class="sxs-lookup"><span data-stu-id="c5481-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="c5481-174">Убедитесь, что в качестве подходящего устройства запуска выбран Окулус Quest.</span><span class="sxs-lookup"><span data-stu-id="c5481-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Окулус запустить устройство](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="c5481-176">Выбор сборки и запуска</span><span class="sxs-lookup"><span data-stu-id="c5481-176">Select Build and Run</span></span>
    - <span data-ttu-id="c5481-177">При выборе *сборки и запуска* в первый раз, скорее всего, будет появляться следующий набор ошибок сборки.</span><span class="sxs-lookup"><span data-stu-id="c5481-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="c5481-178">Вы можете успешно выполнить развертывание после выбора *сборки и запуска* .</span><span class="sxs-lookup"><span data-stu-id="c5481-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Окулус ожидаемые ошибки сборки](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="c5481-180">Принятие запроса на _отладку по USB-порту_ в приглашении</span><span class="sxs-lookup"><span data-stu-id="c5481-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="c5481-181">Просмотр сцены в Окулус Quest</span><span class="sxs-lookup"><span data-stu-id="c5481-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="c5481-182">Удаление интеграции Окулус из Project</span><span class="sxs-lookup"><span data-stu-id="c5481-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="c5481-183">перейдите к набор средств смешанной реальности > окулус > отдельных модулей Unity окулус Integration ![ окулус разделение асмдеф](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="c5481-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="c5481-184">Разрешить обновление Unity в виде ссылок в Microsoft. Микседреалити. набор средств. На этом шаге изменяются поставщики. Окулус. асмдеф и другие файлы.</span><span class="sxs-lookup"><span data-stu-id="c5481-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="c5481-185">Закрыть Unity</span><span class="sxs-lookup"><span data-stu-id="c5481-185">Close Unity</span></span>
1. <span data-ttu-id="c5481-186">закрыть Visual Studio, если он открыт</span><span class="sxs-lookup"><span data-stu-id="c5481-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="c5481-187">Откройте проводник и перейдите к корню проекта Unity МРТК.</span><span class="sxs-lookup"><span data-stu-id="c5481-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="c5481-188">Удаление каталога Унитипрожектнаме/Library</span><span class="sxs-lookup"><span data-stu-id="c5481-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="c5481-189">Удаление каталога Унитипрожектнаме/Assets/Окулус</span><span class="sxs-lookup"><span data-stu-id="c5481-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="c5481-190">Удаление файла Унитипрожектнаме/Assets/Окулус. meta</span><span class="sxs-lookup"><span data-stu-id="c5481-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="c5481-191">Повторное открытие Unity</span><span class="sxs-lookup"><span data-stu-id="c5481-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="c5481-192">Распространенные ошибки</span><span class="sxs-lookup"><span data-stu-id="c5481-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="c5481-193">Не удается распознать поручение Unity</span><span class="sxs-lookup"><span data-stu-id="c5481-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="c5481-194">Убедитесь, что правильно настроены пути Android.</span><span class="sxs-lookup"><span data-stu-id="c5481-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="c5481-195">Если проблемы продолжают возникать, [следуйте указаниям в этом разделе](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools) .</span><span class="sxs-lookup"><span data-stu-id="c5481-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="c5481-196">**Изменение настроек > > внешних инструментов > Android**</span><span class="sxs-lookup"><span data-stu-id="c5481-196">**Edit > Preferences > External Tools > Android**</span></span>

![Конфигурация инструментов Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)