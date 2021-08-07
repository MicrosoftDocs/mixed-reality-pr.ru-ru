---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212337"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

МРТК в настоящее время не имеет вспомогательных функций для режима РЕПРОЕКЦИИ. Дополнительные сведения см. на одной из других вкладок.

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Режим перепроекции можно настроить, задав для [ксрдисплайсубсистем. репрожектионмоде](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) соответствующее значение.

Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [репрожектионмоде. ориентатиононли](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Режим перепроекции можно настроить, задав для [холографиксеттингс. репрожектионмоде](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) соответствующее значение.

Например, если вы создаете [интерфейс только для ориентации](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) с содержимым, защищенным телом (например, видео с 360-градусами), можно явно задать для режима РЕПРОЕКЦИИ значение только ориентация, задав для него значение [холографикрепрожектионмоде. ориентатиононли](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).