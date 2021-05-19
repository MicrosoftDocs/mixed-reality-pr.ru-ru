---
title: ClippingPrimitive
description: Документация по примитивам обрезки с примерами в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, отсеченный примитив,
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145207"
---
# <a name="clipping-primitive"></a>ClippingPrimitive

[`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive)Поведения позволяют выполнять [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) обрезание, и фигурную обрезку с возможностью указать, какая сторона примитива будет обрезаться (внутри или снаружи) при использовании с шейдерами мртк.

![примитив обрезки приспособлений](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Использование инструкций [Clip/Discard](https://developer.download.nvidia.com/cg/clip.html) в шейдере и отключение возможности Unity для пакетной обрезки модулей подготовки отчетов. При использовании примитивов обрезки учитывайте эти последствия.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) и [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) можно использовать для простого управления обрезкими свойств примитивов. Используйте эти компоненты со следующими шейдерами, чтобы использовать сценарии обрезки.

- *Набор средств для смешанной реальности и Стандартный*
- *Набор средств для смешанной реальности или Текстмешпро*
- *Набор средств для смешанной реальности или Text3DShader*

## <a name="examples"></a>Примеры

Сцены **клиппинжексамплес** и **материалгаллери** демонстрируют использование [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) поведения, и их можно найти по адресу: Мртк/examples/демонстрации/стандардшадер/сцены/

## <a name="advanced-usage"></a>Расширенные возможности использования

По умолчанию только один из них [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) может обрезать модуль [подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html) отчетов за раз. Если в проекте требуется больше одного, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) чтобы зависеть от модуля [подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html)  отчетов, в примере кода ниже показано, как добиться этого.

> [!NOTE]
> Наличие нескольких [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) клипов, [обрабатывающих модуль подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html) отчетов, увеличит количество инструкций шейдера пикселей и повлияет на производительность. Проведите профилирование этих изменений в проекте.

*Как иметь два [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) отрисовки для отрисовки. Например, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) а и в [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) то же время:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> Приведенное выше изменение повлечет за собой дополнительное время компиляции шейдера.

*Способ, с помощью которого [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) отрисовывается один из двух клипов. Например, два [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) в то же время:*

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

Наконец, добавьте [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) компонент и секондклиппингбокс в сцену и укажите тот же модуль отрисовки для обоих полей. Теперь модуль подготовки отчетов должен быть обрезан обоими полями одновременно.

## <a name="see-also"></a>См. также

- [Стандартный шейдер MRTK](mrtk-standard-shader.md)
