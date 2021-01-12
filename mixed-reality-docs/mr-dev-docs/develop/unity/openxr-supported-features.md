---
title: Функции, поддерживаемые подключаемым модулем Опенкср в Unity
description: Ознакомьтесь с функциями Опенкср, поддерживаемыми для разработки смешанной реальности в Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: d65bab65bcb06f7ccba522461e04062458e7400c
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108847"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="38597-104">Функции, поддерживаемые Опенкср Mixed Reality в Unity</span><span class="sxs-lookup"><span data-stu-id="38597-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="38597-105">Пакет **подключаемого модуля опенкср для смешанной реальности** является расширением **подключаемого модуля опенкср** Unity и поддерживает набор функций для головных телефонов HoloLens 2 и Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="38597-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="38597-106">Прежде чем продолжить, убедитесь, что установлено приложение **unity 2020,2** или более поздней **версии, Опенкср подключаемый модуль, версия 0.1.2** или более поздней, а проект Unity [настроен для опенкср](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="38597-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.2** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="38597-107">Поддерживаемые функции</span><span class="sxs-lookup"><span data-stu-id="38597-107">What's supported</span></span>

<span data-ttu-id="38597-108">В настоящее время поддерживаются следующие функции:</span><span class="sxs-lookup"><span data-stu-id="38597-108">The following features are currently supported:</span></span>

* <span data-ttu-id="38597-109">Поддерживает приложения UWP для HoloLens 2 и оптимизированы для модели приложений HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="38597-110">Поддерживает приложения Win32 версий для гарнитуры Windows Mixed Reality с последними профилями контроллеров и удаленным взаимодействием с holographic приложениями.</span><span class="sxs-lookup"><span data-stu-id="38597-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="38597-111">Отслеживание масштаба мира с использованием привязок и неограниченного пространства.</span><span class="sxs-lookup"><span data-stu-id="38597-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="38597-112">[API-интерфейс хранилища привязки для сохранения привязок](#anchors-and-anchor-persistence) в локальном хранилище HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="38597-113">[Взаимодействие контроллера движения и руки](#motion-controller-and-hand-interactions), включая новый контроллер HP REVERB G2.</span><span class="sxs-lookup"><span data-stu-id="38597-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="38597-114">Отслеживание с обобразованием с использованием 26 соединений и совместного входа RADIUS.</span><span class="sxs-lookup"><span data-stu-id="38597-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="38597-115">Взаимодействие взгляда на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="38597-116">Поиск камеры фото/Video (ПС) в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="38597-117">Запись смешанной реальности с помощью визуализации с третьим глазом через камеру ПС.</span><span class="sxs-lookup"><span data-stu-id="38597-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="38597-118">Поддерживает ["Play" в HoloLens 2 с помощью приложения holographic, поддерживающего удаленное взаимодействие](#holographic-remoting-in-unity-editor-play-mode), что позволяет разработчикам выполнять отладку сценариев без создания и развертывания на устройстве.</span><span class="sxs-lookup"><span data-stu-id="38597-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="38597-119">Совместимо с МРТК Unity 2.5.3 и более поздней версии через [поддержку поставщика Мртк опенкср](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="38597-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="38597-120">Совместимо с Unity [арфаундатион 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="38597-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="38597-121">Holographic удаленное взаимодействие в режиме воспроизведения редактора Unity</span><span class="sxs-lookup"><span data-stu-id="38597-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="38597-122">Создание проекта Unity для UWP в проекте Visual Studio, а затем упаковка и развертывание на устройстве HoloLens 2 может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="38597-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="38597-123">Одно из решений — включить удаленное взаимодействие с помощью редактора, которое позволяет выполнять отладку сценария C#, используя режим "Воспроизведение" непосредственно на устройстве HoloLens 2 по сети.</span><span class="sxs-lookup"><span data-stu-id="38597-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="38597-124">Этот сценарий позволяет избежать издержек при создании и развертывании пакета UWP на удаленном устройстве.</span><span class="sxs-lookup"><span data-stu-id="38597-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="38597-125">Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из магазина в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="38597-126">Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.</span><span class="sxs-lookup"><span data-stu-id="38597-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="38597-127">Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="38597-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

3. <span data-ttu-id="38597-129">Откройте **Параметры проекта Edit->**, перейдите в **раздел Управление подключаемыми модулями XR** и установите флажок **набор функций Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="38597-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-features-img-02.png)

4. <span data-ttu-id="38597-131">Разверните раздел " **компоненты** " в разделе **опенкср** и выберите команду " **отобразить все** ".</span><span class="sxs-lookup"><span data-stu-id="38597-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="38597-132">Установите флажок **удаленное взаимодействие с помощью редактора holographic** и введите IP-адрес, полученный из приложения holographic Remoting:</span><span class="sxs-lookup"><span data-stu-id="38597-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенными компонентами](images/openxr-features-img-03.png)

