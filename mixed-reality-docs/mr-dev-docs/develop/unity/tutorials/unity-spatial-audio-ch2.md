---
title: Пространственные аудио учебники — 2. Придание пространственной формы звуку при взаимодействии с кнопками
description: Добавьте кнопку в проект и спатиализе кнопку звуки.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, пространственный аудио, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер, Prefabs, кривая тома
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578495"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="b0a02-105">2. Придание пространственной формы звуку при взаимодействии с кнопками</span><span class="sxs-lookup"><span data-stu-id="b0a02-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="b0a02-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="b0a02-106">Overview</span></span>

<span data-ttu-id="b0a02-107">В этом учебнике вы узнаете, как спатиализе звуки диалога и как использовать аудиоклип для проверки взаимодействия с пространственными кнопками.</span><span class="sxs-lookup"><span data-stu-id="b0a02-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="b0a02-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="b0a02-108">Objectives</span></span>

* <span data-ttu-id="b0a02-109">Добавить и Спатиализе кнопку "звуки"</span><span class="sxs-lookup"><span data-stu-id="b0a02-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="b0a02-110">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="b0a02-110">Add a button</span></span>

<span data-ttu-id="b0a02-111">Чтобы добавить кнопку prefab, в окне **проекта** выберите **активы** и введите "PressableButtonHoloLens2" в строке поиска.</span><span class="sxs-lookup"><span data-stu-id="b0a02-111">To add the Button prefab, in the **Project** window, select **Assets** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Кнопка "prefab" в активах](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="b0a02-113">Кнопка prefab — это запись, представленная синим значком.</span><span class="sxs-lookup"><span data-stu-id="b0a02-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="b0a02-114">Щелкните и перетащите **PressableButtonHoloLens2** prefab в иерархию.</span><span class="sxs-lookup"><span data-stu-id="b0a02-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="b0a02-115">Если объект **PressableButtonHoloLens2** все еще выбран, в окне инспектора настройте компонент **преобразования** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b0a02-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="b0a02-116">**Расположение**: X = 0, Y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="b0a02-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="b0a02-117">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="b0a02-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="b0a02-118">**Scale** (Масштаб): X = 1, Y = 1, Z = 1.</span><span class="sxs-lookup"><span data-stu-id="b0a02-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Преобразование кнопки](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="b0a02-120">Чтобы сосредоточиться на объектах в сцене, можно дважды щелкнуть объект **PressableButtonHoloLens2** , а затем немного увеличить масштаб.</span><span class="sxs-lookup"><span data-stu-id="b0a02-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="b0a02-121">Обратная связь кнопки спатиализе</span><span class="sxs-lookup"><span data-stu-id="b0a02-121">Spatialize button feedback</span></span>

<span data-ttu-id="b0a02-122">На этом шаге вы спатиализе голосовую реакцию на кнопку.</span><span class="sxs-lookup"><span data-stu-id="b0a02-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="b0a02-123">Связанные предложения по проектированию см. в разделе [проектирование пространственных звуков](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="b0a02-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="b0a02-124">В окне **микшера звука** будут определены назначения, называемые **группами микшера**, для воспроизведения звука из компонентов **источника аудио** .</span><span class="sxs-lookup"><span data-stu-id="b0a02-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="b0a02-125">Чтобы открыть окно " **звук микшера** ", в меню Unity выберите пункт **окно**  >  **аудио**  >  **аудио микшера**: ![ открыть окно микшера звука.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="b0a02-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="b0a02-126">Создайте **микшер** , щелкнув значок "+" рядом с **миксерс** и введите подходящее имя для микшера, например " _пространственный звуковой микшер_".</span><span class="sxs-lookup"><span data-stu-id="b0a02-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="b0a02-127">Новый микшер будет включать в себя **группу** по умолчанию с именем **master**.</span><span class="sxs-lookup"><span data-stu-id="b0a02-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Панель микшера с первым микшером](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="b0a02-129">Пока в 5-й главе не будет включена команда переглагола [: для добавления расстояния к пространственному звуку](unity-spatial-audio-ch5.md), индикатор громкости микшера не отображает действия для звуков, воспроизводимых через Microsoft спатиализер</span><span class="sxs-lookup"><span data-stu-id="b0a02-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="b0a02-130">В окне "иерархия" выберите **PressableButtonHoloLens2** , затем в окне инспектора найдите компонент " **источник аудио** " и настройте компонент "источник звука" следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b0a02-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="b0a02-131">Для свойства **выход** щелкните селектор и выберите созданное **микшер** .</span><span class="sxs-lookup"><span data-stu-id="b0a02-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="b0a02-132">Установите флажок **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="b0a02-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="b0a02-133">Переместите ползунок **пространственный Blend** в 3D (1).</span><span class="sxs-lookup"><span data-stu-id="b0a02-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Источник звука кнопки](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="b0a02-135">Если вы перемещаете **пространственное смешение** в 1 (3D) без проверки флажка **спатиализе** , Unity будет использовать Спатиализер панорамирования вместо **Microsoft спатиализер** с хртфс.</span><span class="sxs-lookup"><span data-stu-id="b0a02-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="b0a02-136">Настройка кривой тома</span><span class="sxs-lookup"><span data-stu-id="b0a02-136">Adjust the Volume curve</span></span>

<span data-ttu-id="b0a02-137">По умолчанию Unity будет расослабленить пространственные звуки по мере того, как они появятся дальше от прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="b0a02-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="b0a02-138">Когда это ослабление применяется к звуковым сообщениям о взаимодействии, интерфейс может стать более трудным для использования.</span><span class="sxs-lookup"><span data-stu-id="b0a02-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="b0a02-139">Чтобы отключить это ослабление, необходимо скорректировать кривую **громкости** в компоненте " **источник звука** ".</span><span class="sxs-lookup"><span data-stu-id="b0a02-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="b0a02-140">В окне "иерархия" выберите **PressableButtonHoloLens2** , затем в окне инспектора перейдите к   >  **параметрам трехмерный звук** источника аудио и настройте следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b0a02-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="b0a02-141">Задайте для свойства **Volume роллофф** значение линейное роллофф.</span><span class="sxs-lookup"><span data-stu-id="b0a02-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="b0a02-142">Перетащите конечную точку на кривой **тома** (красную кривую) из "0" на оси y до "1"</span><span class="sxs-lookup"><span data-stu-id="b0a02-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="b0a02-143">Чтобы изменить форму кривой **тома** на плоскую, перетащите элемент управления "фигурная кривая", чтобы он был параллельно с осью X.</span><span class="sxs-lookup"><span data-stu-id="b0a02-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Параметры трехмерного звука кнопки](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="b0a02-145">Тестирование звука спатиализе</span><span class="sxs-lookup"><span data-stu-id="b0a02-145">Testing the spatialize audio</span></span>

<span data-ttu-id="b0a02-146">Для тестирования звука спатиализе в редакторе Unity необходимо добавить аудиоклип в компоненте " **источник звука** " с параметром **цикла** , возвращенным в объекте **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="b0a02-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="b0a02-147">В режиме воспроизведения переместите объект **PressableButtonHoloLens2** слева направо и сравните с и без поддержки пространственного звука на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="b0a02-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="b0a02-148">Также можно изменить настройки источника звука для тестирования следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b0a02-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="b0a02-149">Перемещение свойства **пространственного смешения** между 0-1 (2D-непространственный и трехмерный Пространственный звук)</span><span class="sxs-lookup"><span data-stu-id="b0a02-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="b0a02-150">Проверка и извлечение свойства **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="b0a02-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="b0a02-151">Попробуйте приложение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b0a02-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="b0a02-152">В приложении можно нажать кнопку и слышать звуки для взаимодействия с пространственными кнопками.</span><span class="sxs-lookup"><span data-stu-id="b0a02-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="b0a02-153">Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="b0a02-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b0a02-154">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b0a02-154">Congratulations</span></span>

<span data-ttu-id="b0a02-155">В этом учебнике вы узнаете, как спатиализе диалоговое воспроизведение кнопки и использовать аудиоклип для проверки взаимодействия с пространственными кнопками.</span><span class="sxs-lookup"><span data-stu-id="b0a02-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="b0a02-156">В следующем учебном курсе вы узнаете, как спатиализе звук из источника видео.</span><span class="sxs-lookup"><span data-stu-id="b0a02-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0a02-157">Следующий учебник: 3. Спатиализинг Audio из видео</span><span class="sxs-lookup"><span data-stu-id="b0a02-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
