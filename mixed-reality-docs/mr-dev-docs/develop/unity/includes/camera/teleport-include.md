---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636374"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

МРТК предоставляет встроенную [систему телепортироваться](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) , которая автоматически работает во множестве рук и контроллеров.

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Мы рекомендуем использовать МРТКную реализацию для переноса.
Если вы решили не использовать МРТК, Unity предоставляет реализацию телетранспорта в [наборе средств XR для взаимодействия](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую. Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject. Это эквивалентно Плайспаце МРТК.

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Мы рекомендуем использовать МРТКную реализацию для переноса.
Если вы решили реализовать собственное, то помните, что вы не можете перемещать камеру напрямую. Из-за управления камерой с помощью камеры для отслеживания головок необходимо предоставить камере родительский элемент в иерархии и переместить этот GameObject. Это эквивалентно Плайспаце МРТК.