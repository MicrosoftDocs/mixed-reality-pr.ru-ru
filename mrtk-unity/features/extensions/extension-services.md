---
title: Службы расширения
description: Документация по расширенным функциональным возможностям в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187000"
---
# <a name="extension-services"></a>Службы расширения

службы расширения — это компоненты, расширяющие функциональные возможности набор средств смешанной реальности. Эти службы могут предоставляться МРТК или другими сторонами.

## <a name="creating-an-extension-service"></a>Создание службы расширений

Самый эффективный способ создать службу расширения — использовать [Мастер создания службы расширения](../tools/extension-service-creation-wizard.md).
чтобы запустить мастер создания службы расширений, выберите **смешанная реальность набор средств > служебные программы > создать службу расширения**.

![Мастер создания службы расширений](../images/extension-wizard/ExtensionServiceCreationWizard.png)

Мастер автоматизирует создание компонентов службы и обеспечивает правильное наследование интерфейса.

![Компоненты, созданные с помощью мастера создания службы расширений](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> В МРТК версии 2.0.0 существует ошибка в мастере службы расширений, где необходимо создать инспектор служб и профиль службы. Дополнительные сведения см. в описании проблемы [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .

По завершении работы мастера можно реализовать функциональность службы.

## <a name="registering-an-extension-service"></a>Регистрация службы расширений

чтобы приложение было доступно для приложения, необходимо зарегистрировать новую службу расширения в набор средств смешанной реальности.

Для регистрации службы можно использовать мастер создания службы расширения.

![Регистрация мастера создания службы расширения](../images/extension-wizard/ExtensionServiceWizardRegister.png)

службу также можно зарегистрировать вручную с помощью инспектора конфигурации набор средств смешанной реальности.

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
- [Мастер создания службы расширений](../tools/extension-service-creation-wizard.md)
- [имикседреалитекстенсионсервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [микседреалитисервицерегистри](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
