---
title: Пространственные аудио учебники — 2. Придание пространственной формы звуку при взаимодействии с кнопками
description: Добавьте кнопку в проект и спатиализе кнопку звуки.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, пространственный аудио, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер, Prefabs, кривая тома
ms.openlocfilehash: 62825ed8922cd904212160748018446cbc76b839
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002599"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="d8c94-105">Придание пространственной формы звуку при взаимодействии с кнопками</span><span class="sxs-lookup"><span data-stu-id="d8c94-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="d8c94-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="d8c94-106">Objectives</span></span>
<span data-ttu-id="d8c94-107">В этой второй главе модуля пространственное аудио в учебниках HoloLens 2 вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d8c94-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="d8c94-108">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="d8c94-108">Add a button</span></span>
* <span data-ttu-id="d8c94-109">Спатиализе кнопку "звуки"</span><span class="sxs-lookup"><span data-stu-id="d8c94-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="d8c94-110">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="d8c94-110">Add a button</span></span>
<span data-ttu-id="d8c94-111">В области **проект** выберите **активы** и введите "PressableButtonHoloLens2" в строке поиска:</span><span class="sxs-lookup"><span data-stu-id="d8c94-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Кнопка "prefab" в активах](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="d8c94-113">Кнопка prefab — это запись, представленная синим значком, а не белым значком.</span><span class="sxs-lookup"><span data-stu-id="d8c94-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="d8c94-114">Перетащите prefab с именем **PressableButtonHoloLens2** в область **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="d8c94-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="d8c94-115">На панели **инспектора** для новой кнопки задайте для свойства " **Расположение** " значение (0,-0,4, 2), чтобы оно отображалось перед пользователем при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="d8c94-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="d8c94-116">Компонент **преобразования** кнопки будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d8c94-116">The **Transform** component of the button will look like this:</span></span>

