---
title: Поставщик системных расширений
description: Расширения МРТК и поставщики данных
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, расширения системы,
ms.openlocfilehash: 358294702971b7d9e8de1b842d3bc1844e5dc9bf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121472"
---
# <a name="systems-extension-services-and-data-providers"></a>Системы, службы расширений и поставщики данных

В наборе средств Mixed Reality многие функции предоставляются в виде служб. Службы группируются по трем основным категориям: системам, службам расширений и поставщикам данных.

## <a name="systems"></a>системы

Системы — это службы, которые предоставляют основные функциональные возможности набора средств Mixed Reality. Все системы являются реализациями [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) интерфейса.

- [баундарисистем](../features/boundary/boundary-system-getting-started.md)
- [камерасистем](../features/camera-system/camera-system-overview.md)
- [диагностикссистем](../features/diagnostics/diagnostics-system-getting-started.md)
- [инпутсистем](../features/input/overview.md)
- [сценесистем](../features/scene-system/scene-system-getting-started.md)
- [спатиалаваренесссистем](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [телепортсистем](../features/teleport-system/teleport-system.md)

Каждая из перечисленных систем отображается в [профиле](../features/profiles/profiles.md)конфигурации компонента микседреалититулкит.

## <a name="extensions"></a>Расширения

Службы расширения — это компоненты, расширяющие функциональные возможности набора средств Mixed Reality. Все службы расширений должны указывать, что они реализуют [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) интерфейс.

Сведения о создании служб расширения см. в статье [службы расширений](../features/extensions/extension-services.md) .

Для доступа к МРТК службы расширения регистрируются и настраиваются с помощью раздела Extensions в профиле конфигурации компонента Микседреалититулкит.

![Настройка службы расширений](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Поставщики данных

Поставщики данных — это компоненты, которые по имени предоставляют данные для службы набора средств смешанной реальности. Все поставщики данных должны указывать, что они реализуют [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейс.

> [!NOTE]
> Не все службы потребует поставщиков данных. Систем, появляющихся системами набора средств смешанной реальности, являются единственной службой для использования поставщиков данных.

Для доступа к конкретной службе МРТК поставщики данных регистрируются в профиле конфигурации службы.

Код приложения обращается к поставщикам данных через [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) интерфейс. Для упрощения доступа поставщики данных также можно получить с помощью `CoreServices` вспомогательного класса.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Несмотря на то `IMixedRealityDataProvider` , что наследует от `IMixedRealityService` , поставщики данных не регистрируются в `MixedRealityServiceRegistry` . Для доступа к поставщикам данных код приложения должен запросить экземпляр службы, для которого они были зарегистрированы (например, система ввода).

### <a name="input"></a>Входные данные

Система ввода МРТК использует только поставщики данных, реализующие [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Поставщики входных системных данных](../features/images/input/RegisteredServiceProviders.PNG)

В следующем примере демонстрируется доступ к поставщику имитации ввода и переключается свойство Смусэйетраккинг.

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

Доступ к поставщику данных для основной входной системы также можно упростить с помощью `CoreServices` вспомогательного класса.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> Входная система возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.

Сведения о создании поставщика данных для входной системы МРТК см. в разделе [Создание входного системного поставщика данных](../features/input/create-data-provider.md).

### <a name="spatial-awareness"></a>Поддержка пространственных сведений

Система пространственной осведомленности МРТК использует только поставщики данных, реализующие [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) интерфейс.

![Поставщики системных данных для пространственного отслеживания](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

В следующем примере демонстрируется доступ к зарегистрированным поставщикам данных пространственной сетки и изменение видимости сеток.

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

Доступ к поставщику данных для основной системы пространственной информации также можно упростить с помощью `CoreServices` вспомогательного класса.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> Система пространственной информации возвращает только поставщики данных, которые поддерживаются платформой, на которой выполняется приложение.

Сведения о написании поставщика данных для системы поддержки пространственной информации МРТК см. в разделе [Создание системного поставщика данных с](../features/spatial-awareness/create-data-provider.md)поддержкой пространственного доступа.

## <a name="see-also"></a>См. также

- [Службы расширений](../features/extensions/extension-services.md)
- [Создание поставщика входных системных данных](../features/input/create-data-provider.md)
- [Создание поставщика системных системных данных для пространственного отслеживания](../features/spatial-awareness/create-data-provider.md)
- [Интерфейс Имикседреалитисервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Интерфейс Имикседреалитидатапровидер](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [Интерфейс Имикседреалитекстенсионсервице](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
