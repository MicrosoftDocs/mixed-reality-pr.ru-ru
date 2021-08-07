---
title: MaterialInstance
description: Документация по экземпляру материала и его применению в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, материалинстанце,
ms.openlocfilehash: 6d9a2a35a009bfce1fcfae15000ea02c47be637a8c5a483254ea30d9948922e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210054"
---
# <a name="material-instance"></a>MaterialInstance

[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)Поведение АИДЕС в процессе отслеживания времени существования материала экземпляра и автоматически уничтожает экземпляры материалов для пользователя. Этот служебный компонент можно использовать в качестве замены для модуля [подготовки. материалов](https://docs.unity3d.com/ScriptReference/Renderer-material.html) или модуля подготовки отчетов. [материалы](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).

> [!NOTE]
> [Материалпропертиблоккс](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) являются предпочтительными по сравнению с созданием экземпляров материалов, но не всегда доступны во всех сценариях.

Почему может использоваться модуль [подготовки отчетов. материал](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ? Если добавить приведенный ниже код в сцену Unity и попадание в память воспроизведения, будет по-прежнему вырасти и выигрывает:

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
> Описанное выше поведение **приведет к сбою Unity** при слишком длительном запуске.

В качестве альтернативы попробуйте использовать [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) поведение:

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

## <a name="usage"></a>Использование

При вызове модуля [подготовки к просмотру Unity. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html)Unity автоматически создает экземпляры новых материалов. Он несет ответственность за уничтожение материалов, когда материал больше не нужен или объект Game уничтожается. [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)Такое поведение помогает избежать утечек ресурсов и обеспечивает согласованность путей выделения материалов во время редактирования и выполнения.

Если [материалпропертиблокк](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) не может использоваться и материал должен быть экземпляром, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) его можно использовать следующим образом:

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

Если нескольким объектам требуется владение экземпляром материала, лучше использовать явный владелец для отслеживания ссылок. (Необязательный интерфейс [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) с именем существует для телеметрическую с владельцем.) Ниже приведен пример использования:

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

Дополнительные сведения см. в примере использования, продемонстрированном в описании [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) поведения.

## <a name="see-also"></a>См. также раздел

* [Стандартный шейдер МРТК](mrtk-standard-shader.md)
