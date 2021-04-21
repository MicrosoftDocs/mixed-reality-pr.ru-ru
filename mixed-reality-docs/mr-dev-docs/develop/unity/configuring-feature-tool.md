---
title: Настройка Mixed Reality Feature Tool
description: Узнайте, как скачать и установить пакеты Unity для смешанной реальности с помощью Mixed Reality Feature Tool для разработки решений для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731953"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="f0b3c-104">Настройка Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="f0b3c-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="f0b3c-105">При использовании Mixed Reality Feature Tool у вас есть доступ к трем разным категориям параметров, которые вы можете настроить по своему усмотрению:</span><span class="sxs-lookup"><span data-stu-id="f0b3c-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* <span data-ttu-id="f0b3c-106">[параметры скачивания](#download-settings);</span><span class="sxs-lookup"><span data-stu-id="f0b3c-106">[Download settings](#download-settings)</span></span>
* <span data-ttu-id="f0b3c-107">[параметры функций](#feature-settings);</span><span class="sxs-lookup"><span data-stu-id="f0b3c-107">[Feature settings](#feature-settings)</span></span>
* [<span data-ttu-id="f0b3c-108">Импорт параметров</span><span class="sxs-lookup"><span data-stu-id="f0b3c-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="f0b3c-109">Параметры скачивания</span><span class="sxs-lookup"><span data-stu-id="f0b3c-109">Download settings</span></span>

![Параметры скачивания](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="f0b3c-111">Перезаписать существующие файлы пакетов</span><span class="sxs-lookup"><span data-stu-id="f0b3c-111">Overwrite existing package files</span></span>

<span data-ttu-id="f0b3c-112">Включение этого параметра означает, что файлы пакетов будут скачиваться при каждом получении.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="f0b3c-113">**Мы рекомендуем отключить этот параметр, чтобы сократить потребление пропускной способности сети.**</span><span class="sxs-lookup"><span data-stu-id="f0b3c-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="f0b3c-114">По умолчанию ранее приобретенные файлы пакетов повторно не скачиваются.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="f0b3c-115">Package cache (Кэш пакетов)</span><span class="sxs-lookup"><span data-stu-id="f0b3c-115">Package cache</span></span>

<span data-ttu-id="f0b3c-116">Измените этот параметр, чтобы указать расположение для размещения скачанных пакетов компонентов.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b3c-117">Этот параметр в текущем выпуске доступен **только для чтения**.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="f0b3c-118">В будущих выпусках он может стать доступным для настройки.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="f0b3c-119">Параметры функций</span><span class="sxs-lookup"><span data-stu-id="f0b3c-119">Feature settings</span></span>

![Параметры функций](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="f0b3c-121">Показывать предварительные выпуски</span><span class="sxs-lookup"><span data-stu-id="f0b3c-121">Show preview releases</span></span>

<span data-ttu-id="f0b3c-122">Включите этот параметр, чтобы получать предварительные выпуски.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="f0b3c-123">По умолчанию предварительные выпуски не отображаются в Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="f0b3c-124">Предварительным считается любой выпуск, у которого в версии пакета указано **-preview**.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="f0b3c-125">Показывать компоненты в программе раннего доступа</span><span class="sxs-lookup"><span data-stu-id="f0b3c-125">Show early access program features</span></span>

<span data-ttu-id="f0b3c-126">Включите этот параметр, чтобы получать компоненты из зарегистрированных выпусков программ раннего доступа.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="f0b3c-127">По умолчанию компоненты в раннем доступе не отображаются в Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="f0b3c-128">Если включить `Show early access program features` без `Show preview releases`, это может привести к тому, что пакеты раннего доступа не будут отображаться на странице "Обнаружение".</span><span class="sxs-lookup"><span data-stu-id="f0b3c-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="f0b3c-129">Импорт параметров</span><span class="sxs-lookup"><span data-stu-id="f0b3c-129">Import settings</span></span>

![Импорт параметров](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="f0b3c-131">Replace existing package files (Заменять существующие файлы пакетов)</span><span class="sxs-lookup"><span data-stu-id="f0b3c-131">Replace existing package files</span></span>

<span data-ttu-id="f0b3c-132">По умолчанию Mixed Reality Feature Tool удаляет предыдущие копии импортируемых пакетов, чтобы уменьшить размер файла и не выполнять ненужные вычисления.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="f0b3c-133">Снимите этот флажок, чтобы сохранять все версии.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="f0b3c-134">Project relative import path (Относительный путь импорта проекта)</span><span class="sxs-lookup"><span data-stu-id="f0b3c-134">Project relative import path</span></span>

<span data-ttu-id="f0b3c-135">Измените этот параметр, чтобы указать путь к папке проекта, в которую будут копироваться пакеты компонентов при импорте.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="f0b3c-136">Например, если используется папка проекта **C:\GalaxyExplorer**, полный путь для этого параметра будет **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b3c-137">Этот параметр в текущем выпуске доступен **только для чтения**.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="f0b3c-138">В будущих выпусках он может стать доступным для настройки.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="f0b3c-139">Параметры раннего доступа</span><span class="sxs-lookup"><span data-stu-id="f0b3c-139">Early Access settings</span></span>

![Параметры раннего доступа](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="f0b3c-141">Запрашивать подтверждение до удаления программы раннего доступа</span><span class="sxs-lookup"><span data-stu-id="f0b3c-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="f0b3c-142">Этот параметр определяет, будет ли отображаться запрос при каждом удалении программы раннего доступа.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="f0b3c-143">Мои предварительные версии</span><span class="sxs-lookup"><span data-stu-id="f0b3c-143">My previews</span></span>

<span data-ttu-id="f0b3c-144">Список зарегистрированных программ раннего доступа.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-144">The list of registered early access programs.</span></span> <span data-ttu-id="f0b3c-145">Используйте `Add`, `Edit` и `Remove` для управления коллекцией зарегистрированных программ.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="f0b3c-146">Параметры диагностики</span><span class="sxs-lookup"><span data-stu-id="f0b3c-146">Diagnostic settings</span></span>

![Параметры диагностики](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="f0b3c-148">Файл журнала</span><span class="sxs-lookup"><span data-stu-id="f0b3c-148">Log file</span></span>

<span data-ttu-id="f0b3c-149">Отображает путь к файлу журнала диагностики.</span><span class="sxs-lookup"><span data-stu-id="f0b3c-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0b3c-150">См. также</span><span class="sxs-lookup"><span data-stu-id="f0b3c-150">See also</span></span>

- [<span data-ttu-id="f0b3c-151">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="f0b3c-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)