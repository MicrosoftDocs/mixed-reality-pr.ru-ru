---
title: Создание удаленного приложения holographic с удаленным взаимодействием (Опенкср)
description: Узнайте, как выполнить потоковую передачу удаленного содержимого, отображаемого на удаленном компьютере, в HoloLens 2 с помощью приложений с удаленным взаимодействием Опенкср.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, NuGet
ms.openlocfilehash: 616765143309fe2a4883c1393713133fcbe2a9d5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006494"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Создание удаленного приложения holographic с удаленным взаимодействием с помощью API Опенкср

>[!IMPORTANT]
>В этом документе описывается создание удаленного приложения для головных телефонов HoloLens 2 и Windows Mixed Reality с помощью [API опенкср](../native/openxr.md). Удаленные приложения для **HoloLens (1-го поколения)** должны использовать пакет NuGet версии **1. x. x**. Это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот. Документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).

В приложениях с удаленным взаимодействием можно потокировать удаленно визуализированное содержимое в HoloLens 2 и впечатляющие головные гарнитуры Windows Mixed Reality. Вы также можете получить доступ к дополнительным системным ресурсам и интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК. Удаленное приложение получает поток входных данных из HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2. Подключение устанавливается с использованием стандартного Wi-Fi. Holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP через пакет NuGet. Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения. Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Предварительные требования

