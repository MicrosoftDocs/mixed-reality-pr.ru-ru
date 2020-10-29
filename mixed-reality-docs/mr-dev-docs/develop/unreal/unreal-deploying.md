---
title: Развертывание на устройстве в Unreal
description: Рекомендации по развертыванию на устройство в нереальном режиме в HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Нереал, Нереал. 4, UE4, HoloLens, HoloLens 2, Mixed Reality, развертывание на устройстве, ПК, документация
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691956"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="cc243-104">Развертывание на устройстве в Unreal</span><span class="sxs-lookup"><span data-stu-id="cc243-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="cc243-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="cc243-105">Overview</span></span>
<span data-ttu-id="cc243-106">Существует два способа развертывания нереального приложения в HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="cc243-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="cc243-107">Непосредственно из нереального редактора</span><span class="sxs-lookup"><span data-stu-id="cc243-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="cc243-108">Как пакет, отправленный через портал устройств</span><span class="sxs-lookup"><span data-stu-id="cc243-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="cc243-109">Для обоих вариантов требуется настроить HoloLens для использования [портала устройств](../platform-capabilities-and-apis/using-the-windows-device-portal.md) для разработки.</span><span class="sxs-lookup"><span data-stu-id="cc243-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="cc243-110">Развертывание на устройстве из нереального редактора</span><span class="sxs-lookup"><span data-stu-id="cc243-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="cc243-111">Щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** .</span><span class="sxs-lookup"><span data-stu-id="cc243-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="cc243-112">Изначально параметр устройства HoloLens будет неактивен.</span><span class="sxs-lookup"><span data-stu-id="cc243-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Параметры раскрывающегося списка запуска](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="cc243-114">Откройте **Device Manager** .</span><span class="sxs-lookup"><span data-stu-id="cc243-114">Open the **Device Manager** .</span></span> <span data-ttu-id="cc243-115">Обратите внимание, что HoloLens не будет автоматически отображаться в списке устройств.</span><span class="sxs-lookup"><span data-stu-id="cc243-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="cc243-116">Разверните раздел **Добавление устройства, не имеющего списка** .</span><span class="sxs-lookup"><span data-stu-id="cc243-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="cc243-117">Выберите **HoloLens** в качестве **платформы** .</span><span class="sxs-lookup"><span data-stu-id="cc243-117">Select **HoloLens** as your **Platform** .</span></span>

5. <span data-ttu-id="cc243-118">Введите IP-адрес устройства и сведения о портах, разделенные двоеточием, в качестве идентификатора устройства.</span><span class="sxs-lookup"><span data-stu-id="cc243-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="cc243-119">Например, "127.0.0.1:10080" (при подключении через USB).</span><span class="sxs-lookup"><span data-stu-id="cc243-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="cc243-120">Используйте учетные данные пользователя и пароля на портале устройства.</span><span class="sxs-lookup"><span data-stu-id="cc243-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="cc243-121">Нажмите кнопку **Добавить** и закройте Диспетчер устройств.</span><span class="sxs-lookup"><span data-stu-id="cc243-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="cc243-122">В случае ошибки (например, неправильного адреса, имени пользователя или пароля) сообщение будет напечатано в выходном журнале.</span><span class="sxs-lookup"><span data-stu-id="cc243-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Добавление устройства, не добавленного в список](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="cc243-124">Снова щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** . на этот раз вы должны увидеть только что добавленное устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cc243-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="cc243-125">Выберите устройство HoloLens для сборки и развертывания в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cc243-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="cc243-126">Сборка для устройства может потребовать перекомпиляции шейдеров (особенно при первом запуске). это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="cc243-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="cc243-127">Не позволяйте устройству переходить в спящий режим до тех пор, пока не будет запущена приложение (возможно, его придется поработать).</span><span class="sxs-lookup"><span data-stu-id="cc243-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="cc243-128">В противном случае компиляция шейдера завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="cc243-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="cc243-129">Развертывание на устройстве с помощью портала устройств</span><span class="sxs-lookup"><span data-stu-id="cc243-129">Deploying to device via device portal</span></span>

<span data-ttu-id="cc243-130">Подробные инструкции по [упаковке и развертыванию приложения](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) можно найти в последнем разделе Начало работы с нереальными сериями руководств.</span><span class="sxs-lookup"><span data-stu-id="cc243-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cc243-131">Контрольная точка следующей разработки</span><span class="sxs-lookup"><span data-stu-id="cc243-131">Next Development Checkpoint</span></span>

<span data-ttu-id="cc243-132">Если вы подготовились к нереальному пути к контрольной точке разработки, мы собрались, что вы находитесь на стадии развертывания.</span><span class="sxs-lookup"><span data-stu-id="cc243-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="cc243-133">Здесь можно перейти к добавлению дополнительных служб:</span><span class="sxs-lookup"><span data-stu-id="cc243-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc243-134">Дополнительные службы</span><span class="sxs-lookup"><span data-stu-id="cc243-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="cc243-135">Вы всегда можете вернуться к [нереальным контрольным точкам разработки](unreal-development-overview.md#4-deploying-to-a-device) в любое время.</span><span class="sxs-lookup"><span data-stu-id="cc243-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>