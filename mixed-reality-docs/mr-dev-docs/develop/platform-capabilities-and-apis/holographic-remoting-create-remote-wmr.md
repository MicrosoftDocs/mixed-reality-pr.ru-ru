---
title: Создание удаленного приложения holographic с удаленным взаимодействием (ВМР)
description: Создав удаленное содержимое удаленного приложения с удаленным удаленным доступом, которое будет отображаться на удаленном компьютере, можно передать потоковую передачу в HoloLens 2. В этой статье описывается, как это можно сделать.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, NuGet
ms.openlocfilehash: 3bbb75d9f1b6db64326f5b429103828266650a52
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469523"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="13c4d-105">Создание удаленного приложения holographic с удаленным взаимодействием с помощью API Холографикспаце</span><span class="sxs-lookup"><span data-stu-id="13c4d-105">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="13c4d-106">В этом документе описывается создание удаленного приложения для HoloLens 2 с помощью [API холографикспаце](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="13c4d-106">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="13c4d-107">Удаленные приложения для **HoloLens (1-го поколения)** должны использовать пакет NuGet версии **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="13c4d-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="13c4d-108">Это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="13c4d-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="13c4d-109">Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="13c4d-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="13c4d-110">При создании удаленного приложения с удаленным удаленным доступом удаленное содержимое, отображаемое на удаленном компьютере, можно передать в HoloLens 2 и иммерсивное устройство, например гарнитуры Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="13c4d-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="13c4d-111">В этой статье описывается, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="13c4d-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="13c4d-112">Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="13c4d-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="13c4d-113">Holographic удаленное взаимодействие позволяет приложению ориентироваться на гарнитуры HoloLens 2 и Windows Mixed Reality с holographic-содержимым, отображаемым на настольном компьютере или на устройстве UWP, например на Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и позволяет интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК.</span><span class="sxs-lookup"><span data-stu-id="13c4d-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="13c4d-114">Удаленное приложение получает поток входных данных из HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="13c4d-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="13c4d-115">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="13c4d-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="13c4d-116">Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="13c4d-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="13c4d-117">Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="13c4d-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="13c4d-118">Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки.</span><span class="sxs-lookup"><span data-stu-id="13c4d-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="13c4d-119">Приложение проигрывателя может сообщать о задержке в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="13c4d-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13c4d-120">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="13c4d-120">Prerequisites</span></span>

