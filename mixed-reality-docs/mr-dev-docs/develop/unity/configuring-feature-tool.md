---
title: Настройка Mixed Reality Feature Tool
description: Узнайте, как скачать и установить пакеты Unity для смешанной реальности с помощью Mixed Reality Feature Tool для разработки решений для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244016"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="7ec28-104">Настройка Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="7ec28-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="7ec28-105">При использовании Mixed Reality Feature Tool у вас есть доступ к трем разным категориям параметров, которые вы можете настроить по своему усмотрению:</span><span class="sxs-lookup"><span data-stu-id="7ec28-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* <span data-ttu-id="7ec28-106">[параметры скачивания](#download-settings);</span><span class="sxs-lookup"><span data-stu-id="7ec28-106">[Download settings](#download-settings)</span></span>
* <span data-ttu-id="7ec28-107">[параметры функций](#feature-settings);</span><span class="sxs-lookup"><span data-stu-id="7ec28-107">[Feature settings](#feature-settings)</span></span>
* [<span data-ttu-id="7ec28-108">Импорт параметров</span><span class="sxs-lookup"><span data-stu-id="7ec28-108">Import settings</span></span>](#import-settings)

![Параметры](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="7ec28-110">Параметры скачивания</span><span class="sxs-lookup"><span data-stu-id="7ec28-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="7ec28-111">Перезаписать существующие файлы пакетов</span><span class="sxs-lookup"><span data-stu-id="7ec28-111">Overwrite existing package files</span></span>

<span data-ttu-id="7ec28-112">Включение этого параметра означает, что файлы пакетов будут скачиваться при каждом получении.</span><span class="sxs-lookup"><span data-stu-id="7ec28-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="7ec28-113">**Мы рекомендуем отключить этот параметр, чтобы сократить потребление пропускной способности сети.**</span><span class="sxs-lookup"><span data-stu-id="7ec28-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="7ec28-114">По умолчанию ранее приобретенные файлы пакетов повторно не скачиваются.</span><span class="sxs-lookup"><span data-stu-id="7ec28-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="7ec28-115">Package cache (Кэш пакетов)</span><span class="sxs-lookup"><span data-stu-id="7ec28-115">Package cache</span></span>

<span data-ttu-id="7ec28-116">Измените этот параметр, чтобы указать расположение для размещения скачанных пакетов компонентов.</span><span class="sxs-lookup"><span data-stu-id="7ec28-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="7ec28-117">Этот параметр в текущем выпуске доступен **только для чтения**.</span><span class="sxs-lookup"><span data-stu-id="7ec28-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="7ec28-118">В будущих выпусках он может стать доступным для настройки.</span><span class="sxs-lookup"><span data-stu-id="7ec28-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="7ec28-119">Параметры функций</span><span class="sxs-lookup"><span data-stu-id="7ec28-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="7ec28-120">Include preview releases (Включать предварительные выпуски)</span><span class="sxs-lookup"><span data-stu-id="7ec28-120">Include preview releases</span></span>

<span data-ttu-id="7ec28-121">Включите этот параметр, чтобы получать предварительные выпуски.</span><span class="sxs-lookup"><span data-stu-id="7ec28-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="7ec28-122">По умолчанию предварительные выпуски не отображаются в Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="7ec28-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="7ec28-123">Предварительным считается любой выпуск, у которого в версии пакета указано **-preview**.</span><span class="sxs-lookup"><span data-stu-id="7ec28-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="7ec28-124">Импорт параметров</span><span class="sxs-lookup"><span data-stu-id="7ec28-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="7ec28-125">Replace existing package files (Заменять существующие файлы пакетов)</span><span class="sxs-lookup"><span data-stu-id="7ec28-125">Replace existing package files</span></span>

<span data-ttu-id="7ec28-126">По умолчанию Mixed Reality Feature Tool удаляет предыдущие копии импортируемых пакетов, чтобы уменьшить размер файла и не выполнять ненужные вычисления.</span><span class="sxs-lookup"><span data-stu-id="7ec28-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="7ec28-127">Снимите этот флажок, чтобы сохранять все версии.</span><span class="sxs-lookup"><span data-stu-id="7ec28-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="7ec28-128">Project relative import path (Относительный путь импорта проекта)</span><span class="sxs-lookup"><span data-stu-id="7ec28-128">Project relative import path</span></span>

<span data-ttu-id="7ec28-129">Измените этот параметр, чтобы указать путь к папке проекта, в которую будут копироваться пакеты компонентов при импорте.</span><span class="sxs-lookup"><span data-stu-id="7ec28-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="7ec28-130">Например, если используется папка проекта **C:\GalaxyExplorer**, полный путь для этого параметра будет **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="7ec28-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="7ec28-131">Этот параметр в текущем выпуске доступен **только для чтения**.</span><span class="sxs-lookup"><span data-stu-id="7ec28-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="7ec28-132">В будущих выпусках он может стать доступным для настройки.</span><span class="sxs-lookup"><span data-stu-id="7ec28-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ec28-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7ec28-133">See also</span></span>

- [<span data-ttu-id="7ec28-134">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="7ec28-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)