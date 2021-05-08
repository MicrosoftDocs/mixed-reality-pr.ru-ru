---
title: текстпрефаб
description: Общие сведения о Текстпрефаб в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489294"
---
# <a name="text-prefab"></a><span data-ttu-id="63024-104">Prefab текста</span><span class="sxs-lookup"><span data-stu-id="63024-104">Text prefab</span></span>

<span data-ttu-id="63024-105">Эти Prefabs оптимизированы для качества подготовки к просмотру в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="63024-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="63024-106">Дополнительные сведения см. в статье текст рекомендации [в Unity](/windows/mixed-reality/text-in-unity) в центре разработки Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="63024-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="63024-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="63024-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="63024-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="63024-108">3DTextPrefab</span></span>

<span data-ttu-id="63024-109">Сетка трехмерного текста prefab (Assets/МРТК/SDK/Стандардассетс/Prefabs/Text) с оптимизированным коэффициентом масштабирования на 2-м расстоянии.</span><span class="sxs-lookup"><span data-stu-id="63024-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="63024-110">(Ознакомьтесь с приведенными ниже инструкциями).</span><span class="sxs-lookup"><span data-stu-id="63024-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="63024-111">уитекстпрефаб</span><span class="sxs-lookup"><span data-stu-id="63024-111">UITextPrefab</span></span>

<span data-ttu-id="63024-112">Сетка текста пользовательского интерфейса prefab (Assets/МРТК/SDK/Стандардассетс/Prefabs/Text) с оптимизированным коэффициентом масштабирования на 2-м расстоянии.</span><span class="sxs-lookup"><span data-stu-id="63024-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="63024-113">(Ознакомьтесь с приведенными ниже инструкциями).</span><span class="sxs-lookup"><span data-stu-id="63024-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="63024-114">Шрифты</span><span class="sxs-lookup"><span data-stu-id="63024-114">Fonts</span></span>

<span data-ttu-id="63024-115">Шрифты с открытым исходным кодом (Assets/МРТК/Core/Стандардассетс/шрифты), входящие в состав набора средств для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="63024-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63024-116">Text prefab использует шрифт с открытым кодом "Селавик".</span><span class="sxs-lookup"><span data-stu-id="63024-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="63024-117">Чтобы использовать текст prefab с другим шрифтом, импортируйте файл шрифта и следуйте приведенным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="63024-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="63024-118">Ниже приведен пример использования шрифта "Segoe UI" с текстом prefab.</span><span class="sxs-lookup"><span data-stu-id="63024-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Импорт файла Segoe UI шрифтов](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="63024-120">Назначьте текстуру шрифта 3DTextSegoeUI. Material.</span><span class="sxs-lookup"><span data-stu-id="63024-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Назначение текстуры шрифта](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="63024-122">В материале 3DTextSegoeUI. Material выберите шейдер Custom/3DTextShader. Shader.</span><span class="sxs-lookup"><span data-stu-id="63024-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Назначение шейдера](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="63024-124">Назначение Segoe UI шрифта и 3DTextSegoeUI материала для текстовых компонентов в Prefabs.</span><span class="sxs-lookup"><span data-stu-id="63024-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Назначение файла шрифта и материала](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="63024-126">Работа со шрифтами в Unity</span><span class="sxs-lookup"><span data-stu-id="63024-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="63024-127">При добавлении новых трехмерных Текстмеш в сцену в Unity возникают две проблемы, которые визуально очевидны.</span><span class="sxs-lookup"><span data-stu-id="63024-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="63024-128">Один шрифт выглядит очень крупным и двумя, шрифт выглядит очень размытым.</span><span class="sxs-lookup"><span data-stu-id="63024-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="63024-129">Также интересно отметить, что в инспекторе значение размера шрифта по умолчанию равно нулю.</span><span class="sxs-lookup"><span data-stu-id="63024-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="63024-130">Замена этого нулевого значения на 13 не повлияет на размер, поскольку значение 13 фактически является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="63024-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="63024-131">В Unity предполагается, что все новые элементы, добавленные в сцену, имеют размер 1 единицы Unity или шкалу 100%, которая преобразуется в примерно один счетчик на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="63024-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="63024-132">В случае с шрифтами ограничивающий прямоугольник для 3D-Текстмеш по умолчанию имеет значение около 1 индикатора высоты.</span><span class="sxs-lookup"><span data-stu-id="63024-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="63024-133">Масштаб шрифта и размеры шрифтов</span><span class="sxs-lookup"><span data-stu-id="63024-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="63024-134">Большинство визуальных конструкторов используют точки для определения размеров шрифтов в реальном мире, а также для программ проектирования.</span><span class="sxs-lookup"><span data-stu-id="63024-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="63024-135">Имеется около 2835 (2, 834.645666399962) точек в единицах измерения.</span><span class="sxs-lookup"><span data-stu-id="63024-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="63024-136">На основе преобразования системы точек в 1 измеритель и размер шрифта Текстмеш по умолчанию для Unity, равный 13, простой математический коэффициент 13, поделенный на 2835 равным 0,0046 (0.004586111116), обеспечивает оптимальный Стандартный масштаб, хотя некоторые из них могут быть округлены до 0,005.</span><span class="sxs-lookup"><span data-stu-id="63024-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="63024-137">В любом случае, масштабирование текстового объекта или контейнера до этих значений не только приводит к 1:1 преобразованию размеров шрифтов из программы-конструктора, но также предоставляет стандарт для поддержания согласованности во всем приложении или игре.</span><span class="sxs-lookup"><span data-stu-id="63024-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="63024-138">Текст пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="63024-138">UI Text</span></span>

<span data-ttu-id="63024-139">При добавлении текстового элемента на основе элементов пользовательского интерфейса или полотна в сцену по-прежнему увеличивается размер четности.</span><span class="sxs-lookup"><span data-stu-id="63024-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="63024-140">Различия в двух размерах составит примерно 1000%, что приведет к увеличению коэффициента масштабирования для текстовых компонентов на основе пользовательского интерфейса в 0,00046 (0.0004586111116) или 0,0005 для округленного значения.</span><span class="sxs-lookup"><span data-stu-id="63024-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="63024-141">**Заявление об отказе**: значение по умолчанию любого шрифта может влиять на размер текстуры этого шрифта или на то, как шрифт был импортирован в Unity.</span><span class="sxs-lookup"><span data-stu-id="63024-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="63024-142">Эти тесты были выполнены на основе шрифта Arial по умолчанию в Unity, а также одного другого импортированного шрифта.</span><span class="sxs-lookup"><span data-stu-id="63024-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Размер шрифта с коэффициентами масштабирования](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="63024-144">Text3DSelawik.</span><span class="sxs-lookup"><span data-stu-id="63024-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="63024-145">Материал для 3DTextPrefab с поддержкой перекрытия.</span><span class="sxs-lookup"><span data-stu-id="63024-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="63024-146">Требуется 3DTextShader. шейдер</span><span class="sxs-lookup"><span data-stu-id="63024-146">Requires 3DTextShader.shader</span></span>

![Материалы по шрифтам по умолчанию и материалы по 3DTextSegoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="63024-148">Text3DShader. шейдер</span><span class="sxs-lookup"><span data-stu-id="63024-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="63024-149">Шейдер для 3DTextPrefab с поддержкой перекрытия.</span><span class="sxs-lookup"><span data-stu-id="63024-149">Shader for 3DTextPrefab with occlusion support.</span></span>