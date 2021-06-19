---
title: Выбор конвейера разработчика
description: Оставайтесь в курсе последних рекомендаций по конвейерам разработки Unity для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394558"
---
# <a name="choosing-your-developer-pipeline"></a>Выбор конвейера разработчика

![Баннер с логотипом Unity](../images/unity_logo_banner.png)<br>

В настоящее время мы **рекомендуем установить Unity 2019,4 LTS и использовать устаревшие встроенные XR** для разработки смешанной реальности. Кроме того, вы можете создавать приложения с другими конфигурациями Unity.

## <a name="mixed-reality-toolkit-recommended"></a>Набор средств для смешанной реальности (рекомендуется)

Текущая Рекомендуемая конфигурация Unity корпорации Майкрософт для HoloLens 2 — это набор средств Mixed Reality...

### <a name="install-the-mixed-reality-feature-tool"></a>Установка средства "функция смешанной реальности"

Средство [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) предоставляет новый способ для обнаружения и добавления пакетов функций смешанной реальности в проекты Unity. 

Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом. Когда вы подтвердите список нужных пакетов, средство Mixed Reality Feature Tool скачает их в выбранный вами проект.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Импорт набора средств Mixed Reality для Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

[Набор средств для смешанной реальности](mrtk-getting-started.md) (MRTK) — это кросс-платформенный пакет разработки с открытым кодом для приложений смешанной реальности. 

* Установите пакет Mixed Reality Toolkit, следуя [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md#system-requirements), и выберите пакет **Mixed Reality Toolkit Foundation**.

Мы рекомендуем изучить раздел по началу работы, следуя нашим курируемым этапам разработки для[HoloLens](unity-development-overview.md#1-getting-started) или [виртуальной реальности](unity-development-wmr-overview.md#1-getting-started). Если вы уже работаете с этими этапами, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Обратите внимание, что инструкции по установке приведены для последнего стабильного сочетания выпусков MRTK и Unity — **MRTK 2.6.1** и **Unity 2019.4 LTS**.

> [!NOTE]
> Если вы не хотите использовать MRTK для Unity, вам придется [самостоятельно написать скрипты для всех взаимодействий и моделей поведения](configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Баннер Unity](../images/MRTK-Unity-Banner.png)<br>**Набор средств для смешанной реальности — Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>Вручную 

Подлежит уточнению...