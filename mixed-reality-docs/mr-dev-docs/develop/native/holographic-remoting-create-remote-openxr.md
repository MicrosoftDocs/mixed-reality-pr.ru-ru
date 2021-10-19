---
title: Написание удаленного приложения holographic с удаленным взаимодействием выдающие API Опенкср
description: узнайте, как выполнять потоковую передачу удаленного содержимого, отображаемого на удаленном компьютере, для HoloLens 2 с помощью приложений holographic с удаленным доступом с помощью опенкср.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 9/3/2021
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, удаленное взаимодействие, гарнитура смешанной реальности, гарнитура windows mixed reality, гарнитура виртуальной реальности, NuGet
ms.openlocfilehash: a324703a749128b9c4bac74632a696980baf5e26
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158188"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Создание удаленного приложения holographic с удаленным взаимодействием с помощью API Опенкср

Если вы не знакомы с holographic удаленное взаимодействие, то можете ознакомиться с [нашим обзором](../advanced-concepts/holographic-remoting-overview.md).

>[!IMPORTANT]
>в этом документе описывается создание удаленного приложения для HoloLens 2 и Windows Mixed Reality гарнитур с помощью [API опенкср](../native/openxr.md). удаленные приложения для **HoloLens (1-го поколения)** должны использовать NuGet пакета версии **1. x. x**. это означает, что удаленные приложения, написанные для HoloLens 2, несовместимы с HoloLens 1 и наоборот. документацию по HoloLens 1 можно найти [здесь](add-holographic-remoting.md).

в приложениях с удаленным взаимодействием можно передавать содержимое с удаленного просмотра на HoloLens 2 и Windows Mixed Reality впечатляющие головные телефоны. Вы также можете получить доступ к дополнительным системным ресурсам и интегрировать удаленные [иммерсивное представления](../../design/app-views.md) в имеющееся программное обеспечение для настольного ПК. удаленное приложение получает поток входных данных от HoloLens 2, отображает содержимое в виртуальном иммерсивное представление и передает потоки содержимого обратно в HoloLens 2. Подключение устанавливается с использованием стандартного Wi-Fi. holographic удаленное взаимодействие добавляется в приложение для настольных систем или UWP с помощью пакета NuGet. Требуется дополнительный код, который обрабатывает соединение и готовится к просмотру в режиме погружения. Типичное подключение удаленного взаимодействия будет иметь как минимум 50 мс задержки. Приложение проигрывателя может сообщать о задержке в режиме реального времени.

Весь код на этой странице и рабочих проектах можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Предварительные требования

Хорошей отправной точкой является работающая Рабочая станция или приложение UWP на основе Опенкср. Дополнительные сведения см. [в статье Приступая к работе с опенкср](../native/openxr-getting-started.md).

> [!IMPORTANT]
> Любое приложение, использующее holographic удаленное взаимодействие, должно быть создано для использования [многопоточного подразделения](/windows/win32/com/multithreaded-apartments). Использование [однопотокового подразделения](/windows/win32/com/single-threaded-apartments) поддерживается, но может привести к неоптимальной производительности и, возможно, "дергания" во время воспроизведения. При использовании C++/WinRT [WinRT:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) многопотоковое подразделение является значением по умолчанию.

## <a name="get-the-holographic-remoting-nuget-package"></a>получение пакета NuGet holographic для удаленного взаимодействия

чтобы добавить NuGet пакет в проект в Visual Studio, необходимо выполнить следующие действия.
1. Откройте проект в Visual Studio.
2. щелкните правой кнопкой мыши узел проекта и выберите пункт **управление NuGet пакетами...**
3. На появившейся панели нажмите кнопку **Обзор** и выполните поиск по фразе "удаленное взаимодействие".
4. Выберите **Microsoft. Holographic. Remoting. опенкср**, убедитесь, что выбрана последняя версия **2. x. x** , и нажмите кнопку **установить**.
5. Если отображается диалоговое окно **Предварительный просмотр** , нажмите кнопку **ОК**.
6. Выберите **я принимаю** , когда появится диалоговое окно Лицензионное соглашение.
7. повторите шаги 3 – 6 для следующих пакетов NuGet: опенкср. headers, опенкср. loader.

