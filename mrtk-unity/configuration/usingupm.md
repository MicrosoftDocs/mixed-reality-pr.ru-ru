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
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="7aa42-104">Использование диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="7aa42-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="7aa42-105">начиная с версии 2.5.0, используя [средство "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)", набор средств Microsoft Mixed reality интегрируется с диспетчер пакетов unity (упм) при использовании unity 2019,4 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="7aa42-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="7aa42-106">Использование Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="7aa42-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="7aa42-107">Как описано в разделе [Добро пожаловать в средство "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ", можно скачать средство с помощью [этой ссылки](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="7aa42-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7aa42-108">Если манифест проекта содержит `Microsoft Mixed Reality` запись в `scopedRegistries` разделе, рекомендуется удалить его.</span><span class="sxs-lookup"><span data-stu-id="7aa42-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="7aa42-109">Чтобы удалить настроенный реестр с заданной областью, перейдите по адресу `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="7aa42-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Удаление реестра с заданной областью](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="7aa42-111">Пакеты МРТК отображаются под `Mixed Reality Toolkit` заголовком при обнаружении компонентов.</span><span class="sxs-lookup"><span data-stu-id="7aa42-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Поиск компонентов](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="7aa42-113">При выборе компонентов нет нужды беспокоиться о необходимых зависимостях, средство автоматически скачивает и интегрирует их в проект.</span><span class="sxs-lookup"><span data-stu-id="7aa42-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Необходимые зависимости](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="7aa42-115">управление функциями смешанной реальности с помощью Unity диспетчер пакетов</span><span class="sxs-lookup"><span data-stu-id="7aa42-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="7aa42-116">после добавления пакета набор средств смешанной реальности в манифест пакета можно управлять им с помощью пользовательского интерфейса Unity диспетчер пакетов.</span><span class="sxs-lookup"><span data-stu-id="7aa42-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Пакет УПМ МРТК Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="7aa42-118">если пакет набор средств смешанной реальности удаляется с помощью диспетчер пакетов Unity, его необходимо добавить повторно с помощью [описанных выше действий](#using-the-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="7aa42-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="7aa42-119">примеры использования смешанной реальности набор средств</span><span class="sxs-lookup"><span data-stu-id="7aa42-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="7aa42-120">В отличие от использования файлов пакета ресурсов (. пакет unitypackage) `com.microsoft.mixedreality.toolkit.examples` и `com.microsoft.mixedreality.toolkit.handphysicsservice` не импортируйте примеры сцен и ресурсов автоматически.</span><span class="sxs-lookup"><span data-stu-id="7aa42-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="7aa42-121">Чтобы использовать один или несколько примеров, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="7aa42-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="7aa42-122">В редакторе Unity перейдите к `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="7aa42-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="7aa42-123">В списке пакетов выберите `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="7aa42-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="7aa42-124">Расположение нужных примеров в `Samples` списке</span><span class="sxs-lookup"><span data-stu-id="7aa42-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="7aa42-125">Щелкните `Import into Project`.</span><span class="sxs-lookup"><span data-stu-id="7aa42-125">Click `Import into Project`</span></span>

![Импорт примеров](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="7aa42-127">При обновлении примера пакета Unity предоставляет возможность обновления импортированных образцов.</span><span class="sxs-lookup"><span data-stu-id="7aa42-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="7aa42-128">При обновлении импортированного образца будут перезаписаны все изменения, внесенные в этот образец и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="7aa42-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aa42-129">См. также:</span><span class="sxs-lookup"><span data-stu-id="7aa42-129">See Also</span></span>

- [<span data-ttu-id="7aa42-130">пакеты набор средств смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="7aa42-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
