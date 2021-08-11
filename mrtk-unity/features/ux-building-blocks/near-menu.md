---
title: Быстрое меню
description: Общие сведения о типах меню в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, мртк, Near меню,
ms.openlocfilehash: 75e7ee195a5838e88c42b7547e7b75205bfe1ee2fa1c8b1ba0a868b294883347
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190661"
---
# <a name="near-menu"></a>Быстрое меню

![Быстрое меню](../images/near-menu/MRTK_UX_NearMenu.png)

Ближайшее меню — это элемент управления UX, который предоставляет коллекцию кнопок или других компонентов пользовательского интерфейса. Он будет плавающим вокруг тела пользователя и легко доступен в любое время. Так как он слабо связан с пользователем, он не затрагивает взаимодействие пользователя с целевым содержимым. Пользователь может использовать кнопку "закрепить", чтобы заблокировать или разблокировать меню. Меню можно заменять и размещать в определенной позиции.

## <a name="interaction-behavior"></a>Поведение взаимодействия

- **Тег**. в этом меню вы выполняете действия в пределах 30-60cm диапазона от пользователя для близкого взаимодействия.
- **ПИН-код**: с помощью кнопки "закрепить" меню можно заблокировать по всему миру и освободить.
- **Захват и перемещение**. меню всегда можно переносить и перемещать. Независимо от предыдущего состояния меню будет закреплено (блокировка по всему миру) при извлечении и освобождении. Имеются визуальные подсказки для области захвата. Они раскрываются с учетом расположения.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefabs

Near меню Prefabs предназначены для демонстрации использования различных компонентов МРТК для создания меню для практических взаимодействий.

- **NearMenu2x4. prefab**
- **NearMenu3x1. prefab**
- **NearMenu3x2. prefab**
- **NearMenu3x3. prefab**
- **NearMenu4x1. prefab**
- **NearMenu4x2. prefab**

## <a name="example-scene"></a>Пример сцены

Примеры NEAR меню Prefabs можно найти в `NearMenuExamples` сцене.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Структура

Рядом с Prefabs меню создаются следующие компоненты МРТК.

- [**PressableButtonHoloLens2**](button.md) prefab
- [**Коллекция объектов Grid**](object-collection.md): макет с несколькими кнопками в сетке
- [**Обработчик манипуляции**](manipulation-handler.md): захват и перемещение меню
- [**Радиалвиев Solver**](solvers/solver.md): следование мне (с тегом)

![Ближайшее меню prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Как выполнять настройку

**1. кнопки "Добавить" и "Удалить"**

В разделе `ButtonCollection` объект добавьте или удалите кнопки.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Обновление коллекции объектов Grid**

Нажмите кнопку `Update Collection` в инспекторе `ButtonCollection` объекта. Будет обновлен макет сетки.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Количество строк можно настроить с помощью `Rows` свойства коллекции объектов Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. изменение размера формы**

Измените размер `Quad` объекта в поле `Backplate` . Ширина и высота формы должны иметь значение `0.032 * [Number of the buttons + 1]` . Например, если у вас есть три кнопки, ширина формы будет равна, `0.032 * 4` а высота — `0.032 * 3` . Это выражение можно напрямую разместить в поле Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- размер по умолчанию для кнопки HoloLens 2 составляет 3.2 x 3.2 cm (0.032 m)

## <a name="see-also"></a>См. также раздел

- [**Кнопки**](button.md)
- [**Элемент управления Bounds**](bounds-control.md)
- [**Ползунок**](sliders.md)
- [**Коллекция объектов Grid**](object-collection.md)
- [**Обработчик манипуляции**](manipulation-handler.md)
- [**Поиск решения Радиалвиев**](solvers/solver.md)
