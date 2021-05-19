---
title: Отслеживание взгляда — базовая настройка
description: Как настроить отслеживание взглядов в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, отслеживание глаз,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144091"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="3f8ec-104">Приступая к работе с отслеживанием взгляда в МРТК</span><span class="sxs-lookup"><span data-stu-id="3f8ec-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="3f8ec-105">На этой странице описано, как настроить сцену МРТК для Unity для использования отслеживания взгляда в приложении.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="3f8ec-106">В следующем примере предполагается, что вы начинаете с новой сцены.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="3f8ec-107">Кроме того, вы можете просмотреть уже настроенные [примеры отслеживания мрткных глаз](../../example-scenes/eye-tracking-examples-overview.md) с помощью тонн с превосходными примерами, которые можно создавать напрямую.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="3f8ec-108">Контрольный список требований к отслеживанию глаз</span><span class="sxs-lookup"><span data-stu-id="3f8ec-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="3f8ec-109">Чтобы отслеживание взгляда работало правильно, должны выполняться следующие требования.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="3f8ec-110">Если вы не знакомы с отслеживанием взгляда на HoloLens 2 и в МРТК, не беспокойтесь!</span><span class="sxs-lookup"><span data-stu-id="3f8ec-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="3f8ec-111">Мы подробно рассмотрим, как устранить эти шаги ниже.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="3f8ec-112">В систему ввода должен быть добавлен _"поставщик данных_ с взглядом на глаза".</span><span class="sxs-lookup"><span data-stu-id="3f8ec-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="3f8ec-113">Это предоставляет данные отслеживания взгляда с платформы.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="3f8ec-114">Возможность _"газеинпут"_ должна быть включена в манифесте приложения.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="3f8ec-115">**Эта возможность может быть задана в Unity 2019, но в Unity 2018 и более ранних версиях эта возможность доступна только в Visual Studio и с помощью средства сборки МРТК.**</span><span class="sxs-lookup"><span data-stu-id="3f8ec-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="3f8ec-116">Для текущего пользователя HoloLens **должен** быть калибровкой.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="3f8ec-117">Ознакомьтесь с нашим [образцом, чтобы определить, является ли пользователь откалиброванным глазом](eye-tracking-is-user-calibrated.md).</span><span class="sxs-lookup"><span data-stu-id="3f8ec-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="3f8ec-118">Примечание о возможности Газеинпут</span><span class="sxs-lookup"><span data-stu-id="3f8ec-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="3f8ec-119">Предоставляемые МРТК средства сборки (т. е. набор средств для смешанной реальности, > служебные программы — > сборка) могут автоматически включить возможность Газеинпут.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="3f8ec-120">Для этого необходимо убедиться, что на вкладке "параметры сборки appx" установлен флажок "возможность ввода с клавиатуры".</span><span class="sxs-lookup"><span data-stu-id="3f8ec-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Средства сборки МРТК](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="3f8ec-122">Это средство обнаружит манифест AppX после завершения сборки Unity и добавит функцию Газеинпут вручную.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="3f8ec-123">**До Unity 2019 эта программа неактивна при использовании встроенного окна сборки Unity** (т. е. параметров сборки > файлов).</span><span class="sxs-lookup"><span data-stu-id="3f8ec-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="3f8ec-124">До Unity 2019 при использовании окна сборки Unity эту возможность потребуется вручную добавить после сборки Unity следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3f8ec-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="3f8ec-125">Откройте скомпилированный проект Visual Studio, а затем откройте в решении _"Package. appxmanifest"_ .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="3f8ec-126">Установите флажок _"газеинпут"_ в разделе " _возможности_".</span><span class="sxs-lookup"><span data-stu-id="3f8ec-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="3f8ec-127">Если вы не видите возможность _"газеинпут"_ , убедитесь, что ваша система соответствует [предварительным требованиям для использования мртк](/windows/mixed-reality/develop/install-the-tools) (в частности Windows SDK версии).</span><span class="sxs-lookup"><span data-stu-id="3f8ec-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="3f8ec-128">_Примечание._ Это необходимо сделать только в том случае, если сборка выполняется в новую папку сборки.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="3f8ec-129">Это означает, что если вы уже создали проект Unity и настроили appxmanifest до и теперь нацелить эту же папку, вам не потребуется повторно применять изменения.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="3f8ec-130">Пошаговая настройка отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="3f8ec-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="3f8ec-131">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="3f8ec-131">Setting up the scene</span></span>

