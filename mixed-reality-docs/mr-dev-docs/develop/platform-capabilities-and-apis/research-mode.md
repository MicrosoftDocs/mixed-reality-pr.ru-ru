---
title: Режим исследования в HoloLens
description: С помощью режима исследований в HoloLens приложение может получать доступ к потокам датчиков устройств (глубина, отслеживание среды и IR-рефлективити).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Режим исследований, ОПС, RS4, компьютерное зрение, исследование, HoloLens, HoloLens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237135"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="7bc2a-104">Режим исследования в HoloLens</span><span class="sxs-lookup"><span data-stu-id="7bc2a-104">HoloLens Research Mode</span></span>

<span data-ttu-id="7bc2a-105">Режим исследования появился на устройствах HoloLens (1-го поколения) для предоставления доступа к датчикам ключей, специально для исследования приложений, которые не предназначены для развертывания.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-105">Research Mode was introduced on HoloLens (1st Gen) devices to give access to key sensors, specifically for research applications that aren't intended for deployment.</span></span>  <span data-ttu-id="7bc2a-106">Режим исследования для HoloLens 2 сохраняет возможности HoloLens 1, но добавляет доступ к следующим потокам:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-106">Research Mode for HoloLens 2 keeps the capabilities of HoloLens 1 but adds access to the following streams:</span></span>

* <span data-ttu-id="7bc2a-107">**Видимые камеры с отслеживанием светлых окружений** — серые камеры, используемые системой для отслеживания и создания карт.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="7bc2a-108">**Камера с глубиной** — работает в двух режимах:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="7bc2a-109">АХАТ, высокая частота (45 кадров/с). используется для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="7bc2a-110">По-разному в первом режиме короткого создания версии, АХАТ дает псевдо-глубину, а не 1 индикатор.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-110">Differently from the first version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="7bc2a-111">Длительное исключение (1-5 кадров/с низкой частотой), используемое для [пространственного сопоставления](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="7bc2a-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="7bc2a-112">**Две версии потока IR-рефлективити** , используемые HoloLens для расчета глубины.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="7bc2a-113">Эти изображения загораются инфракрасной связью и не зависят от внешнего видимого светового индикатора.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="7bc2a-114">Если вы используете HoloLens 2, у вас также есть доступ к дополнительным входным данным ниже:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-114">If you're using a HoloLens 2, you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="7bc2a-115">**Акселерометр** — используется системой для определения линейного ускорения по осям X, Y и Z, а также сила притяжения.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y, and Z axes and gravity.</span></span>
* <span data-ttu-id="7bc2a-116">**Гиро** — используется системой для определения поворотов.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="7bc2a-117">**Магнитометр** — используется системой для оценки абсолютной ориентации.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bc2a-118">Режим исследования в настоящее время находится в общедоступной предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="7bc2a-119">![Снимок экрана приложения в режиме исследования](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="7bc2a-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="7bc2a-120">*Запись в смешанной реальности тестового приложения, отображающего восемь потоков датчиков, доступных в режиме исследования.*</span><span class="sxs-lookup"><span data-stu-id="7bc2a-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="7bc2a-121">Использование</span><span class="sxs-lookup"><span data-stu-id="7bc2a-121">Usage</span></span>

<span data-ttu-id="7bc2a-122">Режим исследования предназначен для академических и промышленных исследователей, посвященных новым идеям в полях Компьютерное зрение и Robotics.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="7bc2a-123">Он не предназначен для приложений, развернутых в корпоративных средах или доступных через Microsoft Store или другие каналы распространения.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="7bc2a-124">Кроме того, корпорация Майкрософт не предоставляет гарантии, что режим исследования или эквивалентные функции будут поддерживаться в будущих обновлениях оборудования или ОС.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="7bc2a-125">Тем не менее, не разрешите, что вы не будете использовать его для разработки и тестирования новых идей!</span><span class="sxs-lookup"><span data-stu-id="7bc2a-125">However, don't let that stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="7bc2a-126">Безопасность и производительность</span><span class="sxs-lookup"><span data-stu-id="7bc2a-126">Security and performance</span></span>

