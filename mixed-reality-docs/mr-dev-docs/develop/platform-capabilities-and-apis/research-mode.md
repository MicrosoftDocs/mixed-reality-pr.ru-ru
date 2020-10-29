---
title: Режим исследования HoloLens
description: С помощью режима исследований в HoloLens приложение может получать доступ к потокам датчиков устройств (глубина, отслеживание среды и IR-рефлективити).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Режим исследований, ОПС, RS4, компьютерное зрение, исследование, HoloLens, HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692044"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="c7441-104">Режим исследования HoloLens</span><span class="sxs-lookup"><span data-stu-id="c7441-104">HoloLens Research Mode</span></span>

<span data-ttu-id="c7441-105">Режим исследования появился в первом поколение HoloLens, чтобы предоставить доступ к датчикам ключей на устройстве, специально для исследования приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="c7441-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="c7441-106">Режим исследования для HoloLens 2 обеспечивает возможности HoloLens 1, добавляя доступ к дополнительным потокам:</span><span class="sxs-lookup"><span data-stu-id="c7441-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="c7441-107">**Видимые камеры с отслеживанием светлых окружений** — серые камеры, используемые системой для отслеживания и создания карт.</span><span class="sxs-lookup"><span data-stu-id="c7441-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="c7441-108">**Камера с глубиной** — работает в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="c7441-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="c7441-109">АХАТ, высокая частота (45 кадров/с). используется для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="c7441-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="c7441-110">По-разному в режиме короткого создания, АХАТ предоставляет псевдо-depth с этапом, превышающим 1 счетчик.</span><span class="sxs-lookup"><span data-stu-id="c7441-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="c7441-111">Длительное исключение (1-5 кадров/с низкой частотой), используемое для [пространственного сопоставления](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="c7441-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="c7441-112">**Две версии потока IR-рефлективити** , используемые HoloLens для расчета глубины.</span><span class="sxs-lookup"><span data-stu-id="c7441-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="c7441-113">Эти изображения загораются инфракрасной связью и не зависят от внешнего видимого светового индикатора.</span><span class="sxs-lookup"><span data-stu-id="c7441-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="c7441-114">Если вы используете HoloLens 2, вы также получите доступ к дополнительным входным данным ниже:</span><span class="sxs-lookup"><span data-stu-id="c7441-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="c7441-115">**Акселерометр** — используется системой для определения линейного ускорения по осям X, Y и Z, а также сила притяжения.</span><span class="sxs-lookup"><span data-stu-id="c7441-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="c7441-116">**Гиро** — используется системой для определения поворотов.</span><span class="sxs-lookup"><span data-stu-id="c7441-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="c7441-117">**Магнитометр** — используется системой для оценки абсолютной ориентации.</span><span class="sxs-lookup"><span data-stu-id="c7441-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7441-118">Режим исследования в настоящее время находится в общедоступной предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="c7441-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="c7441-119">![Снимок экрана приложения в режиме исследования](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7441-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="c7441-120">*Запись в смешанной реальности тестового приложения, отображающего восемь потоков датчиков, доступных в режиме исследования.*</span><span class="sxs-lookup"><span data-stu-id="c7441-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="c7441-121">Использование</span><span class="sxs-lookup"><span data-stu-id="c7441-121">Usage</span></span>

<span data-ttu-id="c7441-122">Режим исследования предназначен для академических и промышленных исследователей, посвященных новым идеям в полях Компьютерное зрение и Robotics.</span><span class="sxs-lookup"><span data-stu-id="c7441-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="c7441-123">Он не предназначен для приложений, развернутых в корпоративных средах или доступных через Microsoft Store или другие каналы распространения.</span><span class="sxs-lookup"><span data-stu-id="c7441-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="c7441-124">Кроме того, корпорация Майкрософт не предоставляет гарантии, что режим исследования или эквивалентные функции будут поддерживаться в будущих обновлениях оборудования или ОС.</span><span class="sxs-lookup"><span data-stu-id="c7441-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="c7441-125">Однако это не должно помешать вам использовать его для разработки и тестирования новых идей!</span><span class="sxs-lookup"><span data-stu-id="c7441-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="c7441-126">Безопасность и производительность</span><span class="sxs-lookup"><span data-stu-id="c7441-126">Security and performance</span></span>

<span data-ttu-id="c7441-127">Имейте в виду, что включение режима исследования использует больше энергии аккумулятора, чем использование HoloLens 2 в нормальных условиях.</span><span class="sxs-lookup"><span data-stu-id="c7441-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="c7441-128">Это справедливо, даже если приложение, использующее функции режима исследования, не работает.</span><span class="sxs-lookup"><span data-stu-id="c7441-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="c7441-129">Включение этого режима может также снизить общую безопасность устройства, так как приложения могут использовать данные датчика неверно.</span><span class="sxs-lookup"><span data-stu-id="c7441-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="c7441-130">Дополнительные сведения о безопасности устройств можно найти в [разделе вопросы и ответы о безопасности HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="c7441-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="c7441-131">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="c7441-131">Device support</span></span>
<table><span data-ttu-id="c7441-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="c7441-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="c7441-133"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="c7441-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c7441-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1-го поколения</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7441-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="c7441-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7441-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c7441-136">Камеры для отслеживания головного подразделения</span><span class="sxs-lookup"><span data-stu-id="c7441-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="c7441-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-137">✔️</span></span></td>
        <td><span data-ttu-id="c7441-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7441-139">Глубина & ИК-камере</span><span class="sxs-lookup"><span data-stu-id="c7441-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="c7441-140">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-140">✔️</span></span></td>
        <td><span data-ttu-id="c7441-141">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7441-142">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="c7441-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7441-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7441-144">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="c7441-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7441-145">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7441-146">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="c7441-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7441-147">✔️</span><span class="sxs-lookup"><span data-stu-id="c7441-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="c7441-148">Включение режима исследований (HoloLens 1 Gen и HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="c7441-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="c7441-149">Режим исследования — это расширение режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="c7441-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="c7441-150">Перед началом работы необходимо включить функции разработчика устройства для доступа к параметрам режима исследования:</span><span class="sxs-lookup"><span data-stu-id="c7441-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="c7441-151">Откройте **меню "Пуск" > "Параметры** " и выберите " **обновления** ".</span><span class="sxs-lookup"><span data-stu-id="c7441-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="c7441-152">Выберите **для разработчиков** и включите **режим разработчика** .</span><span class="sxs-lookup"><span data-stu-id="c7441-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="c7441-153">Прокрутите вниз и включите **Портал устройств** .</span><span class="sxs-lookup"><span data-stu-id="c7441-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="c7441-154">После включения функций [для разработчиков подключитесь к порталу устройств](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) , чтобы включить функции режима исследования:</span><span class="sxs-lookup"><span data-stu-id="c7441-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="c7441-155">Перейдите в **режим "система > исследований** " на **портале устройств** .</span><span class="sxs-lookup"><span data-stu-id="c7441-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="c7441-156">Выберите **Разрешить доступ к потоку датчика** .</span><span class="sxs-lookup"><span data-stu-id="c7441-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="c7441-157">Перезапустите устройство из пункта меню " **Электропитание** " в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="c7441-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="c7441-158">После перезагрузки устройства приложения, загруженные с помощью **портала устройств** , могут получить доступ к потокам в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="c7441-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="c7441-159">![Вкладка "режим исследования" портала устройств HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="c7441-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="c7441-160">*Окно режима исследований на портале устройств HoloLens*</span><span class="sxs-lookup"><span data-stu-id="c7441-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7441-161">Режим исследования для HoloLens 2 доступен начиная с сборки 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="c7441-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="c7441-162">Если вам нужен доступ в более ранней сборке, зарегистрируйтесь для получения [предварительной версии программы предварительной оценки](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="c7441-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="c7441-163">Использование данных датчика в приложениях</span><span class="sxs-lookup"><span data-stu-id="c7441-163">Using sensor data in your apps</span></span>

<span data-ttu-id="c7441-164">Приложения могут получать доступ к данным потока датчика точно так же, как к видеокамере и видеокамерам обращаются через [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="c7441-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="c7441-165">Все API-интерфейсы, работающие для разработки HoloLens, также доступны в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="c7441-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="c7441-166">В частности, приложение точно знает, где HoloLens находится в 6DoF пространстве во время записи каждого кадра датчика.</span><span class="sxs-lookup"><span data-stu-id="c7441-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="c7441-167">Вы можете найти примеры приложений для доступа к различным потокам в режиме исследования, используя [встроенные функции и внешние компоненты](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), а также записывая потоки в соответствующем режиме исследований репозиториев:</span><span class="sxs-lookup"><span data-stu-id="c7441-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="c7441-168">HoloLens (1-го поколения)</span><span class="sxs-lookup"><span data-stu-id="c7441-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="c7441-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c7441-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="c7441-170">Поддержка</span><span class="sxs-lookup"><span data-stu-id="c7441-170">Support</span></span>

<span data-ttu-id="c7441-171">Для HoloLens (1-го поколения) используйте [средство записи проблем](https://github.com/Microsoft/HololensForCV/issues) в репозитории хололенсфоркв, чтобы публиковать отзывы и контролировать известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="c7441-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="c7441-172">Для HoloLens 2 Используйте [средство записи проблем](https://github.com/microsoft/HoloLens2ForCV/issues) в репозитории HoloLens2ForCV, чтобы публиковать отзывы и контролировать известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="c7441-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7441-173">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c7441-173">See also</span></span>

* [<span data-ttu-id="c7441-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="c7441-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="c7441-175">Репозиторий GitHub Хололенсфоркв</span><span class="sxs-lookup"><span data-stu-id="c7441-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="c7441-176">Репозиторий GitHub HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="c7441-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="c7441-177">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="c7441-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
