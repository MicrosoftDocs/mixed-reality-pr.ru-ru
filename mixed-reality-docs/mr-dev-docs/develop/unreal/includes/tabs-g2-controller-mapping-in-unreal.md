---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638725"
---
# <a name="all-platforms"></a>[Все платформы](#tab/all)

Те же действия и сопоставления осей в параметрах входного проекта игры можно использовать из C++.

1. Создание нового класса C++ с помощью файла или нового класса C++...

![Создание нового класса C++](../images/reverb-g2-img-11.png)

2. Создание пешки

![Создание пешки](../images/reverb-g2-img-12.png)

3. В решении Visual Studio проекта найдите новый класс пешки и настройте его для ввода.
* Сначала в конструкторе задайте Аутопоссессплайер для первого игрока, чтобы направить входные данные в пешку.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* Затем в Сетупплайеринпуткомпонент привяжите действия и события оси к именам действий из входных параметров проекта.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Добавьте функции обратного вызова в класс:

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

* Обновите заголовок пешки с помощью определений функций обратного вызова:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Скомпилируйте из Visual Studio, чтобы запустить редактор с новой пешкой. Перетащите пешку из браузера содержимого в игру, и пешка теперь будет выполнять обратные вызовы при нажатии клавиши ВВОД.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

При использовании событий осей на панели стик имя события оси должно заканчиваться на "_X" или "_Y", соответствующим используемому ключу.

![Использование событий аналогового стика](../images/reverb-g2-img-09.png)

Наконец, зарегистрируйте действия в игре с помощью Стеамвр, используя кнопки **повторно создать манифест действия** и **повторно создать привязки контроллеров** в параметрах проекта > Steam VR input.

![Регистрация действий в параметрах проекта](../images/reverb-g2-img-10.png)

