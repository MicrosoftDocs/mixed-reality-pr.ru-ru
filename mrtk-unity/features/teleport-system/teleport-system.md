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
# <a name="teleport-system"></a><span data-ttu-id="ce216-104">Система телепортирования.</span><span class="sxs-lookup"><span data-stu-id="ce216-104">Teleport system</span></span>

<span data-ttu-id="ce216-105">Система телепортируйтесь — это подсистема МРТК, которая обрабатывает телеперенос пользователя, когда приложение использует непрозрачное отображение.</span><span class="sxs-lookup"><span data-stu-id="ce216-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="ce216-106">для работы с AR (например, HoloLens) система телетранспорта неактивна.</span><span class="sxs-lookup"><span data-stu-id="ce216-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="ce216-107">Для ХМДных возможностей (Опенвр, ВМР) можно включить систему телепортируйтесь.</span><span class="sxs-lookup"><span data-stu-id="ce216-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="ce216-108">Включение и отключение</span><span class="sxs-lookup"><span data-stu-id="ce216-108">Enabling and disabling</span></span>

<span data-ttu-id="ce216-109">Систему телепортируйтесь можно включить или отключить, установив флажок в его профиле.</span><span class="sxs-lookup"><span data-stu-id="ce216-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="ce216-110">Это можно сделать, выбрав объект Микседреалититулкит в сцене, щелкнув "телепортируйтесь", а затем установив флажок "включить телепортировать систему".</span><span class="sxs-lookup"><span data-stu-id="ce216-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="ce216-111">Это также можно сделать во время выполнения:</span><span class="sxs-lookup"><span data-stu-id="ce216-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="ce216-112">События</span><span class="sxs-lookup"><span data-stu-id="ce216-112">Events</span></span>

<span data-ttu-id="ce216-113">Система телепортируйтесь предоставляет события через [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) интерфейс для предоставления сигналов о начале, окончании или отмене действий телепортируйтесь.</span><span class="sxs-lookup"><span data-stu-id="ce216-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="ce216-114">Дополнительные сведения об механике событий и связанных с ними полезных данных см. в документации по связанному API.</span><span class="sxs-lookup"><span data-stu-id="ce216-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="ce216-115">Использование</span><span class="sxs-lookup"><span data-stu-id="ce216-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="ce216-116">Регистрация для мероприятий по сопортам</span><span class="sxs-lookup"><span data-stu-id="ce216-116">How to register for teleportation events</span></span>

<span data-ttu-id="ce216-117">В приведенном ниже коде показано, как создать Недействительное поведение, которое будет прослушивать события телепередачи.</span><span class="sxs-lookup"><span data-stu-id="ce216-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="ce216-118">В этом коде предполагается, что система телепортируйтесь включена.</span><span class="sxs-lookup"><span data-stu-id="ce216-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="ce216-119">Телеперенос на МРТК</span><span class="sxs-lookup"><span data-stu-id="ce216-119">Teleporting on MRTK</span></span>

<span data-ttu-id="ce216-120">Чтобы телепортируйтесь с контроллером на устройствах MR с конфигурациями по умолчанию, используйте аналоговый стик.</span><span class="sxs-lookup"><span data-stu-id="ce216-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="ce216-121">Чтобы телепортируйтесь с поднятыми руки, нарисуйте жест с помощью своего карманного ПК с помощью индекса и пальца, чтобы выполнить телепортироваться через фигуру указателя.</span><span class="sxs-lookup"><span data-stu-id="ce216-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="ce216-122">Чтобы телепортируйтесь с моделированием ввода, ознакомьтесь с нашей обновленной [документацией по службе моделирования ввода](../input-simulation/input-simulation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ce216-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Жест телепортируйтесь](../images/teleport/handteleport.gif)