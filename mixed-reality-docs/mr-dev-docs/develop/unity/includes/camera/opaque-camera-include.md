---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636365"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

МРТК будет автоматически выполнять определенные настройки камеры в зависимости от [конфигурации в профиле системы камеры](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Пространство имен:** *Microsoft. микседреалити. Toolkit. камерасистем*<br>
**Тип:** *микседреалитикамерасистем*

Чтобы проверить непрозрачность камеры, система Микседреалитикамера имеет [ `IsOpaque` свойство](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Пространство имен:** *UnityEngine. XR*<br>
**Тип:** *ксрдисплайсубсистем*

Вы можете использовать код скрипта, чтобы определить во время выполнения, является ли гарнитура впечатляющим или holographic, проверив [дисплайопакуе](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) на активном [ксрдисплайсубсистем](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип:** *холографиксеттингс*

Вы можете использовать код скрипта, чтобы определить во время выполнения, является ли гарнитура увлекательной или holographic, проверив [холографиксеттингс. исдисплайопакуе](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).