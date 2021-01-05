---
title: Установка PIX для HoloLens 2
description: Узнайте, как установить PIX для устройств HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, захват, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822920"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="ee9fe-104">Установка PIX для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ee9fe-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="ee9fe-105">[PIX](https://devblogs.microsoft.com/pix) — это средство настройки и отладки производительности для приложений DirectX 12 в Windows.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="ee9fe-106">Настройка</span><span class="sxs-lookup"><span data-stu-id="ee9fe-106">Setup</span></span>

1. <span data-ttu-id="ee9fe-107">Загрузите последнюю [версию PIX с]( https://devblogs.microsoft.com/pix/download) главного компьютера и подключите свой HoloLens 2 к компьютеру через USB-кабель.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="ee9fe-108">Если HoloLens 2 находится в сборке программы [предварительной оценки Windows](https://insider.windows.com) или имеет конфигурацию, которая отменяет PIX, изменяйте  [устройство](https://docs.microsoft.com/hololens/hololens-recovery) , чтобы стереть все данные.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="ee9fe-109">Включить **режим разработчика** и **портал устройств**:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="ee9fe-110">Откройте **Параметры** из дома смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-110">Open **Settings** from Mixed Reality Home:</span></span>

![Снимок экрана: меню HoloLens с выделенной кнопкой "Параметры"](images/pix-img-01.jpg)

* <span data-ttu-id="ee9fe-112">Выберите **обновление & безопасность**:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-112">Select **Update & Security**:</span></span>

![Снимок экрана: окно параметров открыто в HoloLens с выделенной кнопкой обновления и безопасности](images/pix-img-02.jpg)

* <span data-ttu-id="ee9fe-114">Выберите **для разработчиков**:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-114">Select **For Developers**:</span></span>

![Снимок экрана: окно "безопасность и обновления" с выделенной кнопкой "для разработчиков"](images/pix-img-03.jpg)

* <span data-ttu-id="ee9fe-116">Включение **использования функций разработчика** и **Включение портала устройств**</span><span class="sxs-lookup"><span data-stu-id="ee9fe-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Снимок экрана для окна "разработчики" в окне "Параметры" с выделенной кнопкой "включить на портале устройства"](images/pix-img-04.jpg)

![Снимок экрана: окно "для разработчиков" открыто в меню "параметры с помощью переключателя" Разработка компонентов "](images/pix-img-05.jpg)

* <span data-ttu-id="ee9fe-119">Если устройство по-прежнему подключено, в спящем режиме и пользователь вошел в систему, запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee9fe-120">Убедитесь, что устройство находится не в режиме ожидания или в спящем режиме.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="ee9fe-121">Если у вас возникли проблемы с этим шагом, см. [инструкции на портале устройств Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="ee9fe-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="ee9fe-122">Подготовка к развертыванию</span><span class="sxs-lookup"><span data-stu-id="ee9fe-122">Preparing for deployment</span></span>

1. <span data-ttu-id="ee9fe-123">В Visual Studio задайте **ARM64** в качестве платформы и **устройства** в качестве устройства:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Снимок экрана решения Visual Studios с выделенными параметрами платформы и устройства](images/pix-img-06.png)

2. <span data-ttu-id="ee9fe-125">Когда Visual Studio запрашивает у устройства **ПИН-код** :</span><span class="sxs-lookup"><span data-stu-id="ee9fe-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Снимок экрана всплывающего окна Visual Studio с запросом ПИН-кода](images/pix-img-07.png)

* <span data-ttu-id="ee9fe-127">Выбор **параметров** из оболочки</span><span class="sxs-lookup"><span data-stu-id="ee9fe-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="ee9fe-128">Выберите **обновление & безопасность**</span><span class="sxs-lookup"><span data-stu-id="ee9fe-128">Select **Update & Security**</span></span>
* <span data-ttu-id="ee9fe-129">Выберите **для разработчиков** и нажмите пару в разделе **обнаружение устройства**</span><span class="sxs-lookup"><span data-stu-id="ee9fe-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Снимок экрана для окна "разработчики", Открытый в параметрах с выделенным обнаружением устройств](images/pix-img-08.jpg)

![Снимок экрана: всплывающее окно платного устройства с выделенным кодом регистрации](images/pix-img-09.jpg)

* <span data-ttu-id="ee9fe-132">Введите созданный ПИН-код в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ee9fe-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="ee9fe-133">Visual Studio развернет приложение в подключенный HoloLens. 2, что может занять несколько минут в зависимости от приложения.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="ee9fe-134">Запуск PIX</span><span class="sxs-lookup"><span data-stu-id="ee9fe-134">Launching PIX</span></span>

<span data-ttu-id="ee9fe-135">Сначала используйте портал устройств, чтобы убедиться, что приложение не выполняется в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="ee9fe-136">Затем запустите PIX, подключитесь к устройству и выберите **Домашняя страница**:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Снимок экрана с начальным экраном приложения PIX](images/pix-img-10.png)

