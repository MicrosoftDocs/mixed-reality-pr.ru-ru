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
# <a name="progress-indicator"></a><span data-ttu-id="37de7-104">Индикатор хода выполнения</span><span class="sxs-lookup"><span data-stu-id="37de7-104">Progress indicator</span></span>

![Индикаторы хода выполнения](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="37de7-106">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="37de7-106">Example scene</span></span>

<span data-ttu-id="37de7-107">Примеры использования индикаторов хода выполнения можно найти в `ProgressIndicatorExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="37de7-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="37de7-108">В этой сцене демонстрируется каждый индикатор хода выполнения Prefabs, входящий в состав пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="37de7-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="37de7-109">Здесь также показано, как использовать индикаторы хода выполнения в сочетании с некоторыми распространенными асинхронными задачами, такими как загрузка сцены.</span><span class="sxs-lookup"><span data-stu-id="37de7-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="37de7-110">Пример: открытие, обновление & закрытие индикатора хода выполнения</span><span class="sxs-lookup"><span data-stu-id="37de7-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="37de7-111">Индикаторы хода выполнения реализуют [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="37de7-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="37de7-112">Этот интерфейс можно получить из GameObject с помощью `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="37de7-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="37de7-113">`IProgressIndicator.OpenAsync()`Методы и `IProgressIndicator.CloseAsync()` возвращают [задачи](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="37de7-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="37de7-114">Рекомендуется ожидать эти задачи в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="37de7-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="37de7-115">Prefabs индикатор хода выполнения по умолчанию МРТК должен быть неактивным при помещении в сцену.</span><span class="sxs-lookup"><span data-stu-id="37de7-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="37de7-116">Когда их `IProgressIndicator.OpenAsync()` методы называются индикаторами хода выполнения, они автоматически активируются и деактивируются объекты gameobject.</span><span class="sxs-lookup"><span data-stu-id="37de7-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="37de7-117">(Этот шаблон не является обязательным для интерфейса Ипрогрессиндикатор.)</span><span class="sxs-lookup"><span data-stu-id="37de7-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="37de7-118">Присвойте `Progress` свойству индикатора значение от 0-1, чтобы обновить ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="37de7-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="37de7-119">Установите его `Message` свойство, чтобы обновить отображаемое сообщение.</span><span class="sxs-lookup"><span data-stu-id="37de7-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="37de7-120">Различные реализации могут отображать это содержимое различными способами.</span><span class="sxs-lookup"><span data-stu-id="37de7-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="37de7-121">Состояния индикатора</span><span class="sxs-lookup"><span data-stu-id="37de7-121">Indicator states</span></span>

<span data-ttu-id="37de7-122">`State`Свойство индикатора определяет, какие операции являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="37de7-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="37de7-123">Вызов недопустимого метода, как правило, приводит к тому, что индикатор сообщает об ошибке и не принимает никаких действий.</span><span class="sxs-lookup"><span data-stu-id="37de7-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="37de7-124">Состояние</span><span class="sxs-lookup"><span data-stu-id="37de7-124">State</span></span> | <span data-ttu-id="37de7-125">Допустимые операции</span><span class="sxs-lookup"><span data-stu-id="37de7-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="37de7-126">`AwaitTransitionAsync()` можно использовать, чтобы убедиться, что индикатор полностью открыт или закрыт перед использованием.</span><span class="sxs-lookup"><span data-stu-id="37de7-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
