---
title: Визуализация пространственной сетки
description: Ознакомьтесь с рекомендациями по проектированию и физической средой, посвященной визуализации пространственной сетки в МРТК.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Смешанная реальность, HoloLens, элементы управления ИП, взаимодействие, Пользовательский интерфейс, UX, проектирование UX, пространственный пользовательский интерфейс, пространственное взаимодействие, трехмерный Пользовательский интерфейс, трехмерный UI, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 0d8d2811c2fae96f679eeb1df2f1053e7ecf5def
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300349"
---
# <a name="spatial-mesh"></a>Виртуальная сетка

![Виртуальная сетка](images/MRTK_PulseShader_SpatialMesh.gif)

Пользователи узнают, как устройство воспринимает и понимает физическую среду с помощью визуализации пространственной сетки. Правильная визуализация пространственной сетки может создать удобство и Magical при предоставлении пространственного контекста.  

## <a name="design-guideline"></a>Рекомендации по проектированию

Важно позволить пользователю сосредоточиться на содержимом и взаимодействовать с ним. Непрерывная визуализация пространственной сетки в фоновом режиме может отвлечь внимание. Мы рекомендуем визуализировать среду экономно, либо только один раз при первом запуске, либо когда пользователь четко показывает, что им нужно видеть сетку окружающей среды, нацеливание и касание воздуха. Это поведение можно наблюдать на портале Mixed Reality.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Визуализация пространственной сетки в МРТК (набор средств для смешанной реальности) для Unity

МРТК предоставляет несколько материалов для визуализации пространственной сетки.

- **MRTK_Wireframe. материально, MRTK_Wireframe.** Material: сведения о статической пространственной сетке по умолчанию, которые показывают контуры сетки без анимации. Этот материал полезен в целях отладки, так как он отображает все геометрические объекты сетки. Однако это не рекомендуется для рабочей среды.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.** материально. этот материал предоставляет анимированный импульсный результат для пространственной сетки. Этот материал можно использовать для визуализации среды на заданный момент времени или на входе пользователя в Air. Примеры см. в сцене **пулсешадерексамплес. Unity** .
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Дополнительные сведения см. в разделе [мртк-пространственное осведомленность](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) и [Мртк-Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

<br>

---

## <a name="see-also"></a>См. также

* [Курсоры](cursors.md)
* [Телекинез](point-and-commit.md)
* [Кнопка](button.md)
* [Активный объект](interactable-object.md)
* [Ограничивающая рамка и панель приложения](app-bar-and-bounding-box.md)
* [Оперирование](direct-manipulation.md)
* [Меню руки](hand-menu.md)
* [Быстрое меню](near-menu.md)
* [Коллекция объектов](object-collection.md)
* [Голосовая команда](voice-input.md)
* [Клавиатура](keyboard.md)
* [Подсказка](tooltip.md)
* [Планшет](slate.md)
* [Ползунок](slider.md)
* [Шейдер](shader.md)
* [Биллбординг и закрепление элемента в пространстве](billboarding-and-tag-along.md)
* [Индикация хода выполнения](progress.md)
* [Притяжение к поверхности](surface-magnetism.md)
