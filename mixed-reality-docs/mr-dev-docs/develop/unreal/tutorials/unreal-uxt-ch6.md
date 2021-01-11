---
title: 6. Упаковка и развертывание на устройстве или в эмуляторе
description: Часть 6 (из 6) серии руководств по созданию приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, UX Tools, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 83d8068ca8ce73f23edb85cf9044db5409105380
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865399"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="e8221-104">6. Упаковка и развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="e8221-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="e8221-105">В предыдущем разделе мы добавили простую кнопку, которая возвращает шахматную фигуру в исходное положение.</span><span class="sxs-lookup"><span data-stu-id="e8221-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="e8221-106">Этот раздел — последний в серии. Здесь мы подготовим приложение к выполнению на устройстве HoloLens 2 или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="e8221-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="e8221-107">Если у вас есть HoloLens 2, вы можете вести потоковую передачу с компьютера или упаковать приложение для выполнения непосредственно на устройстве.</span><span class="sxs-lookup"><span data-stu-id="e8221-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="e8221-108">Если же вы не располагаете устройством, то нужно будет упаковать приложение для выполнения в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="e8221-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="e8221-109">К концу раздела у вас будет развернутое и готовое к выполнению приложение смешанной реальности с соответствующими взаимодействиями и пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="e8221-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="e8221-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="e8221-110">Objectives</span></span>

* <span data-ttu-id="e8221-111">[Только для устройства] Потоковая передача на HoloLens 2 в режиме голографического удаленного взаимодействия с приложением.</span><span class="sxs-lookup"><span data-stu-id="e8221-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="e8221-112">Упаковка и развертывание приложения на устройстве или в эмуляторе HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e8221-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="e8221-113">[Только для устройства] Потоковая передача</span><span class="sxs-lookup"><span data-stu-id="e8221-113">[Device Only] Streaming</span></span>

