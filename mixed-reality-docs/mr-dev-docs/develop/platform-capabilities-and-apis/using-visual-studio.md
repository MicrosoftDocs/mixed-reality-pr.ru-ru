---
title: Развертывание и отладка с помощью Visual Studio
description: Узнайте, как создавать, отлаживать и развертывать приложения для HoloLens и Windows Mixed Reality с помощью Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, смешанная реальность, отладка, развертывание
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "100496100"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="a0c89-104">Развертывание и отладка с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a0c89-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="a0c89-105">Независимо от того, что вы используете для разработки приложения смешанной реальности — DirectX или Unity, для отладки и развертывания лучшим средством будет Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0c89-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="a0c89-106">В этом разделе вы научитесь:</span><span class="sxs-lookup"><span data-stu-id="a0c89-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="a0c89-107">развертывать приложения на иммерсивной гарнитуре HoloLens или Windows Mixed Reality с помощью Visual Studio;</span><span class="sxs-lookup"><span data-stu-id="a0c89-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="a0c89-108">использовать эмулятор HoloLens, встроенный в Visual Studio;</span><span class="sxs-lookup"><span data-stu-id="a0c89-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="a0c89-109">отлаживать приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a0c89-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0c89-110">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="a0c89-110">Prerequisites</span></span>

1. <span data-ttu-id="a0c89-111">Инструкции по установке см. в разделе [Установка инструментов](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="a0c89-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="a0c89-112">Создайте проект универсального приложения для Windows в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0c89-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="a0c89-113">Для HoloLens (1-го поколения) используйте Visual Studio 2017 или более позднюю версию.</span><span class="sxs-lookup"><span data-stu-id="a0c89-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="a0c89-114">Для HoloLens 2 используйте Visual Studio 2019 16.2 или более позднюю версию.</span><span class="sxs-lookup"><span data-stu-id="a0c89-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="a0c89-115">Поддерживаются языки C# и C++.</span><span class="sxs-lookup"><span data-stu-id="a0c89-115">C# and C++ are supported.</span></span> <span data-ttu-id="a0c89-116">(Вы можете также следовать инструкции по [созданию приложения в Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="a0c89-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="a0c89-117">Включение режима разработчика</span><span class="sxs-lookup"><span data-stu-id="a0c89-117">Enabling Developer Mode</span></span>

<span data-ttu-id="a0c89-118">Для начала включите **режим разработчика** на устройстве, чтобы среда Visual Studio могла к нему подключиться.</span><span class="sxs-lookup"><span data-stu-id="a0c89-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="a0c89-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0c89-119">HoloLens</span></span>

1. <span data-ttu-id="a0c89-120">Включите устройство HoloLens и наденьте его.</span><span class="sxs-lookup"><span data-stu-id="a0c89-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="a0c89-121">Выполните [жест "Пуск"](../../design/system-gesture.md), чтобы запустить главное меню.</span><span class="sxs-lookup"><span data-stu-id="a0c89-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="a0c89-122">Щелкните плитку **Параметры**, чтобы запустить приложение в среде.</span><span class="sxs-lookup"><span data-stu-id="a0c89-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="a0c89-123">Выберите пункт меню **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="a0c89-124">Выберите пункт меню **Для разработчиков**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="a0c89-125">Включите **Режим разработчика**, чтобы развертывать приложения из Visual Studio в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0c89-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="a0c89-126">Дополнительно Прокрутите вниз и включите **Портал устройств**, чтобы подключаться к [порталу устройств Windows](using-the-windows-device-portal.md) на HoloLens с помощью веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="a0c89-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="a0c89-127">Компьютер с Windows</span><span class="sxs-lookup"><span data-stu-id="a0c89-127">Windows PC</span></span>

<span data-ttu-id="a0c89-128">При работе с гарнитурой Windows Mixed Reality, подключенной к компьютеру, на этом компьютере необходимо включить **Режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="a0c89-129">Перейдите в раздел **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-129">Go to **Settings**</span></span>
2. <span data-ttu-id="a0c89-130">Выберите **Обновление и безопасность**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="a0c89-131">Выберите **Для разработчиков**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-131">Select **For developers**</span></span>
4. <span data-ttu-id="a0c89-132">Включите **Режим разработчика**, прочитайте заявление об отказе от ответственности для выбранного параметра, затем щелкните "Да", чтобы принять изменения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="a0c89-133">Развертывание приложения HoloLens по Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="a0c89-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="a0c89-134">Настройте проект Visual Studio со следующими свойствами:</span><span class="sxs-lookup"><span data-stu-id="a0c89-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="a0c89-135">Выберите варианты компиляции приложений.</span><span class="sxs-lookup"><span data-stu-id="a0c89-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="a0c89-136">Для проектов Unity выберите **Выпуск** или **Мастер**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="a0c89-137">Для всех остальных проектов выберите **Выпуск**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="a0c89-138">Полные определения для каждого варианта компиляции можно найти в разделе [Создание и развертывание решений Unity в Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="a0c89-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="a0c89-139">Выберите конфигурацию сборки в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="a0c89-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="a0c89-140">Выберите **Удаленный компьютер** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="a0c89-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Удаленный компьютер как цель развертывания в Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="a0c89-142">Затем необходимо установить удаленное подключение.</span><span class="sxs-lookup"><span data-stu-id="a0c89-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="a0c89-143">Для проектов C++ и JavaScript выберите **Проект > Свойства > Свойства конфигурации > Отладка**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="a0c89-144">Если вы работаете с проектом C#, автоматически откроется диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="a0c89-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="a0c89-145">Если диалоговое окно удаленного подключения не отображается в проекте C#, его можно открыть вручную в меню **Properties > Debug** (Свойства > Отладка).</span><span class="sxs-lookup"><span data-stu-id="a0c89-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="a0c89-146">Введите IP-адрес своего устройства в поле **Адрес** или **Имя компьютера**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="a0c89-147">IP-адрес HoloLens можно найти в меню **Параметры > Сеть и Интернет > Дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="a0c89-148">Всегда рекомендуется вводить IP-адрес вручную и не пользоваться функцией автоматического обнаружения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="a0c89-149">Задайте для параметра **Режим аутентификации** значение **Универсальный (незашифрованный протокол)** .</span><span class="sxs-lookup"><span data-stu-id="a0c89-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Диалоговое окно удаленного подключения в Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="a0c89-151">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="a0c89-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="a0c89-152">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="a0c89-153">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="a0c89-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="a0c89-155">При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="a0c89-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="a0c89-156">Выполните приведенные ниже инструкции по **связыванию устройства**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="a0c89-157">Развертывание приложения HoloLens по USB</span><span class="sxs-lookup"><span data-stu-id="a0c89-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="a0c89-158">Выберите варианты компиляции приложений.</span><span class="sxs-lookup"><span data-stu-id="a0c89-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="a0c89-159">Для проектов Unity выберите **Выпуск** или **Мастер**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="a0c89-160">Для всех остальных проектов выберите **Выпуск**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="a0c89-161">Полные определения для каждого варианта компиляции можно найти в разделе [Создание и развертывание решений Unity в Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="a0c89-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="a0c89-162">Выберите конфигурацию сборки в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="a0c89-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="a0c89-163">Выберите **Устройство** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="a0c89-163">Select **Device** in the deployment target drop-down menu</span></span>

![Развертывание устройства в Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="a0c89-165">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="a0c89-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="a0c89-166">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="a0c89-167">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="a0c89-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="a0c89-169">При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="a0c89-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="a0c89-170">Выполните приведенные ниже инструкции по **связыванию устройства**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="a0c89-171">Если при развертывании приложения по USB возникает значительная задержка, мы рекомендуем воспользоваться [инструкциями для удаленного компьютера](#deploying-a-hololens-app-over-wi-fi) из предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="a0c89-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="a0c89-172">Развертывание приложения в эмуляторе HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0c89-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="a0c89-173">Убедитесь, что вы **[установили эмулятор HoloLens 2 или HoloLens (1-го поколения)](../install-the-tools.md#installation-checklist)** .</span><span class="sxs-lookup"><span data-stu-id="a0c89-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="a0c89-174">Выберите конфигурацию сборки и эмулятор в зависимости от устройства.</span><span class="sxs-lookup"><span data-stu-id="a0c89-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="a0c89-175">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="a0c89-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="a0c89-176">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="a0c89-177">Выберите **Build > Deploy** (Сборка > Развернуть), чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="a0c89-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="a0c89-179">Развертывание приложения виртуальной реальности на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="a0c89-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="a0c89-180">Чтобы использовать иммерсивную гарнитуру Windows Mixed Reality, которая подключается к компьютеру, или [эмулятор смешанной реальности](using-the-windows-mixed-reality-simulator.md), выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="a0c89-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="a0c89-181">Выберите для приложения конфигурацию сборки **x86** или **x64**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="a0c89-182">Выберите **Локальный компьютер** в раскрывающемся меню цели развертывания.</span><span class="sxs-lookup"><span data-stu-id="a0c89-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="a0c89-183">Выполните сборку, развертывание и отладку приложения в соответствии со своими потребностями.</span><span class="sxs-lookup"><span data-stu-id="a0c89-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="a0c89-184">Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="a0c89-185">Выберите **Сборка > Развернуть**, чтобы выполнить сборку и развертывание без отладки.</span><span class="sxs-lookup"><span data-stu-id="a0c89-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="a0c89-186">Связывание устройства</span><span class="sxs-lookup"><span data-stu-id="a0c89-186">Pairing your device</span></span>

<span data-ttu-id="a0c89-187">При первом развертывании приложения из Visual Studio на HoloLens будет предложено ввести ПИН-код.</span><span class="sxs-lookup"><span data-stu-id="a0c89-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="a0c89-188">Создайте ПИН-код на HoloLens, запустив приложение Settings, выберите **Update > For Developers** (Обновление > Для разработчиков) и коснитесь действия **Pair** (Связать).</span><span class="sxs-lookup"><span data-stu-id="a0c89-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="a0c89-189">Когда ПИН-код появится в HoloLens, введите его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0c89-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="a0c89-190">После завершения связывания коснитесь **Done** (Готово) на HoloLens, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="a0c89-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="a0c89-191">Теперь этот компьютер связан с HoloLens, и приложения можно развертывать автоматически.</span><span class="sxs-lookup"><span data-stu-id="a0c89-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="a0c89-192">Повторите эти действия для всех остальных компьютеров, которые используются для развертывания приложений в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0c89-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="a0c89-193">Чтобы отменить связь HoloLens со всеми связанными компьютерами, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="a0c89-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="a0c89-194">Откройте приложение **Settings**, перейдите к разделу **Update > For Developers** (Обновление > Для разработчиков) и коснитесь элемента **Clear** (Очистить).</span><span class="sxs-lookup"><span data-stu-id="a0c89-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="a0c89-195">Отладчик графики для HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="a0c89-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="a0c89-196">Инструменты диагностики графики в Visual Studio очень полезны для создания и оптимизации голографического приложения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="a0c89-197">Подробные сведения см. в разделе [Диагностика графики в Visual Studio](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) на сайте MSDN.</span><span class="sxs-lookup"><span data-stu-id="a0c89-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="a0c89-198">**Запуск отладчика графики**</span><span class="sxs-lookup"><span data-stu-id="a0c89-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="a0c89-199">Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.</span><span class="sxs-lookup"><span data-stu-id="a0c89-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="a0c89-200">Выберите **Отладка > Графика > Начать диагностику**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="a0c89-201">При первом запуске диагностики для HoloLens может появиться сообщение об ошибке "Отказано в доступе".</span><span class="sxs-lookup"><span data-stu-id="a0c89-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="a0c89-202">Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="a0c89-203">Профилирование</span><span class="sxs-lookup"><span data-stu-id="a0c89-203">Profiling</span></span>

<span data-ttu-id="a0c89-204">Инструменты профилирования Visual Studio позволяют анализировать производительность и использование ресурсов приложения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="a0c89-205">Сюда входят инструменты для оптимизации использования ЦП, памяти, графического процессора и сети.</span><span class="sxs-lookup"><span data-stu-id="a0c89-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="a0c89-206">Подробные сведения см. в разделе [Запуск средств диагностики без отладки](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) на сайте MSDN.</span><span class="sxs-lookup"><span data-stu-id="a0c89-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="a0c89-207">**Запуск инструментов профилирования для HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a0c89-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="a0c89-208">Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.</span><span class="sxs-lookup"><span data-stu-id="a0c89-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="a0c89-209">Выберите **Отладка > Запустить средства диагностики без отладки**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="a0c89-210">Выберите инструменты, которые вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="a0c89-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="a0c89-211">Выберите команду **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-211">Select **Start**</span></span>
5. <span data-ttu-id="a0c89-212">При первом запуске диагностики без отладки для HoloLens может появиться сообщение об ошибке "Отказано в доступе".</span><span class="sxs-lookup"><span data-stu-id="a0c89-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="a0c89-213">Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="a0c89-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="a0c89-214">Отладка установленного или работающего приложения</span><span class="sxs-lookup"><span data-stu-id="a0c89-214">Debugging an installed or running app</span></span>

<span data-ttu-id="a0c89-215">Visual Studio можно использовать для отладки установленного универсального приложения для Windows, не развертывая его из проекта Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0c89-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="a0c89-216">Это удобно в тех случаях, когда нужно выполнить отладку установленного пакета приложения или уже запущенного приложения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="a0c89-217">Выберите **Отладка > Другие целевые объекты отладки > Отладка установленного пакета приложения**.</span><span class="sxs-lookup"><span data-stu-id="a0c89-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="a0c89-218">Выберите цель **Удаленный компьютер**, если используется HoloLens, или **Локальный компьютер**, если используются иммерсивные гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="a0c89-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="a0c89-219">Введите **IP-адрес** устройства.</span><span class="sxs-lookup"><span data-stu-id="a0c89-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="a0c89-220">Выберите режим аутентификации **Universal** (Универсальная).</span><span class="sxs-lookup"><span data-stu-id="a0c89-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="a0c89-221">В окне отображаются как работающие, так и неактивные приложения.</span><span class="sxs-lookup"><span data-stu-id="a0c89-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="a0c89-222">Выберите приложение, которое хотите отладить.</span><span class="sxs-lookup"><span data-stu-id="a0c89-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="a0c89-223">Выберите тип отлаживаемого кода (управляемый, собственный, смешанный).</span><span class="sxs-lookup"><span data-stu-id="a0c89-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="a0c89-224">Щелкните **Attach** (Присоединить) или **Start** (Запустить).</span><span class="sxs-lookup"><span data-stu-id="a0c89-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a0c89-225">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="a0c89-225">Next Development Checkpoint</span></span>

<span data-ttu-id="a0c89-226">Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину.</span><span class="sxs-lookup"><span data-stu-id="a0c89-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="a0c89-227">Вы можете перейти к следующей статье:</span><span class="sxs-lookup"><span data-stu-id="a0c89-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0c89-228">Развертывание на эмуляторе HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0c89-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="a0c89-229">Или сразу перейдите к добавлению расширенных служб:</span><span class="sxs-lookup"><span data-stu-id="a0c89-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0c89-230">Расширенные службы</span><span class="sxs-lookup"><span data-stu-id="a0c89-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="a0c89-231">Вы можете в любой момент вернуться к [этапам разработки для Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator).</span><span class="sxs-lookup"><span data-stu-id="a0c89-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0c89-232">См. также статью</span><span class="sxs-lookup"><span data-stu-id="a0c89-232">See also</span></span>
* [<span data-ttu-id="a0c89-233">Установка средств</span><span class="sxs-lookup"><span data-stu-id="a0c89-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="a0c89-234">Использование эмулятора HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0c89-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="a0c89-235">Развертывание и отладка приложений универсальной платформы Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="a0c89-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="a0c89-236">Включение устройства для разработки</span><span class="sxs-lookup"><span data-stu-id="a0c89-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)