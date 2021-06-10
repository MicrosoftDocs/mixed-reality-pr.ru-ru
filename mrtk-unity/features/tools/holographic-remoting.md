---
title: Голографическое удаленное взаимодействие
description: Документация по МРТК удаленного взаимодействия
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 196bbb7027389ea75ddc577e4efc397ca779d550
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647184"
---
# <a name="holographic-remoting"></a><span data-ttu-id="4b8c1-104">Голографическое удаленное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="4b8c1-104">Holographic Remoting</span></span>

<span data-ttu-id="4b8c1-105">Holographic удаленное взаимодействие создает потоки с компьютера в Microsoft HoloLens в режиме реального времени с помощью Wi-Fi или USB-подключения.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="4b8c1-106">Эта функция может значительно повысить производительность разработчиков при разработке приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="4b8c1-107">Пакет SDK XR, как упоминалось ниже, относится к [новому конвейеру XR Unity в unity 2019,3 и более поздних версиях](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="4b8c1-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="4b8c1-108">Дополнительные сведения об использовании пакета SDK для XR с МРТК см. [здесь](../../configuration/getting-started-with-mrtk-and-xrsdk.md) .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="4b8c1-109">Устаревший XR относится к существующему конвейеру XR, который входит в Unity 2018, не рекомендуется в Unity 2019,3 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="4b8c1-110">Начальная настройка</span><span class="sxs-lookup"><span data-stu-id="4b8c1-110">Initial setup</span></span>

<span data-ttu-id="4b8c1-111">Чтобы обеспечить удаленное взаимодействие для HoloLens, важно убедиться, что проект использует новейшие компоненты удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="4b8c1-112">Открыть **Диспетчер пакетов > окон**</span><span class="sxs-lookup"><span data-stu-id="4b8c1-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="4b8c1-113">Если используется устаревший XR: Убедитесь, что установлена последняя версия пакета **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="4b8c1-114">При использовании XR SDK: Убедитесь, что установлена последняя версия пакета **подключаемого модуля XR для Windows** .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="4b8c1-115">Убедитесь, что последнее приложение holographic Remoting установлено на HoloLens через Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="4b8c1-116">Перейдите к [старым инструкциям по установке XR](#legacy-xr-setup-instructions) или [инструкциям по установке пакета SDK XR](#xr-sdk-setup-instructions) в зависимости от используемого конвейера в проекте.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="4b8c1-117">Инструкции по установке устаревших XR</span><span class="sxs-lookup"><span data-stu-id="4b8c1-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="4b8c1-118">Приведенные ниже инструкции применимы только к удаленному взаимодействию с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="4b8c1-119">Если вы выполняете удаленное взаимодействие только с HoloLens (1-й общий), перейдите к [подключению к hololens с помощью Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="4b8c1-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="4b8c1-120">При использовании HoloLens 2 в МРТК добавлена поддержка удаленного взаимодействия с управляемыми данными и отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="4b8c1-121">Чтобы включить эти функции, выполните действия, описанные в разделе [Импорт дотнетвинрт в проект](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="4b8c1-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="4b8c1-122">После импорта следующего шага необходимо выбрать средства набора средств для **смешанной реальности**  >    >    >  Проверка конфигурации **Windows Mixed Reality**  >  .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="4b8c1-123">На этом шаге добавляется определение скрипта, которое включает зависимость Дотнетвинрт.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8c1-124">При использовании Unity 2019,4 и более поздних версий необязательно запускать программу проверки конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="4b8c1-125">Чтобы включить отслеживание соединений и отслеживания взгляда, выполните действия, описанные в разделах **Отладка удаленного взаимодействия HoloLens 2 через импорт пакетов Unity** и связанные разделы.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="4b8c1-126">Отладка удаленного взаимодействия HoloLens 2 через импорт пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="4b8c1-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="4b8c1-127">Если соединения HoloLens 2 и отслеживание взгляда не работают по удаленному взаимодействию, существует несколько распространенных моментов, связанных с возможными проблемами.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="4b8c1-128">Они перечислены ниже в том порядке, в котором они должны быть проверены.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="4b8c1-129">Эти проблемы особенно важны при работе в **Unity 2019,3** или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="4b8c1-130">Импорт Дотнетвинрт в проект</span><span class="sxs-lookup"><span data-stu-id="4b8c1-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="4b8c1-131">Загрузка [средства "функция смешанной реальности](https://aka.ms/MRFeatureTool) "</span><span class="sxs-lookup"><span data-stu-id="4b8c1-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="4b8c1-132">В представлении " **функции обнаружения** " выберите *проекции "смешанная реальность" WinRT*</span><span class="sxs-lookup"><span data-stu-id="4b8c1-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Выбор пакета Дотнетвинрт](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="4b8c1-134">Щелкните **Get Features (получить компоненты** ) и продолжайте [Импорт пакета](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="4b8c1-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="4b8c1-135">DOTNETWINRT_PRESENT определения, записанные в параметры проигрывателя</span><span class="sxs-lookup"><span data-stu-id="4b8c1-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="4b8c1-136">При использовании Unity 2019,4 и более поздних версий определение DOTNETWINRT_PRESENT содержится в соответствующих асмдеф-файлах, а не в параметрах проигрывателя Unity.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="4b8c1-137">Шаг проверить конфигурацию не требуется.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="4b8c1-138">Начиная с версии МРТК 2.5.0, в целях повышения производительности этот #define больше не устанавливается автоматически.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="4b8c1-139">Чтобы включить этот флаг, используйте пункт меню "Конфигурация" для служебных программ " **Смешанная реальность**" для  >    >  **Windows Mixed Reality**  >   .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="4b8c1-140">В элементе конфигурации проверки не отображается подтверждение.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="4b8c1-141">Чтобы убедиться, что определение задано, перейдите к параметрам проигрывателя Unity.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="4b8c1-142">После этого на вкладке UWP установите флажок другие параметры для параметра скрипт определения символов.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="4b8c1-143">Убедитесь, что DOTNETWINRT_PRESENT правильно написаны в этом списке.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="4b8c1-144">Если это так, этот шаг выполнен.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-144">If that's there, this step succeeded.</span></span>

![Дотнетвинрт](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="4b8c1-146">Удаление удаленной поддержки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4b8c1-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="4b8c1-147">Если вы используете конфликты или другие проблемы из-за наличия адаптера Дотнетвинрт, обратитесь [к одному из наших справочных материалов](../../index.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="4b8c1-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="4b8c1-148">Инструкции по установке пакета SDK для XR</span><span class="sxs-lookup"><span data-stu-id="4b8c1-148">XR SDK setup instructions</span></span>

<span data-ttu-id="4b8c1-149">Следуйте [инструкциям по установке Windows Mixed Reality на странице Приступая к работе с мртк и XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) и убедитесь, что выполнен шаг, необходимый для удаленного взаимодействия на основе HoloLens в редакторе.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="4b8c1-150">Подключение к HoloLens с помощью Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="4b8c1-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="4b8c1-151">После настройки проекта можно установить подключение к HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="4b8c1-152">В **файле > параметры сборки** убедитесь, что для типа сборки проекта задано значение **универсальная платформа Windows**</span><span class="sxs-lookup"><span data-stu-id="4b8c1-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="4b8c1-153">На HoloLens запустите приложение **holographic Remoting** .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="4b8c1-154">В Unity выберите **Window > XR > holographic (если используется устаревшая XR) или удаленное взаимодействие подключаемого модуля Windows XR (при использовании пакета SDK для XR)**.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Запуск эмуляции holographic](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="4b8c1-156">Задайте для **режима эмуляции** значение **удаленно на устройство**.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Задать режим эмуляции](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="4b8c1-158">(**_Применимо только к устаревшим XR_**) Выберите **версию устройства**.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Выбор версии устройства](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="4b8c1-160">Используя IP-адрес, отображаемый приложением удаленного взаимодействия holographic, установите поле **Удаленный компьютер** .</span><span class="sxs-lookup"><span data-stu-id="4b8c1-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Введите IP-адрес](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="4b8c1-162">Нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8c1-163">Если вы не можете подключиться, убедитесь, что HoloLens 2 не подключен к компьютеру и перезапустите Unity.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="4b8c1-164">Подключение к HoloLens с помощью USB-кабеля</span><span class="sxs-lookup"><span data-stu-id="4b8c1-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="4b8c1-165">Подключение через USB-кабель обеспечивает лучшее качество и стабильность при визуализации.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="4b8c1-166">Чтобы использовать подключение по USB-кабелю, отключитесь от HoloLens Wi-Fi в параметрах HoloLens и запустите приложение удаленного проигрывателя Holographic.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="4b8c1-167">Он отобразит IP-адрес, который начинается с 169.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="4b8c1-168">Используйте этот IP-адрес в параметре эмуляции holographic в Unity для подключения.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="4b8c1-169">После определения IP-адреса для кабеля USB можно с легкостью подключить HoloLens к Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="4b8c1-170">Запуск сеанса удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="4b8c1-170">Starting a remoting session</span></span>

<span data-ttu-id="4b8c1-171">В Unity, подключенном к HoloLens, в редакторе введите режим воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="4b8c1-172">После завершения сеанса выйдите из режима воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8c1-173">Существует известная ситуация с некоторыми версиями Unity, в которых редактор может зависнуть при входе в режим воспроизведения во время сеанса удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="4b8c1-174">Эта проблема может проявляться, если при загрузке проекта открыто окно с Holographic.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="4b8c1-175">Чтобы убедиться, что эта проблема не возникает, всегда закрывайте диалоговое окно holographic перед выходом из Unity.</span><span class="sxs-lookup"><span data-stu-id="4b8c1-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b8c1-176">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4b8c1-176">See also</span></span>

- [<span data-ttu-id="4b8c1-177">Устранение неполадок и ограничения удаленного взаимодействия с holographic</span><span class="sxs-lookup"><span data-stu-id="4b8c1-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="4b8c1-178">Условия лицензионного соглашения на использование программного обеспечения для удаленного взаимодействия Microsoft holographic</span><span class="sxs-lookup"><span data-stu-id="4b8c1-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)