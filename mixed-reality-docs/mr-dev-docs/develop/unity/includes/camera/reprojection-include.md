---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636362"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

МРТК в настоящее время не имеет вспомогательных функций для режима РЕПРОЕКЦИИ. Дополнительные сведения см. на одной из других вкладок.

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Режим перепроекции можно настроить, задав для [ксрдисплайсубсистем. репрожектионмоде](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) соответствующее значение.

Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [репрожектионмоде. ориентатиононли](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Режим перепроекции можно настроить, задав для [холографиксеттингс. репрожектионмоде](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) соответствующее значение.

Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [холографикрепрожектионмоде. ориентатиононли](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).