<span data-ttu-id="7bc2a-127">Включение режима исследований использует больше энергии аккумулятора, чем использование HoloLens 2 при нормальных условиях, даже если приложение, использующее функции режима исследования, не запущено.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-127">Enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions, even if the application using the Research Mode features isn't running.</span></span>  <span data-ttu-id="7bc2a-128">Включение этого режима может также снизить общую безопасность устройства, так как приложения могут использовать данные датчика неверно.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-128">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="7bc2a-129">Дополнительные сведения о безопасности устройств можно найти в [разделе вопросы и ответы о безопасности HoloLens](/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="7bc2a-129">You can find more information on device security in the [HoloLens security FAQ](/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="7bc2a-130">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="7bc2a-130">Device support</span></span>
<table><span data-ttu-id="7bc2a-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="7bc2a-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="7bc2a-132"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="7bc2a-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7bc2a-133"><a href="/hololens/hololens1-hardware"><strong>HoloLens первого поколения</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bc2a-133"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="7bc2a-134"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bc2a-134"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7bc2a-135">Камеры для отслеживания головного подразделения</span><span class="sxs-lookup"><span data-stu-id="7bc2a-135">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="7bc2a-136">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-136">✔️</span></span></td>
        <td><span data-ttu-id="7bc2a-137">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-137">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7bc2a-138">Глубина & ИК-камере</span><span class="sxs-lookup"><span data-stu-id="7bc2a-138">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="7bc2a-139">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-139">✔️</span></span></td>
        <td><span data-ttu-id="7bc2a-140">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-140">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7bc2a-141">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="7bc2a-141">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7bc2a-142">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7bc2a-143">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="7bc2a-143">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7bc2a-144">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7bc2a-145">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="7bc2a-145">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7bc2a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="7bc2a-146">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a><span data-ttu-id="7bc2a-147">Включение режима исследований (первое поколение HoloLens и HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="7bc2a-147">Enabling Research Mode (HoloLens first Gen and HoloLens 2)</span></span>

<span data-ttu-id="7bc2a-148">Режим исследования — это расширение режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-148">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="7bc2a-149">Перед началом работы необходимо включить функции разработчика устройства для доступа к параметрам режима исследования:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-149">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="7bc2a-150">Откройте **меню "Пуск" > "Параметры** " и выберите " **обновления**".</span><span class="sxs-lookup"><span data-stu-id="7bc2a-150">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="7bc2a-151">Выберите **для разработчиков** и включите **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-151">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="7bc2a-152">Прокрутите вниз и включите **Портал устройств**.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-152">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="7bc2a-153">После включения функций [для разработчиков подключитесь к порталу устройств](/windows/uwp/debug-test-perf/device-portal-hololens) , чтобы включить функции режима исследования:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-153">After the developer features  are enabled, [connect to the device portal](/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="7bc2a-154">Перейдите в **режим "система > исследований** " на **портале устройств**.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-154">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="7bc2a-155">Выберите **Разрешить доступ к потоку датчика**.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-155">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="7bc2a-156">Перезапустите устройство из пункта меню " **Электропитание** " в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-156">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="7bc2a-157">После перезагрузки устройства приложения, загруженные с помощью **портала устройств** , могут получить доступ к потокам в режиме исследования.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-157">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="7bc2a-158">![Вкладка "режим исследования" портала устройств HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="7bc2a-158">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="7bc2a-159">*Окно режима исследований на портале устройств HoloLens*</span><span class="sxs-lookup"><span data-stu-id="7bc2a-159">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bc2a-160">Режим исследования для HoloLens 2 доступен начиная с сборки 19041,1364.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-160">Research Mode for HoloLens 2 is available beginning with build 19041.1364 .</span></span> <span data-ttu-id="7bc2a-161">Если вам нужен доступ в более ранней сборке, зарегистрируйтесь для получения [предварительной версии программы предварительной оценки](/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="7bc2a-161">If you need access in an earlier build, sign up for our [Insider Preview](/hololens/hololens-insider) program.</span></span> <span data-ttu-id="7bc2a-162">Дополнительные сведения можно найти в [репозитории GitHub в режиме исследований](https://github.com/microsoft/HoloLens2ForCV).</span><span class="sxs-lookup"><span data-stu-id="7bc2a-162">You can find more details in the [Research Mode GitHub repository](https://github.com/microsoft/HoloLens2ForCV).</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="7bc2a-163">Использование данных датчика в приложениях</span><span class="sxs-lookup"><span data-stu-id="7bc2a-163">Using sensor data in your apps</span></span>

<span data-ttu-id="7bc2a-164">Приложения могут получать доступ к данным потока датчика так же, как [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) доступ к потокам фото и видео.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-164">Applications can access the sensor stream data in the same way that [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) accesses photo and video camera streams.</span></span> 

<span data-ttu-id="7bc2a-165">Все API-интерфейсы, работающие для разработки HoloLens, также доступны в режиме исследований.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="7bc2a-166">В частности, приложение точно знает, где HoloLens находится в 6DoF пространстве во время записи каждого кадра датчика.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="7bc2a-167">У нас есть образцы приложений, демонстрирующие доступ к потоку в режиме исследований, использование [встроенных функций и внешних](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)компонентов, а также запись потоков:</span><span class="sxs-lookup"><span data-stu-id="7bc2a-167">We have sample applications showing Research Mode stream access, using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams:</span></span>
* [<span data-ttu-id="7bc2a-168">HoloLens (первый общий)</span><span class="sxs-lookup"><span data-stu-id="7bc2a-168">HoloLens (first gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="7bc2a-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7bc2a-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="7bc2a-170">Поддержка</span><span class="sxs-lookup"><span data-stu-id="7bc2a-170">Support</span></span>

<span data-ttu-id="7bc2a-171">Для HoloLens (First Gen) используйте [средство записи проблем](https://github.com/Microsoft/HololensForCV/issues) в репозитории хололенсфоркв, чтобы публиковать отзывы и контролировать известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-171">For HoloLens (first gen), use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="7bc2a-172">Для HoloLens 2 Используйте [средство записи проблем](https://github.com/microsoft/HoloLens2ForCV/issues) в репозитории HoloLens2ForCV, чтобы публиковать отзывы и контролировать известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="7bc2a-172">For HoloLens 2, use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bc2a-173">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7bc2a-173">See also</span></span>

* [<span data-ttu-id="7bc2a-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="7bc2a-174">Microsoft Media Foundation</span></span>](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [<span data-ttu-id="7bc2a-175">Репозиторий GitHub Хололенсфоркв</span><span class="sxs-lookup"><span data-stu-id="7bc2a-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="7bc2a-176">Репозиторий GitHub HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="7bc2a-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="7bc2a-177">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="7bc2a-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)