<span data-ttu-id="e8221-114">[Голографическое удаленное взаимодействие](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) — это потоковая передача данных с компьютера или автономного устройства UWP на устройство HoloLens 2, а не переключение канала.</span><span class="sxs-lookup"><span data-stu-id="e8221-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="e8221-115">Ведущее приложение в удаленном взаимодействии принимает входной поток данных от устройства HoloLens, отрисовывает содержимое в виртуальном иммерсивном режиме и передает кадры этого содержимого в потоковом режиме обратно на HoloLens по Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="e8221-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="e8221-116">Потоковая передача позволяет реализовывать иммерсивные режимы удаленного взаимодействия в существующем программном обеспечении для настольных компьютеров и обеспечивает доступ к большему объему системных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e8221-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="e8221-117">Если вы выбрали этот вариант для своего шахматного приложения, нужны будут следующие приготовления:</span><span class="sxs-lookup"><span data-stu-id="e8221-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="e8221-118">Установите и запустите **проигрыватель голографического удаленного взаимодействия** из Microsoft Store на устройстве HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e8221-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="e8221-119">Запишите IP-адрес, отображаемый в приложении.</span><span class="sxs-lookup"><span data-stu-id="e8221-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="e8221-120">Выберите **Edit > Project Settings** (Правка > Параметры проекта) и убедитесь, что для параметра Windows **Default RHI** (RHI по умолчанию) задано значение **Default** (По умолчанию) или **D3D11**:</span><span class="sxs-lookup"><span data-stu-id="e8221-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![RHI по умолчанию](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="e8221-122">В редакторе Unreal выберите **Edit > Project Settings** (Правка > Параметры проекта) и в разделе **Holographic Remoting** (Голографическое удаленное взаимодействие) установите флажок **Enable Remoting** (Включить удаленное взаимодействие).</span><span class="sxs-lookup"><span data-stu-id="e8221-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="e8221-123">Перезапустите редактор, а затем введите IP-адрес устройства (как показано в приложении Holographic Remoting Player), а затем нажмите кнопку **Connect** (Подключить).</span><span class="sxs-lookup"><span data-stu-id="e8221-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="e8221-124">Когда устройство подключится, щелкните стрелку раскрывающегося списка справа от кнопки **Play** (Воспроизведение) и выберите вариант **VR Preview** (Просмотр виртуальной реальности).</span><span class="sxs-lookup"><span data-stu-id="e8221-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="e8221-125">Приложение запустится в окне просмотра виртуальной реальности с потоковой передачей на гарнитуру HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e8221-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="e8221-126">Упаковка и развертывание приложения на портале устройств</span><span class="sxs-lookup"><span data-stu-id="e8221-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="e8221-127">Если вы впервые упаковываете приложение Unreal для HoloLens, потребуется скачать вспомогательные файлы из Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="e8221-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="e8221-128">Выберите **Editor Preferences > General > Source Code > Source Code Editor** (Параметры редактора > Общие > Исходный код > Редактор исходного кода) и убедитесь, что решение Visual Studio 2019 выбрано.</span><span class="sxs-lookup"><span data-stu-id="e8221-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="e8221-129">Перейдите на вкладку **Library** (Библиотека) в Epic Games Launcher. Щелкните стрелку раскрывающегося списка рядом с полем **Launch** (Запуск) и выберите вариант **Options** (Параметры).</span><span class="sxs-lookup"><span data-stu-id="e8221-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="e8221-130">В разделе **Target Platforms** (Целевые платформы) выберите элемент **HoloLens 2** и щелкните команду **Apply** (Применить).</span><span class="sxs-lookup"><span data-stu-id="e8221-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="e8221-131">![Изменение целевой платформы в параметрах проекта](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="e8221-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="e8221-132">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="e8221-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="e8221-133">В разделе **Project > Description > About > Project Name** (Проект > Описание > Сведения > Имя проекта) введите имя проекта.</span><span class="sxs-lookup"><span data-stu-id="e8221-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="e8221-134">Добавьте **CN=название_вашей_компании** в разделе **Project > Description > Publisher > Company Distinguished Name** (Проект > Описание > Издатель > Название организации).</span><span class="sxs-lookup"><span data-stu-id="e8221-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="e8221-135">Выберите **Start in VR** (Запустить в виртуальной реальности) на вкладке **Project > Description > Settings** (Проект > Описание > Настройки).</span><span class="sxs-lookup"><span data-stu-id="e8221-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8221-136">Если оставить любое из этих полей пустым, при попытке создать новый сертификат на шаге 3 будет выдаваться ошибка.</span><span class="sxs-lookup"><span data-stu-id="e8221-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8221-137">Имя издателя должно быть указано в формате [LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="e8221-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="e8221-138">Неправильно сформированное имя издателя приведет к возникновению ошибки "Signing key not found.</span><span class="sxs-lookup"><span data-stu-id="e8221-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="e8221-139">The app could not be digitally signed" (Ключ подписывания не найден. Не удалось подписать приложение)</span><span class="sxs-lookup"><span data-stu-id="e8221-139">The app could not be digitally signed."</span></span> <span data-ttu-id="e8221-140">при упаковке.</span><span class="sxs-lookup"><span data-stu-id="e8221-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8221-141">Если параметр Start in VR (Запустить в виртуальной реальности) не выбран, ваше приложение попытается запуститься на экране.</span><span class="sxs-lookup"><span data-stu-id="e8221-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Параметры проекта — Описание](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="e8221-143">В разделе **Platforms > HoloLens** (Платформы > HoloLens) установите флажок **Build for HoloLens Emulation** (Сборка для эмуляции HoloLens) и/или **Build for HoloLens Device** (Сборка для устройства HoloLens).</span><span class="sxs-lookup"><span data-stu-id="e8221-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="e8221-144">В разделе **Packaging** (Упаковка) рядом с полем **Signing Certificate** (Сертификат для подписания) нажмите кнопку **Generate new** (Создать).</span><span class="sxs-lookup"><span data-stu-id="e8221-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8221-145">Если вы используете уже созданный сертификат, имя издателя сертификата должно совпадать с именем издателя приложения.</span><span class="sxs-lookup"><span data-stu-id="e8221-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="e8221-146">В противном случае возникнет ошибка "Signing key not found.</span><span class="sxs-lookup"><span data-stu-id="e8221-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="e8221-147">The app could not be digitally signed" (Ключ подписывания не найден. Не удалось подписать приложение)</span><span class="sxs-lookup"><span data-stu-id="e8221-147">The app could not be digitally signed."</span></span> <span data-ttu-id="e8221-148">ошибка".</span><span class="sxs-lookup"><span data-stu-id="e8221-148">error.</span></span>

