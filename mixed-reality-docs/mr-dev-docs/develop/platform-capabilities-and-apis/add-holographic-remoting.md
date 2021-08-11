---
title: Добавление удаленного взаимодействия holographic
description: узнайте, как установить, настроить и использовать holographic удаленное взаимодействие, чтобы визуализировать голограммы на HoloLens устройстве по сети.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, удаленное взаимодействие, дистанционная визуализация, подготовка к просмотру сети, HoloLens, удаленные голограммы, гарнитура смешанной реальности, гарнитура Windows Mixed reality, гарнитура виртуальной реальности
ms.openlocfilehash: ecfc49477e202b08303160e54ce986577a9d79eb387dc1edb1bc33c63644615f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198860"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>добавить удаленное взаимодействие с holographic (HoloLens (первые поколения))

>[!IMPORTANT]
> в этом документе описывается создание ведущего приложения для HoloLens 1. ведущее приложение для **HoloLens (1 общий)** должно использовать NuGet пакета версии **1. x. x**. это подразумевает, что ведущие приложения, написанные для HoloLens 1, несовместимы с HoloLens 2 и наоборот.

## <a name="hololens-2"></a>HoloLens 2

HoloLens разработчикам, использующим holographic удаленное взаимодействие, потребуется обновить свои приложения, чтобы они были совместимы с HoloLens 2. для этого требуется новая версия пакета NuGet holographic с удаленным взаимодействием. при подключении к удаленному проигрывателю holographic на HoloLens 2 или при подключении произойдет сбой, обязательно используйте версию 2.0.0.0 или выше для пакета NuGet holographic remoting.

