---
title: Мастер создания службы расширений
description: Документация по мастеру для перехода с Singleton на службы МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6b4efa39a99755f3c031757c7298465886d0c39512c93750f4653200edce9e17
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214300"
---
# <a name="extension-service-creation-wizard"></a>Мастер создания службы расширений

Переход от Singleton к службам может быть трудной задачей. Этот мастер может дополнить нашу другую документацию и пример кода, позволяя разработчики создавать новые службы с помощью (примерно) той же простоты, что и создание нового сценария с использованием режима «без применения». Чтобы узнать о создании служб с нуля, ознакомьтесь [с нашим руководством по созданию зарегистрированных служб](../../configuration/mixed-reality-configuration-guide.md) (ожидается в ближайшее время).

## <a name="launching-the-wizard"></a>Запуск мастера

Запустите мастер из главного меню: **микседреалититулкит/Utilities/создание службы расширения** — мастер выполнит все этапы процесса создания скрипта службы, интерфейса и класса профиля.

## <a name="editing-your-service-script"></a>Изменение скрипта службы

По умолчанию новые ресурсы скрипта будут созданы в `MixedRealityToolkit.Generated/Extensions` папке. Завершив работу с мастером, перейдите сюда и откройте новый скрипт службы.

В создаваемые сценарии службы входят некоторые запросы, аналогичные новым скриптам с несложным поведением. Они помогут вам понять, где можно инициализировать и обновить службу.

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

Если вы решили зарегистрировать службу в мастере, то все, что нужно сделать, — это изменить этот сценарий, и служба будет автоматически обновлена. В противном случае вы можете ознакомиться [с регистрацией новой службы здесь](../../configuration/mixed-reality-configuration-guide.md).
