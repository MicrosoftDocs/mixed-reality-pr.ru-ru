---
title: Голографическое удаленное взаимодействие в классическом приложении
description: Узнайте, как использовать удаленное взаимодействие в классических приложениях с помощью Опенкср.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, наушники смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, Настольный компьютер
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906730"
---
# <a name="holographic-remoting-in-desktop-app"></a>Голографическое удаленное взаимодействие в классическом приложении

> [!NOTE]
> В выпуске пакета 0.1.3 добавлена поддержка удаленного взаимодействия автономных приложений Windows.
> Начиная с версии 0.1.3 Эта функция не поддерживает сборки UWP.

1. Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](unity-play-mode.md#holographic-remoting-setup) .
2. Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** . Кроме того, снимите флажок **инициализировать XR при запуске**:

    ![Снимок экрана: панель "Параметры проекта" открыта в редакторе Unity с снятым флажком "инициализировать XR при запуске"](images/openxr-features-img-02-app.png)

3. Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".
4. Установите флажок **удаленное взаимодействие с приложением holographic** .

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с включенной удаленным взаимодействием приложений](images/openxr-features-img-03-app.png)

5. Затем напишите некоторый код, чтобы задать конфигурацию удаленного взаимодействия и инициировать инициализацию XR. Пример приложения, распространяемый с [подключаемым модулем Mixed Reality опенкср](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) , содержит аппремотинг. cs, в котором показан пример сценария для подключения к ОПРЕДЕЛЕННОМУ IP-адресу во время выполнения. При развертывании примера приложения на локальном компьютере в этом месте будет отображаться поле ввода IP-адреса с кнопкой подключения. Введите IP-адрес и нажмите кнопку Подключить, чтобы инициализировать XR и попытаться подключиться к целевому устройству:

    ![Снимок экрана примера приложения, отображающего пример пользовательского интерфейса удаленного взаимодействия](images/openxr-sample-app-remoting.png)

6. Чтобы написать пользовательский код соединения, вызовите `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` его с помощью заполнения `RemotingConfiguration` . Пример приложения предоставляет это в инспекторе и показывает, как заполнить IP-адрес из текстового поля. Вызов `Connect` задаст конфигурацию и автоматически инициализирует XR, поэтому ее необходимо вызвать как соподпрограмму:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Во время выполнения можно получить текущее состояние соединения с помощью `AppRemoting.TryGetConnectionState` API, а также при необходимости отключить и деинициализировать XR с помощью `AppRemoting.Disconnect()` . Это можно использовать для отключения и повторного подключения к другому устройству в рамках одного сеанса приложения. Пример приложения предоставляет управляемый куб, который отключает сеанс удаленного взаимодействия, если он нажат.

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