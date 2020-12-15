---
title: Профилирование с помощью неreal Insights
description: Узнайте, как использовать неreal Insights в HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Нереал, Нереальный механизм 4, UE4, HoloLens, HoloLens 2, разработка, профилирования, нереалная информация, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486375"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="54458-104">Профилирование с помощью неreal Insights</span><span class="sxs-lookup"><span data-stu-id="54458-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="54458-105">[Нереалная аналитика](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) — это система профилирования, собирающая, анализирующая и визуализирующая данные из нереального механизма.</span><span class="sxs-lookup"><span data-stu-id="54458-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="54458-106">Система профилирования помогает найти узкие места оптимизации и области, в которых производительность приложений может увеличиться.</span><span class="sxs-lookup"><span data-stu-id="54458-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="54458-107">Как правило, вы включаете функцию "неreal Insights" прямо из редактора, но для HoloLens 2 потребуется использовать командную строку.</span><span class="sxs-lookup"><span data-stu-id="54458-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="54458-108">Настройка</span><span class="sxs-lookup"><span data-stu-id="54458-108">Setup</span></span>

<span data-ttu-id="54458-109">Нереал. позволяет создать и настроить "настраиваемый профиль" в средстве запуска HoloLens с параметрами командной строки, которые включают неreal Insights.</span><span class="sxs-lookup"><span data-stu-id="54458-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="54458-110">Найдите IP-адрес компьютера с помощью команды **ipconfig** в командной строке.</span><span class="sxs-lookup"><span data-stu-id="54458-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="54458-111">IP-адрес — это адрес IPv4, указанный в ipconfig.</span><span class="sxs-lookup"><span data-stu-id="54458-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="54458-112">Помните об этом при настройке параметров командной строки.</span><span class="sxs-lookup"><span data-stu-id="54458-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54458-113">Если вы находитесь за VPN, вам может потребоваться предоставить IP-адрес, предоставленный через VPN.</span><span class="sxs-lookup"><span data-stu-id="54458-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Снимок экрана: результаты командной строки для команды ipconfig](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="54458-115">Перейдите в начало панели нереала и откройте **Device Manager** под кнопкой **запуска** :</span><span class="sxs-lookup"><span data-stu-id="54458-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Снимок экрана параметров запуска с выделенным диспетчером устройств](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="54458-117">В Device Manager выберите **Добавить устройство, которое** не было добавлено в список.</span><span class="sxs-lookup"><span data-stu-id="54458-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Снимок экрана: Открытие диспетчера устройств в нереальном ядре](images/unreal-insights-img-03.png)

4. <span data-ttu-id="54458-119">Щелкните **выбрать платформу** и выберите **HoloLens**:</span><span class="sxs-lookup"><span data-stu-id="54458-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Снимок экрана: Добавление раскрывающегося списка непоставленных устройств с выделенным HoloLens](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="54458-121">Если вы используете Иповерусб, введите 127.0.0.1:10080 в качестве идентификатора устройства.</span><span class="sxs-lookup"><span data-stu-id="54458-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="54458-122">Введите имя пользователя и пароль HoloLens в соответствующие поля и заполните **Отображаемое название** по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="54458-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54458-123">Идентификатор устройства — это IP-адрес HoloLens, а не компьютер с нереальными сведениями, найденными на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="54458-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Снимок экрана сведений об устройстве HoloLens в диспетчере устройств](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="54458-125">Выберите **Добавить** , и HoloLens должен появиться в списке устройств диспетчера устройств:</span><span class="sxs-lookup"><span data-stu-id="54458-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Снимок экрана: HoloLens добавлен в список устройств](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="54458-127">Launch</span><span class="sxs-lookup"><span data-stu-id="54458-127">Launch</span></span>

1. <span data-ttu-id="54458-128">Откройте **средство запуска проектов** на панели UE4 под кнопкой **запустить** :</span><span class="sxs-lookup"><span data-stu-id="54458-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Снимок экрана параметров запуска с выделенным средством запуска проекта](images/unreal-insights-img-07.png)

2. <span data-ttu-id="54458-130">Нажмите **+** кнопку, чтобы создать настраиваемый профиль в разделе **пользовательские профили запуска**.</span><span class="sxs-lookup"><span data-stu-id="54458-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="54458-131">После создания этот профиль можно изменить позже:</span><span class="sxs-lookup"><span data-stu-id="54458-131">Once created, you can always edit this profile later:</span></span>

![Снимок экрана средства запуска проекта с выделенными пользовательскими профилями запуска](images/unreal-insights-img-08.png)

3. <span data-ttu-id="54458-133">Нажмите кнопку **изменить профиль** в настраиваемом профиле запуска HoloLens и настройте:</span><span class="sxs-lookup"><span data-stu-id="54458-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="54458-134">Выберите в **книге** **Кука** , чтобы включить копирование на устройство</span><span class="sxs-lookup"><span data-stu-id="54458-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="54458-135">Возможно, вы захотите выполнить **архивацию** в разделе " **Архив** ", чтобы сохранить созданный. appxbundle вместо удаления, чтобы сэкономить место на диске.</span><span class="sxs-lookup"><span data-stu-id="54458-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="54458-136">Укажите расположение для appxbundle и переключитесь на сборку разработки, если хотите</span><span class="sxs-lookup"><span data-stu-id="54458-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Снимок экрана с параметрами Кука в конфигурации профиля с Кука, выделенной книгой и HoloLens](images/unreal-insights-img-09.png)

