---
title: Экземпляр материала
description: Документация по экземпляру материала и его применению в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, материалинстанце,
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176727"
---
# <a name="material-instance"></a><span data-ttu-id="187c8-104">Экземпляр материала</span><span class="sxs-lookup"><span data-stu-id="187c8-104">Material instance</span></span>

<span data-ttu-id="187c8-105">[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)Поведение АИДЕС в процессе отслеживания времени существования материала экземпляра и автоматически уничтожает экземпляры материалов для пользователя.</span><span class="sxs-lookup"><span data-stu-id="187c8-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="187c8-106">Этот служебный компонент можно использовать в качестве замены для модуля [подготовки. материалов](https://docs.unity3d.com/ScriptReference/Renderer-material.html) или модуля подготовки отчетов. [материалы](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span><span class="sxs-lookup"><span data-stu-id="187c8-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="187c8-107">[Материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) являются предпочтительными по сравнению с созданием экземпляров материалов, но не всегда доступны во всех сценариях.</span><span class="sxs-lookup"><span data-stu-id="187c8-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="187c8-108">Почему может использоваться модуль [подготовки отчетов. материал](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ?</span><span class="sxs-lookup"><span data-stu-id="187c8-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="187c8-109">Если добавить приведенный ниже код в сцену Unity и попадание в память воспроизведения, будет по-прежнему вырасти и выигрывает:</span><span class="sxs-lookup"><span data-stu-id="187c8-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="187c8-110">Описанное выше поведение **приведет к сбою Unity** при слишком длительном запуске.</span><span class="sxs-lookup"><span data-stu-id="187c8-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="187c8-111">В качестве альтернативы попробуйте использовать [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) поведение:</span><span class="sxs-lookup"><span data-stu-id="187c8-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="187c8-112">Использование</span><span class="sxs-lookup"><span data-stu-id="187c8-112">Usage</span></span>

<span data-ttu-id="187c8-113">При вызове модуля [подготовки к просмотру Unity. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html)Unity автоматически создает экземпляры новых материалов.</span><span class="sxs-lookup"><span data-stu-id="187c8-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="187c8-114">Он несет ответственность за уничтожение материалов, когда материал больше не нужен или объект Game уничтожается.</span><span class="sxs-lookup"><span data-stu-id="187c8-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="187c8-115">[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)Такое поведение помогает избежать утечек ресурсов и обеспечивает согласованность путей выделения материалов во время редактирования и выполнения.</span><span class="sxs-lookup"><span data-stu-id="187c8-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="187c8-116">Если [материалпропертиблокк](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) не может использоваться и материал должен быть экземпляром, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) его можно использовать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="187c8-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="187c8-117">Если нескольким объектам требуется владение экземпляром материала, лучше использовать явный владелец для отслеживания ссылок.</span><span class="sxs-lookup"><span data-stu-id="187c8-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="187c8-118">(Необязательный интерфейс [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) с именем существует для телеметрическую с владельцем.) Ниже приведен пример использования:</span><span class="sxs-lookup"><span data-stu-id="187c8-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="187c8-119">Дополнительные сведения см. в примере использования, продемонстрированном в описании [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) поведения.</span><span class="sxs-lookup"><span data-stu-id="187c8-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="187c8-120">См. также:</span><span class="sxs-lookup"><span data-stu-id="187c8-120">See also</span></span>

* [<span data-ttu-id="187c8-121">Стандартный шейдер MRTK</span><span class="sxs-lookup"><span data-stu-id="187c8-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
