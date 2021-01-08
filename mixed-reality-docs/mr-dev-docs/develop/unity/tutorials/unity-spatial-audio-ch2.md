---
title: Придание пространственной формы звуку при взаимодействии с кнопками
description: Узнайте, как добавить кнопку и спатиализе эффекты взаимодействия кнопки в приложении смешанной реальности.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, пространственный аудио, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер, Prefabs, кривая тома
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007364"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="250bd-104">Придание пространственной формы звуку при взаимодействии с кнопками</span><span class="sxs-lookup"><span data-stu-id="250bd-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="250bd-105">Задачи</span><span class="sxs-lookup"><span data-stu-id="250bd-105">Objectives</span></span>

<span data-ttu-id="250bd-106">В этой второй главе модуля пространственное аудио в учебниках HoloLens 2 вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="250bd-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="250bd-107">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="250bd-107">Add a button</span></span>
* <span data-ttu-id="250bd-108">Спатиализе кнопку "звуки"</span><span class="sxs-lookup"><span data-stu-id="250bd-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="250bd-109">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="250bd-109">Add a button</span></span>

<span data-ttu-id="250bd-110">В области **проект** выберите **активы** и введите "PressableButtonHoloLens2" в строке поиска:</span><span class="sxs-lookup"><span data-stu-id="250bd-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Кнопка "prefab" в активах](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="250bd-112">Кнопка prefab — это запись, представленная синим значком, а не белым значком.</span><span class="sxs-lookup"><span data-stu-id="250bd-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="250bd-113">Перетащите prefab с именем **PressableButtonHoloLens2** в область **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="250bd-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="250bd-114">На панели **инспектора** для новой кнопки задайте для свойства " **Расположение** " значение (0,-0,4, 2), чтобы оно отображалось перед пользователем при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="250bd-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="250bd-115">Компонент **преобразования** кнопки будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="250bd-115">The **Transform** component of the button will look like this:</span></span>

