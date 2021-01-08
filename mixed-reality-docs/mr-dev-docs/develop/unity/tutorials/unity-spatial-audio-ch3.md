---
title: Придание пространственной формы звуку из видео
description: Узнайте, как импортировать ресурс видео в проект Unity Mixed Reality и спатиализе звук из видео.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер, импорт видео, проигрыватель видео
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007415"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="b4024-104">Придание пространственной формы звуку из видео</span><span class="sxs-lookup"><span data-stu-id="b4024-104">Spatializing audio from a video</span></span>

<span data-ttu-id="b4024-105">В этой третьей главе, посвященной пространственному аудио модулю в учебниках по Unity в HoloLens 2, вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="b4024-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="b4024-106">Импорт видео и добавление видеопроигрывателя</span><span class="sxs-lookup"><span data-stu-id="b4024-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="b4024-107">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="b4024-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="b4024-108">Перенаправление звука с видео на куадрангле и спатиализе звук</span><span class="sxs-lookup"><span data-stu-id="b4024-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="b4024-109">Импорт видео и добавление видеопроигрывателя</span><span class="sxs-lookup"><span data-stu-id="b4024-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="b4024-110">Перетащите видеофайл в область **проекта** в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="b4024-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="b4024-111">[Это видео](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) можно использовать из примера проекта пространственного звука.</span><span class="sxs-lookup"><span data-stu-id="b4024-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Папка Assets с видео](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="b4024-113">Настройка параметров качества видеоклипа обеспечивает плавное воспроизведение в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4024-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="b4024-114">Щелкните видеофайл в области **проекта** .</span><span class="sxs-lookup"><span data-stu-id="b4024-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="b4024-115">Затем на панели **инспектора** для видеофайла Переопределите параметры приложений для Магазина Windows и:</span><span class="sxs-lookup"><span data-stu-id="b4024-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="b4024-116">Включить **перекодировать**</span><span class="sxs-lookup"><span data-stu-id="b4024-116">Enable **Transcode**</span></span>
* <span data-ttu-id="b4024-117">Задать для **кодека** H264 Single bitrate</span><span class="sxs-lookup"><span data-stu-id="b4024-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="b4024-118">Установите низкий **режим** скорости</span><span class="sxs-lookup"><span data-stu-id="b4024-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="b4024-119">Установка среднего значения **пространственного качества**</span><span class="sxs-lookup"><span data-stu-id="b4024-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="b4024-120">После выполнения этих корректировок панель **инспектора** для файла видео будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Панель свойств видео](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="b4024-122">Затем добавьте объект **видеопроигрывателя** в **иерархию** , щелкнув правой кнопкой мыши панель **Иерархия** и выбрав **видео-> видеопроигрыватель**:</span><span class="sxs-lookup"><span data-stu-id="b4024-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Видеопроигрыватель в иерархии](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="b4024-124">Воспроизведение видео на куадрангле</span><span class="sxs-lookup"><span data-stu-id="b4024-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="b4024-125">Объекту **видеопроигрывателя** требуется текстурированный объект Game, на котором будет отображаться видео.</span><span class="sxs-lookup"><span data-stu-id="b4024-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="b4024-126">Во-первых, добавьте к своей **иерархии** « **четыре** », щелкнув правой кнопкой мыши панель « **Иерархия** » и выбрав « **объемные объекты», > «четыре»**:</span><span class="sxs-lookup"><span data-stu-id="b4024-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Добавить Quad в иерархию](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="b4024-128">Чтобы гарантировать, что **четыре** части появляются перед пользователем при запуске приложения, задайте **для свойства "значение"** **Quad** равным (0, 0, 2) и свойству **Scale** значение (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="b4024-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="b4024-129">После внесения этих изменений компонент **преобразования** на панели **инспектора** для **четырех** компонентов будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Четыре преобразования](images/spatial-audio/quad-transform.png)

