---
title: Добавление удаленного взаимодействия holographic
description: Объясняется, как с помощью удаленного взаимодействия holographic визуализировать голограммы в HoloLens по сети.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, удаленное взаимодействие, удаленная подготовка к просмотру сети, HoloLens, голограммы на удаленных языках, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 809258d3387b5e45885c0eb207544c176f891a1d
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530305"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="f2ec0-104">Добавление удаленного взаимодействия с holographic (HoloLens (первый общий))</span><span class="sxs-lookup"><span data-stu-id="f2ec0-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f2ec0-105">В этом документе описывается создание ведущего приложения для HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="f2ec0-106">Ведущее приложение для **HoloLens (1-го поколения)** должно использовать пакет NuGet версии **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="f2ec0-107">Это подразумевает, что ведущие приложения, написанные для HoloLens 1, несовместимы с HoloLens 2 и наоборот.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="f2ec0-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f2ec0-108">HoloLens 2</span></span>

<span data-ttu-id="f2ec0-109">Разработчики HoloLens, использующие holographic удаленное взаимодействие, должны обновить свои приложения, чтобы они были совместимы с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="f2ec0-110">Для этого требуется новая версия пакета NuGet удаленного взаимодействия Holographic.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="f2ec0-111">При подключении к удаленному проигрывателю holographic в HoloLens 2 используйте версию 2.0.0.0 или более позднюю из пакетов NuGet удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="f2ec0-112">Рекомендации, относящиеся к HoloLens 2, можно найти [здесь](holographic-remoting-create-remote-wmr.md).</span><span class="sxs-lookup"><span data-stu-id="f2ec0-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="f2ec0-113">Добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или UWP</span><span class="sxs-lookup"><span data-stu-id="f2ec0-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="f2ec0-114">На этой странице описывается добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или приложений UWP.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="f2ec0-115">Holographic удаленное взаимодействие позволяет приложению ориентироваться на HoloLens с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например на Xbox One.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="f2ec0-116">Кроме того, у вас есть доступ к дополнительным системным ресурсам, что позволяет интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="f2ec0-117">Удаленное приложение узла удаленного взаимодействия получает поток входных данных от HoloLens, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="f2ec0-118">Подключение устанавливается с использованием стандартного Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="f2ec0-119">Чтобы использовать удаленное взаимодействие, используйте пакет NuGet, чтобы добавить holographic удаленное взаимодействие в приложение для настольных систем или приложения UWP, а затем напишите код для обработки соединения и отображения иммерсивного представления.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="f2ec0-120">Вспомогательные библиотеки включены в пример кода, который упрощает задачу обработки подключения устройства.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="f2ec0-121">Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="f2ec0-122">Приложение проигрывателя может сообщать о задержке в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="f2ec0-123">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="f2ec0-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f2ec0-124">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="f2ec0-125">Получение пакетов NuGet для удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f2ec0-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="f2ec0-126">Выполните следующие действия, чтобы получить пакет NuGet для удаленного взаимодействия holographic и добавить ссылку из проекта:</span><span class="sxs-lookup"><span data-stu-id="f2ec0-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="f2ec0-127">Перейдите к проекту в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="f2ec0-128">Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="f2ec0-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="f2ec0-129">На появившейся панели селеккт **Обзор** и выполните поиск по фразе "удаленное взаимодействие" (holographic Remoting).</span><span class="sxs-lookup"><span data-stu-id="f2ec0-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="f2ec0-130">Выберите **Microsoft. Holographic. удаленное взаимодействие** и селеккт **Install**.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="f2ec0-131">Если отображается диалоговое окно **Предварительный просмотр** , нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="f2ec0-132">Выберите **я принимаю** , когда откроется диалоговое окно Лицензионное соглашение.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="f2ec0-133">Создание Холографикстреамерхелперс</span><span class="sxs-lookup"><span data-stu-id="f2ec0-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="f2ec0-134">Сначала необходимо добавить экземпляр Холографикстреамерхелперс в класс, который будет обслуживать удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="f2ec0-135">Кроме того, необходимо будет отслеживанию состояния соединения.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-135">You'll also need to track connection state.</span></span> <span data-ttu-id="f2ec0-136">Если вы хотите подготовить к просмотру предварительную версию, необходимо иметь текстуру для копирования.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="f2ec0-137">Кроме того, необходимо выполнить несколько действий, например блокировку состояния подключения, способ хранения IP-адреса HoloLens и т. д.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="f2ec0-138">Инициализация Холографикстреамерхелперс и подключение к HoloLens</span><span class="sxs-lookup"><span data-stu-id="f2ec0-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="f2ec0-139">Чтобы подключиться к устройству HoloLens, создайте экземпляр Холографикстреамерхелперс и подключитесь к целевому IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="f2ec0-140">Необходимо задать размер видеокадра в соответствии с шириной и высотой HoloLens, так как библиотека holographic Remoting предполагает, что декодеры и разрешения кодировщика полностью совпадают.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="f2ec0-141">Подключение устройства является асинхронным.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-141">The device connection is asynchronous.</span></span> <span data-ttu-id="f2ec0-142">Приложение должно предоставить обработчики событий для событий подключения, отключения и отправки кадров.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="f2ec0-143">Событие onconnected может обновлять пользовательский интерфейс, начинать отрисовку и т. д.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="f2ec0-144">В нашем примере кода для настольной системы мы обновляем заголовок окна с сообщением "Connected" (подключено).</span><span class="sxs-lookup"><span data-stu-id="f2ec0-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="f2ec0-145">Событие OnDisconnection может поддерживать повторное подключение, обновления пользовательского интерфейса и т. д.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="f2ec0-146">В этом примере мы выполним повторное подключение при наличии временного сбоя.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-146">In this example, we reconnect if there's a transient failure.</span></span>

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