<span data-ttu-id="13c4d-121">Хорошей отправной точкой является работа рабочего стола на основе DirectX или приложения UWP, предназначенного для [API холографикспаце](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="13c4d-121">A good starting point is a working DirectX based Desktop or UWP app which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="13c4d-122">Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="13c4d-122">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="13c4d-123">[Шаблон проекта с + + holographic](../native/creating-a-holographic-directx-project.md) является хорошей отправной точкой.</span><span class="sxs-lookup"><span data-stu-id="13c4d-123">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="13c4d-124">Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="13c4d-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="13c4d-125">Использование [однопотокового подразделения](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="13c4d-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="13c4d-126">При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="13c4d-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="13c4d-127">Получение пакета NuGet для удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="13c4d-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="13c4d-128">Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="13c4d-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="13c4d-129">Откройте проект в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13c4d-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="13c4d-130">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="13c4d-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="13c4d-131">На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="13c4d-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="13c4d-132">Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="13c4d-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="13c4d-133">Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="13c4d-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="13c4d-134">Следующее появившееся диалоговое окно — это лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="13c4d-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="13c4d-135">Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="13c4d-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="13c4d-136">Версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, желающих выбрать HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="13c4d-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="13c4d-137">Дополнительные сведения см. в разделе [Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="13c4d-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="13c4d-138">Создание удаленного контекста</span><span class="sxs-lookup"><span data-stu-id="13c4d-138">Create the remote context</span></span>

<span data-ttu-id="13c4d-139">В качестве первого шага приложение должно создать удаленный контекст.</span><span class="sxs-lookup"><span data-stu-id="13c4d-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="13c4d-140">Holographic удаленное взаимодействие выполняется путем замены среды выполнения Windows Mixed Reality, которая является частью Windows, на среду выполнения с удаленным взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="13c4d-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="13c4d-141">Это делается во время создания удаленного контекста.</span><span class="sxs-lookup"><span data-stu-id="13c4d-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="13c4d-142">По этой причине любой вызов любого API Windows Mixed Reality перед созданием удаленного контекста может привести к непредвиденному поведению.</span><span class="sxs-lookup"><span data-stu-id="13c4d-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="13c4d-143">Рекомендуемый подход состоит в том, чтобы создать удаленный контекст как можно раньше перед взаимодействием с любым API смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="13c4d-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="13c4d-144">Никогда не смешивать объекты, созданные или полученные через API Windows Mixed Reality до вызова Креатеремотеконтекст с объектами, созданными или полученными позже.</span><span class="sxs-lookup"><span data-stu-id="13c4d-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="13c4d-145">После этого необходимо создать новый Holographic.</span><span class="sxs-lookup"><span data-stu-id="13c4d-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="13c4d-146">Указывать CoreWindow не требуется.</span><span class="sxs-lookup"><span data-stu-id="13c4d-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="13c4d-147">Классические приложения, у которых нет CoreWindowа, могут просто передать ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="13c4d-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="13c4d-148">Подключение к устройству</span><span class="sxs-lookup"><span data-stu-id="13c4d-148">Connect to the device</span></span>

<span data-ttu-id="13c4d-149">Когда удаленное приложение будет готово к отрисовке содержимого, можно установить подключение к устройству проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="13c4d-149">Once the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="13c4d-150">Соединение может быть выполнено одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="13c4d-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="13c4d-151">Удаленное приложение подключается к проигрывателю, работающему на устройстве.</span><span class="sxs-lookup"><span data-stu-id="13c4d-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="13c4d-152">Проигрыватель, выполняющийся на устройстве, подключается к удаленному приложению.</span><span class="sxs-lookup"><span data-stu-id="13c4d-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="13c4d-153">Чтобы установить подключение из удаленного приложения к устройству проигрывателя, вызовите ```Connect``` метод в удаленном контексте, указав имя узла и порт.</span><span class="sxs-lookup"><span data-stu-id="13c4d-153">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="13c4d-154">Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.</span><span class="sxs-lookup"><span data-stu-id="13c4d-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="13c4d-155">Как и в случае любого API-интерфейса C++/WinRT, ```Connect``` может возникнуть исключение WinRT:: hresult_error, которое необходимо обработать.</span><span class="sxs-lookup"><span data-stu-id="13c4d-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="13c4d-156">Чтобы избежать использования проекции языка [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) , ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` можно добавить файл, расположенный внутри пакета NuGet удаленного взаимодействия с удаленным доступом.</span><span class="sxs-lookup"><span data-stu-id="13c4d-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="13c4d-157">Он содержит объявления базовых COM-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="13c4d-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="13c4d-158">Однако рекомендуется использовать C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="13c4d-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="13c4d-159">Прослушивание входящих подключений в удаленном приложении можно выполнить, вызвав ```Listen``` метод.</span><span class="sxs-lookup"><span data-stu-id="13c4d-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="13c4d-160">Во время этого вызова можно указать как порт подтверждения, так и порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="13c4d-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="13c4d-161">Порт подтверждения используется для первоначального подтверждения.</span><span class="sxs-lookup"><span data-stu-id="13c4d-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="13c4d-162">Затем данные пересылаются через порт транспорта.</span><span class="sxs-lookup"><span data-stu-id="13c4d-162">The data is then send over the transport port.</span></span> <span data-ttu-id="13c4d-163">По умолчанию используются **8265** и **8266** .</span><span class="sxs-lookup"><span data-stu-id="13c4d-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="13c4d-164">В ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` пакете NuGet содержится подробная документация по API, предоставляемому с помощью holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="13c4d-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="13c4d-165">Обработка событий, связанных с удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="13c4d-165">Handling Remoting specific events</span></span>

<span data-ttu-id="13c4d-166">Удаленный контекст предоставляет три события, которые важны для отслеживания состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="13c4d-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="13c4d-167">Подключено: активируется при успешном установлении подключения к устройству.</span><span class="sxs-lookup"><span data-stu-id="13c4d-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="13c4d-168">Ondisconnectо: активируется, если установленное соединение закрыто или не удалось установить подключение.</span><span class="sxs-lookup"><span data-stu-id="13c4d-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="13c4d-169">Идет ожидание: при прослушивании входящих подключений начинается.</span><span class="sxs-lookup"><span data-stu-id="13c4d-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="13c4d-170">Кроме того, состояние соединения можно запросить с помощью ```ConnectionState``` свойства в удаленном контексте.</span><span class="sxs-lookup"><span data-stu-id="13c4d-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="13c4d-171">Обработка событий речи</span><span class="sxs-lookup"><span data-stu-id="13c4d-171">Handling speech events</span></span>

<span data-ttu-id="13c4d-172">С помощью удаленного речевого интерфейса можно зарегистрировать речевые триггеры в HoloLens 2 и удаленно взаимодействовать с удаленным приложением.</span><span class="sxs-lookup"><span data-stu-id="13c4d-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="13c4d-173">Этот дополнительный элемент необходим для отслеживания состояния удаленного распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="13c4d-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="13c4d-174">Сначала необходимо получить удаленный речевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="13c4d-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="13c4d-175">С помощью асинхронного вспомогательного метода можно инициализировать удаленный голос.</span><span class="sxs-lookup"><span data-stu-id="13c4d-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="13c4d-176">Это необходимо сделать асинхронно, так как инициализация может занять значительное время.</span><span class="sxs-lookup"><span data-stu-id="13c4d-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="13c4d-177">[Параллельные и асинхронные операции с c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) объясняет, как создавать асинхронные функции с помощью c++/винрт.</span><span class="sxs-lookup"><span data-stu-id="13c4d-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="13c4d-178">Существует два способа указания фраз для распознавания.</span><span class="sxs-lookup"><span data-stu-id="13c4d-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="13c4d-179">Спецификация внутри XML-файла грамматики речи.</span><span class="sxs-lookup"><span data-stu-id="13c4d-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="13c4d-180">Дополнительные сведения см. [в статье Создание базовой грамматики XML](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="13c4d-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="13c4d-181">Укажите, передав их в векторе словаря в ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="13c4d-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="13c4d-182">Внутри обратного вызова Онрекогнизедспич можно обработать события речи:</span><span class="sxs-lookup"><span data-stu-id="13c4d-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="13c4d-183">Предварительный просмотр потокового содержимого на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="13c4d-183">Preview streamed content locally</span></span>

<span data-ttu-id="13c4d-184">Чтобы отобразить то же содержимое в удаленном приложении, которое отправляется на устройство, ```OnSendFrame``` можно использовать событие удаленного контекста.</span><span class="sxs-lookup"><span data-stu-id="13c4d-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="13c4d-185">```OnSendFrame```Событие активируется каждый раз, когда в удаленной библиотеке holographic текущий кадр отправляется на удаленное устройство.</span><span class="sxs-lookup"><span data-stu-id="13c4d-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="13c4d-186">Это идеальное время для получения содержимого, а также Блит его в окно рабочего стола или UWP.</span><span class="sxs-lookup"><span data-stu-id="13c4d-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="13c4d-187">Репроектная глубина</span><span class="sxs-lookup"><span data-stu-id="13c4d-187">Depth Reprojection</span></span>

<span data-ttu-id="13c4d-188">Начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0), holographic удаленное взаимодействие поддерживает [репроекцию с глубиной](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="13c4d-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="13c4d-189">Для этого в дополнение к буферу цвета также требуется потоковая передача буфера глубины из удаленного приложения в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="13c4d-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="13c4d-190">По умолчанию потоковая передача буфера глубины включена и настроена для использования половины разрешения буфера цвета.</span><span class="sxs-lookup"><span data-stu-id="13c4d-190">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="13c4d-191">Это можно изменить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="13c4d-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="13c4d-192">Обратите внимание, что если не следует использовать значения по умолчанию, ```ConfigureDepthVideoStream``` необходимо вызвать метод перед установкой соединения с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="13c4d-192">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="13c4d-193">Лучшее место будет сразу после создания удаленного контекста.</span><span class="sxs-lookup"><span data-stu-id="13c4d-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="13c4d-194">Возможные значения для Депсбуфферстреамресолутион:</span><span class="sxs-lookup"><span data-stu-id="13c4d-194">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="13c4d-195">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="13c4d-195">Full_Resolution</span></span>
* <span data-ttu-id="13c4d-196">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="13c4d-196">Half_Resolution</span></span>
* <span data-ttu-id="13c4d-197">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="13c4d-197">Quarter_Resolution</span></span>
* <span data-ttu-id="13c4d-198">Отключено (добавляется с версией [2.1.3](holographic-remoting-version-history.md#v2.1.3) и при использовании дополнительного видеопотока глубины не создается)</span><span class="sxs-lookup"><span data-stu-id="13c4d-198">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="13c4d-199">Помните, что использование буфера глубины полного разрешения также влияет на требования к пропускной способности и должно учитывать максимальное значение пропускной способности, которое вы предоставляете ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="13c4d-199">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="13c4d-200">При настройке разрешения необходимо также зафиксировать буфер глубины с помощью [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="13c4d-200">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="13c4d-201">Чтобы проверить правильность работы РЕПРОЕКЦИИ в HoloLens 2, можно включить визуализатор глубины с помощью портала устройств.</span><span class="sxs-lookup"><span data-stu-id="13c4d-201">To verify if depth reprojection is correctly working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="13c4d-202">Дополнительные сведения см. в разделе [Проверка глубины правильно настроена](hologram-stability.md#verifying-depth-is-set-correctly) .</span><span class="sxs-lookup"><span data-stu-id="13c4d-202">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="13c4d-203">Необязательно: пользовательские каналы данных</span><span class="sxs-lookup"><span data-stu-id="13c4d-203">Optional: Custom data channels</span></span>

<span data-ttu-id="13c4d-204">Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение.</span><span class="sxs-lookup"><span data-stu-id="13c4d-204">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="13c4d-205">Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="13c4d-205">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="13c4d-206">См. также:</span><span class="sxs-lookup"><span data-stu-id="13c4d-206">See Also</span></span>
* [<span data-ttu-id="13c4d-207">Создание пользовательского проигрывателя для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="13c4d-207">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="13c4d-208">Пользовательские каналы данных с голографическим удаленным взаимодействием</span><span class="sxs-lookup"><span data-stu-id="13c4d-208">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="13c4d-209">Установка безопасного подключения с использованием голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="13c4d-209">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="13c4d-210">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="13c4d-210">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="13c4d-211">Условия лицензии на использование ПО для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="13c4d-211">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="13c4d-212">Заявление о конфиденциальности Майкрософт</span><span class="sxs-lookup"><span data-stu-id="13c4d-212">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
