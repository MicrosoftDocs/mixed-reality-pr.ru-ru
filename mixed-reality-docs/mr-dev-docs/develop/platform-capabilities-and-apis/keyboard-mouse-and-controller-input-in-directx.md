---
title: Ввод с помощью клавиатуры, мыши и контроллера в DirectX
description: объясняется, как создать приложение для Windows Mixed Reality, которое использует клавиатуру, мышь и игровые контроллеры.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, клавиатура, мышь, игровой контроллер, контроллер xbox, HoloLens, настольный компьютер, пошаговое руководство, пример кода
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244178"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Ввод с помощью клавиатуры, мыши и контроллера в DirectX

> [!NOTE]
> Эта статья связана с устаревшими собственными API-интерфейсами WinRT.  Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](../native/openxr-getting-started.md)**.

клавиатуры, мыши и игровые контроллеры могут быть полезными формами ввода для Windows Mixed Reality устройств. Bluetooth клавиатуры и мыши поддерживаются в HoloLens, для использования с отладкой приложения или в качестве альтернативной формы ввода. Windows Mixed Reality также поддерживает впечатляющие головные телефоны, подключенные к компьютерам. это значит, что мышь, клавиатуры и игровые контроллеры были исторически.

чтобы использовать ввод с клавиатуры на HoloLens, свяжите Bluetoothную клавиатуру с устройством или используйте виртуальный ввод через портал Windows устройств. чтобы использовать ввод с клавиатуры во время людьми Windows Mixed Reality иммерсивное гарнитуру, присвойте фокус ввода смешанной реальности, поместив устройство или используя сочетание клавиш Windows ключ + Y. помните, что приложения, предназначенные для HoloLens, должны предоставлять функциональные возможности без подключения к этим устройствам.
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](../native/creating-a-holographic-directx-project.md).  Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.

## <a name="subscribe-for-corewindow-input-events"></a>Подписка на события ввода CoreWindow

### <a name="keyboard-input"></a>Ввод с клавиатуры

в шаблоне Windows holographic приложение включает обработчик событий для ввода с клавиатуры, как и любое другое приложение UWP. Приложение использует входные данные клавиатуры так же, как и в Windows Mixed Reality.

Из Аппвиев. cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Виртуальный ввод с клавиатуры
для впечатляющих головных телефонов настольных систем можно поддерживать виртуальные клавиатуры, подготовленные к просмотру, Windows в иммерсивное представление путем реализации **коретекстедитконтекст**. это позволяет Windows понять состояние собственных текстовых полей, отображаемых в приложении, поэтому виртуальная клавиатура может правильно дополнять текст.

Дополнительные сведения о реализации поддержки Коретекстедитконтекст см. в [примере коретекстедитконтекст](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Ввод с помощью мыши

Вы также можете использовать ввод с помощью мыши, используя обработчики событий ввода UWP CoreWindow. ниже показано, как изменить шаблон Windows holographic приложение для поддержки щелчков мыши так же, как нажатые жесты. После внесения этого изменения щелкните мышью, когда людьми иммерсивное устройство гарнитуры изменит расположение Куба.

> [!NOTE]
> Приложения UWP также могут получать необработанные ТОЧЕЧные данные для мыши с помощью API [мауседевице](/uwp/api/Windows.Devices.Input.MouseDevice) .

Начните с объявления нового обработчика Онпоинтерпрессед в Аппвиев. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

В Аппвиев. cpp добавьте следующий код в Сетвиндов:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Затем установите это определение для Онпоинтерпрессед в нижней части файла:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

Только что добавленный обработчик событий является транзитным классом шаблона Main. Давайте изменим класс main для поддержки этого транзитного класса. Добавьте это объявление общедоступного метода в заголовочный файл:

```
// Handle mouse input.
       void OnPointerPressed();
```

Вам потребуется также эта переменная члена Private:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Наконец, мы будем обновлять класс Main с помощью новой логики для поддержки щелчков мыши. Начните с добавления этого обработчика событий. Обязательно обновите имя класса:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Теперь в методе Update замените существующую логику для получения указателя a следующим:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Перекомпиляция и повторное развертывание. обратите внимание, что щелчок мыши теперь перемещает куб в имеющуюся гарнитуру или HoloLens с подключенной мышью по bluetooth.

### <a name="game-controller-support"></a>Поддержка игрового контроллера

игровые контроллеры могут быть увлекательным и удобным способом предоставления пользователям возможности управления эффектными Windows Mixed Reality.

 Добавьте следующие объявления закрытых членов в класс заголовка для основного файла:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Инициализируйте события игрового планшета и все подключенные к нему игровые планшеты в конструкторе основного класса:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Добавьте эти обработчики событий в основной класс. Обязательно обновите имя класса:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Наконец, обновите логику ввода, чтобы распознать изменения в состоянии контроллера. Здесь мы используем ту же переменную m_pointerPressed, описанную в разделе выше, для добавления событий мыши. Добавьте его в метод Update, непосредственно перед тем, как он проверяет наличие Спатиалпоинтерпосе:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Не забудьте отменить регистрацию событий при очистке основного класса:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Перекомпиляция и повторное развертывание. Теперь можно присоединить или связать игровой контроллер и использовать его для перемещения вращающегося куба.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Важные рекомендации по вводу с клавиатуры и мыши

существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens – это устройство, которое использует в основном на естественном вводе пользователя, и что доступно на компьютерах с поддержкой Windows Mixed Reality.
* Вы не можете полагаться на ввод с клавиатуры или с помощью мыши. Все функции вашего приложения должны работать с помощью взгляда, жеста и речевого ввода.
* при присоединении Bluetooth клавиатуры может быть полезно включить ввод с клавиатуры для любого текста, который может запрашивать приложение. Например, это может быть отличным дополнением для диктовки.
* Когда дело доходит до разработки приложения, не полагайтесь на то, что (например,) трассе и мышь для поиска в игре. HoloLens предназначен для того, чтобы пользователь просматривает комнату. В этом случае пользователь управляет камерой напрямую. Интерфейс для передачи камеры вокруг комнаты с элементами управления перемещением и просмотром не обеспечивает такой же возможности.
* Ввод с клавиатуры — это отличный способ управления отладкой приложения или игрового модуля, особенно потому, что пользователю не нужно использовать клавиатуру. Подключение выполняется так же, как и при использовании API-интерфейсов событий CoreWindow. В этом сценарии вы можете реализовать способ настройки приложения для маршрутизации событий клавиатуры в режим "только входные данные" во время сеансов отладки.
* контроллеры Bluetooth также работают.

## <a name="see-also"></a>См. также раздел
* [Аксессуары к оборудованию](../../discover/hardware-accessories.md)