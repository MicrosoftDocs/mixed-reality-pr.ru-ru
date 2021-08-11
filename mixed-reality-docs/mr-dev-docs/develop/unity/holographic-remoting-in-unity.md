---
title: Holographic удаленное взаимодействие в Unity
description: Узнайте, как использовать удаленное взаимодействие holographic в классическом приложении и режиме воспроизведения Unity с Опенкср.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: опенкср, unity, hololens, hololens 2, mixed reality, мртк, смешанная реальность набор средств, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, настольный компьютер
ms.openlocfilehash: 0b18bf4a187190da3ef9d17fd87f2c42feaa271210345330887ce618b49a0442
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192186"
---
# <a name="holographic-remoting-in-unity"></a>Holographic удаленное взаимодействие в Unity

> [!NOTE]
> Windows В выпуске пакета 0.1.3 добавлена поддержка удаленного взаимодействия автономных приложений.
> Начиная с версии 0.1.3 Эта функция не поддерживает сборки UWP.

[Изучите основы голографического удаленного взаимодействия.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

с помощью удаленного взаимодействия holographic можно передавать данные в HoloLens 2 в режиме реального времени. Это отличный способ быстрой отладки приложения без создания и развертывания полного проекта. 

Прежде чем приступить к работе, важно понимать два основных варианта в Unity:
* **Holographic удаленное взаимодействие в режиме воспроизведения Unity**: запустите приложение локально в редакторе Unity на компьютере в режиме воспроизведения, чтобы обеспечить быстрый способ предварительного просмотра содержимого на HoloLens 2. режим воспроизведения также можно использовать с головной гарнитурой Windows Mixed Reality, прикрепленной к компьютеру разработки.
* **Holographic удаленное взаимодействие из файла сборки Unity**. Запустите приложение из удаленного приложения Unity holographic Remote Remoting, экспортированного на Рабочий стол, в HoloLens 2. Это может быть полезно, если приложение имеет ресурсы или модели с высоким разрешением. графический процессор рабочего стола обрабатывает отрисовку до HoloLens 2.

## <a name="holographic-remoting-setup"></a>Настройка удаленного взаимодействия с holographic

независимо от того, какой маршрут выполняется с помощью удаленного взаимодействия, необходимо [установить приложение с помощью удаленного проигрывателя holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store на HoloLens 2.

после загрузки запустите приложение с удаленным проигрывателем holographic на HoloLens 2, и вы увидите номер версии и IP-адрес для подключения. **Для работы с подключаемым модулем опенкср потребуется v 2.4 или более поздней версии**.

![Снимок экрана: проигрыватель holographic Remoting, работающий на HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Режим воспроизведения Unity с holographic удаленное взаимодействие

[!INCLUDE[](includes/unity-play-mode.md)]

Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение. Дополнительные сведения можно найти в документации по [удаленному проигрывателю holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Для достижения лучших результатов убедитесь, что приложение правильно устанавливает [фокусную точку](focus-point-in-unity.md). Это помогает holographic удаленно адаптировать сцену для адаптации сцены к задержке беспроводного подключения.

## <a name="holographic-remoting-from-a-remote-application"></a>Holographic удаленное взаимодействие из удаленного приложения

1. в строке меню выберите **изменить > Project Параметры**.
1. В столбце слева выберите **XR Plug-in Management (Управление подключаемыми модулями**).
1. в разделе **XR Plug-in Management (подключаемый модуль управления** ) выберите **группу функций Microsoft HoloLens** и **группу функций удаленного приложения holographic удаленное взаимодействие**.
1. Снимите флажок **инициализировать XR при запуске**:

    ![Снимок экрана: панель "Параметры проекта" открыта в редакторе Unity с снятым флажком "инициализировать XR при запуске"](images/001-openxr-features.png)

1. Напишите некоторый код, чтобы задать конфигурацию удаленного взаимодействия и инициировать инициализацию XR. Пример приложения, распространяемый с [подключаемым модулем Mixed Reality опенкср](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) , содержит аппремотинг. cs, в котором показан пример сценария для подключения к ОПРЕДЕЛЕННОМУ IP-адресу во время выполнения. При развертывании примера приложения на локальном компьютере в этом месте будет отображаться поле ввода IP-адреса с кнопкой подключения. введите IP-адрес и нажмите Подключение инициализировать XR, а затем попытаться подключиться к целевому устройству:

    ![Снимок экрана примера приложения, отображающего пример пользовательского интерфейса удаленного взаимодействия](images/openxr-sample-app-remoting.png)

1. Чтобы написать пользовательский код соединения, вызовите `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` его с помощью заполнения `RemotingConfiguration` . Пример приложения предоставляет это в инспекторе и показывает, как заполнить IP-адрес из текстового поля. Вызов `Connect` задаст конфигурацию и автоматически инициализирует XR, поэтому ее необходимо вызвать как соподпрограмму:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Во время выполнения можно получить текущее состояние соединения с помощью `AppRemoting.TryGetConnectionState` API, а также при необходимости отключить и деинициализировать XR с помощью `AppRemoting.Disconnect()` . Это можно использовать для отключения и повторного подключения к другому устройству в рамках одного сеанса приложения. Пример приложения предоставляет управляемый куб, который отключает сеанс удаленного взаимодействия, если он нажат.

### <a name="migration-from-previous-apis"></a>Миграция с предыдущих API

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. WSA. Холографикремотинг

Из примера кода в [документах Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):

| XR. Головк. холографикремотинг | Опенкср. Remoting. Аппремотинг |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [Н/д: автоматически происходит при вызове `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. Виндовсмр. Виндовсмрремотинг

| XR. Виндовсмр. Виндовсмрремотинг | Опенкср. Remoting. Аппремотинг |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` и `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Передается `AppRemoting.Connect` через `RemotingConfiguration` структуру |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>См. также раздел

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Учебник. Начало работы с PC holographic для удаленного взаимодействия](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Учебник. Создание приложения для удаленного взаимодействия holographic](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