<span data-ttu-id="38597-134">Теперь можно нажать кнопку "Воспроизвести", чтобы воспроизвести приложение Unity в удаленном приложении holographic на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38597-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="38597-135">Вы также можете [присоединить Visual Studio к Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) для отладки скриптов C# в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="38597-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="38597-136">Начиная с версии 0.1.0, среда выполнения holographic Remoting не поддерживает привязки, а функции Аранчорманажер не будут работать через удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="38597-136">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="38597-137">Эта функция появилась в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="38597-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="38597-138">Привязки и сохранение привязки</span><span class="sxs-lookup"><span data-stu-id="38597-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="38597-139">Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity.</span><span class="sxs-lookup"><span data-stu-id="38597-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="38597-140">Основные сведения о **аранчор** s в арфаундатион см. в руководстве по [Арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="38597-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="38597-141">Начиная с версии 0.1.0 этот подключаемый модуль поддерживает все функциональные возможности Аранчорманажер, за исключением создания привязок, присоединенных к плоскости, которая ожидается в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="38597-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="38597-142">Сохранение привязки и Ксранчорсторе</span><span class="sxs-lookup"><span data-stu-id="38597-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="38597-143">Дополнительный API, называемый **ксранчорсторе** , позволяет сохранять привязки между сеансами.</span><span class="sxs-lookup"><span data-stu-id="38597-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="38597-144">Ксранчорсторе — это представление сохраненных привязок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="38597-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="38597-145">Привязки можно сохранять из **аранчорс** в сцене Unity, загружать из хранилища в новый **аранчорс** или удалять из хранилища.</span><span class="sxs-lookup"><span data-stu-id="38597-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="38597-146">Эти привязки должны быть сохранены и загружены на одном устройстве.</span><span class="sxs-lookup"><span data-stu-id="38597-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="38597-147">Хранилище с привязкой между устройствами будет поддерживаться с помощью пространственных привязок Azure в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="38597-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="38597-148">Чтобы загрузить Ксранчорсторе, подключаемый модуль предоставляет метод расширения для Ксранчорсубсистем, подсистему Аранчорманажер:</span><span class="sxs-lookup"><span data-stu-id="38597-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="38597-149">Чтобы использовать этот метод расширения, необходимо получить доступ к нему из подсистемы Аранчорманажер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="38597-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="38597-150">Полный пример сохранения и несохраненных привязок см. в разделе привязки-> примеры привязок в образце [сцены подключаемого модуля Mixed Reality опенкср](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="38597-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Снимок экрана: панель иерархии открыта в редакторе Unity с выделенным образцом "привязки"](images/openxr-features-img-04.png)

