---
title: Индикатор хода выполнения
description: Обзор индикатора выполнения в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176572"
---
# <a name="progress-indicator"></a>Индикатор хода выполнения

![Индикаторы хода выполнения](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Пример сцены

Примеры использования индикаторов хода выполнения можно найти в `ProgressIndicatorExamples` сцене. В этой сцене демонстрируется каждый индикатор хода выполнения Prefabs, входящий в состав пакета SDK. Здесь также показано, как использовать индикаторы хода выполнения в сочетании с некоторыми распространенными асинхронными задачами, такими как загрузка сцены.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Пример: открытие, обновление & закрытие индикатора хода выполнения

Индикаторы хода выполнения реализуют [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) интерфейс. Этот интерфейс можно получить из GameObject с помощью `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

`IProgressIndicator.OpenAsync()`Методы и `IProgressIndicator.CloseAsync()` возвращают [задачи](xref:System.Threading.Tasks.Task). Рекомендуется ожидать эти задачи в асинхронном методе.

Prefabs индикатор хода выполнения по умолчанию МРТК должен быть неактивным при помещении в сцену. Когда их `IProgressIndicator.OpenAsync()` методы называются индикаторами хода выполнения, они автоматически активируются и деактивируются объекты gameobject. (Этот шаблон не является обязательным для интерфейса Ипрогрессиндикатор.)

Присвойте `Progress` свойству индикатора значение от 0-1, чтобы обновить ход выполнения. Установите его `Message` свойство, чтобы обновить отображаемое сообщение. Различные реализации могут отображать это содержимое различными способами.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>Состояния индикатора

`State`Свойство индикатора определяет, какие операции являются допустимыми. Вызов недопустимого метода, как правило, приводит к тому, что индикатор сообщает об ошибке и не принимает никаких действий.

Состояние | Допустимые операции
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` можно использовать, чтобы убедиться, что индикатор полностью открыт или закрыт перед использованием.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
