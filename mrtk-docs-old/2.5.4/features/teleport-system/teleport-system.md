---
title: TeleportSystemOverview
description: Общие сведения о включении и выключении системы телепортации в MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK, система телепортации
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197644"
---
# <a name="teleport-system"></a>Система телепортации

Система телепортации — это подсистема Mixed Reality Toolkit (MRTK), которая выполняет перенос пользователя, когда приложение использует непрозрачное отображение. В интерфейсах AR, например HoloLens, система телепортации неактивна. В интерфейсах виртуальных шлемов, например OpenVR, Windows Mixed Reality, систему телепортации можно включить.

## <a name="enabling-and-disabling"></a>Включение и выключение

Систему телепортации можно включить или выключить, используя флажок в ее профиле.
Для этого выберите объект MixedRealityToolkit в сцене, нажмите "Телепортация", а затем установите флажок "Включить систему телепортации".

Это можно сделать и во время работы:

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

Система телепортации предоставляет события с помощью интерфейса [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler), чтобы передавать сигналы о начале, завершении или отмене действий телепортации.
Дополнительные сведения о работе событий и о связанных с ними полезных данных см. в документации по соответствующему API.

## <a name="usage"></a>Использование

### <a name="how-to-register-for-teleportation-events"></a>Как регистрировать события телепортации

На примере кода ниже показано, как создать прослушиватель MonoBehaviour для событий телепортации. Для этого кода предполагается, что система телепортации включена.

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
