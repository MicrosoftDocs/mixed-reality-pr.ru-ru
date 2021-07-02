---
title: Быстрое меню
description: Общие сведения о типах меню в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, мртк, Near меню,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175655"
---
# <a name="near-menu"></a><span data-ttu-id="9ebfc-104">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="9ebfc-104">Near menu</span></span>

![Быстрое меню](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="9ebfc-106">Ближайшее меню — это элемент управления UX, который предоставляет коллекцию кнопок или других компонентов пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="9ebfc-107">Он будет плавающим вокруг тела пользователя и легко доступен в любое время.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="9ebfc-108">Так как он слабо связан с пользователем, он не затрагивает взаимодействие пользователя с целевым содержимым.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="9ebfc-109">Пользователь может использовать кнопку "закрепить", чтобы заблокировать или разблокировать меню.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="9ebfc-110">Меню можно заменять и размещать в определенной позиции.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="9ebfc-111">Поведение взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9ebfc-111">Interaction behavior</span></span>

- <span data-ttu-id="9ebfc-112">**Тег**. в этом меню вы выполняете действия в пределах 30-60cm диапазона от пользователя для близкого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="9ebfc-113">**ПИН-код**: с помощью кнопки "закрепить" меню можно заблокировать по всему миру и освободить.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="9ebfc-114">**Захват и перемещение**. меню всегда можно переносить и перемещать.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="9ebfc-115">Независимо от предыдущего состояния меню будет закреплено (блокировка по всему миру) при извлечении и освобождении.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="9ebfc-116">Имеются визуальные подсказки для области захвата.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="9ebfc-117">Они раскрываются с учетом расположения.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="9ebfc-118">Prefabs</span><span class="sxs-lookup"><span data-stu-id="9ebfc-118">Prefabs</span></span>

<span data-ttu-id="9ebfc-119">Near меню Prefabs предназначены для демонстрации использования различных компонентов МРТК для создания меню для практических взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="9ebfc-120">**NearMenu2x4. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="9ebfc-121">**NearMenu3x1. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="9ebfc-122">**NearMenu3x2. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="9ebfc-123">**NearMenu3x3. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="9ebfc-124">**NearMenu4x1. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="9ebfc-125">**NearMenu4x2. prefab**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="9ebfc-126">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="9ebfc-126">Example scene</span></span>

<span data-ttu-id="9ebfc-127">Примеры NEAR меню Prefabs можно найти в `NearMenuExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="9ebfc-128">Структура</span><span class="sxs-lookup"><span data-stu-id="9ebfc-128">Structure</span></span>

<span data-ttu-id="9ebfc-129">Рядом с Prefabs меню создаются следующие компоненты МРТК.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="9ebfc-130">[**PressableButtonHoloLens2**](button.md) prefab</span><span class="sxs-lookup"><span data-stu-id="9ebfc-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="9ebfc-131">[**Коллекция объектов Grid**](object-collection.md): макет с несколькими кнопками в сетке</span><span class="sxs-lookup"><span data-stu-id="9ebfc-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="9ebfc-132">[**Обработчик манипуляции**](manipulation-handler.md): захват и перемещение меню</span><span class="sxs-lookup"><span data-stu-id="9ebfc-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="9ebfc-133">[**Радиалвиев Solver**](solvers/solver.md): следование мне (с тегом)</span><span class="sxs-lookup"><span data-stu-id="9ebfc-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Ближайшее меню prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="9ebfc-135">Как выполнять настройку</span><span class="sxs-lookup"><span data-stu-id="9ebfc-135">How to customize</span></span>

<span data-ttu-id="9ebfc-136">**1. кнопки "Добавить" и "Удалить"**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="9ebfc-137">В разделе `ButtonCollection` объект добавьте или удалите кнопки.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="9ebfc-138">**2. Обновление коллекции объектов Grid**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="9ebfc-139">Нажмите кнопку `Update Collection` в инспекторе `ButtonCollection` объекта.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="9ebfc-140">Будет обновлен макет сетки.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="9ebfc-141">Количество строк можно настроить с помощью `Rows` свойства коллекции объектов Grid.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="9ebfc-142">**3. изменение размера формы**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="9ebfc-143">Измените размер `Quad` объекта в поле `Backplate` .</span><span class="sxs-lookup"><span data-stu-id="9ebfc-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="9ebfc-144">Ширина и высота формы должны иметь значение `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="9ebfc-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="9ebfc-145">Например, если у вас есть три кнопки, ширина формы будет равна, `0.032 * 4` а высота — `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="9ebfc-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="9ebfc-146">Это выражение можно напрямую разместить в поле Unity.</span><span class="sxs-lookup"><span data-stu-id="9ebfc-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="9ebfc-147">размер по умолчанию для кнопки HoloLens 2 составляет 3.2 x 3.2 cm (0.032 m)</span><span class="sxs-lookup"><span data-stu-id="9ebfc-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="9ebfc-148">См. также:</span><span class="sxs-lookup"><span data-stu-id="9ebfc-148">See also</span></span>

- [<span data-ttu-id="9ebfc-149">**Кнопки**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="9ebfc-150">**Элемент управления границами**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="9ebfc-151">**Slider**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="9ebfc-152">**Коллекция объектов Grid**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="9ebfc-153">**Обработчик манипуляции**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="9ebfc-154">**Поиск решения Радиалвиев**</span><span class="sxs-lookup"><span data-stu-id="9ebfc-154">**RadialView Solver**</span></span>](solvers/solver.md)
