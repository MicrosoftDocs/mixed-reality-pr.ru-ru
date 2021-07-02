---
title: Система телепортируйтесь
description: Общие сведения о включении и отключении системы телепортируйтесь в МРТК
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, система телепортируйтесь,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176181"
---
# <a name="teleport-system"></a>Система телепортирования.

Система телепортируйтесь — это подсистема МРТК, которая обрабатывает телеперенос пользователя, когда приложение использует непрозрачное отображение. для работы с AR (например, HoloLens) система телетранспорта неактивна. Для ХМДных возможностей (Опенвр, ВМР) можно включить систему телепортируйтесь.

## <a name="enabling-and-disabling"></a>Включение и отключение

Систему телепортируйтесь можно включить или отключить, установив флажок в его профиле.
Это можно сделать, выбрав объект Микседреалититулкит в сцене, щелкнув "телепортируйтесь", а затем установив флажок "включить телепортировать систему".

Это также можно сделать во время выполнения:

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a>События

Система телепортируйтесь предоставляет события через [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) интерфейс для предоставления сигналов о начале, окончании или отмене действий телепортируйтесь.
Дополнительные сведения об механике событий и связанных с ними полезных данных см. в документации по связанному API.

## <a name="usage"></a>Использование

### <a name="how-to-register-for-teleportation-events"></a>Регистрация для мероприятий по сопортам

В приведенном ниже коде показано, как создать Недействительное поведение, которое будет прослушивать события телепередачи. В этом коде предполагается, что система телепортируйтесь включена.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a>Телеперенос на МРТК

Чтобы телепортируйтесь с контроллером на устройствах MR с конфигурациями по умолчанию, используйте аналоговый стик. Чтобы телепортируйтесь с поднятыми руки, нарисуйте жест с помощью своего карманного ПК с помощью индекса и пальца, чтобы выполнить телепортироваться через фигуру указателя. Чтобы телепортируйтесь с моделированием ввода, ознакомьтесь с нашей обновленной [документацией по службе моделирования ввода](../input-simulation/input-simulation-service.md).

  ![Жест телепортируйтесь](../images/teleport/handteleport.gif)
