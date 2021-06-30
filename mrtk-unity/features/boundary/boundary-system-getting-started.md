---
title: Общие сведения о системе границ
description: Целевая страница для системы границ в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, система границ,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121362"
---
# <a name="boundary-system"></a>Система границ

Система границ обеспечивает поддержку визуализации компонентов границ виртуальной реальности в приложениях смешанной реальности. Границы определяют область, в которой пользователи могут безопасно перемещаться, людьми гарнитуру VR. Границы являются важным компонентом смешанной реальности, чтобы помочь пользователям избежать незамеченных препятствий при людьмие гарнитуры VR.

Многие платформы Virtual Reality предоставляют автоматическое отображение, например, белый контур, наложенный на виртуальный мир в качестве пользователя или контроллера вблизи границы. Система границ набора средств Mixed Reality расширяет эту функцию, позволяя отображать контур области, плоскости и другие функции, которые можно использовать для предоставления пользователям дополнительных сведений.

## <a name="getting-started"></a>Начало работы

Для добавления поддержки границ требуются два ключевых компонента набора средств Mixed Reality: система границ и платформа Virtual Reality, настроенная с границей.

1. [Включение](#enable-boundary-system) системы границ
2. [Настройка](#configure-boundary-visualization) визуализации границ
3. [Сборка и развертывание](#build-and-deploy) на платформе VR с настроенной границей

## <a name="enable-boundary-system"></a>Включить систему границ

Системой управления границей управляет объект Микседреалититулкит (или другой компонент [регистратора служб](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

В следующих шагах предполагается использование объекта Микседреалититулкит. Действия, необходимые для других регистраторов служб, могут отличаться.

1. Выберите объект Микседреалититулкит в иерархии сцены.

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

1. Перейдите на панель инспектора к разделу система границ и установите флажок Включить.

    ![Включение системы границ](../images/boundary/MRTKConfig_Boundary.png)

1. Выберите реализацию системы границ. Реализацией класса по умолчанию, предоставляемой МРТК, является [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Выбор реализации системы границ](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Вся реализация системы границ должна расширять [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Настройка визуализации границ

[Система границ использует профиль конфигурации](configuring-boundary-visualization.md) , чтобы указать, какие компоненты границ должны быть отображены, и настроить их внешний вид.

![Параметры визуализации границ](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> У пользователей профиля по умолчанию `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/мртк/SDK/Profiles) будет предварительно настроена система границ для показа плоскости этажа, области воспроизведения и области с отслеживанием.

## <a name="build-and-deploy"></a>Сборка и развертывание

После настройки системы границ с требуемыми параметрами визуализации проект можно построить на целевой платформе.

> [!NOTE]
> Режим воспроизведения Unity позволяет визуализировать настроенную границу в редакторе. Эта функция обеспечивает быструю разработку и тестирование без необходимости выполнять этап сборки и развертывания. Обязательно выполните окончательное приемочное тестирование с помощью созданной и развернутой версии приложения, работающей на целевом оборудовании и платформе.

## <a name="accessing-boundary-system-via-code"></a>Доступ к граничной системе через код

Если параметр включен и настроен, доступ к системе границ можно получить с помощью статического вспомогательного класса Коресервицес. Затем можно использовать ссылку для динамического изменения параметров границ и доступа к связанным объекты gameobject, управляемым системой.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>См. также

- [Документация по API границ](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Настройка визуализации границ](configuring-boundary-visualization.md)
