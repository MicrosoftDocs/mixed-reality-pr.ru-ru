---
title: Службы расширения
description: Документация по расширенным функциональным возможностям в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: a39616a091a3f6800c429dc797ec2f3130e96f40
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144547"
---
# <a name="extension-services"></a>Службы расширений

Службы расширения — это компоненты, расширяющие функциональные возможности набора средств Mixed Reality. Эти службы могут предоставляться МРТК или другими сторонами.

## <a name="creating-an-extension-service"></a>Создание службы расширений

Самый эффективный способ создать службу расширения — использовать [Мастер создания службы расширения](../tools/extension-service-creation-wizard.md).
Чтобы запустить мастер создания службы расширения, выберите **набор средств для смешанной реальности > служебные программы > создать службу расширения**.

![Мастер создания службы расширения](../images/extension-wizard/ExtensionServiceCreationWizard.png)

Мастер автоматизирует создание компонентов службы и обеспечивает правильное наследование интерфейса.

![Компоненты, созданные с помощью мастера создания службы расширений](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> В МРТК версии 2.0.0 существует ошибка в мастере службы расширений, где необходимо создать инспектор служб и профиль службы. Дополнительные сведения см. в описании проблемы [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .

По завершении работы мастера можно реализовать функциональность службы.

## <a name="registering-an-extension-service"></a>Регистрация службы расширений

Чтобы приложение было доступно для приложения, необходимо зарегистрировать новую службу расширения в наборе средств Mixed Reality.

Для регистрации службы можно использовать мастер создания службы расширения.

![Регистрация мастера создания службы расширения](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Службу также можно зарегистрировать вручную с помощью инспектора конфигурации набора средств для смешанной реальности.

![Регистрация службы расширения вручную](../images/profiles/RegisterExtensionService.png)

Если служба расширений использует профиль, убедитесь, что он указан в инспекторе.

![Настроенная служба расширений](../images/profiles/ConfiguredExtensionService.png)

Имя и приоритет компонента также можно изменить.

## <a name="accessing-an-extension-service"></a>Доступ к службе расширений

Доступ к службам расширений осуществляется в коде с использованием, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) как показано в примере ниже.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>См. также

- [Системы, службы расширений и поставщики данных](../../architecture/systems-extensions-providers.md)
- [Мастер создания службы расширения](../tools/extension-service-creation-wizard.md)
- [имикседреалитекстенсионсервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [микседреалитисервицерегистри](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
