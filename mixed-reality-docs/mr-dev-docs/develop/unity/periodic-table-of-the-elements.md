---
title: Периодическая таблица элементов
description: Узнайте, как разместить массив объектов в трехмерном пространстве с различными типами поверхностей, используя коллекцию объектов с периодической таблицей примера приложения Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, пример приложения, элементы управления, МРТК, набор средств для смешанной реальности, Unity, примеры приложений, примеры приложений, Открытый исходный код, Microsoft Store, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 19307b310d104f418e4f7739b0576c63407d83fd
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759740"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="69daa-104">Периодическая таблица элементов</span><span class="sxs-lookup"><span data-stu-id="69daa-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="69daa-105">В этой статье рассматривается исследовательская выборка, созданная в [лабораторных занятиях по смешанной реальности](https://github.com/Microsoft/MRDesignLabs_Unity), где мы предоставляем наши знания и предложения по разработке приложений для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="69daa-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="69daa-106">Наши статьи и код, относящиеся к проектированию, будут развиваться по мере внесения новых обнаружений.</span><span class="sxs-lookup"><span data-stu-id="69daa-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="69daa-107">[Периодическая таблица элементов](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) — это пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="69daa-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="69daa-108">Узнайте, как разместить массив объектов в трехмерном пространстве с различными типами поверхностей с помощью **[коллекции объектов](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="69daa-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="69daa-109">Также Узнайте, как создавать взаимодействующие объекты, реагирующие на стандартные входные данные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="69daa-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="69daa-110">Вы можете использовать компоненты этого проекта, чтобы создать собственный интерфейс приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="69daa-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Таблица периодов приложения элементов](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="69daa-112">Демонстрационное видео</span><span class="sxs-lookup"><span data-stu-id="69daa-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="69daa-113">Записано с помощью HoloLens 2 с записью смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="69daa-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="69daa-114">Сведения о приложении</span><span class="sxs-lookup"><span data-stu-id="69daa-114">About the app</span></span>

<span data-ttu-id="69daa-115">Периодическая таблица элементов визуализирует химические элементы и все их свойства в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="69daa-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="69daa-116">Он включает основные взаимодействия HoloLens, таких как взгляд и воздушный нажим.</span><span class="sxs-lookup"><span data-stu-id="69daa-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="69daa-117">Пользователи могут узнать об элементах с анимированными трехмерными моделями.</span><span class="sxs-lookup"><span data-stu-id="69daa-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="69daa-118">Они могут визуально понять электронную оболочку элемента и ее всегда, которая состоит из прочего и неутронс.</span><span class="sxs-lookup"><span data-stu-id="69daa-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="69daa-119">Историческая справка</span><span class="sxs-lookup"><span data-stu-id="69daa-119">Background</span></span>

<span data-ttu-id="69daa-120">После первого изучения HoloLens я знал, что я хотел бы поэкспериментировать с периодическим табличным приложением в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="69daa-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="69daa-121">Поскольку каждый элемент имеет много точек данных, отображаемых с текстом, я думал, что это было бы очень удобно для изучения типографской композиции в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="69daa-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="69daa-122">Предоставление пользователям возможности визуализировать модель электронного представления элемента была еще одна интересная часть этого проекта.</span><span class="sxs-lookup"><span data-stu-id="69daa-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="69daa-123">Конструирование</span><span class="sxs-lookup"><span data-stu-id="69daa-123">Design</span></span>

<span data-ttu-id="69daa-124">Для представления периодической таблицы по умолчанию я предполагаю трехмерные поля, которые будут содержать электронную модель каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="69daa-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="69daa-125">Поверхность каждого поля будет прозрачной, чтобы пользователь мог получить грубое представление о том элемента.</span><span class="sxs-lookup"><span data-stu-id="69daa-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="69daa-126">С помощью взгляда и касания Air пользователь может открыть подробное представление каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="69daa-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="69daa-127">Чтобы переход между табличным представлением и подробным представлением был плавно и естественным, я сделал это как физическое взаимодействие флажка, открывающегося в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="69daa-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="69daa-128">![Эскиз проектирования](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="69daa-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="69daa-129">*Разработка набросков*</span><span class="sxs-lookup"><span data-stu-id="69daa-129">*Design sketches*</span></span>

<span data-ttu-id="69daa-130">В подробном представлении я хотел визуализировать информацию каждого элемента с помощью элегантноного текста в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="69daa-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="69daa-131">В центральной области отображается анимированная трехмерная модель электронов, которую можно просмотреть с разных углов.</span><span class="sxs-lookup"><span data-stu-id="69daa-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Взаимодействие](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="69daa-133">![Прототипы](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="69daa-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="69daa-134">*Прототипы взаимодействия*</span><span class="sxs-lookup"><span data-stu-id="69daa-134">*Interaction prototypes*</span></span>

<span data-ttu-id="69daa-135">Пользователь может изменить тип поверхности, коснувшись кнопок в нижней части таблицы — они могут переключаться между плоскостью, цилиндром, сферой и точечной.</span><span class="sxs-lookup"><span data-stu-id="69daa-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="69daa-136">Общие элементы управления и шаблоны, используемые в этом приложении</span><span class="sxs-lookup"><span data-stu-id="69daa-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="69daa-137">Взаимодействующий объект (кнопка)</span><span class="sxs-lookup"><span data-stu-id="69daa-137">Interactable object (button)</span></span>

<span data-ttu-id="69daa-138">[Взаимодействующий объект](../../design/interactable-object.md) — это объект, который может отвечать на базовые входные данные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="69daa-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="69daa-139">Он предоставляется в виде prefab или сценария, который можно легко применить к любому объекту.</span><span class="sxs-lookup"><span data-stu-id="69daa-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="69daa-140">Например, можно сделать чашку кофе в сцене интерактивной и реагировать на такие входные данные, как взгляд, касание, Навигация и жесты манипуляции.</span><span class="sxs-lookup"><span data-stu-id="69daa-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="69daa-141">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="69daa-141">Learn more</span></span>](../../design/interactable-object.md)

![Объект нтерактабле](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="69daa-143">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="69daa-143">Object collection</span></span>

<span data-ttu-id="69daa-144">[Коллекция объектов](../../design/object-collection.md) — это объект, который помогает размещать несколько объектов в различных фигурах.</span><span class="sxs-lookup"><span data-stu-id="69daa-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="69daa-145">Он поддерживает плоскость, цилиндр, сферу и точечную диаграмму.</span><span class="sxs-lookup"><span data-stu-id="69daa-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="69daa-146">Можно настроить дополнительные свойства, такие как радиус, число строк и расстояния.</span><span class="sxs-lookup"><span data-stu-id="69daa-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="69daa-147">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="69daa-147">Learn more</span></span>](../../design/object-collection.md)

![Коллекция объектов](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="69daa-149">Технические сведения</span><span class="sxs-lookup"><span data-stu-id="69daa-149">Technical details</span></span>

<span data-ttu-id="69daa-150">Вы можете найти сценарии и Prefabs для периодической таблицы приложения Elements в лаборатории по [проектированию смешанной реальности в GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="69daa-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="69daa-151">Перенос истории для HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="69daa-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="69daa-152">Ознакомьтесь со статьей о том, как периодическая таблица в приложении Elements была обновлена с использованием взаимодействий инстинктуал HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="69daa-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="69daa-153">Periodic Table of the Elements 2.0</span><span class="sxs-lookup"><span data-stu-id="69daa-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="69daa-154">Об авторе</span><span class="sxs-lookup"><span data-stu-id="69daa-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="69daa-155"><b>Дон Юн Парк</b> (Dong Yoon Park)</span><span class="sxs-lookup"><span data-stu-id="69daa-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="69daa-156">Разработчик средств взаимодействия с пользователем @Microsoft</span><span class="sxs-lookup"><span data-stu-id="69daa-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="69daa-157">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="69daa-157">See also</span></span>

* <span data-ttu-id="69daa-158">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [(скачайте из Microsoft Store в HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="69daa-158">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="69daa-159">[Surfaces](sampleapp-surfaces.md) - [(скачайте из Microsoft Store в HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="69daa-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="69daa-160">Periodic Table of the Elements 2.0</span><span class="sxs-lookup"><span data-stu-id="69daa-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="69daa-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="69daa-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)