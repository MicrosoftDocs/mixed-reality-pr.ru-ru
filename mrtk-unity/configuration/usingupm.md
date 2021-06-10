---
title: Использование диспетчера пакетов Unity
description: Использование МРТК в диспетчере пакетов Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК пакеты,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345077"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Набор средств для смешанной реальности и диспетчер пакетов Unity

Начиная с версии 2.5.0, с помощью [средства смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)набор средств Microsoft Mixed Reality интегрируется с диспетчером пакетов Unity (УПМ) при использовании Unity 2019,4 и более поздних версий.

## <a name="using-the-mixed-reality-feature-tool"></a>Использование Mixed Reality Feature Tool

Как описано в разделе [Добро пожаловать в средство "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ", можно скачать средство с помощью [этой ссылки](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Если манифест проекта содержит `Microsoft Mixed Reality` запись в `scopedRegistries` разделе, рекомендуется удалить его.
>
> Чтобы удалить настроенный реестр с заданной областью, перейдите по адресу `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Удаление реестра с заданной областью](../features/images/packaging/RemoveScopedRegistry.png)

Пакеты МРТК отображаются под `Mixed Reality Toolkit` заголовком при обнаружении компонентов.

![Поиск компонентов](../features/images/packaging/DiscoverFeatures.png)

При выборе компонентов нет нужды беспокоиться о необходимых зависимостях, средство автоматически скачивает и интегрирует их в проект.

![Необходимые зависимости](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Управление функциями смешанной реальности с помощью диспетчера пакетов Unity

После добавления пакета набора средств Mixed Reality в манифест пакета его можно управлять с помощью пользовательского интерфейса диспетчера пакетов Unity.

![Пакет УПМ МРТК Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Если пакет набора средств для смешанной реальности удаляется с помощью диспетчера пакетов Unity, его необходимо добавить повторно с помощью [описанных выше действий](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>Примеры использования набора средств для смешанной реальности

В отличие от использования файлов пакета ресурсов (. пакет unitypackage) `com.microsoft.mixedreality.toolkit.examples` и `com.microsoft.mixedreality.toolkit.handphysicsservice` не импортируйте примеры сцен и ресурсов автоматически.

Чтобы использовать один или несколько примеров, выполните следующие действия.

1. В редакторе Unity перейдите к `Window` > `Package Manager`
1. В списке пакетов выберите `Mixed Reality Toolkit Examples`
1. Расположение нужных примеров в `Samples` списке
1. Щелкните `Import into Project`.

![Импорт примеров](../features/images/packaging/MRTK_ExamplesUpm.png)

При обновлении примера пакета Unity предоставляет возможность обновления импортированных образцов.

> [!NOTE]
> При обновлении импортированного образца будут перезаписаны все изменения, внесенные в этот образец и связанные ресурсы.

## <a name="see-also"></a>См. также

- [Пакеты набора средств для смешанной реальности](../packages/mrtk-packages.md)