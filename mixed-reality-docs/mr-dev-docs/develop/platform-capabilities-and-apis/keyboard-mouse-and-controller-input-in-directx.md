---
title: Ввод с помощью клавиатуры, мыши и контроллера в DirectX
description: В этой статье объясняется, как создать приложение для Windows Mixed Reality, которое использует клавиатуру, мышь и игровые контроллеры.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, клавиатура, мышь, игровой контроллер, контроллер Xbox, HoloLens, Настольный компьютер, пошаговое руководство, пример кода
ms.openlocfilehash: 47d5ac7c7517d607d29d004497f62ac0755c3051
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692080"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="99036-104">Ввод с помощью клавиатуры, мыши и контроллера в DirectX</span><span class="sxs-lookup"><span data-stu-id="99036-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="99036-105">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="99036-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="99036-106">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](../native/openxr-getting-started.md)** .</span><span class="sxs-lookup"><span data-stu-id="99036-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="99036-107">Клавиатуры, мыши и игровые контроллеры могут быть полезными в качестве входных данных для устройств Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99036-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="99036-108">Клавиатуры и мыши Bluetooth поддерживаются в HoloLens для использования с отладкой приложения или в качестве альтернативного вида входных данных.</span><span class="sxs-lookup"><span data-stu-id="99036-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="99036-109">Windows Mixed Reality также поддерживает впечатляющие головные телефоны, подключенные к компьютерам, на которых были исторически мышь, клавиатуры и игровые контроллеры.</span><span class="sxs-lookup"><span data-stu-id="99036-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="99036-110">Чтобы использовать ввод с клавиатуры для HoloLens, свяжите клавиатуру Bluetooth с устройством или используйте виртуальный ввод через портал устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="99036-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="99036-111">Чтобы использовать ввод с клавиатуры при людьмиии иммерсивного головной гарнитуры Windows Mixed Reality, присвойте фокус ввода смешанной реальности, поместив устройство или используя сочетание клавиш Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="99036-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="99036-112">Помните, что приложения, предназначенные для HoloLens, должны предоставлять функциональные возможности без подключения к этим устройствам.</span><span class="sxs-lookup"><span data-stu-id="99036-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="99036-113">Фрагменты кода в этой статье в настоящее время демонстрируют использование C++/CX вместо C + +17, совместимого с C++/WinRT, как используется в [шаблоне C++ holographic](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="99036-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="99036-114">Понятия эквивалентны для проекта C++/WinRT, хотя код необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="99036-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="99036-115">Подписка на события ввода CoreWindow</span><span class="sxs-lookup"><span data-stu-id="99036-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="99036-116">Ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="99036-116">Keyboard input</span></span>

