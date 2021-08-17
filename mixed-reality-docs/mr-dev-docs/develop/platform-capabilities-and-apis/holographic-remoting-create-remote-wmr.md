---
title: Создание удаленного приложения holographic с удаленным взаимодействием (ВМР)
description: узнайте, как выполнять потоковую передачу удаленного содержимого, отображаемого на удаленном компьютере, для HoloLens 2 с помощью приложений holographic с удаленным доступом с помощью холографикспаце.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие, гарнитура смешанной реальности, гарнитура windows mixed reality, гарнитура виртуальной реальности, NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184725"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Создание удаленного приложения holographic с удаленным взаимодействием с помощью API Холографикспаце

>[!IMPORTANT]
>в этом документе описывается создание удаленного приложения для HoloLens 2 с помощью [API холографикспаце](../native/getting-a-holographicspace.md). удаленные приложения для **HoloLens (1-го поколения)** должны использовать NuGet пакета версии **1. x. x**. это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот. документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).

в приложениях с удаленным взаимодействием можно передавать содержимое с удаленного просмотра на HoloLens 2 и Windows Mixed Reality впечатляющие головные телефоны. Вы также можете получить доступ к дополнительным системным ресурсам и интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК. удаленное приложение получает поток входных данных от HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2. Подключение устанавливается с использованием стандартного Wi-Fi. holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP с помощью пакета NuGet. Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения. Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Необходимые компоненты

Хорошей отправной точкой является работающая Рабочая станция на основе DirectX или приложение UWP, которое предназначено для [API холографикспаце](../native/getting-a-holographicspace.md). Дополнительные сведения см. в статье [Общие сведения о разработке DirectX](../native/directx-development-overview.md). [Шаблон проекта с + + holographic](../native/creating-a-holographic-directx-project.md) является хорошей отправной точкой.

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](/windows/win32/com/multithreaded-apartments). Использование [однопотокового подразделения](/windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.



## <a name="get-the-holographic-remoting-nuget-package"></a>получение пакета NuGet holographic для удаленного взаимодействия

чтобы добавить NuGet пакет в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. щелкните правой кнопкой мыши узел проекта и выберите пункт **управление NuGet пакетами...**
3. На появившейся панели нажмите кнопку **Обзор** и выполните поиск по фразе "удаленное взаимодействие".
4. Выберите **Microsoft. Holographic. удаленное взаимодействие**, обязательно выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.
5. Если отображается диалоговое окно **Предварительный просмотр** , нажмите кнопку **ОК**.
6. Выберите **я принимаю** , когда появится диалоговое окно Лицензионное соглашение.

>[!NOTE]
>версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, которые хотят ориентироваться HoloLens 1. дополнительные сведения см. в разделе [добавление удаленного взаимодействия с holographic (HoloLens (1-й общий))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Создание удаленного контекста

В качестве первого шага приложение должно создать удаленный контекст.

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
>holographic удаленное взаимодействие работает путем замены среды выполнения Windows Mixed Reality, которая является частью Windows с помощью среды выполнения с удаленным взаимодействием. Это делается во время создания удаленного контекста. по этой причине любой вызов любого Windows Mixed Reality API перед созданием удаленного контекста может привести к непредвиденному поведению. Рекомендуемый подход состоит в том, чтобы создать удаленный контекст как можно раньше перед взаимодействием с любым API смешанной реальности. никогда не создавайте объекты, созданные или полученные через API Windows Mixed Reality до вызова креатеремотеконтекст с объектами, созданными или полученными позже.

После этого необходимо создать новый Holographic. Указание CoreWindow не требуется. Классические приложения, у которых нет CoreWindowа, могут просто передать ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Подключение на устройство

Когда удаленное приложение готово к отрисовке содержимого, можно установить подключение к устройству проигрывателя.

Соединение может быть выполнено одним из двух способов.
1) Удаленное приложение подключается к проигрывателю, работающему на устройстве.
2) Проигрыватель, выполняющийся на устройстве, подключается к удаленному приложению.

Чтобы установить подключение из удаленного приложения к устройству проигрывателя, вызовите ```Connect``` метод в удаленном контексте, указав имя узла и порт. Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.

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
>Как и в случае любого API-интерфейса C++/WinRT, ```Connect``` может возникнуть исключение WinRT:: hresult_error, которое необходимо обработать.

