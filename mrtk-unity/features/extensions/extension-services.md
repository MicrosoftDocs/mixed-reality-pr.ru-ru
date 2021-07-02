---
title: Службы расширений
description: Документация по расширенным функциональным возможностям в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176277"
---
# <a name="extension-services"></a><span data-ttu-id="f6e00-104">Службы расширений</span><span class="sxs-lookup"><span data-stu-id="f6e00-104">Extension services</span></span>

<span data-ttu-id="f6e00-105">службы расширения — это компоненты, расширяющие функциональные возможности набор средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f6e00-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f6e00-106">Эти службы могут предоставляться МРТК или другими сторонами.</span><span class="sxs-lookup"><span data-stu-id="f6e00-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="f6e00-107">Создание службы расширений</span><span class="sxs-lookup"><span data-stu-id="f6e00-107">Creating an extension service</span></span>

<span data-ttu-id="f6e00-108">Самый эффективный способ создать службу расширения — использовать [Мастер создания службы расширения](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="f6e00-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="f6e00-109">чтобы запустить мастер создания службы расширений, выберите **смешанная реальность набор средств > служебные программы > создать службу расширения**.</span><span class="sxs-lookup"><span data-stu-id="f6e00-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Мастер создания службы расширения](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="f6e00-111">Мастер автоматизирует создание компонентов службы и обеспечивает правильное наследование интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f6e00-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Компоненты, созданные с помощью мастера создания службы расширений](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="f6e00-113">В МРТК версии 2.0.0 существует ошибка в мастере службы расширений, где необходимо создать инспектор служб и профиль службы.</span><span class="sxs-lookup"><span data-stu-id="f6e00-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="f6e00-114">Дополнительные сведения см. в описании проблемы [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .</span><span class="sxs-lookup"><span data-stu-id="f6e00-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="f6e00-115">По завершении работы мастера можно реализовать функциональность службы.</span><span class="sxs-lookup"><span data-stu-id="f6e00-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="f6e00-116">Регистрация службы расширений</span><span class="sxs-lookup"><span data-stu-id="f6e00-116">Registering an extension service</span></span>

<span data-ttu-id="f6e00-117">чтобы приложение было доступно для приложения, необходимо зарегистрировать новую службу расширения в набор средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f6e00-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="f6e00-118">Для регистрации службы можно использовать мастер создания службы расширения.</span><span class="sxs-lookup"><span data-stu-id="f6e00-118">The extension service creation wizard can be used to register the service.</span></span>

![Регистрация мастера создания службы расширения](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="f6e00-120">службу также можно зарегистрировать вручную с помощью инспектора конфигурации набор средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f6e00-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Регистрация службы расширения вручную](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="f6e00-122">Если служба расширений использует профиль, убедитесь, что он указан в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="f6e00-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Настроенная служба расширений](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="f6e00-124">Имя и приоритет компонента также можно изменить.</span><span class="sxs-lookup"><span data-stu-id="f6e00-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="f6e00-125">Доступ к службе расширений</span><span class="sxs-lookup"><span data-stu-id="f6e00-125">Accessing an extension service</span></span>

<span data-ttu-id="f6e00-126">Доступ к службам расширений осуществляется в коде с использованием, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) как показано в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="f6e00-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="f6e00-127">См. также:</span><span class="sxs-lookup"><span data-stu-id="f6e00-127">See also</span></span>

- [<span data-ttu-id="f6e00-128">Системы, службы расширений и поставщики данных</span><span class="sxs-lookup"><span data-stu-id="f6e00-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="f6e00-129">Мастер создания службы расширения</span><span class="sxs-lookup"><span data-stu-id="f6e00-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="f6e00-130">имикседреалитекстенсионсервице</span><span class="sxs-lookup"><span data-stu-id="f6e00-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="f6e00-131">микседреалитисервицерегистри</span><span class="sxs-lookup"><span data-stu-id="f6e00-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
