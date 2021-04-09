---
title: Кнопки
description: Общие сведения о кнопках в МРТК
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, кнопки МРТК
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003121"
---
# <a name="button"></a><span data-ttu-id="f901d-104">Кнопка</span><span class="sxs-lookup"><span data-stu-id="f901d-104">Button</span></span>

![Кнопка "Main"](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="f901d-106">Кнопка предоставляет пользователю возможность вызвать немедленное действие.</span><span class="sxs-lookup"><span data-stu-id="f901d-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="f901d-107">Это один из самых базовых компонентов в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f901d-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="f901d-108">МРТК предоставляет различные типы кнопок Prefabs.</span><span class="sxs-lookup"><span data-stu-id="f901d-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="f901d-109">Кнопка Prefabs в МРТК</span><span class="sxs-lookup"><span data-stu-id="f901d-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="f901d-110">Примеры кнопки Prefabs в ``MRTK/SDK/Features/UX/Interactable/Prefabs`` папке</span><span class="sxs-lookup"><span data-stu-id="f901d-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="f901d-111">Изображение или кнопки на основе графического интерфейса Unity</span><span class="sxs-lookup"><span data-stu-id="f901d-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="f901d-112">Кнопки на основе "конфликты"</span><span class="sxs-lookup"><span data-stu-id="f901d-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="f901d-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="f901d-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="f901d-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="f901d-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="f901d-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="f901d-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f901d-119">Кнопка в стиле "оболочка" HoloLens 2 с поддержкой обратной связи, которая поддерживает различные визуальные отзывы, такие как границы, освещение и сжатые формы спереди.</span><span class="sxs-lookup"><span data-stu-id="f901d-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-120">Кнопка типа оболочки HoloLens 2 без формы</span><span class="sxs-lookup"><span data-stu-id="f901d-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-121">Кнопка типа оболочки HoloLens 2 с круглой фигурой</span><span class="sxs-lookup"><span data-stu-id="f901d-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f901d-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="f901d-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="f901d-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="f901d-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f901d-125">Широкая кнопка в стиле 32x96mm HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f901d-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-126">Горизонтальная панель кнопки HoloLens 2 с общей службой</span><span class="sxs-lookup"><span data-stu-id="f901d-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-127">Вертикальная панель кнопки HoloLens 2 с общей службой</span><span class="sxs-lookup"><span data-stu-id="f901d-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f901d-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="f901d-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="f901d-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="f901d-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f901d-131">32x32mm. флажок в стиле оболочки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f901d-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-132">32x32mm коммутатора HoloLens 2 в стиле оболочки</span><span class="sxs-lookup"><span data-stu-id="f901d-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-133">32x32mm-радио в стиле оболочки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f901d-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f901d-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="f901d-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="f901d-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="f901d-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f901d-137">32x96mm. флажок в стиле оболочки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f901d-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-138">32x96mm коммутатора HoloLens 2 в стиле оболочки</span><span class="sxs-lookup"><span data-stu-id="f901d-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-139">32x96mm-радио в стиле оболочки HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f901d-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f901d-140">![Радиальный ](../images/button/MRTK_Button_Radial.png) **радиальный**</span><span class="sxs-lookup"><span data-stu-id="f901d-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-141">![Флажок](../images/button/MRTK_Button_Checkbox.png) **Флажок**</span><span class="sxs-lookup"><span data-stu-id="f901d-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-142">![Тогглесвитч ](../images/button/MRTK_Button_ToggleSwitch.png) **тогглесвитч**</span><span class="sxs-lookup"><span data-stu-id="f901d-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f901d-143">Радиальная кнопка</span><span class="sxs-lookup"><span data-stu-id="f901d-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-144">Флажок</span><span class="sxs-lookup"><span data-stu-id="f901d-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-145">Тумблер</span><span class="sxs-lookup"><span data-stu-id="f901d-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f901d-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="f901d-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-147">![Прессаблераундбуттон ](../images/button/MRTK_Button_Round.png) **прессаблераундбуттон**</span><span class="sxs-lookup"><span data-stu-id="f901d-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-148">![Кнопка "Базовая" кнопки ](../images/button/MRTK_Button_Base.png) </span><span class="sxs-lookup"><span data-stu-id="f901d-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f901d-149">Кнопка стиля оболочки 1-го поколения HoloLens</span><span class="sxs-lookup"><span data-stu-id="f901d-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-150">Кнопка "круглая фигура"</span><span class="sxs-lookup"><span data-stu-id="f901d-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f901d-151">Кнопка "базовый"</span><span class="sxs-lookup"><span data-stu-id="f901d-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="f901d-152">`Button`Ресурсы (Asset/мртк/SDK/Features/UX/взаимодействовать/Prefabs/Button. prefab) основаны на [взаимодействующей](interactable.md) концепции, обеспечивающей простоту элементов управления пользовательского интерфейса для кнопок или других типов интерактивных поверхностей.</span><span class="sxs-lookup"><span data-stu-id="f901d-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="f901d-153">Кнопка базовые показатели поддерживает все доступные входные методы, включая вводные данные для практических действий, а также взгляните + Air — касание для дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f901d-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="f901d-154">Можно также использовать команду Voice для активации кнопки.</span><span class="sxs-lookup"><span data-stu-id="f901d-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="f901d-155">`PressableButtonHoloLens2` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2. prefab) — это кнопка в стиле оболочки HoloLens 2, которая поддерживает точное перемещение кнопки для входных данных прямого отслеживания.</span><span class="sxs-lookup"><span data-stu-id="f901d-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="f901d-156">Он сочетает `Interactable` скрипт со `PressableButton` сценарием.</span><span class="sxs-lookup"><span data-stu-id="f901d-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="f901d-157">Для HoloLens 2 рекомендуется использовать кнопки с непрозрачной службой.</span><span class="sxs-lookup"><span data-stu-id="f901d-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="f901d-158">Прозрачные кнопки не рекомендуются из-за таких проблем с удобством использования и стабильностью:</span><span class="sxs-lookup"><span data-stu-id="f901d-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="f901d-159">Трудно прочитать значок и текст в физической среде.</span><span class="sxs-lookup"><span data-stu-id="f901d-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="f901d-160">Трудно понять, когда триггер события</span><span class="sxs-lookup"><span data-stu-id="f901d-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="f901d-161">Голограммы, отображаемые с помощью прозрачной плоскости, могут быть нестабильными с глубиной ЛСР в HoloLens 2 стабилизации</span><span class="sxs-lookup"><span data-stu-id="f901d-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Пластина кнопки](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="f901d-163">Использование нажатых кнопок</span><span class="sxs-lookup"><span data-stu-id="f901d-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="f901d-164">Кнопки на основе пользовательского интерфейса Unity</span><span class="sxs-lookup"><span data-stu-id="f901d-164">Unity UI based buttons</span></span>

<span data-ttu-id="f901d-165">Создание холста в сцене (GameObject-> пользовательского интерфейса > Canvas).</span><span class="sxs-lookup"><span data-stu-id="f901d-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="f901d-166">На панели инспектора для холста:</span><span class="sxs-lookup"><span data-stu-id="f901d-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="f901d-167">Щелкните "преобразовать в МРТК холст".</span><span class="sxs-lookup"><span data-stu-id="f901d-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="f901d-168">Нажмите кнопку "добавить Неаринтерактионтаучаблеунитюи".</span><span class="sxs-lookup"><span data-stu-id="f901d-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="f901d-169">Установить масштаб X, Y и Z компонента преобразования Rect в значение 0,001</span><span class="sxs-lookup"><span data-stu-id="f901d-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="f901d-170">Затем перетащите `PressableButtonUnityUI` (Assets/мртк/SDK/Features/UX/взаимодействовать/Prefabs/прессаблебуттонунитюи. prefab), `PressableButtonUnityUICircular` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/прессаблебуттонунитюиЦиркулар. prefab) или `PressableButtonHoloLens2UnityUI` (Assets/мртк/SDK/FEATUREs/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2UnityUI. prefab) на холст.</span><span class="sxs-lookup"><span data-stu-id="f901d-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="f901d-171">Кнопки на основе "конфликты"</span><span class="sxs-lookup"><span data-stu-id="f901d-171">Collider based buttons</span></span>

<span data-ttu-id="f901d-172">Просто перетащите `PressableButtonHoloLens2` (Assets/мртк/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2. prefab) или `PressableButtonHoloLens2Unplated` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2Unplated. prefab) в сцену.</span><span class="sxs-lookup"><span data-stu-id="f901d-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="f901d-173">Эти кнопки Prefabs уже настроены на воспроизведение звука для различных типов входных данных, включая ввод с клавиатуры и взгляд.</span><span class="sxs-lookup"><span data-stu-id="f901d-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="f901d-174">События, предоставляемые в prefab, а также [взаимодействующий](interactable.md) компонент, можно использовать для активации дополнительных действий.</span><span class="sxs-lookup"><span data-stu-id="f901d-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="f901d-175">Нажатые кнопки в [сцене хандинтерактионексампле](../example-scenes/hand-interaction-examples.md) используют интерактивное событие *OnClick* для активации изменения в цвете Куба.</span><span class="sxs-lookup"><span data-stu-id="f901d-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="f901d-176">Это событие активируется для различных типов методов ввода, таких как "взгляд", "Воздушный нажим", "рука-Ray", а также для нажатия физической кнопки с помощью сценария "нажатая кнопка".</span><span class="sxs-lookup"><span data-stu-id="f901d-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="f901d-177">Можно настроить, когда нажатая кнопка вызывает событие *OnClick* с помощью `PhysicalPressEventRouter` кнопки.</span><span class="sxs-lookup"><span data-stu-id="f901d-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="f901d-178">Например, можно установить *OnClick* , чтобы срабатывать при первом нажатии кнопки, а не при нажатии и освобождении, настроив параметр *"взаимодействовать"* при нажатии кнопки " *событие при нажатии*".</span><span class="sxs-lookup"><span data-stu-id="f901d-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="f901d-179">Чтобы воспользоваться конкретными сведениями о состоянии ввода, можно использовать нажатые кнопки события: начать, *сенсорный элемент*, *нажата* кнопка, *кнопка* *запущена*.</span><span class="sxs-lookup"><span data-stu-id="f901d-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="f901d-180">Однако эти события не будут срабатывать в ответ на вход воздуха, руки или глаз.</span><span class="sxs-lookup"><span data-stu-id="f901d-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="f901d-181">**Чтобы обеспечить поддержку практических и дальнего взаимодействия, рекомендуется использовать интерактивное событие *OnClick* .**</span><span class="sxs-lookup"><span data-stu-id="f901d-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="f901d-182">Состояния взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f901d-182">Interaction states</span></span>

