---
title: Взгляните на входные данные в нереальном режиме
description: Руководство по настройке входных данных взгляда для HoloLens и нереального модуля
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens 2, отслеживание взгляда, ввод с экрана, подключенный головной дисплей, нереалный механизм, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925984"
---
# <a name="gaze-input"></a><span data-ttu-id="eed6a-104">Входные данные взгляда</span><span class="sxs-lookup"><span data-stu-id="eed6a-104">Gaze Input</span></span>

<span data-ttu-id="eed6a-105">Взгляните на ввод в приложениях смешанной реальности, чтобы узнать, что пользователи видят.</span><span class="sxs-lookup"><span data-stu-id="eed6a-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="eed6a-106">Когда камеры отслеживания взгляда на устройстве сопоставляются с лучами в нереальном пространстве, данные о пользователе становятся доступными.</span><span class="sxs-lookup"><span data-stu-id="eed6a-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="eed6a-107">Взгляд можно использовать как в чертежах, так и в C++, и является основным компонентом для таких ядер, как взаимодействие объектов, Поиск и управление камерой.</span><span class="sxs-lookup"><span data-stu-id="eed6a-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="eed6a-108">Включение отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="eed6a-108">Enabling eye tracking</span></span>

- <span data-ttu-id="eed6a-109">В **параметрах проекта > HoloLens** включите функцию **ввода** с помощью средства входа.</span><span class="sxs-lookup"><span data-stu-id="eed6a-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Снимок экрана возможностей настройки проекта HoloLens с выделенными входными данными Взгляните](images/unreal-gaze-img-01.png)

- <span data-ttu-id="eed6a-111">Создание нового субъекта и его добавление в сцену</span><span class="sxs-lookup"><span data-stu-id="eed6a-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="eed6a-112">Отслеживание глаз HoloLens в нереальном режиме имеет один луч для обоих глаз.</span><span class="sxs-lookup"><span data-stu-id="eed6a-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="eed6a-113">Отслеживание стереоскопик, для которого требуется два луча, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="eed6a-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="eed6a-114">Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="eed6a-114">Using eye tracking</span></span>

<span data-ttu-id="eed6a-115">Сначала убедитесь, что устройство поддерживает отслеживание взгляда с помощью функции **исэйетраккерконнектед** .</span><span class="sxs-lookup"><span data-stu-id="eed6a-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="eed6a-116">Если функция возвращает значение true, вызовите **жетгазедата** , чтобы найти, где глаза пользователя просматриваются в текущем кадре:</span><span class="sxs-lookup"><span data-stu-id="eed6a-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Схема подключенной функции отслеживания взгляда](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="eed6a-118">Точка с фиксацией и значение достоверности недоступны в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="eed6a-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="eed6a-119">Используйте источник и направление взгляда в трассировке строки, чтобы точно определить, где находятся ваши пользователи.</span><span class="sxs-lookup"><span data-stu-id="eed6a-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="eed6a-120">Значение взгляда является вектором, начинающимся с источника взгляда и заканчивая началом координат, а также направлением взгляда, умноженным на расстояние трассировки строки:</span><span class="sxs-lookup"><span data-stu-id="eed6a-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Схема функции получения данных об взгляде](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="eed6a-122">Получение ориентации головного экрана</span><span class="sxs-lookup"><span data-stu-id="eed6a-122">Getting head orientation</span></span>

<span data-ttu-id="eed6a-123">Также можно использовать поворот головного дисплея (ХМД) для представления направления заголовка пользователя.</span><span class="sxs-lookup"><span data-stu-id="eed6a-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="eed6a-124">Вы можете получить направление заголовка пользователей, не включив функцию ввода с клавиатуры, но не будете получать сведения об отслеживании взгляда.</span><span class="sxs-lookup"><span data-stu-id="eed6a-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="eed6a-125">Добавьте ссылку на проект в качестве контекста мира, чтобы получить правильные выходные данные:</span><span class="sxs-lookup"><span data-stu-id="eed6a-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="eed6a-126">Получение данных ХМД доступно только в нереальных 4,26 и более.</span><span class="sxs-lookup"><span data-stu-id="eed6a-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Схема функции Get Хмддата](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="eed6a-128">Использование C++</span><span class="sxs-lookup"><span data-stu-id="eed6a-128">Using C++</span></span>

- <span data-ttu-id="eed6a-129">В файле **Build.CS** вашей игры добавьте **Эйетраккер** в список **публикдепенденцимодуленамес** :</span><span class="sxs-lookup"><span data-stu-id="eed6a-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="eed6a-130">В **файле или новом классе c++** создайте новый субъект c++ с именем **эйетраккер**</span><span class="sxs-lookup"><span data-stu-id="eed6a-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="eed6a-131">В решении Visual Studio откроется новый класс Эйетраккер.</span><span class="sxs-lookup"><span data-stu-id="eed6a-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="eed6a-132">Выполните сборку и запустите, чтобы открыть нереальную игру с новым субъектом Эйетраккер.</span><span class="sxs-lookup"><span data-stu-id="eed6a-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="eed6a-133">Выполните поиск строки "Эйетраккер" в окне " **место субъектов** " и перетащите класс в окно игры, чтобы добавить его в проект:</span><span class="sxs-lookup"><span data-stu-id="eed6a-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Снимок экрана субъекта с открытым окном субъекта](images/unreal-gaze-img-06.png)

- <span data-ttu-id="eed6a-135">В **эйетраккер. cpp** добавьте включения для **эйетраккерфунктионлибрари** и **дравдебугхелперс**:</span><span class="sxs-lookup"><span data-stu-id="eed6a-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="eed6a-136">Убедитесь, что устройство поддерживает отслеживание взгляда с помощью **уэйетраккерфунктионлибрари:: исэйетраккерконнектед** , прежде чем пытаться получить данные о взгляде.</span><span class="sxs-lookup"><span data-stu-id="eed6a-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="eed6a-137">Если отслеживание взгляда поддерживается, найдите начало и конец луча для трассировки строки из **уэйетраккерфунктионлибрари:: жетгазедата**.</span><span class="sxs-lookup"><span data-stu-id="eed6a-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="eed6a-138">После этого можно создать вектор взгляда и передать его содержимое в **линетрацесинглебичаннел** для отладки любых результатов попадания луча:</span><span class="sxs-lookup"><span data-stu-id="eed6a-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="eed6a-139">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="eed6a-139">Next Development Checkpoint</span></span>

<span data-ttu-id="eed6a-140">Если вы подготовились к нереальному пути разработки, мы собрались изучить основные конструктивные блоки МРТК.</span><span class="sxs-lookup"><span data-stu-id="eed6a-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="eed6a-141">Отсюда можно перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="eed6a-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eed6a-142">Отслеживание рук</span><span class="sxs-lookup"><span data-stu-id="eed6a-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="eed6a-143">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="eed6a-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eed6a-144">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="eed6a-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="eed6a-145">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="eed6a-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="eed6a-146">См. также статью</span><span class="sxs-lookup"><span data-stu-id="eed6a-146">See also</span></span>
* [<span data-ttu-id="eed6a-147">Калибровка</span><span class="sxs-lookup"><span data-stu-id="eed6a-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="eed6a-148">Комфорт</span><span class="sxs-lookup"><span data-stu-id="eed6a-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="eed6a-149">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="eed6a-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="eed6a-150">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="eed6a-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
