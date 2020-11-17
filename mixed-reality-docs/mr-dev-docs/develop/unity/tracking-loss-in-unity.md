---
title: Потеря слежения в Unity
description: Обработка потерь отслеживания в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, отслеживание потерь, отслеживание потерь изображения, опрос, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 52b81069e6b9f94a2a6a4fb552be4234cf43d1f0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678423"
---
# <a name="tracking-loss-in-unity"></a>Потеря слежения в Unity

Если устройство не может располагать себя в мире, в приложении происходит «отслеживание потерь». По умолчанию Unity приостанавливает цикл обновления и отображает для пользователя изображение заставки. Когда отслеживание восстанавливается, изображение-заставка исчезает, а цикл обновления продолжается.

В качестве альтернативы пользователь может вручную справиться с этим переходом, отменив параметр. При отслеживании потерь все содержимое становится заблокированным, если не выполняется никаких действий по его обработке.

## <a name="default-handling"></a>Обработка по умолчанию

По умолчанию цикл обновления приложения, а также все сообщения и события будут прекращаться на время отслеживания потери. В то же время для пользователя будет отображаться изображение. Вы можете настроить этот образ, перейдя в меню "Правка"->"Параметры" — >"проигрыватель", щелкнув изображение заставки и задав образ потери отслеживания с помощью.

## <a name="manual-handling"></a>Ручная обработка

Чтобы вручную обрабатывалась трассировка, необходимо вернуться к разделу **изменение**  >  **параметров проекта параметры**  >  **проигрывателя**  >  **универсальная платформа Windows параметры**  >  **изображение заставки**  >  **Windows holographic** и снять флажок "при отслеживании потерь приостановить и показывать изображение". После этого необходимо выполнить обработку изменений отслеживания с помощью API, указанных ниже.

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип:** *ворлдманажер*

* Менеджер по всему миру предоставляет событие для обнаружения потерянных или полученных данных отслеживания (*ворлдманажер. онпоситионаллокаторстатечанжед*) и свойство для запроса текущего состояния (*ворлдманажер. State).*
* Если отслеживание состояния неактивно, Камера не будет переводиться в виртуальном мире даже при преобразовании пользователя. Это означает, что объекты больше не будут соответствовать ни одному физическому расположению, а все будут отображаться как заблокированные.

При обработке собственных изменений необходимо опросить свойство State для каждого кадра или обработать событие *онпоситионаллокаторстатечанжед* .

### <a name="polling"></a>Опрос

Наиболее важное состояние — *поситионаллокаторстате. Active* . Это означает, что отслеживание полностью работоспособно. Любое другое состояние приведет к появлению в основной камере только ротации. Пример:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Обработка события Онпоситионаллокаторстатечанжед

Кроме того, можно также подписываться на *онпоситионаллокаторстатечанжед* для выполнения переходов:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>См. также
* [Обработка потерь отслеживания в DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
