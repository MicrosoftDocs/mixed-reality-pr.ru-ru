---
title: Функции, поддерживаемые подключаемым модулем Опенкср в Unity
description: Ознакомьтесь с функциями Опенкср, поддерживаемыми для разработки смешанной реальности в Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230745"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Функции, поддерживаемые Опенкср Mixed Reality в Unity

Пакет **подключаемого модуля опенкср для смешанной реальности** является расширением **подключаемого модуля опенкср** Unity и поддерживает набор функций для головных телефонов HoloLens 2 и Windows Mixed Reality. Прежде чем продолжить, убедитесь, что установлен **unity 2020,2** или более поздней **версии, подключаемый модуль опенкср версия 0.1.3** или более поздней, а проект Unity [настроен для опенкср](openxr-getting-started.md).

## <a name="whats-supported"></a>Поддерживаемые функции

В настоящее время поддерживаются следующие функции:

* Поддерживает приложения UWP для HoloLens 2 и оптимизированы для модели приложений HoloLens 2.
* Поддерживает приложения Win32 версий для гарнитуры Windows Mixed Reality с последними профилями контроллеров и удаленным взаимодействием с holographic приложениями.
* Отслеживание масштаба мира с использованием привязок и неограниченного пространства.
* [API-интерфейс хранилища привязки для сохранения привязок](#anchors-and-anchor-persistence) в локальном хранилище HoloLens 2.
* [Взаимодействие контроллера движения и руки](#motion-controller-and-hand-interactions), включая новый контроллер HP REVERB G2.
* Отслеживание с обобразованием с использованием 26 соединений и совместного входа RADIUS.
* Взаимодействие взгляда на HoloLens 2.
* Поиск камеры фото/Video (ПС) в HoloLens 2.
* Запись смешанной реальности с помощью визуализации с третьим глазом через камеру ПС.
* Поддерживает ["Play" в HoloLens 2 с помощью приложения holographic, поддерживающего удаленное взаимодействие](#holographic-remoting-in-unity-editor-play-mode), что позволяет разработчикам выполнять отладку сценариев без создания и развертывания на устройстве.
* Совместимо с МРТК Unity 2.5.3 и более поздней версии через [поддержку поставщика Мртк опенкср](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Совместимо с Unity [арфаундатион 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) или более поздней версии.
* (Добавлено в 0.1.3) Поддерживает [настольное приложение holographic удаленное взаимодействие](#holographic-remoting-in-desktop-app) из созданного и развернутого автономного приложения Windows.
* (Добавлено в 0.1.4) Поддержка [отслеживания QR-кода](#qr-codes) в HoloLens2 через спатиалграфноде

## <a name="holographic-remoting-setup"></a>Настройка удаленного взаимодействия с holographic

1. Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store в HoloLens 2.
2. Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.
    * Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic удаленное взаимодействие в режиме воспроизведения редактора Unity

Создание проекта Unity для UWP в проекте Visual Studio, а затем упаковка и развертывание на устройстве HoloLens 2 может занять некоторое время. Одним из решений является включение функции удаленного взаимодействия в holographic Editor, которая позволяет выполнять отладку сценария C# с помощью режима Play непосредственно на устройстве HoloLens 2 по сети. Этот сценарий позволяет избежать издержек при создании и развертывании пакета UWP на удаленном устройстве.

1. Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](#holographic-remoting-setup) .
2. Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** :

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-features-img-02.png)

3. Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".
4. Установите флажок **удаленное взаимодействие с помощью редактора holographic** и введите IP-адрес, полученный из приложения holographic Remoting:

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенными компонентами](images/openxr-features-img-03.png)

Теперь можно нажать кнопку "Воспроизвести", чтобы воспроизвести приложение Unity в удаленном приложении holographic на HoloLens. Вы также можете [присоединить Visual Studio к Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) для отладки скриптов C# в режиме воспроизведения.

> [!NOTE]
> Начиная с версии 0.1.0, среда выполнения holographic Remoting не поддерживает привязки, а функции Аранчорманажер не будут работать через удаленное взаимодействие.  Эта функция появилась в будущих выпусках.

## <a name="holographic-remoting-in-desktop-app"></a>Holographic удаленное взаимодействие в классическом приложении

> [!NOTE]
> В выпуске пакета 0.1.3 добавлена поддержка удаленного взаимодействия автономных приложений Windows.
> Начиная с версии 0.1.3 Эта функция не поддерживает сборки UWP.

1. Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](#holographic-remoting-setup) .
2. Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** . Кроме того, снимите флажок **инициализировать XR при запуске**:

    ![Снимок экрана: панель "Параметры проекта" открыта в редакторе Unity с снятым флажком "инициализировать XR при запуске"](images/openxr-features-img-02-app.png)

3. Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".
4. Установите флажок **удаленное взаимодействие с приложением holographic** .

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с включенной удаленным взаимодействием приложений](images/openxr-features-img-03-app.png)

5. Затем напишите некоторый код, чтобы задать конфигурацию удаленного взаимодействия и инициировать инициализацию XR. Пример приложения, распространяемый с помощью [подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md#hololens-2-samples) , содержит AppRemoting.cs, в котором показан пример сценария для подключения к ОПРЕДЕЛЕННОМУ IP-адресу во время выполнения. При развертывании примера приложения на локальном компьютере в этом месте будет отображаться поле ввода IP-адреса с кнопкой подключения. Введите IP-адрес и нажмите кнопку Подключить, чтобы инициализировать XR и попытаться подключиться к целевому устройству:

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

## <a name="anchors-and-anchor-persistence"></a>Привязки и сохранение привязки

Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity. Основные сведения о **аранчор** s в арфаундатион см. в руководстве по [Арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). Начиная с версии 0.1.0 этот подключаемый модуль поддерживает все функциональные возможности Аранчорманажер, за исключением создания привязок, присоединенных к плоскости, которая ожидается в будущем выпуске.

### <a name="anchor-persistence-and-the-xranchorstore"></a>Сохранение привязки и Ксранчорсторе

Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами. Ксранчорсторе — это представление сохраненных привязок на устройстве. Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.

> [!NOTE]
> Эти привязки должны быть сохранены и загружены на одном устройстве. Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Полный пример сохранения и несохраненных привязок см. в разделе привязки-> примеры привязок в образце [сцены подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md#hololens-2-samples):

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>Взаимодействие контроллера движения и руки

Основные сведения о взаимодействии смешанной реальности в Unity см. в [руководстве по Unity для XR данных Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Эта документация по Unity охватывает сопоставления от входных данных, относящихся к конкретному контроллеру, с более обобщенными **инпутфеатуреусажеами**, как можно идентифицировать и классифицировать доступные входные данные XR, как считывать их из этих входных данных и многое другое.

Подключаемый модуль Mixed Reality Опенкср предоставляет дополнительные профили взаимодействия ввода, сопоставленные со стандартным **инпутфеатуреусаже**, как описано ниже.

| инпутфеатуреусаже | HP reverbы G2 Controller (Опенкср) | HoloLens (Опенкср) |
| ---- | ---- | ---- |
| primary2DAxis | Джойстик | |
| primary2DAxisClick | Джойстик — щелчок | |
| триггер | Триггер  | |
| регулировки | Регулировки | Воздушный нажим или сжатие |
| примарибуттон | [X/A] — нажмите клавишу | Жест касания |
| секондарибуттон | [Y/B] — нажмите клавишу | |
| грипбуттон | Захват и нажатие клавиши | |
| тригжербуттон | Триггер-нажатие | |
| менубуттон | Меню | |

### <a name="aim-and-grip-poses"></a>AIM и захват

У вас есть доступ к двум наборам экземпляров через входные взаимодействия Опенкср:

* Захват для отрисовки объектов в руки
* Цель, указывающая на мир.

Дополнительные сведения об этой структуре и различиях между ними можно найти в [подкаталогах Опенкср Specification-input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Представления, предоставляемые Инпутфеатуреусажес **девицепоситион**, **девицеротатион**, **девицевелоЦити** и **девицеангуларвелоЦити** , представляют собой OpenXR **захват** . Инпутфеатуреусажес, связанные с захватом, определяются в [Коммонусажес](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Представления, предоставляемые Инпутфеатуреусажес **поинтерпоситион**, **поинтерротатион**, **поинтервелоЦити** и **поинтерангуларвелоЦити** , представляют собой OpenXR **Цель** . Эти Инпутфеатуреусажес не определены во вложенных файлах C#, поэтому необходимо определить собственный Инпутфеатуреусажес следующим образом:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>хаптикс

Сведения об использовании хаптикс в системе ввода XR в Unity можно найти в [руководстве по Unity для Unity XR input-хаптикс](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>QR-коды

HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода. Дополнительные сведения можно найти в документации по [отслеживанию QR-кода](../platform-capabilities-and-apis/qr-code-tracking.md) .  При использовании подключаемого модуля Опенкср Извлеките [ `SpatialGraphNodeId` из QR-интерфейса API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) и используйте `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API для нахождение QR-кода.

Для справки у нас есть [Пример проекта отслеживания QR](https://github.com/yl-msft/QRTracking) -кодов на сайте GitHub с более подробным описанием использования [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="whats-coming-soon"></a>Что ожидается в ближайшее время

Следующие проблемы и отсутствующие функции известны с помощью Опенкср подключаемого модуля Mixed Reality **версии 0.1.0**. Мы работаем над этим и выпустили исправления и новые функции в будущих выпусках.

* **Арпланесубсистем** еще не поддерживается. **Арпланеманажер**, **АРРАЙКАСТМАНАЖЕР** и связанный API, такие как **аранчорманажер. аттачанчор** , также не поддерживаются в HoloLens 2.
* **Сохраняемость привязки** пока не поддерживается с помощью удаленного взаимодействия holographic, но в ближайшем будущем.
* Отслеживание **сетки руки** и **ксрмешсубсистем** пока не поддерживаются.
* Поддержка **пространственных привязок Azure** появилась в следующем выпуске.
* **ARM64** — единственная поддерживаемая платформа для приложений HoloLens 2. Платформа **ARM** поступает в будущем выпуске.

## <a name="troubleshooting"></a>Устранение неполадок

При приостановке и возобновлении работы приложения Unity в HoloLens 2 приложение не может корректно возобновить работу, что приводит к 4 вращающимся точкам в представлении HoloLens.

* Установка для **режима отправки глубины** значения " **нет** " в параметрах проекта опенкср в качестве обходного пути