<span data-ttu-id="3f8ec-132">Настройте _микседреалититулкит_ , просто щелкнув _"набор средств" Mixed Reality "— > configure..."_</span><span class="sxs-lookup"><span data-stu-id="3f8ec-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="3f8ec-133">в строке меню.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-133">in the menu bar.</span></span>

![Настройка МРТК](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="3f8ec-135">Настройка профилей МРТК, необходимых для отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="3f8ec-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="3f8ec-136">После настройки сцены МРТК вам будет предложено выбрать профиль для МРТК.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="3f8ec-137">Можно просто выбрать _дефаултмикседреалититулкитконфигуратионпрофиле_ , а затем выбрать параметр _"Копировать & настройку"_ .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Профиль МРТК](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="3f8ec-139">Создание поставщика данных "взгляд глаз"</span><span class="sxs-lookup"><span data-stu-id="3f8ec-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="3f8ec-140">Щелкните вкладку _"вход"_ в профиле мртк.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="3f8ec-141">Чтобы изменить значение по умолчанию ( _"дефаултмикседреалитинпутсистемпрофиле"_ ), нажмите кнопку _"клонировать"_ рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="3f8ec-142">Откроется меню _"профиль клона"_ .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="3f8ec-143">Просто щелкните _клон_ в нижней части этого меню.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="3f8ec-144">Дважды щелкните новый входной профиль, разверните узел _"входные поставщики данных"_ и выберите _"+ добавить поставщик данных"_.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="3f8ec-145">Создать новый поставщик данных:</span><span class="sxs-lookup"><span data-stu-id="3f8ec-145">Create a new data provider:</span></span>
  - <span data-ttu-id="3f8ec-146">В разделе **тип** выберите _Microsoft. микседреалити. Toolkit. виндовсмикседреалити. Input '_  ->  _' виндовсмикседреалитеегазедатапровидер '_</span><span class="sxs-lookup"><span data-stu-id="3f8ec-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="3f8ec-147">Для **платформ** выберите _"универсальная платформа Windows"_.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Поставщик данных МРТК](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="3f8ec-149">Имитация отслеживания взгляда в редакторе Unity</span><span class="sxs-lookup"><span data-stu-id="3f8ec-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="3f8ec-150">Вы можете имитировать входные данные отслеживания взгляда в редакторе Unity, чтобы обеспечить правильную активацию событий до развертывания приложения в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="3f8ec-151">Сигнал взгляда глаза имитируется путем простого использования расположения камеры в качестве источника глаза и вектора перенаправления камеры в качестве направления взгляда.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="3f8ec-152">Хотя это отлично подходит для первоначального тестирования, обратите внимание, что он не является хорошим имитацией для быстрого перемещения глаз.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="3f8ec-153">Для этого лучше обеспечить частые тесты взаимодействий на основе класса HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="3f8ec-154">**Включить имитацию отслеживания взгляда**:</span><span class="sxs-lookup"><span data-stu-id="3f8ec-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="3f8ec-155">Щелкните вкладку _"вход"_ в профиле конфигурации мртк.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="3f8ec-156">После этого перейдите к пункту "входные _поставщики данных"_  ->  .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="3f8ec-157">Клонировать _"дефаултмикседреалитинпутсимпулатионпрофиле"_ , чтобы внести в него изменения.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="3f8ec-158">Установите флажок _"имитировать расположение глаз"_ .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![Имитация МРТКных глаз](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="3f8ec-160">**Отключить курсор по умолчанию для головного взгляда**: в целом рекомендуется избегать отображения курсора глаза или, если необходимо, сделать его _очень_ незаметным.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="3f8ec-161">Мы советуем скрыть курсор Head по умолчанию, который по умолчанию присоединен к профилю указателя МРТК.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="3f8ec-162">Перейдите к профилю конфигурации мртк-> _"входные_"  ->  _"указатели"_ .</span><span class="sxs-lookup"><span data-stu-id="3f8ec-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="3f8ec-163">Клонировать _"дефаултмикседреалитинпутпоинтерпрофиле"_ , чтобы внести в него изменения.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="3f8ec-164">В верхней части параметра _"Параметры указателя"_ следует назначить _"газекурсор"_ невидимый курсор prefab.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="3f8ec-165">Это можно сделать, выбрав prefab _"эйегазекурсор"_ в мртк Foundation.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="3f8ec-166">Включение взгляда на основе глаз в поставщике взгляда</span><span class="sxs-lookup"><span data-stu-id="3f8ec-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="3f8ec-167">В HoloLens v1 в качестве основного указывающего метода использовался головной взгляд.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="3f8ec-168">Несмотря на то, что головной взгляд по-прежнему доступен через _газепровидер_ в мртк, присоединенном к [камере](https://docs.unity3d.com/ScriptReference/Camera.html), можно проверить использование взгляда глаз, поделенную на флажок _"исэйетраккинженаблед"_ в параметрах взгляда профиля входного указателя.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="3f8ec-169">Разработчики могут переключаться между взглядом на глаза и взглядом на заголовки в коде, изменяя свойство _"исэйетраккинженаблед"_ объекта _"газепровидер"_.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="3f8ec-170">Если какие-либо требования к отслеживанию взгляда не выполняются, приложение автоматически перейдет к взгляду на голове.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="3f8ec-171">Доступ к данным взгляда на глаза</span><span class="sxs-lookup"><span data-stu-id="3f8ec-171">Accessing eye gaze data</span></span>

<span data-ttu-id="3f8ec-172">Теперь, когда сцена настроена на использование отслеживания взгляда, давайте посмотрим, как получить к ним доступ в скриптах: доступ к [данным отслеживания взгляда через эйегазепровидер](eye-tracking-eye-gaze-provider.md) и [Поддерживаемые варианты целевого объекта](eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="3f8ec-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="3f8ec-173">Тестирование приложения Unity в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f8ec-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="3f8ec-174">Создание приложения с отслеживанием взгляда должно быть похоже на то, как будут компилироваться другие приложения МРТК HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="3f8ec-175">Убедитесь, что включена возможность ввода с помощью *взгляда* , как описано выше в разделе [*а Примечание о возможности газеинпут*](#a-note-on-the-gazeinput-capability).</span><span class="sxs-lookup"><span data-stu-id="3f8ec-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="3f8ec-176">Калибровка глаз</span><span class="sxs-lookup"><span data-stu-id="3f8ec-176">Eye calibration</span></span>

<span data-ttu-id="3f8ec-177">Наконец, не забудьте выполнить калибровку глаз в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="3f8ec-178">Система отслеживания взгляда не будет возвращать никаких входных данных, если пользователь не откалиброван.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="3f8ec-179">Самый простой способ перейти к калибровке заключается в зеркальном отображении гипервизора и резервном копировании.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="3f8ec-180">Системное уведомление должно появиться, дружелюбны вас как новый пользователь, и попросит вас пройти по калибровке глаз.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="3f8ec-181">Кроме того, можно найти калибровку глаз в окне Системные параметры: параметры > калибровка > системы > калибровка глаз.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="3f8ec-182">Разрешение на отслеживание глаз</span><span class="sxs-lookup"><span data-stu-id="3f8ec-182">Eye tracking permission</span></span>

<span data-ttu-id="3f8ec-183">При первом запуске приложения в HoloLens 2 будет выведен запрос на разрешение пользователя на использование отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="3f8ec-184">Если он не отображается, то, как правило, это указывает на то, что возможность _"газеинпут"_ не задана.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="3f8ec-185">После того как запрос на разрешение выводится один раз, он не отображается автоматически.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="3f8ec-186">Если вы _"отклонили разрешение на отслеживание глаз"_, то можете сбросить его в окне "Параметры" — > > приложения о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="3f8ec-187">Вы должны приступить к работе с отслеживанием взгляда в приложении МРТК Unity.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="3f8ec-188">Не забудьте просмотреть [учебники по отслеживанию взглядов мртк и примеры](../../example-scenes/eye-tracking-examples-overview.md) , демонстрирующие использование входных данных отслеживания взгляда и удобное предоставление сценариев, которые можно повторно использовать в проектах.</span><span class="sxs-lookup"><span data-stu-id="3f8ec-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="3f8ec-189">Вернуться к "Отслеживание взглядов в Микседреалититулкит"</span><span class="sxs-lookup"><span data-stu-id="3f8ec-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)