---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717780"
---
# <a name="426"></a>[4.26](#tab/426)

Чтобы получить данные для луча, следует использовать функцию получения данных контроллера движения из предыдущего раздела. Возвращаемая структура содержит два параметра, которые можно использовать для создания руки луча — **нацеленности** и **ротации**. Эти параметры формируют луч, направленный уступом. Вы должны взять их и найти голограмму, на которую указывает.

Ниже приведен пример того, как определить, попадает ли рука-Ray в мини-приложение, и задать пользовательский результат попадания:

![Схема функции получения данных контроллера движения](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Чтобы использовать лучи в схемах, выполните поиск любых действий в **Windows Mixed Reality ХМД**:

![BP](../images/unreal/hand-rays-bp.png)

Чтобы получить доступ к ним в C++, включите `WindowsMixedRealityFunctionLibrary.h` в начало файла вызывающего кода.

### <a name="enum"></a>Перечисление

Кроме того, у вас есть доступ к входным вариантам в **ехмдинпутконтроллербуттонс**, которые можно использовать в схемах:

![Кнопки контроллера ввода](../images/unreal/input-controller-buttons.png)

Для доступа в C++ используйте `EHMDInputControllerButtons` Класс Enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Ниже приведена разбивка двух применимых вариантов перечисления.

* **SELECT** — пользователь активировал событие SELECT.
    * Активируется в HoloLens 2, выполняя касание, взгляните и зафиксировать, или выполнив команду "Select" с включенным [голосовым входом](../unreal-voice-input.md) .
* Пользовательское событие **, активируемое с** учетом продачи.
    * Активируется в HoloLens 2, закрывая пальцы пользователя на голограмме.

Вы можете получить доступ к состоянию отслеживания сетки руки в C++ с помощью `EHMDTrackingStatus` перечисления, показанного ниже:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Ниже приведена разбивка двух применимых вариантов перечисления.

* **Ноттраккед** — рука не отображается
* С **отслеживанием** — рука полностью отслеживание

### <a name="struct"></a>Структура

Структура Поинтерпосеинфо может предоставить сведения о следующих данных:

* **Источник** — источник руки
* **Направление** — направление руки
* **Вверх** — вверх в виде вектора руки
* **Orientation** — ориентация кватерниона
* **Состояние отслеживания** — текущее состояние отслеживания

Доступ к структуре Поинтерпосеинфо можно получить с помощью схем, как показано ниже:

![BP, сведения о указателе](../images/unreal/pointer-pose-info-bp.png)

Или с + +:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Функции

Все перечисленные ниже функции можно вызывать для каждого кадра, что позволяет выполнять непрерывный мониторинг.

1. **Получить сведения о выведении указателя** возвращает полные сведения о направлении ладони в текущем кадре.

Схем

![Получить сведения о указателе](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. Если рука проблюдается в текущем кадре, **будет** возвращено значение true.

Схем

![Есть BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. При **нажатии кнопки выбрать** возвращается значение true, если пользователь активировал выбор в текущем кадре.

Схем

![Выбрана нажатая нажимаемая BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Нажата **кнопка "** возвращает значение true", если событие или кнопка активированы в текущем кадре.

Схем

![Нажата кнопка BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Получение состояния отслеживания контроллера** возвращает состояние отслеживания в текущем кадре.

Схем

![Получить состояние отслежения контроллера](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```