---
title: Пространственные аудио учебники — 4. Включение и отключение пространственного звука во время выполнения
description: Используйте кнопку, чтобы включить или отключить пространственность звука во время выполнения.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: c9e510e544962c5d1a4c462d20dafa222c6a5289
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002609"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Включение и отключение пространственности во время выполнения

## <a name="objectives"></a>Задачи
В этой 4-ой главе вы выполните следующие действия:
* Добавление нового скрипта для управления пространственностью игрового объекта
* Использование сценария управления пространственными из действий кнопки

## <a name="add-spatialization-control-script"></a>Добавление скрипта управления пространственными
Щелкните правой кнопкой мыши в области **проекта** и создайте новый скрипт c#, выбрав **создать-> скрипт c#**. Присвойте своему скрипту имя "Спатиализеонофф".

![Создать скрипт](images/spatial-audio/create-script.png)

Дважды щелкните скрипт в области **проекта** , чтобы открыть его в Visual Studio. Замените содержимое скрипта по умолчанию следующим:

> [!NOTE]
> Несколько строк сценария заносятся в комментарий. Эти строки будут раскомментироваться в [главе 5](unity-spatial-audio-ch5.md).

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
> Чтобы включить или отключить пространственность, скрипт настраивает только свойство **спатиалбленд** , при этом свойство **пространственное** значение включено. В этом режиме Unity по-прежнему применяет кривую **тома** . В противном случае, если пользователю пришлось отключить пространственное расстояние от источника, он будет слышать внезапное увеличение объема данных. <br> <br>
> Если вы предпочитаете полностью отключить пространственность, измените скрипт, чтобы также настроить логическое свойство **пространственности** для переменной **объект SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Присоединение сценария и его добавление с помощью кнопки
На панели **инспектора** в окне « **четыре**» нажмите кнопку **Добавить компонент** и добавьте сценарий **спатиализе On Off** :

![Добавить сценарий к четырем](images/spatial-audio/add-script-to-quad.png)

В компоненте **Спатиализе on** of **четыре**:
1. Найдите в **иерархии** тему **PressableButtonHoloLens2-> Иконандтекст-> текстмешпро** .

![Поиск объекта PressableButtonHoloLens2 в иерархии](images/spatial-audio/pressable-button-object.png)

2. Перетащите тему **текстмешпро** в поле **Буттонтекстобжект** компонента **спатиализе On Off** .

После этих изменений компонент **Спатиализе on** of **четырехъядерия** будет выглядеть следующим образом:

![Спатиализе на отключенном базовом](images/spatial-audio/spatialize-on-off-basic.png)

Чтобы установить кнопку для вызова сценария **Спатиализе On Off** при отпускании кнопки, откройте панель **инспектора** объекта **PressableButtonHoloLens2** , найдите **взаимодействующий** компонент и выполните следующие действия.
1. Поиск региона **OnClick ()** подраздела **событий**
2. Перетащите **Quad** из **иерархии** в область целевого объекта.
3. Выберите **спатиализеонофф. свапспатиализатион** из раскрывающегося списка действие.

После этих изменений **взаимодействующий** компонент будет выглядеть следующим образом:

![Параметры действия кнопки](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Дальнейшие действия
Попробуйте приложение в HoloLens 2 или в редакторе Unity. Теперь в приложении можно нажать кнопку, чтобы активировать и деактивировать пространственность в видео. При тестировании в редакторе Unity нажмите клавишу пробел и прокрутите прокрутку с помощью колесика прокрутки, чтобы активировать моделирование руки. 

> [!div class="nextstepaction"]
> [Глава 5](unity-spatial-audio-ch5.md) 

