---
title: Включение и отключение пространственного звука во время выполнения
description: Узнайте, как написать сценарий C#, использующий кнопку для включения и отключения пространственной речи во время выполнения.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: eaaf8a05088b5bab674ca11b15b0c63383faa479
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007344"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="49a0c-104">Включение и отключение пространственности во время выполнения</span><span class="sxs-lookup"><span data-stu-id="49a0c-104">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="49a0c-105">Задачи</span><span class="sxs-lookup"><span data-stu-id="49a0c-105">Objectives</span></span>

<span data-ttu-id="49a0c-106">В этой 4-ой главе вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="49a0c-106">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="49a0c-107">Добавление нового скрипта для управления пространственностью игрового объекта</span><span class="sxs-lookup"><span data-stu-id="49a0c-107">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="49a0c-108">Использование сценария управления пространственными из действий кнопки</span><span class="sxs-lookup"><span data-stu-id="49a0c-108">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="49a0c-109">Добавление скрипта управления пространственными</span><span class="sxs-lookup"><span data-stu-id="49a0c-109">Add spatialization control script</span></span>

<span data-ttu-id="49a0c-110">Щелкните правой кнопкой мыши в области **проекта** и создайте новый скрипт c#, выбрав **создать-> скрипт c#**.</span><span class="sxs-lookup"><span data-stu-id="49a0c-110">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="49a0c-111">Присвойте своему скрипту имя "Спатиализеонофф".</span><span class="sxs-lookup"><span data-stu-id="49a0c-111">Name your script "SpatializeOnOff".</span></span>

![Создать скрипт](images/spatial-audio/create-script.png)

<span data-ttu-id="49a0c-113">Дважды щелкните скрипт в области **проекта** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49a0c-113">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="49a0c-114">Замените содержимое скрипта по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="49a0c-114">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="49a0c-115">Несколько строк сценария заносятся в комментарий. Эти строки будут раскомментироваться в [главе 5](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="49a0c-115">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="49a0c-116">Чтобы включить или отключить пространственность, скрипт настраивает только свойство **спатиалбленд** , при этом свойство **пространственное** значение включено.</span><span class="sxs-lookup"><span data-stu-id="49a0c-116">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="49a0c-117">В этом режиме Unity по-прежнему применяет кривую **тома** .</span><span class="sxs-lookup"><span data-stu-id="49a0c-117">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="49a0c-118">В противном случае, если пользователю пришлось отключить пространственное расстояние от источника, он будет слышать внезапное увеличение объема данных.</span><span class="sxs-lookup"><span data-stu-id="49a0c-118">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="49a0c-119">Если вы предпочитаете полностью отключить пространственность, измените скрипт, чтобы также настроить логическое свойство **пространственности** для переменной **объект SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="49a0c-119">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="49a0c-120">Присоединение сценария и его добавление с помощью кнопки</span><span class="sxs-lookup"><span data-stu-id="49a0c-120">Attach your script and drive it from the button</span></span>

<span data-ttu-id="49a0c-121">На панели **инспектора** в окне « **четыре**» нажмите кнопку **Добавить компонент** и добавьте сценарий **спатиализе On Off** :</span><span class="sxs-lookup"><span data-stu-id="49a0c-121">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Добавить сценарий к четырем](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="49a0c-123">В компоненте **Спатиализе on** of **четыре**:</span><span class="sxs-lookup"><span data-stu-id="49a0c-123">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="49a0c-124">Найдите в **иерархии** тему **PressableButtonHoloLens2-> Иконандтекст-> текстмешпро** .</span><span class="sxs-lookup"><span data-stu-id="49a0c-124">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![Поиск объекта PressableButtonHoloLens2 в иерархии](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="49a0c-126">Перетащите тему **текстмешпро** в поле **Буттонтекстобжект** компонента **спатиализе On Off** .</span><span class="sxs-lookup"><span data-stu-id="49a0c-126">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="49a0c-127">После этих изменений компонент **Спатиализе on** of **четырехъядерия** будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="49a0c-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Спатиализе на отключенном базовом](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="49a0c-129">Чтобы установить кнопку для вызова сценария **Спатиализе On Off** при отпускании кнопки, откройте панель **инспектора** объекта **PressableButtonHoloLens2** , найдите **взаимодействующий** компонент и выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="49a0c-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="49a0c-130">Поиск региона **OnClick ()** подраздела **событий**</span><span class="sxs-lookup"><span data-stu-id="49a0c-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="49a0c-131">Перетащите **Quad** из **иерархии** в область целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="49a0c-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="49a0c-132">Выберите **спатиализеонофф. свапспатиализатион** из раскрывающегося списка действие.</span><span class="sxs-lookup"><span data-stu-id="49a0c-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="49a0c-133">После этих изменений **взаимодействующий** компонент будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="49a0c-133">After these changes, the **Interactable** component will look like this:</span></span>

![Параметры действия кнопки](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="49a0c-135">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="49a0c-135">Next steps</span></span>

<span data-ttu-id="49a0c-136">Попробуйте приложение в HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="49a0c-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="49a0c-137">Теперь в приложении можно нажать кнопку, чтобы активировать и деактивировать пространственность в видео.</span><span class="sxs-lookup"><span data-stu-id="49a0c-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="49a0c-138">При тестировании в редакторе Unity нажмите клавишу пробел и прокрутите прокрутку с помощью колесика прокрутки, чтобы активировать моделирование руки.</span><span class="sxs-lookup"><span data-stu-id="49a0c-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="49a0c-139">Глава 5</span><span class="sxs-lookup"><span data-stu-id="49a0c-139">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

