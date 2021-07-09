---
title: Развертывание и отладка с помощью Visual Studio
description: Узнайте, как создавать, отлаживать и развертывать приложения для HoloLens и Windows Mixed Reality с помощью Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, смешанная реальность, отладка, развертывание
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543230"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="e61da-104">Развертывание и отладка с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e61da-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="e61da-105">Независимо от того, что вы используете для разработки приложения смешанной реальности — DirectX или Unity, для отладки и развертывания лучшим средством будет Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e61da-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="e61da-106">В этом разделе вы научитесь:</span><span class="sxs-lookup"><span data-stu-id="e61da-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="e61da-107">развертывать приложения на иммерсивной гарнитуре HoloLens или Windows Mixed Reality с помощью Visual Studio;</span><span class="sxs-lookup"><span data-stu-id="e61da-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="e61da-108">использовать эмулятор HoloLens, встроенный в Visual Studio;</span><span class="sxs-lookup"><span data-stu-id="e61da-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="e61da-109">отлаживать приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e61da-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e61da-110">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="e61da-110">Prerequisites</span></span>

1. <span data-ttu-id="e61da-111">Инструкции по установке см. в разделе [Установка инструментов](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="e61da-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="e61da-112">Создайте проект универсального приложения для Windows в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e61da-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="e61da-113">Для HoloLens (1-го поколения) используйте Visual Studio 2017 или более позднюю версию.</span><span class="sxs-lookup"><span data-stu-id="e61da-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="e61da-114">Для HoloLens 2 используйте Visual Studio 2019 16.2 или более позднюю версию.</span><span class="sxs-lookup"><span data-stu-id="e61da-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="e61da-115">Поддерживаются языки C# и C++.</span><span class="sxs-lookup"><span data-stu-id="e61da-115">C# and C++ are supported.</span></span> <span data-ttu-id="e61da-116">(Вы можете также следовать инструкции по [созданию приложения в Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="e61da-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="e61da-117">Включение режима разработчика</span><span class="sxs-lookup"><span data-stu-id="e61da-117">Enabling Developer Mode</span></span>

<span data-ttu-id="e61da-118">Для начала включите **режим разработчика** на устройстве, чтобы среда Visual Studio могла к нему подключиться.</span><span class="sxs-lookup"><span data-stu-id="e61da-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="e61da-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="e61da-119">HoloLens</span></span>

1. <span data-ttu-id="e61da-120">Включите устройство HoloLens и наденьте его.</span><span class="sxs-lookup"><span data-stu-id="e61da-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="e61da-121">Выполните [жест "Пуск"](../../design/system-gesture.md), чтобы запустить главное меню.</span><span class="sxs-lookup"><span data-stu-id="e61da-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="e61da-122">Щелкните плитку **Параметры**, чтобы запустить приложение в среде.</span><span class="sxs-lookup"><span data-stu-id="e61da-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="e61da-123">Выберите пункт меню **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="e61da-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="e61da-124">Выберите пункт меню **Для разработчиков**.</span><span class="sxs-lookup"><span data-stu-id="e61da-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="e61da-125">Включите **Использование функций разработчика**, чтобы развертывать приложения из Visual Studio в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e61da-125">Enable **Use developer features** to deploy apps from Visual Studio to your HoloLens.</span></span> <span data-ttu-id="e61da-126">Если на устройстве установлена платформа Windows Holographic версии 21H1 или более поздней, также включите **Обнаружение устройств**.</span><span class="sxs-lookup"><span data-stu-id="e61da-126">If your device is running Windows Holographic version 21H1 or newer, also enable **Device discovery**.</span></span>
7. <span data-ttu-id="e61da-127">Дополнительно Прокрутите вниз и включите **Портал устройств**, чтобы подключаться к [порталу устройств Windows](using-the-windows-device-portal.md) на HoloLens с помощью веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="e61da-127">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="e61da-128">Компьютер с Windows</span><span class="sxs-lookup"><span data-stu-id="e61da-128">Windows PC</span></span>

<span data-ttu-id="e61da-129">При работе с гарнитурой Windows Mixed Reality, подключенной к компьютеру, на этом компьютере необходимо включить **Режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="e61da-129">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="e61da-130">Перейдите в раздел **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="e61da-130">Go to **Settings**</span></span>
2. <span data-ttu-id="e61da-131">Выберите **Обновление и безопасность**.</span><span class="sxs-lookup"><span data-stu-id="e61da-131">Select **Update and Security**</span></span>
3. <span data-ttu-id="e61da-132">Выберите **Для разработчиков**.</span><span class="sxs-lookup"><span data-stu-id="e61da-132">Select **For developers**</span></span>
4. <span data-ttu-id="e61da-133">Включите **Режим разработчика**, прочитайте заявление об отказе от ответственности для выбранного параметра, затем щелкните "Да", чтобы принять изменения.</span><span class="sxs-lookup"><span data-stu-id="e61da-133">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="e61da-134">Развертывание приложения HoloLens по Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="e61da-134">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="e61da-135">Настройте проект Visual Studio со следующими свойствами:</span><span class="sxs-lookup"><span data-stu-id="e61da-135">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="e61da-136">Выберите варианты компиляции приложений.</span><span class="sxs-lookup"><span data-stu-id="e61da-136">Select your apps compilation options</span></span>
    * <span data-ttu-id="e61da-137">Для проектов Unity выберите **Выпуск** или **Мастер**.</span><span class="sxs-lookup"><span data-stu-id="e61da-137">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="e61da-138">Для всех остальных проектов выберите **Выпуск**.</span><span class="sxs-lookup"><span data-stu-id="e61da-138">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="e61da-139">Полные определения для каждого варианта компиляции можно найти в разделе [Создание и развертывание решений Unity в Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="e61da-139">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="e61da-140">Выберите конфигурацию сборки в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="e61da-140">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="e61da-141">Выберите **Удаленный компьютер** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="e61da-141">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Удаленный компьютер как цель развертывания в Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="e61da-143">Затем необходимо установить удаленное подключение.</span><span class="sxs-lookup"><span data-stu-id="e61da-143">Next, you need to set your remote connection.</span></span> <span data-ttu-id="e61da-144">Для проектов C++ и JavaScript выберите **Проект > Свойства > Свойства конфигурации > Отладка**.</span><span class="sxs-lookup"><span data-stu-id="e61da-144">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="e61da-145">Если вы работаете с проектом C#, автоматически откроется диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="e61da-145">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="e61da-146">Если диалоговое окно удаленного подключения не отображается в проекте C#, его можно открыть вручную в меню **Properties > Debug** (Свойства > Отладка).</span><span class="sxs-lookup"><span data-stu-id="e61da-146">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="e61da-147">Введите IP-адрес своего устройства в поле **Адрес** или **Имя компьютера**.</span><span class="sxs-lookup"><span data-stu-id="e61da-147">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="e61da-148">IP-адрес HoloLens можно найти в меню **Параметры > Сеть и Интернет > Дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="e61da-148">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="e61da-149">Всегда рекомендуется вводить IP-адрес вручную и не пользоваться функцией автоматического обнаружения.</span><span class="sxs-lookup"><span data-stu-id="e61da-149">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="e61da-150">Задайте для параметра **Режим аутентификации** значение **Универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="e61da-150">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Диалоговое окно удаленного подключения в Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="e61da-152">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="e61da-152">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="e61da-153">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="e61da-153">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="e61da-154">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="e61da-154">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="e61da-156">При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="e61da-156">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="e61da-157">Выполните приведенные ниже инструкции по **связыванию устройства**.</span><span class="sxs-lookup"><span data-stu-id="e61da-157">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="e61da-158">Развертывание приложения HoloLens по USB</span><span class="sxs-lookup"><span data-stu-id="e61da-158">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="e61da-159">Выберите варианты компиляции приложений.</span><span class="sxs-lookup"><span data-stu-id="e61da-159">Select your apps compilation options</span></span>
    * <span data-ttu-id="e61da-160">Для проектов Unity выберите **Выпуск** или **Мастер**.</span><span class="sxs-lookup"><span data-stu-id="e61da-160">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="e61da-161">Для всех остальных проектов выберите **Выпуск**.</span><span class="sxs-lookup"><span data-stu-id="e61da-161">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="e61da-162">Полные определения для каждого варианта компиляции можно найти в разделе [Создание и развертывание решений Unity в Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="e61da-162">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="e61da-163">Выберите конфигурацию сборки в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="e61da-163">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="e61da-164">Выберите **Устройство** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="e61da-164">Select **Device** in the deployment target drop-down menu</span></span>

![Развертывание устройства в Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="e61da-166">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="e61da-166">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="e61da-167">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="e61da-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="e61da-168">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="e61da-168">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="e61da-170">При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="e61da-170">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="e61da-171">Выполните приведенные ниже инструкции по **связыванию устройства**.</span><span class="sxs-lookup"><span data-stu-id="e61da-171">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="e61da-172">Если при развертывании приложения по USB возникает значительная задержка, мы рекомендуем воспользоваться [инструкциями для удаленного компьютера](#deploying-a-hololens-app-over-wi-fi) из предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="e61da-172">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="e61da-173">Развертывание приложения в эмуляторе HoloLens</span><span class="sxs-lookup"><span data-stu-id="e61da-173">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="e61da-174">Убедитесь, что вы **[установили эмулятор HoloLens 2 или HoloLens (1-го поколения)](../install-the-tools.md#installation-checklist)** .</span><span class="sxs-lookup"><span data-stu-id="e61da-174">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="e61da-175">Выберите конфигурацию сборки и эмулятор в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="e61da-175">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="e61da-176">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="e61da-176">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="e61da-177">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="e61da-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="e61da-178">Выберите **Build > Deploy** (Сборка > Развернуть), чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="e61da-178">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="e61da-180">Развертывание приложения виртуальной реальности на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="e61da-180">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="e61da-181">Чтобы использовать иммерсивную гарнитуру Windows Mixed Reality, которая подключается к компьютеру, или [эмулятор смешанной реальности](using-the-windows-mixed-reality-simulator.md), выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="e61da-181">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="e61da-182">Выберите для приложения конфигурацию сборки **x86** или **x64**.</span><span class="sxs-lookup"><span data-stu-id="e61da-182">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="e61da-183">Выберите **Локальный компьютер** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="e61da-183">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="e61da-184">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="e61da-184">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="e61da-185">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="e61da-185">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="e61da-186">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="e61da-186">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="e61da-187">Связывание устройства</span><span class="sxs-lookup"><span data-stu-id="e61da-187">Pairing your device</span></span>

<span data-ttu-id="e61da-188">При первом развертывании приложения из Visual Studio на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="e61da-188">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="e61da-189">Создайте ПИН-код на HoloLens, запустив приложение Settings, выберите **Update > For Developers** (Обновление > Для разработчиков) и коснитесь действия **Pair** (Связать).</span><span class="sxs-lookup"><span data-stu-id="e61da-189">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="e61da-190">Когда ПИН-код появится в HoloLens, введите его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e61da-190">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="e61da-191">После завершения связывания коснитесь **Done** (Готово) на HoloLens, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="e61da-191">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="e61da-192">Теперь этот компьютер связан с HoloLens, и приложения можно развертывать автоматически.</span><span class="sxs-lookup"><span data-stu-id="e61da-192">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="e61da-193">Повторите эти действия для всех остальных компьютеров, которые используются для развертывания приложений в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e61da-193">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="e61da-194">Чтобы отменить связь HoloLens со всеми связанными компьютерами, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="e61da-194">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="e61da-195">Откройте приложение **Settings**, перейдите к разделу **Update > For Developers** (Обновление > Для разработчиков) и коснитесь элемента **Clear** (Очистить).</span><span class="sxs-lookup"><span data-stu-id="e61da-195">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="e61da-196">Отладчик графики для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="e61da-196">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="e61da-197">Инструменты диагностики графики в Visual Studio очень полезны для создания и оптимизации голографического приложения.</span><span class="sxs-lookup"><span data-stu-id="e61da-197">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="e61da-198">Подробные сведения см. в разделе [Диагностика графики в Visual Studio](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) на сайте MSDN.</span><span class="sxs-lookup"><span data-stu-id="e61da-198">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="e61da-199">**Запуск отладчика графики**</span><span class="sxs-lookup"><span data-stu-id="e61da-199">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="e61da-200">Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.</span><span class="sxs-lookup"><span data-stu-id="e61da-200">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="e61da-201">Выберите **Отладка > Графика > Начать диагностику**.</span><span class="sxs-lookup"><span data-stu-id="e61da-201">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="e61da-202">При первом запуске диагностики для HoloLens может появиться сообщение об ошибке "Отказано в доступе".</span><span class="sxs-lookup"><span data-stu-id="e61da-202">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="e61da-203">Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="e61da-203">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="e61da-204">Профилирование</span><span class="sxs-lookup"><span data-stu-id="e61da-204">Profiling</span></span>

<span data-ttu-id="e61da-205">Инструменты профилирования Visual Studio позволяют анализировать производительность и использование ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="e61da-205">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="e61da-206">Сюда входят инструменты для оптимизации использования ЦП, памяти, графического процессора и сети.</span><span class="sxs-lookup"><span data-stu-id="e61da-206">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="e61da-207">Подробные сведения см. в разделе [Запуск средств диагностики без отладки](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) на сайте MSDN.</span><span class="sxs-lookup"><span data-stu-id="e61da-207">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="e61da-208">**Запуск инструментов профилирования для HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e61da-208">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="e61da-209">Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.</span><span class="sxs-lookup"><span data-stu-id="e61da-209">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="e61da-210">Выберите **Отладка > Запустить средства диагностики без отладки**.</span><span class="sxs-lookup"><span data-stu-id="e61da-210">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="e61da-211">Выберите инструменты, которые вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="e61da-211">Select the tools you want to use</span></span>
4. <span data-ttu-id="e61da-212">Выберите команду **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="e61da-212">Select **Start**</span></span>
5. <span data-ttu-id="e61da-213">При первом запуске диагностики без отладки для HoloLens может появиться сообщение об ошибке "Отказано в доступе".</span><span class="sxs-lookup"><span data-stu-id="e61da-213">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="e61da-214">Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="e61da-214">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="e61da-215">Отладка установленного или работающего приложения</span><span class="sxs-lookup"><span data-stu-id="e61da-215">Debugging an installed or running app</span></span>

<span data-ttu-id="e61da-216">Visual Studio можно использовать для отладки установленного универсального приложения для Windows, не развертывая его из проекта Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e61da-216">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="e61da-217">Это удобно в тех случаях, когда нужно выполнить отладку установленного пакета приложения или уже запущенного приложения.</span><span class="sxs-lookup"><span data-stu-id="e61da-217">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="e61da-218">Выберите **Отладка > Другие целевые объекты отладки > Отладка установленного пакета приложения**.</span><span class="sxs-lookup"><span data-stu-id="e61da-218">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="e61da-219">Выберите цель **Удаленный компьютер**, если используется HoloLens, или **Локальный компьютер**, если используются иммерсивные гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="e61da-219">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="e61da-220">Введите **IP-адрес** устройства.</span><span class="sxs-lookup"><span data-stu-id="e61da-220">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="e61da-221">Выберите режим аутентификации **Universal** (Универсальная).</span><span class="sxs-lookup"><span data-stu-id="e61da-221">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="e61da-222">В окне отображаются как работающие, так и неактивные приложения.</span><span class="sxs-lookup"><span data-stu-id="e61da-222">The window shows both running and inactive apps.</span></span> <span data-ttu-id="e61da-223">Выберите приложение, которое хотите отладить.</span><span class="sxs-lookup"><span data-stu-id="e61da-223">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="e61da-224">Выберите тип отлаживаемого кода (управляемый, собственный, смешанный).</span><span class="sxs-lookup"><span data-stu-id="e61da-224">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="e61da-225">Щелкните **Attach** (Присоединить) или **Start** (Запустить).</span><span class="sxs-lookup"><span data-stu-id="e61da-225">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e61da-226">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="e61da-226">Next Development Checkpoint</span></span>

<span data-ttu-id="e61da-227">Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину.</span><span class="sxs-lookup"><span data-stu-id="e61da-227">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="e61da-228">Вы можете перейти к следующей статье:</span><span class="sxs-lookup"><span data-stu-id="e61da-228">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e61da-229">Развертывание на эмуляторе HoloLens</span><span class="sxs-lookup"><span data-stu-id="e61da-229">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="e61da-230">Или сразу перейдите к добавлению расширенных служб:</span><span class="sxs-lookup"><span data-stu-id="e61da-230">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e61da-231">Расширенные службы</span><span class="sxs-lookup"><span data-stu-id="e61da-231">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="e61da-232">Вы можете в любой момент вернуться к [этапам разработки для Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator).</span><span class="sxs-lookup"><span data-stu-id="e61da-232">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e61da-233">См. также статью</span><span class="sxs-lookup"><span data-stu-id="e61da-233">See also</span></span>
* [<span data-ttu-id="e61da-234">Установка средств</span><span class="sxs-lookup"><span data-stu-id="e61da-234">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="e61da-235">Использование эмулятора HoloLens</span><span class="sxs-lookup"><span data-stu-id="e61da-235">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="e61da-236">Развертывание и отладка приложений универсальной платформы Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="e61da-236">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="e61da-237">Включение устройства для разработки</span><span class="sxs-lookup"><span data-stu-id="e61da-237">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)