<span data-ttu-id="99036-117">В шаблоне приложения Windows holographic мы включаем обработчик событий для ввода с клавиатуры точно так же, как любое другое приложение UWP.</span><span class="sxs-lookup"><span data-stu-id="99036-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="99036-118">Приложение использует входные данные клавиатуры так же, как и в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99036-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="99036-119">Из Аппвиев. cpp:</span><span class="sxs-lookup"><span data-stu-id="99036-119">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="99036-120">Виртуальный ввод с клавиатуры</span><span class="sxs-lookup"><span data-stu-id="99036-120">Virtual keyboard input</span></span>
<span data-ttu-id="99036-121">Для впечатляющих головок настольных компьютеров можно также поддерживать виртуальные клавиатуры, отображаемые Windows, в режиме погружения.</span><span class="sxs-lookup"><span data-stu-id="99036-121">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="99036-122">Для поддержки этой возможности приложение может реализовать **коретекстедитконтекст** .</span><span class="sxs-lookup"><span data-stu-id="99036-122">To support this, your app can implement **CoreTextEditContext** .</span></span> <span data-ttu-id="99036-123">Это позволяет Windows понять состояние собственных текстовых полей, отображаемых в приложении, поэтому виртуальная клавиатура может правильно участвовать в тексте.</span><span class="sxs-lookup"><span data-stu-id="99036-123">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="99036-124">Дополнительные сведения о реализации поддержки Коретекстедитконтекст см. в [примере коретекстедитконтекст](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="99036-124">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="99036-125">Ввод с помощью мыши</span><span class="sxs-lookup"><span data-stu-id="99036-125">Mouse Input</span></span>

<span data-ttu-id="99036-126">Вы также можете использовать ввод с помощью мыши, используя обработчики событий ввода UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="99036-126">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="99036-127">Вот как можно изменить шаблон приложения Windows holographic для поддержки щелчков мыши так же, как нажатые жесты.</span><span class="sxs-lookup"><span data-stu-id="99036-127">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="99036-128">После внесения этого изменения щелкните мышью, когда людьми иммерсивное устройство гарнитуры изменит расположение Куба.</span><span class="sxs-lookup"><span data-stu-id="99036-128">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="99036-129">Обратите внимание, что приложения UWP также могут получать необработанные ТОЧЕЧные данные для мыши с помощью API [мауседевице](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="99036-129">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="99036-130">Начните с объявления нового обработчика Онпоинтерпрессед в Аппвиев. h:</span><span class="sxs-lookup"><span data-stu-id="99036-130">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="99036-131">В Аппвиев. cpp добавьте следующий код в Сетвиндов:</span><span class="sxs-lookup"><span data-stu-id="99036-131">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="99036-132">Затем установите это определение для Онпоинтерпрессед в нижней части файла:</span><span class="sxs-lookup"><span data-stu-id="99036-132">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="99036-133">Только что добавленный обработчик событий является транзитным классом шаблона Main.</span><span class="sxs-lookup"><span data-stu-id="99036-133">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="99036-134">Давайте изменим класс main для поддержки этого транзитного класса.</span><span class="sxs-lookup"><span data-stu-id="99036-134">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="99036-135">Добавьте это объявление общедоступного метода в заголовочный файл:</span><span class="sxs-lookup"><span data-stu-id="99036-135">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="99036-136">Вам потребуется также эта переменная члена Private:</span><span class="sxs-lookup"><span data-stu-id="99036-136">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="99036-137">Наконец, мы будем обновлять класс Main с помощью новой логики для поддержки щелчков мыши.</span><span class="sxs-lookup"><span data-stu-id="99036-137">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="99036-138">Начните с добавления этого обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="99036-138">Start by adding this event handler.</span></span> <span data-ttu-id="99036-139">Обязательно обновите имя класса:</span><span class="sxs-lookup"><span data-stu-id="99036-139">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="99036-140">Теперь в методе Update замените существующую логику для получения указателя a следующим:</span><span class="sxs-lookup"><span data-stu-id="99036-140">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="99036-141">Перекомпиляция и повторное развертывание.</span><span class="sxs-lookup"><span data-stu-id="99036-141">Recompile and redeploy.</span></span> <span data-ttu-id="99036-142">Обратите внимание, что щелчок мыши теперь перемещает куб в иммерсивное головной или HoloLens с подключенной мышью по Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="99036-142">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="99036-143">Поддержка игрового контроллера</span><span class="sxs-lookup"><span data-stu-id="99036-143">Game controller support</span></span>

<span data-ttu-id="99036-144">Игровые контроллеры могут быть увлекательным и удобным способом предоставления пользователям возможности контролировать иммерсивное взаимодействие с Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99036-144">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="99036-145">Первым шагом в добавлении поддержки игровых контроллеров в шаблон приложения Windows holographic является добавление следующих закрытых объявлений членов в класс Header для основного файла:</span><span class="sxs-lookup"><span data-stu-id="99036-145">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="99036-146">Инициализируйте события игрового планшета и все подключенные к нему игровые планшеты в конструкторе основного класса:</span><span class="sxs-lookup"><span data-stu-id="99036-146">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="99036-147">Добавьте эти обработчики событий в основной класс.</span><span class="sxs-lookup"><span data-stu-id="99036-147">Add these event handlers to your main class.</span></span> <span data-ttu-id="99036-148">Обязательно обновите имя класса:</span><span class="sxs-lookup"><span data-stu-id="99036-148">Make sure to update the class name:</span></span>

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

<span data-ttu-id="99036-149">Наконец, обновите логику ввода, чтобы распознать изменения в состоянии контроллера.</span><span class="sxs-lookup"><span data-stu-id="99036-149">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="99036-150">Здесь мы используем ту же переменную m_pointerPressed, описанную в разделе выше, для добавления событий мыши.</span><span class="sxs-lookup"><span data-stu-id="99036-150">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="99036-151">Добавьте его в метод Update, непосредственно перед тем, как он проверяет наличие Спатиалпоинтерпосе:</span><span class="sxs-lookup"><span data-stu-id="99036-151">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="99036-152">Не забудьте отменить регистрацию событий при очистке основного класса:</span><span class="sxs-lookup"><span data-stu-id="99036-152">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="99036-153">Перекомпиляция и повторное развертывание.</span><span class="sxs-lookup"><span data-stu-id="99036-153">Recompile, and redeploy.</span></span> <span data-ttu-id="99036-154">Теперь можно присоединить или связать игровой контроллер и использовать его для перемещения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="99036-154">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="99036-155">Важные рекомендации по вводу с клавиатуры и мыши</span><span class="sxs-lookup"><span data-stu-id="99036-155">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="99036-156">Существует ряд ключевых различий в том, как этот код можно использовать в Microsoft HoloLens, то есть на устройстве, который в основном используется для естественного ввода данных, и о том, что доступно на ПК с поддержкой Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99036-156">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="99036-157">Вы не можете полагаться на ввод с клавиатуры или с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="99036-157">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="99036-158">Все функции вашего приложения должны работать с помощью взгляда, жеста и речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="99036-158">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="99036-159">При подключении клавиатуры Bluetooth может быть полезно включить ввод с клавиатуры для любого текста, который может запрашивать приложение.</span><span class="sxs-lookup"><span data-stu-id="99036-159">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="99036-160">Например, это может быть отличным дополнением для диктовки.</span><span class="sxs-lookup"><span data-stu-id="99036-160">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="99036-161">Когда дело доходит до разработки приложения, не полагайтесь на то, что (например,) трассе и мышь для поиска в игре.</span><span class="sxs-lookup"><span data-stu-id="99036-161">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="99036-162">HoloLens предназначен для пользователя, чтобы проанализировать комнату.</span><span class="sxs-lookup"><span data-stu-id="99036-162">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="99036-163">В этом случае пользователь управляет камерой напрямую.</span><span class="sxs-lookup"><span data-stu-id="99036-163">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="99036-164">Интерфейс для передачи камеры вокруг комнаты с элементами управления перемещением и просмотром не обеспечивает такой же возможности.</span><span class="sxs-lookup"><span data-stu-id="99036-164">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="99036-165">Ввод с клавиатуры может быть отличным способом управления аспектами отладки приложения или игрового модуля, особенно потому, что пользователю не потребуется использовать клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="99036-165">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="99036-166">Подключение выполняется так же, как и при использовании API-интерфейсов событий CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="99036-166">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="99036-167">В этом сценарии вы можете реализовать способ настройки приложения для маршрутизации событий клавиатуры в режим "только входные данные" во время сеансов отладки.</span><span class="sxs-lookup"><span data-stu-id="99036-167">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="99036-168">Контроллеры Bluetooth также работают.</span><span class="sxs-lookup"><span data-stu-id="99036-168">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="99036-169">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="99036-169">See also</span></span>
* [<span data-ttu-id="99036-170">Аксессуары к оборудованию</span><span class="sxs-lookup"><span data-stu-id="99036-170">Hardware accessories</span></span>](../../discover/hardware-accessories.md)
