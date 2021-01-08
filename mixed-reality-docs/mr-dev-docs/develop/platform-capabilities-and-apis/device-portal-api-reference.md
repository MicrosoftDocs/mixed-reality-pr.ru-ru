---
title: Справочник по API портала устройств
description: Следите за обновлениями API портала устройств Windows для разработки HoloLens.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, портал устройств Windows, API, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 13845a5a5668ee8c86178196326425f46be9b321
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006654"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="890db-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="890db-104">Device portal API reference</span></span>

<span data-ttu-id="890db-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="890db-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="890db-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="890db-106">App deloyment</span></span>

<span data-ttu-id="890db-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="890db-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="890db-108">Uninstalls an app</span></span>

<span data-ttu-id="890db-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-109">Parameters</span></span>
* <span data-ttu-id="890db-110">Пакет: имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="890db-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="890db-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="890db-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="890db-112">Installs an App</span></span>

<span data-ttu-id="890db-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-113">Parameters</span></span>
* <span data-ttu-id="890db-114">Пакет: имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="890db-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="890db-115">Payload</span><span class="sxs-lookup"><span data-stu-id="890db-115">Payload</span></span>
* <span data-ttu-id="890db-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="890db-116">multi-part conforming http body</span></span>

<span data-ttu-id="890db-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="890db-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="890db-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="890db-119">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-119">Return data</span></span>
* <span data-ttu-id="890db-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="890db-120">List of installed packages with details</span></span>

<span data-ttu-id="890db-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="890db-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="890db-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="890db-123">Дамп коллекции</span><span class="sxs-lookup"><span data-stu-id="890db-123">Dump collection</span></span>

<span data-ttu-id="890db-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="890db-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="890db-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-126">Parameters</span></span>
* <span data-ttu-id="890db-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="890db-127">packageFullname : package name</span></span>

<span data-ttu-id="890db-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="890db-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="890db-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-130">Parameters</span></span>
* <span data-ttu-id="890db-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="890db-131">packageFullname : package name</span></span>

<span data-ttu-id="890db-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="890db-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="890db-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-134">Parameters</span></span>
* <span data-ttu-id="890db-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="890db-135">packageFullname : package name</span></span>

<span data-ttu-id="890db-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="890db-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="890db-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-138">Parameters</span></span>
* <span data-ttu-id="890db-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="890db-139">packageFullname : package name</span></span>
* <span data-ttu-id="890db-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="890db-140">fileName : dump file name</span></span>

<span data-ttu-id="890db-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="890db-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="890db-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-143">Parameters</span></span>
* <span data-ttu-id="890db-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="890db-144">packageFullname : package name</span></span>
* <span data-ttu-id="890db-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="890db-145">fileName : dump file name</span></span>

<span data-ttu-id="890db-146">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-146">Return data</span></span>
* <span data-ttu-id="890db-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="890db-147">Dump file.</span></span> <span data-ttu-id="890db-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="890db-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="890db-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="890db-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="890db-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="890db-151">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-151">Return data</span></span>
* <span data-ttu-id="890db-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="890db-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="890db-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="890db-153">ETW</span></span>

<span data-ttu-id="890db-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="890db-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="890db-155">Enumerates registered providers</span></span>

<span data-ttu-id="890db-156">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-156">Return data</span></span>
* <span data-ttu-id="890db-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="890db-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="890db-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="890db-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="890db-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="890db-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="890db-160">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-160">Return data</span></span>
* <span data-ttu-id="890db-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="890db-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="890db-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="890db-162">Holographic OS</span></span>

<span data-ttu-id="890db-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="890db-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="890db-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="890db-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="890db-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="890db-166">Returns the states of all services running.</span></span>

<span data-ttu-id="890db-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="890db-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="890db-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="890db-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="890db-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="890db-170">Sets the IPD</span></span>

<span data-ttu-id="890db-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-171">Parameters</span></span>
* <span data-ttu-id="890db-172">IPD: новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="890db-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="890db-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="890db-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="890db-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="890db-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="890db-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="890db-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="890db-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-177">Parameters</span></span>
* <span data-ttu-id="890db-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="890db-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="890db-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="890db-179">Holographic Perception</span></span>

<span data-ttu-id="890db-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="890db-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="890db-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="890db-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="890db-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-182">Parameters</span></span>
* <span data-ttu-id="890db-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="890db-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="890db-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="890db-184">Holographic Thermal</span></span>

<span data-ttu-id="890db-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="890db-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="890db-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="890db-187">Диспетчер карт</span><span class="sxs-lookup"><span data-stu-id="890db-187">Map Manager</span></span>

