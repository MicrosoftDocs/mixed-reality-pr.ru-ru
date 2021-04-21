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
# <a name="configuring-the-mixed-reality-feature-tool"></a>Настройка Mixed Reality Feature Tool

При использовании Mixed Reality Feature Tool у вас есть доступ к трем разным категориям параметров, которые вы можете настроить по своему усмотрению:

* [параметры скачивания](#download-settings);
* [параметры функций](#feature-settings);
* [Импорт параметров](#import-settings)

## <a name="download-settings"></a>Параметры скачивания

![Параметры скачивания](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Перезаписать существующие файлы пакетов

Включение этого параметра означает, что файлы пакетов будут скачиваться при каждом получении. 

* **Мы рекомендуем отключить этот параметр, чтобы сократить потребление пропускной способности сети.**
* По умолчанию ранее приобретенные файлы пакетов повторно не скачиваются.

### <a name="package-cache"></a>Package cache (Кэш пакетов)

Измените этот параметр, чтобы указать расположение для размещения скачанных пакетов компонентов.

> [!NOTE]
> Этот параметр в текущем выпуске доступен **только для чтения**. В будущих выпусках он может стать доступным для настройки.

## <a name="feature-settings"></a>Параметры функций

![Параметры функций](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Показывать предварительные выпуски

Включите этот параметр, чтобы получать предварительные выпуски.
* По умолчанию предварительные выпуски не отображаются в Mixed Reality Feature Tool. 

> [!NOTE]
> Предварительным считается любой выпуск, у которого в версии пакета указано **-preview**.

### <a name="show-early-access-program-features"></a>Показывать компоненты в программе раннего доступа

Включите этот параметр, чтобы получать компоненты из зарегистрированных выпусков программ раннего доступа.

* По умолчанию компоненты в раннем доступе не отображаются в Mixed Reality Feature Tool. 

> [!NOTE]
> Если включить `Show early access program features` без `Show preview releases`, это может привести к тому, что пакеты раннего доступа не будут отображаться на странице "Обнаружение".

## <a name="import-settings"></a>Импорт параметров

![Импорт параметров](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Replace existing package files (Заменять существующие файлы пакетов)

По умолчанию Mixed Reality Feature Tool удаляет предыдущие копии импортируемых пакетов, чтобы уменьшить размер файла и не выполнять ненужные вычисления. 

* Снимите этот флажок, чтобы сохранять все версии.

### <a name="project-relative-import-path"></a>Project relative import path (Относительный путь импорта проекта)

Измените этот параметр, чтобы указать путь к папке проекта, в которую будут копироваться пакеты компонентов при импорте. 

* Например, если используется папка проекта **C:\GalaxyExplorer**, полный путь для этого параметра будет **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Этот параметр в текущем выпуске доступен **только для чтения**. В будущих выпусках он может стать доступным для настройки.

## <a name="early-access-settings"></a>Параметры раннего доступа

![Параметры раннего доступа](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Запрашивать подтверждение до удаления программы раннего доступа

Этот параметр определяет, будет ли отображаться запрос при каждом удалении программы раннего доступа.

### <a name="my-previews"></a>Мои предварительные версии

Список зарегистрированных программ раннего доступа. Используйте `Add`, `Edit` и `Remove` для управления коллекцией зарегистрированных программ.

## <a name="diagnostic-settings"></a>Параметры диагностики

![Параметры диагностики](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>Файл журнала

Отображает путь к файлу журнала диагностики.

## <a name="see-also"></a>См. также

- [Вас приветствует Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)