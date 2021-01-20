---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581103"
---
# <a name="426"></a>[4.26](#tab/426)

Иерархия описана в разделе `EHandKeypoint` enum:

![Изображение параметров руки кэйпоинт хранится](../images/hand-keypoint-bp.png)

Все эти данные можно получить из руки пользователя с помощью функции **получения данных контроллера движения** . Эта функция возвращает структуру **ксрмотионконтроллердата** . Ниже приведен пример скрипта схемы, который анализирует структуру Ксрмотионконтроллердата для получения Объединенных расположений и рисует отладочную систему координат в каждом расположении соединения.

![Схема функции получения данных с данными о получении, подключенной к трассировке строки по функциям канала](../images/unreal-hand-tracking-img-03.png)

Важно проверить, является ли структура допустимой, и что она является рукой. В противном случае вы можете получить неопределенное поведение в доступе к позициям, поворотам и массивам радиусов.

# <a name="425"></a>[4.25](#tab/425)

`EWMRHandKeypoint`Перечисление описывает иерархию костей руки. Вы можете найти все руки кэйпоинт, перечисленные в ваших чертежах:

![Кэйпоинт BP](../images/hand-keypoint-bp.png)

Полное перечисление C++ показано ниже.
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Числовые значения для каждого варианта перечисления можно найти в таблице [Windows. восприятие. People. ханджоинткинд](/uwp/api/windows.perception.people.handjointkind) .

### <a name="supporting-hand-tracking"></a>Поддержка отслеживания

Вы можете использовать отслеживание вручную в схемах, добавив **поддержку отслеживания вручную** для **отслеживания > Windows Mixed Reality**:

![BP для отслеживания](../images/unreal/hand-tracking-bp.png)

Эта функция возвращает значение `true` , если отслеживание поддерживается на устройстве, и `false` Если отслеживание недоступно.

![Поддерживает отправную очередь для отслеживания](../images/unreal/supports-hand-tracking-bp.png)

C++:

Добавьте `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Отслеживание отслеживания

**Жесанджоинттрансформ** можно использовать для возврата пространственных данных из руки. Данные обновляются каждым кадром, но если вы находитесь внутри фрейма, возвращаемые значения кэшируются. В этой функции не рекомендуется использовать интенсивную логику для повышения производительности.

![Преобразование «получение соединения с рукой»](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Ниже приведена декомпозиция параметров функции Жесанджоинттрансформ:

* **Рука** — может быть пользователем слева или справа.
* **Кэйпоинт** — кость руки.
* **Transform** — координаты и ориентация базы данных-основания кости. Можно запросить основу следующей кости, чтобы получить данные преобразования для конца кости. Специальная кость TIP дает окончание дистал.
* * * Радиус — радиус основы кости.
* * * Возвращаемое значение — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.