---
title: Неблизкое освещение
description: Документация по неблизкому освещению с примерами в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176387"
---
# <a name="proximity-light"></a><span data-ttu-id="370d9-104">Неблизкое освещение</span><span class="sxs-lookup"><span data-stu-id="370d9-104">Proximity light</span></span>

<span data-ttu-id="370d9-105">[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)— это [система Fluent Design](https://www.microsoft.com/design/fluent/) парадигма, которая имитирует "градиентная точка инверсии", наведя указатель мыши на поверхность объекта.</span><span class="sxs-lookup"><span data-stu-id="370d9-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="370d9-106">Часто используется для практических взаимодействий, поэтому приложение может управлять свойствами светлого объекта с помощью [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) компонента.</span><span class="sxs-lookup"><span data-stu-id="370d9-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="370d9-107">чтобы получить материал, на который влияет [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) использование шейдера *смешанной реальности набор средств/Standard* , необходимо включить построитель текстуры, а свойство « *освещение* » должно быть включено.</span><span class="sxs-lookup"><span data-stu-id="370d9-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="370d9-108">[`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)По умолчанию поддерживаются до двух.</span><span class="sxs-lookup"><span data-stu-id="370d9-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="370d9-109">Примеры</span><span class="sxs-lookup"><span data-stu-id="370d9-109">Examples</span></span>

<span data-ttu-id="370d9-110">В большинстве сцен в МРТК используется [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .</span><span class="sxs-lookup"><span data-stu-id="370d9-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="370d9-111">Наиболее распространенный вариант использования можно найти в МРТК/SDK/Features/UX/Prefabs/Cursors/Финжеркурсор. prefab</span><span class="sxs-lookup"><span data-stu-id="370d9-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="370d9-112">Расширенные возможности использования</span><span class="sxs-lookup"><span data-stu-id="370d9-112">Advanced Usage</span></span>

<span data-ttu-id="370d9-113">По умолчанию только два из них [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) могут загорать [материал](https://docs.unity3d.com/ScriptReference/Material.html) за раз.</span><span class="sxs-lookup"><span data-stu-id="370d9-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="370d9-114">Если проект требует более двух, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) чтобы зависеть от [материала](https://docs.unity3d.com/ScriptReference/Material.html) , приведенный ниже пример кода демонстрирует, как это добиться.</span><span class="sxs-lookup"><span data-stu-id="370d9-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="370d9-115">Наличие большого количества [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) освещения [материала](https://docs.unity3d.com/ScriptReference/Material.html) увеличит инструкции шейдера пикселей и повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="370d9-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="370d9-116">Проведите профилирование этих изменений в проекте.</span><span class="sxs-lookup"><span data-stu-id="370d9-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="370d9-117">*Как увеличить число доступных [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) от двух до четырех.*</span><span class="sxs-lookup"><span data-stu-id="370d9-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="370d9-118">Если Unity регистрирует предупреждение, аналогичное приведенному ниже, необходимо перезапустить Unity, чтобы изменения вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="370d9-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="370d9-119">См. также:</span><span class="sxs-lookup"><span data-stu-id="370d9-119">See also</span></span>

* [<span data-ttu-id="370d9-120">Стандартный шейдер MRTK</span><span class="sxs-lookup"><span data-stu-id="370d9-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