Хорошей отправной точкой является работающая Рабочая станция или приложение UWP на основе Опенкср. Дополнительные сведения см. [в статье Приступая к работе с опенкср](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments). Использование [однопотокового подразделения](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.

## <a name="get-the-holographic-remoting-nuget-package"></a>Получение пакета NuGet для удаленного взаимодействия с holographic

Чтобы добавить пакет NuGet в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. Щелкните правой кнопкой мыши узел проекта и выберите пункт **Управление пакетами NuGet...**
3. На появившейся панели нажмите кнопку **Обзор** и выполните поиск по фразе "удаленное взаимодействие".
4. Выберите **Microsoft. Holographic. Remoting. опенкср**, выберите последнюю версию **2. x. x** и нажмите кнопку **установить**.
5. Если отображается диалоговое окно **Предварительный просмотр** , нажмите кнопку **ОК**.
6. Выберите **я принимаю** , когда появится диалоговое окно Лицензионное соглашение.
7. Повторите шаги 3 – 6 для следующих пакетов NuGet: Опенкср. Headers, Опенкср. Loader.

>[!NOTE]
>Версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, желающих выбрать HoloLens 1. Дополнительные сведения см. в разделе [Добавление удаленного взаимодействия holographic (HoloLens (1-й общий))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Выберите среду выполнения Опенкср для удаленного взаимодействия с holographic

Первым шагом, который необходимо сделать в удаленном приложении, является выбор среды выполнения Опенкср holographic Remoting, которая является частью пакета NuGet Microsoft. Holographic. Remoting. Опенкср. Это можно сделать, задав ```XR_RUNTIME_JSON``` для переменной среды путь к RemotingXR.jsфайла в приложении. Эта переменная среды используется загрузчиком Опенкср для того, чтобы не использовать системную среду Опенкср по умолчанию, а вместо этого перенаправлять в среду выполнения Опенкср удаленного взаимодействия Holographic. При использовании RemotingXR.jsпакета NuGet Microsoft. Holographic. Remoting. Опенкср для файла, который автоматически копируется во время компиляции в выходную папку, выбор среды выполнения Опенкср обычно выглядит следующим образом.

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Создание Ксринстанце с расширением holographic для удаленного взаимодействия

Первым шагом является типичное приложение Опенкср — выбор расширений Опенкср и создание Ксринстанце. Спецификация ядра Опенкср не предоставляет API для удаленного взаимодействия. По этой причине holographic удаленное взаимодействие вводит собственное расширение Опенкср с именем ```XR_MSFT_holographic_remoting``` . Убедитесь, что при вызове Ксркреатеинстанце, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` включенном в ксринстанцекреатеинфо.

>[!TIP]
>По умолчанию отображаемое содержимое приложения передается только в поток удаленного взаимодействия holographic, который работает в HoloLens 2 или на гарнитурах Windows Mixed Reality. Чтобы отобразить содержимое, подготовленное на удаленном компьютере, с помощью цепочки подкачки окна для экземпляра, то удаленное взаимодействие удаленного взаимодействия предоставляет второе расширение Опенкср с именем ```XR_MSFT_holographic_remoting_frame_mirroring``` . Также обязательно включите это расширение с помощью ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` , если вы хотите использовать эту функцию.

>[!IMPORTANT]
>Чтобы узнать об API расширения Опенкср для удаленного взаимодействия с holographic, ознакомьтесь со [спецификацией](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) , которую можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Подключение к устройству

После создания удаленного приложения Ксринстанце и запроса Ксрсистемид через Ксржетсистем можно установить подключение к устройству проигрывателя.

>[!WARNING]
> Среда выполнения Опенкср с holographic удаленное взаимодействие может предоставлять данные только для конкретных устройств, такие как конфигурации представления или режимы смешения среды после установки соединения. ```xrEnumerateViewConfigurations```,,, ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` и ```xrGetSystemProperties``` будут предоставлять значения по умолчанию, соответствующие действиям, которые обычно получаются при подключении к проигрывателю, работающему в HoloLens 2, до полного подключения.
Настоятельно рекомендуется не вызывать эти методы до установки соединения. Предложение используется в следующих методах после успешного создания Ксрсессион и состояния сеанса по крайней мере XR_SESSION_STATE_READY.

Общие свойства, такие как максимальная скорость, включение звука, видеокодек или поток глубины, можно настроить ```xrRemotingSetContextPropertiesMSFT``` с помощью следующего.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

Соединение может быть выполнено одним из двух способов.
1) Удаленное приложение подключается к проигрывателю, работающему на устройстве.
2) Проигрыватель, выполняющийся на устройстве, подключается к удаленному приложению.

Чтобы установить подключение из удаленного приложения к устройству проигрывателя, вызовите метод, ```xrRemotingConnectMSFT``` указывающий имя узла и порт через  ```XrRemotingConnectInfoMSFT``` структуру. Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

Прослушивание входящих подключений в удаленном приложении можно выполнить, вызвав ```xrRemotingListenMSFT``` метод. Порт подтверждения и порт транспорта можно указать с помощью ```XrRemotingListenInfoMSFT``` структуры. Порт подтверждения используется для первоначального подтверждения. Затем данные отправляются через порт транспорта. По умолчанию используются **8265** и **8266** .

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

При вызове или вызывается состояние соединения должно быть отключено ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` . Состояние подключения можно получить в любой момент после создания Ксринстанце и запроса для Ксрсистемид с помощью ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Доступные состояния подключения:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```метод или должен быть вызван перед попыткой создать ксрсессион через ксркреатесессион. Если вы попытаетесь создать Ксрсессион, а состояние соединения — ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` Создание сеанса, то будет выполнена успешная операция, но состояние сеанса немедленно переходит на XR_SESSION_STATE_LOSS_PENDING.

Реализация службы удаленного взаимодействия holographic ```xrCreateSession``` поддерживает ожидание установки соединения. Можно вызвать ```xrRemotingConnectMSFT``` или ```xrRemotingListenMSFT``` сразу после вызова метода, который блокирует и ждет установления соединения. Время ожидания истекает до 10 секунд. Если подключение может быть установлено в течение этого времени, создание Ксрсессион будет продолжено, а состояние сеанса будет перенесено в XR_SESSION_STATE_READY. Если соединение не может быть установлено, то создание сеанса также выполняется без немедленного перехода на XR_SESSION_STATE_LOSS_PENDING.

Как правило, соединение имеет состояние Ксрсессион. Любое изменение состояния соединения также влияет на состояние сеанса. Например, если состояние подключения переключается с `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` на ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` состояние сеанса, также будет перенесено в XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Обработка событий, связанных с удаленным взаимодействием

Среда выполнения Опенкср с удаленным взаимодействием предоставляет три события, которые важны для отслеживания состояния соединения.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Активируется при успешном установлении подключения к устройству.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Активируется, если установленное соединение закрыто или не удалось установить соединение.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: При ожидании запуска входящих подключений.

Эти события помещаются в очередь, и удаленное приложение должно считывать данные из очереди с регулярным использованием через ```xrPollEvent``` .

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

## <a name="preview-streamed-content-locally"></a>Предварительный просмотр потокового содержимого на локальном компьютере

Чтобы отобразить то же содержимое в удаленном приложении, которое отправляется на устройство, ```XR_MSFT_holographic_remoting_frame_mirroring``` можно использовать расширение. С помощью этого расширения можно отправить текстуру в Ксрендфраме, используя объект ```XrRemotingFrameMirrorImageInfoMSFT``` , который не связан с ксрфраминдинфо, как показано ниже.

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

В приведенном выше примере используется текстура цепочки подкачки DX11 и представление окна сразу после вызова Ксрендфраме. Использование не ограничено текстурами цепочки подкачки, а дополнительная синхронизация GPU не требуется. Дополнительные сведения об использовании и ограничениях см. в [спецификации расширения](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Если удаленное приложение использует DX12, вместо XrRemotingFrameMirrorImageD3D11MSFT используйте XrRemotingFrameMirrorImageD3D12MSFT.

## <a name="see-also"></a>См. также:
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Установка безопасного подключения с использованием голографического удаленного взаимодействия](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
