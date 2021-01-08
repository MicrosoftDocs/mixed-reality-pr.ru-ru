---
title: Развертывание на устройстве в Unreal
description: Узнайте все, что необходимо знать о развертывании нереальных приложений смешанной реальности в HoloLens 2 с помощью редактора или портала устройств.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Нереал, Нереал. 4, UE4, HoloLens, HoloLens 2, Mixed Reality, развертывание на устройстве, ПК, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
appliesto:
- HoloLens 2
ms.openlocfilehash: 24b2c013e1c9f25f54be9a6fefec8a86846c1746
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009754"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="c0909-104">Развертывание на устройстве в Unreal</span><span class="sxs-lookup"><span data-stu-id="c0909-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="c0909-105">Существует два способа развертывания нереального приложения в HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="c0909-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="c0909-106">Непосредственно из нереального редактора</span><span class="sxs-lookup"><span data-stu-id="c0909-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="c0909-107">Как пакет, отправленный через портал устройств</span><span class="sxs-lookup"><span data-stu-id="c0909-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="c0909-108">Для обоих вариантов требуется настроить HoloLens для использования [портала устройств](../platform-capabilities-and-apis/using-the-windows-device-portal.md) для разработки.</span><span class="sxs-lookup"><span data-stu-id="c0909-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="c0909-109">Развертывание на устройстве из нереального редактора</span><span class="sxs-lookup"><span data-stu-id="c0909-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="c0909-110">Щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** .</span><span class="sxs-lookup"><span data-stu-id="c0909-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="c0909-111">Изначально параметр устройства HoloLens будет неактивен.</span><span class="sxs-lookup"><span data-stu-id="c0909-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Параметры раскрывающегося списка запуска](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="c0909-113">Откройте **Device Manager** и обратите внимание, что HoloLens не будет автоматически отображаться в списке устройств.</span><span class="sxs-lookup"><span data-stu-id="c0909-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="c0909-114">Разверните раздел **Добавление устройства, не имеющего списка** .</span><span class="sxs-lookup"><span data-stu-id="c0909-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="c0909-115">Выберите **HoloLens** в качестве **платформы**.</span><span class="sxs-lookup"><span data-stu-id="c0909-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="c0909-116">Введите IP-адрес устройства и сведения о портах, разделенные двоеточием, в качестве идентификатора устройства.</span><span class="sxs-lookup"><span data-stu-id="c0909-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="c0909-117">Например, "127.0.0.1:10080" (при подключении через USB).</span><span class="sxs-lookup"><span data-stu-id="c0909-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="c0909-118">Используйте учетные данные пользователя и пароля на портале устройства.</span><span class="sxs-lookup"><span data-stu-id="c0909-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="c0909-119">Нажмите кнопку **Добавить** и закройте Диспетчер устройств.</span><span class="sxs-lookup"><span data-stu-id="c0909-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="c0909-120">При возникновении ошибки, например неправильного адреса или учетных данных пользователя, сообщение выводится в выходной журнал.</span><span class="sxs-lookup"><span data-stu-id="c0909-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Добавление устройства, не добавленного в список](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="c0909-122">Снова щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** . на этот раз вы должны увидеть только что добавленное устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c0909-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="c0909-123">Выберите устройство HoloLens для сборки и развертывания в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c0909-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="c0909-124">Сборка для устройства может потребовать перекомпиляции шейдеров (особенно при первом запуске). это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="c0909-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="c0909-125">Не позволяйте устройству переходить в спящий режим до тех пор, пока не будет запущена приложение (возможно, его придется поработать).</span><span class="sxs-lookup"><span data-stu-id="c0909-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="c0909-126">В противном случае компиляция шейдера завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c0909-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="c0909-127">Развертывание на устройстве с помощью портала устройств</span><span class="sxs-lookup"><span data-stu-id="c0909-127">Deploying to device via device portal</span></span>

<span data-ttu-id="c0909-128">Подробные инструкции по упаковке и развертыванию приложения см. в статье [серия нереальных руководств](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="c0909-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c0909-129">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="c0909-129">Next Development Checkpoint</span></span>

<span data-ttu-id="c0909-130">Если вы подготовились к нереальному пути разработки, мы разработали этап развертывания.</span><span class="sxs-lookup"><span data-stu-id="c0909-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="c0909-131">Здесь можно продолжить добавление дополнительных служб:</span><span class="sxs-lookup"><span data-stu-id="c0909-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0909-132">Расширенные службы</span><span class="sxs-lookup"><span data-stu-id="c0909-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="c0909-133">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device).</span><span class="sxs-lookup"><span data-stu-id="c0909-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