>[!NOTE]
> рекомендации, относящиеся к HoloLens 2, можно найти [здесь](holographic-remoting-create-remote-wmr.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или UWP

На этой странице описывается добавление удаленного взаимодействия holographic в приложение для настольных компьютеров или приложений UWP.

holographic удаленное взаимодействие позволяет приложению выбрать HoloLens с holographic-содержимым, размещенным на настольном компьютере или на устройстве UWP, например Xbox One. Кроме того, у вас есть доступ к дополнительным системным ресурсам, что позволяет интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК. удаленное приложение узла удаленного взаимодействия получает поток входных данных из HoloLens, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens. Подключение устанавливается с использованием стандартного Wi-Fi. чтобы использовать удаленное взаимодействие, используйте пакет NuGet, чтобы добавить holographic удаленное взаимодействие в приложение для настольных систем или приложения UWP, а затем напишите код для обработки соединения и отображения иммерсивного представления. Вспомогательные библиотеки включены в пример кода, который упрощает задачу обработки подключения устройства.

Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](../native/creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

### <a name="get-the-remoting-nuget-packages"></a>получение пакетов NuGet удаленного взаимодействия

выполните следующие действия, чтобы получить пакет NuGet для удаленного взаимодействия holographic и добавить ссылку из проекта:
1. Перейдите к проекту в Visual Studio.
2. щелкните правой кнопкой мыши узел проекта и выберите пункт **управление пакетами NuGet...**
3. На появившейся панели селеккт **Обзор** и выполните поиск по фразе "удаленное взаимодействие" (holographic Remoting).
4. Выберите **Microsoft. Holographic. удаленное взаимодействие** и селеккт **Install**.
5. Если отображается диалоговое окно **Предварительный просмотр** , нажмите кнопку **ОК**.
6. Выберите **я принимаю** , когда откроется диалоговое окно Лицензионное соглашение.

### <a name="create-the-holographicstreamerhelpers"></a>Создание Холографикстреамерхелперс

Сначала необходимо добавить экземпляр Холографикстреамерхелперс в класс, который будет обслуживать удаленное взаимодействие.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Кроме того, необходимо будет отслеживанию состояния соединения. Если вы хотите подготовить к просмотру предварительную версию, необходимо иметь текстуру для копирования. кроме того, необходимо выполнить некоторые действия, например блокировку состояния подключения, способ хранения IP-адреса HoloLens и т. д.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Инициализация Холографикстреамерхелперс и подключение к HoloLens

чтобы подключиться к HoloLens устройству, создайте экземпляр холографикстреамерхелперс и подключитесь к целевому IP-адресу. необходимо задать размер кадра видео в соответствии с HoloLens отображаемой шириной и высотой, так как библиотека holographic удаленного взаимодействия предполагает, что разрешения кодировщика и декодера полностью совпадают.

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

Подключение устройства является асинхронным. Приложение должно предоставить обработчики событий для событий подключения, отключения и отправки кадров.

Событие onconnected может обновлять пользовательский интерфейс, начинать отрисовку и т. д. В нашем примере кода для настольной системы мы обновляем заголовок окна с сообщением "Connected" (подключено).

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Событие OnDisconnection может поддерживать повторное подключение, обновления пользовательского интерфейса и т. д. В этом примере мы выполним повторное подключение при наличии временного сбоя.

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

Когда компонент удаленного взаимодействия готов отправить кадр, приложение предоставляет возможность создать его копию в Сендфрамивент. Здесь мы копируем фрейм в цепочку буферов, чтобы мы могли отобразить ее в окне предварительного просмотра.

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

### <a name="render-holographic-content"></a>Прорисовка с holographic содержимым

Для отображения содержимого с помощью удаленного взаимодействия вы настраиваете виртуальные IFrameworkView в приложении для настольных систем или приложения UWP и обрабатываюте holographic-пакеты с удаленного взаимодействия. все Windows holographic api в этом представлении используются одинаково, но они настраиваются немного иначе.

Вместо того, чтобы создавать их самостоятельно, компоненты holographic и речи берутся из класса Холографикремотингхелперс:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Вместо использования цикла обновления в методе Run вы предоставляете обновления тактов из главного цикла приложения UWP или рабочего стола. Это позволяет рабочему столу или приложению UWP оставаться в управлении обработкой сообщений.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Метод Tick () в представлении приложения holographic завершает одну итерацию обновления, прорисовки, представления цикла.

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

цикл обновления, подготовки к просмотру и показу приложений с помощью приложения holographic точно такой же, как и при работе на HoloLens, за исключением того, что у вас есть доступ к гораздо большей части системных ресурсов на настольном компьютере. Вы можете визуализировать больше треугольников, увеличить число проходов рисования, сделать более физикой и использовать процессы x64 для загрузки содержимого, которое требует более 2 ГБ ОЗУ.

### <a name="disconnect-and-end-the-remote-session"></a>Отключение и завершение удаленного сеанса

Для отключения, например, когда пользователь нажимает кнопку пользовательского интерфейса для отключения команды Disconnect () на Холографикстреамерхелперс, а затем освобождает объект.

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

## <a name="get-the-remoting-player"></a>Получение проигрывателя удаленного взаимодействия

Windows holographic remoting player предлагается в Windows app store в качестве конечной точки для подключения приложений узла удаленного взаимодействия. чтобы получить Windows holographic remoting, посетите Windows app store из HoloLens, выполните поиск удаленного взаимодействия и скачайте приложение. Проигрыватель удаленного взаимодействия включает функцию для отображения статистики на экране, которая может быть полезной при отладке приложений удаленного узла.

## <a name="notes-and-resources"></a>Заметки и ресурсы

В представлении с holographic приложений потребуется способ предоставить приложению Direct3D-устройство, которое должно использоваться для инициализации Holographic. Приложение должно использовать это устройство Direct3D для копирования и вывода кадра предварительного просмотра.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Пример кода:** Доступен полный [пример кода с удаленным взаимодействием holographic](https://github.com/Microsoft/HoloLensCompanionKit) , включающий представление приложения holographic, совместимое с удаленным взаимодействием и проектами удаленного взаимодействия для настольных приложений Win32, UWP DirectX и UWP с XAML. 

**Примечание к отладке:** Библиотека holographic Remoting может создавать исключения с первого шанса. эти исключения могут отображаться в сеансах отладки в зависимости от Visual Studio параметров исключений, которые активны в момент времени. Эти исключения захватываются внутри библиотеки holographic Remoting и могут быть пропущены.
