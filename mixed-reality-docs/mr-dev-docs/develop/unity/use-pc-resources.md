---
title: Использование ресурсов ПК для управления приложением с помощью удаленного приложения holographic с удаленным взаимодействием
description: используйте ресурсы пк, вместо того чтобы полагаться на встроенную вычислительную мощность HoloLens, чтобы включить приложение с помощью удаленного взаимодействия с holographic.
author: vtieto
ms.author: v-vtieto
ms.date: 10/05/2021
ms.topic: article
keywords: опенкср, unity, hololens, hololens 2, mixed reality, мртк, смешанная реальность набор средств, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, настольный, предварительный просмотр, отладка
ms.openlocfilehash: 18d605b2de01df19fa61c2778b2dc2894a59ec6a
ms.sourcegitcommit: 4f847aba212e97b1639299ddbe2b1a7b27c60f4d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2021
ms.locfileid: "130204136"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting-remote-app"></a>Использование ресурсов ПК для управления приложением с помощью удаленного приложения holographic с удаленным взаимодействием

В этой статье описывается следующий вариант использования для удаленного взаимодействия с Holographic.

-  **вы хотите, чтобы ресурсы компьютера были включены в приложение, а не полагаться на HoloLensные ресурсы**: вы можете создать и построить приложение с возможностью удаленного взаимодействия с holographic. пользователь работает с приложением на HoloLens, но приложение на самом деле выполняется на пк, что позволяет приложению использовать преимущества более мощных ресурсов компьютера. Это может быть особенно полезно, если в приложении есть ресурсы или модели с высоким разрешением, и вы не хотите, чтобы частота кадров была негативно снижена. Мы вызываем это _Удаленное приложение holographic для удаленного взаимодействия_. входные данные HoloLens--взгляда, жеста, голоса и пространственного сопоставления — отправляются на компьютер, где содержимое подготавливается к просмотру в виртуальном иммерсивное представление. Затем отображаемые кадры отправляются в HoloLens.

этот тип holographic remoting также доступен Windows Mixed Reality для вмрных головных телефонов. Это может быть полезно, если, например, гарнитура ВМР подключена к ранец ПК и вы хотите передать приложение с более мощного компьютера на ранец ПК.

Дополнительные сведения об удаленном взаимодействии с holographic см. в статье [Обзор удаленного взаимодействия](../advanced-concepts/holographic-remoting-overview.md) с Holographic.

Обратите внимание, что можно также использовать holographic удаленное взаимодействие, если [вы хотите просмотреть и отладить приложение](preview-and-debug-your-app.md)в процессе разработки.

## <a name="set-up-the-holographic-remoting-player-app"></a>Настройка приложения удаленного проигрывателя holographic

чтобы использовать удаленное взаимодействие с holographic, необходимо установить приложение с помощью [удаленного проигрывателя holographic](../advanced-concepts/holographic-remoting-player.md) из Microsoft Store на HoloLens 2. Как описано ниже, после загрузки и запуска приложения вы увидите номер версии и IP-адрес для подключения. **Для работы с подключаемым модулем опенкср потребуется v 2.4 или более поздней версии**.

Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение. Дополнительные сведения см. в статье, посвященной удаленному проигрывателю Holographic.

![Снимок экрана: проигрыватель holographic Remoting, работающий на HoloLens](images/openxr-features-img-01.png)

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

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Переход с предыдущих API-интерфейсов удаленного взаимодействия holographic

Дополнительные сведения об удаленном взаимодействии с holographic см. в статье [Обзор удаленного взаимодействия](../advanced-concepts/holographic-remoting-overview.md) с Holographic.

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

## <a name="see-also"></a>См. также:

* [Holographic Remoting Player](../advanced-concepts/holographic-remoting-player.md)
* [Предварительный просмотр и отладка приложения с помощью holographic, удаленного взаимодействия и режима воспроизведения](preview-and-debug-your-app.md)
* [Учебник. Начало работы с PC holographic для удаленного взаимодействия](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Учебник. Создание приложения для удаленного взаимодействия holographic](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