>[!TIP]
>чтобы избежать использования проекции языка [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) , ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` можно добавить файл, расположенный в пакете NuGet с удаленным взаимодействием holographic. Он содержит объявления базовых COM-интерфейсов. Однако рекомендуется использовать C++/WinRT.

Прослушивание входящих подключений в удаленном приложении можно выполнить, вызвав ```Listen``` метод. Во время этого вызова можно указать как порт подтверждения, так и порт транспорта. Порт подтверждения используется для первоначального подтверждения. Затем данные отправляются через порт транспорта. По умолчанию используются **8265** и **8266** .

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
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```внутри пакета NuGet содержит подробную документацию по API, предоставляемому с помощью holographic remoting.

## <a name="handling-remoting-specific-events"></a>Обработка событий, связанных с удаленным взаимодействием

Удаленный контекст предоставляет три события, которые важны для отслеживания состояния соединения.
1) Подключено: активируется при успешном установлении подключения к устройству.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) Ondisconnectо: активируется, если установленное соединение закрыто или не удалось установить соединение.
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
3) Идет ожидание: при прослушивании входящих подключений начинается.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Кроме того, состояние соединения можно запросить с помощью ```ConnectionState``` свойства в удаленном контексте.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Обработка событий речи

с помощью удаленного речевого интерфейса можно регистрировать речевые триггеры HoloLens 2 и удаленно взаимодействовать с удаленным приложением.

Этот дополнительный элемент необходим для отслеживания состояния удаленного распознавания речи.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Сначала необходимо получить удаленный речевой интерфейс.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

С помощью асинхронного вспомогательного метода можно инициализировать удаленный голос. Это необходимо сделать асинхронно, так как инициализация может занять значительное время. [Параллельные и асинхронные операции с c++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) объясняет, как создавать асинхронные функции с помощью c++/винрт.

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

Существует два способа указания фраз для распознавания.
1) Спецификация внутри XML-файла грамматики речи. Дополнительные сведения см. [в статье Создание базовой грамматики XML](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Укажите, передав их в векторе словаря в ```ApplyParameters``` .

Внутри обратного вызова Онрекогнизедспич можно обрабатывать события речи:

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

## <a name="preview-streamed-content-locally"></a>Предварительный просмотр потокового содержимого на локальном компьютере

Чтобы отобразить то же содержимое в удаленном приложении, которое отправляется на устройство, ```OnSendFrame``` можно использовать событие удаленного контекста. ```OnSendFrame```Событие активируется каждый раз, когда в удаленной библиотеке holographic текущий кадр отправляется на удаленное устройство. Это идеальное время для получения содержимого, а также Блит его в окно рабочего стола или UWP.

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

## <a name="depth-reprojection"></a>Репроектная глубина

Начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0), holographic удаленное взаимодействие поддерживает [репроекцию с глубиной](hologram-stability.md#reprojection). Для этого требуется потоковая передача и буфер цвета, и буфера глубины из удаленного приложения в HoloLens 2. По умолчанию потоковая передача буфера глубины включена и настроена для использования половины разрешения буфера цвета. Это можно изменить следующим образом:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Обратите внимание, что если не следует использовать значения по умолчанию, ```ConfigureDepthVideoStream``` необходимо вызвать метод, прежде чем устанавливать соединение с HoloLens 2. Лучшее место будет сразу после создания удаленного контекста. Возможные значения для Депсбуфферстреамресолутион:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Отключено (добавляется с версией [2.1.3](holographic-remoting-version-history.md#v2.1.3) и при использовании дополнительного видеопотока глубины не создается)

Помните, что использование буфера глубины полного разрешения также влияет на требования к пропускной способности и должно учитывать максимальное значение пропускной способности, которое вы предоставляете ```CreateRemoteContext``` .

Чтобы настроить разрешение, необходимо также зафиксировать буфер глубины с помощью [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

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

чтобы проверить правильность работы репроекции в HoloLens 2, можно включить визуализатор глубины с помощью портала устройств. Дополнительные сведения см. в разделе [Проверка глубины правильно настроена](hologram-stability.md#verifying-depth-is-set-correctly) .

## <a name="optional-custom-data-channels"></a>Необязательно: пользовательские каналы данных

Пользовательские каналы данных можно использовать для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. в разделе [пользовательские каналы данных](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>См. также:
* [Обзор удаленного взаимодействия с holographic](holographic-remoting-overview.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Пользовательские каналы данных с голографическим удаленным взаимодействием](holographic-remoting-custom-data-channels.md)
* [Установка безопасного подключения с использованием голографического удаленного взаимодействия](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)