![Преобразование кнопки](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="d8c94-118">Обратная связь кнопки спатиализе</span><span class="sxs-lookup"><span data-stu-id="d8c94-118">Spatialize button feedback</span></span>
<span data-ttu-id="d8c94-119">На этом шаге вы спатиализе голосовую реакцию на кнопку.</span><span class="sxs-lookup"><span data-stu-id="d8c94-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="d8c94-120">Связанные предложения по проектированию см. в разделе [проектирование пространственных звуков](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="d8c94-120">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="d8c94-121">На панели **микшера звука** можно определить назначения, называемые **группами микшера**, для воспроизведения звука из компонентов **источника аудио** .</span><span class="sxs-lookup"><span data-stu-id="d8c94-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="d8c94-122">Откройте панель **звукового микшера** в строке меню с помощью **> окна аудио-> звукового микшера** .</span><span class="sxs-lookup"><span data-stu-id="d8c94-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="d8c94-123">Создайте **микшер** , щелкнув значок "+" рядом с **миксерс**.</span><span class="sxs-lookup"><span data-stu-id="d8c94-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="d8c94-124">Новый микшер будет включать в себя **группу** по умолчанию с именем **master**.</span><span class="sxs-lookup"><span data-stu-id="d8c94-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="d8c94-125">Теперь панель **микшера** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d8c94-125">Your **Mixer** pane will now look like this:</span></span>

![Панель микшера с первым микшером](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="d8c94-127">Пока в [главе 5](unity-spatial-audio-ch5.md)не будет включена команда переглагола, индикатор громкости микшера не отображает действия для звуков, воспроизводимых через Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="d8c94-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="d8c94-128">Щелкните **PressableButtonHoloLens2** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="d8c94-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="d8c94-129">На панели **инспектора** :</span><span class="sxs-lookup"><span data-stu-id="d8c94-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="d8c94-130">Поиск компонента " **источник аудио** "</span><span class="sxs-lookup"><span data-stu-id="d8c94-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="d8c94-131">В качестве **выходного** свойства щелкните селектор и выберите микшер.</span><span class="sxs-lookup"><span data-stu-id="d8c94-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="d8c94-132">Установите флажок **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="d8c94-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="d8c94-133">Переместите ползунок **пространственный Blend** в 3D (1).</span><span class="sxs-lookup"><span data-stu-id="d8c94-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="d8c94-134">В версиях Unity, предшествовавших 2019, флажок "Спатиализе" находится в нижней части панели **инспектора** для **источника звука**.</span><span class="sxs-lookup"><span data-stu-id="d8c94-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="d8c94-135">После внесения этих изменений компонент **источника звука** **PressableButtonHoloLens2** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d8c94-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Источник звука кнопки](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="d8c94-137">Если вы перемещаете **пространственное смешение** в 1 (3D) без проверки флажка **спатиализе** , Unity будет использовать Спатиализер панорамирования вместо **Microsoft спатиализер** с хртфс.</span><span class="sxs-lookup"><span data-stu-id="d8c94-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="d8c94-138">Настройка кривой тома</span><span class="sxs-lookup"><span data-stu-id="d8c94-138">Adjust the Volume curve</span></span>
<span data-ttu-id="d8c94-139">По умолчанию Unity будет расослабленить пространственные звуки по мере того, как они появятся дальше от прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="d8c94-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="d8c94-140">Когда это ослабление применяется к звуковым сообщениям о взаимодействии, интерфейс может стать более трудным для использования.</span><span class="sxs-lookup"><span data-stu-id="d8c94-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="d8c94-141">Чтобы отключить это ослабление, измените кривую **громкости** .</span><span class="sxs-lookup"><span data-stu-id="d8c94-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="d8c94-142">В компоненте " **источник аудио** " панели **инспектора** для **PressableButtonHoloLens2** есть раздел **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="d8c94-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="d8c94-143">В этом разделе:</span><span class="sxs-lookup"><span data-stu-id="d8c94-143">In that section:</span></span>
1. <span data-ttu-id="d8c94-144">Установка для свойства **Volume роллофф** значения линейная</span><span class="sxs-lookup"><span data-stu-id="d8c94-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="d8c94-145">Перетащите конечную точку на кривой **тома** (красную кривую) из "0" на оси y до "1"</span><span class="sxs-lookup"><span data-stu-id="d8c94-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="d8c94-146">Чтобы изменить форму кривой **тома** на плоскую, перетащите элемент управления "фигурная кривая", чтобы он был параллельно с осью X.</span><span class="sxs-lookup"><span data-stu-id="d8c94-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="d8c94-147">После внесения этих изменений раздел **3D Sound Settings** (свойства **источника звука** ) **PressableButtonHoloLens2** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d8c94-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Параметры трехмерного звука кнопки](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="d8c94-149">Тестирование звука спатиализе</span><span class="sxs-lookup"><span data-stu-id="d8c94-149">Testing the spatialize audio</span></span>

<span data-ttu-id="d8c94-150">Вы можете протестировать новые эффекты взаимодействия с пространственными кнопками:</span><span class="sxs-lookup"><span data-stu-id="d8c94-150">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="d8c94-151">Переход в режим игры в редакторе Unity в идеале с циклическим примером звука в сцене</span><span class="sxs-lookup"><span data-stu-id="d8c94-151">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="d8c94-152">Переместите объект с источником аудио слева направо и сравните с включенным пространственным звуком и без него.</span><span class="sxs-lookup"><span data-stu-id="d8c94-152">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="d8c94-153">Параметры источника звука для тестирования можно изменить следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d8c94-153">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="d8c94-154">Перемещение свойства пространственного смешения между 0-1 (2D-непространственный и трехмерный Пространственный звук)</span><span class="sxs-lookup"><span data-stu-id="d8c94-154">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="d8c94-155">Проверка и извлечение свойства Спатиализе</span><span class="sxs-lookup"><span data-stu-id="d8c94-155">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="d8c94-156">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="d8c94-156">Next steps</span></span>

<span data-ttu-id="d8c94-157">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="d8c94-157">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="d8c94-158">В приложении можно коснуться кнопки и слышать звуки для взаимодействия с пространственными кнопками.</span><span class="sxs-lookup"><span data-stu-id="d8c94-158">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="d8c94-159">При тестировании в редакторе Unity нажмите клавишу пробел и прокрутите прокрутку с помощью колесика прокрутки, чтобы активировать моделирование руки.</span><span class="sxs-lookup"><span data-stu-id="d8c94-159">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="d8c94-160">Дополнительные сведения см. в [документации по мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="d8c94-160">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8c94-161">Глава 3</span><span class="sxs-lookup"><span data-stu-id="d8c94-161">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

