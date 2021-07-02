---
title: Светлое наведение
description: Документация по Ховерлигхт с примерами в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, светлое наведение,
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176732"
---
# <a name="hover-light"></a><span data-ttu-id="df20e-104">Светлое наведение</span><span class="sxs-lookup"><span data-stu-id="df20e-104">Hover light</span></span>

<span data-ttu-id="df20e-105">[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)— это [система Fluent Design](https://www.microsoft.com/design/fluent/) парадигма, которая имитирует [точку](https://docs.unity3d.com/Manual/Lighting.html) , наведя на нее курсор мыши рядом с поверхностью объекта.</span><span class="sxs-lookup"><span data-stu-id="df20e-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="df20e-106">Как правило, для далекого взаимодействия приложение может управлять свойствами светлого наведения с помощью [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) компонента.</span><span class="sxs-lookup"><span data-stu-id="df20e-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="df20e-107">чтобы на материал повлияло [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) использование шейдера " *смешанная реальность" набор средств/Standard* , необходимо использовать построитель текстуры, а свойство « *светлое* » должно быть включено.</span><span class="sxs-lookup"><span data-stu-id="df20e-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="df20e-108">Шейдер МРТК/Standard поддерживает [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) по умолчанию до двух, но будет масштабироваться для поддержки четырех, а затем десять раз по мере добавления источников света в сцену.</span><span class="sxs-lookup"><span data-stu-id="df20e-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="df20e-109">Примеры</span><span class="sxs-lookup"><span data-stu-id="df20e-109">Examples</span></span>

<span data-ttu-id="df20e-110">В большинстве сцен в МРТК используется [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="df20e-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="df20e-111">Наиболее распространенный вариант использования можно найти в МРТК/SDK/Features/UX/Prefabs/Cursors/Дефаулткурсор. prefab</span><span class="sxs-lookup"><span data-stu-id="df20e-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="df20e-112">В сцене **ховерлигхтексамплес** также демонстрируется использование [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) поведения, и их можно найти по адресу: мртк/examples/демонстрации/стандардшадер/сцены/</span><span class="sxs-lookup"><span data-stu-id="df20e-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="df20e-113">Расширенные возможности использования</span><span class="sxs-lookup"><span data-stu-id="df20e-113">Advanced Usage</span></span>

<span data-ttu-id="df20e-114">Только десять [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) может загорать [материал](https://docs.unity3d.com/ScriptReference/Material.html) за раз.</span><span class="sxs-lookup"><span data-stu-id="df20e-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="df20e-115">Если в проекте требуется более десяти [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) для влияния на [материал](https://docs.unity3d.com/ScriptReference/Material.html) , приведенный ниже пример кода демонстрирует, как это добиться.</span><span class="sxs-lookup"><span data-stu-id="df20e-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="df20e-116">Наличие большого количества [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) освещения [материала](https://docs.unity3d.com/ScriptReference/Material.html) увеличит инструкции шейдера пикселей и повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="df20e-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="df20e-117">**Проведите профилирование этих изменений в проекте.**</span><span class="sxs-lookup"><span data-stu-id="df20e-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="df20e-118">*Как увеличить число доступных [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) с десяти до двенадцати.*</span><span class="sxs-lookup"><span data-stu-id="df20e-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> <span data-ttu-id="df20e-119">Если Unity регистрирует предупреждение, аналогичное приведенному ниже, необходимо перезапустить Unity, чтобы изменения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="df20e-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="df20e-120">См. также:</span><span class="sxs-lookup"><span data-stu-id="df20e-120">See also</span></span>

* [<span data-ttu-id="df20e-121">Стандартный шейдер MRTK</span><span class="sxs-lookup"><span data-stu-id="df20e-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
