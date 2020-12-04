---
title: Взгляните на входные данные в нереальном режиме
description: Руководство по настройке входных данных взгляда для HoloLens и нереального модуля
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens 2, отслеживание взгляда, ввод с экрана, подключенный головной дисплей, нереалный механизм, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578893"
---
# <a name="gaze-input"></a><span data-ttu-id="1c99a-104">Входные данные взгляда</span><span class="sxs-lookup"><span data-stu-id="1c99a-104">Gaze Input</span></span>

<span data-ttu-id="1c99a-105">Взгляните, чтобы указать, что видят пользователи.</span><span class="sxs-lookup"><span data-stu-id="1c99a-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="1c99a-106">С помощью камер отслеживания взгляда на устройстве можно найти луч в нереальном пространстве, соответствующем текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="1c99a-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="1c99a-107">Включение отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="1c99a-107">Enabling eye tracking</span></span>

- <span data-ttu-id="1c99a-108">В **параметрах проекта > HoloLens** включите функцию **ввода** с помощью средства входа.</span><span class="sxs-lookup"><span data-stu-id="1c99a-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Снимок экрана возможностей настройки проекта HoloLens с выделенными входными данными Взгляните](images/unreal-gaze-img-01.png)

- <span data-ttu-id="1c99a-110">Создание нового субъекта и его добавление в сцену</span><span class="sxs-lookup"><span data-stu-id="1c99a-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="1c99a-111">Отслеживание глаз HoloLens в нереальном режиме имеет один луч для обоих глаз, а не два луча, необходимых для отслеживания стереоскопик, что не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="1c99a-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="1c99a-112">Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="1c99a-112">Using eye tracking</span></span>

<span data-ttu-id="1c99a-113">Сначала убедитесь, что устройство поддерживает отслеживание взгляда с помощью функции Исэйетраккерконнектед.</span><span class="sxs-lookup"><span data-stu-id="1c99a-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="1c99a-114">Если возвращается значение true, вызовите Жетгазедата, чтобы найти место, где глаза пользователя просматриваются во время текущего кадра:</span><span class="sxs-lookup"><span data-stu-id="1c99a-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Схема подключенной функции отслеживания взгляда](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="1c99a-116">Точка с фиксацией и значение достоверности недоступны в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c99a-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="1c99a-117">Чтобы найти, что видят пользователи, используйте источник и направление взгляда в трассировке строки.</span><span class="sxs-lookup"><span data-stu-id="1c99a-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="1c99a-118">Начало этого вектора — это источник взгляда, а элемент End — источник и направление взгляда, умноженное на нужное расстояние:</span><span class="sxs-lookup"><span data-stu-id="1c99a-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Схема функции получения данных об взгляде](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="1c99a-120">Получение ориентации головного экрана</span><span class="sxs-lookup"><span data-stu-id="1c99a-120">Getting head orientation</span></span>

<span data-ttu-id="1c99a-121">Кроме того, можно использовать поворот ХМД для представления направления заголовка пользователя.</span><span class="sxs-lookup"><span data-stu-id="1c99a-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="1c99a-122">Это не требует возможности ввода с помощью взгляда, но не даст никаких сведений об отслеживании взгляда.</span><span class="sxs-lookup"><span data-stu-id="1c99a-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="1c99a-123">Для получения правильных выходных данных необходимо добавить ссылку на проект в качестве международного контекста:</span><span class="sxs-lookup"><span data-stu-id="1c99a-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="1c99a-124">Получение данных ХМД доступно только в нереальных 4,26 и более.</span><span class="sxs-lookup"><span data-stu-id="1c99a-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Схема функции Get Хмддата](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="1c99a-126">Использование C++</span><span class="sxs-lookup"><span data-stu-id="1c99a-126">Using C++</span></span> 

- <span data-ttu-id="1c99a-127">В файле build.cs игры добавьте "Эйетраккер" в список Публикдепенденцимодуленамес:</span><span class="sxs-lookup"><span data-stu-id="1c99a-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="1c99a-128">В «файл/новый класс C++» создайте новый субъект C++ с именем «Эйетраккер».</span><span class="sxs-lookup"><span data-stu-id="1c99a-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="1c99a-129">Решение Visual Studio откроется в новом классе Эйетраккер.</span><span class="sxs-lookup"><span data-stu-id="1c99a-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="1c99a-130">Выполните сборку и запустите, чтобы открыть нереальную игру с новым субъектом Эйетраккер.</span><span class="sxs-lookup"><span data-stu-id="1c99a-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="1c99a-131">Выполните поиск строки "Эйетраккер" в окне "место субъектов".</span><span class="sxs-lookup"><span data-stu-id="1c99a-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="1c99a-132">Перетащите этот класс в окно игры, чтобы добавить его в проект:</span><span class="sxs-lookup"><span data-stu-id="1c99a-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Снимок экрана субъекта с открытым окном субъекта](images/unreal-gaze-img-06.png)

- <span data-ttu-id="1c99a-134">В Эйетраккер. cpp добавьте включения для Эйетраккерфунктионлибрари и Дравдебугхелперс:</span><span class="sxs-lookup"><span data-stu-id="1c99a-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="1c99a-135">В такте убедитесь, что устройство поддерживает отслеживание глаз с помощью Уэйетраккерфунктионлибрари:: Исэйетраккерконнектед.</span><span class="sxs-lookup"><span data-stu-id="1c99a-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="1c99a-136">Затем найдите начало и конец луча для трассировки строки из Уэйетраккерфунктионлибрари:: Жетгазедата:</span><span class="sxs-lookup"><span data-stu-id="1c99a-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="1c99a-137">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="1c99a-137">Next Development Checkpoint</span></span>

<span data-ttu-id="1c99a-138">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="1c99a-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1c99a-139">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="1c99a-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c99a-140">Отслеживание рук</span><span class="sxs-lookup"><span data-stu-id="1c99a-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="1c99a-141">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="1c99a-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c99a-142">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="1c99a-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1c99a-143">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="1c99a-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c99a-144">См. также статью</span><span class="sxs-lookup"><span data-stu-id="1c99a-144">See also</span></span>
* [<span data-ttu-id="1c99a-145">Калибровка</span><span class="sxs-lookup"><span data-stu-id="1c99a-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="1c99a-146">Комфорт</span><span class="sxs-lookup"><span data-stu-id="1c99a-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="1c99a-147">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="1c99a-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="1c99a-148">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="1c99a-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
