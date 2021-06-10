---
title: Пространственные аудио учебники — 4. Включение и отключение пространственного звука во время выполнения
description: Используйте кнопку, чтобы включить или отключить пространственность звука во время выполнения.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712759"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="b9d34-105">4. Включение и отключение функции пространственности во время выполнения</span><span class="sxs-lookup"><span data-stu-id="b9d34-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="b9d34-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="b9d34-106">Overview</span></span>

<span data-ttu-id="b9d34-107">В этом руководстве вы узнаете, как включить и отключить пространственное выполнение во время выполнения и проверить это в редакторе Unity и HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b9d34-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="b9d34-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="b9d34-108">Objectives</span></span>

* <span data-ttu-id="b9d34-109">Добавление нового скрипта для управления пространственностью игрового объекта</span><span class="sxs-lookup"><span data-stu-id="b9d34-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="b9d34-110">Использование сценария управления пространственными из действий кнопки</span><span class="sxs-lookup"><span data-stu-id="b9d34-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="b9d34-111">Добавление скрипта управления пространственными</span><span class="sxs-lookup"><span data-stu-id="b9d34-111">Add spatialization control script</span></span>

 <span data-ttu-id="b9d34-112">Щелкните правой кнопкой мыши в окне проекта и выберите **создать**  >  **Скрипт c#** , чтобы создать новый скрипт c#, введите подходящее имя для скрипта, например _спатиализеонофф_:</span><span class="sxs-lookup"><span data-stu-id="b9d34-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Создать сценарий](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="b9d34-114">Дважды щелкните скрипт в окне проекта, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9d34-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="b9d34-115">Замените содержимое скрипта по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="b9d34-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="b9d34-116">Несколько строк сценария заносятся в комментарий. Эти строки будут раскомментироваться в [следующей главе: использование переглагола для добавления расстояния к пространственному аудио](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="b9d34-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="b9d34-117">Чтобы включить или отключить пространственность, скрипт настраивает только свойство **спатиалбленд** , а свойство **пространственное** включено.</span><span class="sxs-lookup"><span data-stu-id="b9d34-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="b9d34-118">В этом режиме Unity по-прежнему применяет кривую **тома** .</span><span class="sxs-lookup"><span data-stu-id="b9d34-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="b9d34-119">В противном случае, если пользователю пришлось отключить пространственное расстояние от источника, он будет слышать внезапное увеличение объема данных.</span><span class="sxs-lookup"><span data-stu-id="b9d34-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="b9d34-120">Если вы предпочитаете полностью отключить пространственность, измените скрипт, чтобы также настроить логическое свойство **пространственности** для переменной **объект SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="b9d34-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="b9d34-121">Присоединение сценария и его добавление с помощью кнопки</span><span class="sxs-lookup"><span data-stu-id="b9d34-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="b9d34-122">Выберите « **четыре** » в иерархии и в окне инспектора нажмите кнопку Добавить компонент, чтобы добавить **спатиализеонофф (сценарий)** .</span><span class="sxs-lookup"><span data-stu-id="b9d34-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Добавить сценарий к четырем](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="b9d34-124">В иерархии откройте **PressableButtonHoloLens2**  >  **иконандтекст**  >  **текстмешпро**.</span><span class="sxs-lookup"><span data-stu-id="b9d34-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="b9d34-125">Если объект **Quad** по-прежнему выбран в иерархии, в окне инспектора выберите компонент **спатиализе On Off (скрипт)** и перетащите компонент **текстмешпро** в PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="b9d34-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Поиск объекта PressableButtonHoloLens2 в иерархии](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="b9d34-127">Чтобы установить для кнопки вызов скрипта **спатиализеонофф** при отпускании кнопки, необходимо настроить взаимодействующий скрипт.</span><span class="sxs-lookup"><span data-stu-id="b9d34-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="b9d34-128">В окне Иерархия выберите **PressableButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="b9d34-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="b9d34-129">В окне инспектора выберите компонент " **взаимодействие (скрипт)** " и щелкните значок "+" под событием OnClick ().</span><span class="sxs-lookup"><span data-stu-id="b9d34-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="b9d34-130">Когда объект **PressableButtonHoloLens2** все еще выбран в окне Иерархия, щелкните и перетащите объект **Quad** из окна Иерархия в пустое поле **нет (объект)** события, которое вы только что добавили, чтобы объект буттонпарент прослушивает событие нажатия кнопки мыши на этой кнопке:</span><span class="sxs-lookup"><span data-stu-id="b9d34-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="b9d34-131">Откройте раскрывающийся список **No Function** (Нет функции) того же события.</span><span class="sxs-lookup"><span data-stu-id="b9d34-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="b9d34-132">Затем выберите **спатиализеонофф**  >  **свапспатиализатион ()** , чтобы включить и отключить Пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="b9d34-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Параметры действия кнопки](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="b9d34-134">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b9d34-134">Congratulations</span></span>

<span data-ttu-id="b9d34-135">В этом руководстве вы узнали, как включать и отключать пространственные во время выполнения, тестировать приложение на HoloLens 2 или в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="b9d34-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="b9d34-136">Теперь в приложении можно нажать кнопку, чтобы активировать и деактивировать пространственность звука.</span><span class="sxs-lookup"><span data-stu-id="b9d34-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="b9d34-137">В следующем учебном курсе вы добавите действие с переглаголом, чтобы дать звуковое представление о расстоянии.</span><span class="sxs-lookup"><span data-stu-id="b9d34-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="b9d34-138">Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="b9d34-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b9d34-139">Следующее руководство: 5. Использование команды REVERB для добавления расстояния в пространственный звук</span><span class="sxs-lookup"><span data-stu-id="b9d34-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
