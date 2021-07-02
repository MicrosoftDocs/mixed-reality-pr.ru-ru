---
title: Использование диспетчера пакетов Unity
description: использование мртк в Unity диспетчер пакетов
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк пакеты,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177321"
---
# <a name="using-the-unity-package-manager"></a>Использование диспетчера пакетов Unity

начиная с версии 2.5.0, используя [средство "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)", набор средств Microsoft Mixed reality интегрируется с диспетчер пакетов unity (упм) при использовании unity 2019,4 и более поздних версий.

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

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>управление функциями смешанной реальности с помощью Unity диспетчер пакетов

после добавления пакета набор средств смешанной реальности в манифест пакета можно управлять им с помощью пользовательского интерфейса Unity диспетчер пакетов.

![Пакет УПМ МРТК Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> если пакет набор средств смешанной реальности удаляется с помощью диспетчер пакетов Unity, его необходимо добавить повторно с помощью [описанных выше действий](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>примеры использования смешанной реальности набор средств

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

## <a name="see-also"></a>См. также:

- [пакеты набор средств смешанной реальности](../packages/mrtk-packages.md)
