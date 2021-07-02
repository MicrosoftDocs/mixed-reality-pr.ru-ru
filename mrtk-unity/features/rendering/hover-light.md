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
# <a name="hover-light"></a>Светлое наведение

[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)— это [система Fluent Design](https://www.microsoft.com/design/fluent/) парадигма, которая имитирует [точку](https://docs.unity3d.com/Manual/Lighting.html) , наведя на нее курсор мыши рядом с поверхностью объекта. Как правило, для далекого взаимодействия приложение может управлять свойствами светлого наведения с помощью [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) компонента.

чтобы на материал повлияло [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) использование шейдера " *смешанная реальность" набор средств/Standard* , необходимо использовать построитель текстуры, а свойство « *светлое* » должно быть включено.

> [!Note]
> Шейдер МРТК/Standard поддерживает [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) по умолчанию до двух, но будет масштабироваться для поддержки четырех, а затем десять раз по мере добавления источников света в сцену.

## <a name="examples"></a>Примеры

В большинстве сцен в МРТК используется [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . Наиболее распространенный вариант использования можно найти в МРТК/SDK/Features/UX/Prefabs/Cursors/Дефаулткурсор. prefab

В сцене **ховерлигхтексамплес** также демонстрируется использование [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) поведения, и их можно найти по адресу: мртк/examples/демонстрации/стандардшадер/сцены/

## <a name="advanced-usage"></a>Расширенные возможности использования

Только десять [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) может загорать [материал](https://docs.unity3d.com/ScriptReference/Material.html) за раз. Если в проекте требуется более десяти [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) для влияния на [материал](https://docs.unity3d.com/ScriptReference/Material.html) , приведенный ниже пример кода демонстрирует, как это добиться.

> [!Note]
> Наличие большого количества [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) освещения [материала](https://docs.unity3d.com/ScriptReference/Material.html) увеличит инструкции шейдера пикселей и повлияет на производительность. **Проведите профилирование этих изменений в проекте.**

*Как увеличить число доступных [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) с десяти до двенадцати.*

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
> Если Unity регистрирует предупреждение, аналогичное приведенному ниже, необходимо перезапустить Unity, чтобы изменения вступили в силу.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>См. также:

* [Стандартный шейдер MRTK](mrtk-standard-shader.md)
