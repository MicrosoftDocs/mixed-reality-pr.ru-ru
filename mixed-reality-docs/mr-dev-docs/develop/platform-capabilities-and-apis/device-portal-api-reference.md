---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: 6b8f99fbc6f1965639ceef218f5c516d2e6ba467
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691445"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="6877c-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="6877c-104">Device portal API reference</span></span>

<span data-ttu-id="6877c-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="6877c-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="6877c-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="6877c-106">App deloyment</span></span>

<span data-ttu-id="6877c-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="6877c-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="6877c-108">Uninstalls an app</span></span>

<span data-ttu-id="6877c-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-109">Parameters</span></span>
* <span data-ttu-id="6877c-110">Пакет: имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="6877c-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="6877c-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="6877c-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="6877c-112">Installs an App</span></span>

<span data-ttu-id="6877c-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-113">Parameters</span></span>
* <span data-ttu-id="6877c-114">Пакет: имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="6877c-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="6877c-115">Payload</span><span class="sxs-lookup"><span data-stu-id="6877c-115">Payload</span></span>
* <span data-ttu-id="6877c-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="6877c-116">multi-part conforming http body</span></span>

<span data-ttu-id="6877c-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="6877c-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="6877c-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="6877c-119">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-119">Return data</span></span>
* <span data-ttu-id="6877c-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="6877c-120">List of installed packages with details</span></span>

<span data-ttu-id="6877c-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="6877c-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="6877c-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="6877c-123">Дамп коллекции</span><span class="sxs-lookup"><span data-stu-id="6877c-123">Dump collection</span></span>

<span data-ttu-id="6877c-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="6877c-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="6877c-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-126">Parameters</span></span>
* <span data-ttu-id="6877c-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6877c-127">packageFullname : package name</span></span>

<span data-ttu-id="6877c-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="6877c-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="6877c-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-130">Parameters</span></span>
* <span data-ttu-id="6877c-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6877c-131">packageFullname : package name</span></span>

<span data-ttu-id="6877c-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="6877c-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="6877c-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-134">Parameters</span></span>
* <span data-ttu-id="6877c-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6877c-135">packageFullname : package name</span></span>

<span data-ttu-id="6877c-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="6877c-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6877c-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-138">Parameters</span></span>
* <span data-ttu-id="6877c-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6877c-139">packageFullname : package name</span></span>
* <span data-ttu-id="6877c-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="6877c-140">fileName : dump file name</span></span>

<span data-ttu-id="6877c-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="6877c-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6877c-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-143">Parameters</span></span>
* <span data-ttu-id="6877c-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6877c-144">packageFullname : package name</span></span>
* <span data-ttu-id="6877c-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="6877c-145">fileName : dump file name</span></span>

<span data-ttu-id="6877c-146">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-146">Return data</span></span>
* <span data-ttu-id="6877c-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="6877c-147">Dump file.</span></span> <span data-ttu-id="6877c-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6877c-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="6877c-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="6877c-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6877c-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="6877c-151">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-151">Return data</span></span>
* <span data-ttu-id="6877c-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="6877c-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="6877c-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="6877c-153">ETW</span></span>

<span data-ttu-id="6877c-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="6877c-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="6877c-155">Enumerates registered providers</span></span>

<span data-ttu-id="6877c-156">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-156">Return data</span></span>
* <span data-ttu-id="6877c-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="6877c-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="6877c-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6877c-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="6877c-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="6877c-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="6877c-160">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-160">Return data</span></span>
* <span data-ttu-id="6877c-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="6877c-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="6877c-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="6877c-162">Holographic OS</span></span>

<span data-ttu-id="6877c-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="6877c-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="6877c-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="6877c-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="6877c-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="6877c-166">Returns the states of all services running.</span></span>

<span data-ttu-id="6877c-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="6877c-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="6877c-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="6877c-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="6877c-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="6877c-170">Sets the IPD</span></span>