![Снимок экрана: Панель инспектора открыта в редакторе Unity с выделенным образцом сценария "привязки"](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="38597-153">Взаимодействие контроллера движения и руки</span><span class="sxs-lookup"><span data-stu-id="38597-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="38597-154">Основные сведения о взаимодействии смешанной реальности в Unity см. в [руководстве по Unity для XR данных Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="38597-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="38597-155">Эта документация по Unity охватывает сопоставления от входных данных, относящихся к конкретному контроллеру, с более обобщенными **инпутфеатуреусажеами**, как можно идентифицировать и классифицировать доступные входные данные XR, как считывать их из этих входных данных и многое другое.</span><span class="sxs-lookup"><span data-stu-id="38597-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="38597-156">Подключаемый модуль Mixed Reality Опенкср предоставляет дополнительные профили взаимодействия ввода, сопоставленные со стандартным **инпутфеатуреусаже**, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="38597-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="38597-157">инпутфеатуреусаже</span><span class="sxs-lookup"><span data-stu-id="38597-157">InputFeatureUsage</span></span> | <span data-ttu-id="38597-158">HP reverbы G2 Controller (Опенкср)</span><span class="sxs-lookup"><span data-stu-id="38597-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="38597-159">HoloLens (Опенкср)</span><span class="sxs-lookup"><span data-stu-id="38597-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="38597-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="38597-160">primary2DAxis</span></span> | <span data-ttu-id="38597-161">Джойстик</span><span class="sxs-lookup"><span data-stu-id="38597-161">Joystick</span></span> | |
| <span data-ttu-id="38597-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="38597-162">primary2DAxisClick</span></span> | <span data-ttu-id="38597-163">Джойстик — щелчок</span><span class="sxs-lookup"><span data-stu-id="38597-163">Joystick - Click</span></span> | |
| <span data-ttu-id="38597-164">триггер</span><span class="sxs-lookup"><span data-stu-id="38597-164">trigger</span></span> | <span data-ttu-id="38597-165">Триггер</span><span class="sxs-lookup"><span data-stu-id="38597-165">Trigger</span></span>  | |
| <span data-ttu-id="38597-166">регулировки</span><span class="sxs-lookup"><span data-stu-id="38597-166">grip</span></span> | <span data-ttu-id="38597-167">Регулировки</span><span class="sxs-lookup"><span data-stu-id="38597-167">Grip</span></span> | <span data-ttu-id="38597-168">Воздушный нажим или сжатие</span><span class="sxs-lookup"><span data-stu-id="38597-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="38597-169">примарибуттон</span><span class="sxs-lookup"><span data-stu-id="38597-169">primaryButton</span></span> | <span data-ttu-id="38597-170">[X/A] — нажмите клавишу</span><span class="sxs-lookup"><span data-stu-id="38597-170">[X/A] - Press</span></span> | <span data-ttu-id="38597-171">Жест касания</span><span class="sxs-lookup"><span data-stu-id="38597-171">Air tap</span></span> |
| <span data-ttu-id="38597-172">секондарибуттон</span><span class="sxs-lookup"><span data-stu-id="38597-172">secondaryButton</span></span> | <span data-ttu-id="38597-173">[Y/B] — нажмите клавишу</span><span class="sxs-lookup"><span data-stu-id="38597-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="38597-174">грипбуттон</span><span class="sxs-lookup"><span data-stu-id="38597-174">gripButton</span></span> | <span data-ttu-id="38597-175">Захват и нажатие клавиши</span><span class="sxs-lookup"><span data-stu-id="38597-175">Grip - Press</span></span> | |
| <span data-ttu-id="38597-176">тригжербуттон</span><span class="sxs-lookup"><span data-stu-id="38597-176">triggerButton</span></span> | <span data-ttu-id="38597-177">Триггер-нажатие</span><span class="sxs-lookup"><span data-stu-id="38597-177">Trigger - Press</span></span> | |
| <span data-ttu-id="38597-178">менубуттон</span><span class="sxs-lookup"><span data-stu-id="38597-178">menuButton</span></span> | <span data-ttu-id="38597-179">Меню</span><span class="sxs-lookup"><span data-stu-id="38597-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="38597-180">AIM и захват</span><span class="sxs-lookup"><span data-stu-id="38597-180">Aim and Grip Poses</span></span>

<span data-ttu-id="38597-181">У вас есть доступ к двум наборам экземпляров через входные взаимодействия Опенкср:</span><span class="sxs-lookup"><span data-stu-id="38597-181">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="38597-182">Захват для отрисовки объектов в руки</span><span class="sxs-lookup"><span data-stu-id="38597-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="38597-183">Цель, указывающая на мир.</span><span class="sxs-lookup"><span data-stu-id="38597-183">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="38597-184">Дополнительные сведения об этой структуре и различиях между ними можно найти в [подкаталогах Опенкср Specification-input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="38597-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="38597-185">Представления, предоставляемые Инпутфеатуреусажес **девицепоситион**, **девицеротатион**, **девицевелоЦити** и **девицеангуларвелоЦити** , представляют собой OpenXR **захват** .</span><span class="sxs-lookup"><span data-stu-id="38597-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="38597-186">Инпутфеатуреусажес, связанные с захватом, определяются в [Коммонусажес](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="38597-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="38597-187">Представления, предоставляемые Инпутфеатуреусажес **поинтерпоситион**, **поинтерротатион**, **поинтервелоЦити** и **поинтерангуларвелоЦити** , представляют собой OpenXR **Цель** .</span><span class="sxs-lookup"><span data-stu-id="38597-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="38597-188">Эти Инпутфеатуреусажес не определены во вложенных файлах C#, поэтому необходимо определить собственный Инпутфеатуреусажес следующим образом:</span><span class="sxs-lookup"><span data-stu-id="38597-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="38597-189">хаптикс</span><span class="sxs-lookup"><span data-stu-id="38597-189">Haptics</span></span>

<span data-ttu-id="38597-190">Сведения об использовании хаптикс в системе ввода XR в Unity можно найти в [руководстве по Unity для Unity XR input-хаптикс](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="38597-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="38597-191">Что ожидается в ближайшее время</span><span class="sxs-lookup"><span data-stu-id="38597-191">What's coming soon</span></span>

<span data-ttu-id="38597-192">Следующие проблемы и отсутствующие функции известны с помощью Опенкср подключаемого модуля Mixed Reality **версии 0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="38597-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="38597-193">Мы работаем над этим и выпустили исправления и новые функции в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="38597-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="38597-194">**Арпланесубсистем** еще не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="38597-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="38597-195">**Арпланеманажер**, **АРРАЙКАСТМАНАЖЕР** и связанный API, такие как **аранчорманажер. аттачанчор** , также не поддерживаются в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="38597-196">**Привязка** еще не поддерживается с помощью удаленного взаимодействия holographic, но в ближайшем будущем.</span><span class="sxs-lookup"><span data-stu-id="38597-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="38597-197">Отслеживание **сетки вручную** , **QR-коды** и **ксрмешсубсистем** пока не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="38597-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="38597-198">Поддержка **пространственных привязок Azure** появилась в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="38597-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="38597-199">**ARM64** — единственная поддерживаемая платформа для приложений HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38597-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="38597-200">Платформа **ARM** поступает в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="38597-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="38597-201">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="38597-201">Troubleshooting</span></span>

<span data-ttu-id="38597-202">При приостановке и возобновлении работы приложения Unity в HoloLens 2 приложение не может корректно возобновить работу, что приводит к 4 вращающимся точкам в представлении HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38597-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="38597-203">Установка для **режима отправки глубины** значения " **нет** " в параметрах проекта опенкср в качестве обходного пути</span><span class="sxs-lookup"><span data-stu-id="38597-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
