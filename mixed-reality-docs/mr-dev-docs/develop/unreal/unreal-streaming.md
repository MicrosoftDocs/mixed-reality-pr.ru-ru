---
title: Потоковая передача в Unreal
description: Сведения о том, как осуществлять потоковую передачу приложений Unreal на устройства HoloLens 2, а также об ограничениях потоковой передачи и параметрах командной строки.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, потоковая передача, компьютер, голографическое удаленное взаимодействие с приложением, проигрыватель для голографического удаленного взаимодействия, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: a0c376ed6366e57b8a521c52db2fc02fcd1c0285
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009954"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="1b335-104">Потоковая передача в Unreal</span><span class="sxs-lookup"><span data-stu-id="1b335-104">Streaming in Unreal</span></span>

<span data-ttu-id="1b335-105">Потоковая передача с компьютера в HoloLens обеспечивает два основных преимущества:</span><span class="sxs-lookup"><span data-stu-id="1b335-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="1b335-106">Ваше приложение смешанной реальности может использовать вычислительные мощности компьютера.</span><span class="sxs-lookup"><span data-stu-id="1b335-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="1b335-107">Ускоренная итерация разработки.</span><span class="sxs-lookup"><span data-stu-id="1b335-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="1b335-108">Чтобы приступить к работе, скачайте [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) на устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1b335-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="1b335-109">Holographic Remoting Player позволит вашему приложению передавать данные в потоковом режиме непосредственно на проигрыватель удаленного взаимодействия на HoloLens из следующих источников:</span><span class="sxs-lookup"><span data-stu-id="1b335-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="1b335-110">редактор Unreal Engine;</span><span class="sxs-lookup"><span data-stu-id="1b335-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="1b335-111">упакованный исполняемый файл Windows.</span><span class="sxs-lookup"><span data-stu-id="1b335-111">A packaged Windows executable</span></span> 

<span data-ttu-id="1b335-112">При потоковой передаче вы получаете доступ практически ко всем возможностям HoloLens, которые можно использовать при запуске приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="1b335-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="1b335-113">К ним относятся [отслеживание суставов рук](unreal-hand-tracking.md), если вы используете HoloLens 2, [пространственное картирование](unreal-spatial-mapping.md) и [пространственные привязки](unreal-spatial-anchors.md). Но при этом недоступны функции из этого [списка](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="1b335-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="1b335-114">Качество потоковой передачи в значительной степени зависит от уровня сигнала вашей беспроводной сети.</span><span class="sxs-lookup"><span data-stu-id="1b335-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="1b335-115">Все возможности автоматически включаются в приложении Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="1b335-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="1b335-116">Если вы обнаружите возможность, для включения которой требуется разрешение пользователя (например, отслеживание движения глаз) при потоковой передаче, но не при выполнении на устройстве, убедитесь, что вы включили необходимые возможности в параметрах проекта.</span><span class="sxs-lookup"><span data-stu-id="1b335-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="1b335-117">Ограничения потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="1b335-117">Streaming limitations</span></span>

<span data-ttu-id="1b335-118">Виртуальные руки, камера HoloLens и системная клавиатура недоступны при потоковой передаче.</span><span class="sxs-lookup"><span data-stu-id="1b335-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="1b335-119">Обратите внимание, что речевой ввод для приложений с потоковой передачей можно реализовать через микрофон компьютера, с которого выполняется потоковая передача.</span><span class="sxs-lookup"><span data-stu-id="1b335-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="1b335-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="1b335-120">OpenXR</span></span>

