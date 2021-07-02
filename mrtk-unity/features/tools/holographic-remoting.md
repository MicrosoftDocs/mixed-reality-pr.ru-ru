---
title: Голографическое удаленное взаимодействие
description: Документация по МРТК удаленного взаимодействия
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176639"
---
# <a name="holographic-remoting"></a><span data-ttu-id="5fb8c-104">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="5fb8c-104">Holographic remoting</span></span>

<span data-ttu-id="5fb8c-105">holographic удаленно взаимодействии создает потоки с компьютера на Microsoft HoloLens в режиме реального времени, используя подключение Wi-Fi или USB-кабель.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="5fb8c-106">Эта функция может значительно повысить производительность разработчиков при разработке приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="5fb8c-107">Пакет SDK XR, как упоминалось ниже, относится к [новому конвейеру XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="5fb8c-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="5fb8c-108">Дополнительные сведения об использовании пакета SDK для XR с МРТК см. [здесь](../../configuration/getting-started-with-mrtk-and-xrsdk.md) .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="5fb8c-109">Устаревший XR относится к существующему конвейеру XR, который входит в Unity 2018, не рекомендуется в Unity 2019,3 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="5fb8c-110">Начальная настройка</span><span class="sxs-lookup"><span data-stu-id="5fb8c-110">Initial setup</span></span>

<span data-ttu-id="5fb8c-111">чтобы обеспечить удаленное взаимодействие на HoloLens, важно убедиться, что проект использует новейшие компоненты удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="5fb8c-112">открыть **окно > диспетчер пакетов**</span><span class="sxs-lookup"><span data-stu-id="5fb8c-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="5fb8c-113">если используется устаревший XR: убедитесь, что установлена последняя версия пакета **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="5fb8c-114">при использовании XR SDK: убедитесь, что установлена последняя версия пакета **подключаемого модуля XR Windows** .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="5fb8c-115">убедитесь, что последнее приложение holographic remoting установлено на HoloLens с помощью Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="5fb8c-116">Перейдите к [старым инструкциям по установке XR](#legacy-xr-setup-instructions) или [инструкциям по установке пакета SDK XR](#xr-sdk-setup-instructions) в зависимости от используемого конвейера в проекте.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="5fb8c-117">Инструкции по установке устаревших XR</span><span class="sxs-lookup"><span data-stu-id="5fb8c-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="5fb8c-118">Приведенные ниже инструкции применимы только к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="5fb8c-119">если вы выполняете удаленное взаимодействие только с HoloLens (1 Gen), перейдите к [подключению к HoloLens с помощью Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="5fb8c-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="5fb8c-120">при использовании HoloLens 2 в мртк добавлена поддержка удаленного взаимодействия с управляемыми данными и отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="5fb8c-121">Чтобы включить эти функции, выполните действия, описанные в разделе [Импорт дотнетвинрт в проект](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="5fb8c-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="5fb8c-122">после импорта следующего шага необходимо выбрать   >  **набор средств**  >  **служебные программы** смешанной реальности  >  **Windows Mixed Reality**  >  **проверить конфигурацию**.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="5fb8c-123">На этом шаге добавляется определение скрипта, которое включает зависимость Дотнетвинрт.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb8c-124">При использовании Unity 2019,4 и более поздних версий необязательно запускать программу проверки конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="5fb8c-125">чтобы включить отслеживание соединений и отслеживания взгляда, выполните действия, описанные в разделе **отладка HoloLens 2 удаленное взаимодействие через пакет Unity: импорт** и связанные разделы.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="5fb8c-126">отладка HoloLens 2 удаленное взаимодействие через импорт пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="5fb8c-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="5fb8c-127">если HoloLens 2 соединений и отслеживание взгляда не работают с удаленным взаимодействием, существует несколько распространенных моментов, связанных с возможными проблемами.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="5fb8c-128">Они перечислены ниже в том порядке, в котором они должны быть проверены.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="5fb8c-129">Эти проблемы особенно важны при работе в **Unity 2019,3** или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="5fb8c-130">Импорт Дотнетвинрт в проект</span><span class="sxs-lookup"><span data-stu-id="5fb8c-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="5fb8c-131">Загрузка [средства "функция смешанной реальности](https://aka.ms/MRFeatureTool) "</span><span class="sxs-lookup"><span data-stu-id="5fb8c-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="5fb8c-132">В представлении " **функции обнаружения** " выберите *проекции "смешанная реальность" WinRT*</span><span class="sxs-lookup"><span data-stu-id="5fb8c-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Выбор пакета Дотнетвинрт](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="5fb8c-134">Щелкните **Get Features (получить компоненты** ) и продолжайте [Импорт пакета](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="5fb8c-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="5fb8c-135">DOTNETWINRT_PRESENT определения, записанные в параметры проигрывателя</span><span class="sxs-lookup"><span data-stu-id="5fb8c-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="5fb8c-136">при использовании Unity 2019,4 и более поздних версий определение DOTNETWINRT_PRESENT содержится в соответствующих асмдеф-файлах, а не в проигрывателе Unity Параметры.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="5fb8c-137">Шаг проверить конфигурацию не требуется.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="5fb8c-138">Начиная с версии МРТК 2.5.0, в целях повышения производительности этот #define больше не устанавливается автоматически.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="5fb8c-139">чтобы включить этот флаг, используйте   >  пункт меню "проверка конфигурации" набор средств **служебных программ** смешанной реальности  >  **Windows Mixed Reality**  >   .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="5fb8c-140">В элементе конфигурации проверки не отображается подтверждение.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="5fb8c-141">чтобы убедиться, что определение задано, перейдите к проигрывателю Unity Параметры.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="5fb8c-142">после этого на вкладке UWP установите флажок другие Параметры для параметра скрипт определения символов.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="5fb8c-143">Убедитесь, что DOTNETWINRT_PRESENT правильно написаны в этом списке.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="5fb8c-144">Если это так, этот шаг выполнен.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-144">If that's there, this step succeeded.</span></span>

![Дотнетвинрт](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="5fb8c-146">удаление поддержки удаленного взаимодействия HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5fb8c-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="5fb8c-147">Если вы используете конфликты или другие проблемы из-за наличия адаптера Дотнетвинрт, обратитесь [к одному из наших справочных материалов](../../index.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="5fb8c-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="5fb8c-148">Инструкции по установке пакета SDK для XR</span><span class="sxs-lookup"><span data-stu-id="5fb8c-148">XR SDK setup instructions</span></span>

<span data-ttu-id="5fb8c-149">следуйте [инструкциям по установке Windows Mixed Reality на странице приступая к работе с мртк и XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) и обязательно выполните шаг, необходимый для удаленного взаимодействия в редакторе HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="5fb8c-150">подключение к HoloLens с помощью Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="5fb8c-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="5fb8c-151">После настройки проекта можно установить подключение к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="5fb8c-152">в **Параметры сборки > файлов** убедитесь, что для типа сборки проекта задано значение **универсальная платформа Windows**</span><span class="sxs-lookup"><span data-stu-id="5fb8c-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="5fb8c-153">на HoloLens запустите приложение **holographic remoting** .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="5fb8c-154">в Unity выберите **Window > XR > holographic (если используется устаревшая XR)/Windows удаленное взаимодействие подключаемого модуля XR (при использовании пакета SDK для XR)**.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Запуск эмуляции holographic](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="5fb8c-156">Задайте для **режима эмуляции** значение **удаленно на устройство**.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Задать режим эмуляции](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="5fb8c-158">(**_Применимо только к устаревшим XR_**) Выберите **версию устройства**.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Выбор версии устройства](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="5fb8c-160">Используя IP-адрес, отображаемый приложением удаленного взаимодействия holographic, установите поле **Удаленный компьютер** .</span><span class="sxs-lookup"><span data-stu-id="5fb8c-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Введите IP-адрес](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="5fb8c-162">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb8c-163">если вы не можете подключиться, убедитесь, что HoloLens 2 не подключены к компьютеру и перезапустите Unity.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="5fb8c-164">подключение к HoloLens с помощью USB-кабеля</span><span class="sxs-lookup"><span data-stu-id="5fb8c-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="5fb8c-165">Подключение через USB-кабель обеспечивает лучшее качество и стабильность при визуализации.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="5fb8c-166">чтобы использовать USB-кабель, отключитесь от HoloLens Wi-Fi в HoloLens Параметры и запустите приложение удаленного проигрывателя holographic.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="5fb8c-167">Он отобразит IP-адрес, который начинается с 169.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="5fb8c-168">Используйте этот IP-адрес в параметре эмуляции holographic в Unity для подключения.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="5fb8c-169">после определения IP-адреса для кабеля USB можно легко подключить HoloLens для Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="5fb8c-170">Запуск сеанса удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="5fb8c-170">Starting a remoting session</span></span>

<span data-ttu-id="5fb8c-171">в Unity, подключенном к HoloLens, в редакторе введите режим воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="5fb8c-172">После завершения сеанса выйдите из режима воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb8c-173">Существует известная ситуация с некоторыми версиями Unity, в которых редактор может зависнуть при входе в режим воспроизведения во время сеанса удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="5fb8c-174">Эта проблема может проявляться, если при загрузке проекта открыто окно с Holographic.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="5fb8c-175">Чтобы убедиться, что эта проблема не возникает, всегда закрывайте диалоговое окно holographic перед выходом из Unity.</span><span class="sxs-lookup"><span data-stu-id="5fb8c-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb8c-176">См. также:</span><span class="sxs-lookup"><span data-stu-id="5fb8c-176">See also</span></span>

- [<span data-ttu-id="5fb8c-177">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="5fb8c-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="5fb8c-178">Условия лицензионного соглашения на использование программного обеспечения для удаленного взаимодействия Microsoft holographic</span><span class="sxs-lookup"><span data-stu-id="5fb8c-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
