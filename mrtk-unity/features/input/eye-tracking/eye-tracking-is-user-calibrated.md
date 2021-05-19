---
title: Калибровка глаз
description: Как настроить калибровку глаз пользователя в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг, калибровка,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144007"
---
# <a name="eye-calibration"></a><span data-ttu-id="49d9f-104">Калибровка глаз</span><span class="sxs-lookup"><span data-stu-id="49d9f-104">Eye calibration</span></span>

![Снимок экрана с уведомлением об калибровке глаз](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="49d9f-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="49d9f-106">Overview</span></span>

<span data-ttu-id="49d9f-107">Если отслеживание взгляда является фундаментальной частью работы приложения, то может потребоваться обеспечить правильную калибровку пользователя.</span><span class="sxs-lookup"><span data-stu-id="49d9f-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="49d9f-108">Основная причина, по которой она будет недействительной, заключается в том, что пользователь решил пропустить калибровку отслеживания взгляда при размещении на устройстве.</span><span class="sxs-lookup"><span data-stu-id="49d9f-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="49d9f-109">На этой странице рассматриваются следующие вопросы:</span><span class="sxs-lookup"><span data-stu-id="49d9f-109">This page covers the following:</span></span>

- <span data-ttu-id="49d9f-110">Описывает, как определить, что пользователь имеет откалиброванный глаз</span><span class="sxs-lookup"><span data-stu-id="49d9f-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="49d9f-111">В этом примере показано, как активировать уведомление пользователя, чтобы сообщить пользователю о необходимости пройти калибровку глаз.</span><span class="sxs-lookup"><span data-stu-id="49d9f-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="49d9f-112">Автоматически отклонять уведомление, если калибровка глаз станет действительной</span><span class="sxs-lookup"><span data-stu-id="49d9f-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="49d9f-113">Вручную закрыть уведомление, если пользователь решил продолжить без калибровки</span><span class="sxs-lookup"><span data-stu-id="49d9f-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="49d9f-114">Как определить состояние калибровки глаз</span><span class="sxs-lookup"><span data-stu-id="49d9f-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="49d9f-115">Конфигурация отслеживания взгляда в МРТК настраивается через [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="49d9f-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="49d9f-116">Использование [коресервицес. инпутсистем. эйегазепровидер](eye-tracking-eye-gaze-provider.md) предоставляет реализацию поставщика взгляда по умолчанию, зарегистрированную в наборе средств во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="49d9f-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="49d9f-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` Возвращает значение типа, `bool?` равное NULL, если данные из средства регистрации взглядов еще не доступны.</span><span class="sxs-lookup"><span data-stu-id="49d9f-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="49d9f-118">После получения данных будет возвращено значение true или false, чтобы указать, что калибровка отслеживания взгляда пользователя является допустимой или недопустимой.</span><span class="sxs-lookup"><span data-stu-id="49d9f-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="49d9f-119">Уведомление об калибровке образца глаз — пошаговые инструкции</span><span class="sxs-lookup"><span data-stu-id="49d9f-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="49d9f-120">Откройте пример пакета отслеживания взгляда МРТК (Assets/МРТК/examples/демонстрации/Эйетраккинг)</span><span class="sxs-lookup"><span data-stu-id="49d9f-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="49d9f-121">Загрузка сцены _эйетраккингдемо-00-рутсцене. Unity_</span><span class="sxs-lookup"><span data-stu-id="49d9f-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="49d9f-122">Ознакомьтесь с _эйекалибратиончеккер_:</span><span class="sxs-lookup"><span data-stu-id="49d9f-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="49d9f-123">В этой сцене уже есть пример, с помощью которого можно определить, откалиброван ли текущий пользователь в *игровом объекте _эйекалибратиончеккер_*.</span><span class="sxs-lookup"><span data-stu-id="49d9f-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="49d9f-124">Он просто объединяет несколько текстовых сеток и имеет несколько дополнительных триггеров для смешения уведомлений. Это включает в себя медленно увеличивающийся размер и непрозрачность при активации.</span><span class="sxs-lookup"><span data-stu-id="49d9f-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="49d9f-125">Как только уведомление будет закрыто, оно постепенно снизит его размер и плавно уменьшится.</span><span class="sxs-lookup"><span data-stu-id="49d9f-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="49d9f-126">К *игровому объекту _эйекалибратиончеккер_* прикрепляется скрипт [Эйекалибратиончеккер](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) , который предоставляет два события Unity:</span><span class="sxs-lookup"><span data-stu-id="49d9f-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="49d9f-127">Эти события будут запускаться только при изменении состояния калибровки.</span><span class="sxs-lookup"><span data-stu-id="49d9f-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="49d9f-128">Таким образом, если пользователь откроет уведомление, уведомление не отобразится снова до тех пор, пока</span><span class="sxs-lookup"><span data-stu-id="49d9f-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="49d9f-129">Приложение перезапускается</span><span class="sxs-lookup"><span data-stu-id="49d9f-129">The app gets restarted</span></span>
      - <span data-ttu-id="49d9f-130">Обнаружен допустимый пользователь, а затем новый некалиброванный пользователь поместит устройство в</span><span class="sxs-lookup"><span data-stu-id="49d9f-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="49d9f-131">Чтобы проверить, правильно ли запущены анимации и события, сценарий Эйекалибратиончеккер имеет `bool editorTestUserIsCalibrated` флаг.</span><span class="sxs-lookup"><span data-stu-id="49d9f-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="49d9f-132">Например, при запуске в редакторе Unity можно протестировать:</span><span class="sxs-lookup"><span data-stu-id="49d9f-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="49d9f-133">Будет ли уведомление автоматически выводится после того, как состояние калибровки изменится с true на false</span><span class="sxs-lookup"><span data-stu-id="49d9f-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="49d9f-134">Будет ли он автоматически закрывать уведомление после изменения состояния с false на true.</span><span class="sxs-lookup"><span data-stu-id="49d9f-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="49d9f-135">См. также</span><span class="sxs-lookup"><span data-stu-id="49d9f-135">See also</span></span>

- [<span data-ttu-id="49d9f-136">Общие сведения об отслеживании МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="49d9f-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="49d9f-137">Настройка отслеживания МРТКных глаз</span><span class="sxs-lookup"><span data-stu-id="49d9f-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="49d9f-138">Отслеживание взгляда МРТК с помощью кода</span><span class="sxs-lookup"><span data-stu-id="49d9f-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="49d9f-139">Документация по отслеживания взгляда HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="49d9f-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)