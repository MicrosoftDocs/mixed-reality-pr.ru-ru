---
title: прогрессиндикатор
description: Обзор индикатора выполнения в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110123"
---
# <a name="progress-indicators"></a><span data-ttu-id="39217-104">Индикаторы хода выполнения</span><span class="sxs-lookup"><span data-stu-id="39217-104">Progress Indicators</span></span>

![Индикаторы хода выполнения](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="39217-106">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="39217-106">Example scene</span></span>

<span data-ttu-id="39217-107">Примеры использования индикаторов хода выполнения можно найти в `ProgressIndicatorExamples` сцене.</span><span class="sxs-lookup"><span data-stu-id="39217-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="39217-108">В этой сцене демонстрируется каждый индикатор хода выполнения Prefabs, входящий в состав пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="39217-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="39217-109">Здесь также показано, как использовать индикаторы хода выполнения в сочетании с некоторыми распространенными асинхронными задачами, такими как загрузка сцены.</span><span class="sxs-lookup"><span data-stu-id="39217-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="39217-110">Пример: открытие, обновление & закрытие индикатора хода выполнения</span><span class="sxs-lookup"><span data-stu-id="39217-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="39217-111">Индикаторы хода выполнения реализуют [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="39217-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="39217-112">Этот интерфейс можно получить из GameObject с помощью `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="39217-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="39217-113">`IProgressIndicator.OpenAsync()`Методы и `IProgressIndicator.CloseAsync()` возвращают [задачи](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="39217-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="39217-114">Рекомендуется ожидать эти задачи в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="39217-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="39217-115">Prefabs индикатор хода выполнения по умолчанию МРТК должен быть неактивным при помещении в сцену.</span><span class="sxs-lookup"><span data-stu-id="39217-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="39217-116">Когда их `IProgressIndicator.OpenAsync()` методы называются индикаторами хода выполнения, они автоматически активируются и деактивируются объекты gameobject.</span><span class="sxs-lookup"><span data-stu-id="39217-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="39217-117">(Этот шаблон не является обязательным для интерфейса Ипрогрессиндикатор.)</span><span class="sxs-lookup"><span data-stu-id="39217-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="39217-118">Присвойте `Progress` свойству индикатора значение от 0-1, чтобы обновить ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="39217-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="39217-119">Установите его `Message` свойство, чтобы обновить отображаемое сообщение.</span><span class="sxs-lookup"><span data-stu-id="39217-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="39217-120">Различные реализации могут отображать это содержимое различными способами.</span><span class="sxs-lookup"><span data-stu-id="39217-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="39217-121">Состояния индикатора</span><span class="sxs-lookup"><span data-stu-id="39217-121">Indicator states</span></span>

<span data-ttu-id="39217-122">`State`Свойство индикатора определяет, какие операции являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="39217-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="39217-123">Вызов недопустимого метода, как правило, приводит к тому, что индикатор сообщает об ошибке и не принимает никаких действий.</span><span class="sxs-lookup"><span data-stu-id="39217-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="39217-124">Состояние</span><span class="sxs-lookup"><span data-stu-id="39217-124">State</span></span> | <span data-ttu-id="39217-125">Допустимые операции</span><span class="sxs-lookup"><span data-stu-id="39217-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="39217-126">`AwaitTransitionAsync()` можно использовать, чтобы убедиться, что индикатор полностью открыт или закрыт перед использованием.</span><span class="sxs-lookup"><span data-stu-id="39217-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