<span data-ttu-id="1b335-121">Unreal 4.26 на OpenXR поддерживает потоковую передачу в проигрыватель Holographic Remoting Player версий не младше 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="1b335-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="1b335-122">Для потоковой передачи OpenXR в версии 2.4.0 отсутствует поддержка пространственного сопоставления и пространственных привязок.</span><span class="sxs-lookup"><span data-stu-id="1b335-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="1b335-123">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="1b335-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1b335-124"><strong>Источник</strong></span><span class="sxs-lookup"><span data-stu-id="1b335-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="1b335-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens первого поколения</strong></a></span><span class="sxs-lookup"><span data-stu-id="1b335-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="1b335-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="1b335-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="1b335-127"><strong>Иммерсивные гарнитуры</strong></span><span class="sxs-lookup"><span data-stu-id="1b335-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1b335-128">Unreal Editor</span><span class="sxs-lookup"><span data-stu-id="1b335-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="1b335-129">✔️</span><span class="sxs-lookup"><span data-stu-id="1b335-129">✔️</span></span></td>
        <td><span data-ttu-id="1b335-130">✔️</span><span class="sxs-lookup"><span data-stu-id="1b335-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1b335-131">Пакет Windows</span><span class="sxs-lookup"><span data-stu-id="1b335-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1b335-132">✔️</span><span class="sxs-lookup"><span data-stu-id="1b335-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="1b335-133">Потоковая передача из Unreal Editor</span><span class="sxs-lookup"><span data-stu-id="1b335-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="1b335-134">Потоковая передача данных из Unreal Editor на устройство HoloLens обеспечивает разработчикам значительные преимущества при тестировании, а именно отсутствие необходимости ждать, пока приложение будет собрано и развернуто, для оценки обновлений.</span><span class="sxs-lookup"><span data-stu-id="1b335-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="1b335-135">Подробные инструкции по [потоковой передаче из Unreal Editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) можно найти в нашей серии руководств.</span><span class="sxs-lookup"><span data-stu-id="1b335-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="1b335-136">Потоковая передача из упакованного исполняемого файла Windows</span><span class="sxs-lookup"><span data-stu-id="1b335-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="1b335-137">В Unreal 4.25.1 и более поздних версий вы можете передавать данные вашего приложения на устройство HoloLens 2 в потоковом режиме из упакованного исполняемого файла Windows:</span><span class="sxs-lookup"><span data-stu-id="1b335-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="1b335-138">Выберите **File > Package Project > Windows** (Файл > Проект пакета > Windows) в меню редактора.</span><span class="sxs-lookup"><span data-stu-id="1b335-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="1b335-139">Выберите расположение для сохранения пакета и выберите элемент **Select Folder** (Выбрать папку).</span><span class="sxs-lookup"><span data-stu-id="1b335-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="1b335-140">После завершения сборки пакета откройте инструмент **Holographic Remoting Player** на HoloLens 2 и запишите значение IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="1b335-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="1b335-141">Оставьте **Holographic Remoting Player** открытым и с помощью командной строки выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1b335-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="1b335-142">С помощью команды cd перейдите в локальный каталог с сохраненным пакетом.</span><span class="sxs-lookup"><span data-stu-id="1b335-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="1b335-143">Введите следующую команду: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="1b335-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="1b335-144">Имя приложения в параметрах проекта должно быть автоматически использовано для создания пакета Windows.</span><span class="sxs-lookup"><span data-stu-id="1b335-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="1b335-145">Если по какой-либо причине имена отличаются, используйте имя исполняемого файла Windows в командной строке.</span><span class="sxs-lookup"><span data-stu-id="1b335-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="1b335-146">Нажмите клавишу ВВОД, и ваше приложение начнет потоковую передачу.</span><span class="sxs-lookup"><span data-stu-id="1b335-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="1b335-147">Параметры командной строки</span><span class="sxs-lookup"><span data-stu-id="1b335-147">Command line options</span></span>

<span data-ttu-id="1b335-148">Дополнительные параметры командной строки для потоковой передачи с каждой платформы в Unreal Engine 4.26+ можно найти в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="1b335-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="1b335-149">См. также статью</span><span class="sxs-lookup"><span data-stu-id="1b335-149">See also</span></span>

* [<span data-ttu-id="1b335-150">История версий голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1b335-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="1b335-151">Создание пользовательского проигрывателя для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1b335-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="1b335-152">Установка безопасного подключения с использованием голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="1b335-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
