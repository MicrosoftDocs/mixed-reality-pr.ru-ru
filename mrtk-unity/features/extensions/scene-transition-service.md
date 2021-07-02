---
title: Служба смены сцены
description: Документация по переходу на сцену в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, сценетранситион,
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176214"
---
# <a name="scene-transition-service"></a>Служба смены сцены

Это расширение упрощает развитие сцены, выводит индикатор выполнения, загружает сцену, а затем постепенно проводятся.

Операции с сценами управляются службой Сценесистем, но для управления переходом можно использовать любые операции на основе задач.

## <a name="enabling-the-extension"></a>Включение расширения

Чтобы включить расширение, откройте профиль Регистередсервицепровидер. Щелкните зарегистрировать новый поставщик услуг, чтобы добавить новую конфигурацию. В поле Тип компонента выберите Сценетранситионсервице. В поле профиль конфигурации выберите профиль перехода по умолчанию для сцен, входящий в состав расширения.

## <a name="profile-options"></a>Параметры профиля

### <a name="use-default-progress-indicator"></a>Использовать индикатор хода выполнения по умолчанию

Если флажок установлен, по умолчанию используется индикатор хода выполнения по умолчанию prefab, если при вызове объекта индикатора выполнения он будет `DoSceneTransition.` пропущен.

### <a name="use-fade-color"></a>Использовать цвет затухания

Если этот флажок установлен, служба переходов будет применять эффект исчезания во время перехода. Этот параметр можно изменить во время выполнения через `UseFadeColor` свойство службы.

### <a name="fade-color"></a>Цвет затухания

Управляет цветом эффекта угасания. Альфа игнорируется. Этот параметр можно изменить во время выполнения до перехода через `FadeColor` свойство службы.

### <a name="fade-targets"></a>Объекты исчезания

Определяет, к каким камерам будет применен эффект угасания. Этот параметр можно изменить во время выполнения через `FadeTargets` свойство службы.

Параметр | Целевые камеры
--- | --- | ---
Главная ветвь | Применяет эффект исчезания к основной камере.
Пользовательский интерфейс | Применяет эффект исчезания к камерам на уровне пользовательского интерфейса. (Не влияет на пользовательский интерфейс наложения)
Все | Применяется как к основной, так и к камерам пользовательского интерфейса.
Другой | Применяется к пользовательскому набору камер, предоставляемых через `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Исчезание времени и исчезновения по времени

Параметры по умолчанию для длительности перезатухания при входе или выходе из перехода. Эти параметры можно изменить во время выполнения с помощью свойств службы `FadeOutTime` и `FadeInTime` .

### <a name="camera-fader-type"></a>Тип фадер камеры

`ICameraFader`Класс, используемый для применения эффекта угасания к камерам. Класс по умолчанию `CameraFaderQuad` создает экземпляр «четыре» с прозрачным материалом перед целевой камерой, близкой к плоскости обрезки. Другим подходом может быть использование системы отправки эффектов.

## <a name="using-the-extension"></a>Использование расширения

Служба переходов используется путем передачи задач, выполняемых при прохождении камеры.

### <a name="using-scene-system-tasks"></a>Использование системных задач сцены

В большинстве случаев вы будете использовать задачи, предоставляемые службой Сценесистем:

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a>Использование пользовательских задач

В других случаях может потребоваться выполнить переход без фактической загрузки сцены:

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

Или вы можете загрузить сцену без использования службы Сценесистем:

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a>Использование нескольких задач

Можно также указать несколько задач, которые будут выполняться по порядку:

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a>Использование индикатора выполнения

Индикатор выполнения — это любой объект, реализующий `IProgressIndicator` интерфейс. Это может быть экран-заставка, индикатор загрузки объемного тагалонга или любое другое, которое предоставляет отзыв о ходе перехода.

Если `UseDefaultProgressIndicator` в профиле сценетранситионсервице установлен флажок, то при начале перехода будет создан экземпляр индикатора хода выполнения. На время перехода этот индикатор `Progress` и `Message` свойства могут быть доступны через `SetProgressValue` `SetProgressMessage` методы и.

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

Кроме того, при вызове `DoSceneTransition` можно указать собственный индикатор хода выполнения с помощью необязательного `progressIndicator` аргумента. Это переопределит индикатор хода выполнения по умолчанию.
