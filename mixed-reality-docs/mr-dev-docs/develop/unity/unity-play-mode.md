---
title: Режим воспроизведения в Unity
description: Узнайте, как использовать режим воспроизведения в редакторе Unity для предварительного просмотра изменений приложения на устройстве без развертывания приложения.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, удаленное взаимодействие, удаленное взаимодействие с holographic, holographic удаленное взаимодействие, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, режим воспроизведения Unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547099"
---
# <a name="unity-play-mode"></a><span data-ttu-id="bd07c-104">Режим воспроизведения в Unity</span><span class="sxs-lookup"><span data-stu-id="bd07c-104">Unity Play Mode</span></span>

<span data-ttu-id="bd07c-105">Быстрый способ работы с проектом Unity — использование режима воспроизведения, который локально запускает приложение в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bd07c-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="bd07c-106">Unity использует holographic удаленное взаимодействие, чтобы обеспечить быстрый способ предварительного просмотра содержимого на реальном устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bd07c-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="bd07c-107">Режим воспроизведения также можно использовать с головным телефоном Windows Mixed Reality, подключенным к компьютеру разработки.</span><span class="sxs-lookup"><span data-stu-id="bd07c-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="bd07c-108">Настройка удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="bd07c-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="bd07c-109">Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bd07c-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="bd07c-110">Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.</span><span class="sxs-lookup"><span data-stu-id="bd07c-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="bd07c-111">Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="bd07c-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="bd07c-113">Holographic удаленное взаимодействие в режиме воспроизведения редактора Unity</span><span class="sxs-lookup"><span data-stu-id="bd07c-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="bd07c-114">Создание проекта Unity для UWP в проекте Visual Studio, а затем упаковка и развертывание на устройстве HoloLens 2 может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="bd07c-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="bd07c-115">Одним из решений является включение функции удаленного взаимодействия в holographic Editor, которая позволяет выполнять отладку сценария C# с помощью режима Play непосредственно на устройстве HoloLens 2 по сети.</span><span class="sxs-lookup"><span data-stu-id="bd07c-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="bd07c-116">Этот сценарий позволяет избежать издержек при создании и развертывании пакета UWP на удаленном устройстве.</span><span class="sxs-lookup"><span data-stu-id="bd07c-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="bd07c-117">Выполните действия, описанные в разделе [Настройка удаленного взаимодействия с holographic](#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="bd07c-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="bd07c-118">Откройте **Windows > XR > редактор Опенкср удаленное взаимодействие**:</span><span class="sxs-lookup"><span data-stu-id="bd07c-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-features-img-02.png)

3. <span data-ttu-id="bd07c-120">Введите IP-адрес, полученный из приложения holographic удаленного взаимодействия, и выберите **включить удаленное взаимодействие редактора** .</span><span class="sxs-lookup"><span data-stu-id="bd07c-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенными компонентами](images/openxr-features-img-03.png)

<span data-ttu-id="bd07c-122">Теперь можно нажать кнопку "Воспроизвести", чтобы воспроизвести приложение Unity в удаленном приложении holographic на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bd07c-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="bd07c-123">Вы также можете [присоединить Visual Studio к Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) для отладки скриптов C# в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="bd07c-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="bd07c-124">Начиная с версии 0.1.0, среда выполнения holographic Remoting не поддерживает привязки, а функции Аранчорманажер не будут работать через удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="bd07c-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="bd07c-125">Эта функция появилась в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="bd07c-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="bd07c-126">Режим воспроизведения Unity с holographic удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="bd07c-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="bd07c-127">С помощью удаленного взаимодействия с holographic вы можете столкнуться с приложением на HoloLens, когда оно выполняется в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bd07c-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="bd07c-128">Входные данные с помощью взгляда, жеста, голоса и пространственного сопоставления отправляются из HoloLens на компьютер.</span><span class="sxs-lookup"><span data-stu-id="bd07c-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="bd07c-129">Затем отображаемые кадры отправляются обратно в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bd07c-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="bd07c-130">Это отличный способ быстрой отладки приложения без создания и развертывания полного проекта.</span><span class="sxs-lookup"><span data-stu-id="bd07c-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="bd07c-131">Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение.</span><span class="sxs-lookup"><span data-stu-id="bd07c-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="bd07c-132">Дополнительные сведения можно найти в документации по [удаленному проигрывателю holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="bd07c-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="bd07c-133">Для достижения лучших результатов убедитесь, что приложение правильно устанавливает [фокусную точку](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="bd07c-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="bd07c-134">Это помогает более удачному удаленному взаимодействию лучше адаптировать сцену к задержке беспроводного подключения.</span><span class="sxs-lookup"><span data-stu-id="bd07c-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd07c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="bd07c-135">See Also</span></span>

* [<span data-ttu-id="bd07c-136">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="bd07c-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
