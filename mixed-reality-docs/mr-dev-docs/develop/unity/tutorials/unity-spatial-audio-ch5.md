---
title: Пространственные аудио учебники — 5. Использование реверберации для добавления эффекта расстояния пространственному звуку
description: Добавьте переглаголные эффекты, чтобы улучшить смысл варианта расстояния до пространственного звука.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с головным управлением, переглагол, Microsoft Спатиализер, аудио микшер, переглаголы SFX
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712691"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="cb92b-105">5. Использование реверберации для добавления эффекта расстояния пространственному звуку</span><span class="sxs-lookup"><span data-stu-id="cb92b-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="cb92b-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="cb92b-106">Overview</span></span>

<span data-ttu-id="cb92b-107">В предыдущем учебном курсе вы добавили пространственность для звуков, чтобы дать им представление о направлении в этом учебнике, чтобы дать звуковому расприятию силы.</span><span class="sxs-lookup"><span data-stu-id="cb92b-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="cb92b-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="cb92b-108">Objectives</span></span>

* <span data-ttu-id="cb92b-109">Улучшение наблюдаемого расстояния источников звука путем добавления переглагола.</span><span class="sxs-lookup"><span data-stu-id="cb92b-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="cb92b-110">Управление воспринимаемым расстоянием звука с помощью расстояния прослушивателя к голограмме.</span><span class="sxs-lookup"><span data-stu-id="cb92b-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="cb92b-111">Добавление группы микшера и действия по передействию</span><span class="sxs-lookup"><span data-stu-id="cb92b-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="cb92b-112">В [учебнике звуки взаимодействия с кнопкой спатиализинг](unity-spatial-audio-ch2.md)мы добавили микшер.</span><span class="sxs-lookup"><span data-stu-id="cb92b-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="cb92b-113">Микшер включает одну **группу** по умолчанию — **master**.</span><span class="sxs-lookup"><span data-stu-id="cb92b-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="cb92b-114">Так как мы хотим применить к некоторым звукам только переглаголные эффекты, добавим вторую группу для этих звуков.</span><span class="sxs-lookup"><span data-stu-id="cb92b-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="cb92b-115">Чтобы добавить группу, щелкните правой кнопкой мыши главную группу в окне " **аудио-микшер** ", выберите **Добавить дочернюю группу** и укажите подходящее имя, например " _действие комнаты_":</span><span class="sxs-lookup"><span data-stu-id="cb92b-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Добавить дочернюю группу](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

<span data-ttu-id="cb92b-117">Каждая **Группа** имеет собственный набор эффектов.</span><span class="sxs-lookup"><span data-stu-id="cb92b-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="cb92b-118">Чтобы добавить действие в новую группу, нажмите кнопку **Добавить...** в новой группе и выберите пункт **перекоманда SFX**:</span><span class="sxs-lookup"><span data-stu-id="cb92b-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Добавление переглагола SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

<span data-ttu-id="cb92b-120">В терминологии «звук» оригинал, унревербератедный звук называется « _сухой_», а звук после фильтрации с помощью фильтра перезапуска называется «защелка _»._</span><span class="sxs-lookup"><span data-stu-id="cb92b-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="cb92b-121">Оба пути отправляются в выходные данные, и их относительные сильные стороны в этом сочетании называются набором задолженности _/сухой_.</span><span class="sxs-lookup"><span data-stu-id="cb92b-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="cb92b-122">Завлажный или сухой набор сильно влияет на смысл расстояния.</span><span class="sxs-lookup"><span data-stu-id="cb92b-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="cb92b-123">В результате **переглагола SFX** включены элементы управления для корректировки затронутого или сухой набора.</span><span class="sxs-lookup"><span data-stu-id="cb92b-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="cb92b-124">Так как подключаемый модуль **Microsoft спатиализер** обрабатывает сухой путь, мы будем использовать переработку **SFX** только для пути с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="cb92b-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="cb92b-125">На панели инспектора **переглагола SFX**:</span><span class="sxs-lookup"><span data-stu-id="cb92b-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="cb92b-126">Задайте для свойства **уровень сухой** (-10000 МБ) значение наименьшее.</span><span class="sxs-lookup"><span data-stu-id="cb92b-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="cb92b-127">Задайте для **Свойства комнаты** наибольшее значение (0 МБ).</span><span class="sxs-lookup"><span data-stu-id="cb92b-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Свойства переглагола SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

