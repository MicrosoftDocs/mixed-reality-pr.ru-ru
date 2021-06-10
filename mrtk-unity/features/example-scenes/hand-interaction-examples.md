---
title: Примеры взаимодействия с помощью рук
description: Примеры взаимодействия с руки в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, взаимодействия с руки, элемент управления "границы", кнопки
ms.openlocfilehash: 229933dfd2414e485da6c1a77a2ffb08c9982249
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908409"
---
# <a name="hand-interaction-examples-scene"></a><span data-ttu-id="3b641-104">Сцены с примерами взаимодействия руки</span><span class="sxs-lookup"><span data-stu-id="3b641-104">Hand interaction examples scene</span></span>

![Примеры взаимодействия с руки 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="3b641-106">Пример сцены **хандинтерактионексамплес** содержит различные типы взаимодействий и элементов управления пользовательского интерфейса, которые выделяют ввод с клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="3b641-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="3b641-107">С имитацией ввода МРТК вы можете работать с отслеживанием действий в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="3b641-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="3b641-108">**Хандинтерактионексамплес** сцена включена в пакет примеров мртк.</span><span class="sxs-lookup"><span data-stu-id="3b641-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="3b641-109">Пакет **примеров набора средств для смешанной реальности** можно скачать и импортировать с помощью [инструмента для функций смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) .</span><span class="sxs-lookup"><span data-stu-id="3b641-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="3b641-110">В Unity используйте окно меню > диспетчер пакетов > в Project > Custom и выберите **примеры набора средств смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="3b641-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="3b641-111">Нажмите кнопку **импортировать в проект** рядом с пунктом **демонстрации — хандтраккинг**.</span><span class="sxs-lookup"><span data-stu-id="3b641-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="3b641-112">Вы сможете найти сцену **хандинтерактионексамплес** в папке assets > Samples.</span><span class="sxs-lookup"><span data-stu-id="3b641-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="3b641-113">Если вы не используете средство для работы с смешанной реальности, вы можете загрузить и импортировать файл **Microsoft. микседреалити. Toolkit. Unity. examples. пакет unitypackage** со [страницы выпуска мртк GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) .</span><span class="sxs-lookup"><span data-stu-id="3b641-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="3b641-114">В этом примере сцены используется *Текстмеш Pro*.</span><span class="sxs-lookup"><span data-stu-id="3b641-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="3b641-115">Чтобы открыть сцену, нажмите кнопку *"Импорт tmp Essentials"* , когда во время импорта сцены появится соответствующий запрос.</span><span class="sxs-lookup"><span data-stu-id="3b641-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="3b641-116">После этого Unity будет импортировать пакеты Текстмеш Pro.</span><span class="sxs-lookup"><span data-stu-id="3b641-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="3b641-117">Эти компоненты можно изучить в **хандинтерактионексамплес** сцене</span><span class="sxs-lookup"><span data-stu-id="3b641-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="3b641-118">Нажимаемая кнопка</span><span class="sxs-lookup"><span data-stu-id="3b641-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="3b641-119">Элемент управления Bounds</span><span class="sxs-lookup"><span data-stu-id="3b641-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="3b641-120">Манипулятор объекта</span><span class="sxs-lookup"><span data-stu-id="3b641-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="3b641-121">Планшет</span><span class="sxs-lookup"><span data-stu-id="3b641-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="3b641-122">Ползунок</span><span class="sxs-lookup"><span data-stu-id="3b641-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="3b641-123">Системная клавиатура</span><span class="sxs-lookup"><span data-stu-id="3b641-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
