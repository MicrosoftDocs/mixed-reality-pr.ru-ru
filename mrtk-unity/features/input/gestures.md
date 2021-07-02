---
title: Жесты
description: Докумментатион для жестов и его событий в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, жесты,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176885"
---
# <a name="gestures"></a>Жесты

Жесты являются событиями ввода на основе человеческого руки. Существует два типа устройств, которые вызывают события ввода жестов в МРТК:

- Windows Mixed Reality такие устройства, как HoloLens. Это описывает сжатие движений ("Air TAP") и жесты касания и удерживания.

  дополнительные сведения о HoloLens жестах см. в [документации по жестам Windows Mixed Reality](/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)заключает XR Unity в оболочку [. Головк. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) для использования событий жестов Unity с устройств HoloLens.

- Устройства сенсорного экрана.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) заключает [класс касаний Unity](https://docs.unity3d.com/ScriptReference/Touch.html) , который поддерживает физические экраны сенсорного ввода.

оба источника входных данных используют Параметры профиле _жеста_ для преобразования событий касаний и жестов Unity соответственно в [действия ввода](input-actions.md)мртк. этот профиль можно найти в профиле _входной системы Параметры_ .

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>События жестов

События жестов получаются путем реализации одного из интерфейсов обработчика жестов: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) или [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (см. таблицу [обработчиков событий](input-events.md)).

Пример реализации обработчика событий жеста см. в [примере сцены](#example-scene) .

При реализации универсальной версии события *онжестурекомплетед* и *онжестуреупдатед* могут принимать типизированные данные следующих типов:

- `Vector2` — жест 2D-расположения. Создается сенсорными экранами для информирования о них [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` — жест трехмерного позиционирования. создано HoloLens для информирования о:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) события манипуляции
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) события навигации
- `Quaternion` — жест поворота объемного изображения. Доступен для пользовательских источников входных данных, но в данный момент не создается ни одним из существующих.
- `MixedRealityPose` — Объединенный жест трехмерного расположения и поворота. Доступен для пользовательских источников входных данных, но в данный момент не создается ни одним из существующих.

## <a name="order-of-events"></a>Порядок событий

В зависимости от введенных пользователем данных существует две основные цепочки событий:

- "Удержание":
    1. Удержание касания:
        - начать _манипуляцию_
    1. Держите касание за пределами [холдстартдуратион](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - начать _удержание_
    1. Отпустите кнопку:
        - завершить _удержание_
        - завершение _манипуляции_

- "Переместить":
    1. Удержание касания:
        - начать _манипуляцию_
    1. Держите касание за пределами [холдстартдуратион](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - начать _удержание_
    1. Переместить руку за пределы [навигатионстартсрешолд](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):
        - отменить _удержание_
        - начать _навигацию_
    1. Отпустите кнопку:
        - завершение _манипуляции_
        - завершить _навигацию_

## <a name="example-scene"></a>Пример сцены

Сцена **хандинтерактионжестуривентсексампле** (Assets/Мртк/examples/Хандтраккинг/сцены) показывает, как использовать результат указателя для порождения объекта в месте попадания.

`GestureTester`Скрипт (Assets/мртк/examples/хандтраккинг/script) — это пример реализации для визуализации событий жестов через объекты gameobject. Функции обработчика изменяют цвет объектов индикаторов и отображают Последнее записанное событие в текстовых объектах сцены.
