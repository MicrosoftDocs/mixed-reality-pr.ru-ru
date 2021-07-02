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
# <a name="proximity-light"></a>Неблизкое освещение

[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)— это [система Fluent Design](https://www.microsoft.com/design/fluent/) парадигма, которая имитирует "градиентная точка инверсии", наведя указатель мыши на поверхность объекта. Часто используется для практических взаимодействий, поэтому приложение может управлять свойствами светлого объекта с помощью [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) компонента.

чтобы получить материал, на который влияет [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) использование шейдера *смешанной реальности набор средств/Standard* , необходимо включить построитель текстуры, а свойство « *освещение* » должно быть включено.

> [!NOTE]
> [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)По умолчанию поддерживаются до двух.

## <a name="examples"></a>Примеры

В большинстве сцен в МРТК используется [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . Наиболее распространенный вариант использования можно найти в МРТК/SDK/Features/UX/Prefabs/Cursors/Финжеркурсор. prefab

## <a name="advanced-usage"></a>Расширенные возможности использования

По умолчанию только два из них [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) могут загорать [материал](https://docs.unity3d.com/ScriptReference/Material.html) за раз. Если проект требует более двух, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) чтобы зависеть от [материала](https://docs.unity3d.com/ScriptReference/Material.html) , приведенный ниже пример кода демонстрирует, как это добиться.

> [!NOTE]
> Наличие большого количества [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) освещения [материала](https://docs.unity3d.com/ScriptReference/Material.html) увеличит инструкции шейдера пикселей и повлияет на производительность. Проведите профилирование этих изменений в проекте.

*Как увеличить число доступных [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) от двух до четырех.*

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
> Если Unity регистрирует предупреждение, аналогичное приведенному ниже, необходимо перезапустить Unity, чтобы изменения вступили в силу.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>См. также:

* [Стандартный шейдер MRTK](mrtk-standard-shader.md)