<span data-ttu-id="890db-188">**/АПИ/холографик/мапманажер/мапфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="890db-189">Возвращает список доступных файлов карт (. мапкс).</span><span class="sxs-lookup"><span data-stu-id="890db-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="890db-190">**/АПИ/холографик/мапманажер/анчорфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="890db-191">Возвращает список доступных файлов привязки (. анккс).</span><span class="sxs-lookup"><span data-stu-id="890db-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="890db-192">**/АПИ/холографик/мапманажер/срдбфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="890db-193">Возвращает список доступных файлов базы данных пространственной реконструкции (. срдб).</span><span class="sxs-lookup"><span data-stu-id="890db-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="890db-194">**/АПИ/холографик/мапманажер/жетанчорс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="890db-195">Возвращает список материализованных привязок для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="890db-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="890db-196">Скачать, отправить или удалить файлы</span><span class="sxs-lookup"><span data-stu-id="890db-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="890db-197">**/АПИ/холографик/мапманажер/Довнлоад (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="890db-198">Скачивает файл схемы, привязки или базы данных пространственного восстановления.</span><span class="sxs-lookup"><span data-stu-id="890db-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="890db-199">Файл должен быть предварительно отправлен или экспортирован.</span><span class="sxs-lookup"><span data-stu-id="890db-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="890db-200">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-200">Parameters</span></span>
* <span data-ttu-id="890db-201">FileName: имя файла для скачивания.</span><span class="sxs-lookup"><span data-stu-id="890db-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="890db-202">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="890db-203">**/АПИ/холографик/мапманажер/уплоад (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="890db-204">Отправляет файл схемы, привязки или пространственной реконструкции базы данных.</span><span class="sxs-lookup"><span data-stu-id="890db-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="890db-205">После отправки файла его можно будет импортировать в систему в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="890db-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="890db-206">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-206">Parameters</span></span>
* <span data-ttu-id="890db-207">файл: имя файла для отправки.</span><span class="sxs-lookup"><span data-stu-id="890db-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="890db-208">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="890db-209">**/АПИ/холографик/мапманажер/делете (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="890db-210">Удаляет файл схемы, привязки или базы данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="890db-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="890db-211">Файл должен быть предварительно отправлен или экспортирован.</span><span class="sxs-lookup"><span data-stu-id="890db-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="890db-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-212">Parameters</span></span>
* <span data-ttu-id="890db-213">FileName: имя удаляемого файла.</span><span class="sxs-lookup"><span data-stu-id="890db-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="890db-214">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="890db-215">Экспорт</span><span class="sxs-lookup"><span data-stu-id="890db-215">Export</span></span>