<span data-ttu-id="cb92b-129">Другие параметры управляют имитацией комнаты.</span><span class="sxs-lookup"><span data-stu-id="cb92b-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="cb92b-130">В частности, **время Decay** связано с наблюдаемым размером комнаты.</span><span class="sxs-lookup"><span data-stu-id="cb92b-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="cb92b-131">Включение переглагола при воспроизведении видео</span><span class="sxs-lookup"><span data-stu-id="cb92b-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="cb92b-132">Для включения переглагола в источнике звука необходимо выполнить два действия.</span><span class="sxs-lookup"><span data-stu-id="cb92b-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="cb92b-133">Маршрутизация **источника звука** в соответствующую **группу**</span><span class="sxs-lookup"><span data-stu-id="cb92b-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="cb92b-134">Настройка подключаемого модуля **Microsoft спатиализер** для передачи звука в **группу** для обработки</span><span class="sxs-lookup"><span data-stu-id="cb92b-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="cb92b-135">На следующих шагах вы настроите сценарий для управления маршрутизацией аудио и подключайте сценарий управления, предоставляемый с подключаемым модулем **Microsoft спатиализер** , для передачи данных в переглагол.</span><span class="sxs-lookup"><span data-stu-id="cb92b-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="cb92b-136">Выбрав « **четыре** » в иерархии, щелкните **Добавить компонент** в окне инспектора и добавьте **уровень отправки эффектов комнаты (сценарий)**:</span><span class="sxs-lookup"><span data-stu-id="cb92b-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Добавить скрипт уровня отправки](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="cb92b-138">Если вы не включите **уровень отправки "воздействие на комнату** " в подключаемом модуле **Microsoft спатиализер** , он не отправляет звук обратно в подсистему аудиозаписи Unity для обработки эффектов.</span><span class="sxs-lookup"><span data-stu-id="cb92b-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="cb92b-139">Компонент **уровня отправки "эффекты комнаты** " включает элемент управления "график", который задает уровень звука, отправляемого в подсистему аудиозаписи Unity для обработки в виде переглагола.</span><span class="sxs-lookup"><span data-stu-id="cb92b-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="cb92b-140">Чтобы открыть элемент управления графа, щелкните **уровень отправки эффектов комнаты**.</span><span class="sxs-lookup"><span data-stu-id="cb92b-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="cb92b-141">Щелкните и перетащите зеленую кривую вниз, чтобы установить уровень около-30dB:</span><span class="sxs-lookup"><span data-stu-id="cb92b-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Настройка кривой реглагола](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

<span data-ttu-id="cb92b-143">Затем раскомментируйте 4 строки с комментариями в сценарии **спатиализеонофф** .</span><span class="sxs-lookup"><span data-stu-id="cb92b-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="cb92b-144">Теперь сценарий будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cb92b-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="cb92b-145">После раскомментирования этих строк в инспекторе **сценария спатиализеонофф** добавляются два свойства.</span><span class="sxs-lookup"><span data-stu-id="cb92b-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="cb92b-146">назначьте их в окне инспектора компонента **спатиализеонофф** из **четырех**.</span><span class="sxs-lookup"><span data-stu-id="cb92b-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="cb92b-147">Если объект Quad по-прежнему выбран в иерархии, в окне инспектора выберите компонент **скрипта спатиализеонофф** и:</span><span class="sxs-lookup"><span data-stu-id="cb92b-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="cb92b-148">Установка свойства **группы эффектов комнаты** в новую группу микшеров эффектов комнаты</span><span class="sxs-lookup"><span data-stu-id="cb92b-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="cb92b-149">Задание свойства **главной группы** для главной группы микшера</span><span class="sxs-lookup"><span data-stu-id="cb92b-149">Set the **Master Group** property to the Master mixer group</span></span>

![Спатиализе On Off](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="cb92b-151">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cb92b-151">Congratulations</span></span>

<span data-ttu-id="cb92b-152">Вы завершили учебники по пространственному звуку HoloLens 2 для Unity.</span><span class="sxs-lookup"><span data-stu-id="cb92b-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="cb92b-153">Попробуйте приложение в HoloLens 2 или Unity.</span><span class="sxs-lookup"><span data-stu-id="cb92b-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="cb92b-154">При нажатии кнопки в приложении для активации пространственной связи сценарий перенаправит звук видео в группу эффектов комнаты, чтобы добавить переглагол.</span><span class="sxs-lookup"><span data-stu-id="cb92b-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="cb92b-155">При переключении на стерео вы направите звук в главную группу и не добавите команду.</span><span class="sxs-lookup"><span data-stu-id="cb92b-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="cb92b-156">Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="cb92b-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