<span data-ttu-id="f2ec0-147">Когда компонент удаленного взаимодействия готов отправить кадр, приложение предоставляет возможность создать его копию в Сендфрамивент.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="f2ec0-148">Здесь мы копируем фрейм в цепочку буферов, чтобы мы могли отобразить ее в окне предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="f2ec0-149">Прорисовка с holographic содержимым</span><span class="sxs-lookup"><span data-stu-id="f2ec0-149">Render holographic content</span></span>

<span data-ttu-id="f2ec0-150">Для отображения содержимого с помощью удаленного взаимодействия вы настраиваете виртуальные IFrameworkView в приложении для настольных систем или приложения UWP и обрабатываюте holographic-пакеты с удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="f2ec0-151">Все API-интерфейсы Windows holographic по-разному используются в этом представлении, но настраиваются немного иначе.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="f2ec0-152">Вместо того, чтобы создавать их самостоятельно, компоненты holographic и речи берутся из класса Холографикремотингхелперс:</span><span class="sxs-lookup"><span data-stu-id="f2ec0-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="f2ec0-153">Вместо использования цикла обновления в методе Run вы предоставляете обновления тактов из главного цикла приложения UWP или рабочего стола.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="f2ec0-154">Это позволяет рабочему столу или приложению UWP оставаться в управлении обработкой сообщений.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="f2ec0-155">Метод Tick () в представлении приложения holographic завершает одну итерацию обновления, прорисовки, представления цикла.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="f2ec0-156">Цикл обновления, подготовки к просмотру и представления с помощью приложения holographic точно так же, как и при работе в HoloLens, за исключением того, что у вас есть доступ к гораздо большей части системных ресурсов на настольном компьютере.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="f2ec0-157">Вы можете визуализировать больше треугольников, увеличить число проходов рисования, сделать более физикой и использовать процессы x64 для загрузки содержимого, которое требует более 2 ГБ ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="f2ec0-158">Отключение и завершение удаленного сеанса</span><span class="sxs-lookup"><span data-stu-id="f2ec0-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="f2ec0-159">Для отключения, например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения команды Disconnect () на Холографикстреамерхелперс, а затем освобождает объект.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="f2ec0-160">Получение проигрывателя удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f2ec0-160">Get the remoting player</span></span>

<span data-ttu-id="f2ec0-161">Проигрыватель удаленного взаимодействия Windows holographic предлагается в магазине приложений Windows в качестве конечной точки для подключения приложений узла удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="f2ec0-162">Чтобы получить проигрыватель удаленного взаимодействия Windows holographic, перейдите в магазин приложений Windows из HoloLens, найдите удаленное взаимодействие и скачайте приложение.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="f2ec0-163">Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, которая может быть полезной при отладке приложений удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="f2ec0-164">Заметки и ресурсы</span><span class="sxs-lookup"><span data-stu-id="f2ec0-164">Notes and resources</span></span>

<span data-ttu-id="f2ec0-165">В представлении с holographic приложений потребуется способ предоставить приложению Direct3D-устройство, которое должно использоваться для инициализации Holographic.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="f2ec0-166">Приложение должно использовать это устройство Direct3D для копирования и вывода кадра предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="f2ec0-167">**Пример кода:** Доступен полный [пример кода с удаленным взаимодействием holographic](https://github.com/Microsoft/HoloLensCompanionKit) , включающий представление приложения holographic, совместимое с удаленным взаимодействием и проектами удаленного взаимодействия для настольных приложений Win32, UWP DirectX и UWP с XAML.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="f2ec0-168">**Примечание к отладке:** Библиотека holographic Remoting может создавать исключения с первого шанса.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="f2ec0-169">Эти исключения могут отображаться в сеансах отладки в зависимости от параметров исключений Visual Studio, которые активны в момент времени.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="f2ec0-170">Эти исключения захватываются внутри библиотеки holographic Remoting и могут быть пропущены.</span><span class="sxs-lookup"><span data-stu-id="f2ec0-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
