---
title: Пространственные аудио учебники — 4. Включение и отключение пространственного звука во время выполнения
description: Используйте кнопку, чтобы включить или отключить пространственность звука во время выполнения.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590736"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Включение и отключение функции пространственности во время выполнения

## <a name="overview"></a>Обзор

В этом руководстве вы узнаете, как включить и отключить пространственное выполнение во время выполнения и проверить это в редакторе Unity и HoloLens 2.

## <a name="objectives"></a>Задачи

* Добавление нового скрипта для управления пространственностью игрового объекта
* Использование сценария управления пространственными из действий кнопки

## <a name="add-spatialization-control-script"></a>Добавление скрипта управления пространственными

 Щелкните правой кнопкой мыши в окне проекта и выберите **создать**  >  **Скрипт c#** , чтобы создать новый скрипт c#, введите подходящее имя для скрипта, например _спатиализеонофф_:

![Создать скрипт](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Дважды щелкните скрипт в окне проекта, чтобы открыть его в Visual Studio. Замените содержимое скрипта по умолчанию следующим:

> [!NOTE]
> Несколько строк сценария заносятся в комментарий. Эти строки будут раскомментироваться в [следующей главе: использование переглагола для добавления расстояния к пространственному аудио](unity-spatial-audio-ch5.md).

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
> Чтобы включить или отключить пространственность, скрипт настраивает только свойство **спатиалбленд** , а свойство **пространственное** включено. В этом режиме Unity по-прежнему применяет кривую **тома** . В противном случае, если пользователю пришлось отключить пространственное расстояние от источника, он будет слышать внезапное увеличение объема данных.
> Если вы предпочитаете полностью отключить пространственность, измените скрипт, чтобы также настроить логическое свойство **пространственности** для переменной **объект SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Присоединение сценария и его добавление с помощью кнопки

Выберите « **четыре** » в иерархии и в окне инспектора нажмите кнопку Добавить компонент, чтобы добавить **спатиализеонофф (сценарий)** .

![Добавить сценарий к четырем](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

В иерархии откройте **PressableButtonHoloLens2**  >  **иконандтекст**  >  **текстмешпро**.

Если объект **Quad** по-прежнему выбран в иерархии, в окне инспектора выберите компонент **спатиализе On Off (скрипт)** и перетащите компонент **текстмешпро** в PressableButtonHoloLens2.

![Поиск объекта PressableButtonHoloLens2 в иерархии](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Чтобы установить для кнопки вызов скрипта **спатиализеонофф** при отпускании кнопки, необходимо настроить взаимодействующий скрипт.

В окне Иерархия выберите **PressableButtonHoloLens2**. В окне инспектора выберите компонент " **взаимодействие (скрипт)** " и щелкните значок "+" под событием OnClick ().

* Когда объект **PressableButtonHoloLens2** все еще выбран в окне Иерархия, щелкните и перетащите объект **Quad** из окна Иерархия в пустое поле **нет (объект)** события, которое вы только что добавили, чтобы объект буттонпарент прослушивает событие нажатия кнопки мыши на этой кнопке:

* Откройте раскрывающийся список **No Function** (Нет функции) того же события. Затем выберите **спатиализеонофф**  >  **свапспатиализатион ()** , чтобы включить и отключить Пространственный звук.

![Параметры действия кнопки](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Поздравляем!

В этом руководстве вы узнали, как включать и отключать пространственные во время выполнения, тестировать приложение на HoloLens 2 или в редакторе Unity. Теперь в приложении можно нажать кнопку, чтобы активировать и деактивировать пространственность звука.

В следующем учебном курсе вы добавите действие с переглаголом, чтобы дать звуковое представление о расстоянии.

> [!TIP]
> Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Следующее руководство: 5. Использование команды REVERB для добавления расстояния в пространственный звук](unity-spatial-audio-ch5.md)