4. <span data-ttu-id="54458-138">Укажите, **как вы хотите развернуть сборку?** для **копирования на устройство** , чтобы активировать раздел **запуска** пользовательского интерфейса:</span><span class="sxs-lookup"><span data-stu-id="54458-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Снимок экрана средства запуска проектов с параметрами развертывания с выделенным копированием в устройство](images/unreal-insights-img-10.png)

5. <span data-ttu-id="54458-140">Задайте **Дополнительные параметры командной строки** в разделе **Launch** .</span><span class="sxs-lookup"><span data-stu-id="54458-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="54458-141">Параметры записываются в файл ue4commandline.txt, упаковываются в пакет и используются при запуске.</span><span class="sxs-lookup"><span data-stu-id="54458-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="54458-142">Попробуйте для начинающих: **-трацехост = IP_OF_YOUR_PC-Trace = журнал, закладка, кадр, ЦП, GPU, лоадтиме, файл, NET**</span><span class="sxs-lookup"><span data-stu-id="54458-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="54458-143">Полный список доступных параметров запуска можно найти в [справочной документации о нереальных аналитиках](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="54458-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="54458-144">"IP_OF_YOUR_PC" — это IP-адрес, найденный на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="54458-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="54458-145">Это IP-адрес компьютера, на котором выполняются нереальные аналитические сведения, а не IP-адрес HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54458-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54458-146">Трассировка может значительно быстро получиться.</span><span class="sxs-lookup"><span data-stu-id="54458-146">Traces can get large very quickly.</span></span> <span data-ttu-id="54458-147">Включайте только те каналы, которые необходимы для обеспечения низкого размера трассировки.</span><span class="sxs-lookup"><span data-stu-id="54458-147">Enable only those channels you need to keep trace size low.</span></span>

![Снимок экрана параметров конфигурации запуска](images/unreal-insights-img-11.png)

6. <span data-ttu-id="54458-149">Запустите нереалную аналитику перед запуском приложения, иначе нереальное понимание не сможет выполнить правильную инициализацию приложения:</span><span class="sxs-lookup"><span data-stu-id="54458-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="54458-150">Исполняемый файл неreal Insights хранится в папке обработчика двоичных файлов, как правило, следующим образом: "C:\Program Филес\епик Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe".</span><span class="sxs-lookup"><span data-stu-id="54458-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Снимок экрана исполняемого файла неreal Insights](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="54458-152">Нажмите кнопку **назад** , чтобы вернуться в корневую папку диалогового окна **запуска проекта** .</span><span class="sxs-lookup"><span data-stu-id="54458-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="54458-153">В редакторе щелкните **запустить** в настраиваемом профиле запуска.</span><span class="sxs-lookup"><span data-stu-id="54458-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Снимок экрана с пользовательскими профилями запуска](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="54458-155">Следите за тем, чтобы проект был упакован, установлен на устройстве и запущен.</span><span class="sxs-lookup"><span data-stu-id="54458-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="54458-156">Профилирование</span><span class="sxs-lookup"><span data-stu-id="54458-156">Profiling</span></span>

<span data-ttu-id="54458-157">Вернувшись в нереалную аналитику, выберите **активное** подключение к устройству для запуска профилирования.</span><span class="sxs-lookup"><span data-stu-id="54458-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="54458-158">Пользовательский профиль является общим для проектов.</span><span class="sxs-lookup"><span data-stu-id="54458-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="54458-159">Здесь вы можете использовать созданный вами пользовательский профиль вместо того, чтобы делать это каждый раз.</span><span class="sxs-lookup"><span data-stu-id="54458-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="54458-160">Подключение к устройству необходимо создать заново при каждом запуске нереального действия с шагами 3 – 6 в [разделе Настройка](#setup).</span><span class="sxs-lookup"><span data-stu-id="54458-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="54458-161">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="54458-161">See also</span></span>
* [<span data-ttu-id="54458-162">Документация по нереальным аналитикам</span><span class="sxs-lookup"><span data-stu-id="54458-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

