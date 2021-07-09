---
title: Настройка проекта Unreal
description: Узнайте, как настроить проект с использованием последней версии Unreal Engine и средства Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, смешанная реальность, разработка, функции, новый проект, эмулятор, документация, руководства, голограммы, разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394616"
---
# <a name="setting-up-your-unreal-project"></a>Настройка проекта Unreal

Мы рекомендуем установить [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) или более поздней версии, чтобы воспользоваться всеми преимуществами встроенной поддержки HoloLens.

Перейдите на вкладку **Library** (Библиотека) в Epic Games Launcher. Щелкните стрелку раскрывающегося списка рядом с полем **Launch** (Запуск) и выберите **Options** (Параметры). В разделе **Target Platforms** (Целевые платформы) выберите элемент **HoloLens 2** и щелкните команду **Apply** (Применить).
![Параметр установки Unreal для HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Импорт набора средств для смешанной реальности для Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Набор средств для смешанной реальности (MRTK) — это кроссплатформенный пакет SDK с открытым кодом для приложений смешанной реальности. MRTK предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий. Набор используется для ускорения разработки приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.

Для выполнения установки мы рекомендуем изучить [раздел по началу работы](unreal-development-overview.md#1-getting-started) нашего [обзора разработки для Unreal](unreal-development-overview.md). Если вы уже работаете с этим обзором, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Изображение с логотипом Unity](../images/MRTK-Unreal-Banner.png)<br>**Набор средств для смешанной реальности — Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Если вы не хотите использовать MRTK для Unreal, вам придется самостоятельно написать скрипты для всех взаимодействий и моделей поведения.