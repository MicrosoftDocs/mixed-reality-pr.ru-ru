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
# <a name="extension-services"></a><span data-ttu-id="364f0-104">Службы расширений</span><span class="sxs-lookup"><span data-stu-id="364f0-104">Extension services</span></span>

<span data-ttu-id="364f0-105">Службы расширения — это компоненты, расширяющие функциональные возможности набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="364f0-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="364f0-106">Эти службы могут предоставляться МРТК или другими сторонами.</span><span class="sxs-lookup"><span data-stu-id="364f0-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="364f0-107">Создание службы расширений</span><span class="sxs-lookup"><span data-stu-id="364f0-107">Creating an extension service</span></span>

<span data-ttu-id="364f0-108">Самый эффективный способ создать службу расширения — использовать [Мастер создания службы расширения](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="364f0-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="364f0-109">Чтобы запустить мастер создания службы расширения, выберите **набор средств для смешанной реальности > служебные программы > создать службу расширения**.</span><span class="sxs-lookup"><span data-stu-id="364f0-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Мастер создания службы расширения](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="364f0-111">Мастер автоматизирует создание компонентов службы и обеспечивает правильное наследование интерфейса.</span><span class="sxs-lookup"><span data-stu-id="364f0-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Компоненты, созданные с помощью мастера создания службы расширений](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="364f0-113">В МРТК версии 2.0.0 существует ошибка в мастере службы расширений, где необходимо создать инспектор служб и профиль службы.</span><span class="sxs-lookup"><span data-stu-id="364f0-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="364f0-114">Дополнительные сведения см. в описании проблемы [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .</span><span class="sxs-lookup"><span data-stu-id="364f0-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="364f0-115">По завершении работы мастера можно реализовать функциональность службы.</span><span class="sxs-lookup"><span data-stu-id="364f0-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="364f0-116">Регистрация службы расширений</span><span class="sxs-lookup"><span data-stu-id="364f0-116">Registering an extension service</span></span>

<span data-ttu-id="364f0-117">Чтобы приложение было доступно для приложения, необходимо зарегистрировать новую службу расширения в наборе средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="364f0-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="364f0-118">Для регистрации службы можно использовать мастер создания службы расширения.</span><span class="sxs-lookup"><span data-stu-id="364f0-118">The extension service creation wizard can be used to register the service.</span></span>

![Регистрация мастера создания службы расширения](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="364f0-120">Службу также можно зарегистрировать вручную с помощью инспектора конфигурации набора средств для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="364f0-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Регистрация службы расширения вручную](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="364f0-122">Если служба расширений использует профиль, убедитесь, что он указан в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="364f0-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Настроенная служба расширений](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="364f0-124">Имя и приоритет компонента также можно изменить.</span><span class="sxs-lookup"><span data-stu-id="364f0-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="364f0-125">Доступ к службе расширений</span><span class="sxs-lookup"><span data-stu-id="364f0-125">Accessing an extension service</span></span>

<span data-ttu-id="364f0-126">Доступ к службам расширений осуществляется в коде с использованием, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) как показано в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="364f0-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="364f0-127">См. также</span><span class="sxs-lookup"><span data-stu-id="364f0-127">See also</span></span>

- [<span data-ttu-id="364f0-128">Системы, службы расширений и поставщики данных</span><span class="sxs-lookup"><span data-stu-id="364f0-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="364f0-129">Мастер создания службы расширения</span><span class="sxs-lookup"><span data-stu-id="364f0-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="364f0-130">имикседреалитекстенсионсервице</span><span class="sxs-lookup"><span data-stu-id="364f0-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="364f0-131">микседреалитисервицерегистри</span><span class="sxs-lookup"><span data-stu-id="364f0-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