<span data-ttu-id="6877c-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-171">Parameters</span></span>
* <span data-ttu-id="6877c-172">IPD: новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="6877c-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="6877c-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="6877c-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="6877c-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6877c-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="6877c-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="6877c-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6877c-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-177">Parameters</span></span>
* <span data-ttu-id="6877c-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6877c-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="6877c-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="6877c-179">Holographic Perception</span></span>

<span data-ttu-id="6877c-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6877c-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="6877c-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="6877c-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="6877c-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-182">Parameters</span></span>
* <span data-ttu-id="6877c-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="6877c-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="6877c-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="6877c-184">Holographic Thermal</span></span>

<span data-ttu-id="6877c-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="6877c-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="6877c-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="6877c-187">Диспетчер карт</span><span class="sxs-lookup"><span data-stu-id="6877c-187">Map Manager</span></span>

<span data-ttu-id="6877c-188">**/АПИ/холографик/мапманажер/мапфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="6877c-189">Возвращает список доступных файлов карт (. мапкс).</span><span class="sxs-lookup"><span data-stu-id="6877c-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="6877c-190">**/АПИ/холографик/мапманажер/анчорфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="6877c-191">Возвращает список доступных файлов привязки (. анккс).</span><span class="sxs-lookup"><span data-stu-id="6877c-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="6877c-192">**/АПИ/холографик/мапманажер/срдбфилес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="6877c-193">Возвращает список доступных файлов базы данных пространственной реконструкции (. срдб).</span><span class="sxs-lookup"><span data-stu-id="6877c-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="6877c-194">**/АПИ/холографик/мапманажер/жетанчорс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="6877c-195">Возвращает список материализованных привязок для текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="6877c-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="6877c-196">Скачать, отправить или удалить файлы</span><span class="sxs-lookup"><span data-stu-id="6877c-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="6877c-197">**/АПИ/холографик/мапманажер/Довнлоад (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="6877c-198">Скачивает файл схемы, привязки или базы данных пространственного восстановления.</span><span class="sxs-lookup"><span data-stu-id="6877c-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="6877c-199">Файл должен быть предварительно отправлен или экспортирован.</span><span class="sxs-lookup"><span data-stu-id="6877c-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="6877c-200">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-200">Parameters</span></span>
* <span data-ttu-id="6877c-201">FileName: имя файла для скачивания.</span><span class="sxs-lookup"><span data-stu-id="6877c-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="6877c-202">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="6877c-203">**/АПИ/холографик/мапманажер/уплоад (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="6877c-204">Отправляет файл схемы, привязки или пространственной реконструкции базы данных.</span><span class="sxs-lookup"><span data-stu-id="6877c-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="6877c-205">После отправки файла его можно будет импортировать в систему в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="6877c-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="6877c-206">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-206">Parameters</span></span>
* <span data-ttu-id="6877c-207">файл: имя файла для отправки.</span><span class="sxs-lookup"><span data-stu-id="6877c-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="6877c-208">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-208">Example:</span></span>
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

