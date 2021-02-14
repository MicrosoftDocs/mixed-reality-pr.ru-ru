---
title: Функции, поддерживаемые подключаемым модулем Опенкср в Unity
description: Ознакомьтесь с функциями Опенкср, поддерживаемыми для разработки смешанной реальности в Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496156"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="fb553-104">Функции, поддерживаемые Опенкср Mixed Reality в Unity</span><span class="sxs-lookup"><span data-stu-id="fb553-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="fb553-105">Пакет **подключаемого модуля опенкср для смешанной реальности** является расширением **подключаемого модуля опенкср** Unity и поддерживает набор функций для головных телефонов HoloLens 2 и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fb553-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="fb553-106">Прежде чем продолжить, убедитесь, что установлен **unity 2020,2** или более поздней **версии, подключаемый модуль опенкср версия 0.1.3** или более поздней, а проект Unity [настроен для опенкср](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="fb553-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="fb553-107">Поддерживаемые функции</span><span class="sxs-lookup"><span data-stu-id="fb553-107">What's supported</span></span>

<span data-ttu-id="fb553-108">В настоящее время поддерживаются следующие функции:</span><span class="sxs-lookup"><span data-stu-id="fb553-108">The following features are currently supported:</span></span>

* <span data-ttu-id="fb553-109">Поддерживает приложения UWP для HoloLens 2 и оптимизированы для модели приложений HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="fb553-110">Поддерживает приложения Win32 версий для гарнитуры Windows Mixed Reality с последними профилями контроллеров и удаленным взаимодействием с holographic приложениями.</span><span class="sxs-lookup"><span data-stu-id="fb553-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="fb553-111">Отслеживание масштаба мира с использованием привязок и неограниченного пространства.</span><span class="sxs-lookup"><span data-stu-id="fb553-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="fb553-112">[API-интерфейс хранилища привязки для сохранения привязок](#anchors-and-anchor-persistence) в локальном хранилище HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="fb553-113">[Взаимодействие контроллера движения и руки](#motion-controller-and-hand-interactions), включая новый контроллер HP REVERB G2.</span><span class="sxs-lookup"><span data-stu-id="fb553-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="fb553-114">Отслеживание с обобразованием с использованием 26 соединений и совместного входа RADIUS.</span><span class="sxs-lookup"><span data-stu-id="fb553-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="fb553-115">Взаимодействие взгляда на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="fb553-116">Поиск камеры фото/Video (ПС) в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="fb553-117">Запись смешанной реальности с помощью визуализации с третьим глазом через камеру ПС.</span><span class="sxs-lookup"><span data-stu-id="fb553-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="fb553-118">Поддерживает ["Play" в HoloLens 2 с помощью приложения holographic, поддерживающего удаленное взаимодействие](#holographic-remoting-in-unity-editor-play-mode), что позволяет разработчикам выполнять отладку сценариев без создания и развертывания на устройстве.</span><span class="sxs-lookup"><span data-stu-id="fb553-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="fb553-119">Совместимо с МРТК Unity 2.5.3 и более поздней версии через [поддержку поставщика Мртк опенкср](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="fb553-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="fb553-120">Совместимо с Unity [арфаундатион 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="fb553-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="fb553-121">(Добавлено в 0.1.3) Поддерживает [настольное приложение holographic удаленное взаимодействие](#holographic-remoting-in-desktop-app) из созданного и развернутого автономного приложения Windows.</span><span class="sxs-lookup"><span data-stu-id="fb553-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="fb553-122">Настройка удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="fb553-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="fb553-123">Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="fb553-124">Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.</span><span class="sxs-lookup"><span data-stu-id="fb553-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="fb553-125">Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="fb553-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="fb553-127">Holographic удаленное взаимодействие в режиме воспроизведения редактора Unity</span><span class="sxs-lookup"><span data-stu-id="fb553-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="fb553-128">Создание проекта Unity для UWP в проекте Visual Studio, а затем упаковка и развертывание на устройстве HoloLens 2 может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="fb553-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="fb553-129">Одним из решений является включение функции удаленного взаимодействия в holographic Editor, которая позволяет выполнять отладку сценария C# с помощью режима Play непосредственно на устройстве HoloLens 2 по сети.</span><span class="sxs-lookup"><span data-stu-id="fb553-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="fb553-130">Этот сценарий позволяет избежать издержек при создании и развертывании пакета UWP на удаленном устройстве.</span><span class="sxs-lookup"><span data-stu-id="fb553-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="fb553-131">Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="fb553-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="fb553-132">Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="fb553-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-features-img-02.png)

3. <span data-ttu-id="fb553-134">Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".</span><span class="sxs-lookup"><span data-stu-id="fb553-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="fb553-135">Установите флажок **удаленное взаимодействие с помощью редактора holographic** и введите IP-адрес, полученный из приложения holographic Remoting:</span><span class="sxs-lookup"><span data-stu-id="fb553-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенными компонентами](images/openxr-features-img-03.png)

<span data-ttu-id="fb553-137">Теперь можно нажать кнопку "Воспроизвести", чтобы воспроизвести приложение Unity в удаленном приложении holographic на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb553-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="fb553-138">Вы также можете [присоединить Visual Studio к Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) для отладки скриптов C# в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="fb553-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="fb553-139">Начиная с версии 0.1.0, среда выполнения holographic Remoting не поддерживает привязки, а функции Аранчорманажер не будут работать через удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="fb553-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="fb553-140">Эта функция появилась в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="fb553-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="fb553-141">Holographic удаленное взаимодействие в классическом приложении</span><span class="sxs-lookup"><span data-stu-id="fb553-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="fb553-142">В выпуске пакета 0.1.3 добавлена поддержка удаленного взаимодействия автономных приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="fb553-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="fb553-143">Начиная с версии 0.1.3 Эта функция не поддерживает сборки UWP.</span><span class="sxs-lookup"><span data-stu-id="fb553-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="fb553-144">Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="fb553-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="fb553-145">Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="fb553-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="fb553-146">Кроме того, снимите флажок **инициализировать XR при запуске**:</span><span class="sxs-lookup"><span data-stu-id="fb553-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Снимок экрана: панель "Параметры проекта" открыта в редакторе Unity с снятым флажком "инициализировать XR при запуске"](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="fb553-148">Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".</span><span class="sxs-lookup"><span data-stu-id="fb553-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="fb553-149">Установите флажок **удаленное взаимодействие с приложением holographic** .</span><span class="sxs-lookup"><span data-stu-id="fb553-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с включенной удаленным взаимодействием приложений](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="fb553-151">Затем напишите некоторый код, чтобы задать конфигурацию удаленного взаимодействия и инициировать инициализацию XR.</span><span class="sxs-lookup"><span data-stu-id="fb553-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="fb553-152">Пример приложения, распространяемый с помощью [подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md#hololens-2-samples) , содержит AppRemoting.cs, в котором показан пример сценария для подключения к ОПРЕДЕЛЕННОМУ IP-адресу во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="fb553-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="fb553-153">При развертывании примера приложения на локальном компьютере в этом месте будет отображаться поле ввода IP-адреса с кнопкой подключения.</span><span class="sxs-lookup"><span data-stu-id="fb553-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="fb553-154">Введите IP-адрес и нажмите кнопку Подключить, чтобы инициализировать XR и попытаться подключиться к целевому устройству:</span><span class="sxs-lookup"><span data-stu-id="fb553-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Снимок экрана примера приложения, отображающего пример пользовательского интерфейса удаленного взаимодействия](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="fb553-156">Чтобы написать пользовательский код соединения, вызовите `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` его с помощью заполнения `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="fb553-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="fb553-157">Пример приложения предоставляет это в инспекторе и показывает, как заполнить IP-адрес из текстового поля.</span><span class="sxs-lookup"><span data-stu-id="fb553-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="fb553-158">Вызов `Connect` задаст конфигурацию и автоматически инициализирует XR, поэтому ее необходимо вызвать как соподпрограмму:</span><span class="sxs-lookup"><span data-stu-id="fb553-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="fb553-159">Во время выполнения можно получить текущее состояние соединения с помощью `AppRemoting.TryGetConnectionState` API, а также при необходимости отключить и деинициализировать XR с помощью `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="fb553-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="fb553-160">Это можно использовать для отключения и повторного подключения к другому устройству в рамках одного сеанса приложения.</span><span class="sxs-lookup"><span data-stu-id="fb553-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="fb553-161">Пример приложения предоставляет управляемый куб, который отключает сеанс удаленного взаимодействия, если он нажат.</span><span class="sxs-lookup"><span data-stu-id="fb553-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="fb553-162">Миграция с предыдущих API</span><span class="sxs-lookup"><span data-stu-id="fb553-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="fb553-163">UnityEngine. XR. WSA. Холографикремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="fb553-164">Из примера кода в [документах Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="fb553-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="fb553-165">XR. Головк. холографикремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="fb553-166">Опенкср. Remoting. Аппремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="fb553-167">[Н/д: автоматически происходит при вызове `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="fb553-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="fb553-168">UnityEngine. XR. Виндовсмр. Виндовсмрремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="fb553-169">XR. Виндовсмр. Виндовсмрремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="fb553-170">Опенкср. Remoting. Аппремотинг</span><span class="sxs-lookup"><span data-stu-id="fb553-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="fb553-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` и `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="fb553-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="fb553-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="fb553-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="fb553-173">Передается `AppRemoting.Connect` через `RemotingConfiguration` структуру</span><span class="sxs-lookup"><span data-stu-id="fb553-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="fb553-174">Привязки и сохранение привязки</span><span class="sxs-lookup"><span data-stu-id="fb553-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="fb553-175">Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity.</span><span class="sxs-lookup"><span data-stu-id="fb553-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="fb553-176">Основные сведения о **аранчор** s в арфаундатион см. в руководстве по [Арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="fb553-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="fb553-177">Начиная с версии 0.1.0 этот подключаемый модуль поддерживает все функциональные возможности Аранчорманажер, за исключением создания привязок, присоединенных к плоскости, которая ожидается в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="fb553-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="fb553-178">Сохранение привязки и Ксранчорсторе</span><span class="sxs-lookup"><span data-stu-id="fb553-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="fb553-179">Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами.</span><span class="sxs-lookup"><span data-stu-id="fb553-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="fb553-180">Ксранчорсторе — это представление сохраненных привязок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="fb553-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="fb553-181">Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.</span><span class="sxs-lookup"><span data-stu-id="fb553-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="fb553-182">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="fb553-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="fb553-183">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="fb553-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="fb553-184">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:</span><span class="sxs-lookup"><span data-stu-id="fb553-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="fb553-185">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fb553-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="fb553-186">Полный пример сохранения и несохраненных привязок см. в разделе привязки-> примеры привязок в образце [сцены подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="fb553-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="fb553-189">Взаимодействие контроллера движения и руки</span><span class="sxs-lookup"><span data-stu-id="fb553-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="fb553-190">Основные сведения о взаимодействии смешанной реальности в Unity см. в [руководстве по Unity для XR данных Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="fb553-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="fb553-191">Эта документация по Unity охватывает сопоставления от входных данных, относящихся к конкретному контроллеру, с более обобщенными **инпутфеатуреусажеами**, как можно идентифицировать и классифицировать доступные входные данные XR, как считывать их из этих входных данных и многое другое.</span><span class="sxs-lookup"><span data-stu-id="fb553-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="fb553-192">Подключаемый модуль Mixed Reality Опенкср предоставляет дополнительные профили взаимодействия ввода, сопоставленные со стандартным **инпутфеатуреусаже**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="fb553-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="fb553-193">инпутфеатуреусаже</span><span class="sxs-lookup"><span data-stu-id="fb553-193">InputFeatureUsage</span></span> | <span data-ttu-id="fb553-194">HP reverbы G2 Controller (Опенкср)</span><span class="sxs-lookup"><span data-stu-id="fb553-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="fb553-195">HoloLens (Опенкср)</span><span class="sxs-lookup"><span data-stu-id="fb553-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="fb553-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="fb553-196">primary2DAxis</span></span> | <span data-ttu-id="fb553-197">Джойстик</span><span class="sxs-lookup"><span data-stu-id="fb553-197">Joystick</span></span> | |
| <span data-ttu-id="fb553-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="fb553-198">primary2DAxisClick</span></span> | <span data-ttu-id="fb553-199">Джойстик — щелчок</span><span class="sxs-lookup"><span data-stu-id="fb553-199">Joystick - Click</span></span> | |
| <span data-ttu-id="fb553-200">триггер</span><span class="sxs-lookup"><span data-stu-id="fb553-200">trigger</span></span> | <span data-ttu-id="fb553-201">Триггер</span><span class="sxs-lookup"><span data-stu-id="fb553-201">Trigger</span></span>  | |
| <span data-ttu-id="fb553-202">регулировки</span><span class="sxs-lookup"><span data-stu-id="fb553-202">grip</span></span> | <span data-ttu-id="fb553-203">Регулировки</span><span class="sxs-lookup"><span data-stu-id="fb553-203">Grip</span></span> | <span data-ttu-id="fb553-204">Воздушный нажим или сжатие</span><span class="sxs-lookup"><span data-stu-id="fb553-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="fb553-205">примарибуттон</span><span class="sxs-lookup"><span data-stu-id="fb553-205">primaryButton</span></span> | <span data-ttu-id="fb553-206">[X/A] — нажмите клавишу</span><span class="sxs-lookup"><span data-stu-id="fb553-206">[X/A] - Press</span></span> | <span data-ttu-id="fb553-207">Жест касания</span><span class="sxs-lookup"><span data-stu-id="fb553-207">Air tap</span></span> |
| <span data-ttu-id="fb553-208">секондарибуттон</span><span class="sxs-lookup"><span data-stu-id="fb553-208">secondaryButton</span></span> | <span data-ttu-id="fb553-209">[Y/B] — нажмите клавишу</span><span class="sxs-lookup"><span data-stu-id="fb553-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="fb553-210">грипбуттон</span><span class="sxs-lookup"><span data-stu-id="fb553-210">gripButton</span></span> | <span data-ttu-id="fb553-211">Захват и нажатие клавиши</span><span class="sxs-lookup"><span data-stu-id="fb553-211">Grip - Press</span></span> | |
| <span data-ttu-id="fb553-212">тригжербуттон</span><span class="sxs-lookup"><span data-stu-id="fb553-212">triggerButton</span></span> | <span data-ttu-id="fb553-213">Триггер-нажатие</span><span class="sxs-lookup"><span data-stu-id="fb553-213">Trigger - Press</span></span> | |
| <span data-ttu-id="fb553-214">менубуттон</span><span class="sxs-lookup"><span data-stu-id="fb553-214">menuButton</span></span> | <span data-ttu-id="fb553-215">Меню</span><span class="sxs-lookup"><span data-stu-id="fb553-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="fb553-216">AIM и захват</span><span class="sxs-lookup"><span data-stu-id="fb553-216">Aim and Grip Poses</span></span>

<span data-ttu-id="fb553-217">У вас есть доступ к двум наборам экземпляров через входные взаимодействия Опенкср:</span><span class="sxs-lookup"><span data-stu-id="fb553-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="fb553-218">Захват для отрисовки объектов в руки</span><span class="sxs-lookup"><span data-stu-id="fb553-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="fb553-219">Цель, указывающая на мир.</span><span class="sxs-lookup"><span data-stu-id="fb553-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="fb553-220">Дополнительные сведения об этой структуре и различиях между ними можно найти в [подкаталогах Опенкср Specification-input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="fb553-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="fb553-221">Представления, предоставляемые Инпутфеатуреусажес **девицепоситион**, **девицеротатион**, **девицевелоЦити** и **девицеангуларвелоЦити** , представляют собой OpenXR **захват** .</span><span class="sxs-lookup"><span data-stu-id="fb553-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="fb553-222">Инпутфеатуреусажес, связанные с захватом, определяются в [Коммонусажес](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="fb553-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="fb553-223">Представления, предоставляемые Инпутфеатуреусажес **поинтерпоситион**, **поинтерротатион**, **поинтервелоЦити** и **поинтерангуларвелоЦити** , представляют собой OpenXR **Цель** .</span><span class="sxs-lookup"><span data-stu-id="fb553-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="fb553-224">Эти Инпутфеатуреусажес не определены во вложенных файлах C#, поэтому необходимо определить собственный Инпутфеатуреусажес следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fb553-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="fb553-225">хаптикс</span><span class="sxs-lookup"><span data-stu-id="fb553-225">Haptics</span></span>

<span data-ttu-id="fb553-226">Сведения об использовании хаптикс в системе ввода XR в Unity можно найти в [руководстве по Unity для Unity XR input-хаптикс](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="fb553-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="fb553-227">Что ожидается в ближайшее время</span><span class="sxs-lookup"><span data-stu-id="fb553-227">What's coming soon</span></span>

<span data-ttu-id="fb553-228">Следующие проблемы и отсутствующие функции известны с помощью Опенкср подключаемого модуля Mixed Reality **версии 0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="fb553-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="fb553-229">Мы работаем над этим и выпустили исправления и новые функции в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="fb553-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="fb553-230">**Арпланесубсистем** еще не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="fb553-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="fb553-231">**Арпланеманажер**, **АРРАЙКАСТМАНАЖЕР** и связанный API, такие как **аранчорманажер. аттачанчор** , также не поддерживаются в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="fb553-232">**Привязка** еще не поддерживается с помощью удаленного взаимодействия holographic, но в ближайшем будущем.</span><span class="sxs-lookup"><span data-stu-id="fb553-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="fb553-233">Отслеживание **сетки вручную** , **QR-коды** и **ксрмешсубсистем** пока не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="fb553-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="fb553-234">Поддержка **пространственных привязок Azure** появилась в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="fb553-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="fb553-235">**ARM64** — единственная поддерживаемая платформа для приложений HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb553-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="fb553-236">Платформа **ARM** поступает в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="fb553-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="fb553-237">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="fb553-237">Troubleshooting</span></span>

<span data-ttu-id="fb553-238">При приостановке и возобновлении работы приложения Unity в HoloLens 2 приложение не может корректно возобновить работу, что приводит к 4 вращающимся точкам в представлении HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb553-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="fb553-239">Установка для **режима отправки глубины** значения " **нет** " в параметрах проекта опенкср в качестве обходного пути</span><span class="sxs-lookup"><span data-stu-id="fb553-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