<span data-ttu-id="890db-216">**/АПИ/холографик/мапманажер/експорт (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="890db-217">Экспортирует текущую карту, используемую системой.</span><span class="sxs-lookup"><span data-stu-id="890db-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="890db-218">После экспорта его можно скачать.</span><span class="sxs-lookup"><span data-stu-id="890db-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="890db-219">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="890db-220">**/АПИ/холографик/мапманажер/експортанчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="890db-221">Экспортирует текущую карту, используемую системой.</span><span class="sxs-lookup"><span data-stu-id="890db-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="890db-222">После экспорта его можно скачать.</span><span class="sxs-lookup"><span data-stu-id="890db-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="890db-223">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="890db-224">**/АПИ/холографик/мапманажер/експортмапанданчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="890db-225">Экспортирует карту и привязки, используемые системой в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="890db-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="890db-226">После экспорта их можно скачать.</span><span class="sxs-lookup"><span data-stu-id="890db-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="890db-227">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="890db-228">**/АПИ/холографик/мапманажер/експортмапандспатиалмаппингдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="890db-229">Экспортирует базу данных Map и spatial реконструкции, используемую системой в данный момент.</span><span class="sxs-lookup"><span data-stu-id="890db-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="890db-230">После экспорта их можно скачать.</span><span class="sxs-lookup"><span data-stu-id="890db-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="890db-231">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="890db-232">Импорт</span><span class="sxs-lookup"><span data-stu-id="890db-232">Import</span></span>

<span data-ttu-id="890db-233">**/АПИ/холографик/мапманажер/импорт (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="890db-234">Указывает системе, какую карту следует использовать в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="890db-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="890db-235">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="890db-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="890db-236">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-236">Parameters</span></span>
* <span data-ttu-id="890db-237">FileName: имя используемой схемы.</span><span class="sxs-lookup"><span data-stu-id="890db-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="890db-238">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="890db-239">**/АПИ/холографик/мапманажер/импортанчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="890db-240">Указывает системе, какие привязки должны использоваться в текущий момент.</span><span class="sxs-lookup"><span data-stu-id="890db-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="890db-241">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="890db-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="890db-242">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-242">Parameters</span></span>
* <span data-ttu-id="890db-243">FileName: имя используемых привязок.</span><span class="sxs-lookup"><span data-stu-id="890db-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="890db-244">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="890db-245">**/АПИ/холографик/мапманажер/импортспатиалмаппингдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="890db-246">Указывает на систему, в которой должна использоваться база данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="890db-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="890db-247">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="890db-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="890db-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-248">Parameters</span></span>
* <span data-ttu-id="890db-249">FileName: имя базы данных пространственного сопоставления, которая будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="890db-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="890db-250">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="890db-251">Другое</span><span class="sxs-lookup"><span data-stu-id="890db-251">Other</span></span>

<span data-ttu-id="890db-252">**/АПИ/холографик/мапманажер/ресетмапанданчорсандсрдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="890db-253">Сбросьте систему на карту, привязки и базу данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="890db-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="890db-254">Пример</span><span class="sxs-lookup"><span data-stu-id="890db-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="890db-255">**/АПИ/холографик/мапманажер/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="890db-256">Возвращает состояние системы, включая данные о сопоставлении, привязках и базах данных пространственной реконструкции, которые были импортированы в последний раз.</span><span class="sxs-lookup"><span data-stu-id="890db-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="890db-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="890db-257">Mixed Reality Capture</span></span>

<span data-ttu-id="890db-258">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="890db-259">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="890db-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="890db-260">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="890db-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="890db-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-261">Parameters</span></span>
* <span data-ttu-id="890db-262">имя файла: имя, hex64 в кодировке для получаемого видео.</span><span class="sxs-lookup"><span data-stu-id="890db-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="890db-263">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="890db-263">op : stream</span></span>

<span data-ttu-id="890db-264">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="890db-265">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="890db-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="890db-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-266">Parameters</span></span>
* <span data-ttu-id="890db-267">filename: Name, hex64 Encoded (имя файла), которое нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="890db-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="890db-268">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="890db-269">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="890db-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="890db-270">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="890db-271">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="890db-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="890db-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-272">Parameters</span></span>
* <span data-ttu-id="890db-273">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-274">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-275">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="890db-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="890db-276">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="890db-277">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="890db-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="890db-278">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="890db-279">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="890db-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="890db-280">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="890db-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="890db-281">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="890db-282">Возвращает состояние захвата смешанной реальности на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="890db-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="890db-283">\**_Ответ_* _</span><span class="sxs-lookup"><span data-stu-id="890db-283">\**_Response_* _</span></span>

<span data-ttu-id="890db-284">Ответ содержит свойство JSON, указывающее, записывается ли видео на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="890db-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="890db-285">_ */АПИ/холографик/МРК/сумбнаил (Get)*\*</span><span class="sxs-lookup"><span data-stu-id="890db-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="890db-286">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="890db-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="890db-287">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-287">Parameters</span></span>
* <span data-ttu-id="890db-288">filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.</span><span class="sxs-lookup"><span data-stu-id="890db-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="890db-289">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="890db-290">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="890db-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="890db-291">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-291">Parameters</span></span>
* <span data-ttu-id="890db-292">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-293">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-294">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-295">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-296">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="890db-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="890db-297">встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="890db-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="890db-298">встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="890db-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="890db-299">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="890db-300">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="890db-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="890db-301">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="890db-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="890db-302">Из-за изоляции замыкания на себя невозможно подключиться к потоковой передаче смешанной реальности из приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="890db-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="890db-303">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="890db-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="890db-304">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="890db-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="890db-305">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="890db-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="890db-306">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="890db-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="890db-307">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="890db-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="890db-308">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="890db-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="890db-309">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="890db-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="890db-310">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="890db-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="890db-311">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="890db-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="890db-312">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="890db-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="890db-313">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="890db-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="890db-314">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="890db-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="890db-315">**live.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="890db-316">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="890db-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="890db-317">**live_high.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="890db-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="890db-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="890db-319">**live_med.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="890db-320">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="890db-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="890db-321">**live_low.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="890db-322">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="890db-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="890db-323">Сеть</span><span class="sxs-lookup"><span data-stu-id="890db-323">Networking</span></span>

<span data-ttu-id="890db-324">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="890db-325">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="890db-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="890db-326">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="890db-326">OS Information</span></span>

<span data-ttu-id="890db-327">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="890db-328">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="890db-328">Gets operating system information</span></span>

<span data-ttu-id="890db-329">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="890db-330">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="890db-330">Gets the machine name</span></span>

<span data-ttu-id="890db-331">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="890db-332">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="890db-332">Sets the machine name</span></span>

<span data-ttu-id="890db-333">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-333">Parameters</span></span>
* <span data-ttu-id="890db-334">Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="890db-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="890db-335">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="890db-335">Perception Simulation Control</span></span>

<span data-ttu-id="890db-336">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="890db-337">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="890db-337">Get the simulation mode</span></span>

<span data-ttu-id="890db-338">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="890db-339">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="890db-339">Set the simulation mode</span></span>

<span data-ttu-id="890db-340">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-340">Parameters</span></span>
* <span data-ttu-id="890db-341">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="890db-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="890db-342">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="890db-343">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="890db-343">Delete a control stream.</span></span>

<span data-ttu-id="890db-344">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="890db-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="890db-345">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="890db-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="890db-346">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="890db-347">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="890db-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="890db-348">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="890db-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="890db-349">**/АПИ/холографик/симулатион/дисплай/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="890db-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="890db-350">Запросите поток видео имитации, содержащий содержимое, отображаемое для отображения в системе, в режиме "имитация".</span><span class="sxs-lookup"><span data-stu-id="890db-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="890db-351">Сначала будет отправлен заголовок простого дескриптора формата, а затем H. 264-Encoded текстуры, в каждой из которых предшествует заголовок, указывающий индекс глаза и размер текстуры.</span><span class="sxs-lookup"><span data-stu-id="890db-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="890db-352">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="890db-352">Perception Simulation Playback</span></span>

<span data-ttu-id="890db-353">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="890db-354">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="890db-354">Delete a recording.</span></span>

<span data-ttu-id="890db-355">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-355">Parameters</span></span>
* <span data-ttu-id="890db-356">запись: имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="890db-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="890db-357">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="890db-358">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="890db-358">Upload a recording.</span></span>

<span data-ttu-id="890db-359">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="890db-360">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="890db-360">Get all recordings.</span></span>

<span data-ttu-id="890db-361">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="890db-362">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="890db-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="890db-363">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-363">Parameters</span></span>
* <span data-ttu-id="890db-364">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-364">recording : Name of recording.</span></span>

<span data-ttu-id="890db-365">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="890db-366">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="890db-366">Unload a recording.</span></span>

<span data-ttu-id="890db-367">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-367">Parameters</span></span>
* <span data-ttu-id="890db-368">запись: имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="890db-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="890db-369">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="890db-370">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="890db-370">Load a recording.</span></span>

<span data-ttu-id="890db-371">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-371">Parameters</span></span>
* <span data-ttu-id="890db-372">запись: имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="890db-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="890db-373">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="890db-374">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="890db-374">Get all loaded recordings.</span></span>

<span data-ttu-id="890db-375">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="890db-376">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="890db-376">Pause a recording.</span></span>

<span data-ttu-id="890db-377">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-377">Parameters</span></span>
* <span data-ttu-id="890db-378">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-378">recording : Name of recording.</span></span>

<span data-ttu-id="890db-379">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="890db-380">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="890db-380">Play a recording.</span></span>

<span data-ttu-id="890db-381">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-381">Parameters</span></span>
* <span data-ttu-id="890db-382">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-382">recording : Name of recording.</span></span>

<span data-ttu-id="890db-383">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="890db-384">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="890db-384">Stop a recording.</span></span>

<span data-ttu-id="890db-385">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-385">Parameters</span></span>
* <span data-ttu-id="890db-386">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-386">recording : Name of recording.</span></span>

<span data-ttu-id="890db-387">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="890db-388">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="890db-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="890db-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-389">Parameters</span></span>
* <span data-ttu-id="890db-390">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="890db-391">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="890db-391">Perception Simulation Recording</span></span>

<span data-ttu-id="890db-392">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="890db-393">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="890db-393">Start a recording.</span></span> <span data-ttu-id="890db-394">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="890db-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="890db-395">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="890db-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="890db-396">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-396">Parameters</span></span>
* <span data-ttu-id="890db-397">Head: задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="890db-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="890db-398">стрелки: значение 1, чтобы записать данные.</span><span class="sxs-lookup"><span data-stu-id="890db-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="890db-399">Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="890db-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="890db-400">окружение: задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="890db-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="890db-401">имя. имя записи.</span><span class="sxs-lookup"><span data-stu-id="890db-401">name : Name of the recording.</span></span>
* <span data-ttu-id="890db-402">Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="890db-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="890db-403">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="890db-404">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="890db-404">Get recording state.</span></span>

<span data-ttu-id="890db-405">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="890db-406">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="890db-406">Stop the current recording.</span></span> <span data-ttu-id="890db-407">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="890db-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="890db-408">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="890db-408">Performance data</span></span>

<span data-ttu-id="890db-409">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="890db-410">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="890db-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="890db-411">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-411">Return data</span></span>
* <span data-ttu-id="890db-412">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="890db-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="890db-413">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="890db-414">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="890db-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="890db-415">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-415">Return data</span></span>
* <span data-ttu-id="890db-416">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="890db-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="890db-417">Питание</span><span class="sxs-lookup"><span data-stu-id="890db-417">Power</span></span>

<span data-ttu-id="890db-418">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="890db-419">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="890db-419">Gets the current battery state</span></span>

<span data-ttu-id="890db-420">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="890db-421">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="890db-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="890db-422">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="890db-422">Remote Control</span></span>

<span data-ttu-id="890db-423">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="890db-424">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="890db-424">Restarts the target device</span></span>

<span data-ttu-id="890db-425">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="890db-426">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="890db-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="890db-427">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="890db-427">Task Manager</span></span>

<span data-ttu-id="890db-428">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="890db-429">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="890db-429">Stops a modern app</span></span>

<span data-ttu-id="890db-430">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-430">Parameters</span></span>
* <span data-ttu-id="890db-431">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="890db-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="890db-432">форцестоп: принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="890db-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="890db-433">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="890db-434">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="890db-434">Starts a modern app</span></span>

<span data-ttu-id="890db-435">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-435">Parameters</span></span>
* <span data-ttu-id="890db-436">AppID: ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="890db-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="890db-437">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="890db-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="890db-438">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="890db-438">WiFi Management</span></span>

<span data-ttu-id="890db-439">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="890db-440">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="890db-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="890db-441">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-441">Return data</span></span>
* <span data-ttu-id="890db-442">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="890db-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="890db-443">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="890db-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="890db-444">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="890db-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="890db-445">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-445">Parameters</span></span>
* <span data-ttu-id="890db-446">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="890db-446">interface : network interface guid</span></span>
* <span data-ttu-id="890db-447">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="890db-447">profile : profile name</span></span>

<span data-ttu-id="890db-448">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="890db-449">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="890db-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="890db-450">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-450">Parameters</span></span>
* <span data-ttu-id="890db-451">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="890db-451">interface : network interface guid</span></span>

<span data-ttu-id="890db-452">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-452">Return data</span></span>
* <span data-ttu-id="890db-453">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="890db-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="890db-454">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="890db-455">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="890db-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="890db-456">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-456">Parameters</span></span>
* <span data-ttu-id="890db-457">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="890db-457">interface : network interface guid</span></span>
* <span data-ttu-id="890db-458">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="890db-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="890db-459">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="890db-459">op : connect or disconnect</span></span>
* <span data-ttu-id="890db-460">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="890db-460">createprofile : yes or no</span></span>
* <span data-ttu-id="890db-461">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="890db-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="890db-462">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="890db-462">Windows Performance Recorder</span></span>

<span data-ttu-id="890db-463">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="890db-464">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="890db-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="890db-465">Payload</span><span class="sxs-lookup"><span data-stu-id="890db-465">Payload</span></span>
* <span data-ttu-id="890db-466">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="890db-466">multi-part conforming http body</span></span>

<span data-ttu-id="890db-467">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-467">Return data</span></span>
* <span data-ttu-id="890db-468">Возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="890db-468">Returns the WPR session status.</span></span>

<span data-ttu-id="890db-469">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="890db-470">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="890db-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="890db-471">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-471">Return data</span></span>
* <span data-ttu-id="890db-472">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="890db-472">WPR session status.</span></span>

<span data-ttu-id="890db-473">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="890db-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="890db-474">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="890db-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="890db-475">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-475">Return data</span></span>
* <span data-ttu-id="890db-476">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="890db-476">Returns the trace ETL file</span></span>

<span data-ttu-id="890db-477">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="890db-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="890db-478">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="890db-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="890db-479">Параметры</span><span class="sxs-lookup"><span data-stu-id="890db-479">Parameters</span></span>
* <span data-ttu-id="890db-480">Профиль: имя профиля.</span><span class="sxs-lookup"><span data-stu-id="890db-480">profile : Profile name.</span></span> <span data-ttu-id="890db-481">Доступные профили хранятся в перфпрофилес/profiles.jsна</span><span class="sxs-lookup"><span data-stu-id="890db-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="890db-482">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="890db-482">Return data</span></span>
* <span data-ttu-id="890db-483">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="890db-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="890db-484">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="890db-484">See also</span></span>
* [<span data-ttu-id="890db-485">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="890db-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="890db-486">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="890db-486">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