<span data-ttu-id="b4024-131">Чтобы создать текстуру **Quad** с видео, создайте новую **текстуру рендеринга**.</span><span class="sxs-lookup"><span data-stu-id="b4024-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="b4024-132">В области **проекта** щелкните правой кнопкой мыши и выберите **создать-> рендеринг текстуры**:</span><span class="sxs-lookup"><span data-stu-id="b4024-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Создать текстуру рендеринга](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="b4024-134">На панели **инспектора** **текстуры рендеринга** присвойте свойству **size** значение, совпадающее с разрешением 1280 x 720 в собственном разрешении видео.</span><span class="sxs-lookup"><span data-stu-id="b4024-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="b4024-135">Затем, чтобы обеспечить хорошую производительность отрисовки в HoloLens 2, задайте для свойства **буфера глубины** значение не **менее 16 бит**.</span><span class="sxs-lookup"><span data-stu-id="b4024-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="b4024-136">После этих параметров панель **инспектора** для **текстуры рендеринга** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Прорисовка свойств текстуры](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="b4024-138">Затем используйте новую **текстуру рендеринга** в качестве текстуры для **четырех**:</span><span class="sxs-lookup"><span data-stu-id="b4024-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="b4024-139">Перетащите **текстуру рендеринга** из области **проекта** на **четыре** части **иерархии**</span><span class="sxs-lookup"><span data-stu-id="b4024-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="b4024-140">Чтобы обеспечить хорошую производительность в HoloLens 2, на панели **инспектора** для **четырех** выберите **стандартный шейдер набора средств Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="b4024-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="b4024-141">С этими параметрами компонент **текстуры** на панели **инспектора** для **четырех** компонентов будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Свойства с четырьмя текстурами](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="b4024-143">Чтобы задать новый **видеопроигрыватель** и **визуализировать текстуру** для воспроизведения видеоклипа, откройте панель **инспектора** для **видеопроигрывателя** и:</span><span class="sxs-lookup"><span data-stu-id="b4024-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="b4024-144">Задайте для свойства "видеоклип **видео** " видеофайл</span><span class="sxs-lookup"><span data-stu-id="b4024-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="b4024-145">Установите флажок " **цикл** "</span><span class="sxs-lookup"><span data-stu-id="b4024-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="b4024-146">Задать **целевую текстуру** для новой текстуры рендеринга</span><span class="sxs-lookup"><span data-stu-id="b4024-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="b4024-147">Панель **инспектора** для **видеопроигрывателя** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Свойства проигрывателя видео](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="b4024-149">Спатиализе звук из видео</span><span class="sxs-lookup"><span data-stu-id="b4024-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="b4024-150">На панели **инспектора** для « **четырех**» создайте **источник аудио** , в который вы направите звук из видео:</span><span class="sxs-lookup"><span data-stu-id="b4024-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="b4024-151">Щелкните **Добавить компонент** в нижней части панели.</span><span class="sxs-lookup"><span data-stu-id="b4024-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="b4024-152">Добавление **источника звука**</span><span class="sxs-lookup"><span data-stu-id="b4024-152">Add an **Audio Source**</span></span>

<span data-ttu-id="b4024-153">Затем на **источнике аудио**:</span><span class="sxs-lookup"><span data-stu-id="b4024-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="b4024-154">Задание **выходных данных** для микшера</span><span class="sxs-lookup"><span data-stu-id="b4024-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="b4024-155">Установите флажок **спатиализе**</span><span class="sxs-lookup"><span data-stu-id="b4024-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="b4024-156">Переместить ползунок **пространственного смешения** в 1 (объемный)</span><span class="sxs-lookup"><span data-stu-id="b4024-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="b4024-157">После внесения этих изменений компонент " **источник звука** " на панели **инспектора** будет **выглядеть** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Проводник с четырьмя звуковыми источниками](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="b4024-159">Чтобы настроить **видеопроигрыватель** для направления звука в **источник звука** **, откройте** панель **инспектора** для **видеопроигрывателя** и:</span><span class="sxs-lookup"><span data-stu-id="b4024-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="b4024-160">Установите для **режима вывода звука** значение "источник звука".</span><span class="sxs-lookup"><span data-stu-id="b4024-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="b4024-161">Задайте для свойства **источник звука** значение четыре</span><span class="sxs-lookup"><span data-stu-id="b4024-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="b4024-162">После внесения этих изменений панель **инспектора** для **видеопроигрывателя** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4024-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Выбор источника звука видеопроигрывателя](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="b4024-164">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="b4024-164">Next steps</span></span>

<span data-ttu-id="b4024-165">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="b4024-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="b4024-166">Вы увидите и услышите видео, и звук из видео будет пространственно.</span><span class="sxs-lookup"><span data-stu-id="b4024-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4024-167">Глава 4</span><span class="sxs-lookup"><span data-stu-id="b4024-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

