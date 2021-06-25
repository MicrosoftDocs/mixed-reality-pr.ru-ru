---
title: Голографическое удаленное взаимодействие в классическом приложении
description: Узнайте, как использовать удаленное взаимодействие в классических приложениях с помощью Опенкср.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, наушники смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, Настольный компьютер
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906730"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="11e47-104">Голографическое удаленное взаимодействие в классическом приложении</span><span class="sxs-lookup"><span data-stu-id="11e47-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="11e47-105">В выпуске пакета 0.1.3 добавлена поддержка удаленного взаимодействия автономных приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="11e47-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="11e47-106">Начиная с версии 0.1.3 Эта функция не поддерживает сборки UWP.</span><span class="sxs-lookup"><span data-stu-id="11e47-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="11e47-107">Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](unity-play-mode.md#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="11e47-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="11e47-108">Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="11e47-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="11e47-109">Кроме того, снимите флажок **инициализировать XR при запуске**:</span><span class="sxs-lookup"><span data-stu-id="11e47-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Снимок экрана: панель "Параметры проекта" открыта в редакторе Unity с снятым флажком "инициализировать XR при запуске"](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="11e47-111">Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".</span><span class="sxs-lookup"><span data-stu-id="11e47-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="11e47-112">Установите флажок **удаленное взаимодействие с приложением holographic** .</span><span class="sxs-lookup"><span data-stu-id="11e47-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с включенной удаленным взаимодействием приложений](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="11e47-114">Затем напишите некоторый код, чтобы задать конфигурацию удаленного взаимодействия и инициировать инициализацию XR.</span><span class="sxs-lookup"><span data-stu-id="11e47-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="11e47-115">Пример приложения, распространяемый с [подключаемым модулем Mixed Reality опенкср](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) , содержит аппремотинг. cs, в котором показан пример сценария для подключения к ОПРЕДЕЛЕННОМУ IP-адресу во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="11e47-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="11e47-116">При развертывании примера приложения на локальном компьютере в этом месте будет отображаться поле ввода IP-адреса с кнопкой подключения.</span><span class="sxs-lookup"><span data-stu-id="11e47-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="11e47-117">Введите IP-адрес и нажмите кнопку Подключить, чтобы инициализировать XR и попытаться подключиться к целевому устройству:</span><span class="sxs-lookup"><span data-stu-id="11e47-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Снимок экрана примера приложения, отображающего пример пользовательского интерфейса удаленного взаимодействия](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="11e47-119">Чтобы написать пользовательский код соединения, вызовите `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` его с помощью заполнения `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="11e47-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="11e47-120">Пример приложения предоставляет это в инспекторе и показывает, как заполнить IP-адрес из текстового поля.</span><span class="sxs-lookup"><span data-stu-id="11e47-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="11e47-121">Вызов `Connect` задаст конфигурацию и автоматически инициализирует XR, поэтому ее необходимо вызвать как соподпрограмму:</span><span class="sxs-lookup"><span data-stu-id="11e47-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="11e47-122">Во время выполнения можно получить текущее состояние соединения с помощью `AppRemoting.TryGetConnectionState` API, а также при необходимости отключить и деинициализировать XR с помощью `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="11e47-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="11e47-123">Это можно использовать для отключения и повторного подключения к другому устройству в рамках одного сеанса приложения.</span><span class="sxs-lookup"><span data-stu-id="11e47-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="11e47-124">Пример приложения предоставляет управляемый куб, который отключает сеанс удаленного взаимодействия, если он нажат.</span><span class="sxs-lookup"><span data-stu-id="11e47-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="11e47-125">Миграция с предыдущих API</span><span class="sxs-lookup"><span data-stu-id="11e47-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="11e47-126">UnityEngine. XR. WSA. Холографикремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="11e47-127">Из примера кода в [документах Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="11e47-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="11e47-128">XR. Головк. холографикремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="11e47-129">Опенкср. Remoting. Аппремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="11e47-130">[Н/д: автоматически происходит при вызове `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="11e47-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="11e47-131">UnityEngine. XR. Виндовсмр. Виндовсмрремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="11e47-132">XR. Виндовсмр. Виндовсмрремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="11e47-133">Опенкср. Remoting. Аппремотинг</span><span class="sxs-lookup"><span data-stu-id="11e47-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="11e47-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` и `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="11e47-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="11e47-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="11e47-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="11e47-136">Передается `AppRemoting.Connect` через `RemotingConfiguration` структуру</span><span class="sxs-lookup"><span data-stu-id="11e47-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`