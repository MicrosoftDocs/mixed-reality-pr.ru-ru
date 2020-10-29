---
title: Добавление удаленного взаимодействия holographic
description: Объясняется, как с помощью удаленного взаимодействия holographic визуализировать голограммы в HoloLens по сети.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, голограммы, удаленное взаимодействие, удаленная визуализация, подготовка к просмотру сети, HoloLens, удаленные голограммы
ms.openlocfilehash: 0a6cdf34a797a7113c780dee0049125861dd7c32
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692512"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="7cb4a-104">Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))</span><span class="sxs-lookup"><span data-stu-id="7cb4a-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="7cb4a-105">В этом документе описывается создание ведущего приложения для HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="7cb4a-106">Ведущее приложение для **HoloLens (1-го поколения)** должно использовать пакет NuGet версии **1. x. x** .</span><span class="sxs-lookup"><span data-stu-id="7cb4a-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x** .</span></span> <span data-ttu-id="7cb4a-107">Это подразумевает, что ведущие приложения, написанные для HoloLens 1, несовместимы с HoloLens 2 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="7cb4a-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7cb4a-108">HoloLens 2</span></span>

<span data-ttu-id="7cb4a-109">Разработчики HoloLens, использующие holographic удаленное взаимодействие, должны обновить свои приложения, чтобы они были совместимы с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="7cb4a-110">Для этого требуется новая версия пакета NuGet удаленного взаимодействия Holographic.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="7cb4a-111">Если приложение, использующее пакет NuGet для удаленного взаимодействия с номером версии, меньшим 2.0.0.0, пытается подключиться к удаленному проигрывателю holographic с помощью HoloLens 2, произойдет сбой подключения.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="7cb4a-112">Рекомендации, относящиеся к HoloLens 2, можно найти [здесь](holographic-remoting-create-host.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="7cb4a-113">Добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или UWP</span><span class="sxs-lookup"><span data-stu-id="7cb4a-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="7cb4a-114">На этой странице описывается добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или приложений UWP.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="7cb4a-115">Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например Xbox One, что обеспечивает доступ к дополнительным системным ресурсам и делает возможным интеграцию удаленных [иммерсивное представлений](../../design/app-views.md) в существующее программное обеспечение для настольного ПК.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="7cb4a-116">Удаленное приложение узла удаленного взаимодействия получает поток входных данных от HoloLens, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="7cb4a-117">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="7cb4a-118">Для использования удаленного взаимодействия вы будете использовать пакет NuGet для добавления удаленного взаимодействия с настольным компьютером или приложением UWP и написания кода для обработки подключения и визуализации в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="7cb4a-119">Вспомогательные библиотеки включены в пример кода, который упрощает задачу обработки подключения устройства.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="7cb4a-120">Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="7cb4a-121">Приложение проигрывателя может сообщать о задержке в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="7cb4a-122">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7cb4a-123">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="7cb4a-124">Получение пакетов NuGet для удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="7cb4a-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="7cb4a-125">Выполните следующие действия, чтобы получить пакет NuGet для удаленного взаимодействия holographic и добавить ссылку из проекта:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="7cb4a-126">Перейдите к проекту в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="7cb4a-127">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="7cb4a-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="7cb4a-128">На появившейся панели нажмите кнопку **Обзор** и найдите "holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="7cb4a-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="7cb4a-129">Выберите **Microsoft. Holographic. удаленное взаимодействие** и нажмите кнопку **установить** .</span><span class="sxs-lookup"><span data-stu-id="7cb4a-129">Select **Microsoft.Holographic.Remoting** and click **Install** .</span></span>
5. <span data-ttu-id="7cb4a-130">Если откроется диалоговое окно **предварительного просмотра** , нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="7cb4a-130">If the **Preview** dialog appears, click **OK** .</span></span>
6. <span data-ttu-id="7cb4a-131">Следующее появившееся диалоговое окно — это лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="7cb4a-132">Нажмите кнопку **я принимаю** , чтобы принять условия лицензионного соглашения.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="7cb4a-133">Создание Холографикстреамерхелперс</span><span class="sxs-lookup"><span data-stu-id="7cb4a-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="7cb4a-134">Сначала нам нужен экземпляр Холографикстреамерхелперс.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="7cb4a-135">Добавьте его в класс, который будет обрабатывать удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="7cb4a-136">Кроме того, необходимо будет отслеживанию состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-136">You'll also need to track connection state.</span></span> <span data-ttu-id="7cb4a-137">Если вы хотите подготовить к просмотру предварительную версию, необходимо иметь текстуру для копирования.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="7cb4a-138">Кроме того, необходимо выполнить несколько действий, например блокировку состояния подключения, способ хранения IP-адреса HoloLens и т. д.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="7cb4a-139">Инициализация Холографикстреамерхелперс и подключение к HoloLens</span><span class="sxs-lookup"><span data-stu-id="7cb4a-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="7cb4a-140">Чтобы подключиться к устройству HoloLens, создайте экземпляр Холографикстреамерхелперс и подключитесь к целевому IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="7cb4a-141">Необходимо задать размер видеокадра в соответствии с шириной и высотой HoloLens, так как библиотека holographic Remoting предполагает, что декодеры и разрешения кодировщика будут точно соответствовать.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="7cb4a-142">Подключение устройства является асинхронным.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-142">The device connection is asynchronous.</span></span> <span data-ttu-id="7cb4a-143">Приложение должно предоставить обработчики событий для событий подключения, отключения и отправки кадров.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="7cb4a-144">Событие onconnected может обновлять пользовательский интерфейс, начинать отрисовку и т. д.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="7cb4a-145">В нашем примере кода для настольной системы мы обновляем заголовок окна с сообщением "Connected" (подключено).</span><span class="sxs-lookup"><span data-stu-id="7cb4a-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="7cb4a-146">Событие OnDisconnection может поддерживать повторное подключение, обновления пользовательского интерфейса и т. д.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="7cb4a-147">В этом примере мы выполним повторное подключение при наличии временного сбоя.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="7cb4a-148">Когда компонент удаленного взаимодействия готов отправить кадр, приложение предоставляет возможность создать его копию в Сендфрамивент.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="7cb4a-149">Здесь мы копируем фрейм в цепочку буферов, чтобы мы могли отобразить ее в окне предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="7cb4a-150">Прорисовка с holographic содержимым</span><span class="sxs-lookup"><span data-stu-id="7cb4a-150">Render holographic content</span></span>

<span data-ttu-id="7cb4a-151">Для отображения содержимого с помощью удаленного взаимодействия вы настраиваете виртуальные IFrameworkView в приложении для настольных систем или приложения UWP и обрабатываюте holographic-пакеты с удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="7cb4a-152">Все API-интерфейсы Windows holographic аналогичны этому представлению, но настраиваются немного иначе.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="7cb4a-153">Вместо того, чтобы создавать их самостоятельно, компоненты holographic и речи берутся из класса Холографикремотингхелперс:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="7cb4a-154">Вместо того чтобы использовать цикл обновления в методе Run, вы предоставляете обновления тактов из основного цикла рабочего стола или приложения UWP.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="7cb4a-155">Это позволяет рабочему столу или приложению UWP оставаться в управлении обработкой сообщений.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="7cb4a-156">Метод Tick () в представлении приложения holographic завершает одну итерацию обновления, прорисовки, представления цикла.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="7cb4a-157">Цикл обновления, подготовки к просмотру и представления с помощью приложения holographic точно такой же, как и при работе в HoloLens, за исключением того, что у вас есть доступ к гораздо большей части системных ресурсов на настольном компьютере.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="7cb4a-158">Вы можете визуализировать больше треугольников, увеличить число проходов рисования, сделать более физикой и использовать процессы x64 для загрузки содержимого, которое требует более 2 ГБ ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="7cb4a-159">Отключение и завершение удаленного сеанса</span><span class="sxs-lookup"><span data-stu-id="7cb4a-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="7cb4a-160">Для отключения, например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения команды Disconnect () на Холографикстреамерхелперс, а затем освобождает объект.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="7cb4a-161">Получение проигрывателя удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="7cb4a-161">Get the remoting player</span></span>

<span data-ttu-id="7cb4a-162">Проигрыватель удаленного взаимодействия Windows holographic предлагается в магазине приложений Windows в качестве конечной точки для подключения приложений узла удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="7cb4a-163">Чтобы получить проигрыватель удаленного взаимодействия Windows holographic, перейдите в магазин приложений Windows из HoloLens, найдите удаленное взаимодействие и скачайте приложение.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="7cb4a-164">Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, которая может быть полезной при отладке приложений удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="7cb4a-165">Заметки и ресурсы</span><span class="sxs-lookup"><span data-stu-id="7cb4a-165">Notes and resources</span></span>

<span data-ttu-id="7cb4a-166">В представлении с holographic приложений потребуется способ предоставить приложению Direct3D-устройство, которое должно использоваться для инициализации Holographic.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="7cb4a-167">Приложение должно использовать это устройство Direct3D для копирования и вывода кадра предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="7cb4a-168">**Пример кода:** Доступен полный пример кода с удаленным взаимодействием holographic, включающий представление приложения holographic, совместимое с удаленным взаимодействием и проектами удаленного взаимодействия для настольных приложений Win32, UWP DirectX и UWP с XAML.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="7cb4a-169">Чтобы получить его, перейдите по следующему адресу:</span><span class="sxs-lookup"><span data-stu-id="7cb4a-169">To get it, go here:</span></span>
* [<span data-ttu-id="7cb4a-170">Пример Windows holographic для удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="7cb4a-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="7cb4a-171">**Примечание к отладке:** Библиотека holographic Remoting может создавать исключения с первого шанса.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="7cb4a-172">Эти исключения могут отображаться в сеансах отладки в зависимости от параметров исключений Visual Studio, которые активны в момент времени.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="7cb4a-173">Эти исключения захватываются внутри библиотеки holographic Remoting и могут быть пропущены.</span><span class="sxs-lookup"><span data-stu-id="7cb4a-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
