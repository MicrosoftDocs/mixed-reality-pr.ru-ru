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
# <a name="scene-transition-service"></a><span data-ttu-id="68e54-104">Служба смены сцены</span><span class="sxs-lookup"><span data-stu-id="68e54-104">Scene transition service</span></span>

<span data-ttu-id="68e54-105">Это расширение упрощает развитие сцены, выводит индикатор выполнения, загружает сцену, а затем постепенно проводятся.</span><span class="sxs-lookup"><span data-stu-id="68e54-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="68e54-106">Операции с сценами управляются службой Сценесистем, но для управления переходом можно использовать любые операции на основе задач.</span><span class="sxs-lookup"><span data-stu-id="68e54-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="68e54-107">Включение расширения</span><span class="sxs-lookup"><span data-stu-id="68e54-107">Enabling the extension</span></span>

<span data-ttu-id="68e54-108">Чтобы включить расширение, откройте профиль Регистередсервицепровидер.</span><span class="sxs-lookup"><span data-stu-id="68e54-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="68e54-109">Щелкните зарегистрировать новый поставщик услуг, чтобы добавить новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="68e54-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="68e54-110">В поле Тип компонента выберите Сценетранситионсервице.</span><span class="sxs-lookup"><span data-stu-id="68e54-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="68e54-111">В поле профиль конфигурации выберите профиль перехода по умолчанию для сцен, входящий в состав расширения.</span><span class="sxs-lookup"><span data-stu-id="68e54-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="68e54-112">Параметры профиля</span><span class="sxs-lookup"><span data-stu-id="68e54-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="68e54-113">Использовать индикатор хода выполнения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="68e54-113">Use default progress indicator</span></span>

<span data-ttu-id="68e54-114">Если флажок установлен, по умолчанию используется индикатор хода выполнения по умолчанию prefab, если при вызове объекта индикатора выполнения он будет `DoSceneTransition.` пропущен.</span><span class="sxs-lookup"><span data-stu-id="68e54-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="68e54-115">Использовать цвет затухания</span><span class="sxs-lookup"><span data-stu-id="68e54-115">Use fade color</span></span>

<span data-ttu-id="68e54-116">Если этот флажок установлен, служба переходов будет применять эффект исчезания во время перехода.</span><span class="sxs-lookup"><span data-stu-id="68e54-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="68e54-117">Этот параметр можно изменить во время выполнения через `UseFadeColor` свойство службы.</span><span class="sxs-lookup"><span data-stu-id="68e54-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="68e54-118">Цвет затухания</span><span class="sxs-lookup"><span data-stu-id="68e54-118">Fade color</span></span>

<span data-ttu-id="68e54-119">Управляет цветом эффекта угасания.</span><span class="sxs-lookup"><span data-stu-id="68e54-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="68e54-120">Альфа игнорируется.</span><span class="sxs-lookup"><span data-stu-id="68e54-120">Alpha is ignored.</span></span> <span data-ttu-id="68e54-121">Этот параметр можно изменить во время выполнения до перехода через `FadeColor` свойство службы.</span><span class="sxs-lookup"><span data-stu-id="68e54-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="68e54-122">Объекты исчезания</span><span class="sxs-lookup"><span data-stu-id="68e54-122">Fade targets</span></span>

<span data-ttu-id="68e54-123">Определяет, к каким камерам будет применен эффект угасания.</span><span class="sxs-lookup"><span data-stu-id="68e54-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="68e54-124">Этот параметр можно изменить во время выполнения через `FadeTargets` свойство службы.</span><span class="sxs-lookup"><span data-stu-id="68e54-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="68e54-125">Параметр</span><span class="sxs-lookup"><span data-stu-id="68e54-125">Setting</span></span> | <span data-ttu-id="68e54-126">Целевые камеры</span><span class="sxs-lookup"><span data-stu-id="68e54-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="68e54-127">Главная ветвь</span><span class="sxs-lookup"><span data-stu-id="68e54-127">Main</span></span> | <span data-ttu-id="68e54-128">Применяет эффект исчезания к основной камере.</span><span class="sxs-lookup"><span data-stu-id="68e54-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="68e54-129">Пользовательский интерфейс</span><span class="sxs-lookup"><span data-stu-id="68e54-129">UI</span></span> | <span data-ttu-id="68e54-130">Применяет эффект исчезания к камерам на уровне пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="68e54-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="68e54-131">(Не влияет на пользовательский интерфейс наложения)</span><span class="sxs-lookup"><span data-stu-id="68e54-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="68e54-132">Все</span><span class="sxs-lookup"><span data-stu-id="68e54-132">All</span></span> | <span data-ttu-id="68e54-133">Применяется как к основной, так и к камерам пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="68e54-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="68e54-134">Другой</span><span class="sxs-lookup"><span data-stu-id="68e54-134">Custom</span></span> | <span data-ttu-id="68e54-135">Применяется к пользовательскому набору камер, предоставляемых через `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="68e54-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="68e54-136">Исчезание времени и исчезновения по времени</span><span class="sxs-lookup"><span data-stu-id="68e54-136">Fade out time / fade in time</span></span>

