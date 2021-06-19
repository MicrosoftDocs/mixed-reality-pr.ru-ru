---
title: Режим воспроизведения в Unity
description: Узнайте, как использовать режим воспроизведения в редакторе Unity для предварительного просмотра изменений приложения на устройстве без развертывания приложения.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, удаленное взаимодействие, удаленное взаимодействие с holographic, holographic удаленное взаимодействие, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, режим воспроизведения Unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392299"
---
# <a name="unity-play-mode"></a><span data-ttu-id="1aa02-104">Режим воспроизведения в Unity</span><span class="sxs-lookup"><span data-stu-id="1aa02-104">Unity Play Mode</span></span>

<span data-ttu-id="1aa02-105">Быстрый способ работы с проектом Unity — использование режима воспроизведения, который локально запускает приложение в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1aa02-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="1aa02-106">Unity использует holographic удаленное взаимодействие, чтобы обеспечить быстрый способ предварительного просмотра содержимого на реальном устройстве HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1aa02-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="1aa02-107">Режим воспроизведения также можно использовать с головным телефоном Windows Mixed Reality, подключенным к компьютеру разработки.</span><span class="sxs-lookup"><span data-stu-id="1aa02-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="1aa02-108">Настройка удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="1aa02-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="1aa02-109">Сначала необходимо [установить приложение с удаленным проигрывателем holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) из Microsoft Store в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1aa02-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="1aa02-110">Запустите приложение удаленного проигрывателя holographic в HoloLens 2, и вы увидите номер версии и IP-адрес для подключения.</span><span class="sxs-lookup"><span data-stu-id="1aa02-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="1aa02-111">Для работы с подключаемым модулем Опенкср потребуется v версии 2.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="1aa02-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Снимок экрана удаленного проигрывателя holographic, работающего в HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="1aa02-113">Режим воспроизведения Unity с holographic удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="1aa02-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="1aa02-114">С помощью удаленного взаимодействия с holographic вы можете столкнуться с приложением на HoloLens, когда оно выполняется в редакторе Unity на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1aa02-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="1aa02-115">Входные данные с помощью взгляда, жеста, голоса и пространственного сопоставления отправляются из HoloLens на компьютер.</span><span class="sxs-lookup"><span data-stu-id="1aa02-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="1aa02-116">Затем отображаемые кадры отправляются обратно в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1aa02-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="1aa02-117">Это отличный способ быстрой отладки приложения без создания и развертывания полного проекта.</span><span class="sxs-lookup"><span data-stu-id="1aa02-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="1aa02-118">Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение.</span><span class="sxs-lookup"><span data-stu-id="1aa02-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="1aa02-119">Дополнительные сведения можно найти в документации по [удаленному проигрывателю holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="1aa02-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="1aa02-120">Для достижения лучших результатов убедитесь, что приложение правильно устанавливает [фокусную точку](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="1aa02-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="1aa02-121">Это помогает более удачному удаленному взаимодействию лучше адаптировать сцену к задержке беспроводного подключения.</span><span class="sxs-lookup"><span data-stu-id="1aa02-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1aa02-122">См. также</span><span class="sxs-lookup"><span data-stu-id="1aa02-122">See Also</span></span>

* [<span data-ttu-id="1aa02-123">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="1aa02-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
