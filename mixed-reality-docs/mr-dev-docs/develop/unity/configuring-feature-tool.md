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
# <a name="configuring-the-mixed-reality-feature-tool"></a>Настройка Mixed Reality Feature Tool

При использовании Mixed Reality Feature Tool у вас есть доступ к трем разным категориям параметров, которые вы можете настроить по своему усмотрению:

* [параметры скачивания](#download-settings);
* [параметры функций](#feature-settings);
* [Импорт параметров](#import-settings)

![Параметры](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Параметры скачивания

### <a name="overwrite-existing-package-files"></a>Перезаписать существующие файлы пакетов

Включение этого параметра означает, что файлы пакетов будут скачиваться при каждом получении. 
* **Мы рекомендуем отключить этот параметр, чтобы сократить потребление пропускной способности сети.**
* По умолчанию ранее приобретенные файлы пакетов повторно не скачиваются.

### <a name="package-cache"></a>Package cache (Кэш пакетов)

Измените этот параметр, чтобы указать расположение для размещения скачанных пакетов компонентов.

> [!NOTE]
> Этот параметр в текущем выпуске доступен **только для чтения**. В будущих выпусках он может стать доступным для настройки.

## <a name="feature-settings"></a>Параметры функций

### <a name="include-preview-releases"></a>Include preview releases (Включать предварительные выпуски)

Включите этот параметр, чтобы получать предварительные выпуски.
* По умолчанию предварительные выпуски не отображаются в Mixed Reality Feature Tool. 

> [!NOTE]
> Предварительным считается любой выпуск, у которого в версии пакета указано **-preview**.

## <a name="import-settings"></a>Импорт параметров

### <a name="replace-existing-package-files"></a>Replace existing package files (Заменять существующие файлы пакетов)

По умолчанию Mixed Reality Feature Tool удаляет предыдущие копии импортируемых пакетов, чтобы уменьшить размер файла и не выполнять ненужные вычисления. 
* Снимите этот флажок, чтобы сохранять все версии.

### <a name="project-relative-import-path"></a>Project relative import path (Относительный путь импорта проекта)

Измените этот параметр, чтобы указать путь к папке проекта, в которую будут копироваться пакеты компонентов при импорте. 
* Например, если используется папка проекта **C:\GalaxyExplorer**, полный путь для этого параметра будет **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Этот параметр в текущем выпуске доступен **только для чтения**. В будущих выпусках он может стать доступным для настройки.

## <a name="see-also"></a>См. также

- [Вас приветствует Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)