* <span data-ttu-id="ee9fe-138">В меню слева щелкните **Подключиться** .</span><span class="sxs-lookup"><span data-stu-id="ee9fe-138">Select **Connect** from the left-side menu:</span></span>

![Снимок экрана: меню в левой части приложения PIX с выделенной кнопкой "подключить"](images/pix-img-11.png)

2. <span data-ttu-id="ee9fe-140">На вкладке **компьютер** выберите **Добавить** и введите следующие учетные данные:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="ee9fe-141">Псевдоним: по усмотрению пользователя</span><span class="sxs-lookup"><span data-stu-id="ee9fe-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="ee9fe-142">Имя узла или IP-адрес: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="ee9fe-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="ee9fe-143">В правом нижнем углу вкладки **компьютер** щелкните **Подключиться** .</span><span class="sxs-lookup"><span data-stu-id="ee9fe-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Снимок экрана: окно подключения приложения PIX с псевдонимом, именем узла, IP-адресом и выделенной кнопкой "Добавить"](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="ee9fe-145">Первое соединение всегда выполняется медленнее, так как копируются двоичные файлы.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="ee9fe-146">Когда PIX подключается к HoloLens 2, найдите свое приложение в разделе **Выбор целевого процесса** на вкладке Запуск UWP и выберите **Запуск**:</span><span class="sxs-lookup"><span data-stu-id="ee9fe-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Снимок экрана приложения PIX с выделенным окном "Выбор целевого процесса" и "Запуск"](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="ee9fe-148">Записываемый GPU</span><span class="sxs-lookup"><span data-stu-id="ee9fe-148">GPU captured</span></span>

1. <span data-ttu-id="ee9fe-149">Запустите захват GPU, щелкнув **фото** в разделе " **запись GPU** ":</span><span class="sxs-lookup"><span data-stu-id="ee9fe-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Снимок экрана приложения PIX с выделенной панелью подключения к ГРАФИЧЕСКОМу набору данных](images/pix-img-14.png)

2. <span data-ttu-id="ee9fe-151">Откройте запись для анализа, щелкнув созданный снимок экрана на панели **захвата GPU** :</span><span class="sxs-lookup"><span data-stu-id="ee9fe-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Снимок экрана приложения PIX с выделенным фрагментом графического процессора (панель захвата GPU)](images/pix-img-15.png)

3. <span data-ttu-id="ee9fe-153">Чтобы начать анализ, нажмите кнопку " **Пуск** ":</span><span class="sxs-lookup"><span data-stu-id="ee9fe-153">Press **Start** to begin the analysis:</span></span>

![Снимок экрана приложения PIX, выделенного кнопкой "запустить"](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="ee9fe-155">Если сбор данных о времени выполняется после записи GPU, потребуется перезагрузить гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="ee9fe-156">Это одноразовый перезапуск устройства, необходимый для сбора данных о времени.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="ee9fe-157">Теперь PIX готов к использованию.</span><span class="sxs-lookup"><span data-stu-id="ee9fe-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="ee9fe-158">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ee9fe-158">See also</span></span>
* [<span data-ttu-id="ee9fe-159">Домашняя страница PIX</span><span class="sxs-lookup"><span data-stu-id="ee9fe-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)