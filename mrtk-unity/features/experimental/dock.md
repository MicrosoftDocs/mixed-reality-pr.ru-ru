---
title: Dock
description: Описание для элементов управления Dock.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226576"
---
# <a name="dock"></a>Dock

![Dock](../images/dock/MRTK_UX_Dock_Main.png)

Этот элемент управления позволяет перемещать объекты в заранее определенную позицию и из них для создания палитр, полок и панелей навигации.

## <a name="features"></a>Компоненты

- Поддерживает любое количество позиций и макетов закрепления (отлично подходит [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Закрепленные объекты автоматически перемещаются, чтобы освободить место для новых объектов.
- Объекты масштабируются в соответствии с закреплением пространства, а затем изменяются в исходное положение при перетаскивании.

## <a name="getting-started-with-dock"></a>Начало работы с закреплением

- Создайте GameObject с компонентом Dock и добавьте к нему дочерние элементы объекты gameobject.
- Добавьте компонент DockPosition в каждый из дочерних элементов.
- Добавьте закрепляемый компонент в любое количество объектов в сцене, чтобы разрешить их прикрепление. Они также должны иметь [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) компонент и объект-контейнер.
- *Необязательно.* используйте [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) для закрепления, чтобы автоматически разместить доккпоситионс.

### <a name="prerequisites"></a>Предварительные требования

- Каждый закрепляемый объект должен иметь объект с таким же объектом, как [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) или [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .
- Если требуется, чтобы объект запускался при загрузке сцены, назначьте его свойству прикрепленного объекта DockPosition.

## <a name="how-it-works"></a>Принцип работы

Закрепляемый компонент строится на основе событий манипуляции, чтобы можно было закреплять перетаскиваемые объекты и откреплять их в конкретных позициях. Размещение определяется ближайшим перекрывающимся DockPosition, который перемещается к перемещенному объекту, поэтому оба объекта должны иметь конфликты для активации триггера.
