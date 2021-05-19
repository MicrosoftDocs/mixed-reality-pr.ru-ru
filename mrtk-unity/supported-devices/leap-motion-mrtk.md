---
title: Leap Motion — MRTK
description: Документация по настройке LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, LEAP Motion,
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145197"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="d0801-104">Как настроить отслеживание движения с помощью LEAP (by Ултралеап) в МРТК</span><span class="sxs-lookup"><span data-stu-id="d0801-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="d0801-105">Для использования этого поставщика данных требуется [контроллер движения LEAP](https://www.ultraleap.com/product/leap-motion-controller/) .</span><span class="sxs-lookup"><span data-stu-id="d0801-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="d0801-106">Поставщик данных о движении LEAP обеспечивает управляемую функцию отслеживания для VR и может быть полезна для быстрого создания прототипов в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d0801-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="d0801-107">Поставщик данных может быть настроен на использование контроллера Motion LEAP, подключенного к гарнитуре или находящийся на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="d0801-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![леапмотионинтрогиф](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="d0801-109">Этот поставщик можно использовать в редакторе и на устройстве на автономной платформе.</span><span class="sxs-lookup"><span data-stu-id="d0801-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="d0801-110">Его также можно использовать в редакторе на платформе UWP, но не в сборке UWP.</span><span class="sxs-lookup"><span data-stu-id="d0801-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="d0801-111">Поддерживаемые версии модулей Unity для LEAP</span><span class="sxs-lookup"><span data-stu-id="d0801-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="d0801-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="d0801-112">4.5.0</span></span>|
|<span data-ttu-id="d0801-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d0801-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="d0801-114">Отслеживание движения с помощью LEAP (by Ултралеап) в МРТК</span><span class="sxs-lookup"><span data-stu-id="d0801-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="d0801-115">Импорт модулей Unity МРТК и LEAP Motion</span><span class="sxs-lookup"><span data-stu-id="d0801-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="d0801-116">Установите [пакет SDK для LEAP Motion 4.0.0](https://developer.leapmotion.com/releases/?category=orion) , если он еще не установлен.</span><span class="sxs-lookup"><span data-stu-id="d0801-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="d0801-117">Импортируйте пакет **Microsoft. микседреалити. Toolkit. Foundation** в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="d0801-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="d0801-118">Скачайте и импортируйте в проект последнюю версию [модулей Unity Motion](https://developer.leapmotion.com/unity) .</span><span class="sxs-lookup"><span data-stu-id="d0801-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="d0801-119">Импортировать **основной** пакет только в пределах модулей Unity</span><span class="sxs-lookup"><span data-stu-id="d0801-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="d0801-120">Интеграция модулей Unity в LEAP с МРТК</span><span class="sxs-lookup"><span data-stu-id="d0801-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="d0801-121">После того как модули Unity находятся в проекте, перейдите к разделу " **Смешанная реальность Toolkit** с  >  **LEAP Motion**  >  **Интеграция LEAP" модули Unity**</span><span class="sxs-lookup"><span data-stu-id="d0801-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="d0801-122">Интеграция модулей Unity в МРТК добавляет 10 определений сборок в проект и добавляет ссылки на определение сборки **Microsoft. микседреалити. Toolkit. Providers. леапмотион** .</span><span class="sxs-lookup"><span data-stu-id="d0801-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="d0801-123">Убедитесь, что среда Visual Studio закрыта.</span><span class="sxs-lookup"><span data-stu-id="d0801-123">Make sure Visual Studio is closed.</span></span>

     ![леапмотионинтегратион](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="d0801-125">Добавление поставщика данных о движении LEAP</span><span class="sxs-lookup"><span data-stu-id="d0801-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="d0801-126">Создание новой сцены Unity</span><span class="sxs-lookup"><span data-stu-id="d0801-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="d0801-127">Добавьте мртк в сцену, перейдя к **набору средств Mixed Reality**  >  **Добавить в сцену и настроить** .</span><span class="sxs-lookup"><span data-stu-id="d0801-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="d0801-128">Выберите в иерархии объект Game Микседреалититулкит и выберите **Копировать и настроить** , чтобы клонировать профиль смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d0801-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![леапмотионпрофилеклоне](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="d0801-130">Выберите профиль **входной** конфигурации</span><span class="sxs-lookup"><span data-stu-id="d0801-130">Select the **Input** Configuration Profile</span></span>

    ![Входной профиль конфигурации 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="d0801-132">Выберите **клон** во входном системном профиле, чтобы разрешить изменение.</span><span class="sxs-lookup"><span data-stu-id="d0801-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![леапмотионинпутпрофилеклоне](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="d0801-134">Откройте раздел **поставщики входных данных** и выберите **Добавить поставщик данных** вверху. в конце списка будет добавлен новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="d0801-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="d0801-135">Откройте новый поставщик данных и задайте для него **тип** **Microsoft. микседреалити. Toolkit. леапмотион. Input > леапмотиондевицеманажер**</span><span class="sxs-lookup"><span data-stu-id="d0801-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Добавление поставщика данных LEAP](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="d0801-137">Выберите **клон** , чтобы изменить параметры движения по умолчанию LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![леапдатапровидерпреклоне](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="d0801-139">Поставщик данных о движении LEAP содержит `LeapControllerOrientation` свойство, которое является расположением контроллера Motion LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="d0801-140">`LeapControllerOrientation.Headset` Указывает, что контроллер подключен к гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="d0801-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="d0801-141">`LeapControllerOrientation.Desk` Указывает, что контроллер размещается плоским на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="d0801-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="d0801-142">По умолчанию устанавливается значение `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="d0801-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="d0801-143">Ориентация каждого контроллера содержит свойства смещения:</span><span class="sxs-lookup"><span data-stu-id="d0801-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="d0801-144">Свойства смещения ориентации **гарнитуры** отражают свойства смещения в компоненте леапксрсервицепровидер.</span><span class="sxs-lookup"><span data-stu-id="d0801-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="d0801-145">`LeapVRDeviceOffsetMode`Имеет три параметра: Default, смещение и преобразование заголовка вручную.</span><span class="sxs-lookup"><span data-stu-id="d0801-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="d0801-146">Если используется режим смещения по умолчанию, то смещение не будет применяться к контроллеру движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="d0801-147">Режим смещения Головков вручную позволяет изменять три свойства: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` и `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="d0801-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="d0801-148">Затем значения свойств смещения оси применяются к размещению контроллера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d0801-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="d0801-149">Режим смещения преобразования содержит `LeapVRDeviceOrigin` свойство Transform, которое указывает новый источник для контроллера движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="d0801-150">Ориентация на **Рабочий стол** содержит `LeapControllerOffset` свойство, определяющее положение точки привязки для стрелок на столе.</span><span class="sxs-lookup"><span data-stu-id="d0801-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="d0801-151">Смещение вычисляется относительно главной позиции камеры, а значение по умолчанию — (0,-0,2, 0,35), чтобы обеспечить отображение стрелок спереди и в представлении камеры.</span><span class="sxs-lookup"><span data-stu-id="d0801-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="d0801-152">Свойства смещения в профиле применяются один раз при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="d0801-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="d0801-153">Чтобы изменить значения во время выполнения, получите поставщик услуг LEAP Motion на основе диспетчер устройств Motion:</span><span class="sxs-lookup"><span data-stu-id="d0801-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="d0801-154">`EnterPinchDistance` и `ExitPinchDistance` — это пороговые значения расстояния для обнаружения жестов сжатия и воздушного касания.</span><span class="sxs-lookup"><span data-stu-id="d0801-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="d0801-155">Жест сжатия вычисляется путем измерения расстояния между кончиком указателя и кончиком пальца.</span><span class="sxs-lookup"><span data-stu-id="d0801-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="d0801-156">Чтобы вызвать событие при входе в систему, значение по умолчанию равно `EnterPinchDistance` 0,02.</span><span class="sxs-lookup"><span data-stu-id="d0801-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="d0801-157">Чтобы вызвать событие при входе в систему (выход из сжатия), расстояние по умолчанию между кончиком указателя по индексу и подсказкой Thumb будет 0,05.</span><span class="sxs-lookup"><span data-stu-id="d0801-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="d0801-158">`LeapControllerOrientation`: Гарнитура (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="d0801-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="d0801-159">`LeapControllerOrientation`: Рабочий стол</span><span class="sxs-lookup"><span data-stu-id="d0801-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![леафеадсетгиф](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![леапдескгиф](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![леафеадсетинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![леапдескинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="d0801-164">Тестирование поставщика данных движения LEAP</span><span class="sxs-lookup"><span data-stu-id="d0801-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="d0801-165">После добавления поставщика данных о движении LEAP в входной системный профиль нажмите кнопку Воспроизвести, переместите руку перед контроллером движения LEAP, и вы увидите представление руки.</span><span class="sxs-lookup"><span data-stu-id="d0801-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="d0801-166">Сборка проекта</span><span class="sxs-lookup"><span data-stu-id="d0801-166">Building your project</span></span>
    - <span data-ttu-id="d0801-167">Выберите **файл > параметры сборки**</span><span class="sxs-lookup"><span data-stu-id="d0801-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="d0801-168">При использовании поставщика данных о движении LEAP поддерживаются только автономные сборки.</span><span class="sxs-lookup"><span data-stu-id="d0801-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="d0801-169">Инструкции по использованию головного телефона Windows Mixed Reality для автономных сборок см. в статье [Создание и развертывание мртк (автономной)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span><span class="sxs-lookup"><span data-stu-id="d0801-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="d0801-170">Получение соединений с рукой</span><span class="sxs-lookup"><span data-stu-id="d0801-170">Getting the hand joints</span></span>

<span data-ttu-id="d0801-171">Получение соединений с помощью поставщика данных о движении LEAP аналогично получению соединения типа "рука" с МРТКм.</span><span class="sxs-lookup"><span data-stu-id="d0801-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="d0801-172">Дополнительные сведения см. в разделе [Отслеживание вручную](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="d0801-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="d0801-173">С помощью МРТК в сцене Unity и поставщика данных о движении LEAP, добавленного в качестве поставщика входных данных в входном системном профиле, создайте пустой объект Game и присоедините следующий пример скрипта.</span><span class="sxs-lookup"><span data-stu-id="d0801-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="d0801-174">Этот сценарий является простым примером того, как извлекать набор Объединенных соединений Palm при движении в LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="d0801-175">Сфера соответствует левому углу, в то время как куб соответствует правой стороне.</span><span class="sxs-lookup"><span data-stu-id="d0801-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="d0801-176">Совет по рабочему процессу редактора Unity</span><span class="sxs-lookup"><span data-stu-id="d0801-176">Unity editor workflow tip</span></span>

<span data-ttu-id="d0801-177">Для использования поставщика данных о движении LEAP не требуется гарнитура VR.</span><span class="sxs-lookup"><span data-stu-id="d0801-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="d0801-178">Изменения в приложении МРТК можно тестировать в редакторе с помощью LEAP без гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="d0801-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="d0801-179">В редакторе будут отображаться стрелки движения, не подключенные к сети VR.</span><span class="sxs-lookup"><span data-stu-id="d0801-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="d0801-180">Если `LeapControllerOrientation` для задано значение **гарнитура**, то контроллеру Motion в LEAP должен быть назначена одна рука с камерой, направленной вперед.</span><span class="sxs-lookup"><span data-stu-id="d0801-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="d0801-181">Если камера перемещена с помощью ключей трассе в редакторе и `LeapControllerOrientation` является **гарнитурой**, руки не будут следовать за камерой.</span><span class="sxs-lookup"><span data-stu-id="d0801-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="d0801-182">Руки будут перемещаться на камеру только в том случае, если телефонная гарнитура VR подключена, а `LeapControllerOrientation` задается **гарнитура**.</span><span class="sxs-lookup"><span data-stu-id="d0801-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="d0801-183">LEAP будет следовать за перемещением камеры в редакторе, если установлен в `LeapControllerOrientation` **рабочее** место.</span><span class="sxs-lookup"><span data-stu-id="d0801-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="d0801-184">Удаление LEAP из проекта</span><span class="sxs-lookup"><span data-stu-id="d0801-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="d0801-185">Переход к разным модулям управления движением LEAP в **наборе средств Mixed Reality** для  >    >  **разных модулей Unity**</span><span class="sxs-lookup"><span data-stu-id="d0801-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="d0801-186">Разрешите обновление Unity в виде ссылок в файле **Microsoft. микседреалити. Toolkit. Providers. леапмотион. асмдеф** на этом шаге.</span><span class="sxs-lookup"><span data-stu-id="d0801-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="d0801-187">Закрыть Unity</span><span class="sxs-lookup"><span data-stu-id="d0801-187">Close Unity</span></span>
1. <span data-ttu-id="d0801-188">Закрыть Visual Studio, если она открыта</span><span class="sxs-lookup"><span data-stu-id="d0801-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="d0801-189">Откройте проводник и перейдите к корню проекта Unity МРТК.</span><span class="sxs-lookup"><span data-stu-id="d0801-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="d0801-190">Удаление каталога **унитипрожектнаме/Library**</span><span class="sxs-lookup"><span data-stu-id="d0801-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="d0801-191">Удалите каталог **унитипрожектнаме/Assets/plugins/леапмотион**</span><span class="sxs-lookup"><span data-stu-id="d0801-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="d0801-192">Удаление файла **унитипрожектнаме/Assets/plugins/леапмотион. meta**</span><span class="sxs-lookup"><span data-stu-id="d0801-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="d0801-193">Повторное открытие Unity</span><span class="sxs-lookup"><span data-stu-id="d0801-193">Reopen Unity</span></span>

<span data-ttu-id="d0801-194">В Unity 2018,4 можно заметить, что ошибки по-прежнему остаются в консоли после удаления библиотеки и ресурсов ядра движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="d0801-195">Если ошибки регистрируются после повторного открытия, перезапустите Unity еще раз.</span><span class="sxs-lookup"><span data-stu-id="d0801-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="d0801-196">Общие ошибки</span><span class="sxs-lookup"><span data-stu-id="d0801-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="d0801-197">LEAP не интегрирован с МРТК</span><span class="sxs-lookup"><span data-stu-id="d0801-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="d0801-198">Чтобы проверить, интегрированы ли модули Unity Motion с МРТК, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="d0801-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="d0801-199">Выберите **набор средств для смешанной реальности > служебные программы > LEAP Motion > проверить состояние интеграции**</span><span class="sxs-lookup"><span data-stu-id="d0801-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="d0801-200">Откроется всплывающее окно с сообщением о том, интегрированы ли модули Unity для LEAP с МРТК.</span><span class="sxs-lookup"><span data-stu-id="d0801-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="d0801-201">Если сообщение говорит о том, что ресурсы не были интегрированы:</span><span class="sxs-lookup"><span data-stu-id="d0801-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="d0801-202">Убедитесь, что модули Unity Motion находятся в проекте</span><span class="sxs-lookup"><span data-stu-id="d0801-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="d0801-203">Убедитесь, что добавленная версия поддерживается, см. таблицу в верхней части страницы для поддерживаемых версий.</span><span class="sxs-lookup"><span data-stu-id="d0801-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="d0801-204">Пробная работа с **набором средств Mixed Reality > служебные программы > LEAP motion > интеграция модулей Unity Motion**</span><span class="sxs-lookup"><span data-stu-id="d0801-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="d0801-205">Сбой при копировании многопользовательского ХЛАПИ сборки</span><span class="sxs-lookup"><span data-stu-id="d0801-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="d0801-206">При импорте ресурсов ядра Unity для работы с LEAP эта ошибка может быть записана в журнал:</span><span class="sxs-lookup"><span data-stu-id="d0801-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="d0801-207">**Решение**</span><span class="sxs-lookup"><span data-stu-id="d0801-207">**Solution**</span></span>

- <span data-ttu-id="d0801-208">Краткосрочное решение — перезапустить Unity.</span><span class="sxs-lookup"><span data-stu-id="d0801-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="d0801-209">Дополнительные сведения см. в описании [проблемы 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="d0801-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="d0801-210">Сцена примера движения LEAP</span><span class="sxs-lookup"><span data-stu-id="d0801-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="d0801-211">В примере сцены используется профиль Дефаултлеапмотионконфигуратион и определяется, правильно ли настроен проект Unity для использования поставщика данных движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="d0801-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="d0801-212">Пример сцены содержится в пакете **Microsoft. микседреалити. Toolkit. examples** в **мртк/examples/демонстрации/хандтраккинг/** Directory.</span><span class="sxs-lookup"><span data-stu-id="d0801-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d0801-213">См. также</span><span class="sxs-lookup"><span data-stu-id="d0801-213">See also</span></span>

<span data-ttu-id="d0801-214">-Поставщики входных [данных](../features/input/input-providers.md) 
- [Отслеживание вручную](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d0801-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