![Преобразование кнопки](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="250bd-117">Обратная связь кнопки спатиализе</span><span class="sxs-lookup"><span data-stu-id="250bd-117">Spatialize button feedback</span></span>

<span data-ttu-id="250bd-118">На этом шаге вы спатиализе голосовую реакцию на кнопку.</span><span class="sxs-lookup"><span data-stu-id="250bd-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="250bd-119">Связанные предложения по проектированию см. в разделе [проектирование пространственных звуков](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="250bd-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="250bd-120">На панели **микшера звука** можно определить назначения, называемые **группами микшера**, для воспроизведения звука из компонентов **источника аудио** .</span><span class="sxs-lookup"><span data-stu-id="250bd-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="250bd-121">Откройте панель **звукового микшера** в строке меню с помощью **> окна аудио-> звукового микшера** .</span><span class="sxs-lookup"><span data-stu-id="250bd-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="250bd-122">Создайте **микшер** , щелкнув значок "+" рядом с **миксерс**.</span><span class="sxs-lookup"><span data-stu-id="250bd-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="250bd-123">Новый микшер будет включать в себя **группу** по умолчанию с именем **master**.</span><span class="sxs-lookup"><span data-stu-id="250bd-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="250bd-124">Теперь панель **микшера** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="250bd-124">Your **Mixer** pane will now look like this:</span></span>

![Панель микшера с первым микшером](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="250bd-126">Пока в [главе 5](unity-spatial-audio-ch5.md)не будет включена команда переглагола, индикатор громкости микшера не отображает действия для звуков, воспроизводимых через Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="250bd-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="250bd-127">Щелкните **PressableButtonHoloLens2** на панели **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="250bd-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="250bd-128">На панели **инспектора** :</span><span class="sxs-lookup"><span data-stu-id="250bd-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="250bd-129">Поиск компонента " **источник аудио** "</span><span class="sxs-lookup"><span data-stu-id="250bd-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="250bd-130">В качестве **выходного** свойства щелкните селектор и выберите микшер.</span><span class="sxs-lookup"><span data-stu-id="250bd-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="250bd-131">Установите флажок **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="250bd-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="250bd-132">Переместите ползунок **пространственный Blend** в 3D (1).</span><span class="sxs-lookup"><span data-stu-id="250bd-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="250bd-133">В версиях Unity, предшествовавших 2019, флажок "Спатиализе" находится в нижней части панели **инспектора** для **источника звука**.</span><span class="sxs-lookup"><span data-stu-id="250bd-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="250bd-134">После внесения этих изменений компонент **источника звука** **PressableButtonHoloLens2** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="250bd-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Источник звука кнопки](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="250bd-136">Если вы перемещаете **пространственное смешение** в 1 (3D) без проверки флажка **спатиализе** , Unity будет использовать Спатиализер панорамирования вместо **Microsoft спатиализер** с хртфс.</span><span class="sxs-lookup"><span data-stu-id="250bd-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="250bd-137">Настройка кривой тома</span><span class="sxs-lookup"><span data-stu-id="250bd-137">Adjust the Volume curve</span></span>

<span data-ttu-id="250bd-138">По умолчанию Unity будет расослабленить пространственные звуки по мере того, как они появятся дальше от прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="250bd-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="250bd-139">Когда это ослабление применяется к звуковым сообщениям о взаимодействии, интерфейс может стать более трудным для использования.</span><span class="sxs-lookup"><span data-stu-id="250bd-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="250bd-140">Чтобы отключить это ослабление, измените кривую **громкости** .</span><span class="sxs-lookup"><span data-stu-id="250bd-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="250bd-141">В компоненте " **источник аудио** " панели **инспектора** для **PressableButtonHoloLens2** есть раздел **Параметры трехмерного звука**.</span><span class="sxs-lookup"><span data-stu-id="250bd-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="250bd-142">В этом разделе:</span><span class="sxs-lookup"><span data-stu-id="250bd-142">In that section:</span></span>
1. <span data-ttu-id="250bd-143">Установка для свойства **Volume роллофф** значения линейная</span><span class="sxs-lookup"><span data-stu-id="250bd-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="250bd-144">Перетащите конечную точку на кривой **тома** (красную кривую) из "0" на оси y до "1"</span><span class="sxs-lookup"><span data-stu-id="250bd-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="250bd-145">Чтобы изменить форму кривой **тома** на плоскую, перетащите элемент управления "фигурная кривая", чтобы он был параллельно с осью X.</span><span class="sxs-lookup"><span data-stu-id="250bd-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="250bd-146">После внесения этих изменений раздел **3D Sound Settings** (свойства **источника звука** ) **PressableButtonHoloLens2** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="250bd-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Параметры трехмерного звука кнопки](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="250bd-148">Тестирование звука спатиализе</span><span class="sxs-lookup"><span data-stu-id="250bd-148">Testing the spatialize audio</span></span>

<span data-ttu-id="250bd-149">Вы можете протестировать новые эффекты взаимодействия с пространственными кнопками:</span><span class="sxs-lookup"><span data-stu-id="250bd-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="250bd-150">Переход в режим игры в редакторе Unity в идеале с циклическим примером звука в сцене</span><span class="sxs-lookup"><span data-stu-id="250bd-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="250bd-151">Переместите объект с источником аудио слева направо и сравните с включенным пространственным звуком и без него.</span><span class="sxs-lookup"><span data-stu-id="250bd-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="250bd-152">Параметры источника звука для тестирования можно изменить следующим образом.</span><span class="sxs-lookup"><span data-stu-id="250bd-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="250bd-153">Перемещение свойства пространственного смешения между 0-1 (2D-непространственный и трехмерный Пространственный звук)</span><span class="sxs-lookup"><span data-stu-id="250bd-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="250bd-154">Проверка и извлечение свойства Спатиализе</span><span class="sxs-lookup"><span data-stu-id="250bd-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="250bd-155">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="250bd-155">Next steps</span></span>

<span data-ttu-id="250bd-156">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="250bd-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="250bd-157">В приложении можно коснуться кнопки и слышать звуки для взаимодействия с пространственными кнопками.</span><span class="sxs-lookup"><span data-stu-id="250bd-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="250bd-158">При тестировании в редакторе Unity нажмите клавишу пробел и прокрутите прокрутку с помощью колесика прокрутки, чтобы активировать моделирование руки.</span><span class="sxs-lookup"><span data-stu-id="250bd-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="250bd-159">Дополнительные сведения см. в [документации по мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="250bd-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="250bd-160">Глава 3</span><span class="sxs-lookup"><span data-stu-id="250bd-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