> [!NOTE]
> версия **1. x. x** пакета NuGet по-прежнему доступна для разработчиков, которые хотят ориентироваться HoloLens 1. дополнительные сведения см. в разделе [добавление удаленного взаимодействия с holographic (HoloLens (1-й общий))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Выберите среду выполнения Опенкср для удаленного взаимодействия с holographic

первым шагом, который необходимо сделать в удаленном приложении, является выбор среды выполнения опенкср holographic remoting, которая является частью пакета Microsoft. holographic. remoteing. опенкср NuGet. Это можно сделать, задав ```XR_RUNTIME_JSON``` для переменной среды путь к файлу ремотингкср. JSON в приложении. Эта переменная среды используется загрузчиком Опенкср для того, чтобы не использовать системную среду Опенкср по умолчанию, а вместо этого перенаправлять в среду выполнения Опенкср удаленного взаимодействия Holographic. при использовании пакета Microsoft. holographic. remoting. опенкср NuGet файл ремотингкср. json автоматически копируется во время компиляции в выходную папку. выбор среды выполнения опенкср обычно выглядит следующим образом.

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

Первые действия, которые следует выполнить обычному приложению Опенкср, — выберите расширения Опенкср и создайте Ксринстанце. Спецификация ядра Опенкср не предоставляет API для удаленного взаимодействия. По этой причине в holographic удаленное взаимодействие вводится собственное расширение Опенкср с именем ```XR_MSFT_holographic_remoting``` . Убедитесь, что ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` включен в ксринстанцекреатеинфо вызова ксркреатеинстанце.

> [!TIP]
> по умолчанию отображаемое содержимое приложения передается только в поток удаленного взаимодействия holographic, который работает на HoloLens 2 или на Windows Mixed Reality гарнитурах. Чтобы отобразить содержимое, подготовленное на удаленном компьютере, с помощью цепочки подкачки окна для экземпляра, то удаленное взаимодействие удаленного взаимодействия предоставляет второе расширение Опенкср с именем ```XR_MSFT_holographic_remoting_frame_mirroring``` . Также обязательно включите это расширение с помощью ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` , если вы хотите использовать эту функцию.

> [!IMPORTANT]
> Чтобы узнать об API расширения Опенкср для удаленного взаимодействия с holographic, ознакомьтесь со [спецификацией](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html) , которую можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Подключение на устройство

После создания удаленного приложения Ксринстанце и запроса Ксрсистемид через Ксржетсистем можно установить подключение к устройству проигрывателя.

> [!WARNING]
> Среда выполнения Опенкср с holographic удаленное взаимодействие может предоставлять данные только для конкретных устройств, такие как конфигурации представления или режимы смешения среды после установки соединения. ```xrEnumerateViewConfigurations```,,, ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` и ```xrGetSystemProperties``` будут предоставлять значения по умолчанию, соответствующие действиям, которые обычно получаются при подключении к проигрывателю, работающему на HoloLens 2, до полного подключения.
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

Чтобы установить подключение из удаленного приложения к устройству проигрывателя, вызовите ```xrRemotingConnectMSFT``` метод, указав имя узла и порт через  ```XrRemotingConnectInfoMSFT``` структуру. Порт, используемый проигрывателем удаленного взаимодействия (holographic), — **8265**.

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

> [!IMPORTANT]
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

В приведенном выше примере используется текстура цепочки DX11 для подкачки и представлено окно сразу после вызова Ксрендфраме. Использование не ограничивается для перекачки текстур цепочки. Кроме того, не требуется дополнительная синхронизация GPU. Дополнительные сведения об использовании и ограничениях см. в [спецификации расширения](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Если удаленное приложение использует DX12, используйте XrRemotingFrameMirrorImageD3D12MSFT вместо XrRemotingFrameMirrorImageD3D11MSFT.


## <a name="optional-custom-data-channels"></a>Необязательно: пользовательские каналы данных

Начиная с версии [2.5.0](holographic-remoting-version-history.md#v2.5.0), пользовательские каналы данных можно использовать с API опенкср для отправки пользовательских данных через уже установленное удаленное соединение. Дополнительные сведения см. [в разделе Пользовательские каналы данных с помощью API опенкср](../advanced-concepts/holographic-remoting-custom-data-channels-openxr.md).

## <a name="optional-speech"></a>Необязательно: речь

Начиная с версии [2.6.0](holographic-remoting-version-history.md#v2.6.0), ```XR_MSFT_holographic_remoting_speech``` расширение позволяет удаленному приложению реагировать на голосовые команды, обнаруженные приложением Player с помощью API опенкср.

>  [!IMPORTANT]
> Подробную [спецификацию](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html) можно найти в [репозитории GitHub с примерами удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Для инициализации распознавателя речи в приложении проигрывателя удаленное приложение может вызвать ```xrInitializeRemotingSpeechMSFT``` .
Этот вызов передает параметры инициализации речи, состоящие из языка, словаря фраз и содержимого файла грамматики, в приложение проигрывателя.

> [!NOTE]
> До версии [2.6.1](holographic-remoting-version-history.md#v2.6.1) распознаватель речи должен быть инициализирован только один раз в ```XrSession``` .

Если создание распознавателя речи выполнено успешно, как указано в ```XR_TYPE_EVENT_DATA_REMOTING_SPEECH_RECOGNIZER_STATE_CHANGED_MSFT``` событии, удаленное приложение будет уведомлено о создании результата распознавания речи в приложении проигрывателя.
```XrEventDataRemotingSpeechRecognizerStateChangedMSFT```Структура событий помещается в очередь событий при изменении состояния распознавателя речи на стороне проигрывателя.

```XrRemotingSpeechRecognizerStateMSFT``` определяет все возможные состояния распознавателя речи на стороне проигрывателя, а ```XrEventDataRemotingSpeechRecognizedMSFT``` Структура событий помещается в очередь событий, если распознаватель речи на стороне игрока имеет распознанную фразу.
После того как удаленное приложение будет уведомлено о распознанной фразе, оно может получить распознанную фразу, вызвав метод ```xrRetrieveRemotingSpeechRecognizedTextMSFT``` .

> [!NOTE]
> ```XrRemotingSpeechRecognitionConfidenceMSFT```— это прямое сопоставление перечисления [спичрекогнитионконфиденце](/uwp/api/windows.media.speechrecognition.speechrecognitionconfidence) , возвращенное с результатом распознавания речи Windows API распознавания речи.


## <a name="optional-coordinate-system-synchronization"></a>Необязательно: Синхронизация системы координат

Начиная с версии [2.7.0](holographic-remoting-version-history.md#v2.7.0), для согласования пространственных данных между проигрывателем и удаленным приложением можно использовать синхронизацию системы координат.
Дополнительные сведения см. [в статье о синхронизации системы координат с помощью удаленного взаимодействия с holographic](../advanced-concepts/holographic-remoting-coordinate-system-synchronization.md).

## <a name="see-also"></a>См. также:
* [Обзор удаленного взаимодействия с holographic](../advanced-concepts/holographic-remoting-overview.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Установка безопасного подключения с использованием голографического удаленного взаимодействия](holographic-remoting-secure-connection.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
