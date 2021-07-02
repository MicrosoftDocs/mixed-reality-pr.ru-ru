---
title: Реестр службы Mixed Reality
description: Документация по Микседреалитисервицерегистри и Имикседреалитисервицерегистрар
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 061e4233d61de817b1aaed7faaa6d461427d6f07
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176705"
---
# <a name="mixed-reality-service-registry"></a>Реестр службы Mixed Reality

в набор средств смешанной реальности есть два очень схожих именованных компонента, которые выполняют связанные задачи: микседреалитисервицерегистри и имикседреалитисервицерегистрар.

## <a name="mixedrealityserviceregistry"></a>микседреалитисервицерегистри

[Микседреалитисервицерегистри](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) — это компонент, который содержит экземпляры каждой зарегистрированной службы (основные системы и службы расширений).

> [!NOTE]
> Микседреалитисервицерегистри содержит экземпляры объектов, реализующих интерфейс [имикседреалитисервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , включая [имикседреалитекстенсионсервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).
>
>Объекты, реализующие [имикседреалитидатапровидер](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (подкласс имикседреалитисервице), явно не зарегистрированы в микседреалитисервицерегистри. Эти объекты управляются отдельными службами (например, пространственной осведомленностью).

Микседреалитисервицерегистри реализуется как статический класс C# и является рекомендуемым шаблоном, используемым для получения экземпляров службы в коде приложения.

В следующем фрагменте кода демонстрируется получение экземпляра Имикседреалитинпутсистем.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>имикседреалитисервицерегистрар

[Имикседреалитисервицерегистрар](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) — это интерфейс, который определяет функциональные возможности, реализуемые компонентами, которые управляют регистрацией одной или нескольких служб. Компоненты, реализующие Имикседреалитисервицерегистрар, отвечают за добавление и удаление данных в Микседреалитисервицерегистри. Объект [микседреалититулкит](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) является одним из таких компонентов.

Другие регистраторы можно найти в папке МРТК/SDK/эксперименталь/Features. Эти компоненты можно использовать для добавления в приложение поддержки отдельной службы (например, пространственной осведомленности). Эти одиночные Диспетчеры служб перечислены ниже.

- [баундарисистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [камерасистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [диагностикссистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [инпутсистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [спатиалаваренесссистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [телепортсистемманажер](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Каждый из перечисленных выше компонентов, за исключением Инпутсистемманажер, отвечает за Управление регистрацией и состоянием одного типа службы. Для Инпутсистем требуются некоторые дополнительные службы поддержки (например, Фокуспровидер), которые также управляются Инпутсистемманажер.

Как правило, методы, определенные Имикседреалитисервицерегистрар, вызываются внутренне компонентами управления службами или вызываются службами, требующими правильной работы дополнительных компонентов службы. Код приложения, как правило, не вызывает эти методы, так как это может привести к непредсказуемому поведению приложения (например, кэшированный экземпляр службы может стать недопустимым).

## <a name="see-also"></a>См. также:

- [Документация по API Имикседреалитисервицерегистрар](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Документация по API Микседреалитисервицерегистри](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