<span data-ttu-id="68e54-137">Параметры по умолчанию для длительности перезатухания при входе или выходе из перехода.</span><span class="sxs-lookup"><span data-stu-id="68e54-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="68e54-138">Эти параметры можно изменить во время выполнения с помощью свойств службы `FadeOutTime` и `FadeInTime` .</span><span class="sxs-lookup"><span data-stu-id="68e54-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="68e54-139">Тип фадер камеры</span><span class="sxs-lookup"><span data-stu-id="68e54-139">Camera fader type</span></span>

<span data-ttu-id="68e54-140">`ICameraFader`Класс, используемый для применения эффекта угасания к камерам.</span><span class="sxs-lookup"><span data-stu-id="68e54-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="68e54-141">Класс по умолчанию `CameraFaderQuad` создает экземпляр «четыре» с прозрачным материалом перед целевой камерой, близкой к плоскости обрезки.</span><span class="sxs-lookup"><span data-stu-id="68e54-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="68e54-142">Другим подходом может быть использование системы отправки эффектов.</span><span class="sxs-lookup"><span data-stu-id="68e54-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="68e54-143">Использование расширения</span><span class="sxs-lookup"><span data-stu-id="68e54-143">Using the extension</span></span>

<span data-ttu-id="68e54-144">Служба переходов используется путем передачи задач, выполняемых при прохождении камеры.</span><span class="sxs-lookup"><span data-stu-id="68e54-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="68e54-145">Использование системных задач сцены</span><span class="sxs-lookup"><span data-stu-id="68e54-145">Using scene system tasks</span></span>

<span data-ttu-id="68e54-146">В большинстве случаев вы будете использовать задачи, предоставляемые службой Сценесистем:</span><span class="sxs-lookup"><span data-stu-id="68e54-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

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

### <a name="using-custom-tasks"></a><span data-ttu-id="68e54-147">Использование пользовательских задач</span><span class="sxs-lookup"><span data-stu-id="68e54-147">Using custom tasks</span></span>

<span data-ttu-id="68e54-148">В других случаях может потребоваться выполнить переход без фактической загрузки сцены:</span><span class="sxs-lookup"><span data-stu-id="68e54-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

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

<span data-ttu-id="68e54-149">Или вы можете загрузить сцену без использования службы Сценесистем:</span><span class="sxs-lookup"><span data-stu-id="68e54-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

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

### <a name="using-multiple-tasks"></a><span data-ttu-id="68e54-150">Использование нескольких задач</span><span class="sxs-lookup"><span data-stu-id="68e54-150">Using multiple tasks</span></span>

<span data-ttu-id="68e54-151">Можно также указать несколько задач, которые будут выполняться по порядку:</span><span class="sxs-lookup"><span data-stu-id="68e54-151">You can also supply multiple tasks, which will be executed in order:</span></span>

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

## <a name="using-the-progress-indicator"></a><span data-ttu-id="68e54-152">Использование индикатора выполнения</span><span class="sxs-lookup"><span data-stu-id="68e54-152">Using the progress indicator</span></span>

<span data-ttu-id="68e54-153">Индикатор выполнения — это любой объект, реализующий `IProgressIndicator` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="68e54-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="68e54-154">Это может быть экран-заставка, индикатор загрузки объемного тагалонга или любое другое, которое предоставляет отзыв о ходе перехода.</span><span class="sxs-lookup"><span data-stu-id="68e54-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="68e54-155">Если `UseDefaultProgressIndicator` в профиле сценетранситионсервице установлен флажок, то при начале перехода будет создан экземпляр индикатора хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="68e54-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="68e54-156">На время перехода этот индикатор `Progress` и `Message` свойства могут быть доступны через `SetProgressValue` `SetProgressMessage` методы и.</span><span class="sxs-lookup"><span data-stu-id="68e54-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

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

<span data-ttu-id="68e54-157">Кроме того, при вызове `DoSceneTransition` можно указать собственный индикатор хода выполнения с помощью необязательного `progressIndicator` аргумента.</span><span class="sxs-lookup"><span data-stu-id="68e54-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="68e54-158">Это переопределит индикатор хода выполнения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="68e54-158">This will override the default progress indicator.</span></span>
