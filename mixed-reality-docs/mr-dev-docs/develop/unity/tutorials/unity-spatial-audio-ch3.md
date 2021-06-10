---
title: Пространственные аудио учебники — 3. Придание пространственной формы звуку из видео
description: Импортируйте видео-ресурс в проект Unity и спатиализе звук из видео.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер, импорт видео, проигрыватель видео
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712920"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="100a3-105">3. Придание пространственной формы звуку из видео</span><span class="sxs-lookup"><span data-stu-id="100a3-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="100a3-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="100a3-106">Overview</span></span>

<span data-ttu-id="100a3-107">В этом руководстве вы узнаете, как спатиализе звук из источника видео и проверить его в редакторе Unity и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="100a3-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="100a3-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="100a3-108">Objectives</span></span>

* <span data-ttu-id="100a3-109">Импорт видео и добавление видеопроигрывателя</span><span class="sxs-lookup"><span data-stu-id="100a3-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="100a3-110">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="100a3-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="100a3-111">Перенаправление звука с видео на куадрангле и спатиализе звук</span><span class="sxs-lookup"><span data-stu-id="100a3-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="100a3-112">Импорт видео и добавление видеопроигрывателя в сцену</span><span class="sxs-lookup"><span data-stu-id="100a3-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="100a3-113">В этом руководстве вы можете использовать [это видео](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) из примера проекта пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="100a3-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="100a3-114">Для импорта видео в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="100a3-114">To import Video into the unity project.</span></span> <span data-ttu-id="100a3-115">в меню Unity выберите **ресурс**  >  **Импорт нового актива** 
 ![ Импорт ресурса.](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="100a3-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span></span>

<span data-ttu-id="100a3-116">В окне **Импорт нового актива...** выберите скачанный файл **Microsoft HoloLens-пространственный Sound-PTPvx7mDon4** и нажмите кнопку **Открыть** , чтобы импортировать ресурс в проект:</span><span class="sxs-lookup"><span data-stu-id="100a3-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Выбор актива](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

<span data-ttu-id="100a3-118">Настройка параметров качества видеоклипа обеспечивает плавное воспроизведение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="100a3-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="100a3-119">Выберите видеофайл в окне **проекта** и в окне инспектора видеофайла, **Переопределите** параметры для **приложений Магазина Windows** и:</span><span class="sxs-lookup"><span data-stu-id="100a3-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="100a3-120">Включить **перекодировать**</span><span class="sxs-lookup"><span data-stu-id="100a3-120">Enable **Transcode**</span></span>
* <span data-ttu-id="100a3-121">Задать для **кодека** H264 Single bitrate</span><span class="sxs-lookup"><span data-stu-id="100a3-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="100a3-122">Установите низкий **режим** скорости</span><span class="sxs-lookup"><span data-stu-id="100a3-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="100a3-123">Установка среднего значения **пространственного качества**</span><span class="sxs-lookup"><span data-stu-id="100a3-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="100a3-124">После выполнения этих корректировок нажмите кнопку Применить, чтобы изменить параметр качества видеоклипа.</span><span class="sxs-lookup"><span data-stu-id="100a3-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Изменение свойства видео](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

<span data-ttu-id="100a3-126">Щелкните правой кнопкой мыши иерархию, выберите **видео**  >  **видеопроигрыватель** , чтобы добавить компонент видеопроигрывателя.</span><span class="sxs-lookup"><span data-stu-id="100a3-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Добавить проигрыватель видео](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="100a3-128">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="100a3-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="100a3-129">Объекту **видеопроигрывателя** требуется текстурированный объект Game для подготовки к просмотру видео.</span><span class="sxs-lookup"><span data-stu-id="100a3-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="100a3-130">Щелкните правой кнопкой мыши иерархию, выберите **трехмерный объект**  >  **четыре** , чтобы создать четыре и настроить его компонент **преобразования** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="100a3-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="100a3-131">**Расположение**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="100a3-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="100a3-132">**Rotation** (Поворот): X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="100a3-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="100a3-133">**Scale**: X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="100a3-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Добавление четырех](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

<span data-ttu-id="100a3-135">Теперь необходимо создать текстуру с **помощью** видео, в окне **проекта** , щелкнуть правой кнопкой мыши и выбрать команду **создать**  >  **текстуру рендеринга** для создания компонента текстуры рендеринга, ввести подходящее имя для текстуры рендеринга, например, _текстуру пространственного звука_:</span><span class="sxs-lookup"><span data-stu-id="100a3-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Создать текстуру рендеринга](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

<span data-ttu-id="100a3-137">Выберите **текстуру рендеринга** и в окне инспектора установите свойство **size** в соответствии с разрешением 1280 x 720 в собственном разрешении видео.</span><span class="sxs-lookup"><span data-stu-id="100a3-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="100a3-138">Затем, чтобы обеспечить хорошую производительность отрисовки в HoloLens 2, задайте для свойства **буфера глубины** значение не **менее 16 бит**.</span><span class="sxs-lookup"><span data-stu-id="100a3-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Прорисовка свойств текстуры](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

<span data-ttu-id="100a3-140">Затем используйте созданную текстуру для текстурированной текстуры рендеринга **в качестве текстуры** для **четырех**:</span><span class="sxs-lookup"><span data-stu-id="100a3-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="100a3-141">Перетащите **пространственный рисунок** из окна **проекта** на **четыре** в иерархии, чтобы добавить текстуру рендеринга к четырем</span><span class="sxs-lookup"><span data-stu-id="100a3-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="100a3-142">Чтобы обеспечить хорошую производительность в HoloLens 2, выберите «четыре» в иерархии, а в окне инспектора для шейдера выберите Стандартный шейдер **набора средств Mixed Reality**  >   .</span><span class="sxs-lookup"><span data-stu-id="100a3-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Свойства с четырьмя текстурами](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

<span data-ttu-id="100a3-144">Чтобы задать **видеопроигрыватель** и **текстуру прорисовки** для воспроизведения видеоклипа, выберите **видеопроигрыватель** в **иерархии** и в окне **инспектора**</span><span class="sxs-lookup"><span data-stu-id="100a3-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="100a3-145">Задайте для свойства " **видеоклип видео** " скачанный видеофайл "Microsoft HoloLens-spatial Sound-PTPvx7mDon4"</span><span class="sxs-lookup"><span data-stu-id="100a3-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="100a3-146">Установите флажок " **цикл** "</span><span class="sxs-lookup"><span data-stu-id="100a3-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="100a3-147">Задать **целевую текстуру** для текстуры с **текстурной** текстурой рендеринга</span><span class="sxs-lookup"><span data-stu-id="100a3-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Свойства проигрывателя видео](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="100a3-149">Спатиализе звук из видео</span><span class="sxs-lookup"><span data-stu-id="100a3-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="100a3-150">В окне Иерархия выберите " **четыре** объекта", а затем в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить **источник аудио** , в который вы направите звук из видео.</span><span class="sxs-lookup"><span data-stu-id="100a3-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="100a3-151">В **источнике аудио**:</span><span class="sxs-lookup"><span data-stu-id="100a3-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="100a3-152">Задание **выходных данных** для **пространственного звукового микшера**</span><span class="sxs-lookup"><span data-stu-id="100a3-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="100a3-153">Установите флажок **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="100a3-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="100a3-154">Переместить ползунок **пространственного смешения** в 1 (объемный)</span><span class="sxs-lookup"><span data-stu-id="100a3-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Проводник с четырьмя звуковыми источниками](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

<span data-ttu-id="100a3-156">Чтобы настроить видеопроигрыватель для направления звука в **источник аудио**, выберите **видеопроигрыватель** в окне "иерархия", а в объекте видео Player в инспекторе выполните следующие изменения.</span><span class="sxs-lookup"><span data-stu-id="100a3-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="100a3-157">Установка в качестве **режима вывода звука** **звукового источника**</span><span class="sxs-lookup"><span data-stu-id="100a3-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="100a3-158">Установите для свойства **источник звука** значение **четыре**</span><span class="sxs-lookup"><span data-stu-id="100a3-158">Set the **Audio Source** property to the **Quad**</span></span>

![Выбор источника звука видеопроигрывателя](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> <span data-ttu-id="100a3-160">Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="100a3-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="100a3-161">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="100a3-161">Congratulations</span></span>

<span data-ttu-id="100a3-162">В этом руководстве вы узнали, как спатиализе звук из источника видео, чтобы испытать свое приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="100a3-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="100a3-163">Вы увидите и услышите видео, а звук из видео будет пространственно.</span><span class="sxs-lookup"><span data-stu-id="100a3-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="100a3-164">В следующем учебном курсе вы узнаете, как включать и отключать пространственные во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="100a3-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="100a3-165">Следующее руководство: 4. Включение и отключение пространственности во время выполнения</span><span class="sxs-lookup"><span data-stu-id="100a3-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
