---
title: Диалог
description: Сведения о наложения диалоговых окон в МРТК и о том, как их использовать в приложениях смешанной реальности.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Смешанная реальность, HoloLens, элементы управления ИП, взаимодействие, Пользовательский интерфейс, UX, проектирование UX, пространственный пользовательский интерфейс, пространственное взаимодействие, трехмерный Пользовательский интерфейс, трехмерный UI, гарнитура смешанной реальности, гарнитура Windows Mixed, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 18e446f6b35e8073f939d065de3572204e2967a1
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299999"
---
# <a name="dialog"></a><span data-ttu-id="e5085-104">Диалог</span><span class="sxs-lookup"><span data-stu-id="e5085-104">Dialog</span></span>

![Снимок экрана: наложение диалогового окна с кнопками Да и без кнопок, отображаемых в HoloLens](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="e5085-106">Элементы управления диалогового окна — это наложение пользовательского интерфейса, которое предоставляет контекстные сведения о приложении, часто запрашивая действие пользователя.</span><span class="sxs-lookup"><span data-stu-id="e5085-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="e5085-107">Используйте диалоговые окна, чтобы предоставить пользователям важную информацию и запросить подтверждение или дополнительные сведения, прежде чем можно будет завершить действие.</span><span class="sxs-lookup"><span data-stu-id="e5085-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e5085-108">Диалоговое окно в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="e5085-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e5085-109">МРТК предоставляет элемент управления диалогового окна в трех размерах с одним или двумя параметрами кнопки.</span><span class="sxs-lookup"><span data-stu-id="e5085-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="e5085-110">Можно также указать расстояние размещения для практически или дальнего диапазона взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="e5085-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="e5085-111">DialogSmall_192x96. Prefab: 192x96mm</span><span class="sxs-lookup"><span data-stu-id="e5085-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="e5085-112">DialogMedium_192x128. Prefab: 192x128mm</span><span class="sxs-lookup"><span data-stu-id="e5085-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="e5085-113">DialogLarge_192x192. Prefab: 192x192mm</span><span class="sxs-lookup"><span data-stu-id="e5085-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![Снимок экрана с разными наложением диалогового окна размера, выполняемым в HoloLens](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="e5085-115">Дополнительные сведения см. в разделе [мртк-Dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog).</span><span class="sxs-lookup"><span data-stu-id="e5085-115">For more information, see [MRTK - Dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="e5085-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e5085-116">See also</span></span>

* [<span data-ttu-id="e5085-117">Курсоры</span><span class="sxs-lookup"><span data-stu-id="e5085-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e5085-118">Телекинез</span><span class="sxs-lookup"><span data-stu-id="e5085-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e5085-119">Кнопка</span><span class="sxs-lookup"><span data-stu-id="e5085-119">Button</span></span>](button.md)
* [<span data-ttu-id="e5085-120">Активный объект</span><span class="sxs-lookup"><span data-stu-id="e5085-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e5085-121">Ограничивающая рамка и панель приложения</span><span class="sxs-lookup"><span data-stu-id="e5085-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e5085-122">Оперирование</span><span class="sxs-lookup"><span data-stu-id="e5085-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e5085-123">Меню руки</span><span class="sxs-lookup"><span data-stu-id="e5085-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e5085-124">Быстрое меню</span><span class="sxs-lookup"><span data-stu-id="e5085-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e5085-125">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="e5085-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e5085-126">Голосовая команда</span><span class="sxs-lookup"><span data-stu-id="e5085-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e5085-127">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="e5085-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e5085-128">Подсказка</span><span class="sxs-lookup"><span data-stu-id="e5085-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e5085-129">Планшет</span><span class="sxs-lookup"><span data-stu-id="e5085-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="e5085-130">Ползунок</span><span class="sxs-lookup"><span data-stu-id="e5085-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="e5085-131">Шейдер</span><span class="sxs-lookup"><span data-stu-id="e5085-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="e5085-132">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="e5085-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e5085-133">Индикация хода выполнения</span><span class="sxs-lookup"><span data-stu-id="e5085-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e5085-134">Притяжение к поверхности</span><span class="sxs-lookup"><span data-stu-id="e5085-134">Surface magnetism</span></span>](surface-magnetism.md)