<span data-ttu-id="f901d-183">В состоянии простоя Передняя пластина кнопки не видна.</span><span class="sxs-lookup"><span data-stu-id="f901d-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="f901d-184">В качестве подходов к отпечатку пальца или курсора, направленного на ввод целевого объекта, отображается рамка свечения передней формы.</span><span class="sxs-lookup"><span data-stu-id="f901d-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="f901d-185">На поверхности передней панели имеется дополнительное выделение заданной должности.</span><span class="sxs-lookup"><span data-stu-id="f901d-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="f901d-186">При отправке с помощью пальца Передняя пластина перемещается вместе с рукой.</span><span class="sxs-lookup"><span data-stu-id="f901d-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="f901d-187">Когда вы наводите указатель мыши на поверхность передней панели, он показывает слабый импульс, позволяющий визуально отразить сенсорную точку.</span><span class="sxs-lookup"><span data-stu-id="f901d-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="f901d-188">В командной строке HoloLens 2 существует множество визуальных подсказок и аффорданцес для повышения достоверности пользователя при взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="f901d-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Неблизкое освещение](../images/button/ux_button_affordance_proximitylight.jpg) | ![Выделение фокуса](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Сжатие контейнера](../images/button/ux_button_affordance_compression.jpg) | ![Импульс на триггере](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="f901d-193">Неблизкое освещение</span><span class="sxs-lookup"><span data-stu-id="f901d-193">Proximity light</span></span> | <span data-ttu-id="f901d-194">Выделение фокуса</span><span class="sxs-lookup"><span data-stu-id="f901d-194">Focus highlight</span></span> | <span data-ttu-id="f901d-195">Сжатие контейнера</span><span class="sxs-lookup"><span data-stu-id="f901d-195">Compressing cage</span></span> | <span data-ttu-id="f901d-196">Импульс на триггере</span><span class="sxs-lookup"><span data-stu-id="f901d-196">Pulse on trigger</span></span> |

<span data-ttu-id="f901d-197">Ненавязчивый импульс активируется нажатой кнопкой, которая ищет *проксимитилигхт (s)* , которые находятся на текущем взаимодействующем указателе.</span><span class="sxs-lookup"><span data-stu-id="f901d-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="f901d-198">Если обнаружены индикаторы близости, `ProximityLight.Pulse` вызывается метод, который автоматически анимируется параметры шейдера для вывода импульса.</span><span class="sxs-lookup"><span data-stu-id="f901d-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="f901d-199">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="f901d-199">Inspector properties</span></span>

![Структура кнопки](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="f901d-201">**Конфликт Box** 
 `Box Collider` для передней панели кнопки.</span><span class="sxs-lookup"><span data-stu-id="f901d-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="f901d-202">**Нажатая кнопка** Логика движения кнопки с помощью действия руки.</span><span class="sxs-lookup"><span data-stu-id="f901d-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="f901d-203">**Маршрутизатор событий физического нажатия** Этот сценарий отправляет события из руки и [взаимодействует](interactable.md)с пользователем.</span><span class="sxs-lookup"><span data-stu-id="f901d-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="f901d-204">**Взаимодействие** 
 [Взаимодействие](interactable.md) обрабатывает различные типы состояний взаимодействия и событий.</span><span class="sxs-lookup"><span data-stu-id="f901d-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="f901d-205">Этот сценарий непосредственно обрабатывает входные данные и ввод с помощью HoloLens, жестов, голоса и впечатляющих видеоконтроллеров.</span><span class="sxs-lookup"><span data-stu-id="f901d-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="f901d-206">**Источник звука** Источник звука Unity для аудиоклипов с отзывами.</span><span class="sxs-lookup"><span data-stu-id="f901d-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="f901d-207">*Неаринтерактионтаучабле. CS* требуется для того, чтобы любой объект с сенсорным вводом был управляемым.</span><span class="sxs-lookup"><span data-stu-id="f901d-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="f901d-208">Макет prefab</span><span class="sxs-lookup"><span data-stu-id="f901d-208">Prefab layout</span></span>

<span data-ttu-id="f901d-209">Объект *буттонконтент* содержит переднюю форму, текстовую метку и значок.</span><span class="sxs-lookup"><span data-stu-id="f901d-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="f901d-210">*Фронтплате* реагирует на близость индекса с помощью шейдера *Button_Box* .</span><span class="sxs-lookup"><span data-stu-id="f901d-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="f901d-211">В нем показаны свечение границ, световой эффект и импульсное воздействие на касание.</span><span class="sxs-lookup"><span data-stu-id="f901d-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="f901d-212">Текстовая метка создается с помощью Текстмеш Pro.</span><span class="sxs-lookup"><span data-stu-id="f901d-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="f901d-213">Видимость *сиитсайитлабел* контролируется темой [взаимодействия](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="f901d-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Макет кнопки](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="f901d-215">Изменение значка и текста</span><span class="sxs-lookup"><span data-stu-id="f901d-215">How to change the icon and text</span></span>

<span data-ttu-id="f901d-216">Кнопки МРТК используют `ButtonConfigHelper` компонент для изменения значка кнопки, текста и метки.</span><span class="sxs-lookup"><span data-stu-id="f901d-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="f901d-217">(Обратите внимание, что некоторые поля могут отсутствовать, если элементы не представлены на выбранной кнопке.)</span><span class="sxs-lookup"><span data-stu-id="f901d-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Вспомогательная функция настройки кнопки](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="f901d-219">Создание и изменение наборов значков</span><span class="sxs-lookup"><span data-stu-id="f901d-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="f901d-220">**Набор значков** — это общий набор ресурсов значков, используемых `ButtonConfigHelper` компонентом.</span><span class="sxs-lookup"><span data-stu-id="f901d-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="f901d-221">Поддерживаются три *стиля* значков.</span><span class="sxs-lookup"><span data-stu-id="f901d-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="f901d-222">**Четыре** значка визуализируются с помощью `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="f901d-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="f901d-223">Это стиль значка по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f901d-223">This is the default icon style.</span></span>
* <span data-ttu-id="f901d-224">Значки **спрайтов** подготавливаются к просмотру с помощью `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="f901d-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="f901d-225">Это полезно, если вы предпочитаете импортировать значки в виде листа спрайта или хотите предоставить доступ к ресурсам значков с компонентами пользовательского интерфейса Unity.</span><span class="sxs-lookup"><span data-stu-id="f901d-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="f901d-226">Чтобы использовать этот стиль, необходимо установить пакет редактора спрайтов **(Windows-> диспетчер пакетов — > 2D-спрайт)** .</span><span class="sxs-lookup"><span data-stu-id="f901d-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="f901d-227">Значки **char** подготавливаются к просмотру с помощью `TextMeshPro` компонента.</span><span class="sxs-lookup"><span data-stu-id="f901d-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="f901d-228">Это полезно, если вы предпочитаете использовать шрифт значка.</span><span class="sxs-lookup"><span data-stu-id="f901d-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="f901d-229">Чтобы использовать шрифт значка HoloLens, потребуется создать `TextMeshPro` ресурс шрифта.</span><span class="sxs-lookup"><span data-stu-id="f901d-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="f901d-230">Чтобы изменить стиль, используемый для кнопки, разверните раскрывающийся список *значки* в буттонконфигхелпер и выберите из раскрывающегося списка *стиль значка* .</span><span class="sxs-lookup"><span data-stu-id="f901d-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="f901d-231">Новый набор значков кнопок можно создать с помощью меню актив: **создать > набор средств для смешанной реальности > набора значков.**</span><span class="sxs-lookup"><span data-stu-id="f901d-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="f901d-232">Чтобы добавить четыре значка и значки спрайтов, просто перетащите их в соответствующие массивы.</span><span class="sxs-lookup"><span data-stu-id="f901d-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="f901d-233">Чтобы добавить значки char, необходимо сначала создать и назначить ресурс-контейнер шрифта.</span><span class="sxs-lookup"><span data-stu-id="f901d-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="f901d-234">В МРТК 2,4 и более поздних версиях мы рекомендуем перемещать текстуры пользовательских значков в виде значков.</span><span class="sxs-lookup"><span data-stu-id="f901d-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="f901d-235">Чтобы обновить ресурсы на всех кнопках в проекте до нового рекомендуемого формата, используйте Буттонконфигхелпермигратионхандлер.</span><span class="sxs-lookup"><span data-stu-id="f901d-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="f901d-236">(Набор средств для смешанной реальности — > служебные программы — > окно миграции — выбор обработчика миграции > — > Microsoft. Микседреалити. Toolkit. Utilities. Буттонконфигхелпермигратионхандлер)</span><span class="sxs-lookup"><span data-stu-id="f901d-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="f901d-237">Импорт пакета Microsoft. Микседреалититулкит. Unity. Tools, необходимого для обновления кнопок.</span><span class="sxs-lookup"><span data-stu-id="f901d-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Диалоговое окно обновления](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="f901d-239">Если значок не найден в наборе значков по умолчанию во время миграции, в Микседреалититулкит. Generated/Кустомиконсетс будет создан пользовательский набор значков.</span><span class="sxs-lookup"><span data-stu-id="f901d-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="f901d-240">В диалоговом окне будет указано, что выполнено.</span><span class="sxs-lookup"><span data-stu-id="f901d-240">A dialog will indicate that this has taken place.</span></span>

![Уведомление о настраиваемом значке](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="f901d-242">Создание ресурса шрифта значка HoloLens</span><span class="sxs-lookup"><span data-stu-id="f901d-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="f901d-243">Сначала импортируйте шрифт значка в Unity.</span><span class="sxs-lookup"><span data-stu-id="f901d-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="f901d-244">На компьютерах с Windows шрифт HoloLens по умолчанию можно найти в *Windows/Fonts/holomdl2. ttf.*</span><span class="sxs-lookup"><span data-stu-id="f901d-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="f901d-245">Скопируйте и вставьте этот файл в папку Assets.</span><span class="sxs-lookup"><span data-stu-id="f901d-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="f901d-246">Затем откройте средство создания ресурса шрифта Текстмешпро с помощью **окна > текстмешпро > "создатель ресурса шрифта".**</span><span class="sxs-lookup"><span data-stu-id="f901d-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="f901d-247">Ниже приведены рекомендуемые параметры для создания шрифта HoloLens Atlas.</span><span class="sxs-lookup"><span data-stu-id="f901d-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="f901d-248">Чтобы включить все значки, вставьте следующий диапазон Юникода в поле *последовательности символов* :</span><span class="sxs-lookup"><span data-stu-id="f901d-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Создание кнопки 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="f901d-250">После создания ресурса шрифта сохраните его в свой проект и присвойте ему поле *шрифта со значком char* в наборе значков.</span><span class="sxs-lookup"><span data-stu-id="f901d-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="f901d-251">Теперь раскрывающийся список *Доступные значки* будет заполнен.</span><span class="sxs-lookup"><span data-stu-id="f901d-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="f901d-252">Чтобы сделать значок доступным для кнопки, щелкните его.</span><span class="sxs-lookup"><span data-stu-id="f901d-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="f901d-253">Он будет добавлен в раскрывающийся список *Выбранные значки* и теперь будет отображаться в, `ButtonConfigHelper.` при необходимости можно дать значку тег.</span><span class="sxs-lookup"><span data-stu-id="f901d-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="f901d-254">Это позволяет задать значок во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="f901d-254">This enables setting the icon at runtime.</span></span>

![Создание кнопки 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Создание кнопки 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="f901d-257">Чтобы использовать набор значков, нажмите кнопку, разверните раскрывающийся список значков в `ButtonConfigHelper` и назначьте его полю *набора значков* .</span><span class="sxs-lookup"><span data-stu-id="f901d-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Набор значков кнопок](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="f901d-259">Изменение размера кнопки</span><span class="sxs-lookup"><span data-stu-id="f901d-259">How to change the size of a button</span></span>

<span data-ttu-id="f901d-260">Размер кнопки в стиле оболочки HoloLens 2 — 32x32mm.</span><span class="sxs-lookup"><span data-stu-id="f901d-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="f901d-261">Чтобы настроить измерение, измените размер этих объектов на кнопке Prefab:</span><span class="sxs-lookup"><span data-stu-id="f901d-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="f901d-262">**фронтплате**</span><span class="sxs-lookup"><span data-stu-id="f901d-262">**FrontPlate**</span></span>
2. <span data-ttu-id="f901d-263">**Четыре** непечатных панели</span><span class="sxs-lookup"><span data-stu-id="f901d-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="f901d-264">**Box конфликтует** в корне</span><span class="sxs-lookup"><span data-stu-id="f901d-264">**Box Collider** on the root</span></span>

<span data-ttu-id="f901d-265">Затем нажмите кнопку **исправить границы** в скрипте неаринтерактионтаучабле, который находится в корне кнопки.</span><span class="sxs-lookup"><span data-stu-id="f901d-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="f901d-266">Изменение размера ![ кнопки фронтплате Настройка размера 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="f901d-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="f901d-267">Обновление размера ![ плоской кнопки Настройка 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="f901d-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="f901d-268">Обновление размера кнопки "рамка", ![ настройки размера 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="f901d-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="f901d-269">Нажмите кнопку "исправить границы" ![ Настройка размера 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="f901d-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it&quot;></a><span data-ttu-id=&quot;f901d-270&quot;>Голосовая команда (&quot;см.,&quot;, ")"</span><span class="sxs-lookup"><span data-stu-id="f901d-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="f901d-271">**Обработчик речевого ввода** [Взаимодействующий](interactable.md) скрипт в нажатой кнопке уже реализует `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="f901d-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="f901d-272">Здесь можно задать ключевое слово Voice Command.</span><span class="sxs-lookup"><span data-stu-id="f901d-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="f901d-273">**Профиль ввода речи** Кроме того, необходимо зарегистрировать ключевое слово голосовой команды в *профиле глобальных речевых команд*.</span><span class="sxs-lookup"><span data-stu-id="f901d-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="f901d-274">**См. раздел-IT, метка** Нажатая кнопка prefab имеет заполнитель Текстмеш Pro Label в объекте *сиитсайитлабел* .</span><span class="sxs-lookup"><span data-stu-id="f901d-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="f901d-275">Эту метку можно использовать для передачи ключевому слову команды Voice для кнопки пользователю.</span><span class="sxs-lookup"><span data-stu-id="f901d-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="f901d-276">Как сделать кнопку с нуля</span><span class="sxs-lookup"><span data-stu-id="f901d-276">How to make a button from scratch</span></span>

<span data-ttu-id="f901d-277">Примеры этих кнопок можно найти в сцене **прессаблебуттонексампле** .</span><span class="sxs-lookup"><span data-stu-id="f901d-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="f901d-278">1. Создание нажатой кнопки с кубом (только для взаимодействия)</span><span class="sxs-lookup"><span data-stu-id="f901d-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="f901d-279">Создание куба Unity (GameObject > трехмерный объект > Кубу)</span><span class="sxs-lookup"><span data-stu-id="f901d-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="f901d-280">Добавить `PressableButton.cs` Скрипт</span><span class="sxs-lookup"><span data-stu-id="f901d-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="f901d-281">Добавить `NearInteractionTouchable.cs` Скрипт</span><span class="sxs-lookup"><span data-stu-id="f901d-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="f901d-282">На `PressableButton` панели инспектора укажите объект куба для **визуальных элементов кнопки перемещения**.</span><span class="sxs-lookup"><span data-stu-id="f901d-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="f901d-283">При выборе Куба в объекте отображается несколько цветных слоев.</span><span class="sxs-lookup"><span data-stu-id="f901d-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="f901d-284">Это визуализирует значения расстояния в разделе **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="f901d-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="f901d-285">С помощью дескрипторов можно настроить время запуска (перемещения объекта) и время активации события.</span><span class="sxs-lookup"><span data-stu-id="f901d-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="f901d-286">При нажатии кнопки будут перемещены и созданы соответствующие события, представленные в `PressableButton.cs` сценарии, такие как таучбегин (), таученд (), буттонпрессед (), буттонрелеасед ().</span><span class="sxs-lookup"><span data-stu-id="f901d-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="f901d-287">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="f901d-287">Troubleshooting</span></span>

<span data-ttu-id="f901d-288">Если кнопка выполняется двойным щелчком, убедитесь, что свойство **Принудительная отправка на передний план** активна, а плоскость **Начало push-уведомлений** помещается перед **ближайшей сенсорной** плоскостью.</span><span class="sxs-lookup"><span data-stu-id="f901d-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="f901d-289">**Сенсорная плоскость близкого взаимодействия** обозначается синей плоскостью, помещенной перед началом координат белой стрелки в приведенном ниже GIF-файле:</span><span class="sxs-lookup"><span data-stu-id="f901d-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Компонент скрипта для нажатой кнопки с выделенным свойством принудительная передача](../images/button/MRTK_Button_Enforce_Push.png)

![Анимированный пример перемещения начала push-уведомления перед близкой плоскостью с сенсорным взаимодействием](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="f901d-292">2. Добавление визуальной обратной связи к кнопке "базовый куб"</span><span class="sxs-lookup"><span data-stu-id="f901d-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="f901d-293">Стандартный шейдер МРТК предоставляет различные функции, упрощающие Добавление визуальной обратной связи.</span><span class="sxs-lookup"><span data-stu-id="f901d-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="f901d-294">Создайте материал и выберите шейдер `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="f901d-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="f901d-295">Также можно использовать или дублировать один из существующих материалов в `/SDK/StandardAssets/Materials/` , использующий стандартный ШЕЙДЕР мртк.</span><span class="sxs-lookup"><span data-stu-id="f901d-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="f901d-296">Проверьте `Hover Light` и `Proximity Light` в разделе **Параметры Fluent**.</span><span class="sxs-lookup"><span data-stu-id="f901d-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="f901d-297">Это обеспечивает визуальную обратную связь как с ближайшими, так и с большим указателем (светлое изображение).</span><span class="sxs-lookup"><span data-stu-id="f901d-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="f901d-298">3. Добавление обратной связи для кнопки "базовый куб"</span><span class="sxs-lookup"><span data-stu-id="f901d-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="f901d-299">Так как `PressableButton.cs` скрипт предоставляет такие события, как таучбегин (), таученд (), буттонпрессед (), буттонрелеасед (), мы легко можем назначить звуковые отзывы.</span><span class="sxs-lookup"><span data-stu-id="f901d-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="f901d-300">Просто добавьте Unity `Audio Source` в объект Cube, а затем назначьте аудиоклипы, выбрав аудиосаурце. плайонешот ().</span><span class="sxs-lookup"><span data-stu-id="f901d-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="f901d-301">В папке можно использовать MRTK_Select_Main и MRTK_Select_Secondary аудиоклипы `/SDK/StandardAssets/Audio/` .</span><span class="sxs-lookup"><span data-stu-id="f901d-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="f901d-302">4. Добавление визуальных состояний и обработку событий дальнего взаимодействия</span><span class="sxs-lookup"><span data-stu-id="f901d-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="f901d-303">[Взаимодействие](interactable.md) — это скрипт, который упрощает создание визуального состояния для различных типов входных данных.</span><span class="sxs-lookup"><span data-stu-id="f901d-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="f901d-304">Он также обрабатывает события дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f901d-304">It also handles far interaction events.</span></span> <span data-ttu-id="f901d-305">Добавьте `Interactable.cs` объект куба и перетащите его в **целевое** поле в разделе **Профили**.</span><span class="sxs-lookup"><span data-stu-id="f901d-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="f901d-306">Затем создайте новую тему с типом **скалеоффсетколорсеме**.</span><span class="sxs-lookup"><span data-stu-id="f901d-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="f901d-307">В этой теме можно указать цвет объекта для конкретных состояний взаимодействия, например **фокус** и **нажатое**.</span><span class="sxs-lookup"><span data-stu-id="f901d-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="f901d-308">Кроме того, можно также управлять масштабом и смещением.</span><span class="sxs-lookup"><span data-stu-id="f901d-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="f901d-309">Установите флажок **замедление** и задайте длительность, чтобы сделать визуальный переход гладким.</span><span class="sxs-lookup"><span data-stu-id="f901d-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Выбор темы профиля](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="f901d-311">Вы увидите, что объект отвечает на оба (руки или указатель) и почти (руки) взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f901d-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="f901d-312">Примеры настраиваемых кнопок</span><span class="sxs-lookup"><span data-stu-id="f901d-312">Custom button examples</span></span>

<span data-ttu-id="f901d-313">В [сцене хандинтерактионексампле](../example-scenes/hand-interaction-examples.md)ознакомьтесь с примерами пианино и круглыми кнопками, которые используют `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="f901d-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="f901d-314">Каждому ключу пианино `PressableButton` `NearInteractionTouchable` присваивается и назначается сценарий.</span><span class="sxs-lookup"><span data-stu-id="f901d-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="f901d-315">Важно проверить правильность *локального направления вперед* `NearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="f901d-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="f901d-316">Он представлен белой стрелкой в редакторе.</span><span class="sxs-lookup"><span data-stu-id="f901d-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="f901d-317">Убедитесь, что стрелка направлена далеко от лицевой стороны кнопки:</span><span class="sxs-lookup"><span data-stu-id="f901d-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="f901d-318">См. также</span><span class="sxs-lookup"><span data-stu-id="f901d-318">See also</span></span>

* [<span data-ttu-id="f901d-319">Интерактивный объект</span><span class="sxs-lookup"><span data-stu-id="f901d-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="f901d-320">Визуальные темы</span><span class="sxs-lookup"><span data-stu-id="f901d-320">Visual Themes</span></span>](visual-themes.md)