![Параметры проекта — Платформы — HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="e8221-150">При появлении запроса на создание пароля закрытого ключа щелкните **Нет**, чтобы протестировать эту функцию.</span><span class="sxs-lookup"><span data-stu-id="e8221-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Создание сертификата](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="e8221-152">Откройте раздел **File > Package Project** (Файл > Упаковка проекта) и выберите **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e8221-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="e8221-153">Создайте новую папку для сохранения пакета и щелкните **Select Folder** (Выбрать папку).</span><span class="sxs-lookup"><span data-stu-id="e8221-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="e8221-154">Когда завершится создание пакета приложения, откройте [портал устройств Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), перейдите к разделу **Представления > Приложения** и найдите подраздел **Развертывание приложений**.</span><span class="sxs-lookup"><span data-stu-id="e8221-154">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="e8221-155">Нажмите кнопку **Обзор...** , найдите файл **ChessApp.appxbundle** и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="e8221-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="e8221-156">Если приложение впервые устанавливается на этом устройстве, установите флажок **Allow me to select framework packages** (Разрешить выбор пакетов платформы).</span><span class="sxs-lookup"><span data-stu-id="e8221-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="e8221-157">В следующем диалоговом окне включите соответствующие файлы **VCLibs** и **appx**, (**arm64** для устройства и **x64** для эмулятора).</span><span class="sxs-lookup"><span data-stu-id="e8221-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="e8221-158">Их можно найти во вложенной папке **HoloLens** в папке, где вы сохранили пакет.</span><span class="sxs-lookup"><span data-stu-id="e8221-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="e8221-159">Щелкните **Установить**.</span><span class="sxs-lookup"><span data-stu-id="e8221-159">Click **Install**</span></span>
    * <span data-ttu-id="e8221-160">Теперь вы можете перейти в раздел **All Apps** (Все приложения) и коснуться только что установленного приложения для запуска или запустить это приложение непосредственно на **портале устройств Windows**.</span><span class="sxs-lookup"><span data-stu-id="e8221-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="e8221-161">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e8221-161">Congratulations!</span></span> <span data-ttu-id="e8221-162">Ваше приложение смешанной реальности для HoloLens готово к работе.</span><span class="sxs-lookup"><span data-stu-id="e8221-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="e8221-163">Но мы исследовали не все.</span><span class="sxs-lookup"><span data-stu-id="e8221-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="e8221-164">В MRTK есть множество автономных функций, которые вы можете добавлять в свои проекты, в том числе пространственное сопоставление, взгляд, голосовой ввод и даже QR-коды.</span><span class="sxs-lookup"><span data-stu-id="e8221-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="e8221-165">Подробнее об этих функциях можно прочесть в "[Обзоре разработки в Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)".</span><span class="sxs-lookup"><span data-stu-id="e8221-165">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e8221-166">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="e8221-166">Next Development Checkpoint</span></span>

<span data-ttu-id="e8221-167">Если вы следуете изложенным нами инструкциям по разработке для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="e8221-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="e8221-168">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="e8221-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8221-169">Ввод взглядом</span><span class="sxs-lookup"><span data-stu-id="e8221-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="e8221-170">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="e8221-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8221-171">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="e8221-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="e8221-172">Вы можете в любой момент вернуться к [этапам разработки для Unreal](../unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="e8221-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
