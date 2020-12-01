---
title: Создание удаленного приложения holographic с удаленным взаимодействием (Опенкср)
description: При создании удаленного приложения holographic удаленное содержимое, которое отображается на удаленном компьютере, можно передать в HoloLens 2. В этой статье описывается, как это можно сделать.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469519"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="f277b-105">Создание удаленного приложения holographic с удаленным взаимодействием с помощью API Опенкср</span><span class="sxs-lookup"><span data-stu-id="f277b-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="f277b-106">В этом документе описывается создание удаленного приложения для головных телефонов HoloLens 2 и Windows Mixed Reality с помощью [API опенкср](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="f277b-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="f277b-107">Удаленные приложения для **HoloLens (1-го поколения)** должны использовать пакет NuGet версии **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="f277b-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="f277b-108">Это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="f277b-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="f277b-109">Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="f277b-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="f277b-110">При создании удаленного приложения с удаленным удаленным доступом удаленное содержимое, отображаемое на удаленном компьютере, можно передать в HoloLens 2 и иммерсивное устройство, например гарнитуры Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f277b-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="f277b-111">В этой статье описывается, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="f277b-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="f277b-112">Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="f277b-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="f277b-113">Holographic удаленное взаимодействие позволяет приложению ориентироваться на гарнитуры HoloLens 2 и Windows Mixed Reality с holographic-содержимым, отображаемым на настольном компьютере или на устройстве UWP, например на Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и позволяет интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК.</span><span class="sxs-lookup"><span data-stu-id="f277b-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="f277b-114">Удаленное приложение получает поток входных данных из HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f277b-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="f277b-115">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f277b-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="f277b-116">Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="f277b-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="f277b-117">Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="f277b-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="f277b-118">Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки.</span><span class="sxs-lookup"><span data-stu-id="f277b-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="f277b-119">Приложение проигрывателя может сообщать о задержке в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="f277b-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f277b-120">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="f277b-120">Prerequisites</span></span>

<span data-ttu-id="f277b-121">Хорошей отправной точкой является работающая Рабочая станция или приложение UWP на основе Опенкср.</span><span class="sxs-lookup"><span data-stu-id="f277b-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="f277b-122">Дополнительные сведения см. [в статье Приступая к работе с опенкср](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="f277b-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="f277b-123">Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="f277b-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="f277b-124">Использование [однопотокового подразделения](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="f277b-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="f277b-125">При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f277b-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="f277b-126">Получение пакета NuGet для удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f277b-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="f277b-127">Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="f277b-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="f277b-128">Откройте проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f277b-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="f277b-129">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="f277b-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="f277b-130">На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="f277b-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="f277b-131">Выберите **Microsoft. Holographic. Remoting. опенкср**, выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="f277b-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="f277b-132">Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f277b-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="f277b-133">Следующее появившееся диалоговое окно — это лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="f277b-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="f277b-134">Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="f277b-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="f277b-135">Повторите шаги 3 – 6 для следующих пакетов NuGet: Опенкср. Headers, Опенкср. Loader.</span><span class="sxs-lookup"><span data-stu-id="f277b-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="f277b-136">Версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, желающих выбрать HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="f277b-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="f277b-137">Дополнительные сведения см. в разделе [Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="f277b-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="f277b-138">Выберите среду выполнения Опенкср для удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f277b-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="f277b-139">Первым шагом, который необходимо сделать в удаленном приложении, является выбор среды выполнения Опенкср holographic Remoting, которая является частью пакета NuGet Microsoft. Holographic. Remoting. Опенкср.</span><span class="sxs-lookup"><span data-stu-id="f277b-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="f277b-140">Это можно сделать, задав ```XR_RUNTIME_JSON``` для переменной среды путь к RemotingXR.jsфайла в приложении.</span><span class="sxs-lookup"><span data-stu-id="f277b-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="f277b-141">Эта переменная среды используется загрузчиком Опенкср для того, чтобы не использовать системную среду Опенкср по умолчанию, а вместо этого перенаправлять в среду выполнения Опенкср удаленного взаимодействия Holographic.</span><span class="sxs-lookup"><span data-stu-id="f277b-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="f277b-142">При использовании RemotingXR.jsпакета NuGet Microsoft. Holographic. Remoting. Опенкср файл автоматически копируется во время компиляции в выходную папку, поэтому выбор среды выполнения Опенкср обычно выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f277b-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="f277b-143">Создание Ксринстанце с расширением holographic для удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f277b-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="f277b-144">Первым шагом является типичное приложение Опенкср — выбор расширений Опенкср и создание Ксринстанце.</span><span class="sxs-lookup"><span data-stu-id="f277b-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="f277b-145">Спецификация ядра Опенкср не предоставляет API для удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f277b-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="f277b-146">По этой причине holographic удаленное взаимодействие представляет собой собственное расширение Опенкср с именем ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="f277b-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="f277b-147">Убедитесь, что при вызове Ксркреатеинстанце, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` включенном в ксринстанцекреатеинфо.</span><span class="sxs-lookup"><span data-stu-id="f277b-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="f277b-148">По умолчанию отображаемое содержимое приложения передается только в поток удаленного взаимодействия holographic, который работает в HoloLens 2 или на гарнитурах Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f277b-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="f277b-149">Чтобы отобразить содержимое, подготовленное на удаленном компьютере, с помощью цепочки подкачки окна для экземпляра, то удаленное взаимодействие удаленного взаимодействия предоставляет второе расширение Опенкср с именем ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="f277b-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="f277b-150">Также обязательно включите это расширение с помощью ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` , если вы хотите использовать эту функцию.</span><span class="sxs-lookup"><span data-stu-id="f277b-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f277b-151">Чтобы узнать об API расширения Опенкср для удаленного взаимодействия с holographic, ознакомьтесь со [спецификацией](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) , которую можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="f277b-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="f277b-152">Подключение к устройству</span><span class="sxs-lookup"><span data-stu-id="f277b-152">Connect to the device</span></span>

<span data-ttu-id="f277b-153">После создания удаленного приложения Ксринстанце и запроса Ксрсистемид через Ксржетсистем можно установить подключение к устройству проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="f277b-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="f277b-154">Среда выполнения Опенкср с holographic удаленное взаимодействие может предоставлять данные только для конкретных устройств, такие как конфигурации представления или режимы смешения среды после установки соединения.</span><span class="sxs-lookup"><span data-stu-id="f277b-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="f277b-155">```xrEnumerateViewConfigurations```,,, ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` и ```xrGetSystemProperties``` будут предоставлять значения по умолчанию, соответствующие действиям, которые обычно получаются при подключении к проигрывателю, работающему в HoloLens 2, до полного подключения.</span><span class="sxs-lookup"><span data-stu-id="f277b-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="f277b-156">Настоятельно рекомендуется не вызывать эти методы до установки соединения.</span><span class="sxs-lookup"><span data-stu-id="f277b-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="f277b-157">Предложение использует эти методы после успешного создания Ксрсессион и состояния сеанса по крайней мере XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="f277b-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="f277b-158">Общие свойства, такие как максимальная скорость, включение звука, видеокодек или поток глубины, можно настроить ```xrRemotingSetContextPropertiesMSFT``` с помощью следующего.</span><span class="sxs-lookup"><span data-stu-id="f277b-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="f277b-159">Соединение может быть выполнено одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="f277b-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="f277b-160">Удаленное приложение подключается к проигрывателю, работающему на устройстве.</span><span class="sxs-lookup"><span data-stu-id="f277b-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="f277b-161">Проигрыватель, выполняющийся на устройстве, подключается к удаленному приложению.</span><span class="sxs-lookup"><span data-stu-id="f277b-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="f277b-162">Чтобы установить подключение из удаленного приложения к устройству проигрывателя, вызовите метод, ```xrRemotingConnectMSFT``` указывающий имя узла и порт через  ```XrRemotingConnectInfoMSFT``` структуру.</span><span class="sxs-lookup"><span data-stu-id="f277b-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="f277b-163">Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.</span><span class="sxs-lookup"><span data-stu-id="f277b-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="f277b-164">Прослушивание входящих подключений в удаленном приложении можно выполнить, вызвав ```xrRemotingListenMSFT``` метод.</span><span class="sxs-lookup"><span data-stu-id="f277b-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="f277b-165">Порт подтверждения и порт транспорта можно указать с помощью ```XrRemotingListenInfoMSFT``` структуры.</span><span class="sxs-lookup"><span data-stu-id="f277b-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="f277b-166">Порт подтверждения используется для первоначального подтверждения.</span><span class="sxs-lookup"><span data-stu-id="f277b-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="f277b-167">Затем данные пересылаются через порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="f277b-167">The data is then send over the transport port.</span></span> <span data-ttu-id="f277b-168">По умолчанию используются **8265** и **8266** .</span><span class="sxs-lookup"><span data-stu-id="f277b-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="f277b-169">При вызове или вызывается состояние соединения должно быть отключено ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="f277b-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="f277b-170">Состояние подключения можно получить в любой момент после создания Ксринстанце и запроса для Ксрсистемид с помощью ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="f277b-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="f277b-171">Доступные состояния подключения:</span><span class="sxs-lookup"><span data-stu-id="f277b-171">Available connection states are:</span></span>
- <span data-ttu-id="f277b-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="f277b-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="f277b-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="f277b-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="f277b-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="f277b-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f277b-175">```xrRemotingConnectMSFT``````xrRemotingListenMSFT```метод или должен быть вызван перед попыткой создать ксрсессион через ксркреатесессион.</span><span class="sxs-lookup"><span data-stu-id="f277b-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="f277b-176">Если вы попытаетесь создать Ксрсессион, а состояние соединения — ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` Создание сеанса, то будет выполнена успешная операция, но состояние сеанса немедленно переходит на XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="f277b-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="f277b-177">Реализация службы удаленного взаимодействия holographic ```xrCreateSession``` поддерживает ожидание установки соединения.</span><span class="sxs-lookup"><span data-stu-id="f277b-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="f277b-178">Можно вызвать ```xrRemotingConnectMSFT``` или ```xrRemotingListenMSFT``` сразу после вызова, ```xrCreateSession``` который будет блокироваться и ждать установления соединения.</span><span class="sxs-lookup"><span data-stu-id="f277b-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="f277b-179">Время ожидания истекает до 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="f277b-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="f277b-180">Если подключение может быть установлено в течение этого времени, создание Ксрсессион будет продолжено, а состояние сеанса будет перенесено в XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="f277b-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="f277b-181">Если соединение не может быть установлено, то создание сеанса также выполняется без немедленного перехода на XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="f277b-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="f277b-182">В общем случае состояние соединения — это соединено с состоянием Ксрсессион.</span><span class="sxs-lookup"><span data-stu-id="f277b-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="f277b-183">Любое изменение состояния соединения также влияет на состояние сеанса.</span><span class="sxs-lookup"><span data-stu-id="f277b-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="f277b-184">Например, если состояние подключения переключается с `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` на ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` состояние сеанса, также будет перенесено в XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="f277b-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="f277b-185">Обработка событий, связанных с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="f277b-185">Handling Remoting specific events</span></span>

<span data-ttu-id="f277b-186">В удаленной среде выполнения Опенкср имеется три события, которые важны для отслеживания состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="f277b-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="f277b-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Активируется при успешном установлении подключения к устройству.</span><span class="sxs-lookup"><span data-stu-id="f277b-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="f277b-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Активируется, если установленное соединение закрыто или не удалось установить соединение.</span><span class="sxs-lookup"><span data-stu-id="f277b-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="f277b-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: При ожидании запуска входящих подключений.</span><span class="sxs-lookup"><span data-stu-id="f277b-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="f277b-190">Эти события помещаются в очередь, и удаленное приложение должно считывать данные из очереди с регулярным использованием через ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="f277b-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="f277b-191">Предварительный просмотр потокового содержимого на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="f277b-191">Preview streamed content locally</span></span>

<span data-ttu-id="f277b-192">Чтобы отобразить то же содержимое в удаленном приложении, которое отправляется на устройство, ```XR_MSFT_holographic_remoting_frame_mirroring``` можно использовать расширение.</span><span class="sxs-lookup"><span data-stu-id="f277b-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="f277b-193">С помощью этого расширения можно отправить текстуру в Ксрендфраме.</span><span class="sxs-lookup"><span data-stu-id="f277b-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="f277b-194">Это делается с помощью структуры, ```XrRemotingFrameMirrorImageInfoMSFT``` которая связана с ксрфраминдинфо следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f277b-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="f277b-195">В приведенном выше примере используется текстура цепочки подкачки DX11 и представление окна сразу после вызова Ксрендфраме.</span><span class="sxs-lookup"><span data-stu-id="f277b-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="f277b-196">Использование не ограничено текстурами цепочки подкачки, а дополнительная синхронизация GPU не требуется.</span><span class="sxs-lookup"><span data-stu-id="f277b-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="f277b-197">Дополнительные сведения об использовании и ограничениях см. в [спецификации расширения](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="f277b-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="f277b-198">Если удаленное приложение использует DX12, вместо XrRemotingFrameMirrorImageD3D11MSFT используйте XrRemotingFrameMirrorImageD3D12MSFT.</span><span class="sxs-lookup"><span data-stu-id="f277b-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="f277b-199">См. также:</span><span class="sxs-lookup"><span data-stu-id="f277b-199">See Also</span></span>
* [<span data-ttu-id="f277b-200">Создание пользовательского проигрывателя для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f277b-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f277b-201">Установка безопасного подключения с использованием голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f277b-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="f277b-202">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="f277b-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f277b-203">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f277b-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f277b-204">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="f277b-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)