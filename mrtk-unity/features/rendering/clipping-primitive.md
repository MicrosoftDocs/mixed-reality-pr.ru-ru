---
title: Примитив обрезки
description: Документация по примитивам обрезки с примерами в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, отсеченный примитив,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176739"
---
# <a name="clipping-primitive"></a><span data-ttu-id="760d1-104">Примитив обрезки</span><span class="sxs-lookup"><span data-stu-id="760d1-104">Clipping primitive</span></span>

<span data-ttu-id="760d1-105">[`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive)Поведения позволяют выполнять [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) обрезание, и фигурную обрезку с возможностью указать, какая сторона примитива будет обрезаться (внутри или снаружи) при использовании с шейдерами мртк.</span><span class="sxs-lookup"><span data-stu-id="760d1-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![примитив обрезки приспособлений](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="760d1-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Использование инструкций [Clip/Discard](https://developer.download.nvidia.com/cg/clip.html) в шейдере и отключение возможности Unity для пакетной обрезки модулей подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="760d1-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="760d1-108">При использовании примитивов обрезки учитывайте эти последствия.</span><span class="sxs-lookup"><span data-stu-id="760d1-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="760d1-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) и [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) можно использовать для простого управления обрезкими свойств примитивов.</span><span class="sxs-lookup"><span data-stu-id="760d1-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="760d1-110">Используйте эти компоненты со следующими шейдерами, чтобы использовать сценарии обрезки.</span><span class="sxs-lookup"><span data-stu-id="760d1-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="760d1-111">*смешанная реальность набор средств/Standard*</span><span class="sxs-lookup"><span data-stu-id="760d1-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="760d1-112">*смешанная реальность набор средств/текстмешпро*</span><span class="sxs-lookup"><span data-stu-id="760d1-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="760d1-113">*смешанная реальность набор средств/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="760d1-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="760d1-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="760d1-114">Examples</span></span>

<span data-ttu-id="760d1-115">Сцены **клиппинжексамплес** и **материалгаллери** демонстрируют использование [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) поведения, и их можно найти по адресу: Мртк/examples/демонстрации/стандардшадер/сцены/</span><span class="sxs-lookup"><span data-stu-id="760d1-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="760d1-116">Расширенные возможности использования</span><span class="sxs-lookup"><span data-stu-id="760d1-116">Advanced Usage</span></span>

<span data-ttu-id="760d1-117">По умолчанию только один из них [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) может обрезать модуль [подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html) отчетов за раз.</span><span class="sxs-lookup"><span data-stu-id="760d1-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="760d1-118">Если в проекте требуется больше одного, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) чтобы зависеть от модуля [подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html)  отчетов, в примере кода ниже показано, как добиться этого.</span><span class="sxs-lookup"><span data-stu-id="760d1-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="760d1-119">Наличие нескольких [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) клипов, [обрабатывающих модуль подготовки](https://docs.unity3d.com/ScriptReference/Renderer.html) отчетов, увеличит количество инструкций шейдера пикселей и повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="760d1-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="760d1-120">Проведите профилирование этих изменений в проекте.</span><span class="sxs-lookup"><span data-stu-id="760d1-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="760d1-121">*Как иметь два [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) отрисовки для отрисовки. Например, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) а и в [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) то же время:*</span><span class="sxs-lookup"><span data-stu-id="760d1-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="760d1-122">Приведенное выше изменение повлечет за собой дополнительное время компиляции шейдера.</span><span class="sxs-lookup"><span data-stu-id="760d1-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="760d1-123">*Способ, с помощью которого [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) отрисовывается один из двух клипов. Например, два [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) в то же время:*</span><span class="sxs-lookup"><span data-stu-id="760d1-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

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

<span data-ttu-id="760d1-124">Наконец, добавьте [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) компонент и секондклиппингбокс в сцену и укажите тот же модуль отрисовки для обоих полей.</span><span class="sxs-lookup"><span data-stu-id="760d1-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="760d1-125">Теперь модуль подготовки отчетов должен быть обрезан обоими полями одновременно.</span><span class="sxs-lookup"><span data-stu-id="760d1-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="760d1-126">См. также:</span><span class="sxs-lookup"><span data-stu-id="760d1-126">See also</span></span>

- [<span data-ttu-id="760d1-127">Стандартный шейдер MRTK</span><span class="sxs-lookup"><span data-stu-id="760d1-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