<span data-ttu-id="6877c-209">**/АПИ/холографик/мапманажер/делете (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="6877c-210">Удаляет файл схемы, привязки или базы данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="6877c-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="6877c-211">Файл должен быть предварительно отправлен или экспортирован.</span><span class="sxs-lookup"><span data-stu-id="6877c-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="6877c-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-212">Parameters</span></span>
* <span data-ttu-id="6877c-213">FileName: имя удаляемого файла.</span><span class="sxs-lookup"><span data-stu-id="6877c-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="6877c-214">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="6877c-215">Экспорт</span><span class="sxs-lookup"><span data-stu-id="6877c-215">Export</span></span>

<span data-ttu-id="6877c-216">**/АПИ/холографик/мапманажер/експорт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="6877c-217">Экспортирует текущую карту, используемую системой.</span><span class="sxs-lookup"><span data-stu-id="6877c-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="6877c-218">После экспорта его можно скачать.</span><span class="sxs-lookup"><span data-stu-id="6877c-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="6877c-219">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="6877c-220">**/АПИ/холографик/мапманажер/експортанчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="6877c-221">Экспортирует текущую карту, используемую системой.</span><span class="sxs-lookup"><span data-stu-id="6877c-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="6877c-222">После экспорта его можно скачать.</span><span class="sxs-lookup"><span data-stu-id="6877c-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="6877c-223">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="6877c-224">**/АПИ/холографик/мапманажер/експортмапанданчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="6877c-225">Экспортирует карту и привязки, используемые системой в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="6877c-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="6877c-226">После экспорта их можно скачать.</span><span class="sxs-lookup"><span data-stu-id="6877c-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="6877c-227">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="6877c-228">**/АПИ/холографик/мапманажер/експортмапандспатиалмаппингдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="6877c-229">Экспортирует базу данных Map и spatial реконструкции, используемую системой в данный момент.</span><span class="sxs-lookup"><span data-stu-id="6877c-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="6877c-230">После экспорта их можно скачать.</span><span class="sxs-lookup"><span data-stu-id="6877c-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="6877c-231">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="6877c-232">Импортировать</span><span class="sxs-lookup"><span data-stu-id="6877c-232">Import</span></span>

<span data-ttu-id="6877c-233">**/АПИ/холографик/мапманажер/импорт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="6877c-234">Указывает системе, какую карту следует использовать в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="6877c-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="6877c-235">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="6877c-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="6877c-236">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-236">Parameters</span></span>
* <span data-ttu-id="6877c-237">FileName: имя используемой схемы.</span><span class="sxs-lookup"><span data-stu-id="6877c-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="6877c-238">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="6877c-239">**/АПИ/холографик/мапманажер/импортанчорс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="6877c-240">Указывает системе, какие привязки должны использоваться в текущий момент.</span><span class="sxs-lookup"><span data-stu-id="6877c-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="6877c-241">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="6877c-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="6877c-242">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-242">Parameters</span></span>
* <span data-ttu-id="6877c-243">FileName: имя используемых привязок.</span><span class="sxs-lookup"><span data-stu-id="6877c-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="6877c-244">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="6877c-245">**/АПИ/холографик/мапманажер/импортспатиалмаппингдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="6877c-246">Указывает на систему, в которой должна использоваться база данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="6877c-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="6877c-247">Может вызываться для файлов, которые были экспортированы или переданы.</span><span class="sxs-lookup"><span data-stu-id="6877c-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="6877c-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-248">Parameters</span></span>
* <span data-ttu-id="6877c-249">FileName: имя базы данных пространственного сопоставления, которая будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="6877c-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="6877c-250">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="6877c-251">Другое</span><span class="sxs-lookup"><span data-stu-id="6877c-251">Other</span></span>

<span data-ttu-id="6877c-252">**/АПИ/холографик/мапманажер/ресетмапанданчорсандсрдб (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="6877c-253">Сбросьте систему на карту, привязки и базу данных пространственной реконструкции.</span><span class="sxs-lookup"><span data-stu-id="6877c-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="6877c-254">Пример</span><span class="sxs-lookup"><span data-stu-id="6877c-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="6877c-255">**/АПИ/холографик/мапманажер/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="6877c-256">Возвращает состояние системы, включая данные о сопоставлении, привязках и базах данных пространственной реконструкции, которые были импортированы в последний раз.</span><span class="sxs-lookup"><span data-stu-id="6877c-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="6877c-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="6877c-257">Mixed Reality Capture</span></span>

<span data-ttu-id="6877c-258">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="6877c-259">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="6877c-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="6877c-260">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="6877c-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="6877c-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-261">Parameters</span></span>
* <span data-ttu-id="6877c-262">имя файла: имя, hex64 в кодировке для получаемого видео.</span><span class="sxs-lookup"><span data-stu-id="6877c-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="6877c-263">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="6877c-263">op : stream</span></span>

<span data-ttu-id="6877c-264">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="6877c-265">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="6877c-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="6877c-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-266">Parameters</span></span>
* <span data-ttu-id="6877c-267">filename: Name, hex64 Encoded (имя файла), которое нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="6877c-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="6877c-268">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="6877c-269">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="6877c-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="6877c-270">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="6877c-271">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="6877c-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="6877c-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-272">Parameters</span></span>
* <span data-ttu-id="6877c-273">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-274">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-275">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6877c-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="6877c-276">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="6877c-277">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6877c-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="6877c-278">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="6877c-279">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6877c-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="6877c-280">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="6877c-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="6877c-281">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="6877c-282">Возвращает состояние захвата смешанной реальности на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="6877c-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="6877c-283">***Ответ***</span><span class="sxs-lookup"><span data-stu-id="6877c-283">***Response***</span></span>

<span data-ttu-id="6877c-284">Ответ содержит свойство JSON, указывающее, записывается ли видео на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="6877c-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="6877c-285">**/АПИ/холографик/МРК/сумбнаил (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-285">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="6877c-286">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="6877c-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="6877c-287">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-287">Parameters</span></span>
* <span data-ttu-id="6877c-288">filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.</span><span class="sxs-lookup"><span data-stu-id="6877c-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="6877c-289">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="6877c-290">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6877c-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="6877c-291">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-291">Parameters</span></span>
* <span data-ttu-id="6877c-292">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-293">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-294">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-295">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-296">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6877c-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6877c-297">встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6877c-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="6877c-298">встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="6877c-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6877c-299">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="6877c-300">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6877c-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="6877c-301">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6877c-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="6877c-302">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="6877c-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="6877c-303">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="6877c-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="6877c-304">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="6877c-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="6877c-305">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="6877c-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="6877c-306">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="6877c-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="6877c-307">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="6877c-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="6877c-308">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="6877c-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="6877c-309">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="6877c-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="6877c-310">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="6877c-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="6877c-311">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6877c-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6877c-312">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6877c-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="6877c-313">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="6877c-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6877c-314">**live.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="6877c-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="6877c-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6877c-316">**live_high.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="6877c-317">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="6877c-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6877c-318">**live_med.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="6877c-319">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="6877c-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="6877c-320">**live_low.mp4/АПИ/холографик/стреам/(GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="6877c-321">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="6877c-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="6877c-322">Сеть</span><span class="sxs-lookup"><span data-stu-id="6877c-322">Networking</span></span>

<span data-ttu-id="6877c-323">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="6877c-324">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="6877c-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="6877c-325">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="6877c-325">OS Information</span></span>

<span data-ttu-id="6877c-326">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="6877c-327">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="6877c-327">Gets operating system information</span></span>

<span data-ttu-id="6877c-328">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="6877c-329">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="6877c-329">Gets the machine name</span></span>

<span data-ttu-id="6877c-330">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="6877c-331">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="6877c-331">Sets the machine name</span></span>

<span data-ttu-id="6877c-332">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-332">Parameters</span></span>
* <span data-ttu-id="6877c-333">Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="6877c-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="6877c-334">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="6877c-334">Perception Simulation Control</span></span>

<span data-ttu-id="6877c-335">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="6877c-336">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="6877c-336">Get the simulation mode</span></span>

<span data-ttu-id="6877c-337">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="6877c-338">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="6877c-338">Set the simulation mode</span></span>

<span data-ttu-id="6877c-339">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-339">Parameters</span></span>
* <span data-ttu-id="6877c-340">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="6877c-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="6877c-341">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="6877c-342">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="6877c-342">Delete a control stream.</span></span>

<span data-ttu-id="6877c-343">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6877c-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6877c-344">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="6877c-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="6877c-345">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="6877c-346">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="6877c-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="6877c-347">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="6877c-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="6877c-348">**/АПИ/холографик/симулатион/дисплай/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6877c-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6877c-349">Запросите поток видео имитации, содержащий содержимое, отображаемое для отображения в системе, в режиме "имитация".</span><span class="sxs-lookup"><span data-stu-id="6877c-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="6877c-350">Сначала будет отправлен заголовок простого дескриптора формата, а затем H. 264-Encoded текстуры, в каждой из которых предшествует заголовок, указывающий индекс глаза и размер текстуры.</span><span class="sxs-lookup"><span data-stu-id="6877c-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="6877c-351">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="6877c-351">Perception Simulation Playback</span></span>

<span data-ttu-id="6877c-352">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="6877c-353">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-353">Delete a recording.</span></span>

<span data-ttu-id="6877c-354">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-354">Parameters</span></span>
* <span data-ttu-id="6877c-355">запись: имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="6877c-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="6877c-356">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="6877c-357">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-357">Upload a recording.</span></span>

<span data-ttu-id="6877c-358">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="6877c-359">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="6877c-359">Get all recordings.</span></span>

<span data-ttu-id="6877c-360">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="6877c-361">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="6877c-362">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-362">Parameters</span></span>
* <span data-ttu-id="6877c-363">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-363">recording : Name of recording.</span></span>

<span data-ttu-id="6877c-364">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="6877c-365">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-365">Unload a recording.</span></span>

<span data-ttu-id="6877c-366">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-366">Parameters</span></span>
* <span data-ttu-id="6877c-367">запись: имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="6877c-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="6877c-368">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="6877c-369">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-369">Load a recording.</span></span>

<span data-ttu-id="6877c-370">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-370">Parameters</span></span>
* <span data-ttu-id="6877c-371">запись: имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="6877c-372">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="6877c-373">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="6877c-373">Get all loaded recordings.</span></span>

<span data-ttu-id="6877c-374">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="6877c-375">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-375">Pause a recording.</span></span>

<span data-ttu-id="6877c-376">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-376">Parameters</span></span>
* <span data-ttu-id="6877c-377">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-377">recording : Name of recording.</span></span>

<span data-ttu-id="6877c-378">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="6877c-379">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-379">Play a recording.</span></span>

<span data-ttu-id="6877c-380">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-380">Parameters</span></span>
* <span data-ttu-id="6877c-381">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-381">recording : Name of recording.</span></span>

<span data-ttu-id="6877c-382">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="6877c-383">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-383">Stop a recording.</span></span>

<span data-ttu-id="6877c-384">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-384">Parameters</span></span>
* <span data-ttu-id="6877c-385">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-385">recording : Name of recording.</span></span>

<span data-ttu-id="6877c-386">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="6877c-387">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="6877c-388">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-388">Parameters</span></span>
* <span data-ttu-id="6877c-389">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="6877c-390">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="6877c-390">Perception Simulation Recording</span></span>

<span data-ttu-id="6877c-391">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="6877c-392">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-392">Start a recording.</span></span> <span data-ttu-id="6877c-393">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="6877c-394">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="6877c-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="6877c-395">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-395">Parameters</span></span>
* <span data-ttu-id="6877c-396">Head: задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="6877c-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="6877c-397">стрелки: значение 1, чтобы записать данные.</span><span class="sxs-lookup"><span data-stu-id="6877c-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="6877c-398">Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="6877c-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="6877c-399">окружение: задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="6877c-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="6877c-400">имя. имя записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-400">name : Name of the recording.</span></span>
* <span data-ttu-id="6877c-401">Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="6877c-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="6877c-402">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="6877c-403">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="6877c-403">Get recording state.</span></span>

<span data-ttu-id="6877c-404">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="6877c-405">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="6877c-405">Stop the current recording.</span></span> <span data-ttu-id="6877c-406">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="6877c-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="6877c-407">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="6877c-407">Performance data</span></span>

<span data-ttu-id="6877c-408">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="6877c-409">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="6877c-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="6877c-410">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-410">Return data</span></span>
* <span data-ttu-id="6877c-411">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="6877c-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="6877c-412">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="6877c-413">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="6877c-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="6877c-414">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-414">Return data</span></span>
* <span data-ttu-id="6877c-415">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="6877c-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="6877c-416">Питание</span><span class="sxs-lookup"><span data-stu-id="6877c-416">Power</span></span>

<span data-ttu-id="6877c-417">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="6877c-418">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="6877c-418">Gets the current battery state</span></span>

<span data-ttu-id="6877c-419">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="6877c-420">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="6877c-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="6877c-421">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="6877c-421">Remote Control</span></span>

<span data-ttu-id="6877c-422">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="6877c-423">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="6877c-423">Restarts the target device</span></span>

<span data-ttu-id="6877c-424">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="6877c-425">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="6877c-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="6877c-426">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="6877c-426">Task Manager</span></span>

<span data-ttu-id="6877c-427">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="6877c-428">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="6877c-428">Stops a modern app</span></span>

<span data-ttu-id="6877c-429">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-429">Parameters</span></span>
* <span data-ttu-id="6877c-430">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6877c-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="6877c-431">форцестоп: принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="6877c-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="6877c-432">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="6877c-433">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="6877c-433">Starts a modern app</span></span>

<span data-ttu-id="6877c-434">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-434">Parameters</span></span>
* <span data-ttu-id="6877c-435">AppID: ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6877c-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="6877c-436">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6877c-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="6877c-437">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="6877c-437">WiFi Management</span></span>

<span data-ttu-id="6877c-438">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="6877c-439">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="6877c-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="6877c-440">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-440">Return data</span></span>
* <span data-ttu-id="6877c-441">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="6877c-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="6877c-442">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6877c-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="6877c-443">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="6877c-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="6877c-444">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-444">Parameters</span></span>
* <span data-ttu-id="6877c-445">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6877c-445">interface : network interface guid</span></span>
* <span data-ttu-id="6877c-446">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="6877c-446">profile : profile name</span></span>

<span data-ttu-id="6877c-447">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="6877c-448">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="6877c-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="6877c-449">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-449">Parameters</span></span>
* <span data-ttu-id="6877c-450">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6877c-450">interface : network interface guid</span></span>

<span data-ttu-id="6877c-451">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-451">Return data</span></span>
* <span data-ttu-id="6877c-452">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="6877c-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="6877c-453">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="6877c-454">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="6877c-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="6877c-455">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-455">Parameters</span></span>
* <span data-ttu-id="6877c-456">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6877c-456">interface : network interface guid</span></span>
* <span data-ttu-id="6877c-457">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="6877c-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="6877c-458">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="6877c-458">op : connect or disconnect</span></span>
* <span data-ttu-id="6877c-459">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="6877c-459">createprofile : yes or no</span></span>
* <span data-ttu-id="6877c-460">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="6877c-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="6877c-461">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="6877c-461">Windows Performance Recorder</span></span>

<span data-ttu-id="6877c-462">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="6877c-463">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="6877c-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="6877c-464">Payload</span><span class="sxs-lookup"><span data-stu-id="6877c-464">Payload</span></span>
* <span data-ttu-id="6877c-465">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="6877c-465">multi-part conforming http body</span></span>

<span data-ttu-id="6877c-466">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-466">Return data</span></span>
* <span data-ttu-id="6877c-467">Возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6877c-467">Returns the WPR session status.</span></span>

<span data-ttu-id="6877c-468">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="6877c-469">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="6877c-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="6877c-470">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-470">Return data</span></span>
* <span data-ttu-id="6877c-471">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6877c-471">WPR session status.</span></span>

<span data-ttu-id="6877c-472">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="6877c-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="6877c-473">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="6877c-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="6877c-474">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-474">Return data</span></span>
* <span data-ttu-id="6877c-475">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="6877c-475">Returns the trace ETL file</span></span>

<span data-ttu-id="6877c-476">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="6877c-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="6877c-477">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="6877c-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="6877c-478">Параметры</span><span class="sxs-lookup"><span data-stu-id="6877c-478">Parameters</span></span>
* <span data-ttu-id="6877c-479">Профиль: имя профиля.</span><span class="sxs-lookup"><span data-stu-id="6877c-479">profile : Profile name.</span></span> <span data-ttu-id="6877c-480">Доступные профили хранятся в перфпрофилес/profiles.jsна</span><span class="sxs-lookup"><span data-stu-id="6877c-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="6877c-481">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6877c-481">Return data</span></span>
* <span data-ttu-id="6877c-482">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6877c-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="6877c-483">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6877c-483">See also</span></span>
* [<span data-ttu-id="6877c-484">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="6877c-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="6877c-485">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="6877c-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
