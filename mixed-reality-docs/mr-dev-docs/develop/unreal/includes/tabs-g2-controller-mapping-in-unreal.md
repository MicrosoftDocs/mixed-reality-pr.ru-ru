---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638725"
---
# <a name="all-platforms"></a>[<span data-ttu-id="08d83-101">Все платформы</span><span class="sxs-lookup"><span data-stu-id="08d83-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="08d83-102">Те же действия и сопоставления осей в параметрах входного проекта игры можно использовать из C++.</span><span class="sxs-lookup"><span data-stu-id="08d83-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="08d83-103">Создание нового класса C++ с помощью файла или нового класса C++...</span><span class="sxs-lookup"><span data-stu-id="08d83-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Создание нового класса C++](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="08d83-105">Создание пешки</span><span class="sxs-lookup"><span data-stu-id="08d83-105">Create a pawn</span></span>

![Создание пешки](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="08d83-107">В решении Visual Studio проекта найдите новый класс пешки и настройте его для ввода.</span><span class="sxs-lookup"><span data-stu-id="08d83-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="08d83-108">Сначала в конструкторе задайте Аутопоссессплайер для первого игрока, чтобы направить входные данные в пешку.</span><span class="sxs-lookup"><span data-stu-id="08d83-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="08d83-109">Затем в Сетупплайеринпуткомпонент привяжите действия и события оси к именам действий из входных параметров проекта.</span><span class="sxs-lookup"><span data-stu-id="08d83-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="08d83-110">Добавьте функции обратного вызова в класс:</span><span class="sxs-lookup"><span data-stu-id="08d83-110">Add the callback functions to the class:</span></span>

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* <span data-ttu-id="08d83-111">Обновите заголовок пешки с помощью определений функций обратного вызова:</span><span class="sxs-lookup"><span data-stu-id="08d83-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="08d83-112">Скомпилируйте из Visual Studio, чтобы запустить редактор с новой пешкой.</span><span class="sxs-lookup"><span data-stu-id="08d83-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="08d83-113">Перетащите пешку из браузера содержимого в игру, и пешка теперь будет выполнять обратные вызовы при нажатии клавиши ВВОД.</span><span class="sxs-lookup"><span data-stu-id="08d83-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="08d83-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="08d83-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="08d83-115">При использовании событий осей на панели стик имя события оси должно заканчиваться на "_X" или "_Y", соответствующим используемому ключу.</span><span class="sxs-lookup"><span data-stu-id="08d83-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Использование событий аналогового стика](../images/reverb-g2-img-09.png)

<span data-ttu-id="08d83-117">Наконец, зарегистрируйте действия в игре с помощью Стеамвр, используя кнопки **повторно создать манифест действия** и **повторно создать привязки контроллеров** в параметрах проекта > Steam VR input.</span><span class="sxs-lookup"><span data-stu-id="08d83-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Регистрация действий в параметрах проекта](../images/reverb-g2-img-10.png)

