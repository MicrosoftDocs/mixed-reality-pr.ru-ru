---
title: Мастер создания службы расширения
description: Документация по мастеру для перехода с Singleton на службы МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176614"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="eeb37-104">Мастер создания службы расширения</span><span class="sxs-lookup"><span data-stu-id="eeb37-104">Extension service creation wizard</span></span>

<span data-ttu-id="eeb37-105">Переход от Singleton к службам может быть трудной задачей.</span><span class="sxs-lookup"><span data-stu-id="eeb37-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="eeb37-106">Этот мастер может дополнить нашу другую документацию и пример кода, позволяя разработчики создавать новые службы с помощью (примерно) той же простоты, что и создание нового сценария с использованием режима «без применения».</span><span class="sxs-lookup"><span data-stu-id="eeb37-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="eeb37-107">Чтобы узнать о создании служб с нуля, ознакомьтесь [с нашим руководством по созданию зарегистрированных служб](../../configuration/mixed-reality-configuration-guide.md) (ожидается в ближайшее время).</span><span class="sxs-lookup"><span data-stu-id="eeb37-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="eeb37-108">Запуск мастера</span><span class="sxs-lookup"><span data-stu-id="eeb37-108">Launching the wizard</span></span>

<span data-ttu-id="eeb37-109">Запустите мастер из главного меню: **микседреалититулкит/Utilities/создание службы расширения** — мастер выполнит все этапы процесса создания скрипта службы, интерфейса и класса профиля.</span><span class="sxs-lookup"><span data-stu-id="eeb37-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="eeb37-110">Изменение скрипта службы</span><span class="sxs-lookup"><span data-stu-id="eeb37-110">Editing your service script</span></span>

<span data-ttu-id="eeb37-111">По умолчанию новые ресурсы скрипта будут созданы в `MixedRealityToolkit.Generated/Extensions` папке.</span><span class="sxs-lookup"><span data-stu-id="eeb37-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="eeb37-112">Завершив работу с мастером, перейдите сюда и откройте новый скрипт службы.</span><span class="sxs-lookup"><span data-stu-id="eeb37-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="eeb37-113">В создаваемые сценарии службы входят некоторые запросы, аналогичные новым скриптам с несложным поведением.</span><span class="sxs-lookup"><span data-stu-id="eeb37-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="eeb37-114">Они помогут вам понять, где можно инициализировать и обновить службу.</span><span class="sxs-lookup"><span data-stu-id="eeb37-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="eeb37-115">Если вы решили зарегистрировать службу в мастере, то все, что нужно сделать, — это изменить этот сценарий, и служба будет автоматически обновлена.</span><span class="sxs-lookup"><span data-stu-id="eeb37-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="eeb37-116">В противном случае вы можете ознакомиться [с регистрацией новой службы здесь](../../configuration/mixed-reality-configuration-guide.md).</span><span class="sxs-lookup"><span data-stu-id="eeb37-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
