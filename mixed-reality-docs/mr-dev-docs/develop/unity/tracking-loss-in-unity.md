---
title: Потеря слежения в Unity
description: Узнайте, как обрабатывать потери отслеживания вручную и по умолчанию в приложении Unity Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, отслеживание потерь, отслеживание потерь изображения, опрос, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009854"
---
# <a name="tracking-loss-in-unity"></a>Потеря слежения в Unity

Если устройство не может располагаться в мире, в приложении происходит «отслеживание потерь». По умолчанию Unity приостанавливает цикл обновления и отображает изображение заставки для пользователя во время отслеживания. После повторного выполнения отслеживания изображение-заставка исчезает, а цикл обновления продолжается.

В качестве альтернативы пользователь может вручную справиться с этим переходом, отменив параметр. При отслеживании потерь все содержимое становится заблокированным, если не выполняется никаких действий по его обработке.

## <a name="default-handling"></a>Обработка по умолчанию

Цикл обновления и все сообщения и события будут прекращаться по умолчанию на время отслеживания потерь. В то же время для пользователя будет отображаться изображение. Вы можете настроить этот образ, перейдя в меню "Правка"->"Параметры" — >"проигрыватель", щелкнув изображение заставки и задав образ потери отслеживания с помощью.

## <a name="manual-handling"></a>Ручная обработка

Чтобы вручную обрабатывалась трассировка, необходимо вернуться к разделу **изменение**  >  **параметров проекта параметры**  >  **проигрывателя**  >  **универсальная платформа Windows параметры**  >  **изображение заставки**  >  **Windows holographic** и снять флажок "при отслеживании потерь приостановить и показывать изображение". После этого необходимо выполнить обработку изменений отслеживания с помощью API, указанных ниже.

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип:** *ворлдманажер*

* Менеджер по всему миру предоставляет событие для обнаружения потерянных или полученных данных отслеживания (*ворлдманажер. онпоситионаллокаторстатечанжед*) и свойство для запроса текущего состояния (*ворлдманажер. State).*
* Если отслеживание состояния не активно, Камера не будет переводиться в виртуальном мире даже при преобразовании пользователя. Объекты больше не будут соответствовать ни одному физическому расположению, а все будут отображаться как заблокированные.

При самостоятельной обработке изменений необходимо либо опросить свойство State для каждого кадра, либо обработать событие *онпоситионаллокаторстатечанжед* .

### <a name="polling"></a>Опрос

Наиболее важное состояние — *поситионаллокаторстате. Active*. Это означает, что отслеживание полностью работоспособно. Любое другое состояние приведет к появлению в основной камере только ротации. Пример:

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

Более удобно, что вы также можете подписываться на *онпоситионаллокаторстатечанжед* для управления переходами:

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

## <a name="see-also"></a>См. также раздел

* [Обработка потерь отслеживания в DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
